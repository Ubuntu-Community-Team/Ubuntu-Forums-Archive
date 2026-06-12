---
title: "How to mount NFS shares from Ubuntu box onto Windows XP as Client"
date: 2006-11-30
forum: Outdated Tutorials &amp; Tips
---

### Post by Jose Catre-Vandis on 2006-11-30
I gave up on Samba several months ago, and switched to using NFS to share folders over my LAN. But one of my family insists on using Windows XP, so I needed to find a solution to allow them to access the NFS shares. This is neatly done by Microsoft themselves, for "free", using their "Windows Services for Unix" setup. My file server is an Edubuntu Dapper (I use LSTP too) with four NFS shares. Please note that this is a basic, get you up and running howto, there is more configuration required and available, especially for the security conscious, which is beyond the scope of this howto.

First off, you need to understand NFS Server and Client for Ubuntu. I followed this guide, and suggest you do the same.
```
http://www.ubuntuforums.org/showthread.php?t=249889
```

The important part to understand is the syntax for a share
```
yourserver:/data
```

Once you have the nfs server and some shares set up, make a note of the syntax needed to access them from a remote box. You will need these later. You can use a dns name or the IP address.

You may also need the username and password for your server.

QUICK INSTALL OF SFU:

Anyway, fire up your Windows XP box and download the installer for "Windows Services for Unix", currently at version 3.5, from this page:
```
http://www.microsoft.com/technet/interopmigration/unix/sfu/default.mspx
```
This is @ 200mb. You will end up with a file called SFU35SEL_EN.exe.

Double click to unzip this file, it should upzip into your username's Temp folder, something like C:\Documents and Settings\"yourusername"\Local Settings\Temp. Seek out the setup.exe file and double click. Click through the installer process, as much as you might hate to, accept the licence agreement, and the standard installation option, and without changing any other settings until you reach the mapping page.Tick the radio button in the upper part of the window (Remote User Name Mapping Server) and then enter your server name or IP address in the box. Click OK and finish the installation process. Windows may offer you a restart, which you should take up.If it doesn't, do a reboot anyway. The NFS Client should automatically be started on boot up.

ALTERNATE INSTALL OF SFU: - THANKS TO bodhi zazen
(overcomes user name issues)

 Install SFU


Navigate to C:\Documents and Settings\"yourusername"\Local Settings\Temp

Double Click on Sfusetup


    * Select Custom Install
    * We only need to install :
          o NFS -> NFS Client
          o Auth Tools for NFS -> User Name Mapping 
    * Deselect Everything Else 


During the next steps accept all defaults

    * Default to the Machine's Domain
    * Select passwd and group files
    * Select user name mapping 

Reboot Windows


[edit]
Configure SFU


1. From Ubuntu copy /etc/passwd and /etc/groups to C:\

    * You can read these files as Text so you may want to eliminate everything from passwd except the log-in names of your Linux users and everything from groups except users (I did). 

2. Launch SFU

Start -> All Programs -> Windows Services for unix -> Services for Unix Administration

3. In the "Client for NFS (On the Left) set the desired permissions of the sharer (I chose rwx for owner and group, nothing for other)

    * Click Apply 

4. In the "User Name Mapping" (On the Left)

    * Select "Use Password and Groups Files" -> Enter C:\passwd and C:\groups in the appropriate boxes 

5. Maps Tab

    * Select the "Show User Maps" -> Click "Show Windows Users" and "Show Unix Users"
          o Select a Windows user and associate it with the appropriate Linux User (one who can normally mount the NFS Share on a Ubuntu Client)
          o Click the "Add button" 

    * Select the "Show Group Maps" -> Click "Show Windows Groups" and "Show Unix Groups"
          o I mapped Windows Administrators to Linux Users
          o Click the "Add Button" 

6. Back to configuration Tab

Click the "Apply" button on the top left Click the "Synchronize Now" button near the bottom




Once Windows is back up, you can start adding NFS network shares. Do this in just the same way as you would add normal network shares in Windows. From File Explorer, select "Tools" and then "Map Network Drive". In the dialog, type the server/share address in the following format:
```
yourserver:/data
```
using the correct name or IP address for your server, and the correct path to your share. Remember the colon ( : ) !! Tick the Reconnect at Logon so that your shares persist through reboots. Windows firewall (or your own firewall) may block NFS Client on reboot, and should offer you the chance to unblock it.

Now, depending on how you have things set up, you may or may not be asked for a username and password. I wasn't, but this may have been because on the test Windows box I used, I just happened to use the same username and password as I had on the server. Not had a chance to check this out yet. However, click OK on any resultant dialogs that pop up, and head back to Explorer to check out your new nfs network share. (In fact, XP opens up a new window for your share).

OK, this is only supposed to work on server editions of Windows (2000, Server 2003, XP Pro) but there is a hack you can do to make the installer work on XP Home Edition ( I haven't tried it yet) Look here:
```
http://oreilly.com/pub/h/2883
```1

[EDIT] Errors on boot of Windows Box due to Persistent Connections to NFS Server

If I set a network share as a persistent login, I get an error dialog on boot of my windows box. Having used the User Mapping Service, I found I could overcome this error dialog as follows:

Create your network share
Send a shortcut of the share or a sub folder within it to the desktop
Disconnect the share
Reboot (no error dialog! :))
Double click on the shortcut and one of two things will happen:
You will simply get a dialog asking you to confirm your log on details, which if you "OK" will open a folder on the share
or
You will get a dialog asking you to enter login in details

I also selected simple mapping as an option in User Mapping Service, but this requires you to have the same user on the server as on your windows box, I believe.[END OF EDIT]

Finally, there is a control applet to be found in Start>Programs if you want to play with settings. If I come up with anything else, I will update.

**EDIT: I can't personally recommend this effort as a workable/straight forward solution any more, unless you want to tear your hair out. I see nothing wrong in running parallel nfs and samba servers to support Linux and Windows boxes. This is what I have working now for my mixed local network and it doesn't seem to place any real extra load on the server itself.**

---

### Post by mulligan.can on 2006-12-25
Ok, I ser this up myself and it works beautifully except for one thing: windows doesn't like folders like "/shared/photos".

It can access them but you can't create shortcuts or anything to them (which is what I was planning on doing as the windows users aren't technical).

Anyway, I guess I am just going to have to move everything out of /shared on my fileserver and place it in /. Unless someone has a workaround?

---

### Post by Jose Catre-Vandis on 2006-12-27
> **mulligan.can said:**
> Ok, I ser this up myself and it works beautifully except for one thing: windows doesn't like folders like "/shared/photos".

It can access them but you can't create shortcuts or anything to them (which is what I was planning on doing as the windows users aren't technical).

Anyway, I guess I am just going to have to move everything out of /shared on my fileserver and place it in /. Unless someone has a workaround?

Not sure what you mean? Is this folder (sub folder) in your home directory? Where is "shared/photos" on your NFS server that you cannot link to it directly? Why not just set up another NFS folder pointing at this location, or set up the links or mount points on your linux box instead?

[EDIT]
I have just tested this out:

I created the following folders in the home directory of my NFS server:

```
/shared/photos
```

So the full path is now

```
/home/myusername/shared/photos
```

Edit /etc/exports and add the line below to the bottom and then save (myusername is your login name, xx.xx.xx.xx is the IP of your NFS server)

```
/home/myusrename/shared/photos xx.xx.xx.xx/24(rw,no_root_squash, async)
```

then restart the server

```
sudo /etc/init.d/nfs-kernel-server restart
```

and export the file system

```
sudo exportfs -a
```

head back to your Windows client, and in explorer open up a new network share, typing

```
xx.xx.xx.xx:/home/myusername/shared/photos
```

Click Yes in the tick boxes, and reconnect on login so it persists, and you should be presented with your folder :)

---

### Post by mulligan.can on 2006-12-28
Did pretty much exactly that when I tried the first time :S.

