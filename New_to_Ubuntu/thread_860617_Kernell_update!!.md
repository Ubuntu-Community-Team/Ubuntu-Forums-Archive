---
title: "Kernell update??!!"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by Troll_the_Great on 2008-07-15
I am pretty new to linux (been using it for about 3 months) and if is something I can't understand is how the f... a kernel update can completely screw up the system?I updated from 2.6.24-18 to 2.6.24-19 and I've had some minor issues with sound, but now, after an update of this kernel (2.6.24-19) my system wouldn't even log in!The system is loading normally (the progress bar with the Ubuntu logo) but the screen where I enter the user name and password is at a very low resolution and a box appears saying that it doesn't detect any display adapters.I entered my user name and password, all goes orange, and after a few seconds I'm back at entering my user name and password.
I am using kernel 2.6.24-18, but this is very frustrating.I've seen lots of threads starting with "Help!The kernel update destroyed....".
Why? An update isn't suppose to fix things, not brake them?!Shouldn't I upgrade anymore?Every time I see a kernel update I wonder what will screw up next!
Any response will be appreciated!

---

### Post by jimv on 2008-07-15
It *breaks* things.  Braking them would just slow things down.

That said, it usually some driver issue...like the video drivers or sound drivers need to be reinstalled in the new kernel.  They are supposed to automatically, but don't always.

---

### Post by philinux on 2008-07-15
> **Troll_the_Great said:**
> I am pretty new to linux (been using it for about 3 months) and if is something I can't understand is how the f... a kernel update can completely screw up the system?I updated from 2.6.24-18 to 2.6.24-19 and I've had some minor issues with sound, but now, after an update of this kernel (2.6.24-19) my system wouldn't even log in!The system is loading normally (the progress bar with the Ubuntu logo) but the screen where I enter the user name and password is at a very low resolution and a box appears saying that it doesn't detect any display adapters.I entered my user name and password, all goes orange, and after a few seconds I'm back at entering my user name and password.
I am using kernel 2.6.24-18, but this is very frustrating.I've seen lots of threads starting with "Help!The kernel update destroyed....".
Why? An update isn't suppose to fix things, not brake them?!Shouldn't I upgrade anymore?Every time I see a kernel update I wonder what will screw up next!
Any response will be appreciated!

I know this sounds weird but rebooting a couple of times can fix it. Especially shutdown not restart.

---

### Post by Troll_the_Great on 2008-07-15
I will go to sleep now (it's 2:30 in the morning here) but I wait your answers and reed them in the morning.
Thanks in advance and good night!

---

### Post by Old_Grey_Wolf on 2008-07-15
> **Troll_the_Great said:**
> Every time I see a kernel update I wonder what will screw up next!
Any response will be appreciated!

I've gotten accustomed to that happening. After the second time, I cut and pasted the commands I entered in the terminal, to get my network card or video card working, into a file. That way the next time it happened, I was able to copy from the file and past into the terminal to get everything working again very quickly. I what to learn how to write scripts to do that.

So far, the problem with kernel updates have only affected devices that are not supported out of the box.

:rolleyes:

---

### Post by sdennie on 2008-07-15
> **Old_Gray_Wolf said:**
> I've gotten accustomed to that happening. After the second time, I cut and pasted the commands I entered in the terminal, to get my network card or video card working, into a file. That way the next time it happened, I was able to copy from the file and past into the terminal to get everything working again very quickly. I what to learn how to write scripts to do that.

So far, the problem with kernel updates have only affected devices that are not supported out of the box.

:rolleyes:

As Old_Gray_Wolf says, this is usually caused by having manually installed drivers for wifi/video/virtualization.  Generally you just need to re-install whatever drivers you've previously installed but, the whole process can be automated.  Examples:

For manually installed nvidia drivers: [http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573)
For VirtualBox PUEL kernel drivers for (something similar to this should work for many other drivers built with "make"): [http://ubuntuforums.org/showpost.php?p=5271094&postcount=7](http://ubuntuforums.org/showpost.php?p=5271094&postcount=7)

---

### Post by Troll_the_Great on 2008-07-16
> For manually installed nvidia drivers: [http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573)
For VirtualBox PUEL kernel drivers for (something similar to this should work for many other drivers built with "make"): [http://ubuntuforums.org/showpost.php?p=5271094&postcount=7](http://ubuntuforums.org/showpost.php?p=5271094&postcount=7)
Thank you very much for the link vor, but can you help me a little bit to create the script?
> Set this to the exact path of the nvidia driver you plan to use
# It is recommended to use a symlink here so that this script doesn't
# have to be modified when you change driver versions.
I don't understand what to do, or what a symlink is.
I am still very noob when it comes to this thinks.
Thanks again!

---

### Post by sdennie on 2008-07-16
> **Troll_the_Great said:**
> Thank you very much for the link vor, but can you help me a little bit to create the script?

I don't understand what to do, or what a symlink is.
I am still very noob when it comes to this thinks.
Thanks again!

The instructions in the script are exactly the same as the instructions in the post.  If you've followed the instructions where you've moved the installer to /usr/src and then run "ln -s ...", the script is just re-explaining that.

---

