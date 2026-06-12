---
title: "Windows and Ubuntu network - need password"
date: 2012-12-22
forum: New to Ubuntu
---

### Post by archie456 on 2012-12-22
Hi,

I have a Windows 7 network at home and one Ubuntu machine which holds my network shares.

When I access the Ubuntu machine from a Win 7 machine I get "Enter Network Password" - if I enter a password from te Ubuntu machine I can access the shares fine.

But I don't want a password, I want to be able to browse straight in - is there any way I can 'turn off' the password feature.

I edited smb.conf and changed:
guest ok = yes
guest account = an account on the Ubuntu box

but that hasn't changed anything.

Any ideas??

Cheers.

---

### Post by BBQdave on 2012-12-22
> **archie456 said:**
> But I don't want a password, I want to be able to browse straight in - is there any way I can 'turn off' the password feature.

Perhaps I misunderstand... but that is part of security, whether it is samba, vsftp, or any data server - to protect a user, there is a password. Hence a password to access the data in your user account.

Generally, guest accounts are read only, and you can download files. If there was open access - no password, you can imagine what might be uploaded by any *guest user* :)

---

### Post by archie456 on 2012-12-22
Agreed, but the other accounts are accessed by my wife only and (generally) I trust her.

Also, by Media Center PC tends to forget the password every so often and then it requires be to enter it again.

The passwords are just an annoyance.

If I could get the Win 7 computers to remember the password and never ask again, I'd be happy with that, but it remembers for a while and then prompts again.

---

### Post by luvshines on 2012-12-22
What's the output of 'testparm -s' command on Ubuntu ?

Also thinking, as a workaround till this is solved, you may hook a single line script in windows startup to map network drive using hard coded username/password

---

### Post by archie456 on 2012-12-22
I'm new to Ubuntu, so I don't know what testparm does, but it returns this:

```

Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[FileStorage]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	workgroup = PARTRIDGE
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	guest account = kevin
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	username map = /etc/samba/smbusers
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	name resolve order = lmhosts wins bcast host
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	idmap config * : backend = tdb
	guest ok = Yes

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	print ok = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
	valid users = kevin
	read only = No

[FileStorage]
	path = /media/kevin/FileStorage
	read only = No

```

Is there anything of use?

(Regarding the script to map the drives with a coded password - thats a good idea - If I cannot get free access into the network I'll do that).

Cheers.

---

### Post by audiomick on 2012-12-22
> **archie456 said:**
> I'm new to Ubuntu, so I don't know what testparm does, 

You can always use man to find out what a command and it's options do. 

In the terminal
```
man man
```
to find out what man is.

```
man testparm
```
for the case in point.

Generally 
```
man <command name>
```

---

### Post by coldcritter64 on 2012-12-22
OP, how I read your earlier posts is the password box is in Windows, not Ubuntu. If that is the case, have you looked into permanently mounting the shares in Windows as a network drive available in "My Compuer" (using older Win system term)? The Windows system should then permanently store your credentials and allow more "easy" access to the Ubuntu shares. I'm reading your OP as a Windows issue. Cheers.

Edit: if there is an issue from Ubuntu with the password requirements, credentials can also be stored to access smb password protected shares (using gnome-keyring). Rather than turning off passwords and their associated security protection OP, research storing credentials in Windows and Ubuntu for "easy &  safe" access. It can be done :)

---

### Post by luvshines on 2012-12-23
> **archie456 said:**
> 
[global]
...	
        guest ok = Yes

[FileStorage]
	path = /media/kevin/FileStorage
	read only = No


Your share is FileStorage, right ?

Try moving the 'guest ok' from [global] section to the [FileStorage] section since 'guest ok' is a share specific option. 
Then restart smbd service and give it a shot.

To check if a share is accessible with guest account can be tested from Ubuntu terminal itself.
Use following command from terminal```

smbclient //<server-ip>/<share-name> -U%

```

BTW, testparm -s will simply pick up the relevant config parameters defined in your /etc/samba/smb.conf file and display them. You can always choose to filter out any personal details it might display before posting them here :)

---

### Post by archie456 on 2012-12-23
Audiomick - Thanks for the info on the MAN command - that will save me a lot of time!

Coldcritter64 - Yes thats my plan B, the problem I had was that my Media Centre box kept forgetting the remembered password every so oftern, but as someone above mentioned, the answer would be to add the password to the script which maps the drive.

Luvsshines - Reading the smb.conf file, the [FileStorage] section does have guest ok = yes, but looking at the output of testparm it doesn't seem to be reading it...

---

### Post by luvshines on 2012-12-23
> **archie456 said:**
> 
Luvsshines - Reading the smb.conf file, the [FileStorage] section does have guest ok = yes, but looking at the output of testparm it doesn't seem to be reading it...

Oh ok !!
Did you try the guest access to the share from terminal ?

Also, can you check the permission for the path starting from /media```

ls -ld /media
ls -ld /media/kevin
ls -ld /media/kevin/FileStorage
```

---

### Post by archie456 on 2012-12-23
> **luvshines said:**
> Did you try the guest access to the share from terminal

How do I try that?

---

### Post by luvshines on 2012-12-23
> **archie456 said:**
> How do I try that?

Check Comment #8 :)

Also, I updated my last post asking for more info

---

### Post by haqking on 2012-12-23
```
gksudo gedit /etc/samba/smb.conf
```

or editor of choice.

change in the Authentication section:

```
security = share
```

remove semicolon from beginning of

```
;  guest account = nobody
```

at end of file add the following to suit your share

[your share name]
writable = yes
path = /path/to/directory
public = yes
guest ok = yes
guest only = yes
guest account = nobody
browsable = yes

save it and then restart samba

---

### Post by critin on 2012-12-23
> **archie456 said:**
> Hi,



