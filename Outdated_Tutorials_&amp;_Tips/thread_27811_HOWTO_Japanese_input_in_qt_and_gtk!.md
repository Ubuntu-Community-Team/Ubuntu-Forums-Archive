---
title: "HOWTO: Japanese input in qt and gtk!"
date: 2005-04-17
forum: Outdated Tutorials &amp; Tips
---

### Post by Graben on 2005-04-17
How to type Japanese in EVERY!! application.

1) $ sudo apt-get install uim anthy scim-gtk2-immodule scim-uim

2)  Create a file called 75custom-write_japanese in /etc/X11/Xsession.d

3) Paste the following into it

export XMODIFIERS="@im=SCIM"
export GTK_IM_MODULE="scim"
export XIM_PROGRAM="scim -d"
export QT_IM_MODULE="scim"

4) sudo dpkg-reconfigure locales
Select en_US.UTF-8 as default, it may be already.

5)System->Preferences->Sessions
Startup Programs Add scim -d
I left the order at 50

5a)For KDE users/Kubuntu users
Create a file startscim in .kde/Autostart/
Paste the following text.
#!/bin/sh
scim -d

Then  
chmod 744 startscim

6)Restart X or Reboot, Welcome to Japanese Input!

I did not create any of these steps.  This was all done by jalosxal [http://www.mepis.org/node/5638](http://www.mepis.org/node/5638) a mepis user. and [http://www.ubuntulinux.org/wiki/JapaneseInputHowto](http://www.ubuntulinux.org/wiki/JapaneseInputHowto)
The only thing I added was Adding it to auto start with gnome.

---

### Post by mrbass on 2005-04-18
thanks for summarizing it up.  Just a note to do it via commandline (adding scim -d) to a session it is

sudo touch /etc/X11/Xsession.d/74custom-scim_startup
sudo chmod 646 /etc/X11/Xsession.d/74custom-scim_startup
echo 'export XMODIFIERS="@im=SCIM"' >> /etc/X11/Xsession.d/74custom-scim_startup
echo 'export GTK_IM_MODULE="scim"' >> /etc/X11/Xsession.d/74custom-scim_startup
echo 'export XIM_PROGRAM="scim -d"' >> /etc/X11/Xsession.d/74custom-scim_startup
echo 'export QT_IM_MODULE="scim"' >> /etc/X11/Xsession.d/74custom-scim_startup
sudo chmod 644 /etc/X11/Xsession.d/74custom-scim_startup

**Add scim to GNOME (ubuntu)**
sudo touch ~/.gnome2/session-manual
echo "[Default]" >> ~/.gnome2/session-manual
echo "num_clients=1" >> ~/.gnome2/session-manual
echo "0,RestartStyleHint=3" >> ~/.gnome2/session-manual
echo "0,Priority=50" >> ~/.gnome2/session-manual
echo "0,RestartCommand=scim -d" >> ~/.gnome2/session-manual
echo "0,Program=scim" >> ~/.gnome2/session-manual

**Add scim to KDE (kubuntu)**
sudo touch ~/.kde/Autostart/startscim
echo '"#!/bin/sh"' >> ~/.kde/Autostart/startscim
echo "scim -d" >> ~/.kde/Autostart/startscim
sudo chmod 745 ~/.kde/Autostart/startscim

---

### Post by ubuntu27 on 2005-04-23
Hi guys. I am in step, numer 3:
3) Paste the following into it

export XMODIFIERS="@im=SCIM"
export GTK_IM_MODULE="scim"
export XIM_PROGRAM="scim -d"
export QT_IM_MODULE="scim"

I have a problem. When I cannot create a file in /etc/X11/Xsession.d

I also tryed to first create a file by Applications/Accesories/Text Editor

and then I pasted the following: 

export XMODIFIERS="@im=SCIM"
export GTK_IM_MODULE="scim"
export XIM_PROGRAM="scim -d"
export QT_IM_MODULE="scim"

and, then, I tryed to save to  /etc/X11/Xsession.d BUT, I couldn't...
So, I decide to save in "home' (/home/user)
and then move it to /etc/X11/Xsession.d
And it showed a dialog, I mean a box saying that I do not have permission to do that. [See the pic that I atached]

