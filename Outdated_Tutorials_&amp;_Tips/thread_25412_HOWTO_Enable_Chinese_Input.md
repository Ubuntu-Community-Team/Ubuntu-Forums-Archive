---
title: "HOWTO: Enable Chinese Input"
date: 2005-04-10
forum: Outdated Tutorials &amp; Tips
---

### Post by DuKefeng on 2005-04-10
[SIZE=3]**_Chinese Input for Ubuntu Hoary:_**[/SIZE]
[SIZE=1][(version française)](http://forum.ubuntu-fr.org/viewtopic.php?pid=17862#p17862)[/SIZE]

**1)** install the following packages:
    * scim
    * scim-chinese
    * scim-config-socket
    * scim-frontend-socket
    * scim-gtk2-immodule
    * scim-server-socket
    * scim-tables-zh (option)
    * xfonts-intl-chinese
    * xfonts-intl-chinese-big   
    * ttf-arphic-gbsn00lp
    * ttf-arphic-gkai00mp
    * ttf-arphic-bkai00mp
    * ttf-arphic-bsmi00lp

accept all dependencies.

**2)** System -> Preferences -> Sessions

Startup Programs Tab -> Add Button
Startup Command: scim -d
Order: 80

**3)** Restart Gnome: CTRL+ALT+SUPPR

**4)** Open any software and press CTRL+SPACE to activate chinese input
------------------------------------------------------------------------------------------------------

**IF** not working you can as an alternative replace step 2) as follow:

**2)** alt+F2, gedit

type these few lines:
```
scim -d
export XMODIFIERS=@im=scim
export GTK_IM_MODULE=scim
gnome-session
```
Save them under your home directory name: .xsession

Then open a terminal and type:
```
$chmod +x .xsession
```
------------------------------------------------------------------------------------------------------
[B]
_Tips_[/B]

_Additional Instructions for OpenOffice:_
Tools=>Options=>Language Settings=>Languages: enable Asian languages support and choose the asian default language for document. (chinese simplified for example)
Tools=>Options=>Text Document=>Basic Fonts (Asian): change all of them for "AR PL Kaitim GB" or your favorite chinese font.

_Clean Font_
Add Firefly's font "AR PL New Sung"

Open a terminal and type
```

$wget http://firefly.idv.tw/apt/firefly-font/fireflysung-1.3.0.tar.gz
$tar zxvf fireflysung-1.3.0.tar.gz
$sudo cp fireflysung-1.3.0/fireflysung.ttf /usr/share/fonts/truetype/
$sudo fc-cache -f -v
```
Alternative repositories
```
$wget http://cle.linux.org.tw/fonts/FireFly/fireflysung-1.3.0.tar.gz
or
$wget http://apt.nc.hcc.edu.tw/pub/FC_src/fireflysung-1.3.0.tar.gz
or
$wget http://www.study-area.org/apt/firefly-font/fireflysung-1.3.0.tar.gz
```

_More Fonts_
Install msttcorefonts, open a terminal:
```

$sudo apt-get install msttcorefonts
```



&#29616;&#22312;&#33021;&#20889;&#20013;&#25991;

&#35874;&#35874;[pierre](http://pierre.equoy.free.fr/blog/index.php?2005/03/28/36-taper-du-texte-chinois-sous-ubuntu) &#19982;[tzutolin](http://www.ubuntuforums.org/member.php?u=13973)

---

### Post by benkorkor on 2005-04-10
Awesome, thanks.

---

### Post by mesocool on 2005-04-10
> **DuKefeng]**_Chinese input Hoary:_**

**1)** install the following packages:
    * scim
    * scim-chinese
    * scim-config-socket
    * scim-frontend-socket
    * scim-gtk2-immodule
    * scim-server-socket
    * scim-tables-zh (option)
    * xfonts-intl-chinese
    * xfonts-intl-chinese-big   
    * ttf-arphic-gbsn00lp
    * ttf-arphic-gkai00mp
    * ttf-arphic-bkai00mp
    * ttf-arphic-bsmi00lp

accept all dependencies.

**2)** Go to "System" -> "Preferences", and select "Sessions". In "Startup Programs", add the command "scim -d"

**3)** Restart Gnome: CTRL+ALT+SUPPR

