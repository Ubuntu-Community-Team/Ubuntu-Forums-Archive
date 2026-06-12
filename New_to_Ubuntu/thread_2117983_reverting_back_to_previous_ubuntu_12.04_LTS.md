---
title: "reverting back to previous ubuntu 12.04 LTS"
date: 2013-02-19
forum: New to Ubuntu
---

### Post by send2 on 2013-02-19
:cry:Hi all,

i am running Ubuntu 12.04 LTS on a Toshiba Satellite A505-S6986 with 1TB hard drive. I installed Ubuntu with no problems and was using Gnome 3 for desktop when I routinely downloaded updates after being prompted. The download also installed new updates to the LTS version, when i restarted my computer after the prompt to do so the GRUB routinely gave me the option of booting into Ubuntu (the Ubuntu progress dots and purple screen did not appear) but instead of the GUI coming up to show my user name and pass word I got a black screen with the following: 

Ubuntu 12.04.02 LTS username-satellite -A505 tty1
username - satellite -A505 login:

when i tried to input the same info as when i am logging in as usual it does not want to accept my username or password.

When I first booted up this is what i got:

Ubuntu 12.04.02 LTS username-satellite-a505 tty1
then i got :
username-satellite-a-505 login: $
password:

Last log in: Tuesday Feb.19 20:11:03 cst 2013 on tty1
Welcome to Ubuntu 12.04.2 LTS (GNU/Linux 3.2.0-38 generic x86-64)

* Documentation: [https://help-ubuntu.com/](https://help-ubuntu.com/) 
username@username-satellite-A505: ~$

I also got the following: 

-bash : (part of my password): event not found

is there a way to revert to my previous version of Ubuntu without installing everything again? if so can i use the live cd or other method? how do i go about this?

thanks,

please let me know what other info is needed. I am typing this from my Windows 7 side of things. Note: i have Ubuntu installed on external hard drive.

I also installed Ubuntu from making my own desktop live cd.

---

### Post by omeomi on 2013-02-20
Can you boot using [Recovery mode]("https://wiki.ubuntu.com/RecoveryMode")?

Is Ubuntu installed on 1 single partition on your drive or do you have a separate /home partition?

---

### Post by Mark Phelps on 2013-02-20
> **send2 said:**
> :cry:...is there a way to revert to my previous version of Ubuntu without installing everything again? 

Sorry, there's no "rollback" capability, you would have to reinstall from scratch.

---

### Post by send2 on 2013-02-20
> **omeomi said:**
> Can you boot using [Recovery mode]("https://wiki.ubuntu.com/RecoveryMode")?

Is Ubuntu installed on 1 single partition on your drive or do you have a separate /home partition?

Thanks omeomi for your reply, as far as i know when i installed Ubuntu i assigned a home directory as well as root and swap. Not sure if this answered your question. I am new to Ubuntu. I was able to sign in using an older version of Linux from the GRUB menu. 

I had several choices: Ubuntu 12.04 -38  not good it gave me the black screen
                                           Ubuntu 12.04 -37  not good it gave me the black screen
                                           Ubuntu 12.04 -36 i was able to come to my GUI login screen

Can I assign GRUB to load this last version of Linux?

I am doing research on this as I can. I remember from the updates it loaded a 304 video driver as well as other Linux updates before that black screen reboot.

Thanks again for your help.

---

### Post by send2 on 2013-02-20
> **Mark Phelps said:**
> Sorry, there's no "rollback" capability, you would have to reinstall from scratch.

Hi Mark,  thanks for your reply. I am learning the hard way on what not to do. The Linux updates that came my way along with an nvidia 304 video driver install did the trick on ruining my day.

After booting in using an older version of Linux i will be more careful in examining what comes down as an update. In case Omeomi does not know the answer is there a way of making GRUB boot up from the working Linux version into GUI login? I would like to log in without having to choose among a list of Linux versions. 

Thanks again for your help.

---

### Post by SuperFreak on 2013-02-20
You could install Grub Customizer [http://www.webupd8.org/2012/09/grub-customizer-30-released.html]("http://www.webupd8.org/2012/09/grub-customizer-30-released.html") which will provide a graphical means of setting up the order of the Grub menu amongst other options. There is a way through terminal to modify a grub.cfg file also [http://askubuntu.com/questions/100232/how-do-i-change-the-grub-boot-order]("http://askubuntu.com/questions/100232/how-do-i-change-the-grub-boot-order")

---

### Post by send2 on 2013-02-20
> **SuperFreak said:**
> You could install Grub Customizer [http://www.webupd8.org/2012/09/grub-customizer-30-released.html](http://www.webupd8.org/2012/09/grub-customizer-30-released.html) which will provide a graphical means of setting up the order of the Grub menu amongst other options. There is a way through terminal to modify a grub.cfg file also [http://askubuntu.com/questions/100232/how-do-i-change-the-grub-boot-order](http://askubuntu.com/questions/100232/how-do-i-change-the-grub-boot-order)

Thank you SuperFreak for the answer, that is just what I needed, I will look in to this further.

---

### Post by SuperFreak on 2013-02-20
Glad to help :p

---

### Post by send2 on 2013-02-21
Thanks to all of you who replied, i removed a video driver that was experimental that was also installed and i could log on normally. I will mark this thread closed.

---

