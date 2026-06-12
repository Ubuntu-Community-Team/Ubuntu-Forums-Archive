---
title: "So many updates ..."
date: 2012-07-27
forum: New to Ubuntu
---

### Post by lemmingrebel on 2012-07-27
Do you personally work through each update and nitpick your installation?

Or do you just accept them?

Any recommendations for a noob?

---

### Post by sandyd on 2012-07-27
Just accept them - im to lazy + busy to look through them

---

### Post by Cheesemill on 2012-07-27
+1
Accept all of them.
They will all be bug fixes and security patches.

Unless of course you a running an important production server in which case you would test them out on your staging machine first :)

---

### Post by QIII on 2012-07-27
Except...

When you are offered a "partial upgrade" ("The following packages will be held back: ...).  Don't do that unless you know exactly what you are doing.  You can end up with a borked system.  Wait 24 hours to see if all of the dependency issues are resolved.

---

### Post by Toz on 2012-07-27
+1 to what QIII says.

I review the list and look for ones that might affect my installation. I specifically keep an eye out for kernel or video driver updates, or other packages that I may have built from source or that may affect ones that I have built from source. I then generally wait until I have some free time (usually weekends) and apply them - then make sure everything still works as before.

This is probably because I spent part of my previous life in debian sid :)

---

### Post by Kelvari on 2012-07-27
I recommend the following settings for Ubuntu updates
```
Install updates from:
X Important security updates (<release>-security)
X Recommended updates (<release>-updates)
- Pre-released updates (<release>-proposed)
X Unsupported updates (<release>-backports)

Automatically check for updates: Daily
When there are security updates: Download and install automatically
When there are other updates: Display immediately/weekly
Notify me of a new Ubuntu version: For long-term support versions
```

This setup will keep your system up-to-date automatically while providing the most stability possible. It'll still ask for your approval for partial-upgrades, for which I also recommend Quill's advice. Given that you're relatively new to Ubuntu, I doubt that you'll go compiling programs from source without good need, though.

---

### Post by CharlesA on 2012-07-27
> **sandyd said:**
> Just accept them - im to lazy + busy to look through them
This. I just look for errors in the installs. ;)

---

### Post by QIII on 2012-07-27
Fixing the errors is fun for the whole family.

---

### Post by edeneen on 2012-07-27
why use all those terminal commands ?  I use the Update Manager ?  Does it matter in any way ?  
thanks

---

### Post by CharlesA on 2012-07-27
> **edeneen said:**
> why use all those terminal commands ?  I use the Update Manager ?  Does it matter in any way ?  
thanks
You don't have to use the terminal, but some people prefer it;)

---

### Post by Cheesemill on 2012-07-27
What terminal commands?

Kelvari was just describing this dialog box:

---

### Post by QIII on 2012-07-27
Some of us still think this whole GUI thing is a phase that just won't catch on...

---

### Post by CharlesA on 2012-07-27
> **QIII said:**
> Some of us still think this whole GUI thing is a phase that just won't catch on...
*snickers*

terminal ftw.

---

### Post by Cheesemill on 2012-07-27
> **QIII said:**
> Some of us still think this whole GUI thing is a phase that just won't catch on...
Yep, I have way more boxes without a GUI than with :)

---

### Post by Kelvari on 2012-07-27
> **Cheesemill said:**
> Yep, I have way more boxes without a GUI than with :)
Servers, I'm assuming? Or just sarcasm?

---

### Post by Cheesemill on 2012-07-27
> **Kelvari said:**
> Servers, I'm assuming? Or just sarcasm?
Mostly servers. I do have a very old box without a GUI that I sometimes use for browsing, email, text editing and the occasional bit of music.

---

### Post by critin on 2012-07-27
> **edeneen said:**
> why use all those terminal commands ?  I use the Update Manager ?  Does it matter in any way ?  
thanks

The terminal requires only one line and it's way quicker for me.

---

### Post by critin on 2012-07-27
> **lemmingrebel said:**
> Do you personally work through each update and nitpick your installation?

Or do you just accept them?

Any recommendations for a noob?

I accept them unless they offer a partial.  I figure they know better than I do.

---

### Post by rattskjelke on 2012-07-27
I don't understand what is meant by "partial upgrade".

Is that what happens when you "apt-get upgrade" and it says something like "The following packages are held back"?

I always do a "apt-get dist-upgrade". Is that a bad idea? I've never had that break anything.

How can a kernel upgrade be bad or break your system? Isn't Linux supposed to be stable?

---

### Post by yuvraj23 on 2012-07-27
Oy! Don't use terminal for update i.e dist-update as you will end up with a kernel that is not recommended for you system.. Like I already have few updates pending related to new kernel ie headers,kernel image etc but am not updating to it at all! It expects 4gb of RAM and I have only 1GB. So its better to check what are you updating, Its only matter of minutes buddy! :)

---

