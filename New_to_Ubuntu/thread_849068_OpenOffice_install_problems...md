---
title: "OpenOffice install problems.."
date: 2008-07-04
forum: New to Ubuntu
---

### Post by inevaexisted on 2008-07-04
Hi all,

After successfully getting hardy heron up and running, I decided to have a look at the other packages on offer via 'add/remove..' all went well till I noticed that one of the extra packages for openoffice seemed to have stalled while trying to install...

> Adding extension /usr/lib/openoffice/share/extension/install/writer2latex.uno.pkg...

Upon trying to do an update though. The update manager tells me to run  > 'dpkg --configure -a'  in terminal.


However when I do that it tries to install again and just like before doesnt complete..

A little googling led me to launchpad that revealed this bug is to be rectified in the .1 (point)release of 8.04 however since this very problem is preventing the update manager from updating I cant see how it will work less I 'clear the package queue'

Any help would be much appreciated.

Ineva.

---

### Post by bumanie on 2008-07-04
You need to do > sudo dpkg --configure -a It needs admin rights for that operation. The download should start from the point it was interrupted.

---

### Post by ramjet_1953 on 2008-07-04
Copy and paste these commands, one at a time into a terminal and execute them by entering a CR at the end:

 [COLOR="Red"]sudo cp /var/lib/dpkg/status /var/lib/dpkg/status-broken[/COLOR]

 [COLOR="Red"]sudo cp /var lib/dpkg/status-old /var/lib/dpkg/status
[/COLOR]
 [COLOR="Red"]sudo apt-get install -f[/COLOR]

Hopefully this will fix things.

Regards,
Roger :cool:

---

### Post by inevaexisted on 2008-07-04
> **ramjet_1953 said:**
> Copy and paste these commands, one at a time into a terminal and execute them by entering a CR at the end:

 [COLOR="Red"]sudo cp /var/lib/dpkg/status /var/lib/dpkg/status-broken[/COLOR]

 [COLOR="Red"]sudo cp /var lib/dpkg/status-old /var/lib/dpkg/status
[/COLOR]
 [COLOR="Red"]sudo apt-get install -f[/COLOR]

Hopefully this will fix things.

Regards,
Roger :cool:

Nope no luck there... back to square one follows is the output after the 'sudo apt-get install -f'

> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 43 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up openoffice.org-writer2latex (0.5-6) ...
Adding extension /usr/lib/openoffice/share/extension/install/writer2latex.uno.pkg...


also a side note.. it wouldn't let me run those commands from any dir. particularly on the second command(gave some excuse about /var/lib/dpkg/status not being a directory - which it isnt.). I had to make /var/lib/dpkg my working folder to do the copies.
```


 [COLOR="Red"]sudo cp ./status .status-broken[/COLOR]

 [COLOR="Red"]sudo cp ./status-old ./status
[/COLOR]
 [COLOR="Red"]sudo apt-get install -f[/COLOR]
```

Thanks anyway.. anything else I can try..

---

