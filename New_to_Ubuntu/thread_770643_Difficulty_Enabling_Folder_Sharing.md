---
title: "Difficulty Enabling Folder Sharing"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by JediYodaNT on 2008-04-27
Hello Linux World.
So, I'm pretty new to the Ubuntu scene.  I've wanted to get my feet wet for a while, but I've been kept away due to my World Of Warcraft addiction and the lack of gaming support, which is finally beginning to change. (Presently installing patch after patch with Cedega).  The only other element that is concerning me is File Sharing.  I've been looking at a lot of different guides that make it look so easy, however Heron has apparently changed the way file sharing used to be handled.  When I try to share my Media folder on my External USB Drive (Which was originally filled up while connected to a WinXP machine) I get error after error. See below:
[IMG]http://img110.mytextgraphics.com/photolava/2008/04/27/screenshot1-4abho6whm.png[/IMG]
[IMG]http://img702.mytextgraphics.com/photolava/2008/04/27/screenshot2-4abhoy08v.png[/IMG]

What steps am I missing in this process?  I've even tried using the **SUDO Nautilus** command to no avail.  Any help would be greatly appreciated.

---

### Post by lamalex on 2008-04-27
I'm assuming you had clicked the set permissions button on the dialogue box? Could you do an ls -la on Media and post the output?

---

### Post by CornishJoel on 2008-04-27
Have you tried logging out and in again?  

When I tried file sharing I got permission errors despite the group **sambashares** having write permissions on the **/var/lib/samba/usershar**es directory, and according to the **/etc/group** file I was in **sambashares** group.  

Once I logged out and out again I could share the file OK.

Caching of some sort...

---

### Post by JediYodaNT on 2008-04-27
I hate to sound like suck a noob, but what is the command line structure for switching your current directory to a mounted drive so that I can try the **ls** command you had requested?

---

### Post by bodhi.zazen on 2008-04-27
When you share a directory you must have access to it as a user.

I am assuming that the USB hard drive is NTFS, in which case automatic setting of permissions will fail.

You set the permissions of a NTFS partition at the time of mounting and you will need to re-mount to change permissions.

Mounting and permissions depends on the file system:

_Windows:_ [Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)
For read-write: 
[list=number]
[*]vfat (FAT) use umask=000
[*]ntfs use [ntfs-3g](http://ubuntuforums.org/showthread.php?t=217009) and a fstab entry something like this:
```
/dev/hda1  /media/windows  ntfs-3g  defaults  0  0
```
[*]An alternate is ntfs-config. ntfs-config uses ntfs-3g to mount windows partitions via a gui :)
[indent][http://ubuntuforums.org/showthread.php?t=337970](http://ubuntuforums.org/showthread.php?t=337970)[/indent]
[/list]

---

### Post by lamalex on 2008-04-27
I would try logging out and back in first, but when you're back in open up a terminal and do ls -la /media/My\ Book/Media

---

### Post by JediYodaNT on 2008-04-27
Actually, I have just attempted to use the permissions GUI option on the Media folder in question.  When making any changes, the setting snap right back to the original settings.  

See the attached screenshot.

---

### Post by bodhi.zazen on 2008-04-27
Assuming it is a ntfs partition ...

look .... up .... at my first post ^^

---

### Post by JediYodaNT on 2008-04-27
Ok, so I determined that it was FAT and not NTFS, so I used the **umask** command you suggested.  I can now see that the permissions have all been enabled, however I'm still hitting a brick wall when trying to enable sharing.

'net usershare' returned error 255: net usershare add: failed to add share media. Error was Operation not permitted

What steps should I take next?

---

### Post by JediYodaNT on 2008-04-27
also, if this helps...

nathan@Aspire:~$ ls -la /media/My\ Book/Media
total 128
drwxrwxrwx  4 root root 32768 2008-04-27 11:55 .
drwxrwxrwx 10 root root 32768 1969-12-31 19:00 ..
drwxrwxrwx  3 root root 32768 2008-04-27 11:55 Music
drwxrwxrwx  6 root root 32768 2008-04-14 21:00 Video
nathan@Aspire:~$

---

### Post by bodhi.zazen on 2008-04-27
re-mount the device

mount -t vfat /dev/xxx /media/yyy -o uid=1000,gid=100,umask=000

/dev/xxx = partition
/media/yyy = mount point

---

### Post by O||y on 2008-04-27
Hiya

I have been having exactly the same problem, but I am a total noob.  I managed somehow to work out for myself the way to easily enable filesharing for you.

open terminal and type
```
sudo su
```

then type
```
gksudo gedit
```

now navigate to this file: /etc/samba/smb.conf and open it.

This has opened the file as root, enabling you to edit it.

scroll down to the secftion that looks like this:

```
#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast
**[COLOR="Red"]usershare owner only = False[/COLOR]**

#### Networking ####
```

You now need to add the line that  I have highlighted in red with no hashes or spaces in front, on its own line.

Now save the file and close it.

Now navigate to the folder you want to share, right click it, and select **sharing options** click enable sharing.  Edit the **Share Name** box if you wish then press Create Share.

It should now have let you share the folder :D



I hope this is of use, and anyone feel free to correct me, but it worked for me ;)

---

### Post by bodhi.zazen on 2008-04-27
O||y : While that "works" and there is noting "wrong" with that solution, it is a work arround for the underlying problem and is not strictly necessary.

Permissions on linux may be a very new concept if you are migrating from windows.

[http://howtoforge.com/linux_file_permissions](http://howtoforge.com/linux_file_permissions)

Now to share a file you have to have the proper permissions, as either owner or group, on the server. Your solution works because you configured samba to allow anyone network share any file / directory. This is a very minor security risk, almost negligible.

I suggest you look at permissions and how to set them with windows (FAT, NTFS) and linux file systems. The link I usually give is this (on fstab) :

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

That link may feel intimidating, but take it slow in needed.

So what I am saying, fix the permissions fix the problem. No need to config samba, although hats off to you for reading the config file. Most Linux servers are configured by editing test files ...

---

### Post by gkestrel on 2008-04-27
I had a similar problem and kept getting the net usershare' returned error 255 message, after further research i found it was down to nautilus share being install but not configured. The following instructions came from the website shown in synaptics under the nautilus share program. I simply copied and pasted each command into a terminal as root, you also have to log out then log in again to complete the configuration. After that you should have no problem enabling your shares.

Setup and configuration 
    * A quick and easy way to have it running (must be done as root): 

export USERSHARES_DIR="/var/lib/samba/usershare"
export USERSHARES_GROUP="samba"

mkdir -p ${USERSHARES_DIR}
groupadd ${USERSHARES_GROUP}
chown root:${USERSHARES_GROUP} ${USERSHARES_DIR}
chmod 01770 ${USERSHARES_DIR}

    * use the following /etc/samba/smb.conf: 

;/etc/samba/smb.conf

[global]
workgroup =  WORKGROUP ; you can change to your own workgroup
security = share

usershare path = /var/lib/samba/usershare
usershare max shares = 100
usershare allow guests = yes
usershare owner only = yes

    * Add the samba group to your user (replace your_username by your login): 

usermod -a -G ${USERSHARES_GROUP} your_username

    * Logout and login

---

