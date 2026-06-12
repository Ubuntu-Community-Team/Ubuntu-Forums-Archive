---
title: "What's the diff. between Ubuntu MATE and Ubuntu with MATE desktop?"
date: 2020-04-23
forum: New to Ubuntu
---

### Post by rocket57 on 2020-04-23
Hi folks -newbie again!

I'm realizing from research that I can get a MATE look in Ubuntu. I just don't like the Unity desktop that much...
Since I would rather have an LTS that's good to 2023, instead of 2021, and I'm not a programmer or IT/Server guy,
are there any caveats to just installing the Ubuntu 18.04 LTS and putting a MATE desktop on it instead of installing Ubuntu MATE 18.04,
especially in terms of stability and security?

Thanks for your help!
Rocket

---

### Post by CelticWarrior on 2020-04-23
Installing Ubuntu-MATE 20.04 gives you full support until 2023.

---

### Post by TheFu on 2020-04-23
Every package has a support period.  The **ubuntu-support-status** command let's you see which packages are supported by Canonical and which are not.  Ubuntu-Mate would be supported for 3 yrs from the release date, I would expect.

As for risks, that's hard to say. Nobody can predict how many bugs will happen in code 3 yrs in advance. There are always risks in running any software.  The risks are greater the more that networking is part of the software.  Stability and security can never be predicted for just 1 program since the underlying libraries feed into that total.  IF those underlying libraries aren't being patched, who can say what each does to stability or security?

Immediately after installing 20.04, run the **ubuntu-support-status** command and see which aren't supported already. Probably worth running that every month to see the unsupported package list grow over time. In 2023, I'd start being very concerned.

---

### Post by grahammechanical on 2020-04-23
Ubuntu stopped using the Unity User Interface when 17.10 was released. A default install of Ubuntu 18.04 LTS will have a Ubuntu customized Gnome 3 Shell User Interface. The same is true of Ubuntu 20.04 LTS.

[https://arstechnica.com/information-technology/2018/05/ubuntu-18-04-the-return-of-a-familiar-interface-marks-the-best-ubuntu-in-years/](https://arstechnica.com/information-technology/2018/05/ubuntu-18-04-the-return-of-a-familiar-interface-marks-the-best-ubuntu-in-years/)

If the default user interface of Ubuntu does not suit you it might be preferable to install one of the other Ubuntu family members that has a user interface that is closer to your taste. 

Regards.

---

### Post by Dennis N on 2020-04-23
> are there any caveats to just installing the Ubuntu 18.04 LTS and putting a MATE desktop on it instead of installing Ubuntu MATE 18.04

Ubuntu 18.04 + MATE desktop added later will still have the Gnome desktop packages installed. And the MATE packages you add are still only supported to 2021. Some will duplicate functions provided by Gnome Desktop applications - you will have two file managers, for example.

Ubuntu MATE 18.04 has no Gnome Desktop specific packages installed.

---

### Post by rocket57 on 2020-04-23
Thanks again guys!
I think I should just stick with Ubuntu MATE 18.04 and learn more about using Linux instead of vacillating over what version to use.
I have a bit of a perfectionist streak, but as I have been reminded a few times no, no distribution is going to be perfect.
Still wondering what all the hubbub is concerning "snaps" and wondering if they are secure or not...
I learn something every time I post.
Rocket

---

### Post by jim Kane on 2020-04-23
You could try Xubuntu it has the Xfce desktop which is much less Dark doom and gloom ;)

---

### Post by CelticWarrior on 2020-04-24
> **rocket57 said:**
> Thanks again guys!
I think I should just stick with Ubuntu MATE 18.04 and learn more about using Linux instead of vacillating over what version to use.
I have a bit of a perfectionist streak, but as I have been reminded a few times no, no distribution is going to be perfect.
Still wondering what all the hubbub is concerning "snaps" and wondering if they are secure or not...
I learn something every time I post.
Rocket

Again, Ubuntu-MATE 20.04 is already out. If you want the longer support the newer LTS should be the choice, there's really no point in keeping a two years old release with only one year left of support. Keep in mind flavors only have 3 years, standard Ubuntu has 5.

Snaps are arguably safer than the old way. Some would say too much and because of that inconvenient.

---

