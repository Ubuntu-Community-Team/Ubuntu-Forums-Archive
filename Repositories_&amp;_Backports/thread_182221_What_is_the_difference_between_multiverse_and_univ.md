---
title: "What is the difference between multiverse and universe?"
date: 2006-05-25
forum: Repositories &amp; Backports
---

### Post by Isoss on 2006-05-25
Just wondering ... I am new to linux ... I've been using it for 2 months now and I LOVE it so much and ubutnu was a great choice and I am really confortable ... just need to understand some stuff ... What is the difference between multiverse and universe? ... I mean ... what do they even mean when it comes to downloading packages. what about "main and restricted"?

Another question. My original rpositories were something like deb-src [http://sy.archive.ubuntu.com/ubuntu](http://sy.archive.ubuntu.com/ubuntu) breezy main restricted ... I noticed the sy. at the biggening and the update didn't really work well untill I omitted them. What difference does it make if I live in syria so I have to use "as a default" the -correct me i I'm wrong - "Syrian" repositories ... just need to understand al about these stuff so I'd be comprehending what I am doing.

Thanks!

---

### Post by 23meg on 2006-05-25
You'll find the answers [here]("http://www.ubuntu.com/ubuntu/components").

---

### Post by matthew on 2006-05-25
[quote=Isoss]Another question. My original rpositories were something like deb-src [http://sy.archive.ubuntu.com/ubuntu]("http://sy.archive.ubuntu.com/ubuntu") breezy main restricted ... I noticed the sy. at the biggening and the update didn't really work well untill I omitted them. What difference does it make if I live in syria so I have to use "as a default" the -correct me i I'm wrong - "Syrian" repositories ... just need to understand al about these stuff so I'd be comprehending what I am doing.[/quote]For this part of your question...

You can safely remove the "sy." and just use something like this:
deb-src [http://archive.ubuntu.com/ubuntu]("http://sy.archive.ubuntu.com/ubuntu") breezy main restricted

It might be faster or slower depending on a number of things...the local mirrors (like sy.archive.ubuntu.com) are certainly physically closer and are usually, but not always, faster. Some don't get updated as quickly either. Anyway, it's your choice.

---

### Post by Isoss on 2006-05-25
[QUOTE=23meg]You'll find the answers [here]("http://www.ubuntu.com/ubuntu/components").[/QUOTE]

Cool, thanks .. this is just sufficient.

---

### Post by Isoss on 2006-05-25
[QUOTE=matthew]For this part of your question...

You can safely remove the "sy." and just use something like this:
deb-src [http://archive.ubuntu.com/ubuntu]("http://sy.archive.ubuntu.com/ubuntu") breezy main restricted

It might be faster or slower depending on a number of things...the local mirrors (like sy.archive.ubuntu.com) are certainly physically closer and are usually, but not always, faster. Some don't get updated as quickly either. Anyway, it's your choice.[/QUOTE]

Thanks. I guess - also correct me if wrong - it doesn't really matter since I have a DSL connection. I think I am more comfortable with ones without the sy. now.

---

### Post by 23meg on 2006-05-25
According to general net etiquette you should prefer local mirrors whenever possible, so that there will be less long distance net traffic and a more homogeneous distribution of server load.

---

### Post by Isoss on 2006-05-25
Alright ... here is the out put of local "sy." repositories:

```
Ign http://sy.security.ubuntu.com breezy-security Release.gpg
Ign http://sy.security.ubuntu.com breezy-security Release
Ign http://sy.security.ubuntu.com breezy-security/main Packages
Get:1 http://sy.archive.ubuntu.com breezy Release.gpg [189B]
Ign http://sy.security.ubuntu.com breezy-security/restricted Packages
Ign http://sy.security.ubuntu.com breezy-security/main Sources
Ign http://sy.security.ubuntu.com breezy-security/restricted Sources
Get:2 http://sy.archive.ubuntu.com breezy-updates Release.gpg [189B]
Ign http://sy.security.ubuntu.com breezy-security/universe Packages
Get:3 http://sy.archive.ubuntu.com breezy-backports Release.gpg [189B]
Ign http://sy.security.ubuntu.com breezy-security/universe Sources
Err http://sy.security.ubuntu.com breezy-security/main Packages
  503 Service Unavailable [IP: 192.168.2.20 3128]
Get:4 http://sy.archive.ubuntu.com breezy Release [30.9kB]
Err http://sy.security.ubuntu.com breezy-security/restricted Packages
  503 Service Unavailable [IP: 192.168.2.20 3128]
Err http://sy.security.ubuntu.com breezy-security/main Sources
  503 Service Unavailable [IP: 192.168.2.20 3128]
Err http://sy.security.ubuntu.com breezy-security/restricted Sources
  503 Service Unavailable [IP: 192.168.2.20 3128]
Err http://sy.security.ubuntu.com breezy-security/universe Packages
  503 Service Unavailable [IP: 192.168.2.20 3128]
Get:5 http://sy.archive.ubuntu.com breezy-updates Release [30.9kB]
Err http://sy.security.ubuntu.com breezy-security/universe Sources
  503 Service Unavailable [IP: 192.168.2.20 3128]
Get:6 http://sy.archive.ubuntu.com breezy-backports Release [19.6kB]
Get:7 http://sy.archive.ubuntu.com breezy/main Packages [585kB]
Get:8 http://sy.archive.ubuntu.com breezy/restricted Packages [5061B]
Get:9 http://sy.archive.ubuntu.com breezy/main Sources [232kB]
Get:10 http://sy.archive.ubuntu.com breezy/restricted Sources [1454B]
Get:11 http://sy.archive.ubuntu.com breezy/universe Packages [2304kB]
Get:12 http://sy.archive.ubuntu.com breezy/universe Sources [915kB]
Get:13 http://sy.archive.ubuntu.com breezy-updates/main Packages [39.0kB]
Get:14 http://sy.archive.ubuntu.com breezy-updates/restricted Packages [14B]
Get:15 http://sy.archive.ubuntu.com breezy-updates/main Sources [18.6kB]
Get:16 http://sy.archive.ubuntu.com breezy-updates/restricted Sources [14B]
Get:17 http://sy.archive.ubuntu.com breezy-backports/main Packages [14.0kB]
Get:18 http://sy.archive.ubuntu.com breezy-backports/restricted Packages [14B]
Get:19 http://sy.archive.ubuntu.com breezy-backports/universe Packages [26.1kB]
Get:20 http://sy.archive.ubuntu.com breezy-backports/multiverse Packages [1353B]Get:21 http://sy.archive.ubuntu.com breezy-backports/main Sources [5185B]
Get:22 http://sy.archive.ubuntu.com breezy-backports/restricted Sources [14B]
Get:23 http://sy.archive.ubuntu.com breezy-backports/universe Sources [10.2kB]
Get:24 http://sy.archive.ubuntu.com breezy-backports/multiverse Sources [701B]
Fetched 4240kB in 3m30s (20.2kB/s)
Failed to fetch http://sy.security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz  503 Service Unavailable [IP: 192.168.2.20 3128]
Failed to fetch http://sy.security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz  503 Service Unavailable [IP: 192.168.2.20 3128]
Failed to fetch http://sy.security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz  503 Service Unavailable [IP: 192.168.2.20 3128]
Failed to fetch http://sy.security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz  503 Service Unavailable [IP: 192.168.2.20 3128]
Failed to fetch http://sy.security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz  503 Service Unavailable [IP: 192.168.2.20 3128]
Failed to fetch http://sy.security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz  503 Service Unavailable [IP: 192.168.2.20 3128]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
isos@Isos-Ubuntu:~$


```

when I ommit them the update just works!

so what's the problem then?

---

### Post by 23meg on 2006-05-25
Probably the Syrian server was down when you tried. Try again later, and if it still fails, just remove the .sy bits, preferably replacing them with the code of a country that's close to you, such as .tr ;)

---

### Post by Isoss on 2006-05-25
cokguzal ... I love turkey ... yeah, why not ... I'll try it. Teshekur ederim ;)

---

### Post by Isoss on 2006-05-25
Just a question! 
what about these? 
#deb [http://tr.archive.ubuntu.com/ubuntu](http://tr.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
#deb-src [http://tr.archive.ubuntu.com/ubuntu](http://tr.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
What are the backports? I enabled then and I got some errors ...
Do I need them?

---

### Post by Isoss on 2006-05-25
Hey, I just tried them ... but it gave me some errors and as the update manager prompted it seemed all of the [http://tr.security.ubuntu.com/ubuntu](http://tr.security.ubuntu.com/ubuntu) ... if I go to this url it either wil give me 
ERROR
The requested URL could not be retrieved
Or a bad gate way 503! ... 
However, I removed the tr. from the security repositories and kept them with the archive.ubuntu.com and it worked.

I guess I'll always have to try conneting to the countries arround when the server in mine isn't working. anyway ... Thanks a lot guys. but ofcourse still need the answer for the backsport thing which I have mentioned  previously.

---

### Post by 23meg on 2006-05-25
[QUOTE=Backports Wiki] What are 'Backports'?

Backporting is the process of compiling and providing new packages for a distribution that no longer gets any updates except for security purposes - for example backports are often made to bring the latest, greatest version of a crucial piece of software to a version of an OS that it isn't officially available for. Specifically, when backporting, the package is taken from the current development version of the OS.

In Ubuntu's case this means that packages that are in the Dapper Drake repositories(the unreleased successor to Breezy Badger) can be compiled and made to run on Breezy.

As a result, in order for a package to be considered for backporting, it must first be available in the Dapper repositories. Failure to check this is probably the main reason for the refusal of backport requests. [/QUOTE]

[http://backports.ubuntuforums.org/wiki/index.php/Main_Page](http://backports.ubuntuforums.org/wiki/index.php/Main_Page)

It's up to you to decide if you need them. Make sure you issue an ```
sudo apt-get update
```command each time you add or remove a repository.

---

