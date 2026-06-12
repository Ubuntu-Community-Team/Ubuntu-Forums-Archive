---
title: "class not found exceptoion -- ubuntu/mysql/jdbc dfver"
date: 2008-04-07
forum: Programming Talk
---

### Post by badperson on 2008-04-07
Hi,

Found a couple threads on this, I realize this is not an ubuntu-only issue, but the question i have is. 

I followed [these instructions]("https://help.ubuntu.com/community/JDBCAndMySQL"), but am still getting a classNotFound exception, which leads me to believe it's a classpath issue. 

I edted my .bashrc file with this update:
CLASSPATH=$CLASSPATH:/usr/share/java/mysql.jar
export CLASSPATH

I put it at the very end of the .bashrc file...do I need the "fi" entry when it's done? 

Also, I tried setting it to this:

CLASSPATH=".:/usr/share/java/mysql.jar"

any idea what I'm doing wrong? I tried runnign the example java code at the link above; that's where I got my class not found exception. And I changed all the db names, user, pw, etc. 

thanks, 
bp

---

### Post by Zugzwang on 2008-04-07
Three things:
[LIST]
[*]Please post your .bashrc here
[*]Did you check if  the "contents" of your classpath environment variable (run "echo $CLASSPATH" in the terminal) is correct?
[*]Make sure that you start any program which is meant to use the mysql-connector from a bash console.
[/LIST]

More experienced Ubuntu-users may want to correct me regarding the last two points.

---

### Post by badperson on 2008-04-07
thanks for the reply...I'll post my bashrc file when I get home tonight. 
bp

---

### Post by badperson on 2008-04-10
Hi,

the echo $CLASSPATH works in a terminal console. 
I was using eclipse to try to run the demo program, but I put it into a regular text file and tried compiling and running through the console and got the same error. 

Here's my .bashrc:

```
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
export HISTCONTROL=ignoredups
# ... and ignore same sucessive entries.
export HISTCONTROL=ignoreboth

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
xterm-color)
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
    ;;
*)
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
    ;;
esac

# Comment in the above and uncomment this below for a color prompt
#PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD/$HOME/~}\007"'
    ;;
*)
    ;;
esac

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

#if [ -f ~/.bash_aliases ]; then
#    . ~/.bash_aliases
#fi

# enable color support of ls and also add handy aliases
if [ "$TERM" != "dumb" ]; then
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
    #alias dir='ls --color=auto --format=vertical'
    #alias vdir='ls --color=auto --format=long'
fi

# some more ls aliases
#alias ll='ls -l'
#alias la='ls -A'
#alias l='ls -CF'

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
C
fi
# classpath info from website for jdbc
CLASSPATH=$CLASSPATH:/usr/share/java/mysql.jar
EXPORT CLASSPATH

```


here's the java program I'm trying to run: 

```
import java.sql.*;
import java.util.Properties;

public class DBDemo
{
  // The JDBC Connector Class.
  private static final String dbClassName = "com.mysql.jdbc.Driver";

  // Connection string. emotherearth is the database the program
  // is connecting to. You can include user and password after this
  // by adding (say) ?user=paulr&password=paulr. Not recommended!

  private static final String CONNECTION =
                          "jdbc:mysql://127.0.0.1/runnerlog";

  public static void main(String[] args) throws
                             ClassNotFoundException,SQLException
  {
    System.out.println(dbClassName);
    // Class.forName(xxx) loads the jdbc classes and
    // creates a drivermanager class factory
    Class.forName(dbClassName);

    // Properties for user and password. Here the user and password are both 'paulr'
    Properties p = new Properties();
    p.put("user","runner");
    p.put("password","edgarrunner");

    // Now try to connect
    Connection c = DriverManager.getConnection(CONNECTION,p);

    System.out.println("It works !");
    c.close();
    }
}
```

thanks for any help
bp

---

### Post by badperson on 2008-04-10
I also tried installing the mysql-connector-j, followed the instructions, got the same error. 

I changed my classpath in the .bashrc to this: 
```
# classpath info from website for jdbc
CLASSPATH=$CLASSPATH:/home/jason/Documents/MySql/connector-j/mysql-connector-java-5.1.6/mysql-connector-java-5.1.6-bin.jar
EXPORT CLASSPATH
```

---

### Post by badperson on 2008-04-10
weird...it works now. I copied and pasted into the .bashrc file the classpath that was on the website linked above and it worked. 
I'm pretty sure I was typing it correctly before. 
bp

---

