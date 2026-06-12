---
title: "Do you need apt-get for MS Windows?"
date: 2009-05-20
forum: Packaging and Compiling Programs
---

### Post by slavne on 2009-05-20
Hi everybody, ):P
If I understood well, ubuntu system uses apt-get or similar commands to automatically obtaining new or missing packages. This procedure is based on ubuntu machine connected to Internet. But what if you have a MS Windows machine connected to Internet in your company or elsewhere? I did not found any simple automated procedures to such a job.

Well in about a week I will have my simple MS windows application finished that could help in the process of ubuntu packages download even when you do not have ubuntu machine on internet, but you have only ms windows machine on internet. This ms windows application would allow you to choose among possible ubuntu mirror sites, quote your wanted package and it's ubuntu version, and it will find all the necessary dependent packages and download all of them to your Windows machine. The aplication would calculate all dependecies and bring all needed  packages to your local machine. Then you are free to use your usb flash drive to bring them to ubuntu machine and install them with a simple command. 

If there is any need for something like that please let me know. If so and there are some users that would need it, does anybody know where on this forum could I post the ms windows binary for this tool?

---

### Post by eyelessfade on 2009-05-21
great project. I would like the same program for linux. So I can download programs from work and bring them home on a stick.

---

### Post by slavne on 2009-05-21
> **eyelessfade said:**
> great project. I would like the same program for linux. So I can download programs from work and bring them home on a stick.

Yes I agree it would be useful to have a linux program doing the same. I shall see about it if I find some time after this project...

If somebody inlights me with the information where on this site I could download the apl., I shell post the url here, so keep an eye on this thread.

---

### Post by SonicSteve on 2009-05-21
Simple question from a non-programmer

How will the program on a windows machine know what packages are currently installed on the Ubuntu machine? Every machine is slightly different, and sometimes very different.

---

### Post by eyelessfade on 2009-05-21
I hope it will download _all_ dependencies. Maybe not the basic like glibc? but I don't think it takes to much space anyways.

---

### Post by eyelessfade on 2009-05-21
On a later version it would be great if one could specify which version of ubuntu/deb you used and download for those.

---

### Post by slavne on 2009-05-21
> **SonicSteve said:**
> Simple question from a non-programmer

How will the program on a windows machine know what packages are currently installed on the Ubuntu machine? Every machine is slightly different, and sometimes very different.

In this version (say 1.0), the aplication would NOT know that at all, but it's purpose is what I said: to find all dependent packages along with your demanded package and download them all.

If I remember well, if you ALREADY have some packages installed on your Linux machine, and if some of those packages are among the downloaded packages, during installation you would just get some warnings about trying to replace the already existing packages, which would not a problem at all.

If you mean that some packages would not be downloaded if they are already on Linux machine, you are right, and I was planning that for the next version (take it easy guys, I still work for this one :p). In that case you would make the listing of your Linux machine installed packages, then bring that listing to the Window machine, and the program would then read that listing and skipping automatically already installed packages from download.

---

### Post by SonicSteve on 2009-05-21
OK so then this program on the windows machine will download all packages from the mirror and keep them up to date when packages on the mirror get updated? This sounds a bit like Windows Server Update Services. Would you be able to then use the windows machine as the update server for the Ubuntu machine/s hypothetically if they were networked but not directly connected to the internet? It would almost be the same as hosting your own Ubuntu Mirror accessible only to yourself. If you had even 10 machines and each machine downloaded a total of 100mb each month in updates you could save 900mb of downloads simply because only 1 machine would need to do the downloading.

---

### Post by slavne on 2009-05-21
> **SonicSteve said:**
> OK so then this program on the windows machine will download all packages from the mirror and keep them up to date when packages on the mirror get updated? This sounds a bit like Windows Server Update Services. Would you be able to then use the windows machine as the update server for the Ubuntu machine/s hypothetically if they were networked but not directly connected to the internet? It would almost be the same as hosting your own Ubuntu Mirror accessible only to yourself. If you had even 10 machines and each machine downloaded a total of 100mb each month in updates you could save 900mb of downloads simply because only 1 machine would need to do the downloading.

Interesting idea, but maybe for the future. For now, version 1 is not a service but an application that let you manualy start it, type in a package name, choose one of offered ubuntu versions, type in where the download would go, choose one of the offered mirror sites, and press the button. This sutes the need of a user who know the name of the basic package that he needs and get it along with all the rest he needs.

---

### Post by SonicSteve on 2009-05-21
I see the possible appeal,  I would like to see a version that runs on Ubuntu as well though.

---

### Post by slavne on 2009-05-21
> **SonicSteve said:**
> I see the possible appeal,  I would like to see a version that runs on Ubuntu as well though.

Agreed. Depending on my time I could be interested in making that too. Maybe somebody makes it in the meantime!

---

### Post by slavne on 2009-05-29
The application is finished (ver 1.0). It even has the detection of existing packages so it downloads only the necessary packages from internet.

Unfortunately it seems nobody offers the solution for downloading this and other good tools here on this site because those tools runs on windows os. It is strange because those utilities actually help Windows users to convert to Ubuntu. As an additional issue there could be a licence problem with a third party about my tool. Anyway I think I shall find a good implementation for this peace of software for myself.

---

