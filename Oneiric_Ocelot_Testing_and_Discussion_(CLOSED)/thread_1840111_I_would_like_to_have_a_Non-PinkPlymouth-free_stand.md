---
title: "I would like to have a Non-Pink/Plymouth-free standard Linux boot."
date: 2011-09-07
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by effenberg0x0 on 2011-09-07
I would like to have an actual Linux boot, in which I would be able to joyfully see what is being loaded, errors, etc. Moreover, I never really managed to make this Plymouth thing work, no matter in how many different PCs I try. Dell laptops, HP laptops, Lenovo desktops, Acer, Asus, etc. I seriously doubt this thing has ever worked outside the developer's PC.

For me it has always been a pink screen with no text, logo, animation, text anything until the DM login shows if you're lucky. In other PCs I see oversized  or undersized logos, decentered pink squares with large crop bars on sides, stretched pink rectangles with crops bars on top/bottom, trembling pink distorced logos in static/teared background, etc. Never seen something acceptable. 

- Removing Plymouth via apt-get is basically impossible. Apt will tell you that you will need to uninstall everything, even remove the CPU, PSU, RAM, Cables, HDD, the screws, etc. You end up with an empty metal box and pretend you have a working PC, maybe put some led lights on, etc.

- There's no Plymouth config file in /etc or /etc/default as one could expect. Don't know how to disable this thing.
 
- Removing it from /etc/init.d. The pink thing is still in boot. 

- Changing grub2 conf at /etc/default to use no splash, vga=791, whatever, etc won't work. The pink screen will still be there. 

Maybe it find its way into my BIOS, or it contaminated my Monitor somehow, 

Help?

---

### Post by lucazade on 2011-09-07
Plymouth works good only with open source video drivers (with KMS feature).
To disable it, without uninstalling, do this:

```
sudo mv /etc/init/plymouth.conf /etc/init/plymouth.conf.disabled
```

---

### Post by effenberg0x0 on 2011-09-07
```
sudo mv /etc/init/plymouth.conf /etc/init/plymouth.conf.disabled
sudo reboot now
```

Pink is gone man, thanks. Problem is that now I have an entirely black screen, still with no "boot text" on it.

But thank you a lot. Black is already better.

Regards,
Effenberg

---

### Post by lucazade on 2011-09-07
> **effenberg0x0 said:**
> ```
sudo mv /etc/init/plymouth.conf /etc/init/plymouth.conf.disabled
sudo reboot now
```

Pink is gone man, thanks. Problem is that now I have an entirely black screen, still with no "boot text" on it.

But thank you a lot. Black is already better.

Regards,
Effenberg

to enable verbose boot text:
```
gksu gedit /etc/default/grub

```
remove "spash" from GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

