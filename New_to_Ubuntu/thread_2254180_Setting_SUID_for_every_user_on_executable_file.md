---
title: "Setting SUID for every user on executable file"
date: 2014-11-25
forum: New to Ubuntu
---

### Post by ppplayer80 on 2014-11-25
Hi.

I need to set executable file's properties to make it executable for **every** user _with root's privileges_. I found out that SUID will do the trick so I set file's properties with chmod command for owner, for user group and I tried to set it for other users also, but even though there was no error message, file properties do not change. The "best" state I can set is the following: `-rwsrwsrwx`. I cannot make it: `-rwsrwsrws`. What I tried is: `chmod o+s <filename>`, `chmod a+s <filename>` and I also tried this prefixed with `sudo` command. Everytime I do not see any feedback message (just like everything went OK), but nothing is changed on my file.

My OS is Ubuntu 12.04 run on virtual machine.

---

### Post by Lars Noodén on 2014-11-25
SUID is usually something to avoid.  sudo is the usual way to dole out partial privileges.  

```

%subset   ALL=(ALL:ALL) /usr/local/bin/foobar ""

```

That would allow any user that is a member of the group "subset" to run the program (or script) /usr/local/bin/foobar without any parameters.  Alternately, you can list which parameter is allowed.

---

### Post by ppplayer80 on 2014-11-25
Thanks for a reply.

