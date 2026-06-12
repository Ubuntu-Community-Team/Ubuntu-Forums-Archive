---
title: "Understanding the upgrade process?"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by shatteredmindofbob on 2008-10-23
As someone whose still kinda new to Ubuntu and Linux in general, I have a few questions with a new version on the horizon and what to expect. 

First off, I've started updating programs myself since I've noticed the official repositories are pretty slow to get updated (as if I still want to use Gimp 2.4 when 2.6 is such a massive improvement.) Is that going to cause issues when upgrading? 

Same goes for third-party repositories, I've heard this can be an issue...for example, I'm getting my Wine updates from their repository now...is that going to break? 

Sorry if these seem like stupid questions but I've found discussion of installing software in Linux kind of confusing, especially when reading the all-out-war that is this: [http://brainstorm.ubuntu.com/idea/14433/](http://brainstorm.ubuntu.com/idea/14433/)

which gets really confusing...especially the part about using the Firefox 3 Beta for Hardy with someone stating: "It's an LTS, if the beta wasn't included, it'd be three years before they got FF3." I guess I don't understand why someone can't get the latest version of Firefox when it comes out regardless of operating system version, which what people do any other operating system. 

Or maybe I should just not be reading such forums and continue on as I am without getting confused?

---

### Post by Crandom on 2008-10-23
What people are saying is that it is still easy enough to upgrade your programs (just go into synaptic and select firefox3 or follow instructions online for OO3), but that people won't get these programs straight away on the default install. They might not know how to or cannot be bothered to get the updates, so making ubuntu look worse.

---

### Post by hyper_ch on 2008-10-23
the software in the repos is tested and it works together. During a release you will only get security updates and bug fixes - however no version improvments.

Is this bad? Depends... there are rolling releases distros where everything gets updated on the fly. Ubuntu however with a 6 month release cyclus does not follow that.

So, what about those LTS releases? Well, they are aimed at businesses that need productive machines and not necessarly the latestest bleeding edge software. For the normal user, you get aver 6 months major versioning updates (if those happened), so why care too much?

If you don't like it, you can still try to install those software outside your repos but you could irrecoverably damage your system by doing that.

---

### Post by Archmage on 2008-10-23
To explained a little more. In one release the programs are tested as they are to work well together. E.g. it might be possible that Gimp 2.6 and Firefox 3.03 don't run together. So you might have no problem if you use the version in Hardy or if you add Gimp 2.6 manual or Firefox 3.03 manual but together they don't work.

That is the reason why they release every 6 months tested releases where you can use everything without problems.

---

### Post by shatteredmindofbob on 2008-10-23
> **hyper_ch said:**
> the software in the repos is tested and it works together. During a release you will only get security updates and bug fixes - however no version improvments.

Is this bad? Depends... there are rolling releases distros where everything gets updated on the fly. Ubuntu however with a 6 month release cyclus does not follow that.

So, what about those LTS releases? Well, they are aimed at businesses that need productive machines and not necessarly the latestest bleeding edge software. For the normal user, you get aver 6 months major versioning updates (if those happened), so why care too much?

If you don't like it, you can still try to install those software outside your repos but you could irrecoverably damage your system by doing that.

See, it's the irrecoverable damage part that scares me...

---

### Post by Zill on 2008-10-23
> **shatteredmindofbob said:**
> See, it's the irrecoverable damage part that scares me...
It's all about avoiding "dependency hell" - a program expects to find a certain version of a library, for instance.

Each version of Ubuntu has all the dependencies fixed.  If you choose to install a different version of an application then all the corresponding dependencies will also have to be changed - possibly causing mahem with other programs that can only be fixed with a re-install.  :(

---

### Post by markbuntu on 2008-10-23
It often does not pay to be in a hurry to upgrade without some urgent necessity, especially of you are getting things from outside the official repositories. 

Unless you are one of those people who enjoys delving deep into problem solving, you might want to wait a little while and see what sort of problems pop up in these forums and how they get fixed. Once you are sure your fears have been resolved and you are capable of handling any problems, upgrade.

---

### Post by Orographic on 2008-10-24
Nice thread. This is something that takes a bit of a mindset shift from XP. Is it okay that I downloaded Ufraw from Add/Remove? As long as I stick to Add/Remove (All Open Source for Ubuntu and Supported) am I generally okay?

I am using Hardy Heron.

---

### Post by zvacet on 2008-10-24
@ **Orographic**

>  Is it okay that I downloaded Ufraw from Add/Remove?

It is O.K to install any package from synaptic,because thay are tested by Ubuntu.If you use third party repos be sure thay are reliable (like Medibuntu).In short you are just fine.

---

### Post by Orographic on 2008-10-24
Thanks for that. I'm thoroughly impressed with Ubuntu and the community behind it. Doing a fair bit of photography work for my website means that Gimp 2.6.1 would be better for me, having come from Photoshop 7 but I guess I will wait until that is included in the add/remove or in Intrepid or the next one after that? I do an image of my OS before any major changes which makes recovery far easier but don't want to take up to much time fiddling with new program installs away from Add/Remove.

I'm still learning how it all works.

---

