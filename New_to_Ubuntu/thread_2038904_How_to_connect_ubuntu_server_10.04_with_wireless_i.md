---
title: "How to connect ubuntu server 10.04 with wireless internet"
date: 2012-08-07
forum: New to Ubuntu
---

### Post by edsh on 2012-08-07
Hi 
I am a bigineer in ubuntu , i just have install it and  now i am trying to access internet acros my ubuntu server 10.04 ,I dont know what to do,  can anybody help me with give comands for activate wireless on ubuntu [IMG]http://ubuntugeek.com/forum/Smileys/default/huh.gif[/IMG][IMG]http://ubuntugeek.com/forum/Smileys/default/huh.gif[/IMG][IMG]http://ubuntugeek.com/forum/Smileys/default/huh.gif[/IMG]?? 
best regards
waiting for a solve for u!

---

### Post by papibe on 2012-08-07
Hi edsh. Welcome to the Forums ):P

In the server edition all settings are done by editing configuration files. 

Could you post the result of these commands?
```
ifconfig

cat /etc/network/interfaces 
```
Regards.

---

### Post by edsh on 2012-08-07
Hi, thanx for your request, I dont know how to cut and paste the code put i hav attach the two photos of these commands...thanx alot
I am waiting for you!

---

### Post by papibe on 2012-08-07
Thanks.

I see that your server is a VM. 

It looks like your server is already connected to the Internet using a virtual ethernet connection. If your Windows machine is using a wireless connection, then your Ubuntu server will be using that underneath.

Let's test if the server has access to the Internet. Could you post the result of these commands?
```
nslookup ubuntu.com

dig google.com

ping yahoo.com
```
Regards.

---

### Post by edsh on 2012-08-07
Ok thank you very much...and I have think that is connect but I dont know the behavior of the sistem...although here are  the result that I take after gave your command...
I am waitng your replay....
hope for the best :) 
thanx again

---

### Post by papibe on 2012-08-07
It looks OK (although I missing the ping command).

Try updating your sources to see if they can be obtain over the Internet:
```
sudo apt-get update
```
Regards

---

### Post by edsh on 2012-08-07
Ok thanx, I just take these update ...
And now every thing is ok with internet connection...
thanks
I Have an other question... when i power of from VMware ubuntu and powe on again wat command i should take to connect to internet ...?
and the action that i take what i power of and on again are saved each time ?
Regards

---

### Post by papibe on 2012-08-07
Great!

Your are ready to use your server.

Actually, all commands we have ran were not to set anything, but to test your connection (which is fine).

You don't need to run any command for the network to work. If your host machine (Windows) is connected to the Internet, your server will have Internet access.

The only thing I would recommend is instead of powering off your server from the VM menus, turn it off using this command:
```
sudo poweroff
```
That would avoid any disk corruption.
Regards.

---

### Post by edsh on 2012-08-07
ok thanx alot
I have an ather question 
All the action that I take on vmware are saved each time when I shut don my pc, or I miss those things
Regards Edsh

---

### Post by papibe on 2012-08-07
It is *like* a real computer. If make changes they will be there next time ;)

Regards.

---

### Post by edsh on 2012-08-07
Ok thanks alot, yor are very polite :D
can I make you an other question ?
say me if I am bother you...

---

### Post by papibe on 2012-08-07
No problem. Go ahead!

---

### Post by edsh on 2012-08-07
ok thank a lot, I am bigginer in ubuntu as you can see, my questions ar like for dummies...anyway....:)
Now I want to install on ubuntu an virtualizatin platform like Xen  can you ive me any instruksion what I ought to do?

---

### Post by edsh on 2012-08-07
I read that for seeing if my hardware support VT (virtualization technology) can controll it with te command ```
 grep svm /proc/cpuinfo 
``` for my AMD platorm but as result I take nothing  that does mean that my hardware do not support VT, Van you help me to activate it from bios ?

---

### Post by papibe on 2012-08-10
Running a virtual machine inside a virtual machine is indeed possible. However note that the hardware acceleration would be provided just for the main guest machine. The rest will be 'software virtualization'.

I'm not familiar with Xen, so I would advice you to create a new thread requesting tips on how to install and configure Xen. In the meantime, take a look at his community wiki: [Xen]("https://help.ubuntu.com/community/Xen").

Regards.

---

