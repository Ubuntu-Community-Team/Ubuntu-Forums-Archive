---
title: "Steps for Installing Ubuntu16.04"
date: 2018-05-10
forum: New to Ubuntu
---

### Post by sdeflabofficial on 2018-05-10
HI,
We are trying to Install ubuntu 16.04 in DELL precision T7 610 Workstation with GeforceGTX Graphics card, the below mentioned are the steps which we are going to follow, can anybody check it out..and please correct us if its wrong   
 1.Setting up Linux(Ubuntu 16.04LTS)(offline mode) 
     1.a Inserting the bootable DVD in to workstation
   1.b Continunig with "Install ubuntu"
   1.c Without creating partition,we continued
   1.d Select Country
   1.e Giving System Name & password
2.Enabling Root Account(offline mode)
   2.a sudo passwd root
   2.b sudo sh -c 'echo "greeter-show-manual-login=true">>/etc/lightdm/lightdm.conf
   2.c restarting workstation and choose to login as root
3.Installation of Graphic card Drivers(Offline Mode)
4.Updating System Default Packages(Online Mode)

waiting for response

Thanks in Advance..

---

### Post by yancek on 2018-05-10
Ubuntu doesn't enable the root account as a default but uses sudo so I would suggest before you being, you read the Ubuntu documentation at the link below before installing and making that decision.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Topsiho on 2018-05-10
A detailed description is available at

[https://tutorials.ubuntu.com/tutorial/tutorial-install-ubuntu-desktop#0](https://tutorials.ubuntu.com/tutorial/tutorial-install-ubuntu-desktop#0)

which you can read before actually installing Ubuntu.
Ubuntu 16.04 is not the latest LTS-version; you might consider installing 18.04 instead.
A reason to install 16.04 nonetheless is that it has ripened during the past two years, while 18.04, being brand new may still have it's yet unknown deficiencies.
That said, I run 18.04 with almost no problems at all, none serious.

Topsiho

---

