---
title: "ies4linux Only Works Once"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by FredJones on 2008-07-08
I installed ies4linux on my brand new Hardy install. When I launch IE6 it works fine the first time or at least the Congratulations page works. I can't seem to browser anywhere else. When I close it and then reopen it, it opens, sits there for a few seconds, and then goes dark (the whole window including title bar go dark) and then it just stays like that and I must force it to quit.

IE7 doesn't seem to work at all.

Any suggestions how to fix this?

---

### Post by ChameleonDave on 2008-07-08
Works OK for me.

Have you tried simply running the ies4linux installer again?

---

### Post by FredJones on 2008-07-08
Yes, I already tried the reinstall. I think it may have been working (at least ie6) before I installed some software. I installed all the LAMP items from synaptic, removed all games, added geany and dolphin and VirtualBox and a few other things. Now it doesn't work. I tried the reinstall just now, after all other software was installed. No go, unfortunately.

I also edited by xorg.conf trying to get my IntelliMouse Explorer not to scroll so crazy fast. No luck with that yet either.

---

### Post by ChameleonDave on 2008-07-08
This looks like a hard bug to isolate.

I can only suggest reinstalling Wine (as ies4linux relies on it), clearing out the ies4linux files (at *~/.ies4linux*), and running the ies4linux installer yet again.

Aside from that, you can run MSIE natively in VirtualBox.

---

### Post by crtlbreak on 2008-07-08
do a 
#sudo ps ax
find the iexplorer entitled
[www.tatanka.com.br/ies4linux/page/congratulations](www.tatanka.com.br/ies4linux/page/congratulations) and note the pid
then 
#sudo kill pidnnnn 
where pidnnnn is the process id associated with that process

now try and go to [www.anysite.com](www.anysite.com)

BTW - take all the defaults on the ies4linux install

but my advice will still be to stick to firefox as a browser - it is better and less flawed.
let us know if that was successfull
regards

---

### Post by ChameleonDave on 2008-07-08
> **crtlbreak said:**
> 
do a 
#sudo ps ax
find the iexplorer entitled
[www.tatanka.com.br/ies4linux/page/congratulations](www.tatanka.com.br/ies4linux/page/congratulations)

Are you sure?  When I do that, it doesn't come up with the URL in that manner.  In any case, it's not efficient to read through the list looking for it.  It makes more sense to use grep:

```

ps ax | grep ies4linux
kill ***the_number_gleaned_from_the_previous_command***

```

> **crtlbreak said:**
> 
but my advice will still be to stick to firefox as a browser - it is better and less flawed.

I doubt very much he intends to use IE as his main browser.

---

### Post by crtlbreak on 2008-07-08
ChameleonDave
on the first startup ies4linux goes to the "congratulations and donate now" url from tatanka. if you have subsequently tailored your ies4linux it obviously wont.
thank you for the 
ps ax | grep ies4linux
command  - much better fine tuning :)
regards

---

### Post by FredJones on 2008-07-09
Killing that process and then relaunching IE6 indeed worked. IE7 doesn't work, but that's fine as that's only a beta anyway.

When running IE6 and wineserver together use up my entire (2G dual core) CPU, however. Would be better indeed to use VirtualBox if so.

And when I close IE6, wineserver takes 100% of one of my CPU's cores. I have to kill it.

I notice that System Monitor reports IEXPLORE.EXE as status Zombie. Perhaps b/c it depended on wineserver?

I launched IE6 again and closed it. Then I killed the  IEXPLORE.EXE that was Sleeping. There were 3 actually. Now wineserver is quiet. Not running in fact.

I launched and killed IE6 once more and now it seems to work correctly, meaning no CPU draining, including after I close it

Can someone explain to me how these processes work a little bit? Before I started all this today, I rebooted (as I anyway do every day) so why should killing that initial process do anything? If I shut down and then reboot, are there processes running from my last session?

Thanks!

---