What should I do? I normally can install any programs. Besides there is no other user accounts. I am the only one who uses this computer.

---

### Post by tora201 on 2005-04-23
[QUOTE=ubuntu27]Hi guys. I am in step, numer 3:
3) Paste the following into it

export XMODIFIERS="@im=SCIM"
export GTK_IM_MODULE="scim"
export XIM_PROGRAM="scim -d"
export QT_IM_MODULE="scim"

I have a problem. When I cannot create a file in /etc/X11/Xsession.d

I also tryed to first create a file by Applications/Accesories/Text Editor.[/QUOTE]

What you do is type the following into the command terminal: sudo nano <file name>
That will open a little text editor. Paste your stuff as per usual, press CTRL-X to save it as you wish.

Should be no problem. Always remeber use: sudo (command) if you wish to have ROOT privileges.
OR, you should open a root terminal, and type in your password for complete ROOT access.

Cheers.

---

### Post by mrbass on 2005-04-27
ok I've played with Japanese input in KDE, GNOME quite a bit today. General comments are:
you don't need to add the scim -d to your GNOME session.  In fact is bad to as you can wind up with two separate scim processes.  KDE scim -d though is necessary to add it.

Extremely impressed with GNOME/GTK apps as they just all work great.   KDE uses more of a hack like the old kinput method.  It's not seamlessly integrated.

Now KDE apps you can't type Japanese while in GNOME.

When in KDE you can type on all KDE apps and GNOME apps as well.

Example..say your in GNOME or XFCE4 you couldn't input Japanese in Konqueror, kate, or Kolourpaint for example...but only within KDE....sucks.
Firefox works in GNOME, KDE, xfce4 no problem.

Japanese input works in Terminal too....no kterm needed.

Some major apps that don't work are scribus, inkscape, dia(?),...anyway.  I think not till Adobe Photoshop 6 did it accept double-byte characters.  So linux is coming along.

xfce4 works just great...probably reads the X11 startup file. Wow this is awesome.

---

### Post by Graben on 2005-04-27
I can type in Japanese in konqueror and other KDE apps when I am using GNOME...

---

### Post by mrbass on 2005-04-27
ok I'm guessing you can do that because you added scim-d to your gnome session as you outline in step 5.  However, say you have openoffice or firefox open don't you then see two different SCIM keyboards though?  I guess it'll work just may/may not get confusing having two scim sessions running.

---

### Post by Graben on 2005-04-27
Yeah I do have multiple keyboards, but it only shows the keyboard for the window that has focus on it.  Not too confusing.

Actually no I don't have two keyboards I misunderstood.  The only time there are two keyboards in the system tray are when I have something open as root, like synaptic.

---

### Post by pjo on 2005-05-05
[QUOTE=Graben]How to type Japanese in EVERY!! application.

1) $ sudo apt-get install uim anthy scim-gtk2-immodule scim-uim

2)  Create a file called 75custom-write_japanese in /etc/X11/Xsession.d

3) Paste the following into it

export XMODIFIERS="@im=SCIM"
export GTK_IM_MODULE="scim"
export XIM_PROGRAM="scim -d"
export QT_IM_MODULE="scim"

4) sudo dpkg-reconfigure locales
Select en_US.UTF-8 as default, it may be already.

[/QUOTE]


Hello,  i have q question on 4).  The default locale is set to ja_JP.EUC  so what shall I do about this ?
I am trying to input Japanese on KDE v3 on Debian Serge under coLinux.

Thanks in advance,  pjo

---

### Post by nogitsune on 2005-05-08
Hi y'all,

Will this guide let me write in hiragana and kanji like in windows? for now, i can only write in katakana, and not even in romaji->katakana, but katakana stright from the keyboard.

thanks y'all!

---

