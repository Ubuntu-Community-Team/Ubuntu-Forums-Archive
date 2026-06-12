---
title: "Going back to Hardy"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by ex-wirecutter on 2008-11-05
Despite strenuous efforts to get Ubuntu 8.10 to run in wide screen , including changing video cards and x-fix , and as display config no longer exists , it seems determined to stay in 800X600 4:3 mode. This means that in some windows I cannot see the bottom right hand corner which is useless.
So unless some kind person comes up with a solution I am going back to Hardy
Video cards I have tried include Nvida , ATI , and VIA .

---

### Post by mapes12 on 2008-11-05
Can't blame you. Many posts are appearing about screen res issues in 8.10 and as you rightly point out edits in the xorg.conf file are fairly useless in 8.10.

I have a similar issue but will be trying a different video card before rolling back.

Best of luck.

---

### Post by ratmandall on 2008-11-05
I have the same problem and the drivers for my graphics card are only for 7.10, I had a higher res in hardy but now i'm stuck in 800x600 :mad:

---

### Post by bscbrit on 2008-11-05
[http://ubuntuforums.org/showpost.php?p=6086662&postcount=8](http://ubuntuforums.org/showpost.php?p=6086662&postcount=8)

Before you change back, can I ask you to please look at this post and, if you try it, let us know if it helped you.  From what I read, it cannot make your system any worse and it worked for me and a few others.  Its worth a try.

---

### Post by bscbrit on 2008-11-05
mapes12

I don't think it is correct to say the edits in xorg.conf are of no use.  By copying my xorg.conf from 8.04 to 8.10 I recovered my displays again.  The problem is, as I see it, that there is no easy way - or no easy 'approved' way - of getting your settings into xorg.conf.  I experimented with downloading the displayconfig-gtk and dependencies from 8.04 and it worked like a dream.  I've used on 2 systems now to input my graphics card and monitor information.

I know that xorg 7.4 uses HAL, but it doesn't entirely ignore video settings in xorg.conf.  I don't think that the same is true of keyboards and mice i.e. corrections in xorg.conf are ignored in these instances.  But, I'm still trying to learn how the new system should work and how a user is meant to input the information that is required when the automatic system fails.

If you know the answers, or have any clues as to where I might find them, they would be welcome.  My googling fingers are getting sore!

---

### Post by bscbrit on 2008-11-05
ratmandall

I don't think that my suggested solution to this problem will work in your case.  If the drivers are not correct then it doesn't matter how you install them, they still will not work properly.

---

### Post by philinux on 2008-11-05
> **ex-wirecutter said:**
> Despite strenuous efforts to get Ubuntu 8.10 to run in wide screen , including changing video cards and x-fix , and as display config no longer exists , it seems determined to stay in 800X600 4:3 mode. This means that in some windows I cannot see the bottom right hand corner which is useless.
So unless some kind person comes up with a solution I am going back to Hardy
Video cards I have tried include Nvidia , ATI , and VIA .

Have you raised bugs at lauchpad. The only way the autodetect will work 99.99% is if people report the failures. Since xorg is set to disappear completely.

---

### Post by ratmandall on 2008-11-05
> **bscbrit said:**
> ratmandall

I don't think that my suggested solution to this problem will work in your case.  If the drivers are not correct then it doesn't matter how you install them, they still will not work properly.
Yea you're right.

---

### Post by bscbrit on 2008-11-05
philinux

I'm trying to isolate the problem and find a usable solution before I raise my bug report but I encourage everyone to raise bug reports so that the extent of the problem is apparent.  I know that others have complained about the problem so it is not as if the issue is unknown.  But if I can give the devs a possible lead to a solution it might get addressed quickly.  It won't hurt to take a few days to try to solve the problem - I don't see an fix for this coming out in the next couple of weeks.

I wouldn't usually recommend installing packages from an earlier distro version but, as all the dependencies are met under 8.10, I do not see it as much of a risk, particularly if the only other solution is a reformat and return to 8.04.

---

### Post by philinux on 2008-11-05
Yep, the autodetect is failing for some hardware configs and when it does there's not a lot you can do with xorg unless you know exactly what to put in the file. Jockey is supposed look after things. System>admin Hardware Drivers.
When this fails you're up the creek at the moment.

---

### Post by bscbrit on 2008-11-05
Reported as bug report 294202 - I've decided to add more information as I get it.

---

### Post by mapes12 on 2008-11-05
> [http://ubuntuforums.org/showpost.php...62&postcount=8](http://ubuntuforums.org/showpost.php...62&postcount=8)

Before you change back, can I ask you to please look at this post and, if you try it, let us know if it helped you. From what I read, it cannot make your system any worse and it worked for me and a few others. Its worth a try.

I tried it and the application had my graphics card and monitor listed. I selected them and the screen res I need i.e. 1024x768 became available so I selected that as well. I then had a look at my xorg.conf file which now contained the correct screen res, driver and looked like what I needed. To restart X I logged out then back in again. But on logging back in a window popped up telling me I had 3 choices:

1. Start in low graphics mode
2. Reconfigure graphics
3. Troubleshoot graphics

I have played around with all the options but the same result occurs every time. What hapens is the xorg.conf is rewritten exactly the same as before i.e. the changes made by gksudo displayconfig-gtk are deleted and the previous xorg.conf reinstated with the file edited by gksudo displayconfig-gtk then renamed as a backup.

Net result = I'm no closer to resolving my problem.

---

### Post by bscbrit on 2008-11-05
Thanks for the feedback. So if I can just summarise for my own benefit:

It allows you to set the correct display parameters.

The new settings are NOT persistent over a reboot.


OK, thanks again.  I've raised a bug report but I've got some more head-scratching to do.

---

### Post by bscbrit on 2008-11-05
When you get back to Hardy, make a copy of your xorg.conf and keep it safe somewhere.  For my first attempt at solving this problem, I copied my working xorg.conf from 8.04 to 8.10 and it has stayed like that for 5 days now.

---

### Post by DrMega on 2008-11-05
> **philinux said:**
> Have you raised bugs at lauchpad. The only way the autodetect will work 99.99% is if people report the failures. Since xorg is set to disappear completely.

There are certain hardware arrangements that simply have to be manually configured because the hardware doesn't send the necessary info to enable software to interpret it.

For example, in my xorg.conf, I have a ScreenSize setting for my second display (my widescreen TV which is connected via an s-video TV-Out port). If I didn't set that manually, it is reported to some apps as being 0x0 and even those that do work assume the aspect ratio to be 4:3.

---

### Post by philinux on 2008-11-05
> **DrMega said:**
> There are certain hardware arrangements that simply have to be manually configured because the hardware doesn't send the necessary info to enable software to interpret it.

For example, in my xorg.conf, I have a ScreenSize setting for my second display (my widescreen TV which is connected via an s-video TV-Out port). If I didn't set that manually, it is reported to some apps as being 0x0 and even those that do work assume the aspect ratio to be 4:3.

This is going to be tough then for some hardware configs then when xorg goes completely.

---

### Post by DrMega on 2008-11-05
> **philinux said:**
> This is going to be tough then for some hardware configs then when xorg goes completely.

Yep. It won't affect me though as I'm stuck on 7.10 anyway. I'm one of the many who found 8.04 LTS unusable due to the random freeze bug:(

---

### Post by OrangeCrate on 2008-11-05
> **ex-wirecutter said:**
> Despite strenuous efforts to get Ubuntu 8.10 to run in wide screen , including changing video cards and x-fix , and as display config no longer exists , it seems determined to stay in 800X600 4:3 mode. This means that in some windows I cannot see the bottom right hand corner which is useless.
So unless some kind person comes up with a solution **I am going back to Hardy**
Video cards I have tried include Nvida , ATI , and VIA .

Rather than either/or, why don't you dual boot Hardy and Intrepid? I do, on both of my computers. Then just use Hardy day-to-day, and leave 8.10 alone, until Intrepid has enough time, and updates to potentially fix your problems.

---

### Post by Yashiro on 2008-11-05
If people wanted unstable useless systems they'd still be on Windows! :D 

Suggesting someone dual boots two releases of the same distro that are only months apart is not the answer.
Ubuntu is a desktop linux solution. If people cannot get onto, or use their desktops this is a huge failure. 

A GUI (and a working backend) to set display options needs to return, fast.

---

### Post by torgrot on 2008-11-05
> **Yashiro said:**
> If people wanted unstable useless systems they'd still be on Windows! :D 

Suggesting someone dual boots two releases of the same distro that are only months apart is not the answer.
Ubuntu is a desktop linux solution. If people cannot get onto, or use their desktops this is a huge failure. 

A GUI (and a working backend) to set display options needs to return, fast.

Here Here.

torgrot

---

### Post by mapes12 on 2008-11-05
> Thanks for the feedback. So if I can just summarise for my own benefit:

It allows you to set the correct display parameters.

The new settings are NOT persistent over a reboot.

Spot on!

If you want me to re run some of the file outputs just let me know.

And thanks for posting the bug report.

---

### Post by bscbrit on 2008-11-05
No - thanks for the offer, but you're going to be busy re-installing 8.04!

Good Luck, and thanks again. :-)

---

### Post by mapes12 on 2008-11-05
> No - thanks for the offer, but you're going to be busy re-installing 8.04!

I'll give another graphics card a go before resorting to this. My onboard Rage XL is not supported according to the X.org wiki so I have an S3 Savage on its way to me via eBay which is supported (hopefully). Princely sum of £4.50 inc P&P. Can't complain at that.

Thanks for your posts.  ):P

