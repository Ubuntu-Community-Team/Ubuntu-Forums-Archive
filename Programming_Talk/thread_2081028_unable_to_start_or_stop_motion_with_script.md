---
title: "unable to start or stop motion with script"
date: 2012-11-05
forum: Programming Talk
---

### Post by Mia_tech on 2012-11-05
I have the following script that pretty much check for the status of motion daemon and based on that it stop it or start the daemon, I have added the command along with my username to sudoers file so I don't have to run the script with sudo credentials; however, the script is unable to start or stop the service. 

```
#!/bin/bash
# script to start/stop motion and remove content from file
# 11/5/2012

dir=/tmp/motion

ps -e | grep motion
if [ $? -eq 0 ]; then
	#motion is running and need to stop
	echo "Stopping motion and removing files..."
	service motion stop 
	if [ -d $dir ]; then
		rm -rf $dir/ 2> /dev/null
	fi
	
else
	#motion is not running and need to start
	echo "Starting motion..."
	service motion start
fi
```

output when trying to start
```
jorge@nixboxen:~$ ./mocheck.sh 
Starting motion...
chown: changing ownership of `/var/run/motion': Operation not permitted

```
output when trying to stop
```
Stopping motion and removing files...
 * Stopping motion detection daemon motion 
No /usr/bin/motion found running; none killed.
                                                               [ OK ]
```

---

