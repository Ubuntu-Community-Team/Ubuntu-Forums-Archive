---
title: "HOWTO: Installing Japanese Input &amp; Font Setup in Ubuntu 8.10 (Intrepid) with SCIM &#26085;&#26412;&#35486;"
date: 2008-11-08
forum: Outdated Tutorials &amp; Tips
---

### Post by ryukent on 2008-11-08
**[SIZE="3"]HOWTO: Installing Japanese Input and Font Setup in Ubuntu 8.10 (Intrepid) using SCIM: &#26085;&#26412;&#35486;[/SIZE]**

Installing Japanese Input and Superior Font Setup in Ubuntu

**Introduction**

This is a guide to setting up Japanese for Ubuntu 8.10 Intrepid. It is intended as a complete guide encompassing all elements required for using Japanese on any language installation of Ubuntu. It covers input (SCIM-Anthy) and configuring the Japanese fonts. There are other guides around for older versions of Ubuntu or that use the alternative UIM (see other guide). This guide is intended to cover everything. Please note that Kubuntu requires slightly different steps. Please follow the [relevant page]("http://kubuntuforums.net/forums/index.php?topic=3099856") accordingly. This is an updated version based on the original 6.10 one, but with some sections changed. Please note that if you follow this guide, your fonts will be reconfigured. This might mean losing some font settings you may have made. With each version of Ubuntu, there are certain changes, this guide is not the same as the 8.04 version.

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
deb http://archive.ubuntulinux.jp/ubuntu-ja intrepid/
```

Note that you will need to change 'intrepid' if you are using a different version from 8.10. Now update your repos with:

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

Now you want to make SCIM (Language input system) available in your English (or other language) login and not just the Japanese one. Since 8.04, ubuntu will make it available in GTK applications, but if you want to run non-GTK applications such as KDE or pure X software such as those Java based you'll need to make a few changes. If you are running a US locale, it might work with defaults, but any other locale will almost certainly need registering. First restart your computer to make sure the relevant folder have been created, then open the scim global settings file:

```
gedit ~/.scim/global
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

IMPORTANT NOTE: SCIM is very unforgiving with this line. Note that there is NO SPACE between the "," and "en_GB". If you put a space there, it will ignore everything after. Therefore make sure the following locales are separated by a comma only.

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

