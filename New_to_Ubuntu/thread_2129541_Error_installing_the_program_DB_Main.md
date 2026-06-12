---
title: "Error installing the program DB Main"
date: 2013-03-26
forum: New to Ubuntu
---

### Post by flordelis8 on 2013-03-26
Hello!

I'm a beginner in ubuntu/xubuntu, and I followed this document to install the db-main: [http://www.rever-sa.com/DISTRIBUTION/DB-MAIN/readme.html](http://www.rever-sa.com/DISTRIBUTION/DB-MAIN/readme.html)
I tried the two topics, both the installation for single user and for all users. I used the terminal command "sudo thunar" for this, but when I clicked in the icon of executable db_main in bin directory, nothing happens. And when I called "db_main" on terminal, I get the following message: "Error while loading shared libraries: libjpeg.so.62: cannot open shared object file: No such file or directory".

I need some help to do this instalation correctly!

Thanks!



[LIST]
[*]_Installation for single user_
Extract the *dbm-9xx-linux-setup.tar.gz* or *dbm-deasy-9xx-linux-setup.tar.gz* (with the DEASY plug-in) archive in the directory of your choice:cd ~/db-main
tar -xf dbm-9xx-linux-setup.tar.gz *(or tar -xf dbm-deasy-9xx-linux-setup.tar.gz)*
Edit the *.bashrc* file (*.profile* in some environment) in the home directory and add the following lines (adapt the *~/db-main/bin* directory to the one chosen previously):export DB_MAIN_BIN=~/db-main/bin
export PATH=$DB_MAIN_BIN:$PATH
export LD_LIBRARY_PATH=$DB_MAIN_BIN:$DB_MAIN_BIN/../java/jre/lib/i386/client:$LD_LIBRARY_PATH
*#CLASSPATH modification only for dbm-deasy-9xx-linux-setup.tar.gz*
export CLASSPATH=.:$DB_MAIN_BIN/../plugins/deasy/lib/jidbmjava.jar:$DB_MAIN_BIN/../plugins/deasy/lib/sqlite-jdbc-3.6.20.1.jar:$CLASSPATH
[*]_Installation for all users_
Extract the *dbm-9xx-linux-setup.tar.gz* archive in /usr/local/db-main (or any other directory of your choice):cd /usr/local/db-main
sudo tar -xf dbm-9xx-linux-setup.tar.gz *(or sudo tar -xf dbm-deasy-9xx-linux-setup.tar.gz)*
Change the permissions so that any user can execute db_main:sudo chmod a+x /usr/local/db-main/bin/db_main
Edit the global bash profile for all users (something like */etc/bash.bashrc*) and add the following lines (adapt the */usr/local/db-main/bin* directory to the one chosen previously):export DB_MAIN_BIN=/usr/local/db-main/bin
export PATH=$DB_MAIN_BIN:$PATH
export LD_LIBRARY_PATH=$DB_MAIN_BIN:$DB_MAIN_BIN/../java/jre/lib/i386/client:$LD_LIBRARY_PATH
*#CLASSPATH modification only for dbm-deasy-9xx-linux-setup.tar.gz*
export CLASSPATH=.:$DB_MAIN_BIN/../plugins/deasy/lib/jidbmjava.jar:$DB_MAIN_BIN/../plugins/deasy/lib/sqlite-jdbc-3.6.20.1.jar:$CLASSPATH
[/LIST]

[COLOR=#000000][FONT=Times New Roman]To run DB-MAIN, there are also two approaches:[/FONT][/COLOR]

[LIST]
[*]_Execute the file *db_main*_ as a normal user from the command prompt.
[*]_Create a shortcut in your desktop_ that calls a shell file that contains something like this:
#!/bin/sh
export DB_MAIN_BIN=/the-path-to-the-db-main-bin-directory
export PATH=$DB_MAIN_BIN:$PATH
export LD_LIBRARY_PATH=$DB_MAIN_BIN:$DB_MAIN_BIN/../java/jre/lib/i386/client:$LD_LIBRARY_PATH
*#CLASSPATH modification only for dbm-deasy-9xx-linux-setup.tar.gz*
export CLASSPATH=.:$DB_MAIN_BIN/../plugins/deasy/lib/jidbmjava.jar:$DB_MAIN_BIN/../plugins/deasy/lib/sqlite-jdbc-3.6.20.1.jar:$CLASSPATH
cd /the-path-to-the-db-main-bin-directory/
db_main
Adapt *the-path-to-the-db-main-bin-directory* to your environment, save the shell file in the DB-MAIN bin directory (called db_main.sh for example) and give the *execute* permissions for all users.
Finally, put the following command in the shortcut:
/bin/sh /the-path-to-the-db-main-bin-directory/db_main.sh
[/LIST]

---

