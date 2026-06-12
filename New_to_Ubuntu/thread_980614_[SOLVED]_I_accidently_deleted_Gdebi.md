---
title: "[SOLVED] I accidently deleted Gdebi"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by shiningkenmonster on 2008-11-13
I had some error installing skype. So Someone gave me this link on the forum to try to update my Gdebi and to try to install the skype again.

the person gave me the following link:

Gdebi update:

[http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-netbook-remix/main/binary-lpia/gdebi-core_0.3.8netbook1_all.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-netbook-remix/main/binary-lpia/gdebi-core_0.3.8netbook1_all.deb)

crap, i think i accidentally deleted the Gdebi

i downloaded that link. and it was installing. than it asked me to type something in the terminal.

something like:

sudo apt install -a

sorry, i only remember some of it. it was something like that along the line.

It was installing. but than it asked me to delete Gdebi and would you like to continue. I typed in Y for Yes, and it deleted it. (i thought it was asking me to delete the old Gdebi software.)

anyways, than I tried to install a program but it opens with the Archive Manager.

when i right click on the file, it doesn't show the "GDebi package installer" - like it used to before

only shows Archive Manager.

I tried to play around with it on my own. but i'm screwed.

is there a way to have back GDebi Packager installer again?

---

### Post by shifty_powers on 2008-11-13
you should just be able to open a terminal and type

```
sudo apt-get install gdebi
```

---

### Post by bhadotia on 2008-11-13
```
sudo apt-get install gdebi
```

You can also install the .deb file through the terminal:
```
sudo dpkg -i whatever.deb
```

---

### Post by shiningkenmonster on 2008-11-13
i typed that in:

sudo apt-get install gdebi

than this shows up in the terminal

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gdebi: Depends: gdebi-core (= 0.3.8) but 0.3.8netbook1 is to be installed
E: Broken packages

---

### Post by bhadotia on 2008-11-13
Open synaptic (System>Administration>Synaptic..) click on custom filters button on the bottom left. Then, click on broken packages filter on the left side. If broken packages show up remove them all. Then open the terminal and type (this just for making sure that you don't have any other problem):
```
sudo dpkg-reconfigure -a
```
 and then try:
```
sudo apt-get install gdebi
```

---

### Post by shiningkenmonster on 2008-11-14
thanks! gosh jerk! How come you didn't tell me 
sudo dpkg-reconfigure -a 
takes HOURS!!

yeah, i got the gDebi to work

i think i did a
 sudo dpkg autoremove
or whatever is the closest. it solved it.

sudo dpkg-reconfigure -a 
was unnecessary to do. and what a waste of time. I hope i wouldn't do it again.

but thanks again for the gDebi install command

---

