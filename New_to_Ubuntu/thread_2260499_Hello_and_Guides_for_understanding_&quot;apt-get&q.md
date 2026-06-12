---
title: "Hello and Guides for understanding &quot;apt-get&quot;"
date: 2015-01-12
forum: New to Ubuntu
---

### Post by marshall3 on 2015-01-12
Hello Everyone... 
Im completely new to Ubuntu and Linux. Going to give it a BASH (Haha... To soon?)

Im currently installing software and failing. i dont understand this " Sudo apt-get install" stuff. im used to downloading a file from the internet and double clicking it.
most my software ive followed tutorials from the web, but i would love to no what im actually doing.

i no "Sudo" is to get root user, "apt get" is something in my files that gets the software and "Install" clearly means i wont to install... but how do i no what to install for one? im guessing it just takes the filename of the program but how do i no what the filename is called and how does the computer no where to get it from.

Basically in a nutshell i was wandering weather there was a guide for this apt get stuff as ive skimmed a few Terminal books and dont see anything in them. i am also trying to learn the Terminals too as i dont understand the -b -B --- -P -p ---     stuff haha (by the way that stuff was made up lol) but ive found the sticky for that so im ok there.

oh and by the way... THANKS for reading that is!

---

### Post by Dennis N on 2015-01-12
You ask about apt-get, but here's an overview of different ways to install software you should know about:

[http://www.howtogeek.com/191245/beginner-geek-how-to-install-software-on-linux/](http://www.howtogeek.com/191245/beginner-geek-how-to-install-software-on-linux/)

Be sure to look at the linked pages as well.

For more, you could google "Linux installing software" and find many guides.

---

### Post by grahammechanical on 2015-01-12
If you want to find out about stuff use "wiki ubuntu blah bah" as a Google search term. For example, searching for "wiki ubuntu apt-get" will get you this

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

By the way, downloading and installing applications from the internet brings with it the risk that the application may contain malicious code. That is why it is best if we install applications from the Ubuntu Software Centre. Those applications have been code audited before being allowed into the software centre catalogue.

We can also right click a deb file and choose to open the file with the software centre. That can make things a bit easier.

The issue I have with using the terminal is mis-typing the commands. That happens a lot with me. We also need the correct package name. Applications have a name and also a technical package name. It is the technical name that is used with apt-get.

I hope you have two installs of Ubuntu on that machine. One install for normal use and one install for experimentation. Otherwise, you will soon learn how to re-install Ubuntu. :)

Regards.

---

### Post by Lars Noodén on 2015-01-12
Congratulations on delving into the shell.  It is the most flexible and powerful way of working with the system.  Also, anything you can do locally you can also do remotely over SSH.  

One of the first things to start with for any program is to look at the manual page using the [man](http://manpages.ubuntu.com/manpages/trusty/en/man1/man.1.html) utility.  Those will explain all the options for a program, such as what -p, -B or -R mean.  Try these in the terminal:

```

man man
man apt-get
man sudo
man sudoers
man ls

```

They won't all make sense at the beginning and they do vary in quality but they are all worth looking at and at least skimming before testing a new program or when you wonder about its capabilities.  A manual page exists for every program that you can run from the shell.  The [apt-get](http://manpages.ubuntu.com/manpages/trusty/en/man8/apt-get.8.html) package utility is a front end to the package manager and can fetch packages and package updates from a collection known as the repository.  The repository is a more or less vetted pool of programs bundled into packages, each package containing programs and connections to any other programs that it depends on.  You can read a little more here:

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)
[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)
[http://en.wikipedia.org/wiki/Software_repository](http://en.wikipedia.org/wiki/Software_repository)

The package manager, though now common, is a great advancement since it takes care of installation, updates, and removal fairly automatically.

Also, [sudo can be configured](http://manpages.ubuntu.com/manpages/trusty/en/man5/sudoers.5.html) in great detail, but for now one of the things it can do is let you run programs as root when you need to.  Michael W Lucas has a thorough book on the subject, if you're in a great hurry there.

---

### Post by marshall3 on 2015-01-12
Hey, Thanks for all the replies so quick... lots of information that im still going through at the moment. i cant belive ive never stumbled accross the Ubuntus help documentation haha. THATS ME!
i think im going to be using "MAN" quite abit now. just going to finish of all these reads and il be back. just wanted to say thanks quick.

also i have another harddrive running Windows so re installing Ubuntu isnt a problem! ive only installed it to learn anyway.

---

### Post by kerry_s on 2015-01-12
i give to you my ~/.bash_aliases

# custom alias's
alias update='sudo apt-get update'
alias upgrade='sudo apt-get upgrade'
alias search='apt-cache search'
alias show='apt-cache show'
alias install='sudo apt-get install'
alias remove='sudo apt-get purge'
alias add='sudo dpkg -i'
alias clean='sudo apt-get autoremove'
alias fix='sudo apt-get -f install'
alias purge='sudo ppa-purge'

---

