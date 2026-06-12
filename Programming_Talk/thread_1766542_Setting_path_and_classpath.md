---
title: "Setting path and classpath"
date: 2011-05-24
forum: Programming Talk
---

### Post by sandy0594 on 2011-05-24
Hi all,I am lil bit new to Linux platform.Can someone kindly guide me how to set **path **and **classpath** in Ubuntu 10.10..

In windows we go to environment variables and create a new variable **path** for setting path and **classpath** for classpath

```

Variable:PATH
Value   :C:/Program Files/Java/Jdk1.6.0/bin

``````

Variable: CLASSPATH
Value   : **.;**C:/oracle/product/db_1/jdbc/lib/classes12.jar

```The above is the format we set path and class-path in windows..so,how do we do the same thing back here in Ubuntu10.10

---

### Post by r-senior on 2011-05-24
You probably don't need to. Assuming you have installed the JDK from the repositories, a simple example will work out of the box:

```

$ cat Hello.java
public class Hello {
    public static void main(String ... args) {
        System.out.println("hello");
    }
}
$ javac Hello.Java
$ java Hello
hello

```

The PATH is already set up (via /usr/bin/java and a couple more steps via /etc/alternatives).

If you need to compile or run with additional libraries, you can use the -cp option, e.g.

```

$ javac -cp <path-to-jar-file>
$ java -cp <path-to-jar-file>

```

Setting a CLASSPATH variable can just lead to confusion.

If you are using an IDE, it will define its own settings for its Java platforms and libraries (i.e. classpath). Maven will pick up javac and java from the standard path and manage its classpath.

So no need.

---

### Post by sandy0594 on 2011-05-24
As u say,for normal java program path will be set by Ubuntu..But,coming to server side programming like servlets and jsp's and jdbc programming we need to set path and classpath for few jar files..

For eg:

```

import java.sql.*; 
class PureConnection 
{ 
public static void main(String[]args) throws Exception 
{ 
String driver = "oracle.jdbc.driver.OracleDriver"; 
String url = "jdbc:oracle:thin:@localhost:1521:orcl"; 
String user = "scott"; 
String password = "tiger"; 
Class.forName(driver); 
System.out.println("Driver Loaded"); 
Connection con = DriverManager.getConnection(url,user,password); 
System.out.println("connected"); 
con.close(); 
} 
}

```

> 
sandy@ubuntu:~/Java Programs$ javac PureConnection.java
sandy@ubuntu:~/Java Programs$ java PureConnection.java
Exception in thread "main" java.lang.NoClassDefFoundError: PureConnection/java
Caused by: java.lang.ClassNotFoundException: PureConnection.java
    at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
Could not find the main class: PureConnection.java. Program will exit.
sandy@ubuntu:~/Java Programs$ 



For the above program to execute we need to set classpath for classes12.jar available in oracle(C:/oracle/product/db_1/jdbc/lib/classes12.jar).So,how can i set the classpath for that

---

### Post by r-senior on 2011-05-25
As I said above, you can use use the -cp option.

If you must use the CLASSPATH environment variable, and I would advise against it:

```

export CLASSPATH=".:/home/sandy/Somewhere/classes12.jar"

```

That will only exist for your current shell session. To make it permanent, add that line to ~/.bashrc or, preferably, a script called from ~/.bashrc

If you are doing server-side programming with JSP and JDBC, consider the attached screenshot. These are the included libraries in a small web application written with Spring and Hibernate. If this is your direction, you could save yourself a lot of time and trouble by spending two hours working through the Maven tutorial.

---

### Post by sandy0594 on 2011-05-25
This is how my bash profile looks..where should i add that environment variables for setting the path and classpath in the below bash profile

