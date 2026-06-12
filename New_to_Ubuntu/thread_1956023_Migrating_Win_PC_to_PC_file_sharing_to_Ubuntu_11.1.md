---
title: "Migrating Win PC to PC file sharing to Ubuntu 11.10 to"
date: 2012-04-10
forum: New to Ubuntu
---

### Post by Boyntonstu on 2012-04-10
Prior to installing 11.10 I used an ethernet PC to PC connection.

I could share files and use a Brother printer connected to one PC.

My wife's PC ran WinXP-SP2 and mine used Win7 Home Premium.

When I boot Ubuntu it indicates that it has a wired connection.

What steps must I follow to connect the 2 PC's?

If I can manage that, I believe that I will be able to use Ubuntu for almost everything except Netflix.

---

### Post by zandman on 2012-04-10
As far as i know you have to install Samba to do file-sharing from a Linux-system to a Windows machine. On the machine that has to read from another you need the samba client (that's the easy part), on the other one you need to setup the samba server (that's more complicated).
"http://www.samba.org/"
"http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch10_:_Windows,_Linux,_and_Samba"

It requires some reading and testing, but it's not overly complex.
If you want to move the data from the Win-system to the Linux-system you should only have to install the samba client on the Linux-system.
Then enable the file-sharing on the Win-system and you should be good to go.

---

### Post by slyspring on 2012-04-28
To preface this, I am using Ubuntu 11.10 64-bit and am actively sharing with my other Win7 computer.

OMG! I just solved this in 15 minutes with just SAMBA and a few Win7 tweaks! Follow these to the letter

1. Using Ubuntu, open Terminal and run **sudo apt-get install samba**

2. Run the command sudoedit **/etc/samba/smb.conf**

3. Under "Global Settings", where it says #Change this to the Workgroup/NT-domain....#, change the workgroup the actual name of your group. Also, add the string directly underneath that called **netbios name = ** and type the EXACT name of your computer.

4. Hit CTRL and the letter X at the same time to exit. When, asked to save, press the letter Y, and hit Enter.

On to Windows 7 (bane of existence)

1. Open Network and Sharing Center.
2. On the left, click "Change Advanced sharing options"
3. Perform the following (make sure your computer is set for Home/Work):
  a: Network Discovery - On
  b: File and Printer Sharing - On
  c: Public Sharing - On
  d: file sharing connection - 128-bit encryption
  e: password protected sharing - off
  f: use user accounts (just as a precaution)
4. In the Control Panel, select User Accounts.
5. Enable the Guest Account. It is not automatically a part of every folder for permissions sake.
6. On the in the folder permissions (or the root of the external drive you want to share), add the Guest account, and I recommend you give it up to MODIFY rights to all folders and subfolders you need. NTFS permissions trump Share permissions.
7. Create the share you want, with me STRONGLY recommending adding the Group user and giving it up to Modify rights. 

All that other crap about winbind and nss... i undid on my Ubuntu, and my fixes persisted forever. take it or leave it.

---

