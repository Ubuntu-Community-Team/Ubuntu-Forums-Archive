---
title: "problems connecting to the repositories"
date: 2013-10-30
forum: New to Ubuntu
---

### Post by Zombir on 2013-10-30
Hi,
I wanted to install a 32 bit version of a software I've been using in my 64bit laptop which uses Ubuntu 13.04. After some search I found that I should install ia32-libs package in order to do so. So I typed the following code:

```
sudo apt-get install ia32-libs
```

It seemed to me that I couldn't connect to the server when I ran that command because the terminal was stuck at the line:

```
0% [Connecting to ftp.iinet.net.au (203.0.178.32)] [Connecting to extras.ubuntu
```

(This is not exactly the line as I later changed the server I connect)

My internet connection was working well. I could browse internet through my web browser and I could ping to anywhere I wanted. 

So I opened Ubuntu software center and tried to use its feature of getting the best server. This did not resolve my problem. Still the same. Neither software center nor the terminal could connect to the repos now. 

My internet connection goes through a proxy server which can be configured using a configuration script. I've used the GUI tool to set system-wide proxy and it was working fine even few days ago. I urgently need to install this software now so any help would be appreciated. 

Thanks in advance.

---

### Post by grahammechanical on 2013-10-30
It seems that in trying to fix one problem you have created another problem. The second problem needs to be fixed before you can solve the first problem. Please run these two commands and post any error messages back here.

```
sudo apt-get update
```
```
sudo apt-get upgrade
```

More than a year ago we began to get in Ubuntu something called multiarch libraries. They were libraries that made the running of 32 bit applications in 64 bit Ubuntu much more efficient. So, you may have an incorrect name for that library. And it may not be available from the repositories. I have certainly tried looking for ia32-libs-multiarch and I cannot find it in the standard repositories.  but it can be downloaded from here.

[http://packages.ubuntu.com/raring/ia32-libs](http://packages.ubuntu.com/raring/ia32-libs)

Regards.

---

### Post by Zombir on 2013-10-30
> **grahammechanical said:**
> It seems that in trying to fix one problem you have created another problem. The second problem needs to be fixed before you can solve the first problem. Please run these two commands and post any error messages back here.

```
sudo apt-get update
```
```
sudo apt-get upgrade
```

More than a year ago we began to get in Ubuntu something called multiarch libraries. They were libraries that made the running of 32 bit applications in 64 bit Ubuntu much more efficient. So, you may have an incorrect name for that library. And it may not be available from the repositories. I have certainly tried looking for ia32-libs-multiarch and I cannot find it in the standard repositories.  but it can be downloaded from here.

[http://packages.ubuntu.com/raring/ia32-libs](http://packages.ubuntu.com/raring/ia32-libs)

Regards.

Well, turns out its a problem with proxy after all. 
I'm away now from my university ( where the proxy is ) and am visiting my friend's home. I took my laptop to my friend's home where there is no proxy and tried the same thing there and turns out it works well. And ia32-libs is still available and I was able to install it through apt-get at my friend's home. For now my problem is solved. 
So I'm guessing that, for some reason the system-wide proxy settings hadn't affected the apt-get. Anyway will post the result of update and upgrade as soon as I get back to the university.  
Thanks for your help. 

P S : thanks for your information on multiarch. You need to know what exactly libraries you need to install in order to use them right ? I don't know them and hasn't got enough time to find it out either. Anyway thanks, thanks for your link for ia32-libs too.

Regards,
Zombir

UPDATE:
Now I'm back at the university and still cannot update. 

[FONT=arial]```
 sudo apt-get update 
```

results in the same problem above:

[/FONT][FONT=arial]```
0% [Connecting to ftp.iinet.net.au (203.0.178.32)] [Connecting to extras.ubuntu 
```

stuck there. Nothing else. 

```
sudo apt-get upgrade
```

results in:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

But the web browser works well. And I could ping to any outside server. 

Please help! 

[/FONT]

---

