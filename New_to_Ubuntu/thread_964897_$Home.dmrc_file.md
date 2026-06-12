---
title: "$Home/.dmrc file"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by susanpenter on 2008-10-31
Since upgrading to Ubuntu 8.10, I did it at the last stage of the trail version yesterday morning, when I log in I get this message:

"User's $Home/.dmrc file is being ignored.  This prevents the default session and language from being saved.  File should be owned by user and have 644 permissions.  User's home directory must be owned by user and not writable by other users."

Once I ok this it continues to be more or less fine in terms of actual performance but I would like to rectify this if anyone knows how.

Many thanks,

Susan

---

### Post by Pconfig on 2008-10-31
sudo chmod 644 ~/.dmrc
and
sudo chown YOUR_USERNAME ~/.dmrc

Edit:

Hmm on second thought you might need to change permissions of your whole home directory?

Could you post the output of 

ls -l /home/

---

### Post by Marshal0505 on 2008-10-31
to take ownership of the file

```
sudo chown username username /home/your username/.dmrc
```

to change permissions

```
sudo chmod 644 /home/your username/.dmrc
```

---

### Post by Marshal0505 on 2008-10-31
> **Pconfig said:**
> sudo chmod 644 ~/.dmrc
and
sudo chown YOUR_USERNAME ~/.dmrc

Edit:

Hmm on second thought you might need to change permissions of your whole home directory?

Could you post the output of 

ls -l /home/

If that's the case, this would be displayed by an additional error and would be solved by doing 

```
chmod 700 /home/username/
```

---

### Post by philinux on 2008-10-31
I had this last week after messing things up myself.

These two commands need to be done in this order. No need for sudo.

```
chmod 700 /home/username/

chmod 644 /home/username/.dmrc

```

---

### Post by Marshal0505 on 2008-10-31
for some reason i have to chmod 700 /home/marshal on a daily basis. Haven't figured out what's causing it.
And indeed the 'sudo' was bad form. My apologies ;)

---

### Post by philinux on 2008-10-31
> **Marshal0505 said:**
> for some reason i have to chmod 700 /home/marshal on a daily basis. Haven't figured out what's causing it.
;)

That's odd. Have a look in /var/log/auth.log for clues.

---

### Post by susanpenter on 2008-10-31
> **philinux said:**
> I had this last week after messing things up myself.

These two commands need to be done in this order. No need for sudo.

```
chmod 700 /home/username/

chmod 644 /home/username/.dmrc

```
Ok I have followed your instructions in the terminal it seemed to just accept them and mve to the next line, no need for my password as is sometimes needed.  So for now do I assume that has resolved it?

If it says it again after a reboot I'll get back to you thanks.

---

### Post by 5circles on 2008-11-06
Thanks to this thread and other messages in the forum, I was able to get rid of this error message:).

But I have a couple of follow up questions:

Why did this error message come up in the first place?  I think that it happened for me when I added an additional hard drive.  I'm not absolutely certain, because I've been doing a ton of changes to different machines, and hadn't rebooted this one for a while.

How can I find the text of the error message?  I've grepped in /var/log, but it doesn't appear to be there.  One of the threads had captured a picture, so I'm guessing that others are having the same kind of trouble.

Thanks
Mike

---

