---
title: "hoary repositories????"
date: 2005-03-03
forum: Repositories &amp; Backports
---

### Post by fengergold on 2005-03-03
i did an upgrade from warty to hoary by changing my repositories sourcelist. i am getting an error when updating (sudo apt-get update)???

this is my current repositories:

deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe 

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse 

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main 
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main 
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main 

deb [http://ubuntu-bp.sourceforge.net/ubuntu/](http://ubuntu-bp.sourceforge.net/ubuntu/) warty-backports main universe  

-----------------------


This is the error i get when i run the update - can somebody help me on this? this is the message after reading the package lists...


W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: You may want to run apt-get update to correct these problems

---

### Post by cka on 2005-03-03
Take the nerim.net lines out of your sources.list file and update the repository list.

Also, it seems hoary-extras is gone.  :(

---

### Post by LongTooth on 2005-03-05
I too recently upgraded to Hoary and received the same error message when updating or adding a package to my system. Not knowing what extra repositories to install when I first upgrade, I used the 'nerim' sources. I've since commented them out and get no error message. But I did keep the 'sourceforge warty-backports' listing. 

Which brings up some questions: In keeping with this post, what extra repositories listings can I use? Or should I just hang tight until something is made available? Also, is there any potential problems keeping the 'sourceforge' listing? 

By the way, this Hoary, while not 'official', is a knock-out. Just absolutely great! I have Gnome 2.9.92. It's as big of a change as 2.8 was from 2.6. When 2.10 is made available this distro will be unbeatable. 

Sorry, I digress. Back to the repositories. Suggestions anyone?

---

### Post by Ubuntu Warrior on 2005-06-22
Also experiencing problems with the nerim repositories. Is there a place on the Ubuntu site where a list of repositories per release is updated so that we know where we stand with these things?

Fully support the positive view on Hoary. We have successfully deployed the release in our business on both servers (currently 6 production) and desktops (12 in production) with astounding results. Keep up the great work!

---

### Post by billiejoex on 2005-06-22
Try this:
```

gpg --gen-key

```

---

