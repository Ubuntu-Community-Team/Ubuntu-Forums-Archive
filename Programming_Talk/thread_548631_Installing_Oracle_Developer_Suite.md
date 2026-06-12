---
title: "Installing Oracle Developer Suite"
date: 2007-09-11
forum: Programming Talk
---

### Post by Masterslave on 2007-09-11
Hello,

At my school I'm learning Oracle (PL/SQL, Oracle Forms, Oracle Designer).
I've downloaded the [Oracle Developer Suite for Linux]("http://www.oracle.com/technology/software/products/ids/htdocs/101202linuxsoft.html").
When the downloads are ready I extract the folder from the package and I start up the terminal and I run:
```

bash runInstaller

```
And I get the following output:
```

patrick@komkommer:~$ bash oracle_developer_suite/Disk1/runInstaller 

-------------------------------------------------------------------------------------------------------------------
The OUI Screen may take around 5 to 30 seconds to come up depending upon system performance. Please Wait ....... 
-------------------------------------------------------------------------------------------------------------------

Starting Oracle Universal Installer...

Checking installer requirements...

Checking operating system version: must be redhat-2.1, redhat-3, redhat-4, SuSE-8, SuSE-9 or UnitedLinux-1.0
                                      Failed <<<<

Exiting Oracle Universal Installer, log for this session can be found at /tmp/OraInstall2007-09-11_09-24-33PM/installActions2007-09-11_09-24-33PM.log

```

If I'm correct I have to use Redhat or Suse to install the Oracle Developer Suite.
Is it possible to install this on Ubuntu? (I'm using Gusty on my laptop atm).

Thanks in advance.

---

### Post by pmasiar on 2007-09-11
I managed to install Oracle on Dapper, but when I upgraded, same steps did not worked and I gave up. IIRC I managed to get Oracle working but cx_Oracle python binding would not compile, but I forgot now. You are lucky, I keps some pointers on my personal wiki, so here they are: 

[http://catherinedevlin.blogspot.com/2006/04/oracle-xe-and-ubuntu.html](http://catherinedevlin.blogspot.com/2006/04/oracle-xe-and-ubuntu.html)
[http://www.oracle.com/pls/xe102/homepage](http://www.oracle.com/pls/xe102/homepage)
[http://frits.homelinux.com/wordpress/?p=9](http://frits.homelinux.com/wordpress/?p=9)
[http://www.halfcooked.com/mt/archives/001014.html](http://www.halfcooked.com/mt/archives/001014.html)
[http://www.dizwell.com/prod/node/52](http://www.dizwell.com/prod/node/52)

I would recommend try install on current ubuntu, and if no luck, double-boot to Dapper, and use official Oracle repositories.
Good luck, you will need it!

---

### Post by tachibana on 2008-06-04
Hi,
I want to use my company's Information System on Hardy. We are using Oracle Forms Runtime and Reports Runtime 6i on Windows. I've searched about this but i couldn't find anything. After i tried to work it with Wine but it didn't worked. I couldn't start with .fmb files. Can anybody help me about it?

---

### Post by tachibana on 2008-06-12
Isn't there any solution?

---

### Post by askander on 2008-09-05
I just got the company's application running on forms 6i under wine, it was a hard work, and not everybody has the same luck, here, I'll let you some steps to do it

1) install wine
2) install forms 6i using wine
3) replace the oracle_home with an oracle_home installed originally in windows
4) be careful with the tnsnames.ora, it must have only one tns definition
5) run ifrun60.exe in win98 mode

Hope this helps someone here.

---

### Post by opabecker on 2009-03-17
I'm not sure about the older version of Developer, but to install version 10.1.2, use the command

./runInstaller -ignoreSysPrereqs

I was able to install the software; however, I must note that the reports developer did not link correctly.  I'll have to look into that a bit further.

---

### Post by fsabbagh on 2009-04-13
> **opabecker said:**
> I'm not sure about the older version of Developer, but to install version 10.1.2, use the command

./runInstaller -ignoreSysPrereqs

I was able to install the software; however, I must note that the reports developer did not link correctly.  I'll have to look into that a bit further.

Hi,

Did u ever get the Reports Developer to work properly? I'm about to install Oracle Developer's Suite on Ubuntu and wanted to know how u did.

Thanks,
fsabbagh

---

### Post by reve99 on 2010-03-25
> **opabecker said:**
> I'm not sure about the older version of Developer, but to install version 10.1.2, use the command

./runInstaller -ignoreSysPrereqs

I was able to install the software; however, I must note that the reports developer did not link correctly.  I'll have to look into that a bit further.


I'll try it and provide my feedback through the 9.4 with the same developer version

---

### Post by reve99 on 2010-03-25
failed to start it after installation,
and the reports problem poped up too

---

### Post by opabecker on 2010-11-02
Revisiting this after a long time :)  I recently installed Lucid on my laptop and decided to give it one more try.  I continued to have the same issues.

I then made sure that my LD_LIBRARY_PATH was set to include $ORACLE_HOME/jre/1.4.2/lib/i386/client and $ORACLE_HOME/jre/1.4.2/lib/i386/native_threads, that JAVA_HOME was set to $ORACLE_HOME/jre/1.4.2/bin, and that PATH had $ORACLE_HOME/jre/1.4.2/bin at the front of it.

I then ran "rwbuilder.sh".  I immediately received the error "REP-0004".  I had assumed that this meant things would not work; I usually clicked OK, and then the Report Builder would fail.  However, on a whim, I clicked "Help".  The help window came up as expected, but then, so did the "Welcome to Reports Builder" window!  I checked "Open an existing report" and clicked OK, and I was able to bring in the report and work with it.  However, I had to keep the Help Topic window open, or the builder would crash with the following error:

An unexpected exception has been detected in native code outside the VM.
Unexpected Signal : 11 occurred at PC=0xB4B9E5EA
Function=_XtWindowedAncestor+0x2A
Library=/usr/lib/libXt.so.6

followed by a dump of the current Java thread.

It's not very clean, but this may be usable after all.  I hope this helps someone.  And if anyone is game to figure out the Java error, that would be cool too.

---

### Post by damnated on 2010-11-02
This is very helpful is someone else is stuck on this.
[http://www.pythian.com/news/13291/installing-oracle-11gr2-enterprise-edition-on-ubuntu-10-04-lucid-lynx/](http://www.pythian.com/news/13291/installing-oracle-11gr2-enterprise-edition-on-ubuntu-10-04-lucid-lynx/)

---

### Post by adam s on 2011-02-22
I had the same problems and none of the suggestions above worked for me.
I am running 10.04 Lucid with a 2.6.32-28-generic kernal.

To solve:

1. I run the Oracle Installer to un-install all products.
2. Removed the two Oracle Directories
3. Downloaded the Windows version 10.1.0.2 of the Developer suite
4. Installed using WINE following the instructions on this [page]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=11935").

The only note that I would add is that it only worked when I extracted the two files into Disk1 and Disk2 directories.

Hope this helps all your blues.

Adam

---