Must be something funky with that particular laptop. (My parents and sister use it and they dont know a lotbut know enough to mess things up if you know what I mean :( ).

Anyway, thanks for the help. Guess I'll just have to play around with windows a bit.

Cheers :D

---

### Post by zukakog on 2007-04-14
I've got Vista Ultimate, so I have access to the NFS client and other UNIX services.  It installed great.  I can map drives great.  I can even access files that are 777.  The only problem is that most of my files are 775 or 770.

I'm guessing that Vista is sending the wrong UID (and GID)  to my NFS server.  I had the same problem in XP.  I don't know if I can change my UID and GID, or if my Ubuntu server is supposed to be a Name Mapping Server somehow.

> **Jose Catre-Vandis said:**
> Tick the radio button in the upper part of the window (Remote User Name Mapping Server) and then enter your server name or IP address in the box.

I'm guessing that this Name Server is supposed to say, "Hey, for any user with the name Zukakog, use UID 1000 and GID 1000."

How can I check if my Ubuntu server is mapping names correctly?

---

### Post by Erlander on 2007-04-21
> 
```
http://hacks.oreilly.com/pub/h/2883
```
I'm having trouble finding this hack.  Can you help me more in finding it.

Would like to use NFS rather than Samba to network my Ubuntu pc with my dual boot Ubuntu/XP Home so this is important to me.

Having just done a clean install of Feisty this seems a good time.

Thank you.

Rob

---

### Post by Erlander on 2007-04-21
Never mind.  Google found it.

Rob

---

### Post by bodhi.zazen on 2007-05-29
I was excited to see this how-to when you posted it. I did not try it as I do not use Windows.

I recently started using Windows XP Pro in VirtualBox, and must say it has been fun to play with windows networking.

So ...

I tried the how-to and it kind of works, but it is very strange.

The Windows install recognizes the nfs server (which is up an runing on both the server and client side but iwth LInux clients), but I get a "permission denied" error from windows.

This is also a strange program because it is asking for a user name and password to connect to the nfs. I have tried connecting with root and several users, no joy ...

So I see you have posted a link "http://hacks.oreilly.com/pub/h/2883"

Well, that link is no longer working.

I see Erlander found it, but my google is broken and he did not post the link he found ...

OK, so no real problem for me, although I would not mind playing. As I said though I am free of Microsoft anyways, really, really I am. Well except the workplace is enslaved ...

So, what I am asking, ....

[list][*]Please update the oreilly link, or suggest a replacement others may refer to if there are questions beyond your how-to.[*]Any suggestions on how to get this windows NFS thing up and running or trouble shoot?[/list]

---

### Post by Erlander on 2007-05-29
The hack involves hacking Windows XP Home to turn on some of the features of Win XP Pro.  I haven't done it and probably won't as I'm using Windows less nowadays and have found that by setting up a SSH share I can access my Windows XP folders and files from both my Ubuntu pc's.  (One pc is dual boot.)

I don't think I should post links to Windows XP hacks on an open forum.

Rob

---

### Post by bodhi.zazen on 2007-05-30
Update ~

Thanks for the How-to Jose Catre-Vandis

I am a fan of your work on the forums.

I was able to get NFS Sares mounted *But it took some research*

For all interested I updated this how-to on the UDSF wiki :

[http://doc.gwos.org/doku.php/doc:network:nfs#mount_nfs_shares_on_windows](http://doc.gwos.org/doku.php/doc:network:nfs#mount_nfs_shares_on_windows)

---

### Post by drocra on 2007-06-03
I'm having some user/password problems. I've installed the client according to instructions, but when I try to access my nfs share (using 192.168.1.200:/media/av in Add Network Drive) I get prompted for a user ID and password. I tried using two of my ubuntu logins and an XP login - none of them work. I keep getting "The network path could not be found."

This is the only line in my /etc/exports :

/media/av 192.168.1.1/24(sync,rw,no_root_squash)

Any suggestions? Am I missing something obvious?

By the way, the NFS share works perfectly from my other Ubuntu client.

---

### Post by bodhi.zazen on 2007-06-03
I had problems with the how to when I tried it as well.

 
 I got it to work by installing and configuring  "User name mapping"

See this link : : [http://doc.gwos.org/index.php/MountNFS#Install_SFU](http://doc.gwos.org/index.php/MountNFS#Install_SFU)

---

### Post by McSnuffy on 2007-07-12
This guide worked great for the most part (I really didn't want to do the whole Samba thing when all I want is to be able to see my music in Windows), but I seem to be stuck at mounting.

**Some info:**
- I'm running Windows Server 2003 on this laptop, so I didn't use the hack.
-The box I am trying to mount from is not an Ubuntu box, but an Arch box. However, NFS is set up just the same and so are all my export files.
- The share from the Arch box mounts flawlessly on my other laptop, which runs Ubuntu 6.06.
- User Name Mapping in is done with the group and passwd files copied from my box.

Everything seemingly works alright up until when I have to actually mount the volume. When I go to map the network drive by entering "192.168.1.102:/home/myusername" (which, as I said earlier is exported correctly and mounts fine elsewhere) I get the error: "The drive could not be mapped because no network could be found." Also, the share does not show up when I browse under "NFS Network". Only "Default LAN" and "Favorite LAN" show up under this heading. They have no sub-headings. I think that the problem is on the Windows side, but networking in Windows has always been a nightmare for me and I am really not quite sure what to do from here. Could anybody please assist me?

---

### Post by bodhi.zazen on 2007-07-12
I had some difficulty as well. See if the link in my post just above your helps.

Specifically look at the sections on installation and configuration of SFU (on windows).

HTH ;)

---

### Post by McSnuffy on 2007-07-12
> **bodhi.zazen said:**
> I had some difficulty as well. See if the link in my post just above your helps.

Specifically look at the sections on installation and configuration of SFU (on windows).

HTH ;)

I read that section of the wiki very carefully. I only installed the NFS Client and User Name Mapping, and I synchronized everything using the SFU app. It was very helpful, thanks, but I don't think it relates to my specific mounting problem, where the share just isn't showing up under the NFS Network.

---

### Post by McSnuffy on 2007-07-12
If I don't figure this out by the end of tomorow, I'll just install Ubuntu on this laptop as well and mount to that.
Sometimes, it is amazing how much more simple things are on the other side. ;-)

---

### Post by bodhi.zazen on 2007-07-12
> **McSnuffy said:**
> I read that section of the wiki very carefully. I only installed the NFS Client and User Name Mapping, and I synchronized everything using the SFU app. It was very helpful, thanks, but I don't think it relates to my specific mounting problem, where the share just isn't showing up under the NFS Network.

Thanks, I am just trying to understand where you are in the process.

If I understand you correctly, it is an issue with the (windows) client (the NFS server is working).

So, if the server is working, let's configure the windows client. I am no expert on windows ming you ;)

OK, I had to re-read that how-to myself. I had a similar problem which is why I wrote the how to.

My only advice is to follow the "Configure SFU" section, the part where you copy /etc/passwd and /etc/groups to C:\  -> map your users and groups -> apply -> synchronize

[http://doc.gwos.org/index.php/MountNFS#Configure_SFU](http://doc.gwos.org/index.php/MountNFS#Configure_SFU)

You should then be able to mount the NFS share (at least that is what I had to do)

If you have done that and it does not work, dare I say, contact Microsoft ? :lolflag:

---

### Post by Jose Catre-Vandis on 2007-08-16
I have kept things simple on my setup by using the same login and usernames on the windows box as the nfs server, and also all my files and folders have full permissions. This is OK on a closed LAN and for local/my use.

"Permission Denied" is usually due to one of two things: either you do not have the same user on your server as on your Windows box, or you do not have the correct permissions set for the files and folders on your nfs share, or both!

Am about to run a setup on a new machine, so will report back on success. (following my own howto!)

Also, please note XP Home hack link updated (also on original how to)
```
http://www.oreilly.com/pub/h/2883
```

---

### Post by p-stone on 2007-08-25
I'm having an access issue. I can load the root of my share and see all the subdirectories and files, however I cannot load any subdirectories, I get a permission denied error. I have set my windows username and password to the same as my linux one. The shares work perfectly on my linux machines but on two different windows boxes fail. I have tried the remote mapping technique for installation and also local with passwd and groups, both give the same error.

Here is my etc/exports
```

/home/cornucrapia/storage 192.168.1.1/24(rw,no_root_squash,async,insecure)

```
Help is much appreciated

---

### Post by Jose Catre-Vandis on 2007-08-27
All I can suggest is that you work back through your permissions settings on the nfs server and the mappings on your windows boxes.

Also check your syntax for your shares: is the folder you are sharing the one you are mounting?

---

### Post by p-stone on 2007-08-27
> **Jose Catre-Vandis said:**
> All I can suggest is that you work back through your permissions settings on the nfs server and the mappings on your windows boxes.

Also check your syntax for your shares: is the folder you are sharing the one you are mounting?

Thanks for the reply. I've double checked the mappings on the windows boxes, the fact that I can see the first level of the shared folder suggests to me that I have that set up correctly.
Once again, here is my /etc/exports:```

/home/cornucrapia/storage 192.168.1.1/24(rw,no_root_squash,async,insecure)

```
The server is set static to 192.168.1.100 so on the windows boxes I mapped to 192.168.1.100:/home/cornucrapia/storage
That seems pretty straightforward to me.
As for permissions, I confess I don't know enough to say for sure if that's the issue. I'll post some examples of the permissions I have set below in the hopes that someone can assist me further
```

This is the root folder that I am sharing:
drwxr-xr-x 13 cornucrapia cornucrapia 4096 2007-08-24 02:00 storage

A file and two videos in the storage folder:
-rw-r--r--   1 cornucrapia cornucrapia  3555 2007-08-23 09:18 rtorrent.rc.bak
drwx------   7 cornucrapia cornucrapia  4096 2007-08-23 05:10 videos
drwxr-xr-x  18 cornucrapia cornucrapia  4096 2007-08-25 14:45 downloadstosort

Files and Folders within the subdirectories of the storage folder:
-rwx------ 1 cornucrapia cornucrapia 731797504 2007-08-21 09:27 ubuntu-7.04-desktop-i386.iso.iso
drwx------  2 cornucrapia cornucrapia 4096 2007-08-21 12:29 documentaries
drwxr-xr-x  2 cornucrapia cornucrapia 4096 2007-08-23 05:11 isos

```
Hopefully this will mean more to someone else than it does to me. Thanks again for the help

*EDIT* Again I just wanted to clarify that I'm only experiencing this issue on my XP clients, I have two other ubuntu boxes that have full control of the share, I haven't encountered any restrictions so far. Is there a trick to giving the windows boxes the same UID and GUID of my server or something along those lines? As I said I've done local mapping and mapping with passwd and groups, maybe on the latter I didn't configure the file to point to the right user? I'll keep looking for a solution, is anyone else experiencing a similar issue?*EDIT*

---

### Post by Fondor1 on 2007-09-07
> **drocra said:**
> I'm having some user/password problems. I've installed the client according to instructions, but when I try to access my nfs share (using 192.168.1.200:/media/av in Add Network Drive) I get prompted for a user ID and password. I tried using two of my ubuntu logins and an XP login - none of them work. I keep getting "The network path could not be found."

This is the only line in my /etc/exports :

/media/av 192.168.1.1/24(sync,rw,no_root_squash)

Any suggestions? Am I missing something obvious?

By the way, the NFS share works perfectly from my other Ubuntu client.

My problem is very similar to the above.

I've got a sucessful NFS server running on Ubuntu - I've tested with two separate ubuntu machines, both can read and write fine.  XP Pro will not cooporate, however.  Everything was working correctly up to mapping the network drive.  Browsing to my share location (\\192.168.0.7\home\patrick) (which windows can see), I select it and click finish.

It pops up a dialog saying "Attempting to connect to \\192.168.0.7\home\patrick..."  Then a second dialog pops up saying "NFS Login Sucessful"  and "You are currently logged in as:   UserName: rakai  UID: 1000  Primary GUID: 1000", then says choose yes to accept that login or no to change the settings.

Selecting Yes will bring up the XP network prompt for a username and password.  I have only one user on each computer, and neither of these users will login.  When I enter any credentials and click ok, it eats the info and spits the same prompt for credentials again.

So far there's a pretty limited pool of resources dealing with this problem (at least that I found).  Does anyone have any experience in this realm of networking?

---

### Post by ebeaty on 2007-10-15
Fondor1, did you find a solution?  I'm at the same point, where XP asks for a username and password but just repeats the prompt every time I enter it.
Thanks,
Ed

---

### Post by Fondor1 on 2007-10-24
Unfortunately not ebeaty.  I resorted to sharing using Samba.  It works, just not quite like I wanted it to!

-Fondor1

---

### Post by Jose Catre-Vandis on 2007-11-01
Fondor1

I have "async" and not "sync" in my exports file?

You say everything went fine until you got to mapping the networking drive. I take it this is in Explorer? Did you have success in mapping users? This seems the most likely area for your problem. If you are able set up users with the same name on both XP and the NFS server, and follow closely the mapping user info supplied by Bodhi Zazen

---

### Post by hypernihl on 2007-11-06
Any one find a solution? I have this same problem. My XP machine sees the NFS directory, but I get prompted for a password.

---

### Post by TheRealMikeD on 2007-11-07
I was having that problem (with the endless login prompt), but I think I figured out how to get around it.  Here is what I have observed:

[LIST=1]
[*]If I try to browse to the server through Windows Explorer, and NOT using a mapped drive letter (e.g. \\MYUBUNTUBOX\MYSHARE), I get the log in prompt.
[*]If I try mapping a drive letter and click the link for "connect using a different user name" in the drive mapping dialog, I get the login prompt.
[*]If I try mapping a drive letter but DO NOT click "connect using a different user name," no login prompt and the mapping succeeds.
[/LIST]

Hope this helps someone.

-Mike D.

---

### Post by TheRealMikeD on 2007-11-07
So, once I got the mapped drive letters connecting successfully, I noticed that the file transfers are really slow between my WinXP box and my Ubuntu box.  And transfers of large files usually get aborted and don't successfully copy from one to the other.

In other words, it works, but it doesn't work that well.

I have a nearly identical set-up at work with WinXP and a FreeBSD box and that works like a champ.  Not sure why it doesn't seem to work so well with my Ubuntu box at home.  Any insights, anyone?

If it helps you to analyze the situation, I tried Samba and had the same result: it worked, but the file transfers were slow and unreliable.

Thanks,
-Mike D.

---

### Post by TheRealMikeD on 2007-11-08
Another problem I've noticed is that I can't get read-write access to my home directory.  It seems that I can only get read-write access to a directory with 777 permissions, regardless of what's in the exports file.

I've tried sharing it like so:
/home 192.168.0.2(rw,async,no_root_squash)
and like so:
/home/miked 192.168.0.2(rw,async,no_root_squash)
and I get permissions errors every time.

I was able to fake it like this:
/home/miked/share 192.168.0.2(rw,async,no_root_squash)
where /home/miked/share has 777 permissions.

---

### Post by TheRealMikeD on 2007-11-10
So, I solved my slowness problems.  Turns out it was an unsupported network card.  See my post in this thread for details: [http://ubuntuforums.org/showthread.php?t=218373](http://ubuntuforums.org/showthread.php?t=218373).

---

### Post by joTi on 2008-01-29
Hi there, im really busting my *** with this.

I have Vista, not XP, and the SFU for XP seems much more advanced and simple in a way.

The Vista crappy version doesn't have the Map Tab and so forth leaving me scratching my head.

Is there a walkthrough for this on Vista.
Help would be much appreciated.

---

### Post by Jose Catre-Vandis on 2008-01-30
> **joTi said:**
> Hi there, im really busting my *** with this.

I have Vista, not XP, and the SFU for XP seems much more advanced and simple in a way.

The Vista crappy version doesn't have the Map Tab and so forth leaving me scratching my head.

Is there a walkthrough for this on Vista.
Help would be much appreciated.

I agree that Vista appears to handle things in a more transparent way!

You should simply be able to connect network shares from the Tools menu, and map a network drive. Issues may bee around authentification though. I overcome this by using the same logins and passwords on Vista and the server and/or you maybe need to add the "Vista" user to your server.

Where have you got to - when do things stop working, and perhaps we can narrow down where the problem is.

---

### Post by joTi on 2008-01-30
> **Jose Catre-Vandis said:**
> I agree that Vista appears to handle things in a more transparent way!

You should simply be able to connect network shares from the Tools menu, and map a network drive. Issues may bee around authentification though. I overcome this by using the same logins and passwords on Vista and the server and/or you maybe need to add the "Vista" user to your server.

Where have you got to - when do things stop working, and perhaps we can narrow down where the problem is.


First off, the tools menu, I don't know which one exactly you mean because I am on a Swedish edition of Vista.

But if i may translate my Swedish menus freely it says something like this.

Archive  | "Measurements/Manage" | "Show/Display" | Window | Help


If you mean the Manage (perhaps Tools to you?) tab it has these options (still freely translated) when the "Services for NFS" in the left frame is selected.

"Connect to another computer"
"New window "from here""
"Export list..."
"Properties"
"Help"


If the "Client for NFS" is selected in the left frame is selected the following will appear in the "Manage" tab:

"Start service"
"Stop service"
"New window "from here""
"Properties"
"Help"




However if you mean that a Tools post should exist on the left frame there is none for me, neither is there a "User Name Mapping" post in the left frame like all the walkthroughs are referring to.



So im pretty much stuck as soon as I open the Administration application, and really need to be thoroughly guided through this.

Some screenshots from you guys would help a TON.

Sidenote: when i type 
showmount -e servername 
the output lists my shared NFS volumes just as it should.


Ps. Sorry if my English might confuse you.

---

### Post by Jose Catre-Vandis on 2008-01-30
Sorry, haven't done this in a while and was a long way from a Vista box!

#########################
Open an Explorer window using Start -> Computer
You should see "Map A Network Drive" in the Toolbar at the top
Click on this
In the dialog box enter the nfs drive info in this format:
```
192.168.0.10:/media/video
```
(Assumes your nfs server IP is 192.168.0.10 and you are sharing by nfs with /media/video)
Click Finish
#######################

Vista will probably have a think then show the share in the Explorer window, and open another explorer window at the share.

If this doesn't work, try clicking on the "connect using a different user name" and enter the login details for the server. As I said before, I set up a user on the server that matches the user login for Vista so connecting shares requires no authentication for me. 


To access the properties in the Admin Application, right clck on the "Services for nfs" in the left pane, and click on properties - this will open the properties dialog
In the Services for NFS Properties dialog I have ticked the box for user name mapping, and entered the name of my Vista pc in the box (don't know if this makes any difference!)

You can right click on the "Client for nfs" in the left pane to access properties for file permissions as well

Let me know how you get on :)

---

### Post by joTi on 2008-01-31
Ahh, It was an Explorer window, no wonders then :)

Well, it came to an screaming halt again.
Vista just yells that it cannot connect to that adress, i have substituted your example ip for my servers of course!

And i configured the Admin Application like you, and I guess that the "Client for NFS" should be running.
However, when i click "start service" it gives me an error:

"Could not start the service - The depending service does not exist or is marked for removal."


OOk? 

Perhaps i should reinstall nfs-service on vista.


[EDIT]

Reinstalled the nfs-service and got one of the shares mounted in Vista.

Only one left, which is giving me some trouble.

"Could not create the connected network unit because of the following error:
An unexpected error has occurd."

Windows, you gotta love it ;)

---

### Post by Jose Catre-Vandis on 2008-01-31
Yeay we got somewhere!

I do remember that on occasion, if I tried to mount more than one share the second one would bork, but it didn't happen last night!

Well done for sorting it out :)

