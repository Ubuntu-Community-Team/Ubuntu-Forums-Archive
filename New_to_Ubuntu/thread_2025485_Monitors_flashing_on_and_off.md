---
title: "Monitors flashing on and off"
date: 2012-07-14
forum: New to Ubuntu
---

### Post by MarkV13 on 2012-07-14
I recently installed 12.04 and have an issue with my monitors flashing on and off at random. I am using a Radeon HD 3650 graphics card and dual acer 20" monitors. The ATI proprietary drivers just won't work on my system. Any help would be awsome

---

### Post by QIII on 2012-07-14
How have you tried to install the fglrx driver?

The flashing on and off sounds like a hardware issue.  Hopefully minor.  Do the stuff that we all (let's be honest... even the most experienced of us sometimes beat our heads against the wall and throw things when there is a simple issue) sometimes forget:  make sure the graphics card is seated, cables are not loose, power cords are not hanging half way out of the socket, the dog didn't go chasing his tennis ball under the desk and knock something loose, etc.  I spent 15 minutes once cursing because one of my machines would not turn on, thinking I probably had a mobo that went out.  My wife told me the Boxer was rooting around under my desk after his ball earlier in the day.  Stupid dog.  Knocked the power cable out of the socket.  Stupid human.  Didn't think about the power cable.

---

### Post by MarkV13 on 2012-07-14
Yes the fglrx drivers cause the system to reboot in generic and config wont work, but I am very new to this

---

### Post by MarkV13 on 2012-07-14
Yup,  I went thru and checked those things several times, and used your instructions for installing ATI drivers, always reboots in generic nd can't seem to get it to work. won't boot normaly til I purge ATI drivers

---

### Post by QIII on 2012-07-14
Edit:

You used my instructions from the ATI driver wiki?  The part about "Alternate command line method with hardware acceleration"?

I need to know about that!  I may need to do some updates.

(By the way, thanks for reminding me... I just updated some notes about fglrx-updates.)

---

### Post by MarkV13 on 2012-07-14
I'm going to run thru the install again nd read your wiki agantin so I can attempt to give you an intelligent answer

---

### Post by QIII on 2012-07-14
Thanks.  This is a community effort!

If you would, take good notes.  I'll see what I can do to find a resolution and update the wiki as necessary.

---

### Post by MarkV13 on 2012-07-14
went thru "alternate command line method" after step 6(reboot) loked up on xubuntu boot screen, past attemps to install have always booted up in generic but not this time, ctrl-alt-delete reboots to same screen

---

### Post by MarkV13 on 2012-07-14
How do I get it to reboot in generic, without that it seems like I'll have start with fresh install

---

### Post by MarkV13 on 2012-07-14
It looks like my graphics card would be supported if it were PCI but alas it's AGP and I may be out of luck. card is RV635 pro AGP Radeon HD 3650

---

### Post by QIII on 2012-07-14
As soon as you hear the POST beep, press the Shift key and hold it until the GRUB menu shows up.

Select the line that says "Recovery" and press enter.

You will be presented with a recovery menu.

Select the line that says "Networking" and press enter.  That will start a bunch of TTY.  What it is doing is getting you on the network and mounting your drives in read/write mode.

When that is done and you are back to the command prompt, type "Exit" and press enter.

Now, back in the menu, select the line that says "Root".

You'll see a bunch more TTY and eventually get to a command prompt.

Enter

```
sudo apt-get remove --purge fglrx fglrx-amdcccle
```to remove the driver and reboot.

Let me know if you have problems from there.

Looks like I have some research to do.


Edit:  Saw your last post.  Yes, you are correct.  That card won't be supported. Snap!  Sorry.

---

### Post by MarkV13 on 2012-07-14
Thank you Qlll...its folks like you that make this open source stuff fun.....any thoughts on the flashing monitors?

---

### Post by QIII on 2012-07-14
My thought, unfortunately, is a hardware fault.  If both monitors are doing it, it has to be something they have in common.  I think either the card itself or the PSU may be failing.

Does the card get power entirely through the slot, or does it have power via one of the PSU connectors?

---

### Post by MarkV13 on 2012-07-14
Card gets power thru PSU connector, also the monitors do not flash together and at random. I may have a seizure soon :-)

---

### Post by QIII on 2012-07-14
Well, even if not together, something is common.

Do they flash on and off as in power or signal?  Are they plugged into a surge protector in common?

An electrical fault in either (in order of pocketbook damage) the PSU, the card (in terms of replacement cost) or the motherboard might be the culprit.

A quick test, just for a really minor thing, might be to pull the card and check for debris in the slot.  While you have it out, give the contacts a very light rub with an eraser -- slowly and along the long axis of each connector.  Make sure to get all the eraser crumbs off of it.

Is the card cooled by an HSF or passively with a heatsink?

---

### Post by MarkV13 on 2012-07-14
looks like its time for some new hardware....oh well.....hope this helps someone as a good reminder to check your compatibility very carefully, in my case the difference between PCI and AGP  was huge.  Qlll thanks again you rock!!!!

---

