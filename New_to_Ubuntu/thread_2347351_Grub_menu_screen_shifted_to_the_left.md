---
title: "Grub menu screen shifted to the left"
date: 2016-12-23
forum: New to Ubuntu
---

### Post by rdb3 on 2016-12-23
On my Windows 7/ Ubuntu 14.04 desktop pc, the grub menu screen has always appeared shifted over to the left, off the screen, about 1 inch or so.

The border on the left side of the grub menu is not visible and neither are the first several characters in each of the menu's options.

I can see enough to let me navigate up and down between Ubuntu and Windows, and it works fine, but is there a fix for this without having to reinstall Ubuntu?

Thank you for your suggestions.

---

### Post by oldfred on 2016-12-23
Are you using a TV?
It may be settings on the TV. I had to adjust my TV to solve similar issue.

Or is native screen size of monitor not the size you have set for video out?

Various bits of info on video:
 #To see video:
sudo lshw -c display
sudo lshw | grep -A 11 display
lspci | grep VGA
#Resolution:
xwininfo -root
xrandr -q
xrandr --q1
#What is installed
dkms status

Monitor:
 sudo get-edid | parse-edid

---

### Post by rdb3 on 2016-12-24
Thanks!  Everything works fine except for the Grub menu display appearing shifted slightly to the left and off the screen.

The monitor is a HP x22LED and the factory set resolution is 1920 x 1080.

That's what I have the resolution set at on SystemSettings>Displays>Resolution  1920 x 1080.

My other two dektops, Ubuntu 16.04 and 14.04, set the same way, display the Grub menu perfectly when I connect them to this monitor.

I have a feeling that something got messed up during the initial install.  Is there a Grub repair utility I could try?  If it's risky though, then I'll forget it because this is functional and I can live with it.

---

### Post by oldfred on 2016-12-24
You can try this, but may then be 640x480, see below:
 Boot-Repair --> Advanced options --> GRUB options tab --> tick the "Uncomment GFXMODE" option --> Apply 

 Resetting an out&#8208;of&#8208;range resolution (does not include grub's set gfxmode=640x480)
[https://wiki.ubuntu.com/X/Config/Resolution#Resetting_an_out-of-range_resolution](https://wiki.ubuntu.com/X/Config/Resolution#Resetting_an_out-of-range_resolution) 
    
Grub tries to use graphics mode of system use gfxmode setting. But sometime needs it set directly.
       From a grub command line to see available settings pressing <c> & escape to get back to menu
vbeinfo 

 sudo nano /etc/default/grub 
Change this, if vbeinfo says that 1920x1080 is valid:
GRUB_GFXMODE=640x480
GRUB_GFXMODE=1920x1080

---

### Post by rdb3 on 2016-12-25
I opened the terminal and entered this...

[COLOR=#000000]sudo nano /etc/default/grub 

and got this... no GFXMODE

[/COLOR]```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

```

---

### Post by Bashing-om on 2016-12-25
rdb3; Hello;

ninja'a by oldfred; but I will post as a re-inforcement.

In the file " /etc/default/grub " you see :
> 
# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480


Heed that warning ! "use only modes which your graphic card supports via VBE" !!
If you are not absolutely positive of the resolution, then make sure .
Boot to the grub boot menu -> 'c' key for a command line and execute 
```

vbeinfo

```
Now change the line " #GRUB_GFXMODE=640x480 "
to:
```

GRUB_GFXMODE=1920x1080 

```
where  the leading '#' is removed and "1920x1080 " is in the 'vbeinfo' output .

[INDENT][INDENT]this be system administration
[/INDENT][/INDENT]

---

### Post by rdb3 on 2016-12-25
Thank you oldfred and Bashing-om!

After booting to the grub menu and entering 'c', I did not get the full display of the instructions because things are partially shifted off the screen to the left.
Anyway, I entered vbeinfo (in the blind) as I could not see what I was entering, and I got a list of items, also partially shifted off the screen to the left.
At this point, I am not sure about the resolution and I think I will let this go for now.
I don't want to take a chance on messing anything up, as this pc is being used at this time by someone else.
Thanks for your help.

---

### Post by Impavidus on 2016-12-26
Have you tried adjusting the monitor? Monitors may remember settings for different resolutions separately, so if set properly at the native resolution, it may still need adjustment at the low resolution. If you have a VGA connection (analogue) the image may be distorted, but should be easy to fix. I had that problem recently on a new monitor at native resolution connected to an old computer. The grub menu didn't show at all and changing GRUB_GFXMODE didn't help, but disabling the graphical terminal fixed it for me.

---

### Post by rdb3 on 2016-12-26
> **Impavidus said:**
> Have you tried adjusting the monitor? Monitors may remember settings for different resolutions separately, so if set properly at the native resolution, it may still need adjustment at the low resolution. If you have a VGA connection (analogue) the image may be distorted, but should be easy to fix. I had that problem recently on a new monitor at native resolution connected to an old computer. The grub menu didn't show at all and changing GRUB_GFXMODE didn't help, but disabling the graphical terminal fixed it for me.

Thanks.  I'll give it a try when I get the computer back.  By disabling the graphical terminal, do you mean changing the Resolution (dropdown) in Settings>Displays?

---

### Post by Impavidus on 2016-12-27
> **rdb3 said:**
> Thanks.  I'll give it a try when I get the computer back.  By disabling the graphical terminal, do you mean changing the Resolution (dropdown) in Settings>Displays?

I had the shifted and distorted screen during a normal graphical session, so logged in. That was similar to your problem with the grub menu and I fixed it by playing with the settings of the monitor itself. The grub menu was invisible, which was a different problem although both caused by a lack of co-operation between an brand new monitor and a 10 year old graphics card. There was only a "switch to a supported resolution" message on screen. That was solved by uncommenting the line```
#GRUB_TERMINAL=console
```in /etc/default/grub and updating grub.

---

### Post by rdb3 on 2016-12-27
Thanks, I'll give that a try tonight when I have access to the computer.  I did change the resolution in GFXMODE last night, but that did not resolve the problem.
I have 3 desktops running on Ubuntu, and that is the only one that shows the Grub screen shifted a bit to the left.  It is not distorted, and I can still use it to make a selection between Ubuntu and Windows on that computer, so it is not a deal breaker.
There is no problem with the resolution during other normal usage.

---

### Post by rdb3 on 2016-12-29
I have tried all the suggestions mentioned above (and a few others from online searches) and the problem still persists.  I also upgraded to 16.04 last night, but that made no difference as far as the grub screen shift goes.
Fortunately, it is a slight shift off the screen, and making the selection between Ubuntu and Windows in the grub menu can still be done.

---

