---
title: "Google Earth logs me out"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by Paddy Landau on 2008-06-24
Initially, when I installed Google Earth, it was ridiculously slow.

I uninstalled it.

Now, when I reinstall it -- using either Synaptic Package Manager or direct from Google -- it logs me out as soon as I start it.

I've tried both version 4.2 and version 4.3.

Does anyone know how to solve this problem, or at least how to diagnose it?

---

### Post by RomeReactor on 2008-06-24
Hi. It would help if you run it from the terminal and post the errors you get:
```
googleearth %f
```

What video card do you have? If it's ATI or nVidia, do you have the restricted drivers installed?

---

### Post by Paddy Landau on 2008-06-25
> **RomeReactor said:**
> Hi. It would help if you run it from the terminal and post the errors you get:
```
googleearth %f
```What video card do you have? If it's ATI or nVidia, do you have the restricted drivers installed?
Thanks for the reply.

As Google Earth logs me out almost immediately, I cannot see what happens in the terminal. So, I ran the following command:
[FONT=Courier New] googleearth %f 1>googleearth1.log 2>googleearth2.log[/FONT]
Both [FONT=Courier New]googleearth1.log[/FONT] and [FONT=Courier New]googleearth2.log[/FONT] were zero bytes.

(What does the [FONT=Courier New]%f[/FONT] do?)

The Screens and Graphics reports my card as "i810 - Intel Integrated Graphics Chipsets", "Intel 945".

Do you know what else can I do to diagnose or solve this?

---

### Post by chrisccoulson on 2008-06-25
Sounds like Xorg crashing. After you get the crash, log in and have a look at the end of /var/log/Xorg.0.log.old to see if it says anything useful.

---

### Post by gtdaqua on 2008-06-25
download google earth and run the 'bin' file. obviously you have to make the file executable: +x switch.

---

### Post by Paddy Landau on 2008-06-25
> **chrisccoulson said:**
> Sounds like Xorg crashing. After you get the crash, log in and have a look at the end of /var/log/Xorg.0.log.old to see if it says anything useful.
There's a lot in there! I'll play around and post back when I find something.


> **gtdaqua said:**
> download google earth and run the 'bin' file. obviously you have to make the file executable: +x switch.
That's the installation file... I've already installed it!

---

### Post by chrisccoulson on 2008-06-25
> **Paddy Landau said:**
> There's a lot in there! I'll play around and post back when I find something.

If Xorg is crashing, then there will be a backtrace at the end of the file

---

### Post by Paddy Landau on 2008-06-27
> **chrisccoulson said:**
> If Xorg is crashing, then there will be a backtrace at the end of the file
Thanks for your help.

You are correct that it's something to do with xorg. I run a dual-screen (which took me ages to figure out!).

When I reinstall the original default xorg.conf, then Google Earth doesn't crash. It runs fine -- although it runs very, very slow (it runs fine when I boot in Windows Vista). That makes me think that the hardware acceleration is turned off. (I speeded up Google Earth on reading [Low performance with Google Earth 4.3]("https://help.ubuntu.com/community/GoogleEarth"), although that doesn't solve the problem.)

I do notice that when Google Earth starts up (in dual mode), it starts on my secondary monitor, not on the first one. Would that make any difference?

There is no change to the file xorg.0.log between before I start Google Earth and after I log back in again.

Any other suggestions? Perhaps I'll just have to go through xorg.conf again, attempting to figure out what specifically is causing it to crash. Unfortunately, being new to Ubuntu, I don't know where the best place is to start looking!

---

### Post by chrisccoulson on 2008-06-27
First of all, if you're running Hardy, I would try running with the default 'bare' xorg.conf and then work your way from there. Your Intel chipset should work out of the box in Hardy without having to configure anything. Try not to use the Screen and Graphics tool in Hardy, as it can break configurations.

