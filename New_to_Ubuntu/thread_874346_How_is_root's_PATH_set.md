---
title: "How is root's PATH set?"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by unutbu on 2008-07-29
When I run
```

sudo -i
```

root's PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin.

When I run
```

sudo su
```

root's PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

Notice the two PATH's differ. I did manage to discover that `sudo su`s PATH is dependent on /etc/environment, so there is little mystery there.
However, I can't seem to find how /usr/X11R6/bin is being added to the PATH when `sudo -i` is run.

I've tried grepping for 'usr/X11R6/bin' in /etc, /usr, and /root, but didn't find anything illuminating.

Does anyone know how root's PATH gets set when `sudo -i` is run?

---

### Post by original_jamingrit on 2008-07-29
You shouldn't modify it directly, but you can modify it's usage by setting it in root's or your own .bash_profile.

Example of /home/myusername/.bash_profile
```
##.bash_profile, run at login.


PATH=$PATH":/home/myusername/bin:/whatever/bin"

if [ -f ~/.bashrc ]; then
        source ~/.bashrc
fi
```

if .bash_profile doesn't exist, simply create it and copy/paste the example in.

In the above example, we modify the $PATH to include itself, the path to /home/myusername/bin, and the path to /whatever/bin, where we assume the previous two are extra directories containing programs and scripts we would like to call.

the difference between .bashrc and .bash_profile is that .bash_profile is run once you log in.  .bashrc is run everytime you open a new terminal, as well as when .bash_profile is run as in the above example.

---

### Post by ibuclaw on 2008-07-29
```
sudo su
```
with su you are basically root, but your own environmental variables are "preserved".

```
sudo -s
```
And your environmental variables are merged with that of root's.

```
sudo -i
```
On the other hand is "true" root access. None of your variables are carried over and only the root Defaults remain.

And as for the added directory in your $PATH list, well... It's nothing, it's just a symlink that points to /usr/bin. Most probably kept for compatibility with old root access softwares.

Regards
Iain

---

### Post by original_jamingrit on 2008-07-29
$PATH and other variables are something used a lot by bash and shell interpreters, even when you do not see them.

Ubuntu doesn't actually use bash, but it uses a derivative called dash, which is just a slimmed down version.  Look for online bash and dash tutorials to learn more.

---

### Post by pauper on 2008-07-29
> **unutbu said:**
> I've tried grepping for 'usr/X11R6/bin' in /etc, /usr, and /root, but didn't
find anything illuminating.

:)

```
less /usr/share/doc/sudo/OPTIONS
```

[edit:]
> **unutbu said:**
> I did manage to discover that `sudo su`s PATH is dependent on /etc/environment

According to su manual its $PATH is controlled by /etc/login.defs

---

### Post by unutbu on 2008-07-29
Thank you all for the information!

I think I was under the delusion that `sudo -i` would read some file or script in /etc (like /etc/environment) to set root's PATH. 
Yes, now I see from  /usr/share/doc/sudo/OPTIONS that the X11R6 path is hard-coded into Ubuntu's version of sudo.

In case this may be of use to others who wander into this thread, here are some other interesting differences I've found while comparing various sudo command's resultant env's:

I tried "sudo -i", "sudo -s", "sudo bash", and "sudo su", and ran
env > env-{i,s,bash,su} after each one. This is what I found out:

```
				                corrupted by user's 
		HOME=/root	root's PATH     env vars
sudo -i		Y		[2]                 N
sudo -s		N		[2]                 Y
sudo bash	N		[2]                 Y
sudo su		Y		[1]                 Y

```

[1] PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
    probably set by /etc/environment
[2] PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin

---

### Post by unutbu on 2008-07-29
> **pauper said:**
> 

```
less /usr/share/doc/sudo/OPTIONS
```

Thanks, pauper, this really hits the nail on the head.

(And I guess I should not have killed that grep on /usr... :redface:)

> 
According to su manual its $PATH is controlled by /etc/login.defs
Yes, thanks for pointing out this file to me. When does it get read? When I edit ENV_SUPATH to
```

ENV_SUPATH	PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/opt

``` and then run
```
sudo su
echo $PATH
```
PATH does not include /opt. However, if I edit /etc/environment, and then run sudo su, the PATH does change...

---

### Post by pauper on 2008-07-30
> **unutbu said:**
> (And I guess I should not have killed that grep on /usr... :redface:)

The best way to approach it is to concentrate on each root sub-directory one at a 
time and exclude binaries.

