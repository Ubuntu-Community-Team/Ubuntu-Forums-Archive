---
title: "[SOLVED] SSH/SSL security hole"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by bsharp on 2008-05-13
After reading this story I became worried since I SSH into my server pretty often: [http://it.slashdot.org/it/08/05/13/1533212.shtml](http://it.slashdot.org/it/08/05/13/1533212.shtml)

I was wondering if this hole had been fixed, and after running a quick update I noticed that libssl has been upgraded, so I am assuming that it has, but I just wanted to check here just in case.

---

### Post by Monicker on 2008-05-13
An update is available, and it is possible you already have it via the Update Manager.

[http://www.ubuntu.com/usn/usn-612-1]("http://www.ubuntu.com/usn/usn-612-1")
[http://www.ubuntu.com/usn/usn-612-2]("http://www.ubuntu.com/usn/usn-612-2")

Edit: Above link was recently updated with details for regenerating ssh keys.



The following paragraphs are rather important, even if you have the update.

[I]All OpenSSH and X.509 keys generated on such systems must be considered untrustworthy, regardless of the system on which they are used, even after the update has been applied. 

This includes the automatically generated host keys used by OpenSSH, which are the basis for its server spoofing and man-in-the-middle protection.[/I]

To be truly protected, you need to regenerate your ssh keys after getting the update.

This thread has some good information:  [http://ubuntuforums.org/showthread.php?t=792881]("http://ubuntuforums.org/showthread.php?t=792881")

---

### Post by bsharp on 2008-05-13
All right! Thanks

---

### Post by MikeBenza on 2008-05-13
Note: the security updates have not been pushed to all mirrors yet.  Update from the main Ubuntu site.

---

### Post by mister_pink on 2008-05-13
Did the update automatically cause new keys to be generated? Just want to check I don't need to manually change them. It does seem to have done (based on complaints when I ssh in and modification times of the key files).

---

### Post by Monicker on 2008-05-13
> **mister_pink said:**
> Did the update automatically cause new keys to be generated? Just want to check I don't need to manually change them. It does seem to have done (based on complaints when I ssh in and modification times of the key files).

Yes, it updated the keys on my system. I had checked the timestamps before and after.

---

### Post by bodhi.zazen on 2008-05-13
You can check your keys with ssh-vulnkey

To install :

```
sudo apt-get update
sudo apt-get dist-upgrade #apt-get upgrade will not upgrade your packages
```

Then 

```
sudo ssh-vulnkey -a
```

---

### Post by Tarrantella on 2008-05-15
Hi folks,

Be careful upgrading. Having just done this I am having problems with dependencies and apt-get is now refusing to download packages due to the update to libssl. libpq is one that has been hit.

Regards,
T

---

### Post by bodhi.zazen on 2008-05-15
> **Tarrantella said:**
> Hi folks,

Be careful upgrading. Having just done this I am having problems with dependencies and apt-get is now refusing to download packages due to the update to libssl. libpq is one that has been hit.

Regards,
T

Ouch - You should file a bug report :

How to : [http://ubuntuforums.org/showthread.php?t=284595](http://ubuntuforums.org/showthread.php?t=284595)

---

