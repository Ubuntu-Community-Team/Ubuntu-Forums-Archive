---
title: "nautilus problem"
date: 2013-07-06
forum: New to Ubuntu
---

### Post by bdubawoop on 2013-07-06
ubuntu 12.04 lts

when i ran gksu nautilus i got error about 'unable to create /root/.config/nautilus directory'

so i ran 'sudo mkdir /root/.config/nautilus'

now it runs with no error but does not show any of the partitions, only the floppy, ubuntu file system & usb drive.

what do i need to do to get it show all the partitions?

---

### Post by mc4man on 2013-07-06
Gnome (nautilus) really has no interest in users running a root nautilus browser so elements have been removed 
(a bit more extensive in 13.04/13.10

In this case you need to mount any volumes you wish to see in the root browser from a user nautilus browser window - then they'll show.

(this may be more a case of how volumes are now mounted then Gnome's distaste for root browsers

---

### Post by Paqman on 2013-07-06
What were you doing that  you need a root session in Nautilus for? There may be an easier way to do it than fighting against what the Gnome devs think you should or shouldn't be doing using their file browser ;)

---

### Post by BreezyBrooke on 2013-07-06
The funny thing about the new Nautilus is that Root Nautilus cannot mount, BUT if you mount using Non-Root Nautilus, they show up mounted in Root Nautilus. But really, you can cause problems if you don't know what you are doing. Tell us and we can help.

---

### Post by bdubawoop on 2013-07-07
just trying to copy the 10.04 background pics i had copied to another partition to /usr/share/backgrounds. couldn't do it as thats owned by root.
also ran into this irritating business when i couldn't view screenshots or logs in var/logs/installer from my debian wheezy install. by the way. debian nautilus shows all partitions from the gitgo without having to 'mount' first.

i stumbled on the solution mentioned by breezybrooke by viewing (mounting) the partitions in 'computer' then they were visible when i ran nautilus.

on my other computer i used the sudo cp in terminal to do it but its easier with the desktop as you don't have to know/type the exact path name.

---

