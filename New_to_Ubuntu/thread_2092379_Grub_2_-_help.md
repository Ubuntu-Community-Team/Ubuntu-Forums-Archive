---
title: "Grub 2 - help"
date: 2012-12-07
forum: New to Ubuntu
---

### Post by wobwill on 2012-12-07
Hi,

I've duel booted windows 7 and ubuntu 12.10. I installed grub customizer to change the default boot order and to stop having the time out. I wanted no time out and to always choose which OS I wanted at boot. I managed to change the boot order without too much difficulty. 

I have also set the time out to 0, thinking that this would force a choice of OS at every boot. It does not and I can now only boot into windows. 

I've used my ubuntu cd to 'try ubuntu' to then modify /etc/default/grub, but don't have the permission to do so and don't know if I can change my permissions from the live cd. 

Can anyone advise on the best way of changing the default time out in Grub2, knowing that I can't boot ubuntu. 

I have also tried hitting shift at boot, but this does not work. I saw one thread that hitting shift will not work if the time out is set to '0'

Any help much appreciated

Will

---

### Post by audiomick on 2012-12-07
When you have a dual boot installed, you should always see the boot menu. This makes the "hit shift" solution redundant, as it is for that case that the grub menu is set to not appear. This is, for instance, the default setting for an install of Ubuntu that is not a dual boot.  

The reason you are not seeing the grub menu is because the timeout is set to zero. The timeoout is the amount of time that the menu stays visible. When it is set to 0, the menu appears, but does not remain for any length of time. You have obviously set your default boot order to have windows first, and given that you don't get to choose at the menu, you are always landing in Windows.

Apparently you know where you have to go to change the timeout value. That is good, because I don't know without having to look it up. You say you are encountering permission problems trying to change the setting using the live CD. That will be because the file you are trying to change is in a folder belonging to root. You will need root privileges to change it. That probably means you need to use sudo before the command that you are using to change the value, or, if your are editing a file directly, use sudo or gksudo to start an editor with root privileges. This will work from the live environment.

If you don't understand that last section, post exactly how you are trying to change the timeout value, and we will help you with it.

---

### Post by wobwill on 2012-12-07
audiomick,

you've paraphrased my problem very well. Thank you for your quick response. 

I'll look into using sudo or gksudo from the live CD to make the changes I need. 

Many Thanks

Will

---

### Post by audiomick on 2012-12-07
Glad to help. When you are succesful at repairing the problem, do come back and label the thread as solved. That is in the "thread tools" drop down at the top of the thread.

---