**4)** Open any software and press CTRL+SPACE to enable chinese input

Additional Instructions for OpenOffice:
Tools=>Options=>Language Settings=>Languages: enable Asian languages support and choose the asian default language for document. (chinese simplified for example)
Tools=>Options=>Text Document=>Basic Fonts (Asian): change all of them for "AR PL Kaitim GB" or your favorite chinese font.

Tips to have a better choice of fonts, install msttcorefonts&#12290 said:**
> pierre[/url] &#19982;[tzutolin](http://www.ubuntuforums.org/member.php?u=13973)


I can read and write Chinese, but the words shown are blur.. Just not as clear as English characters.. How can I fix that?

---

### Post by benkorkor on 2005-04-11
This is brilliant. I love it. Works very well.

---

### Post by DuKefeng on 2005-04-11
[QUOTE=mesocool]I can read and write Chinese, but the words shown are blur.. Just not as clear as English characters.. How can I fix that?[/QUOTE]

Install firefly's font "AR PL New Sung"

Added in the HowTo

---

### Post by mesocool on 2005-04-11
After I did the following, the Chinese characters are still blur as usual. Seems not changing anything. :-# 

$wget [http://firefly.idv.tw/apt/firefly-font/fireflysung-1.3.0.tar.gz](http://firefly.idv.tw/apt/firefly-font/fireflysung-1.3.0.tar.gz)
$tar zxvf fireflysung-1.3.0.tar.gz
$sudo cp fireflysung-1.3.0/fireflysung.ttf /usr/share/fonts/truetype/
$sudo fc-cache -f -v

---

### Post by DuKefeng on 2005-04-12
Try this : 

[Disable anti-alias technology for Chinese fonts 16px or under](http://wiki.linux.org.hk/index.php/How_to_make_Debian_support_chinese_(eng)#Fontconfig_Settings)

My local.fonts look like this now:

```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
  <include ignore_missing="yes">/var/lib/defoma/fontconfig.d/fonts.conf</include>
<!-- Uncomment below to enable bitmapped fonts -->
<!--
  <dir>/usr/X11R6/lib/X11/fonts</dir>
-->
<!-- Uncomment below to enable subpixel rendering -->
<!--
  <match target="font">
    <test qual="all" name="rgba">
      <const>unknown</const>
    </test>
    <edit name="rgba" mode="assign"><const>rgb</const></edit>
  </match>
-->
<!-- Uncomment below to enable the freetype autohinter module -->
<!--
  <match target="font">
    <edit name="autohint" mode="assign">
      <bool>true</bool>
    </edit>
  </match>
-->
<!-- Disable font alias for Chinese <= 16px -->
  <match target="font">
    <test qual="any" name="family" compare="eq">
      <string>AR PL KaitiM Big5</string>
      <string>AR PL KaitiM GB</string>
      <string>AR PL Mingti2L Big5</string>
      <string>AR PL SungtiL Big5</string>
      <string>AR PL New Sung</string>
      <string>AR PL SungtiL GB</string>
      <string>Kochi Mincho</string>
      <string>Baekmuk Dotum</string>
    </test>
    <test name="pixelsize" compare="less_eq">
      <double>8</double>
    </test>
    <edit name="antialias">
      <bool>false</bool>
    </edit>
    <edit name="hinting">
      <bool>true</bool>
    </edit>
  </match>
</fontconfig>
``` 

But i don't see any differences.  :-? 

Another way is to type with fonts size bigger than 16  :grin:

Maybe you can post a screenshot to see how bad does it look?

---

### Post by jiyuu0 on 2005-04-12
added to ubuntuguide.org
[http://ubuntuguide.org/#scim](http://ubuntuguide.org/#scim)

only prob... seems like some chars can't be displayed in the scim
try the word 'wo' and then scroll... can see boxes (unknown chars)

---

### Post by wlx on 2005-04-12
When I input chinese with scim, sometimes it will occurs firefox's terminate.

---

### Post by DuKefeng on 2005-04-12
[QUOTE=jiyuu0]added to ubuntuguide.org
[http://ubuntuguide.org/#scim](http://ubuntuguide.org/#scim)

only prob... seems like some chars can't be displayed in the scim
try the word 'wo' and then scroll... can see boxes (unknown chars)[/QUOTE]

This is fonts related. Some of them are more complete than the other. Try to type 'wo' with differents chinese fonts and you will see the differences.

---

### Post by mesocool on 2005-04-12
I made an attachment, a screenshot of NBA in China..

When I increase the size of words, they are not blur. But it also changes the frame of the website..  :roll:

---

### Post by DuKefeng on 2005-04-12
Firefox->Edit->Preferences->General->Fonts & Colors

Change all possible fonts to AR PL New Sung
Minimum fonts size: 17
Screen Resolution: Others (it will find the optimized resolution)

Fonts are out of the frames but clear.

Maybe you should check this link for more answers:
[URL]http://wiki.linux.org.hk/index.php/How_to_make_Debian_support_chinese_(eng)
[/URL]

---

### Post by ddhytz on 2005-04-13
How can  Chinese be shown in other apps, such as Music Player playing mp3 songs?

---

### Post by ghost on 2005-04-13
Thanks Buddy, I was just looking for Chinese Input software for my Hoary.  ;-) 

Do you know is there any tool I can use to convert Traditional Chinese to Simlplifed?

---

### Post by DuKefeng on 2005-04-13
Overall, can you ask more precise questions. I like to help but I like people help me help them.


[QUOTE=wlx]When I input chinese with scim, sometimes it will occurs firefox's terminate.[/QUOTE]
Before everything do a restart, if problem occurs again then reinstall the maybe faulty packages (mozilla-firefox, scim....) then if nothing is better ask yourself some questions:
You type in firefox or out of firefox? in the google bar, in the address bar or where? How often?
Check the forum, firefox terminate for obscur reasons for some members, maybe your problem is not Scim related?


[QUOTE=ddhytz]How can  Chinese be shown in other apps, such as Music Player playing mp3 songs?[/QUOTE]
You want to see chinese or to have your software in chinese?
If you want to see it, i presume that you have chinese MP3, send me one to try, i don't have any.
If you want your software to be displayed in chinese, you have to change your whole system in chinese.  :grin: 

Open a terminal

```
$sudo dpkg-reconfigure locales
choose any language you fancy plus: zh_CN GB2312 for simple chinese ou zh_TW BIG5 for traditionnal chinese

Restart gnome (ctrl+alt+del)
choose chinese as language and login

```
You are now in a chinese ubuntu with all software in chinese i guess, this is not the goal of my howto, so i will not answer any questions concerning chinese translation of software. Not to mention that this reconfiguration of languages screwed my scim, do it at your own risk.


[QUOTE=ghost]Thanks Buddy, I was just looking for Chinese Input software for my Hoary.  ;-) 

Do you know is there any tool I can use to convert Traditional Chinese to Simlplifed?[/QUOTE]
I don't know any, i just tried a $sudo dpkg reconfigure-locales adding the BIG5, screwed up my scim, no more chinese input, no more testing. Sorry.

I'll try a fresh install by next week and go on with experimentation.

Maybe a better way of testing is to create a different user and try the reconfigure-locales without sudo, i had issue with this problem in Warty before, might be a solution. (see the thread of my french howto when i was playing with warty).

---

### Post by ddhytz on 2005-04-14
[QUOTE=DuKefeng]

You want to see chinese or to have your software in chinese?
If you want to see it, i presume that you have chinese MP3, send me one to try, i don't have any.
[/QUOTE]

Just want to see Chinese name of the song. Instead of sending you one, can you change the name of any mp3 song you have to a Chinese name, then see if you can see it inside the music player? Thanks.

---

### Post by DuKefeng on 2005-04-14
Look at my screenshot with GN'R attitude renamed &#26538;&#19982;&#29611;&#29808;
The result on Rhythmbox is that i've got the whole name of the band with title and album title.

I'm not a specialized in multimedia or MP3 but i guess that i need to edit the MP3 file to change all these infos.

---

### Post by ddhytz on 2005-04-14
[QUOTE=DuKefeng]Look at my screenshot with GN'R attitude renamed &#26538;&#19982;&#29611;&#29808;
The result on Rhythmbox is that i've got the whole name of the band with title and album title.

I'm not a specialized in multimedia or MP3 but i guess that i need to edit the MP3 file to change all these infos.[/QUOTE]

IWhen Music Player imports a folder it changes file names to unreadable stuff after clicking 'Open'.

---

### Post by khc on 2005-04-14
Make sure the names/titles/other attributes are encoded in utf8.

---

### Post by ddhytz on 2005-04-15
[QUOTE=khc]Make sure the names/titles/other attributes are encoded in utf8.[/QUOTE]

This must be the key of whole trouble!! But I do not know how the name was encoded or if they can be converted in utf8. When I find how to display Chinese names properly I will be able to use Linux as my sole OS.

---

### Post by khc on 2005-04-16
You may need to enter them again. I've never edited the metadatas other when I rip CDs, so I don't know what tools you can use.

---

### Post by Chia on 2005-04-26
For displaying chinese mp3 song titles, I use beep-media-player in universe, make sure you have UTF-8 locale (locale -a) , if not, then 
dpkg-reconfigure locales,
also run beep-media-player from a terminal with the following command

LC_ALL=zh_CN.gb2312 beep-media-player   
or
LC_ALL=zh_CN.UTF-8  beep-media-player
or
LC_ALL=zh_TW.big5  beep-media-player

I also found set-m17n-env  from package m17n-env is a good way to setup input environment using scim , without resorting to hand-editing the .xsession file. This way I can use Kubuntu  (KDE) without having to run gnome-session from .xsession startup file.

---

### Post by ddhytz on 2005-04-27
beep-media-player only shows mp3 song names like ???-???? (invalid UTF) in playlist. My locales are as follows
C
en_AU.utf8
en_GB.utf8
en_US.utf8
POSIX
zh_CN.utf8
zh_TW
zh_TW.big5
zh_TW.utf8

Any idea?

---

### Post by Chia on 2005-04-27
Do you have the following locales? type locale -a to show them
zh_CN
zh_CN.gb2312
zh_CN.gbk
zh_TW.big5
zh_TW.utf8

If not then you need to run and select them:
sudo dpkg-reconfigure locales

and run beep-media-player as i mentioned earlier, 
LC_ALL=zh_CN.gb2312 beep-media-player  
or whichever language your mp3 ID3 is encoded at or create a shortcut in menu to run this everytime you clicked on it.

---

### Post by ddhytz on 2005-04-28
Well, LC_CTYPE=zh_CN.gb2312 beep-media-player works. Thanks.

---

### Post by mrbass on 2005-04-28
ok the openoffice stuff is not entirely needed but nice to set default fonts and other things.  Now for chinese I tested all the input methods and these worked

[Simplified Chinese]
Smart Pinyin (press #)
UIM-py
UIM-m17n-zh-py

[Other]
UIM-pinyin-big5

These input methods did not
UIM-pyunihan
UIM-m17-zh-pinyin

Now here's my question what about the older folks who prefer Chinese Traditional?  At my old work I remember setting up both Traditional and Simplified for a Chinese girl.  She insisted on it.

---

### Post by mrbass on 2005-04-28
Is that fireflysung font really needed?  I'm tending to think it's not.  Here's a screenshot...no I don't know how to type Chinese so it's nonsense but it gives you an idea of the fonts.  Fonts 1 through 4 come with Ubuntu. 

Don't you think font 3 AR PL Mingti2L Big 5 is almost exactly like font 5 AR PL New Sung (aka fireflysung)?

---

### Post by geminifire on 2005-05-06
&#35874;&#35874;&#65281;

---

### Post by migo on 2005-05-07
Thanks, I look forward to trying this out once I get my Hoary CD :D

---

### Post by wlx on 2005-05-08
[QUOTE=DuKefeng]Overall, can you ask more precise questions. I like to help but I like people help me help them.

Before everything do a restart, if problem occurs again then reinstall the maybe faulty packages (mozilla-firefox, scim....) then if nothing is better ask yourself some questions:
You type in firefox or out of firefox? in the google bar, in the address bar or where? How often?
Check the forum, firefox terminate for obscur reasons for some members, maybe your problem is not Scim related?

[/QUOTE]

Thanks for your help.

I don't know the reason of firefox's terminate,and I can't make it happen again.

Any more, I don't know why so many modules of scim existed,but if I just install three modules: scim,scim-chinese,scim-tables-zh, the system will more stable. ( I find this problem with planner. First I install the scim with all the modules as you mentioned, but sometimes the planner can't input any chars when I activate the scim, and when I remove other modules of scim, it is worked! )

---

### Post by lao_V on 2005-05-09
[QUOTE=wlx]Thanks for your help.

I don't know the reason of firefox's terminate,and I can't make it happen again.

Any more, I don't know why so many modules of scim existed,but if I just install three modules: scim,scim-chinese,scim-tables-zh, the system will more stable. ( I find this problem with planner. First I install the scim with all the modules as you mentioned, but sometimes the planner can't input any chars when I activate the scim, and when I remove other modules of scim, it is worked! )[/QUOTE]

Hi guys, the guide works great for gtk apps but can anyone tell me how I can enable chinese input for KDE apps? Thanks

---

### Post by erik-the-red on 2005-07-31
[QUOTE=lao_V]Hi guys, the guide works great for gtk apps but can anyone tell me how I can enable chinese input for KDE apps? Thanks[/QUOTE]
 I should install those ttf fonts if I want to view Chinese in OpenOffice, right?

---

### Post by ubuntutinger on 2005-11-10
> **DuKefeng][SIZE=3]**_Chinese Input for Ubuntu Hoary:_**[/SIZE]
[SIZE=1][(version française)](http://forum.ubuntu-fr.org/viewtopic.php?pid=17862#p17862)[/SIZE]

**1)** install the following packages:
    * scim
    * scim-chinese
    * scim-config-socket
    * scim-frontend-socket
    * scim-gtk2-immodule
    * scim-server-socket
    * scim-tables-zh (option)
    * xfonts-intl-chinese
    * xfonts-intl-chinese-big   
    * ttf-arphic-gbsn00lp
    * ttf-arphic-gkai00mp
    * ttf-arphic-bkai00mp
    * ttf-arphic-bsmi00lp

