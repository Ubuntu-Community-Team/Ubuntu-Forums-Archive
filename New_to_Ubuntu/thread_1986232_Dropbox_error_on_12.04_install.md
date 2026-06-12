---
title: "Dropbox error on 12.04 install"
date: 2012-05-24
forum: New to Ubuntu
---

### Post by Wheel on 2012-05-24
After a clean install of 12.04, I installed Dropbox to recapture all the stuff I have synced there.
I installed via Software Center, which kicked me over to Dropbox's website where I used the terminal method to install (64 bit version).
All seemed to go well.  Everything synced properly.
But I see an error message in the terminal about user sharing.

Is this something I need to worry about?
If so, how do I go about "enabling user sharing"?

This is the content of the terminal message:

joe@joe-XPS-8300:~$ ~/.dropbox-dist/dropboxd
/usr/bin/nautilus
Initializing nautilus-dropbox 0.7.1
Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Shutting down nautilus-gdu extension

^C
joe@joe-XPS-8300:~$

---

### Post by Wheel on 2012-05-25
Bump

---

### Post by kc1di on 2012-05-25
> **Wheel said:**
> Bump

for some reason it's looking for samba,
Try installing samba if it's not already installed.
or delete the file in Dropbox that requires samba share.

---

### Post by Dragonbite on 2012-05-25
Somewhere there should be a setting that turns on file sharing (even if you don't actually share anything).  Try right-clicking on some folder and elect "sharing" to see if that pre-configures what Dropbox is looking for?

---

### Post by trivialpackets on 2012-05-25
I tried installing from the software center and it also seemed to be problematic for me on a fresh install of 12.04.  I found that the safest measure for me at the time was to just uninstall it and then download and install from the web site.

---

### Post by matt_symes on 2012-05-25
Hi

> Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory

That message is not a Dropbox message but a Nautilus message and is not a problem in your case as you are not using Samba.

I used to get it while starting Nautilus from the command line IIRC.

Kind regards

---

### Post by Wheel on 2012-05-25
> **matt_symes said:**
> Hi



That message is not a Dropbox message but a Nautilus message and is not a problem in your case as you are not using Samba.

I used to get it while starting Nautilus from the command line IIRC.

Kind regards


Thanks for that.

In the past half hour or so, I installed Samba to see if that would do anything.  It didn't seem to.

I read up a bit on sharing and this didn't seem applicable to me.

I created some content and jumped over to my Win 7 install.  It synced normally.

I just returned from the Dropbox forum, where I posted this same question.

I am now going to uninstall Samba since I have no particular use for it.

Thanks to all for your comments.

---

