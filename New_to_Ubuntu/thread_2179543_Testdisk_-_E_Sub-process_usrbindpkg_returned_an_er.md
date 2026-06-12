---
title: "Testdisk - E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2013-10-08
forum: New to Ubuntu
---

### Post by usman2 on 2013-10-08
Hey guys,
Please read this [http://askubuntu.com/questions/35527...ore-installing]("http://askubuntu.com/questions/355277/ubuntu-12-04-installed-on-usb-but-i-cant-try-it-before-installing")[ ]("http://askubuntu.com/questions/355277/ubuntu-12-04-installed-on-usb-but-i-cant-try-it-before-installing")to know where I'm coming from.. I made it work after hours of research  then I faced 'Unable to locate Error' finally solved and now this..  point is my 1tb ext. hdd got into RAW format and I want to recover the  data/reapir the partition through Testdisk. It has some really important  data and I can't just let it go.. but I keep recieving such error  messages one after another.

Please know that I don't know how to use ubuntu, so guide like you would guide a newbie or a beginner.. 

>  	 		 			 			 				ubuntu@ubuntu:~$ sudo apt-get install testdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
testdisk is already the newest version.
The following package was automatically installed and is no longer required:
  thunderbird-globalmenu
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up initramfs-tools (0.99ubuntu13.2) ...
update-initramfs: deferring update (trigger activated)
lzma: (stdin): Cannot allocate memory
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1) 			 		

 	
 


Thank You.

---

### Post by heir4c on 2013-10-08
> I successfully installed Ubuntu 12.04 on my 8gb USB stick with - Universal USB installer - LiLi USB Creator and - Unetbootin
What program you use for making the live-usb? You mentioned 3 programs. Why?  And have you installed 12.04 on your harddisk? Or...?

For the error above, use the command:
```
sudo dpkg-reconfigure -a
```

Edit: I think the command above is not right, you can try it or use instead:
```
sudo dpkg --configure -a
```
sorry.

or:
```
sudo apt-get install -f
```

---

### Post by usman2 on 2013-10-08
I tried all three because of the first error I kept getting and for second one I did live boot thing from my laptop some using pic with AHCI eabled didn't help. Right now am at 3rd error.. I hope your suggestions work. I'll try them and get back to you after few hours. 

Thanks for the response.

---

### Post by heir4c on 2013-10-08
I never had made a live-usb on Windows, so somebody else will have to help with that.

But, where do you enter/use than the commando for the testdisk? I do not understand.

Edit: I Edited the commando's I give because I think the first is not right.

---

### Post by usman2 on 2013-10-09
I'm thinking may be I should try to install Ubuntu properly and then try to run testdisk.. because all that data is worth the time and effort. What OS version of Ubuntu, you think would be great?

---

