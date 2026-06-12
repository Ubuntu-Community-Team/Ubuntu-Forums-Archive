---
title: "Printer - Canon LBP 2900B"
date: 2016-09-01
forum: New to Ubuntu
---

### Post by kan1969 on 2016-09-01
Hi Experts,

I have a printer problem and exactly I have the same problem as mentioned in this thread: [https://ubuntuforums.org/showthread.php?t=1592487](https://ubuntuforums.org/showthread.php?t=1592487)  where they advice to install transitional packages: [http://security.ubuntu.com/ubuntu/pool/universe/c/cups/cupsys_1.4.3-1ubuntu1.2_all.deb](http://security.ubuntu.com/ubuntu/pool/universe/c/cups/cupsys_1.4.3-1ubuntu1.2_all.deb).

Here is my problem. I do not know how to install them.

Kindly advice.

Thanks & Regards,
Kannan

---

### Post by kan1969 on 2016-09-19
Hi Friends,

Please help me.

Here is the output that I am having a bad file discriptor. I do not know what it is. This one comes while I try to install and run my printer. I am going through this page: [https://help.ubuntu.com/community/CanonCaptDrv190?action=show&redirect=HardwareSupportComponentsPrinters%2FCanonPrinters%2FCanon_LBP_2900](https://help.ubuntu.com/community/CanonCaptDrv190?action=show&redirect=HardwareSupportComponentsPrinters%2FCanonPrinters%2FCanon_LBP_2900)

vignesh@Krish:~$ service cups start
vignesh@Krish:~$ systemctl status cups
&#9679; cups.service - CUPS Scheduler
   Loaded: loaded (/lib/systemd/system/cups.service; enabled; vendor preset: enabled)
   Active: inactive (dead) since Mon 2016-09-19 14:07:20 IST; 7s ago
     Docs: man:cupsd(8)
  Process: 18327 ExecStart=/usr/sbin/cupsd -l (code=killed, signal=TERM)
 Main PID: 18327 (code=killed, signal=TERM)


Sep 19 14:07:20 Krish systemd[1]: Started CUPS Scheduler.


I do not know how to proceed further. Kindly help me with your valuable information.

Thanks & Regards,
Kannan

---

### Post by mörgæs on 2016-09-19
Hi, for people to help you it's important that you provide as much information as possible.

Which release of Buntu are you using?
What exactly have you done in order to solve the problem? Following advice from 2010 is not always a good idea.

---

### Post by kan1969 on 2016-09-20
Hi Experts,

Thanks for your inputs. Also, I am bit sorry for not providing relevant information.

My Ubuntu Version is 16.04, 64 bits. I have gone through these following threads:

[https://ubuntuforums.org/showthread.php?t=1592487](https://ubuntuforums.org/showthread.php?t=1592487)
[https://help.ubuntu.com/community/CanonCaptDrv190?action=show&redirect=HardwareSupportComponentsPrinters%2FCanonPrinters%2FCanon_LBP_2900](https://help.ubuntu.com/community/CanonCaptDrv190?action=show&redirect=HardwareSupportComponentsPrinters%2FCanonPrinters%2FCanon_LBP_2900)

Kindly help me.
Thanks,

With kind regards,
Kannan

---

### Post by mörgæs on 2016-09-20
I am aware that you have followed the threads but I was asking for the *exact* steps you have taken. 

If someone is going to be able to help he needs to see the precise commands and their results.

---

### Post by kan1969 on 2016-10-17
Hi All,

I am sorry for my late response. Since, I cannot totally remember all that I have done - I took a backup of all my files and foramted it and reinstalled UBUNTU 16.04 again.

Please tell me how to proceed from here.

Thanks,
Kannan

Meanwhile, I tried to add my canon printer to the ubuntu, but I did not find it listed there in printers list.

---

### Post by mörgæs on 2016-10-17
It seems like you have tried this one: 
[https://help.ubuntu.com/community/CanonCaptDrv190](https://help.ubuntu.com/community/CanonCaptDrv190)

My best guess is that it's still valid, also for 16.04. 

If CUPS is not already installed, please begin with **sudo apt-get install cups**.

After that please follow the guide and post the results from each step here (in CODE tags).

---

### Post by kan1969 on 2016-10-21
Hi Experts,

After running the given command, this is what I am getting:

sudo apt-get install cups
[sudo] password for krish: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
cups is already the newest version (2.1.3-4).
cups set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.

Got another doubt. Must we install the Canon Driver for it.


Thanks,
Kannan

---

### Post by colmax on 2016-10-21
This is a link to a linux driver for your printer
[https://driverscollection.com/?H=LBP2900&By=Canon&SS=Linux](https://driverscollection.com/?H=LBP2900&By=Canon&SS=Linux)
Cheers

---

### Post by kan1969 on 2016-10-22
Hi Experts,

Somehow that link did not work out for me. So I downloaded from Canon website and installed it. Hope! It's correct.

[http://search-in.canon-asia.com/canon__in_en__in_b_en/search.x?q=&ie=utf8&cat=0&ct=Support&pagemax=10&imgsize=1&pdf=ok&zoom=1&hf=category%09zubaken&cf=model_sm%3ALBP2900B&modelName=LBP2900B&ref=support-in.canon-asia.com&pid=GOACdiyTySAdlYfWTsajSw..&qid=TqiycIExtQM08Mh4g-DxUNugVEtFCiFs&d=DOWNLOADS%09Linux+64bit](http://search-in.canon-asia.com/canon__in_en__in_b_en/search.x?q=&ie=utf8&cat=0&ct=Support&pagemax=10&imgsize=1&pdf=ok&zoom=1&hf=category%09zubaken&cf=model_sm%3ALBP2900B&modelName=LBP2900B&ref=support-in.canon-asia.com&pid=GOACdiyTySAdlYfWTsajSw..&qid=TqiycIExtQM08Mh4g-DxUNugVEtFCiFs&d=DOWNLOADS%09Linux+64bit)

Thanks,
Kannan

---

### Post by kan1969 on 2016-10-22
Hi Experts,

I installed the driver and got my printer listed in the Printers and also got it listed in localhost:631. I have attached relevant screen shots for you. 

But still I am not able to take Print Test Page. It does not come.

Another thing - I found a note which came with the driver. May be, I am missing something. Please go through it and advise.

- If you are using Ubuntu, when installing with the default settings, you may 
  not be able to install the driver due to a lack of necessary libraries. 
  You can solve the problem by installing libraries using the following 
  commands.

  <For Ubuntu 12.04/14.04/14.10(32-bit)>
   # apt-get install libglade2-0

  <For Ubuntu 12.04(64-bit)>
   # apt-get install libglade2-0
   # apt-get install ia32-libs
   # apt-get install libpopt0:i386

  <For Ubuntu 14.04/14.10(64-bit)>
   # apt-get install libglade2-0
   # apt-get install libxml2:i386
   # apt-get install libstdc++6:i386
   # apt-get install libpopt0:i386

Thanks,
Kannan

---

### Post by Geoffrey_Arndt on 2016-10-22
So did you do the commands listed above ?. . . for example, first one would look like this: (don't input the #)

sudo apt-get install libglade2-0 <enter> . . . and so on down through the list.   Then restart system and try another test print.

---

### Post by kan1969 on 2016-10-24
Hi Experts,

No, I did not run any of those commands. I am just waiting for your confirmation. 

Please advise. 

Thanks, 
Kannan

---

### Post by mörgæs on 2016-10-25
Maybe Geoffrey is but I am far from an expert. I don't even have a Canon printer.

Still I think the commands listed for 14.04 are worth trying. I can't confirm that they work but I think you should try. 

Please run them one at a time and post the results in CODE tags. Stop the process if one piece of output looks strange.

---

### Post by kan1969 on 2016-10-30
Hi All,

I executed those commands and still my I am not able to get printing and here is the outputs:

krish@Vignesh:~$ sudo apt-get install libglade2-0
[sudo] password for krish: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libglade2-0 is already the newest version (1:2.6.4-2).
libglade2-0 set to manually installed.
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-21 linux-headers-4.4.0-21-generic
  linux-image-4.4.0-21-generic linux-image-extra-4.4.0-21-generic
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 39 not upgraded.

krish@Vignesh:~$ sudo apt-get install libxml2:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-21 linux-headers-4.4.0-21-generic
  linux-image-4.4.0-21-generic linux-image-extra-4.4.0-21-generic
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  gcc-5-base:i386 gcc-6-base:i386 libc-dev-bin libc6 libc6:i386 libc6-dbg
  libc6-dev libgcc1:i386 libicu55:i386 liblzma5:i386 libstdc++6:i386
  zlib1g:i386
Suggested packages:
  glibc-doc glibc-doc:i386 locales:i386
Recommended packages:
  xml-core:i386
The following NEW packages will be installed:
  gcc-5-base:i386 gcc-6-base:i386 libc6:i386 libgcc1:i386 libicu55:i386
  liblzma5:i386 libstdc++6:i386 libxml2:i386 zlib1g:i386
The following packages will be upgraded:
  libc-dev-bin libc6 libc6-dbg libc6-dev
4 upgraded, 9 newly installed, 0 to remove and 35 not upgraded.
Need to get 19.8 MB of archives.
After this operation, 45.7 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libc6-dev amd64 2.23-0ubuntu4 [2,084 kB]
Get:2 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libc-dev-bin amd64 2.23-0ubuntu4 [68.7 kB]
Get:3 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libc6-dbg amd64 2.23-0ubuntu4 [3,679 kB]
Get:4 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libc6 amd64 2.23-0ubuntu4 [2,586 kB]
Get:5 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) xenial/main i386 gcc-6-base i386 6.0.1-0ubuntu1 [14.3 kB]
Get:6 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) xenial/main i386 libgcc1 i386 1:6.0.1-0ubuntu1 [46.8 kB]
Get:7 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) xenial-updates/main i386 libc6 i386 2.23-0ubuntu4 [2,265 kB]
Get:8 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) xenial/main i386 liblzma5 i386 5.1.1alpha+20120614-2ubuntu2 [84.2 kB]
Get:9 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) xenial/main i386 zlib1g i386 1:1.2.8.dfsg-2ubuntu4 [52.2 kB]
Get:10 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) xenial-updates/main i386 gcc-5-base i386 5.4.0-6ubuntu1~16.04.2 [16.7 kB]
Get:11 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) xenial-updates/main i386 libstdc++6 i386 5.4.0-6ubuntu1~16.04.2 [418 kB]
Get:12 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) xenial/main i386 libicu55 i386 55.1-7 [7,759 kB]
Get:13 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) xenial-updates/main i386 libxml2 i386 2.9.3+dfsg1-1ubuntu0.1 [730 kB]
Fetched 19.8 MB in 3min 51s (85.7 kB/s)                                        
Preconfiguring packages ...
(Reading database ... 242773 files and directories currently installed.)
Preparing to unpack .../libc6-dev_2.23-0ubuntu4_amd64.deb ...
Unpacking libc6-dev:amd64 (2.23-0ubuntu4) over (2.23-0ubuntu3) ...
Preparing to unpack .../libc-dev-bin_2.23-0ubuntu4_amd64.deb ...
Unpacking libc-dev-bin (2.23-0ubuntu4) over (2.23-0ubuntu3) ...
Preparing to unpack .../libc6-dbg_2.23-0ubuntu4_amd64.deb ...
Unpacking libc6-dbg:amd64 (2.23-0ubuntu4) over (2.23-0ubuntu3) ...
Preparing to unpack .../libc6_2.23-0ubuntu4_amd64.deb ...
Unpacking libc6:amd64 (2.23-0ubuntu4) over (2.23-0ubuntu3) ...
Selecting previously unselected package libc6:i386.
Preparing to unpack .../libc6_2.23-0ubuntu4_i386.deb ...
Unpacking libc6:i386 (2.23-0ubuntu4) ...
Setting up libc6:amd64 (2.23-0ubuntu4) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Processing triggers for man-db (2.7.5-1) ...
Selecting previously unselected package libgcc1:i386.
(Reading database ... 243077 files and directories currently installed.)
Preparing to unpack .../libgcc1_1%3a6.0.1-0ubuntu1_i386.deb ...
Unpacking libgcc1:i386 (1:6.0.1-0ubuntu1) ...
Selecting previously unselected package gcc-6-base:i386.
Preparing to unpack .../gcc-6-base_6.0.1-0ubuntu1_i386.deb ...
Unpacking gcc-6-base:i386 (6.0.1-0ubuntu1) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Setting up gcc-6-base:i386 (6.0.1-0ubuntu1) ...
Setting up libgcc1:i386 (1:6.0.1-0ubuntu1) ...
Setting up libc6:i386 (2.23-0ubuntu4) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Selecting previously unselected package liblzma5:i386.
(Reading database ... 243082 files and directories currently installed.)
Preparing to unpack .../liblzma5_5.1.1alpha+20120614-2ubuntu2_i386.deb ...
Unpacking liblzma5:i386 (5.1.1alpha+20120614-2ubuntu2) ...
Selecting previously unselected package zlib1g:i386.
Preparing to unpack .../zlib1g_1%3a1.2.8.dfsg-2ubuntu4_i386.deb ...
Unpacking zlib1g:i386 (1:1.2.8.dfsg-2ubuntu4) ...
Selecting previously unselected package gcc-5-base:i386.
Preparing to unpack .../gcc-5-base_5.4.0-6ubuntu1~16.04.2_i386.deb ...
Unpacking gcc-5-base:i386 (5.4.0-6ubuntu1~16.04.2) ...
Selecting previously unselected package libstdc++6:i386.
Preparing to unpack .../libstdc++6_5.4.0-6ubuntu1~16.04.2_i386.deb ...
Unpacking libstdc++6:i386 (5.4.0-6ubuntu1~16.04.2) ...
Selecting previously unselected package libicu55:i386.
Preparing to unpack .../libicu55_55.1-7_i386.deb ...
Unpacking libicu55:i386 (55.1-7) ...
Selecting previously unselected package libxml2:i386.
Preparing to unpack .../libxml2_2.9.3+dfsg1-1ubuntu0.1_i386.deb ...
Unpacking libxml2:i386 (2.9.3+dfsg1-1ubuntu0.1) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Setting up libc-dev-bin (2.23-0ubuntu4) ...
Setting up libc6-dev:amd64 (2.23-0ubuntu4) ...
Setting up libc6-dbg:amd64 (2.23-0ubuntu4) ...
Setting up liblzma5:i386 (5.1.1alpha+20120614-2ubuntu2) ...
Setting up zlib1g:i386 (1:1.2.8.dfsg-2ubuntu4) ...
Setting up gcc-5-base:i386 (5.4.0-6ubuntu1~16.04.2) ...
Setting up libstdc++6:i386 (5.4.0-6ubuntu1~16.04.2) ...
Setting up libicu55:i386 (55.1-7) ...
Setting up libxml2:i386 (2.9.3+dfsg1-1ubuntu0.1) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
krish@Vignesh:~$ 

