---
title: "Perl,Python,GCC,Apache and Mysql in ubuntu ultimate"
date: 2007-05-27
forum: Programming Talk
---

### Post by technomaniac on 2007-05-27
I have used suse,redhat,mandriva and lot of others in the past.Ubuntu always put me off because you had to download all programming stuff like GCC etc from the net.I would like to know if ubuntu ultimate edition has the following bundled with it

1.GCC
2.Perl
3.Python
4.Apache
5.MySQL

If not,then which version of ubuntu has?

Regards,
Sandip

---

### Post by adityakavoor on 2007-05-27
GCC is there in the Ubuntu CD itself

just insert CD and type in terminal 
```

sudo apt-get install build-essential

```

---

### Post by christhemonkey on 2007-05-27
I dont think any ubuntu derivatives include GCC by default.

Python and perl are included by default in standard ubuntu.

Apache and mysql can be installed by default on ubuntu server edition.

It really isnt hard to install these things is it?
```
sudo apt-get install build-essential apache2 mysql-server 
```

---

### Post by harun on 2007-05-27
They ALL have the first 3. Like said in the previous post it is one command to get the other 2.

Nearly everything in the system depends on the first three hence they are always there.

---

### Post by technomaniac on 2007-05-29
My prob is that the internet connection at my home is too slow(10 kbps) and at college its fast but the sysadmin has blocked a lot of ports because of which ubuntu is unable to get those apps from repository.I have tried and failed many times.So I would prefer if I get everything in one CD/DVD.

---

### Post by pmasiar on 2007-05-29
There is a way how to use CD instaed of online repository (you need to add CD to sources). When you know that, you have another problem: ask admin to download you one CD. Talk to him/her, thay might be interested in linux - you might be able to be usefull to them in some way. If your dowload is for study (Linux) and not music, they should be amenable to bribes... :-)

---

### Post by technomaniac on 2007-05-30
well....i will try that.But our sysadmin is very tough to deal with.He was installed some keyword detection software on the internet servers so that even orkut,youtube and the like are blocked.Most girls in our college are unable to join ACM Women Special Interest Group coz the word woman is blocked too.Ha ha.

in short, he is a maniac

Anyway lets see

---

### Post by FuriousLettuce on 2007-05-30
You can download the packages manually via http - go to [packages.ubuntu.com](packages.ubuntu.com). From there, you can search for each package in turn and download them. Each page lists the packages dependencies, which you will also have to download and install. It will be very tedious, but it'll only have to be done once. 

Do you not have a mate's house that you can visit to install them?

---

### Post by LaRoza on 2007-05-30
You can buy them on disk also, I did that and it works fine.

[http://www.thelinuxstore.ca/](http://www.thelinuxstore.ca/)

---

### Post by pmasiar on 2007-05-30
> **technomaniac said:**
> Most girls in our college are unable to join ACM Women Special Interest Group coz the word woman is blocked too.Ha ha.

This is not funny - they should complain to administration. Free communication is whole point of internet, and his personal mysogynic preferences needs be restrained. If not secret, which country are you from? Most countries have laws agains women discrimination.

---

### Post by technomaniac on 2007-05-30
yeah...he is a *******...Actually what u call discrimination against women is an attempt to block adult content.He thinks that students will search google with term containing women for adult content.So we cant really do much.However other more explicit terms are not blocked.

  But I have a better way.That guy doesn't know a thing about security.He is using a old version of squid and I have identified many bugs in it.So pretty soon, I will break into his server and simply turn off certain keywords and install a backdoor so that I can log on in the furture.

  By the way, I am from India.

---

