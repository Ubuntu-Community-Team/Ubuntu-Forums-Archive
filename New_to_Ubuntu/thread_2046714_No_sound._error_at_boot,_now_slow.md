---
title: "No sound. error at boot, now slow"
date: 2012-08-23
forum: New to Ubuntu
---

### Post by glendonboy on 2012-08-23
Loaded Ubunto up about a month ago in an older Sony with a brand new hard drive. No other OS. I get there is an error message at boot and have never had sound. Did an update last nite and now the system system is very slow. I have tried several different ideas to get sound to no avail. Any help would be appreciated. Thanks!

---

### Post by glendonboy on 2012-08-23
[http://i27.photobucket.com/albums/c159/glendonboy/Screenshotfrom2012-08-23173425.png]("http://i27.photobucket.com/albums/c159/glendonboy/Screenshotfrom2012-08-23173425.png")


Does this help? I am an old newbie. Sorry!

---

### Post by NikTh on 2012-08-23
Hi , 
what is this lsvpd package ? where did you find it and for what reason you installed ? and how installed ? 

I searched and found [http://linux-diag.sourceforge.net/Lsvpd.html](http://linux-diag.sourceforge.net/Lsvpd.html) , is that the package ? 
Thanks

---

### Post by glendonboy on 2012-08-23
> **NikTh said:**
> Hi , 
what is this lsvpd package ? where did you find it and for what reason you installed ? and how installed ? 

I searched and found [http://linux-diag.sourceforge.net/Lsvpd.html](http://linux-diag.sourceforge.net/Lsvpd.html) , is that the package ? 
Thanks

I am so stupid. I was googling any resolution to my problem. I can't even tell you the answer to your question, I was grabbing and doing whatever anyone said.

---

### Post by NikTh on 2012-08-23
Hi , 
in the future when you have questions - queries - problems , first place to search is here , also you can search at  [http://askubuntu.com/and](http://askubuntu.com/and) and [https://answers.launchpad.net/ubuntu ,]("https://answers.launchpad.net/ubuntu")
and if you cannot find an answer to your problem you can open a question - thread . 

now try to uninstall this package with below method 

Open a terminal (ctrl+alt+t) and copy-paste from here this command 

```
sudo apt-get purge lsvpd*
```It will ask you for your password , write it (nothing will show up , like you write nothing , it is normal) 
then run these commands 
```
sudo apt-get update 
sudo apt-get dist-upgrade
```If any error occur post it here copy from terminal and place it here **inside ```
 tags** 
[noparse][code]the error or result here
```[/noparse]

Thank you.

---

### Post by glendonboy on 2012-08-24
> **NikTh said:**
> Hi , 
in the future when you have questions - queries - problems , first place to search is here , also you can search at [http://askubuntu.com/and](http://askubuntu.com/and) and [https://answers.launchpad.net/ubuntu ,]("https://answers.launchpad.net/ubuntu")
and if you cannot find an answer to your problem you can open a question - thread . 
 
now try to uninstall this package with below method 
 
Open a terminal (ctrl+alt+t) and copy-paste from here this command 
 
```
sudo apt-get purge lsvpd*
```It will ask you for your password , write it (nothing will show up , like you write nothing , it is normal) 
then run these commands 
```
sudo apt-get update 
sudo apt-get dist-upgrade
```If any error occur post it here copy from terminal and place it here **inside ```
 tags** 
[noparse][code]the error or result here
```[/noparse]
 
Thank you.
 
Thank you sir! No error message

---

### Post by NikTh on 2012-08-24
> **glendonboy said:**
> Thank you sir! No error message

Hi , 
and what about the slowness and sound problem ? remained ?

---

