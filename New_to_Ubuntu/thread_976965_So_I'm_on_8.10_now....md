---
title: "So I'm on 8.10 now..."
date: 2008-11-09
forum: New to Ubuntu
---

### Post by Obero on 2008-11-09
Ahh! So I finally installed a fresh copy of Ubuntu 8.10. Now what? But seriously, I have a list of things I need to do, this is I&#8217;m pretty much the titular subject of this forum&#8212;an absolute beginner&#8212;so I have no idea how to do these things. So, please tell me specifically how I can do this or even what I&#8217;m asking is possible. Thanks in advance.

Opera&#8212;I don&#8217;t know about you guys, but I love this browser. It&#8217;s awesome and I want it. How do I get it on Ubuntu?

Flash&#8212;I&#8217;ve heard that you can get a plug-in for Firefox. Yes I&#8217;d like that, but as said before I&#8217;m also using other browsers so how do I generally install it as a program, not a plug-in.

Adobe Reader & Java&#8212;you know the drill.

MSN Messanger&#8212;I&#8217;ve heard that Windows Live unfortunately doesn&#8217;t work with Ubuntu, so what alternatives are there and how can I install them right now? What open-source instant messaging software would you recommend?

VLC&#8212;I, too, already know that Windows Media Player doesn&#8217;t correspond with Ubuntu (duh!) so this is actually a personal question to you. Would you recommend VLC, or something else? Oh and how do I get whatever you recommend?

Video-editing software&#8212;pretty clueless on this one; I actually don&#8217;t know if there IS anything on Ubuntu that can edit videos (you know add effects, sounds, etc.). IF there is, what is it and how do I install it right now?

Separate accounts&#8212;how could I forget! I need separate accounts for basically everybody in my family. Please tell me how I can do this! In addition, how do I make (like in Windows XP) some users administrators and others non-administrators?

My printer&#8212; actually, this is mainly a hardware question. I&#8217;ve pretty much accepted that most printers work automatically, but if I change ink cartridges, will that work with Ubuntu too? I need to change them soon, and I&#8217;m wondering if I have to do something special with Ubuntu?

Fonts&#8212;How do I install them to make them &#8220;default.&#8221; Basically useable on everything that will allow font formats. Is there something I need to know about fonts and Ubuntu? Also I need all of Windows default fonts.

Okay, I think that covers it. Anything you want to recommend? Did you do anything when you rebooted to 8.10 that I&#8217;ve not already asked? Any programs or software that you would recommend?

Thanks a lot if you&#8217;ve answered my questions. I&#8217;m a total newbie, and I figured I might as well throw everything at you into one thread rather than gradually making threads that will only be wasteful. Plus, perhaps other newbies will look here for help as well!

---

### Post by randy78 on 2008-11-09
Welcome to Ubuntu!

Here are some links that will get you started:

