---
title: "Can't mount a network drive"
date: 2012-02-08
forum: New to Ubuntu
---

### Post by Chris_Nickel on 2012-02-08
Hello,
I've been trying to mount a network drive and I always get error 13 access denied.
 
This is what I have been trying.
 
1. downloaded and installed smbfs
2. sudo mkdir /media/public
3. gksudo gedit /etc/fstab
4. At the end of the file I typed:
 
# Mount a network drive
//172.16.23.23/share /media/public smbfs guest 0 0
 
Then I saved the file.
5. sudo mount -a
 
I am running Ubuntu 11.04
 
Does anyone have any ideas?
 
Thanks
 
-Chris

---

### Post by lechien73 on 2012-02-08
Is "guest" the username? If so, you need to supply "username=guest", rather than just "guest". Is there a password on the guest account?

---

### Post by cbanakis on 2012-02-08
I did quite a bit of research to accomplish the same thing.

Assuming it is a windows share your trying to access...

This is the line I added to my fstab to mount a windows share that was NOT password protected.

```

192.168.1.5/Fn-Terabytes /home/chris/Fn-Terabytes/ smbfs guest,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```If there is a password, your fstab should look like this...

```

192.168.1.5/Fn-Terabytes /home/chris/Fn-Terabytes/ smbfs uid=chris,credentials=/etc/smbfspw
```Then you would need to create the credentials file that your fstab is now pointed at.

```
sudo gedit /etc/smbfspw
```And that file should look like this...
```
username=chris
password=password
```

Also, if you did not already do it...
```
sudo apt-get install smbfs
```
to add support for windows shares.

---

### Post by Chris_Nickel on 2012-02-08
Actually, I'm trying to connect to a network server that is attached to anothe Ubuntu box.
I created a .txt file with the login and passwords for the drive.
Then I changed the last line of the fstab to:
//172.16.23.23/share /media/public smbfs uid=chris, credentials=/home/chris/Documents/pswdcredentials.txt
 
I'm still getting the error 13.
 
I guess I can check the login and password in the file, but I'm pretty sure there correct.
 
-Chris

---

### Post by cbanakis on 2012-02-09
Maybe your credentials file should not have an extension? ("pswdcredentials" instead of "pswdcredentials.txt")

Mine do not have an extension, and all is well over here.

Or, maybe your fstab says ".txt" but the actual file does not?


Also, you may want to try cifs instead of smbfs.
```
//172.16.23.23/share /media/public cifs uid=chris, credentials=/home/chris/Documents/pswdcredentials.txt
```

---

### Post by Cheesemill on 2012-02-09
You say you are trying to connect to a share on a Ubuntu system.
How is the file-sharing set up on this machine? Is it with Samba, NFS, SSH etc....

The method you are trying will only work if the file server is set up using Samba.

---

### Post by Chris_Nickel on 2012-02-09
Hmmm,
I'll have to look into that. The share was set up before I started here.
-Chrus

---

### Post by Chris_Nickel on 2012-02-09
OK,
Just checked with the boss.
According to him the drive I'm trying to connect to is a SAMBA drive.
-Chris

---

### Post by Chris_Nickel on 2012-02-09
I just found a tutorial on the net and tried it.
First I created the .smbcredentials file on the root.
Next I edited the fstab with:
//UBUNTU/share /media/teamshare cifs credendentials=/roote says/.smbcredentials,iocharset=utf8,file_mode0777,dir_mode=0777 0 0

The drive now mounts, but I can't get into it, the message says I do not have the necessary permissions to view the drive.
I checked my .smbcredentials file and the login and password are correct.

Thoughts or suggestions?  

Thanks
-Chris

---

### Post by cbanakis on 2012-02-09
Your sure the smb credentials file is in the proper format?

```
username=chris 
password=password
```
The only other thing I can think of, is that it may be a permissions issue on the server.

Maybe the user name and password are correct, but that user has no authority on the server?

---

### Post by cbanakis on 2012-02-09
Oh, actually...

Just noticed you have cifs in your fstab entry

```
//UBUNTU/share /media/teamshare cifs credendentials=/roote says/.smbcredentials,iocharset=utf8,file_mode0777,dir_m  ode=0777 0 0
```

Now that we know its a samba share, try
```
//UBUNTU/share /media/teamshare smbfs credendentials=/roote says/.smbcredentials,iocharset=utf8,file_mode0777,dir_m  ode=0777 0 0
```
Again

---

### Post by Chris_Nickel on 2012-02-09
Still can't view the drive. 
I'll check on the permissions and see where that leads me.

