---
title: "wireless network forgets passphrase"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by jimmy.on on 2008-10-05
everytime i reboot or turn off my computer it forgets the network passphrase. this only happens on a computer with ubuntu as the only o/s, on another computer i have sharing windows XP and ubuntu i dont have this problem. the setup is a peak router and a tp-link tl-wn321g dongle and connections set to DHCP. the passphrase is WPA

---

### Post by cecure on 2008-10-05
Have you tried using Wicd?  [http://soakedandsoaped.com/articles/read/wicd-a-powerful-network-management-tool-for-ubuntu]("http://soakedandsoaped.com/articles/read/wicd-a-powerful-network-management-tool-for-ubuntu")

---

### Post by garyed on 2008-10-05
I've been using this shell script that I found on one of the forums for a while. Put it in my System>Sessions at start up & wala. There is a little security problem but if your not worried it works. I think you have to something with pam-keyring but if you search these forums you should find the post. Good luck 

I forgot you have to substitute your password for "password"

```

#!/bin/sh
exec echo -n "password" | /usr/lib/libpam-keyring/pam-keyring-tool -u -s

```

---

### Post by jimmy.on on 2008-10-05
i have been looking at cecure's sulution first but you need a program called gnome to set it up. as this is only my second day looking at ubuntu i don't know how to enable this. can you help please

---

### Post by jimmy.on on 2008-10-05
it's ok got that bit but after following the instructions i got error message " W: GPG error: [http://apt.wicd.net](http://apt.wicd.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FEC820F4B8C0755A "

---

### Post by garyed on 2008-10-05
This is the thread I found that worked for me,  [http://ubuntuforums.org/showthread.php?t=463639&highlight=keyring](http://ubuntuforums.org/showthread.php?t=463639&highlight=keyring)
If you don't use auto logon its easy but if you use auto logon there's a
post in there further down that will help.

---

