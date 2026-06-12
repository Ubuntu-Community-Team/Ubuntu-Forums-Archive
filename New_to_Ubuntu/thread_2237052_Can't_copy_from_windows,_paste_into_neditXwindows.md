---
title: "Can't copy from windows, paste into nedit/Xwindows"
date: 2014-07-30
forum: New to Ubuntu
---

### Post by bulrush2 on 2014-07-30
Config: 
[LIST=1]
[*]Server config: Ubuntu 14.04 running as a VM under Vsphere 
[*]Client PC: Windows 7 running Putty 0.62 and Xming 6.9.0.31 
[*]Server hardware is already behind a firewall and there will only be one user using this server, me. 
[*]I installed OpenSSH when Ubuntu was installed. 
[*]X Windows now creates an xterminal which works. Nedit works as does the Kate editor. 
[*]Using Xlaunch (for Xming) the "clipboard" checkbox is already checked. There are not a lot of config options in Xlaunch. 
[/LIST]

I am on a new Ubuntu server system that I set up, so FTP, scp, email and other stuff is not set up yet. We are working on getting Samba set up. In the meantime I have to get a text source Perl file from Windows to the new Ubuntu system. 

When I copy from a Windows Editor, then paste into nedit using the middle button, most of the time it does nothing. No error or anything. BUT, if I wait 1-2 minutes, it seems the clipboard from windows finally makes it to the X11 clipboard, and the middle button pastes in the selected text. 

In my /etc/gdm/custom.conf, in the [daemon] section I added "KillInitClients=false". Then at the command line I did "sudo restart gdm". 

That didn't help. Source here: [http://www.alexandre-gomes.com/?p=134](http://www.alexandre-gomes.com/?p=134)


[LIST=1]
[*]Got any ideas how I can get cut and paste into X11 to work? 
[*]Or how to get this text file to Ubuntu? 
[/LIST]

Thanks!
[HR][/HR]EDIT: 
Apparently Xming sometimes interferes with the clipboard. [http://aufather.wordpress.com/2012/02/12/cygwin-x-server-a-better-alternative-to-xming/](http://aufather.wordpress.com/2012/02/12/cygwin-x-server-a-better-alternative-to-xming/)

Maybe time to change to Cygwin?

---

### Post by TheFu on 2014-07-31
For text connections from Windows into Linux, putty has a good select/paste facility.
For GUI-based connections from Windows, I found it less hassle to run a Linux VM and use the native X/Windows.

BTW - X11 doesn't do "cut/paste" - it does select/paste.

If you want to transfer files between Windows and Linux, use any of the network-based solutions. That can be CIFS, sftp, scp, ssh, nfs, webdav, ... there must be 50 others, but most of those like FTP are not secure and shouldn't be used with login data. FTP is a bad habit and should be avoided.  It is easiest to just use sftp always - THAT is a good habit.

---

