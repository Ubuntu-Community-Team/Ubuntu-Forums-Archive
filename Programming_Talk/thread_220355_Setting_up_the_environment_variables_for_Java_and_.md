---
title: "Setting up the environment variables for Java and JSIM"
date: 2006-07-21
forum: Programming Talk
---

### Post by nits_555 on 2006-07-21
Hello,

I have been trying to install a combination of J2SE5.0, JSIM and Apache Ant on ubuntu. Enlisted below are the steps I followed:

1. Installed J2SE (using "sudo" in ubuntu terminal), JSIM and Apache Ant (using root login and extracting the .tar.gz files) in the usr/lib folder.
2. Changed the /etc/environment.txt to include all the "export" (setting of class path) statements.
3. Rebooted the laptop in ubuntu.

While it displays the ubuntu logon splash, when I try to login, it displays a message as "Your session lasted less than 10 seconds.... (the usual text).. Try logging in with one of the failsafe sessions to see". When I try to view the ~/.xsession-error file, it contains the following:

/etc/gdm/PreSession/Default: Registering your session...
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -1 -w
/etc/gdm/Xsession: Beginning session setup
/etc/gdm/Xsession: line 73: ls: command not found
/etc/gdm/Xsession: Executing default failed, will try to run x-terminal-emulator
/etc/gds/Xsession: line 224: exec: x-terminal-emulator: not found

When I try to reboot in "Failsafe Terminal" mode, it simply logs me to the command prompt with message "bash: lesspipe: command not found, bash:dircolors: command not found". On firing any command other than "cd .. or cd" it throws an error "bash: "command tried" (ls or anything): command not found". In "Failsafe Gnome" it shows nothing but a blank screen. 

I am clueless as to how to solve the problem and any inputs in this will be highly appreciated.

Thanks,
Nitin.

---

### Post by robinharvey on 2006-07-22
You should set the environment vars in /etc/profile, like this:
```

export JAVA_HOME=/usr/lib/j2whatever
export ANT_HOME=/here/is/ant

```
I'd take it out of /etc/environment.txt - looks like things are getting upset in your install.
ps. - you have to re-boot for the changes to take effect.

hth
--Robin

---

### Post by jbrown on 2006-08-26
I have the same problem.  The question is how do you change the environment.txt back once your are in failsafe terminal mode as vi and gedit commands are "not found"?

---