Thanks
-Chris

---

### Post by Chris_Nickel on 2012-02-10
Hi,
OK, I have permissions to view the drive, at least I can from my Windows boot, just not from the Ubuntu boot.
Now this is an external drive hooked up to another machine on our network (not sure if I made that cleare before). 
Could this be part of the problem?
 
-Chris

---

### Post by bab1 on 2012-02-10
> **Chris_Nickel said:**
> Hi,
OK, I have permissions to view the drive, at least I can from my Windows boot, just not from the Ubuntu boot.
Now this is an external drive hooked up to another machine on our network (not sure if I made that cleare before). 
Could this be part of the problem?
 
-Chris

You don't state what version of Ubuntu you are using.  The ***package*** "smbfs" has been deprecated in favor of cifs-utils on later Ubuntu releases.  The actual protocol is **[COLOR="Red"]cifs[/COLOR]** when using the incantation //server/share /mountpoint cifs blah blah.

If you are mounting this share directly (not via browsing) then be aware that this is probably a FAT file system that does not natively understand Linux file permissions.

I don't mount shares via fstab any more.  I browse and let Nautilus take care of the "backend" stuff.  The share will be mounted at ~/.gvfs

---

### Post by ianp5a on 2012-02-12
If you don't mount them with fstab, how is it possible to access them through applications when choosing a folder?

Some spplications, like deja dup, allow you to type in the share information when choosing a path, but they do not let you browse them. Conduit works well as it lets you browse the local network. But I think the rest, like Grsync, browse the local machine only. Which is a showstopper.

---

### Post by bab1 on 2012-02-12
> **ianp5a said:**
> If you don't mount them with fstab, how is it possible to access them through applications when choosing a folder?

Some spplications, like deja dup, allow you to type in the share information when choosing a path, but they do not let you browse them. Conduit works well as it lets you browse the local network. But I think the rest, like Grsync, browse the local machine only. Which is a showstopper.

Both fstab and Nautilus mount the share to the local file system. As I said before the Nautilus mount point is```
 /home/user_name/.gvfs/share_name
```In other words, the folder is .gvfs in your home directory.  If you are only using the GUI you need to hit CNTL-h first to see it.  

You may be right in that not all applications will work using a share mounted by Nautilus, but you won't know until you try

I use rsync myself.  It is aware of the /home/user_name/.gvfs for sure.  I have to exclude it won't backup all my mounted samba shares.  I backup the Samba server (using rsync) separately also.

---

### Post by ianp5a on 2012-02-13
my .gvfs folder is empty even if Nautilus has mounted a LAN device.

And most apps only browse the local machine. For Absolute beginners this is a showstopper.

---

### Post by HiImTye on 2012-02-13
you can have nautilus mount the share when you log in using
```
nautilus 'smb://<computername>/<share name>'
```
and then the share will be in
```
~/.gvfs/<share name> on <computername>'
```
for referencing it

the only down side is that a nautilus window will open when you mount the share

---

### Post by Chris_Nickel on 2012-02-13
> **bab1 said:**
> You don't state what version of Ubuntu you are using. The ***package*** "smbfs" has been deprecated in favor of cifs-utils on later Ubuntu releases. The actual protocol is **[COLOR=red]cifs[/COLOR]** when using the incantation //server/share /mountpoint cifs blah blah.
 
If you are mounting this share directly (not via browsing) then be aware that this is probably a FAT file system that does not natively understand Linux file permissions.
 
I don't mount shares via fstab any more. I browse and let Nautilus take care of the "backend" stuff. The share will be mounted at ~/.gvfs
 
I am currently using Ubuntu 11.04 64 bit, the 11.10 won't install correctly for me on the test machine, and once we get the problem figured out on here, we ae going to move into a production machine running 11.10 64 bit.
 
-Chris

---

### Post by bab1 on 2012-02-13
> **Chris_Nickel said:**
> I am currently using Ubuntu 11.04 64 bit, the 11.10 won't install correctly for me on the test machine, and once we get the problem figured out on here, we ae going to move into a production machine running 11.10 64 bit.
 
-Chris

These versions of Ubuntu should use the package *cifs-utils* and you should use the mount type of *cifs * (mount -t cifs) in fstab of via the CLI.  The the package cifs-utils contains the updated cifs routines.

---

### Post by bab1 on 2012-02-13
> **ianp5a said:**
> my .gvfs folder is empty even if Nautilus has mounted a LAN device.

