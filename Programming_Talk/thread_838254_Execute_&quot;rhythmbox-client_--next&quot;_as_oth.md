---
title: "Execute &quot;rhythmbox-client --next&quot; as other user"
date: 2008-06-23
forum: Programming Talk
---

### Post by `GooZ´ on 2008-06-23
Hi,

I'm writing a small web front-end to control rhythmbox (it's so I can use my phone to control it while I'm listening wireless in my house).
So far I'm writing the app as a small python CGI script.

Now I'm trying to execute the os commands by running "rhythmbox-client --next", but of course this won't work on my current running instance of rhythmbox, because apache is executing it as the root user.

I already tried executing it with
```
sudo -u <username> rhythmbox-client --next
```
but all I get is the following dbus error:
```
(rhythmbox-client:30712): Rhythmbox-WARNING **: Failed to connect to socket /tmp/dbus-I1Argi1OJw: Connection refused
```

Any ideas?

---

### Post by `GooZ´ on 2008-06-23
Update: Apparently, if I go inside a terminal, log in as root user, and then type
```
su <username>
```
and after that run the previous command, I get the same error. Maybe this has something to do with the current session of the user?

---

### Post by imac_89 on 2008-10-12
I am wondering the very same. I am attempting to do the same thing only with php. I am getting the same error now as well:
(rhythmbox-client:7893): Rhythmbox-WARNING **: Failed to connect to socket /tmp/dbus-WONJCVH3KM: Connection refused

I have my apache server setup to run as my user so (my obvious hope) that it would interact with my account. My code is: exec('rhythmbox-client --'.$task);
In this case $task would equal someting like 'play-pause'.

---

### Post by boblemur on 2009-07-04
this will do what you are expecting:

DBUS_ADDRESS=`grep -z DBUS_SESSION_BUS_ADDRESS /proc/*/environ 2> /dev/null| sed 's/DBUS/\nDBUS/g' | tail -n 1`

# if it was successfull, then we either print it, or export it or whatever, if we want
if [ "x$DBUS_ADDRESS" != "x" ]; then
export $DBUS_ADDRESS
rhythmbox-client $1
fi


so in python:

os.popen("""export DBUS_ADDRESS=`grep -z DBUS_SESSION_BUS_ADDRESS /proc/*/environ 2> /dev/null| sed 's/DBUS/\nDBUS/g' | tail -n 1` && rhythmbox-client rythmbox-client --play""")

and php should be something reasonably similar. good luck, hopefully you still want to know this :P its been a while...

---

