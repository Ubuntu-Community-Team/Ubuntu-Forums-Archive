---
title: "kde app fails to launch from nautilus"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by zibi on 2008-10-23
Hi, I'm with ubuntu 8.04 (gnome) and I have some kde application installed.
Recently I'm able to launch kdvi only from the gnome menu panel or from console and not from nautilus by double clicking .dvi files (not even with "open with..." from the right click menu).

I noticed that when I was lanching the program from consol I was getting the following message:

kbuildsycoca: WARNING: Parse error in /home/zibi/.config/menus/applications-merged/xdg-desktop-menu-dummy.menu, line 1, col 1: unexpected end of file

I then googled around and I saw that many others had this problem. The solution suggested was that there could have been problems with permission and ownership of the ~/.kde folder.

Accordingly I tried the following command:

chown -R $USER:$USER $HOME/.kde

then I realized that instead of $USER and $HOME I should have put my real username and home location
so I tried

chown -R zibi:zibi ~/.kde

Now I still cannot launch kdvi from nautilus. But if I launch it from console I get the following message:

kbuildsycoca running...
QApplication::notify: Unexpected null receiver

SO I reinstalled with synaptic and the problem is still the same.
The fisrt time I launched kdvi from consol I got the first message. But from the second time I launched it I get the second message.

Everything looks fine with other K applications (kile and kpdf).

FInally I post this

[email]zibi@zibi:~/.kde[/email]$ ls -l
total 4
lrwxrwxrwx 1 zibi zibi   22 2007-06-01 14:26 cache-zibi -> /var/tmp/kdecache-zibi
drwx------ 9 zibi zibi 4096 2007-07-10 18:16 share
lrwxrwxrwx 1 zibi zibi   23 2008-01-05 16:07 socket-zibi -> /tmp/ksocket-zibib9yZSc
lrwxrwxrwx 1 zibi zibi   13 2007-06-01 14:26 tmp-zibi -> /tmp/kde-zibi


I don't know if may be of some help.
Thank you a lot.

---

### Post by aysiu on 2008-10-23
A good next step test would be to create a new test user, log in as that test user and see if you experience the same problem or not.

Then you can see if it's a user-specific problem or a system-wide problem.

---

### Post by zibi on 2008-10-24
I created another user and it has the same problem

no way of lanuching kdvi by double clicking .dvi files in nautilus. 
From console QNotity gives the "unexpected null receiver" message but th program runs.


:confused:

---

### Post by zibi on 2008-10-24
Sorry, I mean that from console I get the following

kbuildsycoca running...
QApplication::notify: Unexpected null receiver

Thanks again
Luca

---

