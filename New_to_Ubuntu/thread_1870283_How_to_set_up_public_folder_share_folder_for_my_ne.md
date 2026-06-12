---
title: "How to set up public folder/ share folder for my network?"
date: 2011-10-27
forum: New to Ubuntu
---

### Post by kiwi89 on 2011-10-27
Hi all,

I am a newbie in using Ubuntu, my fren who help me setup my network had giving me a script about how to setup the public folder. But when I try to do myself, I can't successfully set up the public/share folder. Some one can help me see what's wrong with the script pls?


sudo mkdir /media/public
sudo chown $USER:$USER /media/public
sudo echo "gms:/usr/local/share/public /media/public nfs rsize=8192,wsize=8192,timeo=14,intr" >>/etc/fstab
sudo mount -a

I can complete the step until
sudo mount -a

then the error message appear
mount:wrong fs type,bad option superblock on gms:/usr/local/share/public, missing codepage or helper program, or other error (for several filesystems (e.g. ngs, cifs) you might need a /sbin/mount <type> helper program) In some cases useful info is found in syslog - try


very much appreciate if you guys can help me solve this problem.

Thanks.

---

### Post by HermanAB on 2011-10-27
[http://www.aeronetworks.ca/howtos/nfs-howto.html](http://www.aeronetworks.ca/howtos/nfs-howto.html)

---

### Post by kiwi89 on 2011-10-27
> **HermanAB said:**
> [http://www.aeronetworks.ca/howtos/nfs-howto.html](http://www.aeronetworks.ca/howtos/nfs-howto.html)

Hi Herman,

Thanks for your reply.

In fact, can you please write down a new script or point out the mistake that I make in this script?

very much appreciate if you could provide me more guide for this.

Thanks

---

