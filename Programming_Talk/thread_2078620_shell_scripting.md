---
title: "shell scripting"
date: 2012-10-31
forum: Programming Talk
---

### Post by Mohan1289 on 2012-10-31
hi all
i am beginner in shell scripting 
i wrote this shell script 
tell me does this work

correct me if i am wrong

[B]#!/bin/bash
#Only Sudo can run the script
ROOT_UID=0 #Since Only users with $UID 0 have root privileges
E_NOTROOT=87 #Non-root Exit Error

if [ "$UID" -ne "$ROOT_UID" ]; then
echo "You Must be root to run this script"
exit $E_NOTROOT
fi
echo "Enter your Username"
read r

if [-d "/home/$r"]; then
cd "/home/$r/projects"
else
echo "Incorrect username"
fi
echo "Enter File name"
read f
unzip "$f" "/jboss/default/deploy"
echo "Deployed Successfully"

[/B]

---

### Post by trent.josephsen on 2012-10-31
What do you mean "does it work"? You can test it yourself, right?

---

### Post by muteXe on 2012-10-31
+1

#-o

---

### Post by Lars Noodén on 2012-10-31
Also, the script will be more readable if you nest it in [****code][/code] tags.  What are you aiming to do?

---

### Post by ofnuts on 2012-10-31
Try 
```

sudo printenv

```You'll find SUDO_* variables that contain useful stuff.

The unzip command won't work as it is. unzip writes the files in the current directory, and filters the unzipped file using the second argument. So you are actually unzipping the file in /home/$r/projects instead of /jboss/default/deploy. You need to use "-d /jboss/default/deploy"

Now, your script goes against the general Unix CLI philosophy. Asking for directory and name separately is very bad form in a Unix shell, because you can't use filename completion... Your script should really be called as:
```

deploy_stuff /the/path/to/the/file.zip

```(which is very quickly done using filename completion). And somewhere have
```

sudo unzip $1 -d /jboss/default/deploy

```If more commands require sudo, you can either prefix them all with sudo (password will only be asked for the first), or use a sudo'ed subscript (or call the script itself recursively as a sudo'ed command)

---

### Post by Mohan1289 on 2012-11-01
> **trent.josephsen said:**
> What do you mean "does it work"? You can test it yourself, right?

I am not in home i am abroad and my friend doesn't have a Linux OS so i am asking you Guys

---

### Post by greenpeace on 2012-11-01
> **Mohan1289 said:**
> I am not in home i am abroad and my friend doesn't have a Linux OS so i am asking you Guys

But... we don't know exactly what it is supposed to do! :)

Also, the script involves specific directories, which may or may not exist on our machines.

---

### Post by Mohan1289 on 2012-11-01
> **greenpeace said:**
> But... we don't know exactly what it is supposed to do! :)

Also, the script involves specific directories, which may or may not exist on our machines.

Then at least please tell me this

Is the LOGIC correct???

---

### Post by trent.josephsen on 2012-11-01
Correct for what? What is it *supposed* to do? Don't post a script and ask us to test it without telling us what the expected behavior is...

---

### Post by greenpeace on 2012-11-01
> **Mohan1289 said:**
> Is the LOGIC correct???

