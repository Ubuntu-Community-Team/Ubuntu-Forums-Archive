---
title: "Su not working in shell script"
date: 2012-01-19
forum: New to Ubuntu
---

### Post by iamthepiguy on 2012-01-19
I have a shell script in bash that is run from a launcher using gksudo, so it is root, then is supposed to su into another user and run another shell script (as the other user). However, upon viewing my debug log, it appears that the su doesn't change user, but it still exits with no complaint.

Here is the script:
```
#!/bin/bash
echo "Begin" | tee -a /home/.manage/bukkit/bukkit.log
date | tee -a /home/.manage/bukkit/bukkit.log
echo "Currently logged in as: $USER:$UID" | tee -a /home/.manage/bukkit/bukkit.log
su --login bukkit | tee -a /home/.manage/bukkit/bukkit.log
echo "Starting Server as user $USER:$UID..." | tee -a /home/.manage/bukkit/bukkit.log
screen -dmS bukkit -h 500 '/home/.manage/bukkit/start-server.sh'
touch /home/.manage/bukkit/bukkit_success
echo "Finished" | tee -a /home/.manage/bukkit/bukkit.log
```

And here is the relevant log section:
```
Begin 
Thu Jan 19 15:44:30 EST 2012
Currently logged in as: root:0
Starting Server as user root:0...
Finished
```

---

### Post by WthIteh on 2012-01-19
Indeed the "su" will change user. But the new user session will be closed as soon as that command finished execution and reaches the next line of script.
In order to use some commands using "su" you should use "-c" option like this:
```
su bukkit -c whoami
```It's a good practice to place commands which must be run by another user, in a separate file which leads to command like this:
```
su bukkit -c other.sh
```

---

### Post by iamthepiguy on 2012-01-20
So I should basically plonk the echo, screen and touch commands in the other shell script it links to? I have no problem with that. Sounds like I was already halfway there with the other shell script. Thanks for your help, I forgot the shell script commands after su aren't passed into the new session.

---

