---
title: "how to add winxp to grub menu"
date: 2012-08-06
forum: New to Ubuntu
---

### Post by paichkash on 2012-08-06
hi
i have 2 harddrives in my pc ..
one has xp and i bought another for linux just to be safe .. i removed the xp hdd and pluged linux hdd installed ubuntu ...  after all was done and ubuntu was up and running.. i attached the xp hdd on another seperate IDE cable.. now to boot xp i go to bios and select the correspondign hdd for first boot device and for linux select the other one.. 
its very tiresome work as i frequently swap between both..

Ho can i add an option in the Ubuntu GRUB for XP ?

---

### Post by drs305 on 2012-08-06
Boot your Ubuntu OS. With the Windows drive connected, open a terminal and run:
```
sudo update-grub
```
GRUB should find Windows and add it to the GRUB menu. The next time you boot you should have a choice of which OS you would like to boot.

---

### Post by yuvraj23 on 2012-08-06
Open terminal and enter this commands.. If it doesn't works then reply here

```


sudo update-grub


```

---

### Post by yuvraj23 on 2012-08-06
> **drs305 said:**
> Boot your Ubuntu OS. With the Windows drive connected, open a terminal and run:
```
sudo update-grub
```GRUB should find Windows and add it to the GRUB menu. The next time you boot you should have a choice of which OS you would like to boot.

Very fast! :)

---

### Post by unevenflow on 2012-08-06
Hey, you could use  ###Boot-Repair###
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair
check here for instructions
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by paichkash on 2012-08-07
i added the following to /boot/grub/menu.list file
```
title Windows XP
               map (hd0) (hd1)
               map (hd1) (hd0)
               rootnoverify (hd1,0)
               chainloader +1 

```

and xp showd there . now i mostly use xp as default with once or twice in a bluemoon i use ubuntu to practice on it my linux commands.. which i am trying to study on myself... so i want to make xp default instead of ubuntu... 


i have just moved the above code above all other options .. will see if just that makes xp the default... 

thanks for real fast help..

---

### Post by paichkash on 2012-08-08
moving it to top did made xp as default . so my issue solved..
thanks all

---

