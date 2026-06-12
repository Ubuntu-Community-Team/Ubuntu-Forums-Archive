---
title: "using terminal commands on network?"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by garyed on 2008-08-23
I've got 3 computers connected to a router all dual booting Windows & Ubuntu.
I haven't got into samba yet so I only use whichever computer Linux is running on to manage files on another running Windows. If I click on places/network/... I can manage files between computers(except I can only view my home directory between the Linux ones & Windows I have full access.)
What I'm trying to do is use the terminal to view & copy files from one computer to the other.
Can any one point me in the right direction?

---

### Post by SukruH on 2008-08-23
I'm new into Ubuntu, but I think you can use ssh. It's like:

ssh -l <username> <adress of the remote computer>

---

### Post by loboc on 2008-08-23
mount -t smbfs pc:/shre /media/somefolder

cp /media/somefolder/somefile /home/you/

---

### Post by loboc on 2008-08-23
mount -t smbfs pc:/share /media/somefolder

cp /media/somefolder/somefile /home/you/

---

### Post by txcrackers on 2008-08-23
From the Linux machine, you'll need to use *smbclient*, which works pretty durn well. It'll function kinda like an FTP client if you use it interactively.

---

### Post by tuxulin on 2008-08-23
> What I'm trying to do is use the terminal to view & copy files from one computer to the other.
for bunty machines do a little read on these two commands
RSYNC or SCP
 
if you think its too fiddly to manage multiple files at various location
from CLI then try
have a read here 1st [http://www.opbyte.it/grsync/](http://www.opbyte.it/grsync/)
sudo apt-get install grsync


Tuxulin

---

### Post by sdennie on 2008-08-23
If you are able to manage the files in nautilus, you can probably find all the remote mount points that nautilus knows about in ~/.gvfs.  From there you can treat the samba filesystems as any other filesystem.

---

### Post by garyed on 2008-08-23
Thanks to all for the help.
So far the ssh-client is working a little. 
I can view between computers using ssh but I can't copy between computers.
That's the problem I have now.
If I'm in the terminal viewing one of my computers:
 "me@dell-desktop" viewing files & I want to copy a file to the actual computer I'm physically on which is "me@music-desktop" I'm lost.

I've tried cp [path/to/file me@music-desktop] but it doesn't copy anything. 

AS for loboc's code: 
I don't understand how to fill in the blanks especially "pc:/share" or if i need to install samba.

---

### Post by tangibleorange on 2008-08-23
```
smbclient //*ipaddressofserver/folder*
```

should let you in. then you will need to use the 'get' and 'put' commands to organise your files on the machine. if you're familiar with FTP, the commands are virtually the same so you should feel right at home!

---

### Post by garyed on 2008-08-23
I can get into another computer on the network through the command line.
I can even delete files from it but I can't move files from one to the other.
That's my problem. 
The command line lets me go to any computer but I can't find a command that will copy a file from one to the other like I can through Nautilus.
If I can do it through the GUI it seems like it should be easy to do it though the terminal.

---

### Post by tangibleorange on 2008-08-23
> **garyed said:**
> I can get into another computer on the network through the command line.
I can even delete files from it but I can't move files from one to the other.
That's my problem. 
The command line lets me go to any computer but I can't find a command that will copy a file from one to the other like I can through Nautilus.
If I can do it through the GUI it seems like it should be easy to do it though the terminal.

get into the computer with smbclient. make sure you are in the correct directory by using the 'cd' and 'ls' commands. then when you are in the correct directory, do:

```
get *nameoffile*
```

and it should then copy the file from the machine to the directory from which the command was run (default home directory)

---

### Post by eightmillion on 2008-08-23
I was recently looking for a managable solution to this problem also. What I do is mount most of the remote partitions that I work with on a regular basis:
> sudo mount -t cifs -o uid=1000,gid=1000 //path/to/remote/server /media/smbmountdirectory
You can find out your uid and gid with id -u and id -g respectively. 

If you don't wish to mount, you can use midnight commander. It's a great command line file manager that supports all kinds of remote options such as FTP SMB and NFS.
> sudo apt-get install mc

---

### Post by garyed on 2008-08-23
> **eightmillion said:**
> I was recently looking for a managable solution to this problem also. What I do is mount most of the remote partitions that I work with on a regular basis:

You can find out your uid and gid with id -u and id -g respectively. 

If you don't wish to mount, you can use midnight commander. It's a great command line file manager that supports all kinds of remote options such as FTP SMB and NFS.

I tried that but I keep getting :
"failed, reason given by server : permission denied"
I don't get prompted for a password. 
It acts like there's something I need to do to the other machine.
If I use the ssh command I get prompted for a password & then I get into the other machine but I still can't copy between the two.

---

### Post by eightmillion on 2008-08-23
You might have to add the username and password into the mount command if the other computer has any share security enabled. Like so...

> mount -t cifs -o username=server_user,password=server_password
//192.168.44.100/share_name /path_to/mount_point

---

### Post by garyed on 2008-08-23
Thanks for the ideas but I'm still not getting it.

---

### Post by eightmillion on 2008-08-23
Have you tried midnight commander? I use it regularly on remote systems over ssh.

---

### Post by cariboo on 2008-08-23
You can use sftp in Nautilus to transfer files back and forth. Just click the button on the left beside the location bar and enter something like the following:

```
sftp://<usernmar>@<remote_computer>
```

Jim

---

### Post by garyed on 2008-08-23
I haven't tried midnight commander yet.
The sftp works pretty good in Nautilus.
What I really want to do is eventually write a script for backups so thats why I want to use terminal commands for everything.

---