And most apps only browse the local machine. For Absolute beginners this is a showstopper.
All mounts of remote file systems (such as a Windows share) are attached to the local file system.  To mount it is to make it local.

How did you mount this LAN device using Nautilus?  What is this LAN device?

---

### Post by ianp5a on 2012-02-14
I bought a NAS Disk (Western Digital) and attached it to my Router.
It shows up in Nautilus when I click on Network. (Ub 11.04) And permissions are OK. Under properties it says CIFS. The path (CTRL-L) in Nautilus says smb://NAS-Disk. Deja Dup allows me to type that in as destination for backups. But most programs don't.

Ideally I want to right click on it under Network, and choose Mount. And that should be the end of it all. The [instructions here]("https://help.ubuntu.com/community/MountWindowsSharesPermanently"), for example, are just way too complicated for beginners.

---

### Post by bab1 on 2012-02-14
> **ianp5a said:**
> I bought a NAS Disk (Western Digital) and attached it to my Router.
It shows up in Nautilus when I click on Network. (Ub 11.04) And permissions are OK. Under properties it says CIFS. The path (CTRL-L) in Nautilus says smb://NAS-Disk. Deja Dup allows me to type that in as destination for backups. But most programs don't.

> Typically the mount point using this method is at /home/$USER/.gvfs.  But you can't mount a partition by itself.  You mount the share on a partition (i.e. //NAS-Disk/share.  The //NAS-Disk is not a CIFS endpoint.

Ideally I want to right click on it under Network, and choose Mount. And that should be the end of it all. The [instructions here]("https://help.ubuntu.com/community/MountWindowsSharesPermanently"), for example, are just way too complicated for beginners.

Do you have various shares defined on the //NAS-Disk? 

From the terminal post the output of ```
smbtree
```
Did you login to the NAS or just hit enter to get the results?

---

### Post by ianp5a on 2012-02-14
No login is required. Just click on the icon in Nautilus and see the contents.
The disk has several folders on it accessible to everyone on the LAN.

I see this problem has been requested on a [Launchpad blueprint]("https://blueprints.launchpad.net/ubuntu/+spec/mounting-network-drives"). But that was from 4 years ago. What is going on?

---

### Post by bab1 on 2012-02-14
> **ianp5a said:**
> No login is required. Just click on the icon in Nautilus and see the contents.
The disk has several folders on it accessible to everyone on the LAN.

And the output of smbtree is?> 

I see this problem has been requested on a [Launchpad blueprint]("https://blueprints.launchpad.net/ubuntu/+spec/mounting-network-drives"). But that was from 4 years ago. What is going on?

It's relatively easy for Microsoft to control the environment.  Ubuntu (Linux in general) has many developers and their respective viewpoints.  These folks don't necessarily talk to each other.

The trade off is that *you* have the freedom to develop a solution and add to the general user experience.

---

### Post by ianp5a on 2012-02-15
> **bab1 said:**
> 
The trade off is that *you* have the freedom to develop a solution and add to the general user experience.

That is no use at all if you are not a computer programmer. "Absolute Beginners" (this forum) can tell most developments are designed for the needs of experienced computer techies. It is good that things are now moving slowly away from this. But networking is still lagging behind.

I'll look at smbtree when I finally get home. But what is the alternative to using the command line for that?

---

### Post by Morbius1 on 2012-02-15
> **ianp5a said:**
> I bought a NAS Disk (Western Digital) and attached it to my Router.
It shows up in Nautilus when I click on Network. (Ub 11.04) And permissions are OK. Under properties it says CIFS. The path (CTRL-L) in Nautilus says smb://NAS-Disk. 
So you can access the NAS through Nautilus and do whatever you want to those shares. 
> Deja Dup allows me to type that in as destination for backups. But most programs don't.bab1 has repeatedly answered that part of the question in this thread. The mount point is at:
> /home/your-user-name/.gvfs/share-name on server-nameIt's in a hidden directory so you will have to enable "Show hidden files" in your application - or any application like gedit because doing it once on one application enables it for all.
> Ideally I want to right click on it under Network, and choose Mount. And that should be the end of it all. The [instructions here]("https://help.ubuntu.com/community/MountWindowsSharesPermanently"), for example, are just way too complicated for beginners.
The way it's been implemented it's even easier - click on the share and it's mounted.
> I see this problem has been requested on a [Launchpad blueprint]("https://blueprints.launchpad.net/ubuntu/+spec/mounting-network-drives"). But that was from 4 years ago. What is going on?     
It was implemented years ago. When you click on a remote share in Nautilus the system runs the following command:
```
gvfs-mount smb://server/share
```It autoumatically mounts the partition, allows you to proivide credentials if required, and even allows you to save those credentials "forever" if you so desire. All in all it's very "Windows-like".

