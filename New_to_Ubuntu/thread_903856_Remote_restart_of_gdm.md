---
title: "Remote restart of gdm"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by seattle vic on 2008-08-28
I regularly log into my home machine from work and use x11vnc to work on my machine.  On several occasions I've had to restart the home machine, but have not been able to pull up vnc to log into the gnome display.

Once the home machine boots up, I can ssh to a shell, start x11vnc as I usually do, then:

sudo /etc/init.d gdm start

Then I try to link up via vnc viewer as usual, but with no joy.  I'd have expected to see the login screen where I could log in.

What am I doing wrong?

Thanks in advance...

---

### Post by ggaaron on 2008-08-28
Never done it, but a suggestion - I think that gdm has some options in it's configuration about vnc, check them out, I think that you can get it's configuration from system menu.

---

### Post by bodhi.zazen on 2008-08-28
x11vnc allows you to share a running X session.

When you re-start GDM you kill your x sessions and GDM is waiting for a log in. Once someone logs in, you can then see the X session.

Try a different vnc server, such as vnc4server or freenx.

---

### Post by swoll1980 on 2008-08-28
how about just logging in then starting x "startx" will that work?

---

### Post by krunge on 2008-08-28
> **seattle vic said:**
> 
sudo /etc/init.d gdm start

Then I try to link up via vnc viewer as usual, but with no joy.  I'd have expected to see the login screen where I could log in.


Have a look at the Section Labelled  "Continuously" in this FAQ item: [http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager]("http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager")
it might do what you want by adding 1 line to gdm's Init/Default script.

Also, note the "KillInitClients" setting you will probably need to do for GDM.

It's not clear to me why you need to start gdm, do you not have it enabled to start at boot time?

---

