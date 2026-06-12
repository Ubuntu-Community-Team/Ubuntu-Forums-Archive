---
title: "vmware wifi sorta issue ?"
date: 2014-02-12
forum: New to Ubuntu
---

### Post by eth0up on 2014-02-12
hey guys my name is eth0up ^
so i wanted to use some airmon-ng,s  and snazz then i came across a weird but intriguing problem O.o
ok so i have ubuntu running on a vmware and i have internet and it seems to work fine but when i use iwconfig it says theres no wireless or ethernet. 
so i went through all the hassle of "re installing" my broadcam driver "since i never installed it in the first place and it was working right outa the vmware box ^ "
and then the green text hit me right after the ndiswrapper command line O.O 
i already have it installed ?
so i reached into my idea box and pulled out a taco and ate it and to my demise the taco gave no detail as to how to confront such a problem , so then i came here.
airmon-ng start eth0/wlan0/lo doesent seem to work.
when i use iwconfig says nothing is connected yet i can use the internet.
im wondering if there is some sort of vmware trickery in play here 
id like to be able to make iwconfig say my card is alive! also how do i go abouts configuring it for airmons ?
best regards ):P

---

### Post by TheFu on 2014-02-13
If that is your real name, your parents are idiots, ;)
I plan to name my kid, "delete * from users;" so my kid will be a bug in any SQL.

The real physical network adapters have ZERO do do with what VMware presents inside a VM. Also, which VMware are you running?  They make 6 different products for this with extremely different capabilities.  For example, there might be a way to pass-thru a PCI card if you are on ESXi.

---

### Post by sandyd on 2014-02-13
sorry - we dont support airmon/crack -ng here

Thread closed

---

