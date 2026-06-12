---
title: "Can't change permissions on internal hard drive"
date: 2014-10-01
forum: New to Ubuntu
---

### Post by mark166 on 2014-10-01
Hi all, 

I have just installed the latest flavor of Xubuntu onto a flash drive. I also have an internal HDD connected via Sata3 to the system. This houses all my files (music/movies/etc).

I have set up a samba share so I can access by Xubuntu box from my windows PC. For some reason I am unable to edit permissions on the internal HDD in my xubuntu machine.

I can change permissions for any folder/directory within the Xubuntu install (on the flash drive). But cant get it to work for the internal HDD.

Ive tried via terminal **'sudo chown nobody.nogroup...."** etc. Have also tried via running Nautilus as root. Interrestingly, when i try to change the permissions using nautilus, so that owner is nobody - i click on nobody, it changes, then a second later changes back to my username. 

Hope that made sense. Appreciate your help :)

---

### Post by Impavidus on 2014-10-02
Which partition type is on the data HDD? NTFS for example doesn't support Unix style ownership and permissions.

---

