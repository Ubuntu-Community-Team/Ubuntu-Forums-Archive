---
title: "How to I reset Unity to default settings?"
date: 2012-06-17
forum: New to Ubuntu
---

### Post by bwallum on 2012-06-17
Hello

I have a completely screwed Desktop following upgrade to Ubuntu 12.04 i386.

The display shows the Desktop background but no icons or window headers. I have tried running ```
unity --reset
```and things scroll away then stop without returning to prompt.

How can I reset Unity to default settings please?

I have tried this using a terminal (Ctrl + Alt + F1)```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get -f install
sudo dpkg-reconfigure -a
sudo update-grub
sudo reboot
```and at the dpkg-reconfigure command I had to wait a while for it to return to the prompt. However, no change.

---

### Post by MG&amp;TL on 2012-06-17
If it never ran after you upgraded it, something's probably broken, rather than broken by user error.

Can you post the output of:

```
/usr/lib/nux/unity_support_test -p
```


from a terminal please, to see if Unity is having trouble starting.

---

### Post by CaptainMark on 2012-06-17
you could try before logging in going to a ctrl+alt+f1 terminal and using ```
apt-get purge unity; apt-get install unity; reboot
``` as root

---

### Post by daslinkard on 2012-06-17
@ Captain Mark....

Asking this to learn....would it be the sudo command of:

```
apt-get --purge remove unity
```instead of the ```
apt-get purge unity
```

---

### Post by cortman on 2012-06-17
Deleted.

---

### Post by daslinkard on 2012-06-17
Don't forget that if you do not see the desired effects immediately....reboot the machine to see if this changes things.

---

### Post by CaptainMark on 2012-06-18
> **daslinkard said:**
> @ Captain Mark....

Asking this to learn....would it be the sudo command of:

```
apt-get --purge remove unity
```instead of the ```
apt-get purge unity
```

same thing

---

### Post by NikTh on 2012-06-18
Hi , 
first thing , try to install MyUnity ```
sudo apt-get install myunity
``` , open it and click "default settings" to see if something fixed. 

second , try to create another user and see if environment works for this user correctly. If yes then you can try to give (to new user) admin privileges and move all your personal files, then just delete old user. 
Thanks

---

### Post by soumoks on 2012-06-18
have u tried reinstalling unity using synaptic?
the best way is to completely remove unity using synaptic and then reinstalling using the same..what i am trying to say is don't go for the reinstallation thing provided by synaptic, do a clean install,hope it helps..

---

### Post by CaptainMark on 2012-06-19
> **soumoks said:**
> have u tried reinstalling unity using synaptic?
the best way is to completely remove unity using synaptic and then reinstalling using the same..what i am trying to say is don't go for the reinstallation thing provided by synaptic, do a clean install,hope it helps..
this is the same as the mentioned terminal command but the op cant get to his desktop so your method might be impossible for him/her

---

### Post by NikTh on 2012-06-19
> **CaptainMark said:**
>  but the op cant get to his desktop so your method might be impossible for him/her

Oh , i didn't understood this. Sorry . 
Ok , from VT then (ctrl+alt+F1 or F2..) try to add a new user to test if settings are ok .
```
sudo service lightdm stop
sudo adduser <username> 
sudo service lightdm start 
```and login with new user.

And another thing.. if you purge unity , then you will see that **ubuntu-desktop** will be removed.. so install it after.

---

### Post by bwallum on 2012-06-20
Thanks for the response. I'm afraid I opted for removing and storing the home folder, then reinstalling the os from a live cd, formatting the entire disk en route. I then copied back the home folder on to a second drive.

This is a blunt approach and I regret means little learning but it enabled me to quickly get up and running again.

The thing that put me off removing unity and re-installing was the fact that the Desktop went with it and I was reluctant to risk data. (I have never been confident of Backup, I regret to say, since it failed to remove aged backups as instructed) Once data was backed up to an external drive then re-install became a certain option of known duration. I also took the opportunity to place the home folder on a second drive, with the first drive hosting the OS.

I have to say Precise live cd (i386) is the best Ubuntu distribution I have used to date and entirely painless. Thank you for that everybody.

I have saved and will use this thread should I encounter a similar situation. Many thanks again for the thread contributions.

---

