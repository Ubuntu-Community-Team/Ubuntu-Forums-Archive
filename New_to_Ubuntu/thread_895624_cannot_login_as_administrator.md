---
title: "cannot login as administrator"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by jchoudhary_rocks on 2008-08-20
Hi
I am using UBUNTU 8.04, I used to login as a normal user with administrative powers in the system , In the control panel i changed my permissions and edited the administrative rights and set administrative password but now i cant login as an root administrator. when ever i try to login as root the message is displayed that administrator is not allowed to login from this screen. So without admin powers i cant update , install or uninstall the softwares etc. please tell me how to login as an administrator and how to restore admin rights to my user account.
Thanks
Jatinder choudhary

---

### Post by Gannon8 on 2008-08-20
Unless you had set a root password, you can't. You may probably be able to change your permissions.

---

### Post by jchoudhary_rocks on 2008-08-20
please tell how to login as administrator to ubuntu 8.04, what are login screens.

---

### Post by tuxxy on 2008-08-20
Have you got the account setup in system > admin > users

---

### Post by louieb on 2008-08-20
select recovery mode and add yourself back to the admin group.
usermod --groups --append admin <user name>

---

### Post by jchoudhary_rocks on 2008-08-20
Ya i have one user account that i chosed while instalation and one is administrator account that is root and i have set password for it also.

---

### Post by lianne_john07 on 2008-08-20
#First thing first, wat your trying to say is that you can't use your administrator account.
#You can't login as administrator on GUI.

---

### Post by mlentink on 2008-08-20
> **jchoudhary_rocks said:**
> Ya i have one user account that i chosed while instalation and one is administrator account that is root and i have set password for it also.

