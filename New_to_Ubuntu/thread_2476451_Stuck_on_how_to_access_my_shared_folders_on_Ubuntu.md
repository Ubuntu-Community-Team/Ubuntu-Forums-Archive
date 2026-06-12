---
title: "Stuck on how to access my shared folders on Ubuntu erver on my Windows 10 PC"
date: 2022-06-26
forum: New to Ubuntu
---

### Post by pcman51 on 2022-06-26
Hey Everyone. Help I've tried everything. Using Ubuntu 22.04 and all is setup and working well,...  I think?
Samba is installed, I've shared the Folders from the simple web GUI with no permissions (and With permissions, trying to make it work) required.
And I followed by several Tutorials on YouTube, etc.. Sure seemed easy enough.. But Ughh not happening. LoL

I have both a Windows Server, and OpenMediaVault6 running and all have  shared folders accessible on everything in our home , PC's, Android,  FireTV's, Etc. 
So something I've missed on the Windows 10 PC, as several  Shared Folders show up from the Ubuntu server (Called "server1" at 192.168.0.30).
I can see the shared folders in my Windows 10 PC, but I can't access them.
I am denied access from lack of  permissions. Please see the Message attached.

I know this is likely very elementary to many here, and I'm pretty Windows Network Savvy, but this has me at wits end. 

Thanks in advance for any help I truly appreciate it. And please keep it simple for me as I'm just getting started on Linux.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290653&stc=1[/IMG]

---

### Post by Tadaen_Sylvermane on 2022-06-26
Ubuntu doesn't have a simple web gui for server stuff to my knowledge. I'd be interested to see what you are using. That alone is suspect to me.

---

### Post by SeijiSensei on 2022-06-27
Please run "testparm" from the command prompt in a terminal and copy the results here inside [noparse]```

```[/noparse] tags.

Here's mine :
```

# Global parameters
[global]
        domain master = Yes
        interfaces = lo eth0 192.168.100.0/24 10.1.1.0/24
        log file = /var/log/samba/log.%m
        max log size = 50
        os level = 65
        preferred master = Yes
        security = USER
        server min protocol = SMB2
        server string = Samba Server Version %v
        wins support = Yes
        workgroup = MYWORKGROUP
        idmap config * : backend = tdb
        cups options = raw
        hosts allow = 127. 192.168.100. 10.1.1.  <= *192.168.100.0/24 is my local network; I have some other machines on 10.1.1.0/24*.

[homes]
        comment = Home Directories
        read only = No

[printers]
        browseable = No
        comment = All Printers
        path = /var/spool/samba
        printable = Yes

[raid]
        path = /media/raid
        read only = No

```

The only GUI management tool I've used on Linux servers is webmin.

---

### Post by pcman51 on 2022-06-27
So to be clear. I'm here as a beginner to Linux, and willing to do what it takes to get my installation working.
SO think you all for any suggestions..

I'm using Ubuntu 22.04 and indeed it has a GUI interface to share folders on the network.
Simply "Right Click" on a given folder and the GUI interface come up, allowing many features, very much like Windows does.
When I first clicked the choice to share a folder I was in, it asked if I wanted to install SAMBA and I said yes.
It then asks what rights I wanted for all user, I chose can change, add or delete data in the folder.
Since I am very savvy with Windows this was very much appreciated vs the complicated command lines experienced Linux users are used to.

But I've still not been able to access the shared folder from Windows.
In the reverse I can access my shared Windows folders and copy and paste files to any folder in Ubuntu.

Thinking I'll just delete the entire installation and start from scratch, as this seems overly complicated at this point.
Yeah, I know everything is easy once you know it. SO I'LL HOLD OUT and MAYBE someone will assist here.. Thank you in advance..

My intention was to have a Server that runs XRDP for multiple Thin Clients.. And That It Does very well.
And also to share Folders across my Network, and Sadly (SO FAR) It does not do that..

But its all a Learning process, and That's why I'm here..

---

### Post by pcman51 on 2022-06-27
OK.. I just noticed this.. OK I'll get on this tonight and post my findings..

PS: I did install WebMin and somewhat comfortable using it, however it still won't fix the problem.

I think your idea of running "testparm" from terminal is a great idea.. Thank You Sir !!

---

### Post by pcman51 on 2022-06-27
[B][SIZE=2]I'll likely be embarrassed at the garbage in my obviously failed setup. LOL
But here ya go...  Ughh :o
So if there is a way to just delete this mess, I'll sure follow your directions.. Thank You 

# Global parameters
[global]
    log file = /var/log/samba/log.%m
    logging = file
    map to guest = Bad User
    max log size = 1000
    obey pam restrictions = Yes
    pam password change = Yes
    panic action = /usr/share/samba/panic-action %d
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    passwd program = /usr/bin/passwd %u
    server role = standalone server
    server string = %h server (Samba, Ubuntu)
    unix password sync = Yes
    usershare allow guests = Yes
    idmap config * : backend = tdb
    valid users = rdpadmin remoteuser1 pcman rdp1 @sudo @xrdp
    write list = rdp1 rdpadmin remoteuser1 pcman xrdp @rdp1 @rdpadmin @remoteuser1 @pcman @xrdp


