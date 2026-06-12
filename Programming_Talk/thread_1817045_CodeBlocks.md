---
title: "Code::Blocks"
date: 2011-08-02
forum: Programming Talk
---

### Post by Unpack on 2011-08-02
Ive been having a REALLY hard time installing code::blocks I've been trying to download the normal version of it, but, it seems impossible. Is there any way I can download it? It looks like Code::Blocks doesnt support Ubuntu. Im using Ubuntu 10.04 LST

---

### Post by ve4cib on 2011-08-02
I'm on 11.04, and Ubuntu is on the repos.  I can't imagine that it's a terribly new addition.  Have you already tried just running "sudo apt-get install codeblocks" in a terminal?

---

### Post by Unpack on 2011-08-02
> **ve4cib said:**
> I'm on 11.04, and Ubuntu is on the repos.  I can't imagine that it's a terribly new addition.  Have you already tried just running "sudo apt-get install codeblocks" in a terminal?
Youve gotta be kidding me! Are you serious?! Ive been at this for about an hour or so trying to install this. Can I just type whatever after that command and it will get it if its compatible? I have much to learn about ubuntu. I just installed it today and VERY new to Linux.

---

### Post by ve4cib on 2011-08-02
The way Ubuntu (and most other common Linux distributions, like Fedora, Debian, and Arch, among others) work is the organizations that create the distribution (Canonical, in the case of Ubuntu) maintain servers with all sorts of software on them.  When you run the "sudo apt-get install X" command, you're telling your package manager to go and fetch X from Canonical's servers and install it.

Generally-speaking, yes, you can use the "sudo apt-get install X" command to install almost anything you can think of.  Web browsers, games, programming environments, etc...

Another way of getting programs is to open up either the Ubuntu Software Centre, or Synaptic Package Manager, and search for what you want there and install them through a GUI.  (Behind the scenes those programs do the same thing as apt-get; download the package off the server, and install it.)

For more information on how Ubuntu handles software I suggest you read this: [https://help.ubuntu.com/10.04/add-applications/C/index.html](https://help.ubuntu.com/10.04/add-applications/C/index.html)

---

### Post by Unpack on 2011-08-02
> **ve4cib said:**
> The way Ubuntu (and most other common Linux distributions, like Fedora, Debian, and Arch, among others) work is the organizations that create the distribution (Canonical, in the case of Ubuntu) maintain servers with all sorts of software on them.  When you run the "sudo apt-get install X" command, you're telling your package manager to go and fetch X from Canonical's servers and install it.

Generally-speaking, yes, you can use the "sudo apt-get install X" command to install almost anything you can think of.  Web browsers, games, programming environments, etc...

Another way of getting programs is to open up either the Ubuntu Software Centre, or Synaptic Package Manager, and search for what you want there and install them through a GUI.  (Behind the scenes those programs do the same thing as apt-get; download the package off the server, and install it.)

For more information on how Ubuntu handles software I suggest you read this: [https://help.ubuntu.com/10.04/add-applications/C/index.html](https://help.ubuntu.com/10.04/add-applications/C/index.html)
Gotcha. Thanks!

---

