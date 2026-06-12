---
title: "how to install avast linux anti virus"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by ontherooftop on 2008-06-09
I am a beginner I so far just download from synaptic package manager
or use copy and paste commands in the terminal. You know how in windows
you download a program like avast and it installs and works right away,
when I download from the website I get the file and dont know how to set 
it up or get it working , like what do I do step by step , any commands
I can do in the terminal , thanks. I will get the hang of it , it just takes
some learning.  I want to install avast linux anti virus from there site but 
dont know what to do when I get the file.

---

### Post by avtolle on 2008-06-09
Download the deb package; when it is downloaded, likely on your desktop, double click it, and it should install.

---

### Post by phil66 on 2008-06-09
Avast Linux is only an on demand scanner
It will not scan real time

There are many threads in the forum stating that an anti-virus program is not needed for Linux

Search will lead you to these many post stating why they are not needed

Linux Avast has a step by step instruction on how to install and use

---

### Post by PinkFloyd102489 on 2008-06-09
You only need antivirus on Linux if you're sharing files with Windows machines.

---

### Post by azurepancake on 2008-06-09
You can also do it from terminal.

Open a terminal session, navigate to .deb file and enter:

```

sudo dpkg -i <deb package name> 

```

After running that it normally installs with no problems.

You might find a lot of interesting tips in the following website. It shows you how to install all kinds of programs in Linux and makes a wonderful reference sheet.

[How to install ANYTHING in Ubuntu]("http://monkeyblog.org/ubuntu/installing/")

Enjoy!

---

### Post by Paqman on 2008-06-09
Mind if we ask why you're installing anti-virus software? There's very few situations where you'd need to bother.

Linux anti-virus software scans for Windows viruses, it doesn't actually offer any additional protection to your machine.

---

