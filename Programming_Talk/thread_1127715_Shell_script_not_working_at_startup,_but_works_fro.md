---
title: "Shell script not working at startup, but works from command line"
date: 2009-04-16
forum: Programming Talk
---

### Post by whitemank on 2009-04-16
I've created an Ubuntu Hardy instance on Amazon EC2 that will be used to run nightly batch transactions.  The instance is created inside a cron script on one of my database servers.  On the batch instance, I've created a script that gets called on instance startup that runs the batch and then kills the instance when it is done.
```

#!/bin/bash
# Make sure other startup scripts have finished executing
sleep 300 
# Get IP and instance id
public_ip=`curl -s http://169.254.169.254/latest/meta-data/local-ipv4`
instance_id=`curl -s http://169.254.169.254/latest/meta-data/instance-id`
#authorize this instance_id to access mysql server
ec2-authorize scalr.mysqllvm -P tcp -p 3306 -s $public_ip/32
#run batch transactions
curl http://$public_ip/run_batch.php
#revoke mysql access for this IP
ec2-revoke scalr.mysqllvm -P tcp -p 3306 -s $public_ip/32
#wait 5 minutes to give user time to move the terminate script if they don't want the instance to terminate
sleep 300
#terminate the instance
sh /root/gsTerminate.sh
```


The script is in /etc/init.d and has been added via:
update-rc.d batchStartup.sh defaults

I've added the EXPORT commands for the AWS tools environment variables to /etc/bash.bashrc so they should be available on startup.  However, when I run the instance, the instance comes up, but the script is either not being executed or is failing.  However, I can ssh into the instance and run the script from the command line once the instance is up and it runs fine. 

Looking through /var/log/messages, I found these lines that seem to coincide with startup.  Does anyone know what I am doing wrong???  Weird...  Is it an environment variable issue from within a script versus the shell? 

Apr 15 01:13:14 (none) S71ec2-run-user-data: Retrieving user-data
Apr 15 01:13:14 (none) S71ec2-run-user-data: curl: (22) The requested URL returned error: 404
Apr 15 01:13:14 (none) S71ec2-run-user-data: No user-data available

---

### Post by monkeyking on 2009-04-16
Just an idea,
test if the cron user has permission to run the stuff

---

### Post by whitemank on 2009-04-17
If I add a startup script using update-rc.d while logged in as root, does the script get executed as a cron user when it is run at startup?  If so, you could be on to something.  I'll check it out.

---

### Post by whitemank on 2009-04-17
I just checked it using: 

```

#!/bin/bash
whoami > /root/whoami.txt

```

and it is running the script as root.  Must be something else.

---

### Post by zeex on 2009-04-17
Hi, 

you used the default setting of update-rc.d That could be the problem and your script has networking commands (get ip) some runlevel does not provide networking. 

In default setting of update-rc.d the script is executed at number 20. It's always a good thing to execute your script at the end.

Try this

**$ sudo update-rc.d <*script_name*> remove**
**$ sudo update-rc.d -f <*script_name*> start 99 2 3 4 5 .**
( There is a dot (.) at the end of the command don't forget that and [check this out]("http://stringofthoughts.wordpress.com/2009/04/16/adding-removing-shell-scripts-ubuntu-810/") , might help )

Good luck :)

---

