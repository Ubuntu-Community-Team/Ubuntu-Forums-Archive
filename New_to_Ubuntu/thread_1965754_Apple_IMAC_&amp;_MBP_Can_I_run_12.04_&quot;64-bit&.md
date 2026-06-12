---
title: "Apple IMAC &amp; MBP: Can I run 12.04 &quot;64-bit&quot; virtually using Parallels? (64 vs 32-bit?)"
date: 2012-04-26
forum: New to Ubuntu
---

### Post by swarup on 2012-04-26
As I recall in the past, mac users had to run the 32-bit version of Ubuntu on their computers. But now I have several completely new apple computers in my home office, and would like to run Ubuntu virtually on all of them, utilizing the "parallels" software. Can I install 12.04 at 64-bit? I would prefer that. Or is it still the case today that only 32-bit versions of Ubuntu run smoothly on apple computers?

---

### Post by swarup on 2012-04-26
I see on the [Ubuntu 12.04 LTS (Precise Pangolin) Daily Build]("http://cdimage.ubuntu.com/daily/current/") site, that there is also a special build for 64-bit mac machines:

precise-alternate-amd64+mac.iso 

Would that be better for me? Is it a final version? I ask, because it is not listed on the main 12.04 download site. 

And, if I use this version instead, will it also be supported in the same way with updates etc, for 5 years?

---

### Post by forrestcupp on 2012-04-26
> **swarup said:**
> I see on the [Ubuntu 12.04 LTS (Precise Pangolin) Daily Build]("http://cdimage.ubuntu.com/daily/current/") site, that there is also a special build for 64-bit mac machines:

precise-alternate-amd64+mac.iso 

Would that be better for me? Is it a final version? I ask, because it is not listed on the main 12.04 download site. 

And, if I use this version instead, will it also be supported in the same way with updates etc, for 5 years?

That version is for directly installing onto your Mac computer. It's not for running with Parallels. So I would say that you'd want the regular version for Parallels.

According to the [Parallels System Requirements](http://www.parallels.com/products/desktop/system-requirements/), the latest version of Parallels supports 64-bit guest OSs, specifically a lot of Ubuntu releases. They don't list 12.04 yet, but they really haven't had time yet, either. I'll bet it would work. The worst thing that could happen is that you wasted your time downloading it.

---

### Post by swarup on 2012-04-26
Oh, yes. You are correct-- I see now. I'll go ahead with the standard 64-bit. Thank you!

Will report back to this thread as to how it works.

---

### Post by swarup on 2012-04-27
I have installed 12.04 (64 bit) as well as 11.10 (32 bit)--both virtually--on my new imac, using parallels. Both have the same very significant defect that the cursor function is not good. Here are the issues with cursor function: 

1. When working in Ubuntu, one cannot move the cursor outside the Ubuntu window back on the Mac desktop. The only way to get the cursor to go out of the Ubuntu window is to hit command-tab. That creates a new cursor, which can now go out of the Ubuntu window. (When using Windows virtually on the imac, it is not limited in this fashion.) 

2. The cursor flickers extremely and becomes invisible entirely, in certain apps and utilities. For example, in the system tools utility it does that. And I have installed Kexi database app; there it happens as well. And there are other apps in which the same happens. Plus in general, the cursor is slightly jittery or flickery, even in apps where it works better.

3. One cannot grab the side of the Ubuntu window and expand the size of the window width-wise. One can only adjust the window by grabbing the top or bottom, and then it adjusts the height and width proportionally.

I called Parallels tech support, and found out that these same issues have been existing since Ubuntu 9.04, with Parallels. It has never been fixed.

With these above exceptions, Ubuntu seems to be functioning well. But the above issues with the cursor are significant, and need to be addressed. I have mentioned this in no uncertain words to the Parallels tech support team.

---

### Post by 3rdalbum on 2012-04-27
Virtualbox may be better in this regard; I haven't had any troubles with either Linux or Windows as the guest OSes, and Ubuntu as the host OS.

I did hear a while back that Virtualbox was a bit buggy on Mac OS hosts, but then that might all be fixed now. It's only a couple of megabytes, might be worth a try. Virtualbox is free too.

---

### Post by swarup on 2012-04-27
Excellent suggestion-- I hadn't yet considered trying another virtual software. Let my try with Virtualbox and see how it goes. I'll report back here and let you know how it goes...

---

### Post by swarup on 2012-04-27
I downloaded and installed Virtualbox on OSX. And now I am trying to install 12.04 virtually using it. This is now my second attempt-- the install seems to start out fine, giving the progress bar as it copies all the Ubuntu files. It completes copying the files, then starts a second progress bar in which it says it is "retrieving" files. But on my first install attempt it got stuck while "retrieving" the 57th of 120 or so files. I wasn't sure whether "retrieving" meant it was doing an internet download of updates, or whether it was just retrieving files from the iso-- in which case I don't see why it would have gotten stuck. So I shut it down and am trying the install of 12.04 via virtual box a second time. Again the same thing is happening. It has ever-so-slowly reached the point where it is now "retrieving" the 55th file of 129. Still moving ahead, but incredibly slowly. And this time I did not click either to install updates during the install, or do install the mp3 and video files. So I don't know why it would be downloading anything. But if it stops working again and refuses to finish this progress bar of "retrieving" files, I may have to give up trying to install 12.04 via virtual box. Any ideas about this?

---