---

### Post by ianp5a on 2012-02-15
Thanks, but none of that seems to happen. Which is why I'm asking. I'll check another installation.

---

### Post by Morbius1 on 2012-02-15
If you have created shares on your own Ubuntu machine you can see if gvfs itself is broken by trying to access it's share from Nautilus. Or just run the following command:
```
nautilus smb://ip-address-of-your-own-Ubuntu-machine
```

---

### Post by ianp5a on 2012-02-15
Ok I'm trying out 12.04 in a virtual machine fresh install. And things have improved slightly over my other install 11.04
The Network device appears successfully in the .gvfs folder as described above.
Which means I can access it via the side-pane entry in Libre office. But it does not appear in the side pane of other programs such as Firefox, Deja Dup or Grsync where you still cant access it. 

At least now we can see the direction they are going. But what are we supposed to do until all the apps can access it? Mess with the tricky fstab still?

---

### Post by Morbius1 on 2012-02-15
> But it does not appear in the side pane of other programs such as Firefox, Deja Dup or Grsync where you still cant access it. Once you connect to the remote share:

In Nautilus open up the .gvfs folder then do a Bookmarks > Add Bookmark. It will now show up in the side panel as ".gvfs". In Firefox when you do an "Open File" you should see that bookmark.

---

### Post by ianp5a on 2012-02-16
Thanks. Good tip. 

If I want to request an improvement, does this mean that each application developer has to change it in their individual app? Or is there something that Ubuntu can do?

---

### Post by bab1 on 2012-02-16
> **ianp5a said:**
> Thanks. Good tip. 

If I want to request an improvement, does this mean that each application developer has to change it in their individual app? Or is there something that Ubuntu can do?

Bear in mind that the developer(s) prioritize things and a request that you might see as important may not be so in their opinion.

The request would be to the developer(s) of the individual application itself if the change is core to that application.  If the change is to the configuration only of the application then the request is to the package maintainer of that application.  Most of the time these individuals are unpaid volunteers, so change can be really slow on some applications. 

Ubuntu itself just *aggregates *most applications into the distro.  In some instances Ubuntu has employees that contribute to the source code of individual applications.  Simple, eh.  

I have no problems with sharing files across my Windows/Linux network as it is configured now.  The best thing you can do is understand Samba completely before you make any requests.

FYI -- You might try  a sym-link from the hidden file (.gvfs) in your home directory.

---

### Post by ianp5a on 2012-04-30
I've just done a fresh install of the released 12.04. And no entry appears under the .gvfs folder when Nautilus is browsing the Network server.

Background: 
Select Browse Network-> Windows share in Nautilus: "Error "Unable To mount share. Failed to retrieve share list from server"

So I go File -> "Connect to server" -> Windows share, enter IP address and it connects OK. All folders available in Nautilus. But still no entry in the /home/me/.gvfs folder. (show Hidden Files)

Now I wondering can this be due to my *router* in some way? 
My flatmate had problems with "Failed to retrieve share list from server" on a boot CD "Try Ubuntu" session too.

---

### Post by Morbius1 on 2012-04-30
That's 2 different issues so lets look at the second one first:
> So I go File -> "Connect to server" -> Windows share, enter IP  address and it connects OK. All folders available in Nautilus. But still  no entry in the /home/me/.gvfs folder. (show Hidden Files)You may be missing a package:
```
sudo apt-get install gvfs-backends
```Then add yourself to the fuse group:
```
sudo gpasswd -a me fuse
```then logoff and logon again.

---

### Post by ianp5a on 2012-04-30
Thanks. Initial question though, why would it not install those things? I used the released iso like probably most people. And I have a separate user data partition. I'd really prefer to do the install again from scratch if I could somehow make sure it installed all those bits. As I have other peoples computers to do afterwards.

---

### Post by ianp5a on 2012-05-02
OK gvfs-backends was already installed. And I did the fuse command, logged out then in again. Still nothing in the .gvfs folder.

---

### Post by Morbius1 on 2012-05-02
So if you were to open up a terminal and run the following command substituting real ip addresses and share names:
```
gvfs-mount smb://192.168.0.100/share-name
```It doesn't mount to .gvfs?

---

### Post by ianp5a on 2012-05-05
On running that command the network server immediatly appears under "Networks" in Nautilus OK. But still nothing appears in the .gvfs folder. (Which is empty)

