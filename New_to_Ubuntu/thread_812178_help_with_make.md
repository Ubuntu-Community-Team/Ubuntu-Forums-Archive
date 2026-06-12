---
title: "help with make"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by DThorne on 2008-05-29
I'm tring to follow [these directions]("http://wireless.kernel.org/en/users/Drivers/b43#fw-b43-new")to get my broadcom card working

but when I try to run make to compile fwcutter I get a screen of meaningless text and no binary

I've tried searching for some of it and it seems to be C+ code errors?

any suggestions?

---

### Post by Oldsoldier2003 on 2008-05-29
> **DThorne said:**
> I'm tring to follow [these directions]("http://wireless.kernel.org/en/users/Drivers/b43#fw-b43-new")to get my broadcom card working

but when I try to run make to compile fwcutter I get a screen of meaningless text and no binary

I've tried searching for some of it and it seems to be C+ code errors?

any suggestions?

first off do you have build-essential installed? its not part of the default Ubuntu load so you need that.

```
sudo apt-get install build-essential
```
Show us what errors you get and what step they occur at and we would be more able to help you.

---

### Post by RequinB4 on 2008-05-29
Solution: Don't even mess with fwcutter for broadcom43, not only are those instructions outdated (its in the repos), you'll get 3 times better performance with:

[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

---

### Post by SaDiKe on 2008-05-29
Alternatively, you could also install package b43-fwcutter from Synaptic, and all your dependencies will be automatically added for installation.

---

### Post by DThorne on 2008-05-29
I get couldn't find package build-essential

---

### Post by django0909 on 2008-05-29
You should make sure all your repositories are accessible...

sudo /etc/apt/sources.list

Then add

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) <yourversionofubuntu> universe

and try again.

---

### Post by DThorne on 2008-05-29
> **RequinB4 said:**
> Solution: Don't even mess with fwcutter for broadcom43, not only are those instructions outdated (its in the repos), you'll get 3 times better performance with:

[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)


yikes  

I was hoping for something simpler, I'm very new to linux!

thank god for true image!

---

### Post by RequinB4 on 2008-05-29
> **DThorne said:**
> yikes  

I was hoping for something simpler, I'm very new to linux!

thank god for true image!

It looks a lot worse than it is, it's the most well made tutorial on the subject I know of so all you have to do is copy and paste each and identify which file to download based on your video card.  I can pretty much guarentee if you do that right you will never have a problem.

But, if you want the "easier" way with inferior preformance, follow SaDiKe's suggestion.

---

### Post by DThorne on 2008-05-29
> **RequinB4 said:**
> It looks a lot worse than it is, it's the most well made tutorial on the subject I know of so all you have to do is copy and paste each and identify which file to download based on your video card.  I can pretty much guarentee if you do that right you will never have a problem.

But, if you want the "easier" way with inferior preformance, follow SaDiKe's suggestion.

lspci tells me there is a bcm94311mcg in my system

and my console keeps printing error:You must go to linuxwireless.org...and dnload firmware

it's very disorienting..

my vidcard? is from intel

---

### Post by DThorne on 2008-05-29
> **django0909 said:**
> sudo /etc/apt/sources.list

I get command not found

and sudo apt-get install ndiswrapper-utils-1.9 gets me couldn't find package

---

### Post by DBell5 on 2008-05-29
> **Oldsoldier2003 said:**
> first off do you have build-essential installed? its not part of the default Ubuntu load so you need that.

```
sudo apt-get install build-essential
```


Well, that answered my question, before I could post it!
I did see the Documentation page stating:
> Compiling C and C++ programs requires some packages that are not installed by default.

    *Install the build-essential package (see Add Applications)."


But I couldn't find the package from the Desktop "Add Applications".
Worked fine through Terminal, as above, but where should I have been looking for it, to install via the GUI?

Dave

---

### Post by DThorne on 2008-05-29
I ran administration->update manager and it found a few things, rebooting caused the 'proprietary drivers' popup that I get when I boot to the live cd and prompted me to ok getting the missing fw.

still no connectivity to my desktop though... bloody linux, now I get to figure out peer-to-peer networking (To an XP box briging a wireless nic to a wired nic)

...sigh

---

