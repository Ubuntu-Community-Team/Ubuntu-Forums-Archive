---
title: "Another laptop brightness question..."
date: 2014-04-14
forum: New to Ubuntu
---

### Post by tmach on 2014-04-14
I've been running Ubuntu on an Asus UL30VT laptop sonce 12.04.  Everybody knows the brightness problems (fn keys make the osd appear, but brightness never changes.) That could be fixed with a couple of custom acpi scripts.  Unfortunately, that hasn't worked since the 3.05 kernel, and neither have any of the other workounds.  No biggie, just got used to it since it's a kernel issue and works the same on other distros, too.

Or so i thought.  

I tried Makulu the other day (3.11 kernel) and brightness keys work perfectly.  Just for kicks, i tried other distros more closely related to Debian, and they all worked... LMDE, SolydXK (both flavors) and the aforementioned Makulu all have new kernels, and brightness control is fine.  I then tried Arch derivitives, but they dont work either.  Only the Debian-based distros seem to.

Now, thats nice, but I prefer hopping between Ubuntu and Mint.  LMDE is nice, but not as snappy.   So my question (sorry about the long setup) is... what would those distros have (or not have) that allows those keys to work properly?   Could it be something as simple as a few config files to copy over?

Sorry again about the long post, and thanks!

---

### Post by mastablasta on 2014-04-15
i would have a similar question but with an even more ridiculous fact. only light Fn keys stopped working now. but i tried a few distros live and got
Kubuntu 13.10 - brightness fn keys do not work, sound work, wi-fi doesn't
Lubuntu 13.03 - no Fn keys work
Xubuntu 12.04 - all Fn keys work - brightness, sound, and wi-fi (note: wi-fi hasn't worked in Kubuntu before)

this seems really strange to me - i mean how can something work in one version but not in the next? shouldn't linux continue to support hardware?

moreover what is the difference in the kernels that make it work in one version but not in next? i've tried numerous switches and nothing changed. i have HP dm1 with AMD E-450 APU chip.

now as for you tmach - Arch - they have a newer 3.13 kernel and that kernel has a new kernel switch which might get it to work. furthermore i was investigating this and it seems they also have certian kernel patches available. this brightness is called *backlight* - a keyword to get a better search results for various wikis.
also have you tried 14.04 yet? i am thinking about giving beta a try. depending on the time on my hands...

---

### Post by twinkel1961 on 2014-04-15
I am running Ubuntu precise pangolin (12.05) with kernel 3.5, moved from unity back to gnome
No problems with the Fn-key here, there's a slight delay but the osd appears and brightness can be changed
Have been running ubuntu for at least 4 years on this laptop, never had problems with brightness.

---

### Post by germanix on 2014-04-15
This is very frustrating. The Fn-Keys for brightness does not work on my Lenovo Thinkpad X230 using Ubuntu 14.04. It also did not work running 13.10. Sound however worked in both. Tried OpenSuse and there the brightness keys worked! Yet some who run Ubuntu claims that the Fn-Keys for brightness works on their system, which is all very confusing! So what does OpenSuse have that Ubuntu has not? At the moment I am using the GUI to set the brightness but it would be nice to get those Fn-Keys to work.

---