accept all dependencies.

**2)** System -> Preferences -> Sessions

Startup Programs Tab -> Add Button
Startup Command: scim -d
Order: 80

**3)** Restart Gnome: CTRL+ALT+SUPPR

**4)** Open any software and press CTRL+SPACE to activate chinese input
------------------------------------------------------------------------------------------------------

**IF** not working you can as an alternative replace step 2) as follow:

**2)** alt+F2, gedit

type these few lines:
```
scim -d
export XMODIFIERS=@im=scim
export GTK_IM_MODULE=scim
gnome-session
```
Save them under your home directory name: .xsession

Then open a terminal and type:
```
$chmod +x .xsession
```
------------------------------------------------------------------------------------------------------
[B]
_Tips_[/B]

_Additional Instructions for OpenOffice:_
Tools=>Options=>Language Settings=>Languages: enable Asian languages support and choose the asian default language for document. (chinese simplified for example)
Tools=>Options=>Text Document=>Basic Fonts (Asian): change all of them for "AR PL Kaitim GB" or your favorite chinese font.

_Clean Font_
Add Firefly's font "AR PL New Sung"

Open a terminal and type
```

$wget http://firefly.idv.tw/apt/firefly-font/fireflysung-1.3.0.tar.gz
$tar zxvf fireflysung-1.3.0.tar.gz
$sudo cp fireflysung-1.3.0/fireflysung.ttf /usr/share/fonts/truetype/
$sudo fc-cache -f -v
```
Alternative repositories
```
$wget http://cle.linux.org.tw/fonts/FireFly/fireflysung-1.3.0.tar.gz
or
$wget http://apt.nc.hcc.edu.tw/pub/FC_src/fireflysung-1.3.0.tar.gz
or
$wget http://www.study-area.org/apt/firefly-font/fireflysung-1.3.0.tar.gz
```

