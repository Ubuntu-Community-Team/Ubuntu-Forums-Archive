---
title: "Can not login into Ubuntu"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by Sig_ZA on 2008-07-13
Sorry about the cross posting, but it's been almost a week and my Ubuntu PC is still down.

====
I installed some updates including some kernel bits and pieces using the ubuntu update thingy (the one that pops open a window and says that updates are available).

Ubuntu starts up normally, then goes to a screen that gives the various [ok] on all the services started.

Then a message appears: linux PC login, after this the screen goes blank.

Ubuntu is still running the servers (web, proxy, etc) but I can **not** [edit] login.

Help please...

---

### Post by ajgreeny on 2008-07-13
Are you, or rather were you, using a proprietary graphics driver before your updating was carried out?  If so you may need to do so again in order to get a proper graphics output.

---

### Post by Sig_ZA on 2008-07-13
I'm am using the Nvidia drivers "supplied" with Ubuntu.
The graphics do work as I am able to read the "login" message.

---

### Post by Sig_ZA on 2008-07-15
Please, anybody.
I've been without the PC for a week now.
Surely this is fixable!!

---

### Post by coolman121 on 2008-07-15
ok reinstall ubuntu 8.04 with live cd then *clean install then you should be fine remember to make no password on start up
 and by the way do you have a laptop???? that is tunning ubuntu . cause that might be incompatible or just messed up with your lptop mobo ...... mine was ...*try plugging it in when running ubuntu*

---

### Post by houbysoft.xf.cz on 2008-07-15
Have you tried CTRL+ALT+F1 then login, then sudo dpkg-reconfigure xserver-xorg?

EDIT: whoooops. without the apt-get :)

 By the way, suppose it's a mistype, you said you CAN login in the first message?

---

### Post by Sig_ZA on 2008-07-15
> **coolman121 said:**
> ok reinstall ubuntu 8.04 with live cd then *clean install then you should be fine remember to make no password on start up
 and by the way do you have a laptop???? that is tunning ubuntu . cause that might be incompatible or just messed up with your lptop mobo ...... mine was ...*try plugging it in when running ubuntu*
Thanks, but I hope this isn't the answer.
A re-install sounds very extreme.

It's a desktop and has been working fine for the last 2 years until now when I installed some of the latest updates. I also don't have the live disk as I upgrade from 7.04 to my current version online.

---

### Post by Sig_ZA on 2008-07-15
Yip, CAN NOT. Original post fixed.

Ok, I'm making progress.
CTRL+ALT+F1 gives me a terminal and I can login.

I tried "sudo apt-get dpkg-reconfigure xserver-xorg" but I get an invalid operation error. I might have the spaces in the wrong place.

Could you give it to me again please.

> **houbysoft.xf.cz said:**
> Have you tried CTRL+ALT+F1 then login, then sudo apt-get dpkg-reconfigure xserver-xorg? By the way, suppose it's a mistype, you said you CAN login in the first message?

---

### Post by WRDN on 2008-07-15
Rather than using the code, boot into recovery mode (it should be an option at the GRUB bootloader, unless you removed it), and when given the options, select "Fix X Server" (or something similar).

---

### Post by Sig_ZA on 2008-07-15
Ok, now in English please. 8)

My machine always booted straight up to where I logged into the ubuntu desktop.
Nothing in between, so I'm not sure about GRUB which you mention.

I'm happy typing in code if that is what will get things working.


> **WRDN said:**
> Rather than using the code, boot into recovery mode (it should be an option at the GRUB bootloader, unless you removed it), and when given the options, select "Fix X Server" (or something similar).

---

### Post by houbysoft.xf.cz on 2008-07-15
Try holding ESCAPE at boot, it should bring you a menu with options, then select the revocery mode one.

---

### Post by Sig_ZA on 2008-07-15
Ok, I tried the ESCAPE recovery mode.
The PC booted and eventually ended up in a terminal mode with: root@linux-PC:~#
And that was about it. None of the services (servers) worked.

If I restart normally again it runs up to the blank screen as before and if I press CTRL+ALT+F1 I get Linux_PC login.

So I'm back where I started.

At one stage I got a message about an Xserver problem with something about too many parametres, but I never wrote down the exact error message.

---

### Post by houbysoft.xf.cz on 2008-07-15
OK. Whooooooooops. I see that I have done a REALLY bad mistype :) try my command again, but without the apt-get, that was my mistake. So do that CTRL ALT F1, login, and then type sudo dpkg-reconfigure xserver-xorg. It should ask you some things, try to answer and see if it helps.

---

### Post by Sig_ZA on 2008-07-16
> **houbysoft.xf.cz said:**
> OK. Whooooooooops. I see that I have done a REALLY bad mistype :) try my command again, but without the apt-get, that was my mistake. So do that CTRL ALT F1, login, and then type sudo dpkg-reconfigure xserver-xorg. It should ask you some things, try to answer and see if it helps.

Ok, I followed this command and it asked me a whole lot of questions about my monitor, graphics card, mouse and keyboard. It then over wrote the xorg.conf file.

When I started up again I got the same problem still. :confused:

When I reset and started yet again I got the following message:

Failed to start X Server.
/etc/gdm/failsafeXserver line 47 (too many arguments).
Warning: falling back to gdm to report this issue.

So what's up with Xserver and what is gdm?:-|

---

### Post by houbysoft.xf.cz on 2008-07-16
Could you maybe post that /etc/gdm/failsafeXserver file here?
And by the way, GDM is the Gnome Display Manager, basically it's a GUI login program.

---

### Post by Sig_ZA on 2008-07-16
> **houbysoft.xf.cz said:**
> Could you maybe post that /etc/gdm/failsafeXserver file here?
And by the way, GDM is the Gnome Display Manager, basically it's a GUI login program.
Sorry, I have no idea how to do this.
I only have terminal access (if that's what you call it where you only have text).
The file is 215 lines long!

[PHP]Line 47 is: if [ -z $serverargs ] then;
Line 50 is: fi
Line 51 is: serverargs="${serverargs} -br -once -config $xorg_conf_failsafe"[/PHP]

I never changed any of these or the XServer conf files before the problem, so I don't know what could now have gone wrong.

---

### Post by Sig_ZA on 2008-07-16
I don't know if this helps, but after I press CTRL-ALT-F1 the following appears:

[PHP]Starting up ...
Loading please wait ...
kinit: name_to_dev_t(/dev/disk/by-uuid/LONG NUMBER) = sda5(8,5)
kinit: trying to resume from /dev/disk/by-uuid/SAME LONG NUMBER
kinit: No resume image, doing normal boot ...[/PHP]

---

### Post by t0p on 2008-07-17
Sig_ZA: don't worry about that "kinit: No resume image, doing normal boot" stuff... all the time I was running Gutsy, I had that stuff appear on my Ctrl-Alt_F1 console at login. Must be a Gutsy "bug" but it doesn't really matter...

Unfortunately, I don't know how to fix your problem.  Sorry!!  :(

---

### Post by Sig_ZA on 2008-07-19
Somebody, anybody?

---

