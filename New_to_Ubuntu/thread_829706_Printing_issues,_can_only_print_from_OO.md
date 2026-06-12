---
title: "Printing issues, can only print from OO"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by jeppo on 2008-06-15
Hi all,

Recently made the switch to Ubuntu, so far my biggest problem has been the inability to print from various applications.  I have only been able to successfully print openoffice documents and the Ubuntu Printer test page.

When trying to print from Firefox, nothing happens.  No new item is added to the queue.

When I try to print from gedit or evince, I receive errors similar to this: "Error printing.  Can't prompt for authorization"

This is really frustrating me and somewhat ruining my change to Ubuntu from Windows.  Any help would be very very much appreciated.

Thanks,
Chris

---

### Post by jeppo on 2008-06-17
Bump

---

### Post by avtolle on 2008-06-17
Is your printer set as the default for the system (taking a stab at the obvious first)?

---

### Post by jeppo on 2008-06-18
Hi,

Yep it's set as default.  Thanks for the reply.

Chris

---

### Post by jeppo on 2008-06-24
Noone can help?

Any help would really be appreciated as I really need to print from Firefox and other apps, and I don't want to keep booting into windows to print a single webpage.

Just to clarify, my printers plugged into a router and referenced in CUPS with this address: lpd://192.168.0.1/lp1 which is working fine from open office.

TIA

---

### Post by jeppo on 2008-07-10
Bump

---

### Post by MasterSushi on 2008-07-12
I am experiencing a similar issue. I am using a CUPS print driver and am unable to print in Firefox 3. I can print from over other application that I have attempted so far. Oo, Opera, etc. But, I prefer Firefox 3 and would like to be able to print from FF3. And my printer is also set as the dealt printer as well.

---

### Post by jeppo on 2008-07-13
I'm persisting with this issue as it is one of the only things stopping me from completely switching to Ubuntu (along with the infamous Hibernate/suspend issue).  If this helps this is the output when I run gedit in the terminal and try to print:

```
chris@chris-laptop:~$ gedit
** (gedit:11867): DEBUG: end_print_cb
** (gedit:11867): DEBUG: done_cb
** (gedit:11867): DEBUG: Finalize.

** (gedit:11867): WARNING **: NOT IMPLEMENTED: We need to prompt for authorization

** (gedit:11867): WARNING **: Failed to create file '/home/chris/.gnome2/gedit/gedit-page-setup.9ZS7DU': No such file or directory

** (gedit:11867): WARNING **: Failed to create file '/home/chris/.gnome2/gedit/gedit-print-settings.66Y7DU': No such file or directory

```

And evince:

```
chris@chris-laptop:~$ evince

** (evince:12001): WARNING **: File is empty

** (evince:12001): WARNING **: NOT IMPLEMENTED: We need to prompt for authorization

```

I hope this information can shed some light on the problem.

Chris

---