_More Fonts_
Install msttcorefonts, open a terminal:
```

$sudo apt-get install msttcorefonts
```



&#29616 said:**
> pierre[/url] &#19982;[tzutolin](http://www.ubuntuforums.org/member.php?u=13973)

This is excellent! The original step won't work for me. So I used your alternative 2nd step. It worked fine. However, it seems the input system is only for current user after installation. Once I change to another user the input system icon is not there. How can I make the input system available for all users?

Thanks,

---

### Post by ubuntutinger on 2005-11-15
[QUOTE=ubuntutinger]This is excellent! The original step won't work for me. So I used your alternative 2nd step. It worked fine. However, it seems the input system is only for current user after installation. Once I change to another user the input system icon is not there. How can I make the input system available for all users?

Thanks,[/QUOTE]

Now, I followed the same steps to setup Chinese input on Kubuntu. It did not work. Here is what I did:

1. Open system>Package Manager(Adept)>Manage Repositories
enable
deb [http://tw.archive.ubuntu.com/ubuntu](http://tw.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://tw.archive.ubuntu.com/ubuntu](http://tw.archive.ubuntu.com/ubuntu) breezy universe

install
scim 
 scim-chinese 
 scim-chewing 
 scim-config-socket 
 scim-frontend-socket 
 scim-gtk2-immodule 
 scim-server-socket 
 xfonts-intl-chinese 
 ttf-arphic-gbsn00lp 
 ttf-arphic-gkai00mp 
 ttf-arphic-bkai00mp 
 ttf-arphic-bsmi00lp

2) alt+F2, kate
 
