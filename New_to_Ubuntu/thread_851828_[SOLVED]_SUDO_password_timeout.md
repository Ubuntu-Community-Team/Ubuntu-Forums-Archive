---
title: "[SOLVED] SUDO password timeout"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by alienexplorers on 2008-07-07
Is there a way to increase the timeout period for the sudo password.  I find I am trying to do some things in Ubuntu and I enter the sudo password and several minutes later I have to answer it again.

---

### Post by iaculallad on 2008-07-07
> **alienexplorers said:**
> Is there a way to increase the timeout period for the sudo password.  I find I am trying to do some things in Ubuntu and I enter the sudo password and several minutes later I have to answer it again.

On your terminal:

```
sudo visudo
```

then look for the "Defaults" text inside the configuration file, if you can't find one, insert the line of texts below to you end part of your sudoers file.

> Defaults passwd_timeout=10

Giving it a 10 minutes delay.

Save file.

PS: If "Defaults" exist, just add **passwd_timeout=10** separated by a comma from the latter.

i.e:

> Defaults syslog=auth,passwd_timeout=10

---

### Post by bapoumba on 2008-07-07
> **alienexplorers said:**
> Is there a way to increase the timeout period for the sudo password.  I find I am trying to do some things in Ubuntu and I enter the sudo password and several minutes later I have to answer it again.

Either you get a [root shell]("https://help.ubuntu.com/community/RootSudo#Special%20notes%20on%20sudo%20and%20shells") which is not officially recommended or you tweak the [sudoers file]("http://linux.die.net/man/5/sudoers") and change the passwd_timeout variable.

```
passwd_timeout
    Number of minutes before the sudo password prompt times out. The default is 5, set this to 0 for no password timeout. 
```

[More]("http://ubuntuforums.org/showthread.php?t=765414").

---

### Post by jward3010 on 2009-07-11
I think this is the right place to post this problem. I set up a few tasks the other night - something as follows:
```
sudo apt-get update   &&   sudo apt-get upgrade   &&   sudo apt-get install "several packages"   &&   sudo apt-get autoclean   &&   sudo poweroff
```

I wanted them to all complete through the night while I was resting my weary eyes but the only problem is the "sudo apt-get upgrade" or possibly the "sudo apt-get install XXXXX" we're going to take longer than the 10 minutes allowed for sudo privileges that by the time the job got to "autoclean" or "poweroff" I would need to enter the password again, that could very well have been 3AM, and for that reason the machine may not have shutdown (I'd prefer if it would as it's a hot running laptop). How can I get around this without doing a:
```
sudo su
```
Or is that the only way around this.

---

### Post by utnubuuser on 2009-10-04
in terminal > sudo nano /etc/sudoers

use the arrow keys to navigate to the line that says:>  #%sudo ALL=NOPASSWD: ALL
 

and remove the hash-mark/pound(number sign) at the beginning of the line.

type Cntrl+x (that's the control button and x at the same time), answer y then enter.  Now you'll only need to enter sudo at the start of your session.

---

