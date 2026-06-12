---
title: "Bad Luck... (mostly conversational)"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by Ruhoo246 on 2008-05-11
So I installed Gutsy about 6 months ago.  I fought with the video card settings for probably 3 of those months until i realized i needed to enable use of proprietary drivers XD  Still after that it took a little more work getting the resolution right, since it didn't offer anything over 800x600.  Then i tried to fix the sound.  No luck with that even to today... btw i have an Intel Corporation 82801H (ICH8 Family) HD Audio Controller which many people seem to have issues with, but no solutions for.  So I then upgraded to 8.04, and now my video is messed up again... I don't think I made any huge noob mistakes this time.  I allow proprietary drivers and what not.  Even though it says the drivers are enabled, it wont use them. at boot, it runs in safe mode.  I guess my main question is whether or not i should just stick it out and keep hardy, or downgrade back to gutsy.  I'd like to help out with the new os, but if i can't even get the video working straight i don't think i have much to offer otherwise.  Sorry about writing so much about nothing.  If you're wondering about my video card its a Nvidia 8600.

P.S.  I miss my compiz... *sniff*

---

### Post by 0ni on 2008-05-11
Just download the driverz off of the nvidia website brotha.

[http://www.nvidia.com/object/linux_display_ia32_169.12.html](http://www.nvidia.com/object/linux_display_ia32_169.12.html)

---

### Post by SunnyRabbiera on 2008-05-11
well compiz might not be viable for you, sometimes flashy effects can cuase more issues then being functional

---

### Post by Ruhoo246 on 2008-05-12
Sorry about this crazy post, I've been sick lately and I wrote this when I was a little delirious.  I actually tried to install the drivers manually, but when it goes to install them, it gives me a message about having to match exactly or something and ends the install.  I've actually read quite a few posts about it and nothing seems to work for me... But everything worked fine with 7.10.  Is there an easy way to downgrade back to 7.10?

---

### Post by wpshooter on 2008-05-12
> **SunnyRabbiera said:**
> well compiz might not be viable for you, sometimes flashy effects can cuase more issues then being functional

Amen +1

---

### Post by JoshuaRL on 2008-05-12
> **Ruhoo246 said:**
> Sorry about this crazy post, I've been sick lately and I wrote this when I was a little delirious.  I actually tried to install the drivers manually, but when it goes to install them, it gives me a message about having to match exactly or something and ends the install.  I've actually read quite a few posts about it and nothing seems to work for me... But everything worked fine with 7.10.  Is there an easy way to downgrade back to 7.10?

Nah man, you can't downgrade directly.  You'd have to reinstall 7.10.

But don't do that, you can easily just install the right driver.  Just follow these five steps to having a correctly installed Nvidia driver:

**Five Steps to Nvidia Driver Install!**

1). Reboot the computer and choose Recovery Mode from the GRUB menu.

2). Move into the Desktop:
```

cd /home/username/Desktop

```
The capitol "D" is important, and "username" is the name of the user that has the file in their desktop.

3). Find the name of the installer file:
```

ls

```
That's a lowercase L, not a 1. The file that you downloaded to the Desktop will show up here. When you use that name in the steps below, make sure you type it exactly. I'll be using "nvidiainstallerfile.run" as the fake name.

4). Change permission level of the installer file so it has internet access:
```

chmod +x nvidiainstallerfile.run

```
5). Run the installer file in a shell:
```

sh nvidiainstallerfile.run

```
Go through all the options, picking the defaults unless you KNOW you need something else. If it can't find the right kernal modules, it'll compile them for you no problems.  After that's done, you reboot the computer and the driver should be installed.

Congratulations!

---

### Post by Ruhoo246 on 2008-05-19
I tried the 5 step process, but i ran into a few issues XD First thing it had an issue with me using runlevel1, it said it wanted runlevel3 (telinit3).  No clue if that matters or not (no clue what it is lol).  The next was that it said no precompiled kernel matches. When it checks online, it doesn't connect, even though i gave it permission to. So... if you know whats wrong don't hesitate to say so, i'll try just about anything.  Thanks for you help!!!

---

### Post by JoshuaRL on 2008-05-22
> **Ruhoo246 said:**
> I tried the 5 step process, but i ran into a few issues XD First thing it had an issue with me using runlevel1, it said it wanted runlevel3 (telinit3).  No clue if that matters or not (no clue what it is lol).  The next was that it said no precompiled kernel matches. When it checks online, it doesn't connect, even though i gave it permission to. So... if you know whats wrong don't hesitate to say so, i'll try just about anything.  Thanks for you help!!!

Yeah, I get those too.  Just let it compile a kernal for you, and go ahead and run it in runlevel1.  Go ahead with the dialogs and it should download and work for you.

You can also try envy-ng.  It's in the repos now, and works great.

---

### Post by Nepherte on 2008-05-22
I think you need the build-essential package to install the nvidia drivers manually:
```
sudo apt-get install build-essential
```
Other than that, envy works great and is a lot easier to use.

---