type these few lines:
 
Code:
scim -d
export XMODIFIERS=@im=scim
export GTK_IM_MODULE=scim
startkde

Save as: .xsession in /home/username
 
Then open a terminal and type:
 
Code:
$chmod +x .xsession

3. restart X: Alt-Ctrl-Backspace

I did not see input icon nor can I Ctrl-Space to get Chinese Input.

What did I do wrong?

---

### Post by ezphilosophy on 2005-11-22
This is a nightmare.  It doesn't recongnize what is the next character nor does it even type the right one.  I typed "wei shen me" and it can't even input "wei".  This is huge problem since Ubuntu is "for humanity".  There is no way Ubuntu can reach the 1/4 of the world's population with shitty language input methods.  If Windows can do it, why the hell can't Linux do it?  There are way more "smart" people working on linux.  Seems that people think this is small problem when actually, it's one of the biggest.  I'm not Chinese, I'm just an American living in China who deals with Chinese documents all the time.  I don't want to switch over to Windows for any reason other to play command and conquer.  :-)  So, I'm hoping something can be done for the 1/4 of the WORLD'S population.  (maybe 1/3?).

Ubuntu is Awesome.

-e

---

### Post by ubuntutinger on 2005-11-22
[QUOTE=ezphilosophy]This is a nightmare.  It doesn't recongnize what is the next character nor does it even type the right one.  I typed "wei shen me" and it can't even input "wei".  This is huge problem since Ubuntu is "for humanity".  There is no way Ubuntu can reach the 1/4 of the world's population with shitty language input methods.  If Windows can do it, why the hell can't Linux do it?  There are way more "smart" people working on linux.  Seems that people think this is small problem when actually, it's one of the biggest.  I'm not Chinese, I'm just an American living in China who deals with Chinese documents all the time.  I don't want to switch over to Windows for any reason other to play command and conquer.  :-)  So, I'm hoping something can be done for the 1/4 of the WORLD'S population.  (maybe 1/3?).

