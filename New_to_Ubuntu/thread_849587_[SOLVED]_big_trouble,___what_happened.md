---
title: "[SOLVED] big trouble,   what happened?"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by tjwoosta on 2008-07-04
so ive been trying to hook up my sisters computer with ubuntu

(i actually finished all the setup)


i let the computer stay running while i was eating lunch today

and when i got back the computer was completely frozen

i tried ctrl-alt backspace but nothin happened

the mouse wouldnt even move

so i did a hard reset (held down the power button untill it shutdown)


now when i turn the computer on my monitor wont come on (at all)

i tried changing monitors but the same thing

i tried removing the ati radeon video card and using the onboard video but still the monitor wont come on at all

this is really starting to scare me because this is not my computer to break

does anybody have any ideas what could have happened?


BTW it seems like it is still loading up the harddrive (the light still flickers and i can hear it)

---

### Post by OldTimeTech on 2008-07-04
Have you checked the cable that connects the monitor to the computer, make sure it's connected properly or possibly changing it out for another cable....doesn't sound like it's actually the video card.

---

### Post by tjwoosta on 2008-07-04
> Have you checked the cable that connects the monitor to the computer, make sure it's connected properly or possibly changing it out for another cable....doesn't sound like it's actually the video card.

yea thats the first thing i suspected, so i tried a few different monitors (all with there own cables, and they all work on other computers) but none will do anything when hooked to this computer

i really hope this is not some motherboard issue that i cant fix
(my sisters the type that will make me buy her a new one)

---

### Post by Troll_the_Great on 2008-07-04
Try to boot with the live CD and see what happens.

---

### Post by tjwoosta on 2008-07-04
> Try to boot with the live CD and see what happens.


i tried that too  (but it still dont come on)

i cant ever see as much as the bios screen, it just never turns on at all

this sucks

---

### Post by silkstone on 2008-07-04
It could be either the video card as OldTimeTech suggested, or the power supply. Check the cable from the PSU to the PCI-E feed on the MB, and also the cable to the video card if there is one.

Also check that the video card is seated properly and screwed to the case so it makes good electrical contact. (I once had a machine refusing to post because the cards were held in with a plastic clip, and the graphics card wasn't grounding to the case.)

A faulty MB is the worst option, but all you can do is eliminate one thing at a time.

---

### Post by tjwoosta on 2008-07-04
well ive basicaly eliminated everything

i even tried a different power suppy

i hate to say it but i think i lost this one

its gotta be a motherboard issue or something

the thing that gets me is that this machine has been running fine for like a year

then all of a sudden it craps out, for no apparent reason, when i have it of course

so now to her it looks like i broke it

WTF

---

### Post by medic2000 on 2008-07-04
So it is not the monitor.
It could be the RAM also. Check them one by one. If one of them is broken and the other is well it won't matter. The broken one won't let others to operate. Try all parts of the system on a different computer. First RAM then video card and power supply.

Edit: Oops you posted 1 minute before me so i didn't saw your post :) 

So be sure it is the motherboard by trying it on the other pc. Don't give up until you find the guilty

---

### Post by Dr Small on 2008-07-04
Sounds like a video card problem, since you see the POST screen but everything after that goes black.

---

### Post by tjwoosta on 2008-07-04
no no i dont see any screen at all (monitor never comes on)

also i tried removing the video card and trying the onboard video but it does the same thing

---

### Post by Dr Small on 2008-07-04
Hrm. Then it sounds like a problem with the motherboard. I have two non-functioning motherboards that do the exact same thing, and I have never found the cure for them. They power up, but I get nothing on the monitor.

---

### Post by lazertek on 2008-07-04
some motherboards have led's on them which can help you check if it really is the motherboard or the video card. check the manual of the led combination

---

### Post by whitethorn on 2008-07-04
I read that sometimes taking out the cmos battery helps reset the computer.

---

### Post by Dr Small on 2008-07-04
> **aslam said:**
> some motherboards have led's on them which can help you check if it really is the motherboard or the video card. check the manual of the led combination
I'm pretty sure that it's the speaker that gives the beep codes.

@whitethorn, taking the CMOS battery out may possibly help, but I highly doubt it, since it is only resetting the BIOS settings. But, it's worth a try.

---

### Post by flytripper on 2008-07-04
unplug the vga the wall socket and the cmos battery for 10 secs then reconnect and try restarting.

---

### Post by jamesrfla on 2008-07-04
If you can reset the BOIS back to the defaults you might be able to get the onboard video to work. You might have to take out te video card if you don't get anything the first time.

---

### Post by tjwoosta on 2008-07-05
> I read that sometimes taking out the cmos battery helps reset the computer.
> If you can reset the BOIS back to the defaults you might be able to get the onboard video to work. You might have to take out te video card if you don't get anything the first time.
> unplug the vga the wall socket and the cmos battery for 10 secs then reconnect and try restarting.

O my god,   i love you guys

IT WORKED!!!

it actually worked,  you guys just saved me from buying a new computer

even the graphics card works!

---

### Post by silkstone on 2008-07-05
Great result! :)

---

