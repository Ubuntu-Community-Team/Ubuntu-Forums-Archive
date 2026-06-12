---
title: "Should I use the latest Ubuntu or LTS version?"
date: 2020-01-22
forum: New to Ubuntu
---

### Post by industryhonolulu on 2020-01-22
I'm new to Ubuntu, is it a bad idea to use the newest version or should I use the long term support version?  I mostly just play games on steam and use the browser (firefox)

---

### Post by yancek on 2020-01-22
It's really a personal decision but the primary reasons for moving to a non-LTS release would be if something is failing on the LTS or newer software that you want/need is available on a newer release and not on the LTS.  Much easier to upgrade from one LTS to another is a 3rd reason.

---

### Post by CelticWarrior on 2020-01-22
> **yancek said:**
> It's really a personal decision but the primary reasons for moving to a non-LTS release would be if something is failing on the LTS or newer software that you want/need is available on a newer release and not on the LTS.  Much easier to upgrade from one LTS to another is a 3rd reason.

+1

But brand new hardware is a reason in itself to use the latest release regardless of the LTS status.

---

### Post by CatKiller on 2020-01-22
As a general rule I recommend new users go with the LTS releases. They have 5 years of support, but the interim releases only get 9 months. New users sometimes to forget to upgrade, so they end up stranded on the interim releases. LTS releases get all the security fixes, but don't get new versions of most software.

The main exception is if the user has very new hardware, particularly very new AMD hardware. It takes a little while for support for that hardware to trickle down, so being on the newer releases gets you that support sooner.

If you need other very new software that's only available in a non-LTS release, then you need to go with the non-LTS release, obviously, and remember to upgrade when the time comes.

---

### Post by Autodave on 2020-01-22
19.10 is the most current release.  I would probably install that and then upgrade to the 20.04 LTS release in a few months.  And then I would stay with 20.04.

---

### Post by rsteinmetz70112 on 2020-01-22
> **Autodave said:**
> 19.10 is the most current release.  I would probably install that and then upgrade to the 20.04 LTS release in a few months.  And then I would stay with 20.04.

That makes a good deal of sense. If you want to upgrade only to LTS versions you can set the system to only offer you LTS upgrades. You will be offered an upgrade at 20.04.1 which should appear around June or July.

---

### Post by bunny9000 on 2020-01-22
As above, LTS. You can always go to the software authors website and get the newest software release of your favourite app if it has not been put in the repos yet, like gimp image editor, etc.

---

### Post by Perfect Storm on 2020-01-22
One more vote for LTS.

And if you want to play Windows games on steam, you'll need to install proton on steam. You'll do that in steams settings ---> Steam Play

---

### Post by yetimon_64 on 2020-01-22
> **industryhonolulu said:**
> I'm new to Ubuntu, is it a bad idea to use the newest version or should I use the long term support version?  I mostly just play games on steam and use the browser (firefox)

For your usage style noted above and the longer support periods with each install, sticking with LTS is what I'd recommend.

**Edit**: I'd only consider intermediate installs if some new hardware required the latest kernel etc, otherwise LTS.

---

### Post by TheFu on 2020-01-22
I'm an LTS-only user, unless I happen to have specific hardware that needs a newer kernel.  I don't want to be forced to update or more likely, reinstall, every 6 months.

Today, I'm still running 16.04 across almost all systems. So far, only 1 program where I needed a newer release wasn't available and it wasn't THAT important to risk my current stability.  The more social networking software you use, the more likely that newer software will be required.  That is not me.

If I were new, I'd install 18.04 today, which has no hassle support until 2023, so you aren't forced to move to 20.04 in the early months as the larger bugs addressed.  More and more, Canonical has been putting out less and less "finished" code with each release.  There are still issues with 16.04 updates to networking, for example as they try to move more and more of that under systemd.  To a typical desktop-only user, perhaps those changes don't matter?  IDK. I'm not a typical user.

If you jumped onto Win10 alpha releases, then you would probably be happy with 19.10.
If you ran Win7 until last month, then you'd probably be happiest with 18.04.

