---
title: "deploying software on windows clients using batch script"
date: 2014-09-25
forum: Programming Talk
---

### Post by Swiftjay on 2014-09-25
Sorry if this is the wrong area for this.

I'm trying to find a way of deploying software on Windows desktops using a batch script, when I encounter an issue with runas, obviously because runas is not designed to supply a password of the administrator due to vunerabilities I can't use it to run the command I want.

This is what I was trying to do 

\\zeus\netlogon\psexec \\%computername% -u DOMAIN\USER -p PASSWORD -h  "msiexec /i \\zeus\software\zarafaclient-en.msi  /quiet"

Of course psexec doesn't work so again stuck on what to do regarding this.  Do any of you linux administrators use batch scripts or any reg edits to install msi files on domain computers?  If so do you have any tips for a guy just trying to learn?

---

### Post by TheFu on 2014-09-25
PowerShell?

Also, Puppet and Ansible have MS-Windows facilities - though most companies would elect to use the monster MS-SMS that works 90% of the time.

[http://www.ansible.com/blog/windows-is-coming](http://www.ansible.com/blog/windows-is-coming) is alpha level. It uses powershell to avoid any pre-installation requirements.

Chef seems to work from my reading. Don't know what that entails.
Haven't looked at puppet in a few years - they were working on Windows, so it must be beta or better by now.

---

### Post by Swiftjay on 2014-09-25
I can't do powershell commands from linux, I'm just trying to find a way to do things from the server side rather then client side of things.

This ansible, it seems interesting although I'm curious how it sends these power shell commands over to the client. I'd like to read more into it, I think.

---

### Post by TheFu on 2014-09-25
Sure you can.  Just put the powershell scripts into the automatically run scripts whenever a client connects to a samba server. Then each client will run the commands for you. Of course, user directories need to be on a samba share for this to work.

Windows is not Linux and Linux is not Windows, as you know. Any cross-platform solution between those tends to suck, so I wouldn't bet my job on this working well.  OTOH, if MS-SMS can't do 100% management, there is an opening for a solution that does actually work.  Where I've worked, pushing updates was only 10% of the issue - getting accurate reports was 90% - if we couldn't report to senior management the exact count of patched systems AND the exact count of unpatched systems daily, it was deemed a failure. 

Without facts and data, we are lost.

---

### Post by Michael_McKenney on 2014-09-25
You would need to write a batch file in the startup folder of Windows, modify it each time and give the location of the files.  On reboot, the files can install if the user has sufficient rights.  If you are in a Windows Domain, you can use the GPO and install files from Active Directory Services.

---

