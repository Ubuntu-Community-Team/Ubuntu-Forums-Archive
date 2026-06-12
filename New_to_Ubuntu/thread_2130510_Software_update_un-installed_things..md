---
title: "Software update un-installed things."
date: 2013-03-29
forum: New to Ubuntu
---

### Post by MythicManiac on 2013-03-29
Hello. I'm fairly new to Ubuntu, although I've had plenty of experience dealing with programs and computers as a programmer. I switched to Ubuntu yesterday, as I don't like Microsoft and prefer open-source software. Took me a while to get hand of things and install my graphics card drivers etc, but I had it all done after looking up a few basic commands.

Now today, I got software patch notification, so I decided to update. Turns out the update somehow managed to un-install my graphics card driver and linux headers. I don't have a problem anymore, managed to install those again using the terminal ( As it wouldn't boot to anything else ). But my question would be, what could cause this to happen and is there anything I should be aware of? I don't think programs/drivers should magically disappear after a software patch.

---

### Post by Frogs Hair on 2013-03-29
Some more information about the patch my shed some light on what happened . If the patch was for non official software and there were conflicting dependecies it may account what happened. I have never recieved a patch for software in my Ubuntu experience only updates. What you describe can happen with partial upgrades, but this is uncommom uless you have enabled proposed updates or are testing a pre-release version.

---

### Post by MythicManiac on 2013-03-29
> **Frogs Hair said:**
> Some more information about the patch my shed some light on what happened . If the patch was for non official software and there were conflicting dependecies it may account what happened. I have never recieved a patch for software in my Ubuntu experience only updates. What you describe can happen with partial upgrades, but this is uncommom uless you have enabled proposed updates or are testing a pre-release version.

I don't know what did it update exactly, as it was automated and the amount of things updated was around 270. I remember one of them failing and giving me an error. This is probably the most likely reason to cause what happened, but I'm not sure how would that get already existing programs un-installed

---

### Post by 3rdalbum on 2013-03-29
If you installed the driver from Nvidia.com, it will always stop working after a kernel update. That's why it is better to use the nvidia-current from the Ubuntu repositories instead.

Make sure you install the linux-headers-generic package instead of the one specific to your kernel version (linux-headers-generic-3.0.12 or whatever). The former will update with your kernel, the latter will not.

---

### Post by Frogs Hair on 2013-03-29
Be sure proposed or prereleased updates  are not enabled in software sources > updates , they are not by default and should not be unless you are testing. Look in the update history in the software center and that will display what was updated and  removed. If you ever get a partial upgrade message wait until the full update is available before installing . Parial upgrades can cuase this same thing to happen.

---

