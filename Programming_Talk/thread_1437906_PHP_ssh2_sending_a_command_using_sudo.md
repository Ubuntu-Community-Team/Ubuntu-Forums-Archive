---
title: "PHP ssh2 sending a command using sudo"
date: 2010-03-24
forum: Programming Talk
---

### Post by gdjsmith on 2010-03-24
I've got a linux server that has several scripts that no one wants to run manually.
I created a separate Ubuntu web server with apache and PHP to provide a simple web interface to the scripts on the first linux server.
 
I'm using ssh2_exec to send a command to the first linux server and it works except when I try sending a command that requires sudo.
 
so if the script on the first server is foo.pl
 
I can call it **ssh2_exec($con, "foo.pl");** and this works
HOWEVER **ssh2_exec($con, "sudo foo.pl");** DOES NOT WORK
 
Does anyone have any ideas on how I can make this work?

---

### Post by cdenley on 2010-03-24
What user are you attempting to execute sudo as? Did you configure /etc/sudoers to allow that user to execute foo.pl without a password? What is the full path to foo.pl?

---

### Post by telemalta on 2010-03-25
> **cdenley said:**
> What user are you attempting to execute sudo as? Did you configure /etc/sudoers to allow that user to execute foo.pl without a password? What is the full path to foo.pl?
I'm wondering the same thing.  Here's a post discussing a number of possibilities:

[http://www.frostjedi.com/phpbb/viewtopic.php?f=46&t=15868](http://www.frostjedi.com/phpbb/viewtopic.php?f=46&t=15868)

Per that, the NOPASSWD option was being ignored by the shell when a user SSH'd into it.  Piping the password to sudo didn't work either.

---

