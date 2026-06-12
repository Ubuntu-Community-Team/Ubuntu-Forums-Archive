---
title: "Upgrading to 12.04 yields Black Screen"
date: 2012-04-28
forum: New to Ubuntu
---

### Post by Andavane on 2012-04-28
This problem has occurred when I followed the upgrade path to shift the distro from 11.10 to 12.04, on a model I purchased in 2004, Sony Vaio VGN-S3HP It took quite a long while, then after installing it asked to reboot the computer. 
then it hung on a black screen. As there was no hard drive activity for over ten minutes i held down the on/off button to force it to close. When it booted the picture looked normal but on signing in, there was a pocture with garbled graphics.

I went control-alt-F2 and signed in, then went sudo halt and it went through the shut-down process, but hung before completing the shut-down (although it appeared most of the processes were completed).

Now I am unsure as to what to try next. I'm not  very experienced with the command line, but terminal sems to be working OK, so I hope there is something I can do.

Regards, John

---

### Post by wildmanne39 on 2012-04-28
Hi, try what is in this link please:
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Thanks

---

### Post by Andavane on 2012-05-01
> **wildmanne39 said:**
> Hi, try what is in this link please:
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Thanks

Thank you. I'm reading through this carefully, and trying to understand it.
I'm a bit concerned that it says it's mainly for problems from using 10.04 & 10.10. This old machine is 32-bit and had no problem at all with the 10's and the 11's series.

> vmalloc=xxxM
In some cases kernel drivers can not be loaded due to a lack of virtual addressing space on 32 bit systems. Logs will show errors like
Code:

allocation failed: out of vmalloc space - use vmalloc=<size> to increase size.

Details can be found here:
[http://www.mythtv.org/wiki/Common_Pr...lloc_too_small](http://www.mythtv.org/wiki/Common_Pr...lloc_too_small)

This has been reported by extremejosh who's machine failed to load the restricted nvidia drivers on a geforce 7350 and appears more or less common if you have several tv tuners. Increasing the size of vmalloc to 196 or even more may help in such cases.

i don't remember any issues like "allocation failed: out of vmalloc space - use vmalloc=<size> to increase size.". Graphics appeared with icons and pictures and stuff before the sign-in. But after singing in the screen just goes black with a winking cursor. That's when I ctrl-alt-f2 to sign into the terminal. After that, I am not sure what to do.

I shall need to ask for the machine to be fetched for me.

I need a plan of action as to what to do or type in. Have you any suggestions? When I'm in that situation, I am without this (Thinkpad) machine and have to write down any output on a piece of paper and then transcribe it back.

Looking forward to hearing! :)

Regards, John

---

### Post by wildmanne39 on 2012-05-03
Hi, truthfully I would install lubuntu it will run better on a old computer.
Thanks

---

### Post by Darkness Des on 2012-05-03
> **wildmanne39 said:**
> Hi, truthfully I would install lubuntu it will run better on a old computer.
Thanks
+1. It's a little different, but not much and it's still very simple. I recommend it for an older computer.

---

### Post by anewguy on 2012-05-03
Just for grins, I would try nomodeset in the boot options first as this sounds like a video driver problem.  If you get the GUI login screen, can login, THEN the screen goes black with a blinking cursor or the video is messed up, it sounds like the video driver.  Why this would be different from a prior release I don't understand but that doesn't make any difference.  Going to a terminal breaks you out of X so a driver problem wouldn't show in the terminal.  I would try nomodeset in the boot first - if that doesn't work there are other options to try as well.  If we can get you to the GUI, then you can go to Additional Drivers and let it search (and hopefully install) the correct driver.

Also, you wouldn't have seen the error message mentioned in the link unless you had searched your log file.

Dave

---

### Post by Andavane on 2012-05-05
> **anewguy said:**
> Just for grins, I would try nomodeset in the boot options first as this sounds like a video driver problem.  If you get the GUI login screen, can login, THEN the screen goes black with a blinking cursor or the video is messed up, it sounds like the video driver.  Why this would be different from a prior release I don't understand but that doesn't make any difference.  Going to a terminal breaks you out of X so a driver problem wouldn't show in the terminal.  I would try nomodeset in the boot first - if that doesn't work there are other options to try as well.  If we can get you to the GUI, then you can go to Additional Drivers and let it search (and hopefully install) the correct driver.

