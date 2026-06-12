---
title: "Compiz Config Settings Manager: is it safe now?"
date: 2011-10-23
forum: New to Ubuntu
---

### Post by vasa1 on 2011-10-23
I've been holding back on installing it and then "fiddling" for cosmetic effects. But it seems like a lot of useful stuff can be made available if CCSM is installed:
> Install Compiz Config Settings Manager, click the Unity plugin. Set the Reveal Mode to None and you will be able to open the launcher only when clicking the Super key. You can also set the Reveal Mode to Bottom Left, to avoid opening it accidentally. ... You can also increase the Edge Reveal Timeout.

You can also set the option Hide Launcher to Never, so it will be displayed all the time, on the side of the window.
...
[http://ubuntuforums.org/showpost.php?p=11366578&postcount=21](http://ubuntuforums.org/showpost.php?p=11366578&postcount=21)

I've read some comments about 11.04 recommending that [CCSM be avoided]("http://www.dedoimedo.com/computers/ubuntu-natty-narwhal.html").
> However, do not, under any circumstances, try to play with Compiz. It is enabled in the background, but the configuration menu, either the simple or the advanced one, are not installed.

---

### Post by Ctrl-Alt-F1 on 2011-10-23
Hmm...I've been using it in both Ubuntu 11.04 and 11.10.  However, I don't alter the desktop effects at all.  I just installed it so that I could alter some things about Unity (such as the icon size, it's too big).  It seems to have been working fine for me, but like I said I really only use it to do Unity stuff, not stuff that might conflict with Unity.

---

### Post by coffeecat on 2011-10-23
> **vasa1 said:**
> I've read some comments about 11.04 recommending that [CCSM be avoided]("http://www.dedoimedo.com/computers/ubuntu-natty-narwhal.html").

Like many personal blogs on the web, that site contains misconceptions and errors. There are two glaring ones after the bit you quote.

The "problem" with CCSM is that Unity is a compiz plugin and some other plugins are not compatible with it. This has always been so with compiz - certain plugins being mutually incompatible. Many of the instances of Unity breaking with the use of CCSM is when the user has disabled a compiz feature needed for Unity when enabling another compiz plugin. Disabling desktop wall when trying to enable the cube is one, although there is a workaround for that.

Confine yourself to the settings within Unity itself, or be cautious and stop if CCSM wants to disable something, and you should be OK.

---

### Post by mc4man on 2011-10-23
If you 'don't trust yourself or just want to limit your initial view  - then after installing compizconf-settings-manager do this

Alt+F2 (sometimes you need to do twice to get a "run a command box", current bug

type this in the run box, it will take you directly to the unity settings
```
about:config
```

---

### Post by 3rdalbum on 2011-10-23
> **mc4man said:**
> If you 'don't trust yourself or just want to limit your initial view  - then after installing compizconf-settings-manager do this

Alt+F2 (sometimes you need to do twice to get a "run a command box", current bug

type this in the run box, it will take you directly to the unity settings
```
about:config
```

You're a legend, how did you find that cool feature?

---

### Post by vasa1 on 2011-10-23
Thank you, everyone!

the **about:config** idea maybe a nice way to ensure that a newbie dowsn't get into trouble!

I've installed CCSM after backing up my data :D and the about:config takes me straight to where I want to go!

---

### Post by cozumel on 2011-10-23
Thanks mc4man for the heads-up on "about:config".  It'll help protect my installation from myself!

Nice thread.

---

### Post by mc4man on 2011-10-23
> **3rdalbum said:**
> how did you find that cool feature?
It was put in during natty dev, maybe because there was & thru 11.10, no simple config tool for unity provided.

It's actually running a ccsm command (ccsm -p unityshell
The nice thing about the alt+F2 is it then shows in the history & just can be clicked on

I had a bug during natty on the lack of a tool, that flew like a lead balloon. it still baffles me on the reluctance to do so 
some insight, though dated
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/748739](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/748739)

---

### Post by vasa1 on 2011-10-23
> **mc4man said:**
> ...
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/748739](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/748739)
From the bug: " zero-config experience" :(

---

### Post by beew on 2011-10-23
It seems safe in 11.10. I have been playing with the Compiz settings a bit, it never crashed on me like it did in 11.04. Even enabled the cube in the most painless way,--that used to be somewhat risky in Natty.

---

### Post by vasa1 on 2011-10-23
I'm thinking of giving "Unity grab handles" a try. Any feedback on that one?

---

### Post by coffeecat on 2011-10-24
> **vasa1 said:**
> I'm thinking of giving "Unity grab handles" a try. Any feedback on that one?

Works perfectly.

---

### Post by vasa1 on 2011-11-19
FYI
[http://askubuntu.com/questions/80589/what-are-some-of-the-issues-with-ccsm-and-why-should-i-not-use-it](http://askubuntu.com/questions/80589/what-are-some-of-the-issues-with-ccsm-and-why-should-i-not-use-it)

---

### Post by vasa1 on 2011-11-24
Interesting quote:> I understand that people want the freedom to tweak their desktops, but as soon as you use CCSM, you have basically opted out of Unity's future. The bugs you report will not matter since you're not running the defaults, and any input you may have will be skewed by the customized user experience you've devised. Making a new desktop is challenging, and we can't do it without you. That means filing bugs, proposing new use cases with mock ups, and of course: running the defaults throughout your day.
[http://askubuntu.com/questions/29553/how-can-i-configure-unity](http://askubuntu.com/questions/29553/how-can-i-configure-unity) (near the top of the page)

---

### Post by coffeecat on 2011-11-24
> **vasa1 said:**
> Interesting quote:

It's fair comment. The same applies to alpha and beta testing in the development phase of each Ubuntu release. If systems are personalised and configured differently from the default, they will behave differently and any bug reports from such systems will be of little value to the developers.

---