krish@Vignesh:~$ sudo apt-get install libstdc++6:i386
[sudo] password for krish: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libstdc++6:i386 is already the newest version (5.4.0-6ubuntu1~16.04.2).
libstdc++6:i386 set to manually installed.
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-21 linux-headers-4.4.0-21-generic
  linux-image-4.4.0-21-generic linux-image-extra-4.4.0-21-generic
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 35 not upgraded.

krish@Vignesh:~$ sudo apt-get install libpopt0:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-21 linux-headers-4.4.0-21-generic
  linux-image-4.4.0-21-generic linux-image-extra-4.4.0-21-generic
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed:
  libpopt0:i386
0 upgraded, 1 newly installed, 0 to remove and 35 not upgraded.
Need to get 28.1 kB of archives.
After this operation, 135 kB of additional disk space will be used.
Get:1 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) xenial/main i386 libpopt0 i386 1.16-10 [28.1 kB]
Fetched 28.1 kB in 1s (23.4 kB/s)                       
Selecting previously unselected package libpopt0:i386.
(Reading database ... 243111 files and directories currently installed.)
Preparing to unpack .../libpopt0_1.16-10_i386.deb ...
Unpacking libpopt0:i386 (1.16-10) ...
Setting up libpopt0:i386 (1.16-10) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
krish@Vignesh:~$ 



