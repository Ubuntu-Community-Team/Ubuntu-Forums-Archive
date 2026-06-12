---
title: "can i run compiz effects ?"
date: 2013-03-31
forum: New to Ubuntu
---

### Post by amhndu on 2013-03-31
Hi,I have a fairly old computer running Ubuntu 12.04.1 with the following specs- 
Pentium 4 processor, 1 GB RAM ,Intel Corporation 82915G/GV/910GL Integrated Graphics Controller with 128 MB of video ram.  So can I run compiz effects like wobbly windows without much affecting my user experience and not lag.
If I can run ,then what effects can I run ? Please try to list those effects.


Thanks in advance.:)

PS. Sorry if I posted this in an inappropriate section.

---

### Post by ManamiVixen on 2013-03-31
No, you cant. Intel chipsets older than the i915 are no longer supported and so you may loose graphics in the coming updates to 12.04. Like by the 12.04.3 release.

---

### Post by sudodus on 2013-03-31
I doubt that you can do it with Ubuntu because it is made for more powerful computers. But I do it in computers with even less horsepower with Knoppix, so I suggest that you download and test it :-)

Lubuntu 12.10 or Xubuntu 12.04.2 LTS would be the best choices of the Ubuntu flavours. Or LXLE which is a special LTS edition based on Lubuntu 12.04.

What is best for you depends on what you want to do with the computer, what you like and what you need. If you like compiz effects, select Knoppix. If you want a fast and useful computer and can trade off some eye-candy, select Lubuntu 12.10. If you have time and are interested, download several iso files, make CD/DVD/USB drives and try them live before deciding to install anything. Knoppix is designed to run live or persistent live "poor man's install".

---

### Post by deadflowr on 2013-03-31
The chip's not the problem.
The video ram is.
You need at least 256, having only 128 is too light.

---

### Post by amhndu on 2013-03-31
Thanks for all your replies,I guess I can stick with ubuntu without those eye-candies.

---

### Post by monkeybrain2012 on 2013-03-31
Why not install lubuntu instead? Works great with old machines.

---

### Post by amhndu on 2013-04-01
Well , What are the major differences between other ubuntu variants and ubuntu ?
For better perfomance can I install other environments instead of unity because I'm not much interested in having another fresh install of an OS, after a week or two I have finally customized ubuntu with many softwares etc. If I do install lubuntu etc. I would've to do that again.
As ManamiVixen said does my chipset really going useless in ubuntu after 12.04.3 ?,I know already that Intel doesn't support it officially

---

### Post by sudodus on 2013-04-01
The most evident difference is the desktop environment. There are also different choices of software that are bundled in the iso file. It is possible to install software from the same repositories and this includes the desktop environments. So you can install Lubuntu-desktop with the whole package or only LXDE, the ultra light-weight desktop environment, or only Openbox, the window manager, which gives you an opportunity to play more demanding video or use more memory for the application programs, than with standard Ubuntu with Unity or Gnome shell.

You select desktop environment at the log in screen (click on the circular button near the password window).

```
 sudo apt-get install lubuntu-desktop
```
```
 sudo apt-get install lxde
```
```
 sudo apt-get install openbox
```

There are methods to remove these things and restore Ubuntu. See this link

[[COLOR=#ff0000]http://www.psychocats.net/ubuntu/[/COLOR]]("http://www.psychocats.net/ubuntu/")

Before doing this, you should*** backup your system***, because it is easy to break it but hard to restore it.

I don't know how much *ManamiVixen* knows about the future plans of Ubuntu, but usually the LTS versions are very stable. Things might stop working between versions, but very seldom within them. Ubuntu 12.04.3 will be very similar to the present 12.04.2, it will include some more bug-fixes and security updates. You can download and compare 12.10 which was released last October and the next one, 13.04, to be released this month.

---

### Post by amhndu on 2013-04-01
thank you very much for that info.
BTW can you also tell me about other ubuntu variants , so i can choose from then the most appropriate.

And does these light weight environments have compiz etc. eye candies that I CAN run ? :) (though not a necessity for me)

is lubuntu = light ubuntu ?

---

### Post by amhndu on 2013-04-01
Ok , one last question , running those commands only installs the environments or all those packages the original distribution has ?

---

### Post by deadflowr on 2013-04-01
> **amhndu said:**
> Ok , one last question , running those commands only installs the environments or all those packages the original distribution has ?

Here's the lists of what packages get installed with each one

[lubuntu-desktop]("http://packages.ubuntu.com/precise/lubuntu-desktop")

[lxde]("http://packages.ubuntu.com/precise/x11/lxde")

[openbox]("http://packages.ubuntu.com/precise/openbox")

---

### Post by sudodus on 2013-04-01
> **amhndu said:**
> thank you very much for that info.
BTW can you also tell me about other ubuntu variants , so i can choose from then the most appropriate.

And does these light weight environments have compiz etc. eye candies that I CAN run ? :) (though not a necessity for me)

is lubuntu = light ubuntu ?
I think it is best to try. Either download the iso files or install the desktop environments and run them yourself :-)

Lubuntu is Ubuntu with LXDE and it is light. Xubuntu is medium light and a little more fancy. I guess it is possible to install compiz, but I think very few people run it with Lubuntu and Xubuntu. It is better to choose a distro that comes with it.

---

### Post by grahammechanical on 2013-04-01
Those Compiz effects that you ask about are now discontinued. You still have Wobbly Windows and other effects on 12.04 but you have to install Compiz Configuration Settings Manager and as previous mentioned you need a graphic adapter that can handle those effects. But they are not available from 12.10 onwards. There are not enough developers to maintain those Compiz effects.

Regards.

---

### Post by monkeybrain2012 on 2013-04-02
> **grahammechanical said:**
> Those Compiz effects that you ask about are now discontinued. You still have Wobbly Windows and other effects on 12.04 but you have to install Compiz Configuration Settings Manager and as previous mentioned you need a graphic adapter that can handle those effects. But they are not available from 12.10 onwards. There are not enough developers to maintain those Compiz effects.

Regards.

Most effects (wobbly windows in particular) are still in 13.04 daily build and 12.10 (with Unity)

---

