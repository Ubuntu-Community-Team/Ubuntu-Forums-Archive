---
title: "creating shared folder in lucid to share w/ precise in virtualbox"
date: 2012-06-20
forum: New to Ubuntu
---

### Post by RH9R on 2012-06-20
I'm new to virtual setup, have read for hours so far, and don't understand how folders are shared. The only option to share is to install some windows services - but I only want to share w/ another version of Ubuntu running on virtualbox. Are these windows services neccessary if you're not publishing across a windows network?

---

### Post by Kakers on 2012-06-20
Hello RH9R

In VirtualBox you can set the virtual machine to share folders from the host machine, but there are no settings for sharing between virtual machines. 

My recommendation would be to use something like Samba and install it on the virtual machine that hosts the files you wish to share.

[http://www.unixmen.com/howto-install-and-configure-samba-share-in-ubuntu/](http://www.unixmen.com/howto-install-and-configure-samba-share-in-ubuntu/)

Hopefully someone else will see your post and suggest something better.

---

### Post by RH9R on 2012-06-20
Kakers, Thank you for your kind help. 
 
I'm using a lucid host to run 12.04 in virtualbox (thanks to the kind help of Myrddin) for the purpose of getting to know 12.04. So I just need the host to share w/ the guest system. I suspect its a very simple process, but this is my first experience w/ using a virtual, so its all new and awkward. I appreciate your kind help!

---

### Post by Morbius1 on 2012-06-20
_On the host:_

Open VBox and right click the Guest > Settings > Shared Folders > +

And add a folder to the list and have it automount as shown in Screenshot.

_On the Guest:_

VBox automatically mounts the share at boot at /media with a "sf_"  prefix ( in this example sf_DATA ) as shown in Screenshot2.

---

### Post by RH9R on 2012-06-20
Morbius, I appreciate your kind help. 
when I access shared folders on the host side, the dialogue window doesn't look the same. There's no 'automount' checkbox. I was able to add a shared folder on the host side, but in the guest side - it doesn't show. 'Checked teh /media folder - no sign of it there. 
'Wish I were more savvy on it and could make it easier to be helped. I do appreciate your kindness.

---

### Post by Morbius1 on 2012-06-20
What version of VirtualBox are you running?

---

### Post by RH9R on 2012-06-20
The version in the software Center is 3.2.8

---

### Post by Morbius1 on 2012-06-20
Well, that's the reason.

The current version from Oracle is 4.1.16. The current version in the software center in 12.04 is 4.1.12 so I guess lucid hasn't kept up. I'll have to go through my notes to see if I can find out how to do this in V3 of VBox.

I'm trying to avoid going the samba route because "shared folders" in VBox is a lot easier.

---

### Post by RH9R on 2012-06-20
again, morbius, I appreciate your help!

---

### Post by kanikilu on 2012-06-20
I think you'll need to manually mount it (or add it to fstab), as described in the manual:

[https://www.virtualbox.org/manual/ch04.html#sharedfolders](https://www.virtualbox.org/manual/ch04.html#sharedfolders)

Look under the Manual Mounting > Linux Guest, section.

---

### Post by Morbius1 on 2012-06-20
Yes, you'll have to manually mount it. For the life of me I can't find my notes on how to create the share on the host but it seems you did that part.

To manually mount in the guest the command would look something like this:
```
mount -t vboxsf -o uid=1000 host_shared_folder_name /home/morbius/mount_point
```If you want it to automount the syntax changes in fstab to this:
```
host_shared_folder_name /home/morbius/mount_point vboxsf uid=1000,defaults 0 0
```[COLOR=Blue]*In retrospect it would have been better if you had installed the current version for lucid from the virtualbox web site.*[/COLOR]

---

### Post by RH9R on 2012-06-20
d/l'd the version 4.1 from virtualbox. The install wouldn't proceed due to the existence of the OSE version installed, so I uninstalled the OSE. When I launched the installer, got a dependency error: "Error: Dependency is not satisfiable: libc6 (>= 2.15)"

---

### Post by RH9R on 2012-06-21
Morbius - I realized that since I saw only one download for linux on vbox, that had to be it. Wrong. I found earlier releases (which don't display which version of Ubuntu they're for unless you open them), installed. Sharing is now an option, and I'm fighting w/ the permissions from the two sides.

---

### Post by Morbius1 on 2012-06-21
> Sharing is now an option, and I'm fighting w/ the permissions from the two sidesIt's possible that you are not a member of the right group.

_On the guest:_
Open a terminal and run:
```
sudo gpasswd -a your-user-name vboxsf
```[COLOR=Blue]*Change your-user-name to whatever your user name is on the guest*[/COLOR]
Then logoff and logon again ( on the guest ) for the group membership change to take affect.

---

### Post by RH9R on 2012-06-21
Morbius - 'hard to say how much I appreciate your kind help. I'm out all day, but will do the group add when I get back.
 
Thank You so much!

---

### Post by RH9R on 2012-06-22
Morbius, it worked exactly as you say. 'Can't thank you enough!

---

