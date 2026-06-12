---
title: "STDIO redirect help."
date: 2008-04-22
forum: Programming Talk
---

### Post by kevellis on 2008-04-22
Hi all,

I'm writing a GUI for rsync, ssh and a few other things on Windows.
Basically I'm launching tcsh -i, and redirecting stdout stderr and stdin.

The problem is that when ssh prompts for a password, that doesn't seem to fall under stdout or stderr. I have no idea how to get hold of this string so that I know when to send the password.

Does anyone know how I can merge these prompts with stdout so that I can read them in my program.

For example, these commands successfully redirect stdout and stderr to a file.
ls &> test
zzz &> test

But in this example, the "user@127.0.0.1's password:" prompt is displayed in the terminal and as such, isn't of any use to me.
ssh user@127.0.0.1 &> test


Any ideas would be appreciated.

---

### Post by dwhitney67 on 2008-04-22
I don't fully understand the goal you are trying to reach, but it seems from what you have described, you want to capture the password prompt so that your script will know when to issue a hard-coded password.

If this is the case, the need for this is very questionable.  The point of the password is to prevent unauthorized persons from accessing an account.  If your plan is to place a plain-text password in a script, this go against all the "rules" in place concerning system security.

Why do not consider generating a public-key that can be used to authenticate yourself with the remote system running SSH?  That way you would not need to enter a password.  Here's a site you can look at to get the gist of how to use ssh-keygen:  [http://rcsg-gsir.imsb-dsgi.nrc-cnrc.gc.ca/documents/internet/node31.html](http://rcsg-gsir.imsb-dsgi.nrc-cnrc.gc.ca/documents/internet/node31.html)

Good luck.

---

### Post by kevellis on 2008-04-23
> **dwhitney67 said:**
> I don't fully understand the goal you are trying to reach, but it seems from what you have described, you want to capture the password prompt so that your script will know when to issue a hard-coded password.

Yes, thats right, I was hoping to find someway to make those password prompts appear in the STDOUT so my program could read them.

> **dwhitney67 said:**
> If this is the case, the need for this is very questionable.  The point of the password is to prevent unauthorized persons from accessing an account.  If your plan is to place a plain-text password in a script, this go against all the "rules" in place concerning system security

The program is a GUI to create saved profiles for performing certain sets of actions on single machines or groups of machines. The profiles are all password protected and encrypted.

> **dwhitney67 said:**
> Why do not consider generating a public-key that can be used to authenticate yourself with the remote system running SSH?  That way you would not need to enter a password.  Here's a site you can look at to get the gist of how to use ssh-keygen:  [http://rcsg-gsir.imsb-dsgi.nrc-cnrc.gc.ca/documents/internet/node31.html](http://rcsg-gsir.imsb-dsgi.nrc-cnrc.gc.ca/documents/internet/node31.html)

The problem is that I only control some of the target machines that this will connect to. Also, while I want the user to be able to run the scripts. I don't want them to have access to an SSH password.
The target audience for this program unfortunately are the kind of people who really shouldn't be using the command line.

> **dwhitney67 said:**
> Good luck.

Thanks, I'm gonna need it :)

---

### Post by stroyan on 2008-04-23
Some programs open /dev/tty for sensitive communications like passwords.
You need to provide a pty session to be able to intercept those interactions.
The expect program is a classic example of a way to implement that.
It provides scripted interactions with pattern based parsing and replies.

---

### Post by xtifr on 2008-04-23
ssh goes to great length to prevent you from doing what is a very very bad thing to do.  You should not then turn around and go to great lengths to do that bad thing.

If you want passwordless ssh connections, you should set up public/private key pairs and install them on the appropriate machines.  If you're delivering an app to end users, you may want to embed the key somewhere in the app; that is a far better approach than trying to hack the console drivers.

---

### Post by kevellis on 2008-04-24
Its all good. I figured an easy way to read the prompt from memory :)

Having security forced on you isn't always a useful thing.

---

