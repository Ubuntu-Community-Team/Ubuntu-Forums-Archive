---
title: "[SOLVED] Device Drivers"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by SonOfOdin on 2008-07-27
Hey crew

I have a Metabox 722 laptop (desktop replacement.)  It has a WXGA+ 17" monitor.

For a while now I have been using it with a resolution of 1440x900.  Sweet.

Tonight, for some reason, I decided to clean up my menu.  Hey I'm new to Linux, keen to set up my PC my way, and so far everything that I have touched with the OS has turned to ****, but its been exciting.  So any way, I find that the "Screens and Graphics" shortcut has been hidden from me.  I've seen this in 7.10 so I recognise that this is either the answer or gonna make things worse.  So, I start mucking around.

First thing I notice is that straight away my second monitor becomes uncloned when I set it to secondary!  Awesome.  Then I remember that my secondary screen is a Benq FP951, and the driver selected is generic.  Ok, can fix this.  So I change the driver, and it asks for a reboot.  Hm, ok.

Wham, Safe Graphics Mode.  Alright, lets try and remember where everything was before...  try this.  Nope, try that.  Nope.

6 hours later, I have 640x800 resolution, cloned displays and Im about to thump the crap outta everything on my desk with my keyboard.

Actually, thats not quite true, but the temptation to go back to MS is getting strong.  I dont want to do that either.

So, short of going through the entire driver list on the off chance that one of the drivers is going to work, what can I do to restore some sanity?

Unfortunately, the driver software that came with the laptop is in the form of a MS OEM recovery cd.  No way do I want to restore that, and I dont know how to use Ghost in order to browse the driver/cabs etc.


So, after the rant, the question I need to ask is - is there a driver / hardware detection software for Linux??  Does anyone know what driver the Metabox 722 WXGA+ LCD Panel uses, is it available in Linux, and is that the real name for my screen or just a description?

Thanks for listening, and I appreciate any help.
:popcorn:

---

### Post by northern lights on 2008-07-27
Do the following to automatically reconfigure X11:

Run ```
sudo /etc/init.d/gdm stop
```to exit the Deskto Manager and go to CLI. Jot down the next few lines before running the above.

Reconfigure X with```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Restart the graphical environment```
sudo /etc/init.d/gdm start
```

Usually it'd be reasonable to backup the xorg.conf first, but given how messed up everything is, I'd say it's redundant, but do so if you please.

---

### Post by SonOfOdin on 2008-07-27
Hey, cheers for the reply!

Yeah, its bodged alright.  Im still playing around, just thought about recovery mode in the Grub.  Got my original resolution, but now my Gnome is bugging out on login.

I will give your suggestions a try now, thanks.  Will let you know how it goes.

---

### Post by SonOfOdin on 2008-07-27
Ok, thats awesome.  Thanks, Im back to where I started \\:D/

Now, just before I go and play again, Id really appreciate the save settings lines, and also how to reinstate the saved settings.

Thanks again

---

### Post by northern lights on 2008-07-27
> **SonOfOdin said:**
> Now, just before I go and play again, Id really appreciate the save settings lines, and also how to reinstate the saved settings.

For instance back up your 'xorg.conf' now, after fixing things
```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak1
```

restore with ```
cp /etc/X11/xorg.conf.bak1 /etc/X11/xorg.conf
```

---

### Post by SonOfOdin on 2008-07-27
Great, thanks for your help Northern Lights!

This thread is over.:guitar:

---

### Post by northern lights on 2008-07-27
> **SonOfOdin said:**
> This thread is over.:guitar:

On top of your first post, under thread tools, you can mark it as solved (it will appear with [SOLVED] prefix).

---

