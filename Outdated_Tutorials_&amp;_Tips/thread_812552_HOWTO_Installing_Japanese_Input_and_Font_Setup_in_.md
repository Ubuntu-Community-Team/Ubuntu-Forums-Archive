---
title: "HOWTO: Installing Japanese Input and Font Setup in Ubuntu 8.04 (Hardy) using SCIM &#26085;&#26412;&#35486;"
date: 2008-05-30
forum: Outdated Tutorials &amp; Tips
---

### Post by ryukent on 2008-05-30
[SIZE="4"]**HOWTO: Installing Japanese Input and Font Setup in Ubuntu 8.04 (Hardy) using SCIM: &#26085;&#26412;&#35486;** [/SIZE]
 
Installing Japanese Input and Superior Font Setup in Ubuntu 

**Introduction**

This is a guide to setting up Japanese for Ubuntu 8.04 Hardy. It is intended as a complete guide encompassing all elements required for using Japanese on any language installation of Ubuntu. It covers input (SCIM-Anthy) and configuring the Japanese fonts. There are other guides around for older versions of Ubuntu or that use the alternative UIM (see other guide). This guide is intended to cover everything. Please note that Kubuntu requires slightly different steps. Please follow the relevant page accordingly. This is an updated version based on the original 6.10 one, but with some sections changed. Please note that if you follow this guide, your fonts will be reconfigured. This might mean losing some font settings you may have made. With each version of Ubuntu, there are certain changes, this guide is not the same as the 7.10 version.

**Issues Involved**

There are two main issues here: 
 
1.Installing the SCIM input system that will work in a locale other than converting your whole install to Japanese, i.e. you want Japanese input in an English login. 

2.The fonts look initially terrible. Therefore a certain amount of customisation is required to make all the Kanji's render in the same style and Hiragana & Katakana to render in a matching style. 
  
**Japanese Input with SCIM**

This section covers setting up the Japanese input system using SCIM Anthy. This involves, downloading, installing and configuring it so that you can use it in non-Japanese locales (e.g. your system is in English). 
  
**Setting Up Repositories**

First lets make sure you have the correct repositories installed in order to automatically download the relevant packs. Make sure you have the Universe and Multiverse repositories switched on. This can be done in 'Synaptic Package Manager' under the repositories tab. Also, you need the Japanese repository too. Open the repositories list file: 
  
```
gksudo gedit /etc/apt/sources.list
```

Add the following line at the bottom: 
  
```
deb http://archive.ubuntulinux.jp/ubuntu-ja hardy/
```

Note that you will need to change 'hardy' if you are using a different version from 8.04. Now update your repos with: 

```
sudo apt-get update
```

At this stage, you will probably get an error saying that the repository is not validated. Ignore this for now. The following step will correct it. After adding the repository and running the update, you also need to add a keyring for the new location: 
  
```
sudo apt-get install ubuntu-ja-keyring
```  

**Adding Ubuntu Language Support**

Go to System / Administration / Language Support and select Japanese. This should install the basics. Make sure you've also turned on support for inputting complex characters.

**Making SCIM available under a non-Japanese login**

Now you want to make SCIM (Language input system) available in your English (or other language) login and not just the Japanese one. Since 8.04, ubuntu will make it available in GTK applications, but if you want to run non-GTK applications such as KDE or pure X software such as those Java based you'll need to make a few changes. If you are running a US locale, it might work with defaults, but any other locale will almost certainly need registering. First open the scim global settings file: 

```
gksudo gedit ~/.scim/global
```

Add the line: 

```
/SupportedUnicodeLocales = en_US.UTF-8,en_GB.UTF-8
```

The above line adds support for US and UK locales. If you are using a different locale, you will need to change / add the relevant locale. You can find out the name of your current locale by entering:

```
locale
```

In my case (UK) it returns LANG=en_GB.UTF-8. Add the necessary to the above line. 

**IMPORTANT NOTE**: SCIM is very unforgiving with this line. Note that there is NO SPACE between the "," and "en_GB". If you put a space there, it will ignore everything after. Therefore make sure the following locales are separated by a comma only.

At this stage you'll probably need to log out and back in again. Open a text editor and hit ctrl+space. SCIM should pop up ready to type in Japanese.

**Adding handwriting recognition support for looking up Kanjis**

After adding the above repository, you should be able to install the 'Tomoe' handwriting recognition addon for scim using:

```
sudo apt-get install scim-tomoe
```

Unfortunately, Tomoe is set to load dictionaries that correspond to the locale, so if you're not using a Japanese locale, you'll need to create a link to the dictionary manually.

```
cd /usr/share/tomoe/recognizer
sudo cp handwriting-ja.xml handwriting-en.xml 
```

Where 'en' corresponds to your locale type. In my case (en_GB.UTF-8) it is 'en'. For you, it might be different. You can look it up as mentioned above.

Now that Tomoe is installed, it is accessible on the SCIM menu under the 'SCIM Command Menu' and listed as 'Handwriting recognition'.

**Setting up the system to display Japanese characters properly**

OK, now you've got Japanese input installed (hopefully). It might require rebooting xwindows (CTRL+ALT+Backspace). But for me, I really didn't like the horrible fonts that defaulted. Particularly the fact that hiragana / katakana characters are rendered differently from kanjis and the poor quality of smaller sizes annoys me. The main reason for this is that the fonts provided do not always have a full set of kanjis, with default settings the kanjis are rendered as bitmaps and the hiragana and katakana as vectors. 

At lower font sizes, it would be impossible to render all the strokes in very complicated characters without blurring and this causes a readability problem. This can be overcome with bitmap alternatives at a low end. Certain strokes are omitted and the shape is actually changed in order to improve readability. It's not simply a case of rendering the same vector in a smaller size. Some true type fonts contain bitmap alternatives that can be automatically substituted at the low end. This is a common approach and is adopted by Windows, MacOS and other electronic devices in Asia such as mobile phones. Here's the next step. 
  
**Downloading External Fonts**

Unfortunately, I am very disappointed in the Ubuntu selection and you will almost certainly want this to be changed to MSGothic and MSMincho. They contain a superior vector and bitmap selection. These are Microsoft fonts, but they are freely available to use and are actually from a company called Ricoh. They need to be downloaded and installed manually. They can be found at the following page. 

