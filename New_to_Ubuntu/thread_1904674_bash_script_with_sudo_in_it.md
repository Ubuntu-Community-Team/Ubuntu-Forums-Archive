---
title: "bash script with sudo in it?"
date: 2012-01-05
forum: New to Ubuntu
---

### Post by hopelessone on 2012-01-05
Hi,

> sudo ./.vdr.sh start
works in terminal

trying to start:
> blade@oneiric:~$ ./.vdr.sh start
mkdir: cannot create directory `/var/run/vdr': Permission denied
chown: cannot access `/var/run/vdr': No such file or directory
Starting Linux Video Disk Recorder: vdr
Searching for plugins (VDR 1.7.22/1.7.22) (cache hit): xvdr/usr/lib/vdr/commands-loader.sh: line 30: /var/cache/vdr/commands.conf: Permission denied
/usr/lib/vdr/commands-loader.sh: line 57: /var/cache/vdr/commands.conf: Permission denied
/usr/lib/vdr/commands-loader.sh: line 58: /var/cache/vdr/commands.conf: Permission denied
/usr/lib/vdr/commands-loader.sh: line 57: /var/cache/vdr/commands.conf: Permission denied
/usr/lib/vdr/commands-loader.sh: line 58: /var/cache/vdr/commands.conf: Permission denied
/usr/lib/vdr/commands-loader.sh: line 57: /var/cache/vdr/commands.conf: Permission denied
/usr/lib/vdr/commands-loader.sh: line 58: /var/cache/vdr/commands.conf: Permission denied
/usr/lib/vdr/commands-loader.sh: line 57: /var/cache/vdr/commands.conf: Permission denied
/usr/lib/vdr/commands-loader.sh: line 58: /var/cache/vdr/commands.conf: Permission denied
/usr/lib/vdr/commands-loader.sh: line 30: /var/cache/vdr/reccmds.conf: Permission denied
/usr/lib/vdr/commands-loader.sh: line 57: /var/cache/vdr/reccmds.conf: Permission denied
/usr/lib/vdr/commands-loader.sh: line 58: /var/cache/vdr/reccmds.conf: Permission denied
start-stop-daemon: unable to open pidfile '/var/run/runvdr.pid' for writing (Permission denied)
.
blade@oneiric:~$ 


I edited sudoers:
> # Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
%admin ALL=(ALL)NOPASSWD:/usr/bin/vdr
%admin ALL=(ALL)NOPASSWD:/usr/sbin/runvdr



What am I doing wrong?

---

### Post by Grenage on 2012-01-05
vdr is a directory, does sudoers nopasswd work on entire directories without a wildcard?

---

### Post by hopelessone on 2012-01-05
I think not from above output...how can i make the script work with:
sudo ./.vdr.sh start
in it?

---

### Post by Grenage on 2012-01-05
Well var/run isn't stipulated, so the script won't have access rights for creating a directory; that's the first failure.

I assume there's a reason you're using sudo in the script, rather than when calling the script?

---

### Post by hopelessone on 2012-01-05
> I assume there's a reason you're using sudo in the script, rather than when calling the script?


Yes vdr needs it to start

Should I include var/run in the sudoers?

---

### Post by Grenage on 2012-01-06
Greetings again,

I wouldn't do that if you don't need to; you could just manually create the directory and set the permissions so that the current user has write access.

---

### Post by hopelessone on 2012-01-06
I'm stumped...

Possible to give step by step?

Thanks

---

### Post by Grenage on 2012-01-06
What I mean is, you could do something like this:
```
sudo mkdir /var/vdr
sudo chmod 777 /var/vdr
```
This example creates the folder, then sets the permissions so that anyone can write/delete to it.

While sudoers is a very valid way of doing things, it's usually a lot easier to just set appropriate permissions.  Sometimes you don't have a choice

---

### Post by Lars Noodén on 2012-01-06
What commands are on lines 30, 57 and 58 of the script [font=Courier]/usr/lib/vdr/commands-loader.sh[/font]?

