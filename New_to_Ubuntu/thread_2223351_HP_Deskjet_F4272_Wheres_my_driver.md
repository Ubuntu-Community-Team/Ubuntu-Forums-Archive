---
title: "HP Deskjet F4272 Wheres my driver"
date: 2014-05-10
forum: New to Ubuntu
---

### Post by Bill_Power on 2014-05-10
Im totally new to Linux. I eventually succeeded to install Ubuntu 14.04 on my pentium 4 seperated from my previous XP as I put a new hard drive in the computer just for Ubuntu.

I had the excellent HP software in Windows and I was pleased to see I could have the hplip in ubuntu which promised to be a similar programme.

I have downloaded it but cannot find any trace of it except a file in the file cabinet item called hplip.3.4.14.run and when I click on it it opens somthing called gedit and basically thats it.

I use my scanner a lot but as I have no clue where the programme is hiding or even if it instaled I am totally at a loss sabout waht to do.
The Windows version allowed control of all these functions and I could produce readable PDFs with that no bother etc now I cannot even do a scan.

HELP

---

### Post by rburkartjo on 2014-05-10
bill open the ubuntu software center and in the upper right hand corner there is a search bar. type in hplip it will bring up a program called hplip toolbox. install it. it should be installed under either preferences or system tool. so navigate their from the main menu. open it and follow the directions.

---

### Post by oldfred on 2014-05-10
The hplip from HP is usually quite a bit newer version. 
With my printer I had to have the HP version as the repository version was too old.

The .run file is just a bash/test file, so it default loads into edit mode.
You may have to change to executable, by right clicking on its properties.

and then in terminal change to folder where you downloaded it and run it 

My log file shows I did this as it was in my Downloads folder: not sure why but it seems to want to run without sudo. Change to your downloaded location/folder and version:
 cd Downloads
 sudo bash hplip-3.12.11.run 
bash hplip-3.12.11.run 
hp-setup

---

