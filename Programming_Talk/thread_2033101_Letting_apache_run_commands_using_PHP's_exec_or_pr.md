---
title: "Letting apache run commands using PHP's exec or proc_open commands...security risk?"
date: 2012-07-25
forum: Programming Talk
---

### Post by ltwinner on 2012-07-25
I have a web page that lets users enter commands and then I am using proc_open()/exec() in php to run these commands on the terminal.

I sent in the command 'whoami' and it returned 'www-data' which represents apache afaik. So is this a security risk, does anyone know what this www-data user is and isn't allowed to do on a system?

I sent in the command 'rm delete_me.txt' to delete a file called delete_me.txt which is stored in a subfolder of the apache document root /var/www/subfolder/ and it wouldn't delete the file, it gave an error saying -

[HTML]rm: cannot remove `/var/www/subfolder/delete_me.txt': Permission denied [/HTML]

So that seems pretty promising security wise, considering it won't even let www-data delete files from apaches own document root...

---

### Post by ltwinner on 2012-07-25
So I've looked into it a bit more and /var/www/ and it's subfolders are owned by root, hence why the www-data user can't delete items in them. However I ran the command 'cat /home/me/read_me.txt' and i was able to read the file.

This is obviously unacceptable, I can't have user's reading any file they want to on the system. So is there a way of limiting the www-data user to only have permission to do anything inside the /var/www/ directory?

---

### Post by SlugSlug on 2012-07-25
Your giving the world shell access to your box.

they could wget some code and quite possibly execute it under www-data.

Its a whole can of worms :)

but you can limit your /home/me to only you

chmod 750 /home/me

---

### Post by ofnuts on 2012-07-25
> **SlugSlug said:**
> Your giving the world shell access to your box.

they could wget some code and quite possibly execute it under www-data.

Its a whole can of worms :)

but you can limit your /home/me to only you

chmod 750 /home/meUntil a new exploit comes along... 

You can't really achieve any level of security if you allow your users to execute arbitrary commands.

---

### Post by SlugSlug on 2012-07-25
> **ofnuts said:**
> Until a new exploit comes along... 

You can't really achieve any level of security if you allow your users to execute arbitrary commands.

Don't get me wrong - I strongly advise against this!

---

### Post by RWhitney on 2012-07-26
> **ltwinner said:**
> I have a web page that lets users enter commands and then I am using proc_open()/exec() in php to run these commands on the terminal.

I sent in the command 'whoami' and it returned 'www-data' which represents apache afaik. So is this a security risk, does anyone know what this www-data user is and isn't allowed to do on a system?

I sent in the command 'rm delete_me.txt' to delete a file called delete_me.txt which is stored in a subfolder of the apache document root /var/www/subfolder/ and it wouldn't delete the file, it gave an error saying -

[HTML]rm: cannot remove `/var/www/subfolder/delete_me.txt': Permission denied [/HTML]

So that seems pretty promising security wise, considering it won't even let www-data delete files from apaches own document root...
Whether or not it can delete files is not the issue, the user is still able to execute commands which is bad, nothing is stopping someone from downloading a shell into the /tmp folder of the system and launching it so that they can perform a tcp connection onto their terminal and load into that shell.
From this point they may download other files such as privilege escalation exploits which will allow them to eventually crack into root privileges. Given the experience of any given hacker, this could take only minutes to accomplish.

The goal of security here should be to create as few possibilities for an attacker to enter your systems command line as possible.

I would therefore concluded that yes, this is a security risk and should be removed immediately from your web server.

---

### Post by RWhitney on 2012-07-26
> **ltwinner said:**
> So I've looked into it a bit more and /var/www/ and it's subfolders are owned by root, hence why the www-data user can't delete items in them. However I ran the command 'cat /home/me/read_me.txt' and i was able to read the file.

This is obviously unacceptable, I can't have user's reading any file they want to on the system. So is there a way of limiting the www-data user to only have permission to do anything inside the /var/www/ directory?

