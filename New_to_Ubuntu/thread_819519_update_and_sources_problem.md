---
title: "update and sources problem"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by rockstar on 2008-06-05
I'm not quite sure what's going on here.  Everytime I boot my computer it manually checks the disks which takes forever.  Also I have trouble updating regularly with the Package Manager, so I use the Terminal.  But today something strange happened and I don't know what's going on.

Here is the Output.

paul@paul-laptop:~$ sudo gedit /etc/apt/sources.list
/usr/bin/sudo: line 1: es: command not found
/usr/bin/sudo: line 2: Compiled: command not found
/usr/bin/sudo: line 3: Add: command not found
/usr/bin/sudo: line 4: Forget: command not found
/usr/bin/sudo: line 5: DIR: command not found
/usr/bin/sudo: line 6: directory: command not found
/usr/bin/sudo: line 7: With: command not found
/usr/bin/sudo: line 8: in: command not found
/usr/bin/sudo: line 9: in: command not found
/usr/bin/sudo: line 10: Line: command not found
/usr/bin/sudo: line 11: LINENUM,: command not found
/usr/bin/sudo: line 12: FILE:LINENUM,: command not found
/usr/bin/sudo: line 13: FUNCTION,: command not found
/usr/bin/sudo: line 14: FILE:FUNCTION,: command not found
/usr/bin/sudo: line 15: Default: command not found
/usr/bin/sudo: line 30: syntax error near unexpected token `('
/usr/bin/sudo: line 30: `Reinitialize source path to empty? select_source_symtab: readin pst found and no symtabs.Can't find a default source filedelete_substitute_path_rulefind_source_linesDebugger convenience ("$foo") variables.'
paul@paul-laptop:~$ 

This happens with the update command as well.

paul@paul-laptop:~$ sudo apt-get update
/usr/bin/sudo: line 1: es: command not found
/usr/bin/sudo: line 2: Compiled: command not found
/usr/bin/sudo: line 3: Add: command not found
/usr/bin/sudo: line 4: Forget: command not found
/usr/bin/sudo: line 5: DIR: command not found
/usr/bin/sudo: line 6: directory: command not found
/usr/bin/sudo: line 7: With: command not found
/usr/bin/sudo: line 8: in: command not found
/usr/bin/sudo: line 9: in: command not found
/usr/bin/sudo: line 10: Line: command not found
/usr/bin/sudo: line 11: LINENUM,: command not found
/usr/bin/sudo: line 12: FILE:LINENUM,: command not found
/usr/bin/sudo: line 13: FUNCTION,: command not found
/usr/bin/sudo: line 14: FILE:FUNCTION,: command not found
/usr/bin/sudo: line 15: Default: command not found
/usr/bin/sudo: line 30: syntax error near unexpected token `('
/usr/bin/sudo: line 30: `Reinitialize source path to empty? select_source_symtab: readin pst found and no symtabs.Can't find a default source filedelete_substitute_path_rulefind_source_linesDebugger convenience ("$foo") variables.'
paul@paul-laptop:~$

---

### Post by ubuntu-freak on 2008-06-05
Do you have the Windows boot partition permanantly mounted in Ubuntu? Best not to. As for your sudo problem, boot into recovery mode and try this command:
 
**apt-get --reinstall install sudo** 
 
That should do it.

---

### Post by drs305 on 2008-06-05
We can investigate your disk checks. Please run and post of the following. Substitute the partition being checked for **sdaX**:
```

sudo tune2fs -l /dev/**sdaX** | grep mount
cat /etc/fstab
```

We can see if it is set up to perform an fdisk on each boot.

As to your other problem, I don't have a definitive answer. You could try purging and reinstalling sudo.

---

### Post by rockstar on 2008-06-06
So, I tried to do both of the above in the recovery mode but got the same error messages.  I also tried to repair the system, but the updater would not connect to the server to update.

I decided to re-install, so I put in the 8.04 LTS and attempted to re-install because my /home is separate partition.  However when I tried to re-install I got the following error message.

Failed to Remove Conflicting Files: The installer needs to remove operating system files from the install target but was unable to do so. The install cannot continue.

I'm using the live-cd right now.  I really hope I don't have to re-format my /home partition

---

### Post by ubuntu-freak on 2008-06-06
> **rockstar said:**
> So, I tried to do both of the above in the recovery mode but got the same error messages.  I also tried to repair the system, but the updater would not connect to the server to update.

I decided to re-install, so I put in the 8.04 LTS and attempted to re-install because my /home is separate partition.  However when I tried to re-install I got the following error message.

Failed to Remove Conflicting Files: The installer needs to remove operating system files from the install target but was unable to do so. The install cannot continue.

I'm using the live-cd right now.  I really hope I don't have to re-format my /home partition

 
Your home partition shouldn't prevent an install. Did you manually delete and create a new root ("/") partition with the installation disc?

---

### Post by rockstar on 2008-06-06
Well I re-installed and fixed whatever it was I broke.  I probably messed up my Sources list following directions meant for Gusty.  Most of the time re-installing is what I do to fix problems.

---

### Post by ubuntu-freak on 2008-06-06
> **rockstar said:**
> Well I re-installed and fixed whatever it was I broke.  I probably messed up my Sources list following directions meant for Gusty.  Most of the time re-installing is what I do to fix problems.
 

 I think a dodgy command removed sudo as well. 
 
What were you trying to do? Have a look at my how-to in sig, may be of some help.

---

### Post by rockstar on 2008-06-06
I think I was trying to install some sources or edit my sources list.  I wanted to install something that required adding a line to the list.


These are the directions I think I was following
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Manual_Method_for_Adding_Repositories](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Manual_Method_for_Adding_Repositories)

---