---

### Post by joTi on 2008-02-01
> **Jose Catre-Vandis said:**
> Yeay we got somewhere!

I do remember that on occasion, if I tried to mount more than one share the second one would bork, but it didn't happen last night!

Well done for sorting it out :)


Yeah, we really did!

Well, as you said, after i had rebooted the computer the second one mounted right up as well. 

There is, however, a couple of slight problems left.

1. Windows seems to forget about my User/Pass data between startup's , i wonder how i can get it to remember? hmm.

2. It seems that as soon i browse the NFS mounts Windows get really sluggish, i really don't know why. Sometimes it locks the system up.
With Samba, which i used in between, I never had that problem, something is taking way too long for Vista to handle.

Any suggestions?

Big thumbs up on the support!  =D>

---

### Post by Jose Catre-Vandis on 2008-02-01
If I remember right, (and this worked in XP) once you have your share mounted, try creating a shortcut for the share on your desktop (or place where you like shortcuts). A doubleclick on this shortcut on the next reboot should load up the share.

The other way is to tick the box in the map network drive dialog to make the share persist across reboots. I had some problems with this, so used the first suggestion, though not needed to try this on Vista yet.

---

### Post by joTi on 2008-02-04
I have tried those methods, and they don't seem to work.

However, it seems like I can change my UID and GID by right clicking my mounted drives in Vista  and enter the Properties of the drive.
Perhaps if I enter those values as they should be (instead of 1000 & 1000) I could get rid of that sluggish feel, and mount easier?

Now, an embarrassing question, how do I look up my true UID & GID? :)

[EDIT]
Nevermind, found it :P

---

### Post by KennedyM on 2008-02-09
Thank you all for the excellent HowTo at the start of the thread, and for the subsequent updates, experiences, etc.

We followed the suggestions, and, generally, had success with accessing the NFS exports in the Windows clients, when we used a one-for-one match between Windows and Unix users.

We would prefer an approach whereby a client PC would have a "standard" build, and would have a generic minimal-rights username for initial sign-on for all Windows users. This would not be matched within SFU to any specific username in Linux. Then, when the PC user wants access to the NFS exports, the precise Linux-username (and PW) should be submitted, to define what rights that user has on the shares. We tried with some and no username mappings in SFU, and changed other settings, etc... We get Login screens, but we've never managed to get any username/pw combo to be accepted.

Other posters here seem to have had similar experiences.

We would greatly appreciate any pointers or suggestions.
  - Mike

---

### Post by Jose Catre-Vandis on 2008-02-09
I think the nfs server PC has to have all users who might access the server loaded up for things to work. I have several members of my family, on Windows PCs, who access the nfs servers I have running, they login fine and have different permissions to me. 

Why would you want your users to use different login details (for the nfs server), surely that's the whole point of security and permissions, knowing who can and who can't and who did what! :)

What might be worth a try though, is to set up a group on the server, and set permissions for that group, and then add the users to it. This might work?

Starting to get out of my depth again ! :)

---

### Post by KennedyM on 2008-02-10
Jose,

> I think the nfs server PC has to have all users who might access the server loaded up for things to work.

You might be correct there. Some "Google" searches suggest that SFU can map a single Win-user to multiple *nx-users, and vice-versa, but other posts suggest that this is not permitted. I'll experiment a bit more.

> I have several members of my family, on Windows PCs, who access the nfs servers I have running, they login fine and have different permissions to me.

Does each get a "Login" screen to the NFS shares when they try accessing them (rather than their Windows login)? That's what I'm after.

> Why would you want your users to use different login details (for the nfs server), surely that's the whole point of security and permissions, knowing who can and who can't and who did what! :)

Good question, but I didn't explain the situation very well. Our intention is to roll out totally "standard" PCs, with just a single generic non-admin sign-in at the Windows level. Say, "UserX". That makes life simple with tens or hundreds of PC/Win users. More  like "Dumb Terminals" :frown: And there's no "UserX" on the NFS server, but lots of very specific Users and Groups.

Then, when UserX mounts the NFS exports, they're asked for their specific NFS login. Then all their NFS permissions, etc, kick-in.

> Starting to get out of my depth again ! :)

Absolutely not!. If I make any progress, I'll post here.

Thank you again,
    - Mike

---

### Post by Jose Catre-Vandis on 2008-02-12
> Does each get a "Login" screen to the NFS shares when they try accessing them (rather than their Windows login)? That's what I'm after.

Not tried it that way, I set them up with desktop shortcuts with login already taken care of through windows user authentication and users on the server, so it appears transparent.

There is only one "techie" in my house :) ( I use the word loosely in my case :) )

---

### Post by VanBond on 2008-03-08
*From Mac OSX 10.4.11*
I*n finder, mount the Windows share with the* **Windows Services for UNIX Version 3.5** *temp files*
*In Terminal*
#cd *to the temp directory from above*
#cat SfuSetup.msi | sed 's/VersionNT \= 501 AND MsiNTSuitePersonal/VersionNT \= 510 AND MsiNTSuitePersonal/' > tmp.msi
*In Windows XP Home, double-click **tmp.msi***

---

### Post by Jose Catre-Vandis on 2008-03-08
> **VanBond said:**
> *From Mac OSX 10.4.11*
I*n finder, mount the Windows share with the* **Windows Services for UNIX Version 3.5** *temp files*
*In Terminal*
#cd *to the temp directory from above*
#cat SfuSetup.msi | sed 's/VersionNT \= 501 AND MsiNTSuitePersonal/VersionNT \= 510 AND MsiNTSuitePersonal/' > tmp.msi
*In Windows XP Home, double-click **tmp.msi***

I am sure it's good :), but could you explain a little more as to what you are doing?

---

### Post by VanBond on 2008-03-17
Why, yes I can.  Recently, a situation arose where I had to install software from an msi on a Windows XP Home machine that was looking for version 501 in the VersionNT string, so the sed to 510 enabled that .msi to install and run correctly.

My point is that smb mounting of that networked share to a writeable winxp home volume enabled me to just replace the critical string with the value I needed from it into a file that windows recognized as run-nable, and it worked as the .msi, with issues, would have; only without the issues.