---

### Post by OrangeCrate on 2008-11-05
> **Yashiro said:**
> If people wanted unstable useless systems they'd still be on Windows! :D 

**Suggesting someone dual boots two releases of the same distro that are only months apart is not the answer.**
Ubuntu is a desktop linux solution. If people cannot get onto, or use their desktops this is a huge failure. 

A GUI (and a working backend) to set display options needs to return, fast.

If one of the versions is an LTS, and will be supported for three years, it sure is. You'll always have a stable version to fall back on, if you run into problems with the integral upgrades between LTS releases.

---

### Post by Yashiro on 2008-11-05
So just stay on the LTS. There's nothing in Intrepid thats a significant upgrade over Hardy.

---

### Post by ex-wirecutter on 2008-11-06
Many thanks for all the replies , have tried most of the ones I could with my limited knowledge , but none worked and some screwed up my computer , so I will go back to Hardy .

---

### Post by agoodliffe on 2008-11-06
yeah i am going back to Hardy as well after spending waaaaaaay too much time trying to get my sound to work, and to not log off mysteriously in mid session. 
I am new to Linux can you explain how to go back from Ibex to Hardy?
Thank you

---

### Post by ex-wirecutter on 2008-11-06
As stated in my last post I only have limited knowledge but had done a backup to DVD before doing the upgrade so all I had to do was reinstall .
However I am sure there are people on this forum who may be able to help so suggest you open a new thread , otherwise its start from scratch and loose all your personal information I suppose. 
Good luck.

---

### Post by bscbrit on 2008-11-06
agoodlife

As ex-wirecutter has said, there is no easy route to changing from 8.10 to 8.04.  Back up all the data that you want to save and then re-install the OS from CD/DVD.  Restore your personal data and you're good to go.  Depending on how much data you have to transfer and restore from backup, you could be up and running again quite comfortably inside an hour.  Being pessimistic, give yourself a couple of hours to get thing just how you like them. :-)

---

