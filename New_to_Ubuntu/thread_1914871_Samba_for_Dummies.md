---
title: "Samba for Dummies?"
date: 2012-01-25
forum: New to Ubuntu
---

### Post by 2CV67 on 2012-01-25
Is there a SIMPLE, UNDERSTANDABLE guide to using Samba for the very basic tasks (ONLY) of sharing files & using printers?

Everything I have found has been more-or-less incomprehensible & almost immediately gets into complex situations & terminal manipulations.
Obviously, I started here: [https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)
and spent days Googling.

Last year I got to this stage:
[http://ubuntuforums.org/showpost.php?p=10802119&postcount=7](http://ubuntuforums.org/showpost.php?p=10802119&postcount=7)

Since then, I have upgraded from Vista to W7 & from 11.04 to 11.10.

I now have both printing (W7 > WiFi > 11.10 > usb > Canon) and file sharing working OK but had a strange (but common) problem in that W7 refused to remember the Samba password, so I had to re-enter it every time...

By reading between the lines and some trial & error, I found that if I create a fictitious Samba Username & p/w, then use that Username & p/w in W7 - it sticks OK!
That process was a bit confused because when you try to create & new Samba user the first item is "Unix Username" where you see a list of options like "Debian-exim" & "avahi-autoipd" & existing users but no possibility to invent a new one.
I just chose one at random & added my new "Windows Username" which is what I enter in W7.

A Dummy-level guide would be so welcome!

---

### Post by WasMeHere on 2012-01-25
Hi 2CV67,

Personally I find it easier to use ***SSH*** than Samba. If you install the ssh driver sshd in your Ubuntu computer, you can easily log in from any computer using ssh and do 'any' task or using sftp and transfer files. WinSCP is a convenient client program for Windows. In the file browser Nautilus you have the menu option

'File -- Connect to server -- SSH'

to run sftp. You can drag and drop such sessions to the left panel to make them start at once (except that you may need a password).

Have fun finding out :-)
Olle

---

### Post by mastablasta on 2012-01-25
i configured Samba in Kubuntu 10.10. Samba is there and it works really easy. the only problem (i couldn't get the folder to be shared) was that a package was missing in that version of kubuntu. after installing the missing package all i had to do is set a folder as shared and i could see it in windows.
problem in SAMBA is that many users do not know what their workgroup is. if you know it it preety much works the same as windows sharing.
 
same goes for printing via SAMBA.

---

### Post by Morbius1 on 2012-01-25
There's 2 ways to create a samba share:

** Classic Shares: using something like system-config-samba that creates shares in smb.conf.

** Usershares ( aka - Nautilus Shares ) Created from Nautilus itself.

Usershares resemble the way you create "Simple Shares" on WinXP:
Right click a folder you own > Sharing options > Click on 2 or 3 boxes > Done. If you select "Guest Access" you will not need to pass user names and passwords on the client.

**[COLOR=Blue]Note[/COLOR]**: It's generally not a good idea to use both methods of Samba sharing at the same time - especially not on the same folder.

As far as printing is concerned it looks like you have already accomplished this and in looking at your link it appears you only left off one step. By default Samba can be used as a passthrough to CUPS for remote printing but by default it requires a password to access your printers. In /etc/samba/smb.conf you will find this section:
> [printers] 
   comment = All Printers 
   browseable = no 
   path = /var/spool/samba 
   printable = yes 
   guest ok = no 
   read only = yes 
   create mask = 0700Change "guest ok = no" to yes:
> [printers] 
   comment = All Printers 
   browseable = no 
   path = /var/spool/samba 
   printable = yes 
[COLOR=Blue]**    guest ok = yes**[/COLOR]
   read only = yes 
   create mask = 0700[COLOR=Black]Then restart samba:
[/COLOR]```
[COLOR=Black]sudo service smbd restart[/COLOR]
```[COLOR=Black]

[/COLOR]

---

