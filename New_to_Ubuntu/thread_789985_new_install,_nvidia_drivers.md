---
title: "new install, nvidia drivers"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by Metal Mick on 2008-05-11
Hi all,

I have a new machine with a fresh 8.04, and wish to install the newest nVidia drivers 173.08. I have done nothing with it yet in the way of installing other drivers.

I try using the *.run file I downloaded from the nVidia site and find get the message I cannot run the file whilst in X:

"You appear to be running an X server; please exit X before installing."

Can somebody help me with "exiting X" so I can continue? A link to clear instructions will suffice.

Many thanks.

Michael P

---

### Post by logos34 on 2008-05-11
ctrl+alt+F1

sudo /etc/init.d/gdm stop

sh *.run

This starts up the interactive installer.  But you need to make sure you have all the right linux kernel headers and restricted pkgs

Alternatively, you might want to use [Envy ]("http://albertomilone.com/nvidia_scripts1.html")instead

---

### Post by HotShotDJ on 2008-05-11
> **I_love_p_quarles said:**
> No, he's using the wrong filesystem for the nvidia card.  You can fix this by typing:
```

sudo mkfs.ext3

```

and please post the output so we can analyze it.STOP THAT... Ignore this guy.

---

### Post by Metal Mick on 2008-05-11
> **logos34 said:**
> ctrl+alt+F1

sudo /etc/init.d/gdm stop

sh *.run

This starts up the interactive installer.  But you need to make sure you have all the right linux kernel headers and restricted pkgs

Alternatively, you might want to use [Envy ]("http://albertomilone.com/nvidia_scripts1.html")instead

Hi Logos34 and HotShotDJ,

many thanks for your help. Envy worked a treat. There is a brief Nvidia splash on boot as confirmation.

I've been dabbling with Ubuntu for a short while now, with limited success, but success nonetheless, and its thanks to guys like you that I've persisted.

Cheers,

Michael P

---

### Post by logos34 on 2008-05-11
> **Metal Mick said:**
> Hi Logos34 and HotShotDJ,

many thanks for your help. Envy worked a treat. There is a brief Nvidia splash on boot as confirmation

Super.

Here's how to disable that nvidia splash if you're interested ('nologo' option):

[http://www.funnestra.org/ubuntu/gutsy/#nvidia-driver](http://www.funnestra.org/ubuntu/gutsy/#nvidia-driver) (-->#6)

Enjoy!

---

