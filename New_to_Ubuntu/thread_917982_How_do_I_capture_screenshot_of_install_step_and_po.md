---
title: "How do I capture screenshot of install step and post in thread?"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by cbarnes48 on 2008-09-12
I have been told there are Linux utility programs that allow me to capture a (full?) screenshot and then paste into a thread. My problem is simply this. What if I run into a problem **_during_** the actual install process and need to get help at that particular point or step? A picture or screenshot or what I am seeing and baffled by at that very moment in the installation process from a live DVD would spare me at least a few hundred words!

So, since my version of Unbuntu - Hardy Heron 8.04.1 isn't even (fully) installed yet, it seems to me that at the point i am lost and confused installing a screen capture program is a moot point. Am I wrong here? Anotherwords, how can I use a program that needs to be installed to save endless words and confusing members if my version of Ubuntu hasn't even been fully installed yet?  :confused: :confused:

One last thing, please. I keep on asking everwhere I can on forums and looking in all kinds of documentation, including wiki, how I can locate and then actually execute or run especially video and audio plugins/codecs. I have more than enough information and opinions on how to install programs, including plugins and program applications, but can hardly find anything I can understand in newbie terms on even finding out what directory and path the software has been installed in! :mad: :mad:

I'm running Hardy Heron on an Acer Aspire desktop PC with an AMD64 prcessor and 2GB of SDRAM and one 160GB SATA hard drive.

If I'm so dumb - even as a complete newbie and with as "user friendly" a distro Ubuntu is - how will I ever learn how to use it proficiently? Very discouraged and lost in all the endless documentation. Frustrated as hell, too. As I have said before, it is impossible for me to believe that non-newbies have just installed necessary plugins and other software and then just let them sit unused on their hard drive(s). All I want to know, once again, is to find out where they were installed in the first place and then what to do to actually run them. Every time I have tried this with plugins, I have failed. I go back to the page that has the button saying "Missing Plugings" only to find that same button and/or icon there and still unable to view the clip/flash presentation/streaming video/movie, or hear any sound coming out from any of these.  

Last word. If I knew how to even choose the right installation options for doing a **_manual_** installation, I would definitely supply some screenshots to help me and all of you. Again, how can I possibly install my copy of Unbuntu if I'm not even sure what to during the actual installation process and can't capture critical screenshots of where I just know what to do?  :sad: Thanks to all who even ready this post, I figure that's the only way I'll possibly find somebody who can shed some light on my problems for me. My goal is still to offer some and any help I can, newbie or not, as soon as I can.

cbarnes48

---

### Post by SunnyRabbiera on 2008-09-12
I think the screnshot tool is on the live CD but since it is a live seeion you may want to save the snapshots it makes onto another disk.
If you have a computer with 2 CD drives, one a burner and one standard CD drive (or DVD drive or whatever) you could save your snapshots to a disk.
its easier if you have an external though.

---

### Post by abn91c on 2008-09-12
if you are doing a GUI install from the live cd press prt scr key on your keyboard

---

### Post by Rhubarb on 2008-09-12
To take a screenshot, you don't need to install anything, it's already installed:
Applications --> Accessories --> Take Screenshot

Most programs once installed can be found in the Applications menu, otherwise they can be accessible from the terminal (Applications --> Accessories --> Terminal)
I won't say how to runs programs in the terminal just yet, you need to be more familiar with other easier aspects of Ubuntu first.

As for getting video codecs installed and running, generally you can try and double click on an mp3 / video, and it'll prompt you to install the codecs in an easy manner.
Otherwise, you can just follow some of the tutorials online that should tell you to install some packages, usually gstreamer*.

Hope this starts you off a bit better, and of course, explore around, google around for answers, and ask any questions you like in this forum.

---

### Post by DFlame on 2008-09-12
That's quite a bit of questioning. We'll start at the top.

What's the reason for attempting a "manual" install? I'm assuming you just want to set up the partitions of your hard disk manually wihtout causing damage. Are you attemping to dualboot or something similar? Giving us more information on exactly what you are trying to do here will help us give you some tailored instructions :)

There is a screenshot utility that should be available in the live environment. You can just call it up by pressing the "print screen/PrtSc" key on your keyboard, and save the file. Once you have saved that file, you can upload it to a photo hosting site of your choice, and link it here by placing:

```
[img]link to image[/img]
```

in your post.

If all goes well and you get it installed, codecs are a very easy thing to install nowadays. You need only open Synaptic Package Manager, search for a package called "ubuntu-restricted-extras", mark it then hit apply.

Post up some more info as stated and we'll see how far we get :)

DFlame

---

### Post by cdtech on 2008-09-12
> One last thing, please. I keep on asking everwhere I can on forums and looking in all kinds of documentation, including wiki, how I can locate and then actually execute or run especially video and audio plugins/codecs.
These can be installed through "Synaptic Package Manager" or by opening a terminal and typing:
**sudo apt-get install ubuntu-restricted-extras**

---

### Post by wolfen69 on 2008-09-12
i can't help with the screenshot issue during install, but what problems are you having during install? as far as installing codecs, see [this]("http://www.psychocats.net/ubuntu/") it has documentation for most things. also see [www.ubuntuguide.org](www.ubuntuguide.org)

remember to be patient. after a month or two more using ubuntu, you will start to settle in and get used to it. PATIENCE IS THE KEY. it's not life and death, learn and have fun with it.

---

### Post by meindian523 on 2008-09-12
And about where installed programs go,they go to /usr/sbin or /usr/bin.All programs usually create a menu entry,if not,you can press Alt+F2 and type in the name of the program to run it.

---