```

# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
# ... or force ignoredups and ignorespace
HISTCONTROL=ignoredups:ignorespace

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)
HISTSIZE=1000
HISTFILESIZE=2000

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# make less more friendly for non-text input files, see lesspipe(1)
    [ -x /usr/bin/lesspipe ] && eval "$(SHELL=/bin/sh lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
    xterm-color) color_prompt=yes;;
esac

# uncomment for a colored prompt, if the terminal has the capability; turned
# off by default to not distract the user: the focus in a terminal window
# should be on the output of commands, not on the prompt
#force_color_prompt=yes

if [ -n "$force_color_prompt" ]; then
    if [ -x /usr/bin/tput ] && tput setaf 1 >&/dev/null; then
        # We have color support; assume it's compliant with Ecma-48
        # (ISO/IEC-6429). (Lack of such support is extremely rare, and such  # a case would tend to support setf rather than setaf.)
        color_prompt=yes
    else
        color_prompt=
    fi
fi

if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
unset color_prompt force_color_prompt

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
    ;;
*)
   ;;
esac

# enable color support of ls and also add handy aliases
if [ -x /usr/bin/dircolors ]; then
    test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)"
    alias ls='ls --color=auto'
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'

    alias grep='grep --color=auto'
    alias fgrep='fgrep --color=auto'
    alias egrep='egrep --color=auto'
fi

# some more ls aliases
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'

# Add an "alert" alias for long running commands.  Use like so:
 #   sleep 10; alert
alias alert='notify-send --urgency=low -i "$([ $? = 0 ] && echo terminal || echo error)" "$(history|tail -n1|sed -e '\''s/^\s*[0-9]\+\s*//;s/[;&|]\s*alert$//'\'')"'

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
    . /etc/bash_completion
fi


```

---

### Post by r-senior on 2011-05-25
> **sandy0594 said:**
> This is how my bash profile looks..where should i add that environment variables for setting the path and classpath in the below bash profile
Ah well, I tried. ;)

Anywhere (but not inside an 'if' block, obviously). At the bottom is probably easiest to find later on. You'll need to log out and back in again to see them appearing in new terminal windows.

---

### Post by Blackbug on 2011-05-25
well rightly said above if you have installed JDK it will set the PATH by itself
and its better not to create ambiguity with CLASSPATH
 
To see everythin is installed fine..check
 
$>which java
$>echo $PATH
 
if /usr/bin/java is not in your path( and you are sure its installed ), just export the path using:
export PATH=$PATH;/usr/bin/java

---

### Post by sandy0594 on 2011-05-25
I set the classpath and my java program is executing..But,i do have a small problem that needs to be addressed.I have 2 users in Ubuntu..One is sandy and oracle..In oracle user,oracle is installed and when i set the classpath in oracle user,the program executes.But,back in sandy user the program fails in execution phase.

```

export CLASSPATH=".:/opt/oracle/oracle/product/10.2.0/db_2/jdbc/lib/classes12.jar"

```

In user **sandy**
```

sandy@ubuntu:~/Java Programs$ javac PureConnection.java
sandy@ubuntu:~/Java Programs$ java PureConnection
Exception in thread "main" java.lang.ClassNotFoundException: oracle.jdbc.driver.OracleDriver
    at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
    at java.lang.Class.forName0(Native Method)
    at java.lang.Class.forName(Class.java:186)
    at PureConnection.main(PureConnection.java:10)


```

In user **oracle**
```

oracle@ubuntu:/media/SANDY$ javac PureConnection.java 
oracle@ubuntu:/media/SANDY$ java PureConnection 
Driver Loaded 
connected

```

So,any hunch on how to solve this issue

---