The user you choose at install time already has administrative priviliges through the sudo system.Please refer to [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
As said earlier, restart in recovery mode and add your user back to the admin group. 

Please note that you do not need to set a root password in Ubuntu, and it is even inadvisable to do so.

---

### Post by jchoudhary_rocks on 2008-08-20
can i run ubuntu with administrative account.

---

### Post by Gannon8 on 2008-08-20
You can but it is **HIGHLY** Recommended you don't.

---

### Post by mlentink on 2008-08-20
> **jchoudhary_rocks said:**
> can i run ubuntu with administrative account.

Again: please refer to [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Titan8990 on 2008-08-20
Also, you should note that it against forum policy for us to tell you how to unlock root. I administer a Ubuntu server and the only time I have EVER had to log in as root is to check specific log files (which I wouldn't even have to log in to root for, it just makes it easier).

---

### Post by lianne_john07 on 2008-08-20
#you can try mlentinks advise as long as you don't mess with your /etc/sudoers file...
#then run sudo passwd root (in case you forgot your root password)

---

### Post by jchoudhary_rocks on 2008-08-20
lease tell me where i can get the commands for using the terminal.

---

### Post by lavinog on 2008-08-20
> **jchoudhary_rocks said:**
> can i run ubuntu with administrative account.

There should be no reason to do so.
If you feel that there is a need to do so, please post why you think that. This way it can be remedied correctly since Ubuntu is designed to not require root logins.
Otherwise, it could be that you are just misinformed about superuser access or are using the incorrect terms. In which case read the link mlentink posted.

---

### Post by mlentink on 2008-08-20
Applications>Accessories>Terminal (may use different words, I run a localized version)

You can learn a lot about terminal commands [here]("http://gd.tuwien.ac.at/linuxcommand.org/")


EDIT: in view of the fact that you are obviously a true 'absolute beginner', I advise *very* ***strongly*** against messing with root passwords and the like. You are extremely likely to corrupt your system irretrievably

---

### Post by lianne_john07 on 2008-08-20
#Press ALT + F2
#A run command box will appear
#Type konsole
#There go you're terminal

---

### Post by lavinog on 2008-08-20
> **jchoudhary_rocks said:**
> lease tell me where i can get the commands for using the terminal.

what are you trying to do?

---

### Post by Titan8990 on 2008-08-20
The list of commands you have are in your path directories. In order to see your path you would type:

echo $PATH

by default you would get:

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

Now lets take /bin for example.

```
jordan@einstein:~$ ls /bin
bash                      echo            mount       stty
bunzip2                   ed              mountpoint  su
bzcat                     egrep           mt          sync
bzcmp                     false           mt-gnu      tailf
bzdiff                    fgconsole       mv          tar
bzegrep                   fgrep           nano        tempfile
bzexe                     fuser           nc          touch
bzfgrep                   fusermount      netcat      true
bzgrep                    grep            netstat     ulockmgr_server
bzip2                     gunzip          ntfs-3g     umount
bzip2recover              gzexe           pidof       uname
bzless                    gzip            ping        uncompress
bzmore                    hostname        ping6       vdir
cat                       ip              ps          which
check-foreground-console  kbd_mode        pwd         zcat
chgrp                     kill            rbash       zcmp
chmod                     ln              readlink    zdiff
chown                     loadkeys        rm          zegrep
cp                        login           rmdir       zfgrep
cpio                      ls              rnano       zforce
dash                      lsmod           run-parts   zgrep
date                      lsmod.modutils  sed         zless
dd                        lspci           setpci      zmore
df                        mkdir           setupcon    znew
dir                       mknod           sh
dmesg                     mktemp          sh.distrib
dnsdomainname             more            sleep
```


As you can see there are tons in just this one directory and tons more in the other directories of your path. You can use man to tell you more about the command:

man ls

but the best way is going to be to ask help on the forums for the specific task you are trying to do. This way you will slowly remember and retain the knowledge of certain commands.

To get you started:

cd - change directories
ls - list files and folders in your current directory
pwd - print working (currently in) directory
rm - delete a file
rmdir - delete a directory
mkdir - make a directory
touch - make a file
find - search 

For any of these commands you can put "man" in front of them to view the manual pages:

man find


Good luck!

> #Press ALT + F2
#A run command box will appear
#Type konsole
#There go you're terminal


This thread as a "Ubuntu" prefix yet you give a KDE only command...

---

### Post by lavinog on 2008-08-20
> **lianne_john07 said:**
> #Press ALT + F2
#A run command box will appear
#Type konsole
#There go you're terminal

Ubuntu doesn't have konsole by default
try gnome-terminal instead

---

### Post by Titan8990 on 2008-08-20
Also accessible via Applications -> Accessories -> Terminal 

I always drag it to my bar for quick access and to the AWN bar for my beefier systems.

---

### Post by lianne_john07 on 2008-08-20
#sorry for that i was assuming that his using KDE4 Hardy

---

### Post by drubin on 2008-08-20
> **Gannon8 said:**
> You can but it is **HIGHLY** Recommended you don't.

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by aysiu on 2008-08-20
> **jchoudhary_rocks said:**
> Hi
I am using UBUNTU 8.04, I used to login as a normal user with administrative powers in the system , In the control panel i changed my permissions and edited the administrative rights and set administrative password but now i cant login as an root administrator. when ever i try to login as root the message is displayed that administrator is not allowed to login from this screen. So without admin powers i cant update , install or uninstall the softwares etc. please tell me how to login as an administrator and how to restore admin rights to my user account.
Thanks
Jatinder choudhary There have been a lot of replies, but I don't think anyone fully understands what's going on here.

Do you want *admin* rights restored to your user account?

Or do you want to be able to log in as root graphically?

If it's the former, you can restore *admin* rights by following this tutorial:
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

If it's the latter, there are better ways to obtain root permissions for tasks. You can create a launcher or keyboard shortcut for the command ```
gksudo nautilus
``` for example. This will launch a file browser window with root privileges inside of your regular user session.

---

### Post by bitninja on 2008-08-20
To be able to log in as root from the login window simply go to Settings > Administration (I think) > Login Window and I believe it's under the security tab, there will be a checkbox that says something to the effect of "allow local system administrator to log on" and you just need to check that box. Problem solved.

---