(if you remove also 'quiet' you'll see kernel output)
save and close gedit

```
sudo update-grub

```
reboot

---

### Post by effenberg0x0 on 2011-09-07
Hi Lucazade,

I already had remove splash and quiet from /etc/default/grub and ran update-grub with no success (black screen until greeter). I ran into a script, tried and it fixed the problem. Have a look at it at:

[http://www.webupd8.org/2010/10/script-to-fix-ubuntu-plymouth-for.html](http://www.webupd8.org/2010/10/script-to-fix-ubuntu-plymouth-for.html)

Regards,
Effenberg

---

### Post by rapiertg on 2011-09-07
Since some time, it was also not enough to remove splash and quiet for me to see what system have to tell me. I had to add to /etc/default/grub following line:

```
GRUB_GFXPAYLOAD_LINUX=text
```

---

### Post by Harry33 on 2011-09-07
> **effenberg0x0 said:**
> I would like to have an actual Linux boot, in which I would be able to joyfully see what is being loaded, errors, etc. Moreover, I never really managed to make this Plymouth thing work, no matter in how many different PCs I try. Dell laptops, HP laptops, Lenovo desktops, Acer, Asus, etc. I seriously doubt this thing has ever worked outside the developer's PC.

For me it has always been a pink screen with no text, logo, animation, text anything until the DM login shows if you're lucky. In other PCs I see oversized  or undersized logos, decentered pink squares with large crop bars on sides, stretched pink rectangles with crops bars on top/bottom, trembling pink distorced logos in static/teared background, etc. Never seen something acceptable. 

- Removing Plymouth via apt-get is basically impossible. Apt will tell you that you will need to uninstall everything, even remove the CPU, PSU, RAM, Cables, HDD, the screws, etc. You end up with an empty metal box and pretend you have a working PC, maybe put some led lights on, etc.

- There's no Plymouth config file in /etc or /etc/default as one could expect. Don't know how to disable this thing.
 
- Removing it from /etc/init.d. The pink thing is still in boot. 

- Changing grub2 conf at /etc/default to use no splash, vga=791, whatever, etc won't work. The pink screen will still be there. 

Maybe it find its way into my BIOS, or it contaminated my Monitor somehow, 

Help?

It is the package mountall that prevents the uninstallation of plymouth.
Mountall depends on both plymouth and libplymouth2.
See here:
[https://launchpad.net/ubuntu/oneiric/amd64/mountall/2.31](https://launchpad.net/ubuntu/oneiric/amd64/mountall/2.31)

You may find a version of mountall from a PPA where it has been built without plymouth dependency.

---

### Post by Harry33 on 2011-09-07
> **lucazade said:**
> Plymouth works good only with open source video drivers (with KMS feature).
...


In my 32-bit (Intel) and 64-bit (AMD) setups both with open source graphics drivers
the Plymouth does not work during startup, it is not at all visible.
However, during shutdown I can see the chosen Plymouth theme clearly enough.
But, I see this also in my 64-bit setup with nvidia-current.

---

### Post by lucazade on 2011-09-07
really weird Harry33,
seems I'm lucky because I see plymouth, with correct resolution and theme, with ATI (3 different cards) and with nouveau.
KMS get correct resolution during kernel startup and pass this to plymouth (sometimes plymouth lasts only for a few seconds anyway!)

with closed drivers (nvidia-current and intel-emgd w/o KMS) I can see plymouth in low res (probably 1024x768) and I need to tweak grub in order to keep the resolution found automatically via EDID and keep it for all the startup process (vt.handoff=7).
so I usually add this:
GRUB_GFXPAYLOAD_LINUX=keep

plymouth is far from perfect, obviously.. but with kms drivers my experience is good.
about mountall dep you are correct, IIRC was necessary for fsck check.

---

### Post by Harry33 on 2011-09-07
> **lucazade said:**
> 
...
with closed drivers (nvidia-current and intel-emgd w/o KMS) I can see plymouth in low res (probably 1024x768) and I need to tweak grub in order to keep the resolution found automatically via EDID and keep it for all the startup process (vt.handoff=7).
so I usually add this:
GRUB_GFXPAYLOAD_LINUX=keep
...


Yes I use that line too with my Nvidia card.

---

### Post by sgage on 2011-09-07
> **rapiertg said:**
> Since some time, it was also not enough to remove splash and quiet for me to see what system have to tell me. I had to add to /etc/default/grub following line:

```
GRUB_GFXPAYLOAD_LINUX=text
```

Simply removing splash and quiet works for me. I, too, like to see what's going on at boot time.

---

### Post by effenberg0x0 on 2011-09-07
I never had the time to understand what was responsible for the pink screen of death in the last months. Now that I read about it a little, I am truly amazed people went that far to hide normal boot messages. Messages are logged in background, relocated to system log after plymouth ends its task, etc. A daemon, a client, init scripts, conf scripts, theme packages, etc were created, but no simple option to disable it was ever thought off? Hell, it's just a static background with a logo...

Searching a couple minutes I found probably a hundred or more threads, blogs, etc where people mention they see no logo, or only weird deformed logos, they hate but can't change the color, can't apply any theme, can't disable, can't uninstall, break the system while attempting to uninstall, bug reports, fixes, the thing conflicts with grub, conflicts with video cards, breaks VTs, serious dependency issues, etc. Again, too much trouble for a background and a logo...

IMHO, I think the whole thing was a big misstep considering the only possible "benefit" would be to hide OS information from the user in a very questionable "more pleasant / aesthetic" way.

Regards,
Effenberg

---