[http://degreedirectory.org/articles/13_Of_the_Best_Linux_Tutorials_and_OpenCourseWare_on_the_Web.html]("http://degreedirectory.org/articles/13_Of_the_Best_Linux_Tutorials_and_OpenCourseWare_on_the_Web.html")

[http://ubuntuguide.org/]("http://ubuntuguide.org/")

[http://www.psychocats.net/ubuntu/index.php]("http://www.psychocats.net/ubuntu/index.php")

[http://www.ss64.com/bash/]("http://www.ss64.com/bash/")

[http://www.medibuntu.org/]("http://www.medibuntu.org/")

**PS: DO NOT RUN sudo rm -rf / under ANY circumstance! It will delete your entire Ubuntu install**

---

### Post by 73ckn797 on 2008-11-09
Read the Sticky threads, read the Ubuntu Help resources. Read the Absolute Beginners threads. You will find direction to help in answering your questions. 

Take advantage of the search features.

Welcome to Ubuntu.

):P

---

### Post by LegendofTom on 2008-11-09
OK, you've got a lot here so I think I hit each thing bullet like:

-Opera works fine with Ubuntu, just run *sudo apt-get install opera* in your handy terminal
-the new Flash Player 10 works great, download the deb file from their website
-java you can get from add/remove programs, search java, I don't know what you would need adobe reader for because most things are viewable just fine
-Pidgin works great for that
-VLC is fine for video, banshee is what I use for both music and video, rhythmbox and totem work well also
-not sure about video-editing, not really my gig
-To add or edit accounts go System -> Administration -> Users and Groups
-Printer should be fine, if you need to change the cartridge just do it, Ubuntu won't mind
-I'm sure there is a way to download fonts, but I'm not really sure

Hope that helps, and that your Ubuntu experience is an enjoyable one.

Tom

---

### Post by 73ckn797 on 2008-11-09
ALSO:

Look through the available programs under: System/Administration/Synaptic Package Manager.

You will be surprised at what is there and can be just what you are looking for in applications.

---

### Post by zzHanks on 2008-11-09
Another link that might be useful [Comprehensive Multimedia & Video Howto.]("http://ubuntuforums.org/showthread.php?t=766683")

---

### Post by Metaleks on 2008-11-09
**Opera**
[http://www.opera.com/download/index.dml?platform=linux](http://www.opera.com/download/index.dml?platform=linux)

**Flash**
Type "sudo aptitude install flashplugin-nonfree" in terminal.

**Adobe Reader & Java**
Instead of Reader, install Evince. It's in the repos. You can also do the same with Java (depending on how you want to use it).

**MSN Messanger**
You want Pidgin, or aMSN. Pidgin is constantly getting better and can support multiple protocols (msn, aim, etc), but doesn't have the fancy things like winks, msn games, voice clips, or webcam support. Although, we're getting there! aMSN is much closer to what you want, but if it were up to me I'd go for pidgin.

**VLC**
VLC is in the repos. It's obviously one of the best media players out there. Ubuntu also comes with Totem, though. It's an amazing player. Just install the codecs from the repos if you end up deciding to use Totem (it doesn't play some codecs by default due to licensing issues). Another great alternative is mplayer. 

**Video Editing**
Actually there is quite a bit! Kdenlive, PiTiVi, and the mega professional editor (and extremely hard to learn) Cinelerra. I'd go with Kdenlive as thats the closest thing (and even better!) than Windows Movie Maker. Also, a new video editor is currently in development by some of the people involved in Ubuntu Studio. But don't expect that for a while, they started recently.

**Separate accounts**
For root (admin), you don't need to worry about. As long as you know the password you can administer users and the system without ever having to officially log in as root. You can add new users through the System > Administration > Users and Groups menu. Ubuntu also comes with a quick user changer that you can add to your panel to change users with 1 click.

**Printer**
Shouldn't matter. It'll work!

**Fonts**
Run the command "sudo apt-get install msttcorefonts" in terminal without the quotes. To install fonts normally, download the font and run the command "sudo mv YOURFONTLOCATION /usr/share/fonts/" and then run "sudo fc-cache -f -v" to update the system.

> Okay, I think that covers it. Anything you want to recommend? Did you do anything when you rebooted to 8.10 that I&#8217;ve not already asked? Any programs or software that you would recommend?
If you have any problems just come back here! I'd recommend learning a little about the terminal as a beginner just starting out in Ubuntu. You'll find that it is very useful, and that it gives you much more control over your system. As for programs, I'd recommend to ditch opera, but that's just me :) Any other programs you need?

Welcome to community!:)

---

### Post by 73ckn797 on 2008-11-10
If command line input ain't your bag, the Microsoft core fonts can be found in Synaptic Package Manager and once marked to install will install for you.

---

### Post by zvacet on 2008-11-10
In terminal type 

```
sudo apt-get install ubuntu-restricted-extras
```

add medibuntu repo to your source list by typing 

```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

After that go to the synaptic and in search box type w32 codecs ( if you run 64 bit version it will be w64).That way you will install a/v codecs.

VLC is in synaptic,so install it from there.

Download Opera from their web site by choosing you version (in your case ubuntu interpid).

In system>admion>software sources> go to the third party tab and check partner repository.Reload.
In synaptic type **adobe-flashplugin**.This is latest version and it will remove flashplugin-nonfree but that is O.K.

---

