---
title: "Unity Top Bar Missing indicator session applet"
date: 2011-06-23
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by nonly1n on 2011-06-23
Hi, 

I'm missing my indicator-session-applet (the one with the log out, guest, switch user, shutdown, restart and system settings)and have no idea how to get it back, it say's its installed in synaptic but it just disappeared on me after an update.

Ubuntu 11.10. 

thanks in advance, 

[IMG]https://lh6.googleusercontent.com/-P7In5uQRsTI/TgPUQPTWWlI/AAAAAAAAAFs/mcTRlVi2fVU/Screenshot.png[/IMG]

---

### Post by scradock on 2011-06-23
> **nonly1n said:**
> Hi, 

I'm missing my indicator-session-applet (the one with the log out, guest, switch user, shutdown, restart and system settings)and have no idea how to get it back, it say's its installed in synaptic but it just disappeared on me after an update.

Ubuntu 11.10. 

thanks in advance, 

[IMG]https://lh6.googleusercontent.com/-P7In5uQRsTI/TgPUQPTWWlI/AAAAAAAAAFs/mcTRlVi2fVU/Screenshot.png[/IMG]
Did that on me too today. It came back after a re-boot.

---

### Post by sparker256 on 2011-06-23
> **nonly1n said:**
> Hi, 

I'm missing my indicator-session-applet (the one with the log out, guest, switch user, shutdown, restart and system settings)and have no idea how to get it back, it say's its installed in synaptic but it just disappeared on me after an update.

Ubuntu 11.10. 

thanks in advance, 

[IMG]https://lh6.googleusercontent.com/-P7In5uQRsTI/TgPUQPTWWlI/AAAAAAAAAFs/mcTRlVi2fVU/Screenshot.png[/IMG]
I found that indicator-session was installed but indicator-session-gtk2 was not so I installed that. 

Bill

---

### Post by nonly1n on 2011-06-24
> **sparker256 said:**
> I found that indicator-session was installed but indicator-session-gtk2 was not so I installed that. 

Bill

Hi, 

thanks now that helped my about me indicator is missing i dont get whats going each just keeps disappearing on

---

### Post by nonly1n on 2011-06-24
> **nonly1n said:**
> Hi, 

thanks now that helped my about me indicator is missing i dont get whats going each just keeps disappearing on

corrected i accidentally uninstalled indicator-me trying to remove gwibber, alls sorted.

---

### Post by sparker256 on 2011-06-24
> **nonly1n said:**
> Hi, 

thanks now that helped my about me indicator is missing i dont get whats going each just keeps disappearing on
There is a lot of turmoil with the update breaking things and what I have been using for a couple of cycles is aptitude. I use the following command and has allowed be to not have a broken system unless I don't follow my own rules.
```

sudo aptitude update && sudo aptitude safe-upgrade

```
It also does not come installed so you have to install it. Hope this helps.

Bill

---

