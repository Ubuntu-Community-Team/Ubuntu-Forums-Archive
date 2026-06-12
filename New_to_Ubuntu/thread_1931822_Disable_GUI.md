---
title: "Disable GUI"
date: 2012-02-26
forum: New to Ubuntu
---

### Post by benpack101 on 2012-02-26
I need a quick reminder,

I believe I want to end the XORG process and just run Ubuntu completely through the command line.

How do I do this?

And if I want to enable it again (because I miss my GUI) how do I do that?

Thanks in advance!

---

### Post by JRV on 2012-02-26
<CTRL><ALT><F1> will give you a command line only system.

<CTRL><ALT><F7> will get you back to the GUI.

---

### Post by audiomick on 2012-02-26
when you log in, you can select to log in to xterm instead of a gnome or whatever session.
I don't know if this is what you have in mind, though. I think the x-server is still running in that case.

---

### Post by Krytarik on 2012-02-26
> **benpack101 said:**
> I believe I want to end the XORG process and just run Ubuntu completely through the command line.

How do I do this?

And if I want to enable it again (because I miss my GUI) how do I do that?
Please see this earlier post; but notice that you need to replace "gdm" with "lightdm" in any code bits stated there, if you are using the default display manager of Oneiric 11.10 (stated in your profile):

[http://ubuntuforums.org/showthread.php?p=10798400#post10798400](http://ubuntuforums.org/showthread.php?p=10798400#post10798400)

Regards.

---

### Post by benpack101 on 2012-02-26
Thanks everyone for your help!

Thread solved!

---

