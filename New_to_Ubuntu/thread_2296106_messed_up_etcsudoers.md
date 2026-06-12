---
title: "messed up etc/sudoers"
date: 2015-09-23
forum: New to Ubuntu
---

### Post by rburkartjo on 2015-09-23
running 14.04. i tired the recovery mode but could not install my backup get this message:
sudo gedit /etc/sudoers
>>> /etc/sudoers: syntax error near line 20 <<<
>>> /etc/sudoers: syntax error near line 20 <<<
sudo: parse error in /etc/sudoers near line 20
sudo: no valid sudoers sources found, quitting
sudo: unable to initialize policy plugin
ray@nightmare:~$ 
any ideas/tks

---

### Post by sandyd on 2015-09-23
save this somewhere, boot to recovery, and move it to /etc/sudoers
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
Defaults        mail_badpass
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

### Post by rburkartjo on 2015-09-23
sandy what would be the command to do that

---

### Post by yetimon_64 on 2015-09-23
> **sandyd said:**
> save this somewhere, boot to recovery, and move it to /etc/sudoers
...

> **rburkartjo said:**
> sandy what would be the command to do that

Open gedit and copy/paste the contents in the code box by sandyd.

 Save to your desktop as "sudoers". **Important - change the permissions to 0440 **with the command,
```
chmod 0440 $HOME/Desktop/sudoers
```
Note these permissions will allow the sudoers file to work correctly when you are finished in recovery mode.

Now boot to a recovery mode screen, ensure the drive is mounted as read/write; you may need to choose the option to remount the root drive to do so.

Once the root partition is writable choose the option to "drop to a root prompt". Then you can move the file to the /etc folder as root. 
The command,
```
mv /home/<your-username>/Desktop/sudoers /etc/sudoers
``` _*Reminder*_, you are on a root prompt so "sudo" is not needed in this instance. Also change <your-username> in the command to that of your username on your install.

The ownership of the file after doing so, should also change to that of root. If the file is not owned by root change it by the command,
```
chown root:root /etc/sudoers
``` _*Reminder*_, you are on a root prompt so "sudo" is not needed in this instance.

Once the file is moved and its permissions and ownership are correct, reboot back into your installation and test out if sudo is working correctly.

---

### Post by ajgreeny on 2015-09-23
And if all that works for you, please note carefully the first line of the file you just moved.

You don't tell us how you messed up the file in the first place but if you had edited it with **sudo visudo**, which actually uses nano in Ubuntu, there is an automatic check of syntax before you save the file.  Gedit, of course, does not do this for you so you can easily save a bad file and lock yourself out of using sudo if you're nor sure what you're doing.

---

### Post by rburkartjo on 2015-09-23
getting this now how should i correct
ray@nightmare:~$ !445
sudo nautilus
sudo: /etc/sudoers is owned by uid 1000, should be 0
sudo: no valid sudoers sources found, quitting
sudo: unable to initialize policy plugin
ray@nightmare:~$ 
appreciate all you help

---

### Post by yetimon_64 on 2015-09-23
> **rburkartjo said:**
> ...
sudo: /etc/sudoers is owned by uid 1000, should be 0
...

From my previous post,
> The ownership of the file after doing so, should also change to that of  root. **If the file is not owned by root change it by the command**, 
```
chown root:root /etc/sudoers
``` Bolded text is for emphasis.

Ensure the file is owned by root and has 0440 permissions for it to work. Note that on the recovery panel when on a root prompt you don't need sudo to run that command above. You will need to use the recovery boot option again to change it.

**Edit**: as per ajgreeny's post it is usual practice to use nano and sudo visudo to alter the sudoers file.
However once the sudoers file is messed up  "sudo visudo" itself may not work hence the use of gedit etc. above. 
I **think** ajgreeny is suggesting usage to avoid the problem in the first place. yeti.

---

### Post by rburkartjo on 2015-09-23
tks yeti. my new sudoers file was read only for some reason changed it to exe and ran the last command in recovery mode. all fixed. tks everyone

---

### Post by yetimon_64 on 2015-09-23
> **rburkartjo said:**
> tks yeti. my new sudoers file was read only for some reason changed it to exe and ran the last command in recovery mode. all fixed. tks everyone

The sudoers file is read only even for root on this Ubuntu system. Changing that to executable may not be a very good idea. 

Wait for further advice regarding that aspect of the sudoers file permissions. I am surprised that it is working if the permissions have been changed to executable as I thought the security of the system depends heavily on the sudoers file being correctly set up.

I suspect the last command was used only and the permissions are actually non executable if it now works for you. If the permissions are actually 0440 then the file is NOT executable (nor should it be as far as I'm aware). Cheers, yeti.

---

### Post by ajgreeny on 2015-09-23
Indeed I was talking about using **sudo visudo** to avoid the problem in the first place.

For more info on sudoers and root-sudo see
[https://www.google.com/url?q=http://ubuntuforums.org/showthread.php%3Ft%3D1132821&sa=U&ved=0CAoQFjACahUKEwiEqLqC_o3IAhUIDpIKHQcbDyM&client=internal-uds-cse&usg=AFQjCNGm6-yVxnSdLWgPx0bfLy7zcnT1DA](https://www.google.com/url?q=http://ubuntuforums.org/showthread.php%3Ft%3D1132821&sa=U&ved=0CAoQFjACahUKEwiEqLqC_o3IAhUIDpIKHQcbDyM&client=internal-uds-cse&usg=AFQjCNGm6-yVxnSdLWgPx0bfLy7zcnT1DA)
[https://www.google.com/url?q=https://help.ubuntu.com/community/Sudoers&sa=U&ved=0CAUQFjAAahUKEwiEqLqC_o3IAhUIDpIKHQcbDyM&client=internal-uds-cse&usg=AFQjCNFfDX44y6d6S7oSCoqn9BKHykS34Q](https://www.google.com/url?q=https://help.ubuntu.com/community/Sudoers&sa=U&ved=0CAUQFjAAahUKEwiEqLqC_o3IAhUIDpIKHQcbDyM&client=internal-uds-cse&usg=AFQjCNFfDX44y6d6S7oSCoqn9BKHykS34Q) and Root-Sudo link in my signature.

Finally, as you will see in that Root-Sudo link, **never use sudo for any GUI application**; that could be why you have ended up in this mess in the first place as it can cause an unintentional change of ownership and permissions of files which can then lock you out of your own home files and folders.

---

