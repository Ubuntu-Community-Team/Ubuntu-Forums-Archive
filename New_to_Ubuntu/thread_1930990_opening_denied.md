---
title: "opening denied"
date: 2012-02-24
forum: New to Ubuntu
---

### Post by dvdbpmphry on 2012-02-24
I cannot _open_ software downloads on Ubuntu 11.10.

---

### Post by YesGood on 2012-02-24
Hi 

Type in the terminal

sudo nameofsoftware 

Luck

---

### Post by donkyhotay on 2012-02-24
Umm... more information is necessary. I wouldn't recommend blindly trying to open the file with sudo as YesGood recommended. While it *may* work, doing things with sudo can be dangerous and create problems down the road. First of all, what software download are you talking about? Are you trying to install a program in the software center? Launch a program downloaded from software center? Are you trying to access the downloads folder? Open a file downloaded from the internet? The more you tell us the better we will be able to give relevant help and advice.

---

### Post by dvdbpmphry on 2012-02-24
Thanks for the replys. I cannot open downloads from the Internet (e.g. myheritage.com).  I am new to Ubuntu, so any info you need to help solve problems, you must ask for by using " this, then this, then this". I hope you can understand me.

Dave

---

### Post by audiomick on 2012-02-24
OK, I went to myheritage.com. I landed on the German version because I live in Germany, but I don't think that is an issue.

What is offered there is a program to make a family tree. Is this what you mean? 

That program is a file that ends in .exe . This is a windows program and will not run on Linux. For that particular instance, if you really want to use that program, you will need a virtual machine with a windows on it, or simply a computer running windows.

For other things, there is possibly an alternative that runs on linux. There is one for most common uses, and also for a lot of less common things.

---

### Post by HeroOfCanton on 2012-02-24
You could try wine if you really need to run that particular program. It's not a given it will work though.

[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

---

### Post by audiomick on 2012-02-24
> **HeroOfCanton said:**
> You could try wine_.._[]("https://help.ubuntu.com/community/Wine")

Oh, yeah, forgot about that... ;)

---

### Post by enjoijesus94 on 2012-02-24
Hello 

What Are Your Trying To Install?

And Have You Tried Opening It Through Terminal?

---

### Post by donkyhotay on 2012-02-24
I didn't download it myself but from the website it looks like a genealogy program, there is a native linux genealogy program called GRAMPS which is fully compatible with GEDcom files. It's in the repo's and would be much easier to install then trying to get a windows application installed via wine. If you don't know about the repo's just do a search in the ubuntu software center for 'gramps' and that will help you download/install it automatically.

---

