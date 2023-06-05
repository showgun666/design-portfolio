---
Title: KMOM05-Rapport
Description: Image hosting websites report - KMOM05
Template: analysis-report
---

# Analys av Hemsidor som lagrar bilder

Den här rapporten syftar till att visa på att jag skapat mig förståelse för optimering av webbsidor och sajter samt behärskar nomenklatur inom området.

Urval
-----------------------

Eftersom majoriteten av datamängden som överförs på hemsidor är just bilder så valde jag hemsidor som har bildförvaring och delning som sitt syfte. Jag visste om imgur från början och sökte efter liknande hemsidor och hittade deviantart.com och artstation.com, två sidor som är till för konstnärer att lägga upp sin konst. Jag förväntade mig att hemsidorna skulle vara optimerade för just bilder men kanske skulle vara bristfälliga på andra delar i sin optimering.

Metod
-----------------------
Till min hjälp så använde jag mig utav https://pagespeed.web.dev/ som är ett verktyg som mäter hastigheten på en specifik sida på en websajt. Sedan så använde jag mig utav nätverksdelen i DevTools i min webbläsare för att observera laddningstider och datamängder. För varje webbsajt tog jag sedan och mätte tre sidor devtools flik networks och noterade sidans laddningstid tillsammans med antalet resurser som laddades samt sidans totala storlek. För varje sida så tog jag tre mätningar och använde snittvärdet i resultatet.

Resultat
-----------------------
<iframe src="https://docs.google.com/spreadsheets/d/e/2PACX-1vRQPwjunhaW2xGpuN64puPxr628gKN1wr3_RGJQ11Z7h6uPQZV-bmhWK9k977Dm8IsbiDqEeXTKpcI9/pubhtml?widget=true&amp;headers=false" class="embed-container google-sheet"></iframe>
<a href="%base_url%/image/imgur.jpg" target="_blank">
    ![Bild på imgur](%base_url%/image/imgur.jpg?w=800)
</a>

Ovan bild är förstasidan på imgur.

https://imgur.com/

https://imgur.com/emerald

https://imgur.com/gallery/dQuq0ZR

Imgur hade ganska god hantering av sina bilder trots viss utvecklingspotential men det som var största tidstjuven var hur js-kod laddades som inte användes eller så gjorde js-koden att sidan laddade långsammare, vilket kan arbetas med för att förbättra prestandan i framtiden.

<a href="%base_url%/image/deviantart.jpg" target="_blank">
    ![Bild på deviantart](%base_url%/image/deviantart.jpg?w=800)
</a>

Ovan bild är förstasidan på deviantart.

https://www.deviantart.com/

https://www.deviantart.com/shop

https://www.deviantart.com/core-membership

Deviantart hade slumpmässigt antal bilder och inte alltid bra hantering av bildstorlekar i sin butiksida, en sida som för övrigt bör vara snabb och användarvänlig, vilket gjorde att den laddade långsamt och ibland väldigt långsamt, men för den generelle användaren så handlar det generellt om att komprimera bilderna på ett effektivare sätt vilket skulle kunna spara uppemot 9 sekunder på förstasidan enligt pagespeed.web.dev.

<a href="%base_url%/image/artstation.jpg" target="_blank">
    ![Bild på artstation](%base_url%/image/artstation.jpg?w=800)
</a>

Ovan bild är förstasidan på artstation.

https://www.artstation.com/

https://www.artstation.com/blogs

https://www.artstation.com/marketplace/game-dev

Artstation skulle kunna begränsa antalet bilder som laddas åt gången istället för att ha ett bestämt antal oavsett view, samt använda bättre format och komprimera bilderna.

Imgur hade en redirect till en annan sida för sin butik, så den kunde jag inte använda.





Analys
-----------------------

Med tanke på att alla tre sidorna hanterar bilder i absurda mängder så var mitt antagande att de skulle ha best practice och mycket god hantering av bilder, men så var inte fallet. Imgur som är den största sidan gjorde ett ganska bra jobb men deviantart och särskilt artstation var mycket dålig när det kom till bildhantering. Det var fel storlekar, för många bilder, ingen eller dålig anpassning efter viewstorlek och daterade format som användes för att skicka bilderna. Sedan så fanns det problem med att DOM-träden var stora eller att det var mycket javascriptkod som segade ner eller inte ens användes på sidorna. Artstations förstasida har en redirect, men innan redirecten hinner genomföras så överförs en avsevärd mängd data, uppskattningsvis kring 30 requests och 3mb data innan användaren kommer vidare till dit den ska. Det är inte heller jättebra skulle jag vilja påstå då användaren får vänta längre och det blir en onödig tids- och energiförbrukning. Butiksidan på deviantart laddade olika bannerbilder som var olika stora vilket gav varierande laddningstider och mängd data överförd vilket var ett tydligt sätt att se att bildhanteringen inte var jättebra på sidan. Med min begränsade kunskap i bilder så kan jag tycka att en bild inte borde vara dubbelt så stor som en annan om de båda fyller exakt lika stor yta och samma funktion på en sida.

Generellt sett så hade samtliga sidor problem med sin prestanda men jag anser utan någon särskild förvåning att imgur var bäst. Imgur laddade inte in för många bilder åt gången och var mycket responsiv samt använde rätt format vilket gav den behagligaste användarupplevelsen. Näst efter kom deviantart och sist kom artstation av anledningar som givits ovan.

För mig så känns en hemsida snabb om jag är inne och kan börja orientera mig och förstå vad jag har kring mig på 3 sekunder, även om delar fortfarande laddar in. Om layout flyttar på sig fortfarande så blir jag lätt otålig och kan välja att lämna en sida men om det är statiskt så kan jag vänta på bilder.

När jag väntade på imgur så fick jag ofta en grå bakgrundsskärm att stirra på medan jag väntade vilket jag inte tyckte om, men för artstation så var det värre då jag såg layout byggas och saker hamna på plats innan jag blev redirectad för att få vänta igen. Sedan så är huvudpoängen med dessa sidor just bilderna, vilket gör det hemskt att sitta och vänta uppemot 20 sekunder på att bilder ska ladda in. Samtliga sidor börjar ladda in fler sidor ifall användaren scrollar ned, vilket skulle vara en naturlig reaktion vid vanlig användning av en sådan här hemsida, vilket då skulle förlänga tiden ytterligare. Jag brukade inget scrollande i mina tester och tiderna var ändå tvåsiffriga.

Min gräns för vad som är långsamt kan därför vara lite flytande, men jag har för mig själv identifierat skiftande layout, saknade rubriker och texter samt redirects som element som kortar på min stubin. Självklart kan det också bero på vad jag laddar. Jag kan förstå att en video i superkvalité kan behöva lite tid att buffra, eller en högupplöst bild i fullscreen kan behöva ladda in sina megabytes i några sekunder.

Generellt skulle jag påstå att runt 8 sekunder verkade vara när jag började bli riktigt otålig när jag testade sidorna så det får bli min gräns. Jag anser utöver det att samtliga sidor jag valde var långsamma.



Referenser
-----------------------

Inga referenser att nämna utöver material jag blivit delgiven i kursen.

Övrigt
-----------------------

Mitt namn är Markus Lindgren och jag har skrivit den här rapporten på egen hand.