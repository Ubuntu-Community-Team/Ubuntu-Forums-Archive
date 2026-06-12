---
title: "HOWTO Ubuntu mini ram"
date: 2005-06-19
forum: Outdated Tutorials &amp; Tips
---

### Post by christooss on 2005-06-19
I found [this guide](http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html) little outdated. So I will try to write my own. My interpretation of formmer howto.

0.1 AUTOMATE SCRIPT

I made a automate script for this howto. Script is based on [Automate Script for New Users](http://ubuntuforums.org/showthread.php?t=22646)

1. Installing everything
1.1 Hoary
I imagine that you have Hoary CD already in your CD unit. Reboot computer and when installation screen shows, write server and then press <return>

Go through whole installation process. And when you find yourself in console login and then write

```
$ wget http://ahacic.5gigs.com/miniram.sh
```
```
$ sudo sh miniram.sh
```

When whole proces is done you have all programs listed in this howto installed.

1.2 Breezy

```
$ wget http://ahacic.5gigs.com/miniram-breezy.sh
```
```
$ sudo sh miniram-breezy.sh
```

Warning :)

Breezy automate script doesnt install w32codecs! You can install them with enabling marillat repositories which are in my sources.list which you downloaded with automate script. When you removed # at line with marillat. Type

```
$ sudo apt-get update
```
```
$ sudo apt-get install w32codecs
```

After that you can remove marillat repostiories from sources.list
------------------------------------------------------------------------------------------------------
0.2 MANUAL INSTALLATION

If yoo want to install without script this is how you do it :)

1. Install WM

I imagine that you have Hoary CD already in your CD unit. Reboot computer and when installation screen shows, write server and then press <return>

Go through whole installation process. And when you find yourself in console login and then write

```
$ sudo su -
```
This will put you in permanent sudo sudo status. So you don't have to write sudo over and over again.

1.2 Adding extra repositories

write