Wish I could be more clear.

:^o

Van

---

### Post by Jose Catre-Vandis on 2008-03-18
> **VanBond said:**
> Wish I could be more clear.

:^o

Van

Me too :)

but if it works it works :)

---

### Post by heckheck on 2008-03-29
OK time to share some hard won knowledge on this subject, having burned down an entire Saturday learning it.

Many people have written about getting the " Network path not found" message when trying to connect from a Windows client to an Ubuntu server, which is exporting an NFS share mount point.  I too was suffering from this most of the morning, but decided to get serious on the problem and went into full debug mode.  What I found was that in my case (and probably a good many others out there), the problem was caused by a Reverse DNS lookup that was being done by the Ubuntu server prior to establishing the connection from the Windows client.  I confirmed this by running Wireshark on the server and observing the packet flow.  Indeed, the server was getting the NFS mount command correctly, but then was in turn trying to ask my DNS provider for name resolution on the Windows client address.  I found this curious, since I had no problems mounting the same NFS point from another Ubuntu client (no such RDNS lookup was happening).  A little Googling revealed that this is probably due to some baked in option for NLM that the MS SFU NFS has turned on.  What was happening is that since I didn't have a local DNS server, this reverse DNS request was leaking out to the internet, where it is unresolvable (unroutable, not registered, etc).

So the trick is how to stop that RDNS lookup from happening.  Here are the approaches you can take.

1. Use a different Windows NFS client, I've read that others don't have this problem.  Not an option for me, since MS SFU is free and the others, aren't.

2. The easiest way to fix the problem is to add entries to the Ubuntu server's /etc/hosts file, so that the Windows clients IP addresses are known to the Ubuntu box.  This will suppress the RDNS query, and was my first success.  Unfortunately, I like to use DHCP for the Windows boxes.  There are ways you could make this work.  Use statically assigned DHCP addresses (if you can configure such with your DHCP server), switch to static IP addresses, etc.  So for those of you who want the easy fix, here it is.  Add a line like this (modified with the correct IP) to your /etc/hosts file

192.168.1.1 windowsclient

3. Another gross solution would be to run DNS on the Ubuntu box and add rules to resolve the local IP address range.  I didn't pursue this, but if you want to, you might see if this post helps [http://www.dbforums.com/archive/index.php/t-673970.html](http://www.dbforums.com/archive/index.php/t-673970.html)

4. The solution I settled on is elegant and works great for me, but has an additional hardware requirement.  I happen to have a Linksys router running DDWRT firmware (GREAT STUFF!!!), and I took this as an opportunity to finally setup some DNS capability on this equipment for my local network.  The DDWRT firmware has DNSMasq built in, which allows for some simple local name resolution with flow through to your actual DNS server.  I won't document the whole thing here, but the salient points are that properly setup, DHCP clients will have their names/IPs resolved if the Ubuntu server is using the DDWRT router as it's DNS in /etc/resolv.conf.  Computers using DHCP are pretty easily resolved with the basic DNSMasq, but with some extra work, you can get static IP computers to name resolve too (requires some parameter passing in a startup script).


Well this is already one very long post, but there is some more useful information I found with regards to permissions and the User Name Mapping.  Note I uncheck 'Simple mapping' in all of the following

1. The password that the SFU asks for is your Windows password.  This doesn't even get passed off (from what I've found) to Ubuntu during the NFS authentication.  NFS really isn't secure at all in this regard.

2. If you want to login using a different Linux user that's fine.  Just create the mapping in the User Name Mapping tool.

3. It is possible to login using a different windows user if that user has a mapping.  You will need to click 'connect as a different user' during the drive mapping, and provide that user's name and password.  Note the user name should be decorated with the windows client hostname, like WINDOWBOX\user

4. Another thing I found helpful for multiple users managing data in a common NFS mounted directory, is to change the c:\passwd file so that all the users are in a common group, so that they can create files that can be modified and written by each other.  So create a group on the Ubuntu box like 'data' to which you add all the users, and then modify the c:\passwd file you store on the Windows box, so that they are all in that GID.

Hope this helps some of you.

-Jim Heck

---

### Post by Jose Catre-Vandis on 2008-03-29
Thanks for your additions heckheck, obviously more than one way to skin a cat :)

---

### Post by 4nDr3s on 2008-05-14
> **Jose Catre-Vandis said:**
> I gave up on Samba several months ago, and switched to using NFS to share folders over my LAN. But one of my family insists on using Windows XP, so I needed to find a solution to allow them to access the NFS shares. This is neatly done by Microsoft themselves, for "free", using their "Windows Services for Unix" setup. My file server is an Edubuntu Dapper (I use LSTP too) with four NFS shares. Please note that this is a basic, get you up and running howto, there is more configuration required and available, especially for the security conscious, which is beyond the scope of this howto.

First off, you need to understand NFS Server and Client for Ubuntu. I followed this guide, and suggest you do the same.
```
http://www.ubuntuforums.org/showthread.php?t=249889
```

The important part to understand is the syntax for a share
```
yourserver:/data
```

You may also need the username and password for your server.

QUICK INSTALL OF SFU:

Anyway, fire up your Windows XP box and download the installer for "Windows Services for Unix", currently at version 3.5, from this page:
```
http://www.microsoft.com/technet/interopmigration/unix/sfu/default.mspx
```
This is @ 200mb. You will end up with a file called SFU35SEL_EN.exe.

Double click to unzip this file, it should upzip into your username's Temp folder, something like C:\Documents and Settings\"yourusername"\Local Settings\Temp. Seek out the setup.exe file and double click. Click through the installer process, as much as you might hate to, accept the licence agreement, and the standard installation option, and without changing any other settings until you reach the mapping page.Tick the radio button in the upper part of the window (Remote User Name Mapping Server) and then enter your server name or IP address in the box. Click OK and finish the installation process. Windows may offer you a restart, which you should take up.If it doesn't, do a reboot anyway. The NFS Client should automatically be started on boot up.

ALTERNATE INSTALL OF SFU: - THANKS TO bodhi zazen
(overcomes user name issues)

 Install SFU


Navigate to C:\Documents and Settings\"yourusername"\Local Settings\Temp

Double Click on Sfusetup


    * Select Custom Install
    * We only need to install :
          o NFS -> NFS Client
          o Auth Tools for NFS -> User Name Mapping 
    * Deselect Everything Else 


During the next steps accept all defaults

    * Default to the Machine's Domain
    * Select passwd and group files
    * Select user name mapping 

Reboot Windows


[edit]
Configure SFU


1. From Ubuntu copy /etc/passwd and /etc/groups to C:\

    * You can read these files as Text so you may want to eliminate everything from passwd except the log-in names of your Linux users and everything from groups except users (I did). 

2. Launch SFU

Start -> All Programs -> Windows Services for unix -> Services for Unix Administration

3. In the "Client for NFS (On the Left) set the desired permissions of the sharer (I chose rwx for owner and group, nothing for other)

    * Click Apply 

4. In the "User Name Mapping" (On the Left)

    * Select "Use Password and Groups Files" -> Enter C:\passwd and C:\groups in the appropriate boxes 

5. Maps Tab

    * Select the "Show User Maps" -> Click "Show Windows Users" and "Show Unix Users"
          o Select a Windows user and associate it with the appropriate Linux User (one who can normally mount the NFS Share on a Ubuntu Client)
          o Click the "Add button" 

    * Select the "Show Group Maps" -> Click "Show Windows Groups" and "Show Unix Groups"
          o I mapped Windows Administrators to Linux Users
          o Click the "Add Button" 

6. Back to configuration Tab

Click the "Apply" button on the top left Click the "Synchronize Now" button near the bottom




Once Windows is back up, you can start adding NFS network shares. Do this in just the same way as you would add normal network shares in Windows. From File Explorer, select "Tools" and then "Map Network Drive". In the dialog, type the server/share address in the following format:
```
yourserver:/data
```
using the correct name or IP address for your server, and the correct path to your share. Remember the colon ( : ) !! Tick the Reconnect at Logon so that your shares persist through reboots. Windows firewall (or your own firewall) may block NFS Client on reboot, and should offer you the chance to unblock it.

Now, depending on how you have things set up, you may or may not be asked for a username and password. I wasn't, but this may have been because on the test Windows box I used, I just happened to use the same username and password as I had on the server. Not had a chance to check this out yet. However, click OK on any resultant dialogs that pop up, and head back to Explorer to check out your new nfs network share. (In fact, XP opens up a new window for your share).

OK, this is only supposed to work on server editions of Windows (2000, Server 2003, XP Pro) but there is a hack you can do to make the installer work on XP Home Edition ( I haven't tried it yet) Look here:
```
http://oreilly.com/pub/h/2883
```1

[EDIT] Errors on boot of Windows Box due to Persistent Connections to NFS Server

If I set a network share as a persistent login, I get an error dialog on boot of my windows box. Having used the User Mapping Service, I found I could overcome this error dialog as follows:

Create your network share
Send a shortcut of the share or a sub folder within it to the desktop
Disconnect the share
Reboot (no error dialog! :))
Double click on the shortcut and one of two things will happen:
You will simply get a dialog asking you to confirm your log on details, which if you "OK" will open a folder on the share
or
You will get a dialog asking you to enter login in details

I also selected simple mapping as an option in User Mapping Service, but this requires you to have the same user on the server as on your windows box, I believe.[END OF EDIT]

Finally, there is a control applet to be found in Start>Programs if you want to play with settings. If I come up with anything else, I will update.




