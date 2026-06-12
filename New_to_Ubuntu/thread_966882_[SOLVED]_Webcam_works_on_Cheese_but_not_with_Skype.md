---
title: "[SOLVED] Webcam works on Cheese but not with Skype"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by idodos on 2008-11-01
As the title says, the webcam seems to work well but Skype has trouble with using it, I just get a weird picture..

Any help appreciated!

---

### Post by idodos on 2008-11-02
bump!

---

### Post by idodos on 2008-11-02
Bump!!

---

### Post by Sef on 2008-11-02
Please wait for 24 hours before bumping your post.

What kind of webcam do you have?

---

### Post by spiderbatdad on 2008-11-02
see this launchpad bug report if you are using intrepid:[https://bugs.launchpad.net/debian/+bug/260918](https://bugs.launchpad.net/debian/+bug/260918)

That is; try to start skype with the following command from a console depending on your type of webcam:
```
$ LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
$ LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype
```

---

### Post by idodos on 2008-11-02
Genius VideoCam eye

and how exactly do i use that command?

---

### Post by spiderbatdad on 2008-11-02
I'm guessing that is a v4l2 cam. So open a command line: Applications>>Accessories>>Terminal. Copy/paste this command...no guarantees it will allow your cam to run with skype. Again the bug is specific to intrepid. I was using skype video fine with 8.04.

```
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype
```
I recommend reading the entire report. There are other package recommendations you may need to add.

---

### Post by idodos on 2008-11-02
> **spiderbatdad said:**
> I'm guessing that is a v4l2 cam. So open a command line: Applications>>Accessories>>Terminal. Copy/paste this command...no guarantees it will allow your cam to run with skype. Again the bug is specific to intrepid. I was using skype video fine with 8.04.

```
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype
```
I recommend reading the entire report. There are other package recommendations you may need to add.

it worksssss
thanks!
is there a way to make the skype shortcut start with this command?

---

### Post by spiderbatdad on 2008-11-02
> **idodos said:**
> it worksssss
thanks!
is there a way to make the skype shortcut start with this command?

GRRRR! congratulations! it doesn't work for me. I'm still waiting for an upstream fix, but it seems to work for at least 50% of those contributing to the bug report. You can edit your launcher command. Add it to your panel, right click on it, select properties, and put it in the command box. :)

Please mark your post Solved.

---

### Post by idodos on 2008-11-02
> **spiderbatdad said:**
> GRRRR! congratulations! it doesn't work for me. I'm still waiting for an upstream fix, but it seems to work for at least 50% of those contributing to the bug report. You can edit your launcher command. Add it to your panel, right click on it, select properties, and put it in the command box. :)

Please mark your post Solved.

before that.. one more thing, the picture colors aren't as they used to, it's a bit darger and greenish.. is there a way to change that?

edit:
when i add the command it gives me an error, something about a child proccess

---

### Post by spiderbatdad on 2008-11-02
hmmm. not sure. of course ambient conditions affect the picture. You might try adjusting some of the properties with your cheese or camorama application to see if it works. As for adjusting the picture quality on skype. I just don't know sorry.

---

### Post by idodos on 2008-11-02
ok, when i try to run skype from thet shortcut i get the following error:

Details: Failed to execute child process "LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so" (No such file or directory)

seems like it doesn't notice the "skype" at the end?

---

