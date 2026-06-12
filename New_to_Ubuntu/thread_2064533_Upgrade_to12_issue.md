---
title: "Upgrade to12 issue"
date: 2012-09-29
forum: New to Ubuntu
---

### Post by unabletosync on 2012-09-29
I am a complete nube to Unbuntu. When I downloaded the upgrade to v.12 it went through all of the steps fine, no errors during, but when restarting it stops booting at the Ubuntu title screen and will not go any further. 
I don't want to make things worse... Anyone have a solution?

---

### Post by josephmills on 2012-09-29
After the title screen goes away can you press ctrl+alt+f1 
then log in. (if you can) 
then type in 
```
sudo apt-get install pastebinit 
```
then you are going to use pastebinit to paste some output so we can see what is going on with you computer. When using pastebinit it will return a link You are going to want to write down each link so that you can Put them here for us to see.
 
so after logged in (again if you can with ctrl+alt+f1)  Please enter in these commands and save the link that is outputted to you thanks 
```
lspci -vnn | pastebinit
```
```
lsmod | pastebinit 
```

then put the links here for se to do some debugging work. Thanks

---

### Post by unabletosync on 2012-09-29
Well, I just bought this computer used and I do not know the login.
It is a Dell Inspiron 1526.
 
Above the login prompt there is "Ubuntu 12.04.1 LTS dell-laptop ttyl", if that helps...

---

### Post by unabletosync on 2012-09-29
Got in!
Entered the sudo apt command, then confirmed Y to install new packages then this:
 
[FONT=Courier New]Err http:us.archive.ubuntu.com/ubuntu/ precise/main python-cionfigobj all 4.7.2+ds-3build1[/FONT]
[FONT=Courier New]Could not resolve 'us.archive.ubuntu.com'[/FONT]
 
then goes on to list a long [FONT=Courier New]Failed to Fetch [/FONT][FONT=Tahoma]script.[/FONT]

---

