---
title: "howto: _THE_ Firefox howto"
date: 2005-06-18
forum: Outdated Tutorials &amp; Tips
---

### Post by notos on 2005-06-18
- 9/7/2005 : Updated to make it easy


[size=5]Enable Extensions[/size]
If you want to install some extensions from addons.mozilla.org (needed for this howto) you should fix yourself the [bug 10681](https://bugzilla.ubuntu.com/show_bug.cgi?id=10681)

1.- open Firefox
2.- type in the address bar: about:config
4.- find general.useragent.vendorSub
3.- Set it to 1.0.4 


[size=5]Flash Player[/size]
I had to do a reset to my system now I'm running very stable with the repo plugin now to install it you type

```

sudo apt-get install flashplayer-mozilla

```


[size=5]Java Plug-in[/size]
May be one of the most useful plugin (after flash) for playing games on firefox, you should install the sun-j2re1.5 
simply by

```

sudo apt-get install sun-j2re1.5

```

some times it (for unknow reason) does not install the mozilla plugin so if it is your case (ie. you cant view java applets after apt-get sun-j2re1.5 [LOOK AT: about:plugins ) you can do it by hand
```
sudo ln -s /usr/lib/j2re1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla-firefox/plugins
```

[size=5]Media[/size]
reference: [ HOWTO: Get Streaming Media Working In Firefox, without M-Player!?](http://ubuntuforums.org/showthread.php?t=38703)
in place of installing all the media plugins i will go for a more elegant way to view stream media

frist if you dont have the codecs you cant view videos even on a media player so 
```

 sudo apt-get install w32codecs
 sudo apt-get install gstreamer0.8-plugins
 sudo apt-get install gstreamer0.8-lame
 sudo apt-get install lame
 sudo apt-get install sox
 sudo apt-get install ffmpeg
 sudo apt-get install mjpegtools
 sudo apt-get install vorbis-tools
 gst-register-0.8

```

install VLC, MPlayer, Xine-ui, Totem-xine,  or any other Media player you want you can even install them all

also for audio I recomend beep-media-player as it uses the GTK2 Engine (XMMS uses the ugly GTK1 :P) and its actualy a [fork](http://en.wikipedia.org/wiki/Fork_%28software_development%29) its almost compatible with XMMS:P

```

 sudo apt-get install beep-media-player #for audio player beep-media-player
 sudo apt-get install vlc #for vlc
 sudo apt-get install xine-ui #for xine-ui
 sudo apt-get install mplayer-i386 #for MPlayer*

``` 

[size=2]*reference to other posts in this forum, or beter compile it [/size]

now install realplayer for rm (Real Media) files  
```

 sudo apt-get install realplayer

```

Go To: [https://addons.mozilla.org/extensions/moreinfo.php?id=446](https://addons.mozilla.org/extensions/moreinfo.php?id=446)
And Install the MediaPlayerConnectivity plug-in for Firefox restart firefox and it will run the auto config automaticaly (duh) you may want to configure it yourself to fit your needs

[size=5]Acrobat Reader[/size]
Maybe the painless plugin instalation
```

 sudo apt-get install acroread mozilla-acroread 

```
done ... you dont think its a joy things just works? :P


[size=5]Tweak[/size]
Reference: [HowTo: Tweak Firefox!](http://ubuntuforums.org/showthread.php?t=38646&highlight=firefox)
Frist of you may want to install [ChromEdit](http://cdn.mozdev.org/chromedit/) to make your life Easier

now go to [http://www.testingreflections.com/node/view/1549](http://www.testingreflections.com/node/view/1549) and copy whenever fit your needs :P 
[http://flickr.com/photos/notos/19842994/](http://flickr.com/photos/notos/19842994/)
[img]http://photos16.flickr.com/19842994_081c7b4def_o.png[/img]

[size=5]Unstable FireFox[/size]
Reference: [Firefox randomly dying](http://ubuntuforums.org/showthread.php?t=41031&page=3&pp=10)

If you, **AND ONLY IF**, have experienced Bad Performance (Like Crashing or random-Dying) Of Firefox ITs not normal Firefox makes this ... even any other APP (if you come from win like me you may say "bah a crash i only restart it") but not. 
if a progran any program crash you can report it or ask if any one experiences any thing like that so developers can  build a better more stable system.

Now If FireFox crashes its because a bug a error if you have Update 2 of the kernel you may downgrade to original Ubuntu Hoary Kernel. DO this

[QUOTE=kassetra]1. Open Synaptic.
2. Do a search for Linux.
3. Click the little button above the boxes that show you what's been installed.
4. You should see one or two "linux-headers-2.6.10-5" (one with an extra -k7 after it as well, if you're on an athlon.) You should also see one or two "linux-image-2.6.10-5" (one with -386, possibly, and another with -k7)
5. Click on the first one in the list (for me, it's linux-headers-2.6.10-5) so that it is highlighted.
6. Go to Package->Force Version...
7. In the drop-down box, choose 2.6.10-34 (hoary)
8. Click on the "Force Version" button.
9. Do the same thing for the other ones in this list, "linux-headers-2.6.10-5-k7," "linux-image-2.6.10-5-386," "linux-image-2.6.10-5-k7." Until all of them are marked with a "downgrade" box (little arrow pointing down.)
10. Click Apply.
11. When finished, reboot.[/QUOTE] 

after that you may want to put the kernel on "HOLD" mode so it does not upgrade
just type
```

 echo packagename hold | dpkg --set-selections

```
for each kernel package that you downgraded

so for me it was
```

echo linux-headers-2.6.10-5 hold | sudo dpkg --set-selections
echo linux-headers-2.6.10-5-686 hold | sudo dpkg --set-selections
echo linux-image-2.6.10-5-386 hold | sudo dpkg --set-selections
echo linux-image-2.6.10-5-686 hold | sudo dpkg --set-selections

```
when you want to un-hold the kernel images/headers (ie when the new patch is relased or when you upgrade to breeze) just change "hold" with "install" 

this fixed my firefox no more crashes for me, so no more Opera or Links :P

[size=5]Other HowTo[/size]
[HOWTO: Totem embeded with mozplugger (At Last!)](http://ubuntuforums.org/showthread.php?t=17727&highlight=Firefox)
[SCRIPT: Take back the Firefox & Thunderbird logo](http://ubuntuforums.org/showthread.php?t=34354&highlight=Firefox)
[HOWTO: Nice firefox forms.](http://ubuntuforums.org/showthread.php?t=22034&highlight=Firefox)
[HOWTO: Set up Java Runtime Environment with Firefox autopackage](http://ubuntuforums.org/showthread.php?t=39555&highlight=Firefox)
[Mozilla Firefox - ubuntuforums.org search plugin](http://ubuntuforums.org/showthread.php?t=34643&highlight=Firefox)



Well this concludes my short (?) way to tweak and personalize Firefox i hope it helps you if any question... ask (duh)

Also i will be updating this as i find interesting things to do, if you think i should add some thing ask for it or PM me

note:Sorry for my engrish ... engrish not my natural languaje :( if you want help me fix my poor-english PM me

---

### Post by Dax0r on 2005-06-18
good job

---

### Post by notos on 2005-06-18
thank you i hope it helps :)

---

### Post by rider343 on 2005-06-18
Very good work :)

---

### Post by luca_linux on 2005-06-19
Great! Very good job!

---

### Post by nickless on 2005-07-05
nice thread, but there is something missing to be the "complete guide" :D

How do I get Firefox to open a new tab when I click a link?

Edit the file /etc/mozilla-firefox/mozilla-firefoxrc and change the line that reads FIREFOX_OPEN_IN="window" to be FIREFOX_OPEN_IN="tab". There is a comment about this on the line above.

Found it in the [ubuntu FAQ](http://www.ubuntulinux.org/support/documentation/faq/faqsection_view?section=Using%20Ubuntu)

edit: actually it didn't work for me, but I found out, that one can also change this in firefox :D

---

### Post by mike998 on 2005-07-05
[QUOTE=nickless]nice thread, but there is something missing to be the "complete guide" :D

How do I get Firefox to open a new tab when I click a link?

Edit the file /etc/mozilla-firefox/mozilla-firefoxrc and change the line that reads FIREFOX_OPEN_IN="window" to be FIREFOX_OPEN_IN="tab". There is a comment about this on the line above.

Found it in the [ubuntu FAQ](http://www.ubuntulinux.org/support/documentation/faq/faqsection_view?section=Using%20Ubuntu)

edit: actually it didn't work for me, but I found out, that one can also change this in firefox :D[/QUOTE]

Alternately, Middle click on a link...

---

### Post by PMO6022 on 2005-07-05
The easiest way to get tab options is to:

type: **about:config** in the address bar
search for **browser.tabs.showSingleWindowModePrefs**
double click the result which will set the value to [b]true

[/b]Now when you go to edit->preferences->advanced there will be more options under tabbed browsing, of particular interest is "force links that open new windows to open in a new tab" Selecting that will essentially give you single window browsing. Links should no longer spawn new instances of firefox.

---

### Post by Williams477 on 2005-07-09
Hey, I get everything working fine until this step: enter and type /usr/lib/mozilla-firefox.

The terminal just comes up and says it's a directory. For example:

> tony@ubuntu:~/workdir/install_flash_player_7_linux$ /usr/lib/mozilla-firefox
bash: /usr/lib/mozilla-firefox: is a directory


I also get this:

> tony@ubuntu:~/install_flash_player_7_linux$  sudo ./flash-player-installer
sudo: ./flash-player-installer: command not found

---

### Post by geearf on 2005-07-10
Hello,

my firefox seems a bit unstable : 
- sometimes it crashes when using the mediaplayer plugin or a certain java webpage
- i cannot click on the button of this page : 
[http://roxy.en.norvege.free.fr/index_2.php?page=photos](http://roxy.en.norvege.free.fr/index_2.php?page=photos)

while i have no problem with konqueror.

I tried with my profile and a new one of course.
Also i feel like FF is very slow, and sometime it takes a huge amount of RAM.

Thanks for any information,

---

### Post by notos on 2005-07-11
check what its your kernel version there is a know problem with update-2 of the kernel 

it the how to there is a step on how to downgrade to kernel :) this mainly will slove yu problem :)

---

### Post by geearf on 2005-07-11
I was using a 2.6.12 non ubuntu, but now i am using a 2.6.12 ubuntu.

Did not crash for the moment, but i still cannot use the website mentioned earlier (while it worked with ff on windows).

Thanks :)

---

### Post by nickless on 2005-07-17
Why are there more than one package for acroreader firefox plugins? I mean I have installed acroread-plugin instead of the mozilla-acroread, that is suggested here. Is there a performance difference?

---

### Post by Matchless on 2005-07-17
I have downloaded the latest Firefox 1.05 from the Mozilla site and executed the file, it installed the new version automatically. It works like a charm on Kubuntu. Extentions now also install properly, such as Flashgot etc.
Enjoy
Matchless  :smile:

---

### Post by Sianis on 2005-07-17
Hi!

Your howto is very good! Nice job, thx, but i have a little probleme. I can't install the flashplayer with apt-get cause it doesn't find it. What i need write + in the sources.list? Please help me! Thank you

---

### Post by bored2k on 2005-07-17
[QUOTE=Sianis]Hi!

Your howto is very good! Nice job, thx, but i have a little probleme. I can't install the flashplayer with apt-get cause it doesn't find it. What i need write + in the sources.list? Please help me! Thank you[/QUOTE]
 [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

> ## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

---

### Post by Sianis on 2005-07-17
[QUOTE=bored2k][http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)[/QUOTE]

Thanks!

Before i read this, I download the *.deb file and I installed it, now it works good, but I thanks the answer. 

So the HOWTO is very good NOW!  :-P Thanks the help!

---