```
:~$ **cd /usr**
:/usr$ **sudo find . \( -name bin -o -name sbin -o -name lib \) -prune -o -type f | xargs grep ":/usr/X11R6/bin" 2> /dev/null**
./share/doc/sudo/OPTIONS:       /sbin:/bin:/usr/X11R6/bin"  
./share/doc/sudo/examples/sudoers:# Defaults syslog=auth, secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin"
./share/ubuntu-docs/ubuntu/sample/Default_numlockx:PATH=/usr/bin/X11:/usr/X11R6/bin:/opt/X11R6/bin:$PATH

[highlight]# Meanwhile, open another terminal and let the "find" become a mean son-of-gun.[/highlight]

:~$ **ps aux | grep [f]ind**
:~$ **sudo renice -20 PID**
```

And go walk a dog or something--this might take a while [-o<.

> **unutbu said:**
> PATH does not include /opt. However, if I edit /etc/environment, and then run sudo su, the PATH does change...

As the name of the file (login.defs) slightly suggests it has something to do with
the login. So changes done to ENV_SUPATH and ENV_PATH have effect when your
environment similar to what the user would expect had the user logged in
directly. "su -" or "su - root" provide such capability, but not "sudo su".
By the way, who owns your /etc/environment?

For an amusement only, below are some tests with su and sudo.

```
$USER@$HOSTNAME:~$
GNU bash, version 3.2.25(1)-release (i486-pc-linux-gnu)
$USER@$HOSTNAME:~$ **echo $TERM**
xterm
[color=blue]$USER@$HOSTNAME:~$ **sudo -s**
Password:
root@$HOSTNAME:~# **pwd**
/home/$USER
root@$HOSTNAME:~# **echo $PATH**
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin
root@$HOSTNAME:~# **ps**
  PID TTY          TIME CMD
 9566 pts/1    00:00:00 bash
 9582 pts/1    00:00:00 ps
root@$HOSTNAME:~# **logout**
bash: logout: not login shell: use `exit'
root@$HOSTNAME:~# **exit**
exit[/color]
$USER@$HOSTNAME:~$ **sudo -i**
root@$HOSTNAME:~# **pwd**
/root
root@$HOSTNAME:~# **echo $PATH**
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin
root@$HOSTNAME:~# **ps**
  PID TTY          TIME CMD
 9583 pts/1    00:00:00 bash
 9595 pts/1    00:00:00 ps
root@$HOSTNAME:~# **logout**
[color=blue]$USER@$HOSTNAME:~$ **sudo -i**
root@$HOSTNAME:~# **su**
root@$HOSTNAME:~# **pwd**
/root
root@$HOSTNAME:~# **echo $PATH**
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
root@$HOSTNAME:~# **ps**
  PID TTY          TIME CMD
 9596 pts/1    00:00:00 bash
 9608 pts/1    00:00:00 su
 9609 pts/1    00:00:00 bash
 9620 pts/1    00:00:00 ps
root@$HOSTNAME:~# **logout**
bash: logout: not login shell: use `exit'
root@$HOSTNAME:~# **exit**
exit[/color]
root@$HOSTNAME:~# **su -**
root@$HOSTNAME:~# **pwd**
/root
root@$HOSTNAME:~# **echo $PATH**
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
root@$HOSTNAME:~# **echo $DISPLAY**

root@$HOSTNAME:~# **ps**
  PID TTY          TIME CMD
 9596 pts/1    00:00:00 bash
 9621 pts/1    00:00:00 su
 9622 pts/1    00:00:00 bash
 9634 pts/1    00:00:00 ps
root@$HOSTNAME:~# **logout**
root@$HOSTNAME:~# **logout**
[color=blue]$USER@$HOSTNAME:~$ **pwd**
/home/$USER
$USER@$HOSTNAME:~$ **echo $PATH**
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
$USER@$HOSTNAME:~$ **ps**
  PID TTY          TIME CMD
 9550 pts/1    00:00:00 bash
 9635 pts/1    00:00:00 ps
$USER@$HOSTNAME:~$ **logout**
bash: logout: not login shell: use `exit'[/color]
$USER@$HOSTNAME:~$ **sudo su**
root@$HOSTNAME:$HOME# **pwd**
/home/$USER
root@$HOSTNAME:$HOME# **echo $PATH**
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
root@$HOSTNAME:$HOME# **ps**
  PID TTY          TIME CMD
 9701 pts/1    00:00:00 su
 9702 pts/1    00:00:00 bash
 9713 pts/1    00:00:00 ps
root@$HOSTNAME:$HOME# **logout**
bash: logout: not login shell: use `exit'
root@$HOSTNAME:$HOME# **exit**
exit
$USER@$HOSTNAME:~$
```

---

### Post by Vivaldi Gloria on 2008-07-30
> **original_jamingrit said:**
> Ubuntu doesn't actually use bash, but it uses a derivative called dash, which is just a slimmed down version.  

Not true. Ubuntu links sh to dash but the shell in the terminal is bash. So if you write a script which starts with #!/bin/sh then it's run with dash. But if you give a command in the terminal then it's run by bash.

---

### Post by pauper on 2008-07-30
```
:~$ echo $SHELL
/bin/bash
```

:wink:

---

### Post by t0p on 2008-07-30
> **original_jamingrit said:**
> 
Ubuntu doesn't actually use bash, but it uses a derivative called dash, which is just a slimmed down version..

```
t0p@ubunty:~$ badcommand
bash: badcommand: command not found
t0p@ubunty:~$ 

```

If ubuntu doesn't use bash, why doesn't it say "dash: badcommand: command not found"?  How come the entry in /etc/passwd pertaining to me reads:

> t0p:x:1000:1000:t0p,,,:/home/t0p:/bin/bash

I know there's a bash-derivitive called dash.  But it seems to me that ubuntu also uses bash, which is the shell I use by default.

---

### Post by Vivaldi Gloria on 2008-07-30
Again, ubuntu uses bash in the terminal but uses dash for /bin/sh:

```
vivaldi@narval:~$ ls -lF /bin/sh
lrwxrwxrwx 1 root root 4 2008-04-28 14:14 /bin/sh -> dash*
```

There has been a lot of discussions about this in the past. Ubuntu uses dash because it makes the boot scripts get executed faster. If you have a script 

```

#!/bin/bash
blah blah blah
```

then there is a difference between running it with

```
sh script
```

or

```
./script
```

The first one uses dash and the second one uses bash. If the script starts with #!/bin/sh then both commands use dash.

But as pauper shows above, the terminal executes commands with bash.

---

### Post by unutbu on 2008-07-30
Pauper, thanks for showing me your find/grep technique. It ran under 7mins on my machine... just enough time to eat a pinecone :)

