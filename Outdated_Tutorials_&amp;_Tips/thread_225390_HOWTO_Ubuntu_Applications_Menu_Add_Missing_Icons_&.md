---
title: "HOWTO: Ubuntu Applications Menu: Add Missing Icons &amp; Fix Broken Icons"
date: 2006-07-29
forum: Outdated Tutorials &amp; Tips
---

### Post by greenstar on 2006-07-29
[SIZE=2][COLOR=#000000]**This guide is written for Dapper Drake 6.06**

[B]Note 1: This tutorial assumes that you've enabled the universe & multiverse repositories. If you haven't, the HOWTO for that is [here]("https://help.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html").

Note 2: With the exception of the follow-along examples, all menu entry files are accessed read-only.[/B] [B]This is completely safe as the commands given for this do not use sudo, su, etc. The only other commands that use administrative privilege are the installation of the Debian menu & the Circus Linux game as part of the HOWTO.
[/B]

[B] Purpose:
- [/B][/COLOR][/SIZE]**[SIZE=2]Install the Debian menu so all installed applications are accessible via Applications->Debian.[/SIZE]**[SIZE=2][COLOR=#000000][B]
- Adding missing entries and/or icons to Ubuntu's Applications menu.
- Help with applications that won't launch from the menu icon.
[/B] 

[COLOR=#0000ff]Blue [/COLOR]text is informational and not required to “just get it done”. You will gain a better understanding of the what, where, & why if you read the [COLOR=#0000ff]blue[/COLOR] text.

[/COLOR][/SIZE][LEFT][SIZE=2][COLOR=#000000][COLOR=#0000ff]I have spent a good bit of time customizing my Applications menu, mostly adding entries and icons for the Debian packages that only show in the Debian menu. I like the terminal just fine, it's saved my bacon more than a few times, but I also like a nice, clean uniform Applications menu to peruse. I think Ubuntu has done a great job with the menus for Ubuntu packages, but things can get a bit messy when you start adding Debian packages. Oh yeah, I like a LOT of the Debian packages, especially the games.[/COLOR][/COLOR][/SIZE]


[/LEFT]
     
  [LEFT]   
[LEFT][SIZE=2][COLOR=#000000] [SIZE=4]**A.**[/SIZE]** Install the Debian menu to make all installed applications accessible via the Applications->Debian menu.**[/COLOR][/SIZE]

[SIZE=2][COLOR=#000000] I have the Debian menu installed, it will give us the info necessary to build the menu entries for our Ubuntu menu.[/COLOR][/SIZE]
[/LEFT]
           [SIZE=2][COLOR=#000000] 
Let's make sure you do too:
[COLOR=Red] Edit:[/COLOR] Added suggestion by [ryu kun]("http://ubuntuforums.org/member.php?u=18168") from [this]("http://http://ubuntuforums.org/showpost.php?p=1507303&postcount=7") post further down the thread.
```
sudo apt-get update
sudo apt-get install menu menu-xdg
update-menus
``` 
Verify this after installation finishes by going to: Applications->Debian

[COLOR=#0000ff]If you haven't installed any Debian packages, the Debian menu will still install properly, but may not be enabled. You can verify this in Alacarte by going to: Applications->Accessories->Alacarte and clicking Applications on the left, and it should be listed on the right. The Debian menu will become visible in the Applications menu when you install a Debian package from the repositories. Don't worry if you can't enable it yet, it'll be there when it's supposed to.[/COLOR]
[/COLOR][/SIZE][SIZE=2]
[/SIZE] [/LEFT]
                  [B][SIZE=3]
[/SIZE][/B][CENTER]
   [LEFT]
[/LEFT]
             [/CENTER]
             [SIZE=2][COLOR=#000000] **[SIZE=4]B.[/SIZE] Adding missing entries & icons to Ubuntu's Applications menu.**

[COLOR=#0000ff]I'm going to show you how to do this manually (without Alacarte), but if you know the path to the icon & executable binary (the application) as well as the command to run the application, then you can just as easily use the Alacarte Menu Editor. The reason I have given manual instructions first is that I will also show you how to find the above information if you don't know it.[/COLOR]

**1.** Let's start by identifying the directories that contain the menu entries we'll be working with. [COLOR=#0000ff]As background for noobs, the menu is constructed of a bunch of simple text files stored in the following designated directories. [/COLOR]

Ubuntu Applications menu entries are here:
/usr/share/applications 


Debian Menu entries are here:
/var/lib/menu-xdg/applications/menu-xdg 


Icons are found in these locations:
/usr/share/pixmaps
/usr/share/icons
/usr/bin/name-of-app

[COLOR=#0000ff]Most of these text files are less than 10 lines long and are easy to understand, although many of the menu entries that come pre-installed with Ubuntu have a large number of translations for the text in the Name & Comment fields which adds a significant number to the line count.

The naming convention for .desktop files in the Ubuntu menu is: application-name.desktop so the menu entry for gaim would be a text file named gaim.desktop and would be found in: /usr/share/applications. Simple. Once you get the hang of it, you'll be able to guess the filename easily in most cases.

The naming convention for .desktop files in the Debian menu is: X-Debian-*Maincategory*-*Subcategory*-*app_name*.desktop so the menu entry for gaim would be a text file named X-Debian-Apps-Net-gaim.desktop and would be found in: /var/lib/menu-xdg/applications/menu-xdg. This makes guessing the filename a good bit more difficult, so we'll need to enlist the aid of gedit to browse the Debian menu entry directory, more on this later. [/COLOR]

**2**. Let's take a look at the contents of the Ubuntu menu entry file. I've bolded the lines that are actually necessary for the English menu. For other languages, adjust as necessary. 
Open a terminal by going to: Applications->Accessories->Terminal, then do:

```
gedit /usr/share/applications/gaim.desktop
``` 
Since this is a pre-installed package, we'll see lots of translations:

> 
[B][Desktop Entry]
Encoding=UTF-8
Categories=Application;Network;
Exec=gaim
Icon=gaim.png
StartupNotify=true
Terminal=false
Type=Application
Name=Gaim Internet Messenger[/B]
Name[ca]=Missatger d'Internet Gaim
Name[cs]=Gaim Internet Messenger
Name[da]=Gaim - internet beskeder
Name[de]=Gaim Internet Messenger
Name[es]=Gaim - cliente de mensajería de Internet
Name[fr]=Gaim Messagerie Internet
Name[hu]=Gaim azonnali üzenetküld&#337;
Name[it]=Gaim Internet Messenger
Name[ja]=Gaim > [FONT=DejaVu Sans][FONT=DejaVu Sans]&#12452;&#12531;&#12479;&#12540;&#12493;&#12483;&#12488;&#12539;&#12513;&#12483;&#12475;&#12531;&#12472;&#12515;&#12540;[/FONT][/FONT]
Name[ko]=[FONT=DejaVu Sans][FONT=DejaVu Sans]&#44172;&#51076; &#47700;&#49888;&#51200;[/FONT][/FONT]
Name[nb]=Gaim lynmeldingsklient
Name[nl]=Gaim - Expresberichten
Name[pl]=Komunikator Internetowy Gaim
Name[pt_BR]=Mensageiro via Internet Gaim
Name[pt]=Mensageiro Internet Gaim
Name[ro]=Mesagerul Gaim
Name[ru]=Gaim - &#1082;&#1083;&#1080;&#1077;&#1085;&#1090; &#1086;&#1073;&#1084;&#1077;&#1085;&#1072; &#1084;&#1075;&#1085;&#1086;&#1074;&#1077;&#1085;&#1085;&#1099;&#1084;&#1080; &#1089;&#1086;&#1086;&#1073;&#1097;&#1077;&#1085;&#1080;&#1103;&#1084;&#1080;
Name[sl]=Gaim - spletni sel
Name[sq]=Lajmësjellësi Internet Gaim
Name[sv]=Gaim Internet Messenger
Name[zh_CN]=Gaim [FONT=DejaVu Sans][FONT=DejaVu Sans]&#20114;&#32852;&#32593;&#36890;&#35759;&#31243;&#24207;[/FONT][/FONT]
Name[zh_TW]=Gaim [FONT=DejaVu Sans][FONT=DejaVu Sans]&#32178;&#36335;&#21363;&#26178;&#36890;[/FONT][/FONT]
**GenericName=Internet Messenger**
GenericName[ca]=Missatger d'Internet
GenericName[cs]=Internet Messenger
GenericName[da]=Internet beskeder
GenericName[de]=Internet Messenger
GenericName[es]=Cliente de mensajería de Internet
GenericName[fr]=Messagerie internet
GenericName[hu]=Azonnali üzenetküld&#337;
GenericName[it]=Internet Messenger
GenericName[ja]=[FONT=DejaVu Sans][FONT=DejaVu Sans]&#12452;&#12531;&#12479;&#12540;&#12493;&#12483;&#12488;&#12539;&#12513;&#12483;&#12475;&#12531;&#12472;&#12515;&#12540;[/FONT][/FONT]
GenericName[ko]=[FONT=DejaVu Sans][FONT=DejaVu Sans]&#47700;&#49888;&#51200;[/FONT][/FONT]
GenericName[nb]=Lynmeldingsklient
GenericName[nl]=Expresberichten
GenericName[pl]=Komunikator Internetowy
GenericName[pt_BR]=Mensageiro via Internet
GenericName[pt]=Mensageiro Internet
GenericName[ro]=Client de mesagerie
GenericName[ru]=&#1050;&#1083;&#1080;&#1077;&#1085;&#1090; &#1086;&#1073;&#1084;&#1077;&#1085;&#1072; &#1084;&#1075;&#1085;&#1086;&#1074;&#1077;&#1085;&#1085;&#1099;&#1084;&#1080; &#1089;&#1086;&#1086;&#1073;&#1097;&#1077;&#1085;&#1080;&#1103;&#1084;&#1080;
GenericName[sl]=Spletni sel
GenericName[sq]=Lajmësjellës Internet
GenericName[sv]=Meddelandeklient
GenericName[zh_CN]=[FONT=DejaVu Sans][FONT=DejaVu Sans]&#20114;&#32852;&#32593;&#36890;&#35759;&#31243;&#24207;[/FONT][/FONT]
GenericName[zh_TW]=[FONT=DejaVu Sans][FONT=DejaVu Sans]&#32178;&#36335;&#21363;&#26178;&#36890;[/FONT][/FONT]
**Comment=Send instant messages over multiple protocols**
Comment[ca]=Envieu missatges instantanis en múltiples protocols
Comment[cs]=Posílat instant message r&#367;znými protokoly
Comment[da]=Send beskeder over flere protokoller
Comment[de]=Multi-Protokoll Instant Messenger Client
Comment[es]=Cliente de mensajería instantánea multiprotocolo
Comment[fr]=Envoie des messages instantanés en utilisant divers protocoles
Comment[hu]=Azonnali üzenetküldés többféle protokoll használatával
Comment[it]=Client multiprotocollo per messaggi immediati
Comment[ja]=[FONT=DejaVu Sans][FONT=DejaVu Sans]&#35079;&#25968;&#12398;&#12503;&#12525;&#12488;&#12467;&#12523;&#12434;&#20171;&#12375;&#12390;&#12452;&#12531;&#12473;&#12479;&#12531;&#12488;&#12539;&#12513;&#12483;&#12475;&#12540;&#12472;&#12434;&#36865;&#20449;&#12375;&#12414;&#12377;[/FONT][/FONT]Comment[ko]=[FONT=DejaVu Sans][FONT=DejaVu Sans]&#45796;&#51473; &#54532;&#47196;&#53664;&#53084; &#47700;&#49888;&#51200;[/FONT][/FONT]
Comment[nb]=Send lynmeldinger over flere protokoller
Comment[nl]=Multi-protocol programma voor expresberichten
Comment[pl]=Komunikator internetowy obs&#322;uguj&#261;cy kilka protoko&#322;ów
Comment[pt_BR]=Mande mensagens instantâneas por múltiplos protocolos
Comment[pt]=Envie mensagens instantâneas sobre vários protocolos
Comment[ro]=Trimite&#355;i mesaje instant în orice re&#355;ea
Comment[ru]=&#1054;&#1073;&#1084;&#1077;&#1085; &#1084;&#1075;&#1085;&#1086;&#1074;&#1077;&#1085;&#1085;&#1099;&#1084;&#1080; &#1089;&#1086;&#1086;&#1073;&#1097;&#1077;&#1085;&#1080;&#1103;&#1084;&#1080; &#1089; &#1080;&#1089;&#1087;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1085;&#1080;&#1077;&#1084; &#1084;&#1085;&#1086;&#1078;&#1077;&#1089;&#1090;&#1074;&#1072; &#1087;&#1088;&#1086;&#1090;&#1086;&#1082;&#1086;&#1083;&#1086;&#1074;
Comment[sl]=Pošiljajte neposredna sporo&#269;ila prek razli&#269;nih protokolovs
Comment[sq]=Dërgoni mesazhe të atypëratyshëm protokollesh të ndryshëm
Comment[sv]=Sänder snabbmeddelande över många protokoll
Comment[zh_CN]=[FONT=DejaVu Sans][FONT=DejaVu Sans]&#36890;&#36807;&#22810;&#31181;&#21327;&#35758;&#21457;&#36865;&#21363;&#26102;&#28040;&#24687;[/FONT][/FONT]
Comment[zh_TW]=[FONT=DejaVu Sans][FONT=DejaVu Sans]&#36879;&#36942;&#22810;&#31278;&#36890;&#35338;&#21332;&#23450;&#30332;&#36865;&#21363;&#26178;&#35338;&#24687;[/FONT][/FONT]
X-Ubuntu-Gettext-Domain=gaim
 

If we strip the extra languages off the file, we get this (closer to what you'll see on Debian menu entries):

```

[Desktop Entry]
Encoding=UTF-8
Categories=Application;Network;
Exec=gaim
Icon=gaim.png
StartupNotify=true
Terminal=false
Type=Application
Name=Gaim Internet Messenger
GenericName=Internet Messenger
Comment=Send instant messages over multiple protocols
X-Ubuntu-Gettext-Domain=gaim

``` 

**3.** Next, let's look at the contents of the Debian menu entry file.
Open a terminal and do:
```
gedit /var/lib/menu-xdg/applications/menu-xdg/X-Debian-Apps-Net-gaim.desktop
``` 
As you can see, the Debian menu entry has a hideous filename, but the contents are very simple & straightforward.

```

[Desktop Entry]
Type=Application
Encoding=UTF-8
Name=Gaim
GenericName=
Comment=Multi-protocol Instant Messaging Client
Icon=/usr/share/pixmaps/gaim-menu.xpm
Exec=/usr/bin/gaim
Terminal=false
Categories=X-Debian-Apps-Net

``` 
**4.** Now, let's install the game Circus Linux. This will provide us with an opportunity to create a menu entry for the Ubuntu menu.

To install Circus Linux open a terminal & do:
```
sudo apt-get install circuslinux
``` Verify that it installed correctly by going to Applications->Debian->Games->Arcade->Circus Linux. Also note that it does not appear in Applications->Games.

**5.** Open gedit (without sudo) from the Applications->Accessories menu or do:
```
gedit
``` and browse to: /var/lib/menu-xdg/applications/menu-xdg. In this folder you'll see the .desktop files, but they will show with whatever name is in the "NAME=Application Name Here" section of the file, not the actual filename. 

[Here]("http://img85.imageshack.us/my.php?image=debmenuentriesoi1.png") is a screenshot of what you will see in both of the folders with the .desktop files.
[[IMG]http://img85.imageshack.us/img85/2056/debmenuentriesoi1.th.png[/IMG]]("http://img85.imageshack.us/my.php?image=debmenuentriesoi1.png")

This is not very intuitive at first, but when you create & then save a new menu entry file, you must name it like: app-name.desktop even though that isn't the name you'll see if you open the parent directory (/usr/share/applications) after creating the entry.

[Here]("http://img213.imageshack.us/my.php?image=savedialogincorrectxm1.png") is a screenshot of the gedit save dialog as it comes up. You MUST change the filename here or the entry will not appear in the Applications menu.
[[IMG]http://img213.imageshack.us/img213/8532/savedialogincorrectxm1.th.png[/IMG]]("http://img213.imageshack.us/my.php?image=savedialogincorrectxm1.png")

[Here]("http://img95.imageshack.us/my.php?image=savedialogcorrectxf1.png") is a screenshot of the gedit save dialog as it should look after you change the filename appropriately. 
[[IMG]http://img95.imageshack.us/img95/1263/savedialogcorrectxf1.th.png[/IMG]]("http://img95.imageshack.us/my.php?image=savedialogcorrectxf1.png")

If you forget to name the file appropriately such as: (app-name.desktop or application.desktop), it won't appear in Ubuntu's Applications menu. Dashes & underscores are ok but NO spaces in the filename.

**6.** The Debian menu entry for Circus Linux is an example of a menu entry with just the minimal information. To look at it, do:
```
gedit /var/lib/menu-xdg/applications/menu-xdg/X-Debian-Games-Arcade-circus_linux.desktop
``` 
It's contents look like this: 
```

[Desktop Entry]
Type=Application
Encoding=UTF-8
Name=Circus Linux
GenericName=
Comment=Circus Linux!
Icon=/usr/share/pixmaps/circuslinux-icon.xpm
Exec=/usr/games/circuslinux --fullscreen
Terminal=false
Categories=X-Debian-Games-Arcade

``` 
**7.** We can simply create a new file called circuslinux.desktop in /usr/share/applications: ```
sudo gedit /usr/share/applications/circuslinux.desktop
``` and then copy & paste the contents of the above file into the empty file we just created. 

**8.** Then we have to alter the Categories line to match the Ubuntu Applications menu. To find out what should go there, we look at an existing Ubuntu Applications menu entry from the category we want our new entry to go in. A good choice would be Same GNOME. To see the contents of this file do: ```
gedit /usr/share/applications/same-gnome.desktop
``` and scroll down until you see the Categories line. You can just copy the Categories line and paste it onto the end of your new circuslinux.desktop file and delete the old Categories line. It should now look like this: ```
[Desktop Entry]
Type=Application
Encoding=UTF-8
Name=Circus Linux
GenericName=
Comment=Circus Linux!
Icon=/usr/share/pixmaps/circuslinux-icon.xpm
Exec=/usr/games/circuslinux --fullscreen
Terminal=false
Categories=GNOME;GTK;Game;LogicGame;

```[/COLOR][/SIZE][LEFT][SIZE=2][COLOR=#000000] **9.** Save the file and then you should have a Circus Linux entry complete with icon in Applications->Games.[/COLOR][/SIZE]




 [SIZE=2][COLOR=#000000] **[SIZE=4]C.[/SIZE] If you have a menu entry that just doesn't have an icon:**[/COLOR][/SIZE]
[/LEFT]
            [SIZE=2][COLOR=#000000] This segment is from my [post]("http://www.ubuntuforums.org/showpost.php?p=1307649&postcount=4") in [this]("http://www.ubuntuforums.org/showthread.php?p=1308818#post1308818") thread.

1. Open Application->Accesories->Alacarte Menu Editor
2. Click on the category you want the icons in. 
3. File->New Entry
4. Fill in the lines appropriately.

Example:

Name: Rosegarden
Comment: Whatever-you-want-here
Command: rosegarden
Icon: Location-of-icon-file-here

Hint: look in /usr/share/pixmaps, /usr/share/icons & /usr/bin/name-of-app for the icon that goes with the app in question.

If you don't find it there, you can google for a suitable icon image. 

For example:
To find an icon for Rosegarden:
1. Go to [google images]("http://www.google.com/imghp?hl=en&tab=wi&q="), enter "rose" or whatever you need. Then choose the image that best suits your needs. I would use the blue rose image [here]("http://shop.butterflywisper.com/glycerin_soap_mrose1.shtml") because it has a simple, clear picture with a solid white background. Note that personal, non-commercial use of images grabbed off the net is probably OK, but distribution of these images could be a violation of copyright law. You're on your own with this.

2. I would then right click on the image and select "Save Image As..." then I'd clean up the filename from "rose_blueLt1_small.jpg" to something simpler like "rose.jpg" and save to the Desktop. 

3. Next, I open the image in GIMP. 

4. Once in GIMP, I click Image->Scale Image then I enter 64 in the dimension (Width or Height) that is the largest and hit enter. This should automatically scale the smaller dimension to the new size which is proportionally smaller than the new size of the larger dimension. Then click "Scale". 

5. Next click File->Save as... click "Select File Type (By Extension)" and choose "X PixMap image" from the list and click save, then close GIMP.

6. Open a terminal Applications->Accesories->Terminal and enter:
```
sudo cp ~/Desktop/rose.xpm /usr/share/pixmaps
``` 
7.Then open up Alacarte Menu Editor again, and select the category on the left you put Rosegarden into, then double click the rosegarden entry on the right when the list appears.

8. Click the Icon box and when the dialog box opens, be sure you're in /usr/share/pixmaps, if not, browse there with the Browse button on the top right. once in /usr/share/pixmaps Click on the rose.png icon, then click "OK", the icon should now be visible on the rosegarden entry. Click close on the rosegarden entry.

9. You should now see the icon with the rosegarden entry in Alacarte. Then click close on Alacarte. Check your menu, if you see the entry, but no icon, then do the following in Terminal:
```
killall gnome-panel
``` to refresh the menu.

[B][SIZE=3]

[/SIZE][/B][/COLOR][/SIZE][SIZE=4]**D.**[/SIZE] [SIZE=2][COLOR=#000000]**If you have an application which has an icon in the Ubuntu Applications menu, but only opens from the command line: **


1. Open up Alacarte and verify that the menu entry has the appropriate command to run the application. Verify by opening a Terminal and entering the command listed.


2. Try setting the program to “Run in Terminal”. Some apps need to be opened this way. You can do this by going to Applications->Accesories->Alacarte, select any Category on the left and double-click any entry on the right. In the config dialog that appears, the checkbox just to the right of the icon is what we're after here. You can also do this by entering: ```
sudo gedit /usr/share/applications/name-of-app.desktop
``` in the terminal, and changing the line ```
Terminal=false
``` to ```
Terminal=true
``` or vice-versa. This is from my [post]("http://www.ubuntuforums.org/showpost.php?p=1307061&postcount=2") in this [thread]("http://www.ubuntuforums.org/showpost.php?p=1307061").


3. Verify that the binary has the proper permissions. This was suggested by **ardchoille** [here]("http://www.ubuntuforums.org/showpost.php?p=1307061&postcount=3"). The full thread can be found [here]("http://www.ubuntuforums.org/showpost.php?p=1307061").

[COLOR=Black]
For even more menu customization, use the link below to see **kassetra's** guide, which works hand-in-hand with this guide.
[/COLOR][/COLOR][[COLOR=Black]**HOWTO: Create & populate Sub-Menus in the Applications Menu**[/COLOR]]("http://www.ubuntuforums.org/showthread.php?t=36479")[/SIZE][SIZE=2][COLOR=#000000][COLOR=Black]

Sorry for the extra-long post.

Feedback, suggestions and constructive comments are welcome. As usual, this is probably a work in progress.[/COLOR]  

This is my first HOWTO, so go easy on me.

Greenstar[/COLOR][/SIZE]

---

### Post by andrewski on 2006-09-09
> **greenstar said:**
> [SIZE=2][COLOR=#000000]**[SIZE=4]C.[/SIZE] If you have a menu entry that just doesn't have an icon:**[/COLOR][/SIZE]
          [SIZE=2][COLOR=#000000] This segment is from my [post]("http://www.ubuntuforums.org/showpost.php?p=1307649&postcount=4") in [this]("http://www.ubuntuforums.org/showthread.php?p=1308818#post1308818") thread.

1. Open Application->Accesories->Alacarte Menu Editor
2. Click on the category you want the icons in. 
3. File->New Entry
4. Fill in the lines appropriately.

etc...[/COLOR][/SIZE]

[SIZE=2] ...and then file a bug on Launchpad for the appropriate package. :cool:[/SIZE]

---

### Post by DC@DR on 2006-09-09
Thanks for the well-structured HOWTO, greenstar :)

---

### Post by Dinerty on 2006-09-14
What a brilliant guide, came in handy when my annoying aMSN icon would not delete from menu.

God I love having a terminal for jobs like this

---

### Post by FyreBrand on 2006-09-15
Thank you greenstar.  The guide is great.  I was having a horrible time using the graphical ala carte menu editor.  I had menu entries I didn't want that wouldn't go away and other entries that wouldn't show up no matter what I did.  Thanks for showing me the easy way to edit these.  Great for a first HowTo as well.

---

### Post by BadDolphin on 2006-09-16
I did the "sudo apt-get install menu" with no errors.

However, when I try to look at this file, it doesn't exist, and won't allow me to create it:

gedit /var/lib/menu-xdg/applications/menu-xdg/X-Debian-Apps-Net-gaim.desktop

This just opens an empty file with no contents.  I've tried pasting in what it says the contents SHOULD be, but when I try to save and exit in gedit I get "Unexpected error: File not found"

When I try the same using vi, I get 
"/var/lib/menu-xdg/applications/menu-xdg/X-Debian-Apps-Net-gaim.desktop" E212: Can't open file for writing
Hit ENTER or type command to continue

I've spent hours fighting just to be able to run stuff I've installed but cannot find.  Any tips would be appreciated.

---

### Post by ryu kun on 2006-09-16
> **BadDolphin said:**
> I did the "sudo apt-get install menu" with no errors.

However, when I try to look at this file, it doesn't exist, and won't allow me to create it:

gedit /var/lib/menu-xdg/applications/menu-xdg/X-Debian-Apps-Net-gaim.desktop

This just opens an empty file with no contents.  I've tried pasting in what it says the contents SHOULD be, but when I try to save and exit in gedit I get "Unexpected error: File not found"

When I try the same using vi, I get 
"/var/lib/menu-xdg/applications/menu-xdg/X-Debian-Apps-Net-gaim.desktop" E212: Can't open file for writing
Hit ENTER or type command to continue

I've spent hours fighting just to be able to run stuff I've installed but cannot find.  Any tips would be appreciated.


Please run this code:

```
sudo apt-get update
sudo apt-get install menu menu-xdg
update-menus
```

---

### Post by greenstar on 2006-09-16
Thanks for the feedback, everyone. I'm glad this HowTo has been helpful.  Also, I've incorporated ryu kun's suggestions into the guide regarding installation of the Debian menu. Thanks ryu kun, I credited your contribution in the edit note.

Greenstar

---

### Post by sailor.nir on 2007-07-03
I have the same problem as BadDolphin above. I've installed menu and menu-xdg, and ran update-menus. The verbose option says it found 140 entries, but /var/lib/menu-xdg still doesn't exist.
I run Feisty, BTW.
Any suggestions?

Thanx, GreenStar, for a great HOWTO. I just wish I can get it to work...

---

### Post by greenstar on 2007-07-04
> **sailor.nir said:**
> I have the same problem as BadDolphin above. I've installed menu and menu-xdg, and ran update-menus. The verbose option says it found 140 entries, but /var/lib/menu-xdg still doesn't exist.
I run Feisty, BTW.
Any suggestions?

Thanx, GreenStar, for a great HOWTO. I just wish I can get it to work...

1) Places->Search for Files...

2) In the Search for Files... dialog: 
 a)Name contains: gaim
b)Look in folder: Click the list arrows on the right, select / or filesystem, if neither are present, choose other, then click the paper with pencil in top left of Browse dialog and enter / in the address box that opens and click open. 

3) Click find in Search for Files...

4) The result should show you the files you need to make a menu entry work properly or build a new one from scratch. Example: gaim.desktop, gaim.png, gaim.svg, etc.

5) I have no idea where your menu-xdg is located. Search for it as described above, it works great for me. Matter of fact, the search tool helped me figure out much of the information in the how-to. My search for menu-xdg gave no results on a fresh edgy install, but I've installed almost nothing yet.

6) Beyond this I don't know.

Greenstar

---

### Post by sailor.nir on 2007-07-05
OK, I did a search, and found menu-xdg right where it was supposed to be, in /var/lib/...
Could it be that I needed to restart the system before I saw the directory? Or that it took a long time to process and hadn't yet finished for a while after I ran update-menu? Hmmm...
In any case, it's there now. Thanx again Greenstar!

---

### Post by weishigoname on 2010-05-11
nice ,looking for HOWTO

---

### Post by akash.mahakode@gmail.com on 2010-08-04
Hi,

I have created a file for eclipse viz. eclipse.desktop. Whenever I restart the machine or log out. Icon and entry from Applications menu disappears.
To bring it back I need to manually run following command-
#desktop-file-install /usr/share/applications/eclipse.desktop

Now, I am able to see eclipse in menu. 

But I need to run this manually each time whenever I login.


-akash

---

