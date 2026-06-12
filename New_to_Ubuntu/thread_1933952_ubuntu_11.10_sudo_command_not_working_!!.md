---
title: "ubuntu 11.10 sudo command not working !!"
date: 2012-03-01
forum: New to Ubuntu
---

### Post by anand.ayan on 2012-03-01
<< HELP >>
 
 I Just Installed Ubuntu 11.10,and after installing some compiz package i  found that "sudo" is not working and got the fallowing msg
 ">>> /etc/sudoers: syntax error near line 2 <<<
 >>> /etc/sudoers: syntax error near line 2 <<<
 sudo: parse error in /etc/sudoers near line 2
 sudo: no valid sudoers sources found, quitting
 "
 After searching for solution on various forums i tried to edit my sudoers file using live cd since was not able to edit in recovery mode  either ..
 
 Or simply to say i dont have any sudoers file in etc/sudoers.d
 
 how can i get that etc/sudoers.d/REDME file back as default :( !!!
 
 any help ..

---

### Post by Jeanke on 2012-03-01
Hi,

Try to boot from a live cd and check your sudoers file.
Be aware to check the sudoers file on your hard drive and not the one used by the live cd.
As far as I know it should look like this by default:

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults    env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Allow members of group sudo to execute any command after they have
# provided their password
# (Note that later entries override this, so you might need to move
# it further down)
%sudo ALL=(ALL) ALL
#
#includedir /etc/sudoers.d

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```


Make a backup of your existing sudoers file before editing it or creating a new like above!
```
sudo cp /etc/sudoers /etc/sudoers.old 
```
(again make sure to backup the one on your hard drive and not the one of the live cd)

Note: did you change anything to your sudoers file recently? If so, did you use visudo to make this changes?

---

### Post by anand.ayan on 2012-03-01
hi there  As i said earlier  i changed the file using Live Cd and not using visudo :(

if i now copy paste this default code will it run as like before ..let me try again with this code and Message u back the result !!!!

---

### Post by anand.ayan on 2012-03-01
i Just copied pasted your code on the sudoers file ..still it isnt working.. ..  o.O

---

### Post by Jeanke on 2012-03-01
You are sure you edited the file on your hard drive and not just /etc/sudoers (which would be on your live cd) right?

---

### Post by jerome1232 on 2012-03-01
> **anand.ayan said:**
> i Just copied pasted your code on the sudoers file ..still it isnt working.. ..  o.O

How exactly are you doing it from the live cd?

If your writing to /etc/sudoers then that is the live cd version, you must determine what your root partition is 
(from your actual install) look for the one mounted on /
```
mount | grep /dev/
```

Then you boot from live cd, and mount that partiton (let's pretend it's /dev/sda1
```
sudo mount /dev/sda1 /mnt
```
Now you'll place the sudoers file at /mnt/etc/sudoers

---

### Post by anand.ayan on 2012-03-01
well i booting my live cd and clicking the the drive where my original ubuntu is installed then in my commend promt  i am using gksudo nautilus to edit the etc/sudoer.s file of  my  mounted drive not the one  in live cd 

then created the new file and copy pasted your code ..

now let me try "sudo mount /dev/sda1 /mnt
" as you have said ..

will reply after ,,thanks for the help so far ..jerome :)

---

