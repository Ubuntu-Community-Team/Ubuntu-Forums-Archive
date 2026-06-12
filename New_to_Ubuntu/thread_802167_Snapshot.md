---
title: "Snapshot"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by rraj.be on 2008-05-21
could any one explain the best easy way to make system instalation back up to a live cd.

I'm new to ubuntu and hence i'm just pricking my system continousle.

I'm afraid because reinstalation takes a long time and lots of downloads.

```
I just want to make my system having all my custom along with my  applications installed,  as a live DVD.just like a snapshot.

Then whenever i want i can reinstall using my live DVD to get exact reverting as in virtual machines.
```

---

### Post by quinnten83 on 2008-05-21
i think remastersys does that, you will have to google for additional info.

---

### Post by alexandremrj on 2008-05-21
As quinnten83 said you can use remastersys

[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

Attention that this guide states that there will be no personal data so your personal files will no be saved.

Another option, that is easyer on the wallet because you won't burn cd's, it os have a ubuntu install and then place a virtual machine (search for vmware in the foruns and you will have several guides) and in this virtual machine simply play with all you want (the virtual machine will be slower that your current instalation but at least it will keep you safe).

---

### Post by rraj.be on 2008-05-21
I dont need any personal data.

i just want my personal applications which are installed on my system.

just like a live cd so that i dont want to reinstall each time and to spend days in downloading and installing each application

---

### Post by rraj.be on 2008-05-21
any one there.

plese help me.
I'm waiting for more than an hour for help

---

### Post by BDNiner on 2008-05-21
remastersys would be your best bet. I don't know of a way to create a live cd and leave personal data out. i guess you could try and move your /home directory to another partion and then run remastersys.

---

### Post by alexandremrj on 2008-05-21
Then if you don't need the personal files then follow the link i gave you above.

---

### Post by rraj.be on 2008-05-21
ok.i will try....but i'm very new to Ubuntu.

could you just list the detailed workout of sys masters.

if possible the commands used to perform.

please

---

### Post by Monicker on 2008-05-21
Actually, you have a choice between having your personal data or not.

From the site:

*It can make a full system backup including personal data to a live cd or dvd that you can use anywhere and install. It can make a distributable copy you can share with friends. This will not have any of your personal user data in it.*

---

### Post by Monicker on 2008-05-21
> **rraj.be said:**
> ok.i will try....but i'm very new to Ubuntu.

could you just list the detailed workout of sys masters.

if possible the commands used to perform.

please


Did you even go to the web site given and read it?  It gives all the commands needed.

---

### Post by rraj.be on 2008-05-21
The main problem now is how to add the ROMEO repository and how to install remastersys.

please give a way to this

---

### Post by Maestro23 on 2008-05-21
It gives you the step-by-step terminal commands.  Starting with:

The Remastersys repository needs to be added to your /etc/apt/sources.list

> sudo vi /etc/apt/sources.list

Paste the following into the sources.list:

# Remastersys
deb [http://www.remastersys.klikit.org/repository](http://www.remastersys.klikit.org/repository) remastersys/

Save and exit the file.

Update the source list using the following command

sudo apt-get update



*They are using vi as the text-editor in their directions, you can use whatever is installed on your system.  Probably gedit.  So it would be:

> gksudo gedit /etc/apt/sources.list

---

### Post by rraj.be on 2008-05-21
i cant install remastersys.

the source repository cant be found.

please give me new repository to install remastersys

---

