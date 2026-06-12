---
title: "File sharing with Samba and Mac"
date: 2012-11-25
forum: New to Ubuntu
---

### Post by worldwidejoe on 2012-11-25
Hello all, thank you for reading my post.  Fresh install of Ubuntu 10.04, I'm trying to share a directory from my Ubuntu 10.04 to a Mac 10.6.8

I installed the Samba package from the Ubuntu Software Center, then right clicked on my /home/"user"/Music folder and selected the checkbox to share it.  I got an alert about changing the permissions to which I agreed, save and exit. 

On my Mac 10.6.8,  I can go File > Connect to Server > and enter the ip of my Ubuntu machine.  I am asked for a username and password but they are rejected.  If I try to log in as a Guest, it first shows me the Music share, but when I try to connect it says Guest Account not allowed.

I looked in the /etc/samba/smb.conf file and it is not the one being used to share my folder as there is no Music share definition.  Neither is the one located in /usr/share/samba.

If I go to System > Preferences > Personal File Sharing Preferences :   It says This feature cannot be enabled because the required packages are not installed.  

Here is the output of:  net usershare info

```
user@computer:~$ net usershare info
[music]
path=/home/"user"/Music
comment=
usershare_acl=Everyone:F,
guest_ok=n

user@computer:~$

```And the output of:  testparm -s

```
user@computer:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No
    browsable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
user@computer:~$ 
```

So how is the Mac seeing the share?  Is there a hidden config file somewhere?


Stuck here, so thank you for any help with this.  Cheers

---

### Post by bab1 on 2012-11-25
> **worldwidejoe said:**
> Hello all, thank you for reading my post.  Fresh install of Ubuntu 10.04, I'm trying to share a directory from my Ubuntu 10.04 to a Mac 10.6.8

I installed the Samba package from the Ubuntu Software Center, then right clicked on my /home/"user"/Music folder and selected the checkbox to share it.  I got an alert about changing the permissions to which I agreed, save and exit. 

On my Mac 10.6.8,  I can go File > Connect to Server > and enter the ip of my Ubuntu machine.  I am asked for a username and password but they are rejected.  If I try to log in as a Guest, it first shows me the Music share, but when I try to connect it says Guest Account not allowed.

I looked in the /etc/samba/smb.conf file and it is not the one being used to share my folder as there is no Music share definition.  Neither is the one located in /usr/share/samba.

If I go to System > Preferences > Personal File Sharing Preferences :   It says This feature cannot be enabled because the required packages are not installed.  

Here is the output of:  net usershare info

```
user@computer:~$ net usershare info
[music]
path=/home/"user"/Music
comment=
usershare_acl=Everyone:F,
guest_ok=n

user@computer:~$

```And the output of:  testparm -s

```
user@computer:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No
    browsable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
user@computer:~$ 
```

So how is the Mac seeing the share?  Is there a hidden config file somewhere?


Stuck here, so thank you for any help with this.  Cheers

Non-root user created shares (usershares) are created at /var/lib/samba/usershares.  The admin user can edit the /etc/samba/smb.conf file to configure the 2 daemons (processes) that run Samba (smbd and nmbd) and create shares.  

If you don't grant access to everyone then guests aren't allowed.  Look at the share definition you provided again```
[music]
path=/home/"user"/Music
comment=
[B][COLOR="Red"]usershare_acl=Everyone:F,[/COLOR]
[COLOR="Red"]guest_ok=n[/COLOR][/B]
```

To allow specific users to be able to access the shares, I believe you need to add them as Samba users on the machine that is serving the shares and make sure they have permissions set on the shared folders.  

If you are going to do that you might as well configure the shares in the smb,.conf file too.  See [**_[COLOR="Blue"]here[/COLOR]_**]("http://www.jonathanmoeller.com/screed/?p=3608") for a good tutorial.

---

### Post by worldwidejoe on 2012-11-26
Thank you very much for your reply BAB1.  Using your post and these 2 others, I've gotten the share to work. 

