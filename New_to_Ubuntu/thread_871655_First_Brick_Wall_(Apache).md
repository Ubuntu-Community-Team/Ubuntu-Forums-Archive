---
title: "First Brick Wall (Apache)"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by ingeva on 2008-07-27
I worked so long and tried so many times configuring Apache that I thought it would be best to start from scratch.

So I uninstalled apache using apt-get remove and also removed the directory /etc/apache2.

But it won't re-install. I see that there are a whole lot of files in other directories, but after all I only made changes in the .conf files.

Is there an easy way to resolve this?

---

### Post by dominiquec on 2008-07-27
Have you tried

```
sudo apt-get purge apache2
```

---

### Post by ingeva on 2008-07-27
> **dominiquec said:**
> Have you tried

```
sudo apt-get purge apache2
```


Did now -- didn't help. The extra files are in many different directories and it would take a long time to remove tham manually -- but I can't imagine that being necessary. There must be some way to make the system realize that a new install is needed?

---

### Post by spiderbatdad on 2008-07-27
please try:
```
sudo dpkg --purge apache2
sudo apt-get autoremove
```

---

### Post by ingeva on 2008-07-27
> **spiderbatdad said:**
> please try:
```
sudo dpkg --purge apache2
sudo apt-get autoremove
```

Did that. No change.

Here's what I get trying to re-install:
```
# apt-get install apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  apache2
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/44.6kB of archives.
After this operation, 102kB of additional disk space will be used.
Selecting previously deselected package apache2.
(Reading database ... 114290 files and directories currently installed.)
Unpacking apache2 (from .../apache2_2.2.8-1ubuntu0.3_all.deb) ...
Setting up apache2 (2.2.8-1ubuntu0.3) ...
# cd /etc/apache2
cd: 5: can't cd to /etc/apache2
#
``` 

Should I give up and install the server version instead?

---

### Post by spiderbatdad on 2008-07-27
I don't think you should give up and install the server version, though of course, it is your decision to make. Something seems wrong with the environment...idk, but it was not a no such file or directory error, rather it was "can't cd to /etc/apache2."
I must admit I have not seen that error. Why install apache logged in as root rather than using sudo? How did you become root...sudo -i, or something crazy like sudo su?

---

### Post by eightmillion on 2008-07-27
Could you try this?

> sudo dpkg -P apache2-common apache2

sudo apt-get install apache2-common apache2

---

### Post by spiderbatdad on 2008-07-27
> **eightmillion said:**
> Could you try this?

+1 regarding apache2-common...also using the package manager graphically may sound "low tech" but I often see other packages, like apache2-common that I may have forgotten about.

---

### Post by eightmillion on 2008-07-27
Yeah, that package could also be apache2.2-common.

---

### Post by eightmillion on 2008-07-27
apache2.2-common does contain the config files. I just checked.

---

### Post by ingeva on 2008-07-27
> **spiderbatdad said:**
> I don't think you should give up and install the server version, though of course, it is your decision to make. Something seems wrong with the environment...idk, but it was not a no such file or directory error, rather it was "can't cd to /etc/apache2."
I must admit I have not seen that error. Why install apache logged in as root rather than using sudo? How did you become root...sudo -i, or something crazy like sudo su?

I realize that removing the /etc/apache2 directory was not a smart thing to do.... :)

I used the shell in su mode... easier than typing sudo again and again.

None of the present tips have helped. The install seems to go fine but necessary files are still missing.

I guess I can try something else: Install Ubuntu on another computer and copy the missing files from it. That way I won't have to re-install everything.

---

### Post by spiderbatdad on 2008-07-27
> **ingeva said:**
> I realize that removing the /etc/apache2 directory was not a smart thing to do.... :)

I used the shell in su mode... easier than typing sudo again and again.

None of the present tips have helped. The install seems to go fine but necessary files are still missing.

I guess I can try something else: Install Ubuntu on another computer and copy the missing files from it. That way I won't have to re-install everything.

to gain a root session in user space:```
sudo -i
```

to fix apache: simply open your package manager and completely remove apache2 and apache 2.2-common...any other apache2 packages...or mark them for reinstallation. That should fix the problem.

---

### Post by eightmillion on 2008-07-27
If you just installed apache2.2-common, the package should be in you apt cache. Do this...
```

cd ~
mkdir tmp
cp /var/cache/apt/archives/apache2.2-common_2.2.8-1ubuntu0.3_i386.deb ~/tmp
cd ~/tmp
dpkg --fsys-tarfile apache2.2-common_2.2.8-1ubuntu0.3_i386.deb | tar xf -
sudo cp -r ./etc/apache2 /etc
cd ..
rm -rf ./tmp

```

---

### Post by spiderbatdad on 2008-07-27
you could also make the directory yourself and copy the config files from this thread:[http://ohioloco.ubuntuforums.org/showthread.php?t=871142](http://ohioloco.ubuntuforums.org/showthread.php?t=871142)
of course make sure root owns the apache2 directories and files

---

### Post by ingeva on 2008-07-27
> **spiderbatdad said:**
> to gain a root session in user space:```
sudo -i
```to fix apache: simply open your package manager and completely remove apache2 and apache 2.2-common...any other apache2 packages...or mark them for reinstallation. That should fix the problem.

OK, thanks!
The package manager was new to me, so I had no idea.

But only one directory and one file appeared in the (new) /etc(apache2 directory.

Trying to use apt-get install again, I get this message:

apache2 is already the newest version

When trying to start apache I get this:

```
inge@Pantera:/etc$ sudo init.d/apache2 restart
 * Restarting web server apache2                                                .: 197: Can't open /etc/apache2/envvars
ERROR: APACHE_PID_FILE needs to be defined in /etc/apache2/envvars
apache2: Could not open configuration file /etc/apache2/apache2.conf: No such file or directory
                                                                         [fail]
inge@Pantera:/etc$ 

```

---

### Post by eightmillion on 2008-07-27
Try this...
> apt-get install --reinstall apache2.2-common

---

### Post by ingeva on 2008-07-27
Whatever ...  Thanks for all help!

I now got this:

```
$ sudo init.d/apache2 restart
 * Restarting web server apache2                                                apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]
inge@Pantera:/etc$ 

```

so I'm back to square one and all I need to do now is to define all the virtual hosts (which is what I wanted to do in the first place! :)

The usefulness of this forum is tremendous.
You seldom see anything like it.

Thanks!

---

