---
title: "Scanner Driver"
date: 2013-02-04
forum: New to Ubuntu
---

### Post by daniell59 on 2013-02-04
I am getting ready to do a clean install. I will be going from Ubnutu 10.04 64 to 12.04 64. I just remembered that I will need to install drivers for my Epson V30 Scanner. From what I read so far, the present driver will not work with Ubuntu 12.04. If anyone has resolved this problem, I would appreciate your assistance.

Thanks

---

### Post by howefield on 2013-02-04
Can't vouch for it, but try this...

[http://www.mellowood.ca/documents/essays/epson-v30.html](http://www.mellowood.ca/documents/essays/epson-v30.html)

---

### Post by pdc on 2013-02-04
Hi daniell59

Epson do provide drivers for your scanner

....I was intrigued in the order of install that mellowood gave in the link that howefield kindly pointed you to: 

Epson always say: install the data package first;

......so if I point you in the right direction?

[http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX) is the start point ..entering V30 takes me to this

[http://download.ebz.epson.net/dsc/search/01/search/searchModule](http://download.ebz.epson.net/dsc/search/01/search/searchModule)

and if you click the accept button and download and install

1) [COLOR="SeaGreen"]iscan-data_1.21.0-1_all.deb[/COLOR]

then 

2) [COLOR="SeaGreen"]iscan_2.29.1-5~usb0.1.ltdl7_amd64.deb[/COLOR] ...note the ltd7 for newer kernels

then 

3) the [COLOR="Blue"]iscan plugin package[/COLOR]

[COLOR="SeaGreen"]esci-interpreter-gt-f720_0.1.1-2_amd64.deb[/COLOR]

..........gdebi installer should likely offer to install as you click each to download, so let it ..

---

### Post by daniell59 on 2013-02-07
I am now running Ubuntu 12.04 from flash drive. I did a test to see whether I can install drivers for scanner. I am having trouble.
I tried running the two sudo commnands. I realize that my knowledge is limited,and do appreciate help. I would like to work out the kings before installing it on hard drive.


ubuntu@ubuntu:~$  sudo dpkg -i esci-interpreter-gt-f720_0.1.1-2_i386.deb
dpkg: error processing esci-interpreter-gt-f720_0.1.1-2_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 esci-interpreter-gt-f720_0.1.1-2_i386.deb
ubuntu@ubuntu:~$

---

### Post by pdc on 2013-02-07
hi daniel; welcome back;

.............well...........when you click to download a deb package, I would have thought gdebi installer might leap in and offer to install for you........that saves you using a terminal:

.......but you must have downloaded and saved the deb packages..to your Downloads directory?

if you are using a terminal, and have downloaded and saved the deb package............

....... you need to be "IN" the correct folder (or directory) to issue commands to install things ..so assuming your flash drive is set up as persistent......so you can save things to it .......

...if you open a terminal and type

> [COLOR="Red"]ls[/COLOR] (and hit the ENTER key......)

.....that lists your directories.......it should show you a Downloads directory: so if you type

> [COLOR="Red"]cd Downloads[/COLOR] (and hit the ENTER key......)

that should get you inside the Downloads directory

if you now type

> [COLOR="Red"]ls[/COLOR]

...that should list what is in your Downloads directory ... the iscan packages should be there......? ......so now from within that directory you can install....

ie 

> [COLOR="Red"]sudo dpkg -i whatever.deb[/COLOR]

___________________________________________

another way is just to use the GUI: and click and open the directories ..

....if you right-click on the deb packages, you should get an "install with gdebi installer" option........if you use that it saves you using the terminal.........

.......remember to install the data package first;

1) [COLOR="SeaGreen"]iscan-data_1.21.0-1_all.deb[/COLOR]
then
2) [COLOR="SeaGreen"]iscan_2.29.1-5~usb0.1.ltdl7_whatever.deb[/COLOR]
then
3) [COLOR="SeaGreen"]esci-interpreter-gt-f720_0.1.1-2_whatever.deb[/COLOR]

_____________________________________________-

in your first post, you said you planned to install the 64bit version;

