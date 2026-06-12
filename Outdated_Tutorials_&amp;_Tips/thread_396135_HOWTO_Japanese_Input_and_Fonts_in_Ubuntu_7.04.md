---
title: "HOWTO: Japanese Input and Fonts in Ubuntu 7.04"
date: 2007-03-29
forum: Outdated Tutorials &amp; Tips
---

### Post by ryukent on 2007-03-29
**HOWTO: Installing Japanese that looks nice on Ubuntu 7.04 (Feisty): &#26085;&#26412;&#35486;**

Installing Japanese Input and Superior Font Setup in Ubuntu
Introduction

This is a guide to setting up Japanese for Ubuntu 7.04 Feisty. It is intended as a complete guide encompassing all elements required for using Japanese on any language installation of Ubuntu. It covers input (SCIM-Anthy) and configuring the Japanese fonts. There are other guides around for older versions of Ubuntu or that use the alternative UIM. They tend to cover elements only. This guide is intended to cover everything. Please note that Kubuntu requires slightly different steps. Please follow the relevant page accordingly. This is an updated version based on the original 6.10 one, but with some sections changed. Please note that if you follow this guide, your fonts will be reconfigured. This might mean losing some font settings you may have made.
Issues Involved

**There are two main issues here:**

1.Installing the SCIM input system that will work in a locale other than converting your whole install to Japanese, i.e. you want Japanese input in an English login.

2.The fonts look initially terrible. Therefore a certain amount of customisation is required to make all the Kanji's render in the same style and Hiragana & Katakana to render in a non-handwriting style.
Japanese Input with SCIM

This section covers setting up the Japanese input system using SCIM Anthy. This involves, downloading, installing and configuring it so that you can use it in non-Japanese locales (e.g. your system is in English).

**Setting Up Repositories**

First lets make sure you have the correct repositories installed in order to automatically download the relevant packs. Make sure you have the Universe and Multiverse repositories switched on. This can be done in 'Synaptic Package Manager' under the repositories tab. Also, you need the Japanese repository too. Open the repositories list file:

```
gksudo gedit /etc/apt/sources.list
```

Add the following line at the bottom:

```
deb http://archive.ubuntulinux.jp/ubuntu-ja feisty/
```

Now update your repos with:

```
sudo apt-get update
```

After adding the repository and running the update, you also need to add a keyring for the new location:

```
sudo apt-get install ubuntu-ja-keyring
```

**Adding Ubuntu Language Support**

Go to System / Administration / Language Support and select Japanese. This should install the basics.
[B]
Making SCIM available under a non-Japanese login[/B]

Now you want to make SCIM (Language input system) available in your English (or other lang) login and not just the Japanese one. First open the scim_startup file:
```

gksudo gedit /etc/X11/Xsession.d/74custom-scim_startup
```

Add these lines:
```

export XMODIFIERS="@im=SCIM"
export GTK_IM_MODULE="scim"
export XIM_PROGRAM="scim -d"
export QT_IM_MODULE="scim"
```

**Setting up the system to display Japanese characters properly**

OK, now you've got Japanese input installed (hopefully). It will probably require rebooting xwindows (CTRL+ALT+Backspace). But for me, I really couldn't cope with the horrible fonts that defaulted. Here's the next step.

Now that you have the Japanese repositories set up (see above), you'll want to get a nice set of fonts.
[B]
Downloading Repository Fonts[/B]

```
sudo apt-get install msttcorefonts ttf-dejavu ipafont ipamonafont ttf-arphic-ukai ttf-arphic-uming
```

This will install the Microsoft (Freeware) core fonts and a number of other useful fonts, specifically ones that support Japanese unicode characters.

**Downloading External Fonts**

Unfortunately, I am very disappointed in the Ubuntu selection and you will almost certainly want this to be changed to MSGothic and MSMincho. These are Microsoft fonts, but they are freely available to use and are actually from a company called Ricoh. They need to be downloaded and installed manually. They can be found at the following page.

