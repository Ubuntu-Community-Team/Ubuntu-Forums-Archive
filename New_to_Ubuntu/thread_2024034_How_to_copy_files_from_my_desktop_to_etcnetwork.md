---
title: "How to copy files from my desktop to /etc/network?"
date: 2012-07-13
forum: New to Ubuntu
---

### Post by User1101 on 2012-07-13
I am using ubuntu 12.04. I am trying to copy certain files form my desktop to /etc/network so that iptables can configure it self at system startup. But i get an error: Error opening file 'iptablessave' permission denied.
 
I finaly made the file in the correct posision with the terminal command: pico. Anyway now i also see i cant create new documents or folders anywhere in my root. I am the system administrator. I have the same problem with linux mint 13.
 
How do i fix this so that i can copy my files to where i please without having to use the terminal? :confused:
 
NOTE: i choose to encrypt my home folder and use a password to login on both Ubuntu and Linux Mint 13... Maby this has something to do with it. I am also dual booting them...
 
Thanks... ](*,)

---

### Post by mapes12 on 2012-07-13
Use Nautilus with sudo permission. Launch it in Terminal like this ```
gksu nautilus
```It will ask for your password then the GUI will launch. Clearly, you need to be careful what files you change and move around.

If you need to delete anything then be sure to hold down the Shift key at the same time as pressing del otherwise you will fill roots trash with rubbish. Holding down Shift permanently deletes.

---

### Post by roijac on 2012-07-13
use sudo cp

---

### Post by Kopkins on 2012-07-13
As the others said, you need root privileges to modify certain directories, /etc is one of them. So either use:
```
gksu nautilus
```
 OR 
```
sudo cp /source/files /destination/folder
```
to copy the files you need. 

Best of luck,
Kopkins

---