To reconfigure Xorg, try the following in a terminal:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm restart
```

This will reconfigure your Xserver (it won't ask you any questions about the display in Hardy, but that is ok), and restart GDM so you can log in again with the new settings.

If it doesn't work, then you can just restore the backup.

Give that a go and let me know how you get on

---

### Post by Paddy Landau on 2008-06-28
> **chrisccoulson said:**
> ... Give that a go and let me know how you get on
Thanks again for you suggestions.

Unfortunately, when I do that, it doesn't seem to allow me to use two screens. The larger screen displays correctly, while the smaller screen displays a clone of the first, with the top cropped.

I'd be happy to do this if I could figure out a way to have the second screen as an extended desktop. I followed the instructions in the [Howto: Dual Monitors]("http://ubuntuforums.org/showthread.php?p=1288786#post1288786") and [Xinerama]("http://ubuntuforums.org/showthread.php?p=1773624#post1773624") posts, modified by [my personal discoveries]("http://ubuntuforums.org/showthread.php?p=5245460#post5245460") (it wouldn't work otherwise). I had to use the Screen and Graphics option to discover what I was missing.

If you have any other ideas of how to progress, or start from scratch, I'd really appreciate it. (I still have a backup of the original xorg.conf from before I made any changes.)

---

### Post by chrisccoulson on 2008-06-28
Don't use those HowTo's, as they are far too old, and Xinerama is deprecated now anyway. I found [this]("http://www.thinkwiki.org/wiki/Xorg_RandR_1.2") howto for you, which might be of more use. Basically, you just need to add a 'Virtual' line to the 'Display' section of your bare xorg.conf. I don't have an Intel chipset, so I can't test it for you. Hopefully it will get you your dual monitor support back!

From that HowTo:
> Recent versions of xorg.conf intended for use with xrandr 1.2 considerably simplify the video section of the configuration. If you upgrading from an earlier version you may find your existing xorg.conf works against the effective deployment of xrandr. So it is best to start with a new Xorg configuration.

an updated Xorg.conf should:

    * omit dual Device/Screen/Monitor sections
    * omit MonitorLayout option and Screen lines from the remaining Device section
    * omit dual Screen lines from the ServerLayout section
    * omit RightOf/LeftOf indication to the remaining Screen line in ServerLayout section
    *** add a "Virtual 2048 2048" line in SubSection "Display" to create a large virtual screen**

To create a new xorg.conf or Ubuntu and other Debian based distributions connect the external display to the VGA port, turn on that display, and run 
It seems that the line highlighted in bold doesnt happen automatically in Ubuntu

---

### Post by Paddy Landau on 2008-07-01
Thank you hugely for that [RandR HowTo]("http://www.thinkwiki.org/wiki/Xorg_RandR_1.2"). It was massively easier than the Xinerama option, which had taken me days to do! I've converted to RandR.

When I use the two screens, non-overlapping, I get display problems (I don't get that when booting in Windows). I don't know why. So, I've just had to use overlapping screens. Oh, well, next time I'll buy a machine specifically built for Linux.

---

### Post by chrisccoulson on 2008-07-01
No problem! The need for hand-editing xorg.conf is actually reported as [bug 220563]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/220563")

What sort of display issues are you having?

---

### Post by Paddy Landau on 2008-07-01
> **chrisccoulson said:**
> No problem! The need for hand-editing xorg.conf is actually reported as [bug 220563]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/220563")

What sort of display issues are you having?

Thanks for the extra info.

To answer your question:

*When I use non-overlapping screens:*

[LIST]
[*]Laptop LVDS is 1280x800
[*]VGA monitor is 1280x1024
[*]VGA is to the right of LVDS
[*]Virtual screen is 2560x1024
[/LIST]
Using the command:
```
xrandr --output VGA --mode 1280x1024 --pos 1280x0 --output LVDS --mode 1280x800 --pos 0x224
```The screens are correctly positioned. However, they don't seem to update correctly, and I'm left with lots of lines across the screens. For example, when I scroll in Firefox, it becomes messy and sometimes unreadable.

*When I use overlapping screens:*

[LIST]
[*]Laptop LVDS is 1280x800
[*]VGA monitor is 1280x1024
[*]VGA is to the right of LVDS
[*]Virtual screen is 2048x1024
[/LIST]
Using the command:
```
xrandr --output VGA --mode 1280x1024 --pos 768x0 --output LVDS --mode 1280x800 --pos 0x224
```The screens are correctly positioned, and update correctly. However, I do have the overlap. I just have to live with it, unless you have some idea of how to fix it.

---

### Post by lfini on 2008-07-03
After last updates to Hardy my gooogleearth crashes the X server. See below the error I find in Xorg.0.log. Prior of update googleearth was working properly. 

Does anybody know what to do?

Many thanks,
                                 l.f.



(EE) DoSwapInterval: cx = 0x84ea018, GLX screen = 0x826f7b8

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x7e) [0x80c780e]
1: [0xb7f56420]
2: /usr/lib/xorg/modules/extensions//libglx.so [0xb7b61077]
3: /usr/lib/xorg/modules/extensions//libglx.so [0xb7b65996]
4: /usr/bin/X [0x81506ee]
5: /usr/bin/X(Dispatch+0x2cf) [0x808d8df]
6: /usr/bin/X(main+0x48b) [0x807471b]
7: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7ce9450]
8: /usr/bin/X(FontFileCompleteXLFD+0x201) [0x8073a91]

Fatal server error:
Caught signal 11.  Server aborting

---

### Post by Bill_in_SD on 2008-08-12
Google Earth logs me out as well.

Ubuntu 8.04 all updated to today. (2.6.24-19)

Xorg.log leaves the following gdm error:

 gdm[17839]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 

Restarting X logs me out and I log in to a new screen.  Ideas?

---

### Post by tikey on 2008-08-26
I also had the problem that starting googleearth ended with the login screen. If I boot with the kernel 2.6.24-20 or -21, however, it is working fine. Unfortunately my wifi is not working in the 24-21, so I ended up starting the kernel 24-20 which doesn't seem to cause any problems.

---

