---
title: "How to install GDM themes on ubuntu mate"
date: 2017-02-02
forum: New to Ubuntu
---

### Post by crazzyshooter on 2017-02-02
Hi,

I am using ubuntu mate 16.01 x64 and i would like to ask about GDM themes.

Is there a way to run these two gdm themes on latest 16.04?

**Avio-GDM:** [https://www.gnome-look.org/p/1078445/](https://www.gnome-look.org/p/1078445/)

**Arc-Colors GDM-Walls:** [https://www.gnome-look.org/p/1078513/](https://www.gnome-look.org/p/1078513/)

I really like gdm themes. With latest ubuntu 16.04, System>Administration>Login window is gone. :(

If there is a way to activate these two gdm themes on ubuntu mate 16.04, please do guide me.

Thanks a lot in advance!!

---

### Post by Dennis N on 2017-02-02
I actually did this a while ago in Ubuntu MATE 14.04. Ubuntu MATE uses lightdm display manager, so you need to install a different display manager that can use gdm themes - the one I used was the MDM display manager (package name: mdm) (Linux Mint MATE uses this by default), which I installed from a PPA called noobslab. Also installed with it was mdm-themes. mdm themes includes the arc-colors themes - one is pictured at your link - it's called Arc-Brave. There is also Arc-Brave-Userlist (which I use myself), which is the same, but with a list of users on the left side as well. There is also a nice login window manager to switch between the available themes. As I recall, it was fairly easy to get it switched over from lightdm.

That said, I looked at the PPA again and don't see a version for Ubuntu MATE 16.04 (xenial):

[https://launchpad.net/~noobslab/+archive/ubuntu/mint](https://launchpad.net/~noobslab/+archive/ubuntu/mint)

Don't know why that is. Maybe another source can be found.

---

### Post by crazzyshooter on 2017-02-02
Thanks for replying dennis n.

I started using ubuntu back in 2008 with ubuntu 8.10. I have used GDM themes+screenlets+compiz in the past. Old ubunto looked so cool with all the cool features. too bad that we can't use beautiful GDM themes on latest ubuntu. :(

---

### Post by Dennis N on 2017-02-02
> **crazzyshooter said:**
> Thanks for replying dennis n.

I started using ubuntu back in 2008 with ubuntu 8.10. I have used GDM themes+screenlets+compiz in the past. Old ubunto looked so cool with all the cool features. too bad that we can't use beautiful GDM themes on latest ubuntu. :(

Well, I believe Linux Mint MATE still uses MDM with GDM packages on its latest Serena release (18.1), based on Ubuntu 16.04, so I don't think it is impossible. You could search for another PPA. 

Installing GDM itself from the Ubuntu repository does not look good to me, as it pulls 112 Gnome packages that I would not want. Better to stay with lightdm.
 
Of course, if it was something you really valued, you could just switch to Linux Mint MATE and get everything by default.

---

### Post by crazzyshooter on 2017-02-02
> **Dennis N said:**
> Well, I believe Linux Mint MATE still uses MDM with GDM packages on its latest Serena release (18.1), based on Ubuntu 16.04, so I don't think it is impossible. You could search for another PPA. 

Installing GDM itself from the Ubuntu repository does not look good to me, as it pulls 112 Gnome packages that I would not want. Better to stay with lightdm.
 
Of course, if it was something you really valued, you could just switch to Linux Mint MATE and get everything by default.

I will check linux mint mate. Thank you very much for helping me. ;)

---

