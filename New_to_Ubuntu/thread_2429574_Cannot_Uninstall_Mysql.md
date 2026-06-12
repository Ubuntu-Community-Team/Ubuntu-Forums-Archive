---
title: "Cannot Uninstall Mysql"
date: 2019-10-19
forum: New to Ubuntu
---

### Post by jamesbh101 on 2019-10-19
I am not sure what I have done but I am trying to uninstall my sql but I am getting the following error. The def files are in the home directory.

How do I go about uninstalling mysql in this situation? TY.

```
james@shuttle:~$ sudo apt-get remove --purge mysql*
[sudo] password for james: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package mysql-apt-config_0.8.3-1_all.deb
E: Couldn't find any package by glob 'mysql-apt-config_0.8.3-1_all.deb'
E: Couldn't find any package by regex 'mysql-apt-config_0.8.3-1_all.deb'
E: Unable to locate package mysql-apt-config_0.8.3-1_all.deb.1
E: Couldn't find any package by glob 'mysql-apt-config_0.8.3-1_all.deb.1'
E: Couldn't find any package by regex 'mysql-apt-config_0.8.3-1_all.deb.1'
E: Unable to locate package mysql-apt-config_0.8.9-1_all.deb
E: Couldn't find any package by glob 'mysql-apt-config_0.8.9-1_all.deb'
E: Couldn't find any package by regex 'mysql-apt-config_0.8.9-1_all.deb'


```

---

### Post by 0x656b694d on 2019-10-20
You shouldn't point apt-get to your deb files.

You might rather want to see which mysql* packages are installed:
```

$ dpkg-query -W -f='${db:Status-Abbrev} ${binary:Package}\n' "mysql*" | grep "^ii" | cut -d ' ' -f 3
mysql-common

```

Those packages you can purge with apt then.

I personally use synaptic for such things usually.

---

### Post by Impavidus on 2019-10-20
To remove a package with apt-get, you have to provide the name of the package, not of the .deb file providing that package. In your case, the presence of mysql* files in the current directory means that the shell expands mysql* to the names of all those files in the current directory, which is not acceptable to apt-get. apt-get can also expand the expression mysql* to match all mysql packages, but for that the string mysql* has to be passed on to apt-get. So you must prevent expansion of that string by the shell. The following command should work:```
sudo apt-get remove --purge 'mysql*'
```Note the quote characters.

Check the list of packages it wants to remove before proceding.

---

### Post by Holger_Gehrke on 2019-10-20
Wildcards like '*' are expanded by the shell to a list of the files in the current directory that fit. So if you're executing that command in a directory where there are files whose name begin with mysql ... 

You have to protect the wildcard from the shell by either enclosing it in single quotes or by escaping it by putting a '\' before it
```
sudo apt-get-remove --purge mysql\*
```

You might want to check beforehand what you're telling apt to remove. Either run the command with the additional option '--dry-run' or ask the lower level of package management to give you a list of the installed packages ('dpkg -l mysql\*|grep '^ii'').

Holger

Edit: Ninja'd ...

---

### Post by Tadaen_Sylvermane on 2019-10-20
```
apt --purge autoremove mysql
```

should purge everything including not needed dependencies in one shot. no need for a wildcard. seems simpler and safer to me. let apt pick what it wants to remove instead of forcing it with a *. may lose something you don't want to.

---

