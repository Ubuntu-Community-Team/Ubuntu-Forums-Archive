---
title: "Sudo command on startup?"
date: 2012-05-11
forum: New to Ubuntu
---

### Post by lopz on 2012-05-11
Hello all,

I am a new convert to Ubuntu from Win7 and enjoying the experience.

One problem I have it that my laptop display is very dark, so I use the following command to correct this:-  sudo setpci -s 00:02.0 F4.B=50^C

I am wanting to know, is there a way to set this command to run automatically on startup?

Thank you all in advance

---

### Post by MG&amp;TL on 2012-05-11
The problem with this is that your normal autostart won't work as it can't prompt for your password.

[http://askubuntu.com/questions/88589/run-command-at-boot-as-root]("http://askubuntu.com/questions/88589/run-command-at-boot-as-root")

...this looks like what you want to do.

---

### Post by lopz on 2012-05-11
Perfect.  Thank you! :p

---

