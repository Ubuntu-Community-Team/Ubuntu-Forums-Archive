---
title: "[SOLVED] lost my split screen's 2nd screen, now i'm in &amp;quot;ugly mode&amp;quot;. Nvidia 177 won't"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by surelock22 on 2008-11-20
Well, after all that work i put into getting my 'puter to run a 2 screen set-up, my 2nd screen took a crap on me, so I unplugged it from the graphics card AND I unplugged it PERIOD.

When I started up my computer, it prompted me that my Nvidia driver failed to load, and as a precaution it was going to run in what I like to call "ugly mode". Well, it gave me a choice, I took the top one since i couldn't read the 2nd and 3rd.

When I went to System/Administration/Nvidia X Server Settings it said:

 You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

I went into terminal, typed in sudo su, typed in my password, pasted in nvidia-xconfig, hit return.

It said:

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

Went back to the Nvidia X Server Settings, and still the same thing.

What's wrong?!?! I hate UGLY MODE!!! I have a nice screen, I want to USE IT!!! Grrrrrr.....

Help me plz :)

---

### Post by kestrel1 on 2008-11-20
I could be wrong, but at a guess are you running Ubuntu 8.10 (Intrepid)?
I had a similar issue & tried everything I could think of to get around it. I haven't found a way yet.
I tried the latest drivers for my card direct from Nvidia, but despite following all the instrctions couldn't get them installed. Luckily this was on my test rig & not my main Ubuntu machine (which is still running 8.04 (hardy))
I have just installed Mandriva 2009 on my test rig & so far it seems very good.
Sorry, I haven't been of any help.

---

### Post by fooman on 2008-11-20
> **surelock22 said:**
>  

I went into terminal, typed in sudo su, typed in my password, pasted in nvidia-xconfig, hit return.

It said:

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

Went back to the Nvidia X Server Settings, and still the same thing.


after you did the "sudo nvidia-xconfig",  did you try logging out and then back in again? ...if not,  then you need to.

see if that works.  if it does not...try reinstalling the drivers.

---

### Post by surelock22 on 2008-11-20
I logged out, logged back in, nothing.

I shut down, turned back on, went through a "drive check" that lasted 5 minutes, then I saw the Nvidia Logo (never seen it before on startup, hmmmm) and much to my happiness, I got my old PC back out of ugly mode. WOOPIE!!!

My brother told me that it didn't work after re-boot to hit "alt +ctrl + del" and simultaneously punch myself in the nards. He said me made up that whole "hit alt+ctrl+del" part... lol... wudda character....

But yeah, it's up and running. Me happy. Thanks for the response.

---

### Post by kestrel1 on 2008-11-21
In a way your bro is partly right. If you use CTRL + ALT + Backspace that will restart the x server.
Obviously wouldn't have helped any way, sounds like the drivers hadn't been recognised correctly for some reason.
Anyway, well done & just hit your bro in the nards for the hell of it. :)
Only joking.

---

