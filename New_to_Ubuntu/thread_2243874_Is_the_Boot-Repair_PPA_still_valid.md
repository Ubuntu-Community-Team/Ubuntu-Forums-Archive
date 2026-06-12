---
title: "Is the Boot-Repair PPA still valid?"
date: 2014-09-11
forum: New to Ubuntu
---

### Post by JeQhdMD on 2014-09-11
My ubuntu installs are running with no issues, but I want to add the yannubuntu (?) repo (ppa) so I can install the boot-repair program.   I copied and pasted the two relevant lines of code from the Ubuntu Wiki

but the process didn't work as the terminal reported unable to locate package boot-repair . . . is there a newer method or different ppa, etc.??


[h=2]Step 2 - Install Boot-Repair[/h][COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]Once in the Ubuntu session, install [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") this way:[FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]

[LIST]
[*=left]Connect internet[FONT=inherit][/FONT]
[*=left]Open a terminal (Ctrl+Alt+T) and type :[FONT=inherit][/FONT][FONT=inherit][/FONT]
[/LIST]
[COLOR=#333333][FONT=Ubuntu][FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]
[FONT=inherit][/FONT]sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update[COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu][FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]
[FONT=inherit][/FONT]sudo apt-get install -y boot-repair && boot-repair

---

### Post by oldfred on 2014-09-11
He never has released a trusty version, so you have to use an older one which works. 
There is now another line in install instructions that edits trusty to saucy.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)


sudo add-apt-repository ppa:yannubuntu/boot-repair
[COLOR=#ff0000]sudo sed 's/trusty/saucy/g' -i /etc/apt/sources.list.d/yannubuntu-boot-repair-trusty.list[/COLOR]
sudo apt-get update
sudo apt-get install -y boot-repair && (boot-repair &)

---

### Post by JeQhdMD on 2014-09-12
Thanks Old Fred,

The new line worked.   For future updates - what is the communication process (e.g., a Trusty or Utopic release)?

---

### Post by oldfred on 2014-09-12
As long as Boot-Repair keeps working, you would just change the trusty in the sed command to the version you are using. 
But if Boot-Repair is not getting maintained soon it will not work well with newer versions. It should always be good for 12.04 and should be good for 14.04 for the life of those versions.

---

