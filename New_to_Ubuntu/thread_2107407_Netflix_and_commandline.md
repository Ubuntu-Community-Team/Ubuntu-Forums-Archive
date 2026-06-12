---
title: "Netflix and commandline"
date: 2013-01-21
forum: New to Ubuntu
---

### Post by jbcohen on 2013-01-21
Netflix requires Microsoft Silverlight to see movies online what software can  take silverlight's place on the netflix site?

I have seen a video on youtube about the command line.  I need a written document that shows all the commands, they look similar to the old DOS commands that I am used to many years ago.  What do you recommend?

What  are kbuntu and Xbuntu?

---

### Post by Miljet on 2013-01-21
The last time I checked, about a year ago, there were no viable alternatives for watching Netflix movies in Linux. Might ave changed by now. Try searching for "Netflix on Linux" in your favorite search engine.

Kubuntu, Xubuntu, and Lubuntu are all variations of Ubuntu but with different desktop envioronments.

---

### Post by Cheesemill on 2013-01-22
If you are just after the command to install Netflix then its...
```
sudo apt-add-repository ppa:ehoover/compholio
sudo apt-get update
sudo apt-get install netflix-desktop
```If you are wanting to learn all about the command line then look at the resources here...
[https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)

---

### Post by omeomi on 2013-01-22
The only alternative to Microsoft Silverlight on Linux is using [Moonlight]("http://www.go-mono.com/moonlight/"), but I don't know if that works for Netflix.

---

### Post by LuciferRex on 2013-01-22
> **Cheesemill said:**
> If you are just after the command to install Netflix then its...
```
sudo apt-add-repository ppa:ehoover/compholio
sudo apt-get update
sudo apt-get install netflix-desktop
```If you are wanting to learn all about the command line then look at the resources here...
[https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)

This is currently the ONLY way to watch Netflix in Ubuntu.  It does a great job though!

---

### Post by Warren Hill on 2013-01-22
> **omeomi said:**
> The only alternative to Microsoft Silverlight on Linux is using [Moonlight]("http://www.go-mono.com/moonlight/"), but I don't know if that works for Netflix.

It doesn't as Netflix use DRM which monolight does not support.

The solution offered by Cheesemill should work however.

---

### Post by jbcohen on 2013-01-25
I would like to ask for help when I pull apart cheesmill's code so that I can learn something about the code that cheesmill uses:

I know the sudo command how about apt-add-repository?  What is this command string?

How about ppa:ehoover/compholio - I think that the ppa means to download and install a package called ehoover?  What is /compholio?

The second line is mostly easy enough sudo is simple how about apt-get?  Update I think tells linux to get the latest version of ehoover?

There's that apt-get again on the third line.  However, install netflix-desktop I think tells linux to install the software on the desktop?

---

### Post by Warren Hill on 2013-01-25
```
sudo apt-add-repository ppa:ehoover/compholio 
```This command tells the computer you want to use a new repository.
The repository is called  ppa:ehoover/compholio
Its not an offical Ubuntu one its provided by a third party

```
sudo apt-get update 
```This command says update your database so you know what's in this new repository

```
sudo apt-get install netflix-desktop
```This command installs the application.

In general you should be wary about installing stuff from third party repositories as it could be a source of malware.  However, this particular one is well known so it's safe.

---

### Post by jbcohen on 2013-01-25
Thanks to waren I understand the commands a bit better.  However I would like to keep going so I learn as much as possible: What a repository?

---

### Post by oldos2er on 2013-01-25
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by jbcohen on 2013-01-25
How do I tell the kernel to put a repository on an external hard drive?

---

### Post by arpanaut on 2013-01-25
From a link at the bottom of the previously posted source of information:

[https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)

---

### Post by jbcohen on 2013-01-25
ok,  Iexplored that link I must have missed that information.  My apologies.

---

