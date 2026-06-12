---
title: "HOWTO: Easy PPPoE Connection for n00bs!"
date: 2006-08-19
forum: Outdated Tutorials &amp; Tips
---

### Post by %hMa@?b&lt;C on 2006-08-19
I will try to make this as straight foreward as possible, although I am not the greatest of explainers. This guide is due to my hours of frusteration with my PPPoE setup and with the horrible tool that is "pppoeconf"

Here is what you need: 
1: Your ISP must provide you with PPPoE (the point-to-point over ethernet protocal)
2: I have a modem, I think you need one, but a USB modem will probably not work
3: You need your ISP's username and password, in this guide for username i will use "username" and for password "password"

OK LET'S GET STARTED :KS 

Step 1, get the software!
```
sudo apt-get install build-essential
```
we will be using some software not from the Breezy Repos. it is called "roaring penguin pppoe" to download it run this from terminal.
```
wget http://www.roaringpenguin.com/penguin/pppoe/rp-pppoe-3.8.tar.gz
```
then extract it
```
tar xzf rp-pppoe-3.8.tar.gz
```
now lets enter the directory
```
cd rp-pppoe-3.8
```

Step 2, run the software!
to run the setup tool type
```
sudo ./go
```
press enter to skip all information except entering your username and password and firewall info. for username you do not need the @xxx.com from my experiences i just typed my username. for firewall you want to choose option 1

Step 3, test your internet connection!
run this 
```
sudo pppoe-start
```
if it doesnt work, go back to step 2 and make sure all of the info you put in was correct

Step 4, add PPPoE connection to startup!
you will need to make this pppoe client run with sudo without a password for a seamless connection at startup, first we need to edit out sudoers file
```
export EDITOR=gedit && sudo visudo
```
paste the following lines at the bottom of the file, replacing "username" with your username
```
username ALL= NOPASSWD: /usr/sbin/pppoe-start

username ALL= NOPASSWD: /sbin/ifconfig
```
save and exit.

next will will actually add it to startup.
at the top gnome-panel, you will need to go to 
System>Preferences>Sessions
from there go to the "Startup Programs" tab
click "Add"
paste this in
```
sudo pppoe-start
```
make the priority 50
now press "OK"
click "Add" again
paste this in 
```
sudo ifconfig lo localhost
```
again priority is 50
press "Ok"
click close
REBOOT, you should be automaticly connected to the internet!

---