Hi there. I've tried this and i got the NFS Share mounted on my Win 2003 Server successfully, but i have a problem. I can't create new files in the NFS share from windows because it says that i don't have permissions to do it. Any Ideas?? 
(By the way, i'm also mounting the NFS share from a linux box and it can write to it)


And (and offtopic question)... is it possible to make IIS work with the mounted NFS Share? How? thanks 

Thanks for help

---

### Post by Jose Catre-Vandis on 2008-05-15
@ 4nDr3s

Have a good read through this whole thread, that might produce some solutions. My most regularly repeated fix is to ensure you have the same user on the server as you have on the client (don't have to be logged in on server as a particular user). The other thing might be regarding file/directory permissions. Try 777 on some files/directories and see if that makes a difference?

Don't know about IIS, though i tried linking up NFS shares with Windows Home Server and that didn't work!

---

### Post by pannerrammer on 2008-07-01
Jose, Thanks.

I'm not sure if it's just me, but I couldn''t find anything but words at your ms/technet link. 

Eventually I found the download at [http://www.microsoft.com/downloads](http://www.microsoft.com/downloads) and searching for SFU.

Now the fun starts!

PS... As you'd possibly expect, XP SP4 may (or may not!) have introduced a problem. See [http://www.support.microsoft.com/kb/884852](http://www.support.microsoft.com/kb/884852) for info and patch.

---

### Post by Jose Catre-Vandis on 2008-07-02
@ pannerrammer

Link to download is under **Download** ;) on the right hand side of the page I have linked to in my first post. if you are using FF3 the page might not be rendering correctly - I can only see **load** :D

The fix you refer to is for Windows 2000 with SP4, but your link does provide a route to a hotfix :)

---

### Post by pannerrammer on 2008-07-07
I forgot that MS websites only work with Internet Explorer :(

I think I downloaded the right XP SFU - anyway, with a bit of mucking about with folder permissions on the nfs server it works fine. Thanks.

---

### Post by diehardyouth on 2008-07-18
Hi.  I'm running Vista Enterprise trying to share data over an NFS mount running linux and I'm having user id problems... When I create any file on the drive It makes it as UID  and GID -2... 

I can mount it fine, but I can't find user name mapping?  Is there user name mapping in vista? I don't remember even getting a chance to use it when I installed SUA? I don't have to set up an Active Directory do I?


your help is much appreciated, thanks

---

### Post by Jose Catre-Vandis on 2008-07-20
My idiots way round it is to create the same user with same UID on the server as on the client, this should then allow you to connect and have the right file permissions (as long as you set them up on the server first!)

---

### Post by steve_d on 2008-07-22
> **heckheck said:**
> 
2. The easiest way to fix the problem is to add entries to the Ubuntu server's /etc/hosts file, so that the Windows clients IP addresses are known to the Ubuntu box.  This will suppress the RDNS query, and was my first success.  Unfortunately, I like to use DHCP for the Windows boxes.  There are ways you could make this work.  Use statically assigned DHCP addresses (if you can configure such with your DHCP server), switch to static IP addresses, etc.  So for those of you who want the easy fix, here it is.  Add a line like this (modified with the correct IP) to your /etc/hosts file

192.168.1.1 windowsclient

Hope this helps some of you.

-Jim Heck

I must say this was very helpful. If not for your investigative skills, I'd be lost.

Thanks!

---

### Post by markp1989 on 2008-09-26
just tried this, cannot install it in windows xp home. any one know a work around

---

### Post by Jose Catre-Vandis on 2008-09-27
> **markp1989 said:**
> just tried this, cannot install it in windows xp home. any one know a work around


Doesn't work for Home out of the box, you have to hack some configuration files. The link to the hack was in the first post, but here it is again

[http://oreilly.com/pub/h/2883](http://oreilly.com/pub/h/2883)

---

### Post by ThunderRd on 2008-12-26
I'm not sure if this thread is still being followed, but if I'm lucky someone can help ;)  I've read through it carefully, but there are some things that still don't make sense to me.

I have three XP Pro boxes and 1 Ubuntu server running 8.10.  There are directories on the server I wish to share; I'm the only user, so security isn't a concern.  All are on fixed IPs with the gateway at 192.168.0.1, and the others at 192.168.0.10, etc.

I have been wrestling with SAMBA for a LONG time.  I did get it working but I wasn't satisfied; I found that the file transfer speeds were slow. I decided to try NFS to help that problem.

First, I uninstalled everything SAMBA, then I followed the OP carefully, setting up NFS and portmap.  After that I entered the shares in /etc/exports.  Here is the contents of /etc/exports:

```

/media/FAT32_ARCH 	192.168.0.0/24(rw,no_root_squash,async)
/media/FAH6 	  	192.168.0.0/24(rw,no_root_squash,async)

```

After that, I installed SFU on one of the XP boxes and followed the instructions regarding installing the NFS client and User Name Mapping, and copied over the passwd and group files to the client machine.

After a reboot XP immediately showed the shares in Explorer under NFS Network>Default LAN>opteron-185.  So far, so good.

Problem is, I can't see the contents of the shares.  I guess, if the shares are being advertised, but I can't view the contents, it is a permissions problem of some kind, but I don't know enough to figure it out.  I'm learning Linux gradually, and although I have worked through a number of problems myself, this one has me confused.

I think it's possible that I don't properly understand this [from malco's thread, which I also studied]:

> 
Example to mount server.mydomain.com:/files to /files. 
In this example server.mydomain.com is the name of the server containing the nfs share, and files is the name of the share on the nfs server

The mount point /files must first exist on the client machine.
cd /
sudo mkdir files

to mount the share from a terminal type

sudo mount server.mydomain.com:/files /files

If the server name is "OPTERON-185", and the workgroup is "OFFICE", what should I use as "server.mydomain.com" in order to mount manually? 

What other files should I post to get some troubleshooting help?

---

### Post by heckheck on 2008-12-26
ThunderRd, it would be helpful if you post what you are using for passwd and group files, though your problem seems more basic, since usually, it is possible to at least see files even if you can't write them (because of a permission problem).

In answer to your question on what should you use to mount a drive, try mapping a network drive on the Windows box.  I export top level directories (like /data), so I will give you an example of what works for that.  Use the IP address of the Ubuntu box and the name of the shared folder like this

my /etc/exports on my Ubuntu box 10.100.200.60

```
/data 10.100.200.0/24(rw,no_root_squash,async)
```

What I type in the map network drive window

```
10.100.200.60:/data
```

I use the same username on Windows as I do on Ubuntu.  That username is mapped by the SFU Name mapping application so that it has the correct UID and GID.

If you run into problems where Windows complains along the lines of "Network Path Not Found" check out my post from March 29th, as you problem is likely due to a RDNS lookup by Ubuntu to verify the IP address of the Windows box.

If all else fails, break out Wireshark on the Ubuntu box, and get a capture of the NFS exchange between the two boxes.  That should shed some light on what is or isn't going on.

Hope this helps,

-Jim

---

### Post by heckheck on 2008-12-26
I figure it doesn't hurt to cross post a problem I've been having related to NFS and Vista here.  I originally posted this here [http://ubuntuforums.org/showthread.php?t=640760&page=87](http://ubuntuforums.org/showthread.php?t=640760&page=87) but haven't gotten any help yet.  Maybe someone here can help figure it out.

I have recently been experimenting with setting up LDAP on my Linux server to accommodate NFS authentication for Vista, which doesn't have built in UID/GID mapping, unlike the previous Services For Linux 3.5 (SFU) that MS provided for XP. I have followed the steps outlined in the first post by rickyjones, I have gotten a working openLDAP server running. I was able to get Windows Vista Ultimate 64 bit to join the domain I created (home.local), and it seems to be authenticating the LDAP user I created (heck).

I have run into problems getting an NFS exported mount point to mount as a network drive, however. Under Vista, the drive mounts, but I have been unable to get it to mount with any credentials (it mounts as uid -2, gid -2). I have installed Services for NFS and Subsystem for Unix-based Applications. I edited the Services for NFS Properties dialog to enable 'Active Directory domain name' as 'home' as the Identity mapping source. Is this the correct way to way to configure this property? When I try to mount the drive, I am logged into Vista on the 'home domain' as HOME\heck.

I have attached a Wireshark packet trace of an attempt to establish the mapping of the network drive. Here are the details of my network configuration.

Linux Server running Ubuntu 8.04 is named 'heckmedia' and has IP address 10.100.200.60
Vista Ultimate 64 is named 'heckquad' and has IP address 10.100.200.144
LDAP user logged into Vista is 'heck'
LDAP domain is home.local
Vista machine 'heckquad' is using 10.100.200.60 for DNS, and the Linux box is running bind9 as part of the LDAP setup
The exported NFS directory I am trying to mount is 'datatest', and has UID/GID credentials matching the LDAP entry for 'heck' (these ended up being UID 30000, GID 513, which I could see using PHP to query LDAP under Linux)

From the trace, the early part is the booting of Vista, and the logon of HOME\heck. The mount operation starts around timestamp 73.89 sec, packet 512. It seems Vista first tries to use SMB (Samba?) to find the mountpoint, and then some sort of HTTP mounting. When those fail, it tries LDAP, and runs into a problem around packet 559 (73.986471 time) with the bindRequest response, where LDAP in is complaining of invalid credentials (realm changed to 'home'). I see in packet 557 that the realm in the response to the first bindRequest (556) contains a string saying the realm was 'heckmedia', which is the name of the Linux server.
I'm sure there is just something off in the drive mapping process, where the network name of the linux server is being substituted for the realm. I just don't know enough to figure out how to fix it.

Anyway, I thought someone here could shed light on what may be going wrong. I'm at my wits end trying to get this to work, and am about ready to throw in the towel on Vista and go back to XP, where NFS just worked in my network.

Thanks for any help you can provide,

-Jim

---

### Post by ThunderRd on 2008-12-26
@heckheck:
Thanks for taking time to answer my post and a great holiday season to you ;)

> **heckheck said:**
> ThunderRd, it would be helpful if you post what you are using for passwd and group files, though your problem seems more basic, since usually, it is possible to at least see files even if you can't write them (because of a permission problem).

passwd:
```
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/bin/sh
man:x:6:12:man:/var/cache/man:/bin/sh
lp:x:7:7:lp:/var/spool/lpd:/bin/sh
mail:x:8:8:mail:/var/mail:/bin/sh
news:x:9:9:news:/var/spool/news:/bin/sh
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:13:proxy:/bin:/bin/sh
www-data:x:33:33:www-data:/var/www:/bin/sh
backup:x:34:34:backup:/var/backups:/bin/sh
list:x:38:38:Mailing List Manager:/var/list:/bin/sh
irc:x:39:39:ircd:/var/run/ircd:/bin/sh
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
libuuid:x:100:101::/var/lib/libuuid:/bin/sh
syslog:x:101:102::/home/syslog:/bin/false
klog:x:102:103::/home/klog:/bin/false
messagebus:x:103:106::/var/run/dbus:/bin/false
polkituser:x:104:108:PolicyKit,,,:/var/run/PolicyKit:/bin/false
hplip:x:105:7:HPLIP system user,,,:/var/run/hplip:/bin/false
avahi-autoipd:x:106:114:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
avahi:x:107:115:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
gdm:x:108:117:Gnome Display Manager:/var/lib/gdm:/bin/false
haldaemon:x:109:118:Hardware abstraction layer,,,:/var/run/hald:/bin/false
pulse:x:110:120:PulseAudio daemon,,,:/var/run/pulse:/bin/false
saned:x:111:123::/home/saned:/bin/false
thunderrd:x:1000:1000:[MY NAME HERE],,,:/home/thunderrd:/bin/bash
statd:x:112:65534::/var/lib/nfs:/bin/false
```

group:
```
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:thunderrd
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:thunderrd
fax:x:21:
voice:x:22:
cdrom:x:24:thunderrd
floppy:x:25:
tape:x:26:
sudo:x:27:
audio:x:29:pulse
dip:x:30:
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:
sasl:x:45:
plugdev:x:46:thunderrd
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
libuuid:x:101:
syslog:x:102:
klog:x:103:
scanner:x:104:
nvram:x:105:
messagebus:x:106:
fuse:x:107:
polkituser:x:108:
ssl-cert:x:109:
lpadmin:x:110:thunderrd
crontab:x:111:
mlocate:x:112:
ssh:x:113:
avahi-autoipd:x:114:
avahi:x:115:
netdev:x:116:
gdm:x:117:
haldaemon:x:118:
admin:x:119:thunderrd
pulse:x:120:
pulse-access:x:121:
pulse-rt:x:122:
saned:x:123:
thunderrd:x:1000:
sambashare:x:124:thunderrd
```



> **heckheck said:**
> In answer to your question on what should you use to mount a drive, try mapping a network drive on the Windows box.  I export top level directories (like /data), so I will give you an example of what works for that.  Use the IP address of the Ubuntu box and the name of the shared folder like this

my /etc/exports on my Ubuntu box 10.100.200.60

```
/data 10.100.200.0/24(rw,no_root_squash,async)
```

What I type in the map network drive window

```
10.100.200.60:/data
```

I use the same username on Windows as I do on Ubuntu.  That username is mapped by the SFU Name mapping application so that it has the correct UID and GID.

If you run into problems where Windows complains along the lines of "Network Path Not Found" check out my post from March 29th, as you problem is likely due to a RDNS lookup by Ubuntu to verify the IP address of the Windows box.

If all else fails, break out Wireshark on the Ubuntu box, and get a capture of the NFS exchange between the two boxes.  That should shed some light on what is or isn't going on.

Hope this helps,

-Jim

Here is my /exports file:
```

/media/FAT32_ARCH 	192.168.0.0/24(rw,no_root_squash,async)
/media/FAH6 	  	192.168.0.0/24(rw,no_root_squash,async)
```

And my fstab:
```

# /etc/fstab: static file system information.
#
# <file system> 			   <mount point>   	  <type>         <options>               <dump>      <pass>

proc                                       	/proc              proc         defaults                    0  		0  

## OPTICAL DEVICES
/dev/scd0                                  	/media/cdrom0      udf,iso9660  user,noauto,exec,utf8       0  		0  



## LINUX PARTITIONS
# /dev/sdb1: system
UUID=8ff92a8e-2609-4619-82b6-ceedae423e93  	/                  ext3         relatime,errors=remount-ro  0  		1  

# /dev/sdb6: rbz_home
UUID=cd4f03a0-8fee-4925-896d-a67039f2a10c  	/home              ext3         relatime                    0  		2  

# /dev/sdb5: swap
UUID=9bc8d43c-ddf8-4643-91a6-24dd3c6ab205  	none               swap         sw                          0  		0  




## STORAGE DRIVES
# /dev/sdc1: SATA 250GB
UUID=4889-5BE5                             	/media/FAT32_ARCH vfat  rw,auto,users,exec,umask=000   	    0 		0  
```

and my mtab:
```

/dev/sdb1 / ext3 rw,relatime,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
/proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
lrm /lib/modules/2.6.27-9-generic/volatile tmpfs rw,mode=755 0 0
/dev/sdb6 /home ext3 rw,relatime 0 0
/dev/mapper/nvidia_dcachege1 /media/FAT32_ARCH vfat rw,nosuid,nodev,umask=000 0 0
securityfs /sys/kernel/security securityfs rw 0 0
rpc_pipefs /var/lib/nfs/rpc_pipefs rpc_pipefs rw 0 0
nfsd /proc/fs/nfsd nfsd rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/thunderrd/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=thunderrd 0 0
```

When I try to map /media/FAT32_ARCH in XP I get the following result:

I input "192.168.0.10:/media/FAT32_ARCH" into the field, where 192.168.0.10 is the fixed IP of the server, 
and /media/FAT32_ARCH is the mount point of /dev/mapper/nvidia_dcachege1, a SATA drive

A small dialog window appears, "Attempting to connect to 192.168.0.10:/media/FAT32_ARCH"

Some time passes, and an error message appears,"The network path 192.168.0.10:/media/FAT32_ARCH could not be found".  Is this the problem with reverse DNS you referred to?

Here's a screenshot in explorer, showing the advertised shares but no contents.[http://www.aoaforums.com/forum/attachments/linux/23463d1230361481-samba-problem-sfu1.png]("http://www.aoaforums.com/forum/attachments/linux/23463d1230361481-samba-problem-sfu1.png")

---

### Post by Jose Catre-Vandis on 2008-12-27
ThunderRd, just to clear up one potential issue, you seem to be trying to export a fat32 directory. Try adding a dirctory from one of your ext3 partitions, like /home and see what happens (syntax will need to include username e.g. xx.xx.xx.xx:/home/username).

Fat32 "should work" but can be problematic. (the whole point of my howto was to enable windows users to access linux shares on linux file systems :))

Also do you have another linux box you could test the network shares with, you could always boot up a live cd, and try it from there. This would just ensure that the server is working correctly (although it does appear to be)

You can also check the server is running correctly by running this command at the terminal on your server
```
rpcinfo -p localhost
```
you should get something like this:
```
program vers proto   port
100000    2   tcp    111  portmapper
100000    2   udp    111  portmapper
100011    1   udp    749  rquotad
100011    2   udp    749  rquotad
100005    1   udp    759  mountd
100005    1   tcp    761  mountd
100005    2   udp    764  mountd
100005    2   tcp    766  mountd
100005    3   udp    769  mountd
100005    3   tcp    771  mountd
100003    2   udp   2049  nfs
100003    3   udp   2049  nfs
300019    1   tcp    830  amd
300019    1   udp    831  amd
100024    1   udp    944  status
100024    1   tcp    946  status
100021    1   udp   1042  nlockmgr
100021    3   udp   1042  nlockmgr
100021    4   udp   1042  nlockmgr
100021    1   tcp   1629  nlockmgr
100021    3   tcp   1629  nlockmgr
100021    4   tcp   1629  nlockmgr
```

and you need to be seeing at least a single entry for each of these: portmapper, nfs and mountd

---

### Post by Jose Catre-Vandis on 2008-12-27
> **heckheck said:**
> I figure it doesn't hurt to cross post a problem I've been having related to NFS and Vista here.  I originally posted this here [http://ubuntuforums.org/showthread.php?t=640760&page=87](http://ubuntuforums.org/showthread.php?t=640760&page=87) but haven't gotten any help yet.  Maybe someone here can help figure it out.

I have recently been experimenting with setting up LDAP on my Linux server to accommodate NFS authentication for Vista, which doesn't have built in UID/GID mapping, unlike the previous Services For Linux 3.5 (SFU) that MS provided for XP. I have followed the steps outlined in the first post by rickyjones, I have gotten a working openLDAP server running. I was able to get Windows Vista Ultimate 64 bit to join the domain I created (home.local), and it seems to be authenticating the LDAP user I created (heck).

I have run into problems getting an NFS exported mount point to mount as a network drive, however. Under Vista, the drive mounts, but I have been unable to get it to mount with any credentials (it mounts as uid -2, gid -2). I have installed Services for NFS and Subsystem for Unix-based Applications. I edited the Services for NFS Properties dialog to enable 'Active Directory domain name' as 'home' as the Identity mapping source. Is this the correct way to way to configure this property? When I try to mount the drive, I am logged into Vista on the 'home domain' as HOME\heck.

I have attached a Wireshark packet trace of an attempt to establish the mapping of the network drive. Here are the details of my network configuration.

Linux Server running Ubuntu 8.04 is named 'heckmedia' and has IP address 10.100.200.60
Vista Ultimate 64 is named 'heckquad' and has IP address 10.100.200.144
LDAP user logged into Vista is 'heck'
LDAP domain is home.local
Vista machine 'heckquad' is using 10.100.200.60 for DNS, and the Linux box is running bind9 as part of the LDAP setup
The exported NFS directory I am trying to mount is 'datatest', and has UID/GID credentials matching the LDAP entry for 'heck' (these ended up being UID 30000, GID 513, which I could see using PHP to query LDAP under Linux)

From the trace, the early part is the booting of Vista, and the logon of HOME\heck. The mount operation starts around timestamp 73.89 sec, packet 512. It seems Vista first tries to use SMB (Samba?) to find the mountpoint, and then some sort of HTTP mounting. When those fail, it tries LDAP, and runs into a problem around packet 559 (73.986471 time) with the bindRequest response, where LDAP in is complaining of invalid credentials (realm changed to 'home'). I see in packet 557 that the realm in the response to the first bindRequest (556) contains a string saying the realm was 'heckmedia', which is the name of the Linux server.
I'm sure there is just something off in the drive mapping process, where the network name of the linux server is being substituted for the realm. I just don't know enough to figure out how to fix it.

Anyway, I thought someone here could shed light on what may be going wrong. I'm at my wits end trying to get this to work, and am about ready to throw in the towel on Vista and go back to XP, where NFS just worked in my network.

Thanks for any help you can provide,

-Jim

Way beyond me heckheck !!

But there may be some help [here]("http://nfs.sourceforge.net/nfs-howto/") and [here]("http://nfs.sourceforge.net/")

---

### Post by ThunderRd on 2008-12-27
> **Jose Catre-Vandis said:**
> ThunderRd, just to clear up one potential issue, you seem to be trying to export a fat32 directory. Try adding a dirctory from one of your ext3 partitions, like /home and see what happens (syntax will need to include username e.g. xx.xx.xx.xx:/home/username).
You are correct, one of the shares is on a FAT32 drive.  However, the path to the other one is /home/thunderrd/FAH6.


> **Jose Catre-Vandis said:**
> 

Also do you have another linux box you could test the network shares with, you could always boot up a live cd, and try it from there. This would just ensure that the server is working correctly (although it does appear to be)

You can also check the server is running correctly by running this command at the terminal on your server
```
rpcinfo -p localhost
```


Alas, I have only one Linux box here.  

Here is the output you requested:
```

thunderrd@OPTERON-185:~$ rpcinfo -p localhost
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp  49180  status
    100024    1   tcp  59087  status
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100021    1   udp  36686  nlockmgr
    100021    3   udp  36686  nlockmgr
    100021    4   udp  36686  nlockmgr
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100021    1   tcp  55079  nlockmgr
    100021    3   tcp  55079  nlockmgr
    100021    4   tcp  55079  nlockmgr
    100005    1   udp  52028  mountd
    100005    1   tcp  43687  mountd
    100005    2   udp  52028  mountd
    100005    2   tcp  43687  mountd
    100005    3   udp  52028  mountd
    100005    3   tcp  43687  mountd

```
And attached is the NFS transaction output from wireshark.  Thanks for your time ;)

EDIT:  OK, I tried to map explorer with 192.168.0.10:/media/FAH6/thunderrd per your instructions.

A small window appeared, attempting to connect...then another small window, saying 
"NFS Login Successful
You are currently logged in as: 
UserName : Q6600\Administrator   [Q6600 is the name of the xp box]
UID : 1000
Primary GID : 1000
Choose yes to accept, no to change the login settings."

I chose yes, and received another dialog: "The mapped network drive could not be created because the semaphore timeout has expired"

If I choose no, I see a dialog about logging in with PCNFS authentication, or as Anonymous user.  Anonymous user is already ticked.  PCNFS asks for a server name [currently blank], a username[currently Q6600/Administrator] and a password.  There is another page as well, with mount options like buffer sizes, initial timeout, and a few others.  I did not  meddle in this dialog at all.

Does that mean something to you?

---

### Post by heckheck on 2008-12-27
> 

Some time passes, and an error message appears,"The network path 192.168.0.10:/media/FAT32_ARCH could not be found".  Is this the problem with reverse DNS you referred to?

Here's a screenshot in explorer, showing the advertised shares but no contents.[http://www.aoaforums.com/forum/attachments/linux/23463d1230361481-samba-problem-sfu1.png]("http://www.aoaforums.com/forum/attachments/linux/23463d1230361481-samba-problem-sfu1.png")

ThunderRD, that sure sounds like the reverse DNS problem I mentioned.  The easiest way to fix this (copied from my previous post) is to try this

> 2. The easiest way to fix the problem is to add entries to the Ubuntu server's /etc/hosts file, so that the Windows clients IP addresses are known to the Ubuntu box. This will suppress the RDNS query, and was my first success. Unfortunately, I like to use DHCP for the Windows boxes. There are ways you could make this work. Use statically assigned DHCP addresses (if you can configure such with your DHCP server), switch to static IP addresses, etc. So for those of you who want the easy fix, here it is. Add a line like this (modified with the correct IP) to your /etc/hosts file

192.168.0.1 OFFICE


Jose also has some great suggestions, to test an EXT2 mount point, and to use a LiveCD to test NFS client mounting with Linux, which should work like a charm, and prove to you that the NFS setup on the server is working fine.

Good luck,

heckheck

If that doesn't work for you, I'll see if I can find some time to look at the packet trace.

---

### Post by ThunderRd on 2008-12-27
> **heckheck said:**
> ThunderRD, that sure sounds like the reverse DNS problem I mentioned.  The easiest way to fix this (copied from my previous post) is to try this



Jose also has some great suggestions, to test an EXT2 mount point, and to use a LiveCD to test NFS client mounting with Linux, which should work like a charm, and prove to you that the NFS setup on the server is working fine.

Good luck,

heckheck

If that doesn't work for you, I'll see if I can find some time to look at the packet trace.

OK, I added the following line to /etc/hosts:
```
192.168.0.10 RBZGROUP
```
Where 192.168.0.10 is the fixed IP of the 'buntu server and RBZGROUP is the name of the windows workgroup.

I then tried to map in explorer:
```
192.168.0.10:/media/FAH6/thunderrd
```
Staying with the ext3 share only, for now, and using the syntax that Jose directed, with /username at the end.

I got an error message, but different this time:
"\\opteron-185\media\FAH6 is not accessible.  You might not have permissions to use this network resource.  Contact the admin...a device attached to the system is not functioning."

I also took a look at this.  It is the contents of a file named /var/lib/nfs/rmtab, and it lists in real time which filesystems actually are mounted by certain clients at the moment, like [/etc/mtab]: 
```

192.168.0.1:/media/FAT32_ARCH:0x00000004
192.168.0.1:/media/FAH6:0x00000005
```

Now, I'm not an expert by any means, but it looks like those mount points are mounted.  I can see them in explorer - but why can't I see the contents?  I'm beginning to feel like everything on the server side is ok.  Perhaps I've done something wrong on the client?  If I get this result when I attempt to map in explorer:
> "NFS Login Successful
You are currently logged in as: 
UserName : Q6600\Administrator   [Q6600 is the name of the xp box]
UID : 1000
Primary GID : 1000
Choose yes to accept, no to change the login settings."

I chose yes, and received another dialog: "The mapped network drive could not be created because the semaphore timeout has expired"

Does this not mean that the server has accepted a login attempt from the client?  [The semaphore timeout is another complication, of course.]

I'll try booting the client with a live CD and see what happens now, while you mull this over... ;)

---

### Post by Jose Catre-Vandis on 2008-12-27
> **ThunderRd said:**
> 
Staying with the ext3 share only, for now, and using the syntax that Jose directed, with /username at the end.


Sorry ThunderRd, I wasn't clear about this.

Your two existing mount point syntaxes were fine and should be in the format:
```
192.168.0.10:/media/FAH6
192.168.0.10:/media/FAT32_ARCH
```

when you use explorer to mount network nfs drives

My suggestion for mounting /home was the only situation where you needed to include your username (or the username of the user logged in on the nfs server)
```
192.168.0.10:/home/thunderrd/"myfiles"
```
so that you could test a linux folder share.

From the output of rcpinfo it looks like nfs server is working OK, so we are getting back to permissions. I am still concerned about trying to serve up a FAT32 partition, so lets focus on the FAH6, which is ext3.

Looks like you need to do some manual mapping of usernames on the XP boxes, in order to line up "Administrator" with "thunderrd". have a read of the howto again to see how this is done.

I get round this by having the same users on both boxes, so on XP I would have user: jose pass: abcd and on the nfs server I would have user: jose and pass: abcd, you can do this for each of the main users on the XP boxes and set up a corresponding user on the nfs server.

Can't find anything about semaphore timeouts?

Also what are the file permission settings on the files on the two shares (check this on the server)
```
cd /media/FAT32_ARCH
ls -al
```

If the files have "---" as the last three permissions, (e.g. drwx r-- ---)you won't have any access if you are not the user.

Also, just in case you didn't know, you don't have to be logged into the nfs server for it to work, just boot up to a command prompt or gui login. However, the linux box will still be looking for user rights and permissions :)

---

### Post by ThunderRd on 2008-12-27
> **Jose Catre-Vandis said:**
> 
Your two existing mount point syntaxes were fine and should be in the format:
```
192.168.0.10:/media/FAH6
192.168.0.10:/media/FAT32_ARCH
```
OK, I haven't changed anything there.

> **Jose Catre-Vandis said:**
> 
From the output of rcpinfo it looks like nfs server is working OK, so we are getting back to permissions. I am still concerned about trying to serve up a FAT32 partition, so lets focus on the FAH6, which is ext3.

Looks like you need to do some manual mapping of usernames on the XP boxes, in order to line up "Administrator" with "thunderrd". have a read of the howto again to see how this is done.
I went back through the mapping setup in SFU, and started from scratch.  I turned off simple maps, and mapped windows user "Q6600/Administrator" to UNIX user "thunderrd", this yielded the domain PCNFS, and UID 1000.  I did exactly the same in the Group maps, mapping "Q6600/Administrator" to "thunderrd".

I then tried to map a share, and interestingly enough, this time it allowed me to finish the mapping of:
"FAH6 on '192.168.0.10\media' in explorer.  So progress was made, there was no error message blocking the mapping from completion.  However, I still have an empty right-hand pane when I try to view the contents of /FAH6.

> **Jose Catre-Vandis said:**
> 
Can't find anything about semaphore timeouts?
Still looking ;)

