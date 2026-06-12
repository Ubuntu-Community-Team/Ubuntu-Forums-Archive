---
title: "How to create a new package in PPA"
date: 2010-08-26
forum: Packaging and Compiling Programs
---

### Post by SwedishWings on 2010-08-26
I need some help...

I have created a new package (macfanctld), created a project in ppa (also named macfanctld), and now need to upload it to the ppa. I've tried to use

```
$ dput ppa:macfanctld/ppa macfanctld_0.0_source.changes
```

which succeeds, but nothing shows up in the ppa. I've spent quite some time to understand this, but just get stuck.

Hope someone can help me out.

Thanks,
Mike

---

### Post by SevenMachines on 2010-08-27
Hi, maybe i've missed the page but you dont seem to have any ppa's, you seem to have a bzr branch instead.
As far as i'm aware, unless launchpad does something clever here, the command you specify above will only look for a ppa called 'ppa' (you can choose when you create it) in the launchpad address of user 'macfanctld'. 
You'd need to create that ppa or use the existing bzr branch at lp:macfanctld to push to

---

### Post by KdotJ on 2010-08-28
Just to jump in here, does anyone know of a good tutorial or info about how to create your own PPA with an existing bazaar branch? Do you need to create a DEB of the project first?

---

### Post by SwedishWings on 2010-08-28
> **SevenMachines said:**
> Hi, maybe i've missed the page but you dont seem to have any ppa's, you seem to have a bzr branch instead.
As far as i'm aware, unless launchpad does something clever here, the command you specify above will only look for a ppa called 'ppa' (you can choose when you create it) in the launchpad address of user 'macfanctld'. 
You'd need to create that ppa or use the existing bzr branch at lp:macfanctld to push to

Thanks, i managed to create a personal PPA and upload it there. I still have to figure out how to use a PPA that is not personal though.

---

### Post by SwedishWings on 2010-08-28
> **KdotJ said:**
> Just to jump in here, does anyone know of a good tutorial or info about how to create your own PPA with an existing bazaar branch? Do you need to create a DEB of the project first?

I have just been through this, and needless to say, it took a lot of reading to get into it. 

Start by reading this: [https://help.launchpad.net/Packaging/PPA/Uploading](https://help.launchpad.net/Packaging/PPA/Uploading)

Follow the links, and read very carefully on how to get started. It took me many hours to get it right.

In my case, i wanted to create a package from scratch, which turned out to be a lot harder than modifying an existing package.

Hope this helps.

NB. The Debian/Ubuntu packaging system is barrier. A simpler system would probably result in more people uploading there stuff to a PPA for sharing. It took me like a few days to get up my first package...

---

### Post by KdotJ on 2010-08-29
> **SwedishWings said:**
> I have just been through this, and needless to say, it took a lot of reading to get into it. 

Start by reading this: [https://help.launchpad.net/Packaging/PPA/Uploading](https://help.launchpad.net/Packaging/PPA/Uploading)

Follow the links, and read very carefully on how to get started. It took me many hours to get it right.

In my case, i wanted to create a package from scratch, which turned out to be a lot harder than modifying an existing package.

Hope this helps.

NB. The Debian/Ubuntu packaging system is barrier. A simpler system would probably result in more people uploading there stuff to a PPA for sharing. It took me like a few days to get up my first package...

Thanks for the link, I'll get reading haha. I already have stuff on launchpad and have built a few of my own debs on my machine to test out and stuff, hope this will give me a bit of background knowledge!

---

