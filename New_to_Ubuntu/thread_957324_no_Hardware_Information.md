---
title: "no Hardware Information"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by olimb on 2008-10-24
Hi all
I&#8217;m trying to follow directions in troubleshooting 3.2.1 Check for drive recognition.
1, Open Device Manager (System, Preferences, Hardware Information)

My problem is there is no &#8220;Hardware Information&#8221; listed under System, Preferences

---

### Post by kpkeerthi on 2008-10-24
Lets try with command line. Open a terminal and type this command
```
lspci
```
This should print all hardware Ubuntu has 'detected'. 

You could also try 
```
lshw
```
or
```
sudo lshw
``` 
for more detailed output.

---

### Post by acidsolution on 2008-10-24
```

sudo lshw -html >pcinfo.html

```

now open the file in browser
you can see your PC configuration

---

### Post by eternalnewbee on 2008-10-24
Go to Main Menu > Add/Remove Applications and in the searchbar type: sysinfo. Select it and apply. When it's finished installing, close Add/Remove..., and go to Main Menu > System Tools > Sysinfo, and explore.
Good luck.

---