[http://www.linux.ryukent.co.uk/show.php?id=24](http://www.linux.ryukent.co.uk/show.php?id=24)

So download and extract the files and you need to copy them into the fonts directory. This will need root privileges and is probably easiest done using the file explorer:

```
sudo nautilus --browser
```

That will give you a browser with the right privileges. So copy your downloaded ttf files and paste them into a folder under the fonts tree. I recommend:

```
/usr/share/fonts/truetype/msttcorefonts
```

**Rebuilding the font cache**

Now we need to rebuild the fonts cache:

```
sudo fc-cache -f -v
```
[B]
Setting up the font order[/B]

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
 <family>Times New Roman</family>
 <family>&#65325;&#65331; &#26126;&#26397;</family>
 <family>IPAPMincho</family>
 <family>Sazanami Mincho</family>
 <family>Kochi Mincho</family>
 <family>DejaVu Serif</family>
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
 <family>Verdana</family>
 <family>&#65325;&#65331; &#12468;&#12471;&#12483;&#12463;</family>
 <family>IPAPGothic</family>
 <family>Sazanami Gothic</family>
 <family>Kochi Gothic</family>
 <family>DejaVu Sans</family>
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
 <family>Courier New</family>
 <family>&#65325;&#65331; &#12468;&#12471;&#12483;&#12463;</family>
 <family>IPAGothic</family>
 <family>Sazanami Gothic</family>
 <family>Kochi Gothic</family>
 <family>DejaVu Sans Mono</family>
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
 <bool>false</bool>
 </edit>
 </match>
 <match target="font" >
 <edit mode="assign" name="autohint" >
 <bool>true</bool>
 </edit>
 </match>
</fontconfig>

```

So, save the file and reboot xwindows (CTLR+ALT+Backspace). Now with any luck the order of fonts should have been updated so that the default Japanese type face is actually a clean one first and foremost instead of the ugly first serving. Also it disables the built in bitmap font which can really make kanji's look odd next to anti aliased hiragana etc. For most people this setting will be fine. If you're not happy, by all means leave out the embeddedbitmap setting.

If you're still having problems consider the following:
[B]
Java[/B]

If you are having problems inputting Japanese into some application only (especially Java ones) you might need to update the SCIM settings for the root user too. This can be done by replacing the existing config file in /root/.scim with one from your home directory that you have already set up correctly. Of course you will need root privileges to do that.
[B]
QT[/B]

If you are having problems loading programs that use QT (like skype), try changing your QT_IM_MODULE environment variable to xim (see above).

```
export QT_IM_MODULE=xim
```

---

### Post by mhenriday on 2007-04-10
> **ryukent said:**
> **HOWTO: Installing Japanese that looks nice on Ubuntu 7.04 (Feisty): &#26085;&#26412;&#35486;**...

If you are having problems loading programs that use QT (like skype), try changing your QT_IM_MODULE environment variable to xim (see above).

```
export QT_IM_MODULE=xim
```

Hullo **ryukent** - long time no see ! The question I pose here may seem a little off topic, as it does not deal with fonts and I'm still using **Edgy** (I had some uiid problems and couldn't get the beta version of **Feisty** to work, so I'm waiting for the release on the 19th before upgrading), but since at the very end of your posting you do touch upon the matter which concerns me, I thought it might be OK to address it here. Ever since going over to **Ubuntu** last December, I've had problems with **Skype** - it is only recently that, thanks to another poster, I discovered that my problems had to do with the QT module. Following his advice, I found I was able to gain access to **Skype**, despite having **SCIM** - on which I am absolutely dependent - installed ; the solution I employ is to write the command ```
XMODIFIERS=@im=none QT_IM_MODULE=xim skype
``` in a terminal, after which **Skype** starts without difficulty. BUT, there does remain one problem - I cannot use **SCIM** to type Chinese or Japanese text into a Skype chat message. Even if, for example, I have **SCIM** set to **Anthy**, I can't write the phrase «&#26085;&#26412;&#35486;» in the message ; what I get instead is the equivalent in Latin letters, i e, «nihongo». The same is true, *mutatis mutandi*, of Chinese phrases. My question : if I follow your advice and opening the scim_startup file with :
```
gksudo gedit /etc/X11/Xsession.d/74custom-scim_startup
```
and then add these lines:```
export XMODIFIERS="@im=SCIM"
export GTK_IM_MODULE="scim"
export XIM_PROGRAM="scim -d"
export QT_IM_MODULE="scim"
``` but change the last line to
```
export QT_IM_MODULE=xim
``` instead, what are the chances of obtaining not only access _to_ **Skype**, but also to **SCIM** (i e, CJK languages) _in_ **Skype** ?...

Thanks in advance,

Henri

PS : I presume that these techniques will work as well in **Edgy** as in **Feisty** - or should I wait until after I upgrade ?...

---

### Post by ryukent on 2007-04-10
Hmm.... I would imagine your chances are very slim.&#12288;The fact is, there is a bug in Skype that doesn't like SCIM. This is for the Skype people to fix, but there haven't been any new releases of the linux version for some time and it's not open source. When you change the QT environment variable to XIM, it defaults to standard input for all QT widgets which Skype uses, so with the current offering, you'll only get western characters.

I did once manage to get SCIM working properly through XIM (which it does in other flavours of Linux). Alas it will no longer. Because it works fine in GTK and QT applications which make up most of apps out there, I think people have simply forgotten about XIM support. Pure X apps (like xterm or Java) still don't have SCIM support in Ubuntu. I have spent hours trying to fix this, but have got nowhere. 

You could try using UIM. It does have much better XIM support.... however, I'm currently experiencing severe issues using it with QT applications of which Skype is one. There seems to be a clear solution and that is for the SCIM people to fix XIM support in Ubuntu and for the Skype people to fix Skype to work with SCIM. I'd love to help but am not part of either, so until then all I can say is good luck and please let me know if you find a solution!

---

### Post by mhenriday on 2007-04-11
**Ryukent**, I've checked out your messages to the **SCIM** user forum, and while you don't mention **Skype** explicitly, I presume (please correct me if I am in error) the problem is subsumed under the more general question of **SCIM** in **Java** using **Ubuntu** that you there take up. We shall just have to see if there come any more responses ; for my part, I found it encouraging that James Su (&#33487;&#21746;) himself was the first to respond, even if his suggestion didn't resolve the problem....

As you have covered the **SCIM** end of the problem, I have taken it upon myself to write to **Skype** ; here below a copy of my letter :
[INDENT]The OS I presently use is Ubuntu Edgy (6.10), with Skype installed via Automatix 2. I have also installed the SCIM input system for, among others, CJK texts, which I use both for work and leisure. Installing SCIM, however, led to Skype becoming unavailable to me, a condition which lasted several months until I finally discovered that by typing in the command «XMODIFIERS=@im=none QT_IM_MODULE=xim skype» in my terminal, Skype could be accessed. A problem still remains, however ; from my keyboard I can only input text written in Latin letters into a Skype chat message ; I have found it impossible to write in texts in Chinese or Japanese. I know that this is not a problem for other OS, thus my daughter, who uses a MAC, has no difficulty writing in Japanese to me directly from her keyboard. I, however, am forced to use such subteruges as first writing a CJK text in a notepad and then pasting it into my chat message, which tends to destroy the spontaneity that constitutes the major part of chatting's charm. My query - does Skype have any intention of resolving this difficulty, so that even we Ubuntu users who employ SCIM can use the latter to write CJK texts into Skype chat messages ?...[/INDENT]
Let us see if somebody, inspired by this problem, comes up with a solution !...

Henri

---

### Post by kaminix on 2007-05-01
Any idea how I change it from SCIM to SKIM, the KDE intecface?

EDIT:
btw, with the new fonts I can't see the char meaning ^6 nor half of the chinese chars I use (used mainly for aesthetic purposes), while with the old ones I couldn't see a few of the japanese chars (used for both aesthetic and studying). Any idea how to fix?

---

### Post by HokkaidoHillbilly on 2007-05-02
Ok, here's one that's a stumper to me...

I run Japanese Feisty and in certain Java apps, i.e. Google Talk, etc, I can use scim/anthy and not only switch back & forth from alphabet to Japanese, but view it as well.  On the other hand, on certain Java heavy pages such as [http://weathernews.jp/](http://weathernews.jp/), a lot of the Java-ized text shows up as &#25991;&#23383;&#21270;&#12369;, no mater what kind of encoding I have the page set to (i.e. according to the source page, it's Shift-JIS, but even w/ Shift-JIS encoding, no dice).

Any idea how I can get pages like this to display correctly?

Thanks & &#12393;&#12358;&#12418;&#65281;

HH ;)

---

### Post by doncristobal on 2007-05-04
I have xubuntu 7.04 with scim 1.4.4-7ubuntu1, and for me, the problem is _almost_ solved: 

i can use scim (with all the french and spanish accents, with greek &#949;&#955;&#955;&#951;&#957;&#953;&#954;&#940; and with korean &#54620;&#44544;) if i do the following: 

1. either i open a terminal and type "GTK_IM_MODULE=xim" in order to set that environment variable to the proper value (following the advice on [http://www.nabble.com/How-do-I-enable-scim-internationalize-java-gnome-gui%27s--tf2569312.html#a7162103](http://www.nabble.com/How-do-I-enable-scim-internationalize-java-gnome-gui%27s--tf2569312.html#a7162103))
or 
i add "GTK_IM_MODULE=xim" to ~/.bashrc and reboot. 

2. i open skype _from the terminal_. it does not work from the xfce applications menu, nor from a self-made shortcut button (even if i activate the "run in a terminal" option), nor if it is run at startup as part of the saved xfce session. 

so i always have to open skype manually, and then there is a blocked terminal window, making my desktop even messier :-( 

any hint on how to solve this last little problem? thank you very much!

---

### Post by trowa_zero on 2007-05-07
I run feisty amd 64 and I have no problem running SCIM on my 64 bit version of firefox, but swiftfox (the 32 bit version with plugin's like flash that actually work) will not allow me to use Japanese input.  Any idea how to fix this?

---

### Post by ubuntu27 on 2007-05-09
@ryukent:: Good job on your how-to!! :)

I just wanted to tell you that you will have to add another repo if you want some special Japanese application like Ch2 Browser. 

```
deb http://archive.ubuntulinux.jp/ubuntu-ja feisty/
```

```
deb http://archive.ubuntulinux.jp/ubuntu-ja feisty-ja/
```


Source Page:

[http://www.ubuntulinux.jp/download/index_html#JA_Repository](http://www.ubuntulinux.jp/download/index_html#JA_Repository)

That is all.

Thank you!! :D

---

### Post by LordOfThePigs on 2007-05-22
Are there any similar guides that would allow me to get skim (or at least scim) to work properly for simplified chinese input under an english locale? I couldn't find any, and after hours of fiddling, I just could never get it to run. The best I could do is get it to start, use it or 2 or 3 minutes, and then crash... I can't remember how I did that though...

---

### Post by takayuki on 2007-05-26
Hi,

I've just followed the steps here and I can read Japanese but

i don't have Japanese input support.

i do have scim installed...  but i don't have the switcher applet like i had in dapper.

any thoughts?

takayuki

---

### Post by takayuki on 2007-05-26
ok, i'm a dummy.

after installing everything...

to get scim / anthy japanese input.  press shift + space on the keyboard to activate anthy.  works great!

 &#12391;&#12365;&#12414;&#12375;&#12383;&#65281;

---

### Post by mhenriday on 2007-05-28
**Ryukent**, when I attempt to update, whether via the terminal, using ```
sudo apt-get update
``` or via **System&#8594;Administration&#8594;Update Manager**, I always get a message of the following type : > W: GPG error: [http://archive.ubuntulinux.jp](http://archive.ubuntulinux.jp) feisty/ Release: Följande signaturer kunde inte verifieras för att den publika nyckeln inte är tillgänglig: NO_PUBKEY 058A05E90C4ECFECdespite the fact that I have «deb [http://archive.ubuntulinux.jp/ubuntu-ja](http://archive.ubuntulinux.jp/ubuntu-ja) feisty/» saved in my repository. I haven't noticed any problems as a result of this fact - I have no difficulty, for example, in using **SCIM** to input Japanese text from keyboard in say, **Anthy**, but find it irritating not to know what is going on. How can I obtain the public key and/or do whatever else is necessary to correct this problem ?...

Henri

---

### Post by ubuntu27 on 2007-05-28
> **mhenriday said:**
> **Ryukent**, when I attempt to update, whether via the terminal, using ```
sudo apt-get update
``` or via **System&#8594;Administration&#8594;Update Manager**, I always get a message of the following type : (the key number changes, of course, every time I attempt to verify), despite the fact that I have «deb [http://archive.ubuntulinux.jp/ubuntu-ja](http://archive.ubuntulinux.jp/ubuntu-ja) feisty/» saved in my repository. I haven't noticed any problems as a result of this fact - I have no difficulty, for example, in using **SCIM** to input Japanese text from keyboard in say, **Anthy**, but find it irritating not to know what is going on. How can I obtain the public key and/or do whatever else is necessary to correct this problem ?...

Henri

Seems like it dosn't have the Ubuntu Japan's digital signature 

Try:
```
sudo apt-get update
``` ignore the message that you get.

and then do a:

```
sudo apt-get install ubuntu-ja-keyring
``` 
IGNORE The warning.

Now that message should not appear anymore.

---

### Post by mhenriday on 2007-05-28
Thanks, **ubuntu27** ! I followed your advice, save after performing ```
sudo apt-get install ubuntu-ja-keyring
```instead of ignoring the warning to the effect that the keyring package could not be verified, I replied in the affirmative to the query whether I wanted to install it anyway, which **Feisty** then proceeded to do. Checking after installation, I find I no longer get that irritating message about the missing digital signature - Halleluja ! But what exactly is «keyring» and what does it do - can you tell me in a few words or point me to a tutorial ?...

Henri

---

### Post by Stambo00 on 2007-06-14
I followed all your directions correctly.

Unfortunately OpenOffice no longer works. I now get this following error message:


snppls@snppls-desktop:~$ ooffice -writer
*** glibc detected *** /usr/lib/openoffice/program/soffice.bin: free(): invalid pointer: 0x080d06b0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb6c8d7cd]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb6c90e30]
/usr/lib/openoffice/program/libuno_sal.so.3(rtl_freeMemory+0x1d)[0xb72e60bd]
/usr/lib/openoffice/program/soffice.bin[0x809192e]
/usr/lib/openoffice/program/soffice.bin(_ZdlPv+0x26)[0x8091966]
/usr/lib/libscim-1.0.so.8[0xa97b4156]
/usr/lib/libscim-1.0.so.8(_ZN4scim20scim_get_module_listERSt6vectorISsSaISsEERKSs+0x37)[0xa97b4f77]
/usr/lib/libscim-1.0.so.8(_ZN4scim29scim_get_imengine_module_listERSt6vectorISsSaISsEE+0x45)[0xa97aff05]
/usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so[0xa9856f7b]
/usr/lib/libgobject-2.0.so.0(g_type_class_ref+0x381)[0xb5c96b41]
/usr/lib/libgobject-2.0.so.0(g_object_newv+0xa2f)[0xb5c7d1cf]
/usr/lib/libgobject-2.0.so.0(g_object_new_valist+0x21f)[0xb5c7d5ef]
/usr/lib/libgobject-2.0.so.0(g_object_new+0x40)[0xb5c7d7a0]
/usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so(_Z23gtk_im_context_scim_newv+0x67)[0xa984bb57]
/usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so(im_module_create+0x3c)[0xa985b27c]
/usr/lib/libgtk-x11-2.0.so.0(_gtk_im_module_create+0xb9)[0xb5772d29]
/usr/lib/libgtk-x11-2.0.so.0[0xb577393b]
/usr/lib/libgtk-x11-2.0.so.0[0xb5773b39]
/usr/lib/libgtk-x11-2.0.so.0(gtk_im_context_set_client_window+0x4e)[0xb5770f0e]
/usr/lib/libgtk-x11-2.0.so.0[0xb571a71f]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x49)[0xb5c849d9]
/usr/lib/libgobject-2.0.so.0[0xb5c75e49]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x12b)[0xb5c7762b]
/usr/lib/libgobject-2.0.so.0[0xb5c8859a]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x8c7)[0xb5c89627]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb5c897e9]
/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_realize+0xba)[0xb58aebea]
/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_set_parent+0x1de)[0xb58af1ce]
/usr/lib/libgtk-x11-2.0.so.0(gtk_fixed_put+0xd3)[0xb5747ec3]
/usr/lib/libgtk-x11-2.0.so.0[0xb5747f08]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__OBJECT+0x59)[0xb5c83ee9]
/usr/lib/libgobject-2.0.so.0[0xb5c75e49]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x12b)[0xb5c7762b]
/usr/lib/libgobject-2.0.so.0[0xb5c8859a]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x8c7)[0xb5c89627]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb5c897e9]
/usr/lib/libgtk-x11-2.0.so.0(gtk_container_add+0x12c)[0xb56fe1bc]
/usr/lib/openoffice/program/libvclplug_gtk680li.so[0xb59e22bd]
/usr/lib/openoffice/program/libvclplug_gtk680li.so[0xb59e4043]
/usr/lib/openoffice/program/libvclplug_gtk680li.so[0xb59eeabd]
/usr/lib/openoffice/program/libvcl680li.so[0xb7e41ff5]
/usr/lib/openoffice/program/libvcl680li.so[0xb7dcf09b]
/usr/lib/openoffice/program/libvcl680li.so(_ZN11ModalDialogC2EP6WindowRK5ResId+0x67)[0xb7dcfac7]
/usr/lib/openoffice/program/libsvt680li.so(_ZN12WizardDialogC2EP6WindowRK5ResIdhs+0x3e)[0xb789c99e]
/usr/lib/openoffice/program/libsvt680li.so(_ZN3svt14OWizardMachineC2EP6WindowRK5ResIdmhhs+0x4a)[0xb786e1da]
/usr/lib/openoffice/program/libsvt680li.so(_ZN3svt13RoadmapWizardC2EP6WindowRK5ResIdmS5_h+0x4f)[0xb786b55f]
/usr/lib/openoffice/program/libspl680li.so[0xa9958926]
/usr/lib/openoffice/program/libspl680li.so[0xa994f024]
/usr/lib/openoffice/program/soffice.bin(_ZN7desktop7Desktop4MainEv+0xd59)[0x806bc39]
/usr/lib/openoffice/program/libvcl680li.so[0xb7c4fc3c]
/usr/lib/openoffice/program/libvcl680li.so(_Z6SVMainv+0x35)[0xb7c4fd45]
/usr/lib/openoffice/program/soffice.bin(main+0x65)[0x805ff85]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb6c3bebc]
/usr/lib/openoffice/program/soffice.bin(__gxx_personality_v0+0x249)[0x805fe11]
======= Memory map: ========
08048000-0809c000 r-xp 00000000 08:02 4080140    /usr/lib/openoffice/program/soffice.bin
0809c000-0809e000 rw-p 00053000 08:02 4080140    /usr/lib/openoffice/program/soffice.bin
0809e000-08366000 rw-p 0809e000 00:00 0          [heap]
a9600000-a9621000 rw-p a9600000 00:00 0 
a9621000-a9700000 ---p a9621000 00:00 0 
a974c000-a9820000 r-xp 00000000 08:02 3999618    /usr/lib/libscim-1.0.so.8.1.0
a9820000-a982e000 rw-p 000d4000 08:02 3999618    /usr/lib/libscim-1.0.so.8.1.0
a983f000-a9860000 r-xp 00000000 08:02 4047224    /usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so
a9860000-a9861000 rw-p 00021000 08:02 4047224    /usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so
a9861000-a98c1000 rw-s 00000000 00:08 7536676    /SYSV00000000 (deleted)
a98c1000-a98d1000 r-xp 00000000 08:02 4079933    /usr/lib/openoffice/program/libfileacc.so
a98d1000-a98d2000 rw-p 00010000 08:02 4079933    /usr/lib/openoffice/program/libfileacc.so
a98d2000-a992f000 r-xp 00000000 08:02 4079990    /usr/lib/openoffice/program/libpackage2.so
a992f000-a9932000 rw-p 0005d000 08:02 4079990    /usr/lib/openoffice/program/libpackage2.so
a9932000-a993d000 r-xp 00000000 08:02 4047206    /usr/lib/gtk-2.0/2.10.0/engines/libindustrial.so
a993d000-a993e000 rw-p 0000b000 08:02 4047206    /usr/lib/gtk-2.0/2.10.0/engines/libindustrial.so
a993e000-a9970000 r-xp 00000000 08:02 4080028    /usr/lib/openoffice/program/libspl680li.so
a9970000-a9972000 rw-p 00032000 08:02 4080028    /usr/lib/openoffice/program/libspl680li.so
a9972000-a99b2000 rw-p a9972000 00:00 0 
a99b2000-a99c0000 r-xp 00000000 08:02 4079943    /usr/lib/openoffice/program/libgcc3_uno.so
a99c0000-a99c1000 rw-p 0000e000 08:02 4079943    /usr/lib/openoffice/program/libgcc3_uno.so
a99c1000-a9ca5000 r-xp 00000000 08:02 4079940    /usr/lib/openoffice/program/libfwk680li.so
a9ca5000-a9cb5000 rw-p 002e3000 08:02 4079940    /usr/lib/openoffice/program/libfwk680li.so
a9cb5000-a9cb6000 rw-p a9cb5000 00:00 0 
a9cb6000-a9d51000 r-xp 00000000 08:02 4080069    /usr/lib/openoffice/program/libxcr680li.so
a9d51000-a9d56000 rw-p 0009a000 08:02 4080069    /usr/lib/openoffice/program/libxcr680li.so
a9d56000-a9eb9000 r-xp 00000000 08:02 4080008    /usr/lib/openoffice/program/libsb680li.so
a9eb9000-a9eca000 rw-p 00163000 08:02 4080008    /usr/lib/openoffice/program/libsb680li.so
a9eca000-a9ecb000 rw-p a9eca000 00:00 0 
a9ecb000-a9f65000 r-xp 00000000 08:02 4079938    /usr/lib/openoffice/program/libfwe680li.so
a9f65000-a9f69000 rw-p 0009a000 08:02 4079938    /usr/lib/openoffice/program/libfwe680li.so
a9f69000-aa313000 r-xp 00000000 08:02 4080021    /usr/lib/openoffice/program/libsfx680li.so
aa313000-aa32c000 rw-p 003a9000 08:02 4080021    /usr/lib/openoffice/program/libsfx680li.so
aa32c000-aa32d000 rw-p aa32c000 00:00 0 
aa32d000-aa388000 r-xp 00000000 08:02 4080050    /usr/lib/openoffice/program/libucpfile1.so
aa388000-aa38b000 rw-p 0005a000 08:02 4080050    /usr/lib/open
** (process:11538): WARNING **: Unknown error forking main binary / abnormal early exit ...

---

### Post by beetlejuice321 on 2007-07-03
Stambo00, I got the exact same error opening OpenOffice!  Its now broke!

Also setting up your default fonts states, do a "gksudo gedit ~/.fonts.conf" to edit your font's folder, but this hidden folder/file does not exist in my user account.

Also the guide says...
Add these lines into your "/etc/X11/Xsession.d/74custom-scim_startup"

export XMODIFIERS="@im=SCIM"
export GTK_IM_MODULE="scim"
export XIM_PROGRAM="scim -d"
export QT_IM_MODULE="scim"

except I also can't find the file called 75custom-scm_startup.  And I have cnofirmed I have SCIM installed and it appears to be working perfectly.  So I don't get this step.

Basically all I want is to get my OpenOffice working again (preferrably with &#26085;&#26412;&#35486; support, and I would like to get my fonts setup correctly.  But can't I just do that through System > Preferences > Font ???  Or is that not the same thing?

---

### Post by kaminix on 2007-07-08
How do I make the font changes global?

---

### Post by HokkaidoHillbilly on 2007-07-11
Never did figure out how to view Japanese on Java heavy sites like I mentioned above earlier (i.e. weathernews.jp), but here's a new issue that I've run into if anybody's feeling generous ;)

While it never seems to happen in a non-web based app, i.e. Open Office, etc, occasionally Anthy seems to just go haywire...especially when writing Japanese in Gmail or doing Google searches.

By "haywire", I mean that I'll press the &#21322;&#35282;&#12539;&#20840;&#35282; button to enable Anthy romaji entry, but then about 75% of the time, whenever I press the space bar to convert the kana into kanji, whatever I type just disappears.  Poof...like it was never there.  If I reboot the computer, Japanese entry plays nice for a while, but normally within a few hours or so the problem pops back up.

Anybody else ever run into this problem?  If it helps any, I'm running an English log-on Feisty / Japanese Win XP Pro dual-boot on a Dell XPS M1210 w/ a 2GHz dual core CPU, 2GB of RAM and a Japanese 106 keyboard.

Thanks!



HH ;)

---

### Post by Gorgo13 on 2007-10-08
Hi There,

I cannot have japanese input work under Gutsy Gibbon. I followed the instructions from these pages:

[http://doc.ubuntu-fr.org/uim-anthy](http://doc.ubuntu-fr.org/uim-anthy)

[https://help.ubuntu.com/community/JapaneseInput](https://help.ubuntu.com/community/JapaneseInput)

[http://ubuntuforums.org/archive/index.php/t-312525.html](http://ubuntuforums.org/archive/index.php/t-312525.html)

Nothing happens when I try to switch the input. I tried to configure the switch keys to SHIFT+Space, then "zenkaku-hankaku" (which I have on my japanese laptop keyboard).

Any ideas?

:confused:

---

### Post by mhenriday on 2007-10-08
**Gorgo13**, do you have **scim** installed ? If not, follow the [[COLOR="Blue"]community docs directions[/COLOR]]("https://help.ubuntu.com/community/SCIM"), which, even if they're meant for **Feisty**, should work in **Gutsy** as well....

Henri

---

### Post by kaminix on 2007-10-20
Hello, I'm a little unorthodox sitting on **K**ubuntu 7.10 instead of Ubuntu 7.04, but I hope someone'll be able to help me anyway.

After some work with ~/.scim/global and im-switch I've succesfully got Scim/Skim with anthy set up and able to write Japanese etc etc, but it's bugging the hell out of me. Here are some of the bugs I encounter:
* Usually not being able to go back on a line and type. If I go back and type the cursor will move to the front of the line as soon as I start hitting the letter keys.
* Sometimes some stuff will produce output such as: "s&#12375;tt&#12387;t&#12390;l&#12355;&#12354;&#12358;t&#12392;p&#12401;"l&#12387;t&#12392;" if you understand how I mean?
* Sometimes my entry disappears when I hit space and try searching for kanjis.

Here are some of my configs which might be of interest:
**alex@minipax:~$ cat ~/.scim/global**
/DefaultConfigModule = kconfig
/DefaultKeyboardLayout = Swedish
/DefaultPanelProgram = /usr/bin/scim-panel-kde
/DisabledIMEngineFactories = c6bebc27-6324-4b77-8ad4-6d41dcaf2e08,6e029d75-ef65-42a8-848e-332e63d70f9c
/SupportedUnicodeLocales = en_GB.UTF-8

**alex@minipax:~$ cat /etc/scim/global**
/SupportedUnicodeLocales = en_US.UTF-8
/DefaultPanelProgram = scim-panel-gtk
/DefaultConfigModule = simple
/DefaultSocketFrontEndAddress = local:/tmp/scim-socket-frontend
/DefaultSocketIMEngineAddress = local:/tmp/scim-socket-frontend
/DefaultSocketConfigAddress = local:/tmp/scim-socket-frontend
/DefaultPanelSocketAddress = local:/tmp/scim-panel-socket
/DefaultHelperManagerSocketAddress = local:/tmp/scim-helper-manager-socket
/DefaultSocketTimeout = 5000

**alex@minipax:~$ im-switch -l**
Your input method setup under en_GB locale as below.
=======================================================
The configuration "/home/alex/.xinput.d/en_GB" is defined as a link pointing to
scim
This private configuration supersedes the system wide default.
=======================================================
The system wide default is pointed by "/etc/alternatives/xinput-all_ALL" .
xinput-all_ALL - status is manual.
 link currently points to scim
default - priority 10
none - priority 0
scim - priority 0
scim-immodule - priority 0
Current `best' version is default.
=======================================================
The available input method configuration files are:
default none scim scim-immodule th-xim
=======================================================

**alex@minipax:~$ locale**
LANG=en_GB.UTF-8
LANGUAGE=en_GB:en
LC_CTYPE="en_GB.UTF-8"
LC_NUMERIC="en_GB.UTF-8"
LC_TIME="en_GB.UTF-8"
LC_COLLATE="en_GB.UTF-8"
LC_MONETARY="en_GB.UTF-8"
LC_MESSAGES="en_GB.UTF-8"
LC_PAPER="en_GB.UTF-8"
LC_NAME="en_GB.UTF-8"
LC_ADDRESS="en_GB.UTF-8"
LC_TELEPHONE="en_GB.UTF-8"
LC_MEASUREMENT="en_GB.UTF-8"
LC_IDENTIFICATION="en_GB.UTF-8"
LC_ALL=

**alex@minipax:~$ cat /etc/scim/config**
# This file is encoded in UTF-8 encoding.
/FrontEnd/OnTheSpot = true
/FrontEnd/SharedInputMethod = true
/FrontEnd/ChangeFactoryGlobally = false
/FrontEnd/Socket/ConfigReadOnly = false
/FrontEnd/Socket/MaxClients = 512
/FrontEnd/X11/BrokenWchar = true
/FrontEnd/X11/Dynamic = false
/FrontEnd/X11/OnTheSpot = true
/FrontEnd/X11/ServerName = SCIM
/Hotkeys/FrontEnd/NextFactory = Control+Alt+Down,Shift+Control+KeyRelease+Shift_L,Shift+Control+KeyRelease+Shift_R
/Hotkeys/FrontEnd/PreviousFactory = Control+Alt+Up,Shift+Control+KeyRelease+Control_L,Shift+Control+KeyRelease+Control_R
/Hotkeys/FrontEnd/ShowFactoryMenu = Control+Alt+Right
/Hotkeys/FrontEnd/Trigger = Control+space,Shift+space,Zenkaku_Hankaku,Hangul
/Hotkeys/FrontEnd/ValidKeyMask = Shift+Control+Alt+CapsLock+Meta+QuirkKanaRo
/Panel/Gtk/Color/ActiveBackground = light sky blue
/Panel/Gtk/Color/ActiveText = black
/Panel/Gtk/Color/NormalBackground = #F7F3F7
/Panel/Gtk/Color/NormalText = black
/Panel/Gtk/Font = default
/Panel/Gtk/DefaultSticked = false
/Panel/Gtk/LookupTableEmbedded = true
/Panel/Gtk/LookupTableVertical = false
/Panel/Gtk/ShowStatusBox = false
/Panel/Gtk/ShowTrayIcon = true
/Panel/Gtk/ToolBar/AlwaysShow = false
/Panel/Gtk/ToolBar/AutoSnap = true
/Panel/Gtk/ToolBar/HideTimeout = 2
/Panel/Gtk/ToolBar/POS_X = -1
/Panel/Gtk/ToolBar/POS_Y = -1
/Panel/Gtk/ToolBar/ShowHelpIcon = true
/Panel/Gtk/ToolBar/ShowFactoryIcon = true
/Panel/Gtk/ToolBar/ShowFactoryName = true
/Panel/Gtk/ToolBar/ShowMenuIcon = true
/Panel/Gtk/ToolBar/ShowSetupIcon = true
/Panel/Gtk/ToolBar/ShowStickIcon = false
/IMEngine/RawCode/Locales = default


Sorry for long post, really want this solved!

---

### Post by paulvbrown on 2008-05-16
> **beetlejuice321 said:**
> 
Also setting up your default fonts states, do a "gksudo gedit ~/.fonts.conf" to edit your font's folder, but this hidden folder/file does not exist in my user account.

Basically all I want .... and I would like to get my fonts setup correctly.  But can't I just do that through System > Preferences > Font ???  Or is that not the same thing?

SHORT VERSION: How to get fonts set up???

LONGER VERSION:

Alright, yeah, ancient post to be replying to, but I have the same problem.  Have been trying off and on over the past 3 months to get Japanese input working.  Kept running into problems where input wasn't working like on DESKTOP items or in Eclipse (a Java app, ultimately).  Finally seem to have got that fixed just by following the instructions: copy your home directory .scim/config to /root/.scim/

BUT, yeah, I have at least this problem in common with BeetleJuice still -- my current Japanese font SUCKS big time, and I seem to be missing the .fonts.conf file completely, so am finding it somewhat difficult to edit it properly =o)  I *think* at some point I tried just creating one, but it didn't help.  I may be wrong about that though.

