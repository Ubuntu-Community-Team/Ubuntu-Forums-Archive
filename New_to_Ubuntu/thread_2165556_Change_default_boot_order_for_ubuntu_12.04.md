---
title: "Change default boot order for ubuntu 12.04"
date: 2013-08-05
forum: New to Ubuntu
---

### Post by X8YnhwA on 2013-08-05
How do i go about changing the default boot order? Becuase usally i forget and it boots into ubuntu instead of windows 7. It is a hassle to keep on restarting to windows 7.
 
I tried this link - [http://askubuntu.com/questions/100232/how-do-i-change-the-grub-boot-order](http://askubuntu.com/questions/100232/how-do-i-change-the-grub-boot-order)
Nothing happens and i get "no ultimately trusted keys found"
Is there any other easy way to change boot order?
I have no prior experience programming with linux so please make instuctions simple please.

Terminal results: 
sudo add-apt-repository ppa:danielrichter2007/grub-customizer
sudo apt-get update
sudo apt-get install grub-customizer
 More info: [https://launchpad.net/~danielrichter2007/+archive/grub-customizer](https://launchpad.net/~danielrichter2007/+archive/grub-customizer)
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmp4gXhBC/secring.gpg' created
gpg: keyring `/tmp/tmp4gXhBC/pubring.gpg' created
gpg: requesting key 3F055C03 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmp4gXhBC/trustdb.gpg: trustdb created
gpg: key 3F055C03: public key "Launchpad PPA for Daniel Richter" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK

---

### Post by slickymaster on 2013-08-05
Follow this Psychocats's tutorial: [Configuring the Boot Menu in Ubuntu]("http://www.psychocats.net/ubuntu/bootmenu")

---

### Post by Tom 6 on 2013-08-05
Boot Menu
To put Windows or pre-existing OS at the top of the boot menu
Launchpad question
[https://answers.launchpad.net/ubuntu/+source/grub2/+question/108890](https://answers.launchpad.net/ubuntu/+source/grub2/+question/108890)
Marc Stewart said on 2010-04-30:

It's trivial to move Windows to the top of the GRUB2 menu. Open a terminal and enter:
cd /etc/grub.d
sudo mv 30_os-prober 08_os-prober
sudo update-grub

That'll make GRUB look for non-Linux OSes first, putting Windows at the top.


Regards from 
Tom :)

---

### Post by GwL3eNC on 2013-08-05
Hi,

i think you are on an easy way. Your first post show, that you have added the grub customizer ppa. 
With that you tell ubuntu about a place, where it can find the grub-costomizer. You now have to install
the application with (dont copy it all togehter!!!,only one after one!)

sudo apt-get update
sudo apt-get install grub-customizer 

After the install process is finished open grub-customizer with 

sudo grub-customizer.

If you see the application you see what you have to do. Save your changes an go.

---

### Post by Tom 6 on 2013-08-06
Hi :)
I think it's a question of how comfotable you are with the command-line.  It's good to know there are many different ways of doing the same thing though.  What some people might find easier others will find tougher or longer.  

The 'easier' gui way is to run 3 commands on the command-line and then hunt through a gui.  It also means installing an extra program that will probably only get used once.  

The way i got from Marc Stewart was also 3 lines on the command-line but then that was the job completed.  

So, it is nice to know that there are multiple different ways to get the job done but i don't think it's easy to say which is easier.  It just depends on what you prefer.  Both are easier to the right person ;)

Regards from 
Tom :)

---

