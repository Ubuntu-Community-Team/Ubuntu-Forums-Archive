---
title: "Why would one want to upgrade their kernel?"
date: 2012-06-08
forum: New to Ubuntu
---

### Post by venom104 on 2012-06-08
I don't understand why someone would want to upgrade their kernel. In Ubuntu (and in almost every other linux distro) the update manager will upgrade the kernel when a new release is out.

Why would someone do this? Here is my reasoning...from what I understand, applications will only work on the same kernel tree that they were compiled with; therefore, you would have to upgrade your kernel modules (drivers) whenever you upgrade your kernel (that isn't a revision update). I have to constantly compile my nvidia driver everytime I upgrade my kernel (I use the binary driver from nvidia.com {my card isn't supported by the nvidia-glx driver (it's too new)}).

I understand that if you want a FEATURE that isn't offered in your kernel (just as an EXAMPLE, an x86 kernel wouldn't support x86-64 applications) then you should compile your kernel with the new features added. I've had to compile my VLC install to get it to work with OSS4, so I can understand if the software doesn't support your current hardware.

Anyway, what's the deal? Does a kernel upgrade improve security? What is the advantage of using a new kernel over an older one?

---

### Post by zombifier25 on 2012-06-08
If you don't want to upgrade your kernel, you can always hold it back using the Update Manager. But of course, you will not receive security updates, etc.
> **venom104 said:**
> Here is my reasoning...from what I understand, applications will only work on the same kernel tree that they were compiled with; therefore, you would have to upgrade your kernel modules (drivers) whenever you upgrade your kernel (that isn't a revision update). I have to constantly compile my nvidia driver everytime I upgrade my kernel (I use the binary driver from nvidia.com {my card isn't supported by the nvidia-glx driver (it's too new)}).

I seriously doubt that's how kernel updates work in Ubuntu, or any distro. Only between Ubuntu releases to the kernel version really changes, usually the updates are minor and provides bugfixes and security fixes. Maybe except for graphic drivers, but I don't think "applications will only work on the same kernel tree that they were compiled with" statement is correct.

---

### Post by anewguy on 2012-06-08
Normally it will be invisible.  The things that *might* change would be libraries, and perhaps the equivalents of dll files.  I have yet to find a library or essential subsystem that doesn't support "old" calls, etc., in the newest version.  Rarely, if ever will you need to recompile.  One exception:  if you had to compile your wireless or other driver, after a kernel update you will need to recompile it.  For the normal user, not using a custom driver, things would be invisible.

dave ;)

---

### Post by BeenLikeFlynn on 2012-06-08
Might as well upgrade if new apps or scripts are coming.:P

---

### Post by venom104 on 2012-06-08
> **zombifier25 said:**
> If you don't want to upgrade your kernel, you can always hold it back using the Update Manager. But of course, you will not receive security updates, etc.


I seriously doubt that's how kernel updates work in Ubuntu, or any distro. Only between Ubuntu releases to the kernel version really changes, usually the updates are minor and provides bugfixes and security fixes. Maybe except for graphic drivers, but I don't think "applications will only work on the same kernel tree that they were compiled with" statement is correct.

I was told that by a recent CS graduate; I would consider him a credible source for information. Anyway, I went into a debian IRC chatroom and they said it's not ALL applications that need to be recompiled, it's just kernel modules and drivers that depend on specific kernel headers. So, I apologize, it was my mistake. I've also tried looking this up on google, but I could not find anything, so I would assert that what they guy said in the debian chatroom is true.

UPDATE: After google searching, I found this [http://www.makeuseof.com/tag/5-reasons-update-kernel-linux/](http://www.makeuseof.com/tag/5-reasons-update-kernel-linux/). I quote " You most likely won&#8217;t break your system if you don&#8217;t update your kernel  for this exact reason, but sooner or later you&#8217;ll find programs and  other packages that require a certain version of the kernel. It&#8217;s best  to have the latest one so you know you won&#8217;t come across that issue."

Maybe someone could shed some light on my ignorance?

---

### Post by anewguy on 2012-06-09
Simply stated, it means if you DON'T update your kernel, you will sooner or later run into problems.  Keep in mind when people say "programs" they don't necessarily mean an application you use - it may be things that are integrated into the operating system.  These tools are constantly updated and compiled against the latest kernel when needed.  Not updating the kernel itself would cause those tools to fail.  The same does hold true with applications, depending on what they do.  In an updated version of the application you use, which could be delivered automatically by the update manager, may require things in a newer version of the kernel.  You go backwards on the kernel - you break your app.

You really are worrying about things that are extremely rare.  The package managers (and I believe the update manager) all install things based on dependencies.  You should never have to worry about it.  Yes, there are rare cases when a kernel update my "break" something - but this is extremely rare.

I would be more concerned about NOT letting normal kernel updates go through.

However, as I have said, this is something you should not need to worry about.  As I mentioned in my previous post, yes drivers and certain other things may require a recompilation.  But.....if you never compiled your driver or other software, then it should never affect you.

---

### Post by codemaniac on 2012-06-09
Top 3 reasons why I would upgrade my kernel .
1. Security Fixes
2. Updated Drivers and drivers for newest Hardware .
3. Stability Improvements

---

### Post by andrew.46 on 2012-06-14
> **codemaniac said:**
> Top 3 reasons why I would upgrade my kernel .
1. Security Fixes
2. Updated Drivers and drivers for newest Hardware .
3. Stability Improvements

4. It is fun
5. It is a great learning experience

:)

---

### Post by Bushflyr on 2012-06-15
> **andrew.46 said:**
> 4. It is fun
5. It is a great learning experience

:)

Yeah, great fun trying to figure out WTF a "system_call_fastpath+0x16 0x1b" is and why I could no longer boot my system. 

Was a good learning experience, though. :p

I think something is broken in the 3.2.0-25-generic update. I have no issues with -24 but -25 won't boot. Just hangs repeatedly. I rolled back to -24 and retried the update but same issue.

---

### Post by Paqman on 2012-06-15
> **venom104 said:**
> from what I understand, applications will only work on the same kernel tree that they were compiled with; therefore, you would have to upgrade your kernel modules (drivers) whenever you upgrade your kernel (that isn't a revision update).

Applications don't care, they'll run on whatever kernel you throw at them. Kernel modules will get recompiled, but dkms can do this automatically. If you're using a blob from elsewhere you might find you have to manually reinstall it each time, which is a pain and the main reason it's not advisable to install stuff that way. Unfortunately if your card doesn't support the shipped drivers you're stuffed.

Kernel updates in a stable release of Ubuntu will be security updates, so you should do them even if it's a hassle.

---

### Post by andrew.46 on 2012-06-15
> **Bushflyr said:**
> Yeah, great fun trying to figure out WTF a "system_call_fastpath+0x16 0x1b" is and why I could no longer boot my system. 

There is some value in keeping a 'safe' kernel :).

---

### Post by Bushflyr on 2012-06-15
Yeah. SO glad Grub did it for me. I would have been screwed. I now have multiple backups of my entire boot drive. :)

---