I note you were attempting to install the 32bit plugin ......esci-interpreter-gt-f720_0.1.1-2_[COLOR="Red"]i386[/COLOR].deb......... if you clarify all that for us ........ie changed mind ......or made mistake or whatever...............

---

### Post by daniell59 on 2013-02-08
> **pdc said:**
> hi daniel; welcome back;

.............well...........when you click to download a deb package, I would have thought gdebi installer might leap in and offer to install for you........that saves you using a terminal:

.......but you must have downloaded and saved the deb packages..to your Downloads directory?

if you are using a terminal, and have downloaded and saved the deb package............

....... you need to be "IN" the correct folder (or directory) to issue commands to install things ..so assuming your flash drive is set up as persistent......so you can save things to it .......

...if you open a terminal and type

 (and hit the ENTER key......)

.....that lists your directories.......it should show you a Downloads directory: so if you type

 (and hit the ENTER key......)

that should get you inside the Downloads directory

if you now type



...that should list what is in your Downloads directory ... the iscan packages should be there......? ......so now from within that directory you can install....

ie 



___________________________________________

another way is just to use the GUI: and click and open the directories ..

....if you right-click on the deb packages, you should get an "install with gdebi installer" option........if you use that it saves you using the terminal.........

.......remember to install the data package first;

1) [COLOR="SeaGreen"]iscan-data_1.21.0-1_all.deb[/COLOR]
then
2) [COLOR="SeaGreen"]iscan_2.29.1-5~usb0.1.ltdl7_whatever.deb[/COLOR]
then
3) [COLOR="SeaGreen"]esci-interpreter-gt-f720_0.1.1-2_whatever.deb[/COLOR]

_____________________________________________-

in your first post, you said you planned to install the 64bit version;

I note you were attempting to install the 32bit plugin ......esci-interpreter-gt-f720_0.1.1-2_[COLOR="Red"]i386[/COLOR].deb......... if you clarify all that for us ........ie changed mind ......or made mistake or whatever...............

Thanks for your kind assistance.
I was unsure which plugin to install. I wanted to install the 64 bit one. Soon I will boot to the flash drive and try again.
I need the use of the scanner, so I do not want to give up on 10.04 until I can get it working in 12.04 64.

---

### Post by daniell59 on 2013-02-08
ubuntu@ubuntu:~$ cd Downloads
ubuntu@ubuntu:~/Downloads$ ls
iscan_2.29.1-5~usb0.1.ltdl7_amd64         iscan_2.29.1-5~usb0.1.ltdl7_amd64.deb
iscan_2.29.1-5~usb0.1.ltdl7_amd64(1)      iscan-data_1.21.0-1_all.deb
iscan_2.29.1-5~usb0.1.ltdl7_amd64(1).deb
ubuntu@ubuntu:~/Downloads$ 

I am on the flash drive. This is what is in my Downloads directory.
Any further assistance will be appreciated.

---

### Post by daniell59 on 2013-02-09
In spite of my efforts I have not been able to get Umbutu to detect my scanner. I would appreciate it someone could check the files in my directory, and offer advice.

Thanks

ubuntu@ubuntu:~$ cd Downloads
ubuntu@ubuntu:~/Downloads$ ls
esci-interpreter-gt-f720_0.1.1-2_amd64.deb
iscan_2.29.1-5~usb0.1.ltdl3_amd64(1).deb
iscan_2.29.1-5~usb0.1.ltdl3_amd64(2).deb
iscan_2.29.1-5~usb0.1.ltdl3_amd64.deb
iscan_2.29.1-5~usb0.1.ltdl7_amd64
iscan_2.29.1-5~usb0.1.ltdl7_amd64(1)
iscan_2.29.1-5~usb0.1.ltdl7_amd64(1).deb
iscan_2.29.1-5~usb0.1.ltdl7_amd64(2).deb
iscan_2.29.1-5~usb0.1.ltdl7_amd64(3).deb
iscan_2.29.1-5~usb0.1.ltdl7_amd64.deb
iscan-data_1.21.0-1_all(1).deb
iscan-data_1.21.0-1_all(2).deb
iscan-data_1.21.0-1_all(3).deb
iscan-data_1.21.0-1_all(4).deb
iscan-data_1.21.0-1_all.deb
ubuntu@ubuntu:~/Downloads$

