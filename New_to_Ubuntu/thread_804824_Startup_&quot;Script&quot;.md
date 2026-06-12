---
title: "Startup &quot;Script&quot;"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by markbusu on 2008-05-23
Hi Guys,

I have an application which I want to start as a daemon on start-up of my Linux box.

Command is:

```
mediatomb --interface eth1 --daemon
```

Now... were do i chuck it ? 

:)

Thanks!

---

### Post by Het Irv on 2008-05-23
I'm not 100% sure, but take a look at System-> Prefrences ->Sessions.  Add your command to a new session and it will run when you login to that user. If you want it for multi-users just add it in each.  There might be an easier way, but that is the way that I know.

---

### Post by sisco311 on 2008-05-23
> **markbusu said:**
> Hi Guys,

I have an application which I want to start as a daemon on start-up of my Linux box.

Command is:

```
mediatomb --interface eth1 --daemon
```Now... were do i chuck it ? 

:)

Thanks!

/etc/rc.local
```
gksu gedit /etc/rc.local
```> #!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

**mediatomb --interface eth1 --daemon**
exit 0


make it executable:
```
sudo chmod +x /etc/rc.local
```

---

### Post by quelx on 2008-05-23
[http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/)
or [http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Forums_FAQ#How_can_I_make_Ubuntu_execute_a_script_or_program_at_startup.3F](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Forums_FAQ#How_can_I_make_Ubuntu_execute_a_script_or_program_at_startup.3F)

If you want to be extra fancy pants make a copy of one of the existing init.d scripts and edit it to accommodate your new application

---

### Post by sisco311 on 2008-05-23
> **quelx said:**
> [http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/)
or [http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Forums_FAQ#How_can_I_make_Ubuntu_execute_a_script_or_program_at_startup.3F](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Forums_FAQ#How_can_I_make_Ubuntu_execute_a_script_or_program_at_startup.3F)

If you want to be extra fancy pants make a copy of one of the existing init.d scripts and edit it to accommodate your new application

```
cat /etc/init.d/skeleton
```> ...
# Description:       This file should be used to construct scripts to be
#                    placed in /etc/init.d.
...


---

