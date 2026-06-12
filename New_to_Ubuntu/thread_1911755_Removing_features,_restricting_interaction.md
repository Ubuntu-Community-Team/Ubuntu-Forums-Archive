---
title: "Removing features, restricting interaction"
date: 2012-01-19
forum: New to Ubuntu
---

### Post by Peet42 on 2012-01-19
Hi.  Long time Linux user, first-time Ubuntu user.

I'm setting up Ubuntu on a machine for my 85 year old Mother.  I've installed the latest 11.10 and got all the available updates.  But...

I would ideally like it to have just two "buttons" - one to launch Firefox (it's in "Startup", but the option to launch it again if she accidentally closes it would be handy) and one to shut the computer down.  No "Hibernate" option, no panels that can be opened etc., no dialogs informing her that "Updates may be available", just basically "Start" and "Stop".

For the past eight years or so she was very happy running Xandros Linux, but the distro was so old that when she upgraded to Broadband from dial-up last month it didn't support any form of wi-fi connection, hence my upgrading to Ubuntu.

The problem is that every option I can find seems to add more features or buttons - I want to suppress them!  How can I go about removing "default" features easily?  Is there a "stripped-down" X server I could install, for instance, that would allow me to specify a single application (Firefox) to be run, shutting the computer down if you exit it?

It's taken years to get her to be able to operate Google mail properly, not helped by Google changing the front-end and then insisting on throwing out pop-ups asking what she thought of it.  I don't want to have to teach her how to navigate the OS, I just want to build a Gmail "appliance".

Does anyone have any suggestions?

---

### Post by ubudog on 2012-01-19
Hi there, you may want to try Lubuntu.  It has a very customizable menu and settings, and you can delete the panel altogether if you like.  It's quite simple, and you can add stuff to the desktop (Like, Firefox for example).  

[http://lubuntu.net/](http://lubuntu.net/)

Hope that helps, 
ubudog

---

### Post by Double.J on 2012-01-19
It may be worth considering [chromeOS]("http://getchrome.eu/") - I've only tried it on a VM, so can't attest to hardware support.

But it's very basic - everything is run through the chrome browser.. and I mean everything! it may be worth checking out anyway?

Hope it helps :)

---

### Post by Fernhill Linux Project on 2012-01-19
In ubuntu 11.10 if you click on the dash and search for 'shutdown' you will see the shutdown icon. Left click and hold then drag it in to the unity launcher. You can right click almost all icons in the launcher and remove them, leaving only workspace switcher and rubbish bin, and what you choose.
You can also drag items from the dash programs list on to the desktop.

Another option would be to install gnome-shell and use the classic gnome session with auto login, hide or remove the launcher bars, and just have the shutdown and internet icons on the desktop. Maybe even set to run firefox at start up.

---

### Post by ubudog on 2012-01-19
> **gnu/mirow said:**
> It may be worth considering [chromeOS]("http://getchrome.eu/") - I've only tried it on a VM, so can't attest to hardware support.

But it's very basic - everything is run through the chrome browser.. and I mean everything! it may be worth checking out anyway?

Hope it helps :)

Another good suggestion.

---

### Post by snowpine on 2012-01-19
Have you tried [browserlinux]("http://www.browserlinux.com/")? (based on puppy but much simpler)

---

### Post by Double.J on 2012-01-19
> **snowpine said:**
> Have you tried [browserlinux]("http://www.browserlinux.com/")? (based on puppy but much simpler)

Thanks for this snowpine - this one had escaped my notice :D

---

### Post by snowpine on 2012-01-19
ps I think it's awesome that your 85 year old mom has 8+ years of Linux experience (and that you are helping her). :)

---

### Post by ubudog on 2012-01-19
> **snowpine said:**
> Have you tried [browserlinux]("http://www.browserlinux.com/")? (based on puppy but much simpler)
Another good one! 
> **snowpine said:**
> ps I think it's awesome that your 85 year old mom has 8+ years of Linux experience (and that you are helping her). :)

:D That is awesome.

---

### Post by Fernhill Linux Project on 2012-01-19
I was just removing the desktop 'shutdown' and 'firefox' icons I created to make sure it worked before posting, and I found that right clicking gives you the option to resize them.
I have now got two massive icons covering a big portion of the desktop, and think this may be well suited to your mum's needs.

---

### Post by Peet42 on 2012-01-19
Cheers, everyone, thanks for all the great ideas.  I'll have a play tomorrow and see which seems best - I have the advantage that all her stuff is "in the cloud" - when I originally set her up I made sure that nothing that happened at "her end" could ever lose all her data.  Which means I can wipe the HDD and try other OS's without any downside. :D

---

### Post by ubudog on 2012-01-19
> **Peet42 said:**
> Cheers, everyone, thanks for all the great ideas.  I'll have a play tomorrow and see which seems best - I have the advantage that all her stuff is "in the cloud" - when I originally set her up I made sure that nothing that happened at "her end" could ever lose all her data.  Which means I can wipe the HDD and try other OS's without any downside. :D

:D That is always good.  

Best of luck!
- ubudog

---

### Post by Peet42 on 2012-01-20
First experiment's not too promising...  I tried Chrome, only to find that it can't see the built-in wi-fi. :-( (Her machine is currently an EEE Box B202)

It's the same problem I had the first time I put Ubuntu onto it - I installed 10.04LTS, only to later find that they ahd "broken" the wi-fi driver in that edition, hence my fresh install of 11.10.

---

