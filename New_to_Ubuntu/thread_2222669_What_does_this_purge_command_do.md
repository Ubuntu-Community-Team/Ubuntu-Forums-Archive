---
title: "What does this purge command do ?"
date: 2014-05-07
forum: New to Ubuntu
---

### Post by hebdave on 2014-05-07
[FONT=arial]Hi I am aiming to remove the configuration files from any past programs I uninstalled with software centre only. I looked around the internet and got many diffferent answers. I thought the command below may be good as it removes dependencies also. Although will this also remove Global dependencies removing 'all packages on my system' or something bizarre so I have nothing left ?
[/FONT]
[FONT=arial]So what is the sudo apt-get -f purge && sudo apt-get autoremove . Just to be clear I have learnt about sudo apt-get autoremove and sudo apt-get purge for individual packages but don't no much more than this.[/FONT]

Thanks it appears I am a tiny bit confused :D

---

### Post by tgalati4 on 2014-05-07
```
man apt-get
```

The -f switch is used to fix broken packages and will give recommendations as to what to do.  If it is a simple fix (install a few files) then it will go ahead and do it.  If it requires major work (remove and install several packages) then it will ask "Yes" or "No".  Otherwise if it can't fix your package system it will give you some suggestions.

The purge option will delete previous configuration files for only those packages named--in this case by the -f (fix broken) switch. The && connector says "do the next action only if the previous action was successful--with no errors".  The autoremove option simply removes obsolete packages--stuff left over when installing a bunch of packages.  This is typically a safe command and frees up some space.

To answer your original question, I don't know if it is possible to delete only software installed from the Software Center.  You can install software through the Center, using *synaptic*, *apt-get*, *aptitude*, *gdebi*, *dpkg*, or simply copying the files to the correct location.  I don't think the Debian package management system keeps track of how you installed a package, only that it is either installed or not installed; correctly installed/configured or broken.

Dependencies don't get removed.  Dependencies always exist for any given package.  You can ignore them, force-ignore them, but they still exist.  As a general rule, when you ignore dependencies to install a package, that package will probably not work correctly.  If it does, you got lucky.  If it doesn't then that is expected behavior.

What exactly are you trying to do?

---

### Post by Lars Noodén on 2014-05-07
The purge command to [apt-get](http://manpages.ubuntu.com/manpages/trusty/en/man8/apt-get.8.html) won't do anything by itself.  You have to give it a package name, or several, to purge.  Purge is like 'remove' but also configuration files are removed.  Check the manual page for the official details and for what the -f does.

---

### Post by ibjsb4 on 2014-05-07
A quick reference list

[https://help.ubuntu.com/community/AptGet/Howto#Removal_commands](https://help.ubuntu.com/community/AptGet/Howto#Removal_commands)

---

### Post by hebdave on 2014-05-08
Hi thanks I looked up the links. I had seen the apt-get from the Ubuntu documentation. The man pages manual was quite complex but just about understandable to me being a beginner. Basic commands on here being slightly easier to start with I think for me. Any how I meant Sudo apt-get purge <packet name> but when I said 'purge only' it looked like I had not known that from before when I was on the forum prior to this thread.

To explain better I meant I was looking to globally do a clean up to remove all traces of application I'd uninstalled and hide the dependencies also if no other program was using these. So this might include cleaning - files , configuration files , Ubuntu home files and dependencies no longer needed by them. This is providing nothing else is using them also which commands would hopefully reflect.

I am still fairly clueless with Ubuntu so please don't let me fool you. I am just parrot repeating things I have read about briefly elsewhere.

I really appreciate you help and it never goes unnoticed. I hope many convert to Ubuntu entirely because of the help and encouragement they receive here too. ;)

---

### Post by ibjsb4 on 2014-05-08
Take a look at 'autoremove' in my above link.

---

### Post by tgalati4 on 2014-05-08
Normally, you don't need to worry about it.  The Debian package system takes care of what's needed and what can be dumped.  In fact, you will get a notice from time-to-time about packages that can be safely removed using *autoremove* option.  You don't need to overthink it.  And it's generally not advised to manually delete system files unless you know what you are doing.  Otherwise you may end up breaking your system and end up back here on the forums trying to fix stuff.

Enjoy your journey.

---

### Post by hebdave on 2014-05-10
Okay thanks.

---

