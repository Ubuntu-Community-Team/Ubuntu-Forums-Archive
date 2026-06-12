---
title: "Screen is permanently off after install"
date: 2012-12-23
forum: New to Ubuntu
---

### Post by erazen on 2012-12-23
Hi, I'm completely new with ubuntu although I have some very basic linux experience (simple command line stuff).

I decided to ditch windows 7 completely from my laptop and installed the 32-bit desktop version of ubuntu 12.04 stable release using a liveCD. I backup the data I needed and used the "remove windows 7 completely" option that does all the partitioning etc. automatically using the whole disk.

Setup:
My laptop is an ASUS X58LE with 3GB RAM, Intel Pentium T3400 @ 2.1Ghz, and Intel GMA integrated graphics card. It came with Vista 3.5 years ago when bought, have been using windows 7 for the last 1 year.

Problem: 
After the seemingly successful install, I was prompted to click to restart my system, but when I did the system did not shut down and the screen got completely turned off. After waiting for several seconds (at least 30), it stayed that way (the computer seemed to be on, light indicators on, and I could hear the processor/hard drive/cd drive). I decided to do a hard reboot by holding the button.
From then on and until now whenever I boot it, the screen does not turn on AT ALL, but I can hear the hard disk / processor / cd-drive(if I put a cd in it), although it is completely unresponsive. Also I am not aware if Ubuntu has a booting "sound" but I do not hear any sound at all. Also if it makes any difference, I had set the boot priority to CD/DVD first and HD second in order to do the installation.

I am unable to do ANYTHING (can't get into bios settings for example) since the screen is ALWAYS turned off. I suspect it being a hardware issue (screen or graphics card), but I don't understand why it would happen right after the ubuntu installation.

I'm sorry for the long post, and thanks in advance.

---

### Post by erazen on 2012-12-24
No one has the slightest idea? :(
It really seems like a hardware issue to me and I'll be getting it to the repair store after christmas but if anyone knows how/if this could have happened and/or it could be solved please say so!

---

### Post by squakie on 2012-12-24
So, did you try any of the boot options shown in the MANY threads here about no video after install?

You should try:

i915.modeset=1

if that doesn't work:

i915.modeset=0

if that doesn't work:

nomodeset

if that doesn't work:

acpi=off (I *think* that's the value -> might be "false" or "no")

if that doesn't work:

apic=off (I *think* that's the value -> might be "false" or "no")

might be other options worth trying as well.

If none of that works, try:

booting in recovery mode, safe graphics, then:

post back the output of:

lspci | grep VGA  (that's piping symbol - the shifted backslash key on my keyboard - not a 1, not an "L" of any sort)

This would tell us the actual video adapter and we can go from there.

Also - keep in mind it's a volunteer forum, it's a holiday weekend and that you should only bump a thread after 24 hours, might have something to do with no replies yet.

---

### Post by Zill on 2012-12-24
> **erazen said:**
> ...I decided to ditch windows 7 completely from my laptop and installed the 32-bit desktop version of ubuntu 12.04 stable release using a [COLOR="Red"]**liveCD**[/COLOR]...
One great advantage of many Linux distros being on Live CDs is that you have an option to try the OS *before* you install it to your HDD.  This helps identify any potential hardware problems that may exist so that you are well prepared after installation.

Did you try running Ubuntu from the Live CD or did you just go straight to installation?

Does the Live CD run OK now if you boot with it in the drive and "Try Ubuntu without any change to your computer" (or similar wording!)?

---

### Post by erazen on 2012-12-29
It turned out that the motherboard is gone. 
@Zill: I did try the live cd version first it was fine.
@Squakie: I am not able to try ANY of that since the screen does not get turned on EVER.
The computer didn't start at all.
I'm getting a new laptop.

---

