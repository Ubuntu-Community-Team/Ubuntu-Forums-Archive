---
title: "HOWTO: Installing Japanese that looks nice on Ubuntu Edgy : &#26085;&#26412;&#35486;"
date: 2007-01-15
forum: Outdated Tutorials &amp; Tips
---

### Post by ryukent on 2007-01-15
HOWTO: Installing Japanese that looks nice on Ubuntu Edgy : &#26085;&#26412;&#35486;

OK, so it drove me absolutely crazy and I very nearly switched back to Fedora which would have been a great shame. All I wanted to do was install Japanese input that looked OK in an English install of Ubuntu. There were many different guides out there and most of which were incomplete or based on previous versions. So I have put what worked for me together in this thread. It might not work for you and I don't claim to have come up with it myself, but maybe some people might find it helpful. I hope the next version of Ubuntu has this out of the box (as Fedora does).

There are two issues here:
1.Installing the SCIM input system that will work in a locale other than converting your whole install to Japanese, i.e. you want Japanese input in an English login.
2.The fonts look initially terrible. Therefore a certain amount of customisation is required to make all the Kanji's render in the same style and Hiragana & Katakana to render in a non-handwriting style.
 

1.
First lets make sure you have the correct repositories installed in order to automatically download the relevant packs. Open the repositories list file:

```
sudo gedit /etc/apt/sources.list
```

Add the following line at the bottom:

```
deb http://archive.ubuntulinux.jp/ubuntu-ja edgy/
```

Now update your repos with:

```
sudo apt-get update
```

Go to System / Administration / Language Support and select Japanese. This should install the basics.

You might want to install some other Asian input methods too. To make sure you have all the common ones, use:

```
sudo apt-get install uim anthy scim-gtk2-immodule scim-uim scim-chinese scim-hangul scim-tables-zh scim-tables-ja scim-tables-ko
```

That should install Japanese, Chinese and Korean input. If you don't want them all, don't worry you can always hide them from the list later (in SCIM config), but it's probably a good idea to have them on your system.

Now you want to make SCIM (Language input system) available in your English login and not just the Japanese one. First open the scim_startup file:

```
sudo gedit /etc/X11/Xsession.d/74custom-scim_startup
```

Add these lines:

```
export XMODIFIERS="@im=SCIM"
export GTK_IM_MODULE="scim"
export XIM_PROGRAM="scim -d"
export QT_IM_MODULE="scim"
```

2.
OK, now you've got Japanese input installed (hopefully). It will probably require rebooting xwindows  (CTRL+ALT+Backspace). But for me, I really couldn't cope with the horrible fonts that defaulted especially as they were nice and pretty in Fedora. Here's the next step.

Now that you have the Japanese repositories set up (see above), you'll want to get a nice set of fonts. 

```
sudo apt-get install msttcorefonts ttf-dejavu ipafont ipamonafont ttf-arphic-ukai ttf-arphic-uming
```

This will install the Microsoft (Freeware) core fonts and a number of other useful fonts, specifically ones that support Japanese unicode characters.

Unfortunately, I am very disappointed in the Ubuntu distribution of DejaVu. It seems to be the default font, but you will almost certainly want this to be changed to MSGothic and MSMincho. These are Microsoft fonts, but they are freeware and are actually from a company called Ricoh so you can sleep at night knowing you're not using Microsoft if you want. They need to be downloaded and installed manually. They can be found at the following 2 sites.

