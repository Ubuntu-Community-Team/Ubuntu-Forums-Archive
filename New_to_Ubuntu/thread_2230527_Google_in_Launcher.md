---
title: "Google in Launcher"
date: 2014-06-19
forum: New to Ubuntu
---

### Post by gordon99 on 2014-06-19
I have the Firefox globe icon on launcher which takes me directly to BBC Homepage instead of to Google search engine input page, which is fine. However, I would also like a Google search engine icon so I click on it to go straight to a Google input page as an alternative to using the Google input line in Homepage. Can this be arranged and, if it can, how?

---

### Post by grumblebum2 on 2014-06-20
The best way to do this would be via a quicklist item.
If you create another icon launcher you will have confusion as to which icon the firefox window belongs to.
Run...
```
gedit ~/.local/share/applications/firefox.desktop
```

Copy and paste this into it and then save.
```
[Desktop Entry]
Version=1.0
Name=Firefox
Comment=Browse the World Wide Web
Keywords=Internet;WWW;Browser;Web;Explorer
Exec=firefox %u 
Terminal=false
X-MultipleArgs=false
Type=Application
Icon=firefox
Categories=GNOME;GTK;Network;WebBrowser;
StartupNotify=true

Actions=NewWindow;NewPrivateWindow;google;

[Desktop Action NewWindow]
Name=Open a New Window
Name[ar]=&#1575;&#1601;&#1578;&#1581; &#1606;&#1575;&#1601;&#1584;&#1577; &#1580;&#1583;&#1610;&#1583;&#1577;
Name[ast]=Abrir una ventana nueva
Name[bn]=Abrir una ventana nueva
Name[ca]=Obre una finestra nova
Name[cs]=Otev&#345;ít nové okno
Name[da]=Åbn et nyt vindue
Name[de]=Ein neues Fenster öffnen
Name[el]=&#902;&#957;&#959;&#953;&#947;&#956;&#945; &#957;&#941;&#959;&#965; &#960;&#945;&#961;&#945;&#952;&#973;&#961;&#959;&#965;
Name[es]=Abrir una ventana nueva
Name[fi]=Avaa uusi ikkuna
Name[fr]=Ouvrir une nouvelle fenêtre
Name[gl]=Abrir unha nova xanela
Name[he]=&#1508;&#1514;&#1497;&#1495;&#1514; &#1495;&#1500;&#1493;&#1503; &#1495;&#1491;&#1513;
Name[hr]=Otvori novi prozor
Name[hu]=Új ablak nyitása
Name[it]=Apri una nuova finestra
Name[ja]=&#26032;&#12375;&#12356;&#12454;&#12451;&#12531;&#12489;&#12454;&#12434;&#38283;&#12367;
Name[ko]=&#49352; &#52285; &#50676;&#44592;
Name[ku]=Paceyeke nû veke
Name[lt]=Atverti nauj&#261; lang&#261;
Name[nb]=Åpne et nytt vindu
Name[nl]=Nieuw venster openen
Name[pt]=Abrir nova janela
Name[pt_BR]=Abrir nova janela
Name[ro]=Deschide o fereastr&#259; nou&#259;
Name[ru]=&#1053;&#1086;&#1074;&#1086;&#1077; &#1086;&#1082;&#1085;&#1086;
Name[sk]=Otvori&#357; nové okno
Name[sl]=Odpri novo okno
Name[sv]=Öppna ett nytt fönster
Name[tr]=Yeni pencere aç 
Name[ug]=&#1610;&#1744;&#1709;&#1609; &#1603;&#1734;&#1586;&#1606;&#1749;&#1603; &#1574;&#1744;&#1670;&#1609;&#1588;
Name[uk]=&#1042;&#1110;&#1076;&#1082;&#1088;&#1080;&#1090;&#1080; &#1085;&#1086;&#1074;&#1077; &#1074;&#1110;&#1082;&#1085;&#1086;
Name[vi]=M&#7903; c&#7917;a s&#7893; m&#7899;i
Name[zh_CN]=&#26032;&#24314;&#31383;&#21475;
Name[zh_TW]=&#38283;&#21855;&#26032;&#35222;&#31383;
Exec=firefox -new-window
OnlyShowIn=Unity;

[Desktop Action NewPrivateWindow]
Name=Open a New Private Window
Name[ar]=&#1575;&#1601;&#1578;&#1581; &#1606;&#1575;&#1601;&#1584;&#1577; &#1580;&#1583;&#1610;&#1583;&#1577; &#1604;&#1604;&#1578;&#1589;&#1601;&#1581; &#1575;&#1604;&#1582;&#1575;&#1589;
Name[ca]=Obre una finestra nova en mode d'incògnit
Name[de]=Ein neues privates Fenster öffnen
Name[es]=Abrir una ventana privada nueva
Name[fi]=Avaa uusi yksityinen ikkuna
Name[fr]=Ouvrir une nouvelle fenêtre de navigation privée
Name[he]=&#1508;&#1514;&#1497;&#1495;&#1514; &#1495;&#1500;&#1493;&#1503; &#1490;&#1500;&#1497;&#1513;&#1492; &#1508;&#1512;&#1496;&#1497;&#1514; &#1495;&#1491;&#1513;
Name[hu]=Új privát ablak nyitása
Name[it]=Apri una nuova finestra anonima
Name[nb]=Åpne et nytt privat vindu
Name[ru]=&#1053;&#1086;&#1074;&#1086;&#1077; &#1087;&#1088;&#1080;&#1074;&#1072;&#1090;&#1085;&#1086;&#1077; &#1086;&#1082;&#1085;&#1086;
Name[sl]=Odpri novo okno zasebnega brskanja
Name[tr]=Yeni bir pencere aç
Name[uk]=&#1042;&#1110;&#1076;&#1082;&#1088;&#1080;&#1090;&#1080; &#1085;&#1086;&#1074;&#1077; &#1074;&#1110;&#1082;&#1085;&#1086; &#1091; &#1087;&#1086;&#1090;&#1072;&#1081;&#1083;&#1080;&#1074;&#1086;&#1084;&#1091; &#1088;&#1077;&#1078;&#1080;&#1084;&#1110;
Name[zh_TW]=&#38283;&#21855;&#26032;&#38577;&#31169;&#28687;&#35261;&#35222;&#31383;
Exec=firefox -private-window
OnlyShowIn=Unity;

[Desktop Action google]
Name=Google
Exec=firefox google.com
OnlyShowIn=Unity;
```