> **Jose Catre-Vandis said:**
> 
Also what are the file permission settings on the files on the two shares

```

thunderrd@OPTERON-185:~$ cd /media/FAH6
thunderrd@OPTERON-185:/media/FAH6$ ls -al
total 8
drwxr-xr-x 2 root root 4096 2008-12-24 21:08 .
drwxr-xr-x 5 root root 4096 2008-12-28 02:48 ..
thunderrd@OPTERON-185:/media/FAH6$ cd /media/FAT32_ARCH
thunderrd@OPTERON-185:/media/FAT32_ARCH$ ls -al
total 52
drwxrwxrwx  4 root root 16384 1970-01-01 07:00 .
drwxr-xr-x  5 root root  4096 2008-12-28 02:48 ..
drwxrwxrwx 13 root root 16384 2008-12-22 22:10 file_archive
drwxrwxrwx  5 root root 16384 2008-12-26 18:33 home_backup
thunderrd@OPTERON-185:/media/FAT32_ARCH$ 

```

If I can get /FAH6 to work properly, I have no problem with moving the data off the FAT32 drive, formatting it to ext3, and moving the data back onto it.  It's only in FAT32 because it came from an XP box and I was too lazy to do it; and SAMBA worked.  Although too slowly, hence my move to NFS, hopefully.]