```
# wget http://ahacic.5gigs.com/sources.list
# cp /etc/apt/sources.list /etc/apt/sources.list_backup 
# cp sources.list /etc/apt/sources.list
# apt-get update
# apt-get upgrade
```
1.3 Next step to install x.org
```
# apt-get install x-window-system-core
```
This will install you X server X.org  in Ubuntu. Then you have to install Window Manager. I prefer ICEWM But you can choose any of the WM-s. you have got plany listed [at this link](http://xwinman.org/) 
```
# apt-get install icewm
```
Now we have to install wdm llogin manager.
```
# apt-get install wdm
```

You can still choose to install xdm with:
```
# apt-get install xdm
```
Now we have working enviroment but with no GUI application. You can now login with command
```
# wdm
```
2. Application install.

2.1 We need terminal 
```
# apt-get install xterm
```
2.2 File manager tool
text based
```
# apt-get install mc
```
Gui based
```
# apt-get install emelfm
```
2.3.2 GUI Internet browser and mail client
With mozzila you get them both together
```
# apt-get install mozilla
```
if you want realy something fast instal Dillo browser and Sylpheed mail client
```
# apt-get install dillo
#apt-get install sylpheed
```
Now opera is free of charge you can DL it at
[http://opera.com/free/](http://opera.com/free/)

2.3.2 Text based browser and mail client
For browser you can use lynx
```
# apt-get install lynx
```
and for mail client you can use mutt+procmail+fetchmail+gnupg
You can find tutorial howto setup this thing [at this link](http://wiki.sourcemage.org/index.php?page=HOWTO-Setup+mutt%2Bprocmail%2Bfetchmail%2Bgnupg)
Another page about Mutt. [Click at this link :)](http://www.mutt.blackfish.org.uk/) 
2.4 Text editing tool
```
# apt-get install nedit
```
```
# apt-get install abiword
```
Nedit is gedit replacement and abiword replaces OpenOffice Writer. 

Please DON'T USE OPENOFFICE  [-X 

Why? Beacause it takes to god thamn long to start

2.5 Spreadsheet editor
```
# apt-get install gnumeric
```
Replacement for OOo Spredsheet

2.6 CD burner
```
# apt-get install graveman
```
I use mkisofs and cdrecord - These two are already installed on Ubuntu server
On this [Link](http://www-106.ibm.com/developerworks/linux/library/l-cdburn.html) you can find howto burn with mkisofs and cdrecord. 
Anyway this is it. We have complete system installed

2.7 Multimedia
You are missing media players aren't you. Please read [www.ubuntuguide.org](www.ubuntuguide.org) for installing other applications. But I don't recommend you to install anything else on low-ram system. But its you choice. If you must install media players Install xmms and xine
```
# apt-get install beep-media-player xine-ui
``` 
and codecs
```
# apt-get install w32codecs
```
2.8 Gaim
It has IRC MSN Jabber etc. support
```
# apt-get install gaim
```
2.9 FTP
```
# apt-get install gftp
```
2.10 PDF reader
```
# apt-get install xpdf
```
If I missed something or if I made a mistake let me know.
2.11 Bittorrent client
```
# apt-get install bittornado
```
If you want GUI
```
# apt-get install bittornado-gui
```
I hope this howto helped you.

Sorry for my bad english ](*,)

---

### Post by poofyhairguy on 2005-06-19
I would use regular Mozilla over epiphany. Epiphany is the "official" browser of Gnome, so I bet it installs Gnome stuff.

---

### Post by christooss on 2005-06-19
Yes I changed that. I found that epiphany demands mozilla firefox installed :roll: 

About GNOME: If you install abiword you get gnome libs installed. So if there is an alternative....

---

### Post by poofyhairguy on 2005-06-19
[QUOTE=christooss]Yes I changed that. I found that epiphany demands mozilla firefox installed :roll: 

About GNOME: If you install abiword you get gnome libs installed. So if there is an alternative....[/QUOTE]

gnumeric too. They are part of the "Gnome Office"

I guess the way around it is a lighter editor (leafpad) or a heavier one (openoffice).

---

### Post by Kyral on 2005-06-19
It strikes me that this method could also be used for a "Gentoo Style" install (installing only the packages YOU want, total customization) without having to go through Stages or compiling

---

### Post by christooss on 2005-06-19
Hm I rather see gnome libs on my comp than installing OOo on miniram system.

It "scares" me that mozilla-firefox and OOo need a ubuntu-desktop package

---

### Post by poofyhairguy on 2005-06-19
[QUOTE=christooss]Hm I rather see gnome libs on my comp than installing OOo on miniram system.
[/QUOTE]

How light is koffice?

---

### Post by christooss on 2005-06-19
I think this is not an option beacause it installs kdelibs.

---

### Post by christooss on 2005-06-19
116MB of Hardisc. That light :) Sorry but i don't know how much Gnome office takes. Beacause default Ubuntu system has some of the libaries installed. I think its the same size. But we dont need sql base installed or do we?

---

### Post by spacemonkey on 2005-06-20
I'm trying to use this install method to setup Ubuntu on an old PII server I've got lying around, and I've run into some problems.  I installed x-window-system-core, then fluxbox, then xdm, as suggested, but when I try to log in using xdm, it says there are no window managers found....something about /home/user/.Xsessions.  I went ahead and installed xterm, then when I logged in using xdm, it just went to xterm, no window manager though.  From there I can start fluxbox, by typing it in the xterm, but it still won't start right into it from xdm.  Any suggestions?

EDIT:
Nevermind...I fixed it.  I just added a .xsessions file in my home dir, and in it a put "fluxbox" in it, now logging in via xdm results in fluxbox starting.

---

### Post by mulperi on 2005-06-20
I use Graveman as CD/DVD writer. It has enough options like overburning but doesn't use the KDE libraries. Try it and tell me what you like.

//mulperi

---

### Post by xalphas on 2005-06-20
Graveman is really better. I like to use it. Simple with overburn feature.

If we don't think too light or mini we can use xfce4 instead fluxbox. 14-15 mb and better gui options. Or maybe a rox desktop only without xfce but how?

Gaim stands alone with only gaim-data dependency. 
Emelfm and MC for file manager tools.

---

### Post by christooss on 2005-06-20
I added gaim,  emelfm, mc and graveman

Thanks

Yes xfce is slightly havier :)

---

### Post by xalphas on 2005-06-20
And also for mp3 player. When i look at xmms it takes 6132 kb and beep-media-player 3801 kb with same dependency. Also uses gtk2 not bad looking as xmms. 

Terminal ftp or Gftp. Gftp comes with no dependency and takes around 3500 kb.

And have to fix xine-gui with xine-ui  :)

---

### Post by christooss on 2005-06-20
Thanks

Changed

And I added pdfreader and Link Howto burn with mkisofs and cdrecord.

---

### Post by AndersAA on 2005-06-20
[QUOTE=christooss]It "scares" me that mozilla-firefox and OOo need a ubuntu-desktop package[/QUOTE]

