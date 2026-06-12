---
title: "How can we check"
date: 2012-11-05
forum: Programming Talk
---

### Post by Mohan1289 on 2012-11-05
How can we check whether a program is installed or not??

Suppose i want to write a script which checks whether mysql is installed  or not..

If installed it should ask me the password of root... to connect to Database and create a database...

If not it should ask me whether i want to install mysql or not??

if i entered **"y "** it should install mysql and mysql server

what i don't understand is how can i check whether that  program is installed or not??

if it is installed suppose if i try to enter into database as root

```
mysql -uroot -p
```

if i enter i like this in command prompt it will prompt me for password but how can i do that in shell script??

and if i am installing newly using
```


apt-get install mysql
apt-get install mysql-server

```

how can i prompt for root password ??

generally it will ask me for root password but how is that possible if i try to install through shell script??

does it possible that it will automatically ask me to enter root password even i am doing that in shell script???

i mean shell script is series of commands right?

---

### Post by 2F4U on 2012-11-05
> How can we check whether a program is installed or not??

Have you already tried whereis, for example

whereis mysql

---

### Post by codemaniac on 2012-11-05
In order to check if a package is installed on your system ,
```
dpkg -s <packagename>
```
or
```
dpkg-query -l <packagename>
```

---

### Post by Mohan1289 on 2012-11-05
> **2F4U said:**
> Have you already tried whereis, for example

whereis mysql

yeah i tried after posting this 

i can install mysql with prompting passwords all

but what i don't get it 

how to check whether mysql installed or not

and 

after connecting to database how to execute a mysql command??

here is the script i tried

```

#!/bin/bash

ROOT_UID=0
E_NOTROOT=87
if ["$UID" -ne "$ROOT_UID"]; then
echo "You Must be root/sudo to run this script"
exit $E_NOTROOT
fi
sudo apt-get install mysql-server-5.5

sudo apt-get install mysql-client-5.5

echo "Opening Mysql"

mysql -u root -p



```

until the last command it's commands are performed in shell then after connecting to database i don't understand how to perform a mysql operation

for example show databases;

---

### Post by Mohan1289 on 2012-11-05
> **codemaniac said:**
> In order to check if a package is installed on your system ,
```
dpkg -s <packagename>
```or
```
dpkg-query -l <packagename>
```


look at this thumb nail

i checked whether mysql is installed or not it said it's not installed yet when i typed mysql it opened why??

do i have to give complete name like 

```
$dpkg -s mysql-server-5.5
``` ??

it worked when i gave complete name

and how can i determine whethere mysql is installed or not in the system???

like
```

if installed 
do something
else
install mysql
do something??

```
do i have to check for a directory?? in /bin ??

---

### Post by Vaphell on 2012-11-05
why not simply attempt to install? it won't let you if it's installed, so there is no problem with that.
Besides dpkg -s seems to return 0 when the package is installed and 1 when it's not so you should be able to use simple if on that
```
if dpkg -s <package>; then ....; else ...; fi
```

> i checked whether mysql is installed or not it said it's not installed yet when i typed mysql it opened why??

because package name is not the same as the name of binary file that is located in some place mentioned in PATH.
On my 10.04 box i don't have fullblown mysql installed and this is what i get
```
$ mysql
The program 'mysql' can be found in the following packages:
 * mysql-client-core-5.1
 * mysql-client-5.0
 * mysql-cluster-client-5.1
Try: sudo apt-get install <selected package>
```


Besides you can stop attaching screen dumps, you can easily copy-paste from terminal: just highlight the text in terminal and middle-click in firefox, or use ctrl+shift+c, ctrl+v. And don't forget to wrap it in [code][/co****de] tags

---

### Post by Mohan1289 on 2012-11-05
> **Vaphell said:**
> why not simply attempt to install? it won't let you if it's installed, so there is no problem with that.

Besides you can stop attaching screen dumps, you can easily copy-paste from terminal: just highlight the text in terminal and middle-click in firefox, or use ctrl+shift+c, ctrl+v. And don't forget to wrap it in ```

``` tags

oh that's for the previous script

suppose someone who newly installed the linux run that script it should do all this 


```
1. check whether the user is admin or not
2.Checks whether the user exist or not
3. Then switch to the directory
4. asks for the file name which he/she wants to deploy
5.deploy the file
6.check weather mysql is installed or not
7.if not prompt the user whether he wants to install or not
8. if no then exit
9.if yes install mysql-server-5.5
10. then use mysql-uroot -p (enter into mysql as root)
11. then dump the .sql file which is in the previously deployed directory