### Post by mrbass on 2005-05-08
If you install Japanese tables you can type hiragana and katakana without having the kanji selection pull up. scim-tables-ja
For screenshots see my CJK guide [http://mrbass.org/linux/ubuntu/scim/](http://mrbass.org/linux/ubuntu/scim/)

---

### Post by hanzj on 2005-05-23
Hi, On the day I converted to Ubuntu/Linux (1 week ago), I was helped by a kind person in the Ubuntu Chat room. The person led me thru some steps to get Japanese input set-up on my computer. I don't rememeber the instructions. I checked synaptic and it shows that I have UIM files and Anthy installed. How do I know which is currently running? And if I do have both, is one necessary for the other to work? Or can I delete one of them?

When I press Shift+Space, that's when I enter Japanese input mode, when I press Shift+Space again, I'm back to English.

 Do I need both? Is there a way to get a better Japanese input (for example, choosing between half-character and full-character Japanese text)? Which is the best program?

Where does SCIM fit into the picture?

If I'm understanding correctly, SCIM requires both anthy and UIM.  correct?


Anyway, I'm running Ubuntu 5.04 (hoary hedgehog). 

As I'm living in Japan and bought a Japanese Dell system, I have a Japanese keyboard. I set up Ubuntu to run with a Dvorak layout.

Now my other question: WHich instructions do I follow: Post1, Post2, or both?

---

### Post by df-sean on 2005-05-26
Under KDE, does anyone know how to make the annoying little popup toolbar bugger off?  I'd like to just ctrl-space to toggle Japanese/English input.  The little toolbar thing is unnecessary.  How can I kill it?

---

### Post by mrbass on 2005-05-27
[http://mrbass.org/linux/ubuntu/scim/scim-jp16.png](http://mrbass.org/linux/ubuntu/scim/scim-jp16.png)

I know this shows GTK but either this works or there is perhaps a QT settings...not sure.  Anyway just uncheck some of the Toolbar options in SCIM setup.

---

### Post by df-sean on 2005-05-27
Yes, that removes some of the options from the irritating little toolbar making it smaller -- but still just big enough to cover up my clock!  And no way to close it either!  So I find myself just constantly moving it out of the way.  How can I just close the damn thing?!  ](*,)

---

### Post by Trojan1313 on 2005-08-08
My SCIM doesn't have any installed tables. How do I get Anthy in there?
EDIT 1: Oh, nm.
EDIT 2: Is there any Keyboard-command to switch between katakana and hiragana?

---

### Post by pizzach on 2005-09-04
Two quick questions.

1.  So this  works for gtk and qt. So this wouldn't work for one of those that are neither apps like limewire?  (Though I do notice limewire doesn't even display japanese correctly on my computer.)

2.  anthy is great, but I was wondering if there was an easier way on linux to get katakana to spurt out.  Right now I'm forced to space bar it for each and every character if the word or non word is not in the dictionary.  On my old Mac I used to use the shift key to just type in katakana and it worked well.  Is there an easier way on linux?

---

### Post by mrbass on 2005-09-05
If you don't like the traditional input of katakana &#12450;&#12452;&#12454;&#12456;&#12458; I think what you want then is the katakana tables so you can just press the mouse on which one you want.

not sure about limewire....for example GAIM had trouble with double-byte characters but I believe it's solved now.

---

### Post by TheRealCryss on 2005-09-13
japanese imput works well in firefox but not in any kde app?
what's wrong?

---

### Post by bdash on 2005-09-14
Hello.

I have 2 problems (Breezy):
* scim-setup segfault
----
Loading Config Module gconf
Loading Config Module simple
Loading Config Module socket
Loading Setup Module hangul-imengine-setup
Segmentation fault
----
* When I enable scim, applications take an extra 10 seconds to load while on the console "Launching a SCIM daemon with Socket FrontEnd..." is displayed.

Apart from that, I can input Japanese, but... That's quite a serious problem.

PS: using gdb:
Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread -1218419008 (LWP 11177)]
0xb7241f7e in __gnu_cxx::__mt_alloc<PinyinEntry, __gnu_cxx::__common_pool_policy<__gnu_cxx::__pool, true> >::allocate ()
   from /usr/lib/scim-1.0//1.0.0/IMEngine/pinyin.so

---

### Post by bdash on 2005-09-20
Solved using this post:

[http://ubuntuforums.org/showthread.php?t=59985](http://ubuntuforums.org/showthread.php?t=59985)

---

### Post by James Keating on 2005-10-05
To run SCIM without Gnome or GDM, 
or with any single KDE-based application:

(setup note: I use FVWM2 and also have removed GDM, which means the scripts /etc/X11/Xsession.d/75custom-scim_startup and ~/.gnome2/session-manual have no effect even if I start Gnome. The only KDE-based application I use is Opera, the static version. These instructions are current for Edgy.)

To get SCIM and Anthy for Japanese, I installed the following packages:
anthy
im-switch
scim, scim-anthy, scim-gtk2-immodule, scim-modules-socket, scim-modules-table, scim-qtimm, scim-tables-ja, scim-uim
uim-anthy, uim-common, uim-fep, uim-gtk2.0, uim-qt, uim-utils, uim-xim

If you run GDM, you also will need m17n-env and scim-m17n

Then I ran scim-setup once from the command line to configure it. Recent versions don't seem to require this -- activate SCIM by pressing control+space, and right-click on the SCIM icon, then look around at the options. They used to be confusing but now are straightforward, and the defaults probably will be acceptable.

To make SCIM available for everything, I have a script that starts X, SCIM and FVWM. This should work for any window manager, adjusting the last line. (For Gnome it would be xinit /usr/bin/gnome-session)
#!/bin/sh
LANGUAGE=en_US.UTF-8; export LANGUAGE
LINGUAS=en_US.UTF-8; export LINGUAS
SUPPORTED=en_US:C:en_US:ISO-8859-15:ja_JP.eucJP:ja_JP.UTF-8:ja_JP:ja:ja_JP.JIS7:ja_JP.SJIS; export SUPPORTED
LANG=en_US.UTF-8; export LANG
LC_CTYPE=en_US.UTF-8; export LC_CTYPE
LC_MESSAGES=en_US.UTF-8; export LC_MESSAGES
XMODIFIERS="@im=local"; export XMODIFIERS
GTK_IM_MODULE="scim"; export GTK_IM_MODULE
QT_IM_MODULE="scim"; export QT_IM_MODULE
XIM_PROGRAM="scim -d"; export XIM_PROGRAM
scim -d
# start whatever window manager you use
xinit /usr/bin/fvwm -f /home/james/.fvwm/.fvwm2rc

I've left in the QT line for laughs -- it doesn't make any difference.


To get Opera (or any other single KDE program) to accept input through SCIM, this works from the command line:
scim -d & QT_IM_MODULE="xim" opera &

This does create a second instance of SCIM. But the second one is quite small, and the two don't interfere with each other. If I exit Opera the second instance remains, but if I start Opera again it is reused, so I never have more than those two instances.

You can also make it the startup command for that program in your window manager. In FVWM, the line is 
+ "Opera" Exec exec scim -d & QT_IM_MODULE="xim" opera
In Gnome, I suppose it would be
scim -d & QT_IM_MODULE="xim" opera

---

### Post by Najand on 2006-05-17
Unfortunately SCIM fails with a lot of commercial softwares like Realplayer, Opera, Adobe Acrobat Reader. For personal use, uim and anthy are much more reliable than scim (or skim in KDE).

---

### Post by drepster on 2006-06-05
Hi

Just a quick not to let you know that for kubuntu I had to install the following package: scim-qtimm 
Otherwise only my gnome apps worked with scim.

cheers
andre

---

### Post by Hiroshima on 2006-06-05
[QUOTE=mrbass]

**Add scim to GNOME (ubuntu)**
sudo touch ~/.gnome2/session-manual
echo "[Default]" >> ~/.gnome2/session-manual
echo "num_clients=1" >> ~/.gnome2/session-manual
echo "0,RestartStyleHint=3" >> ~/.gnome2/session-manual
echo "0,Priority=50" >> ~/.gnome2/session-manual
echo "0,RestartCommand=scim -d" >> ~/.gnome2/session-manual
echo "0,Program=scim" >> ~/.gnome2/session-manual

[/QUOTE]

I assume that if I do this, I will have scim working in Ubuntu.  I just upgraded to Dapper, is the process the same?

Cheers,
Hiroshima

---

### Post by emry on 2007-02-04
Thanks!
This worked great!

For those who got errors trying to set it up, make sure to use sudo.
^^

---

### Post by kebellekek on 2007-03-26
Hello all, 

I just had a fresh install of ubuntu. I installed Japanese language support as instructed but I have a problem. 

Here is my problem:
I press "w" and hiragana "wa" shows up on the screen (without waiting for me to enter a)&#65292; then i press "k" it shows "ka" in hiragana. so if i press "sksk" i end up with "sakasaka" on the screen. It has auto completion which i dont want. 

Another problem is that if I press enter after typing "watashiha" ,which is shown in hiragana on screen, it converts that string back to romaji. So i am unable to enter hiragana because they all end up in romaji. 

Also, if i press space the kanji choosing screen does not show up. So I am unable to select kanji characters. 

All of these futures were working on my old ubuntu. I dont know what is wrong with the new one. Any help is appreciated. 
Thanks a lot.

---

### Post by James Keating on 2007-03-26
Looks like you're in hiragana mode. You should be able to get Anthy by cycling through input modes with Control+Alt+Down or Up (I believe that's the default). 

