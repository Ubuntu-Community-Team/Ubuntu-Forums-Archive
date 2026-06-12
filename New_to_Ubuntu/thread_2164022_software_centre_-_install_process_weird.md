---
title: "software centre - install process weird?"
date: 2013-07-20
forum: New to Ubuntu
---

### Post by alphalvr on 2013-07-20
hi,
 
well im trying to play with this new ubuntu toy and im a little confused by the software centre.

For instance if i try to install vlc player...

1. i select it in the software centre and press `install`
2. enter my authorisation code
3. i am informed that software is untrusted, i select `ok`, it repeats message like 5 times, i click `ok` 5 times.
vlc hasnt installed??

then i try again , everythings exactly the same but this time i select `repair` 5 times rather than `ok` and vlc installs, is that right? it didnt feel right.

i just repeated the exact same steps to install `chromium` - choosing repair to install something?? cant be right??

also that install process seemed to bring my pc to its knees

regards

---

### Post by alphalvr on 2013-07-20
ok i decided to try updating (i have no idea what im doing but i try)

so in a terminal i type  -  sudo apt-get upgrade

and i get this....

justin@Ubuntu-Phoenix:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:  THIS IS A LONG LIST

followed by

134 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,437 kB/119 MB of archives.
After this operation, 3,367 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Err [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) raring-updates/main libssl1.0.0 amd64 1.0.1c-4ubuntu8.1
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) raring-security/main libssl1.0.0 amd64 1.0.1c-4ubuntu8.1
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) raring-updates/main plymouth-label amd64 0.8.8-0ubuntu6.1
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) raring-security/main libdbus-1-3 amd64 1.6.8-1ubuntu6.1
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) raring-updates/main plymouth amd64 0.8.8-0ubuntu6.1
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) raring-updates/main libplymouth2 amd64 0.8.8-0ubuntu6.1
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl1.0.0_1.0.1c-4ubuntu8.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl1.0.0_1.0.1c-4ubuntu8.1_amd64.deb)  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/d/dbus/libdbus-1-3_1.6.8-1ubuntu6.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/d/dbus/libdbus-1-3_1.6.8-1ubuntu6.1_amd64.deb)  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/p/plymouth/plymouth-label_0.8.8-0ubuntu6.1_amd64.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/p/plymouth/plymouth-label_0.8.8-0ubuntu6.1_amd64.deb)  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/p/plymouth/plymouth_0.8.8-0ubuntu6.1_amd64.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/p/plymouth/plymouth_0.8.8-0ubuntu6.1_amd64.deb)  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)

im sure somethings not right, i dont know why, just a feeling :)

oh i tried searching the net for the error, nothing came up

---

### Post by Cheesemill on 2013-07-20
It looks like apt-get is having networking problems. Is this machine connected to the internet?

---

