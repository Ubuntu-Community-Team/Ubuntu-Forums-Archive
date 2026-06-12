---
title: "Linux support for VB"
date: 2005-07-30
forum: Programming Talk
---

### Post by hzs202 on 2005-07-30
Hi All,

I was wondering does Ubuntu or Linux in general support Visual Basic or VB.NET or some comparable clone.

Best,

---

### Post by cwaldbieser on 2005-07-30
There is a tool called Gambas that is similar to Visual Basic with respect to creating quick GUIs for apps with a BASIC syntax of some sort.

Is that what you mean?

---

### Post by safecracker on 2005-07-30
You may want to take a look at mono as it has a  .NET implementation which is based on the ECMA standards for C# and the CLI. It's basicly a *nix implementation of the .net developer platform. Mono does support VB.NET.

---

### Post by hzs202 on 2005-07-31
Thank you both... you have anwered my question.

---

### Post by JuanC on 2005-07-31
For Visual Basic also try Python , is very powerfull and has many modules that help your work.

For VB.NET is planned to add full support in future releases of mono and also ASP.NET is full compatible with mono.

---

### Post by hzs202 on 2005-07-31
[QUOTE=JuanC]For Visual Basic also try Python , is very powerfull and has many modules that help your work.[/QUOTE]Actually, the reason I'm looking for this is because I have a class coming this next semester called Advanced Business Computing at NYU. Kind of a generic apps development class where VB and .NET are discussed and used in labs. Since I prefer working with Unices: FreeBSD Ubuntu Linux I wanted to know if there was a VB clone that I can use in Ubuntu or FreeBSD for the labs and class work.

---

### Post by safecracker on 2005-07-31
[QUOTE=hzs202]Actually, the reason I'm looking for this is because I have a class coming this next semester called Advanced Business Computing at NYU. Kind of a generic apps development class where VB and .NET are discussed and used in labs. Since I prefer working with Unices: FreeBSD Ubuntu Linux I wanted to know if there was a VB clone that I can use in Ubuntu or FreeBSD for the labs and class work.[/QUOTE]

My best advice is to use monodevelop and stetic or glade. stetic and glade are UI designers as window forms arent perfect yet in mono. It wont give you the exact same experiance but it will give you an open source .net developer platform. That being said it's still a good idea to look directly at the .net dev suite from MS if your going to be talking about it.

---

### Post by hzs202 on 2005-08-01
[QUOTE=safecracker]That being said it's still a good idea to look directly at the .net dev suite from MS if your going to be talking about it.[/QUOTE]You are 100% correct... I just wanted to have the option to write code on a Linux/BSD machine. My laptop is where I will be doing most of my work and it happens to be my development tool for the University... the laptop is a dual-boot FreeBSD/Ubuntu Linux machine.

So there you have it... my problem in a nutshell. I just installed mono. Does monodevelop come in the complete mono package I just installed?

---

### Post by safecracker on 2005-08-01
[QUOTE=hzs202]You are 100% correct... I just wanted to have the option to write code on a Linux/BSD machine. My laptop is where I will be doing most of my work and it happens to be my development tool for the University... the laptop is a dual-boot FreeBSD/Ubuntu Linux machine.

So there you have it... my problem in a nutshell. I just installed mono. Does monodevelop come in the complete mono package I just installed?[/QUOTE]

You will need to install the monodevelop and UI developer seperate monodevelop and glade2 both have packages for hoary.

---

### Post by hzs202 on 2005-08-02
[QUOTE=safecracker]You will need to install the monodevelop and UI developer seperate monodevelop and glade2 both have packages for hoary.[/QUOTE]I installed mono package which includes monodevelop. I actaully used mono to write some VB and mbas compiler worked fairly well.

---

### Post by PkT on 2005-08-10
[QUOTE=hzs202]I installed mono package which includes monodevelop. I actaully used mono to write some VB and mbas compiler worked fairly well.[/QUOTE]

Hi Guys!

And what about data access? is there a layer of ODBC or someting to access, eg. Sybase/Oracle/etc?  :roll: 

Is there any integration with office too (i mean, ms/open) writing an excel or something?  :roll: 

What should I do if my VB apps already do all of these and if I want to move them to Ubuntu Hoary? 

Thanks all!  ;-)

---

