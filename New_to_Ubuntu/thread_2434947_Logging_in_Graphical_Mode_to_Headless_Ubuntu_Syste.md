---
title: "Logging in Graphical Mode to Headless Ubuntu System"
date: 2020-01-14
forum: New to Ubuntu
---

### Post by robertweir on 2020-01-14
Hi
   I have installed Ubuntu 18.04 LTS on a Raspberry PI 4.  I need to be able to use VNC to log on remotely.  I do not want to tie up a Monitor.  How can I have it boot up Into Graphical Mode through VNC while having no monitor connected to the PI.  I currently have it working, but only when I have a monitor connected.  Can anyone help me with some setting that will allow me to access it while it is 'headless'.
Robert

---

### Post by CatKiller on 2020-01-14
As you've found, X struggles to start when there's no connected display detected, and graphical applications need X to have started.

There are two options available to you. You can fiddle with xorg.conf to add the characteristics of a dummy output and tell it to ignore the lack of EDID, which is fiddly but not ever so difficult; or you can attach a dummy device that does the same thing in hardware - I think they're only a few quid.

---

### Post by robertweir on 2020-01-14
> **CatKiller said:**
> As you've found, X struggles to start when there's no connected display detected, and graphical applications need X to have started.

There are two options available to you. You can fiddle with xorg.conf to add the characteristics of a dummy output and tell it to ignore the lack of EDID, which is fiddly but not ever so difficult; or you can attach a dummy device that does the same thing in hardware - I think they're only a few quid.

Hi CatKiller
   I will have a look into 'xorg.conf' and see what I can find.  I am interested in the 'dummy device' you mention, is it an active or passive device?  I have never heard of them before.  Thanks for the post.
Robert

---

### Post by CatKiller on 2020-01-14
> **robertweir said:**
> I will have a look into 'xorg.conf' and see what I can find. 

/etc/X11/xorg.conf, which is the full path, isn't there by default but it will be used if you make one. **man xorg.conf** details the structure and options. IgnoreEDID is the critical option for what you're after. If you sometimes have a monitor connected you can crib the details from that, or otherwise just make something up that fits the needs of how you'll connect remotely. 

> I am interested in the 'dummy device' you mention, is it an active or passive device?  I have never heard of them before.  

[This](https://www.amazon.co.uk/Headless-Display-Emulator-Headless-1920x1080-generation/dp/B072PV6K8J) is the kind of thing. They were invented for just this situation. It just gives an EDID response of "yes, I'm totally a monitor." Pretty neat.

---

### Post by robertweir on 2020-01-14
> **CatKiller said:**
> /etc/X11/xorg.conf, which is the full path, isn't there by default but it will be used if you make one. **man xorg.conf** details the structure and options. IgnoreEDID is the critical option for what you're after. If you sometimes have a monitor connected you can crib the details from that, or otherwise just make something up that fits the needs of how you'll connect remotely. 



[This]("https://www.amazon.co.uk/Headless-Display-Emulator-Headless-1920x1080-generation/dp/B072PV6K8J") is the kind of thing. They were invented for just this situation. It just gives an EDID response of "yes, I'm totally a monitor." Pretty neat.

Hi CatKiller
   Thank you so much for your answer.  I will follow up with you here as soon as I get the issue sorted.  : - )))
Robert

---

### Post by splasher1901 on 2020-02-28
@robertweir & @CatKiller
I am having the same issue and was lucky to find this thread, BUT, I got helplessly lost in the man pages on xorg.conf.
My installation is of Ubuntu 18.04 and I have it running exactly like I want it until I unplug the monitor.
Could you share the contents of an xorg.conf file to me?  In addition, is there anything else I need to tweak once I have a properly configured xorg.conf file?
My goal is to use this with the model railroading software JMRI, where it will not normally be connected to the outside world, boots & logs in as a specific user and starts the X11VNC server.  The only thing stopping me at this point is this monitor issue.
Thanks in advance for any help you can give me.
-splasher in somd

---

### Post by wildmanne39 on 2020-02-28
Hello and welcome to the forum splasher1901, please start your own thread so you and the OP of this thread can both get the individual help you need and it does not get confusing for everyone trying to solve two users issues in the same thread.

Thanks

---

### Post by splasher1901 on 2020-02-29
@wildmanne39
Okay, but I thought addressing my request to the OP (and his lone responder) for the actual solution that had worked for the OP made sense.  I did not see it as trying to hijack the OP's thread seeing as my issue is exactly the same as the OP's issue.
-splasher in somd

---

### Post by CatKiller on 2020-02-29
At the risk of the ire of the mods:

The easy option is the dongle that I mentioned before: they're cheap, and as far as your computer is concerned there is a monitor connected that says all the right things all the time. Job done.

The next alternative is to tell your computer the things about your monitor without it ever troubling to ask the monitor itself, which means that it shouldn't notice when you unplug the monitor. You'd create a file, called something like /etc/X11/xorg.conf.d/20-monitor.conf, and put in something like (apparently the IgnoreEDID option name is deprecated now)
```

Section "Monitor"
    Identifier     "Default Monitor"
    Option         "UseEDID"    "False"
EndSection

```
along with either HorizSync and VertRefresh ranges for your monitor, or a modeline. You can get that information from the Xorg log when you've booted with the monitor plugged in, or you can read the manual/calculate a modeline yourself. The advantage of this method is that, because you're using information from your actual monitor, it works fine should you actually want to plug your monitor in. It just doesn't notice when you *don't* have your monitor plugged in.

Another alternative is that, relatively recently, the xserver-xorg-video-dummy driver was created. Same kind of thing, except there's no actual display so it never looks for EDID. You'll still need to create an xorg.conf, and probably a full one rather than just a monitor snippet, too.

The significant wrinkle is that every VNC server is different. As I understand it, some of them create their own secondary X screen as part of their normal function, meaning that, on the one hand, you might only need to configure your server properly and not worry about what your normal desktop is doing, but, on the other hand, you might fiddle with your desktop's X configuration and have it completely ignored by your VNC server. I have no interest in learning about the specifics of any particular VNC implementation: everything I do with my headless computers can be done with either SSH or a web browser.

---

### Post by hk42 on 2020-03-02
An alternative to the dongle may be a cheap HDMI to VGA or CVBS converter.
They provide a sound output that may be handy.

---

### Post by splasher1901 on 2020-03-02
@CatKiller
Thanks for the response.  After two solid days of following every lead I could find on the web, I was not able to get this to work.  In the end, I even made the PC un-bootable and had to rebuild from an ISO.

@hk42
Wrong direction for that device, the computer does not have a HDMI port, so the device would not work.

I have a headless Ghost Display Emulator on order which will show up in a couple of days.
Thanks for the suggestions and I will stop with this post to not raise the wrath of the mod again. :)

---