So: how do I get the fonts set up correctly?  I've downloaded the ones suggested in this guide, but now need to comprehend how to tell the system to USE them.

THANKS in advance!!!!

---

### Post by ubuntu27 on 2008-05-16
> **paulvbrown said:**
> SHORT VERSION: How to get fonts set up???

LONGER VERSION:

Alright, yeah, ancient post to be replying to, but I have the same problem.  Have been trying off and on over the past 3 months to get Japanese input working.  Kept running into problems where input wasn't working like on DESKTOP items or in Eclipse (a Java app, ultimately).  Finally seem to have got that fixed just by following the instructions: copy your home directory .scim/config to /root/.scim/

BUT, yeah, I have at least this problem in common with BeetleJuice still -- my current Japanese font SUCKS big time, and I seem to be missing the .fonts.conf file completely, so am finding it somewhat difficult to edit it properly =o)  I *think* at some point I tried just creating one, but it didn't help.  I may be wrong about that though.

So: how do I get the fonts set up correctly?  I've downloaded the ones suggested in this guide, but now need to comprehend how to tell the system to USE them.

THANKS in advance!!!!

Did you read [this thread]("http://ubuntuforums.org/showthread.php?t=684469")? This thread where you have posted is for two versions old of Ubuntu. 

Go to this one which is newer compared to this one. 