Also, you wouldn't have seen the error message mentioned in the link unless you had searched your log file.

Dave
and dear members all, thank you, I will first of all explain the background physical scene. I am manually only able to access one machine at a time and need to arrange physical help to change machines.
Now to try nomodeset first, I need to plan this in a miltary manner and engage my manpower.

So in this tutorial thread [http://ubuntuforums.org/showthread.php?t=1613132]("http://ubuntuforums.org/showthread.php?t=1613132") 

I'll be trying this section, viz:
"**How to temporarily set kernel boot options on an installed OS (not wubi)"**
Is that correct?

I'll switch on the Sony and it will boot and the picture you normally get before signing in with your password will be there, right?
My habit has been to sign in with my password. That's when the screen goes black with just a winking cursor. If then I go ctr-alt-f2 I move away from the x window thing, sign in with my username and password and I am in the terminal. Do  I try to get into nomodeset from there, or must I do it before signing in, say by pressing F6?

I need to plan my moves carefully because my caregiver will be near-by, but doing other things also and if I need more help I will need to arrange to have this thinkpad machine brought to me while I go to see what I have to do next, and then have this machine taken away and the black screen one brought to me.

This is my rough plan and if it needs improving, I'd much appreciate some help; will then print out the plan on a piece of paper or email it to myself on my mobile & take instfructions from there.
Looking forward to making out an Action Plan before I proceed!

Kind regards

John

---

### Post by anewguy on 2012-05-05
The nomodeset overrides kernel mode setting and as such is done far earlier in the boot - if you have a login screen it's gone too far.  What you want to do is press F6 continuosly right from a restart or reboot.  That should get the boot menu for you.  BTW - do you dual boot, say Windows and Ubuntu on the same machine, or is it a dedicated Ubuntu machine?

Dave

---

### Post by Andavane on 2012-05-05
> **anewguy said:**
> The nomodeset overrides kernel mode setting and as such is done far earlier in the boot - if you have a login screen it's gone too far.  What you want to do is press F6 continuosly right from a restart or reboot.  That should get the boot menu for you.  BTW - do you dual boot, say Windows and Ubuntu on the same machine, or is it a dedicated Ubuntu machine?

Dave

Hi: The machine with the problem is a dedicated Ubuntu Machine. It was running 11.10 and I upgraded it to 12.04.

regards

john

---

### Post by Andavane on 2012-05-06
> **anewguy said:**
> The nomodeset overrides kernel mode setting and as such is done far earlier in the boot - if you have a login screen it's gone too far.  What you want to do is press F6 continuosly right from a restart or reboot.  That should get the boot menu for you.  BTW - do you dual boot, say Windows and Ubuntu on the same machine, or is it a dedicated Ubuntu machine?

Dave

By 'continuously' do you mean hold the key down? I think not as it then let out a high-pitched whine,
I then started tapping continuously but it still took me to the log-in screen, which at the bottom says Ubuntu 12.04 LTS

> **wildmanne39 said:**
> Hi, truthfully I would install lubuntu it will run better on a old computer.
Thanks
I'll try a few more times with this, then try lubuntu with the Sony. In any case I have another machine to try that on, and old netbook eeePC with only 20 GB hard drive on it. That will be fun".:)

Regards to all,

John

PS: People show screen shots of their log-in screens.
How do they do that?

---

### Post by Andavane on 2012-05-06
Ah!
I still don't seem to have the knack of getting into the boot menu, but at the login screen I got into "Ubuntu 2D" which is where I'm posting this from :)

---

### Post by Andavane on 2012-05-19
Hi Ubunties
Due to my ISP messing up passwords on my account in a Big Way, I was without Broadband for a full week.

Just rounding off this thread by saying again that I never did get the hang of this nomodeset thing, but selecting 2D option got everything working fine.

Also thanks for introducing me to Lubuntu, so that's given me a project to work on with a netbook with a tiny hard drive (4GB & 16GB).

Thanks again,

John

---

