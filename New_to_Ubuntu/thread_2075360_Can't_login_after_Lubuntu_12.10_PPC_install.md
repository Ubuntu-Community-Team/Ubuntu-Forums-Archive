---
title: "Can't login after Lubuntu 12.10 PPC install"
date: 2012-10-23
forum: New to Ubuntu
---

### Post by woodt3 on 2012-10-23
I am trying to install lubuntu 12.1 PPC using the alt cd on an ibook g4. I've been having a few problems. First, when lubuntu boots it only boots to a black screen, my cursor is visible and brightness functions work but that's it, no login screen ever comes up. I tried logging in after pressing ctrl+alt+f1 but my login didn't work. I reinstalled thinking maybe I just forgot what password I put, and the problem occurred again, this time yaboot wasn't installed, but it won't even boot to a black screen, and when I try to login using ctrl+alt+f1 it just keeps telling me I have an invalid login despite the fact I know with 100% certainty I am using the correct username and password I entered during install

---

### Post by tejpatel98 on 2012-10-23
I had this same problem with Ubuntu 12.10, and could not login. I ended up going through guest, and resetting my password. Once I logged in, I went into terminal and changed my password. I have not encountered the problem since.

---

### Post by tejpatel98 on 2012-10-23
To change password in terminal, enter the following command.

**passwd**

---

### Post by woodt3 on 2012-10-23
The problem is, I can't login so I can't run any commands.

---

### Post by woodt3 on 2012-10-23
So I reinstalled yet again from the exact same disk and for some reason things seemed to work this time. I am still booting to the black screen, but was able to login with cltr+alt+f1, the problem is after a reboot I'm back to not being able to login.

---

### Post by woodt3 on 2012-10-23
so I booted into single user mode and changed my password so I could login again, then used

```
wget http://mac.linux.be/files/xorg/ibook6.txt
mv ibook6.txt /etc/X11/xorg.conf
```

and now I can see the login screen, but when I login a black screen with some text flashes and then takes me back to the login screen. The text flashes too quickly for me to catch before being returned to the login screen.

EDIT: I am however able to select guest and login without a problem.

EDIT EDIT: could these be perhaps related to the fact that during install I elected to encrypt my home directory? Upon logging in via terminal(?) (ctrl+alt+f1) I am greeted with this error:
keyctl_search: Required key not available perhaps try the interactive 'ecryptfs-mount-private'

trying ecryptfs-mount-private asks me for my login passphrase which I then enter yet keep being told its invalid.

Final edit: ecryptfs-mount-private wanted my original passphrase from install not what I changed it to after dropping into root during single user mode.

---

