---
title: "Broadcom wireless won't turn on"
date: 2012-11-25
forum: New to Ubuntu
---

### Post by noveny on 2012-11-25
I am new to Ubuntu.  My processor is an AMD 64 MIL 28.  I have a Broadcom BCM 4318.  Here is what i get:

eelkins@ubuntu:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

I have tried to load the BCMxx drivers but still have no luck.  Any assistance would be GREATLY appreciated.

Thanks

---

### Post by carl4926 on 2012-11-25
With a wired connection install rfkill and then post result of

```
rfkill list
```

Your device needs the firmware of course which is done with:

```
sudo apt-get install firmware-b43-installer
```

---

### Post by NikTh on 2012-11-25
Hi , 

Please open a terminal (CTRL+ALT+T) and execute bellow commands with order. (_Active Internet connection required_)

```
wget "http://ubuntuone.com/1kKCgeRTZHszxUdsSEekYz" -O ~/wirelessinfo
chmod +x wirelessinfo
sudo ./wirelessinfo
```The last command will produce a file named **netinfo.txt** inside your /home folder.
Click on **"New Reply"** and attach the file. [See here on how to attach a file]("http://i.stack.imgur.com/0E6qS.png") 

_Above is a script for debugging proposes. All your sensitive-personal data are hidden for security reasons. _

Thanks

---

### Post by noveny on 2012-11-28
null

---

### Post by noveny on 2012-11-28
Here is the results after typing rfkill list:

eelkins@ubuntu:~$ rfkill list
0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
eelkins@ubuntu:~$ rfkill list
0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
eelkins@ubuntu:~$ rfkill list
0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
eelkins@ubuntu:~$ 


The difference occurs after I toggle between turning the wifi switch on  and off.  It appears to know I have wifi, but the little wifi light on  my laptop will not turn on

---

### Post by noveny on 2012-11-28
> **carl4926 said:**
> With a wired connection install rfkill and then post result of

```
rfkill list
```

Your device needs the firmware of course which is done with:

```
sudo apt-get install firmware-b43-installer
```
It looks like I already downloaded the b43 stuff:

eelkins@ubuntu:~$ sudo apt-get install firmware-b43-installer
[sudo] password for eelkins: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firmware-b43-installer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by westie457 on 2012-11-28
Could you follow the directions posted by NikTh please.
The information supplied in the netinfo.txt file will help tremendously in diagnosing the issue and allow us to suggest a solution without guessing.

Thank you.

---

### Post by noveny on 2012-11-28
The below attachment is for: NikTh.  It is the netinfo.txt stuff

---

### Post by westie457 on 2012-11-28
Follow the directions in this post please. 

[http://ubuntuforums.org/showpost.php?p=11860231&postcount=8](http://ubuntuforums.org/showpost.php?p=11860231&postcount=8)

This should get things working for you.

Thank you.

---

### Post by NikTh on 2012-11-28
> **noveny said:**
> The below attachment is for: NikTh. 

Is not only for NikTh :P 
Is for everyone in here who can examine the file and have a conclusion of what is going on.

So @westie457 examined the file and gave you the appropriate post that includes the possible solution . :) 

Thanks

---

### Post by noveny on 2012-11-30
I am still having a little trouble and want to thank all of you for your patience and assistance:  You guys are GREAT!  

I installed the B43 on my desktop, but then had some trouble with the commands.  I got an error after the first one, but then thought maybe the others would work.  Here are the results:
eelkins@ubuntu:~$ sudo mkdir /lib/firmware/b43
[sudo] password for eelkins: 
mkdir: cannot create directory `/lib/firmware/b43': File exists
eelkins@ubuntu:~$ sudo cp Desktop/b43/* /lib/firmware/b43
eelkins@ubuntu:~$ sudo rmmod -f b43
ERROR: Removing 'b43': No such file or directory
eelkins@ubuntu:~$ sudo rmmod -f ssb
ERROR: Removing 'ssb': No such file or directory
eelkins@ubuntu:~$ sudo modprobe b43
eelkins@ubuntu:~$

Any ideas?

---

### Post by carl4926 on 2012-12-03
Start again:

You can download this and extract the folder b43
[https://dl.dropbox.com/u/10573557/b43_firmware/b43.zip](https://dl.dropbox.com/u/10573557/b43_firmware/b43.zip)

inspect the dir. /lib/firmware
If you have a folder already 'b43'
We need to rename it
Open a terminal in /lib/firmware and do
```
su
mv b43 old-b43
```

Then open a terminal where you have the folder I gave you and do
```
su
mv b43 /lib/firmware
```

---

### Post by noveny on 2012-12-04
> **carl4926 said:**
> Start again:

You can download this and extract the folder b43
[https://dl.dropbox.com/u/10573557/b43_firmware/b43.zip](https://dl.dropbox.com/u/10573557/b43_firmware/b43.zip)

inspect the dir. /lib/firmware
If you have a folder already 'b43'
We need to rename it
Open a terminal in /lib/firmware and do
```
su
mv b43 old-b43
```

Then open a terminal where you have the folder I gave you and do
```
su
mv b43 /lib/firmware
```
I am not sure how to open a terminal in /lib/firmware?  I know how to open a terminal, but not in a certain location.  I did open the terminal and this is what I get:
eelkins@ubuntu:~$ su mv b43 old-b43
Unknown id: mv
eelkins@ubuntu:~$ 

I can find the b43 folder through the file system/lib/firmware/b43, but when I right click to rename it, the rename option is greyed out--not an option.

---

### Post by carl4926 on 2012-12-05
You just do

```
cd /lib/firmware
```

---

### Post by noveny on 2012-12-09
Alright.  Mission accomplished.  I renamed the old b43 and downloaded the new one from drop box and now have the new b43 in the lib/directory.  I did a restart and still have no wireless.  What do I do now?

Thanks,

Ed

---

### Post by carl4926 on 2012-12-11
>  now have the new b43 in the lib/directory.Please confirm it's in /lib/firmware

Then try

```
sudo modprobe -rv b43
```
```
sudo modprobe -v b43
```

---