### Post by jeppo on 2008-07-28
After much searching and no results, I finally fixed this problem.  What I did was instead of setting up my printer in [http://localhost:631/](http://localhost:631/) I just went into System -> Admin and then copied the printer.  After that everything worked.  Don't ask me why cause I have no idea :) all I know is that I can now print from all my applications and I am one step closer to completely moving to Ubuntu.

Now if only I could fix suspend/hibernate...thats for another day.

Chris

---

### Post by weaccept on 2008-08-15
I had this same problem using the Codehost drivers for a Canon C3380.  Copying the printer using System > Administration > Printing didn't work.  Using codehost-config, right clicking on the printer and selecting Duplicate did work.  I made the duplicated printer the default and printing from Firefox and evince works.

Related bugs:
[https://bugs.launchpad.net/ubuntu/+source/evince/+bug/158411](https://bugs.launchpad.net/ubuntu/+source/evince/+bug/158411)
[https://bugs.launchpad.net/ubuntu/+source/evince/+bug/248902](https://bugs.launchpad.net/ubuntu/+source/evince/+bug/248902)

---

### Post by Piraja on 2008-11-04
> **jeppo said:**
> After much searching and no results, I finally fixed this problem.  [...] I just went into System -> Admin and then copied the printer.  After that everything worked.  Don't ask me why cause I have no idea :) all I know is that I can now print from all my applications

Thanks for this mysterious solution — I tried it and it worked for me, too. I have no idea what caused my sudden CUPS authorization problem, but copying the printer fixed it...

---

### Post by khermans on 2008-12-03
Copying the printer worked for me too.  Very strange indeed.  You would think an exact copy should act exactly like the original :-)

---

### Post by Jsunn on 2008-12-10
Ok, I am a very green coffee bean here....

   but this seemed to work for me too!  Has this been reported?  

Thanks, 
Jason

---

### Post by hobbystas on 2008-12-15
Now, that is strange...

Here is my situation:
i have an hp deskjet 500 (kinda old, i know, but serves me well) attached via lpt port on a win2k3 server system. printer is shared. Some months ago I made a fresh installation on my laptop, used ubuntu 8.04.1. Configured the remote printer, everything worked out just fine, as i have done before in ubuntu 7.10. Today I noticed, I'm not able to print through evince, which I was before! But still able to print through OO. Trying to figure out what's wrong, I probably messed up. I used the cups web interface, enabled the kerberos authentication (that was probably a BIG mistake) and now I am not able to make any changes on the printers configuration! not even unmark the keberos authentication. Through the web interface, at "save changes" cups complains with 404 error and through system->administration->printing it says I'm not authorized. Now, since I haven't change any passwords lately and since I have different username/password for each machine, I suppose cups needs the 2k3 server password, which I'm not able to fill in any were. Something tells me the hole kerberos story works a little different. Any ideas how to fix that? How to reconfigure cups or even reinstalling it but without keeping current configuration?

Since I wasn't able to copy the printer, I installed Acrobat Reader, and that was able to print!!

To summarize: a couple of days ago, i installed some updates, among them an update for cups. Could that be a reason for that I wasn't any more able to print through evince? could that be a bug? can anyone else confirm this?

P.S. It's my first reply ever!! Sorry if this shouldn't be posted here.

thanx in advance.

---

### Post by Yfrwlf on 2009-02-25
Had the same problem.  It worked one time, but something I did, throughout messing with usernames and passwords, made something with authentication mess up.  Perhaps whatever is causing the new pop up that tells you that you need to authenticate when you try to print, or checks if you do, is having a problem.

Any way, the copying the printer technique worked for me too.  Thanks for this thread. :)

---

### Post by Naucher on 2009-03-14
> **Yfrwlf said:**
> Had the same problem too.  It worked one time, but ...

Unfortunately the "copy-printer-solution" only works once ;-(

After copying the printer I can print once from i.e. Document Viewer.  The second time I try printing, I get this message: "Too many failed attempts"

Printing from OOo works OK though.

Is this unique?
- since I have great trouble finding forums with suggestions to put this problem away.

Is there perhaps anyone who might be able to read and "translate" an error-log?
Is this error confined to Canon-printers?
What do I do?
It annoys me like ... not being able to do any printing.

/Naucher

---

### Post by Yfrwlf on 2009-03-18
> **Naucher said:**
> Unfortunately the "copy-printer-solution" only works once ;-(

After copying the printer I can print once from i.e. Document Viewer.  The second time I try printing, I get this message: "Too many failed attempts"

Printing from OOo works OK though.

Is this unique?
- since I have great trouble finding forums with suggestions to put this problem away.

Is there perhaps anyone who might be able to read and "translate" an error-log?
Is this error confined to Canon-printers?
What do I do?
It annoys me like ... not being able to do any printing.

/Naucher

Don't know anything more myself, only that printing to Linux machines works fine at home, it was just the Samba/Windows setup at work that I was having a hard time with since I had to authenticate to a Windows AD domain to be able to print.

---

### Post by pdoma on 2009-03-18
Are you using any desktop themes other then the default human or Clear looks.  There was a big bug in previous releases that caused PC to hang when you wanted to print from OOo. Simply switch your desktop theme to the default and that should fix the issue.

---

### Post by Naucher on 2009-03-19
It's solved, actually :-)

With the help form the Danish Ubuntu-forum I was able to address the problem and its solution like this:

Via the Terminal, and the command:  ```
sudo gedit /etc/cups/printers.conf
``` I found, and altered this:
```
<DefaultPrinter iP4500>
**# **AuthInfoRequired username,password
Info Canon Pixma iP4500
Location Kontoret
**DeviceURI smb://*username*:*password*@/ENGHA ... erver-1PR2**
State Idle
StateTime 1237136198
Accepting Yes
Shared No
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>
```

The problem at my place lies in the print-server (and perhaps Samba).
What I did was defining a user and his password ind the line "DeviceURI..." and after that I put the line "AuthInfoRequired..." to pause using # in the beginning of the line.

I don't quite understand why this works, since "#" stops the execution of that line ... but at the same time I had to realize, that wihtout giving username and password in the other line mentioned, it didn't work.

With both alterations ... it does work for me :-)

**/Naucher**

---

### Post by akelsall on 2009-04-20
The copy technique worked for me as well (System | Administration | Printing. Then right-click the current default printer and select Copy).  Very bizarre. Before this fix, I could only print from Open Office. Anytime I tried to print something form a website, I was only given the option to print to PDF. Now, I can print to a real printer!!

Big thanks for this tip!!!

Andy

---

### Post by newenglandcs on 2009-05-13
I know this is an old post, but I was having the same problem under Ubuntu 9.04.  The problem was with a Dell printer hosted via Samba on a Windows machine (I think).  I could only print from OO and received the "can't prompt for authorization" message when trying to print from anywhere else.

I copied the printer and added a "2" at the end of the name, and this fixed the problem.  I ran this by a linux "guru" and he mentioned that when setting up the printer, if you use the same name that the printer is named under the machine it is attached to, that could be part of the reason for the error message.

I don't know if this is true, but just wanted to throw it out there.

Thanks for the fix...

---

### Post by yaztromo on 2009-05-18
I just had this problem after upgrading a system to 9.04.

To fix I opened /etc/cups/printers.conf and removed the line "AuthInfoRequired negotiate". I haven't rebooted yet, but it seems to be working okay now.

---

### Post by levicivita on 2009-06-02
Having the same issue in Ubuntu 9.04.  

Have had moderate luck reading this posting as well as [http://ubuntuforums.org/showthread.php?t=987189](http://ubuntuforums.org/showthread.php?t=987189) and many others.

Right now I can print test pages and from Open Office, but not from PDF viewers for example.  The error message from /var/log/cups/error_log:

E [02/Jun/2009:18:12:07 -0500] cupsdAuthorize: Local authentication certificate not found!
E [02/Jun/2009:18:12:07 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [02/Jun/2009:18:12:38 -0500] [Job 10] Session setup failed: NT_STATUS_NO_SUCH_FILE
E [02/Jun/2009:18:12:40 -0500] [Job 10] Session setup failed: NT_STATUS_LOGON_FAILURE
E [02/Jun/2009:18:12:43 -0500] [Job 10] Tree connect failed (NT_STATUS_ACCESS_DENIED)
E [02/Jun/2009:18:12:43 -0500] PID 6763 (/usr/lib/cups/backend/smb) stopped with status 2!
E [02/Jun/2009:18:14:22 -0500] Print-Job: Unauthorized
E [02/Jun/2009:18:15:00 -0500] Print-Job: Unauthorized

This is a serious error w.r.t. basic functionality.  I love Ubuntu in general, but this needs to get fixed.

---

