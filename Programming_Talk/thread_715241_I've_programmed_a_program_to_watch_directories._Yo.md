---
title: "I've programmed a program to watch directories. You wanna try it ? It'd be great."
date: 2008-03-04
forum: Programming Talk
---

### Post by dest on 2008-03-04
Hi guys.

I've programmed something to fill a personal need.
At the very beginning, I wanted to log when a user of mine downloaded some stuff with SSH.

I don't know very much about FTP server, mine is proftpd and like many others I'm sure, it logs whenever somebody download a file.

My problem with SSH (and so sftp-serv) is it doesn't log anything.

And here comes Repwatcher (my program).

You specify the directories you want to "watch". And each time a program accesses your files, it is logged into the SQL database of MySQL.

There are 2 modes :
- specified_programs, it's ONLY the programs you're interested in
- unwanted_programs, it's EVERY programs except these ones.

It can work with every programs.

I plan to make a major update soon but I'd already like some feedbacks about it, if you like it, if you have some advice,...

It's under GPL and written in OCAML.
You can read the README file to help you.

Feel free to test it, it would be really great. As it fills a need for me, I guess some of you could also be interested in Repwatcher.

The source: [http://bellier.no-ip.org/repwatcher/](http://bellier.no-ip.org/repwatcher/)

Dest.

---

### Post by dest on 2008-03-05
up !

---

### Post by seventhc on 2008-03-05
Most people here would probably want you to post the source code rather than posting a link to download the file.
:)

---

### Post by aks44 on 2008-03-05
> **seventhc said:**
> Most people here would probably want you to post the source code rather than posting a link to download the file.
:)

Most people here would probably want the OP to explain how the program works, rather than have to skim through the code to try and guess it. :p

---

### Post by dest on 2008-03-05
Hello guys !

I don't understand the matter for the sources as soon as you can have it and in a click only.

@ask44 : Have you tried to read the README file in the archive ?

---

### Post by ruy_lopez on 2008-03-05
I liked what I read until I reached the part that says it logs to MySQL. There isn't necessarily anything wrong with that. I'm just too lazy to set up a database just to test your program. Is there an option for logging to flat files?

---

### Post by aks44 on 2008-03-05
> **dest said:**
> @ask44 : Have you tried to read the README file in the archive ?

As far as I can tell, README doesn't explain *how* you monitor the filesystem... ;)

From what I understood from the code, it looks like it is polling on specific process' file descriptors.
If I'm correct about that, you have to realize that some accesses could happen without your program knowing it.

---

### Post by namegame on 2008-03-05
> **dest said:**
> 

I don't understand the matter for the sources as soon as you can have it and in a click only.



Honestly, we don't know what is in your tar.gz. I'm not saying that you would do this, but for all we know, you could have coded a virus of some sort.

For security-minded individuals, the way you present your code causes  issues.

---

### Post by Can+~ on 2008-03-05
No code posted, no download!

We should make that a rule. :KS

Now, really, most people isn't willing to download even a .tar.gz before knowing what the code is about.

---

### Post by seventhc on 2008-03-06
> **aks44 said:**
> Most people here would probably want the OP to explain how the program works, rather than have to skim through the code to try and guess it. :p
Seems  like they want the source code...as I suggested. :lolflag:

---

