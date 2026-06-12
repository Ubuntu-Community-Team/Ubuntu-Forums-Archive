---
title: "Youtube unwachable"
date: 2014-01-18
forum: New to Ubuntu
---

### Post by WinXpRefugee on 2014-01-18
Youtube is unwatchable (Firefox)

My desktop looks grainy

I don't know how to describe this but in windows terms
My desktop looks like a 256 color windows desktop.
Change Color Depth? 

Don't know if my hardware will run more colors  
```

*-pci
          description: Host bridge
          product: 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:e8000000-ebffffff
        *-display
             description: VGA compatible controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:e0000000-e7ffffff memory:ee000000-ee07ffff

```

Is there a fix or a setting that I cant find 
BTW I have been using linux for about 6 hours now so be kind I am a Noob!

---

### Post by mörgæs on 2014-01-18
[URL="https://lists.ubuntu.com/archives/lubuntu-users/2013-November/006117.html"]
https://lists.ubuntu.com/archives/lubuntu-users/2013-November/006117.html[/URL]

---

### Post by WinXpRefugee on 2014-01-18
mörgæs,
Thank you for your reply
I tried doing what you suggested in the link

[https://lists.ubuntu.com/archives/lubuntu-users/2013-November/006117.html](https://lists.ubuntu.com/archives/lubuntu-users/2013-November/006117.html)

To no avail I can create the xorg.conf file and save it to desktop but can't copy, save, or move it to
ect/x11:confused:

[COLOR=#ff0000]Could not save the file /etc/X11/xorg.conf.
You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.[/COLOR]

Installed chrome browser Youtube looks fine
But video is smashed and pink and green in firefox

```
xdpyinfo | grep 'depth of root window' | awk '{ print $5 }'

```
is 15
Would love to get to 16 or 24 but i dont know how to do this

---

### Post by WinXpRefugee on 2014-01-18
[SIZE=3][B][COLOR=#ff0000]THIS DID NOT WORK! DO NOT DO THIS! see next post
[/COLOR][/B][/SIZE]
Based on this 
[http://www.linuxquestions.org/questions/linux-mint-84/linux-mint-13-cinnamon-specific-instructions-4175419632/page2.html](http://www.linuxquestions.org/questions/linux-mint-84/linux-mint-13-cinnamon-specific-instructions-4175419632/page2.html)
 just did this in term
```

gksu gedit /etc/x11/xorg.conf

sudo nano /etc/X11/xorg.conf

```

Pasted in 
Section "Device"
    Identifier "Intel Graphics"
    Driver "intel"
    Option "AccelMethod" "uxa"
    DefaultDepth 16
EndSection

```
 ^X Y <enter> 
```


Will reboot and let you know if its better.

---

### Post by WinXpRefugee on 2014-01-18
Nope beefed the gui
Apperently it does not understand "DefaultDepth" argument
So now I am in term 
I was able to edit the file with using some directory commands cd, dir, ls.
and sudo nano to edit out the argument
it would not let me just remove it ??? rm (something about permissions)

---

### Post by mörgæs on 2014-01-18
Try adding sudo to the cp or rm command.

---

### Post by WinXpRefugee on 2014-01-18
Still can't get color depth.

---

### Post by mörgæs on 2014-01-18
Let's forget about other parameters now. First, please follow the instructions exactly as in the link I posted. 

Now you should get 1) much more than 256 colors and 2) a working Flash player in Firefox. Did it work as expected?

---

### Post by DuckHook on 2014-01-18
Bill,

Default Linux has more native security than default Windows (a good thing) but it does require you to learn about things like permissions and file ownerships. Read [this]("http://www.rackspace.com/knowledge_center/article/linux-file-permission-concepts") site to familiarize yourself with these concepts. Then, mörgæs's reference to *sudo* will make more sense to you. That is: to be usable, xorg.conf must be placed in a system directory and owned by root, and prepending *sudo* to *rm* allows you to act as root in removing it. Without *sudo* you do not have the proper ownership/permissions to delete the file.

---

### Post by WinXpRefugee on 2014-01-18
mörgæs,
Thank you for your reply,
I followed your suggestion from the post again just now
[SIZE=3][COLOR=#ff0000][SIZE=2]
This did not work for me! But I appriciate [/SIZE][/COLOR][/SIZE][COLOR=#ff0000][SIZE=2]**[SIZE=3]mörgæs[/SIZE]** input because it got me on the right track to fix it.[/SIZE][/COLOR]


I did not have  xorg.conf  file but created one as described in the post above
followed the sugestions in the post
This post seemes to be for [COLOR=MediumTurquoise]VIA Technologies, inc. KM400/KN400P4M800 
[/COLOR]I have [COLOR=#0000ff]82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device[/COLOR]

This is mine xorg.conf now
```

Section "Device"
    Identifier "Default  Device"
    Driver "openchrome"
EndSection

```

rebooted and no change 
I have also noticed I cant play tux cart due to graphics issues if that has any thing to do with any thing.
also found this post appears to be one of yours 
[http://ubuntuforums.org/showthread.php?t=2184932](http://ubuntuforums.org/showthread.php?t=2184932)
I have not tried this though[SIZE=3][B][COLOR=#ff0000]
[/COLOR][/B][/SIZE]

---

### Post by WinXpRefugee on 2014-01-18
Just tried this
[http://forums.linuxmint.com/viewtopic.php?f=48&t=149164](http://forums.linuxmint.com/viewtopic.php?f=48&t=149164)
We will see what happens on reboot

---

### Post by WinXpRefugee on 2014-01-18
[COLOR=#ffd700][SIZE=5]**BOOM GOES THE DYNAMITE!!!!**[/SIZE][/COLOR]
[http://forums.linuxmint.com/viewtopic.php?f=48&t=149164](http://forums.linuxmint.com/viewtopic.php?f=48&t=149164)

WORKED for me
Thank you mörgæs and DuckHook for the assistance I hope i can get good enough at this to help other people.

There is some weirdness going on with my title bar
tux car is still jacked 
but the packages were installed prior to me fixing this so the packages may have got settings from the old setup.(if that is how this all works)

---

