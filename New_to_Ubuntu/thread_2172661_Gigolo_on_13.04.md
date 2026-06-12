---
title: "Gigolo on 13.04"
date: 2013-09-05
forum: New to Ubuntu
---

### Post by kc5hwb on 2013-09-05
So 13.04 has changed some things, like directories, etc.  For gigolo, which I previously used to mount my network shares, it now mounts them to the following location:
/run/user/<username>/gvfs
The problem isn't this location, the problem for me is the name that Gigolo gives the share mount.  The current name of one of my shares is **smb-share:server=192.168.1.14,share=volume_1**
Well ok, I guess, but I can't browse to that directory.  I use a program called Subsonic, which is a media streaming service, and subsonic cannot find the directory at /run/user/<myusername>/gvfs/smb-share:server=192.168.1.14,share=volume_1

So does anyone know how I can overcome this?  Or should I go back to mounting with FSTAB?

---

### Post by cariboo on 2013-09-06
You would probably be better off, if Subsonic needs to access the share, by using fstab to mount the share automgically.

---

### Post by Morbius1 on 2013-09-07
For the record it's not Gigolo that's giving you that mount point. It's the newly redesigned gvfs process that's doing it. Back in the Golden Age everything sort-of kind-of worked so it clearly had to be rewritten. And don't be blaming the Ubuntu developers they aren't responsible for this either.

Once upon a time if you really had to you could do a "Save As" in firefox to the mountpoint in the $HOME/.gvfs folder. If you try it now to /run/user/$USER/gvfs it might work once or twice but then it all of a sudden stalls - stalls so bad that you can't even kill the firefox process.

Although clearly this would be a coincidence and not a coordinated effort but it would be nice if this were all fixed by the next LTS release.

---

### Post by kc5hwb on 2013-09-07
I don't really care who is to blame, if anyone is, or why it change.  I just want to know if it is still possible to use Gigolo to map other applications to a shared mount point in this version of the OS.
If not, I need to edit my FSTAB.  Can someone tell me the correct syntax to mount a windows share in FSTAB for 13.04?

---

### Post by Morbius1 on 2013-09-08
> I just want to know if it is still possible to use Gigolo to map other  applications to a shared mount point in this version of the OS.
[COLOR=#0000cd]To translate that question[/COLOR]: "Is it possible to access the mount point reliably within all applications from a gvfs-mount of a samba share?"
No. It's broken in 13.04.
> Can someone tell me the correct syntax to mount a windows share in FSTAB for 13.04?         
Make sure the following package is installed:
```
sudo apt-get install cifs-utils
```
A general template for a cifs mount looks something like this for a guest share:```

//192.168.0.100/share /media/XXX cifs guest,uid=1000,nounix,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```
For something that requires credentials:```

//192.168.0.100/share /media/XXX cifs  username=user-name,password=secret,uid=1000,nounix,iocharset=utf8,file_mode=0777,dir_mode=0777  0 0
```
Where:

**192.168.0.100** is the ip address of the server - can also use the hostname of the server or if mDNS compliant the hostname.local of the server
**share** is the name of the share on that server
**/media/XXX** is the mountpoint on the client

Once you enter that in fstab run the following command which will test for syntax errors and if there are none mount the remote share:
```
sudo mount -a
```

---

### Post by kc5hwb on 2013-09-15
> **Morbius1 said:**
> [COLOR=#0000cd]To translate that question[/COLOR]: "Is it possible to access the mount point reliably within all applications from a gvfs-mount of a samba share?"
No. It's broken in 13.04.

Is it working in 12.10?
I was previously running 12.04 but I kept getting that error saying "Ubuntu has abn internal error, etc" that was a known bug with that version.  That is why I decided to update.  12.04 was LTS, I wanted to keep it for a while, but was tired of getting errors.

---

### Post by kc5hwb on 2013-09-15
When trying to mount the drives (one is on another Ubuntu box and one is a open NAS share) I get the following errors in Terminal after logging the syntax you typed above in the /etc/fstab file:
```
jape@samson:~$ sudo mount -a
mount: unknown filesystem type 'dir_mode=0777'
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
jape@samson:~$ sudo gedit /etc/fstab

(gedit:3567): IBUS-WARNING **: The owner of /home/jape/.config/ibus/bus is not root!
```

I changed the IPs and the shares to match my network drives... same shares I used in 12.04 with Gigolo.

The syntax on the fstab, as I recall, changes somewhat with each version of Ubuntu, and also requires you to log your pw into the fstab file for shares that aren't fully open.  These are reasons why I liked using Gigolo instead.

---

### Post by Morbius1 on 2013-09-16
> mount: unknown filesystem type 'dir_mode=0777' 
mount error(13): Permission denied
2 different errors with 2 different causes.

The first one looks like you have a mistake in the line you added to fstab - dir_mode is in the wrong place. Why not post the entire contents so we can see what's wrong:
```
cat /etc/fstab
```
The error 13 error is most likely happening because of a change in the default security mode for mount.cifs that has happened since 12.04. Change your line to force it to the old default:
```
//192.168.0.100/share /media/XXX cifs guest,uid=1000,nounix,iocharset=utf8,file_mode=0777,dir_mode=0777,[COLOR=#0000cd]sec=ntlm[/COLOR] 0 0
```

---

### Post by kc5hwb on 2013-09-17
It's 2 different errors because it is 2 different shares I am attempting to mount in the fstab file.  Both errored when I entered the syntax you posted, and changed the IP and paths to match my shares.

I will post the entire thing when I get home tonight.  I can't access the Ubuntu box remotely.  Teamviewer doesn't seem to work on 13.04 and I haven't setup VNC yet.  Honestly, I am thinking about going back to 12.10.  Or maybe I'll wait for 13.10 and hope Gigolo works there.

---

### Post by kc5hwb on 2013-09-22
The sec=ntlm entry in the end of the line that mounts to the open share seems to have fixed the mount issue here.



For the entry into the FSTAB file that mounts to my other Ubuntu box, here is the entry I used:
```
//192.168.1.13/ /home/jape/Shares/josephus cifs  username=jape,password=<mypw>,uid=1000,nounix,iocharset=utf8,file_mode=0777,dir_mode=0777  0 0
```

And here is the error I see after running sudo mount -a
```
jape@samson:~$ sudo mount -a
Retrying with upper case share name
mount error(6): No such device or address
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```


That code in the FSTAB has a "nounix" entry, which I am guessing is wrong.  The mount is going to another Ubuntu box on my network, ext3 file share, and should follow the username and password that I've entered in the line.

---

### Post by Morbius1 on 2013-09-22
You can't mount an entire server ( //192.168.1.13/ ). You can only mount a share on that server - //192.168.1.13/some-share-name.

---

### Post by kc5hwb on 2013-09-22
I tried that also and got the same error.
```

//192.168.1.13/home /home/jape/Shares/josephus cifs  username=jape,password=<mypw>,uid=1000,nounix,iocharset=utf8,file_mode=0777,dir_mode=0777  0 0

```

jape@samson:~$ sudo mount -a
Retrying with upper case share name
mount error(6): No such device or address
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

---

### Post by Morbius1 on 2013-09-23
Is there are share by that name on that server?

Can you access the share by running this command from the terminal:
```
nautilus smb://162.168.1.13/home
```
If you can't then you don't have a share by that name on that server. You can verify that by running the following commands on that server:
```
testparm -s
```
```
net usershare info --long
```

---