Ubuntu is Awesome.

-e[/QUOTE]

Hello,

I have followed DuKefeng's instruction to install Chinese input on Ubuntu Breezy. It worked perfectly. If you use Ubuntu Breezy, please see my previous message. My problem is on Kubuntu version.

---

### Post by DuKefeng on 2005-11-29
my howto only work for gnome. :???: 

i'm trying to find an easy way to do it on kde, but failed so far... :( 

haven't tried on xfce, anyone did?

---

### Post by ezphilosophy on 2005-12-11
Well, I happened to do a fresh install and now it all seems to work fine.  It really puzzles me to what happened before.  

Anyway, I have another problem.  Why is it that Chinese characters don't show up in the folders, yet they show up in other programs such as totem.  
(note screenshot)

---

### Post by djib on 2005-12-15
Hello everyone.
For use of SCIM with KDE, you need to have a .xsession as follow:
```
scim -d
export LC_CTYPE=zh_CN.UTF-8
export XMODIFIERS="@im=SCIM"
startkde

```
This means that you must add zh_CN.UTF-8 to your locales by doing a
```
sudo dpkg-reconfigure locales
```
Of course you can still select the locale you want as you default locale.

PS: this solution is not perfect because, I cannot type letters like 'ê' anymore (ie: ^ is no longer a dead key).

---

