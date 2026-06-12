---
title: "HowTo:  Samba: print server quick and dirty"
date: 2006-04-17
forum: Outdated Tutorials &amp; Tips
---

### Post by Thunderbird750 on 2006-04-17
Quick and dirty creating a print server on ubuntu; specifics for Xerox Docuprint M750-1 
key references:
  I did my base setup of samba using:
[http://www.howtoforge.com/samba_setup_ubuntu_5.10](http://www.howtoforge.com/samba_setup_ubuntu_5.10)
  however, I didn't do a base install as indicated in this howto; but instead used my current ubutnu installation.  (btw, the above also has a -very nice- "install ubuntu" imbedded in the instructions; in hindsight, I wish I had it at hand when I did my ubuntu install).
==
[http://support.microsoft.com/?kbid=314499](http://support.microsoft.com/?kbid=314499)
  (this gave me the net use equivalent for printer add command)
==
[http://www.ubuntuforums.org/showthread.php?t=150003&page=4&highlight=samba+print](http://www.ubuntuforums.org/showthread.php?t=150003&page=4&highlight=samba+print)
  (this discussion provided so much of that "secret sauce" that finally led me to get this to work)

So, started off with this:
[http://www.howtoforge.com/samba_setup_ubuntu_5.10](http://www.howtoforge.com/samba_setup_ubuntu_5.10)
## right off the bat, I recommend you add this to your smb.conf file:
#in the [global] section....
# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Put a capping on the size of the log files (in Kb).
   max log size = 1000

## and once you have things settled out, you might want to drop the log
# log level = 0 
## or 1; but 3 (as per above link) is good to start with.
===========


## this was also key to add to my /etc/samba/smbuser file; as someone else 
##setup my xp system and chose a name for me which had a space in it.
ubuntuid = "John Doe" 
#### end addition to /etc/samba/smbuser
===

I also had to add a password for John Doe on windows XP that matched up with the samba password set for ubuntuid, other wise I got a error message when I ran the net use commands. (I've read this should not be necessary, but if you are desperate, it is worth a try.)

Additionally, there was a lack of direction in setting the "workgroups" on windows; for xp home, I found the easiest way was to go to control panel, click on system, select "computer name", click on "change" and update the computer name and work group.  If I remember right, I had to reboot after that for the workgroup to "pickup" everywhere (or at least I thought it might be needed, so I did.)


Next there's really a lot of helpful stuff here:
[http://www.ubuntuforums.org/showthread.php?t=150003&page=4&highlight=samba+print](http://www.ubuntuforums.org/showthread.php?t=150003&page=4&highlight=samba+print)
...it gave me the "net view" commands for Windows which helped debug my problems...  I struggled with this for a long time....
====
C:\Documents and Settings\John Doe>net view \\192.168.1.50
System error 53 has occurred.

The network path was not found.
=========================
At some point I let windows run a network configuration wizard to see if it would help me setup my workgroups; it didn't, but it was a "real sport" and started up the microsoft firewall.  You might think that "kind" -except- for the fact I already had Zone labs fire wall running, so had two fire walls one of which I wasn't expecting to have to alter.  Things improved when I figured that out and "killed" the windows firewall; at least I could see the firewall events in Zone labs at that point... sigh...
I had to add 192.168.1.50 as a "trusted" host.
Also firewall running on ubuntu, had to add... 631, 445, and 139 for my windows box (192.168.1.109)


Here's what I did that help show I was finally getting close to the right path...```


C:\Documents and Settings\John Doe>net view \\192.168.1.50
Shared resources at \\192.168.1.50

u1 server (Samba, Ubuntu)

Share name        Type   Used as  Comment

----------------------------------------------------------------
allusers          Disk            All Users
DocuPrint M750-1  Print           DocuPrint M750-1
netlogon          Disk            Network Logon Service
ubuntuid          Disk            Home
The command completed successfully.

```
-------this convinced me I had beaten the userid issue, password issue, firewall, etc... So I tried to use some raw net use commands to test access....

```

C:\Documents and Settings\John Doe>net use x: \\192.168.1.50\allusers
The command completed successfully.


C:\Documents and Settings\John Doe>x:

X:\>dir
 Volume in drive X is allusers
 Volume Serial Number is 0017-2C31

 Directory of X:\

04/16/2006  07:43 PM    <DIR>          .
04/16/2006  07:43 PM    <DIR>          ..
               0 File(s)              0 bytes
               2 Dir(s)               0 bytes free

```
and I could generally access the X drive from explorer, etc from this point.

From here,
[http://support.microsoft.com/?kbid=314499](http://support.microsoft.com/?kbid=314499)
I got the syntax for the netuse for a printer...
```

C:\Documents and Settings\John Doe>net use lpt2 \\192.168.1.50\DocuPrint
System error 66 has occurred.

The network resource type is not correct.


C:\Documents and Settings\John Doe>net use lpt2 "\\192.168.1.50\DocuPrint M750-1" /persistent:yes
The command completed successfully.

```

Until this point, I had been rather insistent upon going into the windows GUI to try to get workgroups to work w/ shares.  I kept expecting the "add a remote printer" to show me a list of ubuntu's (U1's) samba printers... apparently, this was being excessively optomistic.  While I could get "U1" to show up in some of the workgroup lists, I could never get the GUI to show what the resources were, or what printers were available thru it.  Eventually I had to break down and manually enter the below:
under the "Printer and Faxes", click the add printer, 
choose "A network printer..."(next), choose "Connect to this printer(or to browse for a printer, select this option and click Next)"  AND enter this in the "Name:" field;
\\192.168.1.50\DocuPrint M750-1
,complete with spaces, as the printer I wanted to add and click Next, Finish.  Somewhere in there, it prompted me to download a printer driver; had to enter Xerox and the printer model, it did a network search and found the driver to install (sorry, didn't take notes at that point).



***
Final "gotcha" I ran into... I read up on the quota stuff and set ubuntuid's quotas pretty low; however, I didn't have have the files systems setup the same as in the 
[http://www.howtoforge.com/samba_setup_ubuntu_5.10](http://www.howtoforge.com/samba_setup_ubuntu_5.10)
so ended up enforcing a tight quota on /var/spool/samba
This intially caused prints to fail.  For the short term, I set the hard and soft limits back to Zero, the default, which means really, no quota (or unlimited "over quota", depending on how you look at it).  I will have to decide what I want to do about quotas, filesystems etc. at a later date.  However, I have a functioning print server... phew!  If you follow that link's directions, you won't run into this problem; but you also will likely not have any enforced quotas.

Much thanks to the folks who contributed to the referenced threads.  I'm sure I'd've given up without the resources to look at.

This probably deserves to be polished up.  I'll try to get back to do that sometime.

---

