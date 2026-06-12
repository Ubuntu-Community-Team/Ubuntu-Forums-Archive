---
title: "[SOLVED] net usershare' returned error 255: net usershare add:"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by wawadave on 2008-10-25
'net usershare' returned error 255: net usershare add: cannot share path /media/disk/disk as we are restricted to only sharing directories we own.
	Ask the administrator to add the line "usershare owner only = False" 
	to the [global] section of the smb.conf to allow this.

Ok where how would i go to fix this. i live alone so there is no admin to ask. just me.

i,m trying to share folders on a recently formatted partition.

---

### Post by cariboo on 2008-10-25
Smb.conf is located in /etc/samba. THe easy way is Alt-F2 and type:

```
gksu gedit /etc/samba/smb.conf
```

JIm

---

### Post by wawadave on 2008-10-25
Thank you!
i added the line"usershare owner only = False"
to the notepad that opened up and saved it.
but i still get that error when trying to share any folder on that drive.
should i reboot? then retry?

---

### Post by wawadave on 2008-10-25
ok this is solved! thank you very much!!!

i did not add the line to the global part the first time. works now it in correct place...

is that williams lake B.C? you are from?

---

### Post by OGpmpdog on 2009-01-12
***i did not add the line to the global part the first time. works now it in correct place...***

Hello, I am very new to Ubuntu and having the same problem of sharing folders.

The samba configuration file is quite detailed.:confused:

Where exactly in the samba notepad do you add the "usershare owner only = False" line? 

Do I include the quotation marks?

Can someone please paste an example of where I insert the line in the config menu?

Thanks.):P

---

### Post by tinmice on 2009-01-21
Have pasted the line into the global part but still have no luck. any other suggestions? im not quite sure why my shares arent working as i have had them going on a previous install of 8.10.

---

### Post by Cruella on 2009-01-24
typing
gksu gedit /etc/samba/smb.conf
in terminal window
and adding line "usershare owner only = False" in global section
definitely solved my 'sharing folder' problem
Thank you a lot!

---

### Post by mogul218 on 2009-04-07
I am trying to accomplish the same thing.  I put"usershare owner only = false" under global section and it is not working.  Do I need to type a # at the beginning of the line like all the other lines in smb.conf file?


'net usershare' returned error 255: [2009/04/07 21:17:27,  0] param/loadparm.c:lp_do_parameter(7198)
  Ignoring unknown parameter ""usershare owner only"
net usershare add: cannot share path /media/Windows Vista Home Premium/Users/Sean as we are restricted to only sharing directories we own.
	Ask the administrator to add the line "usershare owner only = false" 
	to the [global] section of the smb.conf to allow this.

---

### Post by mogul218 on 2009-04-07
> **mogul218 said:**
> I am trying to accomplish the same thing.  I put"usershare owner only = false" under global section and it is not working.  Do I need to type a # at the beginning of the line like all the other lines in smb.conf file?


'net usershare' returned error 255: [2009/04/07 21:17:27,  0] param/loadparm.c:lp_do_parameter(7198)
  Ignoring unknown parameter ""usershare owner only"
net usershare add: cannot share path /media/Windows Vista Home Premium/Users/Sean as we are restricted to only sharing directories we own.
	Ask the administrator to add the line "usershare owner only = false" 
	to the [global] section of the smb.conf to allow this.





Solved!  Apparently, when I copied the previous posters line they had F in false capitalized and it didn't work.  Also if you come across this in the future, no quotation marks are needed.  I don't think the previous posters were very clear regarding this.

---

### Post by mistermouse on 2009-08-18
Thanks for this! Other solutions were long, complex and confusing. This took less than 30 seconds! Great for ubuntu-nubs like me :)

---

### Post by dustin.jorge on 2009-10-20
> **Cruella said:**
> typing
gksu gedit /etc/samba/smb.conf
in terminal window
and adding line "usershare owner only = False" in global section
definitely solved my 'sharing folder' problem
Thank you a lot!

This worked for me as well. I had the other lines (noted in other posts) but was missing "usershare owner only = false" in the global section.

After editing/saving "/etc/samba/smb.conf" and restarting samba with "sudo /etc/init.d/samba restart" I was able to "gksudo nautilus" and set my sharing options with no error...

