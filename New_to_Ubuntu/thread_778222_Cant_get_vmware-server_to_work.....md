---
title: "Cant get vmware-server to work...."
date: 2008-05-01
forum: New to Ubuntu
---

### Post by Ducatiboy-stu on 2008-05-01
I am trying to install vmware-server, but having no luck..with hardy 8.04

I am wanting to do this --> [http://www.venturecake.com/a-simple-guide-to-using-your-existing-windows-install-apps-in-ubuntu/](http://www.venturecake.com/a-simple-guide-to-using-your-existing-windows-install-apps-in-ubuntu/)

I cant seem to find it the repo's using add/remove applications.

I downloaded the .rpm file and converted it to .deb with alien

Then installed with synaptic..(even burnt a CD and tried it )

Get the following error, even if i browse into the vmware dir's

myname@myname-laptop:~$ vmware
/usr/bin/vmware: 166: cannot open /etc/vmware/locations: No such file
exec: 180: /lib/wrapper-gtk24.sh: not found
mynamet@myname-laptop:~$ 


Any ideas...or help....

Thanks

---

### Post by spiderbatdad on 2008-05-01
vmware-server is no longer included in the repos. Converting rpm's is not always successful. If you can find a tar, it would be a better start. I believe vmware.com only provides the workstation for free...the server on a trial basis. 

Many Ubuntu users are now using virtual-box.

---

### Post by Victormd on 2008-05-01
I would suggest using virtual box versus vmware. However, not the one in the repos'. Go to [www.virtualbox.org](www.virtualbox.org) but don't download the OSE version as there is no USB support. Download the free version, just not OSE...

---

### Post by Ducatiboy-stu on 2008-05-01
Will try the .tar.gz version of Vmware

Have treid Virtualbox...but keep  getting a kernel error msg..

The reason I wanted to use vmware-server is that I can use my existing XP setup of my existing HD partition...basically vmware-server should ( I hope ) boot of the HD thru Grub...( but I was warned never to let ubuntu start in VM as it will eat itself )

---

### Post by spiderbatdad on 2008-05-01
I could be wrong, but I don't think you can do what you're trying to do. My experience with vmware-server was to start it after my linux OS was running and the select the OS I wanted to run inside the server. Additionally, each OS on the virtual host had to be installed on the host. In the case of XP a product key is necessary.

---

