---
title: "Need help installing .tar.gz"
date: 2012-10-23
forum: New to Ubuntu
---

### Post by alexgo on 2012-10-23
I downloaded gpodder-2.20.1.tar.gz onto my desktop from here: [http://gpodder.org/src/](http://gpodder.org/src/)
I have no idea how to install it. I already extracted it. I'm a total newb to this, could some tell me what do step by step?

---

### Post by dniMretsaM on 2012-10-23
Just install gPodder from the Software Center. It's a newer version and is easier to install.

For instructions on compiling software, read [this]("https://help.ubuntu.com/community/CompilingEasyHowTo").

---

### Post by Laiquendi on 2012-10-23
There should be a file named "Install", which you should read in order to know how to install this :)

You can read full, universal instruction here:
```
http://www.ubuntugeek.com/how-to-install-source-files-in-ubuntu.html
```

---

### Post by Lars Noodén on 2012-10-23
> **alexgo said:**
> I downloaded gpodder-2.20.1.tar.gz onto my desktop from here: [http://gpodder.org/src/](http://gpodder.org/src/)
I have no idea how to install it. I already extracted it. I'm a total newb to this, could some tell me what do step by step?

I would go into the Ubuntu Software Center or Synaptic and look for [gpodder](apt:gpodder) there.  It will then install with a few clicks.  From what I see, the repositories have a recent version.  So unless you really want to, there is no need to mess with tarballs and source code.  You can get it (and keep it updated) automatically from the repository.

---

### Post by alexgo on 2012-10-23
I already have gpodder from the repository, but despite it being a newer version, it has gone backwards and no longer has the syncing functions of the gpodder I'm trying to install.

It looks difficult, but I'm going to try installing using the link dniMretsaM posted.

---

### Post by lykeion on 2012-10-23
I have tested to compile gpodder 2.20.1. It wasn't that difficult actually, only a few extra packages needed to be installed first.

Note that I'm using 12.04 and it might differ if you are using another Ubuntu version.

I guess you already downloaded and extracted the tarball.
Then start a terminal and and go to the extracted directory. If you don't know how to do this please say so and I'll explain.

Then install the needed packages like this:
```
sudo apt-get install python-feedparser python-mygpoclient
```
you can then test to run gpodder from the extracted folder with this command:
```
make test
```
If that works you can install it in the /usr folder with this command
```
make install
```

---

### Post by alexgo on 2012-10-23
In the link I mentioned I was at the ./configure part, but I can't find the configure file.

lykeion, I did the first code you mentioned and that seemed to work. When I did make test I got this:

/usr/local/src/gpodder-2.20.1$ make test
bin/gpodder --verbose
Traceback (most recent call last):
  File "bin/gpodder", line 204, in <module>
    from gpodder import gui
ImportError: cannot import name gui
make: *** [test] Error 1

---

### Post by Paqman on 2012-10-23
> **alexgo said:**
> I already have gpodder from the repository, but despite it being a newer version, it has gone backwards and no longer has the syncing functions of the gpodder I'm trying to install.

It looks difficult, but I'm going to try installing using the link dniMretsaM posted.

What version do you need? It's probably still available as a .deb in one of the repos. Check it out on [packages.ubuntu.com]("http://packages.ubuntu.com/search?keywords=gpodder&searchon=names&suite=all&section=all"). Much easier and cleaner than a nasty old tarball.

---

### Post by alexgo on 2012-10-23
Paqman, I'm currently trying to install gpodder-2.20.1

I think I've almost got it, but I can't find the configure file. Unless the .deb is super easy and fast, I'm probably better off finishing this .tar.gz file.

---

### Post by Cheesemill on 2012-10-23
Just click on the any of the links on [this]("http://packages.ubuntu.com/precise/all/gpodder/download") page to download and automatically install the 2.20.1 gpodder .deb file.

You will also need to apt pin gpodder so that it doesn't get automatically updated with the rest of your system.

---

### Post by alexgo on 2012-10-23
Paqman and Cheesemill, wow, thanks! I wish I had known about .deb earlier, it was super easy. I will bookmark that page for future reference.

Cheesemill, I put "apt pin gpodder" into the terminal and got this:

No command 'apt' found, did you mean:
 Command 'aptd' from package 'aptdaemon' (main)
 Command 'xapt' from package 'xapt' (universe)
 Command 'opt' from package 'llvm' (universe)
 Command 'apm' from package 'apmd' (main)
 Command 'atp' from package 'atp' (universe)
 Command 'ppt' from package 'bsdgames' (universe)
 Command 'apf' from package 'apf-firewall' (universe)
 Command 'apg' from package 'apg' (main)
 Command 'gpt' from package 'gpt' (universe)
 Command 'ant' from package 'ant' (main)
 Command 'ant' from package 'ant1.7' (universe)
 Command 'at' from package 'at' (main)
 Command 'pat' from package 'dist' (universe)
 Command 'aft' from package 'aft' (universe)
apt: command not found

---

### Post by Cheesemill on 2012-10-23
'apt pin' wasn't meant as a command, it's just a method of holding a package at a specific version so it never gets updated. In your case the commands would be:
```
sudo -i
echo gpodder hold | dpkg --set-selections
exit
```

---

### Post by Paqman on 2012-10-23
You can also use the graphical package management tool [Synaptic]("apt:synaptic") to pin a package to a specific version. Synaptic is quite a handy thing to have on your system, I'd recommend installing it.

Glad you were able to get it sorted alexgo. Please mark the thread as "solved" in the thread tools at the top right of this page.

---

### Post by alexgo on 2012-10-23
Cheesemill, When I put "echo gpodder hold | dpkg --set-selections" into the terminal, is it supposed do anything in the terminal? It seemed to just ignore it and setup for the next root command.

---

### Post by Cheesemill on 2012-10-23
It's not meant to show any output, you've done it correctly.
To check you can do the following to see a list of all held packages on your system:
```
dpkg --get-selections | grep hold
```

---

### Post by alexgo on 2012-10-23
It showed gpodder as being held. Thanks for all the help!

---

