---
title: "cancel shutdown script help"
date: 2014-01-10
forum: New to Ubuntu
---

### Post by rburkartjo on 2014-01-10
i have a script that runs when i startup

#!/bin/bash
echo xxx | sudo -S sudo shutdown -h 19:00

works fine
am trying to write a script that will cancel if i want. the below doesnt work

#!/bin/bash
echo xxx | sudo -S sudo shutdown -c now

sure i am overlooking the obvious. any ideas
tks

---

### Post by rburkartjo on 2014-01-10
my bad i am trying to run it in lubuntu not ubuntu

---

### Post by rburkartjo on 2014-01-10
if i open a terminal and type sudo shutdown -c and then enter my password it works. sure i have a syntax problem with my script

---

### Post by Lars Noodén on 2014-01-10
You can set sudo so that it does not require a password for shutdown.

```

%rburkartjo ALL=(ALL) NOPASSWD: /sbin/shutdown -h 19:00, /sbin/shutdown -c 

```

With cancelling a [shutdown](http://manpages.ubuntu.com/manpages/saucy/en/man8/shutdown.8.html) order with -c, a time is not needed.  Any text after the -c will be interpretred as the message.  

You can also specify a pattern instead of "19:00" in [sudoers](http://manpages.ubuntu.com/manpages/saucy/en/man5/sudoers.5.html)

---

### Post by rburkartjo on 2014-01-10
tks lars

---

### Post by rburkartjo on 2014-01-10
okay didnt work. when i added that to line to suders it messed me up. i cant get access to the sudoers file using gksudo nautilus. any idea how to access i need to remove the line from sudoers. tks

error message

ray@ray-Latitude-D630:~$ sudo su
sudo: >>> /etc/sudoers: syntax error near line 27 <<<
sudo: parse error in /etc/sudoers near line 27
sudo: no valid sudoers sources found, quitting
sudo: unable to initialize policy plugin
ray@ray-Latitude-D630:~$ 

tks

---

### Post by Lars Noodén on 2014-01-10
It's possible to lock yourself out with sudo.  I guess since that goes with out saying it went unsaid.  :(

You can boot in recovery mode and rem out the offending line, as one option.  

In the future, it is a good practice to use [visudo](http://manpages.ubuntu.com/manpages/saucy/en/man8/visudo.8.html) to edit sudoers.  It won't let you save a broken configuration.  By default it uses nano, which is a user-friendly editor.

---

### Post by sisco311 on 2014-01-10
There is no need to boot into recovery. You can use pkexec to run a command as another user/root
```
pkexec visudo
```

---

### Post by Lars Noodén on 2014-01-10
> **sisco311 said:**
> You can use pkexec to run a command as another user/root
 
Cool.  That seems to work even with a broken sudoers.

---

### Post by Lars Noodén on 2014-01-10
Also, sudoers doesn't like a colon (:****) so you will have to use a ? instead if you want a pattern for the time.  

```

%rburkartjo  ALL=(ALL) NOPASSWD: /sbin/shutdown -c, /sbin/shutdown -h [0-9][0-9]?[0-9][0-9]

```

The method it uses is [glob](http://manpages.ubuntu.com/manpages/saucy/en/man7/glob.7.html)bing rather than regex.  So a ? stands for any single character.

---

### Post by rburkartjo on 2014-01-10
okay i really messed up the suders it now reads

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo   ALL=(ALL:ALL) ALL
 See sudoers(5) for more information on "#include" directives:

#includedir /etc/sudoers.d
what should it read

appreciate all the help. i have a back up but have time to fix

know it is messed up because still cant run gksudo nautilus from the terminal

have learned a lot from you two

---

### Post by rburkartjo on 2014-01-10
still have the error


ray@ray-Latitude-D630:~$ visudo nautilus
usage: visudo [-chqsV] [-f sudoers]
ray@ray-Latitude-D630:~$ sudo visudo
sudo: >>> /etc/sudoers: syntax error near line 27 <<<
sudo: parse error in /etc/sudoers near line 27
sudo: no valid sudoers sources found, quitting
sudo: unable to initialize policy plugin
ray@ray-Latitude-D630:~$

---

### Post by Lars Noodén on 2014-01-10
The default sudoers is like this:

```

#
# This file MUST be edited with the 'visudo' command as root.
#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaults	env_reset
Defaults	mail_badpass
Defaults	secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo	ALL=(ALL:ALL) ALL

# See sudoers(5) for more information on "#include" directives:

#includedir /etc/sudoers.d

```

That should restore the defaults then you can use visudo to work from there.

---

### Post by ajgreeny on 2014-01-10
Here is a standard default sudoers file from 12.04.

Replace your faulty one with this one and then try editing it again for your needs, but this time do it with command ```
sudo visudo
```
```
#
# This file MUST be edited with the 'visudo' command as root.
#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaults        env_reset
Defaults        secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo   ALL=(ALL:ALL) ALL

# See sudoers(5) for more information on "#include" directives:

#includedir /etc/sudoers.d

```

---

### Post by rburkartjo on 2014-01-10
tks aj

---

### Post by rburkartjo on 2014-01-10
aj thats what i have but still having the same problem if i boot into recovery mode what command should i use. note the file is in etc/sudoers.tmp could that be the problem and if so how to fix.

---

### Post by rburkartjo on 2014-01-10
i found this

[http://askubuntu.com/questions/73864/how-to-modify-a-invalid-etc-sudoers-file-it-throws-out-an-error-and-not-allowi](http://askubuntu.com/questions/73864/how-to-modify-a-invalid-etc-sudoers-file-it-throws-out-an-error-and-not-allowi)


but how would i remove the 

ray@ray-Latitude-D630:~$ sudo su
sudo: >>> /etc/sudoers: syntax error near line 27 <<<
sudo: parse error in /etc/sudoers near line 27
sudo: no valid sudoers sources found, quitting
sudo: unable to initialize policy plugin

---

### Post by Lars Noodén on 2014-01-10
You can copy either of the example default sudoers to a file, say /home/rburkartjo/sudoers.orig and then in recovery mode use cp.

```

cp /home/rburkartjo/sudoers.orig /etc/sudoers

```

But [pkexec](manpages.ubuntu.com/manpages/saucy/en/man1/pkexec.1.html) should work without needing to enter recovery mode as mentioned by sisco311.
```

pkexec visudo

```

Then use ctrl-r to read in a file.

Then be sure to use visudo for subsequent editing of sudoers.

---

### Post by rburkartjo on 2014-01-10
tks will try also tried this from the link i posted but didnt work

ray@ray-Latitude-D630:~$ pkexec visudo -f/etc/sudoers.d/%rburkartjo ALL=(ALL) NOPASSWD: /sbin/shutdown -h 19:00, /sbin/shutdown -c
bash: syntax error near unexpected token `('
ray@ray-Latitude-D630:~$ visudo rm -rf /ect/sudoers.d/%rburkartjo ALL=(ALL) NOPASSWD: /sbin/shutdown -h 19:00, /sbin/shutdown -c
bash: syntax error near unexpected token `('
ray@ray-Latitude-D630:~$

---

### Post by Lars Noodén on 2014-01-10
/etc/sudoers.d/ is a directory.  In it you put regular text files containing sudo configurations.   So the following goes in a file

```

%rburkartjo ALL=(ALL) NOPASSWD: /sbin/shutdown -h 19:00, /sbin/shutdown -c

```

If you add it to a regular text file inside the directory /etc/sudoers.d then you have to uncomment the corresponding line in /etc/sudoers to tell it to include files from /etc/sudoers.d

---

### Post by rburkartjo on 2014-01-10
** Joe's Own Editor v3.7 ** (utf-8) ** Copyright © 2008 **
    I    /etc/sudoers.tmp (Modified)  Row 26   Col 26   2:40  Ctrl-K H for help
 the above is what i have to remove from sudoers

---

### Post by rburkartjo on 2014-01-10
okay one other idea could i fix sudoers using a live cd. if so how

tks

---

### Post by Lars Noodén on 2014-01-10
Did pkexec as described in #8 above not work?  If not, what error did it give?

---

### Post by rburkartjo on 2014-01-10
lars it shows correctly as you instructed #13

however file shows as /etc/sudoers.tmp

and i get note on bottom if i try to use wq! to save

Could not create lock. (I) edit anyway, (Q) cancel edit?

---

### Post by sisco311 on 2014-01-10
Are you using joe to edit the file?

Anyway, the error message indicates that another process is accessing the file.  Try to close/kill all instances of the editor you used to edit the file. Delete the temp files created by the editor and visudo: /etc/sudoers~ /etc/sudoers.tmp /etc/sudoers.tmp~ 

If the error persists, try to hit i to edit the file anyway. 

Don't worry about the file being saved by the editor as sudoers.tmp. After the editor is closed visudo will take care that the content of the temp file is copied to the sudoers file. The sudoer file must have read only permissions and some editors can't deal properly with read only files. That's one of the reasons why the .tmp file is needed.

If you still can't edit the file, then you can try Lars Noodén's suggestion in post #18. Save a copy of file in your home directory and copy it over the one in /etc. After copying the file to /etc make sure that is owned by root:root and has 0440 permissions. If you need more detailed instructions just ask.

---

### Post by rburkartjo on 2014-01-10
tks sisco will try in am. retired have plenty of time . also maybe this might help if i try to run a script in the terminal. i get this

ray@ray-Latitude-D630:~$ ./check
sudo: >>> /etc/sudoers: syntax error near line 33 <<<
sudo: >>> /etc/sudoers: syntax error near line 37 <<<
sudo: parse error in /etc/sudoers near line 33
sudo: no valid sudoers sources found, quitting
sudo: unable to initialize policy plugin
ray@ray-Latitude-D630:~$

---

### Post by rburkartjo on 2014-01-10
and deleted joe  text editor. didnt catch that tks.

---

### Post by rburkartjo on 2014-01-10
okay what is the best rm -rf command to remove the temps. tks

---

### Post by rburkartjo on 2014-01-10
i have 4 sudoers files in /etc
sudoers
sudoers.tmp.save
sudoers.tmp~
sudoers~

---

### Post by sisco311 on 2014-01-10
The best rm command is rm -i because it will prompt for confirmation. :)

You need to be root to delete the files, so you will have to use pkexec:
 ```
pkexec rm -i /etc/sudoers.tmp.save
pkexec rm -i /etc/sudoers.tmp~
pkexec rm -i /etc/sudoers~
```

Since your sudoers file is broken you can cheat a little bit and instead of using visudo you can use a regular text editor. First of all backup the original file:
```
pkexec mv /etc/sudoers /etc/sudoers.borked
```

By default, you can't run GUI apps with pkexec, so you will have to use a CLI text editor like nano, vi, vim or joe. In my example I will use nano, but you can pick the one you are more comfortable with.


```
pkexec nano /etc/sudoers
```
copy/paste the content of the file in nano then press Ctrl+o to save the file and Ctrl+x to exit.

set the correct permissions and ownership of the file:
```
pkexec chown root:root /etc/sudoers
pkexec chmod 0440 /etc/sudoers
```

Now check out if sudo works:```
sudo echo 'It'\''s Alive!'
```

---

### Post by rburkartjo on 2014-01-11
sisco tks followed what you posted and fixed. that was great about linux with effort and HELP most anything is fixable.

---

