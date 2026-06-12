---
title: "Can't apt-get update / install / upgrade basically do anything.. Help!"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by cracka50 on 2008-06-09
I believe the issue comes from an installation that failed out..

When I apt-get update it errors out with:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

When I run dpkg --configure -a this results:

root@newserver:~# dpkg --configure -a
dpkg: dependency problems prevent configuration of dpkg-dev:
 dpkg-dev depends on libtimedate-perl; however:
  Package libtimedate-perl is not installed.
 dpkg-dev depends on patch (>= 2.2-1); however:
  Package patch is not installed.
dpkg: error processing dpkg-dev (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 dpkg-dev

What now?  I can't update anything because it outputs the first error, but I can't use dpkg or it tells me to run 
dpkg --configure -a

Help!

---

### Post by JoshuaRL on 2008-06-09
Try this one:
```

sudo apt-get install -f

```
That's another way to try to fix broken packages and dependencies, but through APT.

If that doesn't work, try going into Synaptic and seeing if it can fix your problems.  The broken packages should be in Custom Filters and the Broken filter.

---

### Post by Joeb454 on 2008-06-09
If that's a server - the OP won't be able to go into synaptic (unless they have the GUI installed of course).

@OP - Have you done any updates before now, or is this the first time you tried? If you've never tried to update, you may find that the install hasn't gone quite as well as planned :(

---

### Post by cracka50 on 2008-06-09
> **JoshuaRL said:**
> Try this one:
```

sudo apt-get install -f

```
That's another way to try to fix broken packages and dependencies, but through APT.

If that doesn't work, try going into Synaptic and seeing if it can fix your problems.  The broken packages should be in Custom Filters and the Broken filter.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem

---

### Post by cracka50 on 2008-06-09
> **Joeb454 said:**
> If that's a server - the OP won't be able to go into synaptic (unless they have the GUI installed of course).

@OP - Have you done any updates before now, or is this the first time you tried? If you've never tried to update, you may find that the install hasn't gone quite as well as planned :(

Server is a fresh install from the datacenter, however I think the version they installed was a bit outdated.. even though its Hardy... anyways, I did update it multiple times, ran into a boatload of problems, but finally got them to all update, (it updated 150+ packages or so..) anyways now I can't do anything with apt or dpkg..

---

### Post by Joeb454 on 2008-06-09
Can you post the output of ```
df -h
``` And also what happen's when you've run ```
dpkg --configure -a
``` as root?

---

### Post by cracka50 on 2008-06-09
> **Joeb454 said:**
> Can you post the output of ```
df -f
``` And also what happen's when you've run ```
dpkg --configure -a
``` as root?

root@newserver:~# df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda2              1984236    248764   1635468  14% /
varrun                 1032772        52   1032720   1% /var/run
varlock                1032772         0   1032772   0% /var/lock
udev                   1032772        48   1032724   1% /dev
devshm                 1032772         0   1032772   0% /dev/shm
lrm                    1032772     38176    994596   4% /lib/modules/2.6.24-16-generic/volatile
/dev/sda1                93307     23190     65300  27% /boot
/dev/sda8            217790660  18751300 188063352  10% /home
/dev/sda5               988084     17744    920544   2% /tmp
/dev/sda6              9714412    704460   8520376   8% /usr
/dev/sda7              9714412    339752   8885084   4% /var

df -f doesnt produce anything.. 


root@newserver:~# dpkg --configure -a
dpkg: dependency problems prevent configuration of dpkg-dev:
 dpkg-dev depends on libtimedate-perl; however:
  Package libtimedate-perl is not installed.
 dpkg-dev depends on patch (>= 2.2-1); however:
  Package patch is not installed.
dpkg: error processing dpkg-dev (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 dpkg-dev

---

### Post by Joeb454 on 2008-06-09
My mistake, I meant ```
df -h
``` :oops: And either way, it doesn't provide any answers (I thought you're drive may be full).

And it seems you need libtimedate-perl installed somehow. Do you have access to the server? If so I'd probably suggest reinstalling it, preferably with a CD burnt at a slower speed (between 1-4x)

---

### Post by cracka50 on 2008-06-09
> **Joeb454 said:**
> My mistake, I meant ```
df -h
``` :oops: And either way, it doesn't provide any answers (I thought you're drive may be full).

And it seems you need libtimedate-perl installed somehow. Do you have access to the server? If so I'd probably suggest reinstalling it, preferably with a CD burnt at a slower speed (between 1-4x)

There's no other options :( ?? Reinstalling costs money.. :(

---

### Post by Joeb454 on 2008-06-09
None that I can think of, somebody else may know of something. And if it does end up having to be reinstalled - you should be able to get it free as it was a faulty install :) I know I'd argue the case.

I'll pass the thread on to some others that may know a solution

---

### Post by iaculallad on 2008-06-09
Try:

```
sudo apt-get install --fix-missing
sudo apt-get update
```

---

### Post by Het Irv on 2008-06-09
Random Idea Warning:

Is it possible to install depenecies with something other than dpkg.  Like a manual install or force feeding it in?  How to do that is way way over my head, I don't even know if it is possible.

---

### Post by cracka50 on 2008-06-09
> **Joeb454 said:**
> None that I can think of, somebody else may know of something. And if it does end up having to be reinstalled - you should be able to get it free as it was a faulty install :) I know I'd argue the case.

