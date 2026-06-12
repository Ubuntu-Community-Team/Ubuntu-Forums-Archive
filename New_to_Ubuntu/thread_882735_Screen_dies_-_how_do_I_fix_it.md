---
title: "Screen dies - how do I fix it?"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by p-jo on 2008-08-07
My screen dies occasionally (once a day appr), and I can't figure out what is wrong. If I turn the computer off and start it again, it's ok again.
I'm running 64bit 8.04 with kde4. My screen is a an Asus MW221U. And these are the settings I get from lspci -v:
```

01:00.0 VGA compatible controller: ATI Technologies Inc RV516 [Radeon X1300/X1550 Series] (prog-if 00 [VGA controller])                                           
        Subsystem: PC Partner Limited Unknown device 5920                        
        Flags: bus master, fast devsel, latency 0, IRQ 11                        
        Memory at d0000000 (64-bit, prefetchable) [size=256M]                    
        Memory at fe9e0000 (64-bit, non-prefetchable) [size=64K]                 
        I/O ports at b000 [size=256]                                             
        Expansion ROM at fe9c0000 [disabled] [size=128K]                         
        Capabilities: <access denied>                                            

01:00.1 Display controller: ATI Technologies Inc RV516 [Radeon X1300/X1550 Series] (Secondary)
        Subsystem: PC Partner Limited Unknown device 5921
        Flags: bus master, fast devsel, latency 0
        Memory at fe9f0000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

```

I don't really know where to start.. I've been looking at the /var/log/Xorg.0.log and one error I found was
RADEON(0): [dri] RADEONDRIGetVersion failed to open the DRM
Does that have something to do with it?

---

### Post by markjensen on 2008-08-07
I've really never had to troubleshoot a problem like this, but you can isolate it to the ATI drivers by switching to the Open Source ones, instead of the proprietary ones from ATI.

You will miss out on the 3D-accelerated goodness, but still should be very functional.   And if it locks up then, too, you have big problems (maybe hardware?).

Plus, right now it looks like you are cycling power.   Could you try a few other things before you cycle power?   One is to use CTRL+ALT+Backspace.  This will just kill X, and kdm should auto-restart X and present you the login screen again.    Also, when it is frozen like that, try CTRL+ALT+F1 to see if you can get to a TTY (text) login screen.   Your X session should be on CTRL+ALT+F7, if you want to go back to that (F1 thru F6 are pretty standard to be used for TTY sessions across many distros).

Hope that helps a bit.

---

### Post by jimv on 2008-08-07
>Screen dies - how do I fix it?

Mouth to screen resuscitation?

---

### Post by p-jo on 2008-08-08
Thanks mark. The proprietary driver is not activated in the Hardware Drivers Manager, is that what you mean? How do I activate the open source one?

---

### Post by markjensen on 2008-08-08
> **p-jo said:**
> Thanks mark. The proprietary driver is not activated in the Hardware Drivers Manager, is that what you mean? How do I activate the open source one?
Ok, that's not exactly what I was expecting at all.  I'm a little confused.

Do you know which driver you are currently using?   You can post the contents of your /etc/X11/xorg.conf file, if you like.  Or just tell me what driver is listed for your video card device in that file.

If you have been using the Open Source version ("ati", I think), then we will use the proprietary "fglrx" one instead.  And vice-versa.

I'm an nVidia person, so never had to set up an ATI card in Linux, so I'm not 100% sure of the procedure.   Ubuntu picked up my nvidia automatically, and did the work for me, but I have a lot of experience doing this manually in Red Hat/Fedora the past 5 years.   It can't be too tough to do the ATI stuff.  Post here if you need help.

---

