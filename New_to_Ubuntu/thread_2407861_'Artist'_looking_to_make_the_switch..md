---
title: "'Artist' looking to make the switch."
date: 2018-12-10
forum: New to Ubuntu
---

### Post by penciltester on 2018-12-10
Hello everyone. I'm new to the idea of using any type of Linux but I've heard good things about Ubuntu. And with programs like Maya, Krita and the soon to be released AnimationPaper Linux is looking more viable for artists. I have a few questions that I have searched for answers to but being new to all that is Linux I could use some clarification if possible.

I was thinking of putting Ubuntu Studio on a Surface Pro 3. I have read some folks saying everything works 'out of the box' now without tweaking or "unofficial kernals". Is this correct?

Does Ubuntu also work with Wacom devices "out of the box"? Such as the intuos line and also their tablet computers, the companion and studio models?

Anyone have trouble with Maya on Linux?

Thanks.

---

### Post by Frogs Hair on 2018-12-10
It is possible to install Maya on Ubuntu, but it requires adding 3rd party repositories to get all the program dependencies. Maya is natively supported on the following. [https://knowledge.autodesk.com/support/maya/troubleshooting/caas/sfdcarticles/sfdcarticles/System-requirements-for-Autodesk-Maya-2018.html](https://knowledge.autodesk.com/support/maya/troubleshooting/caas/sfdcarticles/sfdcarticles/System-requirements-for-Autodesk-Maya-2018.html)

  

[LIST]
[*]Red Hat® Enterprise Linux® 6.5  & 7.2 WS operating system
[*]CentOS 6.5  & 7.2 Linux operating system
[/LIST]

---

### Post by bradleypariah on 2018-12-10
If you create a Live USB with Ubuntu, and you know how to boot from it, choose the option for "Try Ubuntu without installing."

It will run a tad slower than it would if Ubuntu were installed to your internal drive, but it'll give you a chance to see what works and what doesn't before you commit.

You'll most likely want to open the Ubuntu Software Center and download an app called "OnBoard," which will be your touch keyboard for 3rd-party apps.  I use touch screens at work and at home.  

Keep in mind that Ubuntu Studio comes with the desktop environment called "XFCE," which is not really a touch-friendly user interface (in my opinion).  Gnome is touch friendly, so is Plasma, and a couple others might be as well.
Gnome (which is what you'd get if you chose regular "Ubuntu" instead of "Ubuntu Studio") is pretty rigid, but it works.  Plasma (which is what you'd get with "Kubuntu") gives you so many customization options, it will let you hang yourself, which is what I like.

Check out this: [https://www.youtube.com/watch?v=SlmgwHAXgB4](https://www.youtube.com/watch?v=SlmgwHAXgB4) 

On my studio machine, I installed Ubuntu Studio, then installed Plasma on top of it.  I suggest you install the *buntu that comes with what you already like.  Ubuntu Studio comes with a specific kernel for real-time mutli-channel audio recording.  If you're not going to be doing that, just install Maya on top of a normal *buntu flavor.  Ubuntu Studio will come with Gigs of stuff you'll never use, and Maya won't be preinstalled anyway.

Lastly, yes, Ubuntu is known to work well with most Wacom tablets.  Though, again, just boot into a live environment and plug your tablet in.  See if it works or not.  If it doesn't, post your model number into another forum post and ask for help.  Someone might be able to give you easy advice to get it working.

---

### Post by penciltester on 2018-12-11
Thanks guys for the responses. I looked into setting up Maya properly, doesn't look too difficult. Also I was unaware of studio being geared toward audio production.

---

