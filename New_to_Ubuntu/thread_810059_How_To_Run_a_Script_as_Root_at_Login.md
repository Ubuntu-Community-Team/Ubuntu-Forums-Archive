---
title: "How To Run a Script as Root at Login"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by seagullplayer77 on 2008-05-27
Here's my problem: in order to allow Wicd to even attempt to connect to any wireless networks, I have to run the following to commands first:

sudo ifconfig wlan0 down
sudo ifconfig wlan0 hw ether 00:00:00:00:00:00

I wrote a text file containing those commands and I set the permissions so that the file could be executed as a script and then told Wicd to run the script before it tries to connect, but Wicd won't do it--I've gotta run the two commands manually from a terminal and then reconnect with Wicd. I'm not quite sure why my script isn't working, but I'm suspecting it has something to do with the fact that both commands need to be run as sudo (then again, I'm a Ubuntu newbie--what do I know?). Whatever the problem is, I'd appreciate some help. It's not too terribly important to get it fixed, but it would be a lot easier and quicker if I didn't have to run the commands manually and then tell Wicd to reconnect. Thanks!

---

### Post by spiderbatdad on 2008-05-27
sudo ifconfig wlan0 down &
sudo ifconfig wlan0 hw ether 00:00:00:00:00:00

Of course if root owns the script and it is in /etc/init.d there is no need for sudo

---

### Post by quelx on 2008-05-27
Add those lines (minus the sudo) to **/etc/rc.local**

There are a bajillion ways to do this some more *right* than others

[http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/)

---

### Post by seagullplayer77 on 2008-05-27
Perhaps I should've titled the post differently, because I'm not entirely sure that the script is owned by root. I created it in Gedit, but I believe I was only a regular user when I did. Not sure if that makes any difference...

Also, I'm not too comfortable messing around with /etc/init.d. It sounds as though making a mistake in there would probably royally screw things up. Could I just add the script into Sessions, or just put it into Wicd as a script to run before attempting to run before connecting?

---

### Post by spiderbatdad on 2008-05-27
> **quelx said:**
> Add those lines (minus the sudo) to **/etc/rc.local**

There are a bajillion ways to do this some more *right* than others

[http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/)

:oops: meant /etc/rc.local

---

### Post by spiderbatdad on 2008-05-27
```
sudo chown root:root filename.sh
sudo chmod a+x filename.sh
```

---

### Post by seagullplayer77 on 2008-05-27
I'm not finding /etc/rc.local, although I have found /etc/rc0.d, /etc/rc1.d, and so on, all the way up to /etc/rc6.d. I also have /etc/rcS.d. I'm guessing that the rc# probably refers to a certain run level, although I'm not too sure how all that works either. Should I just stick it in all of them?

---

### Post by spiderbatdad on 2008-05-27
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

exit 0

```

Copy that to a file named /etc/rc.local
make it owned by root. Make it executable. Put in in the /etc directory.

---

### Post by seagullplayer77 on 2008-05-27
Just to confirm I did everything right, here's what my /etc/rc.local file looks like:

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

ifconfig wlan0 down
ifconfig wlan0 hw ether 00:00:00:00:00:00

exit 0

```

Obviously, I have my MAC address in place of the zeroes, but other than that detail, everything else is the same. Will this work properly at startup? Just want to make sure before I try rebooting...

---

### Post by seagullplayer77 on 2008-05-28
Well, I rebooted and the script didn't work--I had to run the commands manually anyway. Any ideas as to why it didn't do what I asked? Am I just entering something in wrong?

---

### Post by drs305 on 2008-05-28
I too have been toying with startup scripts. My successes using the /etc/init.d folders have been mixed. If you need this script only for yourself, and wicd can be started after the system boots, you might try putting the script in Sessions, with a final line in the script to start wicd after running the other commands. Of course, now you have to deal with sudo again.

Just a thought.

---

### Post by mbradlcu on 2008-05-28
I'm sure I'll get heat for this and please if you must use it carefully,, that said:
```

echo "your_passwd" | sudo -S some_command

```

---

