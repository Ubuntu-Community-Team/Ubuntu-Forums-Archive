---
title: "Study high quality source code"
date: 2006-02-08
forum: Programming Talk
---

### Post by healychan on 2006-02-08
Hello guys,

I would like to study the source code of application layer protocols such as ftp, telnet...etc

I would like to know where can I find those source code. Are they available in Ubuntu?? Do I need to download via apt???

It is the best if the program is using BSD socket.

Thanks for any help;)

---

### Post by healychan on 2006-02-09
I found some ftp source code in [this]("http://war.jgaa.com/ftp/?cmd=src") web site. You are free to download for education use.

Any ideas on where to find SMTP, POP, SSH source code ??

I searched in the Free Software Foundation but couldn't find any.........

Is there any book contains good examples of these protocols ??

Thanks

---

### Post by nixclusive on 2006-02-09
You can always check out the relevant RFC's to get the basic concept...the implementation can always be made after that. :)

[http://ietf.org/rfc.html](http://ietf.org/rfc.html)

---

### Post by sas on 2006-02-11
Make sure you have ubuntu source repositories enabled in synaptic.

Then:
sudo apt-get source openssh will download the ssh source code used in Ubuntu into your current directory. :)

Just replace "openssh" with any other program you wish to see the source for.

---

### Post by healychan on 2006-02-11
Thank you so much for your help.

I downloaded ftp and ssh already;) The source code is massive

I believe the best way to learn is to analyse the source code of high quality program. Understanding the design of such program offers me a clean vision of how people manage a large scale project.

---

### Post by Vegettex on 2006-02-11
[QUOTE=healychan]I believe the best way to learn is to analyse the source code of high quality program. Understanding the design of such program offers me a clean vision of how people manage a large scale project.[/QUOTE]I think you can also get a good idea when you try it yourself, personal experience is the best teacher imho.

---

### Post by phen on 2006-02-19
hey, this apt-get source command is awesome! i use it at the moment to take a look at octaves high speed matrix manipulation code...

what do i have to do if i wanted to change something, or add own functions? do i just have to ./configure, make and make install in the source folder? where will it save the program?

thanks!

---

### Post by sas on 2006-02-19
phen, basically yes. The exact location of the files will vary depending on the Makefile that is present in the source directory however probably it will overwrite whatever version of the program you have installed. To stop this you should be able to do something like:

make install --prefix=/usr/local/PROGRAMNAME/

This will install the program in /usr/local/ so you can keep both the program that you  have customised and the original program. You can then specify exactly which version you wish to run by giving the full path name.

---

