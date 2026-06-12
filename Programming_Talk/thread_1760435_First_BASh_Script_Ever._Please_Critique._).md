---
title: "First BASh Script Ever. Please Critique. :)"
date: 2011-05-16
forum: Programming Talk
---

### Post by GrantStoner on 2011-05-16
This is my first BASh script. I've found need to create a script for installing a LAMP server. As you can see it invokes YUM - this primarily to be used on Fedora installations. Anyhow, that's not important. I'm more concerned if my syntax is correct, etc. So please! Any tips/helpers, comments, criticisms, critiques, etc. are more than welcome!
```
#! /bin/bash

# This is my first real bash script. Gentle criticism accepted. :)

# by Grant Stone    05/15/2011

# TerminallyUncreative        http://terminallyuncreative.they.org
#                            terminallyuncreative@they.org

clear
echo
echo "   You must be 'root' to invoke this script."
echo && echo "   Checking..."
echo
sleep 1

### Run-As "root" Test ###
ROOT_UID=0
E_WRONG_USER=65

if [ "$UID" -ne "$ROOT_UID" ]
    then
        echo "   Only root can run this script."
        echo "   Log in as root and try again."
        echo
        su -
        exit $E_WRONG_USER
    else
        echo "   Welcome, great and mighty root."
        echo "   Today we're going to install a LAMP server on your machine."
fi


### User Permission ###
read -p "   Is this type of action acceptable? (y/n): " variable
case $variable in
y|Y|yes|YES|Yes)
clear
;;
n|N|no|NO|No)
echo && echo "   You said 'no'... GET OUT OF MY SCRIPT!"
echo && sleep 1
exit 0
;;
*)
echo && echo "   You pressed a random series of keys in excitement!"
echo "   Not sure what to do in this condition. Exiting..."
echo && sleep 1
exit 0
;;
esac

### Clean & Update Repos ###
echo && echo "Updating repositories..."
echo && sleep 2
echo "(CLEANING REPOS THOROUGHLY FIRST)" && yum clean all
echo && echo "(NOW, UPDATING REPOSITORIES)" && yum check-update
clear

### Apache (httpd) ###
echo
read -p "Apache (httpd) should be installed already, but can I try anyways? (y/n): " variable
case $variable in
y|Y|yes|YES|Yes)
echo && echo "Installing Apache..."
echo && sleep 2
yum -y install httpd
clear
;;
n|N|no|NO|No)
echo && echo "   You said 'no'... GET OUT OF MY SCRIPT!"
echo && sleep 1
exit 0
;;
*)
echo && echo "You pressed a random series of keys in excitement!"
echo "You have a medical condition. It's making me nervous. Exiting..."
echo && sleep 1
exit 0
;;
esac

### MySQL ###
echo
read -p "The next step is to install MySQL, if I may? (y/n): " variable
case $variable in
y|Y|yes|YES|Yes)
echo && echo "Installing MySQL..."
echo && sleep 2
yum -y install mysql mysql-server
clear
;;
n|N|no|NO|No)
echo && echo "You said 'no'... GET OUT OF MY SCRIPT!"
echo && sleep 1
exit 0
;;
*)
echo && echo "You pressed a random series of keys in excitement!"
echo "You have a medical condition. It's making me nervous. Exiting..."
echo && sleep 1
exit 0
;;
esac

### PHP ###
echo
read -p "Linux --> Apache --> MySQL --> PHP, dare continue? (y/n): " variable
case $variable in
y|Y|yes|YES|Yes)
echo && echo "Installing PHP..."
echo && sleep 2
yum -y install php php-common php-mysql
clear
;;
n|N|no|NO|No)
echo && echo "You said 'no'... GET OUT OF MY SCRIPT!"
echo && sleep 1
exit 0
;;
*)
echo && echo "You pressed a random series of keys in excitement!"
echo "You have a medical condition. It's making me nervous. Exiting..."
echo && sleep 1
exit 0
;;
esac

### Auto-Start httpd And mysqld"
echo
read -p "Is it okay if I set 'httpd' and 'mysqld' services to start at boot? (y/n): " variable
case $variable in
y|Y|yes|YES|Yes)
/etc/init.d/httpd start
/etc/init.d/mysqld start
chkconfig --levels 235 httpd on
chkconfig --levels 235 mysqld on
clear
;;
n|N|no|NO|No)
echo && echo "Okay, remember to do this later!"
echo && sleep 2
clear
;;
*)
echo && echo "You pressed a random series of keys in excitement!"
echo "You have a medical condition. It's making me nervous. Exiting..."
echo && sleep 1
exit 0
;;
esac

### Optional PHP Modules ###
echo
read -p "(OPTIONAL) Would you like to install some extra PHP modules? (y/n): " variable
case $variable in
y|Y|yes|YES|Yes)
echo && echo "Installing extra PHP modules..."
echo &&    sleep 2
yum -y install php-pear php-pdo php-pgsql php-pecl-memcache php-gd php-mbstring php-mcrypt php-xml
clear
;;
n|N|no|NO|No)
echo && echo "That's okay, they're not essential. You may want them later though."
echo && sleep 3
clear
;;
*)
echo && echo "You pressed a random series of keys in excitement!"
echo "You have a medical condition. It's making me nervous. Exiting..."
echo && sleep 1
exit 0
;;
esac

### Closing Statement ###
echo && echo -e "Thanks for using my script to install a LAMP server!\n\nDid it work properly for you?\nQuestions? Improvements?\nhttp://terminallyuncreative.they.org/\nterminallyuncreative@they.org"
echo && echo -e "You should use the 'MySQL Secure Installation feature' to secure your MySQL installation.\nOpen the terminal as root and enter '/usr/bin/mysql_secure_installation'.\nYou will still then need to create a database via 'mysqladmin'."
echo

exit 0
```

---

### Post by TheStroj on 2011-05-17
I've seen worse. 
Nah, just kidding lol. It is not too difficult to create but as long as it works (can't try atm) and is useful it must be great :)

Suggestion: use Zenity to improve the look of your script, google for more info.

---

### Post by roccivic on 2011-05-17
Your script should fail when the commands that it executes fail. Try something along these lines:

```
echo && echo "(NOW, UPDATING REPOSITORIES)" && yum check-update || echo "REPOSITORY UPDATE FAILED, EXITING" && exit 1
```

---

### Post by Rany Albeg on 2011-05-17
Extensive use of echo && echo bla , instead of printf "\n%s" "$arg".
printf and echo are both Bash built-ins.

I got pretty bored while trying to read this script.
Try to be more specific.

---

### Post by GrantStoner on 2011-05-17
I will likely incorporate your suggestion, roccivic, thanks.
@Rany Albeg: I've gotten a lot of negativity towards using && period, and echo. But this how every example showed me when I was learning. I still am.
Thanks guys.

---