> 
By the way, who owns your /etc/environment?

```
  -rw-r--r--   1 root root        98 2008-07-29 21:44 environment
```

> For an amusement only, below are some tests with su and sudo.

I've often wondered how environment variables get setup when I run cron jobs or a udev-rule script.

Toward that end, I repeated your experiment, after editing /etc/login.defs:
```
ENV_SUPATH	PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/env_supath
ENV_PATH	PATH=/usr/local/bin:/usr/bin:/bin:/usr/games:/env_path

```
and /etc/environment:
```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/etc-environment"

```
and /root/.bashrc:
```
echo "root .bashrc read..."
PATH=$PATH:/root-bashrc-read
export PATH
```

and /root/.profile:
```
echo "root .profile read..."
PATH=$PATH:/root-profile-read
export PATH

```
and /home/snack/.bashrc
```
echo "snack .bashrc read..."
PATH=$PATH:/user-bashrc
export PATH
```

and /home/snack/.profile
```
echo "snack .bashrc read..."
PATH=$PATH:/user-profile
export PATH
```

From this I learn:
```

               PATH                                                                                                   Controlled by
sudo -i	       /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin:/root-bashrc:/root-profile hardcoded into sudo,/root/.bashrc,/root/.profile
sudo -s	       /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin   			      hardcoded into sudo        
sudo bash      /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin   			      hardcoded into sudo
sudo su	       /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/etc-environment:/root-bashrc  /etc/environment,/root/.bashrc
sudo su user   /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/etc-environment:/user-bashrc  /etc/environment,/home/user/.bashrc
sudo su - user /usr/local/bin:/usr/bin:/bin:/usr/games:/env_path:/user-bashrc:/user-profile                           /etc/login.defs(ENV_PATH),/home/user/.bashrc,/home/user/.profile

If run as root
su         /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/etc-environment:/root-bashrc    /etc/environment,/root/.bashrc
su user    /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/etc-environment:/user-bashrc    /etc/environment,/home/user/.bashrc
su -       /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/env_supath:/root-bashrc:/root-profile      /etc/login.defs(ENV_SUPATH),/root/.bashrc,/root/.profile
su - root  /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/env_supath:/root-bashrc:/root-profile      /etc/login.defs(ENV_SUPATH),/root/.bashrc,/root/.profile
su - user  /usr/local/bin:/usr/bin:/bin:/usr/games:/env_path:/user-bashrc:/user-profile                             /etc/login.defs(ENV_PATH),/home/user/.bashrc,/home/user/.profile

```

I know pauper essentially already said all this, but the above allowed me to see an explicit demonstration of the effect of /etc/environment, and /etc/login.defs.

Conclusion: su without a dash reads /etc/evironment and the .bashrc of the user you are su'ing to. 'su -' (with a dash), reads /etc/login.defs ENV_PATH or ENV_SUPATH, then .bashrc, then .profile of the user you are su'ing to.

---

