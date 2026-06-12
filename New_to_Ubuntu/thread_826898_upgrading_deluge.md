---
title: "upgrading deluge"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by Falc7 on 2008-06-12
I downloaded the .deb file from the website, but when i try install it tells me: An older version is avaliable in the software channel, pleasse try to use this. 

Since i don't want to use the older version i want to use the newer version i click install. It then says installation finished, failed to install package deluge....
How can i do it? Should i uninstall older deluge version first?

---

### Post by the_doc on 2008-06-12
Maybe the newer version isn't supported yet, in which case it's probably better to use the older one.

---

### Post by pjnsmb on 2008-06-12
How can i do it? Should i uninstall older deluge version first?

I am using 0.5.9.1 after deleting the older version first, via synaptic, .........

best to do it that way.

---

### Post by kpkeerthi on 2008-06-12
Create a folder **deluge **under your home folder.
Download the two deb files to the folder **deluge **you created above.
Open a terminal and type
```
cd ~/deluge
```
```
sudo dpkg -i *.deb
```

After the installation finishes, you may delete the .deb files.

---

### Post by bumanie on 2008-06-12
I can assure you that the latest deluge (0.5.9.1-1) is supported, because I have installed it in 8.04, and it works. Try as above post suggests. If that still brings up errors, download again, in case something went astray during the download.

---

### Post by Falc7 on 2008-06-12
Thanks guys all fixed, i redownloaded, uninstalled old version, and ran the code

---

