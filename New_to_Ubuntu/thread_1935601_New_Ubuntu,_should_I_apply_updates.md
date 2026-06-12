---
title: "New Ubuntu, should I apply updates?"
date: 2012-03-04
forum: New to Ubuntu
---

### Post by Cyle902 on 2012-03-04
Hello,

I previously installed Ubuntu 11.10  on a home built machine. It worked fine until I applied the 345 updates in the update manager. Somehow my Package System was broken.

Since Then I have reinstalled ubuntu 11.10 and was wondering if I should re apply these updates right away or is there something I should do before that?

---

### Post by sffvba[e0rt on 2012-03-04
Which version of Ubuntu (because if it is any version except 12.04 then you should update your system)?


404

---

### Post by Cyle902 on 2012-03-04
Version 11.10

---

### Post by TheFu on 2012-03-04
Yes, you definitely want to do updates very near the first thing you do. It contains fixes and security updates.  I don't know how you are applying all the updates, but be certain you allow the kernel updates too.  On the command line, the command is 
```
$ sudo apt-get update
$ sudo apt-get dist-upgrade
```That number of updates sounds really excessive - perhaps it would be easier to download and install the latest version of your specific distro - i.e. from a newer ISO?

---

### Post by Cyle902 on 2012-03-04
I am using the most recent ISO image straight from Ubuntu. I downloaded it and created a startup disk with a USB

---

### Post by sffvba[e0rt on 2012-03-04
Well, 11.10 is the latest version of Ubuntu and installing updates shouldn't be an issue and it is recommended to do so.

If you update and your package system becomes "broken" again you can seek assitance on the forum to remedy the situation.


PS - On a side note (in terminal you can use):

```
sudo apt-get update && sudo apt-get upgrade
```


404

---

### Post by Cyle902 on 2012-03-04
Okay im runnig the updates now, I'll let you know how it works out.

Please reply so I dont have to double post. :)

---

### Post by sffvba[e0rt on 2012-03-04
Well, you can edit your post ;)


404

---

### Post by Cyle902 on 2012-03-04
Okay So I ran the updates and everything went smoothly.

But there are a 8updates that didn't install.

Including:
**"Important Updates"**
-complete generic linux kernel
-Header files related to linux version 3.0.0
-Linux kernel headers for version 3.0.0 on x86/x86_64
-Generic linux kernel headers
-Linux kernel image for version 3.0.0 on x86/x86_64
-Generic linux kernel image
-Utility for browsing, installing and removing software
[B]"Distribution updates"
[/B]-Compression method of 7z format in 7-zip program

---

### Post by snowpine on 2012-03-04
Make sure you are running the **exact** commands recommended in post #4 (you can use copy & paste to avoid typos) and copy & paste the **full** output so we can see the error messages. :)

(edit) but don't include the **$ **symbol in the command, that is just to show you the prompt. :)

---

### Post by Cyle902 on 2012-03-04
I didnt receive any error messages.

And I did copy/paste the commands to the terminal and it updated(I assume flawlessly).
But the Update manager says I still have the 8 updates previously listed.

---

### Post by HeroOfCanton on 2012-03-04
Some updates require a reboot before being able to install. Have you rebooted and tried again?

---

### Post by Cyle902 on 2012-03-04
> **HeroOfCanton said:**
> Some updates require a reboot before being able to install. Have you rebooted and tried again?

Ill do that now

edit: Okay, I rebooted amd the update manager still shows the updates available. I guess Ill just apply them and see what happens

---

### Post by snowpine on 2012-03-04
> **Cyle902 said:**
> I didnt receive any error messages.

And I did copy/paste the commands to the terminal and it updated(I assume flawlessly).

Prove it to me by copying & pasting the full output (including the command you issued) otherwise I'm not sure what I can do to help. If the updates applied "flawlessly" then I'm not sure I understand the problem. :)

---

### Post by Cyle902 on 2012-03-04
Lol no problem, all updates installed successfully this time around.

Thanks everyone for all your support!

---

### Post by HeroOfCanton on 2012-03-04
> **Cyle902 said:**
> Lol no problem, all updates installed successfully this time around.

Thanks everyone for all your support!

I love it when simple works. :D Keep an eye out when you do updates. Some of them will display a Restart button after they install (top right of update manager screen). When that shows make sure you reboot before trying any more.

---

### Post by snowpine on 2012-03-04
Probably you did **sudo apt-get upgrade** instead of **sudo apt-get dist-upgrade** the first time, and that is why the new kernel did not install.

Just a guess.

---

### Post by sffvba[e0rt on 2012-03-04
> **snowpine said:**
> Probably you did **sudo apt-get upgrade** instead of **sudo apt-get dist-upgrade** the first time, and that is why the new kernel did not install.

Just a guess.

Doubt that.  I never use *dist-upgrade* (except in the rare case when I actually want to upgrade my distro to a new release) and if a new kernel etc. is available *upgrade* works to install it.


404

---

### Post by maheshtatva on 2012-03-05
i installed gnome 3 and untiy after updation my system became slow any suggestion

---

### Post by TheFu on 2012-03-05
the "upgrade" command to apt-get doesn't replace the kernel, which you probably want.  It is there for the times when you can't or do not wish that.  99% of the time you should do it.  That's why my CLI version showed the "dist-upgrade" command instead. This **will** upgrade the kernel.

If you don't change your APT sources, dist-upgrade applies kernel  updates and other system updates tied to the kernel update. It does not  update your release from 10.04 to 12.04 for example.  It will update  your dist from 10.04.3 to 10.04.4 when it is available.  That upgrade is  probably a good thing.

From the apt-get man page:[I]
dist-upgrade in addition to performing the function of upgrade, also  intelligently handles changing dependencies with new versions of  packages[/I]

Basically, I always use dist-upgrade.

---

### Post by snowpine on 2012-03-05
> **TheFu said:**
> Basically, I always use dist-upgrade.

Me too. :)

---

