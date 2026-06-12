---
title: "Newbie Thanks/Sharing a folder in a Windows LAN"
date: 2005-12-13
forum: Outdated Tutorials &amp; Tips
---

### Post by randbag on 2005-12-13
I'm one week new to Linux and just set up my first machine using Ubuntu. I've learned a lot from this forum and want to thank everyone who's contributed.

I'm in a classroom in a large school district and needed a way to share folders securely and without wasting valuable computing resources. (As a lowly teacher, I am not allowed any access to any of the servers. And as an experienced teacher, I want sometimes to control the share folder.) What I finally did was install Ubuntu on a cranky old Compaq and then create a share folder for my students who use a mix of Win98 and WinXP computers. 

While toiling with this, I found a lot of instructions that left out something a newbie like me really needed to know, so I put it all together in one place, borrowing from others in this forum. Ubuntu/Linux veterans, please correct anything I have wrong. Here it is:

**STEP 1: Set up the user(s) who will access the share folder.**

1. In Ubuntu, click on:**  System, Administration, Users and Groups**.
2. In the Users and Groups window, add the username(s) of the person(s) who will access the share folder. 
3. Decide which password to give to that user and enter it twice; it won't affect the password the user will need to access the folder, as you will set that later. (I decided not to share that password with the user group that includes my students so I could better control the share folder.)
4. Click **OK**.

**STEP 2: Set up the Share Folder**

1. Create/decide which folder to share.
2. Right-mouse click that folder and click on: **Share folder**
3. In the Share Folder window, select: **Share with: SMB**
4. Check: **Allow Browsing Folder**
5. Click: **General Windows Sharing Settings**
6. Fill in the** [B]Host Description** box
7. Fill in the **domain/workgroup **box with the name of your domain or workgroup
8. Click **OK**
9. Right-mouse click the share folder again and click on: **Properties**
10. Click on the **Permissions **tab
11. In the **Others **row, make sure to check all of the boxes: **read, write, execute**

**STEP 3: Set up Samba**

*Note: To use these instructions in Ubuntu, click on Applications then Accessories then Terminal to open the command terminal.*

1. Set up/install Samba with the following command: **sudo apt-get install samba**
2. Once the server is installed, issue the following command: **sudo gedit /etc/samba/smb.conf**
(This will open a text editor)
3. Make the following changes in the file: **workgroup = WORKGROUP** 
(insert the name of your workgroup or domain in place of **WORKGROUP**)
4. Underneath it, add: 	**netbios name = name_of_your_server** (no spaces)    
For example: **netbios name = kenny_smb_server**
Another example: **netbios name = yearlyreview**
5. Make sure **security **is set to **user**. 
6. Scroll down until you see "[homes]" and set:	**browseable = yes **
and **writable = yes**
7. Save the changes and close the text editor.
8. Create a samba user. The code for this is: **sudo smbpasswd -a `whoami`**
An example is: **sudo smbpasswd -a 'susan'**
9. Set that user's password when prompted; it can be different from the one set earlier for the computer.
10. Restart Samba for this to take effect: **sudo /etc/init.d/samba restart **
11. Close the terminal editor.

You're now ready to access that shared folder from a Windows computer. 
When in a Windows computer, **browse network neighborhood**/**network places**. You may need to click on **Entire Network** and navigate to the workgroup/domain. When there, look for the name you gave earlier to the Ubuntu computer and share folder. You may wish also to right mouse click the Ubuntu share folder when you find it and map it to a drive. The first time you access the folder, you'll need to provide the password you created earlier. If you choose for your Windows computer to remember the password, you won't need to enter it any more.

That's it. Forum contributors please let me know if I made errors here. I'll try to compile them all and repost a corrected process. Thanks again.

---

