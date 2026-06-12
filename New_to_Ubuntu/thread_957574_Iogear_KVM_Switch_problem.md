---
title: "Iogear KVM Switch problem"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by marko_4454 on 2008-10-24
Hi All,
So I bought a KVM switch ([click here]("http://www.newegg.com/Product/Product.aspx?Item=N82E16817399001")) And I am unable to get it to switch between computers. Everything else works great: Keyboard, monitor, mouse, sound. I have been reading around and here are what I have tried:
1) adding xmodmap -e 'add mod3 = Scroll_Lock'
2) Press num-lock rather than scroll lock
3) Going to a non-X session (Ctrl+Alt+F1) and pressing scroll lock x2.

None of these worked, so I am stuck now. Any help in how to get this working? Thanks! :)

---

### Post by KB9VGD on 2008-10-24
Greetings;

I have a differant style than what you have but all I have to do is do a double press, quickly, of the Scroll Lock key.

Gary

---

### Post by Kellemora on 2008-10-24
Hi Marko

With most KVM's you have to ENABLE the keyboard or auto-switch functions before they will work.

On my unit (TruLink 4-port) you have to hit the scroll button twice then the letter H to turn ON the auto scroll feature.

Or, to move from computer to computer via the keyboard itself, you hit scroll twice then a number 1 through 4.
Or scroll twice then either the up arrow or down arrow.
If Auto-Scan is turned ON, I only need to hit a number key and hold it for 5 seconds, while NOT in a text document of course.

Mine also has an OSD program (On Screen Display) where you can change the settings from there also.

One handy feature is you can switch the USB hub independently of the computer or tie it to all computers at once.  That's cool too!

TTUL
Gary

---

### Post by louieb on 2008-10-24
> **Kellemora said:**
> ... to move from computer to computer via the keyboard itself, you hit scroll _lock_ twice then a number 1 through 4.


Thats the way my airlink 101 2 port and my noname 4 port  KVM switches work.  No changing setting a comuter. Just plugged them in and they all work. <Scroll Lock><Sroll Lock>#

---

### Post by Iowan on 2008-10-24
My Belkin uses same commands (which I cannot seem to remember - thanks for the memory jog).  I've noticed that machines sometimes do weird things (especially the mouse) when booted with KVM set to a different machine.

---

### Post by marko_4454 on 2008-10-25
Hi All,
Thanks for the responses I really appreciate it. However, I have looked into the problem and here's more weird stuff. I read the manual and it said to plug in the plug (of both inputs: Keyboard and Mouse) in the Keyboard slot. I had it in the Mouse slot (where it worked perfectly). I changed it to the Keyboard slot and mouse worked, however, keyboard does not work. It does detect it though since I have some "media keys" in top of the normal alphanumerical keys and those media keys do work. 
I guess I'll try and remove the xmodmap (with mouse plug) and then restart and try again. Wish me luck :)

---