[printers]
    browseable = No
    comment = All Printers
    create mask = 0700
    path = /var/spool/samba
    printable = Yes
    read only = Yes


[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
    read only = Yes


[File_Share]
    guest ok = Yes
    path = /home
    valid users = remoteuser1
    write list = @remoteuser1


[PublicShare]
    path = /home/public
    write list = remoteuser1 @remoteuser1


[media80gb]
    path = /media/rdpadmin/80GB-Sata
[/SIZE][/B]

---

### Post by pcman51 on 2022-06-27
To keep it simple for now I'd be glad for now to share just one folder "Shared Folder" and (For now anyway) to access it by my network Windows PC .
And also using XRDP with the user name "rdpadmin"  this will also be my Main Administrator user.

Oh I want to learn to use this small SATA drive for shared data.. **[SIZE=2]path = /media/rdpadmin/80GB-Sata[/SIZE]**

Hope this makes sense .. Thanks so much..

---

### Post by Morbius1 on 2022-06-28
> I'm using Ubuntu 22.04 and indeed it has a GUI interface to share folders on the network.
Simply "Right Click" on a given folder and the GUI interface come up, allowing many features, very much like Windows does.
When I first clicked the choice to share a folder I was in, it asked if I wanted to install SAMBA and I said yes.
It then asks what rights I wanted for all user, I chose can change, add or delete data in the folder.
Please post the output of this command so we can see what you shared and how you shared it:
```
net usershare info --long
```

This will not work:
> [media80gb]
path = /media/rdpadmin/80GB-Sata
Well ... it will not work as I think you intended.

You have a [global] valid users list that allows a whole mess of users access to this share but in fact only one user will gain access and that's rdpadmin.

You can fix that by adding a line to that share definition:
```
force user = rdpadmin
```
And then restarting smbd:
```
sudo service smbd restart
```

Note: You can create samba shares two different ways: By editing smb.conf and by using the file manager GUI ( called a usershare ). Problems arise when you share a given folder using both methods at the same time so it should be avoided.

---

### Post by pcman51 on 2022-06-28
Thank You Morbius1..

And I think I got overly ambitious with adding users and shared folders. 
It was to easy to press the options in the GUI interface. So I'm lost in the mess I've created.
Now I find that rdpadmin does not have full rights to share a folder, nor does any other user, rdpuser1, pcman, remoteuser1.
And if I try an error says "You do not have permissions to share a folder"

I'll play some more with your suggestions of, 
net usershare info --long

force user = rdpadmin 

And thinking I should start fresh here, with a totally new install ?

That way keep it simple, one user = rdpadmin, one shared folder ?

But first I'll play with it more and post my findings with  net usershare info --long  command..

Thanks so much..

---

### Post by pcman51 on 2022-06-28
Here's the UserShare Info you requested.. Sure Looks like a big mess.. Ughh LoL

QUESTION: Where is the GLOBAL Valid User List and how do I add "force user = rdpadmin" to it?  Thanks again..

$ net usershare info --long
info_fn: file /var/lib/samba/usershares/testshare is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[Pictures]
path=/home/remoteuser1/Pictures
comment=
usershare_acl=S-1-1-0:F,
guest_ok=y

info_fn: file /var/lib/samba/usershares/sharefolder is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[Downloads]
path=/home/pcman/Downloads
comment=
usershare_acl=S-1-1-0:F,
guest_ok=y

info_fn: file /var/lib/samba/usershares/shared is not a well formed usershare file.
info_fn: Error was Path is not a directory.
info_fn: file /var/lib/samba/usershares/netshare is not a well formed usershare file.
info_fn: Error was Path is not a directory.
info_fn: file /var/lib/samba/usershares/ubuntushare is not a well formed usershare file.
info_fn: Error was Path is not a directory.
info_fn: file /var/lib/samba/usershares/networkshare is not a well formed usershare file.
info_fn: Error was Path is not a directory.
info_fn: file /var/lib/samba/usershares/documents is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[thinclient_drives]
path=/home/remoteuser1/thinclient_drives
comment=
usershare_acl=S-1-1-0:F,
guest_ok=y

info_fn: file /var/lib/samba/usershares/adult is not a well formed usershare file.
info_fn: Error was Path is not a directory.

---

### Post by Morbius1 on 2022-06-28
>  And thinking I should start fresh here, with a totally new install ?


There are a number of things working against you in Ubuntu 22.04 but there is no need to do a reinstall because of samba. You can reset it however:

[1] Create a backup of your smb.conf:
```
sudo mv /etc/samba/smb.conf /etc/samba/smb.conf.bak
```
[2] Copy a backup of the default smb.conf to the working location:
```
sudo cp -a /usr/share/samba/smb.conf /etc/samba/
```
[3] Edit the newly restored default /etc/samba/smb.conf and at the bottom of the file add this:
```
[Downloads]
path = /home/pcman/Downloads
read only = no
guest ok = yes
force user = pcman

```
[4] Go to /var/lib/samba/usershares and delete every file you find in that directory.

[5] Now restart samba:
```
sudo service smbd restart
```

We can make other shares with different requirements but I would suggest starting with this one simple share first.

---