### Post by polt on 2006-02-12
is the SCIM compatable with openoffice.org2?  i have gotten it to work with most of my programs, but when i try to type in openoffice writer2, it just shows up in romanized characters. the font is set to AR PL New Sung so i have no idea what the problem is.

---

### Post by t_huankiat on 2006-10-28
thanks for the archives and how-tos, I can finally start using inputs in chinese! and finally I figured out how to use &#26234;&#33021;&#25340;&#38899; with traditional chinese output!
now i have one more thing to cross out from my windows to linux conversion!:mrgreen:

---

### Post by FrankVdb on 2006-11-11
I tried to install the ttf Arphic fonts (under Edgy) but ran into an error:
"Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defome at line 108."

The error repeats itself for each Arphic font I try to install. 

This seems to be a known bug:
[http://lists.alioth.debian.org/pipermail/pkg-fonts-devel/2006-August/000167.html](http://lists.alioth.debian.org/pipermail/pkg-fonts-devel/2006-August/000167.html)

Anyone who knows a workaround?

---

### Post by precinto on 2006-11-15
I'm trying to use SCIM under xgl/beryl. Under my Gnome session I just followed the tutorial, but it didn't work adding 'scim -d' to the startup programs (scim started and sat on the system tray but i couldn't activate anything and the input methods menu didn't show up when left clicking) so i had to try the second method, editing .xsession, which worked. Now under Xgl I'm having the same problem, but the script doesn't seem to work, could someone tell me what would the correct script for xgl?

Should I replace the "gnome-session" line with "startxgl" (the name of the xgl script)? Like this?

```
scim -d
export XMODIFIERS=@im=scim
export GTK_IM_MODULE=scim
/usr/local/bin/startxgl.sh
```

Because I've tried and it is not working.

Thanks for your help.

---

### Post by ginbuntu on 2007-09-17
HI, I also have problem with some chinese characters not displaying. But I did the following and it fixed the problem. 

go to: 

System -> Preferences -> Fonts

On the font preferences box, select "Best Contrast" instead of "Subpixel smoothing" and you can also click on details and play around with the options and see what you like best.

Hope this helps. :)

---

### Post by chngej1991 on 2007-10-17
&#35874;&#35874;thanks a lot

---

### Post by areskz on 2007-11-21
Thank author for this howto, it works nice for me.

I have just one question: what IMEngine I should use? There are several available for simplified and several fro traditional? Which one should I use for traditional and which one for simplified?

---

### Post by lanchongzi on 2007-12-03
does it work in Gutsy as well?
what about the input in aMSN and Skype?

---

### Post by franksxf on 2008-06-14
Thanks!
The second method works for me and now I could input Chinese.
&#22810;&#35874;&#65281;

---

### Post by hqlong on 2008-10-25
It's works for me anywhere,thank very much!
&#21621;&#21621;&#65292;&#25105;&#36825;&#37324;&#20063;&#21487;&#20197;&#36755;&#20013;&#25991;&#20102;&#12290;&#35874;&#35874;&#65281;:guitar:

---

### Post by shenchen8571 on 2009-06-10
Cheers man, work executed fine.

---

### Post by cdubet on 2009-06-28
For ubuntu 9.04, there are a few changes from the original post

1)install the following packages:
some are missing, do not worry, it works with only the one you find in synaptic

2) System -> Preferences -> Sessions
Startup Programs Tab -> Add Button
Startup Command: scim -d
No more port setting

3) sudo apt-get install msttcorefonts

4) im-switch -z fr_FR -s scim (if you are french, en_US for USA. you get yours by using "locale" in your console)

5) log again (or ctrl alt backspace is you have installed dont zap)

6) on the top of the screen (menu bar, at right) you get a keyboard logo: it is scim. right click on it, interface configure, set your keyboard type (fr, us ..)
you can also remove the charset you do not need (ex chinese traditionel is only for taiwan).
Right click and choose menu item reload config
6) select something where you can type (console, google textfield in firefox ..) and press ctrl+space . you will see at the bottom of the screen on the right the input choice windows of SCIM :-)

---

### Post by aixilin on 2009-07-21
Thanks very much. Now I get great Chinese. 
&#21704;&#21704;&#12290;&#12290;&#12290; &#21704;&#21704;&#12290;&#12290;&#12290;&#25105;&#29233;&#20013;&#25991;&#12290;&#12290;&#12290;&#12290;

