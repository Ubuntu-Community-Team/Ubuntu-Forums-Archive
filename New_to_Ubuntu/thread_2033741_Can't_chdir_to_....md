---
title: "Can't chdir to ..."
date: 2012-07-26
forum: New to Ubuntu
---

### Post by mrhazzy on 2012-07-26
So I was trying to install ttdnsd ([www.mulliner.org/collin/ttdnsd.php](www.mulliner.org/collin/ttdnsd.php)) from the source file since it has not been packaged and I run into a problem. I've compiled the program and when I try and run via the terminal...

(I've basically just installed this a day or two ago and I'm realising the steep learning curve)

[
root@ubuntu:/home/username# '/usr/local/src/ttdnsd' 
can't open ttdnsd.conf
can't open resolvers file ttdnsd.conf, try again after chroot
root@ubuntu:/home/username# can't chdir to /var/run/ttdnsd,
]

If I am executing as root, why cant I change directory to /var/run/ttdnsd ?

I have no idea where to go after this, I'm running Ubuntu (The latest one) via VmWare so I guess I could afford to mess about a bit but I don't want to damage anything internally. 

Any help and suggestions would be gladly appreciated!

---

### Post by lisati on 2012-07-26
As an aside, "root" is usually disabled in Ubuntu. Have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by mrhazzy on 2012-07-26
Yeah I had to enable it to compile the source code. I was getting close to nowhere without it. 

Any suggestions? Please let me know if you need more information

---

### Post by mrhazzy on 2012-07-27
Anyone?

---

### Post by steeldriver on 2012-07-27
> If I am executing as root, why cant I change directory to /var/run/ttdnsd ?Does /var/run/ttdnsd actually exist? it may not be a permissions problem at all...

I have no idea what you are trying to do - your post is confusing (are you running those commands interactively? or is it some kind of script?) but my guess would be

(1) /usr/local/src/ttdnsd can't find the conf file

(2) because of (1) the service / daemon doesn't start

(3) because of (2) there is no /var/run/ttdnsd

(4) the script is not recovering well from the errors

---

