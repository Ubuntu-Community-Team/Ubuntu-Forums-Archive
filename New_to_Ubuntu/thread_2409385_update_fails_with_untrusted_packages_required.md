---
title: "update fails with untrusted packages required"
date: 2019-01-01
forum: New to Ubuntu
---

### Post by twizzard on 2019-01-01
When I try to update my Ubuntu 16.04 I get a message that untrusted packages are required. I tried the solution in the forum that needed 
> sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 56A3DEF863961D39

but I now get an error
 The following signatures couldn't be verified because the public key
 is not available: NO_PUBKEY A8AA1FAA3F055C03

Help?

---

### Post by twizzard on 2019-01-01
Tried searching the forums, only got errors that I was not allowed to search. Used Google, looking for A8AA1FAA3F055C03 site:ubuntuforums.org. Found thread that said to use
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A8AA1FAA3F055C03
Then I returned to the original thread by 1fallen, and ranusing terminal
> sudo apt update
then 
> sudo apt update
sudo apt full-upgrade
sudo apt autoremove

and it seemed to succeed.Now when I run the standard graphical software update it says my system is up to date.

---

### Post by overdrank on 2019-01-01
Under thread tools you can choose to mark solved.

---

