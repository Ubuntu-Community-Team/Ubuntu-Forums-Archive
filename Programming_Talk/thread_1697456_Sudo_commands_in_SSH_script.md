---
title: "Sudo commands in SSH script"
date: 2011-02-28
forum: Programming Talk
---

### Post by japhyr on 2011-02-28
Hello,

I am trying to administer a small group of ubuntu desktops in my classroom.  One of the tasks at the end of each week is to update each desktop, then shut it down.  I would like to automate that task, so I've been learning about ssh.

I have installed openssh-server on one of the target machines.  I set up a key so that I can connect to the target machine without a password.  I can run sudo commands on the target machine through the terminal, and I can run non-sudo commands on that machine through a script.

How do I gain sudo power on the target machine through a local script?  I have seen a number of different recommendations, but nothing that I have confidence in as representing current best practice for Ubuntu.  Should I be ssh'ing in as root?

Pseudocode for what I am thinking so far:
```
#!/bin/bash
ssh adminUsername@ipaddress "sudo apt-get -y update; sudo apt-get -y dist-upgrade; sudo shutdown -h now;"
```

---

### Post by johnl on 2011-02-28
Hi,

You can permit your admin account to run apt-get without asking for a password by editing your /etc/sudoers file.  You should always edit this file with the 'visudo' command (set EDITOR or VISUAL to use the editor of your choice instead of vim).

I think you can add:

```

%admin    ALL = NOPASSWD: /usr/bin/apt-get

```

to accomplish this.  This does have the draw back that now anyone who gains access to your admin account can add/remove software at will.


An alternate solution would be set up a cron job on each machine to perform the update at the end of the week automatically.

---

### Post by lavinog on 2011-02-28
Another option would be to have a daemon that does a check for the existence of a file.  If the file exists it would run the commands.

---

### Post by japhyr on 2011-03-01
I should have been a little more clear.  I would like to be able to run any sudo command through a script, so that when I have to do something to maintain a computer, I can make that part of a script and do the same thing to every computer.  I want to do this the right way.

Is there a "right way" in ubuntu to run administrative commands remotely through a script?

---

### Post by japhyr on 2011-03-02
```
%admin    ALL = NOPASSWD: /usr/bin/apt-get
```
I want to do something like this, but rather than allow all admin users to execute some commands without a password, I want to let just one user do so.  I made a new user 'scriptadmin' for this purpose.  How do I set this in the sudoers file?  Is this correct:
```
scriptadmin All = NOPASSWD: /usr/bin/apt-get
```Do I need a % in front of the username?  Also, does this go after the '%admin All = (ALL) ALL' line?

---

### Post by wormyblackburny on 2011-03-02
I think creating a new user is a fairly bad idea. I would just permit that ONE script to be run without a password in the sudoers file:

A line like the following will allow only  '/usr/local/bin/script.sh' to be run with sudo by the user 'username'  without a password.
  

username ALL = NOPASSWD: /usr/local/bin/script.sh


And schedule the script to run as a chron job so you can save yourself the trouble of having to start it manually. My last piece of advice: You better be testing the updates etc on ONE machine a day or so before to make sure the update doesn't break something before you push out the update to the entire environment ;)

---

### Post by japhyr on 2011-03-02
Why do you think it's a bad idea to create a new user?  I have a specific reason for doing this, so please tell me if this does not make sense.

I have about ten machines in my classroom.  The standard student account has administrative rights, so that students learn to install programs and maintain computers.  The scriptadmin account automates some of the maintenance tasks for periods of times when students are not able to consistently maintain the full set of computers.  Also, I would like to start teaching students how to maintain the network of computers, once they know how to maintain a single machine.  I would like to keep these functions separate, rather than mixing roles.

Does that make sense, or is there another reason not to have separate accounts?

---

