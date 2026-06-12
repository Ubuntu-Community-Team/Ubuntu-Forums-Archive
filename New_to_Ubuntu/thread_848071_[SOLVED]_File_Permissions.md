---
title: "[SOLVED] File Permissions"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by s.fox on 2008-07-03
Hi everyone.

Not totally sure if this is the correct place to post this query, so if its not i am sorry.

Basically i have written a php script that creates a pdf file on my Apache server (runs on Linux).  The php successfully creates the pdf file, however I am having difficulty with  file permissions.  I desperately need to change the file permissions to 755.  It currently creates the file with 644 permissions.

I can execute linux commands from php with no problems but for some reason i can't change the permissions on this particular file.  I am trying to use the code below

```
-sh-3.00$ chmod 777 NEWinvoice.pdf
chmod: changing permissions of `NEWinvoice.pdf': Operation not permitted
-sh-3.00$ 

```

If anybody can help with the linux command problem it would be very much appreciated. 

Thanks to all.

---

### Post by hyper_ch on 2008-07-03
try it with
```

sudo

```

---

### Post by s.fox on 2008-07-03
Thanks for the quick reply.

It didn't work, but i am now getting a new error message.

```
-sh-3.00$ php NEWinvoice.php
Could not open input file: NEWinvoice.php
-sh-3.00$ 

```

Any ideas?  Still looks like a permissions error.

---

### Post by The Cog on 2008-07-03
Think hard before doing that. 755 makes the file executable. Do you really want http requests to create executable files on your server? I see no reason why a PDF file should ever be executable.

---

### Post by hyper_ch on 2008-07-03
```

sudo chmod 0755 file

```

---

### Post by s.fox on 2008-07-03
lol.  i typed in the wrong php file name.  whoops.  sorry, totally my fault


```
-sh-3.00$ php newInvoice.php
Error: Couldn't open PDF file 'NEWinvoice.pdf' for writing (permission denied)-sh-3.00$ 
```


still permissions error though :(

EDIT:  The Cog- I think you are right.  I only need write permissions.  666 would be better.  Thanks

---

### Post by s.fox on 2008-07-03
As a test I just tried to change the file permissions through SSH Secure File Transfer GUI and got an error message pop up.

"Error writing file attributes"

Any ideas?  The folder this file is in has permissions 777.  Thanks for all the support with this problem

---

### Post by The Cog on 2008-07-03
Ah. This is very probably because you (apache) don't have write permission too the directory where the PDF file is being created. Apache probably runs under the user account **nobody**. I don't know what's good practice here - perhaps to have a directory where the script (as nobody) has write permission. But seek the advice of those who are more familiar with administering Apache - this is a security issue.

---

### Post by s.fox on 2008-07-03
Thanks for the advice. 

Is their a way to find out what permissions i have in this directory?

Thanks for everyone's help.

EDIT:  The only reason I ask is that I believe the login I use has admin rights.

---

### Post by ilrudie on 2008-07-03
```
ls -la
``` when you are in the directory will tell you the permissions on the directory.  The current directory in Linux is . and the parent directory ..

For security reasons a directory should never for any reason have 777 permissions.  Also it is ill advised to enable root ssh login.  Since I am assuming you are using Ubuntu and have not changed the default security settings this shouldn't matter because root is disabled.  The Ubuntu security model is based on no user being an "admin" but rather having the right to do administrative tasks using ```
sudo
```Sudo privledges are usually controlled by the sudoers file.  I will decline to mention where it is located because it should never be edited with anything other than ```
sudo visudo
```[COLOR=DarkGreen]Someone with more Ubuntu knowledge please back me up here with the more user friendly way to controll this[/COLOR].  Most likely in order to use sudo you will have to add whatever user is calling the php script to the sudoers file.

---

### Post by s.fox on 2008-07-03
A bit of success :)

I can now change the file permissions from terminal!  

Now I just got to figure out why its not running the command correctly from php.

A big thanks to everyone for the support

---

### Post by s.fox on 2008-07-03
I have got it working from php! :)

It was a little bug in my php script.  

Once again thanks for all the help with the Linux commands

---