[[IMG]https://help.ubuntu.com/htdocs/ubuntu/img/u-www.png[/IMG] http://www.linux.ryukent.co.uk/show.php?id=24]("http://www.linux.ryukent.co.uk/show.php?id=24") 

So download and extract the files and you need to copy them into the fonts directory. This will need root privileges and is probably easiest done using the file explorer: 

```
gksudo "nautilus --browser"
```

That will give you a browser with the right privileges. So copy your downloaded ttf files and paste them into a folder under the fonts tree. I recommend: 

```
/usr/share/fonts/truetype/msjapanesefonts
```
 
**Rebuilding the font cache**

Now we need to rebuild the fonts cache: 

```
sudo fc-cache -f -v
```

**Setting up the font order**

OK, so that might well be enough, but I think you'll probably still have your Japanese fonts not running at optimum and the default might be a little ugly. Lets set up the order in which we like the fonts to be selected. Open the &#8220;.fonts.conf&#8221; file in your home directory: 
  
```
gksudo gedit ~/.fonts.conf
```

It should read as follows: 

```

<?xml version="1.0"?>
<fontconfig>
 <alias>
 <family>serif</family>
 <prefer>
 <family>DejaVu Serif</family>
 <family>Times New Roman</family>
 <family>&#65325;&#65331; &#26126;&#26397;</family>
 <family>IPAPMincho</family>
 <family>Sazanami Mincho</family>
 <family>Kochi Mincho</family>
 <family>Bitstream Vera Serif</family>
 <family>Thorndale AMT</family>
 <family>Luxi Serif</family>
 <family>Nimbus Roman No9 L</family>
 <family>Times</family>
 <family>Frank Ruehl</family>
 <family>MgOpen Canonica</family>
 <family>AR PL SungtiL GB</family>
 <family>AR PL Mingti2L Big5</family>
 <family>FreeSerif</family>
 <family>Baekmuk Batang</family>
 </prefer>
 </alias>
 <alias>
 <family>sans-serif</family>
 <prefer>
 <family>DejaVu Sans</family>
 <family>Verdana</family>
 <family>&#65325;&#65331; &#12468;&#12471;&#12483;&#12463;</family>
 <family>IPAPGothic</family>
 <family>Sazanami Gothic</family>
 <family>Kochi Gothic</family>
 <family>Bitstream Vera Sans</family>
 <family>Arial</family>
 <family>Albany AMT</family>
 <family>Luxi Sans</family>
 <family>Nimbus Sans L</family>
 <family>Helvetica</family>
 <family>Nachlieli</family>
 <family>MgOpen Moderna</family>
 <family>AR PL KaitiM GB</family>
 <family>AR PL KaitiM Big5</family>
 <family>FreeSans</family>
 <family>Baekmuk Dotum</family>
 <family>SimSun</family>
 </prefer>
 </alias>
 <alias>
 <family>monospace</family>
 <prefer>
 <family>DejaVu Sans Mono</family>
 <family>Courier New</family>
 <family>&#65325;&#65331; &#12468;&#12471;&#12483;&#12463;</family>
 <family>IPAGothic</family>
 <family>Sazanami Gothic</family>
 <family>Kochi Gothic</family>
 <family>Bitstream Vera Sans Mono</family>
 <family>Andale Mono</family>
 <family>Cumberland AMT</family>
 <family>Luxi Mono</family>
 <family>Nimbus Mono L</family>
 <family>Courier</family>
 <family>Miriam Mono</family>
 <family>FreeMono</family>
 <family>AR PL KaitiM GB</family>
 <family>Baekmuk Dotum</family>
 </prefer>
 </alias>
 <match target="font" >
 <edit mode="assign" name="embeddedbitmap" >
 <bool>true</bool>
 </edit>
 </match>
</fontconfig>

```

So, save the file and reboot xwindows (CTLR+ALT+Backspace). Now with any luck the order of fonts should have been updated so that the default Japanese type face is actually a clean one first and foremost instead of the ugly first serving. Also it enables the built in bitmap font which can really make kanji's more readable and also enables the bitmap version of hiragana and katakana so that they don't look blurry anti-aliased next to clear bitmap kanjis. For most people this setting will be fine. If you're not happy, by all means leave out the embeddedbitmap setting or change it to false.

To finish things off, I'd suggest making sure in System / Preferences / Appearance / Fonts, you've got subpixel smoothing on and after clicking on details, hinting is set to 'full'.

If you have any additional questions, please don't hesitate to message me in this forum. I'm always happy to help, though I make take a little while responding. &#38929;&#24373;&#12387;&#12390;&#12367;&#12384;&#12373;&#12356; - RyuKent

---

### Post by tacutu on 2008-05-30
thanks for the tutorial.
however, there's something I don't understand: what exactly do we gain by adding the ubuntu-ja repository? Is there any software which is not already available in the ubuntu repos?

---

### Post by ryukent on 2008-05-30
Adding the repos was in previous versions of this guide as they contained fonts that weren't in the normal repos. Some are no longer available, so I've omitted that section. All should work fine without the 'ja' repository, however I find that updates to the Japanese system are released faster in this repository. Also there are a number of other useful programs that you can only find there. In order to keep the guide a complete Japanese setup tutorial, I thought it necessary to leave that section in.

---

### Post by Zorael on 2008-05-30
Awesome tutorial, many thanks. Bitmaps were just the thing I was looking for. (...though by chance happened to enable earlier after furious googling.)

&#36074;&#21839;!

[list][*]Are these Ricoh fonts exact copies of the ones found on a Windows system? Or new-and-improved versions? Because I nicked my whole font directory from my Windows partition, which got me all kinds of peculiar fonts, including MS Mincho and Gothic.


[*]After adding the repository, should I install any extra hitherto-deselected-or-unavailable packages? I see it updated scim, anthy and the bridge packages, which is always nice.


[*]I made a symlink towards my [FONT="Courier New"]~/fonts.conf[/FONT] file at [FONT="Courier New"]/etc/fonts/fonts/conf.d/99-zor.conf[/FONT]. Will this make the setting system-wide? Should it perhaps be named [FONT="Courier New"]01-zor.conf[/FONT]? I figured the higher the number the later it would be included, and as such override any previous settings.


[*][quote="me, in my ignorance"]Semi-relevant, but how do I enter the Japanese quotation signs? :oops: Entering normal " quotes just gives me the suggestions &#8221;, &#8220; and the unmodified ".[/quote]
edit: Pah, found it; [ and ] becomes &#12300; and &#12301;.


[*]Any further steps to take for us Kubuntulings? On a side note, I didn't seem to have a .fonts.conf file to begin with, unless my memory is sorely failing me.


[*]Must the .fonts.conf entry be &#65325;&#65331; &#26126;&#26397; and &#12468;&#12471;&#12483;&#12463; or does MS Mincho and Gothic suffice? (More out of interest.)


[*]The limit at which it stops using bitmaps seems to be at 16px (vectoring above). Is there a way of altering this? (Also out of interest.)


[*]Is there a way to get scim enabled at the login screen? Likely not? (Yep, interest.)[/list]

---

### Post by TokyoYank on 2008-05-30
RyuKent, you are an asset to the ubuntu and linux community, thanks.  (I'll also soon be posting a question to the [_effective *TangoBlaster* thread_]("http://ubuntuforums.org/showthread.php?t=337639").)

However, some comments:

I was able to get SCIM to work for Japanese input on my English installation simply through System > Administration > Langauge Support , however to date there may have been varying degrees of success with that method:  [http://ubuntuforums.org/showthread.php?t=783036](http://ubuntuforums.org/showthread.php?t=783036)

Second, do you use a handwriting recognition program to look up kanji?  The very useful program *tomoe* is not in my default Hardy repo's for some reason.  (I'm located in Japan, thus use the Japan servers)  ..
To be honest, this is one aspect of Hardy which is pushing me back towards Fedora..

[http://ubuntuforums.org/showthread.php?t=783673](http://ubuntuforums.org/showthread.php?t=783673)  tomoe and kanjipad

Any thoughts or comments much appreciated

---

### Post by tacutu on 2008-05-30
Browsing the repo recommended by Ryukent I noticed that tomoe is available:
[http://archive.ubuntulinux.jp/ubuntu-ja/hardy/](http://archive.ubuntulinux.jp/ubuntu-ja/hardy/)

---

### Post by Zorael on 2008-05-31
I couldn't get tomoe to work while under a non-Japanese locale. Modifying [FONT="Courier New"]/usr/bin/scim-tomoe[/FONT] makes it work *if* started manually, but if I right-click the skim toolbar and start it from there it still didn't work. It would seem it calls tomoe directly instead of through the wrapper script in [FONT="Courier New"]/usr/bin/[/FONT]. Note, this is with KDE and skim.
```
$ cat /usr/bin/scim-tomoe
#!/bin/sh
# scim-tomoe launcher
*<truncated comments>*
# $Id: scim-tomoe.in,v 1.2 2006/12/11 06:28:42 makeinu Exp $

prefix=/usr
exec_prefix=${prefix}
libdir=${exec_prefix}/lib
includedir=${prefix}/include
localedir=${datarootdir}/locale
datarootdir=${prefix}/share
datadir=${datarootdir}
sysconfdir=${prefix}/etc

# zor
[B]export LANG=ja_JP.UTF-8
export LC_MESSAGES=ja_JP.UTF-8[/B]

/usr/lib/scim-1.0/scim-helper-launcher tomoe b1bfe2b4-6930-41b0-8c07-d05bce8c92e2 $*
```
(Nevermind the # zor, I always add that so I can see when it's something manually modified, when memory fails me.)

Again, this made it work when running scim-tomoe manually, from a run box or a terminal, but not when having skim start it for me. So I copied the recognition dictionary.
```
zorael@sunspire:~$ cd /usr/share/tomoe/recognizer
zorael@sunspire:/usr/share/tomoe/recognizer$ ls
**handwriting-ja.xml**  handwriting-zh_CN.xml
zorael@sunspire:/usr/share/tomoe/recognizer$ sudo cp handwriting-ja.xml **handwriting-en.xml**
zorael@sunspire:/usr/share/tomoe/recognizer$
```

Oh, and yay for skim-scim-anthy. :>

---

### Post by Sean Dun on 2008-05-31
Hi – I've followed ryukent's instructions (excellent job!) and everything works great except for one program. I'm new to Ubuntu (and Linux) so I'm not sure where to go from here and was hoping someone could point me in the right direction. 

I'm unable to get SCIM-Anthy to work with Anki (a flash card study program). I'm running Ubuntu 8.04 and have the latest version of Anki (0.9.5.7) installed along with all the dependencies listed in the package manager (at >= versions). When I try to start Anthy (either with ctrl + space or by clicking on the SCIM keyboard icon) while using Anki, I don't get the Anthy's menu and SCIM stays set on English/Keyboard. Other people have reported having no issue with Anki & SCIM-Anthy. Below are my are installed packages and the text from /etc/X11/xinit/xinput.d/scim. They seem to match everyone else's that I've found discussing similar issues. Any ideas on where I should look next? Thanks in advance.
```

 dpkg --get-selections | grep scim

libscim8c2a					install

scim						install

scim-anthy					install

scim-bridge-agent				install

scim-bridge-client-gtk			install

scim-bridge-client-qt				install

scim-bridge-client-qt4			install

scim-gtk2-immodule				install

scim-modules-socket				install


dpkg --get-selections | grep -i qt4

libqt4-core					install

libqt4-gui					install

libqt4-qt3support				install

libqt4-sql					install

python-qt4					install

python-qt4-common				install

scim-bridge-client-qt4			install



sudo gedit /etc/X11/xinit/xinput.d/scim

XIM=SCIM

XIM_PROGRAM=/usr/bin/scim

XIM_ARGS="-d"

XIM_PROGRAM_SETS_ITSELF_AS_DAEMON=yes

GTK_IM_MODULE="scim-bridge"

QT_IM_MODULE="scim-bridge"

DEPENDS="scim,scim-anthy|scim-canna|scim-chewing|scim-pinyin|scim-hangle|scim-prime|scim-skk|scim-tables-additional|scim-m17n|scim-uim|scim-tables-ja|scim-tables-ko|scim-tables-zh"
```

Sean Dun

---

### Post by tacutu on 2008-05-31
since anki uses qt, what's the output of:
```
export | grep QT

```
are other non-gtk apps working?

---

### Post by ryukent on 2008-06-01
Sean,

If you're using a QT app like Anki and you're only getting the keyboard and are unable to select Anthy, it is probably because your global file doesn't have your locale enabled. SCIM should have no problem sending data to standard QT input boxes. Have you checked other QT4 apps??

If that doesn't work, it could be that the program was written with some hard coded algorithm that ignores non alphabet text, though if its a kanji flash card program, I doubt it.

---

### Post by ryukent on 2008-06-01
Zorael,

Good work on finding the xml link. I've added that to the original post.

Also, if you want to setup the size at which bitmapping is enabled or disabled, you can add:

<test name="pixelsize" compare="more_eq"><int>17</int></test>

to the fonts.conf file before the embeddedbitmap is switched on or off. In the above case the test passes if the size is more or equal to 17.

---

### Post by Sean Dun on 2008-06-01
tacutu & ryukent &#8211; Thanks for the help.

I installed KNotes & KJots to try non-gtk applications. They both had the same issue as Anki.

Here is some more information:
```

export | grep QT
declare -x QT_IM_MODULE="scim"
```

Here are the contents of ~/.scim/global (I think this is the file ryukent was referring to). My locale is en_US.UTF-8:

```
/SupportedUnicodeLocales = en_US.UTF-8,en_GB.UTF-8
``` 

I don't know if it is relevant, but I had to create the global file when setting up Japanese input.

---

### Post by tacutu on 2008-06-02
dunno is this is going to help, but here the QT_IM_MODULE is set to XIM and I have no problems w/ anki. I used im-switch and everything worked out of the box:
```
im-switch -z all_ALL -s scim-bridge

```
(apparently scim-bridge is to be preffered over scim since it avoids some bugs)

Edit: ok, so I installed Scim-bridge-client-qt4 and did:
```
export QT_IM_MODULE=scim-bridge && anki
```
to force anki to use scim (as opposed to xim) and it worked fine.

---

### Post by TokyoYank on 2008-06-02
> **ryukent said:**
> .. Also there are a number of other useful programs that you can only find there. In order to keep the guide a complete Japanese setup tutorial, I thought it necessary to leave that section in.

Appears that tomoe is an example of the discrepancy.  And I can verify that "ubuntu-ashisuto.ubuntulinux.jp/ubuntu" does not have it--just because it's a server in japan does not mean it's a ubuntu-ja server I guess.  

Any idea why this behavior exists?  Am I alone in thinking that the GUI for adding Japanese language support should also add a ubuntu-ja repo also (or at least give a warning about it)

My only guess so far is that the number of users like us who need multi-language support--different from the session locale, I mean--is small, so that we pass under the ubuntu admin radar..


New Topic:

I started thinking about a way to make the instructions GUI only, without involved command line settings.  The eventual aim would be instructions to incorporate into an official Hardy How-To document, but I didn't get too far before needing CLI again.

Here's how I updated my repositories and installed tomoe using the GUI
[LIST]
[*]*System > Administration > Software Sources > Third-Party Software > Add*
[*]Text entry box, use the OP entry:
**deb [http://archive.ubuntulinux.jp/ubuntu-ja](http://archive.ubuntulinux.jp/ubuntu-ja) hardy/**
Get a warning about this repository is NOT AUTHENTICATED.  OK, can ignore that for now.
[*]*System > Administration > Synaptic Package Manager > Search *
**ubuntu-ja-keyring**
Click on box to Mark for Installation, same authentication error, can ignore.  ==> click "Apply"
[*] *.. to be honest.. after this point I'd like someone else to confirm the instructions.  It's hard for me to go back to a clean install to test this.*  In Synaptic click "Reload"
[*]"Search" for tomoe.   Mark *scim-tomoe* for installation, and allow other required packages.
[/LIST]

At this point the handwriting-ja.xml should be copied manually.  .. perhaps there should/could be a tomoe-scim-compat-multilang (or something) package that does this?

---

### Post by ryukent on 2008-06-02
Sean,

Did you install Hardy from a Hardy CD or is it an upgrade from Gutsy? All the tests I've done are from a fresh install and it is possible old settings somewhere could be interrupting.

Also, as tacutu pointed out, im-switch could help. It was in old versions of my howto, but hardy runs it by default now.

Try running:

im-switch -l

It should say your configuration is pointing to something. This something should be scim-bridge. If it's still not working, can you post the output.


Tokyoyank,

I'm pretty sure us multilinguals get ignored. I've really noticed that there's a huge assumption that the only people who would ever be typing in Japanese are Japanese themselves who would have their entire system in Japanese locale. In my opinion there should be no difference between the repositories. If a newer version of software is released and it has improvements, then why should everyone's system not be updated? Why should software be limited to certain regions? Do people not travel? It's been like this for years.

Plus, why do programmers write software for certain locales? Should not all software run on all ubuntus?? I fully understand the localisation issue as far as language translation is concerned, but beyond that there is no excuse. In my opinion, when you go into the language selection dialogue box and click Japanese (or any other language) on, it should install everything. If fonts or input methods are needed, then of course they should be installed. Who the hell wants half their applications to not work correctly or who wants a partially crippled system with mismatching display?

The day I stop writing in these kind of threads will be the day I consider Ubuntu to truly be worthy as a mainstream OS. I love Ubuntu and will continue to support it fanatically, but I can really understand why some people can't deal with the 'issues'. Until even idiots can set up their system, people will shun linux as an enthusiasts only system. It is not acceptable for this community to look down on people who can't manage complicated setup. It is our responsibility to make it simple for them.

---

### Post by tacutu on 2008-06-02
Venting your frustration, aren't you? :lolflag: 
Seriosusly now, I totally agree with you. There shouldn't be any need for "special" repos. Moreover, the said repos are mentioned only on the Japanese page on the Ubuntu website. (which could be a problem for a beginner who could not read so much Japanese but still wants IME and such for learning purposes)

Maybe we should signal the situation as a bug?

---

### Post by Zorael on 2008-06-02
> **tacutu said:**
> Maybe we should signal the situation as a bug?
Agreed.

---

### Post by Shibata on 2008-06-02
ryuken,
Thank you for nice guide. Let me add some information, if you don't mind.

Fonts:
ttf-vlgothic is beautiful Japanese Gothic font. And you can install it from official repository.

ipamonafont is very beautiful and almost fullset Japanese Gothic/Mincho font. But this package is only in ubuntu-ja repo. For license issue, ipamonafont package cannot be distributed from official repository. Fortunately, there is a possibility in the future that can be archived in official repository (I think it will be Intrepid+1 or Intrepid+2).


Japanese PDF:
If you would like to display Japanese fonts in PDF files by Evince, you should install poppler-data from official repository.


> **tacutu said:**
> There shouldn't be any need for "special" repos.
I agreed. However packages in ubuntu-ja repo have several reasons not to archive into official repository yet. For example, license issue, harmful effect to other locale, have no time to reviewing, etc... I think that developers and Japanese LoCo members are trying to migrate ubuntu-ja's packages to official repository.

---

### Post by Sean Dun on 2008-06-02
tacutu & ryukent,

I used tacutu's export command and could input Japanese into Anki with SCIM-Anthy. As a work around I could just use that command each time – although I would like to get settings “right” so any qt app would work. So if you have any further suggestions I would appreciate them. 

I also tried the im-switch command, but that didn't change the input issue with Anki.

My installation of Hardy is from the CD – not an upgrade. One possible cause of the issue could be that I got SCIM-Anthy working before ryukent's 8.04 instructions. I initially followed the 7.10 instructions (then unistalled SCIM-Anthy and and re-installed following the 8.04 instructions when I had issues with Anki). Maybe I messed something up that way?

More info:
```
im-switch -l
Your input method setup under en_US locale as below.
=======================================================
The configuration "/home/bluemoon/.xinput.d/en_US" is defined as a link pointing to
scim-bridge
This private configuration supersedes the system wide default.
=======================================================
The system wide default is pointed by "/etc/alternatives/xinput-all_ALL" .
xinput-all_ALL - status is auto.
 link currently points to default
default - priority 10
default-xim - priority 0
none - priority 0
Current `best' version is default.
=======================================================
The available input method configuration files are:
default default-xim none scim scim~ scim-bridge scim-immodule th-xim 
=======================================================
```


The contents of "/home/bluemoon/.xinput.d/en_US" are
```
XIM=SCIM
XIM_PROGRAM=/usr/bin/scim
XIM_ARGS="-d"
XIM_PROGRAM_SETS_ITSELF_AS_DAEMON=yes
if [ -e /usr/lib/gtk-2.0/*/immodules/im-scim-bridge.so ]; then
    GTK_IM_MODULE=scim-bridge
else
    GTK_IM_MODULE=xim
fi
if [ -e /usr/lib/qt3/plugins/inputmethods/im-scim-bridge.so ]; then
    QT_IM_MODULE=scim-bridge
else
    QT_IM_MODULE=xim
fi

```

---

### Post by tacutu on 2008-06-02
Ok, so your system is set up to use scim-bridge, but in fact earlier you reported that 
```
export | grep QT
declare -x QT_IM_MODULE="scim"
```
I don't understand why QT_IM_MOD is scim instead of scim-bridge! (or xim, as a fallback, according to the en_US script in your .xinput folder)

There is an additional complication in that there are 2 major versions of QT: 3 and 4. Anki uses QT4.
I don't have any idea how to set up IME if you happen to use QT3 for some apps and QT4 for some other... maybe somebody else can enlighten us. 

Anyhow, maybe you can try this:
```
cd .xinput.d
rm en_US
cp /etc/X11/xinit/xinput.d/scim-bridge en_US
gedit en_US
```
(all this was done in order to avoid changing system files, since en_US is in fact a symlink)
NOw, edit the contents of the file so that it looks like this:
```
XIM=SCIM
XIM_PROGRAM=/usr/bin/scim
XIM_ARGS="-d"
XIM_PROGRAM_SETS_ITSELF_AS_DAEMON=yes
if [ -e /usr/lib/gtk-2.0/*/immodules/im-scim-bridge.so ]; then
    GTK_IM_MODULE=scim-bridge
else
    GTK_IM_MODULE=xim
fi
#if [ -e /usr/lib/qt3/plugins/inputmethods/im-scim-bridge.so ]; #then
    QT_IM_MODULE=scim-bridge
#else
#    QT_IM_MODULE=xim
#fi
```

(i.e. comment out some lines by adding the # symbol)

---

### Post by ryukent on 2008-06-03
Shibata,

Sazanami is another good font, though I have to admit, I prefer the MS and IPA ones.

On my system I have the following font packages installed:

ipamonafont
ttf-kochi-gothic
ttf-kochi-mincho
ttf-sazanami-gothic
ttf-sazanami-mincho
ttf-vlgothic

They should all be available in the above mentioned repository for anyone who wants a more varied font selection.

Plus, I'd recommend the msttcorefonts package to everyone because it allows some web pages to be displayed in the way they were designed.

---

### Post by Sean Dun on 2008-06-03
tacutu – I'm quite puzzled too. From everything I've read so far, my system is setup to use scim-bridge, but I don't understand why QT_IM_MODULE is still set to scim. There must be another step is setting the variable? I tried your latest suggestion, but unfortunately it didn't change my situation. I also tried logging is as a new user and logging in with Japanese as locale, but that didn't help either. Thanks again for all your help. SD

---

### Post by Zorael on 2008-06-04
What does your /etc/X11/xinit/xinput.d/scim-bridge look like, then?

---

### Post by Sean Dun on 2008-06-04
Contents of /etc/X11/xinit/xinput.d/scim-bridge:
```
XIM=SCIM
XIM_PROGRAM=/usr/bin/scim
XIM_ARGS="-d"
XIM_PROGRAM_SETS_ITSELF_AS_DAEMON=yes
if [ -e /usr/lib/gtk-2.0/*/immodules/im-scim-bridge.so ]; then
    GTK_IM_MODULE=scim-bridge
else
    GTK_IM_MODULE=xim
fi
if [ -e /usr/lib/qt3/plugins/inputmethods/im-scim-bridge.so ]; then
    QT_IM_MODULE=scim-bridge
else
    QT_IM_MODULE=xim
fi

DEPENDS="scim | skim, scim-bridge-agent, scim-bridge-client-gtk | scim-bridge-client-qt"
```

If anyone has further suggestions, I'd be happy to try them out. However, since I have a rather simple workaround (thanks to tacutu) I think that I should stop taking up people's time on this issue. So please don't feel obligated to continue helping. Thanks again for you assistance.

SD

---

### Post by Zorael on 2008-06-04
And your output of the following, entered in a terminal?
```
$ ls -l /etc/alternatives/xinput*
```
Make the terminal window wide to avoid wrapping.

---

### Post by tora201 on 2008-06-05
Edit: ok, so I installed Scim-bridge-client-qt4 and did:
```
export QT_IM_MODULE=scim-bridge && anki
```
to force anki to use scim (as opposed to xim) and it worked fine.[/QUOTE]

Ok, how do I&#12288;make this work automactically everytime I&#12288;run a Qt4 application (like skype). It works fine when I&#12288;type it in a terminal but how to make the application work with scim automactially?

-Thanks, in advance.

p.s I&#12288;am actually now running dreamlinux 3.0 btw....

---

### Post by Zorael on 2008-06-05
We'll need to see the contents of your [FONT="Courier New"]/etc/X11/xinit/xinput.d/scim-bridge[/FONT] file as well as the terminal output of the command I listed in my previous post.

---

### Post by Sean Dun on 2008-06-05
Here are my results:
```
ls -l /etc/alternatives/xinput*
lrwxrwxrwx 1 root root 31 2008-05-22 18:54 /etc/alternatives/xinput-all_ALL -> /etc/X11/xinit/xinput.d/default
lrwxrwxrwx 1 root root 35 2008-05-22 18:54 /etc/alternatives/xinput-ja_JP -> /etc/X11/xinit/xinput.d/scim-bridge
lrwxrwxrwx 1 root root 35 2008-05-22 18:54 /etc/alternatives/xinput-ko_KR -> /etc/X11/xinit/xinput.d/scim-bridge
lrwxrwxrwx 1 root root 30 2008-05-22 05:16 /etc/alternatives/xinput-th_TH -> /etc/X11/xinit/xinput.d/th-xim
lrwxrwxrwx 1 root root 35 2008-05-22 18:54 /etc/alternatives/xinput-zh_CN -> /etc/X11/xinit/xinput.d/scim-bridge
lrwxrwxrwx 1 root root 35 2008-05-22 18:54 /etc/alternatives/xinput-zh_HK -> /etc/X11/xinit/xinput.d/scim-bridge
lrwxrwxrwx 1 root root 35 2008-05-22 18:54 /etc/alternatives/xinput-zh_SG -> /etc/X11/xinit/xinput.d/scim-bridge
lrwxrwxrwx 1 root root 35 2008-05-22 18:54 /etc/alternatives/xinput-zh_TW -> /etc/X11/xinit/xinput.d/scim-bridge
```

---

### Post by Zorael on 2008-06-05
> **Sean Dun said:**
> ```
lrwxrwxrwx 1 root root 31 2008-05-22 18:54 /etc/alternatives/xinput-all_ALL -> /etc/X11/xinit/xinput.d/**default**
```
There it is.
```
$ sudo update-alternatives --config xinput-all_ALL
```
Pick scim-bridge. Log out, restart X (Ctrl+Alt+Backspace), log in, see if it worked.

If there is no scim-bridge to pick, we'll need to add it as an alternative. Say if so.

---

### Post by Sean Dun on 2008-06-05
scim-bridge isn't on the list.

This is what I get:
```
$ sudo update-alternatives --config xinput-all_ALL

There are 3 alternatives which provide `xinput-all_ALL'.

  Selection    Alternative
-----------------------------------------------
*+        1    /etc/X11/xinit/xinput.d/default
          2    /etc/X11/xinit/xinput.d/default-xim
          3    /etc/X11/xinit/xinput.d/none

Press enter to keep the default[*], or type selection number: 

```

---

### Post by Zorael on 2008-06-05
Okay.

```
$ sudo update-alternatives --install /etc/alternatives/xinput-all_ALL xinput-all_ALL /etc/X11/xinit/xinput.d/scim-bridge 10
$ sudo update-alternatives --config xinput-all_ALL
```

---

### Post by Sean Dun on 2008-06-06
I was able to successfully get:
```
lrwxrwxrwx 1 root root 35 2008-06-06 11:54 /etc/alternatives/xinput-all_ALL -> /etc/X11/xinit/xinput.d/scim-bridge
```
However, I'm still not able to input Japanese in qt apps (after a restart). Thanks for the suggestion.

---

### Post by Zorael on 2008-06-11
I guess you have to take another approach in Gnome than in KDE, then. :<


One great ***ouch***: no 64-bit packages, only i386. :(

---

### Post by Zorael on 2008-06-11
I guess I forgot to ask. What is the terminal output of the following? Widen the terminal window a bit so strings don't get truncated.
```
$ dpkg -l scim-bridge*
```

---

### Post by Sean Dun on 2008-06-11
Here it is:

```
$ dpkg -l scim-bridge*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                           Version                        Description
+++-==============================-==============================-============================================================================
un  scim-bridge                    <none>                         (no description available)
ii  scim-bridge-agent              0.4.14-1ubuntu3                IME server of scim-bridge communicate with SCIM
ii  scim-bridge-client-gtk         0.4.14-1ubuntu3                IME server of scim-bridge communicate with SCIM
ii  scim-bridge-client-qt          0.4.14-1ubuntu3                IME server of scim-bridge communicate with SCIM
ii  scim-bridge-client-qt4         0.4.14-1ubuntu3                IME server of scim-bridge communicate with SCIM

```

---

### Post by Paladinestar on 2008-06-16
What I did was implement the font setup methods(didn't bother with input or scim since I don't use japanese, just wanted it to display properly instead of something like this [http://s3.supload.com/free/Japanese-20080616165051.png/view/](http://s3.supload.com/free/Japanese-20080616165051.png/view/))
So what happens now is that whenever I want to save a file with a Japanese filename it gives me an error(where it is unable to safe to an ntfs partition.) I tried saving to an ext3 partition and it saves the file, but upon inspection, the filename has the words "(invalid encoding)" appended to it.
Addendum: On sites like nicovideo 2, 5, and 9 are displayed differently.
For example, here's 7:57 [http://s3.supload.com/free/Japanesenumbers.png/view/](http://s3.supload.com/free/Japanesenumbers.png/view/) and for that matter, I'm not sure if it even is displaying properly. I'm just sick and tired of the Japanese fonts not properly displaying and breaking my output.

Anyone know what the problem is?(better yet, how I can fix it.)
Notes: is it compulsory to install SCIM and tomoe even if I am not going to use Japanese input?

Update: seems that some of my files with Japanese filenames(which were broken previously, as in the display of filenames) have "disappeared"
They cannot be seen via nautilus.

---

### Post by Metaleks on 2008-06-19
I have a very simple problem.

Everything works.  &#26085;&#26412;&#35486; is installed properly, as you can see.  Didn't really follow the guide.  All I did was add language support, and set a hotkey in scim for Japanese.  I was quite happy with the results until a few minutes ago.  Out of nowhere scim decided that it would like to bring out a seperate box from the program I was in (gedit) to input characters in this box, where they would later be transferred to the application (gedit).  It wasn't doing this before.  Does anyone know the option to change it back to the regular input?  I can't for the life of me find it.

---

### Post by ryukent on 2008-06-19
Metaleks,

The option you want is "Embed pre-edit screen into client window". It is in the SCIM global setup dialogue box.

---

### Post by ryukent on 2008-06-19
Paladinstar,

Please see my screenshot for how NicoNico&#21205;&#30011; displays after I've set up the fonts as per the above guide. You need the Ricoh fonts and embeddedbitmapping on.

As for your problem with the NTFS drive.... I suspect it's a result of the way it is mounted. I don't seem to have the same problem. Running "mount -l" gives me the following for my NTFS:

/dev/sda2 on /media/ACER type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096) [ACER]

Try remounting using alternative charsets. I seem to remember having the problem a couple of years ago and it was mounting based.

Also, you said you didn't install the input type. In language support when you turn on Japanese, I believe it sets up a japanese locale on your system, which may be helpful running some apps even if you don't want to input in Japanese.

Finally, as far as the number characters being replaced for Katakana on NicoNico.... it does the same for me too. I've not seen this before. I think it might be a flash related issue. If I find a solution, I'll let you know.

---

### Post by ryukent on 2008-06-19
Following from the above post.... it looks as though ubuntu forums has messed with the image and make it look all blurry. The actual screen output is crisp with all characters matching each other and no blurring. The secret is in the bitmap alternative to prevent antialiasing designed for western fonts from ruining asian type.

---

### Post by Metaleks on 2008-06-19
> **ryukent said:**
> Metaleks,

The option you want is "Embed pre-edit screen into client window". It is in the SCIM global setup dialogue box.
Many thanks!:) That did the trick.

---

### Post by jambes on 2008-07-14
ryukent, thanks for this how to. 
I'm having trouble getting Japanese input working in an en session. 
The output of im-switch -l says:

```
Your input method setup under en_US locale as below.
=======================================================
No private "/home/jambes/.xinput.d/en_US or /home/jambes/.xinput.d/all_ALL" is defined.
=======================================================
The system wide default is pointed by "/etc/alternatives/xinput-all_ALL" .
xinput-all_ALL - status is auto.
 link currently points to default
default - priority 10
default-xim - priority 0
none - priority 0
Current `best' version is default.
=======================================================
The available input method configuration files are:
/usr/bin/find: /home/jambes/.xinput.d: No such file or directory
default default-xim none scim scim-immodule scim_xim th-xim 
=======================================================
```

Can I recreate the missing directory somehow?

---

### Post by TokyoYank on 2008-07-16
This is news related to this thread (and for people reading), however it's not directly Ubuntu.

Recent success with Fedora 9:  The application which changes language & input settings, *im-chooser*, works, with no command-line editing required.  (However, I did have to make sure SCIM was installed, and I started scim at the command line before im-chooser would recognize that an input method was indeed installed)

Anyone know if im-chooser will or can be used in a future Ubunutu?

---

### Post by ricoris on 2008-07-16
Hi! I'm trying to follow this post's tutorial. SCIM seems to work fine in the japanese locale but when I try to make it work in my locale (es_ES.UTF-8) I get a message telling me that the folder doesn't exist. What should I do?? Please help!

---

### Post by jambes on 2008-07-16
ricoris, I was having the same problem. I fixed it by running
```
im-switch -z all_ALL -s scim
```
This created the missing folder. 
I don't know if it's nessesary, but before that I also followed Zorael's advise [[COLOR="DarkOrange"]here[/COLOR]]("http://ubuntuforums.org/showpost.php?p=5123748&postcount=31") and chose scim-bridge for all_ALL.

Hope it helps

---

### Post by ricoris on 2008-07-18
I did as you told me but I still get the same message:(

---

### Post by fart_flower on 2008-09-07
Okay, here's a fun one...

Several months ago I used your guide to get nice looking Japanese fonts for my Ubunutu 8.04 desktop install.  No problems.

Last week I bought an EeePC 1000 to serve as a cute little traveling companion for my fast-approaching trip to Japan.  The first order of business was to install Ubuntu 8.04, followed by enabling nice looking Japanese fonts via your guide.  FAIL!

So I double checked my work.  And triple checked.  And compared settings directly with my desktop computer.  Everything is identical, but fonts still remain super-duper ugly.

Here's what I get: Hiragana, katakana, and *some* kanji are all one font, while the remaining kanji look like some sort of Chinese font.  (ie. they don't match up at all.)  Bleah.  Looks as ugly as that guy who's always staring at me in my bathroom mirror.

(I'm guessing the few kanji that are rendered consistent with the kanas are characters that either do not exist, or are slightly altered in Chinese.)

The only difference between my desktop and sub-laptop install is the EeePC is running a custom kernel.  (Not compiled by me.)  But I can't imagine that would have an effect.  Or does it?  Shouldn't all this font business be user space, not kernel space?

---

### Post by Zorael on 2008-09-07
What does your **~/.fonts.conf** file look like?

---

### Post by fart_flower on 2008-09-07
It's completely "cut 'n' paste" from the guide.

---

### Post by Zorael on 2008-09-08
It sounds to me like you're missing some font, then. As I understand things, for any given character you want X to display in the serif/sans-serif/monotype (virtual?) fonts described in the .fonts.conf file, it will go down the list until it finds a font with that unicode char. That would explain why your kana and "some" kanji are displayed in one font, and then the Chinese wotsamajiggits come crawling.

```
<?xml version="1.0"?>
<fontconfig>
 <alias>
 <family>serif</family>
 <prefer>
[B] <family>Times New Roman</family>
 <family>MS Mincho</family>
[/B] </prefer>
 </alias>
 <alias>
 <family>sans-serif</family>
 <prefer>
[B] <family>DejaVu Sans</family>
 <family>MS Gothic</family>
[/B] </prefer>
 </alias>
 <alias>
 <family>monospace</family>
 <prefer>
[B] <family>DejaVu Sans Mono</family>
 <family>MS Gothic</family>
[/B] </prefer>
 </alias>
 <match target="font" >
 <edit mode="assign" name="embeddedbitmap" >
 <bool>true</bool>
 </edit>
 </match>
</fontconfig>
```
I cut mine down to only that. You get the point, no? "Try first font, if char doesn't exist, try second." Then I put the fancy one uptop and the Ricoh fonts second.

Saving the file and reopening a new program is enough to make it apply the changes. Tinker around and see if you get it nailed down.

---

### Post by fart_flower on 2008-09-08
Already tried that, except with Liberation fonts for Western encoding.  And my installed fonts are *identical* between both desktop and laptop.

---

### Post by fart_flower on 2008-09-13
*sigh*

I managed to find time to switch this little guy on today and fix the problem.

Deep down I knew it had to be something simple...

Too busy looking at file contents, etc. -- not enough time looking at file names.  I saved it as "font.conf" not "fonts.conf".  Yeah...

Eff You See Kay!

---

### Post by Kuzja on 2008-09-14
I have beeing trying to setup Ubuntu for my japanese girlfriend, but she's never been satistfied with japanese input, so what I did was installing Japanese team realese, which you can get here [http://www.ubuntulinux.jp/download/](http://www.ubuntulinux.jp/download/), and then you can either keep japanese locale or switch to english preserving japanese input setup. This method works only for those who is installing new system though.

---

### Post by Zorael on 2008-09-14
What's the difference between having a completely Japanese installation and having a normal (English/other) installation with Japanese set as input language?

(No arrogance, honestly curious.)

---

### Post by fart_flower on 2008-09-14
All the desktop menus and whatnot are in Japanese.  I thought of doing this myself, but balked on the idea.  Maybe with Intrepid Ibex (or Fedora 10?)...

Screenshot image here:
[http://commons.wikimedia.org/wiki/Image:Screenshot-ubuntu-704ja.png](http://commons.wikimedia.org/wiki/Image:Screenshot-ubuntu-704ja.png)

---

### Post by Lord C on 2008-09-15
Thanks ryukent, great guide.

---

### Post by Kuzja on 2008-09-19
> What's the difference between having a completely Japanese installation and having a normal (English/other) installation with Japanese set as input language?

(No arrogance, honestly curious.)

Well, it is really hard for me to say since I was installing it for my gf and she says that it is the way better. As far as I understand it just takes care of some nuances which non-native user wouldn't even notice.

Unfortunately, there is no Japanese kubuntu. I can't find a good guide how to enable japanese input properly in KDE.

---

### Post by brandon88tube on 2008-09-19
This may help shorten the process for others:

Well I installed Japanese a different way on Hardy 8.04.1 and its the SCIM gui version. I just went to System > Administration > Language Support selecting Japanese and then I checked the box next to Enable support to enter complex characters. This did everything for me.


Problems:
On a side note I am having problems and wanted to know if someone could help. When I set the FrontEnd > Global Setup hotkeys the Next input method and the Previous input method along with the Show input method menu, they do not work. The trigger hotkey on the other hand seems to be working fine. I do know that under IMEngine > Anthy there is a keybindings settings, but I set those to nothing because I figured the global settings should do the trick.

Another problem I seem to have is typing Japanese in a Flash box such as the Chatango site. It completely refuses to type in anything, but my primary language. In Windows I was able to do this no problem. I am not sure if this is a Flash problem or a SCIM problem, but I figured I would throw it out there to see if anyone could help with this as well.

---

### Post by shan109 on 2008-10-14
thanks pal, this is a great help!!!!

---

### Post by BuntuFirstTimer on 2008-10-31
> **ryukent said:**
> 
```
deb http://archive.ubuntulinux.jp/ubuntu-ja hardy/
```

Tried it, it doesn't work at all. Are you sure this is the right deb?

Edit: Wait, I got it. Nothing to see.

---

### Post by BuntuFirstTimer on 2008-10-31
> **ryukent said:**
> [SIZE="4"**Setting up the font order**

OK, so that might well be enough, but I think you'll probably still have your Japanese fonts not running at optimum and the default might be a little ugly. Lets set up the order in which we like the fonts to be selected. Open the “.fonts.conf” file in your home directory: 
  
```
gksudo gedit ~/.fonts.conf
```

It should read as follows: 

```

<?xml version="1.0"?>
<fontconfig>
 <alias>
 <family>serif</family>
 <prefer>
 <family>DejaVu Serif</family>
 <family>Times New Roman</family>
 <family>&#65325;&#65331; &#26126;&#26397;</family>
 <family>IPAPMincho</family>
 <family>Sazanami Mincho</family>
 <family>Kochi Mincho</family>
 <family>Bitstream Vera Serif</family>
 <family>Thorndale AMT</family>
 <family>Luxi Serif</family>
 <family>Nimbus Roman No9 L</family>
 <family>Times</family>
 <family>Frank Ruehl</family>
 <family>MgOpen Canonica</family>
 <family>AR PL SungtiL GB</family>
 <family>AR PL Mingti2L Big5</family>
 <family>FreeSerif</family>
 <family>Baekmuk Batang</family>
 </prefer>
 </alias>
 <alias>
 <family>sans-serif</family>
 <prefer>
 <family>DejaVu Sans</family>
 <family>Verdana</family>
 <family>&#65325;&#65331; &#12468;&#12471;&#12483;&#12463;</family>
 <family>IPAPGothic</family>
 <family>Sazanami Gothic</family>
 <family>Kochi Gothic</family>
 <family>Bitstream Vera Sans</family>
 <family>Arial</family>
 <family>Albany AMT</family>
 <family>Luxi Sans</family>
 <family>Nimbus Sans L</family>
 <family>Helvetica</family>
 <family>Nachlieli</family>
 <family>MgOpen Moderna</family>
 <family>AR PL KaitiM GB</family>
 <family>AR PL KaitiM Big5</family>
 <family>FreeSans</family>
 <family>Baekmuk Dotum</family>
 <family>SimSun</family>
 </prefer>
 </alias>
 <alias>
 <family>monospace</family>
 <prefer>
 <family>DejaVu Sans Mono</family>
 <family>Courier New</family>
 <family>&#65325;&#65331; &#12468;&#12471;&#12483;&#12463;</family>
 <family>IPAGothic</family>
 <family>Sazanami Gothic</family>
 <family>Kochi Gothic</family>
 <family>Bitstream Vera Sans Mono</family>
 <family>Andale Mono</family>
 <family>Cumberland AMT</family>
 <family>Luxi Mono</family>
 <family>Nimbus Mono L</family>
 <family>Courier</family>
 <family>Miriam Mono</family>
 <family>FreeMono</family>
 <family>AR PL KaitiM GB</family>
 <family>Baekmuk Dotum</family>
 </prefer>
 </alias>
 <match target="font" >
 <edit mode="assign" name="embeddedbitmap" >
 <bool>true</bool>
 </edit>
 </match>
</fontconfig>

```

My fonts.conf file is completely empty. Did I do something wrong? :(

---

### Post by fart_flower on 2008-11-02
Sorta off topic, but I still can't believe 8.10 has the same ugly default Japanese font rendering.  Absolutely flabbergasting.

---

### Post by Monkeybells on 2008-11-04
Just going back a few pages to fixing Japanese input in a qt4 application....
I'm using 'anki' but since upgrading my distro from 8.04 to 8.10 I've lost the ability to enter Japanese characters. It was possible in Hardy but isn't working in Intrepid.

I am able to get it to work by entering the command "$ QT_IM_MODULE=scim-bridge anki" but unable when running 'anki' normally.

I've searched the forums, made changes, restarted numerous times but have yet to get it to work.

Please help.

---

### Post by ryukent on 2008-11-10
I've made a new post for 8.10.

[http://ubuntuforums.org/showthread.php?t=975144](http://ubuntuforums.org/showthread.php?t=975144)

---

### Post by BastardNamban on 2008-11-24
Hey, this looks like EXACTLY what I was looking for!

I'm having a problem, however- everything fine up until ```
gksudo ~/.scim/global
```
I get a tab in my panel saying "starting administrative application", but nothing happens- it times out after a few seconds, just disappearing from the panel- nothing opens. What's going on? Any ideas?

I really want Japanese input!

---

### Post by ryukent on 2008-11-24
Sorry, that should read "gksudo gedit ~/.scim/global". It has been updated in the more recent post that covers 8.10. In fact, if you're using 8.10, please see this thread: [http://ubuntuforums.org/showthread.php?t=975144](http://ubuntuforums.org/showthread.php?t=975144)

---

### Post by BastardNamban on 2008-11-24
Thanks! I will try the proper command now, and continue.

I am using 8.04, though- I like the long term support :)

---

### Post by BastardNamban on 2008-11-24
Ahh, ran into another problem. To set my language support, I ran "locale"- I know I set it to no localization, the "C" option 
(hey, I'm a world traveler, and I don't like the idea of my system having any sort of country meta-data attached to it, say what you will)

Running "locale" gave me the result "LANG=C", but when I used that in global support box, pasting only "/SupportedUnicodeLocales = C", saving, and rebooting, I tried CTRL+space 
in anything I could type in- open office, text editor, etc.-I get nothing. I may have no localization, but I do know the default language for no localization is English! So what can I do?

Any ideas, or is this just not possible if you have no localization? (I find the idea that something isn't possible in linux absurd at this point, however, upon seeing what it CAN do)

---

### Post by ryukent on 2008-11-25
Is there any particular reason why you are using a C locale instead of a regional one? I agree almost anything is possible in linux, but SCIM is famously unforgiving. I'd recommend changing to whichever brand of English is your own for the locale before you try to get the C one working.

---

### Post by BastardNamban on 2008-11-26
About the regional thing, I don't know if it actually has any influence computationally to have my region as "C", but when I installed Ubuntu, I picked it because I didn't like the idea of having any part of my computer "tied" to a region. I don't know how to explain it logically, my thoughts were directed to the idea that, somehow, if someone somewhere were to scan my computer, or I show up on a network or something, I didn't want my regional choice/language to single me out from the rest of traffic.

Maybe there can be no such thing, and it's like someone driving a car saying they chose to drive a car made of concrete, so they'd blend everywhere they drove. Maybe I've had region problems with my DVD drives too many times from trying to watch too many region encoded DVDs, and the very idea of, in any way, enscribing a set region to my computer disgusts me.

That said, does being non-regional for language mean that I cannot set this up, and HAVE to change my regional language setting? If so, how do I? If not, I'd prefer to try this without changing my language settings. Can you help?

---

### Post by ryukent on 2008-11-27
I know how you feel, but setting a locale will basically tell Ubuntu what your default language is. Some application (SCIM included) will use this default to run different processes in order to display correctly for your user session. It won't announce your location on facebook or anything, it will just allow applications to target the language you are using.

You can select one when you log on by clicking on the "Options" button in the bottom left of the login screen and choosing "Select Language". You then chose the language for the session. English (United States) will often be most compatible as some (poorly written) software assumes it. I find English (United Kingdom) works fine for everything. It also means that words are spelt correctly like 'colour' instead of 'color' and stuff uses Ss instead of Zs. You will now have a LANG environment variable set which should make some fussy programs work.

In an ideal world this might not be necessary and indeed it is possible to code around it yourself. But I personally find it works fine with minimum fuss.

---

### Post by BastardNamban on 2008-11-28
Ok, changed lang to en, usa. Followed directions up to creating a dictionary manually for tomoe. Have some problems (this is becoming standard fare for me in ubuntu, and I'm sick of it).

First, after opening a text editor (chose Open Office), using the CTRL+Space move does nothing. Nothing called SCIM opens. Nothing happens. I did notice, on opening Open O., there is a small text at the bottom of the window saying "English (USA)". I thought that might be something, clicked on it, and a window called characters opens. It has English (USA) for western fonts, and a second menu underneath for an asian font selection. I set the asian one to Japanese, but I cannot type Japanese in any way. Perhaps I'm missing something. I tried changing around fonts, to the one listed for asian, to no avail. I figured screw it, just continue.

Installed tomoe, but I don't think it's letting me create a dict. manually, and I don't know why. Here's what I got: ```
(ME)@(COMP):~$ sudo apt-get install scim-tomoe
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libtomoe-gtk0 libtomoe0 tomoe-dic tomoe-gtk-common
Recommended packages:
  tomoe-gtk-l10n
The following NEW packages will be installed:
  libtomoe-gtk0 libtomoe0 scim-tomoe tomoe-dic tomoe-gtk-common
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 2971kB of archives.
After this operation, 24.8MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntulinux.jp hardy/ tomoe-dic 0.6.0-0ubuntu4 [1630kB]
Get:2 http://archive.ubuntulinux.jp hardy/ libtomoe0 0.6.0-0ubuntu4 [1230kB]
Get:3 http://archive.ubuntulinux.jp hardy/ tomoe-gtk-common 0.6.0-0ubuntu2 [13.7kB]
Get:4 http://archive.ubuntulinux.jp hardy/ libtomoe-gtk0 0.6.0-0ubuntu2 [49.5kB]
Get:5 http://archive.ubuntulinux.jp hardy/ scim-tomoe 0.6.0-0ubuntu2 [46.6kB]  
Fetched 2971kB in 10s (275kB/s)                                                
Selecting previously deselected package tomoe-dic.
(Reading database ... 128884 files and directories currently installed.)
Unpacking tomoe-dic (from .../tomoe-dic_0.6.0-0ubuntu4_all.deb) ...
Selecting previously deselected package libtomoe0.
Unpacking libtomoe0 (from .../libtomoe0_0.6.0-0ubuntu4_i386.deb) ...
Selecting previously deselected package tomoe-gtk-common.
Unpacking tomoe-gtk-common (from .../tomoe-gtk-common_0.6.0-0ubuntu2_all.deb) ...
Selecting previously deselected package libtomoe-gtk0.
Unpacking libtomoe-gtk0 (from .../libtomoe-gtk0_0.6.0-0ubuntu2_i386.deb) ...
Selecting previously deselected package scim-tomoe.
Unpacking scim-tomoe (from .../scim-tomoe_0.6.0-0ubuntu2_i386.deb) ...
Setting up tomoe-dic (0.6.0-0ubuntu4) ...
Setting up libtomoe0 (0.6.0-0ubuntu4) ...

Setting up tomoe-gtk-common (0.6.0-0ubuntu2) ...
Setting up libtomoe-gtk0 (0.6.0-0ubuntu2) ...

Setting up scim-tomoe (0.6.0-0ubuntu2) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
(ME)@(COMP):~$ cd /usr/share/tomoe/recognizer
(ME)@(COMP):/usr/share/tomoe/recognizer$ sudo cp handwriting-ja.xml handwriting-en.xml
(ME)@(COMP):/usr/share/tomoe/recognizer$ 
(ME)@(COMP):/usr/share/tomoe/recognizer$ cd /usr/share/tomoe/recognizer
(ME)@(COMP):/usr/share/tomoe/recognizer$ sudo cp handwriting-ja.xml handwriting-en_US.UTF-8.xml
(ME)@(COMP):/usr/share/tomoe/recognizer$ .
bash: .: filename argument required
.: usage: . filename [arguments]

``` Can you shed some light?

---

### Post by ryukent on 2008-11-28
Please give me the output of the following two commands,

export

im-switch -l

... then we should be able to help. Also, please confirm your exact version of Ubuntu and how you installed it. (e.g. 8.04 32bit, from the live CD, or 8.10, 64bit, from WUBI). I feel you're getting fed up at the moment and I do understand, but it sounds like you've got something unusual. On a fresh install of the current Ubuntu, it really is as easy as following the instructions. We should be able to sort you out though.

---

### Post by BastardNamban on 2008-11-29
Ok, thanks- I installed Ubuntu about 1 week ago, 8.04 HH 32 bit (I think 32 bit!) from the Live CD. Here is the output of the 2 commands. I'll just give them, and stop censoring my username/computer.
```
shogun@Valhalla:~$ export
declare -x COLORTERM="gnome-terminal"
declare -x DBUS_SESSION_BUS_ADDRESS="unix:abstract=/tmp/dbus-ObE62GYxQQ,guid=ed983b209ff8930fe0aa509c4930e9e1"
declare -x DESKTOP_SESSION="default"
declare -x DESKTOP_STARTUP_ID=""
declare -x DISPLAY=":0.0"
declare -x GDMSESSION="default"
declare -x GDM_LANG="C"
declare -x GDM_XSERVER_LOCATION="local"
declare -x GNOME_DESKTOP_SESSION_ID="Default"
declare -x GNOME_KEYRING_PID="5733"
declare -x GNOME_KEYRING_SOCKET="/tmp/keyring-S9Tlnf/socket"
declare -x GPG_AGENT_INFO="/tmp/seahorse-w4Vrdn/S.gpg-agent:5852:1"
declare -x GTK_RC_FILES="/etc/gtk/gtkrc:/home/shogun/.gtkrc-1.2-gnome2"
declare -x HISTCONTROL="ignoreboth"
declare -x HOME="/home/shogun"
declare -x LANG="C"
declare -x LESSCLOSE="/usr/bin/lesspipe %s %s"
declare -x LESSOPEN="| /usr/bin/lesspipe %s"
declare -x LOGNAME="shogun"
declare -x LS_COLORS="no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.svgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.rar=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:"
declare -x OLDPWD
declare -x PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
declare -x PWD="/home/shogun"
declare -x SESSION_MANAGER="local/Valhalla:/tmp/.ICE-unix/5734"
declare -x SHELL="/bin/bash"
declare -x SHLVL="1"
declare -x SSH_AUTH_SOCK="/tmp/keyring-S9Tlnf/ssh"
declare -x TERM="xterm"
declare -x USER="shogun"
declare -x USERNAME="shogun"
declare -x WINDOWID="54526035"
declare -x WINDOWPATH="7"
declare -x XAUTHORITY="/home/shogun/.Xauthority"
declare -x XDG_DATA_DIRS="/usr/local/share/:/usr/share/:/usr/share/gdm/"
declare -x XDG_SESSION_COOKIE="50894c0a6faee7fd6b5fa3d649256db2-1227942368.28598-754591976"
shogun@Valhalla:~$ im-switch -l
Your input method setup under C locale as below.
=======================================================
No private "/home/shogun/.xinput.d/C or /home/shogun/.xinput.d/all_ALL" is defined.
=======================================================
The system wide default is pointed by "/etc/alternatives/xinput-all_ALL" .
xinput-all_ALL - status is auto.
 link currently points to default
default - priority 10
default-xim - priority 0
none - priority 0
Current `best' version is default.
=======================================================
The available input method configuration files are:
/usr/bin/find: /home/shogun/.xinput.d: No such file or directory
default default-xim none scim scim-bridge scim-immodule th-xim 
=======================================================

```

---

### Post by ryukent on 2008-11-29
Ok, it looks like you're still logged in under a C locale. I'd recommend setting the locale to en_US.UTF-8 and making it default to avoid problems. It should give you that option when you log in under a new language.

When you've done that, run

im-switch -s scim-bridge

This will create a link under the currently active locale for the currently active user. The link tells Ubuntu to use SCIM as the input method. The reason why you are not currently able to use SCIM is it isn't switched on here. It should be automatically done when you add Japanese and select your version of English in the language support dialogue but I think there was a problem because you were using C. C is not considered as a language there and has confused it.

P.S.
You'll need to log out and then log back in again after you've run im-switch

---

### Post by BastardNamban on 2008-11-29
Ok, I THOUGHT I changed the language, but I tried again at the logon- this time, it gave me a prompt for all future sessions- it didn't before for some reason. It is set now, and I didn't run the im thing- just opened open office, and I got SCIM! Yea! I even figured out how to get it to enter a word in hiragana upto 5 kanji long, and it converted it perfectly- I'm shaking with JOY. This is awesome- finally, I can natively switch between English & Japanese ANYWHERE on my computer! I could never do this in windows, had to cut & paste from NWStar all the time, in crappy font. This ROCKS. Finally my friend can use my computer now too!  &#12371;&#12428;&#12399;&#12394;&#12363;&#12394;&#12363;&#20415;&#21033;&#12384;&#12424;&#65281;&#12288;&#12411;&#12435;&#12414;&#12395;&#12289;&#12354;&#12426;&#12364;&#12392;&#12358;&#65281;

Now I am only having problems where I was before```
cd /usr/share/tomoe/recognizer
sudo cp handwriting-ja.xml handwriting-en_US.UTF-8.xml
``` I put that in, all as one line, but nothing seems to happen. Are those 2 separate lines? I tried putting in each as a separate line as well, and nothing happens. Also, this is for handwriting recognition?! How does that come in to play with a computer & mouse? Am I missing something, and linux can somehow do &#25163;&#26360;&#12365;&#35469;&#35672;&#65311; If so, that would be sweet!

EDIT: HOLY ****! This thing CAN do handwriting recognition! I'm speachless- it actually works pretty well too! :biggrin:

---

### Post by ryukent on 2008-11-29
&#12424;&#12363;&#12387;&#12383;!!!&#12288;&#20170;&#12289;&#12418;&#12358;&#21839;&#38988;&#12364;&#12394;&#12367;&#12394;&#12387;&#12383;&#65311;

---

### Post by BastardNamban on 2008-11-29
&#12356;&#12420;&#12289;&#12414;&#12384;&#12385;&#12423;&#12387;&#12392;&#12354;&#12427;&#12290;&#12354;&#12398;&#19978;&#12398;&#12467;&#12540;&#12489;&#65380;&#12393;&#12358;&#12420;&#12387;&#12390;&#20837;&#21147;&#12377;&#12428;&#12400;&#33391;&#12356;&#12398;&#65311;&#19968;&#25991;&#12392;&#12375;&#12390;&#12289;&#25991;&#12378;&#12388;&#25991;&#12378;&#12388;&#12391;&#12418;&#12289;&#32080;&#26524;&#12398;&#20107;&#12289;&#20309;&#12418;&#36215;&#12371;&#12425;&#12394;&#12356;&#12435;&#12384;&#12290;

Also, going back to English, I noticed that right after typing "koto", my comma refuses to type as one from the bottom like the rest- is that a bug?
As I said, those 2 (?) lines of code above, I'm not sure how you enter them- I tried as one long line, and two separate lines, but nothing happens.

---

### Post by ryukent on 2008-11-29
These are commands to use in the terminal. You can go them one after another.

cd /usr/share/tomoe/recognizer

^ This changes to the correct directory.

sudo cp handwriting-ja.xml handwriting-en_US.UTF-8.xml

^ This makes a copy of the handwriting-ja.xml file and calls it handwriting-en_US.UTF-8.xml.

If your handwriting recognition is working, then it worked fine. There shouldn't be any output after you run them.

Not sure what you mean about the commas. There are a number of options within Anthy where you can adjust how it handles things.

---

### Post by BastardNamban on 2008-11-30
Ok, I got it- all of it. Finally. It all seems to work! This guide gives me things I've dreamed of being able to use on my computer for YEARS. Typing the same ugly text from NWStar in XP and pasting got REAL OLD, real quick. This is incredible, thank you!

I have one final question for you- about adding fonts. You said earlier: > Sazanami is another good font, though I have to admit, I prefer the MS and IPA ones.

On my system I have the following font packages installed:

ipamonafont
ttf-kochi-gothic
ttf-kochi-mincho
ttf-sazanami-gothic
ttf-sazanami-mincho
ttf-vlgothic If I went to synaptic and installed those, would that require editing that fonts file again you gave near the end? If so, how would I go about doing that? If not, I'll just install them.

Sorry for kinda hijacking your awesome thread > I love Ubuntu and will continue to support it fanatically, but I can really understand why some people can't deal with the 'issues'. Until even idiots can set up their system, people will shun linux as an enthusiasts only system. It is not acceptable for this community to look down on people who can't manage complicated setup. It is our responsibility to make it simple for them. I wanted to say, after seeing this comment, I was deeply impressed. It is people like you on here, in the world, that are the only thing that keeps linux going- if everyone was like you who knew anything, and was patient with beginning fools like me, we'd see linux spread a lot more. Thanks for all your help- my computer kicks bilingual *ss now just like me, thanks to you :)

---

### Post by ryukent on 2008-11-30
Thanks!!

If you install the font packages, it should set them all up automatically. The fonts config file basically tells the system what fonts to use when there isn't enough information. So it sets the default font for Japanese characters. For example, say you write something in Times but Times doesn't have the Asian characters, Ubuntu will consult the config file and go down the list selecting the next best font file until it find the character. Sometimes files have been saved (maybe from windows) using fonts that are not available. In this case, Ubuntu will use the config file. It has settings that try to match serif and non-serif fonts too. Plus it's the place you can store anti-aliasing settings and bitmap usage etc.

But, if you install a font and it is set up properly, it should just appear in the list of fonts available in whatever program you are using (Openoffice etc.) As long as you don't want it to be the default system font, you don't need to update the config file.

---

### Post by BastardNamban on 2008-12-03
Ryukent, sorry to post again, but I'm having some problems with SCIM. Perhaps you can help?

1. How do I get rid of Unicode as an input method? (I have Anthy, English/European, & RAW CODE Unicode). I will NEVER use unicode, I want it gone- but whenever I uncheck it in SCIM manager, it removes English/European too! (unclicking it removes the marker infront of other, which houses both of them).

2. I like the handwriting recognition feature a lot, but it seems very picky. Is there a way I can update it/ train it/ make it understand my writing better? I swear, I tried to input &#25351;&#12288;from &#25351;&#23566; over 30 times, and it refused to recognize! Also, is there a way I can hotkey it so that handwriting recognition comes up without having to use the menu? I need to use it a lot (my reading/writing isn't native yet, but reasonably high)

3. If I can't train it, I know things like the DS supposedly have real time stroke correction handwriting recognition, I've seen it, and it's amazing. Are there any programs I could get/buy for linux to better augment this? I'd love something that didn't need a perfect balance in my strokes between the typical 4 square box- a lot of times, you have to actually know the prescribed balance, or it won't enter! (see #2) Surely there has to be SOMETHING else out there that works better, as a standalone/plugin? If not...(#4)

4. #2 got me thinking (especially my annoying as hell corded MS optical mouse in a 2"x2" space, and is trying to write like I'm holding a wobbly BRICK), is there anything I could link up to the handwriting recognition app to better input characters, like a pen tablet? I'll head to the Yodobashi Camera downtown sometime soon, as I want to see if they have computers with small tablet input built in to the laptop somewhere. I could REALLY REALLY use that. There HAS to be a better way to do handwriting recognition on a computer! Maybe hack a gyroscopic wiimote? How would a gyroscopic mouse work, do you think? 

Ideally, I'd like to just have some kind of ring I could slip on, and IR tracking posts or a webcam could track my finger in real time, and I write in the air in front of my screen, and it counts it as a stroke.

Maybe they make touchscreen kits for widescreen laptops (I know netbook kits exist), and I could use a stylus on a screen protector and just write on my screen?

I'm desperate for a better way for writing input on my computer. I bet someone like you knows what I mean- any ideas, as you may have found something? I only have a small table about as big as my laptop and a couple inches, using a mouse to write kanji is a pain in the ***.

---

### Post by ryukent on 2008-12-03
Nanban (not sure I should address you as *******)

I disabled the Raw Code option by disabling other. Now I just have English/Keyboard and Anthy. I use CTRL+Space to switch between the two. Even when I had Rawcode on though as I only used CTRL+Space to toggle anthy on and off, they never got in my way.

About the handwriting..... basically in runs on a system that calculates the start position of each stroke relative to each other stroke and combines this with the stroke direction and stroke order. It can assign a mathematical value to that and looks in its database for a Kanji who's value it most closely resembles. For this reason it's really important to get the stroke order and direction correct. Some are not as you might seem. Good Kanji dictionaries should help you there. I tested &#25351; and it seemed to find it ok.

You can't train it. It is based on a set pattern and there's nothing you can do about that. There is another program called Kanji pad, but I suspect it is based on exactly the same algorithm. As far as I know there isn't anything better. I would like to point out that all the native Japanese people I know never ever use these kind of inputs. They consider it far too slow and pointless if you know the reading anyway. It is only really for a situation when you don't know the kanji the first time round. Once you've entered it and looked it up, you can just type it in Kana and convert much quicker.

As far as setting a keyboard shortcut to run it quickly, try this:

Alt+F2 (Run)
gconf-editor

This is like a registry editor for gnome.
Goto metacity/keybinding_commands

Open command_1 and add "scim-tomoe"

Then goto 
metacity/global_keybindings and set run_command_1 to <Alt>F12

Now hitting Alt+F12 should run the handwriting recognition applet.

As for alternatives to the mouse. I heard the Wacom pads are good. Never tried them in Ubuntu but I know they do make a number of different sizes and you can use a pen which hovers over the pad and is sensed. Might get one of those myself soon. Let me know how you get on.

---

### Post by BastardNamban on 2008-12-04
Ok, I did as you said for both- I disabled other, but then it didn't work. I can't get rid of Unicode- it wont let me. It said "Not all configuration can be reloaded on the fly. Don't forget to restart SCIM in order to let all of the new configuration take effect." I don't know how to reload it, as it doesn't show up as running in system monitor. I restarted the computer, nothing changes.

I did everything you said to launch tomoe, added those values to the specific keys, and that didn't work either. I think my whole SCIM client refuses to cooperated in all this.

I gotta get to sleep, I'll check tommorow. This 12 hour time difference thing is really making it hard to find help, and annoying.

As for the name, I still can't believe I got away with that.:)

---

### Post by ryukent on 2008-12-05
Check that your ~/.scim/ files have the right permissions. You might wanna run file browser as root and check the ownership is set to your username. Actually, that might be my fault as I've put some gksudo's in the how to where they aren't needed. As for the hot key, those key entries can be found in "apps". Are you sure they are entered correctly? Mine work fine.

---

### Post by BastardNamban on 2008-12-06
The hotkeys problem is solved, I found everything the first time fine, and changed the part called "value" on both properly ("value" is all they let you edit in the program one). But after editing, I press the keys (alt+F9, yes, parsed properly in gconf as <Alt>F9), and it didn't work.

I just realized this time around- I purposely disabled all commands/key commands under general in compiz- that was blocking out the metacity stuff. (At the time I disabled it all in compiz, if I didn't know what it was, I disabled it, thinking it might interfere with any hotkeys I assigned) I remembered this, went into compiz, and entered the needed stuff there instead- Tomoe boots up fine now! Nice.

Still wondering about editing the SCIM file- How do I check permissions for the scim files? I opened the browser as root with gksudo nautilus, but searching for .scim, scim, ~/.scim/, *global, and anything I could think of for any scim "files", and I found nothing even called scim, or any folder related. I opened the original global languages part, and saw nothing about whose it is saved as/permissions. I can't even find that file on my computer when I search for it.

---

### Post by ryukent on 2008-12-07
Ahhh.... files that begin with "." are hidden files. Ctrl+H should display them in nautilus. Then right hand click, properties / permissions and you should be able to set / view etc.

---

### Post by BastardNamban on 2008-12-14
Ok, that was a great tip- didn't know I could show hidden files like that.
I didn't find anything in the folder, however- it was empty. I right clicked the empty space in the folder, and set permissions to my username.
I tried again then to remove unicode from SCIM, but it gives me the same crap.

I really, really want to get rid of unicode, and leave English/Japanese ONLY. I'm now comfortable with your whole setup proceedure, so maybe it would be easiest to just uninstall everything and start over? Maybe without adding UK english support? I'm wondering if that had something to do with this. Any ideas Ryu?

BTW, I'm probably the only person on here that would notice your avatar's meaning- nice use of old period style. Classy.

---

### Post by ricoris on 2008-12-14
Hi!
It seems that I installed SCIM correctly but typing ctrl+space doesn't work to trigger it, at least not in my locale. I already did what you explained in this tutorial but it still doesn't respond. In Japanese locale it does respond.

---

### Post by ryukent on 2008-12-14
Namban,

In my ~/.scim/global file I have the following:

/DisabledIMEngineFactories = c6bebc27-6324-4b77-8ad4-6d41dcaf2e08,6e029d75-ef65-42a8-848e-332e63d70f9c
/SupportedUnicodeLocales = en_US.UTF-8,en_GB.UTF-8

The /DisabledIMEngineFactories bit is what disables the Unicode stuff. When it's switched back on, the codes don't apprear after. I did note that none of the affects of changing happened until I had restarted my system. Also I disabled all 'Other', including English/European which now gives me 2 options "Japanese - Anthy" and "English/Keybaord". It might be annoying (OK, no might.... it is annoying) but try editing the global file and see how adding ticks in SCIM setup affects it. Then also try rebooting as it tend to take that for the new effects to take hold.

Ricoris,
Please post the output of "im-switch -l" while logged into the locale you want to use SCIM in.

---

### Post by BastardNamban on 2008-12-16
Ok, I'm sorry I've taken so long to respond- I've been getting so f*^King fed up with this OS's little glitches I haven't been able to stand fooling with it for a week.

I tried your fix, and added that line to the scim global file. It screwed things up royally- it did indeed get rid of the unicode, but also english! Hitting my old hotkey that cycled between languages, CTRL+ALT+Up, it would only flash "Anthy" (Japanese) at me. Furious, I removed your entry from the global scim file, and put it back the way it was, but now, it still doesn't work right! It still refuses to switch between anything, and I have to click the keyboard icon in my tray to get it to go to english. Hot keys/switching don't work at all- it keeps flashing "Anthy" at me.

In case you're wondering exactly what is in my scim global file now, here it is: ```
/SupportedUnicodeLocales = en_US.UTF-8

```That's it.

EDIT:

Ok, it's working normally again, and in open office as well. I have since made my global scim file BLANK- ie, deleted that above line, hoping that might change things and remove unicode. It didn't. But everything still works fine, weird.

I've decided I don't know how to get rid of the unicode, since unclicking it never has an effect, even after reloading scim. I'm contacting the program's author, in hopes that maybe he can help. Thanks for all your help Ryukent!

PS: Remember how I asked about tablets before? You should check this out- [http://www.iogear.com/product/GPEN200N/](http://www.iogear.com/product/GPEN200N/)
That thing is amazing, and has OCR support for both English, AND Japanese! (as well as a few others), can be used on any flat surface/paper, wireless, works as a mouse, everything. It says windows only though.... I wonder if there's any chance this would work in linux for us? What do you think?

---

### Post by Emerald23 on 2009-01-10
I hope it is not too late to post something.  This is my first posting in one of these types of forums. 

I followed your instructions to enable Japanese font, but I'm still not able to type in Japanese.  I can read it on websites; I always could. I just can't type in Japanese.  Whenever I bring up OpenOffice Writer and press Ctrl + Space or Shift + Space  and I get nothing. I tried Text Editor and right clicked in it then selected to use SCIM yet nothing happened.

I can see a small keyboard in the upper left corner of the screen right next to the clock. I click on it and nothing happens. I even tried instructions from this site: [http://www.h4.dion.ne.jp/~apricots/scim-anthy/howto.html#pr3](http://www.h4.dion.ne.jp/~apricots/scim-anthy/howto.html#pr3) 

It recommended...

> Adding the following four lines to ~/.i18n or /etc/sysconfig/i18n will make SCIM start with X and enable you to activate the input method in various applications simply by pressing Ctrl+Space, whether it uses GTK-immodule, Qt-immodule or the XIM (X input method) protocol-GTK_IM_MODULE=scim QT_IM_MODULE=scim XIM_PROGRAM="scim -d" XMODIFIERS=@im=SCIM

And this one for enabling SCIM to use Japanese font: [http://zuttobenkyou.wordpress.com/2008/06/23/linux-mint-elyssa-how-to-enable-korean-japanese-french-and-german/](http://zuttobenkyou.wordpress.com/2008/06/23/linux-mint-elyssa-how-to-enable-korean-japanese-french-and-german/)

> 
* Open up /etc/X11/xinit/xinput.d/scim with root access with any text editor. E.g., something like this: gksudo gedit /etc/X11/xinit/xinput.d/scim.

* Make the file look like this (the lines that start with # are all “comments” and do not affect anything at all):

XIM=SCIM
XIM_PROGRAM=/usr/bin/scim
XIM_ARGS="-d"
XIM_PROGRAM_SETS_ITSELF_AS_DAEMON=yes
GTK_IM_MODULE="scim-bridge"
QT_IM_MODULE="scim-bridge"
DEPENDS="scim,scim-anthy|scim-canna|scim-chewing|scim-pinyin|scim-hangle|scim-prime|scim-skk|scim-tables-additional|scim-m17n|scim-uim|scim-tables-ja|scim-tables-ko|scim-tables-zh"

And I installed all the items recommended at [http://stefanomatic.wordpress.com/2008/07/29/ultra-fast-japanese-scim-for-ubuntu-804/](http://stefanomatic.wordpress.com/2008/07/29/ultra-fast-japanese-scim-for-ubuntu-804/) just in case I had missed something.

> sudo apt-get install scim-anthy im-switch scim-bridge-agent scim-bridge-client-gtk scim-bridge-client-qt scim-bridge-client-qt4 language-support-ja

Nothing. I've read in your forum you ask people to do im-switch -l

Mine says the following--

```
Your input method setup under en_US locale as below.
=======================================================
The configuration "/home/olivia/.xinput.d/en_US" is defined as a link pointing to
scim-bridge
This private configuration supersedes the system wide default.
=======================================================
The system wide default is pointed by "/etc/alternatives/xinput-all_ALL" .
xinput-all_ALL - status is manual.
 link currently points to scim-bridge
default - priority 10
default-xim - priority 0
none - priority 0
scim-bridge - priority 10
Current `best' version is default.
=======================================================
The available input method configuration files are:
default default-xim nabi none scim scim~ scim-bridge scim-chewing scim-hangul scim-hangul_xim scim-immodule scim-pinyin th-gtk-im-libthai th-xim 
=======================================================
```

I recently bought a Dell XPS M1330 that came preinstalled with Ubuntu 8.04 Hardy Heron. Everything else works fine except this one thing, and I'm not sure what else to do without crashing the system because I still new to Ubuntu Linux. Any help?

---

### Post by jewishj on 2009-01-15
For me after following the guide, my fonts didn't really appear to be smooth and anti-aliased anymore.  Making sure all of the following were installed (from a step in ryukents feisty guide) made everything look better for me in hardy.

```

sudo apt-get install msttcorefonts ttf-dejavu ipafont ipamonafont ttf-arphic-ukai ttf-arphic-uming

```

Note: ipafont was not in the repos for me

Hope that it can help someone else too

---

### Post by ryukent on 2009-01-17
Emerald, seems you have SCIM installed. Can you right click on the keyboard, select SCIM setup and check to see if you have Anthy in the IMEEngines section?

---

### Post by Emerald23 on 2009-01-19
Yes it is there. When I went in to enable complex characters and select Japanese in the list of languages it was already selected along with a whole list of other languages. I've tried unselecting it, restarting my computer and re-selecting it. It didn't work.

---

### Post by futuroimperfetto on 2009-01-26
Hello,

 My partner has a Japanese laptop (hence with a Japanese keyboard). I installed 8.04 via Wubi with Japanese installed as its main language.

It came with SCIM preinstalled, but if we left-click on the icon, it only gives us "Other English/European, Other Raw Code, English/Keyboard". We couldn't get any Japanese character working in any program (say Firefox, OpenOffice or gedit).

I am a n00b and don't know how to use SCIM. I followed the tutorial found at this link

[https://help.ubuntu.com/community/Japanese_Input_and_Fonts_in_Ubuntu_8.04_using_SCIM]("https://help.ubuntu.com/community/Japanese_Input_and_Fonts_in_Ubuntu_8.04_using_SCIM")

I had some choices to make which I might have gotten wrong. For example, if I type "locale" in a terminal and this is what we get

```
LANG=ja_JP.UTF-8
LC_CTYPE="ja_JP.UTF-8"
LC_NUMERIC="ja_JP.UTF-8"
LC_TIME="ja_JP.UTF-8"
LC_COLLATE="ja_JP.UTF-8"
LC_MONETARY="ja_JP.UTF-8"
LC_MESSAGES="ja_JP.UTF-8"
LC_PAPER="ja_JP.UTF-8"
LC_NAME="ja_JP.UTF-8"
LC_ADDRESS="ja_JP.UTF-8"
LC_TELEPHONE="ja_JP.UTF-8"
LC_MEASUREMENT="ja_JP.UTF-8"
LC_IDENTIFICATION="ja_JP.UTF-8"
LC_ALL=
```

I added the following line in "~/.scim/global"
```

/SupportedUnicodeLocales = en_US.UTF-8,en_GB.UTF-8,ja_JP-UTF-8
```

and then went on until the end. Perhaps I screwed up something, but we can't get any application to type in Japanese. She also has WinXP and in there she could get it working using a special key and she can choose which language to type in (she tells me its name sounds like "hankaku-zenkaku-kanji"). When we do CTRL+SPACE we can't get SCIM to offer us Japanese.

I apologize if this looks like a mess, but she is positively interested in using Ubuntu (being fed up with Win XP) but I do not know how to make Japanese fonts show up in any application.

Thanks for your patience

Cheers

---

### Post by TWO on 2009-03-12
I've personally had a much better experience using UIM for Japanese input rather than SKIM with Kubuntu.

[https://help.ubuntu.com/community/Japanese_Input_and_Fonts_in_Ubuntu_7.10](https://help.ubuntu.com/community/Japanese_Input_and_Fonts_in_Ubuntu_7.10)

SKIM has caused input issues for me, such as being unable to enter any text into a window unless I clicked odd and back onto it. 

Aside from that, the process of installing UIM seems far less painful,and it works in both QT and GTK programs from the off without any issues...

(Only issue I'm having right now is getting UIM to use good Japanese fonts. If I edit the font.conf file, it ends up changing my entire system's font. Problem is, if I leave it as it is, I come across missing Kanji during text input.. I'm looking into it.)

Edit: No longer an issue. Just copied the earlier example of the *fonts.conf *file and everything now works fine.

---

### Post by aiko.uda on 2009-04-15
Hi

I had been using Japanese font for 6 months or so, wondering about this ugly font. Thank you so so much!

---

### Post by mathrawka on 2009-05-09
Following these instructions worked well to get pretty fonts for Japanese, but they appear to only work in GTK applications. How can I get the same font order defined for Qt applications? (Firefox is pretty, but Opera is not...)

---

### Post by hobo14 on 2009-05-10
Hey Emerald, I had the same problem typing Chinese in Skype.  Saw lots of solutions, including the ones you've posted, but in the end all you need to do is install these (actually I'm not 100% sure you need all three, it may only be one or two, but I didn't check):

scim-bridge-client-qt
scim-bridge-client-qt4
scim-qtimm

Then logout, login, problem solved.

EDIT: ahaha, didn't read your post very closely, did I? You've already got 2 of the 3.  Well, try scim-qtimm too.

---

### Post by Champy on 2009-05-10
i'm trying to get this to work.

i added deb 'http://archive.ubuntulinux.jp/ubuntu-ja jaunty/' to my repositories.

but when I'm in the Synapic Package Manager and i search for 'ubuntu-ja-keyring' i don't get any results. is there a different repository i should add since i'm on 64 bit jaunty jackalope?

I'm new to Ubuntu so I'm having a bit of trouble.

---

### Post by Zorael on 2009-05-11
That repo doesn't seem to have a whole lot of Jaunty packages (yet). You could try adding its intrepid repository, though. (Just replace hardy with intrepid, like you replaced it with jaunty.)

See directory listing at [http://archive.ubuntulinux.jp/ubuntu-ja](http://archive.ubuntulinux.jp/ubuntu-ja).

---

### Post by Thelinguist on 2009-08-24
I know this is kind of late, but I really need some help.  I have just recently switched to ubuntu 9.04 and wanted to set up Japanese input. I was able to do this through Language Support, but as you know the kanji sometimes renders fuzzy. I tried to use the tutorial in this for installing the different fonts, but I'm not terminal savy yet. when I restarted my computer all and I mean all of the text were just blocks. I had to reinstall ubuntu just to fix it and lost all my data, can someone please help me?

---

### Post by Zorael on 2009-08-26
I imagine your .fonts.conf file was too aggressive.

To explain, blocks appear when a character (be it a, B, 1, # or &#23383;) cannot be displayed. By extension, that means that the font in use doesn't contain it. If an invalid font was specified, obviously no characters would be available, and you'd get all squares. No font contains all characters - there's simply too many of them when you take into account there are more alphabets than the Roman one alone. See [this wikipedia entry](http://en.wikipedia.org/wiki/Fallback_font).

To get around this you use the .fonts.conf file to define a list of fonts to comprise the virtual fonts "Serif", "Sans-serif" and "Monospace". When you then try to display a character using "Serif", it will first try to display it using the first font in that list. If it's not present in that font, it'll try the next one, instead of replacing it with a square (as it would normally).

Ryukent supplied an example of such a list in the original post of this thread, with a whole slew of fonts. I like to keep mine smaller. Perhaps yours was malconfigured?
```
<?xml version='1.0'?>
<!DOCTYPE fontconfig SYSTEM 'fonts.dtd'>
<fontconfig>
 <alias>
  <family>serif</family>
  <prefer>
   <family>DejaVu Serif</family>
   <family>Kochi Mincho</family>
   <family>Sazanami Mincho</family>
  </prefer>
 </alias>
 <alias>
  <family>sans-serif</family>
  <prefer>
   <family>DejaVu Sans</family>
   <family>Kochi Gothic</family>
   <family>Sazanami Gothic</family>
  </prefer>
 </alias>
 <alias>
  <family>monospace</family>
  <prefer>
   <family>DejaVu Sans Mono</family>
   <family>Kochi Gothic</family>
   <family>Sazanami Gothic</family>
  </prefer>
 </alias>

 <match target="font" >
  <edit mode="assign" name="embeddedbitmap" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialiasing" >
   <bool>true</bool>
  </edit>
 </match>

<!-- CUT from here to disable subpixel rendering -->
<!-- 8< 8< 8< 8< 8< 8< 8< 8< 8< 8< 8< 8< -->
 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>rgb</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="autohint" >
   <bool>false</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintfull</const>
  </edit>
 </match>
<!-- 8< 8< 8< 8< 8< 8< 8< 8< 8< 8< 8< 8< -->
<!-- those are scissors btw -->

</fontconfig>
```
That .fonts.conf example should set a basic font order up, where the virtual Serif/Sans-serif/Monospace fonts are the DejaVu fonts normally, unless a character cannot be displayed, in which case it tries the (more unicode-complete) Kochi fonts first, and the Sazanami fonts second. The Kochi fonts are supposedly identical to the Ricoh fonts Ryukent suggests you download and use.

This requires you to have the **ttf-kochi-gothic-naga10**, **ttf-kochi-mincho-naga10**, **ttf-sazanami-gothic** and **ttf-sazanami-mincho** packages installed. The first two are non-free software and require you to enable the multiverse repositories. Add them via your package manager of choice, if you don't want to use the terminal.
```
$ sudo aptitude install ttf-kochi-gothic-naga10 ttf-kochi-mincho-naga10 ttf-sazanami-gothic ttf-sazanami-mincho
```

You *will* probably need to set up your desktop environment to use the Serif/Sans-serif/Monospace virtual fonts *instead* of using DejaVu directly. Else this priority list gets circumvented. Set your font settings to point appropriately.

Changes should apply to newly open applications, so just open up a new Gedit or a new Firefox or whatnot.

---

### Post by Thelinguist on 2009-08-26
[SIZE=3]Thanks for your help Zorael. I actually figured out how to fix the problem on my own. I visited the ubuntu page for learning how to install fonts before, I retried Ryukent's fix. I'm feel so proud of myself, I'm loving the ubuntu learning experience. [/SIZE]

---

### Post by l33tminion on 2009-10-01
I was finally able to solve this problem.  At first, my environment variables were not getting set properly:
export | grep QT
> declare -x QT_IM_MODULE="scim-bridge"

I had the config file problem mentioned above (where the scim-bridge config file looks for the QT library in qt3 instead of qt4), which I fixed.  But that didn't solve the problem fully.

What did was:
cd /etc
grep -R QT_IM_MODULE *

At which point I found it was getting set to "scim" in /etc/X11/Xsession.d/74custom-scim.   That file was one I created as part of a work-around for some other problem, following the instructions in another tutorial, and I'd totally forgotten about it.  After deleting the file, things worked fine.

---

### Post by mtheripper on 2009-11-05
Hello,

I am new to ubuntu 9.10.
I tried pretty much all solutions in here as well as in other threads, but I am not able to write Japanese.

I installed SCIM and under System/Administration/Language Support i am able to select under the point "KEYBOARD INPUT METHOD SYSTEM" - Scim, Scim-bridge and Scim-immodule.

I followed all the steps from the original posts,but I have no idea how to write japanese now. I hope somebody can help me. Because I really like Ubuntu, bunt for work reasons, I am currently changing back to Windows, because I need Japanese writing.

Anyway.
If somebody could help me, I would me more than happy!
(I also have skype, if that helps)

Thanks & Reagrds,
Stefan

---

### Post by Zorael on 2009-11-06
> **mtheripper said:**
> Hello,

I am new to ubuntu 9.10.
I tried pretty much all solutions in here as well as in other threads, but I am not able to write Japanese.

I installed SCIM and under System/Administration/Language Support i am able to select under the point "KEYBOARD INPUT METHOD SYSTEM" - Scim, Scim-bridge and Scim-immodule.

I followed all the steps from the original posts,but I have no idea how to write japanese now. I hope somebody can help me. Because I really like Ubuntu, bunt for work reasons, I am currently changing back to Windows, because I need Japanese writing.

Anyway.
If somebody could help me, I would me more than happy!
(I also have skype, if that helps)

Thanks & Reagrds,
Stefan
I have a bunch of terminal commands that can determine whether it is set up right (or what yet needs to be done), but no real graphical approach. GNOME tries to do this its own way, and I'm not completely sure about what it's doing.

What's the terminal output from these four commands? Copy/paste them to get their spelling right, and paste output inbetween code-tags.
```
im-switch -l

ls -l /etc/alternatives/xinput*

ls -l ~/.xinput.d

cat /etc/X11/xinit/xinput.d/scim
```
That should be enough to know what's missing.

---

### Post by mtheripper on 2009-11-06
Hi,

Thank you for the post!

Here are the results:

```
maga@maga-laptop:~$ im-switch -l
Your input method setup under en_US locale as below.
=======================================================
The configuration "/home/maga/.xinput.d/en_US" is defined as a link pointing to
scim-bridge
This private configuration supersedes the system wide default.
=======================================================
The system wide default is pointed by "/etc/alternatives/xinput-all_ALL" .
xinput-all_ALL - auto mode
 link currently points to default
default - priority 10
default-xim - priority 0
none - priority 0
Current `best' version is default.
=======================================================
The available input method configuration files are:
default default-xim ibus none scim scim-bridge scim-immodule th-xim 
=======================================================
```
```
maga@maga-laptop:~$ ls -l /etc/alternatives/xinput*
lrwxrwxrwx 1 root root 31 2009-10-30 05:37 /etc/alternatives/xinput-all_ALL -> /etc/X11/xinit/xinput.d/default
lrwxrwxrwx 1 root root 28 2009-10-30 05:37 /etc/alternatives/xinput-ja_JP -> /etc/X11/xinit/xinput.d/ibus
lrwxrwxrwx 1 root root 28 2009-10-30 05:37 /etc/alternatives/xinput-ko_KR -> /etc/X11/xinit/xinput.d/ibus
lrwxrwxrwx 1 root root 30 2009-10-30 05:37 /etc/alternatives/xinput-th_TH -> /etc/X11/xinit/xinput.d/th-xim
lrwxrwxrwx 1 root root 28 2009-10-30 05:37 /etc/alternatives/xinput-zh_CN -> /etc/X11/xinit/xinput.d/ibus
lrwxrwxrwx 1 root root 28 2009-10-30 05:37 /etc/alternatives/xinput-zh_HK -> /etc/X11/xinit/xinput.d/ibus
lrwxrwxrwx 1 root root 28 2009-10-30 05:37 /etc/alternatives/xinput-zh_SG -> /etc/X11/xinit/xinput.d/ibus
lrwxrwxrwx 1 root root 28 2009-10-30 05:37 /etc/alternatives/xinput-zh_TW -> /etc/X11/xinit/xinput.d/ibus

```
```
maga@maga-laptop:~$ ls -l ~/.xinput.d
total 0
lrwxrwxrwx 1 maga maga 35 2009-11-05 14:05 en_US -> /etc/X11/xinit/xinput.d/scim-bridge
lrwxrwxrwx 1 maga maga 28 2009-11-05 13:53 en_US.backup -> /etc/X11/xinit/xinput.d/scim
``````
maga@maga-laptop:~$ cat /etc/X11/xinit/xinput.d/scim
#
# Use "X input Method" for all applications
#
# Per Ming's Documentation in SCIM, XIM Input Method is activated
# not only for old X-applications but also for GTK and QT appplication.
#
# If a user wish to use, GTK Input Method, (s)he can right-click input 
# area and select "Input Methods" and change from "X input Method" to 
# "SCIM Input Method".
#

XIM=SCIM
XIM_PROGRAM=/usr/bin/scim
XIM_ARGS="-d"
XIM_PROGRAM_SETS_ITSELF_AS_DAEMON=yes
GTK_IM_MODULE=xim
QT_IM_MODULE=xim
DEPENDS="scim,scim-anthy|scim-canna|scim-chewing|scim-pinyin|scim-hangul|scim-prime|scim-skk|scim-tables-additional|scim-m17n|scim-uim|scim-tables-ja|scim-tables-ko|scim-tables-zh"

```These are the 4 commands you gave me.

Thanks already for your help.
I really appreciate it!

Thanks,
Stefan

---

### Post by tokage on 2009-11-07
Hi, I'm having the same problem -- I upgraded to Ubuntu 9.10 last night and now Japanese doesn't show up as one of the input options in SCIM.  The output from the commands you suggested are pretty similar to those posted by mtheripper.  I only have en_CA and en_US in my .xinput.d directory -- do I need to add a link to JA as well?

Thanks.
toki

---

### Post by mtheripper on 2009-11-08
I could fix the problem (finally) by following this tutorial STEP by STEP from the beginning.

[http://www.h4.dion.ne.jp/~apricots/scim-anthy/howto.html](http://www.h4.dion.ne.jp/~apricots/scim-anthy/howto.html)

Thanks for the help though... 

&#12418;&#12358;&#19968;&#22238;&#12354;&#12426;&#12364;&#12392;&#12358;&#65281;

---

### Post by Zorael on 2009-11-09
> **tokage said:**
> Hi, I'm having the same problem -- I upgraded to Ubuntu 9.10 last night and now Japanese doesn't show up as one of the input options in SCIM.  The output from the commands you suggested are pretty similar to those posted by mtheripper.  I only have en_CA and en_US in my .xinput.d directory -- do I need to add a link to JA as well?

Thanks.
toki
You only need links there for the locale you're using. I use a Swedish locale (yet English language) and it uses all_ALL. '**im-switch -l**' will tell you which one is being used; then you can use '**im-switch -z *en_US* -c**' to change a specific locale's setting. Replace **en_US** with **en_CA** or whatever. Or just manually point the link.

Once set up you need to make sure that the file it's pointing to (generally **scim** or **scim-bridge** in /etc/X11/xinit/xinput.d/) contains *CORRECT* entries for variables **GTK_IM_MODULE** and **QT_IM_MODULE**. The scim file mtheripper posted, for instance, is borked. The ***IM_MODULE** variables should say _scim_ or _scim-bridge_. Like so;
```
#
# Use "X input Method" for all applications
#
# Per Ming's Documentation in SCIM, XIM Input Method is activated
# not only for old X-applications but also for GTK and QT appplication.
#
# If a user wish to use, GTK Input Method, (s)he can right-click input 
# area and select "Input Methods" and change from "X input Method" to 
# "SCIM Input Method".
#

XIM=SCIM
XIM_PROGRAM=/usr/bin/scim
XIM_ARGS="-d"
XIM_PROGRAM_SETS_ITSELF_AS_DAEMON=yes
GTK_IM_MODULE=**scim**
QT_IM_MODULE=**scim**
DEPENDS="scim,scim-anthy|scim-canna|scim-chewing|scim-pinyin|scim-hangul|scim-prime|scim-skk|scim-tables-additional|scim-m17n|scim-uim|scim-tables-ja|scim-tables-ko|scim-tables-zh"
```
That will make SCIM the default in (all) apps. I'm unsure what the difference between scim and scim-bridge is; I generally use scim-bridge, in which case the *IM_MODULE variables should say **scim-bridge** instead of scim.

> **mtheripper said:**
> I could fix the problem (finally) by following this tutorial STEP by STEP from the beginning.

[http://www.h4.dion.ne.jp/~apricots/scim-anthy/howto.html](http://www.h4.dion.ne.jp/~apricots/scim-anthy/howto.html)

Thanks for the help though... 

&#12418;&#12358;&#19968;&#22238;&#12354;&#12426;&#12364;&#12392;&#12358;&#65281;
Cheers.

---

### Post by tokage on 2009-11-22
Hi Zorael,

I was able to get Japanese input working by switching to ibus, but I could never figure out how to get SCIM working.  Just in case, here's the results of the commads you brought up to try:

```
toki@toki-desktop:~/.scim$ im-switch -l
Your input method setup under en_US locale as below.
=======================================================
The configuration "/home/toki/.xinput.d/en_US" is defined as a link pointing to
scim
This private configuration supersedes the system wide default.
=======================================================
The system wide default is pointed by "/etc/alternatives/xinput-all_ALL" .
xinput-all_ALL - auto mode
 link currently points to default
default - priority 10
default-xim - priority 0
none - priority 0
Current `best' version is default.
=======================================================
The available input method configuration files are:
default default-xim ibus none scim scim-bridge scim-immodule th-xim 
=======================================================
``````
toki@toki-desktop:~/.scim$ ls -l /etc/alternatives/xinput*
lrwxrwxrwx 1 root root 31 2009-05-02 03:14 /etc/alternatives/xinput-all_ALL -> /etc/X11/xinit/xinput.d/default
lrwxrwxrwx 1 root root 28 2009-11-06 09:35 /etc/alternatives/xinput-ja_JP -> /etc/X11/xinit/xinput.d/ibus
lrwxrwxrwx 1 root root 28 2009-11-06 09:35 /etc/alternatives/xinput-ko_KR -> /etc/X11/xinit/xinput.d/ibus
lrwxrwxrwx 1 root root 30 2009-05-02 03:14 /etc/alternatives/xinput-th_TH -> /etc/X11/xinit/xinput.d/th-xim
lrwxrwxrwx 1 root root 28 2009-11-06 09:35 /etc/alternatives/xinput-zh_CN -> /etc/X11/xinit/xinput.d/ibus
lrwxrwxrwx 1 root root 28 2009-11-06 09:35 /etc/alternatives/xinput-zh_HK -> /etc/X11/xinit/xinput.d/ibus
lrwxrwxrwx 1 root root 28 2009-11-06 09:35 /etc/alternatives/xinput-zh_SG -> /etc/X11/xinit/xinput.d/ibus
lrwxrwxrwx 1 root root 28 2009-11-06 09:35 /etc/alternatives/xinput-zh_TW -> /etc/X11/xinit/xinput.d/ibus
``````
toki@toki-desktop:~/.scim$ ls -l ~/.xinput.d
total 0
lrwxrwxrwx 1 toki toki 35 2009-05-03 11:43 en_CA -> /etc/X11/xinit/xinput.d/scim-bridge
lrwxrwxrwx 1 toki toki 28 2009-11-22 01:16 en_US -> /etc/X11/xinit/xinput.d/scim
lrwxrwxrwx 1 toki toki 35 2009-11-22 00:58 en_US.backup -> /etc/X11/xinit/xinput.d/scim-bridge
``````
toki@toki-desktop:~/.scim$ cat /etc/X11/xinit/xinput.d/scim
#
# Use "X input Method" for all applications
#
# Per Ming's Documentation in SCIM, XIM Input Method is activated
# not only for old X-applications but also for GTK and QT appplication.
#
# If a user wish to use, GTK Input Method, (s)he can right-click input 
# area and select "Input Methods" and change from "X input Method" to 
# "SCIM Input Method".
#

XIM=SCIM
XIM_PROGRAM=/usr/bin/scim
XIM_ARGS="-d"
XIM_PROGRAM_SETS_ITSELF_AS_DAEMON=yes
GTK_IM_MODULE=scim-bridge
QT_IM_MODULE=scim-bridge
DEPENDS="scim,scim-anthy|scim-canna|scim-chewing|scim-pinyin|scim-hangul|scim-prime|scim-skk|scim-tables-additional|scim-m17n|scim-uim|scim-tables-ja|scim-tables-ko|scim-tables-zh"
```Japanese didn't even show up as an option in the SCIM settings editor:

[IMG]http://dl.dropbox.com/u/23652/Screenshot.png[/IMG]

I'm guessing SCIM  was essentially abandoned in 9.10 in favor of ibus.  It would have been nice if they'd made that fact more obvious or otherwise kept existing Japanese support in-place so that folks wouldn't be so confused after upgrading.

Thanks anyway. &#12417;&#12385;&#12419;&#12367;&#12385;&#12419;&#21161;&#12363;&#12387;&#12383;&#12431;&#12290;

toki

---

### Post by Zorael on 2009-11-22
> **tokage said:**
> Japanese doesn't even show up as an option in the SCIM settings editor:

[IMG]http://dl.dropbox.com/u/23652/Screenshot.png[/IMG]

However, if I log in under a Japanese locale, I can use it just fine.  What is broken?  Can you help me?

Thanks,
toki
Now THIS is curious. You *do* have the **scim-anthy** package installed, I assume? And if it works in a Japanese locale, are you sure that's SCIM and not ibus? As per your pasted output, the system-wide ja_JP xinput.d symlink points to ibus.

In the original post, ryukent suggested you add a line to **~/.scim/global**. I see from your pasted terminal output that you were in that directory, so perhaps you already did this. I never had to touch this file myself, even with an all_ALL locale. Perhaps you do, not sure.
```
/SupportedUnicodeLocales = en_US.UTF-8,en_GB.UTF-8
```

Anyway; do you have several users on your machine? Or can the system-wide default safely be set to use SCIM? To simplify things?

On the whole, everything seems (to me) to be set up properly, if in a tad confusing manner. Your system-wide default is to not use any special input method, as these output snippets made evident. (The **default** file is empty on a standard installation.)
```
The system wide default is pointed by "/etc/alternatives/xinput-all_ALL" .
xinput-all_ALL - auto mode
 link currently points to **default**
```
```
toki@toki-desktop:~/.scim$ ls -l /etc/alternatives/xinput*
lrwxrwxrwx 1 root root 31 2009-05-02 03:14 /etc/alternatives/xinput-all_ALL -> /etc/X11/xinit/xinput.d/**default**
```
Your system-wide locale-specific symlinks are pointing to ibus. And your user supposedly listens to your **~/.xinput/en_US** symlink, which points to **/etc/X11/xinit/xinput.d/scim**, whose content looks okay assuming you have scim-bridge packages installed.

On a system where the xinput.d file is read properly and whose content points to scim-bridge like yours does, the following command should output thusly;
```
$ echo GTK: $GTK_IM_MODULE, Qt: $QT_IM_MODULE, XMOD: $XMODIFIERS
**GTK: scim-bridge, Qt: scim-bridge, XMOD: @im=scim**
```
If it does for you too, then either SCIM needs to be told to work in your locale in **~/.scim/global**, or you're missing packages. Currently your xinput.d/scim file says to use **scim-bridge**, and if you don't have that installed, it won't work, obviously. That doesn't account for why the SCIM setup tool doesn't recognize Anthy, though. Unless, of course, that isn't installed either. Regardless, the aptitude command below should install everything you need.
```
$ sudo aptitude install scim scim-anthy ~nscim-bridge
```

SCIM is supposedly dead-ish upstream, so a move to IBus is not entirely unwarranted.

So is IBus the default in Ubuntu installations now? I use UIM in Kubuntu (9.10). I tried IBus and it generally worked, although I had problems with dead keys not working (like ~¨^) which made me move back to UIM again. Sadly neither have Qt panels, and Skim is old and built on Qt3. IBus also starts its panel helper as soon as the daemon starts, which precedes KDE's GTK theming, so the panel ends up looking very grey and goofy. If manually terminated and restarted, it's themed properly but then the fonts in the Candidates window gets overridden by said theming, and ends up being very small and illegible. I want to like IBus, but UIM works better for me.

---

### Post by tokage on 2009-11-22
I did have the scim-anthy packages installed, so I have no idea why it didn't show up as an option.  I suppose I could have tried reinstalling, but either way, I was able to get anthy working by switching to ibus, instead, and since I don't use dead keys, it's not a show-stopper for me.

Even after using the language tool to set everything to ibis, it looks like the input method for Qt is still set to xim:
```
toki@toki-desktop:~$ echo GTK: $GTK_IM_MODULE, Qt: $QT_IM_MODULE, XMOD: $XMODIFIERS
GTK: ibus, Qt: xim, XMOD: @im=ibus
```
Is this because ibis doesn't support Qt applications, or was the environment variable just not set up correctly?

---

### Post by tokage on 2009-11-22
Actually, looks like I didn't have the ibus-qt4 package installed.  I installed it and it shows up fine, now.

Thanks... and sorry for all the back-and-forth. =)

---