To adjust settings, right-click on the SCIM icon at the far left of the SCIM toolbar that pops up. Click on SCIM setup. Front End, Global Setup lets you change the key combinations that turn SCIM on and off, and cycle through the input modes. IMEngine, Global Setup lets you pick which input modes can be available. For simplicity, I have English/European, plus Anthy and Hiragana -- you have to make Hiragana mode available to input with Anthy the usual way by typing Romaji that change to hiragana that you convert to kanji. Under IMEngine, Anthy, I have Input mode: Hiragana, Typing method: Romaji and Conversion mode: Multi segment.

---

### Post by ubuntu27 on 2007-03-26
Guys/Gals! 

[Use this guide ]("https://help.ubuntu.com/community/SCIM")for installing Japanese, Korean or Chinese write support.

The one instructed in this thread is too old. It was meant for Hoary.


So here it is:

[SCIM for Ubuntu (GNOME) ]("https://help.ubuntu.com/community/SCIM")

[SCIM for Kubuntu (KDE)]("https://help.ubuntu.com/community/SCIM/Kubuntu")

---

### Post by kebellekek on 2007-03-28
Thank you so much both of you. 

Now it works like a charm.

---

### Post by ventper on 2009-04-05
thank you, i really needed to find the updated guide.

now i just need to figure out hanyu pinyin input.

---

### Post by shannon.jacobs on 2010-05-24
For Japanese input capability, it used to be sufficient to install Japanese capability from the Language Support tool of the System -> Administration. Obviously not now. I'd already spent a lot of time with the so-called obvious answer before winding up over here... The Language Support tool did SEEM to give me the option of installing Japanese input support, but apparently they fooled me again.

Excuse me, but this is completely insane. Why is Ubuntu getting worse and WORSE with each release? They've already convinced me to stop recommending Ubuntu. I can't even defend Ubuntu against criticism. The reply to "Ubuntu isn't ready for prime time" would be "Yes, but it's even LESS ready than it used to be." I'm still keeping my finger in, but at this point it's basically inertia and residual dislike of Microsoft (and increasing dislike of Apple and Google). I've already spent a lot of time becoming fairly comfortable in the Ubuntu environment, and I think that any other Linux distro would probably give me the same amount of grief. I've given up hoping for any joy here...

---

### Post by James Keating on 2010-05-25
Update for Lucid 10.04:

Ubuntu now uses IBus and no longer supports SCIM. Too bad IBus doesn't work with any Qt-based programs. 

My current language setup:

1. Under System, Administration, Language Support, choose Japanese.

2. Install programs that Ubuntu doesn't include by default (including essential packages ...)
edict
enamdict
gjiten
kanjidic
kdrill
poppler-data (to view Japanese PDFs)
gs-cjk-resource
cmap-adobe-japan1 
cmap-adobe-japan2
xpdf-japanese

To use SCIM, install:
scim-anthy
scim-bridge-agent
scim-bridge-client-gtk
scim-bridge-client-qt
scim-gtk2-immodule
scim-modules-socket
scim-qtimm

Anthy should already be present, along with ibus-anthy.