Well, still I am not getting it done. Somewhere the problem is. I got another doubt. What is a PPD file? In the Add Printer Device, it asks for ppd file. 

Another thing, in this URL:   [https://itsidukki.files.wordpress.com/2011/11/canon-lbp2900_printer-installation_tutorial.pdf](https://itsidukki.files.wordpress.com/2011/11/canon-lbp2900_printer-installation_tutorial.pdf)

The author says: 

sudo /etc/init.d/cups restart 
sudo /usr/sbin/lpadmin -p LBP2900 -m CNCUPSLBP2900CAPTK.ppd -v ccp:/var/ccpd/fifo0 -E 
sudo /usr/sbin/ccpdadmin -p LBP2900 -o /dev/usblp0 
sudo /etc/init.d/ccpd start 
sudo /etc/init.d/ccpd start

Can I try this?


Sorry to trouble you so much. Bit worried that I am not able to print.

Thanks a lot,
Kannan

---

### Post by kan1969 on 2016-10-31
Hi All,

I am bit sorry that first I did not understand what code tag is. I found it out by googling it finally. OK and correct me if I am wrong.

I executed those commands and still my I am not able to get printing and here is the outputs:

```


krish@Vignesh:~$ sudo apt-get install libglade2-0
[sudo] password for krish: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libglade2-0 is already the newest version (1:2.6.4-2).
libglade2-0 set to manually installed.
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-21 linux-headers-4.4.0-21-generic
  linux-image-4.4.0-21-generic linux-image-extra-4.4.0-21-generic
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 39 not upgraded.

krish@Vignesh:~$ sudo apt-get install libxml2:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-21 linux-headers-4.4.0-21-generic
  linux-image-4.4.0-21-generic linux-image-extra-4.4.0-21-generic
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  gcc-5-base:i386 gcc-6-base:i386 libc-dev-bin libc6 libc6:i386 libc6-dbg
  libc6-dev libgcc1:i386 libicu55:i386 liblzma5:i386 libstdc++6:i386
  zlib1g:i386
Suggested packages:
  glibc-doc glibc-doc:i386 locales:i386
Recommended packages:
  xml-core:i386
The following NEW packages will be installed:
  gcc-5-base:i386 gcc-6-base:i386 libc6:i386 libgcc1:i386 libicu55:i386
  liblzma5:i386 libstdc++6:i386 libxml2:i386 zlib1g:i386
The following packages will be upgraded:
  libc-dev-bin libc6 libc6-dbg libc6-dev
4 upgraded, 9 newly installed, 0 to remove and 35 not upgraded.
Need to get 19.8 MB of archives.
After this operation, 45.7 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libc6-dev amd64 2.23-0ubuntu4 [2,084 kB]
Get:2 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libc-dev-bin amd64 2.23-0ubuntu4 [68.7 kB]
Get:3 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libc6-dbg amd64 2.23-0ubuntu4 [3,679 kB]
Get:4 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libc6 amd64 2.23-0ubuntu4 [2,586 kB]
Get:5 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) xenial/main i386 gcc-6-base i386 6.0.1-0ubuntu1 [14.3 kB]
Get:6 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) xenial/main i386 libgcc1 i386 1:6.0.1-0ubuntu1 [46.8 kB]
Get:7 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) xenial-updates/main i386 libc6 i386 2.23-0ubuntu4 [2,265 kB]
Get:8 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) xenial/main i386 liblzma5 i386 5.1.1alpha+20120614-2ubuntu2 [84.2 kB]
Get:9 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) xenial/main i386 zlib1g i386 1:1.2.8.dfsg-2ubuntu4 [52.2 kB]
Get:10 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) xenial-updates/main i386 gcc-5-base i386 5.4.0-6ubuntu1~16.04.2 [16.7 kB]
Get:11 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) xenial-updates/main i386 libstdc++6 i386 5.4.0-6ubuntu1~16.04.2 [418 kB]
Get:12 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) xenial/main i386 libicu55 i386 55.1-7 [7,759 kB]
Get:13 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) xenial-updates/main i386 libxml2 i386 2.9.3+dfsg1-1ubuntu0.1 [730 kB]
Fetched 19.8 MB in 3min 51s (85.7 kB/s)                                        
Preconfiguring packages ...
(Reading database ... 242773 files and directories currently installed.)
Preparing to unpack .../libc6-dev_2.23-0ubuntu4_amd64.deb ...
Unpacking libc6-dev:amd64 (2.23-0ubuntu4) over (2.23-0ubuntu3) ...
Preparing to unpack .../libc-dev-bin_2.23-0ubuntu4_amd64.deb ...
Unpacking libc-dev-bin (2.23-0ubuntu4) over (2.23-0ubuntu3) ...
Preparing to unpack .../libc6-dbg_2.23-0ubuntu4_amd64.deb ...
Unpacking libc6-dbg:amd64 (2.23-0ubuntu4) over (2.23-0ubuntu3) ...
Preparing to unpack .../libc6_2.23-0ubuntu4_amd64.deb ...
Unpacking libc6:amd64 (2.23-0ubuntu4) over (2.23-0ubuntu3) ...
Selecting previously unselected package libc6:i386.
Preparing to unpack .../libc6_2.23-0ubuntu4_i386.deb ...
Unpacking libc6:i386 (2.23-0ubuntu4) ...
Setting up libc6:amd64 (2.23-0ubuntu4) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Processing triggers for man-db (2.7.5-1) ...
Selecting previously unselected package libgcc1:i386.
(Reading database ... 243077 files and directories currently installed.)
Preparing to unpack .../libgcc1_1%3a6.0.1-0ubuntu1_i386.deb ...
Unpacking libgcc1:i386 (1:6.0.1-0ubuntu1) ...
Selecting previously unselected package gcc-6-base:i386.
Preparing to unpack .../gcc-6-base_6.0.1-0ubuntu1_i386.deb ...
Unpacking gcc-6-base:i386 (6.0.1-0ubuntu1) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Setting up gcc-6-base:i386 (6.0.1-0ubuntu1) ...
Setting up libgcc1:i386 (1:6.0.1-0ubuntu1) ...
Setting up libc6:i386 (2.23-0ubuntu4) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Selecting previously unselected package liblzma5:i386.
(Reading database ... 243082 files and directories currently installed.)
Preparing to unpack .../liblzma5_5.1.1alpha+20120614-2ubuntu2_i386.deb ...
Unpacking liblzma5:i386 (5.1.1alpha+20120614-2ubuntu2) ...
Selecting previously unselected package zlib1g:i386.
Preparing to unpack .../zlib1g_1%3a1.2.8.dfsg-2ubuntu4_i386.deb ...
Unpacking zlib1g:i386 (1:1.2.8.dfsg-2ubuntu4) ...
Selecting previously unselected package gcc-5-base:i386.
Preparing to unpack .../gcc-5-base_5.4.0-6ubuntu1~16.04.2_i386.deb ...
Unpacking gcc-5-base:i386 (5.4.0-6ubuntu1~16.04.2) ...
Selecting previously unselected package libstdc++6:i386.
Preparing to unpack .../libstdc++6_5.4.0-6ubuntu1~16.04.2_i386.deb ...
Unpacking libstdc++6:i386 (5.4.0-6ubuntu1~16.04.2) ...
Selecting previously unselected package libicu55:i386.
Preparing to unpack .../libicu55_55.1-7_i386.deb ...
Unpacking libicu55:i386 (55.1-7) ...
Selecting previously unselected package libxml2:i386.
Preparing to unpack .../libxml2_2.9.3+dfsg1-1ubuntu0.1_i386.deb ...
Unpacking libxml2:i386 (2.9.3+dfsg1-1ubuntu0.1) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Setting up libc-dev-bin (2.23-0ubuntu4) ...
Setting up libc6-dev:amd64 (2.23-0ubuntu4) ...
Setting up libc6-dbg:amd64 (2.23-0ubuntu4) ...
Setting up liblzma5:i386 (5.1.1alpha+20120614-2ubuntu2) ...
Setting up zlib1g:i386 (1:1.2.8.dfsg-2ubuntu4) ...
Setting up gcc-5-base:i386 (5.4.0-6ubuntu1~16.04.2) ...
Setting up libstdc++6:i386 (5.4.0-6ubuntu1~16.04.2) ...
Setting up libicu55:i386 (55.1-7) ...
Setting up libxml2:i386 (2.9.3+dfsg1-1ubuntu0.1) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
krish@Vignesh:~$ 

krish@Vignesh:~$ sudo apt-get install libstdc++6:i386
[sudo] password for krish: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libstdc++6:i386 is already the newest version (5.4.0-6ubuntu1~16.04.2).
libstdc++6:i386 set to manually installed.
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-21 linux-headers-4.4.0-21-generic
  linux-image-4.4.0-21-generic linux-image-extra-4.4.0-21-generic
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 35 not upgraded.

krish@Vignesh:~$ sudo apt-get install libpopt0:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-21 linux-headers-4.4.0-21-generic
  linux-image-4.4.0-21-generic linux-image-extra-4.4.0-21-generic
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed:
  libpopt0:i386
0 upgraded, 1 newly installed, 0 to remove and 35 not upgraded.
Need to get 28.1 kB of archives.
After this operation, 135 kB of additional disk space will be used.
Get:1 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) xenial/main i386 libpopt0 i386 1.16-10 [28.1 kB]
Fetched 28.1 kB in 1s (23.4 kB/s)                       
Selecting previously unselected package libpopt0:i386.
(Reading database ... 243111 files and directories currently installed.)
Preparing to unpack .../libpopt0_1.16-10_i386.deb ...
Unpacking libpopt0:i386 (1.16-10) ...
Setting up libpopt0:i386 (1.16-10) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
krish@Vignesh:~$ 


```

Well, still I am not getting it done. Somewhere the problem is. I got  another doubt. What is a PPD file? In the Add Printer Device, it asks  for ppd file. 

Another thing, in this URL:   [https://itsidukki.files.wordpress.co...n_tutorial.pdf]("https://itsidukki.files.wordpress.com/2011/11/canon-lbp2900_printer-installation_tutorial.pdf")

The author says: 


```

sudo /etc/init.d/cups restart 
sudo /usr/sbin/lpadmin -p LBP2900 -m CNCUPSLBP2900CAPTK.ppd -v ccp:/var/ccpd/fifo0 -E 
sudo /usr/sbin/ccpdadmin -p LBP2900 -o /dev/usblp0 
sudo /etc/init.d/ccpd start 
sudo /etc/init.d/ccpd start


```

Can I try this?


Sorry to trouble you so much. Bit worried that I am not able to print.

Thanks a lot,
Kannan

---

### Post by Geoffrey_Arndt on 2016-10-31
Here's something else to try to get your printer going.   It's the process of connecting a "Classic Printer" to Googles "Cloud Print" . . . worth checking into anyway:

[https://support.google.com/cloudprint/answer/1686197?visit_id=1-636135670822501515-106227349&hl=en&rd=1](https://support.google.com/cloudprint/answer/1686197?visit_id=1-636135670822501515-106227349&hl=en&rd=1)

---