I'll pass the thread on to some others that may know a solution


Thanks for your help!

---

### Post by cracka50 on 2008-06-09
> **iaculallad said:**
> Try:

```
sudo apt-get install --fix-missing
sudo apt-get update
```

root@newserver:/home# apt-get install --fix-missing
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the pr oblem.

---

### Post by cracka50 on 2008-06-09
> **Het Irv said:**
> Random Idea Warning:

Is it possible to install depenecies with something other than dpkg.  Like a manual install or force feeding it in?  How to do that is way way over my head, I don't even know if it is possible.

I could possibly try to install manually dpkg? or what do you think should I try to manually install?

---

### Post by NullHead on 2008-06-09
What were you trying to do when this started happening? Were you installing a .deb with dpkg perhaps?

---

### Post by iaculallad on 2008-06-09
What about re-installing **dpkg-dev** using Synaptics first. System->Administration->Synaptics Package Manager, and search for **dpkg-dev**, right-click on it and mark it for re-installation.

---

### Post by cracka50 on 2008-06-09
> **NullHead said:**
> What were you trying to do when this started happening? Were you installing a .deb with dpkg perhaps?

I was using apt-get to remove vsftpd, and then to reinstall it after I had removed it but, it errored out and failed and then all my problems started.

---

### Post by NullHead on 2008-06-09
> **iaculallad said:**
> What about re-installing **dpkg-dev** using Synaptics first. System->Administration->Synaptics Package Manager, and search for **dpkg-dev**, right-click on it and mark it for re-installation.

That would be: ```
apt-cache search dpkg-dev
``````
sudo apt-get --reinstall dpkg-dev
```I would also try this: ```
sudo apt-get check dpkg dpkg-dev
```

---

### Post by cracka50 on 2008-06-09
> **iaculallad said:**
> What about re-installing **dpkg-dev** using Synaptics first. System->Administration->Synaptics Package Manager, and search for **dpkg-dev**, right-click on it and mark it for re-installation.

It's Hardy Server, no gui.. I wish it were gui based, especially if it solved my problem :(

---

### Post by cracka50 on 2008-06-09
> **NullHead said:**
> That would be: ```
apt-cache search dpkg-dev
``````
sudo apt-get --reinstall dpkg-dev
```I would also try this: ```
sudo apt-get check dpkg dpkg-dev
```

root@newserver:/home# apt-cache search dpkg-dev
apt-proxy - Debian archive proxy and partial mirror builder
dpkg-dev-el - Emacs helpers specific to Debian development
svn-buildpackage - helper programs to maintain Debian packages with Subversion
dpkg - package maintenance system for Debian
dpkg-dev - package building tools for Debian