### Post by Blackbug on 2011-05-25
looks like your user has some priviledge issue.
the user 'oracle' has those priviledges.
not very sure, but try to check it and see the link below
 
 
> 
[http://download.oracle.com/javase/1.4.2/docs/api/java/security/AccessController.html](http://download.oracle.com/javase/1.4.2/docs/api/java/security/AccessController.html)


---

### Post by sandy0594 on 2011-05-25
As per my programming knowledge,the problem is regarding the environment variables..Its just that the environment variable specified in user **oracle  **should be used by user **sandy**.How to use the environment variable specified in one user could be used in other user is the point

---

### Post by r-senior on 2011-05-25
System wide environment is created in /etc/profile.

```

# /etc/profile: system-wide .profile file for the Bourne shell (sh(1))
# and Bourne compatible shells (bash(1), ksh(1), ash(1), ...).

[COLOR="Red"]if [ -d /etc/profile.d ]; then
  for i in /etc/profile.d/*.sh; do
    if [ -r $i ]; then
      . $i
    fi
  done
  unset i
fi[/COLOR]

if [ "$PS1" ]; then
  if [ "$BASH" ]; then
    PS1='\u@\h:\w\$ '
    if [ -f /etc/bash.bashrc ]; then
	. /etc/bash.bashrc
    fi
  else
    if [ "`id -u`" -eq 0 ]; then
      PS1='# '
    else
      PS1='$ '
    fi
  fi
fi

umask 022

```

Probably the easiest way to add yours is create a new script and put it in /etc/profile.d/java_classpath.sh, which will be picked up by the code in red above. You'll need sudo to create it, and it should probably look something like this: 

```

#!/bin/sh
export CLASSPATH=???

```

(I should add that I think this is even worse idea than setting a classpath for one user, but you seem determined ...).

---

### Post by sandy0594 on 2011-05-25
No,i was not determined like that..I set the classpath in user sandy also..But,the program fails to execute that is why i raised that question
```

# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
# ... or force ignoredups and ignorespace
HISTCONTROL=ignoredups:ignorespace

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)
HISTSIZE=1000
HISTFILESIZE=2000

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(SHELL=/bin/sh lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
    xterm-color) color_prompt=yes;;
esac

# uncomment for a colored prompt, if the terminal has the capability; turned
# off by default to not distract the user: the focus in a terminal window
# should be on the output of commands, not on the prompt
#force_color_prompt=yes

if [ -n "$force_color_prompt" ]; then
    if [ -x /usr/bin/tput ] && tput setaf 1 >&/dev/null; then
        # We have color support; assume it's compliant with Ecma-48
        # (ISO/IEC-6429). (Lack of such support is extremely rare, and such
        # a case would tend to support setf rather than setaf.)
        color_prompt=yes
else
        color_prompt=
    fi
fi

if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
unset color_prompt force_color_prompt

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
    ;;
*)
    ;;
esac

# enable color support of ls and also add handy aliases
if [ -x /usr/bin/dircolors ]; then
    test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)"
    alias ls='ls --color=auto'
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'

    alias grep='grep --color=auto'
    alias fgrep='fgrep --color=auto'
    alias egrep='egrep --color=auto'
fi

# some more ls aliases
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'

# Add an "alert" alias for long running commands.  Use like so:
#   sleep 10; alert
alias alert='notify-send --urgency=low -i "$([ $? = 0 ] && echo terminal || echo error)" "$(history|tail -n1|sed -e '\''s/^\s*[0-9]\+\s*//;s/[;&|]\s*alert$//'\'')"'

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
    . /etc/bash_completion
fi
export CLASSPATH=".:/opt/oracle/oracle/product/10.2.0/db_2/jdbc/lib/classes12.jar"
            

```As u see,above is the bash profile in user **sandy** and below for user [B]oracle

[/B]```

ORACLE_SID=orcl 
ORACLE_HOME=/opt/oracle/oracle/product/10.2.0/db_2 
PATH=$PATH:$ORACLE_HOME/bin 
 
export ORACLE_SID ORACLE_HOME PATH 
export CLASSPATH=".:/opt/oracle/oracle/product/10.2.0/db_2/jdbc/lib/classes12.jar" 


```

I can run the program successfully in user **oracle** but in **sandy** i am getting errors at runtime as u have seen in my previous posts.

---

### Post by dwhitney67 on 2011-05-25
> **sandy0594 said:**
> 
I can run the program successfully in user **oracle** but in **sandy** i am getting errors at runtime as u have seen in my previous posts.

As user 'sandy', what is the result of running the following command:
```

ls -l /opt/oracle/oracle/product/10.2.0/db_2/jdbc/lib/classes12.jar

```

---

### Post by sandy0594 on 2011-05-25
Here is the result
> 
sandy@ubuntu:~$ ls -l /opt/oracle/oracle/product/10.2.0/db_2/jdbc/lib/classes12.jar
ls: cannot access /opt/oracle/oracle/product/10.2.0/db_2/jdbc/lib/classes12.jar: Permission denied



> 
sandy@ubuntu:~$ sudo ls -l /opt/oracle/oracle/product/10.2.0/db_2/jdbc/lib/classes12.jar
[sudo] password for sandy: 
-rw-r----- 1 oracle oinstall 1590491 2005-06-22 18:52 /opt/oracle/oracle/product/10.2.0/db_2/jdbc/lib/classes12.jar



---

### Post by dwhitney67 on 2011-05-25
This is what Blackbug was trying to tell you earlier.

You need to relax the permissions on the JAR file.  Run this command:
```

sudo chmod 644 /opt/oracle/oracle/product/10.2.0/db_2/jdbc/lib/classes12.jar

```
Then attempt to run your Java app as 'sandy' to confirm the changes work properly.


P.S.  Alternatively, you can add user 'sandy' to the 'oinstall' group.

---

### Post by sandy0594 on 2011-05-25
I followed ur suggestion but things are not working out..I even restarted my pc.But,still when i do the below,permission is denied

```

sandy@ubuntu:~$ sudo chmod 644 /opt/oracle/oracle/product/10.2.0/db_2/jdbc/lib/classes12.jar
sandy@ubuntu:~$ ls -l /opt/oracle/oracle/product/10.2.0/db_2/jdbc/lib/classes12.jar
ls: cannot access /opt/oracle/oracle/product/10.2.0/db_2/jdbc/lib/classes12.jar: Permission denied
sandy@ubuntu:~$ 


```
Where am i doing wrong?

---

### Post by dwhitney67 on 2011-05-25
> **sandy0594 said:**
> I followed ur suggestion but things are not working out..I even restarted my pc.But,still when i do the below,permission is denied

```

sandy@ubuntu:~$ sudo chmod 644 /opt/oracle/oracle/product/10.2.0/db_2/jdbc/lib/classes12.jar
sandy@ubuntu:~$ ls -l /opt/oracle/oracle/product/10.2.0/db_2/jdbc/lib/classes12.jar
ls: cannot access /opt/oracle/oracle/product/10.2.0/db_2/jdbc/lib/classes12.jar: Permission denied
sandy@ubuntu:~$ 


```
Where am i doing wrong?

As user 'oracle' (or root), examine each directory along this path:
/opt/oracle/oracle/product/10.2.0/db_2/jdbc/lib

Make sure each directory has permissions 755 (or rwxr-xr-x).

You can use "sudo -i" to get into the interactive mode; then just navigate to each directory.  If you encounter a directory that has the incorrect permissions, change it using "chmod 755".

P.S.  You do not have to reboot your system after any changes are made.

---

### Post by sandy0594 on 2011-05-25
When accessed through root..i see the permissions right,but when  accessed through user sandy..same old problem "permission denied"

> 
root@ubuntu:~# ls -l /opt/oracle/oracle/product/10.2.0/db_2/jdbc/lib/classes12.jar
-rwxr-xr-x 1 oracle oinstall 1590491 2005-06-22 18:52 /opt/oracle/oracle/product/10.2.0/db_2/jdbc/lib/classes12.jar
root@ubuntu:~# su - sandy
sandy@ubuntu:~$ ls -l /opt/oracle/oracle/product/10.2.0/db_2/jdbc/lib/classes12.jar
ls: cannot access /opt/oracle/oracle/product/10.2.0/db_2/jdbc/lib/classes12.jar: Permission denied
sandy@ubuntu:~$ sudo chmod 755 /opt/oracle/oracle/product/10.2.0/db_2/jdbc/lib/classes12.jar
sandy@ubuntu:~$ ls -l /opt/oracle/oracle/product/10.2.0/db_2/jdbc/lib/classes12.jar
ls: cannot access /opt/oracle/oracle/product/10.2.0/db_2/jdbc/lib/classes12.jar: Permission denied
sandy@ubuntu:~$ 



---

### Post by dwhitney67 on 2011-05-25
I guess my previous suggestion escaped you.

Create the following script (call it chgperm):
```

#!/bin/bash

dir=/opt/oracle/oracle/product/10.2.0/db_2/jdbc/lib

while [ $dir != "/" ]; do
        echo "Changing $dir to mode 755..."
        chmod 755 $dir
        dir=`dirname $dir`
done

```
Then...
```

chmod +x chgperm

sudo ./chgperm

```
Then... go back and test your java app as 'sandy'.

---

### Post by sandy0594 on 2011-05-25
Right on target..your script worked well as far as classpath is concerned but unfortunately there is someother error

```

sandy@ubuntu:~$ vi chgperm
sandy@ubuntu:~$ chmod +x chgperm
sandy@ubuntu:~$ sudo ./chgperm
[sudo] password for sandy: 
Changing /opt/oracle/oracle/product/10.2.0/db_2/jdbc/lib to mode 755...
Changing /opt/oracle/oracle/product/10.2.0/db_2/jdbc to mode 755...
Changing /opt/oracle/oracle/product/10.2.0/db_2 to mode 755...
Changing /opt/oracle/oracle/product/10.2.0 to mode 755...
Changing /opt/oracle/oracle/product to mode 755...
Changing /opt/oracle/oracle to mode 755...
Changing /opt/oracle to mode 755...
Changing /opt to mode 755...
sandy@ubuntu:~$ cd '/home/sandy/Java Programs' 
sandy@ubuntu:~/Java Programs$ javac PureConnection.java
sandy@ubuntu:~/Java Programs$ java PureConnection
Driver Loaded
Exception in thread "main" java.sql.SQLException: Listener refused the connection with the following error:
ORA-12505, TNS:listener does not currently know of SID given in connect descriptor
The Connection descriptor used by the client was:
localhost:1521:orcl

    at oracle.jdbc.driver.DatabaseError.throwSqlException(DatabaseError.java:111)
    at oracle.jdbc.driver.DatabaseError.throwSqlException(DatabaseError.java:260)
    at oracle.jdbc.driver.T4CConnection.logon(T4CConnection.java:386)
    at oracle.jdbc.driver.PhysicalConnection.<init>(PhysicalConnection.java:413)
    at oracle.jdbc.driver.T4CConnection.<init>(T4CConnection.java:164)
    at oracle.jdbc.driver.T4CDriverExtension.getConnection(T4CDriverExtension.java:34)
    at oracle.jdbc.driver.OracleDriver.connect(OracleDriver.java:752)
    at java.sql.DriverManager.getConnection(DriverManager.java:620)
    at java.sql.DriverManager.getConnection(DriverManager.java:200)
    at PureConnection.main(PureConnection.java:12)

```

The same program when ran in oracle user executed successfully.But,no idea why i am getting error here in sandy user.I started the oracle instance and database is opened.

Anyhow,thanks for the replies..If u have any idea of the above errors,kindly share the solution

---

### Post by sandy0594 on 2011-05-25
hey,sorted out the problem..It was just a temporary glitch
> 
sandy@ubuntu:~/Java Programs$ javac PureConnection.java
sandy@ubuntu:~/Java Programs$ java PureConnection
Driver Loaded
connected



Thanks for all your replies

---

### Post by dwhitney67 on 2011-05-25
It appears to be an issue with how your app is connecting to the Oracle database.

Here's some Google [hits]("http://www.google.com/search?q=%22ORA-12505%2C+TNS%3Alistener+does+not+currently+know+of+SID+given+in+connect+descriptor%22").

Try to confirm that your 'sandy' environment matches that of 'oracle'.  Use the 'env' command to get a listing of your environment variables.

---

### Post by sandy0594 on 2011-05-25
Yeah,the classpath variable which i added with your suggestion appears in my environment

```

sandy@ubuntu:~$ env
ORBIT_SOCKETDIR=/tmp/orbit-sandy
SSH_AGENT_PID=1866
TERM=xterm
SHELL=/bin/bash
XDG_SESSION_COOKIE=bf05847f2afbf1357be2e2c500000006-1306348177.697718-932971002
WINDOWID=75497510
GNOME_KEYRING_CONTROL=/tmp/keyring-Yup0UW
GTK_MODULES=canberra-gtk-module
USER=sandy
LS_COLORS=rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.tlz=01;31:*.txz=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.lz=01;31:*.xz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.rar=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.cgm=01;35:*.emf=01;35:*.axv=01;35:*.anx=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.axa=00;36:*.oga=00;36:*.spx=00;36:*.xspf=00;36:
SSH_AUTH_SOCK=/tmp/keyring-Yup0UW/ssh
DEFAULTS_PATH=/usr/share/gconf/gnome.default.path
SESSION_MANAGER=local/ubuntu:@/tmp/.ICE-unix/1836,unix/ubuntu:/tmp/.ICE-unix/1836
USERNAME=sandy
XDG_CONFIG_DIRS=/etc/xdg/xdg-gnome:/etc/xdg
DESKTOP_SESSION=gnome
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
PWD=/home/sandy
GDM_KEYBOARD_LAYOUT=us
LANG=en_US.UTF-8
GNOME_KEYRING_PID=1817
MANDATORY_PATH=/usr/share/gconf/gnome.mandatory.path
GDM_LANG=en_US.utf8
GDMSESSION=gnome
SHLVL=1
HOME=/home/sandy
LANGUAGE=en_US:en
GNOME_DESKTOP_SESSION_ID=this-is-deprecated
LOGNAME=sandy
CLASSPATH=.:/opt/oracle/oracle/product/10.2.0/db_2/jdbc/lib/classes12.jar
XDG_DATA_DIRS=/usr/share/gnome:/usr/local/share/:/usr/share/
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-YQoFmrH54w,guid=f761e72122d86d3a797ce5990000001e
LESSOPEN=| /usr/bin/lesspipe %s
WINDOWPATH=7
DISPLAY=:0.0
LESSCLOSE=/usr/bin/lesspipe %s %s
XAUTHORITY=/var/run/gdm/auth-for-sandy-4OaFha/database
COLORTERM=gnome-terminal
_=/usr/bin/env
sandy@ubuntu:~$ 


```

---

### Post by dilshad029 on 2012-08-17
Hi....
I am new for ubuntu... Plz any body can help me in a problem that is-  "I was using Eclipse 3.6.2 with android SDK 18 meanwhile for another project i installed SDk 21 and ADT 20 in another folder and then we delete previous configuration of android with eclipse.. Then i Configure new eclipse with new SDK and ADT.. But i found a great mess....After a message in console-"Launching Emulator......."
My emulator is not visible even after 15 minute..." Is this is a problem of Ubuntu?? Plz help me...

---

### Post by dwhitney67 on 2012-08-17
> **dilshad029 said:**
> Hi....
I am new for ubuntu... Plz any body can help me in a problem that is-  "I was using Eclipse 3.6.2 with android SDK 18 meanwhile for another project i installed SDk 21 and ADT 20 in another folder and then we delete previous configuration of android with eclipse.. Then i Configure new eclipse with new SDK and ADT.. But i found a great mess....After a message in console-"Launching Emulator......."
My emulator is not visible even after 15 minute..." Is this is a problem of Ubuntu?? Plz help me...

Open a new thread; don't piggy-back on others.

---

### Post by babisayabundar on 2012-11-12
How if we are using Netbeans?
7.0.1?

---