[http://www.themeworld.com/cgi-bin/preview.pl/fonts/msgothic.0.zip]("http://www.themeworld.com/cgi-bin/preview.pl/fonts/msgothic.0.zip")
[http://www.themeworld.com/cgi-bin/preview.pl/fonts/msmincho.0.zip]("http://www.themeworld.com/cgi-bin/preview.pl/fonts/msmincho.0.zip")

or

[http://www.wafu.ne.jp/3dlogo/fonts/msgothic.ttf]("http://www.wafu.ne.jp/3dlogo/fonts/msgothic.ttf")
[http://www.wafu.ne.jp/3dlogo/fonts/msmincho.ttf]("http://www.wafu.ne.jp/3dlogo/fonts/msmincho.ttf")

So download the file and you need to copy them into the fonts directory. This will need root privileges and is probably easiest done using the file explorer:

```
sudo nautilus --browser
```

That will give you a browser with the right privileges. So copy your downloaded ttf files and paste them into a folder under the fonts tree. I recommend:

```
/usr/share/fonts/truetype/msttcorefonts
```

Now we need to rebuild the fonts cache:

```
sudo fc-cache -f -v
```

OK, so that might well be enough, but I think you'll probably still have your Japanese fonts not running at optimum and the default might be a little ugly. Lets set up the order in which we like the fonts to be selected. Open the &#8220;.fonts.conf&#8221; file in your home directory:
```

 sudo gedit .fonts.conf
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

Find your locale (you should already know it)
```
locale | grep LANG=
```

Then (with relevant changes)
```
sudo im-switch -z en_GB -s scim-anthy
```

Note: You will need to change the en_GB to your relevant locale. Mine is en_GB (I'm a Brit living in Tokyo) but your one will no doubt be different)

Also, you might wanna play with:

```
sudo dpkg-reconfigure fontconfig-config
```

So with any luck you should have got Japanese working to a satisfactory level. I still have issues inputting into Java AWT and SWING components, but I guess you can't expect everything. If anyone has any information on this, please let me know!

References:
[http://ubuntuforums.org/showthread.php?t=206280](http://ubuntuforums.org/showthread.php?t=206280)
[http://www.ubuntuforums.org/showthread.php?t=204500](http://www.ubuntuforums.org/showthread.php?t=204500)
[http://www.mrbass.org/linux/ubuntu/scim/](http://www.mrbass.org/linux/ubuntu/scim/)
[http://www.ubuntuforums.org/showthread.php?t=127451](http://www.ubuntuforums.org/showthread.php?t=127451)

---

### Post by seshomaru samma on 2007-01-16
Great Howto except that i couldnt add the repsoitory cause it asked for the public key, where do i get it from?

---

### Post by ryukent on 2007-01-16
> **seshomaru samma said:**
> Great Howto except that i couldnt add the repsoitory cause it asked for the public key, where do i get it from?

After adding the repository and running the update, try:

```
sudo apt-get install ubuntu-ja-keyring
```

Also note:
If you are still not satisfied with the fonts, go to /etc/fonts directory and experiment with (after making backups of course) editing some of the extra .conf files. I found having the the one's that the msttcorefonts pack was not to my taste so I deleted most of the unnecessary files. You only really need fonts.conf and maybe local.conf. The other files just provide extra information. Note that the master fonts.conf file will also reference local.conf. You can rearrange the order under the Serif, Sans Serif and Monospace families to achieve the look you want. The order I've provided above should give you a clean looking 'on par with windows' effect though.

---

### Post by ryukent on 2007-01-19
OK, I've finally cracked how to get SCIM-Anthy to display properly in Java (and possibly many other apps).

I ran nautilus in root, then went to /root/.scim directory and replaced the existing config file with the one that I had in my user home directory of an already set up user.

Works a treat. I can now input Japanese in Java apps like netbeans!

---

### Post by ryukent on 2007-01-22
If you are having problems loading programs that use QT (like skype), try changing your QT_IM_MODULE environment variable to xim.


export QT_IM_MODULE=xim

---

### Post by osarusan on 2007-01-22
Hi, thanks for this great tutorial!

I have one question: after setting this up, including your recommended .fonts.conf, the whole system is now using one of the Japanese fonts to display menus and texts in Ubuntu. It works fine, but it's not the prettiest English font. How can I set this this up while still maintaining the default look for the English fonts in Ubuntu? Or -- alternatively, how to uninstall this?

Thanks again for posting this!

---

### Post by ryukent on 2007-01-22
> **osarusan said:**
> Hi, thanks for this great tutorial!

I have one question: after setting this up, including your recommended .fonts.conf, the whole system is now using one of the Japanese fonts to display menus and texts in Ubuntu. It works fine, but it's not the prettiest English font. How can I set this this up while still maintaining the default look for the English fonts in Ubuntu? Or -- alternatively, how to uninstall this?

Thanks again for posting this!

Go to System / Preferences / Font, then make sure that all the fonts here, especially application and desktop fonts are specified as actual font names, not families. For example, I have specified 'Verdana' instead of simply 'Sans'.

---

### Post by osarusan on 2007-01-22
Ah thanks! That helped.

Verdana works perfectly, but for Monotype, the font still looks screwy -- as if the baseline is on a different level for each font. Which font are you using for the fixed width?
(And additionally, why would this mess up the way Monotype displays?)

Edit:Actually -- I found it out -- it's DejaVu Sans and Mono. 

Ok, I have one more question -- when Ihave windows open, each one gets its own input editor... is there a way to make it so they all use the same one, rather than having to individually change the preferences for each one? It would be nice if it worked as a universal input method editor, rather than per-program.

Thanks again!

---

### Post by ryukent on 2007-01-23
> **osarusan said:**
> Ah thanks! That helped.

Verdana works perfectly, but for Monotype, the font still looks screwy -- as if the baseline is on a different level for each font. Which font are you using for the fixed width?
(And additionally, why would this mess up the way Monotype displays?)

Edit:Actually -- I found it out -- it's DejaVu Sans and Mono. 

Ok, I have one more question -- when Ihave windows open, each one gets its own input editor... is there a way to make it so they all use the same one, rather than having to individually change the preferences for each one? It would be nice if it worked as a universal input method editor, rather than per-program.

Thanks again!

I use Verdana for everything and Courier New for fixed width. As for the per program.... well you can set "Share same input method among all applications" in the global section of SCIM setup. However, as different Linux programs are using different desktop environment runtimes and handle input in different ways, it might remain necessary to have multiple SCIMs spawned.

---

### Post by ryukent on 2007-02-04
I've rewritten this for Kubuntu. As Kubuntu uses SKIM, it needs to be set up differently if you want the input to work in all applications. Also, I've changed the font order to make latin scripts look nicer whilst maintaining Japanese character look.

Please see the Kubuntu link if you are using the KDE desktop version of Ubuntu.

[http://kubuntuforums.net/forums/index.php?topic=13489.0](http://kubuntuforums.net/forums/index.php?topic=13489.0)

---

### Post by ryukent on 2007-02-07
WARNING:
Do not install these packs if you are using KDE:
ttf-sazanami-gothic ttf-sazanami-mincho

For some reason there seems to be a problem whereby you can't boot into the KDE environment because of something the Sazanami packs have done. Removing the packs seems to correct the problem. To be honest though, as far as Japanese fonts are concerned, Kochi is far superior to Sazanami, so you don't really need it. Or, as mentioned above, the Ricoh fonts (MSGothic, MSMincho) look even better, not to mention IPA.

However, if you've installed the Java run time from the repos, it will point to Sazanami as the Japanese font. You can adjust this to Kochi by following this link:

[http://kubuntuforums.net/forums/index.php?topic=13461.0](http://kubuntuforums.net/forums/index.php?topic=13461.0)

---

### Post by Pikestaff on 2007-03-03
> **ryukent said:**
> I've rewritten this for Kubuntu. As Kubuntu uses SKIM, it needs to be set up differently if you want the input to work in all applications. Also, I've changed the font order to make latin scripts look nicer whilst maintaining Japanese character look.

Please see the Kubuntu link if you are using the KDE desktop version of Ubuntu.

[http://kubuntuforums.net/forums/index.php?topic=13489.0](http://kubuntuforums.net/forums/index.php?topic=13489.0)

Thanks for this guide, I've been looking for something like this.  Will it work with Kubuntu Dapper as well?  I just want to make sure before I try it out.

---

### Post by zholistic on 2007-03-03
I've just tried installing the Asian fonts>

sudo apt-get install uim anthy scim-gtk2-immodule scim-uim scim-chinese scim-hangul scim-tables-zh scim-tables-ja scim-tables-ko

and it's given me the message>

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  anthy: Depends: libanthy0 (>= 7900) but 6724-1 is to be installed
         Depends: libc6 (>= 2.4-1) but 2.3.6-0ubuntu20.4 is to be installed
E: Broken packages

I've tried through synaptic to upgrade these packages but it looks like I would be reverting (?)

Any suggestions appreciated.

---

### Post by ryukent on 2007-03-05
Zholistic.... what version of Ubuntu are you running... and have you got the standard Ubuntu repositories, plus universe, multiverse and the Japanese repositories installed?

---

### Post by ryukent on 2007-03-05
Probably not very well... here's a link for Kubuntu Edgy. Not sure about dapper though. This was designed for Edgy. I recommend upgrading anyway Edgy seems much improved.

[http://kubuntuforums.net/forums/index.php?topic=13489.0](http://kubuntuforums.net/forums/index.php?topic=13489.0)

> **Pikestaff said:**
> Thanks for this guide, I've been looking for something like this.  Will it work with Kubuntu Dapper as well?  I just want to make sure before I try it out.

---

### Post by Steve H on 2007-03-25
Thanks a lot for that, it worked beautifully. I can now write emails to my Japanese friends.

As a side note though, is there any way of having emails containing Kana to have the relevant encoding selected automatically? It is only a minor inconvenience, to have to select the Japanese encoding in order to read the kana, but i'm lazy...... :) !!!

---

### Post by ryukent on 2007-03-28
That would all depend on what program you are using to write the emails. If it's web based and you're using firefox, then try selecting View / Character Encoding / Auto Select / Japanese.

Unicode web pages should work fine for all languages. If you are using a mail client with a pop3 account then it will depend on the application.

> **Steve H said:**
> Thanks a lot for that, it worked beautifully. I can now write emails to my Japanese friends.

As a side note though, is there any way of having emails containing Kana to have the relevant encoding selected automatically? It is only a minor inconvenience, to have to select the Japanese encoding in order to read the kana, but i'm lazy...... :) !!!

---

### Post by frychiko on 2007-03-28
> There are two issues here:
1.Installing the SCIM input system that will work in a locale other than converting your whole install to Japanese, i.e. you want Japanese input in an English login.

I haven:t had this problem since I upgraded to feisty... You can have an English locale and just install Japanese and then setup SCIM, easy as windows now.

---

### Post by Steve H on 2007-03-28
I am using Evolution mail at the moment, which is set to "default" encoding, so whenever it needs to be changed I have to do it myself. I use Evolution because it syncs with my IPAQ (which i have also setup with Japanese input and fonts, BTW). Is there a better mail prog that can deal with "Auto-select" encoding? if so which one should i use?

Also, Ryukent, maybe you could answer a related question for me, I recently received an email from a Japanese friend, and all the encoding was REALLY screwy, no setting would make the Kana appear. It all just looked like "&2145,&5426" (that is an example i made up, not a quote form the email, which i opened in Outlook in Windoze). Is there any reason that i wouldn't be able to see the kana?? Is there any other type of character encoding used in Japan?

Many thanks for all your help.

---

### Post by ryukent on 2007-03-29
In evolution under mail options you can change the default mail encoding. It should be UTF-8. However, if your friend is using an older or non unicode supporting system he may have used one of the other popular Japanese encodings. EUC and JIS are the most common.

---

### Post by Steve H on 2007-03-29
Ryukent, Thanks for replying. I'll have a look in to the mail options, i've deleted the email now, so i'll wait and see if his reply does the same thing.

Thanks again.

:)

---

### Post by null84 on 2007-04-05
can u write a guide on installing Chinese? i am new at linux and I am having a hard time to figure out installing canton HK input...

---

### Post by HokkaidoHillbilly on 2007-04-06
Thanks SO much for this How-To!  I'm so psyched that I can just use the &#21322;&#35282;&#12539;&#20840;&#35282; button to switch between English & Japanese!  &#12420;&#12387;&#12383;&#65281; ;)

&#12393;&#12358;&#12418;&#12397;&#65281;&#12381;&#12375;&#12390;&#12371;&#12428;&#12363;&#12425;&#12418;&#12424;&#12429;&#12375;&#12367;&#12357;&#65281; orz

---

### Post by Rondonjin on 2007-04-21
I battled with the ugly DBCS fonts in Edgy and gave up and came back to Fedora. A little while later I discovered a Japanese version of Edgy that looked sooo much better and came with an applet to install Japanese versions of Adobe Reader and some other localised stuff. I installed it onto a spare machine I had, updated it, customised it then switched the default language to UK English :-)

I'm downloading the ja-7.04 ISO right now and will do the same. I did a and upgrade to 7.04 but it's broken Japanese input when running in English, works fine when switched back to Japanese.

Wayne

---

### Post by HokkaidoHillbilly on 2007-04-23
The other cool thing about Feisty is that as soon as installed Japanese support from System->Administration->Language Support, BOOM...anthy was ready to go!  &#12381;&#12375;&#12390;&#12371;&#12428;&#12363;&#12425;&#12300;&#21322;&#35282;&#12539;&#20840;&#35282;&#12301;&#12461;&#12540;&#12434;&#25276;&#12375;&#12383;&#12425;&#26085;&#26412;&#35486;&#12364;&#12377;&#12368;&#20351;&#12360;&#12427;&#65281;

Woot!

Oh yeah...one thing if you don't mind using M$ fonts...meiryo is the default Japanese font in Japanese Vista and about 10 million times better than any roman/Japanese font I've seen before.  I'm using it system-wide now and it looks great!

If anybody'd like more info, just lemme know and I can point you in the right direction.

---

### Post by Steve H on 2007-04-24
Is there anywhere to have a look at the Vista fonts?

I'd like to have a look at them, and if you can point me in the right direction for a download as well that would be nice!!

---

### Post by HokkaidoHillbilly on 2007-04-26
There's actually quite a bit of info on this font...even a Wiki page.  Just Google or Wiki "Meiryo" or "&#12513;&#12452;&#12522;&#12458;".

I've got the .zip of the regular & bold versions, but those 2 alone are almost 10MB.  If you know of a way I can get it to you easily, lemme know.

---

### Post by bren21 on 2007-04-27
I am interested in them as well. If you want, you could upload them to my website and whoever wants them could just download them then. PM me and let me know if you want to.

---

### Post by bren21 on 2007-05-03
Okay I got the Meiryo fonts on my comp now, and I put them on my website so if anyone wants to download them they can. My site is still being made though, so it looks really crappy :) Download them  [[COLOR="Red"]HERE[/COLOR]]("http://www.hovanic.net/downloads")

---

### Post by ryukent on 2007-05-14
Can anyone confirm the licence issues with Meiryo.... I assume they are not public domain.

---

### Post by 005david on 2007-10-11
&#12393;&#12418;&#12354;&#12426;&#12364;&#12392;&#12358;&#12372;&#12374;&#12356;&#12414;&#12377;&#65281;

---

### Post by El Chupacabras on 2007-11-04
This is a great tutorial and all, but I find that it screws up hinting on my regular latin script.
I suggest the last part be replaced with:
```
 <match target="font" >
  <edit mode="assign" name="embeddedbitmap" >
   <bool>false</bool>
  </edit>
 </match>
 <match target="font" >
  <test name="lang" compare="contains">
    <string>ja</string>
  </test>
  <edit mode="assign" name="autohint" >
   <bool>true</bool>
  </edit>
  <edit name="antialias" mode="assign">
   <bool>true</bool>
  </edit>
  <edit name="hintstyle" mode="assign">
   <const>hintnone</const>
  </edit>
 </match>
</fontconfig>
```

The following lines make sure the settings only apply to japanese fonts, thereby sparing you  enormous blocky English fonts.
```
  <test name="lang" compare="contains">
    <string>ja</string>
  </test>
```

---

### Post by ryukent on 2008-02-02
I've written a new version for 7.10 - Gutsy. I'm recommending people move to UIM because of the compatibility issues currently regarding SCIM. From the Japanese forums, I've seen word that Ubuntu SCIM doesn't have one of the patches that fedora and other dists have. This has been posted as an official bug, but so far is yet to be sorted.

In the mean time, people might find this thread helpful:

[http://ubuntuforums.org/showthread.php?t=684469](http://ubuntuforums.org/showthread.php?t=684469)

---

