---
title: "Can some one PLEASE tell me why my keyboard goes undetected."
date: 2008-08-23
forum: New to Ubuntu
---

### Post by adobrakic on 2008-08-23
Wow, I can't believe i fit that into the title bar. :x

Anyway, sometimes Ubuntu doesn't detect my keyboard and I have to restart my computer so it can be detected. Sometimes when it's back up, the keyboard isn't detected again and I have to restart...again. This is really, really, really annoying.

I have a Dynex keyboard & mouse. The mouse is fine.
Also, the keyboard is plugged into a USB port. When it goes undetected, I try switching to a different port, but the only thing that happens is the 3 lights (num lock, etc.) lights up and then turns off.

Is there like a plug-n-play program (kinda like windows has -- the annoying hardware detected thing) that would detect my keyboard once i plug it back in?

---

### Post by zamadatix on 2008-08-23
if im not mistaken ubuntu does support plug in play one sec ill try with my wireless... yep it does. does it work with other os's?

---

### Post by adobrakic on 2008-08-23
With Windows it works fine. Like sometimes when I'm using Windows it'll go undetected, but i just unplug it and plug it back in and it works fine.

---

### Post by zamadatix on 2008-08-23
bye the osunds of it you might want a new more reliable keyboard. i just unplggeed and replugged my usb wireless keyboard and its working normally. i cant see why it owuld work in windows after it failed but not in ubuntu... do all other keyboards work (assumeing you have more)

---

### Post by adobrakic on 2008-08-23
Yeah, other keyboards work fine. And I'm pretty sure your right, about getting a more reliable keyboard, but they're so damn expensive. This one was like $30 or something including a mouse.

Just bothers me that Windows can get it but Ubuntu can't. 
:x

---

### Post by ad_267 on 2008-08-23
> **adobrakic said:**
> Yeah, other keyboards work fine. And I'm pretty sure your right, about getting a more reliable keyboard, but they're so damn expensive. This one was like $30 or something including a mouse.

Just bothers me that Windows can get it but Ubuntu can't. 
:x

Yeah I was going to say it sounds like a dud keyboard. It works the other way too. I have  a computer where Windows will only recognize any USB device about 10% of the time and Ubuntu recognizes them every time.

---

### Post by mgranet on 2008-08-23
I had exactly the same problem when I used to connect my PS/2 keyboard using a PS/2-USB adapter. Drove me crazy. I ended up smashing it to bits with a hammer in a fit of rage, actually. I think it might have something to do with the keyboard not responding with the proper info when the USB hub requests it. I would go buy a new keyboard.

---

### Post by adobrakic on 2008-08-23
I really do want to, but i'm not in the best financial situation :x
i'll save up for it, haha.
get a loan.. :x

---

### Post by seagullplayer77 on 2008-08-24
I've got a wireless Targus mouse that acts up every once in a while too, and the problem isn't too much unlike yours. Sometimes, Ubuntu won't pick up the USB receiver, although I've found a quick fix. Press Alt+F2 to bring up a run dialog, and run the command "lsusb". Always works for me...hopefully it'll work for you as well!

---

### Post by adobrakic on 2008-08-24
i cant run it if my keyboard is out. :P!!

---

### Post by isaacj87 on 2008-08-24
> **adobrakic said:**
> I really do want to, but i'm not in the best financial situation :x
i'll save up for it, haha.
get a loan.. :x

Hey,

I picked up this set awhile back and it's pretty much done the job. On logitech's website they say the MSRP is $30, but I picked up mine for $24.99. Here's the link: [http://www.logitech.com/index.cfm/keyboards/keyboard_mice_combos/devices/154&cl=us,en]("http://www.logitech.com/index.cfm/keyboards/keyboard_mice_combos/devices/154&cl=us,en")

There's probably better deals out there, check your local Fry's (if you're in the US) or tigerdirect.com to see if you can find a good deal. :)

Money has a nasty habit of disappearing faster than you can get it ya know?

---

### Post by adobrakic on 2008-08-24
yeah, definitely haha.

but i'll check it out and try to find some deals on ebay or amazon and whatnot.
thanks for the headsup though. :D

---

### Post by panhandle on 2008-08-24
What is the exact model number of your keyboard? Mouse?

I figure you have searched for known issues with your particular models, but if not, it might help.

---

### Post by adobrakic on 2008-08-24
I have no idea what the model numbers are. I looked on the back of the keyboard, but I only get a s/n which is '7G27A001022', I threw away the box this all came in. :(!

But yeah, I've searched for solutions but nothing came up. I guess I'm the only one using them. :x

---

### Post by Alan Coleman on 2008-09-04
Ive been having probs with usb on ubuntu. Someone kindly gave me a brand new keybord and mouse that they got bundled but didnt need. my heart sank when I saw it was usb and shore enough it was searching for a fix that brought me to your thread. I recon theres a fix for it somewhere in this forum. Its a laptop Im using and I tryed the above lsusb in and it didnt do anything. I did it in a terminal and got

summer@summer-laptop:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
summer@summer-laptop:~$ 

cant say it makes much sence.
so i recon its the usb ports.
keep searching...

---

### Post by Alan Coleman on 2008-09-04
mmm after a bit of thought on that read out form the terminal. lsusb was issued with a usb mouse plugged in. one of those ones with a red light shining out the bottom of it. Red light is shining out but the mouse dos'nt move the courser and it dos'nt appear in the lsusb list. 

so maybe there is some life in that old keyboard of yours yet bud!!

---

### Post by Alan Coleman on 2008-09-05
I decided to install kubuntu from the Ubuntu repository onto my ubuntu pc being at the level of reckless experimentation. It didn't work to well I think I have to add some extra repository's perhaps...but hay presto my usb devices miraculously started working.

its great when it works!

ac

---