---

### Post by peacelake on 2009-12-21
> **DuKefeng said:**
> [SIZE=3]**_Chinese Input for Ubuntu Hoary:_**[/SIZE]
[SIZE=1][(version française)]("http://forum.ubuntu-fr.org/viewtopic.php?pid=17862#p17862")[/SIZE]

**1)** install the following packages:
    * scim
    * scim-chinese
    * scim-config-socket
    * scim-frontend-socket
    * scim-gtk2-immodule
    * scim-server-socket
    * scim-tables-zh (option)
    * xfonts-intl-chinese
    * xfonts-intl-chinese-big   
    * ttf-arphic-gbsn00lp
    * ttf-arphic-gkai00mp
    * ttf-arphic-bkai00mp
    * ttf-arphic-bsmi00lp

accept all dependencies.

**2)** System -> Preferences -> Sessions

Startup Programs Tab -> Add Button
Startup Command: scim -d
Order: 80

Excuse me, where to get the packages? And I dont' see any "Sessions" on System=> perference

---

### Post by ABuNeNe on 2009-12-29
> **peacelake said:**
> Excuse me, where to get the packages? And I dont' see any "Sessions" on System=> perference

It have been changed to "Startup Applications". Below is the updated HOWTO.

> 
**1)** install the following packages:
    * scim
    * scim-chinese
    * scim-config-socket
    * scim-frontend-socket
    * scim-gtk2-immodule
    * scim-server-socket
    * scim-tables-zh (option)
    * xfonts-intl-chinese
    * xfonts-intl-chinese-big   
    * ttf-arphic-gbsn00lp
    * ttf-arphic-gkai00mp
    * ttf-arphic-bkai00mp
    * ttf-arphic-bsmi00lp

2) System -> Preferences -> Startup Applications
Startup Programs Tab -> Add Button
Startup Command: scim -d

3) sudo apt-get install msttcorefonts (if you encounter *Checksum  mismatch for arial32*.*exe*, *aborting*! error, do a remove and install again)

4) im-switch -z fr_FR -s scim (if you are french, en_US for USA. you get yours by using "locale" in your console)

5) log again (or ctrl alt backspace is you have installed dont zap)


---

### Post by FatalChaos on 2009-12-29
In Ubuntu 9.04 (Karmic Koala) ibus is supposed to replace scim as an input manager I think. Go to system -> administration -> language support and install the Chinese language (simplified or traditional, doesn't matter). Then set keyboard input system to ibus. Next, go to system -> ibus preferences, and click on the input method tab to add Chinese. If it asks to start the ibus daemon, do that, and it may also ask you to add some lines to the bashrc file in your home folder. If you can't get ibus to work, make sure to do that too, although ibus worked w/o doing that for me.

---

### Post by nightfall77 on 2010-07-04
can someone tell me where to get the chinese input package?
i just install ubuntu today and have no idea where to look for it.
thanks for your help.

---

### Post by areskz on 2010-07-04
**nightfall77**,
Go to System -> Administration -> Language Support, then click "Install / Remove languages...", find 'chinese' and tick all boxes at the bottom of the window (one of them is 'input'). Press "Apply changes", Ubuntu will download all the neccessary packages.

Then, in "Language & Text" windows, set "Keyboard input method system" to "ibus". Some can advise you set it to "scim", but I prefer "ibus". It is easier to configure, I think.

Feel free to ask questions.

---

### Post by nightfall77 on 2010-07-05
Thanks, man that works !!:D

---

### Post by Koshakee on 2010-08-17
Hi, I've followed the instructions to try and get ibus working but still don't know how to change the language. I have installed the Chinese language package and ibus and done the bit above that says, "Then, in "Language & Text" windows, set "Keyboard input method  system" to "ibus"."

Where do I go from here? Thanks!

---

### Post by gnulab on 2010-11-22
> **Koshakee said:**
> Hi, I've followed the instructions to try and get ibus working but still don't know how to change the language. I have installed the Chinese language package and ibus and done the bit above that says, "Then, in "Language & Text" windows, set "Keyboard input method  system" to "ibus"."

Where do I go from here? Thanks!

In order to switch input method, the default is hotkey is CTRL + SPACE.

---

