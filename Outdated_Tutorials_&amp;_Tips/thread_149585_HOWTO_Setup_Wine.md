---
title: "HOWTO Setup Wine"
date: 2006-03-24
forum: Outdated Tutorials &amp; Tips
---

### Post by gazj on 2006-03-24
*** UPDATE 19-07-2006 (UK DATE SYSTEM :) ) This howto was originally written for breezy badger, I can now confirm it also works on dapper drake

*** UPDATE 15-12-2008 Updated for Intrepid Ibex, and fixed dead winetools link (thanks to Murdoc_of_puts post 485)

After a lot of searching here there and every where I finally know how to get wine working on my machine anyway, every time without fail, and as there is a lack of how to's on wine, I thought i would give the Ubuntu community something back. This is my first how to, so don't be to harsh if it dosen't work for you.

First we get the wine0.95.deb from winehq [http://kent.dl.sourceforge.net/sourceforge/wine/wine_0.9.5-winehq-1_i386.deb]("http://kent.dl.sourceforge.net/sourceforge/wine/wine_0.9.5-winehq-1_i386.deb")

or if you want to open a terminal (alt+F2 then type gnome-terminal then enter) to download it use this command

```
 wget http://kent.dl.sourceforge.net/sourceforge/wine/wine_0.9.5-winehq-1_i386.deb
```

In case your wondering why we are not downloading the latest version of wine its because internet explorer install breaks on newer versions and you will probably need internet explorer to get other programs working, but we will update wine after, so don't worry

Right so we got our Wine .deb so lets unpackage it in our terminal dont forget to change directory to where you downloaded wine (if you used the above command you should already be there)

```
sudo dpkg -i wine*.deb
```

ok, so we no have wine, but how do i use it, set up a C:/ D:/ etc i hear you cry, let alone install anything, well here come the great little app called winetools ;)

I have now learned that winetools has at least one dependancy, pointed out by replies on this forum, here is the command for installing it (added 1st April 06, after 12 not a april fool btw)

```
sudo apt-get install libgtk1.2
```

wine tools can be downloaded here []("http://www.sfr-fresh.com/linux/misc/winetools-0.9jo-III.tar.gz")

or if your still with me in the good old terminal you can use this command

```
wget http://www.sfr-fresh.com/linux/misc/winetools-0.9jo-III.tar.gz
```

ok, so we got this great tool no we need to unpack it

```
tar -xf winetools*
```

and install it

```
cd winetools*
sudo ./install
```

Done :) so lets start this wonderfull tool with this

```
wt
```

you will get loads of messages popup about not being configured etc, just keep clicking ok oh and that you should also own a copy of windows to use some of these tools. Yeah Yeah on with the plot.

You should finally get to a menu

So first we go for base setup, then create a fake windows drive
Next winetools will find your cdrom for you so it can set it up for wine
Followed by a username and organization, I Just leave theese as is
After a few fake windows restarts later we are told fake drive completed. Yippee

We are back to the base setup menu, now select DCOM98 and then go down the list installing all the programs on the list, obvioulsy only do internet explorer in your language, the reason we have left the Arial font out is because the  link to this is dead, but we will sort this later. Just click next and ok on everything, im sure you know how window installers work.

Ok so we have finished the first list, hit the main menu button to get us back to the start.

next click install windows system software then click ok

again install everything thats in the list from top to bottom in your own language, and install visual basic 5 & 6

ok, so now we gotta sort out theese fonts as the links that winetools uses to retrieve them is dead, so click main menu followed by exit to leave winetools

now then back to our friend the terminal
ok so first we need to make and move to the directory where winetools would have downloaded the fonts

```
mkdir ~/winetools/fonts
cd ~/winetools/fonts
```

you might get an error saying the file exsits, if you do don't worry just continue

Next we download the fonts from a link that is still around at the time of writing this, you might want to copy and paste this one into your terminal

```
wget http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe && wget http://kent.dl.sourceforge.net/sourceforge/corefonts/arial32.exe && wget http://kent.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe &&  wget http://kent.dl.sourceforge.net/sourceforge/corefonts/comic32.exe &&  wget http://kent.dl.sourceforge.net/sourceforge/corefonts/courie32.exe &&  wget http://kent.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe &&  wget http://kent.dl.sourceforge.net/sourceforge/corefonts/impact32.exe &&  wget http://kent.dl.sourceforge.net/sourceforge/corefonts/times32.exe &&  wget http://kent.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe &&  wget http://kent.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe &&  wget http://kent.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe
```

Ok, so we now have the fonts downloaded, next back to winetools to install them ;)

```
wt
```

Select base setup again then install true type font arial

Next main menu then select Install Microsoft true type corefonts, yet again go all the way down the list until you have installed all the fonts.

done that, so main menu and exit winetools ;)

Ok so we should now have a working wine, with internet explorer installed and windows media player 6 ;) hopefully :s

we should be able to start Internet Explorer with the following

```
 wine "/home/USERNAME/.wine/c/Program Files/Internet Explorer/IEXPLORE.EXE"
```

Dont forget to change USERNAME to your own username

With any luck your using internet explorer now :)

although we dont want to have to write this in everytime we want to start internet explorer, so right click the desktop and create a launcher and paste the previous code in there for a desktop shortcut, or make a menu shortcut which ever you prefer.

Here is the code for Outlook and Windows Media Player

```
wine "/home/USERNAME/.wine/c/Program Files/Outlook Express/msimn.exe"
```

and

```
 wine "/home/USERNAME/.wine/c/Program Files/Windows Media Player/mplayer2.exe"
```

and really thats about it, you can also navigate using your file browser and double click .exe files and wine will launch them, like installers for programs and so on, then its just a case of finding the .exe that starts the program and making your custom launcher for it,  your wine c: should always be found in /home/USERNAME/.wine/c. As long as know a bit about the windows file layout you should have no problem in finding them, always remember when creating your launchers that linux is case sensitive, so dont forget the caps.

Two last things to do

Firstly updating wine 0.95 to the latest version, remember we had to use 0.95 because internet explorer will not install on newer versions, although this maybe fixed now. There is no need to panic though, we just add a wine repository to our sources.list like this.

```
sudo gedit /etc/apt/sources.list
```

then add this line to the bottom of the file

[http://www.openoffice.de/wt/winetools-0.9jo-III.tar.gz](http://www.openoffice.de/wt/winetools-0.9jo-III.tar.gz)

then save your sources.list and run the following in terminal to update your wine installation

```
sudo apt-get update
sudo apt-get upgrade
```

This should update wine to the latest version released by wineHQ, and will always be updated with the rest of your updates when a new version is released, Good hey

The second thing to do is to tell you about the winecfg command

```
winecfg
```

This little panel allows you to change the default wine settings, like which windows version to try to act as, and what builtin and native dll's to use, I would suggest leaving the global settings to windows98 as this seems to work best, but you can change the windows version for individual .exe's if a program only works on a certain version of windows, if a program dosen't quite work right this is the place to go, although the full usage of winecfg is a bit beyond the scope of this howto, you should get familiar with it quite soon

If you have problems with a certain program i find it always pays to just put in a google search "program name winehq" and you will usually find the program in the winehq database and find out what success people have had at getting the program to work and what they did to achieve it, very helpfull

One last point, if you use any programs that reside in the windows system tray then the system tray icons do not show up, a workaround is to open up a kde application that uses a tray icon and then the windows tray icons will appear, i.e i have amarok start when gnome starts, kalarm is a good one to use if you dont use amarok, even after you quit your kde program the windows icons will remain.  I believe this shouldn't be a problem for KDE users.

Anyway hope this was some help to a least one person out there, and I will probably add a MSN Messenger HOWTO this as soon as i get the time, let me know how you get on, In the meantime happy wineing :)

---

### Post by mark_g on 2006-03-26
Thanks for the HOWTO.

You made one small typo by the way by forgetting the first / in
wine "home/USERNAME/.wine/c/Program Files/Internet Explorer/IEXPLORE.EXE" , but I suppose most people will spot that. Great howto anyway.

---

### Post by oddman on 2006-03-26
First, thanks for putting this up.  I was having a ton of trouble finding help on getting IE to work in Wine and on getting Winetools in Ubuntu. (I'm so much of a noob that the winetools page was confusing.  Do rpm's work in a Debian distribution?)  This howto was exactly what I needed.

Second, I have Wine 0.9.10 installed and everything turned out well after following your guide.  IE is up and running just fine. (Well, I had trouble with the ad page for Salon, but I think that is a flash-in-IE-in-Wine problem not a problem of the Wine version by itself.)

---

### Post by cbudden on 2006-03-26
I already have wine installed, aswell as a few programs.  Am I able to install wine tools without messing up my current wine installation?

---

### Post by gazj on 2006-03-27
> mark_g  	Thanks for the HOWTO.

You made one small typo by the way by forgetting the first / in
wine "home/USERNAME/.wine/c/Program Files/Internet Explorer/IEXPLORE.EXE" , but I suppose most people will spot that. Great howto anyway.

Thanks for pointing that out, is now fixed :)

---

### Post by gazj on 2006-03-27
> cbudden  	I already have wine installed, aswell as a few programs. Am I able to install wine tools without messing up my current wine installation?
13 Hours Ago 11:58 PM

There is an option in wine tools, instead of creating wine base installation, you cant point an exsisting wine installation to it, everything should be ok, but theres never 100% gaurantee, its probably best to start fresh, if your programs you already have won't take too much installing back on, its your choice ;)

---

### Post by gazj on 2006-03-27
[QUOTE=oddman]First, thanks for putting this up.  I was having a ton of trouble finding help on getting IE to work in Wine and on getting Winetools in Ubuntu. (I'm so much of a noob that the winetools page was confusing.  Do rpm's work in a Debian distribution?)  This howto was exactly what I needed.

Second, I have Wine 0.9.10 installed and everything turned out well after following your guide.  IE is up and running just fine. (Well, I had trouble with the ad page for Salon, but I think that is a flash-in-IE-in-Wine problem not a problem of the Wine version by itself.)[/QUOTE]

You can use .rpm in ubuntu although original .deb is better

You can use a command prompt called alien to do the converstion

```
alien exampleprog.rpm
```

to get alien

```
sudo apt-get install alien
```

i havent tried the .rpm of winetools, let me know how you get on

---

### Post by Harold P on 2006-03-27
Umm, the .deb is a little outdated, I suggest you make a new one with the version 9.10 (the current version).

---

### Post by gazj on 2006-03-27
[QUOTE=Harold P]Umm, the .deb is a little outdated, I suggest you make a new one with the version 9.10 (the current version).[/QUOTE]

The reason the old .deb is used, is because internet explorer setup within winetools fails on any newer version, the how to later updates to the latest version from apt-get, this was the case with versions 9.6-9.9, however this may not be an issue with 9.10 as i have not tried it on this version.

Thanks for pointing that out though

---

### Post by reet on 2006-03-27
Hi,
Thanks for the HOWTO, works quite well, and I should report that I've had no problem running IEXPLORE.EXE with Wine 0.9.10. The only problem I am having is that I want to install some software that requires the "Windows Installer 2.0", which I have retrieved from [here]("http://www.microsoft.com/downloads/details.aspx?FamilyID=cebbacd8-c094-4255-b702-de3bb768148f&DisplayLang=en"). The problem is that I can't install the Windows Installer, it just exits with the following errors:
```
fixme:msiexec:main /regserver not implemented yet, ignoring
fixme:msiexec:main /unregserver not implemented yet, ignoring
```

---

### Post by gazj on 2006-03-27
Im not to sure about the windows installer problem, although winetools does say when you install the new windows installer, some older programs may no longer install, the iexplore.exe does work on all versions of wine, its the ie6 setup program that dosen't work on 9.6-9.9

---

### Post by FredSambo on 2006-03-27
excellent how-to.  everything is working beautifully, thanks!

---

### Post by Rizado on 2006-03-27
[QUOTE=FredSambo]excellent how-to.  everything is working beautifully, thanks![/QUOTE]The easiest way to install ie6 is to use [ie4linux.](http://www.tatanka.com.br/ies4linux/)
It's a script that downloads everything that's needed and installs into .ie4linux (by default) instead of .wine
Nothing is done in .wine at all so it can be ran without fear of breaking every other installed app and you'll have a clean .wine for other things.

---

### Post by gazj on 2006-03-27
[QUOTE=Rizado]The easiest way to install ie6 is to use [ie4linux.](http://www.tatanka.com.br/ies4linux/)
It's a script that downloads everything that's needed and installs into .ie4linux (by default) instead of .wine
Nothing is done in .wine at all so it can be ran without fear of breaking every other installed app and you'll have a clean .wine for other things.[/QUOTE]

I agree i use ies4linux aswell, but i like internet explorer 6 in my wine installation aswell, as many programs, rely on aspects of internet explorer to work, my girlfriend for one cannot manage without msn messenger, (gaims fine for me) msn messenger needs ie6 to work, thats why its handy to have it in wine too :)

good point well made if all you want is internet explorer though :)

---

