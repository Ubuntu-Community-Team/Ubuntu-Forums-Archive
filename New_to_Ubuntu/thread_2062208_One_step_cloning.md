---
title: "One step cloning?"
date: 2012-09-24
forum: New to Ubuntu
---

### Post by ahender1 on 2012-09-24
I have an already existing 10.4 OS on two laptops.

To prepare for when and if one or both go out, is there a way to take a snapshot of OS and all files to make the start-up a a brand new laptop a one click job?

---

### Post by irv on 2012-09-24
This might be what you are looking for.
[http://www.howtogeek.com/howto/22145/how-to-create-your-own-customized-ubuntu-live-cd/]("http://www.howtogeek.com/howto/22145/how-to-create-your-own-customized-ubuntu-live-cd/")
Remember that if the hardware is different from one system to another you could have some problems.

---

### Post by alphaamanitin on 2012-09-24
What exactly are you wanting? Something to restore one of the laptops to the other or something to restore the laptop to so that if it fails you can simply reload like nothing happened?

AlphaA

---

### Post by ahender1 on 2012-09-25
Thanks Irv.  I will try Reconstructor out.

Hey Alphaamanitin!  "*God* is a comedian playing to an audience too afraid to laugh." HAHaHaHaHa!

I am doing research and the company I am working for is buying new laptops, so I want to make installing Ubuntu and other programs (Gnu Radio specifically) a very simple and painless process.

---

### Post by jerrrys on 2012-09-25
I don't know of any one step process, but you may want to check out [clonezilla]("http://clonezilla.org/").

Its actually for backing up an HDD or partitions, but I find it can also be used to load other computers.  Ubuntu will usually see the change and automatically adjust its settings.  It does have a one CD/DVD limit.

Also if you know what make/model your company is buying you can check for compatibility.  Video compatibility especially.

And welcome to the forum :)

oops, I forgot [URL="http://www.geekconnection.org/remastersys/index.html"]Remasters
[/URL]

---

### Post by ahender1 on 2012-09-28
Okay guys.  I appreciate the help so far and have chosen to go with Remastersys.  I ran this command apt get install remastersys after adding this to the sources.list: deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic/.

I got this message: 

The program 'apt' is currently not installed.  You can install it by typing:
sudo apt-get install openjdk-6-jdk

So I did and it loaded perfectly.

But when I go to use it via either one of these routes:  "sudo *remastersys* backup", or "sudo su" to become root and then run "*remastersys* dist" 

I get "remastersys: command not found".

Any ideas?

---

### Post by mips on 2012-09-28
> **ahender1 said:**
> 
I am doing research and the company I am working for is buying new laptops, so I want to make installing Ubuntu and other programs (Gnu Radio specifically) a very simple and painless process.

If you simply want to restore computers to a standard install then cloning is the way to go.

Have a look at,
[http://www.fogproject.org/](http://www.fogproject.org/)
[http://clonezilla.org/](http://clonezilla.org/)

If you need more than that, ie controlling desktops, policies, software deploymenent etc etc (in essence managing corporate 10,000+ device environment) then let us know and we can post some links for you.

---

### Post by jerrrys on 2012-10-02
I cannot assist you with remastersys as I use clonezilla and rsync.  But many use this package, I expect someone to drop in.  Till then how bout some reading

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Remastersys&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Remastersys&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by ahender1 on 2012-10-03
Does clonezilla or rsync allow you to save the complete enviroment you have on a laptop.  The reason for my asking is I want to save Ubuntu 10.04, but I also want to have GNU Radio, etc. saved as well.  This is to save time from installing the GNU Radio software onto a new laptop, which can be time consuming at best.

---

### Post by ezsit on 2012-10-03
> **ahender1 said:**
> 
But when I go to use it via either one of these routes:  "sudo *remastersys* backup", or "sudo su" to become root and then run "*remastersys* dist" 

I get "remastersys: command not found".

Any ideas?

Try the instructions and the forum on the [www.remastersys.com](www.remastersys.com) website. I have been using remastersys for several years on Ubuntu and it has worked flawlessly for me. I did read the instructions and ask on the forums when necessary, but the gui for remastersys works well and explains what to do. I have never used remastersys from the command line - I never had to.

Also search youtube for remastersys or remastering Ubuntu and you will find video instructions.

---

### Post by Hadaka on 2012-10-03
Hi, to clone an entire drive...

```
dd if=/dev/sda of=/dev/sdb bs=4096 conv=notrunc,noerror 
```

with SDA being the source drive and SDB being the target drive.

---

### Post by jerrrys on 2012-10-03
> **ahender1 said:**
> Does clonezilla or rsync allow you to save the complete enviroment you have on a laptop.  The reason for my asking is I want to save Ubuntu 10.04, but I also want to have GNU Radio, etc. saved as well.  This is to save time from installing the GNU Radio software onto a new laptop, which can be time consuming at best.

Clonezilla will clone everything on your HDD, it will be a mirror image right down to the [UUID]("https://help.ubuntu.com/community/UsingUUID").   So yes to your question; GNU radio and everything else will be copied.

But understand this is suppose to be used as a backup for the machine in use.  I have used this method to load other computers and it works for me.  Ubuntu has detected different hardware and auto configured,  however this is not a supported method.  Thus we have remastersys, software made to create a bootable ISO to be loaded onto a variety of machines.

Make sense?

---

