---
title: "12,04,1    installation options"
date: 2012-09-07
forum: New to Ubuntu
---

### Post by Tarnand on 2012-09-07
Yesterday I downloaded the installation disc image, burned CD, freed up 75GB on Windows 7 partition and ran the installation.  Then I saw the screen giving me four installation options. The default option was something like this:  "*Install Ubuntu inside Windows 7"*.  What does it really mean???

What I thought would be the best approach for me was to install Ubuntu on the above mentioned partition so none of the OS's "overlaps" the other.  Also, when I am sufficiently comfortable using Ubuntu I would want to remove it completely and revert all the changes I have already done i.e. give the Ubuntu partition back to Windows 7.   Then I would install Ubuntu on another laptop as the only OS there.

Can someone please give me a solid advice on which installation option should I choose?

Thank you.

---

### Post by offgridguy on 2012-09-07
This seems like a long way around to try out ubuntu.  Didn't you get the option of a trial without
the complete install?
Are you sure it said "install ubuntu inside windows 7" and not "alongside windows 7"
I am asking because I have just installed ubuntu 12.04 within the last hour alongside windows 7
and those were the prompts it gave me.

---

### Post by mwl128340 on 2012-09-07
ubuntu is giving you an option to install inside the windows partition. its called a wubi install. i personally have no experince with a wubi install but have read about alot of problems with it here on the forums. it will install ubuntu inside of windows like it says but, and this is just my opinion, why boot up an os to run another os. i use a dual boot with wndows and mint and works like a charm. dual boot might be worth looking into although in your case, since youll be removing the linux partition, before you install linux make sure you have your windows disk onhand so when you remove it recovring the mbr will be easier with the windows disk.

---

### Post by Epodx64 on 2012-09-07
If you just want to try Ubuntu before committing to it just burn the LiveCD boot it from your Cdrom drive and select "Try Ubuntu" You can try it without any risk to your current O.S. and without any risk to Ubuntu if you screw something up just reboot and its all reverted back to its original state.

---

### Post by offgridguy on 2012-09-07
> **mwl128340 said:**
> ubuntu is giving you an option to install inside the windows partition. its called a wubi install. i personally have no experince with a wubi install but have read about alot of problems with it here on the forums. it will install ubuntu inside of windows like it says but, and this is just my opinion, why boot up an os to run another os. i use a dual boot with wndows and mint and works like a charm. dual boot might be worth looking into although in your case, since youll be removing the linux partition, before you install linux make sure you have your windows disk onhand so when you remove it recovring the mbr will be easier with the windows disk.

Thank you for the clarification, I have heard of installing linux inside windows but
didn't know what it meant.  I agree, why install one os inside another to get it to
operate.

---

### Post by barrykgerdes on 2012-09-08
I have just completed an install of 12.04 inside windows. You need to get wubi.exe from Ubuntu. The version I have on my iso built disk gives the same options as you got, not the inside windows option.

For the uses I give to Ubuntu this is the ideal type of installation as you can do an install or uninstall from inside windows. I have installed every version of ubuntu from 10.04 in windows XP or Win 7 as a secondary system to test compiles of Stellarium.

I have also installed 12.04 as a virtual system in VMware 

just run wubi.exe from windows and follow the instructions but give Ubuntu at least 20 GB of space if you have it.

It will install everything needed in a folder called ubuntu

Barry

---

### Post by Tarnand on 2012-09-08
Thank you for your comments.  It seems like the best way to start is to go with the default option: "install inside Windows 7".  Thanks again.

---

