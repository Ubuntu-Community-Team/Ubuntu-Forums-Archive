---
title: "broke repository, please help."
date: 2006-05-11
forum: Repositories &amp; Backports
---

### Post by skudmunky on 2006-05-11
When I try to install something new, like samba server, I get this error message in the terminal:

W: Couldn't stat source package list cdrom://Ubuntu 5.10 _breezy badger_ - Release i386 (20051013) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fbreezy%20badger%5f%20-%20Release%20i386%20(20051013)_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
 W: Couldn't stat source package list cdrom://Ubuntu 5.10 _breezy badger_ - Release i386 (20051013) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fbreezy%20badger%5f%20-%20Release%20i386%20(20051013)_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
 W: You may want to run apt-get update to correct these problems

and when I run apt-get that doesn't find the correct file or something.

I tried to look around and fix it, but I'm guessing I have a mistake in repository. If someone could give me the correct string of code to replace that with, that would be great. (if it works)

Thanks in advance.

---

### Post by louis_nichols on 2006-05-11
there isn't a real mistake. It's just that your sources list is configured to search for packages on the install cd too. Do the following:

1. backup the file we'll be editing:

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
```

2. open it for editing as root:

```
sudo gedit /etc/apt/sources.list
```

3. search all lines that start with *deb cdrom* or *deb-src cdrom* and put a # in front of them, to comment them out.

4. Run a ```
sudo apt-get update
``` and you're good to go again

---

### Post by mjm115 on 2006-05-11
Can you please paste the contents of your source.list file?  It can be found in /etc/apt/sources.list

It looks as if it is looking for the file off of your installation CD, instead of the repository.

**EDIT:**  Nevermind,  louis_nichols beat me to it.

---

### Post by skudmunky on 2006-05-11
Hey, thanks guys. I'll go try that. I thought it was trying to get it off the CD, but I tried putting the CD in and that did nothing.

I'll try the suggestions now.

edit, it's not complaining anymore. Thanks a ton guys!

---