Well, I need to make it available for **every** user. Not only from specific user group. I just wonder why SUID does not work while it does not even display error message...
And your code returns: `bash: syntax error near unexpected token `('`. I may have forgotten to say that I am a Linux noob, so I do not even have an idea what it should do and why it returns syntax error.

---

### Post by Impavidus on 2014-11-25
If you want that every user can execute the file with root privileges, you have to make the file executable for all users and set the SUID bit. This would be -rwsr-xr-x. The second s in -rwsrwsrwx is for the SGID bit. There is no final s as in -rwsrwsrws. Instead there is a t, for the sticky bit, but that is not used on files (not on Linux at least).

And **never** set both the SUID bit and write permission for all users on the same root-owned executable file. It allows all users to change the file into their favorite malware and then execute it with root permission. So the permissions you want are -rwsr-xr-x, or when setting with chmod 4755.

Edit: Lars Noodén was referring to a line you could add to the sudoers file, not to a terminal command. sudo is a bit more complicated to setup, but allows more fine-grained control.

---

### Post by Lars Noodén on 2014-11-25
The above example is a line for sudo's configuration file.  

sudo's options are determined by what you have set in the file /etc/sudoers, so you can set for a user, a group or all users that way.  
You can edit [sudoers](http://manpages.ubuntu.com/manpages/trusty/en/man5/sudoers.5.html) with the program "visudo"

There is a group "users" which is for all users, you can add users to it.
So if you put the following line in /etc/sudoers, 

```

%users   ALL=(ALL:ALL) /usr/local/bin/foobar ""

```

it will let the program "foobar" be run by any user in the group "users", but only without any parameters.  It's *very* important that the script is in a directory that cannot be written by other than root nor should the file itself be writeable by anyone other than root, especially if any user can run it.

Here is a page explaining some of what /etc/sudoers contains:
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

Not all filesystems allow use of suid, since it is considered a problem.  And the same precautions apply about not being writeable or in a writeable directory.

---

### Post by ppplayer80 on 2014-11-25
Thanks Impavidus, now I get it. However it still asks me for a password when I try to execute this program. Maybe I'll say what this program basically does: it launches command prefixed with `sudo`.

And a fragment of `ls -l` output:
> -rwsr-xr-x 1 root  myUsername  8380 Nov 21 15:06 myProgramFilename


EDIT// Lars replied while I was typing this message. I'm gonna read this now...
EDIT2// Thank you Lars. I will try this if SUID method will eventually fail.

---

### Post by Lars Noodén on 2014-11-25
I found a way without groups, it was buried in the manual page for sudoers:

```

ALL   ALL=(ALL:ALL) /usr/local/bin/foobar ""

```

Again the caveats above by Impavidus and I about not leaving the file in a writeable state are important.

If you use suid this time, remember sudo for later.  It might come in handy some other time.

---

### Post by ppplayer80 on 2014-11-25
> Again the caveats above by Impavidus and I about not leaving the file in a writeable state are important.
Yes, I understand. Thanks :)

Well I wanted to use suid but it still seems not to be working... So I tried your method and... it still doesn't work. I basically lost any hope that it will ever work... Do you have any ideas why it still asks me for a password even though it should not?

---

### Post by Lars Noodén on 2014-11-25
With the following on a line in sudoers it should run the script as root, after asking for the password:

```

ALL   ALL=(ALL:ALL) /usr/local/bin/foobar ""

```

With the following, it should run the script without asking for a password:

```

ALL   ALL=(ALL:ALL) NOPASSWD: /usr/bin/whoami ""

```

I hope the script is sane.

---

### Post by ppplayer80 on 2014-11-25
Okay, take a look at what I have here please:

> 
# User privilege specification
root    ALL=(ALL:ALL) ALL
ALL   ALL=(ALL:ALL) NOPASSWD: /home/myUsername/Desktop/[Directories...]/filename ""


Where "[Directories...]" is a directory structure which I am sure is proper. And then I go into this directory and type
> ./filename
And then it asks me for a password...

> I hope the script is sane.
Yes it is. It is wrote by me and this is a program wrote in C language.

---

### Post by Lars Noodén on 2014-11-25
Does it still ask for a password even if you run it like this?

```

sudo /home/myUsername/Desktop/[Directories...]/filename

```

If sudo is used inside "filename" it will need a password unless you add the exact path and name to sudoers.  If it gets anything other than what it is expecting, it will ask for a password.

---

### Post by ppplayer80 on 2014-11-25
> Does it still ask for a password even if you run it like this?
It does.

> If sudo is used inside "filename" it will need a password unless you add the exact path and name to sudoers. If it gets anything other than what it is expecting, it will ask for a password.
But there must be a way to do it without a password :(

---

### Post by Lars Noodén on 2014-11-26
> **ppplayer80 said:**
> But there must be a way to do it without a password :(

There is, we just have to find the exact file+path to put inside /etc/sudoers.  

So to check if I understand the situation, you have a shell script which uses sudo to call another program, right?  Can you show the exact line from the script that calls that other program?  You can sanitize it if you wish.

---

### Post by ppplayer80 on 2014-11-26
> So to check if I understand the situation, you have a shell script which uses sudo to call another program

No. I have program wrote in C language. But yes, it uses sudo to call another program :)

> Can you show the exact line from the script that calls that other program? 

Well, that's it:

```
system("sudo bash");
```

---

### Post by Lars Noodén on 2014-11-26
> **ppplayer80 said:**
> No. I have program wrote in C language. But yes, it uses sudo to call another program :)



Well, that's it:

```
system("sudo bash");
```

Ok but then the line in sudoers would have to be for bash, including the path, not your program.  However, as you describe make it sound, you would be giving each and every user on your machine full root access to all corners of your system.  That's usually quite questionable.  Can I ask what problem you are trying to solve?

---

### Post by ppplayer80 on 2014-11-26
> Can I ask what problem you are trying to solve?

Well, to be honest... It is an exercise on my studies (Operating Systems course). We have to write a program that launches bash shell with root's privileges and then make it executable for every user without passing the password. A tip in this task's description was to use SUID. And by the way: it is a first exercise on a list, it is just a warm up and I already managed to do every other exercise and now I'm stuck here with the first one :(

I know that it sounds crazy (launching bash with root's privileges without a password) but I think that our lecturer just wants to see if we are able to do something like this. He does not want us to use it every day:)

---

### Post by redmk2 on 2014-11-26
> **ppplayer80 said:**
> Well, to be honest... It is an exercise on my studies (Operating Systems course). We have to write a program that launches bash shell with root's privileges and then make it executable for every user without passing the password. A tip in this task's description was to use SUID. And by the way: it is a first exercise on a list, it is just a warm up and I already managed to do every other exercise and now I'm stuck here with the first one :(

I know that it sounds crazy (launching bash with root's privileges without a password) but I think that our lecturer just wants to see if we are able to do something like this. He does not want us to use it every day:)

Ahhhhhhhhhhhhhhhhhhh!  *"Well, to be honest..."* should have come first.  After all that mucking about, this turns out to be a school assignment.  Assisting in homework is frowned upon on this forum.  Note this portion listed in the Ubuntu Forums Posting Guidelines:  > [T]he Ubuntu Forums is not a homework service. Please do not post your homework assignments expecting someone else to do it for you. ...see all the[ posting guidelines listed here]("http://ubuntuforums.org/showthread.php?t=2158945").

You should learn why and why not to use *setuid* yourself.  Certainly you can ask questions.  But ultimately you will find it more helpful to do the programing yourself.  For information on this see the man pages for developers ```
man 2 setuid
```...You may need to install these man pages. For Ubuntu the package is *man-dev* and you can install it with this command```
sudo apt-get install man-dev
```

---

### Post by Elfy on 2014-11-26
Closed.

> "Well, to be honest..." should have come first. After all that mucking about, this turns out to be a school assignment. 

Indeed.

---