---

### Post by Jose Catre-Vandis on 2008-12-27
Do you have any files in FAH6? doesn't look like it.

However, Aha a possibility!

All your files on your shares appear to owned by root in the group root. try getting some files in there that are owned by thunderrd and see what happens. An example:
```
drwxrwxrwx 4 thunderrd thunderrd 12560 2008-12-27 21:08 myfile
```

You can use the chmod, chown and chgrp commands to do this recursively on directories:
```
sudo chown -R thunderrd /media/FAH6
sudo chgrp -R thunderrd /media/FAH6  #(assumes user thunderrd is in group thunderrd)
sudo chmod -R 777 /media/FAH6
```

This should give you this:
```
drwxrwxrwx 4 thunderrd thunderrd 12560 2008-12-27 21:08 myfile
```

Not the most secure, but for testing on an internal LAN you can work back from it.

---

### Post by ThunderRd on 2008-12-27
> **Jose Catre-Vandis said:**
> Do you have any files in FAH6? doesn't look like it.

However, Aha a possibility!

All your files on your shares appear to owned by root in the group root. try getting some files in there that are owned by thunderrd and see what happens. An example:
```
drwxrwxrwx 4 thunderrd thunderrd 12560 2008-12-27 21:08 myfile
```

You can use the chmod, chown and chgrp commands to do this recursively on directories:
```
sudo chown -R thunderrd /media/FAH6
sudo chgrp -R thunderrd /media/FAH6  #(assumes user thunderrd is in group thunderrd)
sudo chmod -R 777 /media/FAH6
```

This should give you this:
```
drwxrwxrwx 4 thunderrd thunderrd 12560 2008-12-27 21:08 myfile
```

Not the most secure, but for testing on an internal LAN you can work back from it.

I can't believe what a dumbazz I am.

In my confusion since abandoning SAMBA, I made a mountpoint /media/FAH6.  Why?  I don't know.  Maybe because there is a mountpoint for the FAT32 SATA drive at /media/FAT32_ARCH.  I'm not sure why I did it, but I did.  And I have been using that as the path to the share...when you said that it looked like there were no files in there, you got me thinking...and you were absolutely right.  The correct path to the share is /home/thunderrd/FAH6...and when I changed the entry in /etc/exports...well, I think you know the rest.

OK. now I have explorer mapped to display "FAH6 on '192.168.0.10\home\thunderrd'", and I can see the share properly, and the contents as well.  I test file copy both to and from the share from the XP box.  With a 250MB file, file copy to the share takes about 13 secconds.  However, copying the same file from the share to XP is a different story.  It was unbearably slow, copying about 5% of the file in the first minute, and then completely stalling.  It doesn't seem to matter what file or what destination on the XP box I copy to, it just stalls and goes no further, gradually XP stating that it needs 95 minutes to finish copying, and hard locking explorer in the process.  This is with the gateway firewall on 192.168.0.1 set to allow all in both directions for the purposes of this test.

Even files as small as 4MB would not complete a copy operation from the server to the client.

Any ideas what I should look at?

---

### Post by Jose Catre-Vandis on 2008-12-28
Out of the frying pan into the fire!

Try adjusting your exports file. I use the following for each of my shares:
```
/media/myshare 192.168.0.1/24(rw,no_root_squash,asynce,no_subtree_check)
```

