---
title: "synaptic error report"
date: 2011-08-24
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by ventrical on 2011-08-24
I should know how to fix this one by now .. but it escapes me. I got this from second most previous update for Oneiric.

Suggestion appreciated.

---

### Post by ventrical on 2011-08-24
whoops .. sorry..

---

### Post by mc4man on 2011-08-24
A couple of ways to resolve, one would be to remove the bad plugin, then upgrade the good plugin
After that just refresh your sources in synaptic and re-install the bad plugin

---

### Post by ventrical on 2011-08-24
Thanks. Synaptic works great. They should always bundle it with Alpha/Beta distros just in case USC does not work.

---

### Post by coffeecat on 2011-08-24
I found an even easier way, which doesn't seem to make much sense. I got the same error from Synaptic, closed Synaptic, and:

```
sudo apt-get dist-upgrade
```

... which output:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  gstreamer0.10-plugins-good
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/1,925 kB of archives.
After this operation, 41.0 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 211959 files and directories currently installed.)
Preparing to replace gstreamer0.10-plugins-good 0.10.30-1ubuntu5 (using .../gstreamer0.10-plugins-good_0.10.30-1ubuntu6_amd64.deb) ...
Unpacking replacement gstreamer0.10-plugins-good ...
Setting up gstreamer0.10-plugins-good (0.10.30-1ubuntu6) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```

Since Synaptic uses apt-get dist-upgrade when you click on "Apply" (or so I understand) that certainly shouldn't work, but it did. And now Synaptic is happy. And so am I. :)

---

### Post by ventrical on 2011-08-24
But that gives me the willies  because there is that word "upgrade' again and so I get apprehensive that something might get busted. I've done two upgrades on other distros  and one install with Oneiric. That was partial upgrade and it seems to work just swell. As it says in the sticky .. try to stay away from partial upgrades .. but I see  that only individual packages were upgraded according to your script.

Thanks anyways for the alternate method. Always good to have a back-up method in case one fails.

---

### Post by coffeecat on 2011-08-24
> **ventrical said:**
> But that gives me the willies  because there is that word "upgrade' again and so I get apprehensive that something might get busted.

The dist-upgrade option for apt-get is not to do with upgrading from one version of Ubuntu to another, although that's a common misunderstanding. It would be a bit difficult to upgrade to Plastered Penguin (or whatever sabdfl is going to call it) from Oneiric just now anyway! :)

From man apt-get:

```
dist-upgrade
           dist-upgrade in addition to performing the function of upgrade,
           also intelligently handles changing dependencies with new versions
           of packages; apt-get has a "smart" conflict resolution system, and
           it will attempt to upgrade the most important packages at the
           expense of less important ones if necessary. So, dist-upgrade
           command may remove some packages. The /etc/apt/sources.list file
           contains a list of locations from which to retrieve desired package
           files. See also apt_preferences(5) for a mechanism for overriding
           the general settings for individual packages.

