---
title: "Ubuntu Distro for a Call Centre"
date: 2014-03-21
forum: New to Ubuntu
---

### Post by kwilliamson85 on 2014-03-21
Hi All

Really new to Ubuntu by time to move away from windows :)

I want to use ubuntu for my call centre agents but i wanted to lock down the whole screen and maybe produce a boot distro based on how i want it to look and just wanted to know how i may be able to do that.

I wanted to have an agent log in and only able to see a bowser button, soft phone button and then an option to login as a superuser which then would show everything as normal.

Any help would be grateful

Kris

---

### Post by TheFu on 2014-03-21
Welcome to the forums.
I wouldn't use Ubuntu for this at all. There are simply too many pre-loaded applications for a specialized need as yours.
I'd start with TinyCore, then add only the apps I want on the systems. Should be less than 100M total, not the 500M+ that a _minimal_ Ubuntu install would require.

---

### Post by kwilliamson85 on 2014-03-21
thanks

---

### Post by tgalati4 on 2014-03-21
Don't forget by locking down the screen, you are treating your employees like machines, and they will resent that and it will be reflected in their performance with their customers.  Now how the customers feel on the other end of the line is another discussion.

Do the operators share machines over shifts?  Does each operator have their own dedicated terminal?  If they have their own machines, then let them customize the machines the way they want.  If they share machines over shifts, include a launch button on the desktop that allows the machine to be reset to a default session.

In fact, I would go one step forward:  tinycore is a good suggestion, but I would put 4 or 5 different distros (one on each machine, such as Linux Mint MATE, Ubuntu, Centos, XFCE, KDE, etc) and rotate your operators through them.  Let them make the choice as to which environment they prefer.  That may narrow it down to 2 or 3.  If you give them the illusion of choice, they will perform better.  Don't forget to change the light levels during the trial period.  That way you can take advantage of the [Hawthorne Effect]("http://en.wikipedia.org/wiki/Hawthorne_Effect").

---

### Post by lykwydchykyn on 2014-03-23
This is an article I published a few years back, but it still applies:

[http://www.alandmoore.com/blog/2011/11/05/creating-a-kiosk-with-linux-and-x11-2011-edition/](http://www.alandmoore.com/blog/2011/11/05/creating-a-kiosk-with-linux-and-x11-2011-edition/)

Essentially it goes through how to create a custom desktop session on Linux and X11, so that you can have a desktop boot into whatever you'd like.  The application I specified was a browser kiosk, but you can replace that with any other application.

This approach combines well with [LTSP](http://www.ltsp.org/) if you want to utilize thin clients to save money.  I have a setup like this at a public library for INNOPAC terminals.

---

### Post by lykwydchykyn on 2014-03-23
> **TheFu said:**
> Welcome to the forums.
I wouldn't use Ubuntu for this at all. There are simply too many pre-loaded applications for a specialized need as yours.
I'd start with TinyCore, then add only the apps I want on the systems. Should be less than 100M total, not the 500M+ that a _minimal_ Ubuntu install would require.

I would agree that building a system from the ground-up would be a better approach than using something like a default Ubuntu install, but this doesn't preclude using Ubuntu or any other general purpose distro (Debian, Suse, Centos, etc).  Most distros have an option to start with a minimal install and add packages manually.  TinyCore is nice when disk space is tight,  but it would probably be less trouble in the long run to use something better supported.

I would check what your softphone software requires, and go from there.

---

