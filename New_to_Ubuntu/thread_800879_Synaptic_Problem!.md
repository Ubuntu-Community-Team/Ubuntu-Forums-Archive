---
title: "Synaptic Problem!"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by Sakss on 2008-05-20
I try to open synaptic but i get the following message

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


i run the command in terminal but i get this message.

dpkg: parse error, in file `/var/lib/dpkg/updates/0093' near line 1:
EOF

`93bd2f464b83f4_31bf3856ad364e35_6.0.6001.18000_no ne_7934ad96f0145855.manifest (first line of 0093)

this is the error in terminal.

Any ideas?I tried many many ways but nothing worked.

Thanks!

---

### Post by pedro_orange on 2008-05-20
Try:

```
sudo dpkg --configure -a
```

---

### Post by Sakss on 2008-05-20
> **pedro_orange said:**
> Try:

```
sudo dpkg --configure -a
```

I ran this command and i get the same message as above....

---

### Post by pedro_orange on 2008-05-20
Hmmmm....

Try the following two commands:

```
sudo apt-get clean
```

```
sudo apt-get update
```

And then try and open Synaptic again.

---

### Post by Sakss on 2008-05-20
> **pedro_orange said:**
> Hmmmm....

Try the following two commands:

```
sudo apt-get clean
```

```
sudo apt-get update
```

And then try and open Synaptic again.

Well, i ran the first command but nothing posted in terminal

I ran the second command and


Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy Release.gpg
Ignore [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy/main Translation-el
Ignore [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy/restricted Translation-el
Ignore [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy/universe Translation-el
Ignore [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy/multiverse Translation-el
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy-updates Release.gpg
Ignore [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy-updates/main Translation-el
Ignore [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy-updates/restricted Translation-el
Ignore [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy-updates/universe Translation-el
Ignore [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy-updates/multiverse Translation-el
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy Release
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy-updates Release
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy/main Packages              
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy/restricted Packages        
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy/main Sources
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy/restricted Sources
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy/universe Packages
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy/universe Sources
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy-updates/multiverse Sources
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

 I ran the dpkg --configure-a and i get the first error EOF and and

---

### Post by pedro_orange on 2008-05-20
apt-get clean won't spam you anything; it just does its job!

You have got Synaptic and Add/Remove closed when you're trying to run this yes?

Ok, lets try a:

```
sudo dpkg --clear-avail
```

Then redo the apt-get clean and update.

Also could have a go at:

```
sudo dpkg --update-avail
```

---

### Post by Sakss on 2008-05-20
> **pedro_orange said:**
> apt-get clean won't spam you anything; it just does its job!

You have got Synaptic and Add/Remove closed when you're trying to run this yes?

Ok, lets try a:

```
sudo dpkg --clear-avail
```

Then redo the apt-get clean and update.

Yes synaptic,add/remove are not open.

I try these 3 commands but nothing happened.The same error as above with hit,ignore ...



I ran the last command and i get the following message

dpkg: &#951; --update-avail demands one exactly parameter one file Packages (something like that because i dont have english in terminal)

and some help commands for help etc

---

### Post by pedro_orange on 2008-05-20
Can you stick the contents of the following 2 files in paste bins for me to look at please?

/etc/dpkg/dpkg.conf
/var/log/dpkg.log

---

### Post by Sakss on 2008-05-20
> **pedro_orange said:**
> Can you stick the contents of the following 2 files in paste bins for me to look at please?

/etc/dpkg/dpkg.conf
/var/log/dpkg.log


/var/log/dpkg.log
:2008-05-14 01:49:42 upgrade gnome-system-monitor 2.22.0-1ubuntu3 2.22.1-0ubuntu1
2008-05-14 01:49:42 status half-configured gnome-system-monitor 2.22.0-1ubuntu3

after tha many #########

I dont have file 
/etc/dpkg/dpkg.conf only .cfg

---

### Post by Ryadt on 2008-05-20
have a look at this tutorial 
[http://ubuntuforums.org/showthread.php?t=140920&highlight=junk](http://ubuntuforums.org/showthread.php?t=140920&highlight=junk)

hope it helps

---

### Post by Sakss on 2008-05-21
Someone to help?

The problem is rather serious.

@Ryandt.

Nope,that guide didnt help.I have errors in many commands

E:dpkg etc

---

### Post by Xiong Chiamiov on 2008-05-21
I'm curious.  I did a [brief Google search]("http://www.google.com/search?hl=en&q=%22dpkg%3A+parse+error%22&btnG=Google+Search"), but that brought to mind the fact that you're getting an EOF (end of file) error.

Can you please post the output of 
```

cat /var/lib/dpkg/updates/0093

```
Also, let's try moving that file away and see what happens:
```

sudo mv /var/lib/dpkg/updates/0093 ~/0093

```

---

### Post by Sakss on 2008-05-21
> **Xiong Chiamiov said:**
> I'm curious.  I did a [brief Google search]("http://www.google.com/search?hl=en&q=%22dpkg%3A+parse+error%22&btnG=Google+Search"), but that brought to mind the fact that you're getting an EOF (end of file) error.

Can you please post the output of 
```

cat /var/lib/dpkg/updates/0093

```
Also, let's try moving that file away and see what happens:
```

sudo mv /var/lib/dpkg/updates/0093 ~/0093

```
 

I move that file away and the EOF was on 0094 so i continue to 0101(last files on the folder with the same problem) and synaptic now works.


Synaptic works,and i l download the updates but i cant install them.

I get the error message




E: /var/cache/apt/archives/libglib2.0-0_2.16.3-1ubuntu1_i386.deb: files list file for package `gnome-system-monitor' is missing final newline

---

### Post by Matt640 on 2008-05-23
Hey.
I'm sorta having the same problem here only the cause was something different. I'm using the ordinary Desktop Edition of Ubuntu 8.04 not the 64AMD one. So I read from the Forums that by installing Sun Java 6, I can get my FrostWire up and running again. So I use my SPM to find it and download it. In the middle of Download/Installing, it hanged/jammed and my only option was to reboot. After I did, I realize that I can't open my SPM and it ask me to manually run sudo dpkg --configure -a. When I do, this turns up:
Setting up sun-java6-doc (6-06-0ubuntu1) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] 

As you can see, I'm in desperate need of HELP! Can anyone encrypt this for me?

---

### Post by Sakss on 2008-05-26
> **Sakss said:**
> I move that file away and the EOF was on 0094 so i continue to 0101(last files on the folder with the same problem) and synaptic now works.


Synaptic works,and i l download the updates but i cant install them.

I get the error message




E: /var/cache/apt/archives/libglib2.0-0_2.16.3-1ubuntu1_i386.deb: files list file for package `gnome-system-monitor' is missing final newline

Somebody to help plz!

Thanks a lot! :(

---

### Post by sayakb on 2008-05-26
> **Sakss said:**
> I try to open synaptic but i get the following message

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


i run the command in terminal but i get this message.

dpkg: parse error, in file `/var/lib/dpkg/updates/0093' near line 1:
EOF

`93bd2f464b83f4_31bf3856ad364e35_6.0.6001.18000_no ne_7934ad96f0145855.manifest (first line of 0093)

this is the error in terminal.

Any ideas?I tried many many ways but nothing worked.

Thanks!

Open the file /var/lib/dpkg/updates/0093 in gedit (open it as root) and add a # at the beginning of line1.

---

