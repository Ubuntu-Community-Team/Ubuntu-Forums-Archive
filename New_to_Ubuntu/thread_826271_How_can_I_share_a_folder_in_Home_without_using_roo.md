---
title: "How can I share a folder in Home without using root."
date: 2008-06-11
forum: New to Ubuntu
---

### Post by philinux on 2008-06-11
Says i don't have privileges to create a share. Dang. 

New territory. :)

---

### Post by Darkade on 2008-06-11
You might want to have a look to this thread
[http://ubuntuforums.org/showthread.php?t=772706](http://ubuntuforums.org/showthread.php?t=772706)

---

### Post by philinux on 2008-06-12
Tried this but in my vbox os the folders contents are only root access.

And even with root I cant access them!

---

### Post by forger on 2008-06-12
we'll need some more details:
1) you're trying to do what?
2) what are you using?
3) is this ubuntu as a guest operating system in virtualbox or..?
4) which version/release of ubuntu?
5) what folders do you want to share?

---

### Post by philinux on 2008-06-12
> **forger said:**
> we'll need some more details:
1) you're trying to do what?
2) what are you using?
3) is this ubuntu as a guest operating system in virtualbox or..?
4) which version/release of ubuntu?
5) what folders do you want to share?

Thanks this is new territory for me.

1. Got a folder in home - click share tab which installed samba and ticked the option to share. This is so I can see these files from my vbox guest which will be ubuntu intrepid. Testing.
2. Host Ubuntu 8.04 Guest 8.04 waiting to upgrade to test intrepid alpha.
3. Yes
4. See 3.
5. One folder in /home called documents.

---

### Post by forger on 2008-06-12
You're trying to share a folder located in host and see it from a virtual guest in virtualbox? I don't think you need samba for that, you can try to install the virtualbox guest additions.

Download the user manual
> 
[http://virtualbox.org/wiki/Downloads](http://virtualbox.org/wiki/Downloads)
[http://virtualbox.org/download/1.6.2/UserManual.pdf](http://virtualbox.org/download/1.6.2/UserManual.pdf)
read page 57 (4.5 Folder sharing)

(or check out the attachment)

otherwise, i'm not really sure, I use kvm for gnu/linux and *bsd virtualization:
[https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

---

### Post by meltindar on 2008-06-12
6) So what are your permissions on this folder? 
If you are using Samba I think you have to be the owner or at least have write permissions.

---

### Post by philinux on 2008-06-12
> **meltindar said:**
> 6) So what are your permissions on this folder? 
If you are using Samba I think you have to be the owner or at least have write permissions.

I used the additions to mount the folder and the files were locked to root too, so I thought I try samba.

See attached screenshots first from host. I'll have to log in the guest and edit the post to show the other - hang on.

---

### Post by philinux on 2008-06-13
Bump.

Any method that works is fine with me.

---

### Post by ukripper on 2008-06-13
Only way i can think of is either you add your username and group to sudoers (but you will still need root access to do that) or use chown or chmod (but again you still need root access in any case) however, that would be only once you need to be root.

By the way why you need to to do this if you dont mind asking.

---

### Post by philinux on 2008-06-13
See post 5.

I'm not sure I'm doing this right anyway.

Ubuntu is the main OS. Got ubuntu intrepid as a guest OS in Virtualbox.

All I need is a common folder to share files.

---

### Post by Golem XIV on 2008-06-13
Well, hopefully this will help, since it's how I did it:
```
sudo apt-get install nautilus-gksu
```
to get the gksu plug-in for Nautilus, or alternatively **gksu nautilus**
Navigate to the directory above the one you want to share;
<note> Nautilus-gksu is a bit buggy and may open 2 windows, apparently only one is a root window.  I just closed one and the other worked, but I've seen complaints about this elsewhere. </note>
right click on the directory you want to share and select "sharing options"
It will ask to install Samba, do so
It will ask to modify permissions, do so
I think you may need to reboot or at least restart Samba for it to work, though.

---

### Post by philinux on 2008-06-14
The problem I have is when I start up my guest in virtualbox, the files in the shared folder are all locked and have root permission. Even using gksu nautilus in the guest fails to access them.

However I've found a solution.

Managed to get usb working in the guest and can now use my usb stick as the go between.

---