### Post by reet on 2006-03-27
Hi,
I have fixed my problem with installing the "Windows Installer 2.0" by installing ActiveX control. I now have the problem that the program has installed a new version of ComCtl32.dll (5.80.2614.3600) but it is still detected as 5.80.0.0 by the program so it won't start. I guess some programs just won't work :(

---

### Post by gazj on 2006-03-28
[QUOTE=reet]Hi,
I have fixed my problem with installing the "Windows Installer 2.0" by installing ActiveX control. I now have the problem that the program has installed a new version of ComCtl32.dll (5.80.2614.3600) but it is still detected as 5.80.0.0 by the program so it won't start. I guess some programs just won't work :([/QUOTE]

There are a lot of programs that don't work, wine is far from 100%, the best thing you can do, is look up your program on the winehq website, and see if anyone else has had success.

---

### Post by halitech on 2006-03-29
I thank you for this, I couldn't figure out all the commands either and this has helped alot.

edit: I'm going to try and get this working on a machine with no net connection, is there someway of getting the fonts and the windows components other then through the net?

---

### Post by gazj on 2006-03-29
[QUOTE=halitech]I thank you for this, I couldn't figure out all the commands either and this has helped alot.

edit: I'm going to try and get this working on a machine with no net connection, is there someway of getting the fonts and the windows components other then through the net?[/QUOTE]

i think you could, if you have setup wine on a machine that is online, then find the winetools folder that was created in your home directory and burn this to a cd, then take the cd to your offline machine, and paste the winetools folder into the home directory, winetools should not need to download the files like it usually does. although i haven't tried this and can say it will work for certain, you can give it a try.  Let me know how it goes

---

### Post by halitech on 2006-03-29
ok, I'll give this a try and hopefully it will work. Will let you know.

---

### Post by mscman on 2006-03-29
What a great HOWTO!!! Thanks a lot for all the help, as I'm probably not the only one who has tried (and failed...) numerous times to install and use wine.  THANKS!!!\\:D/

---

### Post by micrologix on 2006-03-30
Thanks heaps for the How To, as a new user it was very helpful. One thing though, can you please tell me how to get the dialog box back up for installing fonts and applications etc, the one where you keep referencing to go back to the Main Menu, thanks.

---

### Post by gazj on 2006-03-30
[QUOTE=micrologix]Thanks heaps for the How To, as a new user it was very helpful. One thing though, can you please tell me how to get the dialog box back up for installing fonts and applications etc, the one where you keep referencing to go back to the Main Menu, thanks.[/QUOTE]

open up a terminal (press alt+f2 then type gnome-terminal followed by enter) then use the following code

```
wt
```

I will also add this to the original howto, to make things more clear, thanks

---

### Post by halitech on 2006-03-30
okay, we have partial success as it gave me all the files for the fonts and other programs but no IE. Tried to download from M$ and install using winefile but it fails for some reason. May not have all the files needed so will try to get them again. (does 30 meg sound right for an IE download for 98 and XP?)

---

### Post by frup on 2006-03-30
thanks alot :D worked great... note: i had to get libgtk 1.2 (i think thats was what it was called, 2.0 was already installed though :S)

---

### Post by master5o1 on 2006-03-31
This was reallllly helpful...thanks!

---

### Post by Terracotta on 2006-03-31
Hye, I was wondering, how can you update if you have a 64bit system installed, and would like to use a 32bit wine (no chroot). Is installing the new package after having the old one installed a solution?

---

### Post by WoodyMahan on 2006-03-31
Nice How To:

However, when I try to run wt I get this reply to my command:
woody@ubuntu:~/winetools/fonts$ wt
detecting Wine version... done.
Drive C: is /home/woody/.wine/drive_c
Wine 0.9.5
wine is executed as wine
Parameters are --noexit
Browser is /usr/bin/firefox.
WINEVER is "0.9.5".
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
Calls to wine are executed as  "wine".
Config is /home/woody/.wine/winetools.log.
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory


Anybody seen this before?

---

### Post by localzuk on 2006-03-31
> wine "/home/USERNAME/.wine/c/Program Files/Internet Explorer/IEXPLORE.EXE"

Instead of having to type that, you could use

```
wine "c:\program files\internet explorer\iexplore.exe"
```

Also, I would recommend using wine 0.9.10 (I don't know about the newly released 0.9.11 - haven't tried it yet) as it has much better support for far more apps than earlier versions. (It supports install of IE6 once the other basic tasks in wt are complete).

---

### Post by FredSambo on 2006-03-31
[QUOTE=WoodyMahan]Nice How To:

However, when I try to run wt I get this reply to my command:
woody@ubuntu:~/winetools/fonts$ wt
detecting Wine version... done.
Drive C: is /home/woody/.wine/drive_c
Wine 0.9.5
wine is executed as wine
Parameters are --noexit
Browser is /usr/bin/firefox.
WINEVER is "0.9.5".
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
Calls to wine are executed as  "wine".
Config is /home/woody/.wine/winetools.log.
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory


Anybody seen this before?[/QUOTE]

yeah, funny i followed these instructions at home and it worked fine, then i followed the same directions and get the same error as above.

---

### Post by FredSambo on 2006-03-31
[QUOTE=frup]thanks alot :D worked great... note: i had to get libgtk 1.2 (i think thats was what it was called, 2.0 was already installed though :S)[/QUOTE]

please explain how to get libtk 1.2

i think it may have something to do with our error.

---

### Post by gazj on 2006-04-01
[QUOTE=FredSambo]please explain how to get libtk 1.2

i think it may have something to do with our error.[/QUOTE]

```
sudo apt-get install libgtk1.2
```

I will also add this to the guide, must have already had this on my system, Thanks

---

### Post by gazj on 2006-04-01
[QUOTE=Terracotta]Hye, I was wondering, how can you update if you have a 64bit system installed, and would like to use a 32bit wine (no chroot). Is installing the new package after having the old one installed a solution?[/QUOTE]

Im really sorry to say, I have no expirience at all with 64bit systems at this time, anyone know how to help Terracotta out?

---

### Post by FredSambo on 2006-04-01
[QUOTE=gazj]```
sudo apt-get install libgtk1.2
```

I will also add this to the guide, must have already had this on my system, Thanks[/QUOTE]

w00t!  thanks a bunch!

:mrgreen:

---

### Post by joshbrown40 on 2006-04-02
I just had a successful install using wine 0.9.10 (wine_0.9.10-winehq1-2_i386.deb) that I got from the wineHQ site, without starting from 0.9.5 and upgrading.

---

### Post by Olli on 2006-04-03
Thanks for a well detailed recipe. I too could complete my wine installation (wine_0.9.10-winehq1-2_i386.deb) without any other problems but the link to the corefonts site (wget [http://kent.dl.sourceforge.net/sourceforge/corefonts/](http://kent.dl.sourceforge.net/sourceforge/corefonts/)) is dead. I downloaded the font files from [http://prdownloads.sourceforge.net/c/co/corefonts](http://prdownloads.sourceforge.net/c/co/corefonts) to ¨/winetools/fonts,
but the installation script insisted to download the files from a site [http://puzzle](http://puzzle) etc. I could not find where to change the URL in the installation script, nor did not know, how to get the downloaded <font>.exe files installed but to copy them to c:/windows/fonts directory. Is this right?

---

### Post by gold4tune on 2006-04-04
Hi everybody... It's the first time that wine work... Thx a lot for taht
But, did i have to install directx to make game work... I'm trying Worms world party and Worms armageddon and nothing work. It install... But it wont play after that.

thx

---

### Post by That Other Guy on 2006-04-04
Strike my erroneous comments on not finding the fonts - it's all in the HOWTO - just gotta read it ;-)

Just completed the basic installation, and it works well (keeping my fingers crossed, as apt-get is upgrading now).  Now on to install Office (if only OO would make better charts...).

---

### Post by Nordoelum on 2006-04-04
I get this error:
```
nordoelum@nordoelum:~/Desktop/banshee-0.10.9$ winecfg
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/nordoelum/Desktop/banshee-0.10.9', starting in the Windows directory.
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/', starting in the Windows directory.
```

What do I need do to fix this?

---

### Post by manutd on 2006-04-04
I have a newbie question for you... 
I'm following this HOWTO process and I have only gotten to the second step so far! ](*,) 

I can download Wine perfectly but when I put the second command in, which is:

sudo dpkg -i wine*.deb 

it gives me this error message.... :???: 

Selecting previously deselected package wine.
(Reading database ... 58010 files and directories currently installed.)
Unpacking wine (from wine_0.9.5-winehq-1_i386.deb) ...
dpkg: dependency problems prevent configuration of wine:
 wine depends on libstdc++6; however:
  Package libstdc++6 is not installed.
dpkg: error processing wine (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 wine

Does anyone have any suggestions for me! :-k 
and maybe a step by step process on how to fix this part of the installation! 

Its my first time ever installing anything off the net through Ubuntu! 
I just got connected to the net today after at least 1 week of learning how to connect! and my email works... I just want to get Wine up and running so I can play some Poker Stars! lol :-D 

anyway suggestions would be greatly appreciated!!!!!!!!!!!!!:)

---

### Post by That Other Guy on 2006-04-04
Nordoelum: First off, I'm new at Wine, too, so my comments are to be taken for what they're worth.

Did you use Wine Tools as specified on the first page of this thread?  If so, it should have created all the folders that winecfg can't find.  If you did use it and it failed, or you can't use it for whatever reason, you may want to check out the groups at [http://www.frankscorner.org/index.php?p=support]("http://www.frankscorner.org/index.php?p=support") or [http://www.wine-wiki.org/]("http://www.wine-wiki.org/").

---

### Post by That Other Guy on 2006-04-04
> **manutd]
dpkg: dependency problems prevent configuration of wine:
 wine depends on libstdc++6 said:**
> 

Try this:
[QUOTE]$ sudo apt-get update
$ sudo apt-get install libstdc++6

You'll have to enter your password for each command, but it should install the missing library automatically otherwise.  If it has dependencies itself, those should also show up for automatic installation.

Then re-run the wine installation instructions.

Hope this helps.

---

### Post by Princey on 2006-04-05
Thanks for the how to. Wine installed fine but when I run the base install, here's what I get: > Choice is Create a Fake Windows drive with checked=F
waiting for wineservers to exit...
all wineservers endet after 0 seconds...
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:process_attach Could not create default context.
Xlib:  extension "GLX" missing on display ":0.0".
wine: Unhandled page fault on read access to 0x00000000 at address 0x7ec1e13f (thread 0009), starting debugger then the debugger runs for a while and spits out more messages that makes absolutely no sense to me. Thing is if I close the terminal (debugger runs for 5mins plus then exits leaving a hanging terminal) and type in winecfg, the fake drive is there along with some other settings. Should I just ignore or do I have to get that error message sorted? I searched the threads but couldn't come up with that error message.

---

### Post by manutd on 2006-04-05
[QUOTE=That Other Guy]Try this:


You'll have to enter your password for each command, but it should install the missing library automatically otherwise.  If it has dependencies itself, those should also show up for automatic installation.

Then re-run the wine installation instructions.

Hope this helps.[/QUOTE]


Thanks a bunch...you have been great! 
I'll give it a try tonight! 
Man, this is the best place ever to get help! AWESOME! 

THANKS AGAIN! :D

---

### Post by newpants2003 on 2006-04-05
when install the ie(sp1) it tells me   mfc40.dell   not installed yet.  and i chose to keep going, then it tells me install fail. thats where the falls start.

and also my windows are in E:/ , but looks like the wt defaul to looking in C:/ , then tells me could not find the file it need, then falls. 

Wine is finalizing your software installation. This may take a few minutes,
though it never actually does.
err:exec:SHELL_ExecuteW cannot set directory L"c:\\windows\\system32\\shell32.dll"
err:exec:SHELL_ExecuteW cannot set directory L"c:\\windows\\system32\\shell32.dll"
err:exec:SHELL_ExecuteW cannot set directory L"c:\\windows\\system32\\shell32.dll"
err:exec:SHELL_ExecuteW cannot set directory L"c:\\windows\\system32\\shell32.dll"
err:exec:SHELL_ExecuteW cannot set directory L"c:\\windows\\system32\\shell32.dll"
err:exec:SHELL_ExecuteW cannot set directory L"c:\\windows\\system32\\shell32.dll"
err:module:import_dll Library MFC40.DLL (which is needed by L"C:\\Program Files\\Common Files\\Microsoft Shared\\MSInfo\\ieinfo5.ocx") not found
err:exec:SHELL_ExecuteW cannot set directory L"c:\\windows\\system32\\shell32.dll"
err:exec:SHELL_ExecuteW cannot set directory L"c:\\windows\\system32\\shell32.dll"
Registration of c:\windows\system32\StdOle2.Tlb successful.


how to solve the problem?

---

### Post by manutd on 2006-04-05
Ok, gang...


Selecting previously deselected package wine.
(Reading database ... 58010 files and directories currently installed.)
Unpacking wine (from wine_0.9.5-winehq-1_i386.deb) ...
dpkg: dependency problems prevent configuration of wine:
wine depends on libstdc++6; however:
Package libstdc++6 is not installed.
dpkg: error processing wine (--install):
dependency problems - leaving unconfigured
Errors were encountered while processing:
wine

This was my first error!
I was told to try this command to correct the error:

sudo apt-get update
sudo apt-get install libstdc++6

I tried this.. but I get a SECOND error ](*,) , which is:
  
Reading package lists... Done
Building dependency tree... Done
Package libstdc++6 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libstdc++6 has no installation candidate

To me this looks like I need to find the package "libstdc++6" :-? 

Does anyone know where or how I can get this package? :-k 
Does it come with my system or do I need to download it??? :-k 

anyway... info would be greatly appreciated!!! 
Thanks again for your help everyone!!!!

---

### Post by Nordoelum on 2006-04-05
```
$ sudo apt-get update
$ sudo apt-get install libstdc++6
```

---

### Post by That Other Guy on 2006-04-05
OK, this may be quickly getting over my head, but I don't know why your system can't find libstdc++6.  It's listed as part of the Base System, with a Priority of 'important.'  Looks to me like you NEED it if you hope to install many apps in the future.

I don't know if you said you're in KDE or Gnome, but try Adept (KDE, under System) or Synaptic (Gnome, possibly under Administration - I forget).  Fire one of those up and do a search for the file, after you've done a 'Fetch Updates' or 'Reload' to make sure you have all the lastest package listings.  It has to find it, since it's in the default repositories.  Choose to install it from there, along with any dependencies it may have for your system.

---

### Post by tr333 on 2006-04-05
```
$ sudo apt-get update
$ sudo apt-get install build-essential
```
that should install the missing c++ library.

---

### Post by manutd on 2006-04-06
GRREAT! 8) 
I'll give it a shot tonight and let you know how everything works out! 
Hopefully it goes well!  I do use Gnome by the way!! 

Thanks again!

---

### Post by manutd on 2006-04-06
oh boyz,
not looking good so far! :???: 

I've tried many different ways to find libstdc++6 and I dont think it is available on my system! 

When I go to Synaptic and search "libstdc" it finds only two apps.
1st is  - libstdc++5
2nd is - libstdc ++5-3.3.dev

I can't seem to find libstdc ++6 in order to correct my problem! 

Is there a way to correct this or am I going to have to get a new copy of Ubuntu. Maybe an updated version and install it again...
I'm currently running Ubuntu 5.04. Would this affect it???

anyway, help would be great when you get a sec.! 
I'm starting to get bored and annoyed working on this one app so far! :-k 
Its only the first one! 

anyway help would be great, and you guys have been great so far! 

THANKS AGAIN EH!

---

### Post by Mustard on 2006-04-06
[QUOTE=manutd]oh boyz,
not looking good so far! :???: 
<snip>
[/QUOTE]


I would suspect there is a problem with your sources.list, as everyone should be able to install this package with a correct sources.list.  I would try this.

1. Create a copy of your current sources.list on the desktop as a text file.

```
sudo cp /etc/apt/sources.list ~/Desktop/sources.list.txt
```

2. Attach that text file to your next post so that someone can look over it and work out whether you have a problem with your sources.list

---

### Post by tsharpe62 on 2006-04-07
I'm having a couple small problems so far:
At step - I have now learned that winetools has at least one dependancy, pointed out by replies on this forum, here is the command for installing it (added 1st April 06, after 12 not a april fool btw)

I enter "sudo apt-get install libgtk1.2" and get
I'm getting "Package libgtkl.2 is not available, but is referred to by another package. Theis may mean that the package is missing, has been obsoleted, or is only available from another source.
E: Package libgtkl.2 has no installation candidate"

---

### Post by FredSambo on 2006-04-07
[QUOTE=tsharpe62]I'm having a couple small problems so far:
At step - I have now learned that winetools has at least one dependancy, pointed out by replies on this forum, here is the command for installing it (added 1st April 06, after 12 not a april fool btw)

I enter "sudo apt-get install libgtk1.2" and get
I'm getting "Package libgtkl.2 is not available, but is referred to by another package. Theis may mean that the package is missing, has been obsoleted, or is only available from another source.
E: Package libgtkl.2 has no installation candidate"[/QUOTE]

nevermind, bad info.

---

### Post by FredSambo on 2006-04-07
try:

[http://packages.ubuntulinux.org/breezy/doc/libgtk1.2-doc](http://packages.ubuntulinux.org/breezy/doc/libgtk1.2-doc)

---

### Post by Fatstink on 2006-04-07
Does any body know how to fix this error??? I have installes both the libXxf86dga1 lib and the dev files.

Choice is DCOM98 with checked=F
dcom98.exe to check
software installation verified by /home/fatstink/.wine/winetools.log
1229056 bytes previously downloaded
WINEDEBUG="fixme-all" WINEDLLOVERRIDES="ole32=n" wine ./dcom98.exe
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXxf86dga.so.1: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXxf86dga.so.1: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXxf86dga.so.1: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXxf86dga.so.1: cannot open shared object file: No such file or directory
Application tries to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
Application tries to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
waiting for wineservers to exit...

---

### Post by Mustard on 2006-04-07
[QUOTE=tsharpe62]I'm having a couple small problems so far:
At step - I have now learned that winetools has at least one dependancy, pointed out by replies on this forum, here is the command for installing it (added 1st April 06, after 12 not a april fool btw)

I enter "sudo apt-get install libgtk1.2" and get
I'm getting "Package libgtkl.2 is not available, but is referred to by another package. Theis may mean that the package is missing, has been obsoleted, or is only available from another source.
E: Package libgtkl.2 has no installation candidate"[/QUOTE]

From the look of the error message you spelt libgtk1.2 wrong when doing the command.  The error message is saying there is no 'libgtkl.2' where the '1' has been replaced with an 'l' in '1.2'.

---

### Post by gazj on 2006-04-08
[QUOTE=manutd]oh boyz,
not looking good so far! :???: 

I've tried many different ways to find libstdc++6 and I dont think it is available on my system! 

When I go to Synaptic and search "libstdc" it finds only two apps.
1st is  - libstdc++5
2nd is - libstdc ++5-3.3.dev

I can't seem to find libstdc ++6 in order to correct my problem! 

Is there a way to correct this or am I going to have to get a new copy of Ubuntu. Maybe an updated version and install it again...
I'm currently running Ubuntu 5.04. Would this affect it???

anyway, help would be great when you get a sec.! 
I'm starting to get bored and annoyed working on this one app so far! :-k 
Its only the first one! 

anyway help would be great, and you guys have been great so far! 

THANKS AGAIN EH![/QUOTE]


First of all, thank you all for answering peoples problems, as i have been away for a few days, but im back now, and will try to help as much as possible

Anyway manutd, i think your problem probably does lie within you running hoary, any other hoary users had the same problem?

---

### Post by tsharpe62 on 2006-04-08
When I tried the instructions it appears to be installing it in my home folder and I can't complete the instructions and it won't run. Should I be back up to the root before I start?

---

### Post by rverrips on 2006-04-09
Thanks - Was racking my brain trying to get winetools 0.9 to install ie6 with wine 9.10 on dapper ... as per the howto dropping to 9.5 and then upgrading later worked great!

Question though:  Do you know why the winetools guys released an updated version to address the changes between wine 9.5 and 9.10/9.11 and to fix they broken font download links?

---

### Post by tsharpe62 on 2006-04-09
Here is where I'm going wrong with the posted procedure. I hope someone can give me some guidance.

tsharpe@ubuntuTara:~$ tar -xf winetools*
tar: winetools: Cannot read: Is a directory
tar: At beginning of tape, quitting now
tar: Error is not recoverable: exiting now
tsharpe@ubuntuTara:~$ cd winetools*
tsharpe@ubuntuTara:~/winetools$ sudo ./install
Password:
sudo: ./install: command not found
tsharpe@ubuntuTara:~/winetools$ wt
bash: wt: command not found
tsharpe@ubuntuTara:~/winetools$

---

### Post by BarFly on 2006-04-09
Ok, I must have really messed this up before I found this thread.  How to get rid of winetools and wine and start from scratch?  This time I will follow thiis tutorial.  I don't really care about anything I installed using wine before, so I would just assume get rid of all of that as well.

---

### Post by djl on 2006-04-09
Well I knew I could mess it up... install went flawless but when I try to open the program it goes: /home/djlee/.wine/c/Program:" (no such file) I can SEE it!!!  What did I do wrong and can I recover or do I have to start again?

thanks...

---

### Post by djl on 2006-04-09
Nevermind - the idiot remains... I hide my head in shame...

---

### Post by eRoot on 2006-04-10
First of all, great guide! It was really clear and easy to follow.

However, I do have a problem with a certain program, called "Everest Poker".
When I try to run it I get the following messages:
```
barry@box:~$ wine "/home/barry/.wine/c/Program Files/Everest Poker/Everest Poker.exe"
barry@box:~$ fixme:avifile:AVIFileExit (): stub!
fixme:msg:pack_message msg 85 (WM_NCPAINT) not supported yet
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet

```
The program then freezes while displaying the splashscreen.

I've googled a bit for WM_NCPAINT and WM_ERASEBKGND, but failed to find a solution.
Is this a case of a program that just isn't supported (yet), or might this be a fixable problem?

---

### Post by Bullfrogger on 2006-04-10
Great Job Guy's now you made it clearer

---

### Post by tsharpe62 on 2006-04-10
okay, I've made some progress in that I figured out that I had to go into synaptic package manager and enable other repositories. Here is where I'm currently stuck and requesting assistance:

&#65279;techsupp@ubuntuESI:~$ wget [http://kent.dl.sourceforge.net/sourceforge/wine/wine_0.9.5-winehq-1_i386.deb](http://kent.dl.sourceforge.net/sourceforge/wine/wine_0.9.5-winehq-1_i386.deb)
--03:19:12--  [http://kent.dl.sourceforge.net/sourceforge/wine/wine_0.9.5-winehq-1_i386.deb](http://kent.dl.sourceforge.net/sourceforge/wine/wine_0.9.5-winehq-1_i386.deb)
           => `wine_0.9.5-winehq-1_i386.deb'
Resolving kent.dl.sourceforge.net... 212.219.56.167
Connecting to kent.dl.sourceforge.net|212.219.56.167|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 13,951,010 (13M) [application/x-debian-package]

100%[====================================>] 13,951,010    83.50K/s    ETA 00:00

03:22:33 (68.05 KB/s) - `wine_0.9.5-winehq-1_i386.deb' saved [13951010/13951010]
techsupp@ubuntuESI:~$ sudo dpkg -i wine*.deb
Password:
(Reading database ... 57399 files and directories currently installed.)
Preparing to replace wine 0.9.5-winehq-1 (using wine_0.9.5-winehq-1_i386.deb) ...
Unpacking replacement wine ...
Setting up wine (0.9.5-winehq-1) ...

techsupp@ubuntuESI:~$ sudo apt-get install libgtk1.2
Reading package lists... Done
Building dependency tree... Done
libgtk1.2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 86 not upgraded.
techsupp@ubuntuESI:~$ tar -xf winetools*
tar: winetools*: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
techsupp@ubuntuESI:~$

---

### Post by gazj on 2006-04-10
[QUOTE=BarFly]Ok, I must have really messed this up before I found this thread.  How to get rid of winetools and wine and start from scratch?  This time I will follow thiis tutorial.  I don't really care about anything I installed using wine before, so I would just assume get rid of all of that as well.[/QUOTE]

ok to unistall wine completely including all configuration files etc

```
sudo apt-get remove wine
cd ~/.wine
rm -Rv *
```

as for the winetools program that dosen't need removing, but to remove its config files

```
cd ~/winetools
rm -Rv *
cd ~/bin
rm -Rv *
```

You may find you don't have theese files, if you don't do not worry, now you can start a new wine setup

---

### Post by gazj on 2006-04-10
[QUOTE=eRoot]First of all, great guide! It was really clear and easy to follow.

However, I do have a problem with a certain program, called "Everest Poker".
When I try to run it I get the following messages:
```
barry@box:~$ wine "/home/barry/.wine/c/Program Files/Everest Poker/Everest Poker.exe"
barry@box:~$ fixme:avifile:AVIFileExit (): stub!
fixme:msg:pack_message msg 85 (WM_NCPAINT) not supported yet
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet

```
The program then freezes while displaying the splashscreen.

I've googled a bit for WM_NCPAINT and WM_ERASEBKGND, but failed to find a solution.
Is this a case of a program that just isn't supported (yet), or might this be a fixable problem?[/QUOTE]

Im really sorry to say, I have no idea!!, Wine does not work with a lot of programs it really is hit and miss, Sorry

---

### Post by gazj on 2006-04-10
> **tsharpe62]okay, I've made some progress in that I figured out that I had to go into synaptic package manager and enable other repositories. Here is where I'm currently stuck and requesting assistance:

&#65279 said:**
> http://kent.dl.sourceforge.net/sourceforge/wine/wine_0.9.5-winehq-1_i386.deb[/url]
--03:19:12--  [http://kent.dl.sourceforge.net/sourceforge/wine/wine_0.9.5-winehq-1_i386.deb](http://kent.dl.sourceforge.net/sourceforge/wine/wine_0.9.5-winehq-1_i386.deb)
           => `wine_0.9.5-winehq-1_i386.deb'
Resolving kent.dl.sourceforge.net... 212.219.56.167
Connecting to kent.dl.sourceforge.net|212.219.56.167|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 13,951,010 (13M) [application/x-debian-package]

100%[====================================>] 13,951,010    83.50K/s    ETA 00:00

03:22:33 (68.05 KB/s) - `wine_0.9.5-winehq-1_i386.deb' saved [13951010/13951010]
techsupp@ubuntuESI:~$ sudo dpkg -i wine*.deb
Password:
(Reading database ... 57399 files and directories currently installed.)
Preparing to replace wine 0.9.5-winehq-1 (using wine_0.9.5-winehq-1_i386.deb) ...
Unpacking replacement wine ...
Setting up wine (0.9.5-winehq-1) ...

techsupp@ubuntuESI:~$ sudo apt-get install libgtk1.2
Reading package lists... Done
Building dependency tree... Done
libgtk1.2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 86 not upgraded.
techsupp@ubuntuESI:~$ tar -xf winetools*
tar: winetools*: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
techsupp@ubuntuESI:~$


did you miss out the line which sais

```
wget http://ds80-237-203-29.dedicated.hosteurope.de/wt/winetools-0.9jo-III.tar.gz
```

Hope that helps :)

---

### Post by tsharpe62 on 2006-04-10
Okay, I learned something today I'd like to share with the "newbies" out there before they attempt to use this procedure. Go into Symantic Package Manager and click on Settings and then Repositories then click on Settings, check show disabled software sources and Download upgradable packages. Now I'm not sure which ones are THE important ones to check so I checked them all. Do the upgrade and this procedure works great!

---

### Post by bixin on 2006-04-11
[QUOTE=gazj]ok to unistall wine completely including all configuration files etc

```
sudo apt-get remove wine
cd ~/.wine
rm -Rv *
```

as for the winetools program that dosen't need removing, but to remove its config files

```
cd ~/winetools
rm -Rv *
cd ~/bin
rm -Rv *
```

You may find you don't have theese files, if you don't do not worry, now you can start a new wine setup[/QUOTE]


Did this and restarted at the begining of how to word for word, copy pasted everthing, went flawlessly. I checked libtk1.2 it was already updated, checked libstdc++6(just in case) it was updated too. Now here is the printing of my terminal screen:

barbara@ubuntu:~/winetools$ wt
no suitable Wine directory found...
Wine 0.9.5
wine is executed as wine
Parameters are --noexit
Wine is not configured yet!
Browser is /usr/bin/firefox.
WINEVER is "0.9.5".
Calls to wine are executed as  "wine".
Config is /home/barbara/.wine/winetools.log.
Choice is Base setup
Choice is Create a Fake Windows drive with checked=F
waiting for wineservers to exit...
all wineservers endet after 0 seconds...
/usr/bin/wineprefixcreate: line 173: 15303 Segmentation fault      "${WINELOADER:-wine}" rundll32.exe setupapi.dll,InstallHinfSection DefaultInstall 128 wine.inf
/usr/local/bin/wt: line 130: 15313 Segmentation fault      winecfg -D
waiting for wineservers to exit...
all wineservers endet after 2 seconds...
Drive C: is /home/barbara/.wine/drive_c, links will be made for c fake_windows
Linking /home/barbara/.wine/drive_c to c...
Linking /home/barbara/.wine/drive_c to fake_windows...
Linking "/home/barbara/.wine/c/" to "/home/barbara/.wine/c/Program Files"
mv: cannot move `/home/barbara/.wine/c//Program Files' to a subdirectory of itself, `/home/barbara/.wine/c/Program Files/Program Files'
rmdir: `/home/barbara/.wine/c/': Not a directory
ln: `/home/barbara/.wine/c//Program Files': cannot overwrite directory
Linking "/home/barbara/.wine/c/" to "/home/barbara/.wine/c/Program Files/Common Files"
rmdir: `/home/barbara/.wine/c/': Not a directory
waiting for wineservers to exit...
all wineservers endet after 0 seconds...
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
wine: cannot open (null)
no suitable Wine directory found...
Wine 0.9.5
wine is executed as wine
Parameters are NEW
Wine is not configured yet!
barbara@ubuntu:~/winetools$

It said I should get a confirmation of a successful creation, sadly I didn't. Did base selection as told, create fake drive, and nada, just goes through the motions restarts and brings me back to the begining. I have Breezy, I had the up to date version of Wine installed that is why I removed per instructions and started again, cause I could do the create fake drive on it but instead of tada you have created it I got, "Fake drive *not* created" was the asteriks around the not made to tease me :)

Its past midnight and I have to go but would appreciate any help.](*,) 

Its like a love hate relationship, I don't love it until it screws up then I just cant leave it alone.

---

### Post by Nordoelum on 2006-04-11
```
nordoelum@nordoelum:~$ sudo winecfg
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/nordoelum', starting in the Windows directory.
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/', starting in the Windows directory.
```

How to fix?

---

### Post by gazj on 2006-04-11
[QUOTE=bixin]Did this and restarted at the begining of how to word for word, copy pasted everthing, went flawlessly. I checked libtk1.2 it was already updated, checked libstdc++6(just in case) it was updated too. Now here is the printing of my terminal screen:

barbara@ubuntu:~/winetools$ wt
no suitable Wine directory found...
Wine 0.9.5
wine is executed as wine
Parameters are --noexit
Wine is not configured yet!
Browser is /usr/bin/firefox.
WINEVER is "0.9.5".
Calls to wine are executed as  "wine".
Config is /home/barbara/.wine/winetools.log.
Choice is Base setup
Choice is Create a Fake Windows drive with checked=F
waiting for wineservers to exit...
all wineservers endet after 0 seconds...
/usr/bin/wineprefixcreate: line 173: 15303 Segmentation fault      "${WINELOADER:-wine}" rundll32.exe setupapi.dll,InstallHinfSection DefaultInstall 128 wine.inf
/usr/local/bin/wt: line 130: 15313 Segmentation fault      winecfg -D
waiting for wineservers to exit...
all wineservers endet after 2 seconds...
Drive C: is /home/barbara/.wine/drive_c, links will be made for c fake_windows
Linking /home/barbara/.wine/drive_c to c...
Linking /home/barbara/.wine/drive_c to fake_windows...
Linking "/home/barbara/.wine/c/" to "/home/barbara/.wine/c/Program Files"
mv: cannot move `/home/barbara/.wine/c//Program Files' to a subdirectory of itself, `/home/barbara/.wine/c/Program Files/Program Files'
rmdir: `/home/barbara/.wine/c/': Not a directory
ln: `/home/barbara/.wine/c//Program Files': cannot overwrite directory
Linking "/home/barbara/.wine/c/" to "/home/barbara/.wine/c/Program Files/Common Files"
rmdir: `/home/barbara/.wine/c/': Not a directory
waiting for wineservers to exit...
all wineservers endet after 0 seconds...
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
wine: cannot open (null)
no suitable Wine directory found...
Wine 0.9.5
wine is executed as wine
Parameters are NEW
Wine is not configured yet!
barbara@ubuntu:~/winetools$

It said I should get a confirmation of a successful creation, sadly I didn't. Did base selection as told, create fake drive, and nada, just goes through the motions restarts and brings me back to the begining. I have Breezy, I had the up to date version of Wine installed that is why I removed per instructions and started again, cause I could do the create fake drive on it but instead of tada you have created it I got, "Fake drive *not* created" was the asteriks around the not made to tease me :)

Its past midnight and I have to go but would appreciate any help.](*,) 

Its like a love hate relationship, I don't love it until it screws up then I just cant leave it alone.[/QUOTE]

I think you may have permission problems with your home folder, are you sure you own it, and have write permissions, i could be wrong though

---

### Post by gazj on 2006-04-11
[QUOTE=Nordoelum]```
nordoelum@nordoelum:~$ sudo winecfg
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/nordoelum', starting in the Windows directory.
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/', starting in the Windows directory.
```

How to fix?[/QUOTE]

You shouldn't be running winecfg as root, in fact you shouldn't run anything with wine as root, your wine configuration is for your normal user only

the only sudo commands should be to install wine and to install winetools

---

### Post by Ferrat on 2006-04-12
Is is just me that can't download the windows installer?

---

### Post by Vadim on 2006-04-12
I can download the Windows Installer, but I can't install it :(

---

### Post by stuman on 2006-04-12
All looks good until after the IE6 install...get mesage...."err:exec:SHELL_ExecuteW cannot set directory L"c:\\windows\\system32\\shell32.dll" repeated a few times, then "An error has occurred while setting up "c\windows\system32\drmclien.dll". This error has been logged, the installation will continue".

---

### Post by 1oki on 2006-04-12
Why would you want IE on Linux? You have firefox! lol

---

### Post by SteveHoffmanUK on 2006-04-12
The HOWTO looks very promising, and everything went fine until this bit of the dialogue:

```
steve@steve:~$ tar -xf winetools*
steve@steve:~$ wt
bash: wt: command not found
steve@steve:~$ tar -xf winetools*
tar: winetools-0.9jo-III: Cannot read: Is a directory
tar: At beginning of tape, quitting now
tar: Error is not recoverable: exiting now
steve@steve:~$ sudo ./install
sudo: ./install: command not found
```

I did copy/paste everything from the HOWTO, so no typing errors were made.

Any suggestions?

---

### Post by Nordoelum on 2006-04-12
**[gazj:]("http://ubuntuforums.org/member.php?u=71413") **Thank you for explaing :D[B]
[]("http://ubuntuforums.org/member.php?u=71413")[/B]

---

### Post by goblin on 2006-04-15
Hi all, well I am quite proud of myself managing to get this far only to stumble at the one of the last hurdles. I have got to the installation of of DCOM98 when I am told the installation fails...grrrrrrrrr  I assume it has something to do with the "Gdk-WARNING **: locale not supported by C library" but am only guessing at this stage, below is the terminal window from running "wt" any suggestions?

Cheers Mike



[SIZE="1"][SIZE="2"][SIZE="1"]krispie@ubuntu:~ $ wt
detecting Wine version... done.
Drive C: is /home/krispie/.wine/drive_c
Wine 0.9.5[/SIZE]
wine is executed as wine
Parameters are --noexit
Browser is /usr/bin/mozilla.
WINEVER is "0.9.5".

Gdk-WARNING **: locale not supported by C library
Calls to wine are executed as  "wine".
Config is /home/krispie/.wine/winetools.log.

Gdk-WARNING **: locale not supported by C library

Gdk-WARNING **: locale not supported by C library

Gdk-WARNING **: locale not supported by C library
Choice is Base setup

Gdk-WARNING **: locale not supported by C library
Choice is Create a Fake Windows drive with checked=F
waiting for wineservers to exit...

Gdk-WARNING **: locale not supported by C library
all wineservers endet after 0 seconds...

Gdk-WARNING **: locale not supported by C library

Gdk-WARNING **: locale not supported by C library

Gdk-WARNING **: locale not supported by C library
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": l ibXxf86vm.so.1: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": l ibXxf86vm.so.1: cannot open shared object file: No such file or directory
Application tries to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
err:module:load_builtin_dll failed to load .so lib for builtin L"ddraw.dll": lib Xxf86vm.so.1: cannot open shared object file: No such file or directory
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
/home/krispie/.wine updated successfully.
ln: when making multiple links, last argument must be a directory
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": l ibXxf86vm.so.1: cannot open shared object file: No such file or directory
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
waiting for wineservers to exit...

Gdk-WARNING **: locale not supported by C library
all wineservers endet after 2 seconds...
Drive C: is /home/krispie/.wine/drive_c, links will be made for c fake_windows
Linking /home/krispie/.wine/drive_c to c...
Linking /home/krispie/.wine/drive_c to fake_windows...
waiting for wineservers to exit...

Gdk-WARNING **: locale not supported by C library
all wineservers endet after 0 seconds...

Gdk-WARNING **: locale not supported by C library
detecting Wine version... done.
Drive C: is /home/krispie/.wine/drive_c
Wine 0.9.5
wine is executed as wine
Parameters are H:\.wine\NEW

Gdk-WARNING **: locale not supported by C library

Gdk-WARNING **: locale not supported by C library
Choice is DCOM98 with checked=F
dcom98.exe to check
software installation verified by /home/krispie/.wine/winetools.log
1229056 bytes previously downloaded
WINEDEBUG="fixme-all" WINEDLLOVERRIDES="ole32=n" wine ./dcom98.exe
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": l ibXxf86vm.so.1: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": l ibXxf86vm.so.1: cannot open shared object file: No such file or directory
Application tries to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
waiting for wineservers to exit...

Gdk-WARNING **: locale not supported by C library
all wineservers endet after 0 seconds...
Failed: 199
check installation by return value...
waiting for wineservers to exit...

Gdk-WARNING **: locale not supported by C library
all wineservers endet after 0 seconds...

Gdk-WARNING **: locale not supported by C library
Failed: 199

Gdk-WARNING **: locale not supported by C library[/SIZE][/SIZE]

Gdk-WARNING **: locale not supported by C library

---

### Post by stengah on 2006-04-16
Hi there Gazj (and everybody else) ;-),

I've been following your tutorial step by step and everything has installed well, but when I get to this exact step in winetools something messes up:

"Select base setup again then install true type font arial

Next main menu then select Install Microsoft true type corefonts, yet again go all the way down the list until you have installed all the fonts."

It doesn't quite work out 100% for me... download boxes appear, and nothing happens (like links are dead) with the true type font in the base install, and likewise with the Andale font install... all the other font installs work out fine!

Maybe you have any suggestions? Are these two font installs necessary? 

Otherwise, thanks for an excellent tutorial anf for helping out!!!
[B]
EDIT:[/B] I got IE up and running and it looks fine so I guess the font issue isn't that serious!

---

### Post by gazj on 2006-04-18
> **stengah]Hi there Gazj (and everybody else)  said:**
> 
EDIT:[/B] I got IE up and running and it looks fine so I guess the font issue isn't that serious!

The fonts are not critical, although many windows applications use these standard fonts, and may look strange if they use a default linux one, thats all

as long as you have them in the right folder, ie /home/username/winetools/fonts and they have the correct filename they should work

sometimes if you tried to download them with winetools before you downloaded them manually as shown in the how to, you can end up with the manual files taking a new filename, as there is already a unfinshed download of the file wintools tried to download

that sounds horribly complicated, but hopefully you know what i mean

if in doubt delete all files in the /home/username/winetools/fonts folder then run the command to download the fonts again

---

### Post by BjornHaland on 2006-04-18
Thanks for posting that. 
Very helpful, especially considering you took the time to explain those steps that seem obvious to many, but is a stumbling block to the new user. 
Thanks.

---

### Post by laxe on 2006-04-21
[QUOTE=gazj]```
sudo apt-get install libgtk1.2
```

I will also add this to the guide, must have already had this on my system, Thanks[/QUOTE]
admin@ubuntu:~$ sudo apt-get install libgtk1.2
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libgtk1.2


please help?

---

### Post by Mustard on 2006-04-22
[QUOTE=laxe]admin@ubuntu:~$ sudo apt-get install libgtk1.2
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libgtk1.2
please help?[/QUOTE]

Given that libgtk1.2 is in the main repository, thats a pretty strange error.  The only scenario in which I could think that particular error could occur is if you had a completely blank sources.list in your /etc/apt folder, or perhaps if all sources were commented out on your sources.list.  There may be other reasons for why it could occur, but I can't think of any.

---

### Post by tlaloczint on 2006-04-23
ok I have all pretty much install it got ie working till when I update wine 
then a window appear that say it something like "mozilla active x control v1.7.12 
(ReactOS special) so I did and then it only flash for a nanosecond and desapear
then I went and unistall it but then the window pop again saying the aplication as recuested an active x browser bla,bla,bla so if a choose not I got a plain blank window nothing at all 

any help?

this is the output

neo@matrix:~$ wine "c:\program files\internet explorer\iexplore.exe"
fixme:shdocvw:IEWinMain "" 1
fixme:win:SetWindowTextA setting text "Mozilla ActiveX Control v1.7.12 (ReactOS special) Setup" of other process window (nil) should not use SendMessage
fixme:win:SetWindowTextA setting text "Mozilla ActiveX Control v1.7.12 (ReactOS special) Setup" of other process window (nil) should not use SendMessage
fixme:shell:SHAutoComplete SHAutoComplete stub
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:shdocvw:iecs_QueryInterface unknown interface {00020400-0000-0000-c000-000000000046}
fixme:shdocvw:iecs_QueryInterface unknown interface {9c2cad80-3424-11cf-b670-00aa004cd6d8}
fixme:shdocvw:is_CanInPlaceActivate
fixme:shdocvw:is_OnUIActivate
neo@matrix:~$

and then

neo@matrix:~$ wine "c:\program files\internet explorer\iexplore.exe"
fixme:shdocvw:IEWinMain "" 1
fixme:shdocvw:iecs_QueryInterface unknown interface {00020400-0000-0000-c000-000 000000046}
fixme:shdocvw:iecs_QueryInterface unknown interface {9c2cad80-3424-11cf-b670-00a a004cd6d8}
fixme:shdocvw:is_CanInPlaceActivate
fixme:shdocvw:is_OnUIActivate
neo@matrix:~$




soory bad english

---

### Post by la3r on 2006-04-24
[QUOTE=tlaloczint]ok I have all pretty much install it got ie working till when I update wine 
then a window appear that say it something like "mozilla active x control v1.7.12 
(ReactOS special) so I did and then it only flash for a nanosecond and desapear
then I went and unistall it but then the window pop again saying the aplication as recuested an active x browser bla,bla,bla so if a choose not I got a plain blank window nothing at all 

any help?
[/QUOTE]

Yeah I have the same problem.

---

### Post by pug_205 on 2006-04-24
I'm having a niggling issue with wine. Whenever I try to download updates I get timed out in the middle of my update everytime. :mad: Actually, the same thing happened when I was installing, and I had to run the install several times before I could get wine fully downloaded. What's going on?

---

### Post by gazj on 2006-04-24
[QUOTE=pug_205]I'm having a niggling issue with wine. Whenever I try to download updates I get timed out in the middle of my update everytime. :mad: Actually, the same thing happened when I was installing, and I had to run the install several times before I could get wine fully downloaded. What's going on?[/QUOTE]

Unfortunately i have the same problem. although my download does resume from where it left off, so its not a huge pain but it is one.

---

### Post by BobSongs on 2006-04-24
Yeah; I got the same thing. My WINE updated and then a pop-up about a Mozilla plug-in of sorts when I started up Internet Explorer.

Since then IE won't start any more and my WINE apps are all acting kinda funny: crashing, in other words.

Perhaps a bit of a hand holding on how to completely eliminate WINE to the last file and folder so I can start again? I rely on some win32 apps to get me through the day.

If I can scrub it all off my hard disk perhaps a fresh install will do it for me. If not, it's "re-install Ubuntu" time.

Thanks.

*EDIT* I followed all the standard procedures. 1) I removed WINE through Apt-Get; 2) I removed WineTools through sudo ./uninstall; 3) I looked for relevent folders and trashed them; 4) I reinstalled WINE 0.9.5; 5) I reinstalled WineTools... same errors. WINE was not updated and it was still floundering.

---

### Post by raosid on 2006-04-25
hi all,
thanks for the help on how to install wine and setting up. But i am facing a big problem which i was facing even before using the wine tools. The following is the error i get while installing IE in my system...

fixme:shdocvw:IEWinMain "" 1
fixme:shdocvw:iecs_QueryInterface unknown interface {00020400-0000-0000-c000-000 000000046}
fixme:shdocvw:iecs_QueryInterface unknown interface {9c2cad80-3424-11cf-b670-00a a004cd6d8}
fixme:shdocvw:is_CanInPlaceActivate
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not regist ered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for for context 0x1
fixme:ole:CoCreateInstance no classfactory created for CLSID {4955dd33-b159-11d0 -8fcf-00aa006bcc59}, hres is 0x80040154
fixme:shdocvw:is_OnUIActivate
[siddharth@localhost InternetExplorer]$


Please find a solution for this as i need to get IE running in my pc.

regards,
siddharth

---

### Post by sprung on 2006-04-25
same problem here :-|

got complaints about shdocvw.dll, initpki.dll and cryptdlg.dll during ie-reinstall

maybe it's winetools' fault?

any ideas would be very welcome :-k

---

### Post by DoLoop on 2006-04-25
I had the same issue, so I uninstalled everything, again reinstalled exactly following the HOWTO, and this time did not update my wine install to the latest version.  No Mozilla plug-in prompt, and IE runs okay.

Now to install some Windows software...<fingers crossed>

Mike

[QUOTE=BobSongs]Yeah; I got the same thing. My WINE updated and then a pop-up about a Mozilla plug-in of sorts when I started up Internet Explorer.

Since then IE won't start any more and my WINE apps are all acting kinda funny: crashing, in other words.

Perhaps a bit of a hand holding on how to completely eliminate WINE to the last file and folder so I can start again? I rely on some win32 apps to get me through the day.

If I can scrub it all off my hard disk perhaps a fresh install will do it for me. If not, it's "re-install Ubuntu" time.

Thanks.

*EDIT* I followed all the standard procedures. 1) I removed WINE through Apt-Get; 2) I removed WineTools through sudo ./uninstall; 3) I looked for relevent folders and trashed them; 4) I reinstalled WINE 0.9.5; 5) I reinstalled WineTools... same errors. WINE was not updated and it was still floundering.[/QUOTE]

---

### Post by DoLoop on 2006-04-25
Just to add an inconsequential tip (I don't think it has _any_ effect on the install): During the IE 6 setup process using winetools, you are asked if you want to save your setup files locally.  If you choose yes, winetools will attempt to copy the files to "/home/USERNAME/winetools/sys/Windows Update Setup Files" which won't exist unless you create it beforehand.  So if you want to save the setup files, be sure to create that directory!

Mike

PS And yes, you'll want to substitute your user name for the USERNAME placeholder above...  I have a bad habit of cutting, pasting and forgetting to change placeholders to actual values. :)

---

### Post by BobSongs on 2006-04-25
Thanks, DoLoop. I tried that. Honest, I did. And fail, fail, fail.

Just to give everyone a "heads-up." Here's what I've done to date.

1. Trashed Ubuntu. Wiped it from the hard disk. No panic for me. I've got my documents and downloads all on a different partition. So a reinstall isn't a major headache for me. It's also more of a learning experience than anything else.

2. Updated Ubuntu.

3. Installed Automatix and installed a truck-load of goodies but not Wine.

4. Installed a ton of applications via **Applications | Add Applications **.

5. Installed Wine 0.9.5 which I downloaded from this tutorial, first page: error-free. Immediately the "New updates available" message popped up. For the mean time I'll hold off from installing it.

6. Decompressed the WineTools tarball. ./install produced this error: "You do not have gettext installed on your system. WineTools will not run in your native language. Rather it will use english." English IS the system language.

7. Installed **gettext**, uninstalled WineTools, re-installed WineTools: error-free.

8. Installed [PhotoFiltre]("http://www.photofiltre.com/"), a free Win32 application I enjoy using: Success!!

9. Now to set up WineTools.

Setting up WineTools

1. Fake Windows drive setup: error-free. However the PhotoFiltre setup has ... vanished. Part of the "fake drive setup", no doubt. Re-installed PhotoFiltre (PhotoFiltre still works).

2. Installed Arial Font (through WineTools): error-free.

3. Installed Microsoft Foundation Classes 4.x (through WineTools): error-free.

4. Installed Microsoft's Internet Explorer & Media Player 6.4 (through WineTools): (lingers a long time at 45%... but it does carry on... just gotta be patient) error-free (again, for me this means PhotoFiltre works just as it normally does.

5. All steps completed. PhotoFiltre throws up no errors.

NOTE: My assessement is this: a fresh Ubuntu + Wine 0.9.5 + WineTools = **an error-free subsystem**. I would discourage anyone from *updating Wine needlessly beyond 0.9.5*. I believe the associated "mozilla" plugin is what brought on the errors. If I do upgrade, I won't use that thing. In the words of William Shakespeare: "Install not that Mozilla plugin: it shall bugger up thy system." ;)

Bob

---

### Post by sprung on 2006-04-26
thanks! i just uninstalled wine, installed 0.95 and mfc,dcom,.. and ie - works for me

still strange (the strange mozilla-plugin-autoupdate was downloaded from winehq..)

---

### Post by c1ean on 2006-04-26
Great up... This helped lots:)

---

### Post by RobyX on 2006-04-28
I just finished setting it up, took exactly 44 minutes.

Thanks man I can finnaly use my old trusty Windows media player and go on Diablo2.

---

### Post by KrazyPenguin on 2006-04-28
[QUOTE=BobSongs]Thanks, DoLoop. I tried that. Honest, I did. And fail, fail, fail.

NOTE: My assessement is this: a fresh Ubuntu + Wine 0.9.5 + WineTools = **an error-free subsystem**. I would discourage anyone from *updating Wine needlessly beyond 0.9.5*. I believe the associated "mozilla" plugin is what brought on the errors. If I do upgrade, I won't use that thing. In the words of William Shakespeare: "Install not that Mozilla plugin: it shall bugger up thy system."

Bob[/QUOTE]

Just pin the packages and that way when you upgrade, everthing will upgrade except for WINE and everything else you pinned.

;-)

---

### Post by ephman on 2006-04-29
hi,

seems that everything i need to install for system software comes up with no such file or directory.  am i missing something?  sort of stuck here.

ls: Msvbvm50.exe: No such file or directory

any help would be really appreciated.

thanks,
ephman

---

### Post by vruoh on 2006-04-29
Hi!

Firstly thanks for this great tutorial!

I've installed one application and then when i'm trying to launch that it pops ups box with OK-button which says: "Could not read INI file!". When i press OK it will continue to the application BUT this application is useless without that .INI file. Any ideas?

---

### Post by eyesonly on 2006-04-29
This seems to be a great HOWTO.  I can run IE6 after the install however when I try to install Quicken from a disk with
wine install.exe

This is what I get and unfortunately I have no idea what this means?????

jbs@eyesonly:/cdrom$ wine install.exe
fixme:powermgnt:SetThreadExecutionState (0x80000001): stub, harmless.
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:powermgnt:SetThreadExecutionState (0x80000000): stub, harmless.
err:rpc:RPCRT4_OpenConnection protseq mswmsg not supported
wine: Unhandled page fault on write access to 0x00000000 at address 0x7fae9181 (thread 0028), starting debugger...
WineDbg starting on pid 0x27
Unhandled exception: page fault on write access to 0x00000000 in 32-bit code (0x7fae9181).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:1007 GS:0033
 EIP:7fae9181 ESP:7fae9138 EBP:00000017 EFLAGS:00010206(   - 00      - RIP1)
 EAX:00000000 EBX:00000000 ECX:7fd60020 EDX:7fdbe738
 ESI:7fae9220 EDI:7fae914c
Stack dump:
0x7fae9138:  0000007b 7fae9220 7fae9220 7fdf5a58
0x7fae9148:  00000000 7fae91b0 65f149e9 80002d48
0x7fae9158:  7fae917c 00000001 7fdb9680 7fae91a8
0x7fae9168:  7fdf5a58 7fae9220 00000000 80002c00
0x7fae9178:  80002d38 00000017 00000016 00000002
0x7fae9188:  00040005 00000000 00000016 00000017
0200: sel=1007 base=7fec2000 limit=00001fff 32-bit rw-
Backtrace:
=>1 0x7fae9181 (0x7fae9181)
  2 0x00000000 (0x00000000)
0x7fae9181: addb        %al,0x0(%eax)
Modules:
Module  Address                 Debug info      Name (84 modules)
PE      0x00400000-00435000     Deferred        setup
PE      0x47d70000-47d82000     Deferred        sdbapi
PE      0x54100000-54107000     Deferred        sage
PE      0x65f00000-65fc2000     Deferred        ole32
ELF     0x7be86000-7bf00000     Deferred        ntdll<elf>
  \-PE  0x7bea0000-7bf00000     \               ntdll
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7cf0b000-7cf20000     Deferred        midimap<elf>
  \-PE  0x7cf10000-7cf20000     \               midimap
ELF     0x7d032000-7d056000     Deferred        msacm32<elf>
  \-PE  0x7d040000-7d056000     \               msacm32
ELF     0x7d056000-7d09a000     Deferred        wineoss<elf>
  \-PE  0x7d070000-7d09a000     \               wineoss
ELF     0x7d09a000-7d120000     Deferred        winmm<elf>
  \-PE  0x7d0b0000-7d120000     \               winmm
PE      0x7d120000-7d14f000     Deferred        iuser7
PE      0x7d380000-7d3ba000     Deferred        iscript7
PE      0x7d3c0000-7d3c8000     Deferred        objps7
ELF     0x7d76e000-7d7d0000     Deferred        msvcrt<elf>
  \-PE  0x7d780000-7d7d0000     \               msvcrt
ELF     0x7d818000-7d82f000     Deferred        msacm<elf>
  \-PE  0x7d820000-7d82f000     \               msacm
ELF     0x7e0fb000-7e12c000     Deferred        uxtheme<elf>
  \-PE  0x7e100000-7e12c000     \               uxtheme
ELF     0x7e14a000-7e153000     Deferred        libxcursor.so.1
ELF     0x7e153000-7e16f000     Deferred        imm32<elf>
  \-PE  0x7e160000-7e16f000     \               imm32
ELF     0x7e16f000-7e18b000     Deferred        ximcp.so.2
ELF     0x7e18b000-7e8f4000     Deferred        libglcore.so.1
ELF     0x7e8f4000-7e973000     Deferred        libgl.so.1
ELF     0x7e973000-7ea33000     Deferred        libx11.so.6
ELF     0x7ea33000-7ea4c000     Deferred        libice.so.6
ELF     0x7ea4c000-7eacb000     Deferred        winex11<elf>
  \-PE  0x7ea60000-7eacb000     \               winex11
ELF     0x7eacb000-7eaea000     Deferred        libexpat.so.1
ELF     0x7eaea000-7eb18000     Deferred        libfontconfig.so.1
ELF     0x7eb18000-7eb2c000     Deferred        libz.so.1
ELF     0x7eb2c000-7eb96000     Deferred        libfreetype.so.6
ELF     0x7eb96000-7ebb4000     Deferred        iphlpapi<elf>
  \-PE  0x7eba0000-7ebb4000     \               iphlpapi
ELF     0x7ebb4000-7ebfd000     Deferred        rpcrt4<elf>
  \-PE  0x7ebd0000-7ebfd000     \               rpcrt4
ELF     0x7ebfd000-7ec8f000     Deferred        oleaut32<elf>
  \-PE  0x7ec10000-7ec8f000     \               oleaut32
ELF     0x7ec8f000-7ed44000     Deferred        comctl32<elf>
  \-PE  0x7eca0000-7ed44000     \               comctl32
ELF     0x7ed44000-7ee66000     Deferred        user32<elf>
  \-PE  0x7ed60000-7ee66000     \               user32
ELF     0x7ee66000-7eea4000     Deferred        advapi32<elf>
  \-PE  0x7ee70000-7eea4000     \               advapi32
ELF     0x7ef8a000-7f88e000     Deferred        gdi32<elf>
  \-PE  0x7efd0000-7f88e000     \               gdi32
ELF     0x7f88e000-7f8e7000     Deferred        shlwapi<elf>
  \-PE  0x7f8a0000-7f8e7000     \               shlwapi
ELF     0x7f8e7000-7f9b3000     Deferred        shell32<elf>
  \-PE  0x7f900000-7f9b3000     \               shell32
ELF     0x7f9b3000-7f9c7000     Deferred        lz32<elf>
  \-PE  0x7f9c0000-7f9c7000     \               lz32
ELF     0x7f9c7000-7f9e0000     Deferred        version<elf>
  \-PE  0x7f9d0000-7f9e0000     \               version
ELF     0x7faf1000-7faf9000     Deferred        libxrender.so.1
ELF     0x7fc41000-7fd40000     Deferred        kernel32<elf>
  \-PE  0x7fc60000-7fd40000     \               kernel32
ELF     0x7fd44000-7fd48000     Deferred        libxfixes.so.3
ELF     0x7fd48000-7fd4a000     Deferred        xlcutf8load.so.2
ELF     0x7fd4c000-7fd50000     Deferred        libxdmcp.so.6
ELF     0x7fd53000-7fd60000     Deferred        libxext.so.6
ELF     0x7fe70000-7fe75000     Deferred        libxxf86vm.so.1
ELF     0x7fe75000-7fe80000     Deferred        libgcc_s.so.1
ELF     0x7fe80000-7fe8b000     Deferred        libnss_files.so.2
ELF     0x7fe8b000-7fe95000     Deferred        libnss_nis.so.2
ELF     0x7fe95000-7feab000     Deferred        libnsl.so.1
ELF     0x7feab000-7feb5000     Deferred        libnss_compat.so.2
ELF     0x7feb6000-7febb000     Deferred        libxxf86dga.so.1
ELF     0x7febb000-7fec2000     Deferred        libsm.so.6
ELF     0x7fec4000-7fec6000     Deferred        libnvidia-tls.so.1
ELF     0x7fec6000-7fee9000     Deferred        libm.so.6
ELF     0x7fee9000-7ffe0000     Deferred        libwine_unicode.so.1
ELF     0xb7e60000-b7e63000     Deferred        libxau.so.6
ELF     0xb7e65000-b7e69000     Deferred        libdl.so.2
ELF     0xb7e69000-b7f97000     Deferred        libc.so.6
ELF     0xb7f97000-b7faa000     Deferred        libpthread.so.0
ELF     0xb7fb7000-b7fd1000     Deferred        libwine.so.1
ELF     0xb7fd3000-b7fe9000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000027 (D) D:\disk1\setup.exe
        0000002d    0
        00000028    0 <==
00000025
        00000026    0
00000022
        00000024    0
        00000023    0
00000016
        00000019    0
        00000018    0
        00000017    0
0000000f
        00000010    0
jbs@eyesonly:/cdrom$

---

### Post by 255MP on 2006-04-30
[QUOTE=newpants2003]when install the ie(sp1) it tells me   mfc40.dell   not installed yet.  and i chose to keep going, then it tells me install fail. thats where the falls start.

and also my windows are in E:/ , but looks like the wt defaul to looking in C:/ , then tells me could not find the file it need, then falls. 

Wine is finalizing your software installation. This may take a few minutes,
though it never actually does.
err:exec:SHELL_ExecuteW cannot set directory L"c:\\windows\\system32\\shell32.dll"
err:exec:SHELL_ExecuteW cannot set directory L"c:\\windows\\system32\\shell32.dll"
err:exec:SHELL_ExecuteW cannot set directory L"c:\\windows\\system32\\shell32.dll"
err:exec:SHELL_ExecuteW cannot set directory L"c:\\windows\\system32\\shell32.dll"
err:exec:SHELL_ExecuteW cannot set directory L"c:\\windows\\system32\\shell32.dll"
err:exec:SHELL_ExecuteW cannot set directory L"c:\\windows\\system32\\shell32.dll"
err:module:import_dll Library MFC40.DLL (which is needed by L"C:\\Program Files\\Common Files\\Microsoft Shared\\MSInfo\\ieinfo5.ocx") not found
err:exec:SHELL_ExecuteW cannot set directory L"c:\\windows\\system32\\shell32.dll"
err:exec:SHELL_ExecuteW cannot set directory L"c:\\windows\\system32\\shell32.dll"
Registration of c:\windows\system32\StdOle2.Tlb successful.


how to solve the problem?[/QUOTE]

I am having this problem too, except my Windows XP is installed on the C drive... Any sugggestions on how to fix it?

---

### Post by YaNoS on 2006-05-05
hey, i'm getting
```
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
Calls to wine are executed as  "wine".
Config is /home/raphael/.wine/winetools.log.
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
```

Help? =/

---

### Post by macoxp on 2006-05-07
*Bows* so godly thx for the tut. My first day useing linux and i got everything you said :D

---

### Post by sefs on 2006-05-07
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/   <--- generates a malfored error in apt-get can you correct it in the HOWTO as to what it really should be?

Thanks.

---

### Post by YokoZar on 2006-05-08
[QUOTE=sefs]deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/   <--- generates a malfored error in apt-get can you correct it in the HOWTO as to what it really should be?

Thanks.[/QUOTE]
The sourceforge server sucks and is being phased out.  Please use these:

deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) breezy main

**OR**

deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

Yes, there are now separate Breezy and Dapper packages.

---

### Post by Xilon on 2006-05-08
I just installed WINE, I've got an amd64 so I had to install the i386 package and copy over some 32bit libraries for it to work (didn't want to bother with chroot). Upon trying to run winetool I get an error which people here seemed to have solved by installing libgtk1.2... I on the other hand already have it installed :confused: 
```
sebastian@Odin:~$ wt
detecting Wine version... done.
Drive C: is /home/sebastian/.wine/drive_c
Wine 0.9.12
wine is executed as wine
Parameters are --noexit
Browser is /usr/bin/firefox.
WINEVER is "0.9.12".
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
Calls to wine are executed as  "wine".
Config is /home/sebastian/.wine/winetools.log.
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
sebastian@Odin:~$ sudo apt-get install libgtk1.2
Reading package lists... Done
Building dependency tree... Done
libgtk1.2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
sebastian@Odin:~$ locate libgtk-1.2.so.0
/usr/lib/libgtk-1.2.so.0.9.1
/usr/lib/libgtk-1.2.so.0

```Any ideas wth went wrong? Is it in the wrong directory or something?

---

### Post by monomaniacpat on 2006-05-08
After installing Windows installer it comes up saying: "It appears the installation failed". What can I do?

---

### Post by bodhi.zazen on 2006-05-08
An alternate to winetools is sidenet. [http://sidenet.ddo.jp/winetips/config.html](http://sidenet.ddo.jp/winetips/config.html)

For games, how about Cedega?

for other programs how about Corssover office?

---

### Post by Guns90 on 2006-05-08
Sorry, I now realize that I shouldn't have posted here.

---

### Post by disk11 on 2006-05-09
I am getting an error message about mfc40.dll missing when I try to install IE6.  How do I fix this?

Edit: Never mind, I forgot to install something before hand.  Disregard as I cannot figure out how to delete posts.

---

### Post by Guns90 on 2006-05-09
I tried (unsuccessfully) to install wine earlier today.  Following these steps, everything seemed to work alrightafter I did the install; however, when I shut the computer down and came back later, I was getting those 'fix me....." replies.  I tried to removeeverything and start over, but I guess that I'm leaving stuff in because when I get to the 'cd winetools*' followed by the 'sudo ./install', I get ' You already installed winetools.  remove the earlier installation and then come back.'   Any suggestions?

---

### Post by Xilon on 2006-05-09
I had the same problem when uninstalling winetools. Luckily winetools operates on a bash script basis and hence it was easy to see what it was checking :)

Hmm... I just extracted the tarball and it seems that there is an uninstall script... odd since there wasn't one when I was uninstalling :(
just try running ./uninstall

If that doesn't work then just look at the install script```
# installation
echo "Installing WineTools to $BASEDIR..."
if [ -e "$BASEDIR" ]; then
  echo "You already installed WineTools. Uninstall the old installation first and come back."
  exit 1
fi
mkdir -p $BASEDIR
cp -R * $BASEDIR
ln -sf $BASEDIR/$WTFILE /usr/local/bin/wt
ln -sf $BASEDIR/$WTFILE /usr/local/bin/winetools
ln -sf $BASEDIR/findwine /usr/local/bin/findwine
```
You can see that it checks whether $BASEDIR (/usr/local/winetools) exists and hence deleting it would allow you to install winetools. I would delete all the other "residue" files aswell though.

---

### Post by ryan76 on 2006-05-11
I installed to your specs and everything works great (except the program i installed it for, but that's because it needs USB support). :(

EXCEPT the arial font has gone all crazy!
[http://homepages.woosh.co.nz/ryan.kennedy/images/weirdgoogle.jpg](http://homepages.woosh.co.nz/ryan.kennedy/images/weirdgoogle.jpg)

How can I fix it? I thought maybe I could reinstall Arial font but I'm not sure how.

Thanks

---

### Post by gazj on 2006-05-11
[QUOTE=ryan76]I installed to your specs and everything works great (except the program i installed it for, but that's because it needs USB support).

EXCEPT the arial font has gone all crazy!
[http://homepages.woosh.co.nz/ryan.ke...eirdgoogle.jpg](http://homepages.woosh.co.nz/ryan.ke...eirdgoogle.jpg)

How can I fix it? I thought maybe I could reinstall Arial font but I'm not sure how.

Thanks
__________________
registered Linux user number 404927 [/QUOTE]

I think the Arial font is just a bit crazy in wine, but you can run winetools again to reinstall the font if you like, it will warn you that it is already installed but you can force it to install again, but it probably won't make much difference, but by all means give it a go

---

### Post by ryan76 on 2006-05-12
I reinstalled it through winetools and no change. I would like to reinstall Arial through the terminal somehow. I can't find where Arial is sitting other than through winetools/fonts that I set up in the Howto.

Can someone please help? It's really hard to read webpages this way and I have a lot of work to do.

Thanks

Edit: Success! I installed msttcorefonts and that fixed it.

---

### Post by spartan777 on 2006-05-14
***UPDATE***
i've deleted what i already fixed.

but i'm having the same problem several others are having, ie6 breaks after updating wine! i'd like to eventually try using steam and counter-strike source, so using the latest version would be better. somebody mentioned 'pinning' the dependencies. does that fix it, and how do you pin dependencies? thanks for the help.

the other thing, which really isn't a problem per se, is that i need to have wine be usable in other profiles/ for other users. it would be a major pain to go through the whole kit 'n kabootle when everything already works for my user. could i just copy files over to the other profile, and give them the proper permissions? is there a simple option in wine i missed?

---

### Post by sefs on 2006-05-14
The tutorial works perfectly until you do an update to a version like 0.9.13.  Then IE becomes broken.  It just loads with a blank window.  If anyone solved this would, keep us in the loop.

Thanks.

---

### Post by TheHattrick on 2006-05-17
When i try to start IE - blank window 
```
devil@devil:~$ wine "/home/devil/.wine/c/Program Files/Internet Explorer/IEXPLORE.EXE"
fixme:shdocvw:IEWinMain "" 1
fixme:rpc:I_RpcServerStartListening (0x10024): stub
fixme:rpc:I_RpcWindowProc (0x10024,0000001c,00000001,00000000): stub
Could not load Mozilla. HTML rendering will be disabled.
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x7fdda424)->((null) 1 0x7fa4fb0c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x7fdda424)->((null) 25 0 0x7fa4faf8 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x7fdda424)->((null) 26 0 0x7fa4faf8 (nil))
fixme:shdocvw:ClDispatch_Invoke (0x7fdda424)->(-709 {00000000-0000-0000-0000-000000000000} 2048 0002 0x7fa4fa84 0x7fa4fab0 (nil) 0x7fa4fa94)
fixme:shdocvw:ClDispatch_Invoke (0x7fdda424)->(-5512 {00000000-0000-0000-0000-000000000000} 2048 0002 0x7fa4fa64 0x7fa4fa90 (nil) 0x7fa4fa74)
fixme:shdocvw:ClDispatch_Invoke (0x7fdda424)->(-5501 {00000000-0000-0000-0000-000000000000} 2048 0002 0x7fa4fa84 0x7fa4fab0 (nil) 0x7fa4fa94)
fixme:shdocvw:ClDispatch_Invoke (0x7fdda424)->(-5512 {00000000-0000-0000-0000-000000000000} 2048 0002 0x7fa4fa64 0x7fa4fa90 (nil) 0x7fa4fa74)
fixme:shdocvw:ClDispatch_Invoke (0x7fdda424)->(-5502 {00000000-0000-0000-0000-000000000000} 2048 0002 0x7fa4fa84 0x7fa4fab0 (nil) 0x7fa4fa94)
fixme:shdocvw:ClDispatch_Invoke (0x7fdda424)->(-5513 {00000000-0000-0000-0000-000000000000} 2048 0002 0x7fa4fa84 0x7fa4fab0 (nil) 0x7fa4fa94)
fixme:shdocvw:ClDispatch_Invoke (0x7fdda424)->(-726 {00000000-0000-0000-0000-000000000000} 2048 0002 0x7fa4fa84 0x7fa4fab0 (nil) 0x7fa4fa94)
fixme:shdocvw:ClientSite_GetContainer (0x7fdda424)->(0x7fa4fb2c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x7fdda424)->({000214d1-0000-0000-c000-000000000046} 37 0 0x7fa4fc18 (nil))
fixme:rpc:I_RpcWindowProc (0x10024,0000001c,00000000,00000000): stub
fixme:rpc:I_RpcServerStopListening (): stub
fixme:rpc:I_RpcWindowProc (0x10024,00000002,00000000,00000000): stub
fixme:rpc:I_RpcWindowProc (0x10024,00000082,00000000,00000000): stub
fixme:rpc:RpcServerUnregisterIf (IfSpec == (RPC_IF_HANDLE)^0x65f0cf10, MgrTypeUuid == (null), WaitForCallsToComplete == 1): stub
fixme:rpc:RpcServerUnregisterIf (IfSpec == (RPC_IF_HANDLE)^0x65f0cec8, MgrTypeUuid == (null), WaitForCallsToComplete == 1): stub
fixme:rpc:RpcServerUnregisterIf (IfSpec == (RPC_IF_HANDLE)^0x7fdda0a8, MgrTypeUuid == (null), WaitForCallsToComplete == 1): stub
fixme:rpc:RpcServerUnregisterIf (IfSpec == (RPC_IF_HANDLE)^0x7fdc8c28, MgrTypeUuid == (null), WaitForCallsToComplete == 1): stub

```

I don't care about IE, I installed wine, just because I want the pretty version of skype, not that ugly stuf. So I installed Skype 2.5 BETA and here is what happens when i try to start it:
```
devil@devil:~$ wine "/home/devil/.wine/c/Program Files/Skype/Phone/Skype.exe"
wine: Unhandled page fault on read access to 0x7cb42224 at address 0x0000:0x0040430a (thread 0009), starting debugger...
WineDbg starting on pid 0x8
First chance exception: page fault on read access to 0x7cb42224 in 32-bit code (0x0040430a).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:003b GS:0033
 EIP:0040430a ESP:7fa5f374 EBP:7fa5fdcc EFLAGS:00210206(   - 00      - RIP1)
 EAX:7cb42224 EBX:00404ebe ECX:00000000 EDX:7fa5f301
 ESI:7fa5fdac EDI:7fa5fdac
Stack dump:
0x7fa5f374:  00404c05 00404ec8 00000000 7bebb1ff
0x7fa5f384:  7cb42224 7fa5f7c8 7fa5f3b4 7fa5f3cc
0x7fa5f394:  00000001 7fa5fdac 7bef3744 7bed3d55
0x7fa5f3a4:  7fa5f7c8 7fa5fdac 7fa5f4fc 7fa5f44c
0x7fa5f3b4:  7fa5fdac 7beb03f0 7fa5fdac 7beaa27a
0x7fa5f3c4:  7e741395 7e79a0b4 7fa5f3ec 7bed3d29
Backtrace:
=>1 0x0040430a in skype (+0x430a) (0x0040430a)
  2 0x00404f13 in skype (+0x4f13) (0x00404f13)
  3 0x7fcdd01f in kernel32 (+0x4d01f) (0x7fcdd01f)
  4 0xb7f82637 wine_switch_to_stack+0x17 in libwine.so.1 (0xb7f82637)
0x0040430a: movl        0x0(%eax),%ecx
Modules:
Module  Address                 Debug info      Name (101 modules)
PE      0x00400000-017b4000     Export          skype
PE      0x5e380000-5e3a5000     Deferred        msoss
PE      0x65f00000-65fc2000     Deferred        ole32
PE      0x71590000-7159e000     Deferred        wintrust
ELF     0x7be82000-7bf00000     Deferred        ntdll<elf>
  \-PE  0x7be90000-7bf00000     \               ntdll
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7caba000-7cb1c000     Deferred        msvcrt<elf>
  \-PE  0x7cad0000-7cb1c000     \               msvcrt
ELF     0x7cc4b000-7cc60000     Deferred        midimap<elf>
  \-PE  0x7cc50000-7cc60000     \               midimap
ELF     0x7cd9a000-7cdb1000     Deferred        msacm32<elf>
  \-PE  0x7cda0000-7cdb1000     \               msacm32
ELF     0x7cdb1000-7cdf5000     Deferred        wineoss<elf>
  \-PE  0x7cdc0000-7cdf5000     \               wineoss
ELF     0x7cdf5000-7ce41000     Deferred        libgcrypt.so.11
ELF     0x7ce41000-7ce51000     Deferred        libtasn1.so.2
ELF     0x7ce51000-7ceb3000     Deferred        libgnutls.so.11
ELF     0x7ceb3000-7ced0000     Deferred        libcups.so.2
ELF     0x7cf14000-7cf18000     Deferred        libgpg-error.so.0
ELF     0x7ddff000-7de30000     Deferred        uxtheme<elf>
  \-PE  0x7de10000-7de30000     \               uxtheme
ELF     0x7e59a000-7e59e000     Deferred        libxfixes.so.3
ELF     0x7e59e000-7e5a7000     Deferred        libxcursor.so.1
ELF     0x7e5a7000-7e5af000     Deferred        libxrender.so.1
ELF     0x7e5af000-7e5cb000     Deferred        ximcp.so.2
ELF     0x7e5cb000-7e5d2000     Deferred        libdrm.so.1
ELF     0x7e5d2000-7e638000     Deferred        libgl.so.1
ELF     0x7e638000-7e63c000     Deferred        libxdmcp.so.6
ELF     0x7e63c000-7e63f000     Deferred        libxau.so.6
ELF     0x7e63f000-7e6ff000     Deferred        libx11.so.6
ELF     0x7e6ff000-7e70c000     Deferred        libxext.so.6
ELF     0x7e70c000-7e725000     Deferred        libice.so.6
ELF     0x7e725000-7e7a4000     Deferred        winex11<elf>
  \-PE  0x7e730000-7e7a4000     \               winex11
ELF     0x7e7a4000-7e7c3000     Deferred        libexpat.so.1
ELF     0x7e7c3000-7e7f1000     Deferred        libfontconfig.so.1
ELF     0x7e7f1000-7e805000     Deferred        libz.so.1
ELF     0x7e805000-7e86f000     Deferred        libfreetype.so.6
ELF     0x7e86f000-7e883000     Deferred        shfolder<elf>
  \-PE  0x7e880000-7e883000     \               shfolder
ELF     0x7e883000-7e897000     Deferred        oleacc<elf>
  \-PE  0x7e890000-7e897000     \               oleacc
ELF     0x7e897000-7e91e000     Deferred        winmm<elf>
  \-PE  0x7e8a0000-7e91e000     \               winmm
ELF     0x7e91e000-7e95c000     Deferred        crypt32<elf>
  \-PE  0x7e930000-7e95c000     \               crypt32
ELF     0x7e95c000-7e987000     Deferred        winspool<elf>
  \-PE  0x7e960000-7e987000     \               winspool
ELF     0x7e987000-7ea24000     Deferred        comdlg32<elf>
  \-PE  0x7e9a0000-7ea24000     \               comdlg32
ELF     0x7ea24000-7ea44000     Deferred        cabinet<elf>
  \-PE  0x7ea30000-7ea44000     \               cabinet
ELF     0x7ea44000-7ea78000     Deferred        urlmon<elf>
  \-PE  0x7ea50000-7ea78000     \               urlmon
ELF     0x7ea78000-7ea97000     Deferred        mpr<elf>
  \-PE  0x7ea80000-7ea97000     \               mpr
ELF     0x7ea97000-7eada000     Deferred        wininet<elf>
  \-PE  0x7eaa0000-7eada000     \               wininet
ELF     0x7eada000-7eb34000     Deferred        shlwapi<elf>
  \-PE  0x7eaf0000-7eb34000     \               shlwapi
ELF     0x7eb34000-7ec0a000     Deferred        shell32<elf>
  \-PE  0x7eb50000-7ec0a000     \               shell32
ELF     0x7ec0a000-7ec26000     Deferred        imm32<elf>
  \-PE  0x7ec10000-7ec26000     \               imm32
ELF     0x7ec26000-7ecdb000     Deferred        comctl32<elf>
  \-PE  0x7ec30000-7ecdb000     \               comctl32
ELF     0x7ecdb000-7ecef000     Deferred        lz32<elf>
  \-PE  0x7ece0000-7ecef000     \               lz32
ELF     0x7ecef000-7ed08000     Deferred        version<elf>
  \-PE  0x7ed00000-7ed08000     \               version
ELF     0x7ed08000-7ed26000     Deferred        iphlpapi<elf>
  \-PE  0x7ed10000-7ed26000     \               iphlpapi
ELF     0x7ed26000-7ed71000     Deferred        rpcrt4<elf>
  \-PE  0x7ed40000-7ed71000     \               rpcrt4
ELF     0x7ed71000-7ee04000     Deferred        oleaut32<elf>
  \-PE  0x7ed90000-7ee04000     \               oleaut32
ELF     0x7ee04000-7ee42000     Deferred        advapi32<elf>
  \-PE  0x7ee10000-7ee42000     \               advapi32
ELF     0x7ef28000-7f82d000     Deferred        gdi32<elf>
  \-PE  0x7ef70000-7f82d000     \               gdi32
ELF     0x7f82d000-7f950000     Deferred        user32<elf>
  \-PE  0x7f850000-7f950000     \               user32
ELF     0x7fa60000-7fa65000     Deferred        libxxf86vm.so.1
ELF     0x7fa65000-7fa70000     Deferred        libgcc_s.so.1
ELF     0x7fc72000-7fd70000     Export          kernel32<elf>
  \-PE  0x7fc90000-7fd70000     \               kernel32
ELF     0x7fe81000-7fe8c000     Deferred        libnss_files.so.2
ELF     0x7fe8c000-7fe96000     Deferred        libnss_nis.so.2
ELF     0x7fe96000-7feac000     Deferred        libnsl.so.1
ELF     0x7feac000-7feb6000     Deferred        libnss_compat.so.2
ELF     0x7feb6000-7febb000     Deferred        libxxf86dga.so.1
ELF     0x7febb000-7fec2000     Deferred        libsm.so.6
ELF     0x7fec6000-7fee9000     Deferred        libm.so.6
ELF     0x7fee9000-7ffe0000     Deferred        libwine_unicode.so.1
ELF     0xb7e20000-b7e22000     Deferred        xlcutf8load.so.2
ELF     0xb7e2c000-b7e30000     Deferred        libdl.so.2
ELF     0xb7e30000-b7f5e000     Deferred        libc.so.6
ELF     0xb7f5e000-b7f71000     Deferred        libpthread.so.0
ELF     0xb7f7d000-b7f97000     Export          libwine.so.1
ELF     0xb7f99000-b7faf000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a
        0000000b    0
00000008 (D) C:\Program Files\Skype\Phone\Skype.exe
        00000009    0 <==

```

Sorry for the long errors... tomorrow morning I will try [Image Creator 1.5]("http://panasonic.co.jp/pavc/global/projector/download/p1sd.html") so please give advices, cause I'm just ](*,)

---

### Post by peanut butter on 2006-05-17
first. thats for an older version of skype. you should just be able to do wine skypesertup.exe

also if you get a better qttheme it will look a lot better. (the linux version)

---

### Post by peanut butter on 2006-05-17
This how to also works in drapper drake.

---

### Post by Xilon on 2006-05-18
[QUOTE=Xilon]I just installed WINE, I've got an amd64 so I had to install the i386 package and copy over some 32bit libraries for it to work (didn't want to bother with chroot). Upon trying to run winetool I get an error which people here seemed to have solved by installing libgtk1.2... I on the other hand already have it installed :confused: 
```
sebastian@Odin:~$ wt
detecting Wine version... done.
Drive C: is /home/sebastian/.wine/drive_c
Wine 0.9.12
wine is executed as wine
Parameters are --noexit
Browser is /usr/bin/firefox.
WINEVER is "0.9.12".
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
Calls to wine are executed as  "wine".
Config is /home/sebastian/.wine/winetools.log.
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
sebastian@Odin:~$ sudo apt-get install libgtk1.2
Reading package lists... Done
Building dependency tree... Done
libgtk1.2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
sebastian@Odin:~$ locate libgtk-1.2.so.0
/usr/lib/libgtk-1.2.so.0.9.1
/usr/lib/libgtk-1.2.so.0

```Any ideas wth went wrong? Is it in the wrong directory or something?[/QUOTE]
bump

---

### Post by originaluoc on 2006-05-18
Hello I have just installed wine and when I try to run Internet Explorer a blank window appears, and the following information in the terminal.

originaluoc@ubuntu:~$ wine "c:\program files\internet explorer\iexplore.exe"

sizeof(RADEONDRIRec) == 100, devPrivSize 100
fixme:shdocvw:IEWinMain "" 1
fixme:rpc:I_RpcServerStartListening (0x1002a): stub
fixme:rpc:I_RpcWindowProc (0x1002a,0000001c,00000001,00000000): stub
Could not load Mozilla. HTML rendering will be disabled.
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x7fdd9c6c)->((null) 1 0x7faffb0c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x7fdd9c6c)->((null) 25 0 0x7faffaf8 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x7fdd9c6c)->((null) 26 0 0x7faffaf8 (nil))
fixme:shdocvw:ClDispatch_Invoke (0x7fdd9c6c)->(-709 {00000000-0000-0000-0000-000000000000} 2048 0002 0x7faffa84 0x7faffab0 (nil) 0x7faffa94)
fixme:shdocvw:ClDispatch_Invoke (0x7fdd9c6c)->(-5512 {00000000-0000-0000-0000-000000000000} 2048 0002 0x7faffa64 0x7faffa90 (nil) 0x7faffa74)
fixme:shdocvw:ClDispatch_Invoke (0x7fdd9c6c)->(-5501 {00000000-0000-0000-0000-000000000000} 2048 0002 0x7faffa84 0x7faffab0 (nil) 0x7faffa94)
fixme:shdocvw:ClDispatch_Invoke (0x7fdd9c6c)->(-5512 {00000000-0000-0000-0000-000000000000} 2048 0002 0x7faffa64 0x7faffa90 (nil) 0x7faffa74)
fixme:shdocvw:ClDispatch_Invoke (0x7fdd9c6c)->(-5502 {00000000-0000-0000-0000-000000000000} 2048 0002 0x7faffa84 0x7faffab0 (nil) 0x7faffa94)
fixme:shdocvw:ClDispatch_Invoke (0x7fdd9c6c)->(-5513 {00000000-0000-0000-0000-000000000000} 2048 0002 0x7faffa84 0x7faffab0 (nil) 0x7faffa94)
fixme:shdocvw:ClDispatch_Invoke (0x7fdd9c6c)->(-726 {00000000-0000-0000-0000-000000000000} 2048 0002 0x7faffa84 0x7faffab0 (nil) 0x7faffa94)
fixme:shdocvw:ClientSite_GetContainer (0x7fdd9c6c)->(0x7faffb2c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x7fdd9c6c)->({000214d1-0000-0000-c000-000000000046} 37 0 0x7faffc18 (nil))
fixme:rpc:I_RpcWindowProc (0x1002a,0000001c,00000000,00000000): stub
fixme:rpc:I_RpcServerStopListening (): stub
fixme:rpc:I_RpcWindowProc (0x1002a,00000002,00000000,00000000): stub
fixme:rpc:I_RpcWindowProc (0x1002a,00000082,00000000,00000000): stub
fixme:rpc:RpcServerUnregisterIf (IfSpec == (RPC_IF_HANDLE)^0x65f0cf10, MgrTypeUuid == (null), WaitForCallsToComplete == 1): stub
fixme:rpc:RpcServerUnregisterIf (IfSpec == (RPC_IF_HANDLE)^0x65f0cec8, MgrTypeUuid == (null), WaitForCallsToComplete == 1): stub
fixme:rpc:RpcServerUnregisterIf (IfSpec == (RPC_IF_HANDLE)^0x7fdd98f0, MgrTypeUuid == (null), WaitForCallsToComplete == 1): stub
fixme:rpc:RpcServerUnregisterIf (IfSpec == (RPC_IF_HANDLE)^0x7fdc8470, MgrTypeUuid == (null), WaitForCallsToComplete == 1): stub
------------------------------------------------------------------------------------------------
Any ideas?

---

### Post by peanut butter on 2006-05-20
well thats the wrong path to internet explorer.

---

### Post by nami on 2006-05-21
Hi

I followed the instuctions on the first page and everything went fine.  I created launchers and internet explorer outlook express and windows media player worked perfectly.

Until i restarted my computer and now internet explorer and outlook express dont work.  when i click internet explorer it just flashes and closes again???

---

### Post by nami on 2006-05-21
Is it possible to UNDO this HOWTO so I can start again?

---

### Post by peanut butter on 2006-05-21
hi i made a script that will do the first part saveing a significant amount of time just  set your sourceforge mirror and run it. its attached as a tar.gz
the comments should help.
p.s. I have put it under the MIT licence or EXPAT as it is non virul.:)
i wrote it so i could set wine up on my dads computer but ill put it here

---

### Post by peanut butter on 2006-05-21
[QUOTE=nami]Is it possible to UNDO this HOWTO so I can start again?[/QUOTE]
yah just unonstall wine by doing 
```
sudo apt-get remove wine
```

then delete the winetools folder in your home dir.

---

### Post by R3linquish3r on 2006-05-21
[QUOTE=originaluoc]Hello I have just installed wine and when I try to run Internet Explorer a blank window appears, and the following information in the terminal.

originaluoc@ubuntu:~$ wine "c:\program files\internet explorer\iexplore.exe"

sizeof(RADEONDRIRec) == 100, devPrivSize 100
fixme:shdocvw:IEWinMain "" 1
fixme:rpc:I_RpcServerStartListening (0x1002a): stub
fixme:rpc:I_RpcWindowProc (0x1002a,0000001c,00000001,00000000): stub
Could not load Mozilla. HTML rendering will be disabled.
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x7fdd9c6c)->((null) 1 0x7faffb0c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x7fdd9c6c)->((null) 25 0 0x7faffaf8 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x7fdd9c6c)->((null) 26 0 0x7faffaf8 (nil))
fixme:shdocvw:ClDispatch_Invoke (0x7fdd9c6c)->(-709 {00000000-0000-0000-0000-000000000000} 2048 0002 0x7faffa84 0x7faffab0 (nil) 0x7faffa94)
fixme:shdocvw:ClDispatch_Invoke (0x7fdd9c6c)->(-5512 {00000000-0000-0000-0000-000000000000} 2048 0002 0x7faffa64 0x7faffa90 (nil) 0x7faffa74)
fixme:shdocvw:ClDispatch_Invoke (0x7fdd9c6c)->(-5501 {00000000-0000-0000-0000-000000000000} 2048 0002 0x7faffa84 0x7faffab0 (nil) 0x7faffa94)
fixme:shdocvw:ClDispatch_Invoke (0x7fdd9c6c)->(-5512 {00000000-0000-0000-0000-000000000000} 2048 0002 0x7faffa64 0x7faffa90 (nil) 0x7faffa74)
fixme:shdocvw:ClDispatch_Invoke (0x7fdd9c6c)->(-5502 {00000000-0000-0000-0000-000000000000} 2048 0002 0x7faffa84 0x7faffab0 (nil) 0x7faffa94)
fixme:shdocvw:ClDispatch_Invoke (0x7fdd9c6c)->(-5513 {00000000-0000-0000-0000-000000000000} 2048 0002 0x7faffa84 0x7faffab0 (nil) 0x7faffa94)
fixme:shdocvw:ClDispatch_Invoke (0x7fdd9c6c)->(-726 {00000000-0000-0000-0000-000000000000} 2048 0002 0x7faffa84 0x7faffab0 (nil) 0x7faffa94)
fixme:shdocvw:ClientSite_GetContainer (0x7fdd9c6c)->(0x7faffb2c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x7fdd9c6c)->({000214d1-0000-0000-c000-000000000046} 37 0 0x7faffc18 (nil))
fixme:rpc:I_RpcWindowProc (0x1002a,0000001c,00000000,00000000): stub
fixme:rpc:I_RpcServerStopListening (): stub
fixme:rpc:I_RpcWindowProc (0x1002a,00000002,00000000,00000000): stub
fixme:rpc:I_RpcWindowProc (0x1002a,00000082,00000000,00000000): stub
fixme:rpc:RpcServerUnregisterIf (IfSpec == (RPC_IF_HANDLE)^0x65f0cf10, MgrTypeUuid == (null), WaitForCallsToComplete == 1): stub
fixme:rpc:RpcServerUnregisterIf (IfSpec == (RPC_IF_HANDLE)^0x65f0cec8, MgrTypeUuid == (null), WaitForCallsToComplete == 1): stub
fixme:rpc:RpcServerUnregisterIf (IfSpec == (RPC_IF_HANDLE)^0x7fdd98f0, MgrTypeUuid == (null), WaitForCallsToComplete == 1): stub
fixme:rpc:RpcServerUnregisterIf (IfSpec == (RPC_IF_HANDLE)^0x7fdc8470, MgrTypeUuid == (null), WaitForCallsToComplete == 1): stub
------------------------------------------------------------------------------------------------
Any ideas?[/QUOTE]


Looks like this is the fault of the newest version of wine. Same thing happened to me and I re-did the steps and right before I updated it IE worked fine. After I updated it it went bye-bye. We'll just have to wait for another wine update that fixes it or use the old one.

---

### Post by peanut butter on 2006-05-21
you can alwase downgrady your wine version to .95 the deb is on the first post.

---

### Post by TecH on 2006-05-22
I translated the guide into norwegian check out:
[http://metallictech.net/suprn/viewtopic.php?p=3049#3049](http://metallictech.net/suprn/viewtopic.php?p=3049#3049)

---

### Post by cskeide on 2006-05-22
Thanks for an excellent howto, gazj! First time I've had a wine install that actually works.

Having the same problem as some of you with IE6 not working after upgrading wine to version 0.9.13. I guess I'll have to stick with the older version until it gets fixed.

[QUOTE=TecH]I translated the guide into norwegian check out:
[http://metallictech.net/suprn/viewtopic.php?p=3049#3049](http://metallictech.net/suprn/viewtopic.php?p=3049#3049)[/QUOTE]
Nice job, TecH. One comment though... You have a recurring typo: "Insta**ll**ere". Two **L**'s! Not one. ;)

---

### Post by taipan899 on 2006-05-26
Can I ask a "**How to Get Wine Running**", question here?

I have installed Wine and thanks for the help and, Wine seems to be working. But, and there alwaya is. When I run an Exe file to install a program, Wine informs me that I need to be an administrator (under windows I assume) to install programs.

I am using Ubunto, on a single user system and have admin privelages. I also relogged in as root and got the same message from wine.](*,) ]. 

All assistance will be greatly appreciated.

Taipan899

---

### Post by fly5 on 2006-05-26
I translated this to finnish, you can find it from [here]("http://forum.ubuntu-fi.org/index.php?topic=3334.0").
great howto gazj! ;)

---

### Post by peanut butter on 2006-05-26
i might point out to you that source forge might have a faster mirror for finland, the one used in thistutorial isin the UK.

---

### Post by Jose Catre-Vandis on 2006-05-26
[QUOTE=255MP]I am having this problem too, except my Windows XP is installed on the C drive... Any sugggestions on how to fix it?[/QUOTE]

You need to install Microsoft Foundation Classes, from the Base Setup menu.

HTH

---

### Post by Jose Catre-Vandis on 2006-05-27
All has gone well for me with the installation and configuration. My only problem is with IE itself. If i type a url into the address bar/box, IE just dies, and I have to force quite. I can browse using links on web pages, e.g. googling, but cannot use the address bar, favorites and history don't work too well either?

---

### Post by grimdaze on 2006-05-27
[IMG]http://img132.imageshack.us/img132/4646/screenshot6bj.png[/IMG]

What's up with the window borders?

---

### Post by kokas on 2006-05-29
Hi there....Hi installed Wtools and Wine but now I don't know what to do....I manage to start notepad with "wine notepad" so I think the installation went Ok...but I don't know how to install new apps or if I can use the ones already installed in windows....I think that this still a bit of complicated method to begginers like myself....

---

### Post by minisori on 2006-05-29
[QUOTE=kokas]Hi there....Hi installed Wtools and Wine but now I don't know what to do....I manage to start notepad with "wine notepad" so I think the installation went Ok...but I don't know how to install new apps or if I can use the ones already installed in windows....I think that this still a bit of complicated method to begginers like myself....[/QUOTE]

"wine installer.exe"

About to use the ones already installed in windows... you can try but probably the best thing is to install them using wine.

---

### Post by kokas on 2006-05-29
This was what I got

"nelson@nelson-desktop:~$ wine installer.exe
wine: could not load L"c:\\windows\\system32\\installer.exe": Module not found
nelson@nelson-desktop:~$ wineserver: could not save registry branch to /home/nel son/.wine/system.reg : Permission denied
wineserver: could not save registry branch to /home/nelson/.wine/userdef.reg : P ermission denied
wineserver: could not save registry branch to /home/nelson/.wine/user.reg : Perm ission denied"

I would install them in wine if I knew how...I want to install fireworks and acdsee and I think that are suported softwares but I also have two apps that are portugueses versions of BitTorrent am IMessenger that I don't if it work in Wine also...Is wine made to support only the apps in their list ?

Tks

---

### Post by PPower on 2006-05-29
[quote=gazj]
[...]
We are back to the base setup menu, now select DCOM98 and then go down the list installing all the programs on the list, obvioulsy only do internet explorer in your language, the reason we have left the Arial font out is because the link to this is dead, but we will sort this later. Just click next and ok on everything, im sure you know how window installers work.
[...]
[/quote]
The latest build of WineTools does not suffer from this problem.
 
I didnt have time to go through all of the SF servers but I can confirm that the following contain the arial font:
 
UFPR
M
EasyNet
HEANet
Superb
NCHC
Puzzle*
 
* The new script points to puzzle.
 
The following dont:
Mesh
Optus

---

### Post by philetus on 2006-05-30
You're How To is pure genius. Wine installed without a hitch and IE runs great.
The only thing keeping me from switching my wife to Ubuntu is her Hong Kong Mahjong for windows.
I downloaded and installed it in wine, but can't get it to work.
launcher=wine "/home/eve/.wine/c/Program Files/Hong Kong Mahjong1024/Hkmj1024xp.exe. Is it the xp?
Heres the download.
[http://d.trymedia.com/dm/ninedragons/21m7p1024_d_53/trygames/HongKong_Mahjong1024.exe](http://d.trymedia.com/dm/ninedragons/21m7p1024_d_53/trygames/HongKong_Mahjong1024.exe)

---

### Post by minisori on 2006-05-30
[QUOTE=kokas]This was what I got

"nelson@nelson-desktop:~$ wine installer.exe
wine: could not load L"c:\\windows\\system32\\installer.exe": Module not found
nelson@nelson-desktop:~$ wineserver: could not save registry branch to /home/nel son/.wine/system.reg : Permission denied
wineserver: could not save registry branch to /home/nelson/.wine/userdef.reg : P ermission denied
wineserver: could not save registry branch to /home/nelson/.wine/user.reg : Perm ission denied"

I would install them in wine if I knew how...I want to install fireworks and acdsee and I think that are suported softwares but I also have two apps that are portugueses versions of BitTorrent am IMessenger that I don't if it work in Wine also...Is wine made to support only the apps in their list ?

Tks[/QUOTE]

Hmm, when i said "installer.exe" i was refering to any installer the program you wish to install come with. To make it more clear for you. If you are trying to install a program from a cd for example wich the name of the install program is "setup.exe" you would have to do probably

wine /media/cdrom/setup.exe

To ru wine you simply need to point where is the .exe file you want to run. Imagine you download somewhere an installer for a program, or the program itself, in any folder you wish, you would have to run from a terminal:

 wine "path_to_the_program/name_of_the_exe_file"

---

### Post by kokas on 2006-05-30
Ok I will give a try again. I did that with a .exe file I wanted to install but it did opened a Firefox page instead of the setup.

Do I really have to install the IE, Fonts, etc to run Wine and install apps ?

---

### Post by minisori on 2006-05-30
Not really, but maybe some need them.

---

### Post by BobSongs on 2006-05-30
Yo, **gazj**,

First: thanks for the tutorial.

Second: here's a suggestion for it. When Winetools is run it creates a folder in the /home/'user'/ folder called **bin**. Inside it are scripts for running IE6, Outlook Express, Windows Media Player, and DOS. The user just has to open a terminal, type **cd bin** and then one of the following to get it to run:

./ie6
./outlookexpress
./wmplayer
./dos

Third: a question for you Wine users. I have the Microsoft game called **Age of Empires / Gold Edition**. It's a hybrid CD: both music and data files. When I insert the CD I get a request to play music, but I cannot read the files. Any tips on how to do that?

Thanks.

---

### Post by shane2peru on 2006-06-02
Hey, Thanks for this great little howto!  I have used it before for Breezy, and I used it successfully today with Dapper!  Thanks!

Shane

---

### Post by kokas on 2006-06-02
In my BIN folder I only have shortcut for DOS and other saying Uninstall....What should I do to have the others ?

---

### Post by BobSongs on 2006-06-02
Just a sec... I'll post what's in each one.

**Edit 1**: did you install Internet Explorer 6.x in Wine using Winetools? I just cleared my "fake Windows drive" and created a new bin folder. All it has in it is **dos** and **uninstall**. The other files *should* show up when you go through the installation process.

**Edit 2**: installing IE6 now. I'll let you know what appears in the **bin** folder when I'm done. Keep an eye on this post and keep refreshing your page.

**Edit 3**: Okay. I installed IE6. All the shortcuts have appeared. If you've installed IE6 and you don't have the shortcuts, here they are:

For **ie6**,```
#!/bin/bash
. findwine
$WINE "c:\\program files\\internet explorer\\iexplore.EXE" $@ &>/dev/null &

```For **outlookexpress**,```
bob@PC1:~/bin$ cat outlookexpress
#!/bin/bash
. findwine
$WINE "c:\\program files\\outlook express\\msimn.exe" ${PARAM:+"$PARAM"} &>/dev/null &

```For **wmplayer**,```
#!/bin/bash
. findwine
for n in "c:\\archivos de programa\\Reproductor de Windows Media\\mplayer2.exe" \
         "c:\\program files\\windows media player\\mplayer2.exe"; do
  echo -n "localized version $n ... "
  UNIXPATH="`winepath -u "$n"`"
  if [ "$UNIXPATH" = "" ]; then
    echo "not found"
    continue
  fi
  echo "starting"
  $WINE "$n" ${PARAM:+"$PARAM"} &>/dev/null &
  exit 0
done
```For **uninstall**,```
#!/bin/bash
. findwine
$WINE uninstaller
```And for **dos** it's```
#!/bin/bash
. findwine
$WINE wcmd ${PARAM:+"$PARAM"}
```

---

### Post by kokas on 2006-06-02
Ok yeah probably I didn't install them so I went to Terminal typed wintools and I started by trying to install Fonts an the DCOM98 but I keep getting erros and nothing installs. I get a message in the end saying that it failed...heres a part of the terminal messages....they are of the same kind whatever I try to install.

```
check installation by return value...
waiting for wineservers to exit...
all wineservers endet after 0 seconds...
Failed: 255
\*new\* fake Windows drive to check
software installation verified by /home/nelson/.wine/winetools.log
dependency \*new\*
wineserver: could not save registry branch to /home/nelson/.wine/system.reg : Permission denied
wineserver: could not save registry branch to /home/nelson/.wine/userdef.reg : Permission denied
wineserver: could not save registry branch to /home/nelson/.wine/user.reg : Permission denied
dcom98.exe to check
software installation verified by /home/nelson/.wine/winetools.log
dependency dcom98.exe *not* fulfilled
Microsoft Internet Explorer.* to check
software installation verified by /home/nelson/.wine/winetools.log
dependency Microsoft
Choice is Show installed Software
testsw to check
software installation verified by /home/nelson/.wine/winetools.log
cat: /home/nelson/.wine/installed-software: No such file or directory
cat: /home/nelson/.wine/quiet-installed-software: No such file or directory
grep: /home/nelson/.wine/winetools.log: No such file or directory
grep: /home/nelson/.wine/winetools.log: No such file or directory
Choice is Base setup
```

---

### Post by kokas on 2006-06-02
I couldn't make it to work....I quit...I will uninstall Wine since I have essential tools (Autocad, Fireworks, Frontpage 2003) in windows anyway....but Ubuntu is so mcuh faster....it will be hard :( Tks for the help

---

### Post by BobSongs on 2006-06-02
Whoa there. Just a sec. Before you give up on this thread there, kokas, can I ask a few questions? What version of Wine are you running?

Did you download the one at the beginning of this tutorial? Did you upgrade it since? (The notification to upgrade can be a bit annoying and it's real tempting to upgrade to make the red circle go away.)

I can help you if you'd like to try again. I've had no problems when I followed the instructions (don't upgrade Wine). I can point you to the additional fonts. Cool?

---

### Post by eqisow on 2006-06-02
Try following the instructions on the Wiki, instead of this howto. It is much more up to date. :)

[http://wiki.ubuntu.com/Wine](http://wiki.ubuntu.com/Wine)

---

### Post by kokas on 2006-06-03
I was running the latest version of Wine...I did follow the wiki guide...thanks you very much for the help but the I realized that the tools that I need can't run in Wine either

Cheers,
Nelson

---

### Post by shuttleworthwannabe on 2006-06-11
Thansk fro the excellent instructions. I am having makor problem installing WIne and geting winetools working:

I have successfully created the fake ~/.wine drive and the base setup picked up my cdrom and Username was set. When I try to install DCOM98 I get this error (Screenshot-1)

I thus cannot proceed: what is it I am doing wrong or need to get going here?

thanks











> **gazj]*** UPDATE 08-06-2006 (UK DATE SYSTEM :) ) Apparently this how-to works with the Ubuntu 6.06 dapper drake, although i have not tested myself yet, feel free to give it a go, I have just moved house, and am waiting for my new broadband connection before i can download dapper and try, as soon as i know the results, i will update the post ***

After a lot of searching here there and every where I finally know how to get wine working on my machine anyway, every time without fail, and as there is a lack of how to's on wine, I thought i would give the Ubuntu community something back. This is my first how to, so don't be to harsh if it dosen't work for you.

First we get the wine0.95.deb from winehq [http://kent.dl.sourceforge.net/sourceforge/wine/wine_0.9.5-winehq-1_i386.deb]("http://kent.dl.sourceforge.net/sourceforge/wine/wine_0.9.5-winehq-1_i386.deb")

or if you want to open a terminal (alt+F2 then type gnome-terminal then enter) to download it use this command

```
 wget http://kent.dl.sourceforge.net/sourceforge/wine/wine_0.9.5-winehq-1_i386.deb
```

In case your wondering why we are not downloading the latest version of wine its because internet explorer install breaks on newer versions and you will probably need internet explorer to get other programs working, but we will update wine after, so don't worry

Right so we got our Wine .deb so lets unpackage it in our terminal dont forget to change directory to where you downloaded wine (if you used the above command you should already be there)

```
sudo dpkg -i wine*.deb
```

ok, so we no have wine, but how do i use it, set up a C:/ D:/ etc i hear you cry, let alone install anything, well here come the great little app called winetools  said:**
> http://ds80-237-203-29.dedicated.hosteurope.de/wt/winetools-0.9jo-III.tar.gz[/URL]

or if your still with me in the good old terminal you can use this command

```
wget http://ds80-237-203-29.dedicated.hosteurope.de/wt/winetools-0.9jo-III.tar.gz
```

ok, so we got this great tool no we need to unpack it

```
tar -xf winetools*
```

and install it

```
cd winetools*
sudo ./install
```

Done :) so lets start this wonderfull tool with this

```
wt
```

you will get loads of messages popup about not being configured etc, just keep clicking ok oh and that you should also own a copy of windows to use some of these tools. Yeah Yeah on with the plot.

You should finally get to a menu

So first we go for base setup, then create a fake windows drive
Next winetools will find your cdrom for you so it can set it up for wine
Followed by a username and organization, I Just leave theese as is
After a few fake windows restarts later we are told fake drive completed. Yippee

We are back to the base setup menu, now select DCOM98 and then go down the list installing all the programs on the list, obvioulsy only do internet explorer in your language, the reason we have left the Arial font out is because the  link to this is dead, but we will sort this later. Just click next and ok on everything, im sure you know how window installers work.

Ok so we have finished the first list, hit the main menu button to get us back to the start.

next click install windows system software then click ok

again install everything thats in the list from top to bottom in your own language, and install visual basic 5 & 6

ok, so now we gotta sort out theese fonts as the links that winetools uses to retrieve them is dead, so click main menu followed by exit to leave winetools

now then back to our friend the terminal
ok so first we need to make and move to the directory where winetools would have downloaded the fonts

```
mkdir ~/winetools/fonts
cd ~/winetools/fonts
```

you might get an error saying the file exsits, if you do don't worry just continue

Next we download the fonts from a link that is still around at the time of writing this, you might want to copy and paste this one into your terminal

```
wget http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe && wget http://kent.dl.sourceforge.net/sourceforge/corefonts/arial32.exe && wget http://kent.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe &&  wget http://kent.dl.sourceforge.net/sourceforge/corefonts/comic32.exe &&  wget http://kent.dl.sourceforge.net/sourceforge/corefonts/courie32.exe &&  wget http://kent.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe &&  wget http://kent.dl.sourceforge.net/sourceforge/corefonts/impact32.exe &&  wget http://kent.dl.sourceforge.net/sourceforge/corefonts/times32.exe &&  wget http://kent.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe &&  wget http://kent.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe &&  wget http://kent.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe
```

Ok, so we now have the fonts downloaded, next back to winetools to install them ;)

```
wt
```

Select base setup again then install true type font arial

Next main menu then select Install Microsoft true type corefonts, yet again go all the way down the list until you have installed all the fonts.

done that, so main menu and exit winetools ;)

Ok so we should now have a working wine, with internet explorer installed and windows media player 6 ;) hopefully :s

we should be able to start Internet Explorer with the following

```
 wine "/home/USERNAME/.wine/c/Program Files/Internet Explorer/IEXPLORE.EXE"
```

Dont forget to change USERNAME to your own username

With any luck your using internet explorer now :)

although we dont want to have to write this in everytime we want to start internet explorer, so right click the desktop and create a launcher and paste the previous code in there for a desktop shortcut, or make a menu shortcut which ever you prefer.

Here is the code for Outlook and Windows Media Player

```
wine "/home/USERNAME/.wine/c/Program Files/Outlook Express/msimn.exe"
```

and

```
 wine "/home/USERNAME/.wine/c/Program Files/Windows Media Player/mplayer2.exe"
```

and really thats about it, you can also navigate using your file browser and double click .exe files and wine will launch them, like installers for programs and so on, then its just a case of finding the .exe that starts the program and making your custom launcher for it,  your wine c: should always be found in /home/USERNAME/.wine/c. As long as know a bit about the windows file layout you should have no problem in finding them, always remember when creating your launchers that linux is case sensitive, so dont forget the caps.

Two last things to do

Firstly updating wine 0.95 to the latest version, remember we had to use 0.95 because internet explorer will not install on newer versions, although this maybe fixed now. There is no need to panic though, we just add a wine repository to our sources.list like this.

```
sudo gedit /etc/apt/sources.list
```

then add this line to the bottom of the file

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/



then save your sources.list and run the following in terminal to update your wine installation

```
sudo apt-get update
sudo apt-get upgrade
```

This should update wine to the latest version released by wineHQ, and will always be updated with the rest of your updates when a new version is released, Good hey

The second thing to do is to tell you about the winecfg command

```
winecfg
```

This little panel allows you to change the default wine settings, like which windows version to try to act as, and what builtin and native dll's to use, I would suggest leaving the global settings to windows98 as this seems to work best, but you can change the windows version for individual .exe's if a program only works on a certain version of windows, if a program dosen't quite work right this is the place to go, although the full usage of winecfg is a bit beyond the scope of this howto, you should get familiar with it quite soon

If you have problems with a certain program i find it always pays to just put in a google search "program name winehq" and you will usually find the program in the winehq database and find out what success people have had at getting the program to work and what they did to achieve it, very helpfull

One last point, if you use any programs that reside in the windows system tray then the system tray icons do not show up, a workaround is to open up a kde application that uses a tray icon and then the windows tray icons will appear, i.e i have amarok start when gnome starts, kalarm is a good one to use if you dont use amarok, even after you quit your kde program the windows icons will remain.  I believe this shouldn't be a problem for KDE users.

Anyway hope this was some help to a least one person out there, and I will probably add a MSN Messenger HOWTO this as soon as i get the time, let me know how you get on, In the meantime happy wineing :)

---

### Post by FredSambo on 2006-06-11
it looks like you have wine configured to emulate windows NT, as opposed to 98.  i think you can change it to win98 in winecfg and then install DCOM98 in winetools.

---

### Post by shuttleworthwannabe on 2006-06-11
I did set the winecfg to windows 98, and applied changes, but the chnages do not stick.


When I ran winecfg this is the error I got (I selected YES to the debug..), but the terminal was full of error messages.

---

### Post by nir78 on 2006-06-13
I tried over and over to use this guide on dapper with no success (while in breezy it worked like a charm!)

I keep getting stuck in the point where I need to install the winetools:
```
nir@main-storage:~/winetools-0.9jo-III$ sudo ./install
Version: winetools-0.9
Release: 0.9
Installing WineTools to /usr/local/winetools...
[B]ln: creating symbolic link `/usr/local/bin/wt' to `/usr/local/winetools/wt0.9jo' : No such file or directory
ln: creating symbolic link `/usr/local/bin/winetools' to `/usr/local/winetools/w t0.9jo': No such file or directory
ln: creating symbolic link `/usr/local/bin/findwine' to `/usr/local/winetools/fi ndwine': No such file or directory[/B]
Installing translations...
Installed translations for de_DE@euro to /usr/local/share/locale/de_DE@euro/LC_M ESSAGES/wt0.9.mo
Installed translations for es to /usr/local/share/locale/es/LC_MESSAGES/wt0.9.mo
Installed translations for fr to /usr/local/share/locale/fr/LC_MESSAGES/wt0.9.mo
Installed translations for nb to /usr/local/share/locale/nb/LC_MESSAGES/wt0.9.mo
Installed translations for pt_BR to /usr/local/share/locale/pt_BR/LC_MESSAGES/wt 0.9.mo
Start WineTools as *normal* user with "wt". Don't use as root!
nir@main-storage:~/winetools-0.9jo-III$ wt
bash: wt: command not found

```

Any idea guys?? what am I doing wrong ??

Nir

---

### Post by eqisow on 2006-06-14
nir78, the best advice I can offer is to forget winetools and (no offense intended) this howto altoether. Instead, try the [Wine wiki]("http://wiki.ubuntu.com/Wine").

---

### Post by nir78 on 2006-06-14
[QUOTE=eqisow]nir78, the best advice I can offer is to forget winetools and (no offense intended) this howto altoether. Instead, try the [Wine wiki]("http://wiki.ubuntu.com/Wine").[/QUOTE]
Hey eqisow, installing wine is the easiest thing :D but I am just not able to install the explorer! I need for a site that does not work with FireFox and it always stops in the middle of the installation! I was hoping winetools will solve this issue for me...

Nir

---

### Post by nbv4 on 2006-06-14
Winetools is telling me I do not have that dependancy installed, but I indeed have it installed:

```

**priestc@priestc-desktop:~$** wt
detecting Wine version... done.
Drive C: is /home/priestc/.wine/drive_c
Wine 0.9.15
wine is executed as wine
Parameters are --noexit
Browser is /usr/bin/firefox.
WINEVER is "0.9.15".
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
Calls to wine are executed as  "wine".
Config is /home/priestc/.wine/winetools.log.
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
**priestc@priestc-desktop:~$** sudo apt-get install libgtk1.2
Reading package lists... Done
Building dependency tree... Done
libgtk1.2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Wat on earth do I do?

It may be worth mentioning I'm using the amd64 version of ubuntu and I had to use the trick listed [here](http://ubuntuforums.org/showthread.php?t=185557) to get it to install.

---

### Post by Servus on 2006-06-15
I had the same problem. Try installing libgtk1.2.
Here you find the .deb

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=libgtk1.2](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=libgtk1.2)

then install it with dpkg -i ...

Bye

---

### Post by selop on 2006-06-17
i have this problem...

anyone can help  me? :-( :-( 

[IMG]http://freewebs.com/t1t4n2/mirc2.png[/IMG]

---

### Post by babysnakes on 2006-06-20
Hi

thanks for this howto.

unfortunately when I tried this on dapper (2.6.15-25-686), it completely froze my computer. I tried it twice. on the first try my computer rebooted suddenly, and on the second try it completely froze (not even sysrq shortcuts helped).

any ideas?

Thanks

Haim

---

### Post by thunderduck3141 on 2006-06-20
When i tried to install IE 6 (winetools way) it goes fine until it hits flash, then it fails and things just fall apart after that.
any suggestions?

---

### Post by thunderduck3141 on 2006-06-20
yeah, u need to do this

sudo apt-get install libgtk2.0-0

i had the same prob

---

### Post by babysnakes on 2006-06-20
I can't seem to delete my post so I'll just apologize:

I didn't see that your reply wasn't for my message :)

just ignore it.

Bye

[QUOTE=thunderduck3141]yeah, u need to do this

sudo apt-get install libgtk2.0-0

i had the same prob[/QUOTE]
Hi

I've already have it installed:
ii  libgtk2.0-0    2.8.18-0ubuntu The GTK+ graphical user interface library

do I need to uninstall libgtk1.2?

thanx

---

### Post by thunderduck3141 on 2006-06-21
i have 2.0-0 installed and wine (except IE) is vorking okay
prob woth a shot though

---

### Post by miller0521 on 2006-06-23
I am new to Ubuntu, and I am trying to get Wine to work, it will open the program that I want it to, however it will not allow me to maximize or minimize the application. And it will not show up on the gnome-panel. It worked just fine on Mepis, and also on Kubuntu, is there something wrong with Gnome when it comes to using Wine? 

Thanks, 
Mitch

---

### Post by bodhi.zazen on 2006-06-23
miller0521

Wine is an always changing entity. Each version of wine has it's own seemingly unique issues/qwerks.

first, are you useing the same version of wine between distros?

second, each wine will have more or less problems with each application.

third, using the same hardware, wine version, wine configuration, and application each application interact with each WM uniquely.

With that preamble, I have had the best results with fluxbox and/or KDE. Mixed results with GNOME or XFCE. Have not tested wine applications extensively in Enlightenment. No experience with any other WM.

Try KUBUNTU.

---

### Post by miller0521 on 2006-06-24
I figured it was something with Gnome. So I got rid of Ubuntu and reinstalled Mepis... Mepis seems to me to run KDE better than Kubuntu, has a less bloated feeling, but they are both good, I just prefer Mepis I think. And wine works perfectly for me under Mepis/KDE. 

Mitch

---

### Post by anony on 2006-06-24
Ok, I went throug most of this then i get a wine server alert poup:  There is still a wineserver running after 600 seconds to kill it type wineserver in the consol
i go into terminal and see it saying waiting for wineserver to exit...
I waited 20 minutes and nothing happened so I typed wineserver
No result, any ideas its hanging there and not closing.

---

### Post by bodhi.zazen on 2006-06-25
In a terminal type

  wineserver -k

This will end your wine session but you can re-start immediatly

regards

---

### Post by rai4shu2 on 2006-06-26
Funny, but I don't think anyone has mentioned this:

In later versions of Wine (0.9.12 and newer IIRC), the "emulated desktop" option no longer works for specific applications in winecfg. If you want an "emulated desktop" for a particular application, you have to run it like this:

```
wine explorer /desktop=AppName,800x600 AppName.exe
```

---

### Post by bodhi.zazen on 2006-06-26
rai4shu2:

I can not speak for others but this has not been my experience with wine.

In fact I have had just the opposite. Most of my aps only run in the wine desktop. I have no problem configuring the desktop in winecfg.

Must be in the way wine is configured post-install (wine tools vs sidenet) [I use sedenet].

Lastly, what application(s) are your referring to? You are implying some applications do not have this problem.

In my experience with wine I have always had application specific qwerks that change with each version of wine. WineHQ calls this phenomena "regression".

Check the apps database at wineHQ:

[http://appdb.winehq.org/](http://appdb.winehq.org/)

Use the "search" box on the Left.

---

### Post by rai4shu2 on 2006-06-27
No offense bodhi.zazen, but this info comes straight from the devs:

```
Per-application desktop mode settings are no longer supported. Apps can be launched in a specific desktop window by using:

      explorer /desktop=name[,widthxheight] app.exe [args] 

If the named desktop already exists the app is launched inside it. The default desktop is cleverly named "default".
```

[http://www.winehq.org/pipermail/wine-cvs/2006-March/021472.html](http://www.winehq.org/pipermail/wine-cvs/2006-March/021472.html)
[http://www.winehq.com/pipermail/wine-users/2006-May/021652.html](http://www.winehq.com/pipermail/wine-users/2006-May/021652.html)
[http://winehq.org/?issue=310#Major%20Changes%20to%20Desktop%20Mode](http://winehq.org/?issue=310#Major%20Changes%20to%20Desktop%20Mode)

---

### Post by SteveHoffmanUK on 2006-07-13
Great NOWTO, but I didn't seem to succeed in installing wine.

I used Automatix to install wine, then picked up the HOWTO. During installation I got these error messages:

```
An error or exception occurred while calling the function "Dllinstall" in c:\windows\system32\chdocvw.dll [OK]
An error or exception occurred while calling the function "Dllinstall" in c:\windows\system32\chdocvw.dll [OK]
An error occurred loading 'c:\windows\system32\initpki.dll. The file may not have been installed or it has been corrupted.
An error occurred loading 'c:\windows\system32\initpki.dll. The file may not have been installed or it has been corrupted.
```

Then it asked me if it should remove the existing Fake Windows drive. It didn't seem to do anything if I said 'No', so I finally said 'Yes', then got back into the loop of installing the different Windows programs and fonts.

Now when I run winecfg to add an application, I find the .exe file on my CD, click on it, and it appears in the list of applications, but it doesn't install.

Can someone tell me what's happened, why my app won't install and what I need to do to get wine working?

Many thanks

---

### Post by bodhi.zazen on 2006-07-16
SteveHoffmanUK;

since no one else has answered I will try. I am far from an expert on wine, as you can see from some of my previous posts.

I would need more information to give you a detailed answer. What version of wine? What configuration program? What software do you want to run on wine? What how-to are you following?

In a nut shell there are 3 steps with wine. Installation of wine, configuration of wine, and installation of software into wine. The configuration of wine creates your fake c drive. You can have more then 1 fake c drive at a time, but you can use only 1 (as far as I know) when running wine (wineserver).

(Wine) windows uses C:\ as the "root" directory (Linux uses "/"). Wine creates a file which is held out to wine as C:\. this file is usually in your Home directory and is named when you configure wine. I personally use .wine/c and do not know if you use this or another. The .wine/c has the advantage in that .wine/dosdevices can hold symbolic links (to say your CD-ROM) and remain in a single hidden file in your home directory (.wine).

I back up .wine after a fresh install and with any significant changes, like installation of a critical program or prior to update of wine.

SEE ABOVE COMMENTS regarding installation/configuration/configuration of wine. You need to start with the exact versions of wine, your wine configuration program, and software outlined in whatever how-to you are following. wine can typically be updated after an install of software, but not always.

I presume the error messages occurred when you were installing an application.

At any rate, when you "remove the existing Fake Windows drive" you deleted your configuration of wine (thus winecfg will no longer run as winecfg "fine tunes" your wine configuration).

As far as I can determine wine is still installed on your system.

Just re-run your configuration (?automatrix). I am not familiar with automatrix and do not know what application you are running. Look at the automix documentation to see how it configures your fake c drive and wineHQ for configuration of your application.

PS your error messages look like typical of wine. Use winecfg to further configure your set up. Either:

1. If you have a valid windows liscence copy
 
     c:\windows\system32\initpki.dll

to

     /home/Fake_c_drive/windows/system32/

In my case:

     /home/User_name/.wine/c/windows/system32

2. Wine HQ should give explicit directions to over ride the dll.

3. If there are no instructions on winehq, and you do not have explicit instructions, you are on your own. Otherewise you will need to do some reading and follow the directions exactly, to the letter.

I was able to get wine running an critical application for me and used a different "how to" to configure wine.

Welcome to wine.

---

### Post by oc3lot on 2006-07-16
Thanks SO much for the HOWTO, however, I'm running into a bit of a problem.. 

When trying to run winetools, I get a whole bunch of Permission Denied errors in terminal. This prevents me from even getting so far as installing the DCOM98. 

Any suggestions?

---

### Post by bruenig on 2006-07-17
Using Dapper Followed you directly. Everything worked but then upon wine upgrade, internet explorer and the others broke.

---

### Post by balak on 2006-07-18
MANY THANKS for the howto!

I was breaking my head trying to install ie6 with the newer versions (0.9.9 and 0.9.12) of wine (you get 0.9.9 by synaptic on dapper) - wasted a whole afternoon with that. I tried both winetools and wine-config-sidenet and directly too but couldn't get ie6 installed.

I don't understand why they upgrade the s/w if it breaks existing stuff :(
Finally got it working with the version mentioned in your webpage. Thanks a lot. You saved my day.

I was able to successfully install office 2000 (my target). 

To add to other posters on this thread and other similar threads, msoffice is required only for compatibility in a corporate environment :(
I have managed with ubuntu on my work desktop and work laptop since Oct. 05. But not having msoffice was taking its toll..

---

### Post by Dazza on 2006-07-18
I'm in Dapper Drake and have succesfully installed Wine. I have a question.

How do I install Windows Media Player 11, or other programs, using Wine? I have no clue. THank you.

---

### Post by bodhi.zazen on 2006-07-18
Dazza: This is a complex question, much like the meaning of life.

Start here for advice on detailed "how to" configure and run applications in wine:

[http://www.winehq.com/](http://www.winehq.com/)

The basic steps are:

1. Install wine.

2. Configure wine (this how-to is only 1 way to configure wine, there are others). Various configurations of wine work better with individual applications (again see wineHQ for advice).

I assume you have done this.

Next install your programs. See WineHQ and search for detailed instructions on each application.

The general steps are:

1. In a terminal type:
     wine Path_to_.exe_file/installer.exe

     For example, assuming your program is on a CDROM

     Mount the CDROM
     wine /media/cdrom/setup.exe

Did I mention wineHQ?



Question (Better answer): Why not use Linux native programs?

There is more then likely at least 1 Linux native program that will serve your needs. If you name a  windows program (music for example) I can give you several options (XMMS for music).

In general, running windows native programs under wine is more difficult for a new user to linux (newbie) then learning (installing) Linux native programs. Linux native programs are then easier to maintain. Wine is, in my opinion, Alpha software.

You could always consider Crossover Office or cedega (Cedega is for games)

[http://www.codeweavers.com/](http://www.codeweavers.com/)
[http://www.transgaming.com/](http://www.transgaming.com/)


For good starting advice (on Linux native programs) see:

[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

If you name a windows program you need, I can likely name a Linux equivalent or at least get you started.

In general wine can be very buggy and emulates windows 98 best.

As a recovering windows'aholic I suggest you look into Linux native applications before you embark on wine configuration.

---

### Post by El Guapo on 2006-07-19
> **gazj said:**
> I agree i use ies4linux aswell, but i like internet explorer 6 in my wine installation aswell, as many programs, rely on aspects of internet explorer to work, my girlfriend for one cannot manage without msn messenger, (gaims fine for me) msn messenger needs ie6 to work, thats why its handy to have it in wine too :)

good point well made if all you want is internet explorer though :)

I installed wine and ran IE6 according to this description and it worked.  However some IE only sites did not work well.  So I tried the above mentioned ies4linux and the IE only sites worked fine, except that it doesn't look like all of the fonts I installed using winetools are there.  Does the winetools actually install the fonts to the wine system or just to its own system?

My main reason for wanting to use IE is for my wife.  I finally convinced her to try linux, but she is a member of an MSN board that is incompatible with Firefox, so I need IE6.  Having all the fonts installed would be a big help...

---

### Post by bodhi.zazen on 2006-07-19
El Guapo:

Wine uses a fonts directory on your fake_c drive. On my system this is under ~/.wine/c/windows/fonts, but your exact location may vary.

Linux uses several locations for fonts.

either copy your desired to your fonts file on your fake_c/windows/fonts or create a symbolic link.

for example I keep a few fonts in ~/.fonts.

In ~/.wine/c/windows/fonts I made a symbolic link to ~/.fonts.

Example:
cd ~/.wine/c/windows/fonts
ln -s ~/.fonts/name_of_font name_of_font

Note the space between "name_of_font" and "name_of_font".

---

### Post by harryhoudini66 on 2006-07-19
I cannot get mine to work. When I try to install DCOM98 I get the error below. I cannot install anything else either because it all depends on DCOM98.

---

### Post by harryhoudini66 on 2006-07-19
I have uninstalled Wine quite a few times and it looks like it is not completely removed. Each time I go back, the config files is the same as before.

---

### Post by wana10 on 2006-07-19
> **harryhoudini66 said:**
> I cannot get mine to work. When I try to install DCOM98 I get the error below. I cannot install anything else either because it all depends on DCOM98.

run winecfg in terminal and make sure that you have wine set to win98...if you do then i have no idea how to help

---

### Post by harryhoudini66 on 2006-07-19
Thanx. I did have it set to 98 and it still did not work. I decided to uninstall and try again. That was also hard. After some research I ended up removing it completely with 

rm ~/.wine -Rfv


I will see how it works now.

---

### Post by harryhoudini66 on 2006-07-19
Looks like it worked. I am installing BF2 as we speak.

---

### Post by Qwerty_ on 2006-07-20
How can i install and older version of wine?

---

### Post by bodhi.zazen on 2006-07-20
Since no one else has answered:

1. remove your current version of wine and fake c drive.

2. find the desired version of wine.

3. download the wine.version.deb package

4. use dpkg at the command line.

cd /directory_with_wine.version.deb
dpkg -i wine.version.deb

see also [http://linuxreviews.org/man/dpkg/](http://linuxreviews.org/man/dpkg/)

5. if doing a dist-upgrade do not upgrade wine.

---

### Post by mbrang00 on 2006-07-22
Thanks for the How to, it was going smooth for me untill i ran into a bit of a snag, I got though all of the installs with the exception for one. 
MDAC 2.8 and Jet 4.0 SP8 in English.

Here is the error i recieved:

This software requires microsoft internet explorer 4.01 sp2 or greater. Please exit setup and install the latest microsoft explorer..

Im sure I missed somthing, but I dont know what. All I had to do was go down the list and install the stuff...How did I screw it up?


Please Help,
Mike

---

### Post by greythorne on 2006-07-22
> **gazj said:**
> *** UPDATE 19-07-2006 (UK DATE SYSTEM :) ) This howto was originally written for breezy badger, I can now confirm it also works on dapper drake

After a lot of searching here there and every where I finally know how to get wine working on my machine anyway, every time without fail, and as there is a lack of how to's on wine, I thought i would give the Ubuntu community something back. This is my first how to, so don't be to harsh if it dosen't work for you.

First we get the wine0.95.deb from winehq [http://kent.dl.sourceforge.net/sourceforge/wine/wine_0.9.5-winehq-1_i386.deb]("http://kent.dl.sourceforge.net/sourceforge/wine/wine_0.9.5-winehq-1_i386.deb")

or if you want to open a terminal (alt+F2 then type gnome-terminal then enter) to download it use this command

```
 wget http://kent.dl.sourceforge.net/sourceforge/wine/wine_0.9.5-winehq-1_i386.deb
```

In case your wondering why we are not downloading the latest version of wine its because internet explorer install breaks on newer versions and you will probably need internet explorer to get other programs working, but we will update wine after, so don't worry

Right so we got our Wine .deb so lets unpackage it in our terminal dont forget to change directory to where you downloaded wine (if you used the above command you should already be there)

```
sudo dpkg -i wine*.deb
```

ok, so we no have wine, but how do i use it, set up a C:/ D:/ etc i hear you cry, let alone install anything, well here come the great little app called winetools ;)

I have now learned that winetools has at least one dependancy, pointed out by replies on this forum, here is the command for installing it (added 1st April 06, after 12 not a april fool btw)

```
sudo apt-get install libgtk1.2
```

wine tools can be downloaded here [http://ds80-237-203-29.dedicated.hosteurope.de/wt/winetools-0.9jo-III.tar.gz]("http://ds80-237-203-29.dedicated.hosteurope.de/wt/winetools-0.9jo-III.tar.gz")

or if your still with me in the good old terminal you can use this command

```
wget http://ds80-237-203-29.dedicated.hosteurope.de/wt/winetools-0.9jo-III.tar.gz
```

ok, so we got this great tool no we need to unpack it

```
tar -xf winetools*
```

and install it

```
cd winetools*
sudo ./install
```

Done :) so lets start this wonderfull tool with this

```
wt
```

you will get loads of messages popup about not being configured etc, just keep clicking ok oh and that you should also own a copy of windows to use some of these tools. Yeah Yeah on with the plot.

You should finally get to a menu

So first we go for base setup, then create a fake windows drive
Next winetools will find your cdrom for you so it can set it up for wine
Followed by a username and organization, I Just leave theese as is
After a few fake windows restarts later we are told fake drive completed. Yippee

We are back to the base setup menu, now select DCOM98 and then go down the list installing all the programs on the list, obvioulsy only do internet explorer in your language, the reason we have left the Arial font out is because the  link to this is dead, but we will sort this later. Just click next and ok on everything, im sure you know how window installers work.

Ok so we have finished the first list, hit the main menu button to get us back to the start.

next click install windows system software then click ok

again install everything thats in the list from top to bottom in your own language, and install visual basic 5 & 6

ok, so now we gotta sort out theese fonts as the links that winetools uses to retrieve them is dead, so click main menu followed by exit to leave winetools

now then back to our friend the terminal
ok so first we need to make and move to the directory where winetools would have downloaded the fonts

```
mkdir ~/winetools/fonts
cd ~/winetools/fonts
```

you might get an error saying the file exsits, if you do don't worry just continue

Next we download the fonts from a link that is still around at the time of writing this, you might want to copy and paste this one into your terminal

```
wget http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe && wget http://kent.dl.sourceforge.net/sourceforge/corefonts/arial32.exe && wget http://kent.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe &&  wget http://kent.dl.sourceforge.net/sourceforge/corefonts/comic32.exe &&  wget http://kent.dl.sourceforge.net/sourceforge/corefonts/courie32.exe &&  wget http://kent.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe &&  wget http://kent.dl.sourceforge.net/sourceforge/corefonts/impact32.exe &&  wget http://kent.dl.sourceforge.net/sourceforge/corefonts/times32.exe &&  wget http://kent.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe &&  wget http://kent.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe &&  wget http://kent.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe
```

Ok, so we now have the fonts downloaded, next back to winetools to install them ;)

```
wt
```

Select base setup again then install true type font arial

Next main menu then select Install Microsoft true type corefonts, yet again go all the way down the list until you have installed all the fonts.

done that, so main menu and exit winetools ;)

Ok so we should now have a working wine, with internet explorer installed and windows media player 6 ;) hopefully :s

we should be able to start Internet Explorer with the following

```
 wine "/home/USERNAME/.wine/c/Program Files/Internet Explorer/IEXPLORE.EXE"
```

Dont forget to change USERNAME to your own username

With any luck your using internet explorer now :)

although we dont want to have to write this in everytime we want to start internet explorer, so right click the desktop and create a launcher and paste the previous code in there for a desktop shortcut, or make a menu shortcut which ever you prefer.

Here is the code for Outlook and Windows Media Player

```
wine "/home/USERNAME/.wine/c/Program Files/Outlook Express/msimn.exe"
```

and

```
 wine "/home/USERNAME/.wine/c/Program Files/Windows Media Player/mplayer2.exe"
```

and really thats about it, you can also navigate using your file browser and double click .exe files and wine will launch them, like installers for programs and so on, then its just a case of finding the .exe that starts the program and making your custom launcher for it,  your wine c: should always be found in /home/USERNAME/.wine/c. As long as know a bit about the windows file layout you should have no problem in finding them, always remember when creating your launchers that linux is case sensitive, so dont forget the caps.

Two last things to do

Firstly updating wine 0.95 to the latest version, remember we had to use 0.95 because internet explorer will not install on newer versions, although this maybe fixed now. There is no need to panic though, we just add a wine repository to our sources.list like this.

```
sudo gedit /etc/apt/sources.list
```

then add this line to the bottom of the file

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/



then save your sources.list and run the following in terminal to update your wine installation

```
sudo apt-get update
sudo apt-get upgrade
```

This should update wine to the latest version released by wineHQ, and will always be updated with the rest of your updates when a new version is released, Good hey

The second thing to do is to tell you about the winecfg command

```
winecfg
```

This little panel allows you to change the default wine settings, like which windows version to try to act as, and what builtin and native dll's to use, I would suggest leaving the global settings to windows98 as this seems to work best, but you can change the windows version for individual .exe's if a program only works on a certain version of windows, if a program dosen't quite work right this is the place to go, although the full usage of winecfg is a bit beyond the scope of this howto, you should get familiar with it quite soon

If you have problems with a certain program i find it always pays to just put in a google search "program name winehq" and you will usually find the program in the winehq database and find out what success people have had at getting the program to work and what they did to achieve it, very helpfull

One last point, if you use any programs that reside in the windows system tray then the system tray icons do not show up, a workaround is to open up a kde application that uses a tray icon and then the windows tray icons will appear, i.e i have amarok start when gnome starts, kalarm is a good one to use if you dont use amarok, even after you quit your kde program the windows icons will remain.  I believe this shouldn't be a problem for KDE users.

Anyway hope this was some help to a least one person out there, and I will probably add a MSN Messenger HOWTO this as soon as i get the time, let me know how you get on, In the meantime happy wineing :)


I would really appreciate if you can put up a Howto for MSN Messenger or the new Windows Live Messenger. That would be great.

Thank you.

---

### Post by bisconer on 2006-07-25
I allready have a version of winetools that wont work with the older version of wine.  So how do i unistall it?

---

### Post by jrjr on 2006-07-27
> **bruenig said:**
> Using Dapper Followed you directly. Everything worked but then upon wine upgrade, internet explorer and the others broke.

This happened to me as well. Or at least IE and OE quit working. They were working find before I did the updates

sudo apt-get update
sudo apt-get upgrade

I suppose if I commented out

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

in the sources file then it would not update... is that correct?

I was able to install Office 2000 after the update. Word, Excel worked good but Access would not. Access is what I need to get working as I do some db design work with it. Open Office is not compatible with Access databases, or at least I havent had any luck with it.. it wont even open them. If it did I would not need wine. 

I still have dual boot to fall back on! I installed wine twice. The first time I did the updates before trying it. IE was broke so I uninstalled and installed again. Since then I have reinstalled the OS so this wine will be a clean one again.

I'm not sure if I should follow the how to and not update, or go for the latest version and hope I can get it all working with the newer release. 

hmmmmmmmmmmm

---

### Post by bodhi.zazen on 2006-07-27
bisconer:

I do not use winetools but if I recall correctly it is not "installed". Just delete the old winetools directory.

Winetools is a script/program that configures your fake c drive. I use ~/.wine/c with a ~/.wine/dosdevices. If you rename or delete your old fake c drive and create a new one with the new winetools you should be fine.





jrjr

I have similar problems with my use of wine. My advice is:

1. Once wine is working, do not update. If wine is working there is no need to update unless ...

2. The best source of information re: wine is wineHQ. Look up your application Access in the database:

[http://www.winehq.com/](http://www.winehq.com/)
[http://appdb.winehq.org/](http://appdb.winehq.org/) -> enter your application in the search box on the Left.

viola: [http://appdb.winehq.org/appview.php?iAppId=12](http://appdb.winehq.org/appview.php?iAppId=12)

Follow their advice to the letter re versions of wine and update. If they advise an update of wine, go for it. Otherwise do not.

Since I a dependent on wine:
1. Back up your working fake c drive. Often.
2. I have a separate partition for "testing". I test the new wine before I upgrade wine on my mission critical OS. 

If all else fails:

1. Uninstall wine.
2. Re-install an older, known working copy of wine.
3. Restore your fake c drive from backup. You DO NOT need to re-install software (to wine/fake c drive)!!

Good luck.

---

### Post by lupin492 on 2006-07-28
gazj: I don't have the words to THANK YOU.  I think many, many people in the community feels the same way.  Your work on this is VERY appreciated.
Regards!

---

### Post by iammeagain on 2006-08-06
Great How TO! just what i needed!

---

### Post by favad on 2006-08-07
No doubt it is a Great "How To" for newbies like me, but there were a few problems when I tried to run wine for the first time using wt command. Here's the log, I would be glad if someone could please help me fix things up from here.

[B]favad@ubuntu:~/winetools-0.9jo-III$ wt
no suitable Wine directory found...
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
Wine 0.9.5
wine is executed as wine
Parameters are --noexit
Wine is not configured yet!
Browser is /usr/bin/firefox.
WINEVER is "0.9.5".
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
Calls to wine are executed as  "wine".
Config is /home/favad/.wine/winetools.log.
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
[/B]

favad

---

### Post by frogotronic on 2006-08-10
> **cbudden said:**
> I already have wine installed, aswell as a few programs.  Am I able to install wine tools without messing up my current wine installation?

Hi,

  Did you ever determine how to uninstall wine?  I used the Synaptic Package Manager.  BUT, all the IE6 and WMP6 and other programs are still there How can I uninstall those?

---

### Post by frogotronic on 2006-08-11
> **gazj said:**
> *** UPDATE 19-07-2006 (UK DATE SYSTEM :) ) This howto was originally written for breezy badger, I can now confirm it also works on dapper drake

After a lot of searching here there and every where I finally know how to get wine working on my machine anyway, every time without fail, and as there is a lack of how to's on wine, I thought i would give the Ubuntu community something back. This is my first how to, so don't be to harsh if it dosen't work for you.

First we get the wine0.95.deb from winehq [http://kent.dl.sourceforge.net/sourceforge/wine/wine_0.9.5-winehq-1_i386.deb]("http://kent.dl.sourceforge.net/sourceforge/wine/wine_0.9.5-winehq-1_i386.deb")

or if you want to open a terminal (alt+F2 then type gnome-terminal then enter) to download it use this command

```
 wget http://kent.dl.sourceforge.net/sourceforge/wine/wine_0.9.5-winehq-1_i386.deb
```

In case your wondering why we are not downloading the latest version of wine its because internet explorer install breaks on newer versions and you will probably need internet explorer to get other programs working, but we will update wine after, so don't worry

Right so we got our Wine .deb so lets unpackage it in our terminal dont forget to change directory to where you downloaded wine (if you used the above command you should already be there)

```
sudo dpkg -i wine*.deb
```

ok, so we no have wine, but how do i use it, set up a C:/ D:/ etc i hear you cry, let alone install anything, well here come the great little app called winetools ;)

I have now learned that winetools has at least one dependancy, pointed out by replies on this forum, here is the command for installing it (added 1st April 06, after 12 not a april fool btw)

```
sudo apt-get install libgtk1.2
```

wine tools can be downloaded here [http://ds80-237-203-29.dedicated.hosteurope.de/wt/winetools-0.9jo-III.tar.gz]("http://ds80-237-203-29.dedicated.hosteurope.de/wt/winetools-0.9jo-III.tar.gz")

or if your still with me in the good old terminal you can use this command

```
wget http://ds80-237-203-29.dedicated.hosteurope.de/wt/winetools-0.9jo-III.tar.gz
```

ok, so we got this great tool no we need to unpack it

```
tar -xf winetools*
```

and install it

```
cd winetools*
sudo ./install
```

Done :) so lets start this wonderfull tool with this

```
wt
```

you will get loads of messages popup about not being configured etc, just keep clicking ok oh and that you should also own a copy of windows to use some of these tools. Yeah Yeah on with the plot.

You should finally get to a menu

So first we go for base setup, then create a fake windows drive
Next winetools will find your cdrom for you so it can set it up for wine
Followed by a username and organization, I Just leave theese as is
After a few fake windows restarts later we are told fake drive completed. Yippee

We are back to the base setup menu, now select DCOM98 and then go down the list installing all the programs on the list, obvioulsy only do internet explorer in your language, the reason we have left the Arial font out is because the  link to this is dead, but we will sort this later. Just click next and ok on everything, im sure you know how window installers work.

Ok so we have finished the first list, hit the main menu button to get us back to the start.

next click install windows system software then click ok

again install everything thats in the list from top to bottom in your own language, and install visual basic 5 & 6

ok, so now we gotta sort out theese fonts as the links that winetools uses to retrieve them is dead, so click main menu followed by exit to leave winetools

now then back to our friend the terminal
ok so first we need to make and move to the directory where winetools would have downloaded the fonts

```
mkdir ~/winetools/fonts
cd ~/winetools/fonts
```

you might get an error saying the file exsits, if you do don't worry just continue

Next we download the fonts from a link that is still around at the time of writing this, you might want to copy and paste this one into your terminal

```
wget http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe && wget http://kent.dl.sourceforge.net/sourceforge/corefonts/arial32.exe && wget http://kent.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe &&  wget http://kent.dl.sourceforge.net/sourceforge/corefonts/comic32.exe &&  wget http://kent.dl.sourceforge.net/sourceforge/corefonts/courie32.exe &&  wget http://kent.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe &&  wget http://kent.dl.sourceforge.net/sourceforge/corefonts/impact32.exe &&  wget http://kent.dl.sourceforge.net/sourceforge/corefonts/times32.exe &&  wget http://kent.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe &&  wget http://kent.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe &&  wget http://kent.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe
```

Ok, so we now have the fonts downloaded, next back to winetools to install them ;)

```
wt
```

Select base setup again then install true type font arial

Next main menu then select Install Microsoft true type corefonts, yet again go all the way down the list until you have installed all the fonts.

done that, so main menu and exit winetools ;)

Ok so we should now have a working wine, with internet explorer installed and windows media player 6 ;) hopefully :s

we should be able to start Internet Explorer with the following

```
 wine "/home/USERNAME/.wine/c/Program Files/Internet Explorer/IEXPLORE.EXE"
```

Dont forget to change USERNAME to your own username

With any luck your using internet explorer now :)

although we dont want to have to write this in everytime we want to start internet explorer, so right click the desktop and create a launcher and paste the previous code in there for a desktop shortcut, or make a menu shortcut which ever you prefer.

Here is the code for Outlook and Windows Media Player

```
wine "/home/USERNAME/.wine/c/Program Files/Outlook Express/msimn.exe"
```

and

```
 wine "/home/USERNAME/.wine/c/Program Files/Windows Media Player/mplayer2.exe"
```

and really thats about it, you can also navigate using your file browser and double click .exe files and wine will launch them, like installers for programs and so on, then its just a case of finding the .exe that starts the program and making your custom launcher for it,  your wine c: should always be found in /home/USERNAME/.wine/c. As long as know a bit about the windows file layout you should have no problem in finding them, always remember when creating your launchers that linux is case sensitive, so dont forget the caps.

Two last things to do

Firstly updating wine 0.95 to the latest version, remember we had to use 0.95 because internet explorer will not install on newer versions, although this maybe fixed now. There is no need to panic though, we just add a wine repository to our sources.list like this.

```
sudo gedit /etc/apt/sources.list
```

then add this line to the bottom of the file

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/



then save your sources.list and run the following in terminal to update your wine installation

```
sudo apt-get update
sudo apt-get upgrade
```

This should update wine to the latest version released by wineHQ, and will always be updated with the rest of your updates when a new version is released, Good hey

The second thing to do is to tell you about the winecfg command

```
winecfg
```

This little panel allows you to change the default wine settings, like which windows version to try to act as, and what builtin and native dll's to use, I would suggest leaving the global settings to windows98 as this seems to work best, but you can change the windows version for individual .exe's if a program only works on a certain version of windows, if a program dosen't quite work right this is the place to go, although the full usage of winecfg is a bit beyond the scope of this howto, you should get familiar with it quite soon

If you have problems with a certain program i find it always pays to just put in a google search "program name winehq" and you will usually find the program in the winehq database and find out what success people have had at getting the program to work and what they did to achieve it, very helpfull

One last point, if you use any programs that reside in the windows system tray then the system tray icons do not show up, a workaround is to open up a kde application that uses a tray icon and then the windows tray icons will appear, i.e i have amarok start when gnome starts, kalarm is a good one to use if you dont use amarok, even after you quit your kde program the windows icons will remain.  I believe this shouldn't be a problem for KDE users.

Anyway hope this was some help to a least one person out there, and I will probably add a MSN Messenger HOWTO this as soon as i get the time, let me know how you get on, In the meantime happy wineing :)


Okay, did everything and IE was working UNTIL I updated wine to 0.9.18 ( the latest version for 6.06.1) and now IE is broken...Any patches/fixes/suggestions, other than completely uninstalling and starting again?

Thanks

---

### Post by Roasted on 2006-08-11
Just curious, all I did was sudo apt-get install wine and evidently it's installed on my system. How does this how-to differ from the thing I did?

---

### Post by true_friend on 2006-08-25
and i have a basic question. i want to run a dictionary. it is a windows software 98,me, xp etc. can i run it under wine.
if yes how to???
i tried to run it in gnome (now on kubuntu) but could not find and option or tool to install program and run it.
so plz guide me to install a custom windows applicaion under wine and then running it.

---

### Post by jason.b.c on 2006-08-25
> **Rizado said:**
> The easiest way to install ie6 is to use [ie4linux.](http://www.tatanka.com.br/ies4linux/)
It's a script that downloads everything that's needed and installs into .ie4linux (by default) instead of .wine
Nothing is done in .wine at all so it can be ran without fear of breaking every other installed app and you'll have a clean .wine for other things.

Hey , I just installed this **ie4linux** thing , But how do i launch it..???

I've tried everything i could think of but to no avail..](*,)

---

### Post by remoir on 2006-08-26
i am using the synaptic package manager to download wine. There's apparently four wine-related packages after i did a SEARCH for WINE. They are as follow: libwine, libwine-dev, wine, wine-dev. Question : Which one should i install ?

---

### Post by true_friend on 2006-08-26
i think libwine and wine alone.
dev mean development files related to developers.

---

### Post by silent_scream on 2006-08-26
this is a great how-to, although I have some problem:
after I give the command "wt" and i choose "Base setup"
and then "Create a Fake Windows drive",

console displays:

```
silent@MetallicA:~/winetools-0.9jo-III$ wt
detecting Wine version... done.
Drive C: is /home/silent/.wine/drive_c
Wine 0
wine is executed as wine
Parameters are --noexit
Browser is /usr/bin/firefox.
WINEVER is "0".
silent@MetallicA:~/winetools-0.9jo-III$ wt
detecting Wine version... done.
Drive C: is /home/silent/.wine/drive_c
Wine 0.9.20
wine is executed as wine
Parameters are --noexit
Browser is /usr/bin/firefox.
WINEVER is "0.9.20".
Calls to wine are executed as  "wine".
Config is /home/silent/.wine/winetools.log.
Choice is Base setup
Choice is Create a Fake Windows drive with checked=F
waiting for wineservers to exit...

```

then every whilea window pops-up that says: 
"There is still a wineserver running after 10 seconds waiting.
On slow computers or while donloading this need not mean 
anything. If you think wine hangs, you may consider killing it
on the console by typing wineserver"

i choose "ok" in that window, and every little while it pops-up again!
so, what should i do???

thnx for your time..!

---

### Post by frogotronic on 2006-08-27
Hello,

  I used winetools and have also used sidenet.  I couldn't get IE6 to install with winetools - it's a bug in the newer versions of wine.  So I installed IE4LINUX to get around that.  If winteools doesn't work, try configuring wine with the sidenet script.

Check out sidenet - it's a script that should solve your problems. 

[http://frankscorner.org/index.php?p=sidenet](http://frankscorner.org/index.php?p=sidenet)

---

### Post by emale07 on 2006-08-29
winetools tries to download the config files mfc40.dll & mfc42.dll from links that are dead when you select to install Microsoft Foundation Classes (MFC).

you can manually download them yourself here:
[http://www.dll-files.com/dllindex/dll-files.shtml?mfc40](http://www.dll-files.com/dllindex/dll-files.shtml?mfc40)
[http://www.dll-files.com/dllindex/dll-files.shtml?mfc42](http://www.dll-files.com/dllindex/dll-files.shtml?mfc42)

When you are done, place them in ./winetools/sys

continue with the setup instructions but skip the install of Microsoft Foundation Classes (MFC).

Yes!  I finally contributed!

---

### Post by feefs on 2006-08-31
thanks for letting me know where to find the mfc40/42 dll's , damp dlldump is dead!! :D

---

### Post by mkquist on 2006-08-31
[http://www.freedownloadscenter.com/Utilities/Required_Files/MFC_DLLs.html\](http://www.freedownloadscenter.com/Utilities/Required_Files/MFC_DLLs.html\)

i dont know, but i just used this and it seemed to take care of it? :confused:

---

### Post by feefs on 2006-09-01
bah upgrading to the latest version of wine over the initial version loaded here breaks it. I suggest you don't apt-upgrade where it tells you too!

---

### Post by Fraoch on 2006-09-03
> **feefs said:**
> bah upgrading to the latest version of wine over the initial version loaded here breaks it. I suggest you don't apt-upgrade where it tells you too!

Yeah, I second that.  Nothing seems to work after upgrading to the latest wine - 0.9.20.

Starting over again.:(  This time I'll leave out installing IE6, Outlook and WMP.  Didn't realize they weren't required until after I had finished.  I'll never use them and they take forever to install.

Edit: nope, can't do that, other packages depend on IE in order to install properly.:rolleyes:

---

### Post by jeffreyldavidson on 2006-09-04
I completly killed my Windows partition and installed Ubuntu Drake two weeks ago. I decided to go cold turkey to break the Windows habit. The only program I longed for was my Quicken 2006. 

Well I followed your guide step by step and now I am amazed that I have Quicken 2006 fully updated to release 4 and it works perfectly.

Thank you very much!

Now there is no reason to even think of Windows again.

JLD

---

### Post by Fraoch on 2006-09-04
Whoops, I should take the time to thank the OP for this guide.  Provided you resist the urge to update to the latest wine, it works just fine.

winetools is fantastic.

---

### Post by ~LoKe on 2006-09-05
This royally screwed up DirectX, I think.  I had a previous installation, and with winetools I selected my other fake windows directory.  I went through all the steps and installed everything, but now when I try to run Diablo II, I get this long error:

> fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x1ab140) : stub, simulating 64MB for now, returning 64MB left
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x1aaa50)->(0x10024,00000011)
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x1aaa50)->(0x10024,00000011)
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 8
err:dbghelp:pe_load_dbg_file -Unable to peruse .DBG file ole32.dbg ("")
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\wined3d.dll
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\psapi.dll
err:dbghelp:pe_load_dbg_file -Unable to peruse .DBG file dll\imagehlp.dbg ("")
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\midimap.dll
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\msacm32.dll
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\msacm32.drv
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\winealsa.drv
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\winearts.drv
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\wineesd.drv
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\wineoss.drv
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\winejack.drv
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\winenas.drv
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\uxtheme.dll
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\imm32.dll
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\winex11.drv
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\dsound.dll
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\iphlpapi.dll
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\lz32.dll
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\winspool.drv
err:dbghelp:pe_load_dbg_file -Unable to peruse .DBG file dll\comctl32.dbg ("")
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x1aaa50)->((nil),00000008)
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock


Then I get an unhandled access violation and Diablo II crashes.  Any ideas?

---

### Post by ~LoKe on 2006-09-05
No one?

---

### Post by ~LoKe on 2006-09-05
:(?

**EDIT:** Got it working with sound disabled.  But the cursor is laggy as hell and everything's slow. =[

---

### Post by lounies on 2006-09-05
I must admit your howto clicks along quite nicely until I came to: 
**tar -xf winetools*** no go. Ok! you did say it may not work for everyone.
However when I looked back into my home files, I found that two files had become locked.
This is the second time I tried to install programs outside of Synaptic package manager. Both times I have ended up with locked files
I am a newbe to be sure.
Any idea how to unlock these files.

Victor

---

### Post by FastZ on 2006-09-06
Works great!  Thanks a bunch!

---

### Post by Malta Soron on 2006-09-06
> **lounies said:**
> I must admit your howto clicks along quite nicely until I came to: 
**tar -xf winetools*** no go. Ok! you did say it may not work for everyone.
However when I looked back into my home files, I found that two files had become locked.
This is the second time I tried to install programs outside of Synaptic package manager. Both times I have ended up with locked files
I am a newbe to be sure.
Any idea how to unlock these files.

Victor

IIRC it goes like this:

```
cd 'the directory where you put the files'
sudo chmod a+rw winetools*
```

---

### Post by deadheadfred on 2006-09-06
Downloaded wine w/ synaptic, evrything seemed fine.

Installed office 2000, w/ wine, no issues.

Now wine can't seem to fine the file when I:

wine /home/dew3/.wine/c/Program Files/Microsoft Office/OFFICE11/OUTLOOK.EXE'

or

wine "c:\program files\microsoft office\office11\outlook.exe



Can someone help out a noob?

-dhf
Looked overwhere, but to no avail

---

### Post by keasley on 2006-09-06
Thanks for the HOW TO -- Took several tries but got it to work:KS 

the version of wine is "Wine 0.9.5" & 

Now - ](*,) I am trying to install a DOS Program but the following errors 

keasley@kubuntu:~$ cd /media/fd0
keasley@kubuntu:/media/fd0$ ls
ccfpp  INSTALL.EXE
keasley@kubuntu:/media/fd0$ wine install.exe
[B]Warning: unprotecting memory to allow real-mode calls.
         NULL pointer accesses will no longer be caught.
fixme:int:DOSVM_Int10Handler Get Font Information - Not Supported[/B]
keasley@kubuntu:/media/fd0$

As you can see I am trying to install from floppy drive.

Any help is greatly appreciated.

TIA

PS.  the 3rd line of the error - Pls replace the icon with a colon ":" "it is part of the error"  The board replace the ":" with the icon when previewing the post.

---

### Post by vivman1107 on 2006-09-07
I have installed Wine and Winetools with no problems. I am doing the base setup and installing DCOM98. It says that it is downloading but is stuck on 0%. This is from the terminal:

```
downloading http://download.microsoft.com/download/d/1/3/d13cd456-f0cf-4fb2-a17f-20afc79f8a51/DCOM98.EXE to dcom98.exe with 1229056 bytes...

```

I have left it running for quite a while now with no response. Is the link still good?

---

### Post by favad on 2006-09-08
Sir I tried to do this ( wine "/home/favad/.wine/c/Program Files/Internet Explorer/IEXPLORE.EXE" ) after installing the tools and all, but it failed.
My windows partition is mounted here /tmp/disks-conf-hda1

[B]favad@intel2400mhz:~$ wine "/home/favad/.wine//tmp/disks-conf-hda1/Program Files/Internet Explorer/IEXPLORE.EXE"
wine: cannot find '/home/favad/.wine/c/Program Files/Internet Explorer/IEXPLORE.EXE'

favad@intel2400mhz:~$ wine "/home/favad/.wine//tmp/disks-conf-hda1/Program Files/Internet Explorer/IEXPLORE.EXE"
wine: cannot find '/home/favad/.wine//tmp/disks-conf-hda1/Program Files/Internet Explorer/IEXPLORE.EXE'[/B]

I hope u can please help here.

favad

---

### Post by jeffreyldavidson on 2006-09-08
I had Quicken running and then my system did an update to the newer version of wine and it would no longer work. I downgraded and Quicken 2006 now works again, except that I have to force close it.

I have a question. How do I put a link from the wine - Quicken shortcut on the desktop?

Thanks, JLD

---

### Post by iammeagain on 2006-09-10
How do you know what version of wine you have updated to? Does IE work with Wine 0.9.10 or not? How do i get it to update to 0.9.10 because my IE isn't working

---

### Post by jbumgar on 2006-09-10
When I go to this site there is no  wget [http://kent.dl.sourceforge.net/sourceforge/wine/wine_0.9.5-winehq-1_i386.deb](http://kent.dl.sourceforge.net/sourceforge/wine/wine_0.9.5-winehq-1_i386.deb)

---

### Post by machoo02 on 2006-09-11
Not sure if this has been mentioned in this thread yet, but if you use winetools to set up wine, and you have problems with an application, you will get no help from the wine developers to try to solve your problem.  

jbumgar...you are not looking for wget at that site.  type

```
 wget http://kent.dl.sourceforge.net/sourceforge/wine/wine_0.9.5-winehq-1_i386.deb
``` into a terminal to download the .deb from that website.  wget stands for "web get" (I think....:-k)

-Matt

---

### Post by bewell on 2006-09-12
First, so many thanks to gazj for this how-to, and to everyone else who has contributed to this topic.  I can't tell you how many times I was close to successfully installing wine and winetools on several different distributions, but always fell short.  With this how-to and using Breezy, I was able to finally GO THE DISTANCE !  I followed the steps, and IE, Outlook, and Media Player all seem to work great.  =D>  =D>  =D> 

My ultimate goal is to get Microsoft Money ver. 2004 to run.  Looking at the Wine-Apps DB, there seems to be 2 and only 2 specific wine versions that this app. will work under with the Breezy distro: The "Bronze" test uses wine ver 0.9.7, and the "Silver" test uses wine ver. 0.9.9

Now, I apologize if these questions have been asked before, or are answered in some other spot on this forum.  I have read thru many posts, and I'm still not 100% certain as to how to proceed.

Is it better/safer to attempt to upgrade wine? or is it better/safer to uninstall it, and then re-install one of these 2 versions ?  :confused: 

If the answer is it's better/safer to upgrade, how can I make sure I'm only upgrading to one of the 2 versions that I need (and not to any version beyond 0.9.9) ?  What are the specific steps  to upgrade it ?  :confused: 

If the answer is it's better/safer to uninstall and then reinstall wine, where would I get one of the 2 older wine versions that I need?  Are there specific steps or instructions I should follow to uninstall wine?  Same question to reinstall wine (or can I simply follow the early steps in this how-to to reinstall wine) ?  :confused: 

Thanking anyone in advance who will respond to this in advance. :D

---

### Post by bigbearomaha on 2006-09-12
I followed the howto, very good.  however , I am now trying to find out how to find a program I installed to try to run it.  I 'm not sure where to look to find the exe.  I don't seem to find a wine folder or c folder.  Please help.

---

### Post by bewell on 2006-09-12
just a guess..

click on places, then home, then view, then show hidden files...

you should see a .wine folder...

click on it, then on drive_c, and program files...

---

### Post by gbdavidx on 2006-09-12
I get this error message:

> dave@dave-laptop:~$ winecfg
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  1 (X_CreateWindow)
  Resource id in failed request:  0x3600007
  Serial number of failed request:  13
  Current serial number in output stream:  15
dave@dave-laptop:~$


whats wrong?

---

### Post by bigbearomaha on 2006-09-13
Thank you much, always the simple things we overlook.  your help has been invaluable.

Big Bear

---

### Post by bewell on 2006-09-14
Never mind.....I installed ver 9.9 without uninstalling ver 9.5...It worked perfectly !!!

---

### Post by mattice06082 on 2006-09-16
This HOWTO works perfectly, but I have one problem.  Wine does not recognize my sound card.  Ubuntu correctly identifies it as an Intel 82801 AC'97 and I am able to hear audio from Audacity etc. while in Ubuntu.  However, while in Wine I can't get any audio.  I've download the Windows 98 drivers from driversguide.com, but I don't know how to get winecfg to use this information.  I'd appreciate any help.  Thanks for your help.

---

### Post by bryan4134 on 2006-09-18
I followed the howto exactly and eveything worked perfectly - IE working etc.etc.  Then I went through the update/upgrade process and everything stopped working.  For IE I just get a window that is headed "Wine Internet Explorer" but it goes no further.  I am running Ubuntu 6.06 with Wine 0.9.21. 

Not sure how this happened as I installed 0.9.5 as instructed in the howto.

Any thoughts??

Thanks,

---

### Post by gkiller on 2006-09-19
IE didn't work for me either, I tried versions 0.9.19 to 0.9.21.

Is this a general Wine problem? (A bit hard to imagine that wine breaks IE for such a long time).

Or is it a problem of how all the stuff gets installed in this howto (a way old helper program 'winetools' etc.)?

*edit*
BTW, IE worked in the 0.9.5 version.

---

### Post by odzx on 2006-09-20
same problem here. ie comes up blank after upgrade. + another problem i have is that even after istallation of all the fonts i can not write hebrew inside the browser. the same problem accurs when installing ie4linux and even windows firefox (same problem with the hebrew versions of FF and ie4linux)

---

### Post by machoo02 on 2006-09-20
From what I remember, Wine is now using the Gecko engine, and not the microsoft engine, to render HTML.  To get IE working again, you would need to set some DLLOVERRIDES to use the native mshtml and a few others.  Check the Wine AppDB website for tips.

-matt

---

### Post by silent_scream on 2006-09-20
thnx for this how-to!
actually it din't install the ie or win media player or outlook, but i don't care.

my problem is that i installed utorrent, and the fonts (letters) are too small, and some others are dissapeared!!

any idea how to fix this??

---

### Post by BLTicklemonster on 2006-09-23
> **Rizado said:**
> The easiest way to install ie6 is to use [ie4linux.](http://www.tatanka.com.br/ies4linux/)
It's a script that downloads everything that's needed and installs into .ie4linux (by default) instead of .wine
Nothing is done in .wine at all so it can be ran without fear of breaking every other installed app and you'll have a clean .wine for other things.

I just installed it, and used it to go to our main page [www.theblacklegion.com](www.theblacklegion.com) and installed xplug. When it was installing, I saw that it was using the wine path, and freaked because I wasn't sure if this was a wine app or not, but it installed and works, so what the hey, I don't care one way or the other. It also finally allows me to use the gis browser we have for our city. Sweet! Thanks a lot!

---

### Post by delta99 on 2006-09-23
I am surprised it worked for me, im overwhelmed.

What an excellent guide, had no problems, thank you!

---

### Post by BLTicklemonster on 2006-09-23
No doubt. I liked it so much, I even put it in my sig.

---

### Post by tuxcantfly on 2006-09-24
you might want to add my multiple wine configurations guide to yours:
[http://ubuntuforums.org/showthread.php?t=228190](http://ubuntuforums.org/showthread.php?t=228190)

---

### Post by makeshift on 2006-09-25
[QUOTE=gazj;

ok, so now we gotta sort out theese fonts as the links that winetools uses to retrieve them is dead, so click main menu followed by exit to leave winetools

now then back to our friend the terminal
ok so first we need to make and move to the directory where winetools would have downloaded the fonts

```
mkdir ~/winetools/fonts
cd ~/winetools/fonts
```

you might get an error saying the file exsits, if you do don't worry just continue

Next we download the fonts from a link that is still around at the time of writing this, you might want to copy and paste this one into your terminal

```
wget http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe && wget http://kent.dl.sourceforge.net/sourceforge/corefonts/arial32.exe && wget http://kent.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe &&  wget http://kent.dl.sourceforge.net/sourceforge/corefonts/comic32.exe &&  wget http://kent.dl.sourceforge.net/sourceforge/corefonts/courie32.exe &&  wget http://kent.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe &&  wget http://kent.dl.sourceforge.net/sourceforge/corefonts/impact32.exe &&  wget http://kent.dl.sourceforge.net/sourceforge/corefonts/times32.exe &&  wget http://kent.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe &&  wget http://kent.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe &&  wget http://kent.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe
```

Ok, so we now have the fonts downloaded, next back to winetools to install them ;)

```
wt
```

Select base setup again then install true type font arial

Next main menu then select Install Microsoft true type corefonts, yet again go all the way down the list until you have installed all the fonts.
[/QUOTE]

Or just copy fonts from your Windoze drive/partition, if you still got it :) . Again Thanks for da **great** tutorial !

---

### Post by jatazoulja on 2006-09-25
> **gazj said:**
> 
then add this line to the bottom of the file

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/


So dose this mean I should be conected to the internet?
I use my ubuntu at home so no reason for me to be conected and mos t software I got from the net are downloaded at the cafes...

So can I just download? do you guys know a link?

---

### Post by Sokraates on 2006-09-26
This is what you need:
 
[LEFT][http://kent.dl.sourceforge.net/sourceforge/wine/wine_0.9.5-winehq-1_i386.deb](http://kent.dl.sourceforge.net/sourceforge/wine/wine_0.9.5-winehq-1_i386.deb)[/LEFT]
 
[LEFT][http://ds80-237-203-29.dedicated.hosteurope.de/wt/winetools-0.9jo-III.tar.gz](http://ds80-237-203-29.dedicated.hosteurope.de/wt/winetools-0.9jo-III.tar.gz)[/LEFT]
 
[LEFT]Lastly libgtk1.2 from the official ubuntu-repositories. You'll find it under [http://packages.ubuntu.com](http://packages.ubuntu.com)
 [/LEFT]

---

### Post by sharperguy on 2006-09-28
Well it looks like many important links are now dead following microsofts abandoning of windows 98 :(

---

### Post by pompiuses on 2006-09-29
I followed this HOWTO and got wine with IE working fine. Great HOWTO by the way.

I then decided to upgrade wine, and did so using synaptic package manger. So it upgraded to wine 0.9.12.

I then started IE again in wine and got a question if I wanted to install a Mozilla divx component (or whatever, I cant remeber exactly). I chose yes and it seemingly installed ok.

But when I now try to start IE I get the following errormessage and IE just blinks at the screen before it dissapears again:

fixme:shdocvw:IEWinMain "" 1
fixme:shdocvw:iecs_QueryInterface unknown interface {00020400-0000-0000-c000-000000000046}
fixme:shdocvw:iecs_QueryInterface unknown interface {9c2cad80-3424-11cf-b670-00aa004cd6d8}
fixme:shdocvw:is_CanInPlaceActivate
fixme:shdocvw:is_OnUIActivate

Anyone know how to fix this?? I cant figure it out :mad:

---

### Post by pompiuses on 2006-09-29
> **pompiuses said:**
> I followed this HOWTO and got wine with IE working fine. Great HOWTO by the way.

I then decided to upgrade wine, and did so using synaptic package manger. So it upgraded to wine 0.9.12.

I then started IE again in wine and got a question if I wanted to install a Mozilla divx component (or whatever, I cant remeber exactly). I chose yes and it seemingly installed ok.

But when I now try to start IE I get the following errormessage and IE just blinks at the screen before it dissapears again:

fixme:shdocvw:IEWinMain "" 1
fixme:shdocvw:iecs_QueryInterface unknown interface {00020400-0000-0000-c000-000000000046}
fixme:shdocvw:iecs_QueryInterface unknown interface {9c2cad80-3424-11cf-b670-00aa004cd6d8}
fixme:shdocvw:is_CanInPlaceActivate
fixme:shdocvw:is_OnUIActivate

Anyone know how to fix this?? I cant figure it out :mad:

Got it working by just downgrading to the 0.9.5 version again :). This should definately be put into the original post!

If you want IE and outlook to work, don't run anything above 0.9.5.

---

### Post by moreinfo on 2006-09-30
Had the same problem as Pompiuses.

Downgraded again, and works fine.

However the first time I tried It didn't work however, I had the latest wine already installed.  I had tried to download IE6 before reading this post I ended up removing all of wine, but that didn't work, so I went to find the folder and it was still there.  So I deleted them all and sent them to the trash. I restarted the comp then restarted this whole procedure, and it all worked fine.  Good Job!

So I started up IE again and it takes me to the MS update page; IE7, Critical updates etc etc.
What should we do about these, also

What do we do about wine updates?

---

### Post by pgroover on 2006-10-08
Great how to! It had me up and running smoothly with wine (again), but I have what may be a silly question, how can I downgrade and keep my existing settings?

** EDIT **
Never mind, I figured it out, but how can I still use IE without the stupid ActiveX control?  I can refuse to get it but then browsing is disabled and if I accept it IE no longer "runs", it simply blinks and goes away.

thx

---

### Post by saintj0n on 2006-10-09
I have previously installed the latest version of wine but now my internet explorer doesn't work. How do I uninstall wine and restore what it has modified? I would like to just take it off and try again.

---

### Post by Irish J on 2006-10-09
I've just tried this HOWTO, and it seems one of the other links is dead (Classes).

Is this essential?

---

### Post by pgroover on 2006-10-09
If you followed the entire How To, then you can uninstall winetools using the uninstall script within the winetools installation directory.  After that's completed you can then uninstall wine using adept, then remove the .wine directory and the winetools directory.

That should put you at a point to start over again.

---

### Post by trommas on 2006-10-10
Wine is closing in on 1.0, and I just can't wait for it. For now, I would just love to see an updated howto for edgy. 

Is this an unrealistic dream?

---

### Post by BLTicklemonster on 2006-10-10
> First we get the wine0.95.deb from winehq [http://kent.dl.sourceforge.net/sourc...ehq-1_i386.deb](http://kent.dl.sourceforge.net/sourc...ehq-1_i386.deb)

or if you want to open a terminal (alt+F2 then type gnome-terminal then enter) to download it use this command

Code:

wget [http://kent.dl.sourceforge.net/sourceforge/wine/wine_0.9.5-winehq-1_i386.deb](http://kent.dl.sourceforge.net/sourceforge/wine/wine_0.9.5-winehq-1_i386.deb)



The link to 0.9.5 is dead. What other version will this work with? There are many people who see this tutorial as the best one out there, so please, if you could let us know which to use, that would be great.


*edit:
Upon further reflection....

Okay, you say that the reason not to use newer versions is because IE breaks. Therefore, I assume it would be okay to apt-get install wine, then follow your tutorial picking up at the part about winetools, then use this: [http://www.ubuntuforums.org/showthread.php?t=267469&highlight=internet+explorer+4+u](http://www.ubuntuforums.org/showthread.php?t=267469&highlight=internet+explorer+4+u)  to get Internet Explorer in wine, and everything ought to be fine, right? (my IE broke anyway, so I used that link, and IE works great now)

---

### Post by Fingerlakes_Dave on 2006-10-10
> **gazj said:**
> *** UPDATE 19-07-2006 (UK DATE SYSTEM :) )
and really thats about it, you can also navigate using your file browser and double click .exe files and wine will launch them, like installers for programs and so on, then its just a case of finding the .exe that starts the program and making your custom launcher for it, your wine c: should always be found in /home/USERNAME/.wine/c. As long as know a bit about the windows file layout you should have no problem in finding them, always remember when creating your launchers that linux is case sensitive, so dont forget the caps.


  OK.  I understand launchers, Windows files system, etc.

  I have tried two programs, no luck.

  wine "home/UN/.wine/c/Program Files/xyz.exe"

  nada.  The only response I have gotten so far is when I forgot the last "
on the command line for the launched :???: 

  Any help appreciated.

---

### Post by BLTicklemonster on 2006-10-10
What programs are they? Perhaps they are some of the ones that don't work in wine? Or perhaps you have the default version wine runs in as win nt4, and the programs will only run in 98 or xp or something? Have you tried setting the specific file to run in a specific version of windows ( winecfg and chose the file, then set the windows version for it, then apply, then try it)?

I'm not any kind of wine guru (well, okay, I used to be a salesman for a wine distributor, but that was the kind you get drunk on, not the software kind, lol), but I'd start with trying that.

*edit:

by saying I'd start with trying that, you know I mean the version settings, not the getting drunk part, right? ;)

---

### Post by kkuzia on 2006-10-10
> **jeffreyldavidson said:**
> I had Quicken running and then my system did an update to the newer version of wine and it would no longer work. I downgraded and Quicken 2006 now works again, except that I have to force close it.

I have a question. How do I put a link from the wine - Quicken shortcut on the desktop?

Thanks, JLD

My problem is even uglier.  I followed the HOWTO, got Wine working just fine and IE 6 up and running... but I am having problems with Quicken 2006.  I install it via Wine, but when I go to even open up the Quicken folder created in the Program Files... Nautilus crashes.  I tried uninstalling everything for Wine and running it all again... same problem.  Any ideas???](*,)

---

### Post by pgroover on 2006-10-10
> **BLTicklemonster said:**
> 
Okay, you say that the reason not to use newer versions is because IE breaks. Therefore, I assume it would be okay to apt-get install wine, then follow your tutorial picking up at the part about winetools, then use this: [http://www.ubuntuforums.org/showthread.php?t=267469&highlight=internet+explorer+4+u](http://www.ubuntuforums.org/showthread.php?t=267469&highlight=internet+explorer+4+u)  to get Internet Explorer in wine, and everything ought to be fine, right? (my IE broke anyway, so I used that link, and IE works great now)

Great link!!  Thanks, now programs that require it are satisfied!!  :D

*edit*
What should I do for the "required" updates...??

---

### Post by BLTicklemonster on 2006-10-11
No prob. I'd sit on the updates until I posted at that link and asked them! 

Also, anyone having problems with wine, please remember, limited help can be gotten here, but if you can find a wine forum that would be the place to help on thorny issues that can't be resolved here.

---

### Post by gosh on 2006-10-11
I try to setup IE, but mfc40.dll is missing.
I downloaded this file.
Where should I save it?
And how must I proceed to get IE working?

```
~/winetools$ wt
detecting Wine version... done.
Drive C: is /home/jos/.wine/drive_c
Wine 0.9.21
wine is executed as wine
Parameters are --noexit
Browser is /usr/bin/firefox.
WINEVER is "0.9.21".
Calls to wine are executed as  "wine".
Config is /home/jos/.wine/winetools.log.
Choice is Base setup
Choice is Internet Explorer 6.0 SP1 English with checked=F
dcom98.exe to check
software installation verified by /home/jos/.wine/winetools.log
dcom98.exe = installed at 11.10.2006 09:09:59
dependency dcom98.exe fulfilled
mfc40.dll to check
software installation verified by /home/jos/.wine/winetools.log
dependency mfc40.dll *not* fulfilled


```

---

### Post by bodhi.zazen on 2006-10-11
This information has been added to the Ubuntu Wine wiki:

[How to wine](http://doc.gwos.org/index.php/HowToWine)

---

### Post by Aberrix on 2006-10-11
After days and hours of trying to get Quicken 2006 to work, this tutorial has finally made it happen!!!

Thanks for this write up!

---

### Post by weaver73 on 2006-10-11
Thanks for this one! Even an imbecill as me could work it out with this howto.

---

### Post by pgroover on 2006-10-11
Try this link that was posted a few messages before you, it got me up and running quickly and _easily_.

[http://www.ubuntuforums.org/showthre...explore r+4+u]("http://www.ubuntuforums.org/showthread.php?t=267469&highlight=internet+explorer+4+u")

---

### Post by BLTicklemonster on 2006-10-11
> **bodhi.zazen said:**
> This information has been added to the Ubuntu Wine wiki:

[How to wine](http://doc.gwos.org/index.php/HowToWine)

Thanks. I looked over it briefly, but the question remains; can people just install the newest, use winetools, then install internetexplorer 4 u and have the same results, or is there something with the new versions that will cause problems along the way?

---

### Post by pgroover on 2006-10-11
> **BLTicklemonster said:**
> Thanks. I looked over it briefly, but the question remains; can people just install the newest, use winetools, then install internetexplorer 4 u and have the same results, or is there something with the new versions that will cause problems along the way?

I can answer that one as I originally followed the instructions with winetools and then installed internetexplorer 4 u and was completely successful.

---

### Post by bodhi.zazen on 2006-10-11
> **BLTicklemonster said:**
> Thanks. I looked over it briefly, but the question remains; can people just install the newest, use winetools, then install internetexplorer 4 u and have the same results, or is there something with the new versions that will cause problems along the way?

That is a good question.

The problem in giving an answer is that wine is updated every 2 weeks. Each version/update is a little different and who has the time?

Personally I use Sidenet for a variety of reasons.

Personally I have one application for which there is no Linux equivalent (Dragon Naturally Speaking). I can only install Dragon in wine-0.9.12. It runs fine in up to wine-0.9.19, but will not install in anything wine-0.9.13 or higher. With wine-0.9.20 + my application no longer runs.....

My advice: Once you get an application installed and running in wine I see no reason to be running the newest version of wine. Just stay with what works.

If you are having difficulty with an application, however, every two weeks is a new ball game....

If winetools is not working for your application, try Sidenet....

But ever with Sidenet, each version of Sidenet gives different results with the same version of wine.

So again, test, tweak, and stay with what works.

Best way to test wine: Back up your install by backing up ~/.wine ```
cp -R ~/.wine ~/.wine.bak
```
Now you can test away. If you break something, downgrade wine and ```
rm -R ~./wine
cp -R ~/.wine.bak ~/.wine
```


Most of what I put in the wiki is some practical advice on how to install & configure wine, some common solutions to say CD/DVD, and where to look for the best and most current advice in getting applications up and running (wineHQ).

---

### Post by BLTicklemonster on 2006-10-11
Excellent. Thank you for all you do.

---

### Post by BarnOwl on 2006-10-13
Help an absolute noob please!!!

I've been beating my head against the wall trying to get apps in wine to see my dvd burner.  This How-To looks like it addresses that.  However, it's pretty old.  Is is valid for the current version of wine?

---

### Post by BLTicklemonster on 2006-10-13
Now I'm sure you can do this how to with the newest version of wine, just follow the winetools section, then once done, get internet explorer 4 u that I linked to a couple of posts back and you will have internet explorer working fine.

Now in terminal, type

winecfg

and click drives, then click autodetect.

It ought to detect your dvd.



What kind of problems are you having?


Also, if you are running into problems with newer dvds, you will want to have [dvd decryptor and dvd shrink installed](http://www.mrbass.org/linux/ubuntu/dvdshrink/),but [read this first](http://www.ubuntuforums.org/showthread.php?t=36112&highlight=dvd+shrink) then go get this: [http://www.ripit4me.org/](http://www.ripit4me.org/) and use it to rip your dvds. START WITH RIPIT4ME, it will use dvd decryptor as needed. The instructions are on the site, so use them. 

Once you are done, you can use k3b to burn your dvd. Just pay attention to where the dvd rips to! Just drag your video_ts and audio_ts folders into the workspace on k3b and burn your dvd. I archived The General's Daughter using ripit4me and dvdshrink/decryptor, and was watching it on the dvd player upstairs until we took a break for the wifey poo to cook some supper.

---

### Post by BarnOwl on 2006-10-14
winecfg does detect the drive.  However, nothing running in wine including winefile can see the drive.  At least they don't seem to recognize that it's a DVD drive. I've been trying to get this to work for sometime.  I've found the symbolic links that wine uses for the drives and fooled with more configurations than I ever want to know about but, no results.

I'm afraid that there's nothing in the Linux world to compare with the combination of tools I use from windows.  The main tool that I use is DVDRemake pro. It's not free but, it's not too expensive.  Unless I'm mistaken, and I could be, there are no tools in Linux that would allow me to disable individual buttons in menus, selectively cut out portions of frames, split disks across mulitple disks, etc.; in a graphical interface and preserving the menus.

---

### Post by BLTicklemonster on 2006-10-14
That's quite odd. Have you put a dvd in the drive while running winecfg and detecting it?

---

### Post by BarnOwl on 2006-10-15
A little more info.  If I run winecfg and hit the drive tab, it doesn't show a cdrom.  When I hit autodetect, it'll show up in winecfg. Then I hit the apply button and the ok button.  None of the apps can see the drive and if I run winecfg again, it's not there.

I've dug around in the wine registry and it does have the drive properly identified there.

I hate to suggest a windows type rain dance in a Linux forum but, do you think there's anything to be gained be try a clean reinstall of either wine or kubuntu?  This is kind of an interesting situation.  For a month or so I have this extra box.  If I can get it to do what I need in Linux, asta la vista MS.  So, I really don't have a problem reloading it.

---

### Post by bodhi.zazen on 2006-10-15
What is the mount point of your DVD?

Assuming it is /media/cdrom:```
cd ~/.wine/dosdevices
ln -s /media/cdrom g:
```

[list=number][*]use a new "letter" for the windows device, ie do not re-cycle d:.[*]The dvd player must be working in Linux.[*]You must mount the dvd in Linux before it will bee seen in wine.[/list]

You now should see your dvd in wine.

If it is an install dvd:```
wine g:setup
```or```
wine g:install.exe
```

---

### Post by BarnOwl on 2006-10-15
Okay, I've done that and the drive shows up in winefile.  However, winefile can't show the files on it like would see in windows.  DVD Decrypter can't detect it as an ATAPI device and it won't accept it when I browse to it.  Neither will DVDFab Decrypter or DVD Shrink. Interestingly enough when I look at the device in winefile, it does show the correct label.  Should I be providing a windows .dll file perhaps?

---

### Post by bodhi.zazen on 2006-10-15
> **BarnOwl said:**
> Okay, I've done that and the drive shows up in winefile.  However, winefile can't show the files on it like would see in windows.  DVD Decrypter can't detect it as an ATAPI device and it won't accept it when I browse to it.  Neither will DVDFab Decrypter or DVD Shrink. Interestingly enough when I look at the device in winefile, it does show the correct label.  Should I be providing a windows .dll file perhaps?

Did you install the necessary DVD stuff?

[Restricted formats](https://help.ubuntu.com/community/RestrictedFormats)

If not, start there.

---

### Post by BarnOwl on 2006-10-15
I do now and Kaffeine can play DVDs but, still nothing can see the DVD on the wine side.

---

### Post by bodhi.zazen on 2006-10-15
> **BarnOwl said:**
> I do now and Kaffeine can play DVDs but, still nothing can see the DVD on the wine side.

LOL :lol: So you can see the DVD from the wine side, but not play a DVD.

I would assume you would need to install simmilar "restricted fromat" software in wine.

Or did you already install the windows software and it does not work ?

Why not use Kaffeine ?

---

### Post by Fingerlakes_Dave on 2006-10-16
> 
and really thats about it, you can **_also navigate using your file browser and double click .exe files and wine will launch them,_** like installers for programs and so on, then its just a case of finding the .exe that starts the program and making your custom launcher for it, your wine c: should always be found in /home/USERNAME/.wine/c. As long as know a bit about the windows file layout you should have no problem in finding them, always remember when creating your launchers that linux is case sensitive, so dont forget the caps.
 
  How do you get the bold section above to work??  Hasn't worked yet in anything I've tried.  Do you have to type wine at the command prompt, then click an exe?

  Also can't get a launcher to work for anything I've tried so far.](*,) ](*,) 

  I'm about to uninstall.

  Any alternatives to wine that work better??

---

### Post by pgroover on 2006-10-16
> **Fingerlakes_Dave said:**
> How do you get the bold section above to work??  Hasn't worked yet in anything I've tried.  Do you have to type wine at the command prompt, then click an exe?

It should work "automagically", but if it doesn't you could associate ".exe" files to open with wine and that will handle it for you.

---

### Post by bodhi.zazen on 2006-10-16
> **Fingerlakes_Dave said:**
> How do you get the bold section above to work??  Hasn't worked yet in anything I've tried.  Do you have to type wine at the command prompt, then click an exe?

  Also can't get a launcher to work for anything I've tried so far.](*,) ](*,) 

  I'm about to uninstall.

  Any alternatives to wine that work better??

LOL :lol:

To make a launcher work for wine you need to use the proper command.

wine <path_to_program.exe>

You can use your browser to find the program.exe.

Linux does not like the <space> in "Program Files", you have to "escape" it Like this: "Program\ Files".

Thus, in your menu, desktop icon, or launcher use:```
wine /home/user_name/.wine/c/Program\ Files/program.exe
```In the "command" box.

---

### Post by Fingerlakes_Dave on 2006-10-16
> **pgroover said:**
> It should work "automagically", but if it doesn't you could associate ".exe" files to open with wine and that will handle it for you.

OK.  And being new at this, how is it done in linux? 
 I know how to do it in XP/98/3.11, etc :-? 

 Commnad line or a setting somewhere?

---

### Post by Fingerlakes_Dave on 2006-10-16
> **bodhi.zazen said:**
> LOL :lol:

To make a launcher work for wine you need to use the proper command.

wine <path_to_program.exe>

You can use your browser to find the program.exe.

Linux does not like the <space> in "Program Files", you have to "escape" it Like this: "Program\ Files".

Thus, in your menu, desktop icon, or launcher use:```
wine /home/user_name/.wine/c/Program\ Files/program.exe
```In the "command" box.

  I understand command lines, been using since DOS 4 :) 

  It would be nice if it was mentioned somewhere in the install (or I missed it).  Thanks

---

### Post by Fingerlakes_Dave on 2006-10-16
> **bodhi.zazen said:**
> LOL :lol:

To make a launcher work for wine you need to use the proper command.

wine <path_to_program.exe>

You can use your browser to find the program.exe.

Linux does not like the <space> in "Program Files", you have to "escape" it Like this: "Program\ Files".

Thus, in your menu, desktop icon, or launcher use:```
wine /home/user_name/.wine/c/Program\ Files/program.exe
```In the "command" box.

  Any other thoughts?  Still no luck.

---

### Post by bodhi.zazen on 2006-10-16
Just to ask the obvious, can you launch your program from the command line ?

If so, try a single quote arround the whole command in your launcher:```
'wine /home/user_name/.wine/c/Program\ Files/program.exe'
```

---

### Post by BLTicklemonster on 2006-10-16
> **bodhi.zazen said:**
> Just to ask the obvious, can you launch your program from the command line ?

If so, try a single quote arround the whole command in your launcher:```
'wine /home/user_name/.wine/c/Program\ Files/program.exe'
```

I think Dave needs a little more info than "use the command line". Dave, I'm in kde right now, you are probably in gnome, so this may not be the same, but I'd click on the k, then go to terminal sessions and click on shell. 

Anyway, it might be easier if you right click on an .exe and choose "open with wine".

Someone in front of a gnome desktop will be along shortly to tell you how to get to the terminal, though.

Keep asking questions. It won't be long before you're in here offering advice to new users!

---

### Post by bodhi.zazen on 2006-10-16
Perhaps this then:

[list=number][*]Open Nautilus (Places -> Desktop).[*]Browse to a program.exe (/home/user_name/.wine/c/Program\Files)[*]Right-click the program.exe, select Properties, go to the Open With tab, choose Wine.[/list]

Now when you double-click on a program.exe, it will be started with wine. [-o<

---

### Post by pgroover on 2006-10-16
Sorry about that, I forgot you were asking for completeness.

1. Browse to the file with Nautilus
2. Right click on it and view it's properties
3. Select the "Open With" tab and click "+Add"
4. If it exists, select wine in the list box otherwise click "Use a custom command" and type in /usr/bin/wine (this is the default location) and then click "Add" and close the dialog.

After the above you should be fine.

---

### Post by BLTicklemonster on 2006-10-16
By God, that's pretty danged complete there. I hope he can get this resolved now.

---

### Post by BarnOwl on 2006-10-16
> **bodhi.zazen said:**
> LOL :lol: So you can see the DVD from the wine side, but not play a DVD.

I would assume you would need to install simmilar "restricted fromat" software in wine.

Or did you already install the windows software and it does not work ?

Why not use Kaffeine ?

Well if I was just interested in playing DVDs, I would.  As far as I know Linux based DVD rippers give you one of two choices.  You can rip to mpegs and lose useful menus or you can rip to ISOs which can be compressed and that's about it.  As I explained in a previous post, I know of nothing in the unix world that will allow me to rip a DVD, edit individual buttons on the DVD menus, selectively remove portions of the disk, etc. in a grapical interface and keepng working menus.  I do have that in windows programs.  However, none of the windows programs recognize the DVD reader as a DVD reader.  Nor do they recognize it as a writer.  They can see something's there but, they don't appear to know what it is.

---

### Post by bodhi.zazen on 2006-10-16
> **BarnOwl said:**
> Well if I was just interested in playing DVDs, I would.  As far as I know Linux based DVD rippers give you one of two choices.  You can rip to mpegs and lose useful menus or you can rip to ISOs which can be compressed and that's about it.  As I explained in a previous post, I know of nothing in the unix world that will allow me to rip a DVD, edit individual buttons on the DVD menus, selectively remove portions of the disk, etc. in a grapical interface and keepng working menus.  I do have that in windows programs.  However, none of the windows programs recognize the DVD reader as a DVD reader.  Nor do they recognize it as a writer.  They can see something's there but, they don't appear to know what it is.

[DVD Editing/Authoring/Burning with Linux](http://gecius.de/linux/dvd.html)

---

### Post by Fingerlakes_Dave on 2006-10-16
> **BLTicklemonster said:**
> I think Dave needs a little more info than "use the command line". Dave, I'm in kde right now, you are probably in gnome, so this may not be the same, but I'd click on the k, then go to terminal sessions and click on shell. 

Anyway, it might be easier if you right click on an .exe and choose "open with wine".

Someone in front of a gnome desktop will be along shortly to tell you how to get to the terminal, though.

Keep asking questions. It won't be long before you're in here offering advice to new users!

  The problem is there's no "open with line" option on my right click! :confused: :confused: ](*,)

---

### Post by BarnOwl on 2006-10-16
> **bodhi.zazen said:**
> [DVD Editing/Authoring/Burning with Linux](http://gecius.de/linux/dvd.html)
Yes, Ive seen that.  I hate to say it but, the Linux DVD tools are not adequate for what I'm doing.  This is an area where it may take a while to catch up.

I went ahead and defined my DVD drive as a scsi drive to try that.  No joy there either.

---

### Post by pgroover on 2006-10-16
> **Fingerlakes_Dave said:**
> The problem is there's no "open with line" option on my right click! :confused: :confused: ](*,)

I'm not sure what file browser you're using, but you can open a terminal and type "nautilus" (without the quotes), browse to an "exe" file, select properties, and then you'll have the ability to have a right click.

---

### Post by BLTicklemonster on 2006-10-16
> **Fingerlakes_Dave said:**
> The problem is there's no "open with line" option on my right click! :confused: :confused: ](*,)

Are you using Gnome? Here is what it looks like in Gnome, and I know it's there in KDE, too. Just right click the file.

---

### Post by pgroover on 2006-10-16
> **BLTicklemonster said:**
> Are you using Gnome? Here is what it looks like in Gnome, and I know it's there in KDE, too. Just right click the file.

I guess that is the perfect question to be asking at this point as I'm not sure of any file browser that doesn't have that capability, unless it's been customized, or an extremely slimmed down version of a more popular one. :-?

---

### Post by Fingerlakes_Dave on 2006-10-16
> **bodhi.zazen said:**
> Perhaps this then:

[list=number][*]Open Nautilus (Places -> Desktop).[*]Browse to a program.exe (/home/user_name/.wine/c/Program\Files)[*]Right-click the program.exe, select Properties, go to the Open With tab, choose Wine.[/list]

Now when you double-click on a program.exe, it will be started with wine. [-o<
  OK.  I think I'm missing something. 

 Am I supposed to ***install*** to /home/user_name/.wine/c/Program\files\xxx.exe?
**Or is that where I copy an exe file to run?**

  **Or do I go to XP C,D,F, whatever Program Files\Program_Name\xxx.exe and then right click and use wine?**

  Confused is an understatement.

??????   ](*,) ](*,)

---

### Post by BLTicklemonster on 2006-10-16
Once you have wine set up, you can "normally" double click on any .exe file and it "should" automatically open in wine and install as if it were in windows. 

Finding the file may be easier from the terminal (click applications, system tools, terminal) if you type

winefile

and then navigate around to c:\program files and find your recent installation, and then (don't hate me) right click on it and click "open". That is until you get used to making launchers.

---

### Post by Fingerlakes_Dave on 2006-10-16
> **pgroover said:**
> Sorry about that, I forgot you were asking for completeness.

1. Browse to the file with Nautilus
2. Right click on it and view it's properties
3. Select the "Open With" tab and click "+Add"
4. If it exists, select wine in the list box otherwise click "Use a custom command" and type in /usr/bin/wine (this is the default location) and then click "Add" and close the dialog.

After the above you should be fine.

 OK. This is what I get even after the above (needs ' at the start and finish of the command line, also):

 >> xxx.exe indicates that this file is of type "executable". The contents of the file indicate that the file is of type "DOS/Windows executable". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "DOS/Windows executable", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file. <<

---

### Post by Fingerlakes_Dave on 2006-10-16
> **BLTicklemonster said:**
> Once you have wine set up, you can "normally" double click on any .exe file and it "should" automatically open in wine and install as if it were in windows. 

  Not happening. So far I did get ONE (1) program to load in linux.
Still haven't figured out if I can use it.
 Program is ifranview.  Tried every other program in program files.
no luck at all! 
> 
winefile

and then navigate around to c:\program files and find your recent installation,


  Define instillation?  Install from disk, cd, archive file?  Or install click on an exe and have wine run it?

> 
 and then (don't hate me) right click on it and click "open". That is until you get used to making launchers.

  Actually, I made a launcher for GrubEd my first day in linux.  Not that much different than a *.pif file in Windows 3.11

---

### Post by BLTicklemonster on 2006-10-16
Okay, do this, seeing as how we both have irfanview (which rocks, of course)...

winefile, then click on the c drive from the tool bar at the top ( c:\ ) then go to program files, then irfanview, then double click on i_view32.exe. that is what I mean by the installation. (turns out you don't need to rt click and click open)

Hope that helps. Once you install something in wine, that's where it will be.

---

### Post by pgroover on 2006-10-16
> **Fingerlakes_Dave said:**
> OK.  I think I'm missing something. 

 Am I supposed to ***install*** to /home/user_name/.wine/c/Program\files\xxx.exe?
**Or is that where I copy an exe file to run?**


When you install software with wine it is still installed in it's default windows location, but since you're in Linux this is within the .wine directory.  This is typically /home/username/.wine/c/Program\ Files/ProgramName/some.exe.

Regardless of where the executable is that you try to open, once you associate "exe" files to open with wine, it is a global system choice.

---

### Post by bodhi.zazen on 2006-10-16
> **Fingerlakes_Dave said:**
> OK.  I think I'm missing something. 

 Am I supposed to ***install*** to /home/user_name/.wine/c/Program\files\xxx.exe?
**Or is that where I copy an exe file to run?**

  **Or do I go to XP C,D,F, whatever Program Files\Program_Name\xxx.exe and then right click and use wine?**

  Confused is an understatement.

??????   ](*,) ](*,)

LOL :lol:

OK finger, quick review....

Step 1. Install wine.

Step 2. Configure or "set up" wine. This is what this post was about, no.

Step 3. Install a program. Lets call it program.exe. program.exe will be installed onto your fake c drive ~/.wine/c in Program Files, or ~/.wine/c/Program\ Files in Linux speak.

Now, to start progarm.exe:

From CLI (terminal):```
wine ~/.wine/c/Program\ Files/program.exe
```

To launch from the gui follow the above advice. [# 303](http://ubuntuforums.org/showpost.php?p=1625962&postcount=303) is best (Nice post Ticklemonster).

To add a menu item, desktop icon, or launcher, first create the item in question. During configuration you will be asked to enter the command to be run when this item is selected. use the same as the CLI. You may need to add quotes:```
'~/.wine/c/Program\ Files/program.exe'
```

---

### Post by joemacnz on 2006-10-18
Ok, I have read this thread through and I may have a unique problem. I have tried to get IE(and DCOM98) through both winetools and IE4Linux and never succeded because it allways times out. With wine tools I get the "downloading" tile and as far as I can tell it will stay there forever.With IE4Linux, it times out and trys again automaticaly and I have taken it to 20 trys before I give up. I have even tryed the download URL and that times out too. I have no problem downloading anything else but I am running through a router, Could that be the problem? Can anyone suggest anything? Thanks.

---

### Post by pgroover on 2006-10-18
> **joemacnz said:**
> Ok, I have read this thread through and I may have a unique problem. I have tried to get IE(and DCOM98) through both winetools and IE4Linux and never succeded because it allways times out. With wine tools I get the "downloading" tile and as far as I can tell it will stay there forever.With IE4Linux, it times out and trys again automaticaly and I have taken it to 20 trys before I give up. I have even tryed the download URL and that times out too. I have no problem downloading anything else but I am running through a router, Could that be the problem? Can anyone suggest anything? Thanks.

I remember having a timeout problem as well when I set mine up, but I was able to go to the URL and download the necessary files to .wine/c/Windows/System32.  I didn't have any problems with IE4Linux at all, in fact it was so easy I didn't even pay attention to what it was doing.  What files are you unable to get, maybe someone who is at their system can give an alternate location (I'm not at mine now).

---

### Post by joemacnz on 2006-10-18
Idealy, I would like I.E.6 in order to run games but I can't get DCOM98 which I need in order to get IE. I did manage to download DCOM98 from frostwire but not realy sure what to do with it then.In theory this winetools should do all that.

---

### Post by pgroover on 2006-10-19
> **joemacnz said:**
> Idealy, I would like I.E.6 in order to run games but I can't get DCOM98 which I need in order to get IE. I did manage to download DCOM98 from frostwire but not realy sure what to do with it then.In theory this winetools should do all that.

I know this has probably already been done, but have you tried removing all of it and reinstalling from scratch?  Do you have another system to check it with (the timeout that is)?  My laptop is in the shop and is the only one with wine, IE4Linux, etc installed so I can't do much else for you right now.  Anyone else have any ideas?

---

### Post by gasolino on 2006-10-19
Hello everyone,
     Thanks to gazj for writing this howto, its great! Anyway, there is really only one windows application I need to run. It's called Remedy, and I use it for my tech support job at school. Last time I installed Ubuntu Dapper, it installed perfectly under wine with no further setup than adding repositories and an apt-get install wine. However, I screwed up while playing around with the video drivers, and couldn't figure out how to fix it, so I reinstalled Ubuntu. Now, Remedy won't install. The App DB page says that it works perfectly, and is tested under Breezy.
[http://appdb.winehq.org/appview.php?iVersionId=1954]("http://appdb.winehq.org/appview.php?iVersionId=1954")
     The install starts going, but then while loading the installshield wizard files gives the following error in the terminal:
err:ntdll:RtlpWaitForCriticalSection section 0x65faf088 "?" wait timed out in thread 000e, blocked by 0010, retrying(60 sec)
Does ntdll mean that a DLL files is not being found? Anyone know anything about this kind of error or how I would go about fixing it?
Thanks

---

### Post by bodhi.zazen on 2006-10-19
> **gasolino said:**
> Hello everyone,
     Thanks to gazj for writing this howto, its great! Anyway, there is really only one windows application I need to run. It's called Remedy, and I use it for my tech support job at school. Last time I installed Ubuntu Dapper, it installed perfectly under wine with no further setup than adding repositories and an apt-get install wine. However, I screwed up while playing around with the video drivers, and couldn't figure out how to fix it, so I reinstalled Ubuntu. Now, Remedy won't install. The App DB page says that it works perfectly, and is tested under Breezy.
[http://appdb.winehq.org/appview.php?iVersionId=1954]("http://appdb.winehq.org/appview.php?iVersionId=1954")
     The install starts going, but then while loading the installshield wizard files gives the following error in the terminal:
err:ntdll:RtlpWaitForCriticalSection section 0x65faf088 "?" wait timed out in thread 000e, blocked by 0010, retrying(60 sec)
Does ntdll mean that a DLL files is not being found? Anyone know anything about this kind of error or how I would go about fixing it?
Thanks

What version of wine are you using? I would downgrade to 0.9.8

[[color=darkred] Wine-0.9.8, Ubuntu package[/color]](http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=174803&release_id=400655)

---

### Post by joemacnz on 2006-10-20
Quote:
Originally Posted by joemacnz View Post
Idealy, I would like I.E.6 in order to run games but I can't get DCOM98 which I need in order to get IE. I did manage to download DCOM98 from frostwire but not realy sure what to do with it then.In theory this winetools should do all that.
I know this has probably already been done, but have you tried removing all of it and reinstalling from scratch? Do you have another system to check it with (the timeout that is)? My laptop is in the shop and is the only one with wine, IE4Linux, etc installed so I can't do much else for you right now. Anyone else have any ideas?

I have tried getting rid of everything resembling DCOM98 that I got from peer2peer. This hasn't changed anything. I am trying the download now. It has been half an hour and the download tile still says downloading 0%. I have read somewhere about this app. timing out if you are running through a server but I don't think that I am.

---

### Post by joemacnz on 2006-10-20
This is what the terminal says:

joe@joe-desktop:~$ winetools
detecting Wine version... done.
Drive C: is /home/joe/.wine/drive_c
Wine 0.9.23
wine is executed as wine
Parameters are --noexit
Browser is /usr/bin/firefox.
WINEVER is "0.9.23".
Calls to wine are executed as  "wine".
Config is /home/joe/.wine/winetools.log.
Choice is Base setup
Choice is DCOM98 with checked=F
dcom98.exe to check
software installation verified by /home/joe/.wine/winetools.log
downloading [http://download.microsoft.com/download/d/1/3/d13cd456-f0cf-4fb2-a17f-20afc79f8a51/DCOM98.EXE](http://download.microsoft.com/download/d/1/3/d13cd456-f0cf-4fb2-a17f-20afc79f8a51/DCOM98.EXE) to dcom98.exe with 1229056 bytes...

---

### Post by pgroover on 2006-10-20
> **joemacnz said:**
> 
[http://download.microsoft.com/download/d/1/3/d13cd456-f0cf-4fb2-a17f-20afc79f8a51/DCOM98.EXE](http://download.microsoft.com/download/d/1/3/d13cd456-f0cf-4fb2-a17f-20afc79f8a51/DCOM98.EXE) to dcom98.exe with 1229056 bytes...

If you have downloaded dcom98.exe, run it with wine and it should install as necessary on it's own.  IOTW, browse to it with Nautilus, right click on it, and run it with wine.

---

### Post by joemacnz on 2006-10-20
That is the trouble I can't download DCOM98.  It says downloading, but it takes forever. Nothing happens.I have only ever been able to get it from Frostwire and what do I do with it then?

---

### Post by gasolino on 2006-10-21
> **bodhi.zazen said:**
> What version of wine are you using? I would downgrade to 0.9.8

[[color=darkred] Wine-0.9.8, Ubuntu package[/color]](http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=174803&release_id=400655)

Hey, thanks a lot for the suggestion. It makes it past loading the installshield wizard files with wine 0.9.8. However, once it makes it past that, it says that I appear to be running Windows 98, which is not a supported version. 
I went into winecfg and tried changing the windows version to ME, 2000, XP, 2003, and NT, and none of them worked right. ME got to the same point that 98 did, and then said that ME was not supported. NT, 2000, XP, and 2003 will not get past the initial installshield startup. Starting InstallShield Wizard.... comes up, and acts like it is doing something, but does not progress, and the terminal gives me no errors. It seems to be a problem with only the NT-based versions of Windows. Could I possibly need to update my wine InstallShield files? If so, how would I do that?

---

### Post by Aberrix on 2006-10-23
This appears to be broken now...

can anyone shed some light?

---

### Post by BLTicklemonster on 2006-10-23
> **Aberrix said:**
> This appears to be broken now...

can anyone shed some light?

Sorry, what is broken?

---

### Post by pgroover on 2006-10-23
> **Aberrix said:**
> This appears to be broken now...

can anyone shed some light?

What is broken...?

---

### Post by stansaraczewski on 2006-10-24
I'm a bit embarassed to ask, but will anyway: how do I change directory (CD) to Program Files ? No matter what I enter it cannot be found. There must be some sort of invisible joining character between Program and Files...

Sheesh...

---

### Post by Aberrix on 2006-10-24
> **BLTicklemonster said:**
> Sorry, what is broken?

It fails upon trying to install ie6

---

### Post by bodhi.zazen on 2006-10-24
> **stansaraczewski said:**
> I'm a bit embarassed to ask, but will anyway: how do I change directory (CD) to Program Files ? No matter what I enter it cannot be found. There must be some sort of invisible joining character between Program and Files...

Sheesh...

LOL :lol: Yes, Linux does not like the space in "Program Files".

You need to "escape" it with a \, like this: Program\ Files

---

### Post by stansaraczewski on 2006-10-24
Wow - how does one learn all these little tricks ?

(Thank You)

Another question that is challenging me now is how to install Windows programs on Wine. I've looked around and Winetools is mentioned, but there are warnings to not use with Dapper.

How to ?

---

### Post by bodhi.zazen on 2006-10-24
> **stansaraczewski said:**
> Wow - how does one learn all these little tricks ?

(Thank You)

Another question that is challenging me now is how to install Windows programs on Wine. I've looked around and Winetools is mentioned, but there are warnings to not use with Dapper.

How to ?

Just like in Windows: Trial and error, experience, reading.

For your applications, best information is at winehq. Go [here](http://appdb.winehq.org/) and enter your application in the gray search box on the Left.

You may want to look at this as well: [[color=darkred]How to wine[/color]](http://doc.gwos.org/index.php/HowToWine)

8-)

---

### Post by stansaraczewski on 2006-10-24
Yes, all of those are required for Linux or Windows related tasks. 

I've done a bit of it, but am out of time this morning and will definitely pursue the adventure this evening. 

Thanks again for your input.

---

### Post by BLTicklemonster on 2006-11-04
Microsoft foundation classes 4x will not download.

---

### Post by zek725 on 2006-11-04
I've installed Wine from the official Edgy repository.

```
sudo aptitude install wine
```

Installation went fine. However, clicking the AUDIO tab in winecfg returns this error.

```
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
Creating link /home/zek/.kde/socket-warrior2.
can't create mcop directory
```

Should I still follow this HOWTO?

Edit:
> **Eliseo said:**
> Found the solution here!:
[http://groups.google.nl/group/comp.emulators.ms-windows.wine/browse_thread/thread/4e0e59c7bb6c6410/2298146dcf72d61f](http://groups.google.nl/group/comp.emulators.ms-windows.wine/browse_thread/thread/4e0e59c7bb6c6410/2298146dcf72d61f)

I just had to do this:
```
mkdir -pv $HOME/.kde/socket-$HOSTNAME 
```

And voila! No more crashing!

IT WORKED! No longer crashes but terminal outputs these lines:

```
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
/bin/sh: /usr/bin/esd: not found
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory

```

**winecfg** tells me that there are no audio drivers installed/found in registry. It chose for me OSS. I think ALSA is more stable?

---

### Post by bodhi.zazen on 2006-11-04
Although I am not "up to date" on this issue, last time I checked wine did not work so well with ALSA, thus OSS.

---

### Post by BLTicklemonster on 2006-11-05
> **BLTicklemonster said:**
> Microsoft foundation classes 4x will not download.

koff koff anyone else experiencing this problem?

---

### Post by BLTicklemonster on 2006-11-07
Allow me to reiterate...

Anyone else having a problem downloading this?

> downloading [http://www.dlldump.com/dllfiles/M/mfc40.dll](http://www.dlldump.com/dllfiles/M/mfc40.dll) to mfc40.dll with 924432 bytes...


It just sits there saying downloading.
I can manually download mfc40 and 42.dll, and put them in windows/system, but what else can I do to make this step work?

---

### Post by Onomatopoetikon on 2006-11-08
> **BLTicklemonster said:**
> Allow me to reiterate...

Anyone else having a problem downloading this?


It just sits there saying downloading.
I can manually download mfc40 and 42.dll, and put them in windows/system, but what else can I do to make this step work?

EDIT; Figured it out.

The part about the missing font links gives a hint, (btw., they're not missing anymore, just follow the winetools menu and everything goes fine, even the Arial font ;) ).

Go to the [http://www.dlldump.com/dllfiles/M/](http://www.dlldump.com/dllfiles/M/) site, search the page for mfc4* and download mfc40.dll and mfc42.dll to ~/winetools/sys then go with winetools again, and it should install nicely.

---

### Post by jejones3141 on 2006-11-08
> **BLTicklemonster said:**
> koff koff anyone else experiencing this problem?

Indeed I am. OTOH, I can manually download the mfc40.dll file that the diagnostic output to the terminal says it's trying to grab, and put it in ~/.wine/dosdevices/c:/windows/system32. Will that suffice to make wine happy?

---

### Post by BLTicklemonster on 2006-11-09
> **jejones3141 said:**
> Indeed I am. OTOH, I can manually download the mfc40.dll file that the diagnostic output to the terminal says it's trying to grab, and put it in ~/.wine/dosdevices/c:/windows/system32. Will that suffice to make wine happy?

> **Onomatopoetikon said:**
> EDIT; Figured it out.

The part about the missing font links gives a hint, (btw., they're not missing anymore, just follow the winetools menu and everything goes fine, even the Arial font ;) ).

Go to the [http://www.dlldump.com/dllfiles/M/](http://www.dlldump.com/dllfiles/M/) site, search the page for mfc4* and download mfc40.dll and mfc42.dll to ~/winetools/sys then go with winetools again, and it should install nicely.

I'll try that. Thanks

---

### Post by pgroover on 2006-11-09
> **jejones3141 said:**
> Indeed I am. OTOH, I can manually download the mfc40.dll file that the diagnostic output to the terminal says it's trying to grab, and put it in ~/.wine/dosdevices/c:/windows/system32. Will that suffice to make wine happy?

That's what I did and everything has worked fine so far (or at least as expected with windows apps).

---

### Post by joemacnz on 2006-11-09
I still can't download DCOM98 or IE. The tile says downloading but nothing happens. Ever. Can anyone help? I am running dapper(only).

---

### Post by bodhi.zazen on 2006-11-09
I am not 100 % sure, but I do not think you need to download DCOM98 any longer.

For IE go here (free download) [IE](http://www2.kansas.net/download.asp)

---

### Post by CowzRule on 2006-11-09
> **newpants2003 said:**
> when install the ie(sp1) it tells me   mfc40.dell   not installed yet.  and i chose to keep going, then it tells me install fail. thats where the falls start.

and also my windows are in E:/ , but looks like the wt defaul to looking in C:/ , then tells me could not find the file it need, then falls. 

Wine is finalizing your software installation. This may take a few minutes,
though it never actually does.
err:exec:SHELL_ExecuteW cannot set directory L"c:\\windows\\system32\\shell32.dll"
err:exec:SHELL_ExecuteW cannot set directory L"c:\\windows\\system32\\shell32.dll"
err:exec:SHELL_ExecuteW cannot set directory L"c:\\windows\\system32\\shell32.dll"
err:exec:SHELL_ExecuteW cannot set directory L"c:\\windows\\system32\\shell32.dll"
err:exec:SHELL_ExecuteW cannot set directory L"c:\\windows\\system32\\shell32.dll"
err:exec:SHELL_ExecuteW cannot set directory L"c:\\windows\\system32\\shell32.dll"
err:module:import_dll Library MFC40.DLL (which is needed by L"C:\\Program Files\\Common Files\\Microsoft Shared\\MSInfo\\ieinfo5.ocx") not found
err:exec:SHELL_ExecuteW cannot set directory L"c:\\windows\\system32\\shell32.dll"
err:exec:SHELL_ExecuteW cannot set directory L"c:\\windows\\system32\\shell32.dll"
Registration of c:\windows\system32\StdOle2.Tlb successful.


how to solve the problem?

Try downloading [mfc40.dll]("http://www.dll-files.com/dllindex/dll-files.shtml?mfc40"), [mfc42.dll]("http://www.dll-files.com/dllindex/dll-files.shtml?mfc42")  & [shell32.dll]("http://www.dll-files.com/dllindex/dll-files.shtml?shell32") then put the file in your "c:\windows\system32" and try again.

---

### Post by BLTicklemonster on 2006-11-09
I did as you said, and I still get this

err:exec:SHELL_ExecuteW cannot set directory L"c:\\windows\\system32\\shell32.dll"

---

### Post by pgroover on 2006-11-10
> **BLTicklemonster said:**
> I did as you said, and I still get this

err:exec:SHELL_ExecuteW cannot set directory L"c:\\windows\\system32\\shell32.dll"

Have you tried '/home/username/.wine/c/windows/system32'?

---

### Post by BLTicklemonster on 2006-11-10
I forged on past that problem, and finished running winetools, and wine works well enough now. I haven't seen any problems. Installed Unreal Tournament, and played it last night.

---

### Post by pgroover on 2006-11-10
> **BLTicklemonster said:**
> I forged on past that problem, and finished running winetools, and wine works well enough now. I haven't seen any problems. Installed Unreal Tournament, and played it last night.

Glad to hear everything is working for you, now if I can just get Zinio working we can all be happy. :D

---

### Post by gorkur on 2006-11-10
I followed the HOWTO and now I get this error everytime I try to use wine.

```
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  14
  Current serial number in output stream:  15
```

Any ideas? :-k

EDIT: This error also comes when I try to use winecfg

---

### Post by pgroover on 2006-11-10
> **gorkur said:**
> I followed the HOWTO and now I get this error everytime I try to use wine.

```
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  14
  Current serial number in output stream:  15
```

Any ideas? :-k

EDIT: This error also comes when I try to use winecfg

What exactly do you mean by trying to use wine?  It seems like there's a graphics memory problem from what's shown, but that's just a guess.  What type of system do you have, it may also be a driver issue but that's another guess.

---

### Post by gorkur on 2006-11-10
> **pgroover said:**
> What exactly do you mean by trying to use wine?  It seems like there's a graphics memory problem from what's shown, but that's just a guess.  What type of system do you have, it may also be a driver issue but that's another guess.

Well, what I mean is that this error comes up everytime I try to use wine ;)

At first I tried to run Internet Explorer and got this error. Same result with both Outlook Express and Civ2. (Got IE and OE via winetools).

I'm guessing something must've gone wrong after using winetools since I tried to run Civ2 prior to using winetools and got the startup screen (scenario selection, difficulty etc). However I didn't get into the actual game.

System Specs are
AMD Athlon 2.2 Ghz
768 MB RAM
Geforce FX5200 128MB RAM
And the motherboard is some VIA POS

EDIT: Seems to be working now. Otherwise I'll come back and bug you guys :)
;)
Thanks :D

---

### Post by pgroover on 2006-11-10
> **gorkur said:**
> 
EDIT: Seems to be working now. Otherwise I'll come back and bug you guys :)
;)
Thanks :D

Glad to hear it!  If it gets silly again, the only thing that may work right away is to remove it and reinstall it.  If you do want to uninstall it the simplest method would be to just rename the .wine directory to something else (.wine.old) that you may prefer.  Then just reinstall it from there and you can then compare settings if it works properly and then possibly track down the original problem.

---

### Post by Aurora on 2006-11-10
Hi,

I just ran through that lengthy insallation, and everything seemed to install without a hitch.  But if I try double-clicking on any .exe files, nothing happens.  When I try it in the command line, I get "no such file as Program".  Should I type ProgramFiles, with no space?  In the file manager (Thunar, the default in Xubuntu) the folder says "Program Files", with the space.

Any ideas?

Paul DeShaw
Xubuntu Dapper 32 bit (so I can run Flash and Opera)
AMD 64
1GB RAM

---

### Post by bodhi.zazen on 2006-11-10
The command is something like this (in a terminal)
```
wine ~/.wine/c/Program\ Files/program.exe
```

"Program Files" (Windows) becomes "Program\ Files" (Linux)

You can then create a launcher and use this command in the command box.

---

### Post by Aurora on 2006-11-11
Here is the result:

pad@Aurora2:~$ /home/pad/.wine/c/Program\Files/Internet\Explorer/IEXPLORE.EXE
bash: /home/pad/.wine/c/ProgramFiles/InternetExplorer/IEXPLORE.EXE: No such file or directory

When I navigate in Thunar, I can see IEXPLORE.EXE .  Clicking or double clicking does nothing.

--P

---

### Post by bodhi.zazen on 2006-11-11
> **Aurora said:**
> Here is the result:

pad@Aurora2:~$ /home/pad/.wine/c/Program\Files/Internet\Explorer/IEXPLORE.EXE
bash: /home/pad/.wine/c/ProgramFiles/InternetExplorer/IEXPLORE.EXE: No such file or directory

When I navigate in Thunar, I can see IEXPLORE.EXE .  Clicking or double clicking does nothing.

--P

You need to add "wine" in front of the command, like this
```
pad@Aurora2:~$**[color=blue]wine**[/color] /home/pad/.wine/c/Program\ Files/Internet\Explorer/IEXPLORE.EXE
```_Note_: Watch the space between "wine" and "/home/...." and in "Program\ Files"

---

### Post by Aurora on 2006-11-11
OK...

pad@Aurora2:~$ wine /home/pad/.wine/c/Program\Files/Internet\Explorer/IEXPLORE.EXE
wine: cannot find '/home/pad/.wine/c/ProgramFiles/InternetExplorer/IEXPLORE.EXE'

ls doesn't find it:
pad@Aurora2:~$ ls /home/pad/.wine/c/Program\Files/Internet\Explorer/
ls: /home/pad/.wine/c/ProgramFiles/InternetExplorer/: No such file or directory

Backing up the file path:

pad@Aurora2:~$ ls /home/pad/.wine
c           drive_c       installed-software        system.reg   user.reg
dosdevices  fake_windows  quiet-installed-software  userdef.reg  winetools.log

But:

pad@Aurora2:~$ ls /home/pad/.wine/Program\Files
ls: /home/pad/.wine/ProgramFiles: No such file or directory

---

### Post by bodhi.zazen on 2006-11-11
> **Aurora said:**
> OK...

pad@Aurora2:~$ wine /home/pad/.wine/c/Program\Files/Internet\Explorer/IEXPLORE.EXE
wine: cannot find '/home/pad/.wine/c/ProgramFiles/InternetExplorer/IEXPLORE.EXE'
Needs a space "Program\ Files"

> ls doesn't find it:
pad@Aurora2:~$ ls /home/pad/.wine/c/Program\Files/Internet\Explorer/
ls: /home/pad/.wine/c/ProgramFiles/InternetExplorer/: No such file or directory
Needs a space "Program\ Files"

> Backing up the file path:

pad@Aurora2:~$ ls /home/pad/.wine
c           drive_c       installed-software        system.reg   user.reg
dosdevices  fake_windows  quiet-installed-software  userdef.reg  winetools.log
So far so good ....

> But:

pad@Aurora2:~$ ls /home/pad/.wine/Program\Files
ls: /home/pad/.wine/ProgramFiles: No such file or directory
No, no
should be ls /home/pad/.wine/**[color=red]c/Program\ Files**[/color]
See below:

LOL :lol: it is all I big typo.  sorry, I just cut and pated your command !

Try this one:
```
wine /home/pad/.wine/c/Program\ Files/Internet\Explorer/IEXPLORE.EXE
```

_Note_: you need a space in "Program\ Files"

---

### Post by bodhi.zazen on 2006-11-11
Do you know tab completion?

Start typing the path, <tab> will fill in...

/ho<tab> becomes /home

/ho<tab>pa<tab>.wine/c/Pro<tab>/Int<tab>IEXP<tab>

Likely becomes "/home/pad/.wine/c/Program\ Files/Internet\Explorer/IEXPLORE.EXE" on expansion (tab completion) !

Live long and prosper.

---

### Post by manifoldronin on 2006-11-11
Hi all,

I'm trying to get wine working in my new Edgy installation. After installing wine 0.9.22 from synaptic, winecfg always fails:
```

wine: creating configuration directory '/home/user/.wine'...
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  144 (NV-GLX)
  Minor opcode of failed request:  4 ()
  Resource id in failed request:  0x24a
  Serial number of failed request:  19
  Current serial number in output stream:  19

wine: wineprefixcreate failed while creating '/home/user/.wine'.

wineserver: could not save registry branch to /home/user/.wine-V6Fn35/system.reg : No such file or directory
wineserver: could not save registry branch to /home/user/.wine-V6Fn35/user.reg : No such file or directory

```

I'm using nvidia-glx (6800GT).  I googled this and found a few other folks having similar problems but nobody seemed to have got it working.

---

### Post by Aurora on 2006-11-11
> **bodhi.zazen said:**
> Needs a space "Program\ Files"

...And Internet\ Explorer as well.  So I guess the rule is, for \X<space>Y\ in Windows, its /X\<space>Y/ in Linux.

I have IE up and running right now.  Not that I want it; it was a dependency.

I will experiment with that <tab> completion thing too.

IIRC, DOS used to tell you when you had a syntax error.

LOL thought I was done with the command line forever, thanks to Mac and Windows.

/Thank/You/Very\ Much/

PAD

---

### Post by bodhi.zazen on 2006-11-11
> **Aurora said:**
> ...And Internet\ Explorer as well.  So I guess the rule is, for \X<space>Y\ in Windows, its /X\<space>Y/ in Linux.

I have IE up and running right now.  Not that I want it; it was a dependency.

I will experiment with that <tab> completion thing too.

IIRC, DOS used to tell you when you had a syntax error.

LOL thought I was done with the command line forever, thanks to Mac and Windows.

/Thank/You/Very\ Much/

PAD

:p

Or you can enclose the path in " ". Like this:
> wine "/home/bodhi/.wine/c/Program Files/Internet Explorer/iexplore.exe"

---

### Post by pgroover on 2006-11-12
> **Aurora said:**
> 
IIRC, DOS used to tell you when you had a syntax error.

LOL thought I was done with the command line forever, thanks to Mac and Windows.


Actually they provide the same error "path doesn't exist" as the system can't really know where you've placed things.  Regardless, the command line lives forever.  :D

---

### Post by elcasey on 2006-11-12
Got Wine installed via this HOWTO and the discussion (cursory that it is) of it in *Ubuntu Linux for Non-Geeks* (decent book, actually).

When I upgraded to 0.9.25 Internet Explorer stopped working, and Media Player and OL Express wouldn't load, either. I downgraded, got IE working again, and downloaded Firefox.

When I try to install Firefox in "C:\Program Files" it tells me I don't have enough free space. What irks the hell out of me is that it shows 18.7MB necessary for install and, in the Windows installer, tells me I have 75.9GB of free space!

So what gives?! How do I install *anything* for Wine? The only real reason I'm wanting to run Wine is for some DVD applications (rip/shrink) and for a math program I use. It requires both Windows and IE6 (IE7 broke it; no shock there) but I don't run Windows anywhere anymore!

Help is much appreciated as installation of the math app is fairly important. Everything else I don't care so much about, especially if Wine is going to be so finicky.

---

### Post by Suavsilk on 2006-11-13
I followed this how-to word for word and got everything to work fine ^_^

untill i ran the :

```
sudo apt-get update
sudo apt-get upgrade
```

now it all dosnt work... clicking .exe's, the shortcuts i put on my desktop to run IE, Outlook and WMP

how can i revert back to b4 i updated?

it should be noted that im runing on Edgy

---

### Post by elcasey on 2006-11-13
That's the exact same problem I had. You can revert by doing a "wget http://xxx" like you did for the original package. When you unpack it it'll give you a warning about downgrading. You won't have to go through all the Base Setup stuff again.

But you may have problems installing things, like I did, although I still haven't gotten word on what may be causing that. I hate to have to use a Windows box for a single app. :confused:

---

### Post by Suavsilk on 2006-11-13
ok i ran code

```
 wget http://kent.dl.sourceforge.net/sourceforge/wine/wine_0.9.5-winehq-1_i386.deb
```

```
sudo dpkg -i wine*.deb
```

and im back to the old version, i can run the desktop links but cant run .exe's still

i think i somehow need to specify that Wine is the app to open .exe's with, but when i try to do this with 'right click > open with another app' Wine isnt on the list.

is there a way to do this through good ol terminal?

---

### Post by Suavsilk on 2006-11-13
I found that i could add the application im trying to run using winecfg

but i still get this error:

[IMG]http://i21.photobucket.com/albums/b255/Suavsilk/Screenshot-1.png[/IMG]

---

### Post by bodhi.zazen on 2006-11-13
> **Suavsilk said:**
> is there a way to do this through good ol terminal?

```
wine "/home/user_name/.wine/c/Program Files/World of Warcraft/Launcher.exe"
```

Or something to that effect. The part between /home and /World of Warcraft is all a blurr :)

You can add a menu item/launcher with this as the command.

---

### Post by elcasey on 2006-11-14
That didn't answer "our" question about Wine breaking "everything" once we upgraded to the latest version, however. I only need Wine to work for an app which requires Flash and IE6, but I can't even install Firefox under Wine.

Why? That's my only question (see above for reasons). :(

---

### Post by BLTicklemonster on 2006-11-14
Huh. Yeah, I noticed last night that I can't launch and executable like I used to could. I have to open winefile from the terminal, then navigate to the exe file and launch from there. What's up with wine all of a sudden, or is it the mfc*.dll problem which is causing this?

---

### Post by bodhi.zazen on 2006-11-14
> **elcasey said:**
> That didn't answer "our" question about Wine breaking "everything" once we upgraded to the latest version, however. I only need Wine to work for an app which requires Flash and IE6, but I can't even install Firefox under Wine.

Why? That's my only question (see above for reasons). :(

I launch from the CLI and have made menu enteries for my proggies and have had no problems, not that this helps you with your problem, but it may be a potential solution.

Perhaps try IRC, #winehq

Or: [IRC winehq](irc://irc.freenode.net/#winehq)

PS: This is a problem with wine and users call it "regression". IMO this is what makes wine "alpha" and why, with wine, newer is not usually better. If you have a working version of wine consider not upgrading.

---

### Post by elcasey on 2006-11-14
Hm...I've been launching Wine via [FONT="Courier New"]wine "/home/~/.wine/c/Program Files/..."[/FONT] and it runs IE fine. I haven't tried OE or Media Player since I downgraded again (I'll never use either of them, anyway).

The app I need to run installs some user files on the HDD, then opens IE, connects to the server (it serves a large number of colleges), then runs a Flash applet where the actual work takes place. If I can get this running (and maybe DVDShrink) I'll be a happy boy.

I'll try the IRC channel and I'm going to try to attend the local LUG meeting tonight, so maybe those guys can help me as well. Thanks for the IRC link!

---

### Post by jingo811 on 2006-11-14
By following this super fine tutorial, I only get to the part when starting
wt and installing docom98.....then when I tries to install 
**Base Setup==> Microsoft Foundation Classes 4.x** the downloader just sits at 0% for several minutes it seems like it can't connect to the download server.  How can I remedy this?

Maybe this question has already been solved for that I'm sorry.  But I really tried to read all the posts from the very beginning.  But when I got to page 21 without reading anything that could help me much I simply got tired and warped to page 31 read some pages and then jumped to the very end :rolleyes:

---

### Post by bodhi.zazen on 2006-11-14
> **jingo811 said:**
> By following this super fine tutorial, I only get to the part when starting
wt and installing docom98.....

With newer versions of wine I do not think you need to install docm98.

Just proceed without it and see what happens.

---

### Post by BLTicklemonster on 2006-11-14
> **jingo811 said:**
> By following this super fine tutorial, I only get to the part when starting
wt and installing docom98.....then when I tries to install 
**Base Setup==> Microsoft Foundation Classes 4.x** the downloader just sits at 0% for several minutes it seems like it can't connect to the download server.  How can I remedy this?

Maybe this question has already been solved for that I'm sorry.  But I really tried to read all the posts from the very beginning.  But when I got to page 21 without reading anything that could help me much I simply got tired and warped to page 31 read some pages and then jumped to the very end :rolleyes:

> **CowzRule said:**
> Try downloading [mfc40.dll]("http://www.dll-files.com/dllindex/dll-files.shtml?mfc40"), [mfc42.dll]("http://www.dll-files.com/dllindex/dll-files.shtml?mfc42")  & [shell32.dll]("http://www.dll-files.com/dllindex/dll-files.shtml?shell32") then put the file in your "c:\windows\system32" and try again.

:)

---

### Post by elcasey on 2006-11-14
Mine still sits at "Downloading 0%" forever, although the Terminal is showing that WineTools is trying to download MFC40.dll from "dlldump.com."

Should I just upgrade to the latest Wine anyway if the Foundation Classes is just those three DLLs? I downloaded them manually using the links above (thanks!) and moved them to the system32 folder. I'm upgrading now, so I'll let everyone know how it goes when it's finished.

EDIT:
Nope, mega-broke now.

I entered ```
wine "/home/ch/.wine/c/Program Files/Internet Explorer/IEXPLORE.EXE"
```
and saw the following returned:
```
fixme:shell:StopWatchMode () stub!
fixme:shdocvw:IEWinMain "" 10
fixme:rpc:alloc_serverprotoseq protseq "mswmsg" not supported
err:shdocvw:register_class_object failed to register object 800706a7
fixme:rpc:I_RpcServerStopListening (): stub
fixme:rpc:I_RpcWindowProc (0x10024,00000002,00000000,00000000): stub
fixme:rpc:I_RpcWindowProc (0x10024,00000082,00000000,00000000): stub
fixme:rpc:RpcServerUnregisterIf (IfSpec == (RPC_IF_HANDLE)^0x18dd10, MgrTypeUuid == (null), WaitForCallsToComplete == 1): stub
```

Wine has one more chance to work before I classify it as ridiculously useless.

---

### Post by jingo811 on 2006-11-17
> Try downloading mfc40.dll, mfc42.dll & shell32.dll then put the file in your "c:\windows\system32" and try again.
So I copied those file to "drive_c\windows\system32" and discovered that there are other folders under ".wine" , "fake_windows" and "c"but it seems like copying the files to "drive_c" affected them all.  So I guess nothing got broken at this stage, but are you supposed to have 3 identical branches but with different name as I have mentioned (drive_c, fake_windows, c) ??

Anyhow I installed those files, ignored clicking on 
Base Setup==> **Microsoft Foundation Classes 4.x**
and continued with the installation but got this error popup when installing **IE6**: 
> This software depends on "mfc40.dll".
Your config file states that you have not installed "mfc40.dll" yet.  In that case you will not be able to install the desired software.
Continue anyway?

[Yes]	[No]
So it says I have not copied those files to the windows/system32 folder which I already have.  Should I be worry or just ignore this?

I don't know what else to say other than showing the whole log until this IE6 stage:
```
mike@mike-shark:~$ wt
detecting Wine version... done.
Drive C: is /home/mike/.wine/drive_c
Wine 0.9.5
wine is executed as wine
Parameters are --noexit
Browser is /usr/bin/firefox.
WINEVER is "0.9.5".
Calls to wine are executed as  "wine".
Config is /home/mike/.wine/winetools.log.
Choice is Base setup
Choice is DCOM98 with checked=F
dcom98.exe to check
software installation verified by /home/mike/.wine/winetools.log
dcom98.exe = installed at 17.11.2006 17:48:29
Choice is Internet Explorer 6.0 SP1 English with checked=F
dcom98.exe to check
software installation verified by /home/mike/.wine/winetools.log
dcom98.exe = installed at 17.11.2006 17:48:29
dependency dcom98.exe fulfilled
mfc40.dll to check
software installation verified by /home/mike/.wine/winetools.log
dependency mfc40.dll *not* fulfilled
using english setup...
sytempath=/home/mike/.wine/dosdevices/c:/windows/system32
Microsoft Internet Explorer.* to check
Microsoft Internet Explorer 6 SP1 and Internet Tools
software installation verified by registry value
491768 bytes previously downloaded
WINEDEBUG="fixme-all" WINEDLLOVERRIDES="" wine ./ie6setup.exe
waiting for wineservers to exit...
err:setupapi:SetupDefaultQueueCallbackA copy error 32 "C:\\windows\\msdownld.tmp \\AS002BEA.tmp\\mscrlrev.dll" -> "c:\\windows\\system32\\mscrlrev.dll"
Microsoft (R) Cabinet Extraction Tool - Version (32G) 4.11.0610.0 (03/31/99)
Copyright (c) Microsoft Corp 1994-1999. All rights reserved.

 Cabinet mui.cab

Extracting c:\windows\system32\mui\0401\hhctrlui.dll
Extracting c:\windows\system32\mui\0403\hhctrlui.dll
Extracting c:\windows\system32\mui\0404\hhctrlui.dll
Extracting c:\windows\system32\mui\0405\hhctrlui.dll
Extracting c:\windows\system32\mui\0406\hhctrlui.dll
Extracting c:\windows\system32\mui\0407\hhctrlui.dll
Extracting c:\windows\system32\mui\0408\hhctrlui.dll
Extracting c:\windows\system32\mui\0409\hhctrlui.dll
Extracting c:\windows\system32\mui\040B\hhctrlui.dll
Extracting c:\windows\system32\mui\040C\hhctrlui.dll
Extracting c:\windows\system32\mui\040D\hhctrlui.dll
Extracting c:\windows\system32\mui\040E\hhctrlui.dll
Extracting c:\windows\system32\mui\0410\hhctrlui.dll
Extracting c:\windows\system32\mui\0412\hhctrlui.dll
Extracting c:\windows\system32\mui\0413\hhctrlui.dll
Extracting c:\windows\system32\mui\0414\hhctrlui.dll
Extracting c:\windows\system32\mui\0415\hhctrlui.dll
Extracting c:\windows\system32\mui\0416\hhctrlui.dll
Extracting c:\windows\system32\mui\0419\hhctrlui.dll
Extracting c:\windows\system32\mui\041B\hhctrlui.dll
Extracting c:\windows\system32\mui\041D\hhctrlui.dll
Extracting c:\windows\system32\mui\041F\hhctrlui.dll
Extracting c:\windows\system32\mui\0424\hhctrlui.dll
Extracting c:\windows\system32\mui\042D\hhctrlui.dll
Extracting c:\windows\system32\mui\0804\hhctrlui.dll
Extracting c:\windows\system32\mui\0816\hhctrlui.dll
Extracting c:\windows\system32\mui\040A\hhctrlui.dll
Extracting c:\windows\system32\mui\0411\hhctrlui.dll
err:setupapi:SetupDefaultQueueCallbackA copy error 32 "C:\\windows\\msdownld.tmp \\AS009530.tmp\\OLEAUT32.DLL" -> "c:\\windows\\system32\\OLEAUT32.DLL"
all wineservers endet after 37 seconds...
Failed: 194
check installation by path or registry value...
waiting for wineservers to exit...
all wineservers endet after 0 seconds...
Microsoft Internet Explorer.* to check
Microsoft Internet Explorer 6 SP1 and Internet Tools
software installation verified by registry value
Failed: 0
There is already a script called ie6 in /home/mike/bin...
There is already a script called outlookexpress in /home/mike/bin...
There is already a script called wmplayer in /home/mike/bin...
Failed: 0
installing new registry...
waiting for wineservers to exit...
all wineservers endet after 0 seconds...
waiting for wineservers to exit...
all wineservers endet after 2 seconds...
Wine is finalizing your software installation. This may take a few minutes,
though it never actually does.
err:exec:SHELL_ExecuteW cannot set directory L"c:\\windows\\system32\\shell32.dl l"
err:exec:SHELL_ExecuteW cannot set directory L"c:\\windows\\system32\\shell32.dl l"
err:exec:SHELL_ExecuteW cannot set directory L"c:\\windows\\system32\\shell32.dl l"
err:exec:SHELL_ExecuteW cannot set directory L"c:\\windows\\system32\\shell32.dll"
err:exec:SHELL_ExecuteW cannot set directory L"c:\\windows\\system32\\shell32.dll"
err:exec:SHELL_ExecuteW cannot set directory L"c:\\windows\\system32\\shell32.dll"
err:exec:SHELL_ExecuteW cannot set directory L"c:\\windows\\system32\\shell32.dll"
err:exec:SHELL_ExecuteW cannot set directory L"c:\\windows\\system32\\shell32.dll"
Registration of c:\windows\system32\StdOle2.Tlb successful.
mv: cannot stat `/home/mike/.wine/dosdevices/c:/windows/system32/regsvr32.exe': No such file or directory
```

However every step from:
installing all**windows system software** to Visualbasic5/6 to the fonts wen't incredibly smooth.  I'm surprised that Windows still lets us access those files so easily :-)  I even got IE6 with Java to work!
But from all the error mentioned above should I be worried about future program installations or can I just ignore the errors and brush it off my shoulders??

---

### Post by jingo811 on 2006-11-17
**elcasey>>>**
> I downloaded them manually using the links above (thanks!) and moved them to the system32 folder.
Did you remember to extract those three downloaded files before copying them to system32 folder?  I didn't the first time because of my excitement so I simply forgot they were zip files so nothing much happened.

But as you can see from my above post doing so still gives me a bunch of error messages and negative popups.  However I saw that your error message didn't look alike mine so maybe this little thing does something good :-k

---

### Post by joemacnz on 2006-11-17
I have never had much joy with wine but now I have a new problem. On trying to run winetools, I get:

"Winetools cannot run with a wine version older than 20050628"

Sounds fair, however,

"joe@joe-desktop:~$ wine --version
wine-0.9.25"


So now what?

---

### Post by vanishedsoul on 2006-11-17
hi, i am trying to instal wine on the 64 bit version of UBUNTU (6.06) ut he procedure explained here:\

[http://wiki.winehq.org/WineOn64bit](http://wiki.winehq.org/WineOn64bit)

as soon as i give this coomand 
**sudo apt-get install libfreetype6-dev**

i get the following error:

[B]gangsta@gangsta-desktop:~$ sudo apt-get install libfreetype6-dev
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
gangsta@gangsta-desktop:~$[/B]

i'm a newbie and can't solve this problem??Any help...

---

### Post by pgroover on 2006-11-18
> **vanishedsoul said:**
> [B]E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
gangsta@gangsta-desktop:~$[/B]

i'm a newbie and can't solve this problem??Any help...

Not quite sure but a quick guess says that it sounds as if you're running either adept, aptitude or Automatix at the same time you're attempting the install.

---

### Post by vanishedsoul on 2006-11-18
> **pgroover said:**
> Not quite sure but a quick guess says that it sounds as if you're running either adept, aptitude or Automatix at the same time you're attempting the install.

so any solution for this??

---

### Post by pgroover on 2006-11-18
> **vanishedsoul said:**
> so any solution for this??

Close any of them if they are running, if you're not running them, then I don't really know.

---

### Post by vanishedsoul on 2006-11-18
> **pgroover said:**
> Close any of them if they are running, if you're not running them, then I don't really know.

none of then is running...please any one help me out:


i'm trying to instal wine on the 64 bit version of UBUNTU (6.06) ut he procedure explained here:\

[http://wiki.winehq.org/WineOn64bit](http://wiki.winehq.org/WineOn64bit)

as soon as i give this coomand
sudo apt-get install libfreetype6-dev

i get the following error:

gangsta@gangsta-desktop:~$ sudo apt-get install libfreetype6-dev
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
gangsta@gangsta-desktop:~$

i'm a newbie and can't solve this problem??Any help...

---

### Post by pgroover on 2006-11-18
> **vanishedsoul said:**
> none of then is running...please any one help me out:


It could be that one of them is still running from an earlier attempt, try this command in a terminal "ps -x|grep apt" or "ps -x|grep synaptic".  If a process id is returned try "kill -9 pid" where pid = process id returned from the prior commands.  Bear in mind that you will get a process id returned for both of those commands, what you're looking for is a process id that isn't one of them.

Try here for some suggestions as well: [http://www.linuxquestions.org/questions/showthread.php?t=360554]("http://www.linuxquestions.org/questions/showthread.php?t=360554").

---

### Post by vanishedsoul on 2006-11-18
i got this: ( the link you gave, didnt helped too)

[B]gangsta@gangsta-desktop:~$ ps -x|grep apt
Warning: bad ps syntax, perhaps a bogus '-'? See [http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)
 9551 pts/0    S+     0:00 grep apt
gangsta@gangsta-desktop:~$ ps -x|grep synaptic
Warning: bad ps syntax, perhaps a bogus '-'? See [http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)
 9566 pts/0    S+     0:00 grep synaptic
gangsta@gangsta-desktop:~$ killall -w aptget
aptget: no process killed[/B]

thanks for your patience

---

### Post by RichieRich on 2006-11-18
> **elcasey said:**
> I downloaded them manually using the links above (thanks!) and moved them to the system32 folder.

I had the exact same problem. I somehow got it to work by copying the files as follows.

mfc40.dll and mfc42.dll to /home/(my username)/winetools/sys

shell32.dll to system32

I did this during the installation when winetools complained and ran that bit again and it stopped complaining.

---

### Post by BLTicklemonster on 2006-11-18
What gets me, is that up until a couple of weeks ago, everything about this tutorial worked right on the money. What has changed since then?

---

### Post by pgroover on 2006-11-18
> **BLTicklemonster said:**
> What gets me, is that up until a couple of weeks ago, everything about this tutorial worked right on the money. What has changed since then?

I agree with you completely as I used it myself to install and it went flawlessly, with the exception of the dlls.  I know there have been quite a few wine updates since then but the version that is available per the instructions has not changed.

Strange...

---

### Post by elementadiobam on 2006-11-19
The command for running wine programs from your desktop doesn't work for me. It doesn't want to start the program when I do that.

---

### Post by bodhi.zazen on 2006-11-19
> **elementadiobam said:**
> The command for running wine programs from your desktop doesn't work for me. It doesn't want to start the program when I do that.

What command are you typing exactly and what error message?

Otherwise it is quite difficult to assist you...

---

### Post by elementadiobam on 2006-11-19
I was typing

> Code:
wine C:\\Apps\\Keyboarding\ Pro\\kbpro.exe

It worked in the terminal but now when I did the create a launcher. I just converted my friend to linux and I want it to be easier for him so I want to make him a shortcut for the program on his desktop so he doesn't have to type commands all the time.

---

### Post by bodhi.zazen on 2006-11-19
> **elementadiobam said:**
> I was typing



It worked in the terminal but now when I did the create a launcher. I just converted my friend to linux and I want it to be easier for him so I want to make him a shortcut for the program on his desktop so he doesn't have to type commands all the time.

I suspect the problem is the use of \ Linux uses /

\ is to escape white space (spaces). ie Program\ Files 

Try using the full path to the application in the launcher:

wine /home/user_name/.wine/c/Apps/Keyboarding\ Pro/kbpro.exe

You may need to put the path in quotes:

wine "/home/user_name/.wine/c/Apps/Keyboarding Pro/kbpro.exe"

---

### Post by FrankVdb on 2006-11-20
I have a question: has the howto been updated since it was written?

It's full of broken links...

(bit reluctant to wade through 40 pages to find out)

Thanx.

---

### Post by elcasey on 2006-11-20
> **jingo811 said:**
> 
Did you remember to extract those three downloaded files before copying them to system32 folder?  I didn't the first time because of my excitement so I simply forgot they were zip files so nothing much happened.
Hehehe, I was pretty excited myself, but I did remember to unzip them before I copied them to the directory.

Is Wine seriously hardware-dependent? It doesn't make sense that it would be, since basically any PC on the planet can run Windoze (although at least those of us here choose not to). I've basically given up on Wine, though. If I can't get it running well enough to even install Firefox under Wine, then what's the point? :(

---

### Post by pgroover on 2006-11-20
> **elcasey said:**
> Hehehe, I was pretty excited myself, but I did remember to unzip them before I copied them to the directory.

Is Wine seriously hardware-dependent? It doesn't make sense that it would be, since basically any PC on the planet can run Windoze (although at least those of us here choose not to). I've basically given up on Wine, though. If I can't get it running well enough to even install Firefox under Wine, then what's the point? :(

I can understand your frustration when the installation for wine doesn't work, but why would you want to install Firefox with wine when it's native to Linux anyway?  :-?

---

### Post by jingo811 on 2006-11-20
> **BLTicklemonster: wrote;**
What gets me, is that up until a couple of weeks ago, everything about this tutorial worked right on the money. What has changed since then?

**pgroover: wrote;**
I agree with you completely as I used it myself to install and it went flawlessly, with the exception of the dlls. I know there have been quite a few wine updates since then but the version that is available per the instructions has not changed.

Strange...

Seems like this happened...
> **FrankVdb: wrote;  **
I have a question: has the howto been updated since it was written?

It's full of broken links...

(bit reluctant to wade through 40 pages to find out)

Thanx.

I made a little trip to Wines website after having installed it.  Judging by their workload and overall progress it seems Wine is still a version Alpha baby project :( 
Any program where all the necessary files ain't obtained locally in one place is doomed for minor bugs or even sabotage.  From the "richest-guy-in-the-world-now-retired-thus-ran-by-annoying-yelling-bald-guy"
....that's my guess, I know I would if I feared the Linux liberation 8-[

The best thing to stabilyze Wine would be if they got more die-hard programmers interested in their work.  They seem very under-manned. :-k

---

### Post by Aurora on 2006-11-24
Greetings,

How do I uninstall all this stuff now?  Nobody seems to be able to get sound working, and I installed it specifically for music training software (see /www.giamusic.com/scstore/P-audiationassistant.html).  After extensive Googling, I found that it seems the sound problems are limited to the Ubuntu binaries. 

I went to the WINE site, and it said the binaries for Debian and Ubuntu are out of date, so I wanted to try compiling from source.  It said to remove all the binaries first.  Winetools has installed so much stuff...I don't know what it is, where it is, what it does, or how to remove it.  Is there a way to cleanse my system and start over, other than reinsalling Dapper?

If that's the case,  I could make an extra partition for a test Dapper install to see if I could get Wine working with sound, before redoing my main Dapper install.  I would like to know if there is a less drastic way to go about this.  I would like to have my system as it was before step one in the HOWTO.

Thanks,

Paul in Seattle

---

### Post by bodhi.zazen on 2006-11-24
> **Aurora said:**
> Greetings,

How do I uninstall all this stuff now?  Nobody seems to be able to get sound working, and I installed it specifically for music training software (see /www.giamusic.com/scstore/P-audiationassistant.html).  After extensive Googling, I found that it seems the sound problems are limited to the Ubuntu binaries. 

I went to the WINE site, and it said the binaries for Debian and Ubuntu are out of date, so I wanted to try compiling from source.  It said to remove all the binaries first.  Winetools has installed so much stuff...I don't know what it is, where it is, what it does, or how to remove it.  Is there a way to cleanse my system and start over, other that reinsalling Dapper?

If that's the case,  I could make an extra partition for a test Dapper install to see if I could get Wine working with sound, before redoing my main Dapper install.  I would like to know if there is a less drastic way to go about this.  I would like to have my system as it was before step one in the HOWTO.

Thanks,

Paul in Seattle

[list=number][*]Remove wine and winetools with synaptic/apt-get/aptitude[*]delete ~/.wine[/list]

---

### Post by sdude on 2006-11-28
thanks alot i got really confused in how to setup wine with ubuntu on wines main site, and this istalled it easily, thanks so much, laters :)

---

### Post by sdude on 2006-11-28
how do i get into the C: drive?

---

### Post by sdude on 2006-11-28
no worries i found out how to do it, i thought ill try the way of doing it manually in windows through the command prom[t, so i did i went into the terminal and typed start explorer.exe, that didnt work so i though ah yes coz its a excutable file, i typed "wine explorer.exe" and it opened up wines own explorer.exe how cool, so if any body didnt know about that wine have a explorer.exe, well i think it may depend on how you installed your wine, i have the latest wine my self so i dont know if the version or how you installed your wine thing will effect it but give it a go if you didnt know you could do that, i sure didnt lol, laters scotty out! :)

---

### Post by CraftyCathy on 2006-11-29
gazj, I followed your instructions for how to set up Wine. But when I try to add songs to Windows Media Player I get this error:

Invalid character(s) in path.

A file canot contain any of the following characters /:< >|

The file names do not have any of these in them. I have even renamed the file and named it "f" (without quotes). Still got the same errro when I tried to play it. 

Can you tell me what to do to solve this problem?

Cathy

---

### Post by KillerKiwi on 2006-11-29
Fix the colors!!

replace the [Control Panel\\Colors] section in ~/.wine/user.reg

```
[Control Panel\\Colors] 1105779303
"ActiveBorder"="239 235 231"
"ActiveTitle"="239 235 231"
"AppWorkSpace"="198 198 191"
"Background"="93 77 52"
"ButtonAlternativeFace"="200 0 0"
"ButtonDkShadow"="85 85 82"
"ButtonFace"="239 235 231"
"ButtonHilight"="255 255 255"
"ButtonLight"="255 255 255"
"ButtonShadow"="198 198 191"
"ButtonText"="0 0 0"
"GradientActiveTitle"="239 235 231"
"GradientInactiveTitle"="239 235 231"
"GrayText"="198 198 191"
"Hilight"="179 145 105"
"HilightText"="0 0 0"
"InactiveBorder"="239 235 231"
"InactiveTitle"="239 235 231"
"InactiveTitleText"="255 255 255"
"InfoText"="0 0 0"
"InfoWindow"="200 0 0"
"Menu"="239 235 231"
"MenuBar"="0 0 0"
"MenuHilight"="179 145 105"
"MenuText"="0 0 0"
"Scrollbar"="239 235 231"
"TitleText"="255 255 255"
"Window"="255 255 255"
"WindowFrame"="0 0 0"
"WindowText"="0 0 0"
```

Fits in with edgy nicely

---

### Post by error691 on 2006-12-03
I followed this guide and receive an error when trying to run Internet Explorer saying it has encountered a problem and needs to close. Every other program I try to run (Outlook Express and Windows Media Player) also crashes.

When I try to run WineTools to check the settings I get the following pop-up:

Winetools cannot run with a Wine version older than 20050628...

and the following text:

error691@error691-desktop:~$ wt
detecting Wine version... done.
Drive C: is /home/error691/.wine/drive_c
Wine 0
wine is executed as wine
Parameters are --noexit
Browser is /usr/bin/firefox.
WINEVER is "0".

??

---

### Post by Nameless_one on 2006-12-09
> **FrankVdb said:**
> I have a question: has the howto been updated since it was written?

It's full of broken links...

(bit reluctant to wade through 40 pages to find out)

Thanx.

Now that's a good question. 

I tried to follow the guide but the WineTools download link doesn't work. And there are absolutely no mirrors for the file, whatsoever. Anyone care to upload somewhere?

---

### Post by trommas on 2006-12-09
> **Nameless_one said:**
> Now that's a good question. 

I tried to follow the guide but the WineTools download link doesn't work. And there are absolutely no mirrors for the file, whatsoever. Anyone care to upload somewhere?

I would be really great if the author or someone else could write a fresh How-To for Wine. - It has developed a lot the last months!

---

### Post by sdude on 2006-12-09
The wine tools link has gone!!!!!!!!!!!!!!!! lol, or the server is busy, but ive tried getting wine tools lots of times now within the space of four days, still dont work, any change a repost or download somewhere else?:)

---

### Post by sdude on 2006-12-09
[COLOR="Red"]EDITED; (deleted)[/COLOR]

---

### Post by bodhi.zazen on 2006-12-09
> **trommas said:**
> I would be really great if the author or someone else could write a fresh How-To for Wine. - It has developed a lot the last months!

See here: [How to wine](http://doc.gwos.org/index.php/HowToWine)

Other than that, a "new version" of wine is released every two weeks and it is impossible to keep with each an every version, let alone versions of winetools, sidenet, or wine-doors.

The last time I tried wine-doors for example, I was able to install, but not run....

If there is something you feel should be added in the above link feel free to post here or PM me... ;)

Peace be with you,


[color=navy]bodhi.[/color][color=darkgray]zazen[/color]

---

### Post by cdi3d on 2006-12-12
Hello bohdi,

Thanks for all your replies on this thread and thank you gaz for creating it. 

I seem to have wine installed and working well on my dapper version of Kubuntu except for when I try to install a *.msi.

Ive checked around a bit and found Franks Corner and that site advised I should be able to install an *.msi as easily as typing

msiexec /i xxx.msi

I tried that, replacing the Xs with the name of the installer and was informed that the installation package couldnt be found. 

Do I need to include the file path?

---

### Post by pgroover on 2006-12-12
> **cdi3d said:**
> 
Do I need to include the file path?

Unless you're in the same directory as the msi file, that would be a definitive yes. :)

---

### Post by cdi3d on 2006-12-12
:-) Thanks.

---

### Post by true_friend on 2006-12-14
Hi folks
i cannot find winte tools from
wget [http://ds80-237-203-29.dedicated.hosteurope.de/wt/winetools-0.9jo-III.tar.gz](http://ds80-237-203-29.dedicated.hosteurope.de/wt/winetools-0.9jo-III.tar.gz)
is there any other source????
or it is going to an end.
wine does not run applications correctly without it...
from where i can get thme now????
Regards
True_Friend

---

### Post by Sebastral on 2006-12-15
If you have to install wine like this on other pc's copy the ~/winetools folder so files dont have to be redownloaded. With Microsoft Foundation Classes 4.x skip the downloads and with installing explorer I got an error of some infofile missing but everything seems to be working ;)

---

### Post by pgroover on 2006-12-15
> **true_friend said:**
> Hi folks
i cannot find winte tools from
wget [http://ds80-237-203-29.dedicated.hosteurope.de/wt/winetools-0.9jo-III.tar.gz](http://ds80-237-203-29.dedicated.hosteurope.de/wt/winetools-0.9jo-III.tar.gz)
is there any other source????
or it is going to an end.
wine does not run applications correctly without it...
from where i can get thme now????
Regards
True_Friend

A quick google search provided the following:

[http://www.von-thadden.de/Joachim/WineTools/index.html#download]("http://www.von-thadden.de/Joachim/WineTools/index.html#download")

---

### Post by bodhi.zazen on 2006-12-16
> **pgroover said:**
> A quick google search provided the following:

[http://www.von-thadden.de/Joachim/WineTools/index.html#download]("http://www.von-thadden.de/Joachim/WineTools/index.html#download")

Yes that is the download site, but the link is broken :(

Has been for a few days.

Wine-Doors is the replacement for Wine-tools and Sidenet, however wine-doors does not yet appear ready for prime time.....

I can send you a copy of winetools-0.9jo-III.tar.gz if you PM me your E-mail address....

It is 200 Kb.

---

### Post by pgroover on 2006-12-16
> **bodhi.zazen said:**
> Yes that is the download site, but the link is broken :(

Has been for a few days.

Wine-Doors is the replacement for Wine-tools and Sidenet, however wine-doors does not yet appear ready for prime time.....

I can send you a copy of winetools-0.9jo-III.tar.gz if you PM me your E-mail address....

It is 200 Kb.

Strange, I was just on it when I found the link to ensure it worked, oh well...

---

### Post by nkayesmith on 2006-12-18
I've uploaded the latest winetools targz to [download.formationos.net]("http://download.formationos.net") (a public mirror until the winetools site works again).

---

### Post by true_friend on 2006-12-18
These tools does not working with wine 0.9.27 which is officially latest version but the version described here is 0.9.5 and they work with it perfactly.. how strange it i had downloaded wine from winehq's repository which i had to un install and now downloading this version from sourceforge at a miserable download speed.. :(

---

### Post by nkayesmith on 2006-12-18
> **true_friend said:**
> These tools does not working with wine 0.9.27 which is officially latest version but the version described here is 0.9.5 and they work with it perfactly.. how strange it i had downloaded wine from winehq's repository which i had to un install and now downloading this version from sourceforge at a miserable download speed.. :(

I've fixed the problem (by removing the script which checks the wine version), and the modified version is now up for download at [http://download.formationos.net]("http://download.formationos.net").

---

### Post by true_friend on 2006-12-18
its ok now..
thnx

---

### Post by robertrej on 2006-12-19
I am trying to install turbocad on wine but I keep getting the error message:
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
wine: cannot find '/home/bob@bob/.wine/c/Program Files/turbocad/setup.exe'
bob@bob-desktop:~$ 
----------------------------------------------------------------------------------------------------------------------

                                                    please help with this issue
                                                     Thanks /  bob


-----------------------------------------------------------------------------------------------------------------------


> **gazj said:**
> *** UPDATE 19-07-2006 (UK DATE SYSTEM :) ) This howto was originally written for breezy badger, I can now confirm it also works on dapper drake

After a lot of searching here there and every where I finally know how to get wine working on my machine anyway, every time without fail, and as there is a lack of how to's on wine, I thought i would give the Ubuntu community something back. This is my first how to, so don't be to harsh if it dosen't work for you.

First we get the wine0.95.deb from winehq [http://kent.dl.sourceforge.net/sourceforge/wine/wine_0.9.5-winehq-1_i386.deb]("http://kent.dl.sourceforge.net/sourceforge/wine/wine_0.9.5-winehq-1_i386.deb")

or if you want to open a terminal (alt+F2 then type gnome-terminal then enter) to download it use this command

```
 wget http://kent.dl.sourceforge.net/sourceforge/wine/wine_0.9.5-winehq-1_i386.deb
```

In case your wondering why we are not downloading the latest version of wine its because internet explorer install breaks on newer versions and you will probably need internet explorer to get other programs working, but we will update wine after, so don't worry

Right so we got our Wine .deb so lets unpackage it in our terminal dont forget to change directory to where you downloaded wine (if you used the above command you should already be there)

```
sudo dpkg -i wine*.deb
```

ok, so we no have wine, but how do i use it, set up a C:/ D:/ etc i hear you cry, let alone install anything, well here come the great little app called winetools ;)

I have now learned that winetools has at least one dependancy, pointed out by replies on this forum, here is the command for installing it (added 1st April 06, after 12 not a april fool btw)

```
sudo apt-get install libgtk1.2
```

wine tools can be downloaded here [http://ds80-237-203-29.dedicated.hosteurope.de/wt/winetools-0.9jo-III.tar.gz]("http://ds80-237-203-29.dedicated.hosteurope.de/wt/winetools-0.9jo-III.tar.gz")

or if your still with me in the good old terminal you can use this command

```
wget http://ds80-237-203-29.dedicated.hosteurope.de/wt/winetools-0.9jo-III.tar.gz
```

ok, so we got this great tool no we need to unpack it

```
tar -xf winetools*
```

and install it

```
cd winetools*
sudo ./install
```

Done :) so lets start this wonderfull tool with this

```
wt
```

you will get loads of messages popup about not being configured etc, just keep clicking ok oh and that you should also own a copy of windows to use some of these tools. Yeah Yeah on with the plot.

You should finally get to a menu

So first we go for base setup, then create a fake windows drive
Next winetools will find your cdrom for you so it can set it up for wine
Followed by a username and organization, I Just leave theese as is
After a few fake windows restarts later we are told fake drive completed. Yippee

We are back to the base setup menu, now select DCOM98 and then go down the list installing all the programs on the list, obvioulsy only do internet explorer in your language, the reason we have left the Arial font out is because the  link to this is dead, but we will sort this later. Just click next and ok on everything, im sure you know how window installers work.

Ok so we have finished the first list, hit the main menu button to get us back to the start.

next click install windows system software then click ok

again install everything thats in the list from top to bottom in your own language, and install visual basic 5 & 6

ok, so now we gotta sort out theese fonts as the links that winetools uses to retrieve them is dead, so click main menu followed by exit to leave winetools

now then back to our friend the terminal
ok so first we need to make and move to the directory where winetools would have downloaded the fonts

```
mkdir ~/winetools/fonts
cd ~/winetools/fonts
```

you might get an error saying the file exsits, if you do don't worry just continue

Next we download the fonts from a link that is still around at the time of writing this, you might want to copy and paste this one into your terminal

```
wget http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe && wget http://kent.dl.sourceforge.net/sourceforge/corefonts/arial32.exe && wget http://kent.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe &&  wget http://kent.dl.sourceforge.net/sourceforge/corefonts/comic32.exe &&  wget http://kent.dl.sourceforge.net/sourceforge/corefonts/courie32.exe &&  wget http://kent.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe &&  wget http://kent.dl.sourceforge.net/sourceforge/corefonts/impact32.exe &&  wget http://kent.dl.sourceforge.net/sourceforge/corefonts/times32.exe &&  wget http://kent.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe &&  wget http://kent.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe &&  wget http://kent.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe
```

Ok, so we now have the fonts downloaded, next back to winetools to install them ;)

```
wt
```

Select base setup again then install true type font arial

Next main menu then select Install Microsoft true type corefonts, yet again go all the way down the list until you have installed all the fonts.

done that, so main menu and exit winetools ;)

Ok so we should now have a working wine, with internet explorer installed and windows media player 6 ;) hopefully :s

we should be able to start Internet Explorer with the following

```
 wine "/home/USERNAME/.wine/c/Program Files/Internet Explorer/IEXPLORE.EXE"
```

Dont forget to change USERNAME to your own username

With any luck your using internet explorer now :)

although we dont want to have to write this in everytime we want to start internet explorer, so right click the desktop and create a launcher and paste the previous code in there for a desktop shortcut, or make a menu shortcut which ever you prefer.

Here is the code for Outlook and Windows Media Player

```
wine "/home/USERNAME/.wine/c/Program Files/Outlook Express/msimn.exe"
```

and

```
 wine "/home/USERNAME/.wine/c/Program Files/Windows Media Player/mplayer2.exe"
```

and really thats about it, you can also navigate using your file browser and double click .exe files and wine will launch them, like installers for programs and so on, then its just a case of finding the .exe that starts the program and making your custom launcher for it,  your wine c: should always be found in /home/USERNAME/.wine/c. As long as know a bit about the windows file layout you should have no problem in finding them, always remember when creating your launchers that linux is case sensitive, so dont forget the caps.

Two last things to do

Firstly updating wine 0.95 to the latest version, remember we had to use 0.95 because internet explorer will not install on newer versions, although this maybe fixed now. There is no need to panic though, we just add a wine repository to our sources.list like this.

```
sudo gedit /etc/apt/sources.list
```

then add this line to the bottom of the file

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/



then save your sources.list and run the following in terminal to update your wine installation

```
sudo apt-get update
sudo apt-get upgrade
```

This should update wine to the latest version released by wineHQ, and will always be updated with the rest of your updates when a new version is released, Good hey

The second thing to do is to tell you about the winecfg command

```
winecfg
```

This little panel allows you to change the default wine settings, like which windows version to try to act as, and what builtin and native dll's to use, I would suggest leaving the global settings to windows98 as this seems to work best, but you can change the windows version for individual .exe's if a program only works on a certain version of windows, if a program dosen't quite work right this is the place to go, although the full usage of winecfg is a bit beyond the scope of this howto, you should get familiar with it quite soon

If you have problems with a certain program i find it always pays to just put in a google search "program name winehq" and you will usually find the program in the winehq database and find out what success people have had at getting the program to work and what they did to achieve it, very helpfull

One last point, if you use any programs that reside in the windows system tray then the system tray icons do not show up, a workaround is to open up a kde application that uses a tray icon and then the windows tray icons will appear, i.e i have amarok start when gnome starts, kalarm is a good one to use if you dont use amarok, even after you quit your kde program the windows icons will remain.  I believe this shouldn't be a problem for KDE users.

Anyway hope this was some help to a least one person out there, and I will probably add a MSN Messenger HOWTO this as soon as i get the time, let me know how you get on, In the meantime happy wineing :)

---

### Post by bodhi.zazen on 2006-12-19
> **robertrej said:**
> I am trying to install turbocad on wine but I keep getting the error message:
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
wine: cannot find '/home/bob@bob/.wine/c/Program Files/turbocad/setup.exe'
bob@bob-desktop:~$ 
----------------------------------------------------------------------------------------------------------------------

                                                    please help with this issue
                                                     Thanks /  bob


-----------------------------------------------------------------------------------------------------------------------

Try:```
wine /home/bob@bob/.wine/c/Program**\** Files/turbocad/setup.exe
```

Or ```
 wine "/home/bob@bob/.wine/c/Program Files/turbocad/setup.exe"
```

---

### Post by Praxicoide on 2007-01-06
I set up Wine once using this howto and it was a great help, so hats off to Mr. gazj!

Now that the original link doesn't work, I downloaded from the site provided by nkayesmith.  But when I type:

sudo ./install

I get "command not found"

So how do I install winetools?

---

### Post by nkayesmith on 2007-01-08
> **Praxicoide said:**
> I set up Wine once using this howto and it was a great help, so hats off to Mr. gazj!

Now that the original link doesn't work, I downloaded from the site provided by nkayesmith.  But when I type:

sudo ./install

I get "command not found"

So how do I install winetools?


I have no idea about that one, but you might want to try typing "gksudo ./install" instead.

I'm working on a .deb file at the moment.

---

### Post by rippon on 2007-01-11
I have the latest version of Wine installed (0.9.29) and downloaded the latest WineTools (.9.x) installed from the tgz, but when I go to run it I get this in a little window:

[CENTER] ***ERROR***
 WineTools cannot run with a Wine version older than 20050628...[/CENTER]


This is what it gives back in the console:
```
detecting Wine version... done.
Drive C: is /home/dan/.wine/drive_c
Wine 0
wine is executed as wine
Parameters are --noexit
Browser is /usr/bin/firefox.
WINEVER is "0".
```

How do I fix it. I want to get it so I can play CS:S.

---

### Post by rippon on 2007-01-11
> **nkayesmith said:**
> I've fixed the problem (by removing the script which checks the wine version), and the modified version is now up for download at [http://download.formationos.net]("http://download.formationos.net").

Thanks

---

### Post by nkayesmith on 2007-01-11
> **rippon said:**
> I have the latest version of Wine installed (0.9.29) and downloaded the latest WineTools (.9.x) installed from the tgz, but when I go to run it I get this in a little window:

[CENTER] ***ERROR***
 WineTools cannot run with a Wine version older than 20050628...[/CENTER]


This is what it gives back in the console:
```
detecting Wine version... done.
Drive C: is /home/dan/.wine/drive_c
Wine 0
wine is executed as wine
Parameters are --noexit
Browser is /usr/bin/firefox.
WINEVER is "0".
```

How do I fix it. I want to get it so I can play CS:S.

Winetools from the official site has problems. I have fixed this, and another problem with Winetools, and released the new version at my website, [http://download.formationos.net/](http://download.formationos.net/)

Remove your version of Winetools (execute the uninstall script in /usr/local/winetools/ as root) and install the version from download.formationos.net. Let me know if you have any problems.

EDIT: Just noticed that you have already done so (I noticed the post above mine)..whoops!

---

### Post by tartarian on 2007-01-13
Could anyone give me a hand? I've installed wine and winetools with the HowTo, and everything worked fine. I could run Internet Explorer and Media Player etc. I've come back this morning and bizarrely none of them run now. When I run the command for Internet Explorer in Konsole I get:

oliver@oliver-laptop:~$  wine "/home/oliver/.wine/c/Program Files/Internet Explorer/IEXPLORE.EXE"
fixme:shell:StopWatchMode () stub!
fixme:shdocvw:IEWinMain "" 10
fixme:rpc:alloc_serverprotoseq protseq "mswmsg" not supported
err:shdocvw:register_class_object failed to register object 800706a7
fixme:rpc:I_RpcServerStopListening (): stub
fixme:rpc:I_RpcWindowProc (0x50090,00000002,00000000,00000000): stub
fixme:rpc:I_RpcWindowProc (0x50090,00000082,00000000,00000000): stub


Any Ideas?

---

### Post by wild77 on 2007-01-15
> Remove your version of Winetools (execute the uninstall script in /usr/local/winetools/ as root) and install the version from download.formationos.net. Let me know if you have any problems.

could someone tell me how unistall winetools so I can install the one which works with the newer versions of Wine.

---

### Post by bodhi.zazen on 2007-01-15
> **wild77 said:**
> could someone tell me how unistall winetools so I can install the one which works with the newer versions of Wine.

I'm not sure as I do not use winetools.

However, it looks like:```
cd /usr/local/winetools
sudo ./uninstall
```

If not, ls and see if there is an uninstall script ??

---

### Post by nkayesmith on 2007-01-15
> **bodhi.zazen said:**
> I'm not sure as I do not use winetools.

However, it looks like:```
cd /usr/local/winetools
sudo ./uninstall
```

If not, ls and see if there is an uninstall script ??

There is an uninstall script, so those instructions are fine.

---

### Post by sn0m on 2007-01-15
mmm cool thread.

---

### Post by GeoPirate on 2007-01-15
> **tartarian said:**
> Could anyone give me a hand? I've installed wine and winetools with the HowTo, and everything worked fine. I could run Internet Explorer and Media Player etc. I've come back this morning and bizarrely none of them run now. When I run the command for Internet Explorer in Konsole I get:

oliver@oliver-laptop:~$  wine "/home/oliver/.wine/c/Program Files/Internet Explorer/IEXPLORE.EXE"
fixme:shell:StopWatchMode () stub!
fixme:shdocvw:IEWinMain "" 10
fixme:rpc:alloc_serverprotoseq protseq "mswmsg" not supported
err:shdocvw:register_class_object failed to register object 800706a7
fixme:rpc:I_RpcServerStopListening (): stub
fixme:rpc:I_RpcWindowProc (0x50090,00000002,00000000,00000000): stub
fixme:rpc:I_RpcWindowProc (0x50090,00000082,00000000,00000000): stub


Any Ideas?

I get the same error message, but it was caused at the second to last step "update wine" IE and everything worked fine, then I updated, and rebooted my whole system, then I got this error.  Any suggestions?

---

### Post by nkayesmith on 2007-01-15
> **GeoPirate said:**
> I get the same error message, but it was caused at the second to last step "update wine" IE and everything worked fine, then I updated, and rebooted my whole system, then I got this error.  Any suggestions?
Try running winecfg. There should be an entry for IEXPLORE.EXE - click on it and go to the DLL Overides tab.
Remove all the dll overides and add 
* (native, bulletin)

This will make sure that you are not using the winetools (sometimes out-of-date) dll overides when running Internet explorer.

---

### Post by maestrobwh1 on 2007-01-20
I noticed that when Adept upgraded Wine, WineTools would not run, and the newer Wine did little or nothing for my installed apps anyway. 

It has been mentioned that WineTools is not really appreciated by the Wine devs, but it allows you lots of control over Wine and its processes. If you must try it, be using wine 0.9.24:

You'll need 'alien' to be installed: Download the RPM of WineTools into your home, and to a 
sudo alien --scripts *.deb
after that runs
sudo dpkg -i *.deb
[B]
Be sure there are no other deb packages in your home or[/B] in place of the *, use the full name.  It installs and simplifies some things as a debain package as opposed to a tar.gz

Then just type wt in a shell... DONT USE SUDO!  :-)

OR you can use something new I have seen called WineEXS.  It does not offer as many tools, BUT it is simpler and is elegant in that way.  The install is easier as well.

---

### Post by nkayesmith on 2007-01-20
> **maestrobwh1 said:**
> I noticed that when Adept upgraded Wine, WineTools would not run, and the newer Wine did little or nothing for my installed apps anyway. 

It has been mentioned that WineTools is not really appreciated by the Wine devs, but it allows you lots of control over Wine and its processes. If you must try it, be using wine 0.9.24:

You'll need 'alien' to be installed: Download the RPM of WineTools into your home, and to a 
sudo alien --scripts *.deb
after that runs
sudo dpkg -i *.deb
[B]
Be sure there are no other deb packages in your home or[/B] in place of the *, use the full name.  It installs and simplifies some things as a debain package as opposed to a tar.gz

Then just type wt in a shell... DONT USE SUDO!  :-)

OR you can use something new I have seen called WineEXS.  It does not offer as many tools, BUT it is simpler and is elegant in that way.  The install is easier as well.

Or you could use the newer wine with my modified version of winetools - available from [http://download.formationos.net](http://download.formationos.net). There should be no trouble installing this - post here if there is.

---

### Post by hito1 on 2007-01-25
Quick dumb question:

How do you go back when to the program screen after minimizing it in wine? All I get is a green desktop with no taskbars.

Thanks.

---

### Post by bocmaxima on 2007-02-17
Does this tutorial work on Edgy, and should I still be using 9.5?

---

### Post by Matchless on 2007-02-17
> **bocmaxima said:**
> Does this tutorial work on Edgy, and should I still be using 9.5?

Edgy repositories have Wine 9.30 and I am running Quickbooks on it at the moment.

---

### Post by R960XT on 2007-02-27
hii there i'm new here. and new to linux...
i'm using ubuntu 6.06
i have installed wine 0.9.12 using the tutorial in the first page
and i want to upgrade it to the latest version which is 0.9.31
i don't know how to do it
when i try 
```

   sudo apt-get install wine 

```
i get these message 

```

deddy@Ubuntu-Linux:~$ sudo apt-get install wine
Password:
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: libartsc0 (>= 1.5.2-0) but it is not installable
E: Broken packages
deddy@Ubuntu-Linux:~$

```
please help me....

---

### Post by undertakingyou on 2007-02-28
What do you get is you type
```
sudo apt-get install libartsc0
```

If that works then do your
```
sudo apt-get install wine
```

Does it work then?

---

### Post by R960XT on 2007-02-28
the first comman to get the libartcsc0 failed..
but i download it manually and install in.
then i run the second comman..
and everything work like a charm :D (altough it's pain downloading using 56k Modem)

thanks anyway. everything works great

---

### Post by mac71 on 2007-03-03
Fantastic HOWTO!:) I've tried and failed many times with installing and using Wine. But now thanks to this fab post I have my machine singing!

I'd just like to add that I had no success with the original winetools download site. I had to use: [http://download.formationos.net/winetools/winetools-0.9.4.tar.gz](http://download.formationos.net/winetools/winetools-0.9.4.tar.gz)

With the total time it took to complete it even felt like a windows install :lolflag: Thanks again. Nice one!

---

### Post by Big_Fanwah on 2007-03-04
> **mac71 said:**
> Fantastic HOWTO!:) I've tried and failed many times with installing and using Wine. But now thanks to this fab post I have my machine singing!

I'd just like to add that I had no success with the original winetools download site. I had to use: [http://download.formationos.net/winetools/winetools-0.9.4.tar.gz](http://download.formationos.net/winetools/winetools-0.9.4.tar.gz)

With the total time it took to complete it even felt like a windows install :lolflag: Thanks again. Nice one!



First off, great HOW TO! 
I'm a linux  NOOB as they say, not bad on XP - but only had Ubuntu 6.10 as dual boot for 5 days and its starting to show..lol :confused: 

i've followed the 'how to' until i need to install winetools - like mac71 said above the link is down so i tried his instead (thanks mac!)  thing is i can't open winetools, apparently i have installed it but 'wt' does not work, i get 'command not found'...

...i need to install IE6 in WINE to get HyperLobby to install (a haven for flight sim folks) so i'm told

any ideas please :)


here's what i got installing winetools:

Installing WineTools to /usr/local/winetools...
Installing translations...
/home/pete/Desktop/winetools-212jo/install: line 23: cd: /usr/local/winetools/po: No such file or directory
ls: *.po: No such file or directory
Start WineTools as *normal* user with "wt2". Don't use as root!
pete@pete1:~$ wt2
bash: wt2: command not found
pete@pete1:~$ wt
bash: wt: command not found
pete@pete1:~$ winetools
bash: winetools: command not found
pete@pete1:~$

---

### Post by Looney on 2007-03-07
I have some huge problem. I installed Wine, but when I start it, there is no font. This is how it looks like:
[IMG]http://shrani.si/files/screenshotv7v0.png[/IMG]
[IMG]http://shrani.si/files/screenshotv7v4.png[/IMG]
[IMG]http://shrani.si/files/screenshotv7v8.png[/IMG]

Where is my font?:cry:

---

### Post by undertakingyou on 2007-03-08
try installing the mstcorefonts package```
sudo apt-get install mstcorefonts
```

---

### Post by Looney on 2007-03-09
"E: Couldn't find package mstcorefonts"

This is what I get.:|

---

### Post by undertakingyou on 2007-03-09
Sorry there is two t's ```
sudo apt-get install msttcorefonts
```

---

### Post by Looney on 2007-03-10
Yep... that's it. Thanks.:)

---

### Post by AJB2K3 on 2007-03-10
Interesting write up but did you forget the included **winecfg** command? same as winetools but part of wine.
Winetools wouldnt work for me but then i rembered **winecfg** and everything is now working.

---

### Post by Mets on 2007-03-30
Whenever I run the "wt" command, all I get are boxes with blank screens.  There is no text appearing anywhere.  I heard this was a GTK font error, so I ran sudo gedit /etc/gtk/gtkrc.utf-8
and changed default-font to user-font.  This displays some text, but wt won't run any of the menu options, saying "/etc/gtk/gtkrc.utf-8:6: error: invalid string constant "user-font", expected valid string constant"

How can I fix this?

---

### Post by embeemb on 2007-04-01
I followed the initial how-to until I installed Winetoosl.  However, when I do > wt as indicated, I get >  bash: wt: command not found .

I'm quite the noob, so I really can't decide much what's up?

Guys, help? Please?

---

### Post by undertakingyou on 2007-04-03
> **Mets said:**
> Whenever I run the "wt" command, all I get are boxes with blank screens.  There is no text appearing anywhere.  I heard this was a GTK font error, so I ran sudo gedit /etc/gtk/gtkrc.utf-8
and changed default-font to user-font.  This displays some text, but wt won't run any of the menu options, saying "/etc/gtk/gtkrc.utf-8:6: error: invalid string constant "user-font", expected valid string constant"

How can I fix this?

use the following:```
sudo apt-get install msttcorefonts
```

See if that helps

---

### Post by Abhi Kalyan on 2007-04-05
wget [http://ds80-237-203-29.dedicated.hosteurope.de/wt/winetools-0.9jo-III.tar.gz](http://ds80-237-203-29.dedicated.hosteurope.de/wt/winetools-0.9jo-III.tar.gz)
As the above link did not work, So used the link belowe
wget [http://www.sourcefiles.org/Emulators/Microsoft/winetools-0.9jo-III.tar.gz](http://www.sourcefiles.org/Emulators/Microsoft/winetools-0.9jo-III.tar.gz)

Great Tutorial, Thank you. Hope this adds value.
Thank you
Sincerely
Abhi Kalyan

---

### Post by Abhi Kalyan on 2007-04-05
WOW,!!
thats all i got to say,
Beautifull
Thank you

---

### Post by Mets on 2007-04-10
Ok got the font problem to work.  I had to increase the size of GTK utf_8 to 13.  I finished the install and got everything setup.  Worked awesome!  

Now, I ran sudo apt-get update and sudo apt-get upgrade and it installed the newest version of wine.  It says the newest version is 0.933 (even though we used 0.95 to get this thing installed).  I installed the newest one and now when I run wt I get:

```
Winetools cannot run with a Wine version older than 20050628
```  On top of that, wine seemed to stop working.  Internet Explorer won't open, Media Player opens for a nanosecond then crashes, etc.  Everything was running fine with the .deb.  I ran Internet Explorer from the terminal and got this output:

```
fixme:rpc:alloc_serverprotoseq protseq "mswmsg" not supported
err:shdocvw:register_class_object failed to register object 800706a7
fixme:rpc:I_RpcServerStopListening (): stub
fixme:rpc:I_RpcWindowProc (0x20024,00000002,00000000,00000000): stub
fixme:rpc:I_RpcWindowProc (0x20024,00000082,00000000,00000000): stub

```

What do I do?  It was good for a while...

---

### Post by jmelton on 2007-04-10
Okay, I'm a total Wine newbie and I'm confused by some things about this HOWTO.  Mainly, why is this approach given when you can just install wine from the universe repository?  What is the advantage of apt-getting the .deb file for wine and for winetools?  Will wine not work without winetools?

After I installed wine, the first thing I tried to run with it was BlitzIn, the chess interface for playing on the Internet Chess Club.  I managed to actually get it to  run, sort of.  A couple of problems: 

1) I got this prompt after I was logged in: "This application is requesting an ActiveX browser object but the Mozilla Active X control is currently not installed.  Do you wish to download and install it?"  If I clicked either "yes" or "no," the program immediately crashed.  I forget the error messages, there were a lot of them.  HOWEVER, if I just ignored the prompt and moved its window out of the way, I could go ahead and use the program to seek and play a game.  But that brought up major problem #2:

2) I couldn't see the top row of the chess board!  I tried stretching or shrinking that part of the window, getting rid of the toolbar, etc.  Nothing worked.

So, where to go from here?  What is this Mozilla Active X control -- is it something I need, and is it part of Mozilla so that I'd have to install Mozilla to have it?  In general, how does one troubleshoot Wine and go about trying to fix the way it runs stuff?

---

### Post by andrew frank on 2007-04-12
i followed your instruction, but i got messages that libgtk-1.2.so, libgail.so,libatk-bridge etc. were missing. i could not get these from the repositories, but had newer versions of these packages installed.

mind: i use feisty 7.04 - does this make a difference? wine 0.9.33. winetools 0.9.

any help is appreciated!
andrew

---

### Post by DJ_Peng on 2007-04-26
I know it's still kind of new, but has anyone tried this with Dreamweaver CS3? I tried running the installer in Wine and got errors before the first window popped up.

---

### Post by mech7 on 2007-04-26
> **DJ_Peng said:**
> I know it's still kind of new, but has anyone tried this with Dreamweaver CS3? I tried running the installer in Wine and got errors before the first window popped up.

It does not run with me :( the entire cs3 suite btw does not seem to run.

I wonder of there will be a time when windows app run normal under wine... even ps7 still has bugs :(

---

### Post by DJ_Peng on 2007-05-03
I tried it this afternoon and I have no clue what I missed. I'll have to keep my eyes peeled. DW is one of the two programs I still have to rely on WinXP for. (I run DW8 in Wine, but if have to hold onto Win in case I need it to get DW CS3 running under Wine in teh future.)

---

### Post by LuckN1ne on 2007-05-04
says that the dependencies broke... and the tools link isn't working i think

---

### Post by Dylnuge on 2007-05-08
Hopefully Adobe will eventually decide to release their CS products on Linux.

I am still using Dreamweaver and Flash 8 on Linux, can't get CS3 working-yet.

---

### Post by donkey42 on 2007-05-14
where is a different url for winetools ? as> wget [http://ds80-237-203-29.dedicated.hosteurope.de/wt/winetools-0.9jo-III.tar.gz](http://ds80-237-203-29.dedicated.hosteurope.de/wt/winetools-0.9jo-III.tar.gz) doesn't work or is broken

---

### Post by entobuntu on 2007-05-31
Came to this thread when trying to install wine on my dual opteron 64-bit Ubuntu 6.06 machine. I have all the ia32 libs and the latest wine (0.9.37).
But when I run wine <application> I get:

Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/user-id/.wine/drive_c', starting in the Windows directory.
wine: could not load L"c:\\windows\\system32\\application.exe": Module not found

Now I've just read elsewhere that winetools is no longer needed or supported. 
[http://ubuntuforums.org/showthread.php?t=453216](http://ubuntuforums.org/showthread.php?t=453216)

Running winecfg gives:

Warning: the specified Windows directory L"c:\\windows" is not accessible. Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/user-id/.wine/drive_c', starting in the Windows directory.
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  14
  Current serial number in output stream:  15

This is eerily like thread:
[http://ubuntuforums.org/showthread.php?p=1989366](http://ubuntuforums.org/showthread.php?p=1989366)

I'd be very grateful for any suggestions.

---

### Post by you on 2007-07-17
> **FredSambo said:**
> please explain how to get libtk 1.2

i think it may have something to do with our error.

just do: sudo apt-get install libgtk1.2

---

### Post by ibeeby on 2007-08-12
My wine installation for Ubuntu 6.06 LTS Workstation does not work properly in as much as it reports its version as 0.9.43 after 'wine --version' but winetools complains that WINEVER is 0 and therefore the version of wine installed is too old for winetools to work.

How do I set (or where do I set) WINEVER to be 0.9.43 or something that winetools will accept?

Cheers

Ian

---

### Post by doh224 on 2007-08-13
I have a problem opening the winetool? 

terminal:
akaran234@akaran234-desktop:~/Desktop/winetools-0.9jo-III$ wt
detecting Wine version... done.
Drive C: is /home/akaran234/.wine/drive_c
Wine 0
wine is executed as wine
Parameters are --noexit
Browser is /usr/bin/firefox.
WINEVER is "0".
akaran234@akaran234-desktop:~/Desktop/winetools-0.9jo-III$

it pops up with an error that say: "winetools cannot run with a wine version older than 20050628..."
and my wine version is up to date?  
I used the tar.gz file.

---

### Post by mstephens on 2007-08-20
My understanding is that winetools has not been updated for some time and will not work with newer versions of wine.

Have a look at  the applications database [www.winehq.com]("http://www.winehq.com")  to see how to get various applications running.

Anyone wanting Internet Explorer v6 should have a go with  ies4linux which worked "straight out of the box" for me on ubuntu 7.04. The only problem is that I need IE6 and WMP9  and WMP is excluded from the ies4linux version of IE6. 

I'm going to take a look at the trial version of  Codeweavers Crossover to see if it gives me any clues ( For those who don't know Crossover is basically the commercial version of Wine and they cross- fertilise each other)

---

### Post by robinpc on 2007-08-23
I've noted some problems in running a few Windows Programs (SnagIt comes to mind) under 32-bit Wine.  The 64-bit version now available for Feisty solves the problems, but has a minor complication installing the Gecko engine.  I've done a quick detail of directions on my [dorsetwest]("http://dorsetwest.com/node/39") blog.   The gist is:

[LIST=1]
[*]Install 64-bit Wine including keys and repository
[*]Install the Gecko Engine **BEFORE** you try to run your Windows Application.  The magic invocation is:
> $ wine iexplore [http://www.winehq.org](http://www.winehq.org)
[*]Run your Windows application
[/LIST]

---

### Post by bobandirus on 2007-08-29
> 

```
cd winetools*
sudo ./install
```



Being extra ordanerally n00bish, can you please explain what you mean with the star? what do i replase that with?

---

### Post by Hickeydog on 2007-09-01
[QUOTE=gazj;857250]*** UPDATE 19-07-2006 (UK DATE SYSTEM :) ) 
ok, so we no have wine, but how do i use it, set up a C:/ D:/ etc i hear you cry, let alone install anything, well here come the great little app called winetools ;)

I have now learned that winetools has at least one dependancy, pointed out by replies on this forum, here is the command for installing it (added 1st April 06, after 12 not a april fool btw)

```
sudo apt-get install libgtk1.2
```

wine tools can be downloaded here [http://ds80-237-203-29.dedicated.hosteurope.de/wt/winetools-0.9jo-III.tar.gz]("http://ds80-237-203-29.dedicated.hosteurope.de/wt/winetools-0.9jo-III.tar.gz")

or if your still with me in the good old terminal you can use this command

```
wget http://ds80-237-203-29.dedicated.hosteurope.de/wt/winetools-0.9jo-III.tar.gz
```

ok, so we got this great tool no we need to unpack it

```
tar -xf winetools*
```

and install it

```
cd winetools*
sudo ./install
```

Done :) so lets start this wonderfull tool with this

```
wt
```

ok.  I tried running the script and also clicking on the link.  I cannot get to that server/ website.  Is anyone esle having this problem? I downloaded winetools from [http://www.von-thadden.de/Joachim/WineTools/](http://www.von-thadden.de/Joachim/WineTools/)
but I have no idea how to unpackage it and install it.  What is the command for unpacking downloaded material?

---

### Post by Hickeydog on 2007-09-01
ok.  so I got Wine tools to work.  but I don't think that I have the correct version.  In order to run it, I need to enter "WT2" into the terminal.  Also, when I go to install the DCOM98, I get the error "DCOM98 can only be installed on Windows 98.  For Windows NT, please install lates service packs"  Any help as far as correcting that goes?

---

### Post by gavin72 on 2007-09-01
> **bobandirus said:**
> Being extra ordanerally n00bish, can you please explain what you mean with the star? what do i replase that with?
* is just a placeholder that saves you from typing the rest of the name. (as long as it's unique)
So instead of typing cd /home/user/wine_0.0.9_etc
you you just type cd /home//user/wine*

---

### Post by HarshReality on 2007-09-03
So, can somebody do a sticky or updated method for Feisty x64... I tried sudo apt-get install wine and I get no installation candidate

---

### Post by mattdee on 2007-12-05
I'm hoping to get some help...

Wine was working a couple o' days ago.  I updated to wine-0.9.50

And I couldn't get anything running...like notepad.exe etc..

So I removed and reinstall from the repository.
Now I get this error when I run winecfg.

Anyone see this error and fix it?
I'm trying to get IE6 running on my system to use some web apps that 'require' IE.

ERROR
------------------------
matt@Brutus:~/Desktop$ winecfg
Xlib:  extension "ATIFGLRXDRI" missing on display ":0.0".
wine: Unhandled page fault on read access to 0x000000b8 at ...

---

### Post by Youghurt on 2007-12-25
> **Hickeydog said:**
> ok.  so I got Wine tools to work.  but I don't think that I have the correct version.  In order to run it, I need to enter "WT2" into the terminal.  Also, when I go to install the DCOM98, I get the error "DCOM98 can only be installed on Windows 98.  For Windows NT, please install lates service packs"  Any help as far as correcting that goes?

I'm getting this error too. Creating the fake drive works, as does installing the Truetype Font Arial. Everything below it fails to download, claims that I should download a different version for NT or claims that I don't have the correct .dlls (I think this should be fixed if DCOM could be installed).

---

### Post by Neo824 on 2008-01-21
The link for Wine tools doesn't work. ]:

---

### Post by nikoPSK on 2008-01-21
I am sure this will help many. :)

---

### Post by kenninaz on 2008-06-03
I have followed the instructions and had no problems installing wine and winetools. however, when i attempted to run ie6, _nothing happens_ and this is what the terminal responded:

[I]kenninaz@kenninaz-desktop:~$ ie6
detecting Wine version... done.
Drive C: is /home/kenninaz/.wine/drive_c
Wine 0
wine is executed as wine
Parameters are [/I]

If I run it from the terminal:
*kenninaz@kenninaz-desktop:~/.wine/c/Program Files/Internet Explorer$ wine IEXPLORE.EXE* 

_nothing appears as well_, but this is the response in the terminal:
[I]preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:shell:StopWatchMode () stub!
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:rpc:alloc_serverprotoseq protseq "mswmsg" not supported
err:shdocvw:register_class_object failed to register object 800706a7
fixme:rpc:I_RpcServerStopListening (): stub
fixme:rpc:I_RpcWindowProc (0x10024,00000002,00000000,00000000): stub
fixme:rpc:I_RpcWindowProc (0x10024,00000082,00000000,00000000): stub
[email]kenninaz@kenninaz-desktop:~/.wine[/email]/c/Program Files/Internet Explorer$ [/I]

Installation of other programmes such as uTorrent was successful though.

Any thoughts on why my ie6 will not run???

---

### Post by shuttleworthwannabe on 2008-06-04
Hi there,
I am using WINE in Ubuntu 8.04, and installed the RC3 version thru the repo's by adding the repo entry to the sources.list (in this way I get the latest WINE version). Anyway, MSOffice 2003 (Word, PPT and Excel) all work fine (ACCESS, PUB, etc) not work at all, crashing all the time).

I used WINEDOORS also in synaptic to get the other software to enhance windows only functionality. I have not used it a lot, but it has some really simple installtion options.
thanks
s

---

### Post by hansaplast on 2008-11-27
> **Hickeydog said:**
> ok.  so I got Wine tools to work.  but I don't think that I have the correct version.  In order to run it, I need to enter "WT2" into the terminal.  Also, when I go to install the DCOM98, I get the error "DCOM98 can only be installed on Windows 98.  For Windows NT, please install lates service packs"  Any help as far as correcting that goes?

Goto [http://www.dlldump.com/](http://www.dlldump.com/) and download mfc40.dll
copy mfc40.dll to ~/.wine/dosdevices/c:/windows/system32 and continue with wt -> basic setup "Microsoft Foundation Classes 4.x"

---

### Post by Murdoc_of_puts on 2008-12-03
First off, thanks for doing this.
I guess that links as with all things-die after time.  Here's some updated links for 8.10.( 2008 )
wine tools
[http://von-thadden.de/Joachim/WineTools/](http://von-thadden.de/Joachim/WineTools/)

windows script 
[http://www.macropool.com/en/download/scripting.html](http://www.macropool.com/en/download/scripting.html)

source lists for Ibex
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) intrepid main #WineHQ - Ubuntu 8.10 "Intrepid Ibex"
#deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) intrepid main #WineHQ - Ubuntu 8.10 "Intrepid Ibex"

Hope this Helps

---

### Post by gazj on 2008-12-15
> **Murdoc_of_puts said:**
> First off, thanks for doing this.
I guess that links as with all things-die after time.  Here's some updated links for 8.10.( 2008 )
wine tools
[http://von-thadden.de/Joachim/WineTools/](http://von-thadden.de/Joachim/WineTools/)

windows script 
[http://www.macropool.com/en/download/scripting.html](http://www.macropool.com/en/download/scripting.html)

source lists for Ibex
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) intrepid main #WineHQ - Ubuntu 8.10 "Intrepid Ibex"
#deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) intrepid main #WineHQ - Ubuntu 8.10 "Intrepid Ibex"

Hope this Helps

Oooh, Haven't looked at this post for at least a year now, sorry.  Thanks for the above info, have changed the original post.  Any other info you think should be changed please let me know :)

---

### Post by Sebastral on 2008-12-20
Microsoft Script 5.6 English failed to download. try [this link]("ftp://ftp.bizplans.com/scr56en.exe") :popcorn:

Then I used [this post]("http://wawan-kurniawan.web.id/wine-installation-in-ubuntu-intrepid/") to get latest wine in repository. 

The result isn't workable for me. Wine apps @ compiz refuse to show text and when running metacity font rendering is still crap. 

I have wine programs running perfectly fine in compiz on my legtop, so there must be a solution.

> **SeaJayEmm said:**
> I just uninstalled Wine and related packages. I seen something that could be the possible solution and is worth checking out. /usr/share/fonts/truetype/ttf-liberation...look into that and you might find a solution
Well, ttf-liberation fails to install; "ttf-liberation is broken or not fully installed" and therefor msttfcorefonts as well :confused:

[INDENT]E: msttcorefonts: subprocess post-installation script returned error exit status 9
E: ttf-liberation: subprocess post-installation script returned error exit status 9[/INDENT]
but I'll leave this for later. I have other priorities :(

---

### Post by meanmrmustard on 2009-01-06
Nevermind

---

### Post by LFJazz on 2009-01-27
Hi! I'm new to Ubuntu and I'm very confused at the moment. I'm using latest version of Ubuntu and I used the latest of Wine also.

I installed wine. And because I wanted to play games I mounted Windows. Shortly after that I found a Trojan in my comp and after that some others also. A friend of mine said to me to reinstall wine. He said that it would help me out. The viruses are in the "folder" called Media.

 How can I get rid of that Media file? I uninstalled wine but the Media stays after I have tried to remove it too. Can some one help me with this?

 The reason why I want to get rid of it, is a fear that when I'm running mounted Windows the viruses will move to the next target through LAN. So then our other computer would be affected. But hey, I don't even know is it possible, but still tho I would like to get rid of the whole Media-file. After that I would reinstall wine and install the games which I'm seriously hooked up with ^_^ 

 - LFJazz

and hey, I'm working really hard not to be a n44b but ehmm.. I'm not succeeding =D  Don't give up on me..

---

### Post by hansaplast on 2009-01-28
> **LFJazz said:**
> How can I get rid of that Media file? I uninstalled wine but the Media stays after I have tried to remove it too. Can some one help me with this?
Unless the media file is not a folder or a device, you can remove its contents as root using the following command in a terminal window.
```

sudo rm /path/to/mediafile
```

---

### Post by lulumara on 2009-01-30
So first we go for base setup, then create a fake windows drive
Next winetools will find your cdrom for you so it can set it up for wine
Followed by a username and organization, I Just leave theese as is
After a few fake windows restarts later we are told fake drive completed. Yippee

We are back to the base setup menu, now select DCOM98 and then go down the list installing all the programs on the list, obvioulsy only do internet explorer in your language, the reason we have left the Arial font out is because the link to this is dead, but we will sort this later. Just click next and ok on everything, im sure you know how window installers work.

Ok so we have finished the first list, hit the main menu button to get us back to the start.

next click install windows system software then click ok

again install everything thats in the list from top to bottom in your own language, and install visual basic 5 & 6

ok, so now we gotta sort out theese fonts as the links that winetools uses to retrieve them is dead, so click main menu followed by exit to leave winetools

now then back to our friend the terminal
ok so first we need to make and move to the directory where winetools would have downloaded the fonts




this portion makes me lost can't figure it out can you explain how can I do that?How do you install DCom98?

---

### Post by keyboardslave on 2009-02-22
whats wrong with "sudo apt-get insall wine" ?

---

### Post by Found on 2009-03-25
thanks for your help man :)

---

### Post by Found on 2009-03-25
> **lulumara said:**
> 
this portion makes me lost can't figure it out can you explain how can I do that?How do you install DCom98?

In the Basic Setup menu, there is a line named DCOM98 so just double click it to run your installation :) Then you IE6 with your language settings...nothing hard ;) Just read carefuly

---

### Post by sototallycarl on 2009-03-27
Is there a way to setup wine to use an Ubuntu app as the helper for a wine app?

My use is when editing a smart object in Photoshop CS2 you need an EPS/AI editor (depending on content), but none are working for me in wine.

---

### Post by Business Convert on 2009-04-14
> **Matchless said:**
> Edgy repositories have Wine 9.30 and I am running Quickbooks on it at the moment.

okay; what version quickbooks are you using?  thanks.

---

### Post by hortstu on 2009-04-18
> **gazj said:**
> wine tools can be downloaded here [http://www.openoffice.de/wt/winetools-0.9jo-III.tar.gz](http://www.openoffice.de/wt/winetools-0.9jo-III.tar.gz)

or if your still with me in the good old terminal you can use this command

Code:

wget [http://www.openoffice.de/wt/winetools-0.9jo-III.tar.gz](http://www.openoffice.de/wt/winetools-0.9jo-III.tar.gz)




i got this response when I tried this...
HTTP request sent, awaiting response... 404 Not Found
2009-04-18 11:57:50 ERROR 404: Not Found.

---

### Post by sysyphus on 2009-04-21
> **hortstu said:**
> i got this response when I tried this...
HTTP request sent, awaiting response... 404 Not Found
2009-04-18 11:57:50 ERROR 404: Not Found.

Try:

```
wget http://download.formationos.net/winetools/winetools-0.9.4.tar.gz
```

as the old link no longer exists

---

### Post by Advena on 2009-04-22
Hi

It al went pretty well untill now, when i try to download the Microsoft Foundation Classes 4.x the download stays at 0%
it's there for over an hour
What now :o

---

### Post by spike_naples on 2009-04-27
So many thnigs about wine that it can be confusing but its all helpful. All newbies like me need to do is follow the instructions and read every line carefully.

---

### Post by PCFascist on 2009-05-15
> **keyboardslave said:**
> whats wrong with "sudo apt-get insall wine" ?

Your missing a 't' in install!:lolflag:

I'm going to install from apt right now and check it out.

---

### Post by PCFascist on 2009-05-15
apt works fine to install Wine, don't worry about taking the long way.

---

### Post by afrodeity on 2009-06-19
What's the difference between Wine Doors and Wine Tools? Are they the same package? Advantages, disadvantages?

---

### Post by kittyx23 on 2009-06-24
hello. can some one help? 
i typed in "wt" and it says "detecting Wine version..." and dos nothing. 
dos it mean i didnt install it?:confused:

---

### Post by Business Convert on 2009-11-02
> **Matchless said:**
> Edgy repositories have Wine 9.30 and I am running Quickbooks on it at the moment.

What version of Quickbooks?  I am using QB2005 and it's not working.  Appreciate the help!

---

### Post by abansb on 2009-11-10
this is the error I am getting

 "winetools can not run with a version older than 20050628..."

This is what shows in the terminal 

detecting Wine version... done.
Drive C: is /home/nunya/.wine/drive_c
Wine 0
wine is executed as wine
Parameters are --noexit
Browser is /usr/bin/firefox.
WINEVER is "0".

I am using wine version 1.1.32 if winetools wont work with this version should I downgrade to 0.95 ?

---

### Post by Dthon on 2010-06-15
Ok, I too need some help. And be gentle, i'm very n00bish :p.

I got through the HowTo until the point that i type in "wt" i get the following message

detecting Wine version... done.
Drive C: is /home/lisa/.wine/drive_c
Wine 0
wine is executed as wine
Parameters are --noexit
Browser is /usr/bin/firefox.
WINEVER is "0".
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory



:confused: I have no idea what any of this is/means. If anyone can help me, i would really like to get this up and running. 
Thank you :-D

---

### Post by hansaplast on 2010-06-16
> **Dthon said:**
> 
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory


The error kind of gives you the answer. It say's it can't find libgtk-1.2.so.0 shared object file. Probably because libgtk isn't installed.

I don't have an ubuntu box at hand but I suggest you search for the package "libgtk" in synaptic or apt```
$ sudo apt-cache search libgtk
```Then install the common package. Probably something like this (mind the version number)```
$ sudo apt-get install libgtk-1.2-common
```

Good luck

---