root@newserver:/home# sudo apt-get check dpkg dpkg-dev
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

sigh

---

### Post by iaculallad on 2008-06-09
> **cracka50 said:**
> It's Hardy Server, no gui.. I wish it were gui based, especially if it solved my problem :(

My error: That would be to re-install it using the terminal.

---

### Post by NullHead on 2008-06-09
> **iaculallad said:**
> What about re-installing **dpkg-dev** using Synaptics first. System->Administration->Synaptics Package Manager, and search for **dpkg-dev**, right-click on it and mark it for re-installation.

@OP: post the output of this: ```
dpkg-query -status patch
```

---

### Post by cracka50 on 2008-06-09
> **NullHead said:**
> @OP: post the output of this: ```
dpkg-query -status patch
```

root@newserver:/home# dpkg-query -status patch
dpkg-query: unknown option -t

Use --help for help about querying packages;
Use --license for copyright license and lack of warranty (GNU GPL).

---

### Post by cracka50 on 2008-06-09
> **NullHead said:**
> @OP: post the output of this: ```
dpkg-query -status patch
```


root@newserver:/home# dpkg-query --status patch
Package `patch' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.

---

### Post by NullHead on 2008-06-09
> **cracka50 said:**
> root@newserver:/home# dpkg-query --status patch
Package `patch' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.

AHH that's the problem! patch isn't installed therefore dpkg-dev can't be installed either! Lets install 'em```
sudo apt-get install patch dpkg-dev
```I would also clear the package cache first .. this might be a problem for you, but I'd run "*sudo apt-get clean*" !!!**that will clear the package cache!!!**

---

### Post by cracka50 on 2008-06-09
> **NullHead said:**
> AHH that's the problem! patch isn't installed therefore dpkg-dev can't be installed either! Lets install 'em```
sudo apt-get install patch dpkg-dev
```I would also clear the package cache first .. this might be a problem for you, but I'd run "*sudo apt-get clean*" !!!**that will clear the package cache!!!**

root@newserver:/home# apt-get clean
root@newserver:/home# apt-get install patch dpkg-dev
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
:(

Manually install maybe?

---

### Post by iaculallad on 2008-06-09
Post whatever comes out with:

```
sudo dpkg -C
```

---

### Post by JoshuaRL on 2008-06-09
It sounds like it to me.  The problem is that you need dpkg to install what you need to fix this.  For instance, you could go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and get the deb for patch and dpgk-dev, but you'll need dpkg to install them.

But you might hold off for a second to see if anyone else has an idea.

---

### Post by cracka50 on 2008-06-09
> **iaculallad said:**
> Post whatever comes out with:

```
sudo dpkg -C
```

root@newserver:/home# dpkg -C
The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 dpkg-dev             package building tools for Debian

---

### Post by cracka50 on 2008-06-09
> **JoshuaRL said:**
> It sounds like it to me.  The problem is that you need dpkg to install what you need to fix this.  For instance, you could go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and get the deb for patch and dpgk-dev, but you'll need dpkg to install them.

But you might hold off for a second to see if anyone else has an idea.

I'm almost sure if I try to use dpkg -i to install anything it will just error out with that dpkg --configure again.

---

### Post by NullHead on 2008-06-09
Well JoshuaRL has a good idea. I'd download and install patch first, then install libtimedate-perl, then dpkg-dev. So download all of those. I'll post wget links. 
[B]
libtimedate-perl:[/B]
```
wget http://mirrors.kernel.org/ubuntu/pool/main/t/timedate/libtimedate-perl_1.1600-9_all.deb
```

[B]patch: 
AMD64:[/B]```
wget http://mirrors.kernel.org/ubuntu/pool/main/p/patch/patch_2.5.9-4_amd64.deb
```
**i386:**
```
http://mirrors.kernel.org/ubuntu/pool/main/p/patch/patch_2.5.9-4_i386.deb
```
[B]
dpkg-dev:[/B]```
wget http://mirrors.kernel.org/ubuntu/pool/main/d/dpkg/dpkg-dev_1.14.16.6ubuntu3_all.deb
```

If when you're installing any of those packages and it gives you errors I'd try doing "sudo dpkg -i --force-all *packagename.deb*

---

### Post by cracka50 on 2008-06-09
> **NullHead said:**
> Well JoshuaRL has a good idea. I'd download and install patch first, then install libtimedate-perl, then dpkg-dev. So download all of those. I'll post wget links. 
[B]
libtimedate-perl:[/B]
```
wget http://mirrors.kernel.org/ubuntu/pool/main/t/timedate/libtimedate-perl_1.1600-9_all.deb
```

[B]patch: 
AMD64:[/B]```
wget http://mirrors.kernel.org/ubuntu/pool/main/p/patch/patch_2.5.9-4_amd64.deb
```
**i386:**
```
http://mirrors.kernel.org/ubuntu/pool/main/p/patch/patch_2.5.9-4_i386.deb
```
[B]
dpkg-dev:[/B]```
wget http://mirrors.kernel.org/ubuntu/pool/main/d/dpkg/dpkg-dev_1.14.16.6ubuntu3_all.deb
```

If when you're installing any of those packages and it gives you errors I'd try doing "sudo dpkg -i --force-all *packagename.deb*

Installed all of them

root@newserver:~# dpkg --configure -a
root@newserver:~# apt-get upgrade
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

---

### Post by NullHead on 2008-06-09
> **cracka50 said:**
> Installed all of them

root@newserver:~# dpkg --configure -a
root@newserver:~# apt-get upgrade
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

Well if all those packages install just fine then run "**dpkg --configure -a"** and see what happens.

---

### Post by cracka50 on 2008-06-09
> **NullHead said:**
> Well if all those packages install just fine then run "**dpkg --configure -a"** and see what happens.

nothing, it returns nothing.. :confused:

---

### Post by NullHead on 2008-06-09
> **cracka50 said:**
> nothing, it returns nothing.. :confused:

Did you run it as root? Post the output please. It could be more useful than you think ;)