uhm.. no, ubuntu-desktop depends on firefox and OO, not the other way around.

---

### Post by christooss on 2005-06-20
Ok sorry. 

I only know that when iI want too uninstall OOo ubuntu-desktop gets uninstalled to. And than if I want to install back ubuntu-desktop OOo gets installed too.

---

### Post by derrick1985 on 2005-06-20
[QUOTE=christooss]Ok sorry. 

I only know that when iI want too uninstall OOo ubuntu-desktop gets uninstalled to. And than if I want to install back ubuntu-desktop OOo gets installed too.[/QUOTE]


ubuntu-desktop is a meta package that simply tells apt to install these specific packages with so and so configuration.

Anyways, that's a great howto. I have used the one that was outdated, except adding xfce4 for my wm (i still like a little gui in my machine) granted, it is SLOW, but for an old cyrix II 250mhz PC, with only 128 mb of ram, and half a leg to stand on, it does pretty damn good.

---

### Post by xalphas on 2005-06-21
What about dillo for browser. Will it be too light  :) ? 

> #  Dillo is small: source is less than 420 KB, and the binary is around  350 KB! 

[http://www.dillo.org/](http://www.dillo.org/)

---

### Post by eric71 on 2005-06-21
A nice improvement on XDM is WDM, which is in universe, I think.  It ends up being somewhat of a GDM-lite.  Not sure about the dependancies, but I'm sure its a lot lighter than GDM.

---

### Post by christooss on 2005-06-21
are tabs supported in dillo.

I will give it as an option. What about light thunderbird clone?

I will change xdm to wdm

---

### Post by christooss on 2005-06-21
xfce is a Desktop Enviroment

Does anybody know link to where al wms are listed?

---

### Post by xalphas on 2005-06-21
Like this? [http://xwinman.org/](http://xwinman.org/)  ;-)

---

### Post by christooss on 2005-06-21
Thanks. 

I added the link

---

### Post by trash on 2005-06-21
Awesome lil setup, I hope it's ok to post my spec's here...

OLD pentium120 not even mmx, 64 mb ram!
800x600/256

Ok it takes a while for fluxbox to be up and running but once it is it's smooth sailing!

Dillo(no tabs:( ), gaim, mc, xclock, xterm, xclipboard all running while i am posting this message.... and Dillo is still faster than ANY other browser lol.

NICE!

---

### Post by christooss on 2005-06-21
what do you use for mail agent? Anybody has an idea about it?

---

### Post by xalphas on 2005-06-21
Even i use a strong machine i like minimal installs. I tried so many of them. And i like to play. 

Anyway for mail agent. Will also be secure combination. I think of Mutt+Procmail+Fetchmail from terminal. 

This is for howto : [http://wiki.sourcemage.org/index.php?page=HOWTO-Setup+mutt%2Bprocmail%2Bfetchmail%2Bgnupg](http://wiki.sourcemage.org/index.php?page=HOWTO-Setup+mutt%2Bprocmail%2Bfetchmail%2Bgnupg)

Maybe for gui we can think of Sylpheed?

---

### Post by trash on 2005-06-21
Haven't dealt with email yet.

Is Opera an option? I am finding Dillo a little strange even with the way it deals with these forums, little things like the 'new posts' link will automatically sign me out and 'todays posts' link will take me to a 'nothing found' search page... and I so can't live without tabs anymore.

xalphas, YES! I am now thinking I want gnome off my better machines... perhaps a howto is needed for people who are running out of disk space, its a great solution for freeing up 1gb + on smaller drives. EDIT: or maybe its as easy as removing ubuntu desktop and then following this guide?

---

### Post by poofyhairguy on 2005-06-22
[QUOTE=trash]
Is Opera an option? [/QUOTE]


Yep.....

---

### Post by christooss on 2005-06-22
I will add sylpheed and mutt+....

Thanks

In my opinion opera is not an option. Why beacause its not free. OK its free with banners. and WE don't like banners do we? :)

---

### Post by trash on 2005-06-22
[QUOTE=eric71]A nice improvement on XDM is WDM, which is in universe, I think.  It ends up being somewhat of a GDM-lite.  Not sure about the dependancies, but I'm sure its a lot lighter than GDM.[/QUOTE]

Has anybody else tried WDM because I first tried XDM and didn't notice any extreme login times, where as with WDM I am now waiting 2-3 minutes while my password is validated.

christooss: I know but it works so well... the 'generic' ad's are almost unnoticable compared to the 'custom' ones that are colored and flash.

---

### Post by jackwhite on 2005-06-23
hey,

can anyone explain how i could do this without internet access? (i can get files off net elsewhere and burn them to cd)

thanks!

---

### Post by christooss on 2005-06-23
Hm Which of these files are on Ubuntu DVD?

---

### Post by jackwhite on 2005-06-24
I guess i should have explained things a little better. I'm try to set up a laptop for a friend of mine. It only has a really slow modem, and doesn't have a dvd drive. I wonder if its possible to download these files (and their dependencies) on another computer, burn them onto cd and then follow the above instructions? Sorry if this is an annoying or frequent question, like i said i'm more or less a total noobie...

---

### Post by christooss on 2005-06-24
[QUOTE=jackwhite]I guess i should have explained things a little better. I'm try to set up a laptop for a friend of mine. It only has a really slow modem, and doesn't have a dvd drive. I wonder if its possible to download these files (and their dependencies) on another computer, burn them onto cd and then follow the above instructions? Sorry if this is an annoying or frequent question, like i said i'm more or less a total noobie...[/QUOTE]
 Yes its posible

Go to page universe repositories. You got link

[http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)

And there download all packages

---

### Post by christooss on 2005-06-24
You than install them with dpkg -i package_name

---

### Post by christooss on 2005-06-24
Is there a HOWTO make CD from which user could apt-get these things from.

I am more than happy to do it

MRbuntu :)

---

### Post by christooss on 2005-06-25
One of kind guys from linuxquestions showed me this

[Link](http://www.debian-administration.org/articles/125) 
[Link](http://www.debian-administration.org/articles/149) 
[Link](http://www.debian-administration.org/articles/148) 

And now I can get in to making CD for low ram system. \\:D/

---

### Post by odie5533 on 2005-06-27
This tutorial is great! I have tryed about 8 distros so far on my family computer, none of which work good, applications constantly dying from lack of memory. I hope this works, I am going to go try it right now.

---

### Post by jackwhite on 2005-06-28
thanks for the advice christoss, i'll hopefully be able to give that a go over or after the weekend

---

### Post by tread on 2005-06-28
Have you thought of mutt as an email client? Its no x application, but it is really good.
[http://www.mutt.blackfish.org.uk/](http://www.mutt.blackfish.org.uk/) 
The above chap has a nice howto on mutt for beginner users, including how to setup mime extensions to open attachments etc.

---

### Post by xalphas on 2005-06-28
[QUOTE=xalphas]Even i use a strong machine i like minimal installs. I tried so many of them. And i like to play. 

Anyway for mail agent. Will also be secure combination. I think of Mutt+Procmail+Fetchmail from terminal. 

This is for howto : [http://wiki.sourcemage.org/index.php?page=HOWTO-Setup+mutt%2Bprocmail%2Bfetchmail%2Bgnupg](http://wiki.sourcemage.org/index.php?page=HOWTO-Setup+mutt%2Bprocmail%2Bfetchmail%2Bgnupg)

Maybe for gui we can think of Sylpheed?[/QUOTE]

Already mentioned and added to the howto.

---

### Post by christooss on 2005-06-28
I will still add this page to howto. you can never get to informed. Right?

---

### Post by derrick1985 on 2005-06-28
[QUOTE=christooss]One of kind guys from linuxquestions showed me this

[Link](http://www.debian-administration.org/articles/125) 
[Link](http://www.debian-administration.org/articles/149) 
[Link](http://www.debian-administration.org/articles/148) 

And now I can get in to making CD for low ram system. \\:D/[/QUOTE]

I can't wait to see this.

Not that doing this from the Ubuntu CD isn't good, all in one step would be better.

---

### Post by zielony on 2005-06-29
[QUOTE=christooss]
Now we have to install xdm llogin manager.
```
# apt-get install wdm
```
Now we have working enviroment but with no GUI application. You can now login with command
```
# wdm
```
[/QUOTE]

I have a little problem with that point.
I don't have net in computer that I wanted to install ubuntu(with fluxbox(because it is very old computer)) and I downloaded alle packeges with their relationships but after instalation wdm there is a problem. When I run 'wdm' my monitor only blinks samoe times and nothig else. I don't now is that ok?

---

### Post by christooss on 2005-06-29
try xdm

---

### Post by zielony on 2005-06-29
"command not found"

hmm.. I think I've done something bad with that all depencies..
where could I find a step-by-step instructions how to install fluxbox on ubuntu(server installed)? My main problem is thet I can't pin the net into that computer.. only sitting here and looking for packeges..and burn it on cd and go with that cd to another computer.. :(


sorry for my english I now it is terrible :|

---

### Post by christooss on 2005-07-05
Any one know about bittorennt client.

Azareus is Java based so it sux :)

---

### Post by christooss on 2005-07-07
[QUOTE=christooss]Any one know about bittorennt client.

Azareus is Java based so it sux :)[/QUOTE]
 Ok I added bittornado torrent client

---

### Post by mattheweast on 2005-07-14
Top guide! is this on the wiki? If not, I will port it or at least make a note so that someone can do it :)

thanks, Matt

---

### Post by christooss on 2005-07-19
[QUOTE=mattheweast]Top guide! is this on the wiki? If not, I will port it or at least make a note so that someone can do it :)

thanks, Matt[/QUOTE]
 YOu can ofcourse port it . But I want credits :) :) :) :)

---

### Post by mattheweast on 2005-07-19
There was already a similar page, although not as detailed as your guide. So I tidied it up and bit and added a link to your guide on the page.

[https://wiki.ubuntu.com/InstallUbuntuOnLowMemorySystems](https://wiki.ubuntu.com/InstallUbuntuOnLowMemorySystems)

Thanks for your work!!

---

### Post by christooss on 2005-07-24
I added a script to this howto.

---

### Post by christooss on 2005-08-01
Hello I changed Fluxbox into IceWM beacause after installation there was no programs in menus. I couldn't handle that. In ice WM you just do Update-menus and thats it.

---

### Post by Rogue Elephant on 2005-08-04
having network problems and want to continue on from where christos was almost going.

how can you install a low memory/old system version without an internet connection.

meaning, which programs are on the install CD already, which can replace gnome and other resource-hungry apps?

can't find fluxbox or icewm, for instance, so the mini howt guide is irrelevant if your system is so shite as to not even be "connected"

also, if gnome is the only alternative, when using the CD (i'm assuming you can apt-get stuff from the CD after installing the 'server' version of ubuntu), what do you need to apt-get (from the CD) to make it work properly? (other supporting progtams and libraries - minimum possible) and in what order. i might just search around for the list of all apps on the CD...

so basically, a barebones GUI server from the CD alone... any suggestions?

---

### Post by christooss on 2005-08-04
[QUOTE=Rogue Elephant]having network problems and want to continue on from where christos was almost going.

how can you install a low memory/old system version without an internet connection.

meaning, which programs are on the install CD already, which can replace gnome and other resource-hungry apps?

can't find fluxbox or icewm, for instance, so the mini howt guide is irrelevant if your system is so shite as to not even be "connected"

also, if gnome is the only alternative, when using the CD (i'm assuming you can apt-get stuff from the CD after installing the 'server' version of ubuntu), what do you need to apt-get (from the CD) to make it work properly? (other supporting progtams and libraries - minimum possible) and in what order. i might just search around for the list of all apps on the CD...

so basically, a barebones GUI server from the CD alone... any suggestions?[/QUOTE]
 Try on [www.ubuntulite.org](www.ubuntulite.org)

And on this link

[http://groups.google.com.au/group/ubuntu_lite](http://groups.google.com.au/group/ubuntu_lite)

---

### Post by Willcan on 2005-08-05
Hi.

I tried your install script and everything worked just fine.  I have only two problems, well I guess it's really only one.   There are others but this one rose to the top.

When I try to print from Abiword two thing's happen.

1.. Abiword disappears.

2..Nothing gets printed.

Any thoughts or ideas would be greatly appreciated.

Thank you.

---

### Post by Willcan on 2005-08-05
Continued to play, and got it to print., after noticing that lpr, wghich Abiword wants to print through wasn't installed.  So I sudo apt-get install lpr, and the printer prints.

This is what wanted printed, on an Epson Stylus C60 printer.  "This is a test.

This is what I got:
"%%Orientation: Portrait
%%Pages: 1
%%DocumentPaperSizes: A4
%%DocumentSuppliedResources: font BitstreamVeraSerif-Roman
%%EndComments
%%BeginProlog
  /FSF {findfont exch scalefont} bind def
  /MS  {neg moveto show} bind def
  /GS  {glyphshow} bind def
  /MV  {neg moveto} bind def
  /BP  {gsave 72 exch div dup scale} bind def
  /SZ  {/HH exch def /WW exch def} bind def
  /BPP {BP SZ 0 HH translate} bind def
  /BPL {BP SZ 90 rotate} bind def
  /EP  {grestore showpage} bind def
  /ML  {neg moveto neg lineto stroke} bind def
  /LAT {dup length dict copy dup begin
         {1 index /FID ne {def} {pop pop} ifelse} forall
         /Encoding ISOLatin1Encoding 256 array copy def
         Encoding 39 /quotesingle put
         Encoding 45 /hyphen put
         currentdict
         end} bind def
  /EXC {exch definefont pop} bind def
  /CP {closepath} bind def
  /F {fill} bind def
  /LT {neg lineto} bind def
  /MT {neg moveto} bind def
  /F0 {12 /BitstreamVeraSerif-Roman FSF setfont} bind def
%%EndProlog
%%BeginSetup
%!PS-TrueTypeFont
11 dict begin
/FontName"

Any ideas on what "m doing wrong?

---

### Post by DarthMandeep on 2005-08-20
If you run a lot of terminal apps you might want to use rxvt instead of xterm. It's just xterm with some of the rarely used features removed. On truly old systems, the xvt terminal emulator and the dash shell work great as a command line app launcher.

For a file manager, I've got to suggest either rox-filer or Xfe.  Both are fairly light, but very usable.

---

### Post by picpak on 2005-08-25
[QUOTE=christooss]Hello I changed Fluxbox into IceWM beacause after installation there was no programs in menus. I couldn't handle that. In ice WM you just do Update-menus and thats it.[/QUOTE]

Can you explain, please? The terminal says it's not found. Sorry, I switched back to Windows for about a month and I forgot how to use Linux ](*,)

---

### Post by christooss on 2005-08-25
WHich part you don't understand?

---

### Post by picpak on 2005-08-25
nvm, I got it. I needed to install "menu" and "menu-xdg".

---

### Post by Teroedni on 2005-08-28
This is a great Howto

Unlucky for me i started wdm
now i cant get back to console:(
And i havent got installed xterm:(
so it seems that i need to do all over again tommorow:(

also i tried to install amiwm with no luck
i wget [ftp://ftp.lysator.liu.se/pub/X11/wm/amiwm/amiwm0.20pl48.tar.gz](ftp://ftp.lysator.liu.se/pub/X11/wm/amiwm/amiwm0.20pl48.tar.gz)
but when i try to install it i cant
probably because is it in tar.gz format 
So how do i unpack it and make it work in console?

---

### Post by christooss on 2005-08-28
Just press crl+alt+ F1 to get back to konsole

---

### Post by Teroedni on 2005-08-29
To late:(
Anyway thanks:)
And icewm was looking quite good:)

---

### Post by John.Michael.Kane on 2005-09-08
christooss do you need to have net access to use this guide? i thought that apt get was for downloading files from the repo's ect. if this is the case how can you use this how to with net access? 


Thanks

---

### Post by christooss on 2005-09-08
Yes you have to have net acces. But let me remind you about Ubuntu lite

[http://groups.google.com/group/ubuntu_lite?lnk=li&hl=en](http://groups.google.com/group/ubuntu_lite?lnk=li&hl=en)

And page

[http://ubuntulite.org/](http://ubuntulite.org/)

---

### Post by John.Michael.Kane on 2005-09-08
,sorry. i wish to use the ubuntu i have. thanks how ever there should be way for the guide to be used with out internet access. mainly cause you state. how is someone going to have net access this way. in any case thanks for the help ubuntu lite is not what i need.. 

I imagine that you have Hoary CD already in your CD unit. Reboot computer and when installation screen shows, write server and then press <return>

---

### Post by xequence on 2005-09-08
Great howto! Ill try it out after. It will be good to only have the things I need.

Plus it will be a good learning experience =P How many MB is the install of the things you listed? As in how much of the HDD does this install take?

---

### Post by christooss on 2005-09-09
[QUOTE=xequence]Great howto! Ill try it out after. It will be good to only have the things I need.

Plus it will be a good learning experience =P How many MB is the install of the things you listed? As in how much of the HDD does this install take?[/QUOTE]
 Im not sure less than 1 GB

---

### Post by draugen on 2005-09-09
instead of xdm, wdm etc, you could use mingetty.

```
sudo apt-get mingetty
``` 

then edit /etc/inittab. replace: '
```

1:2345:respawn:/sbin/getty 38400 tty1
```

with

```
1:2345:respawn:/sbin/mingetty --autologin <yourusername> tty1
``` 

then run:
```
$ mv .bash_profile .bash_profile.bak
$ echo "tty | grep tty1 && startx" > .bash_profile
$ ln .bash_profile .profile
```

to automagically start X when logging in on TTY1.

(shamelessly lifted from [here](http://www.cs.rit.edu/~css8044/?q=autologin#) )

works great for me :)

--martin

---

### Post by christooss on 2005-09-09
sudo apt-get install mingetty ;)

---

### Post by draugen on 2005-09-09
ofcourse :) my bad...

---

### Post by Rxke on 2005-09-11
CHRISTOOS, kudos for this update!

in the original guide there was the following note:
> From Frank Martelli [frank at foodsavvy dot com]: Just a note when dealing with the ppc version of Ubuntu -- for some
reason, icewm (silently) requires /usr/lib/libtiff.so.3. A very frustrating bug, as X starts lets you login and then (without any errors)
returns to the login screen.
Solution:

ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3

Is this still an issue? and where in the process of installing does this apply? 
(going to try this out myself, so can come up with the answer... if all goes well... )

---

### Post by Rxke on 2005-09-12
Got it working. Now stupid of me, i got wet feet and did the ln -s... before checking out if it would work without, smart eh?
I got IceWm running in the end, but don't ask me how, heehee, on the way in, i did some kludging with different WM's and... But it definitely works.

Anyhoo... I had a sleepless night and tried the Xfce-on-server setup here:
[http://ubuntuforums.org/showthread.php?p=346504&posted=1#post346504](http://ubuntuforums.org/showthread.php?p=346504&posted=1#post346504)

and that went even smoother.

Since I prefer Xfce because it has a possibility to adjust screengamma (which I need for my broken screen), I'll stick to it, for now... But it would be interesting to see a cross-pollination, or a comparison between the two setups?

---

### Post by christooss on 2005-09-12
Its slightly different setup with xfce setup ju get xfce and gdm and FF

With this howto you get full operating sistem with everithing you need :)

I can make another script with xfce4 installation.

---

### Post by 8FootSativa on 2005-09-15
A few apps that some should consider are:

SLiM - Simple Login Manager: [http://slim.berlios.de/index.php](http://slim.berlios.de/index.php)

Qingy - [http://qingy.sourceforge.net/news.php](http://qingy.sourceforge.net/news.php)

Conky - [http://conky.sourceforge.net/](http://conky.sourceforge.net/)

Also, these packages would be of use:

[http://vljubovic.members.epn.ba/ubuntu.html](http://vljubovic.members.epn.ba/ubuntu.html)

Includes Ubuntu packages for Qingy, Equinox Desktop Enviroment, a highly patched Dillo, and a lightweight GDM with no need for Gnome.

Also, is the 2.4 kernel a possibility?

---

### Post by 8FootSativa on 2005-09-27
Bump!

---

### Post by pppetter on 2005-09-27
Hmz. Will there be a new automate script for breezy maybe?

---

### Post by christooss on 2005-09-28
Ok I will make it today. No problem

---

### Post by bugmenot on 2005-09-28
opera is now an option: [http://opera.com/free/](http://opera.com/free/)

---

### Post by christooss on 2005-09-28
I added opera as an option. But it will still not find its way to automate script :P

---

### Post by christooss on 2005-09-28
Breezy automate script has been added!!!

I hope t works. Please report.

---

### Post by krasator on 2005-09-28
Maybe you could add GQview as an image viewer. Very little dependencies, and it's really fast for the features it provides.

---

### Post by nytfox on 2005-10-01
This howto is amazing! :smile: :smile: :smile: 
btw what files in the server install that I can safely remove?  what I mean is when I do a server install in ubuntu5.04, will it also automatically install server applications like apache, mail etc.. which I don't need because I will use it for desktop only.
I'm new in ubuntu linux(just 3 day ago when I start experimenting, this distro is great).

---

### Post by christooss on 2005-10-01
You can try installing minimal and not server. I don't know how but there is a package ubuntu-minimal. Mybe try sudo apt-get install minimall but beware it might uninstall all f your programs.

Try this and report. Maybe you could choose minimal installation at first installation step?

If anyone can second that.

---

### Post by nytfox on 2005-10-02
I tried the above sudo apt-get install minimal or sudo apt-get install ubuntu-minimal but it give me can't find package error...

---

### Post by christooss on 2005-10-03
Are you using breezy. I don't think there is a minimal package in hoary.

BTW. for breezy users: xubuntu-package is avalible in repositories. And there will soon be a ubuntu-lite included. I hope. I have to lurn how to do meta package :) If any body has an Idea I would be realy happy if you could tell me how to do it

---

### Post by CAPTAIN RON FL on 2005-10-05
I want to use mozilla. I have the latest breezy. I get an error because the backports are no longer there. Have you got a way to fix this? I am using all the latest updates etc. from brezy.

Thanks, Ron

---

### Post by christooss on 2005-10-06
You have to use breezy sources.list + multiverse

---

### Post by CAPTAIN RON FL on 2005-10-06
You said "Breezy automate script doesnt install w32codecs". What is w32codecs? 

Thanks, Ron

OK I found out what they are far. I guess I should have stayed with what I had. Now I have to wait till new HOW TO'S are written. Oh well.
Close , Oh so close but no cigar.

---

### Post by christooss on 2005-10-06
OK I found out what they are far. I guess I should have stayed with what I had. Now I have to wait till new HOW TO'S are written. Oh well.
Close , Oh so close but no cigar.


I don't get this. Why you have to wait?

---

### Post by john280z on 2005-10-08
Hello all,

Timings on a Dell Gn P1/233 64Meg ram.
no sound card.
X11 is running at 800x600x16.
Xubuntu is Breezy server install with xubuntu-desktop
Boot timings:
PC is powered Off for one minute.
Power button pushed.
Timer is started after Grub;
"boot
Uncompressing Linux..."  <-- start timer.

Xubuntu boots to a login prompt requiring
the user to login and then type "startx".
UbuntuLite boots to X11.
Both are running FireFox version 1.0.7

        Xubuntu      UbuntuLite 1.1
Boot      2:19
startx    0:33         1:48
FireFox   0:34         0:27

john mitchell

---

### Post by christooss on 2005-10-08
WHat about this howto?

---

### Post by blackpaw on 2005-10-25
I'd like to give this script a try... what is happening on your page, christoss? half of the things seem not to work :(

well, guess I'll be stuck with the console for a while.. but the browsing is very fast now :)

ciao,


blackpaw

---

### Post by christooss on 2005-10-25
Ups sorry. The scripts will work tomorrow (upss its already today :) in the evening.

---

### Post by steeley on 2005-11-20
Just tried the script, but it fails because various links in the script point to files that do not exist on the servers.

---

### Post by christooss on 2005-11-20
Yes curently my page is down. Don't know why. Hope I will fix it today. But I will provide script soon as I find it on my disc. Sorry for the inconvinience

---

### Post by christooss on 2005-11-20
Is there anyone who can provide a space for my little files. For now I can provide these files in a package.

---

### Post by blackpaw on 2005-11-20
*waves* Webspace I have plenty and some traffic is no problem, as long as it's linux related. :grin: 

I volunteer, as I want to try your script badly! 
can you add an option to go for xfce4, maybe? :rolleyes: 

Post me a message or mail me then I will upload it for you. Or you upload it yourself..  Or something else ;)


andreas

---

### Post by christooss on 2005-11-20
For xfce4 try sudo apt-get install xubuntu-desktop

Check you PM :)

---

### Post by blackpaw on 2005-11-21
how could I have forgotten about xubuntu!!!

thanks ;)

but for getting the laptop-stuff to work (like Fn-Keys and stuff)
I am doing a full installation first and then stripping the system of gnome, gdm, evolution, and so on and put xubuntu-desktop on it afterwards.. it won't get me the FN-Keys to work if I do the server-install 

(too lame, I am)

can't wait to try out your skript, christooss

---

### Post by christooss on 2005-12-04
Hello every body new howto is out

[http://ubuntuforums.org/showthread.php?t=98233](http://ubuntuforums.org/showthread.php?t=98233)

---

### Post by DarthMandeep on 2005-12-13
JWM uses half the memory of IceWM while providing a similar look and features.
I've converted all my boxes to use it instead. Bye bye IceWM! We had a good run, but I've found something thinner and younger :)

---

### Post by christooss on 2005-12-13
Yes Jwm has been discussed on our mailin list. But I haven't check tat and I hav to check first :)

---

### Post by zx80 on 2006-05-20
Qingy could be a lightweight replacement for wdm:

[http://qingy.sourceforge.net/](http://qingy.sourceforge.net/)

---

### Post by Golgoth on 2006-06-01
[QUOTE=christooss]
About GNOME: If you install abiword you get gnome libs installed. So if there is an alternative....[/QUOTE]

[http://freshmeat.net/projects/siagoffice/](http://freshmeat.net/projects/siagoffice/)

---

