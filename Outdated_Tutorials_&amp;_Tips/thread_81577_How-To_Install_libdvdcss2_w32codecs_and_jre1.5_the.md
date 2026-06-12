---
title: "How-To: Install libdvdcss2 w32codecs and jre1.5 the easy way"
date: 2005-10-24
forum: Outdated Tutorials &amp; Tips
---

### Post by manicka on 2005-10-24
Visit the [Penguin Liberation Front]("http://wiki.ubuntu-fr.org/doc/plf") and follow the instructions there for adding repositories and installing these packages from their repos.

This site provides packages for i386 users at this stage. Instructions for building packages from source for other platforms and architectures are provided as well.

PLF has been a trusted source of mandrake/mandriva packages for several years and is now starting a Ubuntu repository.

How-to also available at the [Ubuntu Document Storage Facility]("http://doc.gwos.org/index.php/Main_Page")

---

### Post by seethru on 2005-10-24
nice work manicka :)

---

### Post by vassalle on 2005-10-26
it did mention that its gonna change soon. well indeed it did i guess.. cant seem to connect to server.. 

btw, thanks for the tip manicka!

---

### Post by manicka on 2005-10-27
[QUOTE=vassalle]it did mention that its gonna change soon. well indeed it did i guess.. cant seem to connect to server.. 
[/QUOTE]
Server seems to be back up again, probably just a maintenance issue :)

---

### Post by brokejumper on 2005-10-30
Has anyone been able to connect recently?  I tried tonight with no luck....

---

### Post by manicka on 2005-10-30
No problems connecting to the server here

---

### Post by brokejumper on 2005-10-30
Thanks... I am completely new at this so it is likely user error! I'll try again.

---

### Post by brokejumper on 2005-10-30
Just got it... thanks! Now to figure out the rest of this Linux world...

---

### Post by Skebaristi on 2005-11-01
Is the antesis mirror down at the moment? At least I can't access it... Well, if someone else is experiencing same kind of problems, here's a mirror that's working, at least at the moment:

[http://plf.acnova.com/ubuntu/plf/](http://plf.acnova.com/ubuntu/plf/)

---

### Post by kahping on 2005-11-01
[QUOTE=Skebaristi]Is the antesis mirror down at the moment? At least I can't access it...[/QUOTE]

same thing on this end. i just keep getting "failed to connect" errors :-(

kahping

EDIT: scratch that. it's OK now. probably a maintenance issue like manicka said :-P

---

### Post by manicka on 2005-11-01
[QUOTE=Skebaristi]Is the antesis mirror down at the moment? At least I can't access it... Well, if someone else is experiencing same kind of problems, here's a mirror that's working, at least at the moment:

[http://plf.acnova.com/ubuntu/plf/](http://plf.acnova.com/ubuntu/plf/)[/QUOTE]

They are probably in the process of changing mirrors. Watch the main website for an announcement

---

### Post by ecobuntu on 2005-11-01
Alternatively...to get w32codecs and java visit here [http://tinyurl.com/bpxbf](http://tinyurl.com/bpxbf)
and install the packages via dpkg....i.e. dpkg -i *.deb

To get libdvdcss-
Install libdvdread3 then run this script...
sudo /usr/share/doc/libdvdread3/examples/install-css.sh

I believe libdvdread3 is installed by default and this script is also installed by default.

---

### Post by ecobuntu on 2005-11-01
Alternatively...to get w32codecs and java visit here [http://tinyurl.com/bpxbf](http://tinyurl.com/bpxbf)
and install the packages via dpkg....i.e. dpkg -i *.deb

To get libdvdcss-
Install libdvdread3 then run this script...
sudo /usr/share/doc/libdvdread3/examples/install-css.sh

I believe libdvdread3 is installed by default and this script is also installed by default.

---

### Post by MirSPCM on 2005-11-03
[QUOTE=Skebaristi]Is the antesis mirror down at the moment? At least I can't access it... Well, if someone else is experiencing same kind of problems, here's a mirror that's working, at least at the moment:

[http://plf.acnova.com/ubuntu/plf/](http://plf.acnova.com/ubuntu/plf/)[/QUOTE]

Hi !
I'm the maintainer of plf reps and mirrors.
We change content quite often, so please, if you are willing to provide a mirror, contact me mir at freecontrib dot org
If you don't won't get into offical mirroring, please don't provide unupdate unmaintained mirrors.

Thank you very much.


For those wandering if we gonna change mirrors of if it's down etc :

We actually have sync issues on some of our mirros so we provide only the main one.
But the popularity of plf grwing the load becomes enormous. thttpd which is running the reps is going down. So i'm providing ftp too. Se please use ftp instead of http if you get problems.
see wiki for details.

I'm gonna reinstall completely this server in few days maybe weeks, that should be the only change for urls. after that they should be definitiv.

Have a nice day

---

### Post by mustang on 2005-11-03
Thank you sir. I forgot to install jre on ubuntu.

Getting it now (@ 360 k/s + I might add) :)

---

