---
title: "Running bash script as root from anywhere"
date: 2011-09-22
forum: New to Ubuntu
---

### Post by elysianfields44 on 2011-09-22
I wrote a bash script which I want to be able to run from anywhere, and I need to run it as root. I have done the following:
[LIST]
[*]Permissioned it 777
[*]Added the /path/to/myscript.sh to the $PATH (both in ~/.bashrc and in /root/.bashrc)
[*]Ran: source .bashrc on both bashrc files
[/LIST]

Yet, when I try to run:

```
sudo myscript.sh
```

I get the following error:

```
sudo: myscript.sh: command not found
```


(Please note that when I run: myscript.sh, that works just fine. However, for the purposes of my script, I need to run it as root.)

Also, the output of *which* is correctly identifying the /path/to/myscript.sh

What am I missing? Thanks in advance.

---

### Post by psrdotcom on 2011-09-22
Please use 
 
```
sudo ./your_script.sh
```
 
else use
 
```
 
sudo sh your_script.sh

```

---

### Post by bodhi.zazen on 2011-09-22
Any script to be run as root should be owned as root and writable ONLY by root, so permissions of 777 are inappropriate.

When you run sudo, it cleans your environmental variables.

You can sudo -E or sudo /full/path/to/script

see man sudo for details

---

### Post by elysianfields44 on 2011-09-22
> **psrdotcom said:**
> Please use 
 
```
sudo ./your_script.sh
```
 
else use
 
```
 
sudo sh your_script.sh

```

The whole point is to be able to run the script from *anywhere* so I don't want to have to do sudo ./myscript.sh - if I add the /path/to/myscript.sh to $PATH, that should allow me to simply run sudo myscript.sh.

Please note that running:

```
myscript.sh
```

from anywhere does work. Running it as root, however, does not. 

Also, the second command you suggested gives the following error:

```
sudo sh myscript.sh
sh: Can't open myscript.sh
```

---

### Post by psrdotcom on 2011-09-22
Have you given the permissions with sudo 
 
```
sudo chmod 777 myscript.sh
```
 
Try this ..

---

### Post by elysianfields44 on 2011-09-22
> **bodhi.zazen said:**
> Any script to be run as root should be owned as root and writable ONLY by root, so permissions of 777 are inappropriate.

When you run sudo, it cleans your environmental variables.

You can sudo -E or sudo /full/path/to/script

see man sudo for details

I tried:

```
sudo chown root:root myscript.sh
sudo chmod 755 myscript.sh
```

Still doesn't work.

I also tried:

```
sudo -E myscript.sh
```

but alas that doesn't work as well, same command not found error as before.

Can you please explain why is it that root can't run scripts that are owned or editable by users?

Thanks.

---

### Post by elysianfields44 on 2011-09-22
> **psrdotcom said:**
> Have you given the permissions with sudo 
 
```
sudo chmod 777 myscript.sh
```
 
Try this ..

Yes, I have... it's in my original post.

---

### Post by psrdotcom on 2011-09-22
Try to put your script in /usr/sbin and then try to run ..

---

### Post by Porcini M. on 2011-09-22
> **elysianfields44 said:**
> 
```
sudo: myscript.sh: command not found
```


That error message might be due to a command not found *within* the script - i.e. it might actually be running the script, then tripping over one of the steps. Try adding some echo statements in there.

---

### Post by sisco311 on 2011-09-22
As bodhi.zazen pointed it out, sudo resets PATH. If memory servers, /usr/local/bin is in sudo's PATH by default. You can check it with **sudo sudo -V**. So, I'd put the script there.

Call it nitpicking, but you shouldn't use extensions for your scripts. Scripts are commands that you can run, and commands are generally not given extensions. Also, bash scripts are NOT sh scripts.

---

### Post by elysianfields44 on 2011-09-22
> **psrdotcom said:**
> Try to put your script in /usr/sbin and then try to run ..

That does work! Thanks.

But why is that? Note that I added the original path to the $PATH variable and exported it (I added it to both the user bashrc AND the root bashrc files). When I run: 

```
echo $PATH
```

the returned path does include the original /path/to/myscript.sh