### Post by spiderbatdad on 2008-11-02
google:
[http://forum.skype.com/index.php?showtopic=106357](http://forum.skype.com/index.php?showtopic=106357)

---

### Post by spiderbatdad on 2008-11-02
> **idodos said:**
> ok, when i try to run skype from thet shortcut i get the following error:

Details: Failed to execute child process "LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so" (No such file or directory)

seems like it doesn't notice the "skype" at the end?

looks more like it isnt seeing it period. You can remove the LD_PRELOAD= but the i think you'll get a permissions error. Maybe make the flie executable:```
sudo chmod +x /usr/lib/libv4l/v4l2convert.so
```and try again.
Sorry, I'm not an expert.

---

### Post by spiderbatdad on 2008-11-02
I'm having the same problem. At least it runs fine from the terminal...can't have everything all at once.:)

---

### Post by kentkarl on 2008-11-17
- create a small start script (e.g. ~/start_skype)
- insert the line "LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype"
- chmod 700 ~/start_skype
- use this script for launcher, autostart, etc...

---

### Post by spiderbatdad on 2008-11-17
the problem seems to do with preload permissions. I actually run "sudo LD_PRELOAD...

---

### Post by kentkarl on 2008-11-19
Ubuntu 8.10 an no such problem here. "LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so" sets imho only a variable and you should only need the rights to read /usr/lib/libv4l/v4l2convert.so. Not to set the variable but to preload the shared object.

# ls -la /usr/lib/libv4l/
drwxr-xr-x   2 root root  4096 2008-10-29 23:59 .
drwxr-xr-x 202 root root 69632 2008-11-18 17:20 ..
-rw-r--r--   1 root root  5296 2008-10-10 15:57 v4l1compat.so
-rw-r--r--   1 root root  5352 2008-10-10 15:57 v4l2convert.so

---

### Post by scoopy on 2008-11-20
my genius eye 110 works well on cheese but not on skype too.  in skype get a mostly green background with some static movement.  it seems to be trying to show something because the static will change when there is movement in front of the webcam

I'm running 8.10

when i run skype from terminal i get some sort of blue tooth failure?   and then:
[HTML]Skype Xv: ports available: 64
Skype SShm: SShm support enabled
Skype Xv Using Sv port 355[/HTML]

any idea friends?

---

### Post by ciacco on 2009-03-24
Hi,

I tried your suggestions, but when I start skype it prints this message:

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

and

LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype
ERROR: ld.so: object '/usr/lib/libv4l/v4l2convert.so' from LD_PRELOAD cannot be preloaded: ignored.

Is it a problem of skype? I mean, when I try to do these with camorama or mplayer everything works.

Thanks.

Ciao

---

### Post by newseamus on 2009-03-25
> **kentkarl said:**
> - create a small start script (e.g. ~/start_skype)
- insert the line "LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype"
- chmod 700 ~/start_skype
- use this script for launcher, autostart, etc...

I am trying to create a custom launch for my skype with these instructions.
I am not sure what I do with this info...

I have tried adding this stuff to the skype launcher command (under properties) but nothing seems to work.

Any help is appreciated!

PS.
I can launch skype correctly from the terminal, but the launcher doesn't start skype with the webcam correctly.

PROBLEM SOLVED! -in this thread:
[http://ubuntuforums.org/showthread.php?t=1097073&highlight=create+launcher](http://ubuntuforums.org/showthread.php?t=1097073&highlight=create+launcher)

---

### Post by sinuk on 2009-04-14
> **ciacco said:**
> Hi,

I tried your suggestions, but when I start skype it prints this message:

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

and

LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype
ERROR: ld.so: object '/usr/lib/libv4l/v4l2convert.so' from LD_PRELOAD cannot be preloaded: ignored.

Is it a problem of skype? I mean, when I try to do these with camorama or mplayer everything works.

Thanks.

Ciao
Hi,


i'm facing the same problem, and change from :

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

to :

LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

and it works...

skype is using 32 bit lib and it seems, same as me, you are using 64 bit linux :)

Hope it helps and not too late...

Thank you and good luck.

---

### Post by ThomasU on 2009-04-29
How to launch Skype + V4L2 directly from Gnome menus so that the webcam works:
Menu System --> Preferences --> Main Menu
In the window select Internet, then Skype
Click on [Properties] button
In Command enter:
bash -c 'export LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so; skype'

---

### Post by finchmatt on 2009-05-07
> **ThomasU said:**
> How to launch Skype + V4L2 directly from Gnome menus so that the webcam works:
Menu System --> Preferences --> Main Menu
In the window select Internet, then Skype
Click on [Properties] button
In Command enter:
bash -c 'export LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so; skype'
worked perfectly for me. my webcam is ID 04fc:0561 Sunplus Technology Co., Ltd Flexcam 100, and was showing only green in Skyple. This fixed it. Thanks ThomasU

---

### Post by rka on 2009-10-11
> **spiderbatdad said:**
> see this launchpad bug report if you are using intrepid:[https://bugs.launchpad.net/debian/+bug/260918](https://bugs.launchpad.net/debian/+bug/260918)

That is; try to start skype with the following command from a console depending on your type of webcam:
```
$ LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
$ LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype
```

Thank you for this solution (found it here after some searching with Logitech 3500 camera) - both command lines works in Ubuntu 9.04 for camera testing and broadcasting, but when communicating with someone else who also has his/her camera on at the same time, Skype breaks down (strange filter-like flickering images appear before program shutdown).

Does anyone recognize this and found a solution?

Highly appreciated.....

---

### Post by scoopy on 2009-10-12
> **ciacco said:**
> Hi,

I tried your suggestions, but when I start skype it prints this message:

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

and

LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype
ERROR: ld.so: object '/usr/lib/libv4l/v4l2convert.so' from LD_PRELOAD cannot be preloaded: ignored.

Is it a problem of skype? I mean, when I try to do these with camorama or mplayer everything works.

Thanks.

Ciao

Awesome - works a treat!!!

---

### Post by benditoelqueviene on 2009-10-21
It is not solved to me.  I've an Eye 110 Genius webcam and it still gives the answer:
```
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: clase ELF errónea: ELFCLASS64
```
Skype works well with sound, i can see the another persons video, but they can't see mine.  In Options i see only one option "CIF Single Chip" but it's the right option.

I guess the problem is in the permissions.  v4l2convert.so y v4l2compat.so are owned by root and i don't know how to change that.  It happens the same with /dev/video0.

The camera works well with Cheese.

---

### Post by astathios on 2010-01-21
today i download the new version 2.1.0.81 on carmic and i faced the same problem 
so i follow ur instructions and works perfect here as well
thanks guys

---

### Post by djtechsupport on 2010-01-21
Tried all this, now when I try to load my webcam, skype just disappears.  Somewhat a noob with Linux, but familiar enough to work stuff.  Asus X83-VB with a 32bit 9.10.  Help?

---

### Post by siquad on 2010-02-13
Followed the advice in this thread, did't completely work, here's my experience in case it helps someone:
[LIST]
[*]If you get green screen, you need v4l1compat.so (read earlier in this thread on how to pre-load it)
[*]If you have 64bit ubuntu, /usr/[COLOR="Red"]lib[/COLOR]/libv4l/v4l1compat.so will point to the 64bit version, which doesn't play nicely with skype 64bit and you'll get:
[INDENT][FONT="Courier New"]ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.[/FONT][/INDENT]
So you need to use /usr/[COLOR="#ff0000"]lib32[/COLOR]/libv4l/v4l1compat.so instead
[*]/usr/lib32/libv4l/v4l1compat.so is likely owned by root, but we only care to have read/execute permissions so need something like:
sudo chmod 755 /usr/lib32/libv4l/v4l1compat.so
[*]At this point, my camera worked when I do: sudo skype, but not without sudo.
[*]I didn't like running skype with root privileges, so had to dig more into what makes sudo work. I noticed that the graphics of skype windows were different when I ran with sudo, some headscratching lead me to suspect my display driver. I remembered I had enabled the proprietary ATI/AMD FGLRX graphics driver for my display card, and I thought doing sudo might either be using the display libraries for the root account which probably isn't that proprietary driver or that it gives me permission to some ATI library that has it's permissions set wrong, not to delve into either case I decided to just disable the driver under system > administration > hardware drivers, and sure enough, the camera worked with skype without sudo. I'm not really sure what part of the ATI driver skype didn't like or didn't have permission to, and since I don't really care for any specific features of the ATI driver, disabling it is the easiest way out for me
[/LIST]

---

### Post by chowdhury.indranil on 2010-02-16
I have recently upgraded my os to ubuntu 8.10. in 8.04 there was no problem in using skype video calls. but now iam not being able to use skype video calls. the webcam is not capturing any picture. mthe test video call is unsuccessful. i have logitech quickcam pro4000. please help me to fix this problem

---

### Post by chowdhury.indranil on 2010-02-16
same problem persists, i have upgraded my os to 9.10

---

### Post by eppo on 2010-02-17
i'm having the same problem, no matter which one of those i use i get LD_PRELOAD cannot be preloaded: ignored.
is there a way to see why it can not be preloaded?

---

### Post by nonducor on 2010-05-18
> **siquad said:**
> Followed the advice in this thread, did't completely work, here's my experience in case it helps someone:
[LIST]
[*]If you get green screen, you need v4l1compat.so (read earlier in this thread on how to pre-load it)
[*]If you have 64bit ubuntu, /usr/[COLOR="Red"]lib[/COLOR]/libv4l/v4l1compat.so will point to the 64bit version, which doesn't play nicely with skype 64bit and you'll get:
[INDENT][FONT="Courier New"]ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.[/FONT][/INDENT]
So you need to use /usr/[COLOR="#ff0000"]lib32[/COLOR]/libv4l/v4l1compat.so instead
[*]/usr/lib32/libv4l/v4l1compat.so is likely owned by root, but we only care to have read/execute permissions so need something like:
sudo chmod 755 /usr/lib32/libv4l/v4l1compat.so
[*]At this point, my camera worked when I do: sudo skype, but not without sudo.
[*]I didn't like running skype with root privileges, so had to dig more into what makes sudo work. I noticed that the graphics of skype windows were different when I ran with sudo, some headscratching lead me to suspect my display driver. I remembered I had enabled the proprietary ATI/AMD FGLRX graphics driver for my display card, and I thought doing sudo might either be using the display libraries for the root account which probably isn't that proprietary driver or that it gives me permission to some ATI library that has it's permissions set wrong, not to delve into either case I decided to just disable the driver under system > administration > hardware drivers, and sure enough, the camera worked with skype without sudo. I'm not really sure what part of the ATI driver skype didn't like or didn't have permission to, and since I don't really care for any specific features of the ATI driver, disabling it is the easiest way out for me
[/LIST]

One last detail I found that may be useful to some of you using NVidia drivers. I found that using the latest drivers (in Lucid 64) does not work (I think the driver number was 195), but when I reverted to the old version (173) all went back to work, so I think part of the issue was related to the driver.

Hope it helps.

---

### Post by joris1977 on 2011-10-27
For anyone else trying to get skype working with their videocamera:

On a fresh install of 11.10 the lib32 libv4l libraries seemed to be missing on my 64 bit computer. 

I could find them in synaptic package manager with the name libv4l-0:i386

You need to install this package and after that skype would work with video on my computer by launching it from the command line with: 

env LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l2convert.so skype

Don't know why but in Oneiric  the path is different from earlier versions of Ubuntu.

---

### Post by fayeav on 2011-12-13
I also have a problem with my webcam in skype. The camera works ok on every program i am trying it. Also it works in the options section of skype but not when i am trying to make a call. I am running 11.10 and my laptop is a hp pavilion dv6000 with build in camera. Thanks in advance! Any help it will be great.

---

### Post by premodern on 2011-12-17
> **joris1977 said:**
> For anyone else trying to get skype working with their videocamera:

On a fresh install of 11.10 the lib32 libv4l libraries seemed to be missing on my 64 bit computer. 

I could find them in synaptic package manager with the name libv4l-0:i386

You need to install this package and after that skype would work with video on my computer by launching it from the command line with: 

env LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l2convert.so skype

Don't know why but in Oneiric  the path is different from earlier versions of Ubuntu.

Thanks for this ! Solved my problem all right !

---

### Post by albertodl on 2012-01-08
Hi all,

as far as I can tell, the path for the libv4l folder in Ubuntu Oneiric (11.10) 32bit is slightly different from the one mentioned above, here's the command that works for me:
 
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l2convert.so skype

Thanks to all for all the comments, very helpful for me.

---

### Post by realmagnum on 2012-03-03
> **albertodl said:**
> Hi all,

as far as I can tell, the path for the libv4l folder in Ubuntu Oneiric (11.10) 32bit is slightly different from the one mentioned above, here's the command that works for me:
 
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l2convert.so skype

Thanks to all for all the comments, very helpful for me.


Same here with Lubuntu 11.10 32 bits.

Solved with:
```
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l2convert.so skype
```
My video:
```
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro] (rev 01)
```
My webcam:
```
Bus 001 Device 002: ID 0402:5602 ALi Corp. M5602 Video Camera Controller
```

---

