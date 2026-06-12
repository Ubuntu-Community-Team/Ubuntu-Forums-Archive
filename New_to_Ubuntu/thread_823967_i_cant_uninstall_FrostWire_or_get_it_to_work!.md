---
title: "i cant uninstall FrostWire or get it to work!"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by zman2209 on 2008-06-09
would some one please help me i am new to ubuntu, and having issues with frost wire and need help to uninstall it, install the right java and reinstall frost wire, i was talking to some one earlier and they told me to use sudo apt-get remove frostwire to remove frost wire but i got this message in return 

user@user:~$ sudo apt-get remove frostwire
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

---

### Post by dje on 2008-06-09
Do what it says, in a terminal run the following:
```
sudo dpkg --configure -a
```

---

### Post by zman2209 on 2008-06-09
ok i did that and then i retyped sudo apt-get remove frostwire
 and i got a message saying

You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java6-bin: Depends: sun-java6-jre (= 6-06-0ubuntu1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

and i entered apt-get -f install and got this message

user@user:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

---

### Post by dje on 2008-06-09
You need to give it root permission, do the following:
```
sudo apt-get -f install
```
sudo gives root permission to a command, and root can do ANYTHING so always be careful with root

---

### Post by zman2209 on 2008-06-09
yea i just noticed that a secound ago i did that and i got the packege configuration witch looks like this

Package configuration

 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring sun-java6-jre &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474;                                                                           &#9474; 
 &#9474;     its subject matter.  It supersedes all prior or contemporaneous       &#8593; 
 &#9474;     oral or written communications, proposals, representations and        &#9618; 
 &#9474;     warranties and prevails over any conflicting or additional terms      &#9618; 
 &#9474;     of any quote, order, acknowledgment, or other communication           &#9618; 
 &#9474;     between the parties relating to its subject matter during the term    &#9618; 
 &#9474;     of this Agreement.  No modification of this Agreement will be         &#9618; 
 &#9474;     binding, unless in writing and signed by an authorized                &#9618; 
 &#9474;     representative of each party.                                         &#9618; 
 &#9474;                                                                           &#9618; 
 &#9474;                                                                           &#9618; 
 &#9474; For inquiries please contact: Sun Microsystems, Inc., 4150 Network        &#9618; 
 &#9474; Circle, Santa Clara, California 95054, U.S.A.                             &#9618; 
 &#9474;                                                                           &#9646; 
 &#9474; DLJ v1.1                                                  27APR2006ANS    &#8595; 
 &#9474;                                                                             
 &#9474;                                  <Ok>                                       
 &#9474;                                                                           &#9474; 
 &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496; 
                                                                               


and i dont know what to do now

---

### Post by dje on 2008-06-09
use tab to highlight ok and then press return, see if that works

---

### Post by zman2209 on 2008-06-09
ok that worked but now im getting this message saying theres a serious warning

dpkg: serious warning: files list file for package `sun-java6-bin' missing, assuming package has no files currently installed.
125311 files and directories currently installed.)
Preparing to replace sun-java6-bin 6-06-0ubuntu1 (using .../sun-java6-bin_6-06-0ubuntu1_i386.deb) ...
Unpacking replacement sun-java6-bin ...
Preparing to replace sun-java6-jre 6-06-0ubuntu1 (using .../sun-java6-jre_6-06-0ubuntu1_all.deb) ...
sun-dlj-v1-1 license has already been accepted
Unpacking replacement sun-java6-jre ...
Setting up sun-java6-bin (6-06-0ubuntu1) ...

Setting up sun-java6-jre (6-06-0ubuntu1) ...

---

### Post by dje on 2008-06-09
hmmm never seen that before, but is java installed. if it is its probably ok to ignore it

---

### Post by zman2209 on 2008-06-09
how do i tell if it was installed?

---

### Post by dje on 2008-06-09
post the output of:
```
java -version
```

---

### Post by zman2209 on 2008-06-09
kk it worked thank you. kk now if i install frostwire should it work?

---

### Post by dje on 2008-06-09
only one way to find out ;), install it and see if it works

---

### Post by zman2209 on 2008-06-09
kk this is guna be ineresting because it looks like it never deleted even though it did hm.. well ill just have to see

---

### Post by s3r4phim on 2008-06-09
Yea, it should work. Just get the .deb file online and run it w/GDebi Package Installer. It will prompt for a password, and then install. It will appear in the "Internet" catagory in the "Applications" drop down menu. Remember with FrostWire the following things:

1. When it asks you where to store downloaded files, the default is ~(user home directory)/Shared. Only agree to this if you want others to be able to acces the stuff you download. It is more secure to just make a FrostWire Downloads folder in your home directory and put everything there, so you are the only one who can access it.
2. When it asks to scan your HD for media files, always say no, as it will give people online more information than is secure. If you want to upload things to the FrostWire server system, do so manually. It is very dangerous to give a web app the ability to scan your hard drive.

Good Luck!

---

### Post by zman2209 on 2008-06-09
hmmm... i dont think it likes me cause it still dose not work =.=

---

### Post by zman2209 on 2008-06-09
oh never mind i got it to work my friend told me to run sudo update-java-alternatives -s java-6-sunand it works now =) thanks for helping me

---

