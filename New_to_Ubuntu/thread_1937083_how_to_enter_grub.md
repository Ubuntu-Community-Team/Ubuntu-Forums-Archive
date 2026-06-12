---
title: "how to enter grub"
date: 2012-03-07
forum: New to Ubuntu
---

### Post by Ericyue on 2012-03-07
[SIZE=3]Hi all, i just install the ubuntu 10.04LTS version on my pc and it was the only OS on my pc. i want to install some software but 1st i have to log in as root just can install. i forget the root password already and when startup, it don't appear grub menu screen. i have try to press the "Shift" button and also "Esc" button but it still don't appear. 

Anyone got idea how to work about this problem ? Thanks in advance [/SIZE]

---

### Post by bogan on 2012-03-07
Hi! **ericyue,**

Does your PC boot at all?  to login prompt ?? or to the GUI login Window ??? , and if so, can you log-in normally ????

Can you boot from the CD or USB you installed from?

The root password is the same as your login user password as administrator.

Chao!,** bogan**.

---

### Post by Gone fishing on 2012-03-07
Shift should work if pressed immedietly after the BIOS screen goes. However, you could modify grub so that grub displays by changing the GRUB_HIDDEN_TIMEOUT setting.

[http://ubuntuforums.org/showthread.php?t=1302743](http://ubuntuforums.org/showthread.php?t=1302743)

and here's a gui way

[http://www.howtogeek.com/howto/43471/how-to-configure-the-linux-grub2-boot-menu-the-easy-way/](http://www.howtogeek.com/howto/43471/how-to-configure-the-linux-grub2-boot-menu-the-easy-way/)

However, why do you need to be root open up a terminal and sudo -i will give you root temporally

---

### Post by winh8r on 2012-03-07
You seem to be starting multiple threads with the same request for help which is a bit confusing.

I have posted a response here:

[http://ubuntuforums.org/showthread.php?t=1937091]("http://ubuntuforums.org/showthread.php?t=1937091")

---

### Post by mikewhatever on 2012-03-07
There is no need to login as root to install software, in fact, it's strongly discouraged, unless you know exactly what you are doing. Just use your regular user account instead.

---

### Post by Ericyue on 2012-03-07
thanks so much for all your reply .. i have solved the problem to install the software .

but i meet another problem when install another software-xibo

in this website --> [http://wiki.xibo.org.uk/wiki/Install_Guide_Xibo_Server](http://wiki.xibo.org.uk/wiki/Install_Guide_Xibo_Server)


it teach me to move the xibo.tar.gz to the /var/www and type this --> 
sudo tar zxvf ~/xibo-1.0.5-server.tar.gz

but after i type, i get this result -->

root@pc-main-desktop:/var/www# sudo tar zxvf ~/xibo-server-1.2.2.1.tar.gz
tar: /root/xibo-server-1.2.2.1.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors

is anyone know what is happen ? thanks in advance :)

---

### Post by Gone fishing on 2012-03-08
You seem to have moved the file to /var/www but trying to extract it at /root. Simply use the cd command to go to /var/www and then extract

---

### Post by winh8r on 2012-03-08
> **Ericyue said:**
> thanks so much for all your reply .. i have solved the problem to install the software .

but i meet another problem when install another software-xibo

in this website --> [http://wiki.xibo.org.uk/wiki/Install_Guide_Xibo_Server](http://wiki.xibo.org.uk/wiki/Install_Guide_Xibo_Server)


it teach me to move the xibo.tar.gz to the /var/www and type this --> 
sudo tar zxvf ~/xibo-[COLOR="Lime"]1.0.5[/COLOR]-server.tar.gz

but after i type, i get this result -->

root@pc-main-desktop:/var/www# sudo tar zxvf ~/xibo-server[COLOR="Red"]-1.2.2.1.[/COLOR]tar.gz
tar: /root/xibo-server-1.2.2.1.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors

is anyone know what is happen ? thanks in advance :)


You need to make sure the version number in your command is the same as the version number of the package you downloaded.

It looks like you have just copied and pasted the command from the website which is only an example .

change the command to the correct version number and it should run.


Also remember that running your system as root is dangerous, it can cause many problems.

When you need extra permissions you should use the "sudo" command

Hope this helps you.

---

### Post by Ericyue on 2012-03-19
Dear Gone Fishing,

i press sudo  and it want me to enter a password . and i type in the password only it keeps tell me incorrect password. 

so i have to go in grub and change the root password .. 

thanks for your reply .. it helps me a lot .

---

### Post by raja.genupula on 2012-03-19
you this thing to reset your passoword 
[http://www.howtogeek.com/howto/linux/reset-your-ubuntu-password-easily-from-the-live-cd/](http://www.howtogeek.com/howto/linux/reset-your-ubuntu-password-easily-from-the-live-cd/)

for all grub related operation we have a GUI names as Grub Customizer (My Signature). 

Hope that helps

---

### Post by Ericyue on 2012-03-20
Hi , all 

after i enter grub, i wan to change the password of root so i press "e" and it tells me -->

recordfail
insmod ext2
set root=' (hd0,1)'
search --no-floopy--fs-uuid--set d50bc135-eaf0-4f13-80c9-b8bf2c50b\7aa
Linux /boot/vmlinuz-2.6.32-39-generic-pae root=UUID=d50bc135-eaf-4f13-80c9-b8bf2c50b\7aa ro quite splash
initrd/boot/initrd.img-2.6.32-39-generic-pae


can anyone tell me why it will recordfail because i have do the same way for the other 2 machine with no problem .. 

Thanks in advance

---

### Post by raja.genupula on 2012-03-20
If you want to change root password , you can do with sudo passwd?  

have you reset your password with the link i have given  ?

---

### Post by Ericyue on 2012-03-22
i have found a easiest way to reset password with enter the grub .

got to Terminal, type sudo passwd.

enter your user account password and u can change the root password . :)

---

