---
title: "Password in single command"
date: 2006-08-29
forum: Programming Talk
---

### Post by rupy on 2006-08-29
Is it possible to specify the password in the shell in one command.

Eg when you typing "sudo thecmd" it prompts for passwd when required, I would like to be able to do it with one command. I need this specifically for the "run command feature".

---

### Post by Anonii on 2006-08-29
> **rupy said:**
> Is it possible to specify the password in the shell in one command.

Eg when you typing "sudo thecmd" it prompts for passwd when required, I would like to be able to do it with one command. I need this specifically for the "run command feature".


I dont think its possible to use:
lets say for example your password is 1234.
**sudo root 1234 apt-get install kde**

And thats for security reasons, because someone could easily steal your password by checking the command logs or by just pressing the "up" button in the terminal.
Well, I have possibly misunderstood, or there is a way, but I highly doubt it.

---

### Post by -Rick- on 2006-08-29
From the man page:
> 
-S  The -S (stdin) option causes sudo to read the password from the
           standard input instead of the terminal device.


For example:
```

echo mysecretpassw | sudo -S ls

```
To execute ls as root.

---

### Post by Anonii on 2006-08-29
Hmm, I didnt know that, and from what I tested it works!
But well, isnt it a bit.... well, unsafe? <:

---

### Post by jimcooncat on 2006-08-29
You might explore the NOPASSWD option of /etc/sudoers. Then you can use sudo without a password, and limit the allowed actions to a single command.

Walking on dangerous ground ...:twisted:

---

### Post by snyper82 on 2006-08-29
How would you create a password for the root account? I need to copy files to a ntfs partition and root is the only one that can do it, it desn't even ask me for a password.  I'm tring to do this in gnome as it would be a huge task in term
I'm also wanting to create accounts with very limited access (for children) I have no idea how to do this...

if it would be easier to reply to my email here it is
[email]snyper82@gmail.com[/email]

---

### Post by kaamos on 2006-08-29
You do not need the root account. Use
```
sudo nautilus
```

---

### Post by skymt on 2006-08-29
If you really want to activate the root account (and know *exactly* what you're doing), it couldn't be easier: sudo passwd

---

### Post by Sam on 2006-08-29
> **Anonii said:**
> Hmm, I didnt know that, and from what I tested it works!
But well, isnt it a bit.... well, unsafe? <:

It is possible to disable console history by making ~/.bash_history not writeable for anyone. However someone may look over your shoulder or scroll the console up.

---

### Post by snyper82 on 2006-08-29
All that seemed to do was show me the root folder, I still can't place the files in my NTFS partition

---

### Post by skymt on 2006-08-29
If Nautilus opened to the root folder, it was running as root. Are sure you have your NTFS drive mounted read/write? Read-only is the default. See [this thread](http://www.ubuntuforums.org/showthread.php?t=217009) (especially the warning at the top) for details.

---

