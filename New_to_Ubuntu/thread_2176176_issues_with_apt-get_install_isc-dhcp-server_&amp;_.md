---
title: "issues with apt-get install isc-dhcp-server &amp; sudo apt-get install update commands on"
date: 2013-09-23
forum: New to Ubuntu
---

### Post by ewPxkfp on 2013-09-23
i'm a newbie in the Ubuntu server environment. Installed Ubuntu 12 on our dell poweredge server at work. 
After successful installing ubuntu, went ahead to run command - sudo apt-get install isc-dhcp-server at command line 
to enable dhcp service. However each time i execute the command i keep getting the error message "unable to locate package isp-dhcp server ubuntu". 

Also the update command "sudo apt-get install update" (to install newest versions of packages) also comes up with error message "400 bad response from server" each time i run this command at command line.


Please can someone explain to me what i'm doing wrong and how to resolve these issues.



thanks
Tolu

---

### Post by Elfy on 2013-09-23
> unable to locate package isp-dhcp server ubuntuthe package is isc-dhcp-server

so 

```
sudo apt-get install isc-dhcp-server
```

> sudo apt-get install updateThere is no update package, if you're trying to update then it's

```
sudo apt-get update
```

Have a look at 

```
man apt-get
```

---

### Post by jerome1232 on 2013-09-23
apt-get update updates your list of packages, it needs to be run once before you can install any packages (the package you want to install should work after an update)
```
sudo apt-get update
```

to do upgrades, you use apt-get upgrade
```
sudo apt-get upgrade
```

---