Thank you kindly!

---

### Post by finsyourfriend on 2010-08-17
I know this post is almost two years running, but after playing around more times than I wanted to with the smb.conf file, here is the exact position to put this line of code and what it should look like in your smb.conf file: ( I highlighted it in blue for your convenience.)

```
#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Any line which starts with a ; (semi-colon) or a # (hash) 
# is a comment and is ignored. In this example we will use a #
# for commentary and a ; for parts of the config file that you
# may wish to enable
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 
#

#======================= Global Settings =======================

[global]

[COLOR="RoyalBlue"]usershare owner only = false[/COLOR]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = EXAMPLE

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

```

---

### Post by ToFue on 2010-10-26
To thuroughly beat the dead horse...

Do I *want* to set "usershare owner only" to false? does this open a volnerability if anyone but the owner can access my usershare? What scenario should I impliment this to "false" vs. "true"?

Thanx, and sorry for the rezz.. :p

---

### Post by johnmay on 2010-11-30
This thread worked to solve my problem. With the 10.10 change that the 
/etc/init.d/smbd 
is now what to restart
after adding "usershare owner only = false" in the samba conf file:   /etc/samba/smb.conf 


for the person who posted last, you are not creating a big vulnerability, because you still set the permissions on the share once you create it. Most of the time you just give people read access, which will prevent 'anyone' from writing, and therefore also executing any malignant program.

---

### Post by Salvagluque on 2010-12-01
Hello guys,

I had the same problem mentioned before, but now that I solved it using the method described above it turns out Samba keeps asking me forever for my password, no matter how many times I write it even if is correct any time.

I don't know why this happens. One machine has the ubunu 10.10 and the other one the 9.10. I tryed installing samba4 in both but that just got it worse so I uninstalled the samba 4 relalted packages from synaptic and reinstalled the ones taken out.

Thanks in advance

Salvador

---

### Post by hahnemann on 2010-12-01
Finally after 3 days looking for some light!

Everything solved in less than 3 minutes, you rock guys!

Thank you so much!

---

### Post by Morbius1 on 2010-12-01
> **Salvagluque said:**
> Hello guys,

I had the same problem mentioned before, but now that I solved it using the method described above it turns out Samba keeps asking me forever for my password, no matter how many times I write it even if is correct any time.

I don't know why this happens. One machine has the ubunu 10.10 and the other one the 9.10. I tryed installing samba4 in both but that just got it worse so I uninstalled the samba 4 relalted packages from synaptic and reinstalled the ones taken out.

Thanks in advance

Salvador
You really should start a separate topic but .....
Please post the output of the following commands:
```
net usershare info --long
```
```
testparm -s
```

---

### Post by Salvagluque on 2010-12-01
here they are:

[música]
path=/home/salvador/Música
comment=
usershare_acl=Everyone:F,
guest_ok=n

[documentos]
path=/home/salvador/Documentos
comment=
usershare_acl=Everyone:F,
guest_ok=n




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
	usershare owner only = No
	panic action = /usr/share/samba/panic-action %d

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

---

### Post by Morbius1 on 2010-12-01
Actually, everything looks to be in order. Both of your shares have guest access disabled (  guest_ok=n ) so you're going to have to create users and give them samba passwords in order for the remote user to gain access.

Are you sure you don't want to allow guest access? If you do then just go back into Nautilus and click on the guest access option.

If you really want to limit access to users with usernames and passwords then it's a two step process:

Let's say you have a remote user named morbius:

(1) Create a local user with no home folder and no local login capability:
```
sudo useradd -s /bin/true morbius
```(2) Then give morbius a samba password to use to connect to the share:
```
sudo smbpasswd -a morbius
```But the easiest way is to allow guest access

---

### Post by Salvagluque on 2010-12-02
Thanks those worked fine.

---

### Post by skodsamler on 2011-03-13
deletet by uiser i dropped the  whole thing

---

### Post by ColoradoMadMan on 2013-04-15
Ohh Man!  I've been looking everywhere for this information for days!  Thanks Guys!  Your Awesome.

---

### Post by oldos2er on 2013-04-15
Closed, please don't bump old threads.

---