---

### Post by iaculallad on 2008-06-09
Attach the output file of:

```
sudo dpkg --configure -a > error.log
```

---

### Post by JoshuaRL on 2008-06-09
Could you try this again:
```

sudo apt-get install -f

```

---

### Post by cracka50 on 2008-06-09
> **iaculallad said:**
> Attach the output file of:

```
sudo dpkg --configure -a > error.log
```

root@newserver:~# dpkg --configure -a > error.log
root@newserver:~#

I open error.log and its completely blank, nothing there.

---

### Post by cracka50 on 2008-06-09
> **NullHead said:**
> Did you run it as root? Post the output please. It could be more useful than you think ;)

yup.. see post above

---

### Post by cracka50 on 2008-06-09
> **JoshuaRL said:**
> Could you try this again:
```

sudo apt-get install -f

```

root@newserver:~# apt-get install -f
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

---

### Post by cracka50 on 2008-06-09
this got anyone stumped?

---

### Post by JoshuaRL on 2008-06-09
> **iaculallad said:**
> Attach the output file of:

```
sudo dpkg --configure -a > error.log
```

Have you tried this?  If dpkg --configure -a has run then it should have fixed the problem.  This will give the error log and we can see what else is the issue.

But this is seeming more and more like a botched install problem that can best be fixed by reinstalling.

---

### Post by cracka50 on 2008-06-09
> **JoshuaRL said:**
> Have you tried this?  If dpkg --configure -a has run then it should have fixed the problem.  This will give the error log and we can see what else is the issue.

But this is seeming more and more like a botched install problem that can best be fixed by reinstalling.

It doesn't list any errors, the log file is completely blank... 

I'm starting to think this is un-salvageable.

---

### Post by JoshuaRL on 2008-06-09
Sounds like it.  This seems like a bad install, and it would be best to redo it.  That way, you're sure it works well.

---

### Post by Het Irv on 2008-06-10
If your system is working correctly dpgk --configure -a doesn't have an output.  Have you tried to see if your problem is fixed?  It should work now.

---

