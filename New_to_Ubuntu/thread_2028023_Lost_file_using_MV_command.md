---
title: "Lost file using MV command"
date: 2012-07-17
forum: New to Ubuntu
---

### Post by rickygarg on 2012-07-17
Hi - I was trying to move my amazon EC2 Key to a more appropriate location in the /.ssh folder but I omitted the / by mistake. This is the command I ran:

sudo su
mv /home/mohit/Rocio/amazonkey.pem .ssh

Now the file has disappeared from the /home/mohit/Rocio folder and hasn't appeared in the /.ssh folder. Moreover, there is now no file in the /home/mohit/Rocio folder. 

Since this is the EC2 Key - if I dont get this, I have to regenerate my EC2 instance and copy stuff which will be a lot of mess. Any help is appreciated!

Regards

---

### Post by steeldriver on 2012-07-17
Why are you using su to move a file within your home dir?

You have likely just renamed the file /home/mohit/Rocio/amazonkey.pem to .ssh (which will be a hidden file) in the current directory - type

```
ls -al 
```and you should see it - you should be able to just mv it again

```
mv .ssh /home/mohit/Rocio/.ssh/amazonkey.pem
```

You will likely need to correct the ownership / permissions after

---

### Post by BBQdave on 2012-07-17
> **rickygarg said:**
> mv /home/mohit/Rocio/amazonkey.pem .ssh

I believe you moved *amazonkey.pem* to (a newly created) hidden directory *.ssh*,
which is located in /home/mohit/Rocio or the directory you were in when you executed the command.

---

### Post by rickygarg on 2012-07-17
> **steeldriver said:**
> Why are you using su to move a file within your home dir?

You have likely just renamed the file /home/mohit/Rocio/amazonkey.pem to .ssh (which will be a hidden file) in the current directory - type

```
ls -al 
```and you should see it - you should be able to just mv it again

```
mv .ssh /home/mohit/Rocio/.ssh/amazonkey.pem
```  

You will likely need to correct the ownership / permissions after



Thanks! I was trying to move to '/' which is not my home directory? I was able to find the file and have restored it.

> **BBQdave said:**
> I believe you moved *amazonkey.pem* to (a newly created) hidden directory *.ssh*,
which is located in /home/mohit/Rocio or the directory you were in when you executed the command.

A hidden file actually. Got it. Thanks!

---

### Post by Cheesemill on 2012-07-17
You will have moved it to a file called .ssh in roots home folder.
To get it back:
```
sudo mv /root/.ssh /home/mohit/Rocio/.ssh/amazonkey.pem
```
You will also have to change ownership back to yourself:
```
sudo chown mohit:mohit /home/mohit/Rocio/.ssh/amazonkey.pem
```

Moral of the story - don't use sudo unless you have to.

---

