---
title: "shraring folders with xp"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by hammeraxe on 2008-07-25
ive been trying to set up folder sharing with xp using samba

i got it working after a bit of tinkering following this thread
[http://ubuntuforums.org/showthread.php?t=304131](http://ubuntuforums.org/showthread.php?t=304131)

i can see all my ubuntu shared folders from xp

there is a problem though

i have shared one folder from my WinXP laptop and then theres the default SharedDocs. from ubuntu i see one more mysterious folder C$. 
```

majas@majas:/media/network/WORKGROUP/408VZ$ ls
C$  Edgars  SharedDocs

```
i cannot view or edit any files in the folder i shared or the C$ folder: permission denied even for root although when creating my mountpoint folder i set all the permissions to Read&Write. only the SharedDocs folder works properly.

how to fix this?

---

### Post by boblemur on 2008-07-25
the c$ is an administrative share on windows, every drive should have one... hard disk that is, cd drives usb sticks etc wont...

but they should all have them, if you login as an administrator with the xp username and password you should be able to edit the files within those shares....

note that the $ at the end of any share will make it hidden( in xp at least) so for example... if you go myhiddenshare$ for one of your shares, browsing the computer from another windows machine will not show your hidden share... however if you try and map the share... and use say \\computername\myhiddenshare$ it will be accessible...

with your networking in general, xubuntu isnt really that great with networking (in my experience) maybe i didnt try hard enough but still was a battle for me

because xubuntu dosent have a network browser (as far as i know) that will be annoying, but you can add one...


so basically make sure that you have put in the XP username and pw not your ubuntu one... (you will need an admin account to access the c$ one)

and if that dosent work, then try turning simple file sharing off in windows (that causes some seriously strange errors)

---

### Post by BDNiner on 2008-07-25
Yes the c$ is the root of the C drive on your windows computer. It doesn't show up when using a windows only environment but you can still access it. you need admin rights to access that share, so using the admin login and password for your windows computer should open the share so you can browse it.

---

### Post by hammeraxe on 2008-07-25
i did set up network browsing with thunar as described in the above mentioned thread

the thing is that i dont care about that C$
all i need is my Edgars folder but it cannot be accessed for some reason

---

### Post by BDNiner on 2008-07-25
did you add your account to the samba users group? that is the only thing i could see stopping you from accessing the share

---

### Post by victorbrca on 2008-07-25
Try this on Windows...


1- Add an account with the same username and password that you have on Linux
2- Right click on Edgars and select properties
3- Go into sharing tab and add full access to the user you just created
4- Go into security tab and add full access to the user you just created

That might resolve it!!

---

