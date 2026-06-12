---
title: "[SOLVED] Install a Package"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by subai on 2008-10-26
Hi there
I'm absolute newbie about Linux & ubuntu , can anybody tell me how to install a package in ubuntu , I've tried 
```
sudo apt-get install *packageName*
```
but it couldn't find the packages, should I download package and copy it in a specific folder? 
how i can install a package?
thx in advance?

---

### Post by bulldog on 2008-10-26
The most practical manner is to use synaptic packet manager.
You'll find it in your menu.
If the package you want to install is in the repositories,you can use the terminal as well.

---

### Post by subai on 2008-10-26
thank u for your reply, my first big problem is I'm using Ubunto server with no GUI (I'm a terminal fan indeed) but when you don't know anything about ubuntu it could be some sort of pain. I've read some manuals and run Apptitude but I can't figured out how to install a simple package,ummmmm and I don't know what the "synaptic packet manager" is.:(
is there a step by step complete newbie guide to install a package?
thx

---

### Post by teaker1s on 2008-10-26
Save yourself a lot of pain your best bit of advice is to install a gui and use "webmin" to configure your server.
For those who complain about gui taking precious system resources-shut it down after you have finished.

Secondly apt-get,synaptic or whatever package manager you use is only as good as sources list,plus you want to 
update sources prior to looking for a package

---

### Post by subai on 2008-10-27
thx for your time,

---

### Post by jespdj on 2008-10-27
The "sudo apt-get install ..." command you gave is correct, but you do have to specify the exact package name. On [http://packages.ubuntu.com/](http://packages.ubuntu.com/) you can search what packages are available in the Ubuntu repositories.

If you specified a correct package name and it doesn't work, try
```
sudo apt-get update
```
and try again after that.

---

### Post by hyper_ch on 2008-10-27
> **teaker1s said:**
> Save yourself a lot of pain your best bit of advice is to install a gui and use "webmin" to configure your server.
For those who complain about gui taking precious system resources-shut it down after you have finished.
You mean purging all that stuff it installs? Yet again, there's no reason why you need a full-fledge gui on a server - just give me one... editing config files is no different on a gui or command line. Also "webmin" makes administrating things easy however the learn process will be lost. If you encounter any problems you still won't be able to get a solution.

As the others have said, the packages found depends on what you have in your sources.list file. Furthermore if you alter the sources.list you'll also need to update it. The command for that was already given.

When you don't know a package name, you can search for it:
```

sudo apt-cache serach KEYWORD

```
This will search the package name and description. If you want to modify it, have a look at the manpages.

Furthermore, if something complains about a specific file missing, you can use "apt-file" for that:
```

sudo apt-get install apt-file
sudo apt-file udate

```
and then finally search
```

apt-file search FILENAME

```
It's very handy when you compile and it's complaining about missing files.

---

### Post by teaker1s on 2008-10-27
no I mean shutting down xserver after you have finished config to free up system resources-if you need to alter something start xserver again

---

### Post by hyper_ch on 2008-10-27
still there is no compelling reason to install xserver in first place.

---

### Post by teaker1s on 2008-10-27
we will have to agree to disagree,
 I believe that webmin offers an easy way to configure a server for a new user.
If the person is happy with commandline only then thats okay too

---

### Post by subai on 2008-10-28
thanks for your time & reply, I'm at the level zero and just started reading documents that **teaker1s **has their links in his signature(thx for that too), the machine that I running ubuntu server on it does not connect to internet , I opened sources.list and saw the Urls  so guessed may it is because of lack of internet then tried the apt-cdrom command and then apt-get update, and finally the package installed

having command line make me to go and learn about packages and repository, that make joy of learning sweeter

---

