---
title: "ubuntu installation help needed"
date: 2011-11-09
forum: New to Ubuntu
---

### Post by cherryw on 2011-11-09
Hello guys,
Im new to ubuntu and I have some doubts regarding its installation.  During the installation process it asks whether to install it by  formatting the complete hard drive or specify the partitions manually.  Actually many guys suggested me that I need to choose the 2nd option  bcoz that will be more effective. But i am not highly knowledgable with  filesystems and partitions of linux(UBUNTU). So pls tell me how to do it  with the 2nd option . I want to completely erase the existing OS and  install ubuntu. I will definitely help some more ppl back after gaining  some experience in ubuntu and ill be grateful to whoever gives a  soultion for this.

And also pls tell me how to create the C,D,E,F drives like in windows in Ubuntu or their equivalents.

---

### Post by Rodney9 on 2011-11-10
The easiest way is to let the installer use the entire drive, you just tell it which drive, and it automatically formats the drive  for you.

Rodney

---

### Post by Miljet on 2011-11-10
Linux doesn't use C,D,E,etc to name drives and partitions. Your first drive will be sda and the first partition will be sda1. Next partition on the same drive will be sda2, and so forth. The second drive will be sdb and its partitions will be sdb1, sdb2,sdb3, and so forth.

---

### Post by cherryw on 2011-11-10
generally do you recommend 4 drives for Ubuntu like windows(C,D,E,F)?
And also pls answer my another question I specified above that is "How to do this the manual way,I mean what partitions or anything else shall i create?"

---

### Post by Rodney9 on 2011-11-10
I did read your question, as you are asking in the Absolute Beginner Talk forum, I thought it would be best for you to use the whole disk.

However if you wish to learn, here is the Ubuntu How To page for partitioning - [https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Rodney

---

### Post by cherryw on 2011-11-10
I read it but its too confusing. Anyways if I use the (erase and use the entire disk) option will it create everything needed like ( swap,root,home etc). But I also have another doubt is the option (specify partitions manually) more effective than this one? And also tell me exactly which option is best to erase the entire disk and install Ubuntu freshly.

---

### Post by Rodney9 on 2011-11-10
> **cherrywarrior said:**
> I read it but its too confusing. Anyways if I use the (erase and use the entire disk) option will it create everything needed like ( swap,root,home etc). But I also have another doubt is the option (specify partitions manually) more effective than this one? And also tell me exactly which option is best to erase the entire disk and install Ubuntu freshly.

The erase entire disk install will format to Ubuntu/Linux standards and as you say that will be swap home root etc.

Some people like to manually format for their specific needs, but for most home users the **Erase disk and install Ubuntu** is *easiest and best* way.

Here is the way it will go - [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by Denver Dave on 2011-11-10
The installation process always scares the crap out of me - asks if we want to erase the entire disk before we get to identify which disk.

---

### Post by mastablasta on 2011-11-10
still in this case i agree, erase the entire disk and install ubuntu is the best and easiest option for beginner. 
 
also Linux filesystem doesn't fragment as much as windows, so if you wish you can always add more partitions later on or change the size of existing ones (by using livecd and gparted porgramme). gparted is a nice programme with GUi that is really easy to use. so for now just go with default install. later if you see you need more you can add more.

---

### Post by WasMeHere on 2011-11-10
> **cherrywarrior said:**
> Hello guys,
Im new to ubuntu and I have some doubts regarding its installation.  During the installation process it asks whether to install it by  formatting the complete hard drive or specify the partitions manually.  Actually many guys suggested me that I need to choose the 2nd option  bcoz that will be more effective. But i am not highly knowledgable with  filesystems and partitions of linux(UBUNTU). So pls tell me how to do it  with the 2nd option . I want to completely erase the existing OS and  install ubuntu. I will definitely help some more ppl back after gaining  some experience in ubuntu and ill be grateful to whoever gives a  soultion for this.

And also pls tell me how to create the C,D,E,F drives like in windows in Ubuntu or their equivalents.

Hi cherrywarrior,

It will be easier to help if you describe your computer (brand, age, cpu, disk size, graphics card/chip, network card/chip/adapter ...) and how you plan to use your computer. Then we can give more specific advice. I think that the advice in this thread is relevant: just select the most 'standard' options. But with more details from you, the advice to you will also be more detailed.

Have fun finding out about Ubuntu :-)
Olle

---