Where 'en' corresponds to your locale type. In my case (en_GB.UTF- it is 'en'. For you, it might be different. You can look it up as mentioned above.

Now that Tomoe is installed, it is accessible on the SCIM menu under the 'SCIM Command Menu' and listed as 'Handwriting recognition'.

**Setting up the system to display Japanese characters properly**

OK, now you've got Japanese input installed (hopefully). It might require rebooting xwindows (CTRL+ALT+Backspace). But for me, I really didn't like the horrible fonts that defaulted. Particularly the fact that hiragana / katakana characters are rendered differently from kanjis and the poor quality of smaller sizes annoys me. The main reason for this is that the fonts provided do not always have a full set of kanjis, with default settings the kanjis are rendered as bitmaps and the hiragana and katakana as vectors.

At lower font sizes, it would be impossible to render all the strokes in very complicated characters without blurring and this causes a readability problem. This can be overcome with bitmap alternatives at a low end. Certain strokes are omitted and the shape is actually changed in order to improve readability. It's not simply a case of rendering the same vector in a smaller size. Some true type fonts contain bitmap alternatives that can be automatically substituted at the low end. This is a common approach and is adopted by Windows, MacOS and other electronic devices in Asia such as mobile phones. Here's the next step.

**Downloading External Fonts**

Unfortunately, I am very disappointed in the Ubuntu selection and you will almost certainly want this to be changed to MSGothic and MSMincho. They contain a superior vector and bitmap selection. These are Microsoft fonts, but they are freely available to use and are actually from a company called Ricoh. They need to be downloaded and installed manually. They can be found at the following page.

[http://www.linux.ryukent.co.uk/show.php?id=24]("http://www.linux.ryukent.co.uk/show.php?id=24")

So download and extract the files and you need to copy them into the fonts directory. This will need root privileges and is probably easiest done using the file explorer:

```
gksudo "nautilus --browser"
```

That will give you a browser with the right privileges. So copy your downloaded ttf files and paste them into a folder under the fonts tree. I recommend:

```
/usr/share/fonts/truetype/msjapanesefonts
```
[B]
Rebuilding the font cache[/B]

Now we need to rebuild the fonts cache:

```
sudo fc-cache -f -v
```

**Setting up the font order**

OK, so that might well be enough, but I think you'll probably still have your Japanese fonts not running at optimum and the default might be a little ugly. Lets set up the order in which we like the fonts to be selected. Open the &#8220;.fonts.conf&#8221; file in your home directory:

```
gedit ~/.fonts.conf
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
So, save the file and reboot xwindows (CTLR+ALT+Backspace). Now with any luck the order of fonts should have been updated so that the default Japanese type face is actually a clean one first and foremost instead of the ugly first serving. Also it enables the built in bitmap font which can really make kanjis more readable and also enables the bitmap version of hiragana and katakana so that they don't look blurry anti-aliased next to clear bitmap kanjis. For most people this setting will be fine. If you're not happy, by all means leave out the embeddedbitmap setting or change it to false.

To finish things off, I'd suggest making sure in System / Preferences / Appearance / Fonts, you've got subpixel smoothing on and after clicking on details, hinting is set to 'full'.

If you have any additional questions, please don't hesitate to message me in this forum. I'm always happy to help, though I make take a little while responding. &#38929;&#24373;&#12387;&#12390;&#12367;&#12384;&#12373;&#12356; - RyuKent

---

### Post by TWO on 2008-11-11
&#12424;&#12369;&#12428;&#12400;&#12289;Kubuntu Intrepid&#12398;SKIM&#12398;&#35373;&#23450;&#12392;&#20351;&#12356;&#26041;&#12434;&#25945;&#12360;&#12390;&#12418;&#12425;&#12360;&#12414;&#12379;&#12435;&#12363;&#12290;

Sorry, I couldn't resist! :lolflag:

No, I would use Kubuntu Intrepid, however I wasn't quite able to work out how to set up Skim, which I prefered over SCIM because it was much easier to set up under Kubuntu Hardy.

Would you be able to write about set-up under Kubuntu Intrepid?

&#12362;&#39000;&#12356;&#12375;&#12414;&#12377;

TWO

---

### Post by twosnakes on 2008-11-11
Unfortunately I wasn't able to type in Japanese text via SCIM once I completed the steps for "Making SCIM available under a non-Japanese login." 

I opened up the text editor, pressed ctrl+space and had the SCIM box pop up in the lower right hand corner. Japanese text was not among the options listed, however "Other-English/European," "Other-RAW CODE," and "English/Keyboard" was available to use as an input method.

I completed the rest of the outlined steps in hopes that this would correct any kind of error but I'm sure thats just wishful thinking.

Also, I ensured that I had the most recent updates and packages installed via Update Manager. If that helps

According to the characteristics that I just described, could you give me a hint as to how I correct the SCIM configuration?

Thank you very much

---

### Post by sharon.gmc on 2008-11-12
very good post. . . thank you!

---

### Post by Lexicon101 on 2008-11-13
is there something I'm doing wrong? I didn't do the bit with adding the handwriting support, but I didn't see a need for it, and it'd add trouble for me that I don't care for..
That being said.. none of the triggers work for my SCIM... I've tried all kinds of little configuration tweaks via the GUI setup tool, just.. when I press ctrl + space, nothing happens.
I have SCIM, anthy, language-pack-ja, language-pack-gnome-ja, language-support-ja, and all that stuff installed.. Anthy shows up in my input method list in the SCIM GUI setup tool.. Frankly, I'm pretty stumped by why I still can't type in basic japanese characters..
(Oh, and I've got the fonts installed, I believe.. If that sounds like something that would cause my problem to anyone else, I'll confirm later, I'm just way too tired and irritated from trying to get this to work right now..)

---

### Post by ryukent on 2008-11-13
Two snakes, can you confirm that 'Anthy' is on your list within SCIM. It should be automatically installed when you select Japanese in the language support.

---

### Post by ryukent on 2008-11-13
Lexicon101.... you say you have Anthy installed and appears on your list in SCIM. So when you're in gedit, right click and select SCIM as the input method. When SCIM is running, can you select Anthy?

---

### Post by Lexicon101 on 2008-11-14
Well now that solves that.. But I don't see a way of doing the same in firefox..

---

### Post by ryukent on 2008-11-14
Hmm... SCIM should be available automatically. Can you give me the output of:

im-switch -l

Also, can you confirm that you're running a fresh install of 8.10, or did you upgrade??

---

### Post by Jimmy9pints on 2008-11-15
This is a great how to. 

But does anybody know how to get this working for Chinese in Kubuntu (intrepid KDE 4.1)

Any help greatly appreciated.

Cheers,

James

---

### Post by twosnakes on 2008-11-16
Ryukent,

No, anthy is not an option to SCIM.

I might have solved my own problem here, and I apologize for not mentioning it earlier. I am using Hardy Heron and I when setting up the repositories in the sources list, I typed in "Intrepid" as per the guidelines written by you, not Hardy. I'll give correcting this a try and see if it works.

---

### Post by ryukent on 2008-11-17
Twosnakes,
Yes, you'll need to change the distribution code to hardy. I'm still a little concerned that Anthy hasn't been installed automatically. Are the packages "anthy" and "scim-anthy" present on your system? These should have been automatically put on when you used the 'System/Administration/Language Support' menu to add Japanese. It could be damaged install. It's worth making sure that this script has been run as it installs a number of essential packages including the language packs, input method packages and run the input method selector script.

If you're still having no luck, I recommend removing Japanese and support for complex characters, restarting, then adding them back. This should hopefully correct any errors.

Finally, if that still doesn't work, consider replacing (not upgrading) your distribution with Intrepid. There are all sorts of other reasons why this will benefit you, but I can confirm that running through the instructions in the original post will definitely work on a fresh install (has been tested on many systems).

---

### Post by YannBuntu on 2008-11-17
First of all thanks for your tutorials, they helped me a lot for Gutsy and Hardy.

When I installed my Ubuntu 8.10 in French, then added the Japanese language + Complex characters option, _SCIM happened to work perfectly_ in my French session. :KS

So, sorry if I missed something, but **what does this last HOW TO improve in Intrepid ?** display?

Thanks in advance

---

### Post by ryukent on 2008-11-17
YannBuntu,

The first step (through language support) will indeed install SCIM and Anthy which nowadays should work in GTK applications even in non-Japanese logins. It didn't used to. It is still a vital step in setting up an environment for Japanese input.

Following the HOWTO will also add the additional Japanese repository which often has different and more updated versions of SCIM and Anthy. It also contains a number of other packages not present in the normal repos which are useful for users who speak Japanese.

Making SCIM available under a non-Japanese login section focusses on setting up SCIM to run in non GTK applications, such as Java, X windows etc. This is absolutely essential to anyone who doesn't only use gnome stuff, though you could probably get away with only running GTK applications on Ubuntu nowadays. I'd rather not.

Handwriting support is covered. This is not installed by default and is difficult to set up if you are unaware of the non-documented 'features' requiring setup of the xml file etc.

The last part covers the display of Japanese characters in Ubuntu. Most people who use Japanese would prefer an experience similar to Windows or MacOS and not simply the default 'it works but doesn't look nice' scheme that comes out of the box and is designed for roman type users.

The aim of the HOWTO, as stated, is not to provide a simple setup guide for SCIM, but to walk users through the entire setup process for a usable Japanese environment sitting on top of a non-Japanese install of Ubuntu. That's why there are different parts. If you are happy with bad looking Japanese characters that input only into GTK applications with no handwriting support and poorly updated incomplete repositories, then it is possible to simply use the bundled script. I just wanted to elaborate on what's possible for people who want more.

---

### Post by sstamnes on 2008-11-18
I am running into the following problem:

<pre>
# apt-get install scim-tomoe
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package scim-tomoe is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package scim-tomoe has no installation candidate
</pre>

<pre>
# apt-cache search tomoe
tomoe-dic - handwriting recognition library - dictionary
tomoe-gtk-l10n - class library for tomoe's GTK+ GUI parts - lanugage
tomoe-gtk-common - class library for tomoe's GTK+ GUI parts - common
tomoe-gtk-doc - class library for tomoe's GTK+ GUI parts - doc
tomoe-doc - handwriting recognition library - document
tomoe-l10n - handwriting recognition library - locale data
libtomoe0 - handwriting recognition library - runtime
libtomoe-dev - handwriting recognition library - development


# apt-get install tomoe-gtk-l10n
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  tomoe-gtk-l10n: Depends: libtomoe-gtk0 (= 0.6.0-0ubuntu3) but it is not installable
E: Broken packages
</pre>

---

### Post by ryukent on 2008-11-18
sstamnes,

Did you make sure you added the Japanese repository in the first post? If so, did you do the update so that its package list is imported?

After that, scim-tomoe should be available and all relevant dependencies.

---

### Post by Zorael on 2008-11-18
Please prove me wrong, but I think some of the packages in the repository only have i386 debs. Which would account for such errors if you're running other architectures (like x86_64).

If someone would compile and upload 64-bit packages (of tomoe, skim-scim-anthy, updated versions of scim, etc; what's on that repo as i386-only), that'd be seriously awesome.

---

### Post by Zorael on 2008-11-18
```
[COLOR="Lime"]emacs-env-ja_8.10_all.deb		2008-Oct-30 21:36:28	3.1K	application/x-debian-package[/COLOR]

[COLOR="SeaGreen"]jd_2.0.2-080919-0ubuntu2_amd64.deb	2008-Nov-04 21:59:59	1.6M	application/x-debian-package[/COLOR]
jd_2.0.2-080919-0ubuntu2_i386.deb	2008-Oct-25 01:18:37	1.5M	application/x-debian-package

[COLOR="Sienna"]kasumi_2.3-0ubuntu3_i386.deb		2008-Oct-17 23:45:50	71.7K	application/x-debian-package[/COLOR]

[COLOR="SeaGreen"]libtomoe-dev_0.6.0-0ubuntu5_amd64.deb	2008-Nov-05 22:12:49	11.3K	application/x-debian-package[/COLOR]
libtomoe-dev_0.6.0-0ubuntu5_i386.deb	2008-Oct-18 00:48:05	10.7K	application/x-debian-package
[COLOR="Sienna"]libtomoe-gtk-dev_0.6.0-0ubuntu3_i386.deb	2008-Oct-18 01:10:58	53.2K	application/x-debian-package
libtomoe-gtk0_0.6.0-0ubuntu3_i386.deb	2008-Oct-18 01:10:58	45.8K	application/x-debian-package[/COLOR]
[COLOR="SeaGreen"]libtomoe0_0.6.0-0ubuntu5_amd64.deb	2008-Nov-05 22:12:44	1.9M	application/x-debian-package[/COLOR]
libtomoe0_0.6.0-0ubuntu5_i386.deb	2008-Oct-18 00:48:04	1.1M	application/x-debian-package

[COLOR="Sienna"]libx11-6-dbg_1.1.5-2ubuntu1ja1_i386.deb	2008-Oct-18 00:12:48	2.8M	application/x-debian-package
libx11-6_1.1.5-2ubuntu1ja1_i386.deb	2008-Oct-18 00:12:44	613.9K	application/x-debian-package[/COLOR]
[COLOR="Lime"]libx11-data_1.1.5-2ubuntu1ja1_all.deb	2008-Oct-18 00:12:04	178.8K	application/x-debian-package[/COLOR]
[COLOR="Sienna"]libx11-dev_1.1.5-2ubuntu1ja1_i386.deb	2008-Oct-18 00:12:49	1.6M	application/x-debian-package
libx11-xcb-dev_1.1.5-2ubuntu1ja1_i386.deb	2008-Oct-18 00:12:49	68.6K	application/x-debian-package
libx11-xcb1-dbg_1.1.5-2ubuntu1ja1_i386.deb	2008-Oct-18 00:12:49	80.2K	application/x-debian-package
libx11-xcb1_1.1.5-2ubuntu1ja1_i386.deb	2008-Oct-18 00:12:49	66.4K	application/x-debian-package[/COLOR]

[COLOR="Sienna"]scim-anthy_1.2.6-0ubuntu2_i386.deb	2008-Oct-18 00:31:35	734.0K	application/x-debian-package
scim-tomoe_0.6.0-0ubuntu3_i386.deb	2008-Oct-18 01:15:22	42.1K	application/x-debian-package[/COLOR]

[COLOR="Lime"]tomoe-dic_0.6.0-0ubuntu5_all.deb	2008-Nov-05 22:11:12	1.5M	application/x-debian-package
tomoe-doc_0.6.0-0ubuntu5_all.deb	2008-Nov-05 22:11:16	28.6K	application/x-debian-package
tomoe-gtk-common_0.6.0-0ubuntu3_all.deb	2008-Oct-18 01:10:58	13.4K	application/x-debian-package
tomoe-gtk-doc_0.6.0-0ubuntu3_all.deb	2008-Oct-18 01:10:58	28.0K	application/x-debian-package
tomoe-gtk-l10n_0.6.0-0ubuntu3_all.deb	2008-Oct-18 01:10:58	12.0K	application/x-debian-package
tomoe-l10n_0.6.0-0ubuntu5_all.deb	2008-Nov-05 22:11:21	4.9K	application/x-debian-package[/COLOR]

[COLOR="Lime"]ttf-umefont_394-1ubuntu0ja1_all.deb	2008-Oct-25 20:50:22	30.9M	application/x-debian-package[/COLOR]

[COLOR="Sienna"]ubuntu-desktop-ja_8.10-20081025-1_i386.deb	2008-Oct-25 13:41:15	2.3K	application/x-debian-package[/COLOR]
[COLOR="Lime"]ubuntu-ja-keyring-udeb_2005.09.28_all.udeb	2005-Sep-28 11:31:26	2.0K	application/x-debian-package
ubuntu-ja-keyring_2005.09.28_all.deb	2005-Sep-28 11:31:26	3.2K	application/x-debian-package[/COLOR]

[COLOR="SeaGreen"]zenity_2.24.0-0ubuntu1ja1_amd64.deb	2008-Nov-04 22:18:37	2.0M	application/x-debian-package[/COLOR]
zenity_2.24.0-0ubuntu1ja1_i386.deb	2008-Oct-28 23:37:32	2.0M	application/x-debian-package
```
Lime green: "all" package, darker green: amd64 package, dark red: *ONLY* available for i386.

If you're not running i386, you can't get kasumi, scim-tomoe, scim-anthy, ubuntu-desktop-ja, nor other packages that break because of missing library packages, like tomoe with libtomoe-gtk0.

Soo, if there's someone out there handy and knowledgeable about compiling and creating packages, I'd love to get amd64 (or better yet, "all") .debs of those. Hint hint!

---

### Post by LunaEqualsLuna on 2008-11-20
when i install SCIM i can no longer do use the file quick search in nautilus.

How do i fix this?
Its the only thing stopping from using SCIM. other than that it works perfectly.

I tried UIM but it doesn't work...

---

### Post by Futsuriai on 2008-11-20
Hello, not really sure if this is the best place to post but after following the instructions it seems that everything is working as it should (save the lack of 64 bit packages) however on the Firefox 3.1b1 from Mozilla's site I can't get Japanese input going, it works on the default Firefox but I was wondering if someone with more SCIM knowledge might know why a program would fail to work when all others do...?

Thanks

---

### Post by senor_smile on 2008-11-22
I get the same error that another member gets when trying to install scim-tomoe.  I have JUST installed ubuntu for the first time, coming from an only windows based background(I have dabbled in linux before with little success).  I followed the directions to the T, yet get that error.  Here is the error as it appears exactly in my terminal: 

```
shaun@ubuntu:~$ sudo apt-get install scim-tomoe
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package scim-tomoe is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package scim-tomoe has no installation candidate
```

Any help would be greatly appreciated.  

--shaun

---

### Post by ryukent on 2008-11-22
Are you running the 64-bit version of Ubuntu?

---

### Post by senor_smile on 2008-11-22
I installed it using wubi, so it downloaded the version it needed.  It's a 3 year old laptop...

I searched and found the command: 
> cat /proc/cpuinfo

and  got the following output:

```
model name	: AMD Turion(tm) 64 Mobile Technology ML-34
```

so, i guess i need to try installing manually.

---

### Post by ryukent on 2008-11-23
Yeah, unfortunately Tomoe is not available in the repos yet for 64 bit. Do you really need it though? It's just a system for recognising kanji's you draw with a mouse. But Kanji's will be autoconverted when you type in Kana anyway. To be honest, I never really use it myself. The only time I could ever imagine using it would be if you had a kanji on paper and couldn't read it. If it's onscreen, you can look it up with copy and paste. If you know it's reading, you can type it on the keyboard. You could always use radical searching to avoid this anyway.

---

### Post by ryukent on 2008-11-23
Also, unless you're running high performance memory intensive applications, there's no reason to use 64-bit ubuntu. Standard 32-bit is much more compatible. You probably won't notice any difference in performance.

---

### Post by senor_smile on 2008-11-23
Ah, so I could potentially downgrade to 32 bit?  

I did use that feature quite often in windows.  I am learning kanji using Heisig's Remembering the Kanji III(already went through the first book) and fairly regularly have kanji in my mind that I mix up with some other kanji, and can't quite remember the meaning of.  With that feature, I can just manually input the kanji in my head and instantly find the meaning of the kanji.

---

### Post by ryukent on 2008-11-24
There is a program called Kanjipad which will pretty much do everything tomoe did whilst not being integrated into the SCIM toolbar.

---

### Post by Zorael on 2008-11-24
You can't outright downgrade an installation into one of another processor archetype, like 32-bit <-> 64-bit. As for the pros and cons of those two, please see [this thread](http://ubuntuforums.org/showthread.php?t=765428).

I'm too stubborn to use 32-bit when my processor supports more. And it saddens me to see stuff that doesn't work/install in 64-bit environments. Adobe recently released a 64-bit Flash alpha/beta, which is very good news - now we just need Sun to release proper 64-bit Java plugin support, which is supposedly to come with Java 7. Then we can finally launch our crusade and make 32-bit deprecated.

Heck, I remember when there were two files to pick between when downloading mIRC; mirc16 and mirc32. So we just need to take the next step.

---

### Post by senor_smile on 2008-11-24
thanks, Kanjipad does the trick.  Exactly what I needed.  I installed it with 

```
sudo apt-get install kanjipad 

```

and was able to launch it from the terminal immediately.  I then just had to go to System,Preferences,Main Menu and add /usr/kanjipad as a menu item.  


Zorael:  I didn't figure so, but it never hurts to ask those much more experienced than I.  I am rather liking my new OS, and don't really want to go through the process of reinstalling anything as I've spent a lot of time already getting this installation going well.  

--shaun

---

### Post by ryukent on 2008-11-28
I have written a KDE version for Kubuntu which has a number of key differences.

[http://kubuntuforums.net/forums/index.php?topic=3099856](http://kubuntuforums.net/forums/index.php?topic=3099856)

I want to dedicate this one to Zorael, who's been so helpful in these threads and who's sig got me interested in KDE again.

---

### Post by twosnakes on 2008-12-04
OK. It seems that once I did a package update that I was suddenly able to do Japanese input. Sorry about all the trouble earlier.

&#12415;&#12394;&#12383;&#12385;&#12289;&#25945;&#12360;&#12387;&#12390;&#19979;&#12373;&#12387;&#12390;&#12393;&#12418;&#12354;&#12426;&#12364;&#12392;&#12358;&#12372;&#12374;&#12356;&#12414;&#12375;&#12383;&#12290;

---

### Post by Zorael on 2008-12-05
It struck me that I've never actually done this in Gnome since Feisty, so now that I'm trying out Linux Mint (Gnome) I hit a wall. It works, but the scim daemon doesn't start upon login. Obviously I can work around it by making an entry in Sessions, but why do I need to?

Everything else is set up, /etc/alternatives/xinput* all point to /etc/X11/xinit/xinput.d/scim-bridge where I set up the variables properly.
```
XIM=SCIM
XIM_PROGRAM=/usr/bin/scim
XIM_ARGS="-d"
XIM_PROGRAM_SETS_ITSELF_AS_DAEMON=yes
...
```


It just doesn't start by itself for some reason? In skim's setup I could set it to automatically start, but I can't find any such option in scim-setup. And yeuch, by the way, at scim's logo. :3

edit: oh hey, new bean icons.

---

### Post by Zorael on 2008-12-05
And now it works for no reason whatsoever, bleh.

---

### Post by ryukent on 2008-12-05
Very weirdly I occasionally get that, but only in KDE, gnome always works 100%, but in Kubuntu, every 30 times or so, it'll just not start for no reason what so ever. Also, I occasionally have to terminate SKIM before Kubunu will shut down. If only we could have the functionality of KDE with the stability and robustness of gnome.

---

### Post by Zorael on 2008-12-05
I would adore KDE4, *IF AND ONLY IF* I didn't get that awful [video garbage bug](http://bugs.kde.org/show_bug.cgi?id=170462) on every single machine I install it on. (Also [here](https://bugs.launchpad.net/ubuntu/+source/kubuntu-kde4-meta/+bug/254468).) It's a blemish on a beautiful environment, and it doesn't seem to get the attention of the correct people.

[Example video](http://bugs.kde.org/attachment.cgi?id=28151) and [example screenshot](http://bugs.kde.org/attachment.cgi?id=27830). If you get it as well, go vote for it on KDE's bugtracker! Shameless? Phaw!


</hijack>
Where were we? Oh, right, skim.

Even if I haven't got the xinput configuration file (/etc/X11/xinit/xinput.d/skim) correctly setup, it will still autostart if I tell it to, in skim's setup window. I didn't find any such option in scim's, which confused me. But obviously I did *something* right, since now it's autostarting even though I haven't told it to.

I don't like "spontaneous fixes" much more than I like spontaneous breakage.

---

### Post by YannBuntu on 2008-12-09
> **ryukent said:**
> YannBuntu,

The first step (through language support) will indeed install SCIM and Anthy which nowadays should work in GTK applications even in non-Japanese logins. It didn't used to. It is still a vital step in setting up an environment for Japanese input.

Following the HOWTO will also add the additional Japanese repository which often has different and more updated versions of SCIM and Anthy. It also contains a number of other packages not present in the normal repos which are useful for users who speak Japanese.

Making SCIM available under a non-Japanese login section focusses on setting up SCIM to run in non GTK applications, such as Java, X windows etc. This is absolutely essential to anyone who doesn't only use gnome stuff, though you could probably get away with only running GTK applications on Ubuntu nowadays. I'd rather not.

Handwriting support is covered. This is not installed by default and is difficult to set up if you are unaware of the non-documented 'features' requiring setup of the xml file etc.

The last part covers the display of Japanese characters in Ubuntu. Most people who use Japanese would prefer an experience similar to Windows or MacOS and not simply the default 'it works but doesn't look nice' scheme that comes out of the box and is designed for roman type users.

The aim of the HOWTO, as stated, is not to provide a simple setup guide for SCIM, but to walk users through the entire setup process for a usable Japanese environment sitting on top of a non-Japanese install of Ubuntu. That's why there are different parts. If you are happy with bad looking Japanese characters that input only into GTK applications with no handwriting support and poorly updated incomplete repositories, then it is possible to simply use the bundled script. I just wanted to elaborate on what's possible for people who want more.

Hello Ryukent, thanks for your kind answer. 
I tried the HOWTO, and it seems I still can't use SCIM in my English session (it still works in my French one, which is my main). Also when i did gedit ~/.scim/global , the file was blank, is it normal?
Same for gedit ~/.fonts.conf (this looks NG) ?

Thanks again for your precious help. I hope one day all this will natively work on Ubuntu, so that you won't have to make other HOWTO :p 
(by the way, is there a \\:D/ bug report on Launchpad? )

---

### Post by fiona-conn on 2008-12-09
This is so awesome. xD

&#24230;&#12418;&#26377;&#38627;&#12358;&#12372;&#12374;&#12356;&#12414;&#12377;!&#12288;&#65342;&#65343;&#65342;

~Fiona

---

### Post by ryukent on 2008-12-12
YannBuntu,

There might not necessarily be anything in those files before you edit them. If you are using more than one locale to log in, check that the input method is set for each one. It should be set to scim-bridge and you can check by running

im-switch -l

Then to set it, use

im-switch -c

---

### Post by akai_kenshi on 2008-12-23
Great tutorial. I have a small problem that makes a few websites unusable, however. Occasionally, there is garbage where their should be Japanese text, like the links at the bottom of Muji's website (attached screenshot).

Any ideas?

---

### Post by travnewmatic on 2008-12-28
Japanese input works fine at Japanese login

Japanese input works fine at English login

Unfortunately, my fonts in the English login are messed up.

Theyre readable, but as you can see, theres something slightly off...  any suggestions?

---

### Post by linuxguiri on 2009-01-02
I followed this howto faithfully, but now text does not display correctly (or at all) on some webpages (Facebook and Blogger, for example--screenshot attached).

These webpages displayed correctly before installing Japanese support; however, removing scim and Japanese language support did not fix the problem.

Any ideas?

(Ubuntu 8.10 clean install, Firefox 3.0.5)

---

### Post by ryukent on 2009-01-17
This is indeed strange. Try deleting your fonts.conf file, then rebuilding the font cache.

---

### Post by ryukent on 2009-01-17
Akai Kenshi,

Your problem with garbled text is because the text is from a flash file. It is a flash problem and based on your flash player's ability to render Japanese fonts. Try using a different flash player or changing its config.

---

### Post by ryukent on 2009-01-17
Travnewmatic,

Looks like your english fonts render fine, but your font setup is a bit weird. You can edit it using System / preferences / appearance / font.

---

### Post by urbandryad on 2009-01-19
I've followed all the settings, and everything looks like its working, except that now all my text is underlined in the Japanese. o.o Also, I'm not sure the fancy 'MS' Japanese fonts are being used, I don't see a difference in the font. I had to create the .fonts file because it didn't exist. I also had to do the same with the ~/.scim/global file. :/ Was this wrong?

---

### Post by BuntuFirstTimer on 2009-01-19
I cannot save the **~/.scim/global** file in any ways with a new SupportedUnicodeLocale.

---

### Post by ryukent on 2009-01-21
~/.scim/global and .fonts might not exist before you create them.

If you have problems saving a file, it's probably because of a permissions issue. Try running gedit in sudo mode:

gksu gedit

---

### Post by Zorael on 2009-01-22
Worth mentioning is that nothing in your home directory should really (per default) require greater permissions than that of your user, perhaps excepting some encryption-related files. So you may want to correct the permissions themselves instead of abiding them. :3

Do correct me if I'm wrong.

```
$ sudo chown *<user>*:*<usergroup>* ~/.scim/global ~/.fonts.conf
$ chmod +rw ~/.scim/global ~/.fonts.conf
```

---

### Post by rexregum on 2009-01-22
Thanks for the How-to. Unfortunately, my font is overzealous in its application:

It's converting parts of English text into Japanese characters. :shock:

---

### Post by ryukent on 2009-01-23
That would be a problem with the character set that firefox is rendering your web page. Try View / Character Encoding / Auto Detect, or select western.

Also try Preferences / Content / Advanced for more font setup.

---

### Post by tpp on 2009-02-04
Hi I've followed all instructions and installed the Japanese support in Ubuntu intrepid. It all works fine - I can input japanese everywhere except here:

[http://www.learn-hiragana-katakana.com/typing-hiragana-characters/](http://www.learn-hiragana-katakana.com/typing-hiragana-characters/)

Is this a problem with Flash? Can anyone else recreate or fix this problem?

---

### Post by Balcerzak on 2009-02-11
Followed the tutorial successfully up until trying to install tomoe, which fails with the following.  

~$ sudo apt-get install scim-tomoe
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package scim-tomoe is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package scim-tomoe has no installation candidate

The only tomoe packages in the package manager are tomoe-gtk-doc, tomoe-gtk-|10n, tomoe-gtk-common, tomoe-dic, tomoe-|10n, tomoe-doc, libtomoe0, libtomoe-dev.  Has scim-tomoe been replaced with one of these?  I'm running the 64 bit version of Ubuntu.  Not sure what else to do, but I'll try rooting around and testing a few things.

---

### Post by Zorael on 2009-02-13
> **Balcerzak said:**
> I'm running the 64 bit version of Ubuntu.  Not sure what else to do, but I'll try rooting around and testing a few things.
The ubuntu-ja repository doesn't have amd64 versions of all packages, as I detailed a few pages back.
> **Zorael said:**
> Please prove me wrong, but I think some of the packages in the repository only have i386 debs. Which would account for such errors if you're running other architectures (like x86_64).

If someone would compile and upload 64-bit packages (of tomoe, skim-scim-anthy, updated versions of scim, etc; what's on that repo as i386-only), that'd be seriously awesome.
> **Zorael said:**
> ```
[COLOR="Lime"]emacs-env-ja_8.10_all.deb		2008-Oct-30 21:36:28	3.1K	application/x-debian-package[/COLOR]

[COLOR="SeaGreen"]jd_2.0.2-080919-0ubuntu2_amd64.deb	2008-Nov-04 21:59:59	1.6M	application/x-debian-package[/COLOR]
jd_2.0.2-080919-0ubuntu2_i386.deb	2008-Oct-25 01:18:37	1.5M	application/x-debian-package

[COLOR="Sienna"]kasumi_2.3-0ubuntu3_i386.deb		2008-Oct-17 23:45:50	71.7K	application/x-debian-package[/COLOR]

[COLOR="SeaGreen"]libtomoe-dev_0.6.0-0ubuntu5_amd64.deb	2008-Nov-05 22:12:49	11.3K	application/x-debian-package[/COLOR]
libtomoe-dev_0.6.0-0ubuntu5_i386.deb	2008-Oct-18 00:48:05	10.7K	application/x-debian-package
[COLOR="Sienna"]libtomoe-gtk-dev_0.6.0-0ubuntu3_i386.deb	2008-Oct-18 01:10:58	53.2K	application/x-debian-package
libtomoe-gtk0_0.6.0-0ubuntu3_i386.deb	2008-Oct-18 01:10:58	45.8K	application/x-debian-package[/COLOR]
[COLOR="SeaGreen"]libtomoe0_0.6.0-0ubuntu5_amd64.deb	2008-Nov-05 22:12:44	1.9M	application/x-debian-package[/COLOR]
libtomoe0_0.6.0-0ubuntu5_i386.deb	2008-Oct-18 00:48:04	1.1M	application/x-debian-package

[COLOR="Sienna"]libx11-6-dbg_1.1.5-2ubuntu1ja1_i386.deb	2008-Oct-18 00:12:48	2.8M	application/x-debian-package
libx11-6_1.1.5-2ubuntu1ja1_i386.deb	2008-Oct-18 00:12:44	613.9K	application/x-debian-package[/COLOR]
[COLOR="Lime"]libx11-data_1.1.5-2ubuntu1ja1_all.deb	2008-Oct-18 00:12:04	178.8K	application/x-debian-package[/COLOR]
[COLOR="Sienna"]libx11-dev_1.1.5-2ubuntu1ja1_i386.deb	2008-Oct-18 00:12:49	1.6M	application/x-debian-package
libx11-xcb-dev_1.1.5-2ubuntu1ja1_i386.deb	2008-Oct-18 00:12:49	68.6K	application/x-debian-package
libx11-xcb1-dbg_1.1.5-2ubuntu1ja1_i386.deb	2008-Oct-18 00:12:49	80.2K	application/x-debian-package
libx11-xcb1_1.1.5-2ubuntu1ja1_i386.deb	2008-Oct-18 00:12:49	66.4K	application/x-debian-package[/COLOR]

[COLOR="Sienna"]scim-anthy_1.2.6-0ubuntu2_i386.deb	2008-Oct-18 00:31:35	734.0K	application/x-debian-package
scim-tomoe_0.6.0-0ubuntu3_i386.deb	2008-Oct-18 01:15:22	42.1K	application/x-debian-package[/COLOR]

[COLOR="Lime"]tomoe-dic_0.6.0-0ubuntu5_all.deb	2008-Nov-05 22:11:12	1.5M	application/x-debian-package
tomoe-doc_0.6.0-0ubuntu5_all.deb	2008-Nov-05 22:11:16	28.6K	application/x-debian-package
tomoe-gtk-common_0.6.0-0ubuntu3_all.deb	2008-Oct-18 01:10:58	13.4K	application/x-debian-package
tomoe-gtk-doc_0.6.0-0ubuntu3_all.deb	2008-Oct-18 01:10:58	28.0K	application/x-debian-package
tomoe-gtk-l10n_0.6.0-0ubuntu3_all.deb	2008-Oct-18 01:10:58	12.0K	application/x-debian-package
tomoe-l10n_0.6.0-0ubuntu5_all.deb	2008-Nov-05 22:11:21	4.9K	application/x-debian-package[/COLOR]

[COLOR="Lime"]ttf-umefont_394-1ubuntu0ja1_all.deb	2008-Oct-25 20:50:22	30.9M	application/x-debian-package[/COLOR]

[COLOR="Sienna"]ubuntu-desktop-ja_8.10-20081025-1_i386.deb	2008-Oct-25 13:41:15	2.3K	application/x-debian-package[/COLOR]
[COLOR="Lime"]ubuntu-ja-keyring-udeb_2005.09.28_all.udeb	2005-Sep-28 11:31:26	2.0K	application/x-debian-package
ubuntu-ja-keyring_2005.09.28_all.deb	2005-Sep-28 11:31:26	3.2K	application/x-debian-package[/COLOR]

[COLOR="SeaGreen"]zenity_2.24.0-0ubuntu1ja1_amd64.deb	2008-Nov-04 22:18:37	2.0M	application/x-debian-package[/COLOR]
zenity_2.24.0-0ubuntu1ja1_i386.deb	2008-Oct-28 23:37:32	2.0M	application/x-debian-package
```
Lime green: "all" package, darker green: amd64 package, dark red: *ONLY* available for i386.

If you're not running i386, you can't get kasumi, scim-tomoe, scim-anthy, ubuntu-desktop-ja, nor other packages that break because of missing library packages, like tomoe with libtomoe-gtk0.

Soo, if there's someone out there handy and knowledgeable about compiling and creating packages, I'd love to get amd64 (or better yet, "all") .debs of those. Hint hint!

---

### Post by frankytea on 2009-02-25
hello and thanks for the small how-to guide. I already had scim up and running (on an English login) and everything was ok (typing in this and that application proved to be ok) but when typing in Japanese I noticed that different characters were rendered different. It didn't look too appealing so... hence me following the guide.

I jumped in from the "Downloading External Fonts" part and was working my way through...

[i](by the way I think the .zip files on 
[http://www.linux.ryukent.co.uk/show.php?id=24](http://www.linux.ryukent.co.uk/show.php?id=24)
are duds as they are only ~250KB and the native extractor didn't recognize them. I got the real mccoy from the original site though at 2.2MB a pop)[/i]

... up to the point of 'gedit ~/.fonts.conf'

I did this and not only did it come up with a fresh page but the .font.conf isn't on my home directory.

So... why is that the case and does it matter?

I do however a ~/.fontconfig/ directory with, what look like, a couple of md5sum named binaries (I thought I may throw in the most probably incorrect jargon at the end so that the reader recognises that yes I am a keen-bean-newb). That may mean something but it may not. 

Umm.. Thanks!

---

### Post by Iceman_B on 2009-02-26
Heya,

I'm running Intrepid on a headless machine, and I only administer it through Putty. Is there a way to input japanese through the terminal?
By some miracle, putty does display japanese filenames correctly in a dir:

```

&#9618;&#33775;&#31070;&#31085; [Reitaisai 5]ravi@Rin-chan:~/share/Audio/IOSYS - &#26481;&#26041;&#30495;&#33775;&#31070;&#31085; [Reitaisai 5]$ ls
01 Pray.mp3                   06 &#12458;&#12491;&#12398;&#12424;&#12358;&#12395;&#12363;&#12431;&#12356;&#12367;.mp3        11 &#34028;&#33713;&#12398;&#24819;&#12356;&#20154;.mp3        cover.jpg
02 Boder of extacy.mp3        07 Care over!!.mp3                 12 &#24651;&#12395;&#28966;&#12364;&#12428;&#12383;&#20843;&#30334;&#19975;.mp3  IOSYS - &#26481;&#26041;&#30495;&#33775;&#31070;&#31085; [Reitaisai 5].sfv
03 &#24651;&#33394;&#34987;&#23475;&#23626;.mp3             08 &#24651;&#12398;&#21610;&#25991;&#12434;&#21809;&#12360;&#12427;&#31243;&#24230;&#12398;&#12539;&#21147;.mp3  13 &#26376;&#35211;&#28271;&#28201;&#27849;&#24651;&#26053;&#24773;.mp3
04 &#12428;&#12415;&#12426;&#12419;&#65312;&#12501;&#12523;&#12512;&#12540;&#12531;.mp3   09 &#34892;&#21015;&#12398;&#12391;&#12365;&#12427;&#12360;&#12540;&#12426;&#12435;&#35386;&#30274;&#25152;.mp3  14 &#21338;&#38666;&#31070;&#31038;&#30010;&#20869;&#20250;&#38899;&#38957;.mp3
05 &#12490;&#12452;&#12501;&#12391;&#12452;&#12490;&#12501; &#38272;&#30058;&#32232;.mp3  10 &#31070;&#29539;&#12398;&#21517;&#12398;&#19979;&#12395;.mp3              15 B&#12539;E&#12539;E&#12539;R.mp3

```

Unfortunately, putty beeps with every stroke I make and the prompt gets messed up as well.
I can include a screenshot if so needed.
But if I want to type out a filename or use it with tab completion...well I simply have no way.
How would I go about this?

Here's my locale list:
```
LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=
```

---

### Post by Zorael on 2009-02-27
> **frankytea said:**
> ... up to the point of 'gedit ~/.fonts.conf'

I did this and not only did it come up with a fresh page but the .font.conf isn't on my home directory.

So... why is that the case and does it matter?

I do however a ~/.fontconfig/ directory with, what look like, a couple of md5sum named binaries (I thought I may throw in the most probably incorrect jargon at the end so that the reader recognises that yes I am a keen-bean-newb). That may mean something but it may not. 

Umm.. Thanks!
If you don't have a **~/.fonts.conf**, just create it. I'm not sure what *creates* it; I've never had it created automatically on my Kubuntu installations.

---

### Post by ryukent on 2009-02-28
Interesting, I just checked the files on that link and they are working fine. 2.2MB. Also .font.conf should sit in your home directory. Make sure you've regenerated the fonts cache and restarted X windows.

> **frankytea said:**
> 
I jumped in from the "Downloading External Fonts" part and was working my way through...

[i](by the way I think the .zip files on 
[http://www.linux.ryukent.co.uk/show.php?id=24](http://www.linux.ryukent.co.uk/show.php?id=24)
are duds as they are only ~250KB and the native extractor didn't recognize them. I got the real mccoy from the original site though at 2.2MB a pop)[/i]

... up to the point of 'gedit ~/.fonts.conf'

I did this and not only did it come up with a fresh page but the .font.conf isn't on my home directory.

So... why is that the case and does it matter?

I do however a ~/.fontconfig/ directory with, what look like, a couple of md5sum named binaries (I thought I may throw in the most probably incorrect jargon at the end so that the reader recognises that yes I am a keen-bean-newb). That may mean something but it may not. 

Umm.. Thanks!

---

### Post by senor_smile on 2009-04-04
FYI

I have successfully gotten japanese input set up on Jaunty beta.  Make sure the universe/multiverse repositories are enabled(I did not have to, nor could I enable a Jaunty equivalent of the Japanese Ubuntu repository).  Enable Japanese input from system/administration/language support. Make sure "use input method engines (IME) to enter complex characters"  is checked off.  Finally, follow the instructions on adding the two fonts, and creating the fonts.conf file and restart X.

---

### Post by Iceman_B on 2009-04-04
Is there any way to have japanese input and display in pure text?
I have switched from Ubuntu Desktop to Ubuntu Server and am therefore no in posession of a GUI.

I have a monitor hooked up locally and use it for important tasks.
When I connect from the outside(lan or wan) I use putty.
How can I display and type japanese text?

Is it even possible?

---

### Post by fridley on 2009-04-08
> **senor_smile said:**
> FYI

I have successfully gotten japanese input set up on Jaunty beta.  Make sure the universe/multiverse repositories are enabled(I did not have to, nor could I enable a Jaunty equivalent of the Japanese Ubuntu repository).  Enable Japanese input from system/administration/language support. Make sure "use input method engines (IME) to enter complex characters"  is checked off.  Finally, follow the instructions on adding the two fonts, and creating the fonts.conf file and restart X.

I have tried to follow in you foot steps to no avail. In 8.10 I had no problems adding Japanese language support, but 9.04 is giving me a headache. I have got scim installed and can see anthy as one of the options inside it, but can not for the life of me figure out what to do next.

Hope someone can help.

---

### Post by senor_smile on 2009-04-08
> **fridley said:**
> I have tried to follow in you foot steps to no avail. In 8.10 I had no problems adding Japanese language support, but 9.04 is giving me a headache. I have got scim installed and can see anthy as one of the options inside it, but can not for the life of me figure out what to do next.

Hope someone can help.

What is (or is not) happening?  Any errors?  Does Ctrl+space change scim's mode?

---

### Post by kamaaina on 2009-04-10
I have been using this tutorial for sometime on different installations and I have a few questions about font rendering.    

The best rendering (maybe too smooth for some, but ok for me) of hiragana, katakana and kanji seems to be the rendering that comes with firefox before applying this tutorial.  Other programs (like evolution) have inconsistent rendering.  Could the firefox rendering be used system wide?  

If not, then can some smoothing be put on the fonts used in the tutorial?  Everything looks sharp and contrasts with the roman characters that are well smoothed.  

I know this sounds insignificant but I would just like everything to have a consistent appearance.    

Thanks!

---

### Post by lesterness on 2009-04-13
Will this work with Chinese as well?  I definitely need kanji/hanzi.

Lesterness

---

### Post by Hakaroi on 2009-04-17
> **ryukent said:**
> **[SIZE="3"]HOWTO: Installing Japanese Input and Font Setup in Ubuntu 8.10 (Intrepid) using SCIM: &#26085;&#26412;&#35486;[/SIZE]**

Go to System / Administration / Language Support and select Japanese. This should install the basics. Make sure you've also turned on support for inputting complex characters.



For some reason. That menu option (Language Support) will not show up.:confused:](*,)](*,)](*,)

---

### Post by stokedfish on 2009-04-25
Hello, does this also work for Jaunty?

---

### Post by Dutar on 2009-04-27
Through language support (System->Admin)I add Japanese, but it didn't work. So in System->Prefe->SCIM-> I set "show" to "Always", and now it is working. The usual key combinations are also working :)

---

### Post by Silwing on 2009-04-28
I have now succesfully installed Japanese input in Ubuntu 9.04 (Jaunty). I followed the guide in the first post, except the part with adding the japanese repository, as it couldn't find it when I tried and I seemingly do not need it.

After succesfully installing and typing in Japanese characters in gedit I ran into a problem with my Spaced Repetition System software (I guess it is either java or QT4 that is the problem) which would not change input method to Anthy. I solved it by right clicking and selecting Select Input Method - XIM.

---

### Post by Zorael on 2009-04-28
These are the *minimal* steps to enable **SKIM** - the KDE SCIM frontend - under KDE. It's the same for Intrepid and Jaunty. Adding repositories and changing fonts are unnecessary steps per se, though certainly recommended if you want fresher packages and nicer font display.

[list=1][*]Install needed packages
```
$ sudo aptitude install skim scim-anthy ~nscim-bridge scim-qtimm
```
[*]Start skim, make sure it's set to load automatically on KDE startup [list][*]General SCIM -> Other -> scim-panel-kde, kconfig
[*]X Window -> Start skim automatically[/list]
[*]Restart X and repeat above step to make sure it stuck (difficult to restore if it didn't)
[*]Set SCIM as default input method via xinput.d _configuration file_: **skim** (located at **/etc/X11/xinit/xinput.d/skim**)
```
$ sudo im-switch -v -s skim
$ sudo im-switch -v -s skim -z *lang_CODE    # for other than current locale if needed, isn't if you're just using one locale since it defaults to current if not specified*
```
[list][*]Alternatively, an automated script to enable it for all locales which currently have an xinput "alternative" (generally translates to all installed locales + a few extras)
```
$ for X in $(ls /etc/alternatives/xinput*); do sudo update-alternatives --set $X /etc/X11/xinit/xinput.d/skim; done
```[/list]
[*]Modify skim xinput.d configuration file to cover XIM programs
```
$ kdesudo "kate /etc/X11/xinit/xinput.d/skim" &
$ sudo nano /etc/X11/xinit/xinput.d/skim &           *# alternative, terminal editor*
```
Make it look like the following, special attention paid to part in bold, rest should already be identical
```
[B]XIM=SCIM
XIM_PROGRAM=/usr/bin/scim
XIM_ARGS="-d"
XIM_PROGRAM_SETS_ITSELF_AS_DAEMON=yes[/B]

if [ -e /usr/lib/gtk-2.0/*/immodules/im-scim-bridge.so ]; then
    GTK_IM_MODULE=scim-bridge
elif [ -e /usr/lib/gtk-2.0/*/immodules/im-scim.so ]; then
    GTK_IM_MODULE=scim
else
    GTK_IM_MODULE=xim
fi
if [ -e /usr/lib/qt3/plugins/inputmethods/im-scim-bridge.so ] || [ -e /usr/lib/qt4/plugins/inputmethods/im-scim-bridge.so ]; then
    QT_IM_MODULE=scim-bridge
elif [ -e /usr/lib/qt3/plugins/inputmethods/libqscim.so ]; then
    QT_IM_MODULE=scim
else
    QT_IM_MODULE=xim
fi

DEPENDS="skim, scim-bridge-client-gtk | scim-bridge-client-qt | scim-bridge-client-qt4 | scim-gtk2-immodule | scim-qtimm"
```
[*]Restart X.
[*]Use a mixture of skim's configuration window and **scim-setup** to configure Anthy, unless you can somehow compile/install **skim-scim-anthy** (was present in ubuntu-ja Gutsy/Hardy repo, never since)
```
$ scim-setup &
```[/list]

The only thing that's really "difficult" is to get skim - the KDE scim frontend - to autostart without being preempted by scim. Hence the extra restart of X, just to make sure.

One bug I keep getting is that when restarting X, the skim icon doesn't dock to the tray and instead launches itself in a detached window. The workaround is to log out *first*, then restart X (by switching to a console, or by zapping with ctrl+alt+backspace if enabled). To immediately get rid of the window if detached, just hit Alt+F4. This doesn't happen when booting normally, just when restarting X manually.

---

### Post by hugstrees on 2009-05-07
Hey guys,

I'm having trouble using scim. I installed anthy from Administration->Language Support, but I can't seem to use it. The hotkeys don't seem to do anything. I can launch scim by typing scim-bridge in a terminal window. This gives me a tray icon, but it doesn't do anything. It's just taunting me. Any advice? Thanks!

Oh, I'm also using Jaunty, if that makes a difference. Is it a common problem?

Edit: It works fine now.

---

### Post by sorryd on 2009-05-11
I am using Japanese SCIM in an English version of Jaunty and I have a problem with ZIP files containing files with Japanese filenames becoming garbled for windows users. I remember having the same problem with Macs before so is this actually a Windows problem or can it be addressed in Ubuntu?

Sorry if this is the wrong thread for this, but I figured more people in the know would notice my post here.

---

### Post by peacen1k on 2009-05-18
This is a great How to.....

Massively easier than i expected.....

As I've discovered there is no jaunty repository, so where can I find Tomoe or another touchpad, mousepointer kanji input app?

&#12362;&#19990;&#35441;&#12395;&#12394;&#12426;&#12414;&#12375;&#12383;&#65281;

---

### Post by Zorael on 2009-05-18
There's a "Japanese Team" ppa that I use instead of that ubuntu-ja one. It has jaunty packages, though no intrepid ones.

[https://launchpad.net/~japaneseteam/+archive/ppa](https://launchpad.net/~japaneseteam/+archive/ppa)

```
$ echo deb http://ppa.launchpad.net/japaneseteam/ppa/ubuntu jaunty main | sudo tee /etc/apt/sources.list.d/japaneseteam.list
$ echo deb-src http://ppa.launchpad.net/japaneseteam/ppa/ubuntu jaunty main | sudo tee -a /etc/apt/sources.list.d/japaneseteam.list
$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CDC1D865
$ sudo aptitude update
$ sudo aptitude install scim-tomoe
```

---

### Post by peacen1k on 2009-05-19
Right!

I'll give that a go then!

Might not 8other with the source code tho'  :)

---

### Post by magomago on 2009-05-26
Hi I'd just like to give my inputs.  

I have Jaunty and want to use tomoe for Chinese input.  


This is what I ended up doing (figured it out on my own as opposed to have found this thread in the first place ><)

Found the repos on launchpad that had the latest version of tomoe.  If you try to use hardy ja repos, you'll run into a problem of having to use older versions of software whose latest version is already installed on the pc.  

So anyways I installed it and from the command prompt can type: 

Then from the tomoe website I found that I could type

 LANG=zh_CN scim-tomoe

in the command prompt and and it would work. The window would load up and it would recognize my input.  Awesome!

I restarted with glee, but then upon restart I found that I couldn't use 'handwriting with tomoe' option in SCIM. It would open up the window and I could write in things, but nothing would get recognized.  

Any idea on what to do?   I want to be able to type directly into programs such as firefox..the way I have to do it now leaves me crippled.  I input directly into command prompt and have to exit tomoe, copy it to a webpage, and redo the whole process.

---

### Post by Zorael on 2009-05-26
Did you copy/symlink the recognition database?
```
$ cd /usr/share/tomoe/recognizer
$ sudo ln -s handwriting-zh_CN.xml handwriting-en.xml
```
That way it'll load the (copy of the) zh_CN file even when running an English locale.

---

### Post by magomago on 2009-05-27
> **Zorael said:**
> Did you copy/symlink the recognition database?
```
$ cd /usr/share/tomoe/recognizer
$ sudo ln -s handwriting-zh_CN.xml handwriting-en.xml
```
That way it'll load the (copy of the) zh_CN file even when running an English locale.

doh you were right that did it

---

### Post by James Keating on 2009-06-04
My experience with installing SCIM in 9.04 (Jaunty) was mostly simple. I added full Japanese support through Administration/Language Support, and SCIM worked fine with the standard set of packages. 

However, I had one problem that I didn't recognize as being related to SCIM: I had constant trouble with losing keyboard input. If I used any input field or blank in my Web browser, the keyboard wouldn't respond again until I forced window manager to focus on the program again by clicking on the title bar or by right-clicking on the page and canceling. The problem with typing showed up mainly with Opera, which uses the Qt toolkit, and in TkDesk, which uses Tcl/Tk. I thought that this might be a problem with my window manager, FVWM, or with GDM, since GDM is the background to everything else. 

The problem was that SCIM defaulted to using XIM, though SCIM-bridge is better. Other posts here refer to editing the file /etc/X11/xinit/xinput.d/scim-bridge. You don't have to go there directly. In your home directory, there should be a hidden directory called .xinput.d, with a file that links to  /etc/X11/xinit/xinput.d/scim-bridge. My file is named en_US. All I had to do was edit it (as root) and change the module lines. For GTK-based programs, I changed them to prefer SCIM-bridge and then SCIM. For Qt-based programs, I changed the module lines to prefer SCIM, then XIM. The only Qt-based program I use is Opera, but Opera won't work with SCIM-bridge, even though the file /usr/lib/qt3/plugins/inputmethods/im-scim-bridge.so is present.  

My /etc/X11/xinit/xinput.d/scim-bridge now looks like:

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
    QT_IM_MODULE=scim
else
    QT_IM_MODULE=xim
fi
DEPENDS="scim | skim, scim-bridge-agent, scim-bridge-client-gtk | scim-bridge-client-qt"

This also fixed the focus problem with TkDesk. 

Qt programs need the packages scim-bridge-client-qt and scim-qtimm. 
Also, it may help to edit your file ~/.scim/global to add the line 
/DefaultConfigModule = kconfig

Before I found a proper fix for Opera, I was able to start it with
scim -d & XMODIFIERS="@im=SCIM" QT_IM_MODULE="scim" opera

#####

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

### Post by clementeb on 2009-06-04
I am writing since I have some problems with Japanese fonts on Writer.
I have installed many MS fonts taken from my personal copy of Windows and I am able to visualize MS Gothic and Mincho properly. Anyhow I noticed that with other fonts I often have problems in the sense that the characters sometimes might differ. This happens especially when I use the Times New Roman/Dejavu Sans as the basic font, which are the ones I like the most, but unfortunately in some compounds some of the characters differ and look quite ugly. The funny thing is that if I write other words that include some of the ugly characters, these get displayed correctly in the non-ugly way. I even tried pasting these nice-looking characters in place of the ugly-looking ones, but they are automatically turned into the ugly ones. What is going on?
Do I really need to renounce using the nicer fonts to have a coherent display?
In the following jpeg there is an example. The font ideally is the same for all the characters, Dejavu Sans. If I change everything to Times New Roman all the fonts become like the bolder type, if I change all to Dejavu Sans, they become mixed again.
[http://yfrog.com/16thefontproblemj](http://yfrog.com/16thefontproblemj)
[http://img42.imageshack.us/my.php?image … roblem.jpg]("http://img42.imageshack.us/my.php?image=thefontproblem.jpg")
To further show you the problem, I also include a jpeg of Tomoe handwriting recognition, that shows me the possible characters using two different fonts although only one can be set.
[http://yfrog.com/0wfontproblem2tomoeexamplj](http://yfrog.com/0wfontproblem2tomoeexamplj)
[http://img32.imageshack.us/my.php?image … exampl.jpg]("http://img32.imageshack.us/my.php?image=fontproblem2tomoeexampl.jpg")
is there a problem in the font set of my OS?

---

### Post by Zorael on 2009-06-05
What's happening there is that your nice font doesn't have a bitmap for (or simply doesn't contain definitions for) those characters that end up ugly. So it draws them as vertex fonts, alternatively falls back to another font lower in the priority list defined in your ~/.fonts.conf.

Times New Roman, for intance, contains no CJK characters. It's not a unicode font per se. As soon as you type any CJK character in Times, your system realizes it can't and falls back to another font - and if there are no other fonts available, it displays a square.

That's where your ~/.fonts.conf file comes in; you set up the "virtual" font Serif (as well as Sans-serif and Monospace) to use a priority of fonts, with the *nicest* ones up top, and gradually the ones with the best range of unicode characters afterwards.

As a simple example:
```
<?xml version="1.0"?>
<fontconfig>
 <alias>
 <family>serif</family>
 <prefer>
 <family>Times New Roman</family>
 <family>MS Mincho</family>
 </prefer>
 </alias>

 <alias>
 <family>sans-serif</family>
 <prefer>
 <family>DejaVu Sans</family>
 <family>MS Gothic</family>
 </prefer>
 </alias>

 <alias>
 <family>monospace</family>
 <prefer>
 <family>DejaVu Sans Mono</family>
 <family>MS Gothic</family>
 </prefer>
 </alias>

 <match target="font" >
 <edit mode="assign" name="embeddedbitmap" >
 <bool>true</bool>
 </edit>
 </match>
</fontconfig>
```
Now, if you have a ~/.fonts.conf file like that and you use the Serif virtual font, whenever you enter a character it will *first* try to display it using Times New Roman. If Times doesn't contain the font, it will fallback to the second font in the priority list; MS Mincho, which has a much greater chance of containing that character. As in the example on the first post in this thread, you're not limited to just one fallback font; you can have a long, long list. You might perhaps add Sazanami Mincho/Gothic below the MS/Kochi/Ricoh fonts just to get extra coverage.

Toy around with that ~/.fonts.conf file. Save it after having made changes, then open up a new application and observe effects. Just make sure you use Serif instead of Times directly.


edit: DejaVu Sans seems to only have partial unicode support, as it is missing a lot of very common kanji. So if you use DejaVu Sans with say, Mikachan as a fallback (ttf-mikachan from repos), you'll see that *some* CJK chars will be DejaVu, while others fallback to Mikachan. So in a way it's better to have one nice font with zero CJK char definitions, and one font with excellent unicode coverage, to get consistent display. (= all roman characters look alike, all CJK characters look alike)

---

### Post by Zorael on 2009-06-05
(Cut out from James Keating's post above)
```
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
```

As a small mention, this is basically how skim is set up per default, and it is *broken* in a KDE environment. Skim *needs* a XIM wrapper, and I don't understand why the powers at be decided it explicitly shouldn't get one. Ergo, the following makes no sense.
```
if [ -e /usr/bin/skim ]; then
    XIM_PROGRAM=" "
```
Just try using skim like that, then boot up xterm and hit your Anthy keybinds. Woe :<

I set mine up as detailed at [http://ubuntuforums.org/showthread.php?p=7166581](http://ubuntuforums.org/showthread.php?p=7166581), and while I can't say I've really tested Tk apps yet, everything else definitely works.

---

### Post by clementeb on 2009-06-05
Thank you very much for your kind and exhaustive reply.
I still have one question related to fonts. What is the name of the font I call nice? It is the one I used to get automatically from Times and Dejavu, but I don't know what its real name is and how many characters it covers (it's quite funny since I get very complicated fonts and not some of the easy ones and then if I write somewhere else or in some other combination I get it)
I also have another question, how do I add a dictionary to my Anthy dictionary, in the way MS ime could import from .txt and .dic? The default editor allows me to do just one word at a time, but I have to add 10000 (I'm doing classical studies, with a lot of strange words and readings)
Cheers

---

### Post by peacen1k on 2009-06-14
Ok!

Final question I hope....... I would like some help understanding the ~/.fonts.conf. file that I have created.

It states in an earlier post that I'm setting preferences for virtual fonts (serif, sans serif, and another one).

I've set this file up as suggested 8ut I don't like the default font &#12377;&#12390;&#12365;&#12376;&#12419;&#12394;&#12356;&#12392;&#24605;&#12358;!
Is this 8ecause I haven't done it right?

If I have done it right how do I edit the preferences so that it uses a font that I like 8etter first.

Any help appreciated;)

---

### Post by Zorael on 2009-06-14
> **peacen1k said:**
> Ok!

Final question I hope....... I would like some help understanding the ~/.fonts.conf. file that I have created.

It states in an earlier post that I'm setting preferences for virtual fonts (serif, sans serif, and another one).

I've set this file up as suggested 8ut I don't like the default font &#12377;&#12390;&#12365;&#12376;&#12419;&#12394;&#12356;&#12392;&#24605;&#12358;!
Is this 8ecause I haven't done it right?

If I have done it right how do I edit the preferences so that it uses a font that I like 8etter first.

Any help appreciated;)
Well, could you attach or paste the contents (in code tags) of your .fonts.conf here, then? And a screenshot of how it looks for you, if possible.

---

### Post by TokyoYank on 2009-08-07
Did I miss any instructions for 9.04 (Jaunty)?  

I tried following as much of the OP's instructions for 8.10 before running into trouble with the sources.list, even modifying it for jaunty.  It seems like everything I've tried does nothing:  no tray icon, nothing visible if SCIM is set to always visible..  adding Zorael's fix to obtain tomoe didn't help either.  :confused:

Perhaps related:  Anyone know a way to revert the scim configuration to it's initial/default settings?  (I assume removing the package and reinstalling might not clobber everything)

Thanks

---

### Post by TokyoYank on 2009-08-08
OK.. I'm happy:), but still confused :confused:

It works now.  I rebooted.  

Why would a reboot behave differently than logout/login?  ...  And while I'm at it, does SCIM not automatically restart when you close scim-setup, ie System > Preferences > SCIM  ? 

.. If someone knows how this all works, I'd be happy to type up a how-to or help.ubuntu page, for posterity

---

### Post by Zorael on 2009-08-09
**@TokyoYank**

You can't get tomoe in Jaunty even after having added that repository? What's your terminal output for the following commands? (Omit the dollarsign.)
```
$ grep -iRn japaneseteam /etc/apt/*
$ apt-cache policy scim-tomoe
```
Further, SCIM is an input method for X (**xinput**). The SCIM tray icon and panels you're interacting with are merely helpers; frontends; interfaces to the input method itself.

By default in Kubuntu (and likely Ubuntu as well), when logging out, X "regens"; it returns to the login screen after having closed down all apps (etc), but it's still the same X process as before. By extension, the same input method libraries are loaded as before. It's a neat way by design, as X doesn't have to close down entirely and restart bits it'll just reuse anyway. This includes xinput, so any changes to what input method you use won't apply when X soft-restarts this way.

So the real way to "restart X" is to either zap (by hitting the ctrl+alt+backspace shortcut, which is disabled by default in Jaunty and onwards), or to tell the gdm/kdm process to restart. Preferably after you've saved your work and shut down your apps. Even more preferably from a console (the ctrl+alt+f*n* kind).
```
$ sudo service gdm restart      # GNOME/Xfce/*
$ sudo service kdm restart      # KDE
```
It's possible to disable these faux restarts of X by manually modifying the gdm.conf/kdmrc files, but while easyish, it's a bit out of scope for what we're doing here. (Some Intel video controllers need it disabled though, else you just get a black screen when you log out. Off topic, pm me.)

If SCIM isn't reacting or isn't showing up, that suggests you don't have the xinput alternative set up properly (with the im-switch commands ryukent listed), or that the file they point to is malconfigured. In your case, I think you did everything right but merely logging out and back in wasn't enough to make the changes apply.


**@clementeb**

Figuring out which fonts are which is a royal pain, and I really haven't figured out a good way of doing it yet that doesn't involve a whole lot of trial and error with .fonts.conf and writing test sentences in OpenOffice in different fonts. If someone knows of a Firefox addon where you could select a bit of text and ask it "hey, what font is this?", do share.

The Anthy dictionary is in text form, so I guess it depends. If you find someone (perhaps in #ubuntu on irc.freenode.net) who knows a bit of sed or awk, you can perhaps get him/her to cook up a nice terminal command to parse your source file and write the lines to your Anthy personal dictionary.

The dictionary file itself is at **~/.anthy/private_words_default**. It seems to have three fields (well four), separated by a single space.
```
[COLOR="RoyalBlue"]<sound>[/COLOR]	 	 	 #[COLOR="SeaGreen"]WORDCLASS[/COLOR]*[COLOR="YellowGreen"]FREQUENCY[/COLOR]	 [COLOR="Orange"]<spelling>[/COLOR]
```
I'm confused by the "wordclass" and "frequency" fields, but I'm far from an expert on computer dictionaries.

As an example, here's my private_words_default with its amazing two entries. I'll add tabs to make it more legible. 
```
[COLOR="RoyalBlue"]&#12356;&#12360;&#12426;&#12400;&#12540;&#12428;[/COLOR]	 	 	#[COLOR="SeaGreen"]CN[/COLOR]*[COLOR="YellowGreen"]500[/COLOR]	 	 [COLOR="Orange"]&#12452;&#12456;&#12522;&#12496;&#12540;&#12524;[/COLOR]
[COLOR="RoyalBlue"]&#12395;&#12387;&#12385;&#12418;&#12373;&#12387;&#12385;&#12418;&#12356;&#12363;&#12394;&#12356;[/COLOR]	 	#[COLOR="SeaGreen"]CJ[/COLOR]*[COLOR="YellowGreen"]500[/COLOR]	 	 [COLOR="Orange"]&#20108;&#36914;&#12418;&#19977;&#36914;&#12418;&#34892;&#12363;&#12394;&#12356;[/COLOR]
```
So assuming your source dictionary (with the words you want to add) is a simple text file with just two fields, sound and spelling, it should be very possible to get a script to read those and add them to a new row in that Anthy dictionary file, with #[COLOR="SeaGreen"]CJ[/COLOR]*[COLOR="YellowGreen"]500[/COLOR] added inbetween them. Or #[COLOR="SeaGreen"]CN[/COLOR], or whatever's appropriate. Obviously if your source dictionary also has wordclasses, it'd still be possible to convert those into kasumi's/anthy's #[COLOR="SeaGreen"]WORDCLASS[/COLOR]*[COLOR="YellowGreen"]FREQUENCY[/COLOR] format.

Unless of course this is some form of international standard and you only need to copy your file to replace that dictionary file in **~/.anthy/** and be done with it. *shrug*

---

### Post by TokyoYank on 2009-08-11
Zorael, thanks for the help.  If a 9.04 how-to comes into being, I hope it'll include tomoe

Regarding restarting X:  I've used the Ctrl-Alt-Backspace in the past, though I'll admit I'd forgotten it, and I hadn't known it was disabled on Jaunty.  ... In terms of a SCIM how-to, is restarting X required, or just restarting persistent scim jobs?  (BTW, I hope it's normal to have two slightly different "scim-launcher -d" and two exactly similar "scim-helper-launcher --daemon" jobs)

Regarding tomoe:  Finally got it configured.  Looking back at the 8.10 how-to, copying handwriting-ja.xml to en (my locale), and clicking the SCIM panel for the config "Handwriting recognition", I now see the tomoe "drawing pencil" icon, the way I like. 

Regarding a jaunty how-to:  unless I'm on crack, the steps I followed to make all this happen were[LIST=1]
[*]System > Administration > Language Support > Install > Japanese ja > Install
[*]SupportedUnicodeLocales line in .scim/global per 8.10 howto OP
[*]added japaneseteam to apt and tomoe packages as per your instructions earlier in this thread
[*]cp /usr/share/tomoe/recognizer/handwriting-ja.xml to -en
[*]Ctrl-Space to initiate scim panel, find the config icon, click "handwriting recognition", toggle tomoe off
[/LIST]... but maybe I forgot a step or two?


BTW, I guess no troubleshooting is required, but since you asked:
```
$ sudo grep -iRn japaneseteam /etc/apt/*
[sudo] password for ##: 
/etc/apt/sources.list.d/japaneseteam.list:1:deb http://ppa.launchpad.net/japaneseteam/ppa/ubuntu jaunty main
/etc/apt/sources.list.d/japaneseteam.list:2:deb-src http://ppa.launchpad.net/japaneseteam/ppa/ubuntu jaunty main
##@##:~$ apt-cache policy scim-tomoe
scim-tomoe:
  Installed: 0.6.0-0ubuntu5
  Candidate: 0.6.0-0ubuntu5
  Version table:
 *** 0.6.0-0ubuntu5 0
        500 http://ppa.launchpad.net jaunty/main Packages
        100 /var/lib/dpkg/status
##@##:~$ aptitude search tomoe
p   libtomoe-dev       - handwriting recognition lib
p   libtomoe-gtk-dev   - class library for tomoe's G
i A libtomoe-gtk0      - class library for tomoe's G
i A libtomoe0          - handwriting recognition lib
i   scim-tomoe         - handwriting UI for SCIM    
i A tomoe-dic          - handwriting recognition lib
p   tomoe-doc          - handwriting recognition lib
i A tomoe-gtk-common   - class library for tomoe's G
i   tomoe-gtk-doc      - class library for tomoe's G
i A tomoe-gtk-l10n     - class library for tomoe's G
p   tomoe-l10n         - handwriting recognition lib

```

---

### Post by Zorael on 2009-08-11
Have you enabled scim as the xinput alternative? I'm not completely sure what is the default in Ubuntu, but it's certainly not the Kubuntu default. Regardless of what it is after installation, it needs enabling.

Copying from a few pages back;
[indent]Set SCIM as default input method via xinput.d _configuration file_: **skim** (located at **/etc/X11/xinit/xinput.d/skim**)
```
$ sudo im-switch -v -s **scim**
$ sudo im-switch -v -s **scim** -z *lang_CODE    # for other than current locale if needed, isn't if you're just using one locale since it defaults to current if not specified*
```
[list][*]Alternatively, an automated script to enable it for all locales which currently have an xinput "alternative" (generally translates to all installed locales + a few extras)
```
$ for X in $(ls /etc/alternatives/xinput*); do sudo update-alternatives --set $X /etc/X11/xinit/xinput.d/scim; done
```[/list][/indent]
Lastly, post the contents of that **/etc/X11/xinit/xinput.d/scim** file so we can make sure it's not incomplete.

---

### Post by TokyoYank on 2009-08-13
as far as I can recall, SCIM was here by default on Ubuntu. even with only the default locale.  ... Can anyone reading with a fresh install of Ubuntu 9.04 (or at least, a better memory than mine) confirm?

Zorael, I have not used Kubuntu so with your permission I will cut and paste your instructions for the skim configuration file.  ... it would be nice if we could double check that the how-to works for an official release of Kubuntu (as opposed to "testing" status release)



Since you asked;  this is Ubuntu 9.04 with updates:

```
$ more /etc/X11/xinit/xinput.d/scim
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
DEPENDS="scim,scim-anthy|scim-canna|scim-chewing|scim-pinyin|scim-hangle|scim-pr
ime|scim-skk|scim-tables-additional|scim-m17n|scim-uim|scim-tables-ja|scim-table
s-ko|scim-tables-zh"
```

---

### Post by Zorael on 2009-08-13
> **TokyoYank said:**
> ```
GTK_IM_MODULE=xim
QT_IM_MODULE=xim

```
I think you want those lines to say **scim**, or maybe **scim-bridge** if installed. It seems to be given preferential treatment.

Have you tried using this instead? It's not Skim-specific per se - it just has if clauses that check if scim-bridge is installed.
```
XIM=SCIM
XIM_PROGRAM=/usr/bin/scim
XIM_ARGS="-d"
XIM_PROGRAM_SETS_ITSELF_AS_DAEMON=yes

if [ -e /usr/lib/gtk-2.0/*/immodules/im-scim-bridge.so ]; then
    GTK_IM_MODULE=scim-bridge
elif [ -e /usr/lib/gtk-2.0/*/immodules/im-scim.so ]; then
    GTK_IM_MODULE=scim
else
    GTK_IM_MODULE=xim
fi
if [ -e /usr/lib/qt3/plugins/inputmethods/im-scim-bridge.so ] || [ -e /usr/lib/qt4/plugins/inputmethods/im-scim-bridge.so ]; then
    QT_IM_MODULE=scim-bridge
elif [ -e /usr/lib/qt3/plugins/inputmethods/libqscim.so ]; then
    QT_IM_MODULE=scim
else
    QT_IM_MODULE=xim
fi

DEPENDS="skim, scim-bridge-client-gtk | scim-bridge-client-qt | scim-bridge-client-qt4 | scim-gtk2-immodule | scim-qtimm"
```
As for Kubuntu, I believe I described the steps you'd need to take to get it working in KDE a few pages back. The only essential difference is that you can't rely on the GNOME language menus and whatnot to install the necessary packages, and you have to make sure to switch the input method to that skim file, which in turn you have to modify to make it work with XIM apps.

---

### Post by brookie on 2009-09-04
hello,

i had installed japanese language support and scim in intrepid for my wife. 

she could use the input editor from the task bar to type japanese.
 
i then found this how to and followed all the steps in hopes of improving her japanese input experience. 

i now see handwriting recognition available when i right click on scim in the panel applett and scim-tomoe will start. 

so...the big question is...
how does my wife use this handwriting recognition tool? 

also, when i look in synaptic package manager and search for scim-tomoe no package shows up, however, it was installed as in the how to. 

one more question...
are there any tips or tricks in the scim setup that could improve the way japanese sites look in firefox or any other settings that would improve how scim works/displays for her? 


cheers, 
brook

---

### Post by TokyoYank on 2009-09-04
> **brookie said:**
> hello,

i had installed japanese language support and scim in intrepid for my wife. 

she could use the input editor from the task bar to type japanese.
 
i then found this how to and followed all the steps in hopes of improving her japanese input experience. 

i now see handwriting recognition available when i right click on scim in the panel applett and scim-tomoe will start. 

so...the big question is...
how does my wife use this handwriting recognition tool? 
This has unfortunately become a very long thread.  I want to confirm before thinking about your questions:  were you using the How To on the first post?

About your big question..
To clarify, are you able to start the scim-tomoe window if you click on that option?  ...  Tomoe = a window where you can draw in kanji with your mouse clicks.  ...  Are you asking for instructions about how to use tomoe?

About your Synaptic issue:  if you downloaded the package manually then it will not appear in the repositories that Synaptic checks.  So if that's what you did, I wouldn't worry about it.  The specific answer here depends on which how-to you followed.  :)

---

### Post by YannBuntu on 2009-09-08
**@ryukent:** thanks again for your howto. Have you done a similar Howto for Ubuntu 9.04 ? :)

---