But I don't want a password, I want to be able to browse straight in - is there any way I can 'turn off' the password feature.

I edited smb.conf and changed:
guest ok = yes
guest account = an account on the Ubuntu box

but that hasn't changed anything.

Any ideas??

Cheers.

When setting up sharing in Windows there is a tick box in the 'allow all networks' section to remember password.  You enter it once in ubuntu and don't have to enter again.

---

### Post by archie456 on 2012-12-23
haqking - I tried your suggestions - still had the same problem whereas a login box appears when I try to the computer.

critin - I used to do that, tick the remember password box, but annoyingly, my media center pc would only remember it for a few days and then require it again - which would cause all the synchronization scripts to fail...(thouch I'll add the password to the script if I cannot get free access to work.

---

### Post by haqking on 2012-12-23
> **archie456 said:**
> haqking - I tried your suggestions - still had the same problem whereas a login box appears when I try to the computer.

critin - I used to do that, tick the remember password box, but annoyingly, my media center pc would only remember it for a few days and then require it again - which would cause all the synchronization scripts to fail...(thouch I'll add the password to the script if I cannot get free access to work.

There is also a requirement in the LSA policy on Windows machines to require auth for shares such as LM, NTLM, NTLMv2 etc, and I know sometimes this needs to be changed to allow to connect to NAS shares for example which run samba (i did it for my friend last year to disable login box when connecting to a NAS share), however i cant be bothered to fire up a windows machine or to Google to find out cos im enjoying my Whisky too much ;-)

But it will give you something to Google ;-)

Peace

---

### Post by luvshines on 2012-12-24
> **archie456 said:**
> haqking - I tried your suggestions - still had the same problem whereas a login box appears when I try to the computer.

critin - I used to do that, tick the remember password box, but annoyingly, my media center pc would only remember it for a few days and then require it again - which would cause all the synchronization scripts to fail...(thouch I'll add the password to the script if I cannot get free access to work.

Did you check the ls -ld output I had suggested in my 2nd last post ? Your user 'kevin' should have atleast '--x' permission on each of the directory, to login.

Also did u try guest access from command line.

---

### Post by archie456 on 2012-12-24
> **luvshines said:**
> Did you check the ls -ld output I had suggested in my 2nd last post ? Your user 'kevin' should have atleast '--x' permission on each of the directory, to login.

Also did u try guest access from command line.

OK, when I try ls -ld I get this:

kevin@TVSERVER:~$ ls -ld /media
drwxr-xr-x 3 root root 4096 Dec 15 10:31 /media
kevin@TVSERVER:~$ ls -ld /media/kevin
drwxr-x---+ 3 root root 4096 Dec 24 08:35 /media/kevin
kevin@TVSERVER:~$ ls -ld /media/kevin/FileStorage
drwx------ 1 kevin kevin 16384 Dec 15 18:19 /media/kevin/FileStorage

I think thats OK if I've read your post correctly.


I tried to access the shares from the Ubuntu box: (is this what you meant by guest access to the share from terminal?)

1. Opened Home Folder window
2. Clicked on 'Browse Network'
3. Browse to the Ubuntu machine I'm using
4. Clicked on 'FileStorage' and got this error: Unable to mount location. Failed to mount Windows share


When I look at the filer window, I can see an arrow to the right of FileStorage and so its certainly mounted.

Any pointers?

---

### Post by Morbius1 on 2012-12-24
Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Change your share definition to look like this:
> [FileStorage]
path = /media/kevin/FileStorage
read only = No
guest ok = yes
[COLOR=Blue]**force user = keven**[/COLOR]Then restart samba:
```
sudo service smbd restart
```Wait a few minutes before trying to access the share.

Only keven can access what looks like an external ntfs formatted usb partition. Force user will convert the remote user to keven for that share.

[COLOR=Blue]*Side Note: This is the new parent folder to all these non-fstab partitions: *[/COLOR]
>  drwxr-x---+ 3 root root 4096 Dec 24 08:35 /media/kevinIt's using ACL's to determine who has access and it this case it's keven so you would have to use "force user" even if it was not formatted in NTFS. Why did they do this? Because ACL's are more complicated and the old way was far too simple to use.

---

### Post by archie456 on 2013-01-11
OK, well I've cocked up my smb.conf file now, and rather cleverly, not backed it up.

Is there anyway to reset it to defaults - or can someone post theirs? I'm on 12.120.

Cheers

---

### Post by luvshines on 2013-01-12
> **archie456 said:**
> Is there anyway to reset it to defaults - or can someone post theirs? I'm on 12.120.


You posted the contents in the comment #5 :)
Copy the contents starting from [global] upto the end, and that should be good

---

### Post by archie456 on 2013-01-12
Post 5 was the response to the testparm command - is that just the same as the contents of smb.conf?

Also, I'd slightly modified it at that stage - I was hoping to reset it to the OOTB condition...

---

### Post by Morbius1 on 2013-01-12
[1] Testparm is the smb.conf interpreter so it's output can be used to replace smb.conf - If it was a known good smb.conf.

[2] There is also a copy of the default ( except it has one mistake ) smb.conf file that is kept just for people like us who make a mess of things. It's located at: /usr/share/samba/smb.conf [COLOR=Blue]( make sure it's there before following the next steps )[/COLOR]:

** Make a backup of your current smb.conf:
```
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.bak
```** Copy the default:
```
sudo cp -a /usr/share/samba/smb.conf /etc/samba/
```** Correct the mistake:

Look for the following line:
```
encrypt passwords = false
``` [COLOR=Blue][I]Could also state it as no.

[/I][/COLOR]And Change it to true:
```
encrypt passwords = true
```Then restart samba:
```
sudo service smbd restart
```

---

