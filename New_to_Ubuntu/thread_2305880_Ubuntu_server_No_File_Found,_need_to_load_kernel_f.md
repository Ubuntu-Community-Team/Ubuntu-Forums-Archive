---
title: "Ubuntu server No File Found, need to load kernel first"
date: 2015-12-10
forum: New to Ubuntu
---

### Post by Abdul_Anafi on 2015-12-10
I really in need of help, this morning i find out that my server is accidentally shutdown due to electrical problem in my office.
the server consist of several VM that running on Proxmox VE, some of the server survived and can go live again,

but one problem came, i have 500GB Filesharing using Ubuntu Server 12.04, when i tried to turn it live, the screen says like this picture bellow,

See post below.

then i click ubuntu with (recovery mode), then this show up

See post below.

iam very new on Ubuntu or Grub, could anyone save me, its really frustating because the file server hold so many data in it.

thanks in advance for you help



this is the url Ubuntu pastebin for my server

[http://paste.ubuntu.com/13889442/](http://paste.ubuntu.com/13889442/)

please help me, thanks in advance

---

### Post by matt_symes on 2015-12-12
Hi

I have attached your images to this post. 

Please attach any images to the Ubuntu forums directly.

[ATTACH=CONFIG]266105[/ATTACH][ATTACH=CONFIG]266106[/ATTACH]

Kind regards

---

### Post by sandyd on 2015-12-12
Linux Kernel that is required to boot may be corrupt.

That being said, may be that it is only that kernel version.

Choose 'Previous Linux Versions', and go through whats there. See if any of them boot.

If none of them boot, boot from a livecd, and you can recover files from the livecd before reinstalling.

---