see if that makes any difference (don't forget to re-export the exports and restart the nfs server)

May also be something to do with block/packet sizes but all I can see is edits on the client side, which we do not have with Windows

Are you using a wireless LAN? (NFS sometimes has problems with this, and gets confused sending and receiving packets, depends on the wireless adapters etc)

Also (you may have fixed this) there is no need to have a mount /media/FAH6 that points to /home/thunderrd/FAH6, just use /home/thunderrd/FAH6 in your exports file.

Again test if this behaviour is present when using a linux client so we can see if it is a sefver/network issue or a windows one

Also have a look in the control applet for Services for Unix Adminstration. Click on Client for NFS and choose the Performance tab. My settings are as follows (the defaults I think)

Transport Protocol          UDP
Mount type                  Soft
Max tries                    1
Interval                     0.8
Read buffer                  32
Write buffer                 32

I have never played with these to see what effect they have.

---

### Post by ThunderRd on 2008-12-28
> **Jose Catre-Vandis said:**
> Out of the frying pan into the fire!

Try adjusting your exports file. I use the following for each of my shares:
```
/media/myshare 192.168.0.1/24(rw,no_root_squash,asynce,no_subtree_check)
```

see if that makes any difference (don't forget to re-export the exports and restart the nfs server)
I have the same:
```

/home/thunderrd/FAH6    192.168.0.0/24(rw,no_root_squash,async,no_subtree_check) 

/media/ext3_REPO  	192.168.0.0/24(rw,no_root_squash,async,no_subtree_check) 
```


> **Jose Catre-Vandis said:**
> 
Are you using a wireless LAN? (NFS sometimes has problems with this, and gets confused sending and receiving packets, depends on the wireless adapters etc)
No, it's a wired ethernet connection.

> **Jose Catre-Vandis said:**
> 
Also (you may have fixed this) there is no need to have a mount /media/FAH6 that points to /home/thunderrd/FAH6, just use /home/thunderrd/FAH6 in your exports file.

Done already.

> **Jose Catre-Vandis said:**
> 
Again test if this behaviour is present when using a linux client so we can see if it is a sefver/network issue or a windows one.
I'd like to do that.  I booted the client box with a live distro cd...but couldn't figure out what to do there to check it out; I haven't used the live cd much and I was a bit confused.  Any tests you'd like to see me do there? 

> **Jose Catre-Vandis said:**
> 
Also have a look in the control applet for Services for Unix Adminstration. Click on Client for NFS and choose the Performance tab. My settings are as follows (the defaults I think)
Already done, all at defaults.

At this point I have two shares as you see in my exports. The new one, ext3_REPO, is a ext3 drive onto which I intend to copy over the files from that FAT32 drive. I put some test files onto it.  It is /dev/sdc1, and it mounts into /media/ext3_REPO.  From there I advertise it in /etc/exports.

I do have a question here, though.  Should it be mounted as ext3, or nfs in fstab?  I can do it either way, but I'm not sure what's correct.  Take a look:
```
# /etc/fstab: static file system information.
#
# <file system> 			   <mount point>   	  <type>         <options>               <dump>      <pass>

proc                                       	/proc              proc         defaults                    0  		0  

## OPTICAL DEVICES
/dev/scd0                                  	/media/cdrom0      udf,iso9660  user,noauto,exec,utf8       0  		0  



## LINUX PARTITIONS
# /dev/sdb1: system
UUID=8ff92a8e-2609-4619-82b6-ceedae423e93  	/                  ext3         relatime,errors=remount-ro  0  		1  

# /dev/sdb6: rbz_home
UUID=cd4f03a0-8fee-4925-896d-a67039f2a10c  	/home              ext3         relatime                    0  		2  

# /dev/sdb5: swap
UUID=9bc8d43c-ddf8-4643-91a6-24dd3c6ab205  	none               swap         sw                          0  		0  




## STORAGE DRIVES

#### /dev/sdc1: SATA 160GB
#note to self: if the uuid syntax is used to mount as ext3, first create the mount point in /media
UUID=d02c821d-ea3f-4aae-8446-ee6589683628	/media/ext3_REPO  ext3  	rw,users,exec		    0 		0

#note to self: if this nfs syntax is used, it will automatically create its own mountpoint in /media on demand.  Why? Dunno.
#192.168.0.10:/dev/sdc1	     /media/ext3_REPO     nfs        rw,users,rsize=32768,wsize=32768,hard,intr,nfsvers=3,noatime,nodev,asynch,lock    0         0
```

In the client box, I can see the shares in explorer, and I can see the files within them, but explorer is behaving very erratically, locking up every time I attempt a file operation in either direction.  I really need explorer to work properly, and locking up and stalling the file movements is far worse than anything SAMBA threw at me.  SAMBA was a bit irregular, a bit vague, but it didn't freeze up my throughput.  I thought it was somewhat slow, but this is ridiculous. ;)

I am certainly farther along than I was before, thanks to you, but I have to get to the bottom of why I can't copy anything.  I still have some gas in the tank and I don't want to give up and go back to SAMBA...

---

### Post by Jose Catre-Vandis on 2008-12-28
On the server in fstab you mount as ext3, you would only use nfs if you were creating a mount point for a share on a client (what you are actually doing is behaving like a client on the server, and mounting the share!). So you are OK as you are.

Not sure why your explorer is giving you so much trouble, and haven't found out much about improving speed (one way or the other).

Done a bit of research on alternatives for you though, depending on what you are ultimately trying to achieve.

You could use an open source program called **winscp**, which is a bit like an ftp program but works like explorer. you need to have openssh server running on your linux box, but then winscp gives you a pretty seamless file sharing experience. However, say you wanted to view a film (avi) on your XP machine and it was stored on your linux box, you would have to download the whole thing onto your XP machine before you could watch it. Winscp has a nice clear up facility to remove donwloaded files next time round. Still worth a try regardless, its joined my Windows freeware repository.

For real seamlessness and streaming using ssh you 'can' do it by hacking around in XP, but I also found a shareware proggie called **sftpdrive**, that mounting your ssh shares just like a network drive. you get a six week trial period so worth a look. I really like it, but won't be shelling out the $39 or whatever as nfs is working OK here, at the moment. 

Also, see this thread:[here]("http://ubuntuforums.org/showthread.php?t=218630&highlight=ssh+network+share")

and continuing with the idea of using ssh have a look here [at dokan]("http://dokan-dev.net/en/docs/dokan-sshfs-readme/") which promises sshfs for windows for free.

Keep pluggin away :)

---

### Post by Jose Catre-Vandis on 2008-12-28
> I'd like to do that. I booted the client box with a live distro cd...but couldn't figure out what to do there to check it out; I haven't used the live cd much and I was a bit confused. Any tests you'd like to see me do there?

Boot the live cd
Set up as an nfs client following the malco howto (portmap nfs-common)
manually try mounting the nfs shares (mount 168.192.0.10:/files /media/files....)
test traffic in both directions, try copy and move, they seem to work at different rates.

My speed, though not brilliant (takes a couple of minutes to shift a 1.4GB file to/from the share), is about the same in both directions, and gives the  same performance for small, and large files (not same speed for small and large!)

---

### Post by ThunderRd on 2008-12-29
I have checked everything over again; still the same slow speeds. locking up explorer. I booted the client from a Knoppix cd I had around, and had the same result, so I'm thinking the server isn't right.  Tonight I'll make a new install of 8.10 n the server; I have a separate /home partition so it won't be too tedious.

Then tomorrow I'll try to do this again, from scratch.  Maybe the results will be better now that I know my way around a bit better.    If I'm not successful I'll take a look at the options you gave me.  Then I'll report back here...I'm sure I'll need something ;)

You've been really helpful.  Thanks.

---

### Post by finkas on 2009-06-11
Hi,

just as a note, I found out that unfs3 does not interoperate with Windows UNIX Services properly. There are two user-space NFS daemons available in Ubuntu - unfs3 and nfs-user-server - and it seems you will have to choose the latter one if you want to mount the shares from Windows. unfs3 works fine with another Ubuntu machine, but my Windows XP Professional SP3 stalls if I try to mount the shares through unfs3 (aka. unfsd).

Of course, this only applies if you need to use the user-space NFS daemon as opposed to nfs-kernel-server, for some reason.

---

### Post by Jose Catre-Vandis on 2009-06-11
Have a good read through the whole thread first, this might give you some pointers (it could be one of many things!) If you can't get it going then post back.

You might also want to try dokan & sshfs, which is a somewhat easier solution:

[http://ubuntuforums.org/showthread.php?t=1027820](http://ubuntuforums.org/showthread.php?t=1027820)

---

### Post by rgl2020 on 2009-06-29
I know this thread is about XP, but it looks like multiple people with Vista looks at it for help as I am one of them.  I finally found through hours of searching how to fix the Gid and Uid problem with Vista and nfs.  Here's the link to the fix.

[http://forum.qnap.com/viewtopic.php?f=13&t=13054]("http://forum.qnap.com/viewtopic.php?f=13&t=13054")

Hopefully it'll save people time since I was extremely frustrated for hours until I found this.

---

### Post by bodhi.zazen on 2009-06-29
Thank you for the link rgl2020.

I have it book marked , although I run a Samba server now and no Windows (XP or Vista).

---

### Post by LiLoather on 2009-07-03
Needing, as usual, to do the impossible immediately I stumbled across this thread as a response to a search but unhappily don't have time to devote the study to all nine pages that would be necessary to comprehend it.

I'd like to offer some spare GB on a server for remote storage for a dozen or so subscribers.

The almost ideal solution would be the i-bays system of the SME server, but:

     a) I prefer Debian and would rather use the Ubuntu Server for everything else, and
     b) the users need to have control both of access to their 'boxes' and of encryption of their shares so that their 'box' is locked or private even against the sysadmin.

Thus I need a way to create 'storage boxes' of a few GB, password protected and cryptable by the owner, easily accessible over a network by Windows users, even by mapping network shares.

Are the answers in this thread or is there another, off-the-shelf, way of doing it?

Thanks.

---

### Post by Jose Catre-Vandis on 2009-07-03
@ LiLoather

This is one way, but there are others:

Samba (should offer transparent sharing for windows boxes

sshfs using Dokan ([see my tut on this]("http://ubuntuforums.org/showthread.php?t=1027820"))

ftp?

scp?

---

### Post by LiLoather on 2009-07-07
> **Jose Catre-Vandis said:**
> @ LiLoather

This is one way, but there are others:

Samba (should offer transparent sharing for windows boxes

sshfs using Dokan ([see my tut on this]("http://ubuntuforums.org/showthread.php?t=1027820"))

ftp?

scp?


Thanks Jose.  I'll give Dokan a look. Anything with a tutorial - better yet an idiot's guide - is worth its weight in gold!

---

### Post by kooldino on 2009-12-22
I'm getting a "path too deep" error when I go to copy files.  Apparently this means that it's a permission error.  If I chmod a file to 777, I don't get this error.

However, I get this error while trying to access files that I own and have permissions to according to my user mapping.

---

### Post by kooldino on 2009-12-28
> **kooldino said:**
> I'm getting a "path too deep" error when I go to copy files.  Apparently this means that it's a permission error.  If I chmod a file to 777, I don't get this error.

However, I get this error while trying to access files that I own and have permissions to according to my user mapping.

I found more on this issue...it doesn't seem to have anything to do with permissions, and EVERYTHING to do with file size.  If I copy a file that's a few kilobytes, it will work perfectly.  If it's a few megabytes, the copy will time out and tell me that "The semaphore timeout period has expired".

---

### Post by biro on 2011-01-21
> **kooldino said:**
> I found more on this issue...it doesn't seem to have anything to do with permissions, and EVERYTHING to do with file size.  If I copy a file that's a few kilobytes, it will work perfectly.  If it's a few megabytes, the copy will time out and tell me that "The semaphore timeout period has expired".

Hi kooldino,
did you solve this issue.

I now have the same issue, even though I didn't have it at first.
Before I could move large files around, but now, a couple of  hours after the first installation of SFU, only small sized ones could be copied
I did play with permission and after that I couldn't have it right anymore.
It's driving me crazy ;{

Thanks for any help...

---

