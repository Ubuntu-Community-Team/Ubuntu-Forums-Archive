---
title: "SSH connection"
date: 2011-10-12
forum: New to Ubuntu
---

### Post by pmohankumar on 2011-10-12
Hi friends,

Iam using ubuntu 10.04.
i installed openssh-server.
i dono to connect other ubuntu system through ssh.

how to connect other ubuntu systems using ssh?

---

### Post by haqking on 2011-10-12
> **pmohankumar said:**
> Hi friends,

Iam using ubuntu 10.04.
i installed openssh-server.
i dono to connect other ubuntu system through ssh.

how to connect other ubuntu systems using ssh?

you can only connect if they are running ssh and you are authorised to connect, though if you dont know how to SSH it is unlikely you are authorised to connect ;-)

```
ssh username@ipaddressorhostname
```

---

### Post by pmohankumar on 2011-10-12
Thanks Haqking,

i just installed ssh in client system and connected using this command:

ssh username@ipaddress
its working friend.

---

### Post by haqking on 2011-10-12
> **pmohankumar said:**
> Thanks Haqking,

i just installed ssh in client system and connected using this command:

ssh username@ipaddress
its working friend.

cool, please mark the thread as solved using the thread tools menu.

Cheers

---

### Post by anur.bhargav on 2011-10-12
I think this is the GUI method...
Try the following (Assume Inter networking between a Desktop and a Laptop, works on any 2 computers)

1. First you need to install (SSH), on "both computers" open a terminal  by going to > Applications > accessories > Terminal and type in  this code:
```
sudo apt-get install ssh
```it will ask you for your password, make sure to enter the correct password.

----Ur on the DESKTOP----
2. Next setup the folder you want to share (On Desktop). I called mine  (Jumpy) and is on the desktop of one of the computers but you can  put it anywhere, like your Home folder.

3. Right click the folder and choose ‘Sharing Options’. Make sure "Share this folder" is checked and has a name. 
Also check "Allow other people to write in this folder" if you want to  be able to modify > add > or remove files from your main computer.

4. You will be prompted to install Samba, just follow the steps. After it is done, you will have to logout and log back in.

5. A Nautilus window will popup asking you if you want to add  permissions, hit "add the permissions automatically". thats it you're  done creating your share folder.

6. Next get the IP address from your Desktop computer that you want to share files with "where you made the share folder"
Right click on the network icon in the top right of the screen and click on "connection information"

7. Make sure to write the "IP Address" down you will need it.

8. Now you can connect the two computers to share the folder. Switch to the Laptop(or whatever) now

----LAPTOP PART BEGINS NOW-----
Go to > Places > Connect to Server 

9. i.  Service type: Choose SSH
  ii.  IP address of the Desktop computer in the "Server" field
 iii.  Enter 22 in the "Port" field
  iv.  In the "Folder" field, enter the path of the folder you   created i.e /home/username/Desktop/Foldername
   v.  Under "User Name" enter the username of the second computer.
  vi.  You could make a "Bookmark" of your share, just click the  checkbox next to Bookmark and name it may be 'SSH tunnel to Desktop'

10. Click Connect. It'll ask for the login password for the Desktop, enter it to connect. UR DONE :popcorn:

12. Repeat Steps 2 through 11 on Ur laptop too. Now U can SSH to the Desktop computer.

13. If u just enter the IP address of the other computer and say connect  u can see the whole of the other computer. Including all the drives  (NTFS) u've mounted. (I'm assuming that u are dual booting)

See all the screen-shots to understand better :smile:

---

### Post by haqking on 2011-10-12
> **anur.bhargav said:**
> I think this is the GUI method...
Try the following (Assume Inter networking between a Desktop and a Laptop, works on any 2 computers)

1. First you need to install (SSH), on "both computers" open a terminal  by going to > Applications > accessories > Terminal and type in  this code:
```
sudo apt-get install ssh
```it will ask you for your password, make sure to enter the correct password.

----Ur on the DESKTOP----
2. Next setup the folder you want to share (On Desktop). I called mine  (Jumpy) and is on the desktop of one of the computers but you can  put it anywhere, like your Home folder.

3. Right click the folder and choose &#8216;Sharing Options&#8217;. Make sure "Share this folder" is checked and has a name. 
Also check "Allow other people to write in this folder" if you want to  be able to modify > add > or remove files from your main computer.

4. You will be prompted to install Samba, just follow the steps. After it is done, you will have to logout and log back in.

5. A Nautilus window will popup asking you if you want to add  permissions, hit "add the permissions automatically". thats it you're  done creating your share folder.

6. Next get the IP address from your Desktop computer that you want to share files with "where you made the share folder"
Right click on the network icon in the top right of the screen and click on "connection information"

7. Make sure to write the "IP Address" down you will need it.

8. Now you can connect the two computers to share the folder. Switch to the Laptop(or whatever) now

----LAPTOP PART BEGINS NOW-----
Go to > Places > Connect to Server 

9. i.  Service type: Choose SSH
  ii.  IP address of the Desktop computer in the "Server" field
 iii.  Enter 22 in the "Port" field
  iv.  In the "Folder" field, enter the path of the folder you   created i.e /home/username/Desktop/Foldername
   v.  Under "User Name" enter the username of the second computer.
  vi.  You could make a "Bookmark" of your share, just click the  checkbox next to Bookmark and name it may be 'SSH tunnel to Desktop'

10. Click Connect. It'll ask for the login password for the Desktop, enter it to connect. UR DONE :popcorn:

12. Repeat Steps 2 through 11 on Ur laptop too. Now U can SSH to the Desktop computer.

13. If u just enter the IP address of the other computer and say connect  u can see the whole of the other computer. Including all the drives  (NTFS) u've mounted. (I'm assuming that u are dual booting)

See all the screen-shots to understand better :smile:

thread OP was answered and they achieved the goal, and this only applies if using a GUI.

why do you assume they are dual booting ?

and you dont need to setup samba to simply ssh which is what the OP asked for.

---

### Post by anur.bhargav on 2011-10-18
> **haqking said:**
> thread OP was answered and they achieved the goal, and this only applies if using a GUI.

why do you assume they are dual booting ?

and you dont need to setup samba to simply ssh which is what the OP asked for.

Done :) I completely understand it now ... I'm learning by the minute... I Agree that assumptions are wrong.. I didn't chose my words wisely ;)

---

### Post by haqking on 2011-10-18
> **anur.bhargav said:**
> Done :) I completely understand it now ... I'm learning by the minute... I Agree that assumptions are wrong.. I didn't chose my words wisely ;)

no worries ;-)

peace

---

