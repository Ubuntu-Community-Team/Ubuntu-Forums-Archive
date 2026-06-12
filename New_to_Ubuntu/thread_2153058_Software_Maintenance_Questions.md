---
title: "Software Maintenance Questions"
date: 2013-06-10
forum: New to Ubuntu
---

### Post by ClarkH85 on 2013-06-10
I have two questions about how to keep my machine up to date, and lean. 

1: do you just install all updates suggested by the Update Manager? There are tons. Like 50-100 updates every time I start Ubuntu. It's kind of a pain to read them all. Is it safe to assume that none of the updates will 'break' anything? Sometimes updates can be problematic in Windows. Is it the same on Ubuntu? I'm using 12.04, and plan to stay with it.

2: I'm almost done installing and updating everything I had planned before I starting using Ubuntu. But, during the process, I've also tried some installs that didn't work and/or were unnecessary. I've installed using both the Ubuntu Software Center, and the Terminal (including PPAs). Is there a way I can see: installed software, date last used, dependencies, and then easily uninstall?

Thanks!

---

### Post by Cheesehead on 2013-06-10
> **ClarkH85 said:**
> 
do you just install all updates suggested by the Update Manager?
There are tons. Like 50-100 updates every time I start Ubuntu. It's kind of a pain to read them all.
Is it safe to assume that none of the updates will 'break' anything? 
Sometimes updates can be problematic in Windows. Is it the same on Ubuntu?

Yes. If you don't want to keep it updated, then you probably shouldn't install it.
That's an unusually high number every day. Mine averages four or five.
Yes, if it's from the Ubuntu Repositories. No, if it's from a PPA or non-Ubuntu repository.
No, if it's from the Ubuntu repositories. Yes, if it's from a PPA or non-Ubuntu repository.

Updates include security fixes and bug fixes. Updates to packages from the Ubuntu Repositories are tested before release. Use them.

If the same packages recur in Update Manager day after day, then the updates are not actually being installed. You should fix that. If you need help, let us know.


> **ClarkH85 said:**
> Is there a way I can see: installed software, date last used, dependencies, and then easily uninstall?

Yes, no, yes, yes.

The best way to see what you installed is to use the Synaptic application, to look in the var/cache/apt logs, or to see the prettier versions of the same data in the Synaptic history.

Installing packages (and dependencies) and uninstalling packages (and no-longer-needed dependencies) are basic functions of the package manager, and it does those tasks quite well. The Synaptic application and apt-cache command will happily show you how the magic works. You should not need to do any dependency checking by hand, simply read the system's output - it will tell you.

"Installed Software" covers a lot of territory. Your Sound Menu, for example, is both Installed Software and a dependency of the desktop environment. Your package manager can tell you about the thousands of packages you have installed, but since few can agree on what a top-level list of software should include, there is no tool to give you that list.

There are several ways to de-bloat your system...if it's actually bloated. A fresh install of Ubuntu is not very bloated.

One easy way to de-bloat your system is to keep an eye on those daily updates. If it's for something you don't recognize or don't use, simulate removing it to see what happens. If it turns out to remove nothing you use anyway, then remove it for real. Simulate first! The system assumes you are an adult who understand the consequences of uninstalling your kernel or desktop environment, and will faithfully break itself because you said to.

---

### Post by mastablasta on 2013-06-10
actually it's not safe to assume they won't break anything. they managed to break my sound (it stopped working), and last time also mouse stopped working via PS2. this is on LTS.

however one can turn off the programme updates and then use only security updates. thouse are really safe and it will be less of them and usually they are also   bit smaller (appart from kernel updates). LInux MInt has a scale to help you select which updates you wish to have. for example the safe ones are only security patches i believe.

---

### Post by 3rdalbum on 2013-06-10
Ubuntu updates are among the safest updates in Linux. Bug fixes are tested by upstream developers, then by Ubuntu developers, then pushed to the "proposed" repository for wider testing by volunteers, then pushed to the regular updates repository.

I haven't had an update affect me adversely, and I used to test "proposed". Several annoying and nearly showstopping bugs got fixed, though, so installing updates was definitely worthwhile.

Just install them all.

---

### Post by monkeybrain2012 on 2013-06-10
Instead of using the update manager, use synaptic to manage your software. I have disabled the update manager and only used synaptic (choose "never" in the ubpdate manager's option)  It gives you a lot more control in terms of what you want to update, which packages you want to pin (no updates) etc. It also shows you a lot more infoemation and is a lot faster. It should be installed by default instead of the bloated Ubuntu Software Centre.

```
sudo apt-get install synaptic

```
If your update wants to remove something, better find out what it does. If you use ppas then you should install ppa-purge, just in case..

Finally, if you have 50 updates everytime you use Ubuntu it probably means you don't update or log into Ubuntu every often, I hardly have any most of the time except for things in a couple of ppas.
Also, I don't see a problems with a lot of updates, it does it in the background and doesn't nag you to reboot like Windows, just more freebies. :)

---

### Post by mastablasta on 2013-06-10
> **monkeybrain2012 said:**
> Instead of using the update manager, use synaptic to manage your software. I have disabled the update manager and only used synaptic (choose "never" in the ubpdate manager's option) It gives you a lot more control in terms of what you want to update, which packages you want to pin (no updates) etc. It also shows you a lot more infoemation and is a lot faster. It should be installed by default instead of the bloated Ubuntu Software Centre.
[QUOTE]
once i pinned a kernel in 10.10. i've patched it so that ALSA worked correctly. next update overwrote the kernel and same issue occured. though i do not remember anymore if i disabled update manager or not.

[QUOTE]
Also, I don't see a problems with a lot of updates, it does it in the background and doesn't nag you to reboot like Windows, just more freebies. 

thats' true. you can also do updates with no reboot.

i install proposed updates (despite they broke the mouse driver once). so far they worked wlel for the most part. though i must admit that after mouse fiasco i though about patching for security only...

---

### Post by monkeybrain2012 on 2013-06-10
> **mastablasta said:**
> 
once i pinned a kernel in 10.10. i've patched it so that ALSA worked correctly. next update overwrote the kernel and same issue occured. though i do not remember anymore if i disabled update manager or not.

..

I think that if you do sudo apt-get upgrade it over-rules the pin in synaptic (but I haven't gone through, just noticed the pinned program appeans in the upgrade list, may be it is a bug), there is a command for pinning things with the terminal, but I forget what it is.

---

### Post by sum1nil on 2013-06-10
They done busted up my little Creative sound card (CA0106) since 12.04. 
Play the login screen drums and then it runs off after login.
I do still like Ubuntu the best though.
Sorry to butt in...2 bits.

---