[http://ubuntuforums.org/showthread.php?t=1501320](http://ubuntuforums.org/showthread.php?t=1501320)
[http://www.jonathanmoeller.com/screed/?p=1590](http://www.jonathanmoeller.com/screed/?p=1590)

I could still could use a few more pointers if possible.

There seems to be two methods of using samba to share directories in Ubuntu, Nautilus-share, which is the right-click and select the Sharing checkbox method, and Classic-share where you manually edit the /etc/samba/smb.conf file.  

My /var/lib/samba directory is empty.  

I used Nautilus to browse to the shared folder and right click - UNCHECK the sharing checkbox.  Then I manually edited my /etc/samba/smb.conf file and created my share.  

```

[Music]
path = /home/"user"/Music
availble = yes
valid users = "user"
read only = no
browseable =  yes
public = yes
writable = yes

```I'm still a bit confused as to why my setup works though because in the link you (BAB1) provided, it says: 

> 
It’s important to realize about Samba is that it stores its own set of user accounts, separate from the main accounts, in the /etc/samba/smbpasswd file.
I don't have an /etc/samba/smbpasswd file.  I didn't create a separate samba user.  But I did set a samba password for an existing user:

```

sudo smbpasswd -a "user"

```After doing that and restarting samba, I could connect from my Mac.

In my share definition I have:

```

valid users = "user"

```If I haven't created a separate samba user, how is samba verifying aginst a main user account?  The other thing that I would like to have is for the share to show up in the Finder on the Mac instead of having to connect manually.  

Again, thank you for your reply and help.

---

### Post by bab1 on 2012-11-26
> **worldwidejoe said:**
> Thank you very much for your reply BAB1.  Using your post and these 2 others, I've gotten the share to work. 

[http://ubuntuforums.org/showthread.php?t=1501320](http://ubuntuforums.org/showthread.php?t=1501320)
[http://www.jonathanmoeller.com/screed/?p=1590](http://www.jonathanmoeller.com/screed/?p=1590)

I could still could use a few more pointers if possible.

There seems to be two methods of using samba to share directories in Ubuntu, Nautilus-share, which is the right-click and select the Sharing checkbox method, and Classic-share where you manually edit the /etc/samba/smb.conf file.  

My /var/lib/samba directory is empty.  

I used Nautilus to browse to the shared folder and right click - UNCHECK the sharing checkbox.  Then I manually edited my /etc/samba/smb.conf file and created my share.  

```

[Music]
path = /home/"user"/Music
availble = yes
valid users = "user"
read only = no
browseable =  yes
public = yes
writable = yes

```I'm still a bit confused as to why my setup works though because in the link you (BAB1) provided, it says: 

I don't have an /etc/samba/smbpasswd file.  I didn't create a separate samba user.  But I did set a samba password for an existing user:

```

sudo smbpasswd -a "user"

```After doing that and restarting samba, I could connect from my Mac.

In my share definition I have:

```

valid users = "user"

```If I haven't created a separate samba user, how is samba verifying aginst a main user account?  The other thing that I would like to have is for the share to show up in the Finder on the Mac instead of having to connect manually.  

Again, thank you for your reply and help.

The samba user databases are at /var/lib/samba.  They are the ones with the .tdb extension (trivial data base).  You can see a listing of all samba users with this```
sudo pdbedit -L
```  

You did create a Samba user with the command *smbpasswd -a*.  See ```
man smbpasswd
```
Specifically ```
 When run by root, smbpasswd allows new users to be added and deleted in
       the smbpasswd file, as well as allows changes to the attributes of the
       user in this file to be made. When run by root,
        smbpasswd accesses the local smbpasswd file directly, thus enabling
       changes to be made even if smbd is not running.

```

If you have a functioning LOCAL LAN DNS set up you should see the shares with your MAC.  If not then you need to broadcast the netbios name.  Do you have LOCAL LAN DNS set up?  We are NOT talking about Internet DNS here, only DNS for local LAN machines.

I do not have any experience with MAC but I have heard that the latest OSX does not use Samba for CIFS sharing.  You might post on the Apple forums if this is an issue.

---

### Post by worldwidejoe on 2012-11-28
Thank you very much for a perfect explanation.

> 
You did create a Samba user with the command *smbpasswd -a*.  See man smbpasswd.
I do not have a local DNS set up so seeing the ip address of the samba server instead of the hostname is fine.  

I originally chose samba to share with a Mac and a Windows computer which is not yet on site.  I just found out today that the windows computer will not be used at all, it will only be Mac's connecting to my Ubuntu system.  Should I skip samba and try NFS or CIFS?  

Thank you again for the help, cheers.

---

### Post by bab1 on 2012-11-29
> **worldwidejoe said:**
> Thank you very much for a perfect explanation.

I do not have a local DNS set up so seeing the ip address of the samba server instead of the hostname is fine.

Without functioning name services I don't think you can browse the shares at all.  You  will be able to connect directly, but you can view all the shares and select one by just seeing it.>  

I originally chose samba to share with a Mac and a Windows computer which is not yet on site.  I just found out today that the windows computer will not be used at all, it will only be Mac's connecting to my Ubuntu system.  Should I skip samba and try NFS or CIFS?  

Thank you again for the help, cheers.

Samba is an Open source implementation of CIFS.  The is the **S**erver **M**essage **B**lock (SMB) protocol.  There are other implementations of the protocol.  Apple has created their own version for the latest version of OSX and it has incompatibilities.  Of course you can install Samba, but why do that when there are other methods to browse the shares.

Maybe [**_[COLOR="Blue"]this[/COLOR]_**]("http://www.cornext.com/2012/04/use-ubuntu-as-macs-server.html") will work.

[COLOR="Blue"]Edit:  I have always wanted to try this.  We can use this thread to discuss it.[/COLOR]

---