And all aside from my last note, they would also be able to read your /etc/passwd file which contains most user data from the system, this right there allows them to learn user names of all those who have access to your box, which can open up another "can of worms" in which they could attempt to brute-force or launch a dictionary attack on your SSH logins in attempt to gain access as well. but why should they need to do that when hell, you are giving them a shell right off the bat! lol. I'd call it quits with this and delete the PHP shell from the drive.

---

### Post by ltwinner on 2012-07-26
> **RWhitney said:**
> And all aside from my last note, they would also be able to read your /etc/passwd file which contains most user data from the system, this right there allows them to learn user names of all those who have access to your box, which can open up another "can of worms" in which they could attempt to brute-force or launch a dictionary attack on your SSH logins in attempt to gain access as well. but why should they need to do that when hell, you are giving them a shell right off the bat! lol. I'd call it quits with this and delete the PHP shell from the drive.

It seems you are saying that this www-data user can do anything they want on the system...

Linux seems wide open security wise from what you are saying. If any user (and www-data is just another user) who has an account on the system can do whatever they want and raise their privileges through some means then Linux is completely unsecure as a multi user system.

So what is the point of even having a root user or an adminstrator group if any user with an account on the system is capable of exploiting the system?

---

### Post by ltwinner on 2012-07-27
So is this safe to do or not? Does anyone have a definitive answer?

---

### Post by SlugSlug on 2012-07-27
Well it's going to open your system up to the world. You'd be better creating shell access for users you trust.

You'd need to know your all file permissions are correct.

Be aware that www-data would be able to spy to a certain degree

(eg. ps -ef might show firefox pages open)

---

### Post by albandy on 2012-07-27
Never let a web server execute system commands. But if you need or want to do it, use a chroot environment in apache.

---

### Post by Some Penguin on 2012-07-28
> **albandy said:**
> Never let a web server execute system commands. But if you need or want to do it, use a chroot environment in apache.

...and preferably with no write permissions anywhere (and on a partition marked 'noexec' if it must be able to write), as a *different* user than the web server itself uses, with strict limitations on the number of file handles and processes that this particular user may create to avoid trivial DOS attacks on everything else it can do.

Even if it had only ordinary privileges and a limited area in which to write files, you really don't need e.g. somebody cat'ing into it a fork bomb to fill your process table, or a web client with which to download child pr0n and then dropping a dime to the Feds.

---

### Post by ltwinner on 2012-07-30
> **Some Penguin said:**
> ...and preferably with no write permissions anywhere (and on a partition marked 'noexec' if it must be able to write), as a *different* user than the web server itself uses, with strict limitations on the number of file handles and processes that this particular user may create to avoid trivial DOS attacks on everything else it can do.

Even if it had only ordinary privileges and a limited area in which to write files, you really don't need e.g. somebody cat'ing into it a fork bomb to fill your process table, or a web client with which to download child pr0n and then dropping a dime to the Feds.

What exactly is the difference between a web server and another regular user? Your post implies that having multiple users on a linux system is a wide open security hole? Because a regular user has just as much power to do damage as the web server.

---

### Post by Tony Flury on 2012-07-30
> **ltwinner said:**
> What exactly is the difference between a web server and another regular user? Your post implies that having multiple users on a linux system is a wide open security hole? Because a regular user has just as much power to do damage as the web server.

One of the key differences is that other users have to log in - with a (hopefully) secure password before they can get to the command line, where as you seem to want to allow anyone at all to have access to the command line via your web server.

It maybe that your plan is to just have PHP execute some commands (server side) with no user input, in which case this will as secure as you can resonably make it.

---

### Post by Some Penguin on 2012-07-30
> **ltwinner said:**
> What exactly is the difference between a web server and another regular user? Your post implies that having multiple users on a linux system is a wide open security hole? Because a regular user has just as much power to do damage as the web server.

You can set separate, per-user limits on things like max simultaneous file handles and processes.  Making any ol' user empowered to easily starve your web server of those limits is not a smart move, assuming that your web server is actually doing anything useful.

---

