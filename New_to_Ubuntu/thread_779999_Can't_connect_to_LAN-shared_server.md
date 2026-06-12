---
title: "Can't connect to LAN-shared server"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by Thorun on 2008-05-03
Hi. 

I thought I did remember, that when i set up Gutsy the last time, my network worked as a charm. But i was wrong. Now i can't seem to get anything to work with my LAN. 

SETUP:
I have a lokal WinXP-pro server running with a shared drive (Through LAN). I can access this shared drive from any other of my computers (windows though) and I think, I have set the permissions on the server-share up right. 

When I use the LiveCD both with Gutsy and Hardy, i can access the LAN, see the other computers on the LAN and i can even get access to the shared partition on my XP-server. 
Normally i have not given permission just to access the partition without entering a user/pass, but when using the LiveCD's I can access the shared server partition without any user/pass. (Which i think is wery odd!)

My ubuntu's name is linx1 and my users name is linxa (at my terminal it says: linxa@linx1: )
On my Windows XP server i have given permission to both linxa and linx1 with the same password. 



BUT my problem is now:
When I have installed gutsy or hardy, i can access the network too. I can see the other computers at the network and i can even see the shared server-partition. When clicking on the folder that is shared, i can even get access to see the sub-folders. But when clikcing on the sub-folders the problem arrives. 
I can't get access to the sub-folders. and
I can't get a prompt to type in user/pass to get access to the shared server-partition.


I'm really confused. 
Why can i access it from the LiveCD without typing a user/pass?
Why can't i access it from the installed ubuntu?
Why don't i get a prompt for typing in my user/pass?
Why can i see the shared sub-folders, but not have access to them?


I really hope, that someone out there can pinpoint my problem. 


-Rune

---

### Post by drsox1899 on 2008-05-03
Try this guide for connecting to Windows shares.  Works fine in 7.10, but I haven't tried it from the live CD.  Probably doesn't work unless you install.

[http://ubuntuforums.org/showthread.php?t=202605&highlight=Setup+Samba+peer-to-peer+Windows](http://ubuntuforums.org/showthread.php?t=202605&highlight=Setup+Samba+peer-to-peer+Windows)

Luck

---

### Post by Thorun on 2008-05-03
Hi again. 

I have tried the wery well written guide and have followed some links at the bottom. But still no success. 
I'm able to watch the windows-domain-name: thonbogade
I'm able to watch all the computers at the smb-network at thonbogade
I'm able to click at all the computers without being prompted for either username or password. 
I'm able to see, what folders there is on the XP-server. 
I'm NOT able to enter the folders. I'm just being denied. 

What I think should happen:
When clicking at the server-computer "zxcv" I should be prompted for user/pass to login the server. And after typing user/pass there should be access to all sub-folders. But that not what's happens. 

Is the error in my XP-server maybe?
I have set user-accounts up for my other XP and Vista-boxes and they are being prompted for user/pass to login. But not my Ubuntu 7.10

In the XP-server i have to add the username (the name of the computer) that want to be connected. I can find it in any windows-boxes by typing: echo %username% in a prompt. How do i know what the Ubuntu's username is?

Is it the first or the last or none? when the terminal says:
linxa@linx1:~$

---

### Post by halitech on 2008-05-03
the username is the first one (linxa) and the computers name is the second (linx1)

---

### Post by Thorun on 2008-05-03
```
linxa@linx1:/etc/samba$ smbclient //zxcv/Film -U linx1
Password: 
Domain=[ZXCV] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]
smb: \> ls -la
NT_STATUS_ACCESS_DENIED listing \-la

                44712 blocks of size 16777216. 2051 blocks available
smb: \> read_data: read failure for 4. Error = Connection reset by peer
Read from server failed, maybe it closed the connection
Read from server failed, maybe it closed the connection

```



```
linxa@linx1:/etc/samba$ smbclient //zxcv/Mp3 -U linx1
Password: 
Domain=[ZXCV] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]
tree connect failed: NT_STATUS_BAD_NETWORK_NAME
linxa@linx1:/etc/samba$ smbclient //zxcv/Mp3 -U linxa
Password: 
Domain=[ZXCV] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]
tree connect failed: NT_STATUS_BAD_NETWORK_NAME
linxa@linx1:/etc/samba$ smbclient //zxcv/Mp3 -U linx1
Password: 
Domain=[ZXCV] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]
tree connect failed: NT_STATUS_BAD_NETWORK_NAME
linxa@linx1:/etc/samba$ 

```

I just don't know where the problem is located?!




EDIT:

I have now added a user in my WinXP server called linx1 with password ****. I have added this user to have access to the c:/
I have added this user to have all rights to the c:/ drive in windows. 

Now i turn to my ubuntu 7.10 and the terminal where i type

```

linxa@linx1:~$ smbclient //zxcv/c linx1 
password: ****
```

which results in:
```
Domain=[ZXCV] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]
smb: \> ls -l
NT_STATUS_ACCESS_DENIED listing \-l

                40162 blocks of size 131072. 9735 blocks available
smb: \>
```

Am i on the right track? Is there some rights i have to change somewhere to get 100% control (rwx) of the c:/ ?

---