You could run the whole script as root.  What is the full path to [font=Courier]vdr.sh[/font]?
(Edit: See lampi's suggestion below)


(PS.  Please don't set anything to 777, it is unsafe and will necessitate cleaning up afterwards.)

---

### Post by Lampi on 2012-01-06
@hopelessone: start/stop vdr like this:

sudo /etc/init.d/vdr start
sudo /etc/init.d/vdr stop

vdr will run as user vdr then + this script will take care of file permissions.

---

### Post by hopelessone on 2012-01-11
I had to pull vdr from init.d because the channels dont load, so i put it in my home dir, and i start it with:

sudo ./vdh.sh start <-- and everything loads up fine

But I wanna make up a script that:

Loads vdr
loads lirc
then loads xbmc

without entering sudo everytime, so my wife can watch tv when i'm out...

I've already submitted a bug report but want to get this going asap for the family..

Many thanks..

---

### Post by Lars Noodén on 2012-01-12
At the head of the script is a comment that the file is called by /etc/init.d/vdr, so if I understand the context correctly it might make sense to just call it with sudo since it calls everything else.

You can authorize several people to run sudo with or without a password by using groups and putting the relevant accounts into those groups.  From sudoers:
 
```

%vdrrun ALL=(ALL) NOPASSWD: /etc/init.d/vdr

```

and

```

sudo groupadd vdrrun
sudo gpasswd --add wife
sudo gpasswd --add kid1
sudo gpasswd --add kid2
# etc.

```

Does that take it a step in the right direction?

---

### Post by hopelessone on 2012-01-12
Hi,

I've just got 1 user: blade

I had to move the script out of /etc/init.d/vdr so i can start it manually (long story doesnt work, bug reported)

```
%blade ALL=(ALL) NOPASSWD: /home/blade/.vdr.sh

```
but no go same as before with permissions...

Tried exactly as shown above and same:
```
blade@oneiric:~$ ./.vdr.sh start
mkdir: cannot create directory `/var/run/vdr': Permission denied
chown: cannot access `/var/run/vdr': No such file or directory
Starting Linux Video Disk Recorder: vdr
Searching for plugins (VDR 1.7.22/1.7.22) (cache hit): xineliboutput xvdr/usr/lib/vdr/commands-loader.sh: line 30: /var/cache/vdr/commands.conf: Permission denied
/usr/lib/vdr/commands-loader.sh: line 57: /var/cache/vdr/commands.conf: Permission denied
/usr/lib/vdr/commands-loader.sh: line 58: /var/cache/vdr/commands.conf: Permission denied
/usr/lib/vdr/commands-loader.sh: line 57: /var/cache/vdr/commands.conf: Permission denied
/usr/lib/vdr/commands-loader.sh: line 58: /var/cache/vdr/commands.conf: Permission denied
/usr/lib/vdr/commands-loader.sh: line 57: /var/cache/vdr/commands.conf: Permission denied
/usr/lib/vdr/commands-loader.sh: line 58: /var/cache/vdr/commands.conf: Permission denied
/usr/lib/vdr/commands-loader.sh: line 57: /var/cache/vdr/commands.conf: Permission denied
/usr/lib/vdr/commands-loader.sh: line 58: /var/cache/vdr/commands.conf: Permission denied
/usr/lib/vdr/commands-loader.sh: line 30: /var/cache/vdr/reccmds.conf: Permission denied
/usr/lib/vdr/commands-loader.sh: line 57: /var/cache/vdr/reccmds.conf: Permission denied
/usr/lib/vdr/commands-loader.sh: line 58: /var/cache/vdr/reccmds.conf: Permission denied
start-stop-daemon: unable to open pidfile '/var/run/runvdr.pid' for writing (Permission denied)
```
.
blade@oneiric:~$

---

### Post by Lars Noodén on 2012-01-12
It should have been this:

```

sudo ./.vdr.sh start

```

You'll have to adjust the line in [font=Courier New]/etc/sudoers[/font] accordingly.

If you don't want to type 'sudo' each time, then you could make an alias and set it in [font=Courier New].bashrc[/font].

```

alias vdr.sh='sudo ./.vdr.sh'

```

---

### Post by hopelessone on 2012-01-12
You mean?

```
%vdrrun ALL=(ALL) NOPASSWD: sudo ./.vdr.sh start

```

I tried adding your line in .bashrc
> alias vdr.sh='sudo ./.vdr.sh'

Same result..

---

### Post by Lars Noodén on 2012-01-12
> **hopelessone said:**
> You mean?

```
%vdrrun ALL=(ALL) NOPASSWD: [s]sudo[/s] ./.vdr.sh start

```

I tried adding your line .bashrc

Same result..

That one is for sudoers.  The alias is for .bashrc.

I have to admit I am having trouble visualizing how you have your setup.  Can you give an example of what you can type right now that works?

---

### Post by hopelessone on 2012-01-12
```
sudo ./.vdr.sh start 

```
works but i want to do this without the sudo so i can make a script to then start xbmc..

```
%vdrrun ALL=(ALL) NOPASSWD: ./.vdr.sh

```

gives me an error cant save it..

> # Cmnd alias specification

# User privilege specification
root    ALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo   ALL=(ALL:ALL) ALL
%vdrrun ALL=(ALL) NOPASSWD: ./.vdr.sh start

#includedir /etc/sudoers.d

---

### Post by hopelessone on 2012-01-12
Hey look at this:
Plugin-loader.sh
has:
mkdir -p /var/run/vdr
chown -R vdr:vdr /var/run/vdr

That could be the problem?

---

### Post by Lars Noodén on 2012-01-12
It could be.  Both mkdir and chown need root access to work as described in that script.  If you make /var/run/vdr and set the ownership manually, then you can skip that step.

---

