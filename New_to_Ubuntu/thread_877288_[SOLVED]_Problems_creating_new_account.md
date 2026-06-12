---
title: "[SOLVED] Problems creating new account"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by mczonie on 2008-08-01
I'm trying to create an unprivileged guest account and keep getting a pop-up saying "Home directory already exists. Please enter a different home directory path." Any idea what this means and how I can fix it? 

TIA.

---

### Post by dca on 2008-08-01
Is this Ubuntu GNOME vers and are you trying to add from the 'System -> Administration -> Users & Groups' app?

---

### Post by dca on 2008-08-01
The last tab on there allows you to give a location of /home for new user if need be unless you're creating a new user w/ same name as yours.

---

### Post by mczonie on 2008-08-01
*Is this Ubuntu GNOME vers *

I have no idea. I'm a total noob and don't even know what "gnome" is, except for that it's some Linux-type thingie.

[I]are you trying to add from the 'System -> Administration -> Users & Groups' app?
[/I]
Yes.

---

### Post by dca on 2008-08-01
The new user you're adding is different than your current username?

---

### Post by mczonie on 2008-08-01
> **dca said:**
> The new user you're adding is different than your current username?

Yes.

---

### Post by dca on 2008-08-01
Lemme' know if this post is similar to what you're encountering

[http://ubuntuforums.org/showthread.php?t=807057](http://ubuntuforums.org/showthread.php?t=807057)

---

### Post by mczonie on 2008-08-01
> **dca said:**
> Lemme' know if this post is similar to what you're encountering

[http://ubuntuforums.org/showthread.php?t=807057](http://ubuntuforums.org/showthread.php?t=807057)

Yup. Exactly.

---

### Post by mczonie on 2008-08-01
OK, I just entered the following command:

```
useradd --home /home/username --shell /bin/bash username
```

When I did it told me "unable to lock password file."

---

### Post by Paqman on 2008-08-01
Your problem is that there's already folders in /home for that user name. Personally i'd just back them up (since you should have a backup somewhere anyway), delete the originals, set up the user account and copy the backups into the fresh account.

---

### Post by mczonie on 2008-08-01
> **Paqman said:**
> Your problem is that there's already folders in /home for that user name. Personally i'd just back them up (since you should have a backup somewhere anyway), delete the originals, set up the user account and copy the backups into the fresh account.

How do I delete them? I don't think I need to back them up, since I think this is a guest account from a previous install, and there was nothing in that guest account I care about anyway.

---

### Post by Paqman on 2008-08-01
Open a terminal and enter:
```

sudo rm -rf /home/username

```
Careful though, this command will totally delete any folder you tell it to, including all contents. Make sure you get the right folder!

---

### Post by mczonie on 2008-08-01
> **Paqman said:**
> Open a terminal and enter:
```

sudo rm -rf /home/username

```
Careful though, this command will totally delete any folder you tell it to, including all contents. Make sure you get the right folder!

So basically I should enter "sudo rm -rf /home/guest" and that will take care of it, right?

---

### Post by cybagorilla on 2008-08-01
yes, you got it ;)

---

### Post by mczonie on 2008-08-01
> **cybagorilla said:**
> yes, you got it ;)

Thanks.

---

### Post by 9paros on 2008-08-02
Thanks too. Wish someday I get a self-confidence with Ubuntu as I used to have with Windows.

---