```

what i don't get it is how can run mysql commands in bash script??

---

### Post by vasa1 on 2012-11-05
What is the package name? You need to use that when you install.
Maybe there's just no package called mysql whereas there is a command called mysql. IMO, you may have to find the correct package name from the list you get by running "dpkg --get-selections" as already suggested.

---

### Post by Mohan1289 on 2012-11-05
> **vasa1 said:**
> What is the package name? You need to use that when you install.
Maybe there's just no package called mysql whereas there is a command called mysql. IMO, you may have to find the correct package name from the list you get by running "dpkg --get-selections" as already suggested.

pardon i don't get it can you explain in a bit detailed manner

---

### Post by Vaphell on 2012-11-05
you can also use shell suggestion/autocompletion feature (tab)
**dpkg -s mysql[tab][tab]** shows me the full list of mysql* packages.

---

### Post by Mohan1289 on 2012-11-05
> **Vaphell said:**
> you can also use shell suggestion/autocompletion feature (tab)
**dpkg -s mysql[tab][tab]** shows me the full list of mysql* packages.


Thank you vaphell i understand why dpkg -s showed not installed..

when i typed dpkg -s mysql-server-5.5

it showed me the details...

can you please tell how to connect to database as root user and then execute mysql commands through shell script

i am able to connect to database but i am unable to execute mysql commands through shell script file

---

### Post by codemaniac on 2012-11-05
You can  use dpkg-query for your purpose, it accepts wild cards, too.
To check if mysql is installed or not in your system use the below,

```
dpkg-query -l "mysql*"
```
see man dpkg-query for more info.

---

### Post by Mohan1289 on 2012-11-05
> **codemaniac said:**
> You can  use dpkg-query for your purpose, it accepts wild cards, too.
To check if mysql is installed or not in your system use the below,

```
dpkg-query -l "mysql*"
```see man dpkg-query for more info.
```

ii  mysql-client-c 5.5.24-0ubuntu MySQL database core client binaries
ii  mysql-common   5.5.24-0ubuntu MySQL database common files, e.g. /etc/mysql
```


What does ii mean?? 
does it means installed??

---

### Post by codemaniac on 2012-11-05
> **Mohan1289 said:**
> ```

ii  mysql-client-c 5.5.24-0ubuntu MySQL database core client binaries
ii  mysql-common   5.5.24-0ubuntu MySQL database common files, e.g. /etc/mysql
```


What does ii mean?? 
does it means installed??

from manpages 

> 

              dpkg-query -l 'libc6*'

              The  first  three columns of the output show the desired action,
              the package status, and errors, in that order.

              Desired action:
                u = Unknown
                i = Install
                h = Hold
                r = Remove
                p = Purge

              Package status:
                n = Not-installed
                c = Config-files
                H = Half-installed
                U = Unpacked
                F = Half-configured
                W = Triggers-awaiting
                t = Triggers-pending
                i = Installed

              Error flags:
                <empty> = (none)
                R = Reinst-required

              An uppercase status or error letter  indicates  the  package  is
              likely  to  cause  severe  problems. Please refer to dpkg(1) for
              information about the above states and flags.

---

### Post by Mohan1289 on 2012-11-05
when i tried this command it is showing that mysql-server-5.5 is installed but when i run the script it's not displaying like that.. correct me if i am wrong

```
 
#!/bin/bash
if [ dpkg --list mysql-server-5.5 | egrep -q ^ii ]; then
echo " MySql is already Installed"
else
echo "MySql is not Installed"
fi

```

i wrote this to test whether mysql is installed or not but it's out put is not installed

but when i run that command in command prompt 

```

krishna@ubuntu:~/Desktop/test$ dpkg --list mysql-server-5.5
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                           Version                        Description
+++-==============================-==============================-============================================================================
ii  mysql-server-5.5               5.5.24-0ubuntu0.12.04.1        MySQL database server binaries and system database setup

```

Where lay my fault?

---

### Post by spjackson on 2012-11-05
The syntax is thrown by the test '[' when there are no arguments to the test.

You should also get an error message:
```

egrep: ]: No such file or directory

```
I cannot imagine why you are not getting that.

Here's one way to do it:
```

#!/bin/bash

if dpkg --list mysql-server-5.5 2>/dev/null | egrep -q ^ii ; then
    echo " MySql is already Installed"
else
    echo "MySql is not Installed"
fi

```

---

### Post by Mohan1289 on 2012-11-05
> **spjackson said:**
> The syntax is thrown by the test '[' when there are no arguments to the test.

You should also get an error message:
```

egrep: ]: No such file or directory

```I cannot imagine why you are not getting that.

Here's one way to do it:
```

#!/bin/bash

if dpkg --list mysql-server-5.5 2>/dev/null | egrep -q ^ii ; then
    echo " MySql is already Installed"
else
    echo "MySql is not Installed"
fi

```

does that mean i have to use **[       ]** **'s **only when there is file/directory?

---

### Post by Lars Noodén on 2012-11-05
Do you want to look for a specific version of mysql-server or just for mysql-server in general?

'[' is not needed except when you do a [test](http://manpages.ubuntu.com/manpages/precise/en/man1/test.1.html), and you might want to route output to /dev/null

```

