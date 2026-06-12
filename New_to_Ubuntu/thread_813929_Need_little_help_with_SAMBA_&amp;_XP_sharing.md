---
title: "Need little help with SAMBA &amp; XP sharing"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by nantax on 2008-05-31
My Hardy Heron is working with no major problem and I'm now beginning to explore on how to access network shares. I have read the tutorials posted on this forum but its just not going into my head.

I have another PC downstairs named COMMON running WindowsXP and my problem is that when I type smb:\\common, my PC will display a blank window. but when I type smb:\\common\movies (shared folder), Ubuntu prompts me with a login/password screen and I can access the share.

Is there a way to list the shared folders residing on the COMMON PC just like in XP wherein you are asked for the login/pass and see them?

Thanks in advance...

---

### Post by sayakb on 2008-05-31
smb://COMMON/ should display the shared folders. Which process have you used to set a password protected sharing? Have you set the guest password and added Movies to Guest?

---

### Post by nantax on 2008-05-31
I have not yet touched any setting. I was afraid that I might mess things up and was just reading along the other posts that did not involve any editing. So I tried that advice of entering the shared folder directly and it worked.

I was just wondering if its possible for Ubuntu to ask the login password when I browse the COMMON computer and list the shared folder without touching stuff. And if its not possible how do I get about it?

---

### Post by dvessels on 2008-05-31
I have the same prob. Not until v8.04. 7.10 played real nice w/XP, but am only able to get v8 to SEE the XP shares. When Ub tries to get into the share it locks up the nw browse. I'm seriously considering returning to v7.10. Ironic -- v8 is supposed to be the really good one LTS. I'm afraid now it stands for "Lots of Trouble with SAMBA".:roll:

---

### Post by sayakb on 2008-05-31
When you open COMMON, it shall just display the shared folders but not their files. So when you attempt to open a folder, you will be asked for password. This can be done using the following process:
1. Right click on My Computer and click Manage. There, select Local Users and Groups from left column.
2. Click on Users folder on the right side(among Users and Groups, that is)
3. Right click on Guest and select "Set Password". Click "Proceed" if you see a dialog box.
4. Enter the new password and press OK. Close the Computer Management Window.
5. Now open My Computer.\
6. Goto Tools->Folder Options->View tab
7. Scroll down and **uncheck **"Use simple file sharing"
8. Close the window.
9. Now navigate to the folder you wish to share. Right click and select Properties. Click onSharing tab and click "Share this Folder".
10. Click on Permissions button and Remove the "Everyone" permission. 
11. Press Add button. Press Advanced (in the new window opened) and click Find Now. 
12. Now select **Guests **from the list and press OK. Press OK again.
13. Now at the "Permissions for xxxxxx" press Apply and then OK. Press OK again to close the properties window.

Try if this works.. Sorry, took a long time to type this whole thing ;)

---

### Post by Nampla on 2008-05-31
have you set up a user in your linux system for samba? ensure you do this. Remember linux is secure! not like windows who lets anyone in. You need to have permission in Linux.  
To do this in a terminal type sudo smbpasswd -a (enter a name of a user on the system) it will ask for a password and enter one (i reccomend it be different from the one you use for primary user for security). 
Now ensure that you have the shared folder correct by allowing others to read and write.

Good luck

---

### Post by nantax on 2008-05-31
Thank you for the response LinuxIsInnovation and Nampla.

@LinuxIsInnovation
When I open up COMMON, I can't see any shared folders, it is blank, so unless I know specifically what folders are shared, I can't access it. But if I add the shared folder like smb://COMMON/movies, I can access it with no problem.

@Nampla
I know linux is secure, but I have not yet reached the stage where XP needs to share something owned by Ubuntu. So its more like Ubuntu trying to gain access to shared folders owned by XP.

Lol, just noticed that Compiz is gone. Icing on the cake... Just tried to find a way around the NetworkManager error when you shutdown and I decided to remove the splash screen entirely and display the login/logout screen at 1024x768 resolution. Xorg now boots at 640x480, running that reconfigure command gave me 1024x768. 1280x1024 with Compiz used to work before. Oh well... One problem at a time. I just need to see the shared folder on COMMON at the moment.

---

### Post by sayakb on 2008-05-31
Try accessing the Shares from XP itself and check whether you can see the folders or not. I think the C$, D$ etc. administrative shares are somehow disabled on your XP box ad because of that, you're not being able to see the folders.

---

### Post by nantax on 2008-05-31
Everything is working right (I dual boot XP and Ubuntu and can see the shares in XP) except that when I type smb://Common, the right pane where the folders are supposed to be shown is blank. But I can access smb://Common/movies, smb://Common/utorrent, smb://Common/Installer directly, I get the login/password dialog and I can browse the folder. If I type just smb://Common, I am not asked anything, and I can't see anything.

---

### Post by oedha on 2008-05-31
what if you mount that share folder ?
open terminal :==> sudo apt-get install smbfs  { to install smbfs }
then :==> sudo mkdir /media/x                 { x is just a folder name }
then :==> sudo mount -t smbfs //computer_name or ip/shared folder name /media/x

i hope this can help.....

---

### Post by sayakb on 2008-05-31
You might as well create a Launcher.
Right click on desktop and select Create Lancher. Set type as "Location". Enter whatever name and smb://COMMON/movies as Location.

---

### Post by nantax on 2008-05-31
LoL, I give up, (for tonight). I'm just going to remember the shared folder name and access it directly. :)

---

### Post by dvessels on 2008-06-07
When I put "smb://home/" ('home' is my home workgroup name) in the address line, it displays every PC which is online at that time in my home network. Used to be, (before Ubuntu version eight) when I'd open one of the machines (I have shared them all internally) it would then display their contents. I was able to very easily send/receive files back & forth between the Ub & Win machines. Now when I try to browse into the Windows machines it simply locks up that task such that I am forced to force the browser closed (using the "force quit" app). Please--what have I done to anger the Ubuntu gods?!?!?](*,)

Oh, and THANK YOU and all those who serve as info-people/resources for those of use Linux-challenged individuals!

---

### Post by jonandrews on 2008-06-09
I've put an illustrated guide to 

integrating Ubuntu PC's into a Windows 

home network onto a website:

[www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/)

See if that is helpful...

---