To be able to add Japanese words to the dictionary (such as names and place names), install kasumi.

I also installed more ttf fonts, but not all: Sazanami and Kochi gothic and mincho, VL Gothic, , Kiloji, Mikachan and ttf-mscorefonts (MS Gothic and Mincho, Osaka).
Other nice fonts are available at [http://www.wazu.jp/gallery/Fonts_Japanese2.html;](http://www.wazu.jp/gallery/Fonts_Japanese2.html;) download and put in your ~/.fonts directory. Not all have romaji, and not all even work. I kept: Aoyagi Kouzan(&#38738;&#26611;&#34913;&#23665;), Soseki and Reishoka (&#38738;&#26611;&#38583;&#26360;&#19979;), Aquafont, Armed Lemon, Azukifont, Cinecaption, Deshima (&#20986;&#23798;), several Epson fonts, HuiFont, Kouzan brush (two), Makiba, Mona, Moon, MtTare, nagurigaki, Ohisama, Onryou, SZG Memo, Sanafon (two), Sea, Sword, unifont 

3. the hidden home directory file ~/.xinput.d/en_US, which links to /etc/X11/xinit/xinput.d/scim-bridge, may need editing (as root)
I changed mine to prefer scim-bridge, then scim, and not xim:

XIM=SCIM
if [ -e /usr/bin/skim ]; then
XIM_PROGRAM=" "
else
XIM_PROGRAM=/usr/bin/scim-bridge
fi
XIM_ARGS="-d"
if [ -e /usr/lib/gtk-2.0/*/immodules/im-scim-bridge.so ]; then
GTK_IM_MODULE=scim-bridge
else
GTK_IM_MODULE=scim
fi
if [ -e /usr/lib/qt3/plugins/inputmethods/im-scim-bridge.so ]; then
QT_IM_MODULE=scim-bridge
else
QT_IM_MODULE=scim
fi
DEPENDS="scim | skim, scim-bridge-agent, scim-bridge-client-gtk | scim-bridge-client-qt"

4. Opera, and possibly other QT-based applications, may have more trouble than before. If you can't get Opera to work again with scim, you can start it from the command line with 
scim -d & XMODIFIERS="@im=SCIM" QT_IM_MODULE="scim" opera

To start it from the regular menu, I made a file called ~/.bin/opera-scim:

#!/bin/sh
QT_IM_MODULE="scim"; export QT_IM_MODULE
XIM_PROGRAM="scim -d"; export XIM_PROGRAM
opera

and then edited the menus to change the properties of the Opera item to run that file:
opera-scim %u

---

### Post by orengolan on 2010-06-12
Thank you so much James for taking the time and writing those steps for Lucid.

since I use Lubuntu Lucid I don't think I can use the visual instructions on this thread. 
I would really like a step by step instructions (I would assume text-based) including all the packages I need and the way to switch between English and Japanese.

having Those instructions will be valuable for
xubuntu/lubuntu/kubuntu or any ubuntu-based distro.

Thanks again!

---

### Post by James Keating on 2010-06-13
Thanks. I've edited my post to note a few more packages that may be needed, especially for those running QT programs like Opera and KDE.

I never heard of Lubuntu before, but the steps ought to work for any variant of Ubuntu. I think it's all there. Add Japanese under System > Administration > Language Support, and pick an input method (IBus is preferred now, but SCIM-Bridge is still better). With Synaptic, add the packages Ubuntu forgot, plus those you may need for QT applications. 

Ubuntu makes this all simple, aside from pushing IBus before it's ready.

The only thing that has confused me so far was switching the display language. Anything in the list you initially see under Language Support is available, even if it is grayed out. To change to a language that is grayed out, you can't click on it. Instead, you have to grab it and drag it to the top of the list, then log out and in. Took me quite a while to figure that out. The whole interface is very counterintuitive. (And I wish it would stop insisting I have every English variant installed.)

---

### Post by orengolan on 2010-06-13
thanks!

I also found this thread and going to try it as well:
[http://swiss.ubuntuforums.org/showthread.php?t=1473389&page=3](http://swiss.ubuntuforums.org/showthread.php?t=1473389&page=3)

---