### Post by miegiel on 2012-07-27
I always read what's being updated. If you update daily there shouldn’t be to many packages. Not that I know what every package is, but after a while you'll start to recognize stuff. Depending on what needs to be updated, I either postpone it or update it right away. For some stuff you need to reboot or restart the GUI and that can be inconvenient. And when I'm test driving an ubuntu that isn't officially released yet, I often wait to see if nothing important breaks. (But if you're still a noob, you should wait till the official release. Though fixing broken 'buntu's is a fast track to unnoobing yourself).

---

### Post by critin on 2012-07-27
> Though fixing broken 'buntu's is a fast track to unnoobing yourself).

So true!  lol

---

### Post by ub07 on 2012-07-28
Since I use dial-up, I am very selective about which updates I install, and I usually check for updates about once per week.

---

### Post by MadmanRB on 2012-07-28
Just update, bugfixes are a good thing and what makes linux overall better then windows as the bugs actually... get fixed, perish the thought!

---

### Post by vasa1 on 2012-07-28
> **yuvraj23 said:**
> Oy! Don't use terminal for update i.e dist-update as you will end up with a kernel that is not recommended for you system.. Like I already have few updates pending related to new kernel ie headers,kernel image etc but am not updating to it at all! It expects 4gb of RAM and I have only 1GB. So its better to check what are you updating, Its only matter of minutes buddy! :)

I'm not sure that any of ^^^ is correct and I'd be surprised if it is.

---

### Post by yuvraj23 on 2012-07-28
> **vasa1 said:**
> I'm not sure that any of ^^^ is correct and I'd be surprised if it is.

Trust me I too got surprised. This kernel (Kernel Linux 3.2.0-23-generic-pae) contains drivers for nvidia on board graphics. 
                                                                  Few weeks ago, after installing Ubuntu I had tried to install graphics drivers but it used almost 50% ram and my computer used to hang from boot. Good know how I recovered from it. Therefore, am afraid to install even a simplest kernel update. If you have computer with better specs then you can do a test drive, btw you will always get an option to choose (at grub) which kernel you want to use.

Thankx
Yuvraj

---

### Post by HiImTye on 2012-07-28
> **yuvraj23 said:**
> Trust me I too got surprised. This kernel (Kernel Linux 3.2.0-23-generic-pae) contains drivers for nvidia on board graphics. 
                                                                  Few weeks ago, after installing Ubuntu I had tried to install graphics drivers but it used almost 50% ram and my computer used to hang from boot. Good know how I recovered from it. Therefore, am afraid to install even a simplest kernel update. If you have computer with better specs then you can do a test drive, btw you will always get an option to choose (at grub) which kernel you want to use.

Thankx
Yuvraj
that sounds like hardware issues, not an issue with the kernel itself. that's the problem with using kernels that are pre-release. if you stick to the official releases you should be fine. I do my best to stick to the repos and official or trusted PPAs for my canon printer drivers, nVidia updates, Gnome3, medibuntu, and WebKit updates (since I use LuaKit to browse). I am very selective in the sources I get software from so that I don't end up with issues down the road. if you follow a good selective policy for software sources then you can usually be pretty confident that updating your software will be a painless task.

---

### Post by yuvraj23 on 2012-07-28
> **HiImTye said:**
> that sounds like hardware issues, not an issue with the kernel itself. that's the problem with using kernels that are pre-release. if you stick to the official releases you should be fine. I do my best to stick to the repos and official or trusted PPAs for my canon printer drivers, nVidia updates, Gnome3, medibuntu, and WebKit updates (since I use LuaKit to browse). I am very selective in the sources I get software from so that I don't end up with issues down the road. if you follow a good selective policy for software sources then you can usually be pretty confident that updating your software will be a painless task.

Ya you are correct.. Its my hardware issue.. but even though I never update my kernel.. If I need one then i simple download its source and build one

---

### Post by Ji Ruo on 2012-07-29
> **yuvraj23 said:**
> Oy! Don't use terminal for update i.e dist-update 

This is actually true when *upgrading* to a new version of Ubuntu. However this is different from the regular updating that is done for the current version you are using.

You shouldn't use dist-upgrade to upgrade to a new version. It's an important difference between Ubuntu and Debian.

---

### Post by CharlesA on 2012-07-29
> **Ji Ruo said:**
> This is actually true when *upgrading* to a new version of Ubuntu. However this is different from the regular updating that is done for the current version you are using.

You shouldn't use dist-upgrade to upgrade to a new version. It's an important difference between Ubuntu and Debian.

dist-upgrade doesn't even upgrade you to the latest release unless you mess with the sources.list file **(don't do it)**.

The only thing dist-upgrade does that upgrade doesn't do is install new packages, such as updated kernels.

If you would rather use aptitude safe-upgrade, go for it. ;)

---

### Post by yuvraj23 on 2012-07-29
> **CharlesA said:**
> dist-upgrade doesn't even upgrade you to the latest release unless you mess with the sources.list file **(don't do it)**.

The only thing dist-upgrade does that upgrade doesn't do is install new packages, such as updated kernels.

If you would rather use aptitude safe-upgrade, go for it. ;)

Yup!

I didn't knew about aptitude thing... thankx for it :)

---

