---
title: "Windows/Ubuntu Install Partition Question"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by gekkexx on 2008-11-24
Hi there, 

I am trying to install a dual boot Windows XP / Ubuntu 8.10 system with Windows already installed.  At first when I got to the disk partition stage, the guided partition wouldn't work and resulted in some sort of error.  Then I ran disk defrag in Windows and tried to run the install again.  However, this time around, I no longer get the option of using the 'Guided' option.  I.e., I only have the options of 'Guided - use entire disk', 'Guided - use the largest continuous free space', and 'Manual'.  

Does anyone have any suggestions for me?

Thanks a lot.

---

### Post by jemate18 on 2008-11-24
> **gekkexx said:**
> Hi there, 

I am trying to install a dual boot Windows XP / Ubuntu 8.10 system with Windows already installed.  At first when I got to the disk partition stage, the guided partition wouldn't work and resulted in some sort of error.  Then I ran disk defrag in Windows and tried to run the install again.  However, this time around, I no longer get the option of using the 'Guided' option.  I.e., I only have the options of 'Guided - use entire disk', 'Guided - use the largest continuous free space', and 'Manual'.  

Does anyone have any suggestions for me?

Thanks a lot.

You can try WUBI..

1. Boot to your windows OS...
2. Insert Ubuntu Installer. 
3. (Autorun) It should prompt you about installing Ubuntu inside windows.
4. Choose the harddrive on which to install
5. Choose the size of the installation

---

### Post by benhur99ph on 2008-11-24
Hmmm, I am not sure on how you are to proceed because the easiest way is to use the parition manager. The manual option is for the more advanced users. There are also other tools for partitioning like gParted -- [read more...]("http://www.packtpub.com/article/Partitioning_with_GParted")

You could try installing it via Wubi... though there maybe some issues regarding performance because you will be installing Ubuntu on an NTFS filesystem, and since you are installing it inside Windows, should your Windows installation crash, your Ubuntu goes along with it.

Edit: Waaaaaaa! jemate18 beat me to it XD

---

### Post by gekkexx on 2008-11-24
Even the Windows based installer does not seem to work, it reads the CD to a certain point and then I get the following message: "Could not access the CD, please make sure other applications are not trying to use it and try again."  Could it be a problem with the way the iso was burned?

---

### Post by jemate18 on 2008-11-24
> **gekkexx said:**
> Even the Windows based installer does not seem to work, it reads the CD to a certain point and then I get the following message: "Could not access the CD, please make sure other applications are not trying to use it and try again."  Could it be a problem with the way the iso was burned?

Try checking out the CD for errors.

Insert the CD and restart. Make sure CD is the first boot option, once on the menu....choose the option check CD for errors.... I'm not sure about the exact words, but the menu will say it clearly.....

---

### Post by gekkexx on 2008-11-24
The report comes back clean, theres nothing wrong with the CD.  But now I get the option again of partitioning the disk using the 'Guided' option but I keep getting the same error that I got before:

"An error occurred while writing the changes to the storage devices.  The resize operation has been aborted."

Has anyone seen this type of error before?

Thanks a lot.

---