---

### Post by westcoast01 on 2013-02-09
I have a HP but solved my problems by uninstalling simple scan and insalling xsane through the software center. To install the required plug-in I had to use the terminal as root, ......   sudo -i   ..... gave me temporary root in terminal. Best of luck.

---

### Post by daniell59 on 2013-02-09
> **westcoast01 said:**
> I have a HP but solved my problems by uninstalling simple scan and insalling xsane through the software center. To install the required plug-in I had to use the terminal as root, ......   sudo -i   ..... gave me temporary root in terminal. Best of luck.

I think that it is more complicated with Epson Scanners.

---

### Post by cbtengr on 2013-02-09
I recall trying to test my Epson scanner while using a live CD.  Despite installing the packages listed in reply #5, it wouldn't work.  After installing to my HD & installing the Epson pkgs, the scanner was detected and worked fine.  I did not have to remove Simple Scan.

---

### Post by daniell59 on 2013-02-09
> **cbtengr said:**
> I recall trying to test my Epson scanner while using a live CD.  Despite installing the packages listed in reply #5, it wouldn't work.  After installing to my HD & installing the Epson pkgs, the scanner was detected and worked fine.  I did not have to remove Simple Scan.

How can you install packages while using a  live CD? I thought that it cannot be done. Please correct me if I am wrong. I am using a flash drive. That should work.

---

### Post by cbtengr on 2013-02-09
> **daniell59 said:**
> How can you install packages while using a  live CD? I thought that it cannot be done. Please correct me if I am wrong. I am using a flash drive. That should work.

It can be done.  I've tested quite a few programs before deciding to upgrade to new versions of Ubuntu.  Doesn't always work.

---

### Post by daniell59 on 2013-02-09
I finally got the scanner to be detected. I did not realize that I needed to put in esci-interpreter- etc etc.I now know that it will work with a flash drive.

Thanks to all for your kind and informative replies.

How do I indicate that the problem has been solved?

---

### Post by deadflowr on 2013-02-09
Click on the thread tools at the top section of the page, and mark as solved.

---

### Post by pdc on 2013-02-09
glad to see you got it working

are you launching it by typing

> [COLOR="Red"]iscan[/COLOR] 

in a terminal?

---

### Post by daniell59 on 2013-02-09
> **pdc said:**
> glad to see you got it working

are you launching it by typing



in a terminal?

I used the flash drive to be sure that it would work before installing in on the HD. I do not really know what I am doing.

---

### Post by pdc on 2013-02-09
so you get the scanning to work by typing iscan in a terminal? ..that should bring up the GUI for iscan...........

one can create a launcher to save you opening a terminal each time

---

### Post by gaxfax on 2013-05-20
This works for My Epson V330:

[COLOR=#000000]*another way is just to use the GUI: and click and open the directories ..*[/COLOR]

[COLOR=#000000]*....if you right-click on the deb packages, you should get an "install with gdebi installer" option........if you use that it saves you using the terminal.........*[/COLOR]

[COLOR=#000000]*.......remember to install the data package first;*[/COLOR]

[COLOR=#000000]*1) *[/COLOR][COLOR=SeaGreen]*iscan-data_1.21.0-1_all.deb*[/COLOR]
[COLOR=#000000]*then*[/COLOR]
[COLOR=#000000]*2) *[/COLOR][COLOR=SeaGreen]*iscan_2.29.1-5~usb0.1.ltdl7_whatever.deb*[/COLOR]
[COLOR=#000000]*then*[/COLOR]
[COLOR=#000000]*3) *[/COLOR][COLOR=SeaGreen][I]esci-interpreter-gt-f720_0.1.1-2_whatever.deb

Files are here:
[/I][/COLOR][http://download.ebz.epson.net/dsc/search/01/search/searchModule](http://download.ebz.epson.net/dsc/search/01/search/searchModule)

---