```

Don't mistake apt-get dist-upgrade with do-release-upgrade.

---

### Post by ventrical on 2011-08-24
Thanks for clearing that up. Yes.. it all makes sense while running that code from the terminal. Makes me wonder then why synaptic is there at all.

  I think 12.04 will be 'Tenacious Tortise' or 'Happy Hare'  :)

---

### Post by mc4man on 2011-08-24
There seems to be some instances where synaptic isn't working like it used to. 
A couple of them - 
**sometimes** if for example  package a depends on b which depends on c.
If marking a, synaptic can refuse, saying b & c can't be installed. If then marking b 1st, same thing, says c can't be installed. If marking c-b-a then it will install.

Other times if removing a package then synaptic will not want to re-install
Ex. remove gnome-shell, then try to install gnome-tweak-tool. synaptic usually refuses to install gnome-shell. In this case reloading the sources will allow - I just never remember having to do these things.
There are a couple of other occasional oddities..

---

### Post by seeker5528 on 2011-08-24
> **coffeecat said:**
> I found an even easier way, which doesn't seem to make much sense. I got the same error from Synaptic, closed Synaptic, and:

```
sudo apt-get dist-upgrade
```

If that worked, it seems likely that' in Synaptic' hitting the apply button a second time as soon as you get back to the main interface after the failure to overwrite, probably would have worked.

> Since Synaptic uses apt-get dist-upgrade when you click on "Apply" (or so I understand) that certainly shouldn't work, but it did. And now Synaptic is happy. And so am I. :)

It might potentially use 'apt-get upgrade'/'apt-get dist-upgrade' when you hit the 'Mark All Upgrades' button, for package selection and dependency resolution. Depending on how you have 'settings --> preferences --> general --> system upgrade' set, 'Default Upgrade' for the equivalent to 'apt-get upgrade', 'Smart Upgrade' for the equivalent to 'apt-get dist-upgrade'.

Once the packages are selected, I'm pretty sure Synaptic just feeds a list to apt-get, no matter what method was used to select them.

Later, Seeker

---

### Post by ranch hand on 2011-08-24
The term "update" in apt-get or aptitude refers to updating the list of packages available in the repo on your box.

The term "upgrade" in apt-get and aptitude refers to upgrading the packages installed on you box so that they are current.

"apt-get upgrade" will not upgrade packages that need to have other packages removed or added.

"apt-get dist-upgrade" will upgrade those packages and do the installation or removal as needed.  It is also the preferred way to upgrade from one version of Debian to the next.  It is also the way I always upgraded Ubuntu.

UM stands for Update Mangler.  Be warned.

---

### Post by ventrical on 2011-08-24
I just had a major problem with synaptic. Amazing. Perhaps I will keep it here and not start a new thread. 

  I decided to do a fresh install on a Dell OptiGTX, 30GB hdd. All went well and then I used synpatic to update after the fresh install. All files were downloaded and then it got half way through the install process and just froze up !!

  I had to hard re-boot and went to terminal, logged in as root and entered apt-get distro-upgrade

It gave me an error report and told me to enter : sudo-dpkg --configure -a    and I did this and it is now Setting Up some files. I am not sure if it is recovering from where it left off or if it is worth trying to recover this install . Sorry I can send any screen shots.

any tips .. helpful.

update..***

Ok... sudo-dpkg --configure -a

restored the system and allowed me back to the desktop to finish installing updates.

---

### Post by mc4man on 2011-08-24
> **ranch hand said:**
> .

UM stands for Update Mangler.  
U=M is only a 'mangler' in the hands of the uninformed or idiots, I gather you're speaking from personal experience?

---

### Post by ventrical on 2011-08-24
> **mc4man said:**
> There seems to be some instances where synaptic isn't working like it used to. 
A couple of them - 
**sometimes** if for example  package a depends on b which depends on c.
If marking a, synaptic can refuse, saying b & c can't be installed. If then marking b 1st, same thing, says c can't be installed. If marking c-b-a then it will install.

Other times if removing a package then synaptic will not want to re-install
Ex. remove gnome-shell, then try to install gnome-tweak-tool. synaptic usually refuses to install gnome-shell. In this case reloading the sources will allow - I just never remember having to do these things.
There are a couple of other occasional oddities..


Thanks for your help and input. I guess we can expect anomolies , especially during an Alpha testing period.

Thanks again.

---

### Post by ranch hand on 2011-08-25
> **mc4man said:**
> U=M is only a 'mangler' in the hands of the uninformed or idiots, I gather you're speaking from personal experience?
Sure am.  I can also see, by reading on these UF forums that the thing is a pig.

On the other hand I have just about come to the conclusion that only an idiot would use Ubuntu so I guess that I qualify.

---

### Post by cariboo on 2011-08-25
Please keep it civil, the natives are getting restless. :)

---

