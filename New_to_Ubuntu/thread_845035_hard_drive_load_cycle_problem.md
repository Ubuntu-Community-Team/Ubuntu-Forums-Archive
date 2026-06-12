---
title: "hard drive load cycle problem"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by muteXe on 2008-06-30
[http://ubuntuforums.org/showthread.php?t=591503](http://ubuntuforums.org/showthread.php?t=591503)

I believe I am experiencing this "bug" on my new laptop.  As explained in the above thread there are so-called ugly fixes to try and stop this, but (rightly so) there are numerous warnings stating things like "if you don't know what you are doing DO NOT try this".

In other words, I have to say goodbye to ubuntu on my laptop because I'm not a linux whiz.  A shame really, as I like ubuntu and have used it on my desktop for a long time.

Does anybody know if there are any official fixes coming soon?  If not, can anyone suggest a distro that will not ruin my harddrive?

Thanks,

mute

---

### Post by nowshining on 2008-06-30
what ver. of Ubuntu/kubuntu are u using?

---

### Post by ByteJuggler on 2008-06-30
> **muteXe said:**
> [url]
Does anybody know if there are any official fixes coming soon?  If not, can anyone suggest a distro that will not ruin my harddrive?


From the threads you reference, it appears Hardy already has the fix in.

---

### Post by muteXe on 2008-06-30
Thanks for the replies :)
No it doesn't have the fix in.  My drive is spinning up, or doing something, every 6 or 7 seconds.  from the links, it's been fixed in debian, but not ubuntu.


@nowshining:  I'm using ubuntu 8.04.  

When i boot into vista, my drive is silent and doesn't appear to have this problem.
cheers.

---

### Post by ByteJuggler on 2008-06-30
> **muteXe said:**
> No it doesn't have the fix in.  My drive is spinning up, or doing something, every 6 or 7 seconds.  from the links, it's been fixed in debian, but not ubuntu.


See the bottom of [this thread]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810") by Nicholas M and the followup implying its been fixed. This is why I said it appears fixed/marked as fixed. I think you need to get posting there then, so they re-open the issue as its obv. not fixed.

Edit: OK this is obviously a big can of worms... seems like HDD firmware may be implicated as well in some cases at least... (/me wonders about his laptop drive...)

---

### Post by muteXe on 2008-06-30
Cheers bytejuggler, however that thread is titled "bad hard disk noise on shutdown".  I am referring to a tiny HD spin noise every 6 or 7 seconds.

---

### Post by muteXe on 2008-06-30
This is the bug:
[https://bugs.launchpad.net/bugs/59695](https://bugs.launchpad.net/bugs/59695)

A fix for both debian and suse has been released, and there are lots of "fixes" for ubuntu if you know what you are doing.  I don't know what i'm doing though :(

---

### Post by nowshining on 2008-06-30
try in terminal

sudo apt-get update
sudo apt-get upgrade

---

### Post by muteXe on 2008-06-30
okay, i'll try when i get home from work.
thanks :)

although how will this fix a bug??

---

### Post by muteXe on 2008-06-30
> **ByteJuggler said:**
> See the bottom of [this thread]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810") by Nicholas M and the followup implying its been fixed. This is why I said it appears fixed/marked as fixed. I think you need to get posting there then, so they re-open the issue as its obv. not fixed.

Edit: OK this is obviously a big can of worms... seems like HDD firmware may be implicated as well in some cases at least... (/me wonders about his laptop drive...)

might be a firmware problem, but there's no problem with the drive when i boot into windows on the same laptop...  Goodbye ubuntu i'm afraid.  At least until this is officially fixed.

thanks for your advice and help though guys.

mute

---

### Post by sdennie on 2008-06-30
I'm not sure why this would cause you to abandon linux.  There are known and easy ways to fix this problem and the disclaimer of "Do not do this unless you know what you are doing" is just that, a disclaimer.  If you have verified that you are having Load_Cycle_Count issues, then try the fixes and see if they help.  The fixes are fairly benign and won't cause your laptop to explode.

See this thread: [http://ubuntuforums.org/showthread.php?t=805570](http://ubuntuforums.org/showthread.php?t=805570)
Or, alternatively, this can also reduce disk activity in general: [http://ubuntuforums.org/showthread.php?t=839998](http://ubuntuforums.org/showthread.php?t=839998)

---

### Post by muteXe on 2008-07-01
Thanks vor,  I might give them a go if I'm feeling brave.
And I'm not completely abandoning linux, I still run it on both of my desktops :)

---

