---
title: "NAS - Adding removing files using Ubuntu?"
date: 2014-04-26
forum: New to Ubuntu
---

### Post by Bialetti741 on 2014-04-26
Hi, i'm new to Linux/Ubuntu.

Can anyone advise if it's possbile to access my NAS (Network Attached Storage) using Ubuntu?

I'm wanting to be able to add and remove files as i did using Windows.

Any suggestions?


Thanks,

---

### Post by nerdtron on 2014-04-26
Please provide more details. What is this NAS device that you are using and how do you add/remove files when you use windows?

---

### Post by Bialetti741 on 2014-04-27
Hi, it's a Seagate Go-Flex NAS 3TB. In windows, i installed the installation disc that came with it and it allows me to access the NAS through my LAN via my router. My PC and the NAS are both hardwired to the network via an unmanaged switch. If you need more info, please let me know. Sorry about late respose. Can you help with accessing NAS on this setup not having to use Win7?

---

### Post by squakie on 2014-04-27
Do you know IP address of the NAS?  Can you ssh to that IP address?  Does the NAS show if you click on Network while in the file manager?

---

### Post by Bialetti741 on 2014-04-27
Yes i know what the IP of the NAS is and if i put it on my web browser i can log into it (via Seagates server) but will take ages to transfer files to/from NAS i think. I don't know what ssh is? i've quickly googled it, but don't know what it is/how to use it. I'll check file manager when i'm back on my main PC (currently using someones laptop).

---

### Post by squakie on 2014-04-27
If you know the userid/password, then try the following:

Access via the file manager:
[LIST]
[*]open the file manager 
[*]on the left hand side is a selection that says "Network" 
[*]click on that and see what shows.  If your NAS doesn't directly show there, you may need to click on the "Windows Network" folder - but I've never done that.  If you NAS does show, just click on it and see if you can now navigate it.  Try dragging a test file to/from it and see what happens.  Try deleting a test file and see what happens.
[*]If you don't see your NAS, you can try the "Connect to server" option - enter sftp://<IP address here> 
[/LIST]

Access via ssh (secure shell - basically a secure command line connection):
[LIST]
[*]open a terminal window (use terminal in the menus) and log in with your normal user name and password.  The password is not echoed to the screen but it is being accepted by the system - press enter when done. 
[*]type sudo ssh <insert IP address here>   Example: sudo ssh 10.0.0.110 
[*]the sudo password is your normal password, and again it is not echoed to the screen 
[*]when prompted, enter the userid for NAS 
[*]when prompted, enter the password for the NAS 
[*]you should now have command line access to the NAS 
[/LIST]

---

### Post by migs73 on 2014-04-29
I have nearly the same network setup as you. For me to access my goflex I have to click on browse network then click on the windows network folder ( ignore the NAS if it appears at the same level as the windows network folder as you cannot login to it from here for some reason) then click on SEAGATEGROUP then click on your NAS then the folder you want to access. If the user name and passwords are set up it will prompt you for those at some point too. Once this is done it is drag and drop/cut 'n' paste whatever you normally do. If you have any more problems let me know.

Mike :)

---

### Post by migs73 on 2014-04-29
Just a quick extra tip, once you have logged into NAS, if you click 'Ctrl +D' it'll bookmark the location and it will be added to the lefthand pane. Assuming you have set the password to remember for ever you are now only one click from your NAS.

Mike

---

### Post by Bialetti741 on 2014-04-29
Hi All, sorry about the late reply again (i'm struggling to get a minute to myself to get on my PC).

Right i have finnaly manged to get access to my NAS. Thank you all for your assistance.

I installed SAMBA, then i accessed my Network via the file manager, then i tried accessing the Seagate group on the first level and didn't work. Thanks to Mike (migs73) i then tried accessing via the Windows group which also had a Seagate group and it aked me for login....BINGO....logged in and i can now access my NAS and all the files.

Guys, that was actually pretty simple now that you have shown me what to do.....i'm such a Noob :P

Thanks for all your excellent advice.....this forum is Awesome :P

---

