---
title: "Ubuntu 12.10 64  and VBox"
date: 2013-02-14
forum: New to Ubuntu
---

### Post by gpreston on 2013-02-14
I have a laptop running Ubuntu 12.10 64bit.  I have replaced the CD drive with a HD tray which contains my Ubuntu OS.  I want to use Virtual Box to run the internal HD as a VM.
The supplied internal HD has Windows 7x64.  Is this possible to do.  Thanks - George

---

### Post by Kopkins on 2013-02-14
You would have to try to set up the HD as a raw disk drive in virtual box. 

I'm unclear on what you want. To me, it sounds like you have two Ubuntu installs and a windows that doesn't matter.

Your laptop has 12.10 on the normal HD? 

And you took the optical bay out for another hard drive running Ubuntu?

And you want to run the new optical bay located HD as your main OS to use the internal HD in VBox, that also has windows on it?

Nonetheless, whatever your doing, you'll need to have VBox in your host OS (obviously) and you'll have to configure the other drive(s) as a raw disk in VBox. Note that they warn you against doing so. You should be able to find a tutorial somewhere about it. Google.

Best of luck,

Kopkins

---

### Post by gpreston on 2013-02-14
My laptop internal HD is Windows 7x64
I replaced the cd drive with a HD bay and it contains my Ubuntu OS.
This set up allows me to boot either Windows 7 or Ubuntu.

What I would like is to boot from Ubuntu then run VBox using the internal HD (Windows 7) as my VM.
Thanks for your reply.

---

### Post by Kopkins on 2013-02-14
That cleared it up. Thank you. 

You'll have to try to set up the windows HD as a raw disk in Vbox.

I haven't set up a raw disk in a while and I don't really remember how to do it. What it does is instead of using the virtual HDD .vdi file for the hard drive of the VM, it uses a real drive, for example, your windows drive. 

I found this, and I think it could be very helpful. Be careful though, remember that you aren't using a virtual drive now and that if you aren't careful you could damage your windows install. Unless you have absolutely nothing to lose on your windows install I  recommend a thorough backup. 

Here ya go: [https://www.virtualbox.org/wiki/Migrate_Windows](https://www.virtualbox.org/wiki/Migrate_Windows)

Best of luck,

Kopkins

---

### Post by gpreston on 2013-02-14
Thanks for the info!  That is what I am looking for. After reading that article I will have to make a decision whether to do or not.

---

### Post by DuckHook on 2013-02-14
It's a very risky procedure. Windows acts like a petulant child and is absolutely embedded on the system to which it was originally installed. I have installed dozens of XP images onto VMs over the years and have tried this procedure on 3 or 4. Never got a single one to work. I don't know anything about W7, but I suspect that it's even harder than XP. I believe that it arises from Microsoft's paranoia over DRM. They probably code their OS to be as resistant to portability as possible. This means that it would actually be designed to fail if it detects any change to MB or HDD, as these are taken as signs of an attempt to copy illegally. If you use this procedure, you absolutely must have everything backed up and be prepared to lose your Windows installation because it will certainly cease to boot up in native mode after you make your changes, but may refuse to boot in the VM either.

---