#!/bin/sh
if dpkg -s mysql-server &> /dev/null ; then
  echo "MySql server is already Installed"
else
  echo "MySql server is not Installed"
fi

```

---

### Post by Mohan1289 on 2012-11-05
> **Lars Noodén said:**
> Do you want to look for a specific version of mysql-server or just for mysql-server in general?

'[' is not needed except when you do a [test]("http://manpages.ubuntu.com/manpages/precise/en/man1/test.1.html"), and you might want to route output to /dev/null

```

#!/bin/sh
if dpkg -s mysql-server &> /dev/null ; then
  echo "MySql server is already Installed"
else
  echo "MySql server is not Installed"
fi

```

No no particular version.. i just wanna check whether in that system mysql installed or not that's all

if not i want  to prompt whether he/she wants to install it?

if they type y then it should install and if not it should just quit

---

### Post by ofnuts on 2012-11-05
> **Mohan1289 said:**
> How can we check whether a program is installed or not??

Suppose i want to write a script which checks whether mysql is installed  or not..

If installed it should ask me the password of root... to connect to Database and create a database...

If not it should ask me whether i want to install mysql or not??

if i entered **"y "** it should install mysql and mysql server

what i don't understand is how can i check whether that  program is installed or not??

if it is installed suppose if i try to enter into database as root

```
mysql -uroot -p
```if i enter i like this in command prompt it will prompt me for password but how can i do that in shell script??

and if i am installing newly using
```


apt-get install mysql
apt-get install mysql-server

```how can i prompt for root password ??

generally it will ask me for root password but how is that possible if i try to install through shell script??

does it possible that it will automatically ask me to enter root password even i am doing that in shell script???

i mean shell script is series of commands right?

The "canonical" way (pardon the pun) is to provide an installation package for your stuff (.DEB file) with a dependency on mysql, so that the package manager install mysql if it's not installed when someone installs your package.

You cannot depend on the user's ability to install packages when your script is run. He could be a plain user with no privileges.

---

### Post by Mohan1289 on 2012-11-05
> **ofnuts said:**
> The "canonical" way (pardon the pun) is to provide an installation package for your stuff (.DEB file) with a dependency on mysql, so that the package manager install mysql if it's not installed when someone installs your package.

You cannot depend on the user's ability to install packages when your script is run. He could be a plain user with no privileges.

How can i do that?? i mean without depending on the user ability to install packages when my script is run???

how can i connect to Database automatically and execute mysql commands... 

like i have to connect to database automatically and show the databases..

but when i tried like this it showed me no results

```

mysql -u root -p #Since it will prompt the user for the root password
show databases;

```

what i am getting is 

it is prompting me for password all right but  it is not executing the **show databases;** command why so??

---

### Post by ofnuts on 2012-11-06
> **Mohan1289 said:**
> How can i do that?? i mean without depending on the user ability to install packages when my script is run???
As I said... you make sure that when your script is installed (*)(because before being run, it must be installed) it drags with it the required mysql installs. This what the package manager in Linux distributions is all about. Individual packages (here, the one with your script) list their dependencies and the package manager makes sure the required packages get also installed. So your script doesn't need to worry about mysql, because if it's there and running, then the package manager also made sure mysql would be available.

This is the standard way of making sure your needed packages will be available but it is rather theoretical when it comes to databases:  these things always require some setup to work efficiently and in any case installing an RDBMS is not a trivial thing on a system, it has consequences (RAM and CPU usage, even when not in use, backups...) so in practice you can't really install it implicitly. Furthermore these often run on a different system, you can only have a dependency on the RDBMS client, and hope that the server part is already available somewhere. So here it would be completely legitimate to just state the dependency and expect a system administrator to install mysql independently (this would also leave him the choice of the edition of mysql). 

(*) and it is of course installed by someone who has the privileges to do so...

---

### Post by Mohan1289 on 2012-11-06
> **ofnuts said:**
> As I said... you make sure that when your script is installed (*)(because before being run, it must be installed) it drags with it the required mysql installs. This what the package manager in Linux distributions is all about. Individual packages (here, the one with your script) list their dependencies and the package manager makes sure the required packages get also installed. So your script doesn't need to worry about mysql, because if it's there and running, then the package manager also made sure mysql would be available.

This is the standard way of making sure your needed packages will be available but it is rather theoretical when it comes to databases:  these things always require some setup to work efficiently and in any case installing an RDBMS is not a trivial thing on a system, it has consequences (RAM and CPU usage, even when not in use, backups...) so in practice you can't really install it implicitly. Furthermore these often run on a different system, you can only have a dependency on the RDBMS client, and hope that the server part is already available somewhere. So here it would be completely legitimate to just state the dependency and expect a system administrator to install mysql independently (this would also leave him the choice of the edition of mysql). 

(*) and it is of course installed by someone who has the privileges to do so...


can you Please give me a Example so that i can understand??

---

