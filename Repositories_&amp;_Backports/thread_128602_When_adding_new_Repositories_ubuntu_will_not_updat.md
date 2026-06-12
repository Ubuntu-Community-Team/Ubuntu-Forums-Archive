---
title: "When adding new Repositories ubuntu will not update."
date: 2006-02-11
forum: Repositories &amp; Backports
---

### Post by the_duce on 2006-02-11
I added new Repositories last night it updated just fine, but now it will not update.

---

### Post by eriefisher on 2006-02-11
What did you add?
Did you backup your souces.list first?
Are you getting any errors?
Can you remove the new repo and update?
Are you using synaptic reload or apt-get update?

eriefisher

---

### Post by the_duce on 2006-02-11
I'm using apt-get. I even tried the recommended ones on top of this page and apt-get just stalls. P.S I believe it could something with Actiontec DSL Modem.


I meant the repositories on the top page of this forum.

---

### Post by aysiu on 2006-02-11
Yes, please be specific.

What did you have before? What do you have now? What errors are you getting?

---

### Post by the_duce on 2006-02-11
they're no errors it just stalls.
P.S It could be the DSL Modem I have the ISP here trying to fix it a lot times.


when I've got the default repositories it update just fine.

---

### Post by eriefisher on 2006-02-11
So this is a connection problem and not a repo or OS problem. If the connection is bad you should get a message stating that it could not connect to the repos.
Process of elimination I guess.

eriefisher

---

### Post by the_duce on 2006-02-11
Whoops, Sorry for being an Idiot.

---

### Post by the_duce on 2006-02-12
It did give connetion warnings I just didn't let it go all the way through. I reinstalled 
Ubuntu last night, and it update just fine but I tried it five minuets ago it gave me this warning:

Reading package lists... Done
W: GPG error: [http ://security.ubuntu.com](http ://security.ubuntu.com) breezy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signin g Key <ftpmaster@ubuntu.com>

---

### Post by AgenT on 2006-02-12
If you have the correct GPG key and are still having problems this **fix** should help.

There's some weird glitch where residual info hangs out and gives you a GPG signature error. If that's the case, do this: 
Back up the sources.list with this command: ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup 
``` Then edit the sources.list by typing ```
sudo gedit /etc/apt/sources.list
``` and delete everything. 
```
 sudo apt-get update 
```with your empty repositories list. 
Finally, ```
sudo cp /etc/apt/sources.list_backup /etc/apt/sources.list
``` ```
sudo apt-get update
``` [Source]("http://www.psychocats.net/linux/sources.php")

---

### Post by gpeck157 on 2006-02-13
Thank you AgenT! I've been ripping my hair out over this for the last couple of days. This worked!

G

---

