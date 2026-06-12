---
title: "[solved] adding a line to rc.conf"
date: 2013-04-06
forum: New to Ubuntu
---

### Post by santiagorf on 2013-04-06
Hi all,
I have the following **/etc/rc.conf** file, and I would like to generate a script (installer) that adds a couple of command to the **/etc/rc.conf** file before the **exit 0** line.
I want to add this commands here as they both run as root and are executed at the end of the start up process.

The command in the script that adds the line to the **/etc/rc.conf** file could be something like this:
```

sudo echo <command_to_add> >>/etc/rc.conf

```
but in this case the line would be added after the **exit 0** command.

The script should run on Ubuntu 12.4. Note that the **rc.conf** below might differ since this one is taken from another distribution.
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

mkdir -p /dev/cgroup/cpu
mount -t cgroup cgroup /dev/cgroup/cpu -o cpu
mkdir -m 0777 /dev/cgroup/cpu/user
echo "/usr/local/sbin/cgroup_clean" > /dev/cgroup/cpu/release_agent

**echo 'I want to add the commands here !'**

exit 0

```

Any help would be much appreciated!

---

### Post by ajgreeny on 2013-04-06
Have a good look at the sed command which can certainly do what you want.  As an example I found:

sudo sed -e '/^d.*$/a\energetic' /path/to/file
Which says use sed **(sed)** to execute the sed command **(-e)** 'match a line **(/)** starting with d **(^d)**, continuing with any following characters **(.*)** to the end of the line **($) (/)**, then append a line **(a\)** with the word **(energetic)**'

It is also possible to specify line number, but I'm afraid I have never used sed so I'm not the right person to try to give more detailed answers.  Hopefully this may point you in the right direction

---

### Post by schragge on 2013-04-06
In your case, it probably should be
```
sudo sed -i '/^exit 0/i[COLOR=blue]command to add[/COLOR]' /etc/rc.local
```
**/^exit 0/i** meaning *insert _before_ each line containing exactly [COLOR=red]exit 0[/COLOR]* As long as there's only one such line in the script it will do the right thing.

To insert a line before the last line, just do:
```
sudo sed -i '$i[COLOR=blue]command to add[/COLOR]' /etc/rc.local
```
To combine both conditions, do
```
sudo sed -i $'${/^exit 0/i[COLOR=blue]command to add[/COLOR]\n}' /etc/rc.local
```
As there may be several blanks before *exit* or between *exit* and *0*, a better way to do it would be
```
sudo sed -i $'${/^[ \t]*exit[ \t]\+0/i[COLOR=blue]command to add[/COLOR]\n}' /etc/rc.local
```
If you want to add a command only before the first occurence of *exit 0*, do it like this:
```
sudo sed -i '0,/^[ \t]*exit[ \t]\+0/s//[COLOR=blue]command to add[/COLOR]\n&/' /etc/rc.local
```
To do the same only before the last occurence of *exit 0* when it is not on the last line, you can
```
sudo sed -inr '1h;1!H;${g;s/(.*\n)([ \t]*exit[ \t]+0)/\1[COLOR=blue]command to add[/COLOR]\n\2/p}'
```
But I'd rather use [ex]("http://manpages.ubuntu.com/manpages/precise/en/man1/ex.1posix.html") or [ed]("http://manpages.ubuntu.com/manpages/precise/en/man1/ed.1.html") than sed for this:
```
sudo ex -s /etc/rc.local <<<$'?^[ \t]*exit[ \t]\+0?i\n[COLOR=blue]command to add[/COLOR]\n.\nx'
```
The same in more readable form:
```

<<END sudo ex -s /etc/rc.local
?^[ \t]*exit[ \t]\+0?i
[COLOR=blue]command to add[/COLOR]
.
x
END

```
Even this may be problematic as *exit 0* not necessarily stands alone on the line. Consider something like
```

if some_test
then do_something; exit 0 # comment
else exit 1
fi

```
The right thing to do in this case probably would be
```
sudo ex -s /etc/rc.local <<<$'?exit[ \t]\+0?s//[COLOR=blue]command to add[/COLOR]; &\nx'
```
or
```
sudo sed -inr '1h;1!H;${g;s/(.*)(exit[ \t]+0)/\1[COLOR=blue]command to add[/COLOR]; \2/p}'
```
The expression above may be simplified if using GNU sed 4.2.2
```
sudo sed -irz 's/(.*)(exit[ \t]+0)/\1[COLOR=blue]command to add[/COLOR]; \2/'
```
or perl
```
sudo perl -i -0pe 's/(.*)(exit\h+0)/$1[COLOR=blue]command to add[/COLOR]; $2/s'
```
As you can see doing it right is non-trivial when you are not controlling the contents of the file. Rather than trying to insert something immediately before *exit 0*, I'd insert my commands just before the first non-empty line that doesn't start with a comment:
```
sudo sed -i '0,/^[^#]/s//[COLOR=blue]command to add[/COLOR]\n&/' /etc/rc.local
```
or
```
sudo ex -s /etc/rc.local <<<$'/^[^#]/i\n[COLOR=blue]command to add[/COLOR]\n.\nx'
```

BTW, I believe automatically changing */etc/rc.local* by script to be a bad idea per se. This file is intended for local changes made by system administrator. Applications should install their traditional init scripts in */etc/init.d/* or their upstart rules in */etc/init/*.

---

### Post by ajgreeny on 2013-04-06
Thanks for that schragge; it's a great help to me as well as the OP, I suspect.

I found **man sed** a bit convoluted and difficult to follow properly, but your detailed info does the trick.

---

### Post by Hadaka on 2013-04-06
hi, give this a try
```
echo command_to_add | sudo tee -a /etc/rc.conf
```
have fun !

---

### Post by schragge on 2013-04-06
@**Hadaka** Please reread the thread. Your command will append a line after the last line in the file, not _before_ it.

---

### Post by santiagorf on 2013-04-06
Thank you for the prompt prompt replies!!
When I get home, I'll have a look at them.

---