How can I check the $PATH environment variable for the root user? I feel like that's the key thing that wasn't working.

---

### Post by elysianfields44 on 2011-09-22
> **Porcini M. said:**
> That error message might be due to a command not found *within* the script - i.e. it might actually be running the script, then tripping over one of the steps. Try adding some echo statements in there.

That's not it - when I run 

```
sudo ./myscript.sh
```

(i.e. from within the same directory), it runs with no errors.

---

### Post by psrdotcom on 2011-09-22
As per the previous reply, you can **remove the .sh extension** and just place you **myscript **file with **executable** permission in **usr/local/bin** folder ..

Hope, it will solve your problem ..

---

### Post by elysianfields44 on 2011-09-22
> **sisco311 said:**
> As bodhi.zazen pointed it out, sudo resets PATH. If memory servers, /usr/local/bin is in sudo's PATH by default. You can check it with **sudo sudo -V**. So, I'd put the script there.

The ownership and permissions should be root:root 0755 or root:mygroup 0750 (if you only want to allow users from mygroup to run the script).

Call it nitpicking, but you shouldn't use extensions for your scripts. Scripts are commands that you can run, and commands are generally not given extensions. Also, bash scrips are NOT sh scripts.

Aha! I ran:

```
sudo sudo -V
```

And it looks like the root's PATH does not include the /path/to/myscript.sh

So how do I go about adding a path to the root user's PATH? I already added it in /root/.bashrc using:

```
export PATH=$PATH:/path/to/myscript.sh
```

but it's not showing up in the output of sudo sudo -V...??

PS - I'll rename the script to have no extension. :)

---

### Post by elysianfields44 on 2011-09-22
Also, yes, you are right and it does work when I put it in /usr/local/bin but I would still like to figure out how to make it run when it's located in /my/path/.

---

### Post by sisco311 on 2011-09-22
> **elysianfields44 said:**
> 
So how do I go about adding a path to the root user's PATH?


You could edit the sudoers file (see: **man sudoers**), but I wouldn't do that. If you don't want to move the script in a directory which is already in sudo's PATH, then you could create an alias or function for your user:
```
alias script='sudo /full/path/to/script'
```

---

### Post by elysianfields44 on 2011-09-22
> **sisco311 said:**
> You could edit the sudoers file (see: **man sudoers**), but I wouldn't do that. If you don't want to move the script in directory which is already in sudo's PATH, then you could create an alias or function for your user:
```
alias script='sudo /full/path/to/script'
```

Thank you for the suggestions! In addition to the above, I found the following also works:

```
sudo -i myscript
```

Thanks again. I'll mark this thread as solved.

---

### Post by psrdotcom on 2011-09-22
See these links may help you ..

[http://ubuntuforums.org/archive/index.php/t-968662.html](http://ubuntuforums.org/archive/index.php/t-968662.html)

[http://stackoverflow.com/questions/257616/sudo-changes-path-why](http://stackoverflow.com/questions/257616/sudo-changes-path-why)

[http://ubuntuforums.org/archive/index.php/t-512521.html](http://ubuntuforums.org/archive/index.php/t-512521.html)

Try this one ..

copied from [https://answers.launchpad.net/ubuntu/+question/3199](https://answers.launchpad.net/ubuntu/+question/3199)
```

i just add this to my ~/.bashrc
 export JAVA_HOME=/usr/lib/jvm/java-6-openjdk
export PATH=$PATH:$JAVA_HOME/bin
export CATALINA_HOME=/opt/apache-tomcat-5.5.26
export PATH=$PATH:$CATALINA_HOME/bin
export ANT_HOME=/usr/share/ant
export PATH=$PATH:$ANT_HOME/bin
 $CATALINA_HOME/bin/startup.sh
 then
$  source ~/.bashrc
 it works


```

---

### Post by anewguy on 2011-09-22
I'm a little curious as to what is IN the script.  Just why exactly do you need to be able to run it from anywhere?  Are you planning on taking this on a flash drive or other media to another PC and run something as root?
If so, why - and that's an important answer we should have before we proceed any further.

Dave ;)

---