Log out/in and you should see a right click item for "Google" in the firefox launcher icon.

.desktop files in **~/.local/share/applications** override those in **/usr/share/applications**
To revert back to the default launcher just remove the one in **~/.local/share/applications**

---

### Post by gordon99 on 2014-06-20
Hello grumblebum2. You have certainly gone to a lot of trouble to answer my two questions and I am very grateful for that. I note you have shown me 'the best way' to achieve what I am seeking to do. I dread to think what would be involved doing it any other way. I realize that all I have to do is 'copy and paste' but why does it require a long algorithm just to get a convenient access to Google's input page? I may just carry on with what I've got. Thanks again however.

---

### Post by grumblebum2 on 2014-06-20
It may seem like a lot of trouble but it's just a copy of an existing .desktop file
With a couple of lines added for a quicklist item.
Prefer to use bookmarks myself. :p

---

### Post by pfeiffep on 2014-06-20
I suggest enabling the FF bookmarks toolbar , then add [https://www.google.com](https://www.google.com) to it.

---

### Post by buzzingrobot on 2014-06-20
Gordon, that desktop file is responsible for the icon that appears and what it does when you click on it. Every icon you click to execute something has a corresponding ".desktop" file. Grumblebum's tells the icon to launch Firefox and display google.com.

Firefox displays whatever URL has been set in Preferences as the default Home page when launched.  You can set it to Google or any other site. You csn only have one, though.


An alternative: Create bookmarks in the Bookmarks Toolbar so Google, BBC, etc. are always readily available. You may need to enable the Bookmarks Toolbar, first.

---

### Post by gordon99 on 2014-06-20
My problem, as I well realize, is that I am trying to migrate away from Windows taking the convenient aspects of that OS with me. I will certainly try the 'Create bookmarks' suggestion however. Thanks all.

---

### Post by gordon99 on 2014-06-21
When I looked further i noticed that, in what I believe to be the "bookmarks toolbar" in homepage, I can click on "Ubuntu start page" to get to google input. This involves one click more than I was seeking to achieve but it is good enough for me. I know that google can be inputted within the homepage itself but I prefer a  clear page with a large box to write in.

---

### Post by buzzingrobot on 2014-06-21
The Bookmarks Toolbar in Firefox is illustrated and explained here: [https://support.mozilla.org/en-US/kb/bookmarks-toolbar-display-favorite-websites](https://support.mozilla.org/en-US/kb/bookmarks-toolbar-display-favorite-websites).  Bookmarking google.com to the Bookmarks Toolbar -- right click, select "Bookmark This Page", then change "Bookmarks Menu" to "Bookmarks Toolbar" -- will create in tab in the Toolbar that opens the Google search page.  That page can also be set as the home page:  When it's open, open preferences (Edit->Preferences), click on the "General" icon, make sure "use my home page" appears in the "When Firefox starts..." field, and click "Use Current Page".

---

