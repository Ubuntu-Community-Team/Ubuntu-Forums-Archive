---
title: "sharing folder with windows computers"
date: 2011-11-05
forum: New to Ubuntu
---

### Post by antobbo on 2011-11-05
Hi there, I have some laptops running windows and I would lke to share my ubuntu laptop (a folder) with them.
I was looking at this [https://help.ubuntu.com/10.04/internet/C/networking-shares.html](https://help.ubuntu.com/10.04/internet/C/networking-shares.html). I managed to get to point 3 only, then when I attempted to install NFS and SMB I get an error message saying "Could not install package. The necessary applications to install the package cannot be found." SO I am a bit stuck now, any idea as to what to do?
Thanks

---

### Post by cogier on 2011-11-05
Are you trying to use UbuntuOne to do this or are the Windows computers on the same network?

You will need UbuntuOne if the computers are not on the same network.

You don't say which "point 3" you got to.
1/. Sharing folders via the Shared Folders application
2/. Sharing folders via Nautilus
3/. Accessing shared folders via Windows

If you can provide a little more detail I am sure we can help.

---

### Post by antobbo on 2011-11-05
Apologies Cogies, I wasn't clear you're right.
I am not using ubuntu one, the computers are on the same network. When I said point 3 i was referring to point 3 under Sharing folders via the Shared Folders application.

---

### Post by Mark Phelps on 2011-11-06
I believe that Ubuntu One is a "cloud" service -- and the link is explaining how to grant access to that to different PCs.

The problem with what you're trying to do is that Windows can't understand Ext4 partitions.  SO, if your /home folder is on such a partition (the default filesystem for Ubuntu 11.x installes), your Windows PCs are not going to be able to use it.

---

### Post by antobbo on 2011-11-06
HI ya,
thanks for that. I see what you mean, but I have done in the the past, althought it was a different version of ubuntu, 8.10 I believe and I managed to share folders between them, so I kind of thought I can do it again. So the error I am getting is it due to the fact that Windows can't understand Ext4 partitions?
The thing is that I haven't done anything in windows yet, all I was doing was on Ubuntu
thanks

---

### Post by Morbius1 on 2011-11-06
[1] As for that Howto you referenced I don't think shares-admin is  functional anymore. If you want to peruse the more classical way of  creating a Samba share I would suggest you use:
```
system-config-samba
```[2] Or you could create a Samba Usershare:

Bring up Nautilus.
Right click a test folder say ... Documents.
Select "Sharing Options"

If you don't have samba installed it will ask you if you want to install it - I think it calls it "Windows Networking"

Select all the boxes after the "Sharing Options" step to create a guest share.

Run the following command to see if you can see your own shares and report back if it gives you any errors:
```
smbtree
```If not then see if your Windows machine can access your share.

The process of creating a Samba Usershare looks a lot like creating a "Simple Share" on WinXP.

---

### Post by antobbo on 2011-11-06
hi thanks for that.
I followed the procedure in your post, option n2. Now, I managed to link one of my windows machines to the ubuntu one pretty easily but when I run the ```
smbtree
```  I don't think I have any error but it shows me just the ubuntu machine details but not the windows one. I believe it is normal
One more thing: now that I connected the windows machine to the ubuntu one (I can now access my ubuntu shared folder from my windows machine) can I somehow access my windows folder from the ubuntu machine? I am referring to sth similar to the "map network drive" in windows, not sure if there is anything like that in ubuntu
thanks

---

### Post by Morbius1 on 2011-11-06
Well, here's the thing. The way you access the Windows machine ( or at least the way you would "browse" to the shares on the Windows machine ) is through "Network" in Nautilus. But that should show you exactly what smbtree would show you.

When you run smbtree you get no errors? All you get is a list of the Ubuntu shares?

Try accessing the Windows machine by ip address:

Open up a terminal and type:
```
nautilus smb://192.168.0.100
```Changing 192.168.0.100 to the ip address of the Windows machine.

---

### Post by antobbo on 2011-11-07
Of course, the damn nautilus! Sorry I didn't know what nautilus was, I am pretty new to linux. It works I can get to my windows computer through nautilus.
thanks a lot

---

