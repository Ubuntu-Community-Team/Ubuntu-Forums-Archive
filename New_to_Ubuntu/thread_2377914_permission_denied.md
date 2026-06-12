---
title: "permission denied"
date: 2017-11-17
forum: New to Ubuntu
---

### Post by berno94 on 2017-11-17
I'm trying to install vesta vesta server in my PC but i always get permission denied when I entered the right password. ssh [email]root@your.server[/email](Ssh root@192.168.0.13) when he asked me for the password I put the password but he kept saying that permission denied and password, public key. Can someone help me solve this mystery please.

---

### Post by Bucky Ball on 2017-11-18
Welcome. Are you following a tutorial or 'how-to' to do this? If so, please post a link to it here.

Also, please let us know which Ubuntu release and flavour you are running. [This link is older]("https://www.digitalocean.com/community/tutorials/how-to-install-vestacp-and-set-up-a-website-on-ubuntu-14-04") as it's for 14.04 LTS, but looks like it might be close to what you are trying to do. Take note of the prerequisites. Are you running a Ubuntu server? Do you have Filezilla installed? Does your system meet all other prerequisites listed there?

* Update: but maybe it's simpler than that now. Have a[ look at this link]("http://www.ubuntuboss.com/installing-and-configuring-vesta-control-panel-in-ubuntu16-04/") for installing on 16.04 LTS.

---

### Post by berno94 on 2017-11-18
Yes, I've a unbutu server installed.No, I don't have filezila install in my server and my system meets all the requirements. I tried to follow ur link u but the system said that "curl-0 command not found. When I kept putting the same command he said that the page I'm to reach does not exist anymore or maybe just.

---

### Post by ubname on 2017-11-18
> **berno94 said:**
> I'm trying to install vesta vesta server in my PC but i always get permission denied when I entered the right password. ssh [EMAIL="root@your.server"]root@your.server[/EMAIL](Ssh root@192.168.0.13) when he asked me for the password I put the password but he kept saying that permission denied and password, public key. Can someone help me solve this mystery please.

I dont know vesta but you cannot remotely login as root unless you change your sshd config file so to permit root login (possibly a bad idea in general).

---

### Post by berno94 on 2017-11-18
> **ubname said:**
> I dont know vesta but you cannot remotely login as root unless you change your sshd config file so to permit root login (possibly a bad idea in general).

I change sshd config to permit root login but for some reason he doesn't work.

---

### Post by ubname on 2017-11-18
> **berno94 said:**
> I change sshd config to permit root login but for some reason he doesn't work.

Did you enable the root password?
Dis you restart the ssh daemon?

is it mandatory that you connect with root?

---

### Post by berno94 on 2017-11-18
> **ubname said:**
> Did you enable the root password?
Dis you restart the ssh daemon?

is it mandatory that you connect with root?

The password was set to prohibited password and I changed it to Yes. Yes I enabled the root password and I even change it multiple times.

---

### Post by ubname on 2017-11-18
> **berno94 said:**
> The password was set to prohibited password and I changed it to Yes. Yes I enabled the root password and I even change it multiple times.

Well i still do not understand what you have done, you should have done as below:

login to remote server with standard "admin account"
become root with sudo su and set a new root password
Permtirrootlogin = Yes
restart the sshd service
logout, relogin as "[EMAIL="root@xxx.xxx.xxx.xxx"]root@xxx.xxx.xxx.xxx"[/EMAIL]

hope this hepls

---

### Post by Bucky Ball on 2017-11-18
I repeat: are you following a tutorial or how-to to do this and if so, please post a link to it. We are flying a little blind here. :)

---

### Post by shintaomonk on 2017-12-07
Question...

Are you using ```
sudo
```?

---

