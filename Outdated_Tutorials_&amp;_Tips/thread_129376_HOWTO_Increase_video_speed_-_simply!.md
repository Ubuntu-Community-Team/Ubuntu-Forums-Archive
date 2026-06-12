---
title: "HOWTO: Increase video speed - simply!"
date: 2006-02-13
forum: Outdated Tutorials &amp; Tips
---

### Post by dcstar on 2006-02-13
Just another little thing I have found, I could increase my reported 
glxgears -printfps" rate just by changing my colour depth (in /etc/Xorg/xorg.conf) from 24 to 16.

I get a ~40% increase, and my display doesn't look that different (to me, anyway). I do have a video card using system RAM, so this may not work as well in other environments.

But, less data to write to the video card does mean less time to take to do it........

---

### Post by kittcankitt on 2006-02-14
Just wondering if you actually feel any "faster" response from your desktop/system after making this change and are there any drawbacks?  This to me seems like changing a "Windows" desktop to 16 million colors from 24 million in which case, I never really noticed a difference either way.  Of course it's been years since I've had a "windows" desktop.

Nice tip though! I was just wondering about the above mentioned things.

---

### Post by BoyOfDestiny on 2006-02-14
[QUOTE=kittcankitt]Just wondering if you actually feel any "faster" response from your desktop/system after making this change and are there any drawbacks?  This to me seems like changing a "Windows" desktop to 16 million colors from 24 million in which case, I never really noticed a difference either way.  Of course it's been years since I've had a "windows" desktop.

Nice tip though! I was just wondering about the above mentioned things.[/QUOTE]
24-bit is 16 million (well 16,777,216 to be exact), and 16-bit is 65,536 colors. You won't notice it unless these images/video are very "color rich".

---

### Post by Teren on 2006-02-14
On a TFT the difference between 16 and 24bpp is very noticable.

Try looking at the Ubuntuforums logo at the top of the page in 24bpp, then in 16bpp ;)

---

### Post by dcstar on 2006-02-16
The real value for this is in those systems where people are having problems with video performance in gaming etc.

These people may be having trouble getting hardware acceleration going on their systems, so something like this may provide some help before they can implement a real fix (either by better video drivers or a new Ubuntu version).

---

