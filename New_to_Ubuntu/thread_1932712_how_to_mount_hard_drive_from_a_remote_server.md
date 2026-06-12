---
title: "how to mount hard drive from a remote server"
date: 2012-02-27
forum: New to Ubuntu
---

### Post by 007casper on 2012-02-27
On kde, how do I mount a hard drive from a remote server?

On gnome it is places > connect to server

service type: ssh
server: remote.server.com
port: 22
folder: http

that gives you a ssh connection and mounts the hard drive to the file manager.

how do I go about this on kde?  How secure is it?

I tried file manager dolphin.  

on file manager dolphin
fish://remoteuser@sremoteserver

and that will mount the hard drive from the remote server to the file manager like on gnome.

However, it seems to hick up. I dont know why.  When I login from the terminal I see all the files.  However, from the mounted hard drive on the dolphin file manager it doesnt list any of the files.

At one point, I also got weird artifacts on the remote server.

what is the best way to do this?

---

### Post by Gone fishing on 2012-02-28
When you say remote is this over the internet or over a lan? If it is over a lan have you considered NFS?

---

### Post by 007casper on 2012-02-28
over the net - information superhighway

---

### Post by Gone fishing on 2012-02-28
Have a look at

[http://ubuntuforums.org/showthread.php?t=1173714](http://ubuntuforums.org/showthread.php?t=1173714)

---

### Post by 007casper on 2012-03-05
thank you.

dumb question - how come dolphin hicks up?
on file manager dolphin
fish://remoteuser@sremoteserver

I can see the files, and everything.  But it is slow and buggy.

And how come kde doesnt have the "Connect to Server" option like gnome
[https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)

> Using the GUI

Alternatively you can mount a directory over SSHFS using the Gnome "Connect to Server" tool in the desktop Places menu. In the tool, set the service type to SSH and fill in the boxes as needed. If a password is required when connecting then you will be prompted for it. Unmounting a SSHFS connection is the same as for any other volume. Open the File Browser (Nautilus). In the Places panel on the left click the arrow next to the SSHFS mount you want to disconnect or right-click it and select "Unmount". 

---

### Post by 007casper on 2012-03-05
bump

---

### Post by philipballew on 2012-03-05
Open a shell and type

```
sudo fdisk -l
```
now you see all mounted and unmounted drives. YOu can pick the one you want and then you type in the shell ```
sudo mount /dev/thenameofthedrive
``` For instance if I was wanting to mount /dev/sda, sda would be what I would type as the name of the drive.

If you have a different format then most you can read this as to how to get the thing to mount.

[https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)

---

### Post by philipballew on 2012-03-06
You need to look into ssh.

---

### Post by 007casper on 2012-03-07
yeah, ssh is the way to go, I guess.  Even though, you get midnight commander on shell.  I feel it is easier to move around the files with graphical interface, copy, paste, open, edit, etc.  

In shell you open a file and it is pain the a55 to get to a section of the file.  Copy and moving files are a bit pain too... I think shell is great for hard things, but for simple things a graphical interface is a lot quicker.

---

### Post by aeiah on 2012-03-07
mount with sshfs on the command line. if dolphin still fails once the drive is mounted, you may have to resort to other methods. either ssh directly, rsync things back and forth, or drag and drop with an ftp client on the sftp protocol (which is essentially ssh)

---

