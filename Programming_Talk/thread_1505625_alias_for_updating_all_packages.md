---
title: "alias for updating all packages"
date: 2010-06-09
forum: Programming Talk
---

### Post by cajunlibra on 2010-06-09
I created the following alias by hand and it gave me an error:

alias updater='sudo apt-get update | apt-get upgrade | apt-get autoclean | apt-get autoremove'

Error: 
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
E: Could not open lock file /var/cache/apt/archives/lock - open (13: Permission denied)
E: Unable to lock the download directory
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
[sudo] password: 

Entering my password does nothing.

How can I make this work?
Thanks

---

### Post by diesch on 2010-06-09
This runs *sudo apt-get update* feeds its output into *apt-get upgrade* (without sudo).

Use
```
 sudo sh -c 'apt-get update; apt-get upgrade; apt-get autoclean; apt-get  autoremove'
```

---

### Post by nvteighen on 2010-06-09
> **diesch said:**
> This runs *sudo apt-get update* feeds its output into *apt-get upgrade* (without sudo).

Use
```
 sudo sh -c 'apt-get update; apt-get upgrade; apt-get autoclean; apt-get  autoremove'
```

I would avoid placing the sudo in the alias definition. Following Python's philosophy, explicit is better than implicit... specially with regards to sudo and other similar root-privileges granting programs. That way you'll always know when you're root and when not; no, you may sometimes forget that works using sudo.

It's just about being aware what one does with one's own computer.

---

### Post by diesch on 2010-06-09
For me an alias is just a shortcut to avoid typing the same things over and over again. As *sudo* asks for the password in any case I don't see a problem here.

---

### Post by nvteighen on 2010-06-09
> **diesch said:**
> As *sudo* asks for the password in any case I don't see a problem here.

No, it doesn't if the timeout is set and you didn't do sudo -k. But well, it's not going to be a super security risk either.

---

### Post by Tony Flury on 2010-06-09
> **cajunlibra said:**
> I created the following alias by hand and it gave me an error:

alias updater='sudo apt-get update | apt-get upgrade | apt-get autoclean | apt-get autoremove'

Error: 
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
E: Could not open lock file /var/cache/apt/archives/lock - open (13: Permission denied)
E: Unable to lock the download directory
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
[sudo] password: 

Entering my password does nothing.

How can I make this work?
Thanks

The reason it did not work initially is that you used the "|" pipe - which runs each command as a seperate process and streams the output of one process into the input of the next - and since all those apt-get's run at the same time under your command, each one tries to lock the file - and only the first one that starts up is able to lock it - and the rest generate an error. To get this working you should use the ";" (semicolon) as diesch suggested - this will run each command when the previous one completes - which i am fairly sure that is what you intended.

---

