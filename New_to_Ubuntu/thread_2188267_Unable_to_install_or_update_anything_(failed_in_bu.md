---
title: "Unable to install or update anything (failed in buffer_read(fd) error)"
date: 2013-11-16
forum: New to Ubuntu
---

### Post by arjuns.iisc on 2013-11-16
Whenever I try to update or install any package I get the following error:

arjun@ubuntu:/var/lib/dpkg/info$ sudo apt-get install --reinstall linux-headers-2.6.32-38-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 66 not upgraded.
Need to get 793kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main linux-headers-2.6.32-38-generic 2.6.32-38.83 [793kB]
Fetched 793kB in 27s (28.6kB/s)                                                
(Reading database ... 55%dpkg: unrecoverable fatal error, aborting:
 failed in buffer_read(fd): files list for package `linux-headers-2.6.32-38': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)


I noticed that there have been others who faced similiar problems with other packages (threads [here]("http://ubuntuforums.org/showthread.php?t=1073380") and [here]("http://ubuntuforums.org/showthread.php?t=1274061")). However, none of the methods mentioned there seem to work for me. Can somebody kindly tell me how to get over this without doing a fresh installation of ubuntu?

Regards,
Arjun

---

### Post by mörgæs on 2013-11-16
Hi, welcome to the fora.

Kernel 2.6.32 indicates Ubuntu 10.04, which is out of support (for the desktop). 
Have you thought of a fresh install of a newer release?

---

### Post by philinux on 2013-11-16
This should help.[http://askubuntu.com/questions/182991/software-install-failure](http://askubuntu.com/questions/182991/software-install-failure)

I'm running a 10.04 box and still receiving the server security updates ok.

---

### Post by arjuns.iisc on 2013-11-22
@morgaes: I have had to spend quite some time to install my tools in this version of ubuntu. I am also not sure whether the tools I use will work on the newer version of ubuntu. Hence, given the choice I would like to continue using this version for at least another year.

@philinux: Thanks a lot! Will try the steps in the link and post the updates on this thread!

---

### Post by newb85 on 2013-11-22
I'm no security guru, but I'm pretty sure server security updates are insufficient for a desktop system.  Updates are also issued to take care of vulnerabilities in other components of your system.  (And I'm sure that you all use something in the desktop component that interfaces with the internet, like a browser, an email client, a media player that searches for song information, etc.)

---

### Post by ian-weisser on 2013-11-22
One explanation of the exact error message is at [http://administratosphere.wordpress.com/2010/08/16/dpkg-fails/](http://administratosphere.wordpress.com/2010/08/16/dpkg-fails/)

Good solution there, too.

---

### Post by arjuns.iisc on 2013-11-24
@philinux: Yes the steps mentioned in your link worked for me. Thanks a  lot! I guess I can throw away that Linux Mint DVD that I prepared some  time back.
@ian-weisser: Thank you for the link

---

### Post by philinux on 2013-11-24
I would consider upgrading the OS as I'm going to on my old box soon.

---