---

### Post by Morbius1 on 2012-05-05
Run the following command:
```
/usr/lib/gvfs/gvfs-fuse-daemon ~/.gvfs
```
Is it there now?

---

### Post by ianp5a on 2012-05-05
No. that command returned

> fusermount: user has no write access to mountpoint /home/ian/.gvfs

I ran your gpasswd fuse command again before trying again. But still nothing in the folder.

In fact there is a lock symbol on the .gvfs folder in Nautilus. I just changed permissions on the folder and ran your last command. This time no error message. Nothing in the gvfs folder. Even after mounting another network location.

I just ran /usr/lib/gvfs/gvfs-fuse-daemon ~/.gvfs again and got this:
> fuse: mountpoint is not empty
fuse: if you are sure this is safe, use the 'nonempty' mount option

But that could have been because I ran it twice.

---

### Post by Morbius1 on 2012-05-05
Before I spend the rest of the day searching the web for this peculiar problem do you by any change have a gvfs folder at this location:

```
/home/ian/.cache/gvfs
```

---

### Post by ianp5a on 2012-05-05
No. No gvfs or similar there.

I just did a search but found no gvfs under the home folder. 
But there are gvfs folders in:
/usr/lib
/usr/lib/i386-linux-gnu/gvfs
/usr/share/gvfs
/usr/share/doc/gvfs

---

### Post by Morbius1 on 2012-05-05
I did find 2 instances of this phenomenon with 2 different fixes:

The first one is simply to remove 2 packages:
```
sudo apt-get remove gvfs-fuse
sudo apt-get remove gvfs-bin
```Then install them back:
```
sudo apt-get install gvfs-fuse
sudo apt-get install gvfs-bin
```The user then logged off and on again.

The second one is a bit odd and I'm not sure what's going on with it but in a terminal was run the following sequence:
```
dbus-launch bash
gvfs-mount smb://192.168.0.100/share-name
```This one seems a little impractical if you have to do it manually every time but if it works then we can try to figure out why it works.

---

### Post by ianp5a on 2012-05-06
Thanks. Neither made any difference. The second one took about 30 seconds to complete yet did not mount anything.

Wait a moment.... casually checking gvfs again there is a new entry appeared. Not sure when it arrived. I'll go through the scenarios again.

1) Login new. Nothing in gvfs
2) Navigate to a folder on the server with Nautilus. Nothing in gvfs
3) a)dbus-launch bash b)gvfs-mount smb://192.168.. Nothing in gvfs
4) Navigate to a folder on the server with Nautilus. TADA! The top level folder appears in gvfs.

I went through it again and step 3 is always needed before step 4. Otherwise nothing shows up.
After a couple more logout and logins show that step 3 is not needed. Things are appearing in gvfs every time now.
Additionally I can browse to the network without the original error message.

---

### Post by henthorn1 on 2012-05-07
OUR WORKING SOLUTION
 
While this may or may not be the easiest or most stable method to mount drives, it definitely was an easy solution. We found that by going to Places > Connect to a server ... > and entering our windows share information, it mounted the specified information we had wanted. This created a link in Nautilus which when you hovered over it, it gave you an smb link. We took that link and made it into a very simple script:
 
nautilus smb://172.20.0.15/students/$USER
 
The 172.20.0.15 is the server that our student information is stored on. 
The $USER variable tells the script to mount the folder for the specific user that logged on. 
 
Then we created a simple launcher on the desktop that points to the script as well as adding the script to the startup applications. (System > Preferences > Startup Applications) This makes it run the script every time the user logs in.
 
In order to run that script for every user, we had to place the script in the home folder. Since we wanted it to be in everyones home folder so they can run the script when they log in, we had to create a default profile that gets assigned to everyone on their first login. In order to do this, we simply created a user on the machine named edstudent. We configured everything we wanted for the users to have using this profile, then went onto the root account and opened Nautilus, the file manager. We then copied the whole user folder (/home/edstudent/) into the directory /etc/skel/  Now whenever a new user logs in, the folder from /etc/skel/ gets copied to the new users home folder.
 
We would appreciate any comments on our solution or if anyone knows of an easier way of doing this. At this date we are no longer having problems with rights and access to the home folders.
 
This was the solution we created for 10.04 instead of 11.10 - because we were having the same problem you were having and thought it would be easier in 10.04. However after experiencing the same problems in 10.04 and workling through them I believe this solution will work in 11.10 as well. Let me know :-)

---