We can't tell you if it is "correct" or not, as you still haven't said what it should actually do.  Also, because you haven't used ```
 tags (see the # icon in the editor), it's very hard to read.  I've separated it out a little, and put it in tags to make it readable:

[CODE]#!/bin/bash
#Only Sudo can run the script
ROOT_UID=0   #Since Only users with $UID 0 have root privileges
E_NOTROOT=87 #Non-root Exit Error

if [ "$UID" -ne "$ROOT_UID" ]; then
        echo "You Must be root to run this script"
        exit $E_NOTROOT
fi

echo "Enter your Username"
read r

if [-d "/home/$r"]; then
        cd "/home/$r/projects"
        else
        echo "Incorrect username"
fi

echo "Enter File name"
read f

unzip "$f" "/jboss/default/deploy"
echo "Deployed Successfully"


```

Then I will assume that you want to do the following:

1. check the user is root (return error 87 if not)
2. collect a string representing a username
3. check if that username has an existing home directory (returning "Incorrect username" if not)
4. "cd" to a dir called projects in that user's directory 
5. collect a string representing a file name
6. unzip this file to a jboss directory
7. regardless of success of previous command, report the deployment as a success.

Some comments:

1. The "check they're root" section could be much simpler (and your current code doesn't actually work):

```
if [ "$(id -u)" != "0" ]; then
   echo "This script must be run as root" 1>&2
   exit 87 # non-root user exit code
fi
```

2. why not skip checking that the user's home dir exists, and just check that the projects dir exists before you cd into it?

3. that unzip command will not explode the .zip to that directory.  you're missing the "-d" option, check the man pages for more details.

4. Is that how you're deploying your jboss applications?  Is there someway you can see that the deployment command exited successfully?  At the moment, you're saying that it was deployed successfully without even being sure that it was... 

5. use more explicit variables (no, not that kind of explicit). eg. "$file_to_be_deployed" instead of $f; it makes it easier for you when you come back to make changes to a script after 6 months.

---

### Post by ofnuts on 2012-11-01
> **Mohan1289 said:**
> hi all
i am beginner in shell scripting 
i wrote this shell script 
tell me does this work

correct me if i am wrong

[B]#!/bin/bash
#Only Sudo can run the script
ROOT_UID=0 #Since Only users with $UID 0 have root privileges
E_NOTROOT=87 #Non-root Exit Error

if [ "$UID" -ne "$ROOT_UID" ]; then
echo "You Must be root to run this script"
exit $E_NOTROOT
fi
echo "Enter your Username"
read r

if [-d "/home/$r"]; then
cd "/home/$r/projects"
else
echo "Incorrect username"
fi
echo "Enter File name"
read f
unzip "$f" "/jboss/default/deploy"
echo "Deployed Successfully"

[/B]

Hmmm. This also means you run your server as 'root'. Bad idea....

---

### Post by Mohan1289 on 2012-11-02
> **ofnuts said:**
> Hmmm. This also means you run your server as 'root'. Bad idea....

why so?

---

### Post by greenpeace on 2012-11-02
Running jboss as a privileged user exposes you to security issues in the eventuality that your web application is compromised.

---

### Post by Mohan1289 on 2012-11-02
> **greenpeace said:**
> Running jboss as a privileged user exposes you to security issues in the eventuality that your web application is compromised.

Yes that's true so how can i prevent it...

so i should create a user group and allow them only to run this script??

by using Group id??

---

### Post by greenpeace on 2012-11-02
Probably best you do some research about setting up Jboss... Search in the wiki [1], and on Google [2]
 
[1] [https://wiki.ubuntu.com/JBoss](https://wiki.ubuntu.com/JBoss)
[2] [https://www.google.com/search?q=jboss+ubuntu](https://www.google.com/search?q=jboss+ubuntu)

---

### Post by Mohan1289 on 2012-11-03
> **greenpeace said:**
> We can't tell you if it is "correct" or not, as you still haven't said what it should actually do.  Also, because you haven't used ```
 tags (see the # icon in the editor), it's very hard to read.  I've separated it out a little, and put it in tags to make it readable:

[CODE]#!/bin/bash
#Only Sudo can run the script
ROOT_UID=0   #Since Only users with $UID 0 have root privileges
E_NOTROOT=87 #Non-root Exit Error

if [ "$UID" -ne "$ROOT_UID" ]; then
        echo "You Must be root to run this script"
        exit $E_NOTROOT
fi

echo "Enter your Username"
read r

if [-d "/home/$r"]; then
        cd "/home/$r/projects"
        else
        echo "Incorrect username"
fi

echo "Enter File name"
read f

unzip "$f" "/jboss/default/deploy"
echo "Deployed Successfully"


```Then I will assume that you want to do the following:

1. check the user is root (return error 87 if not)
2. collect a string representing a username
3. check if that username has an existing home directory (returning "Incorrect username" if not)
4. "cd" to a dir called projects in that user's directory 
5. collect a string representing a file name
6. unzip this file to a jboss directory
7. regardless of success of previous command, report the deployment as a success.

Some comments:

1. The "check they're root" section could be much simpler (and your current code doesn't actually work):

```
if [ "$(id -u)" != "0" ]; then
   echo "This script must be run as root" 1>&2
   exit 87 # non-root user exit code
fi
```2. why not skip checking that the user's home dir exists, and just check that the projects dir exists before you cd into it?

3. that unzip command will not explode the .zip to that directory.  you're missing the "-d" option, check the man pages for more details.

4. Is that how you're deploying your jboss applications?  Is there someway you can see that the deployment command exited successfully?  At the moment, you're saying that it was deployed successfully without even being sure that it was... 

5. use more explicit variables (no, not that kind of explicit). eg. "$file_to_be_deployed" instead of $f; it makes it easier for you when you come back to make changes to a script after 6 months.

Thanks for your suggestions i will try to improve myself

---

