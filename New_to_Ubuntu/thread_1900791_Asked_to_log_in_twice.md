---
title: "Asked to log in twice"
date: 2011-12-27
forum: New to Ubuntu
---

### Post by Merisi on 2011-12-27
I logged into Ubuntu today for the first time in 9 days and initially the log in screen seemed to have a glitch and had some weird icon and smudging on the top of the screen and when I entered  my password it was also being entered at the top of the screen too.  After entering my password correctly the screen cleared back to normal and I had to enter my password again after which everything was fine.  Has anyone any ideas about why this happened?

---

### Post by roscorcoran on 2012-02-20
Hey there, 
I am getting the same problem on 11.10
Did you ever find a solution / explanation for this?

It's annoying, makes me feel like theres a keylogger or something at startup. Or my password is being phished somehow....

---

### Post by Merisi on 2012-02-20
I never found a solution so I took an extreme response and deleted Ubuntu.  I'm waiting for the long term release in April before I install it again.  I felt like you that my password had become vulnerable and it made me feel very nervous.

---

### Post by MCJavaMonkey on 2012-02-25
Im also seeing this within the last couple of weeks. Was intermittent, now its consistently occurring. Anyone have a solution or know the cause?

---

### Post by HeroOfCanton on 2012-02-25
Couple of possible solutions offered here [http://ubuntuforums.org/showthread.php?t=1867733](http://ubuntuforums.org/showthread.php?t=1867733)

There are also several similar bugs reported on launchpad.

It's more likely a video card issue than a password sniffer. I understand the concern though.

---

### Post by paolik65 on 2013-03-20
Same problem here.

Solution: use GDM instead of LIGHTDM solved it for me.

Install GDM and select it in terminal mode with the following command line:


sudo dpkg-reconfigure gdm

---

