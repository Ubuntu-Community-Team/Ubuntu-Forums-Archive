---
title: "Can't run updates or open Software Center"
date: 2013-09-26
forum: New to Ubuntu
---

### Post by dylan7 on 2013-09-26
Hey guys,

I'm very very new to Ubuntu. I've got 12.04LTS successfully dual booted on my desktop with Windows 7 (both 64-bit), so I tried to do the same on my laptop with 13.04. After the first install, Windows was somehow corrupted and would not boot. I had one of my friends look at it, try to save it, but all his attempts failed. So, I reinstalled Windows Ultimate 64-bit on my laptop and had the same friend partition my hard drive better, so that Ubuntu would run better, or so he claimed. After the install, both operating systems ran fine. For two days.

I discovered yesterday that the Software Center would not open. When I would select the Software Center icon, the following pop-up box would appear: 

"Sorry, can not open the software database
Please re-install the 'software-center' package."

So, like the naive person I am, I googled the issue, downloaded the software-center package, and could not figure out how to install the package. Since my only prior experience was from Windows, I looked through every folder to find an .exe, to no avail. So I googled that too! And I found my problem was much, much larger.

Some of the results I read said to use the following commands on the terminal:
```
sudo apt-get update
sudo apt-get upgrade
```

The first command ran as it should, no errors found. The second ended with the folloring two lines:
```
dpkg: error: corrupt info database format file '/var/lib/dpkg/info/format'
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

I googled this, too, and I found more of the same thing, but without that specific file. I tried everything that did not seem file-specific on this post: [http://ubuntuforums.org/showthread.php?t=2112029](http://ubuntuforums.org/showthread.php?t=2112029) 

Additionally, every thirty minutes or so, the Software Updater GUI pops up, saying that I need to download a lot of updates, which I can agree with. So I select install, put in my password, and another pop up appears that says that some of the updates are unlicensed. The only two options are "Okay" and "Settings", so I would just click okay. Normally (4 out of 5 times), the box would disappear, and nothing would happen. The Software Updater would come back after a little while, and I would just repeat the same thing. Occasionally (the fifth time), another box would pop up, saying installing updates, and it would have a loading bar. This hurts me to say, but the first time it came up, it seemed like it was working, But I was in class, about 15 minutes from the end of class (which I would then have to leave campus), and my battery was about 10 minutes from dying. So... I canceled the updates, packed up my stuff, and went home, thinking that I could just do the same thing that night, which never happened (the errors returned). I've even been trying since starting this post, and I've began to get this error after the box with the loading bar pops up. That goes away, and is replaced with this:

"Package Operation Failed
The installation or removal of a software package failed."

And now, as of about an hour ago, Windows won't boot anymore, it stops right after the logo appears. I gave it about 10 minutes of just sitting on the Windows logo, but to no avail.

And I just don't know what to do anymore. I've considered just reinstalling Windows (again) and scrapping my hopes and dreams of using Ubuntu. It's clearly not meant to be. I can post full system specs and full blocks of code, if anyone thinks that will help.

Thanks guys,
Dylan

---

### Post by grahammechanical on 2013-09-26
There are two separate issues here. We can do more damage when we confuse problems with each other. The Windows issue is separate from the Ubuntu Update Manager issue.

Do you still get a Grub boot menu? If you do, at the Grub boot menu select Advanced Options for Ubuntu. And then select the Recovery Mode option. This is on 13.04, by the way. You will get the Recovery Menu and you can select dpkg - repair broken packages. That may fix what is wrong. You will be brought back to the Recovery menu where you can select Resume and that will load to a desktop with a lower video resolution. A further reboot will fix the lower video resolution situation.

Now run those two apt-get update and upgrade commands again. See what happens.

Of course, if you re-install Windows you might want to also re-install Ubuntu. That will solve it. Maybe.

As regards the software Centre, If and when you can run

```
sudo apt-get remove software-center
```
```
sudo apt-get install software-center
```

Regards.

---

### Post by dylan7 on 2013-09-26
Thank you for the advice, I haven't tried it yet. I wanted to clarify, should I run the get update and get upgrade commands in the recovery mode as well, or the normal boot? Yes, I still have access to the Grub menu and 13.04. I will have to reinstall Windows, and that will overwrite the boot menu, so I will have to reinstall Ubuntu as well. But for now, I will try booting into the Recovery mode and attempting to repair the damages packages.

Thank you for the advice and the quick response.

---

### Post by dylan7 on 2013-09-26
Okay, so I ran the option in recovery mode, like you suggested. At the end of all of it, the same two error lines appeared, and then it said "Finished, press enter to continue." I hit enter, it took me back to the recovery screen. I selected to boot normally, ran the get update and get upgrade commands, update was fine, like normal, and upgrade got the same error again. I shut down the computer, let it sit for a few seconds, and booted back to Ubuntu, ran the two commands again, with the same results. Since I have to reinstall anyway, I might just try to install 12.04LTS and see if that works any better for me. But I'm still willing to try to get 13.04 to work, if you have more suggestions!

---

### Post by dylan7 on 2013-09-26
I really should have put this all in one post, I'm so sorry. I just tried to run the remove software-center command, the following was produced, just like get upgrade:
```
sudo apt-get remove software-center
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  software-center ubuntu-desktop
0 upgraded, 0 newly installed, 2 to remove and 256 not upgraded.
After this operation, 3647 kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: error: corrupt info database format file '/var/lib/dpkg/info/format'
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

---

### Post by kmb9205 on 2013-09-27
I'm in the same boat as you with regard to experience with linux.  My suggestion would be to try the above commands but you've already thought of that. I finally just removed 13 and created a pendrive with 12.04 and loaded it that way. I got my windows back and all seems to be stable with both for the past few days. I guess 12.04 might possibly be better for you as it is long term support. That was my thinking for myself anyway.

---

### Post by mansonfan78 on 2013-09-27
try running "sudo apt-get clean" and then try the update and upgrade commands.

---

