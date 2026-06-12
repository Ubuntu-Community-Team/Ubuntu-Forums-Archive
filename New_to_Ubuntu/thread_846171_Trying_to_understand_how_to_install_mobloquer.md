---
title: "Trying to understand how to install mobloquer"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by Cylonraider6 on 2008-07-01
Hi
  Ive been trying to install mobloquer now for nearly 2 months.
Ive been looking though hundreds web pages saying that its easy
but because ive been a windows user for nearly 10 years plus im
finding it very very hard to install.Ie it always says this that
and the other is missing.When try to find the missing this that
and the other I can never find what im looking for.
Ive kept the os (8.0.4 LTS) upto date.
Some how ive managed to install Moblock.Which I think works ok
done all the "sudo moblock-control what ever" tests.But I cannot
install the Mobloquer GUI for this program.
Is there an very easy way of installing this GUI.

                 Thanks

---

### Post by Hospadar on 2008-07-01
First, add some repositories, edit your sources.list file.  From a terminal:```
gksu gedit /etc/apt/sources.list
```Add this to the end of the file:```
deb http://moblock-deb.sourceforge.net/debian hardy main
deb-src http://moblock-deb.sourceforge.net/debian hardy main
```Save and close gedit, back to the terminal, add the gpg key for the moblock repository and update apt```
gpg --keyserver wwwkeys.eu.pgp.net --recv 9072870B
gpg --export --armor 9072870B | sudo apt-key add -
sudo apt-get update
```now install the packages```

sudo aptitude install moblock
sudo aptitude install mobloquer
```

Found the instructions here:
[http://moblock-deb.sourceforge.net/](http://moblock-deb.sourceforge.net/)

---

### Post by Cylonraider6 on 2008-07-01
Thanks for the instructions.But ive been down this path before.I got the same result last time I did this.
This the text I get when it says its finished:-  



2:~$ sudo aptitude install mobloquer
[sudo] password for me: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Writing extended state information... Done
Building tag database... Done             
No candidate version found for mobloquer
No candidate version found for mobloquer
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      

What the hell am I doing wrong?

---

### Post by jre on 2008-07-02
Did you do the
```
sudo aptitude update
```
?

If yes and you still have the problem please post your /etc/apt/sources.list, 
/etc/apt/apt.conf and /etc/apt/preferences (if they exist).

Do you find mobloquer in the graphical software installer (synaptic or something like that. Some Ubuntu guy has to tell how to get there)?

jre

---

### Post by Cylonraider6 on 2008-07-05
Many thanks jre

But I gave up on this one far to much messing around and found another ip blocker.It worked almost right away with all the packages and Debian installer all ready to go.It gets the iplists from the same place as moblock.
Or so ive been led to belive.The app its self is called IPblock from sorceforge.Plus the GTK bittorent client (Deluge Writen in Python and C++)  im using also has an ipblocker built in.
But any way thank you for time.

---

### Post by jre on 2008-07-07
Yes, I know IPBlock. Indeed it does the same as MoBlock and also uses lists from bluetack, so you will be fine.

---

