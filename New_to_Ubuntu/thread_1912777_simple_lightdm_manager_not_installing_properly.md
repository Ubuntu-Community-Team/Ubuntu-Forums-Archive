---
title: "simple lightdm manager not installing properly?"
date: 2012-01-21
forum: New to Ubuntu
---

### Post by arun_nr on 2012-01-21
im using ubuntu 11.10
and i tried to install simple light dm manager and got this error while doing sudo

arun@ubuntu:~$ sudo apt-get install simple-lightdm-manager
[sudo] password for arun: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 


how could i install properly?

---

### Post by kazztan0325 on 2012-01-21
It is not a problem due to install "simple-lightdm-manager".

Maybe your previous installing some software or updating some packages have not completed yet.

You would have to run the command 'sudo dpkg --configure -a' with Terminal to correct the problem first, then you would be able to install "simple-lightdm-manager".

---

### Post by arun_nr on 2012-01-21
nothing comes i have done  that earlier!

arun@ubuntu:~$ sudo dpkg --configure -a
arun@ubuntu:~$

---

### Post by kazztan0325 on 2012-01-21
Then did you get same error message when you tried to install "simple-lightdm-manager" again?

---

### Post by jerrrys on 2012-01-21
There is no simple-lightdm-manager in my 11.10 repository.  Where you finding this?

Edit: nevermind; its a PPA

Edit#2:  is this how you installed it?

sudo apt-add-repository ppa:claudiocn/slm
sudo apt-get update
sudo apt-get install simple-lightdm-manager

Edit#3:  in terminal, try:

sudo apt-get install -f

---

### Post by arun_nr on 2012-01-21
got this message now


arun@ubuntu:~$ sudo apt-get install -f
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by jerrrys on 2012-01-21
You have a package manager open; close it.

---

### Post by jerrrys on 2012-01-21
Also should mention that if you use the software center as your package manager that there are better ways to keep track of your PPA's. I use synaptic package manager for this and many other things.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9)

And also ppa-purge may help you in the future.

[ATTACH]211261[/ATTACH]

---

