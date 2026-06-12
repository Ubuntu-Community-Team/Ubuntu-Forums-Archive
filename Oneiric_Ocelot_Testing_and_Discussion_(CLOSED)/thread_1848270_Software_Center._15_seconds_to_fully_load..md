---
title: "Software Center. 15 seconds to fully load."
date: 2011-09-22
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by philinux on 2011-09-22
I just rebooted to double check this. 

It takes about 15 seconds to get to "Our Star Apps" from a cold boot up. Subsequent launches of SC still takes 10 seconds.

Anyone else seeing this.

[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/845579](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/845579)

---

### Post by dino99 on 2011-09-22
sorry, i only use serious tools :)

---

### Post by whoop on 2011-09-22
> **dino99 said:**
> sorry, i only use serious tools :)
Funny...

3 seconds over here...

---

### Post by lucazade on 2011-09-22
> **dino99 said:**
> sorry, i only use serious tools :)

we all Dino..
but it would be nice to report bugs also for tools we don't use often :)

---

### Post by MacUntu on 2011-09-22
Yeah, but it's not like "USC starting slow" is something new. :-/

---

### Post by dino99 on 2011-09-22
> **lucazade said:**
> we all Dino..
but it would be nice to report bugs also for tools we don't use often :)

oh i do all the days long :(

---

### Post by lucazade on 2011-09-22
> **dino99 said:**
> oh i do all the days long :(

I had no doubts

anyway.. usc is quite slow here as well.. more or less 15sec to fullystartup like philinux said
this is the output launching it from terminal:

luca@vbox:~$ software-center-gtk3 
2011-09-22 16:07:45,374 - softwarecenter.ui.gtk3.em - INFO - EM's: 15 12 17
2011-09-22 16:07:49,446 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2011-09-22 16:07:49,985 - softwarecenter.ui.gtk3.utils - INFO - Softwarecenter style provider for ambiance Gtk theme: /usr/share/software-center/ui/gtk3/css/softwarecenter.css
2011-09-22 16:08:04,454 - softwarecenter.ui.gtk3.app - INFO - software-center-agent finished with status 1

---

### Post by philinux on 2011-09-22
> **MacUntu said:**
> Yeah, but it's not like "USC starting slow" is something new. :-/

Agreed but 15 seconds. This is where newbies will be heading too.

---

### Post by Quackers on 2011-09-22
Synaptic used to take that amount of time for me, but in the last week or so it starts almost immediately now :-)

---

### Post by tobluntoo on 2011-09-22
so what do you more ubuntu-savvy chaps use to download your software?

---

### Post by philinux on 2011-09-22
> **tobluntoo said:**
> so what do you more ubuntu-savvy chaps use to download your software?

Synaptic package manager.
Terminal
Sometimes via firefox apt url.

---

### Post by Quackers on 2011-09-22
Synaptic here too.
In fact I just noticed that USC isn't even an option in my gnome-shell system!

---

### Post by tobluntoo on 2011-09-22
Nice one, i shall get on it :-) very impressed with the quick responses round here :-) my enthusiasm for linux/ubuntu is growing by the hour! And to think less than a month ago I had know idea what an operating system even was. There were just windows computers or apple ones!

---

### Post by fjgaude on 2011-09-22
> **tobluntoo said:**
> so what do you more ubuntu-savvy chaps use to download your software?

I normally use apt-get or synaptic, never software center.

Everything done in USB takes about 5 seconds or less.

---

### Post by fillmont on 2011-09-22
Software center is also really slow for me, and not just for loading. Even switching between Installed Programs and Programs to Download can take 10 seconds (and sometimes even greying out.)

Synaptic is still speedy as ever though.

---

