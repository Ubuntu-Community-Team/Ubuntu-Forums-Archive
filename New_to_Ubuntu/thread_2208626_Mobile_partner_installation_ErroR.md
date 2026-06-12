---
title: "Mobile partner installation ErroR"
date: 2014-03-01
forum: New to Ubuntu
---

### Post by salim3 on 2014-03-01
I have been trying to install Mobile Parnter but i get permission error messages,See code below...
How do i fix the problem.!
```
Installed version: 21.003.28.12.169
Installing version: 21.003.28.12.169

The software is exist. Do you want overwrite it? ([Y]/N):y

Local path is: /usr/local/Vodacom

Installing Modile Partner...chmod: cannot access ‘/usr/local/Vodacom/config’: No such file or directory
usage: sudo [-D level] -h | -K | -k | -V
usage: sudo -v [-AknS] [-D level] [-g groupname|#gid] [-p prompt] [-u user
            name|#uid]
usage: sudo -l[l] [-AknS] [-D level] [-g groupname|#gid] [-p prompt] [-U user
            name] [-u user name|#uid] [-g groupname|#gid] [command]
usage: sudo [-AbEHknPS] [-r role] [-t type] [-C fd] [-D level] [-g
            groupname|#gid] [-p prompt] [-u user name|#uid] [-g groupname|#gid]
            [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AknS] [-r role] [-t type] [-C fd] [-D level] [-g
            groupname|#gid] [-p prompt] [-u user name|#uid] file ...
There is no sudo command in your system,you'd better run the software by root
Press any key to continue...



```

---

### Post by varunendra on 2014-03-03
Welcome to the forums Salim!

Why do you want to install it? Do you need its advanced features or just want to use the modem?

You don't usually need to install anything to just use the modem. You can use the native Network Manager program to configure the connection. However, it doesn't offer the advanced features that Mobile Partner offers.

But you should also be aware that installing/using Mobile Partner also creates a potential security risk - a big one !

The risk is that it adds an entry in /etc/sudoers file that allows 'Everyone' to be able to run sudo commands without requiring to enter any password.

What is **more dangerous** is, as far as I have seen, the Mobile Partner application **[COLOR="#FF0000"]starts the browser with root permissions[/COLOR]**. IF that happens, not only that would causes some confusions (like anything you download will go in root's home instead of yours), but would also be almost a written invitation to the bad guys on the internet to invade your system.

---

### Post by salim3 on 2014-07-08
Hi,
I get this message when I want to install mobile partner on ubuntu,
I tried changing the install file's PERMISSION to executable but still not luck,,
Below is the message i get.

Please input the absolute path for install[/usr/local/Modile_Partner]: 

Local path is: /usr/local/Modile_Partner

Installing Modile Partner...chmod: cannot access ‘/usr/local/Modile_Partner/config’: No such file or directory
usage: sudo -h | -K | -k | -V
usage: sudo -v [-AknS] [-g group] [-h host] [-p prompt] [-u user]
usage: sudo -l [-AknS] [-g group] [-h host] [-p prompt] [-U user] [-u user]
            [command]
usage: sudo [-AbEHknPS] [-r role] [-t type] [-C num] [-g group] [-h host] [-p
            prompt] [-u user] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AknS] [-r role] [-t type] [-C num] [-g group] [-h host] [-p
            prompt] [-u user] file ...
There is no sudo command in your system,you'd better run the software by root
Press any key to continue...

sed: can't read MobilePartner.desktop: No such file or directory
chmod: cannot access ‘./driver/*’: No such file or directory
./install: line 502: ./driver/install: No such file or directory
chmod: cannot access ‘./sbin/*’: No such file or directory
chmod: cannot access ‘./hw_pppd’: No such file or directory
chmod: cannot access ‘./hw_pppd’: No such file or directory
./install: line 518: ./hw_pppd/sbin/install_pppd: No such file or directory
cp: cannot stat ‘./hw_pppd’: No such file or directory
cp: cannot stat ‘/usr/local/Modile_Partner/qtlib/lib*.so*’: No such file or directory
mv: cannot stat ‘/usr/local/Modile_Partner/MobilePartner’: No such file or directory
chmod: cannot access ‘/usr/local/Modile_Partner/MobilePartner.bin’: No such file or directory
grep: /usr/local/Modile_Partner/SysConfig.dat: No such file or directory
grep: /usr/local/Modile_Partner/RunInfo.ini: No such file or directory
sed: can't read /usr/local/Modile_Partner/RunInfo.ini: No such file or directory
grep: /usr/local/Modile_Partner/SysConfig.dat: No such file or directory
cp: cannot stat ‘/usr/local/Modile_Partner/sbin/67hw_hook’: No such file or directory
chmod: cannot access ‘/etc/pm/sleep.d/67hw_hook’: No such file or directory
sed: can't read ./UninstallMobilePartner: No such file or directory
sed: can't read ./UninstallMobilePartner: No such file or directory
sed: can't read ./UninstallMobilePartner: No such file or directory
sed: can't read ./UninstallMobilePartner: No such file or directory
sed: can't read ./UninstallMobilePartner: No such file or directory
sed: can't read ./UninstallMobilePartner: No such file or directory
grep: ./UninstallMobilePartner: No such file or directory
                                          [ done ] 

If that's not visible pls see snapshot on attachment.

---

### Post by coffeecat on 2014-07-08
I've merged your new thread with your old one because varundendra made some important observations which you did not respond to. You might wish to consider them.

---

