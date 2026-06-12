---
title: "updated 2 laptops - 1 cannot start."
date: 2018-07-02
forum: New to Ubuntu
---

### Post by bodhin2 on 2018-07-02
i updated 2 thinkpads.  one did not need a restart - the other did - so when i restarted the 2nd - it froze on startup and had to power button down - now cannot start up or get to login page.  hate to redo it - just did them all weeks ago  help please

---

### Post by Frogs Hair on 2018-07-02
Can you get to the page with the kernel list and advanced options ?

---

### Post by bodhin2 on 2018-07-02
no - there is a long list of startup stuff that freezes and i tried everything.  no way to do anything.  thannks

a page of chock lists with Ok - last item - Ok in green and thenstrated gnome displaymanager - dispatcher service...system changes pp link was shutdown

---

### Post by bodhin2 on 2018-07-02
all i did was update.  did not add or tweak anything - all was running smooth.

this is my better faster good office laptop too.  damn.

---

### Post by bodhin2 on 2018-07-02
i will just have to reinstall - nothing works and i did some searches online and notta.  thanks my friend.  a waste of a day to tweak all the stuff up again.

:-(

---

### Post by kerry_s on 2018-07-02
move the mouse while booting up, just swing it back & fourth. 
or
boot the old kernel

it's a kernel bug.

---

### Post by bodhin2 on 2018-07-02
i was just going io reinstall - let me try this - any fix for it?  i do not see a way to use old kernel....

---

### Post by bodhin2 on 2018-07-02
rebooted out of the ubunti dvd. worked but shut it down and it is stuck again.  tried shutting down and still back to that same page.

how do i get back the old kernel never had to do this?  what's the bug too

---

### Post by kerry_s on 2018-07-02
power off your computer, when you turn it on hold the shift key.

i forget what the bug is, it's waiting for some kind of response, moving the mouse gives it a similar response.

no fix, ubuntu has to fix in kernel.

---

### Post by bodhin2 on 2018-07-02
thanks too late - reinstalling and i am not very happy.  everything was working so sweet n my 2 laptops and the wife's.  hate shut the other one down now for fear that will be the same - did not update my wife's.  maybe command line updates and upgrades are not good in 18.04.  may have to use software updater only.  i never had any issue ever with a kernel issue.  in ver 10 years of linux too,  problem is time is a problem to retweak all the apps and settings etc.

this is the first bad thing i can say about ubuntu.  never should have let it out if it had a bug that makes one redo the system.  not cool at all.

---

### Post by kerry_s on 2018-07-02
if you update your new install it will happen again. it took fedora & solus a day to fix, just wait it out.

---

### Post by kerry_s on 2018-07-02
also i was wrong it's the esc key-> then advanced settings

---

### Post by bodhin2 on 2018-07-02
ok installed it and did the software updater and again - stuck.  tried everything i cannot even load ubuntu on it.

---

### Post by kerry_s on 2018-07-02
now just get into grub & select the 23 kernel

actually it might be the 20 kernel from a fresh install.

---

### Post by bodhin2 on 2018-07-02
man tried everything i have a decent computer that cannot even run ubuntu now.  any help would be greatly appreciated.  i did not even start to tweak it.  and it already pooped out.

---

### Post by bodhin2 on 2018-07-02
only 20 and 24 no 23.  i tried them all and nothing.still same thing

---

### Post by kerry_s on 2018-07-02
strange, the 20 should work. that's what it booted with on the installer.

you could drop down to ubuntu 16 or 16 based distro
or
another distro with the higher 2.16 kernel

that bug was only in the 2.15.0.24 kernel

---

### Post by bodhin2 on 2018-07-02
Thanks - will try 1 more install and no updates.  man - you try to be on top of stuff to be safe and diligent and wham.  now i can see how people feel when they get trashed systems.   i really am ticked.  thanks again will see what happens.  yes i did ry the other 20 and same things - still hangs.

---

### Post by kerry_s on 2018-07-02
a little tip for next time, wait at least a week, before you do the updates, they do not have to be applied right away. just ignore the notifications.

---

### Post by bodhin2 on 2018-07-02
esc doesn't do it shift does but still have issues.

---

### Post by bodhin2 on 2018-07-02
kerry - ok you have to hit shift and hold when it freezes before it gets to the list page.  that is when the ubuntu name shows but the dots do nothing re: turning red or whatever color they do. on a fast system you do not even see that step.what a pain - wish i knew before i redid the total system. thanks for your help!

---

### Post by bodhin2 on 2018-07-02
is this kernel bug considered an urgent fix?  sahould be - just wondering how it becomes known to this that can fix this,  busiest time of the season for me here and the last thing i needed was to waste a day reinstalling and tweaking all settings and apps up.  hope many people are not affected!

---

### Post by Impavidus on 2018-07-03
Just as a precaution, you can edit the file /etc/default/grub (you need root permissions for that). Change it so that it has the line```
GRUB_TIMEOUT=3
```or something like that. That's what it says on my system. Then update grub:```
sudo update-grub
```That command is run automatically at every kernel upgrade. With these settings, the grub menu, which allows you to choose an older kernel, shows automatically at every boot for 3 seconds. No more need to hit shift or escape at the right moment. 3 seconds is short enough not to cause an annoying delay during boot and long enough to give you a chance to hit a button (like an arrow key).

BTW, I've been using Ubuntu for 12 years and never had a kernel upgrade go wrong. Maybe I've been lucky.

---

### Post by bodhin2 on 2018-07-03
thanks but not sure how to  do what you say.  i too have never had this happen before.  still did not shutoff the slower one i upgraded.  you read about kernel bugs - but this one is bad news.  as much as i like this bionic beaver experience - this is a strike 1...   everything was so sweet until i had to redo my system.  too tedious with all the app setting tweaks etc,

---

### Post by bodhin2 on 2018-07-03
another thought.  i update almost every other day yet the kernel went from .20 to 24 with the said 23 not there.  why?  also can a mod make some type of announcement when they do fix this kernel bug?  that was be nice.

---

### Post by bodhin2 on 2018-07-04
fwiw - the older x series thinkpad is an ironlake chip and the newer older and much faster x series thinkpad is sandybridge - yje sandybridge seems affected - the one time i tried the older one it seemed to start.

---

### Post by bodhin2 on 2018-07-04
wife's dell with the ironlake - updated and upgraded and no issues at started the one time i tried it.  hope this helps a bit.

---

### Post by monkeybrain20122 on 2018-07-05
Hi, From the last post from [this thread ]("https://ubuntuforums.org/showthread.php?t=2395459&page=2&p=13780980#post13780980"):
> ```
sudo apt install haveged
sudo systemctl enable haveged 
```
This issue only seems to affect kernel 4.15.0-24. getrandom() is  called when starting Xorg and for some reason in 4.15.0-24, it hangs for  a bit until the entropy is high enough to generate a random number to  use as a magic cookie for xauth. Xorg, LightDM, and GDM won't start  until xauth is given a random number to use. Any kind of mouse/keyboard  input probably raises entropy, which explains why pressing keys or  moving the mouse fixes the problem. Haveged generates enough entropy at  boot, eliminating the problem.

It's been reported as a bug, so hopefully haveged won't be necessary in future kernels once the bug is fixed.

The previous 4.15.0-23 kernel doesn't have this problem, so booting into that instead would also work.

It works here. Now boot time is back to normal to ~ 4 -5 sec 

The bug in question is [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=897572](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=897572)

---

### Post by bodhin2 on 2018-07-05
Ok Thank you so much!  i powered down and hit the power button and wham - it works.  Man i really appreciate this so much.  felt so bad that you had to do physical workarounds with starting linux in this day and age.  thanks to whoever figured it out.

---