[http://ubuntuforums.org/showthread.php?t=684469](http://ubuntuforums.org/showthread.php?t=684469)

It is still old (from previous version), but newer nonethless.

---

### Post by paulvbrown on 2008-05-20
> **ubuntu27 said:**
> Did you read [this thread]("http://ubuntuforums.org/showthread.php?t=684469")? This thread where you have posted is for two versions old of Ubuntu. 


Yeah, totally aware of how old a version of Ubuntu I'm using -- I'm still with Feisty, so am trying to follow the Feisty instructions.

I would say that perhaps the answer to MANY of my questions about these instructions is this:

YES! BEETLEJUICE is absolutely right -- there *IS* no .fonts.conf file.  Also, there *IS* no "/etc/X11/Xsession.d/74custom-scim_startup" file either.

I have the same hang-up as Beetlejuice -- the way the instructions are written, it SEEMS (to the two of us anyway) that these files should exist, and we're just editing them.  Assuming I *now* understand correctly, NO, that's not the case.  In fact we CREATE these files on our own.

So far (knock on wood), ever since I finally just went ahead and CREATED the 74custom-scim_startup (and the fonts file), I haven't been having the wacko errors I was having.

Thanks!!!

---

### Post by Zorael on 2008-05-27
I'm running Kubuntu 8.04 and after tweaking fonts as suggested in this thread I now have Japanese input (through skim and scim-anthy) in Gtk/Qt programs. All is (almost) well.

Java applications simply refuse to acknowledge scim. They ignore the keybinds and manually enabling Anthy (which spawns the panel) and then refocusing the Java window makes the panel disappear. I don't really understand what's going on, but somehow it's listening for keypresses elsewhere? Copying and pasting some cjk characters works; the font used seems to support it. It's just not using the correct input method. **GTK_IM_MODULE** and **QT_IM_MODULE** are both set to "**scim-bridge**", though Java apps don't strike me as based on etiher Gtk nor Qt, heh. **XMODIFIERS** is properly set to "**@im=SCIM**".

On a side note, OpenOffice won't acknowledge scim if the Gnome extensions ([FONT="Courier New"]openoffice.org-gnome[/FONT] package) aren't installed. If the KDE ones are ([FONT="Courier New"]openoffice.org-kde[/FONT]) then it behaves as described above. If neither are installed the same thing happens. Installing the Gnome ones, however, makes OpenOffice unusable; icons disappearing on mouseover, no borders on menus nor popups. (See [http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=3100](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=3100).)

The point being, OpenOffice doesn't acknowledge scim either without some special Gtk exensions. Isn't StarOffice - and, by extension, OpenOffice - written in Java? Azureus is scim-aware, though, so I'm having a hard time attributing all of this to Java.


I can (grudgingly) live without OpenOffice and use KOffice for the time being, but no scim in Java is another thing. I attached a small test class which just spawns a popup if you want to try running it for yourself.
```
$ tar xfvj javatest.tar.bz2
$ java SCIMTest
```

---

### Post by Zorael on 2008-05-27
My apologies for suspecting you, Java; mea culpa.
```
$ ls -l /etc/alternatives/xinput-all_ALL
lrwxrwxrwx 1 root root 28 2008-05-28 00:50 /etc/alternatives/xinput-all_ALL -> /etc/X11/xinit/xinput.d/skim

$ grep -i xim_ /etc/X11/xinit/xinput.d/skim
**XIM_PROGRAM=" "**
```
What is this! Hwrr!


Modifying said skim file to the following made everything work.
```
XIM=SCIM
[b]XIM_PROGRAM=/usr/bin/scim
XIM_ARGS=-d
XIM_PROGRAM_SETS_ITSELF_AS_DAEMON=yes[/b]

if [ -e /usr/lib/gtk-2.0/*/immodules/im-scim-bridge.so ]; then
    GTK_IM_MODULE="scim-bridge"
elif [ -e /usr/lib/gtk-2.0/*/immodules/im-scim.so ]; then
    GTK_IM_MODULE=scim
else
    GTK_IM_MODULE=xim
fi
if [ -e /usr/lib/qt3/plugins/inputmethods/im-scim-bridge.so ] || [ -e /usr/lib/qt4/plugins/inputmethods/im-scim-bridge.so ]; then
    QT_IM_MODULE="scim-bridge"
elif [ -e /usr/lib/qt3/plugins/inputmethods/libqscim.so ]; then
    QT_IM_MODULE=scim
else
    QT_IM_MODULE=xim
fi

DEPENDS="skim, scim-bridge-client-gtk | scim-bridge-client-qt | scim-bridge-client-qt4 | scim-gtk2-immodule | scim-qtimm"
```

All is [well](http://www.cristalab.com/images/anime/evangelion/wallpaper-nerv.jpg).

---

### Post by ryukent on 2008-05-30
For all those using hardy, please follow this thread instead:

[http://ubuntuforums.org/showthread.php?t=812552](http://ubuntuforums.org/showthread.php?t=812552)

The guide has been much updated and particularly the font setup which will give better results for hardy.

UIM guide to follow.... when I have time.

---