I have the luxury of being able to choose whatever OS I want.  I'm hoping that 20.04 will meet my stability needs better than 18.04 does.  I'm afraid that some larger architecture choices by Canonical will force me to move to Debian next fall, before 16.04 support ends in 2021. With Linux, 1-size doesn't fit everyone, so we have choices.

New is the enemy of stable.

---

### Post by mastablasta on 2020-01-23
> **CelticWarrior said:**
> +1

But brand new hardware is a reason in itself to use the latest release regardless of the LTS status.


LTS has hardware compatibility stack, so you can install new kernels to get support for new hardware on the LTS edition. i still went with LTS, but used new kernel (same as in 19.10) for compatibility. there were no driver issues and i am on 18.04 LTS until next year when i will upgrade to the next LTS (20.04).

---

### Post by Perfect Storm on 2020-01-23
If you're setting up a linux gaming computer, you may try check out "Game Mode" for Linux; *There's an article on OMGUbuntu about it: [https://www.omgubuntu.co.uk/2019/08/feral-gamemode-ubuntu](https://www.omgubuntu.co.uk/2019/08/feral-gamemode-ubuntu)

---

### Post by Impavidus on 2020-01-23
Originally, I used LTS releases only. 6.06 LTS, 8.04 LTS, 10.04 LTS. Then I got a new computer that didn't like 10.04 LTS, so I installed 11.04. IIRC, the HWE stack was only introduced with 12.04 LTS. I upgraded then to 11.10, 12.04 LTS and planned to stick to LTS releases only again. But after a while I got annoyed by older software. Some add-ons for a number of packages I used where no longer available for the versions on 12.04 LTS. You can (as bunny9000 writes) install later version of software manually or (better) from PPA, but it's harder and often gives instability. So, I installed 13.10. From then onwards I have used the short term releases, but I dual boot and always keep one older LTS release on my other partition as a spare. I rarely need it. I usually fresh install e.10, wiping (e-2).04 LTS in the process, and upgrade it three times until I have (e+2).04 LTS, with e an even number. It works for me.

So, for a server, I suggest LTS releases. Servers rarely need the latest features, but need stability as they tend to run unattended and annoy many people if they don't work. For a desktop/laptop, it depends. I don't mind the slightly less polished nature of the short term releases, found release upgrades reliable and easy and don't mind occasionally fixing something, as I usually manage. But if you're new, it's probably better to stay with LTS releases.

The next LTS release is 20.04 LTS. You could now install 18.04 LTS, but 19.10 is also a single step away from 20.04 LTS, so for the number of release upgrades or fresh installs it doesn't matter. If you want to move to 20.04 LTS soon, install 19.10. Else I suggest 18.04 LTS.

---

### Post by mörgæs on 2020-01-23
> **Impavidus said:**
> If you want to move to 20.04 LTS soon, install 19.10. Else I suggest 18.04 LTS.

Yes, this sentence sums it all up. The LTS part of 18.04 has no value if you are going to 20.04 anyway. 

Test 19.10 on your particular hardware and see if you have any reason to consider old software - I wouldn't expect it.

---

### Post by MoebusNet on 2020-02-04
> **TheFu said:**
>  [SNIP] I'm afraid that some larger architecture choices by Canonical will force me to move to Debian next fall [SNIP]. With Linux, 1-size doesn't fit everyone, so we have choices.

New is the enemy of stable.

+1

---

### Post by odesseylost on 2020-02-14
It really depends on what you´re looking to do. I like the updates in 19.04 and 19.10 but I´m using 18.04 LTS since the programs I need are better supported on 18.04 LTS. Also depending on your hardware and it´s compatibility you may find that patches are fewer and further between on the new releases. For instance my girlfriend has a Microsoft Surface Laptop, it has some compatibility issues and Jake Day´s kernel fixes them brilliantly, his updates fail in 19.04 due to the new kernel, so if she were to upgrade she´d have to go through all that hastle again but with a new library, so she´s content with 18.04 LTS until 20.04 comes out.

---

