---
title: "Catch-all email account with dovecot-postfix"
date: 2009-05-11
forum: Outdated Tutorials &amp; Tips
---

### Post by curvedinfinity on 2009-05-11
Most of the info out there for setting up postfix with a catch-all account uses the virtual-user set of features of postfix. Dovecot uses actual unix users, so it makes no sense to turn on the virtual user system and re-enter all of dovecot's users.

Here's how you set up postfix to have a catch-all email account that is savy along with dovecot. The account will receive all of the mail that is sent to an address which doesn't exist. In other words, it will collect a TON of spam, but it is sometimes important for business to be very thorough and receive the occasional mistyped email address.

So, assuming dovecot-postfix is installed, first make the user which will catch the mail:

```

sudo useradd -d /home/catchall -m catchall
sudo passwd catchall
#enter a password

```

Then add these lines to /etc/postfix/main.cf:

```

local_recipient_maps =
luser_relay = catchall

```

Now restart postfix:

```

sudo /etc/init.d/postfix restart

```

...and you should be golden. To check the inbox, just use imap or pop, entering catchall/yourpassword. Good luck!

---

### Post by jpeddicord on 2009-05-12
I've made a quick edit to the 'sudo passwd catchall' line, otherwise you would not be setting the password for the catchall user. Anyway, approved, and thank you for your tutorial contribution!

---

### Post by kameelperdza on 2009-07-02
[http://ubuntuforums.org/showthread.php?p=7550893#post7550893](http://ubuntuforums.org/showthread.php?p=7550893#post7550893)
 
I have virtual domain users, what now? I cant use the local user relay cos they are not local. any other advice?

---

### Post by curvedinfinity on 2009-08-03
I don't think you are using dovecot-postfix, because that package sets up postfix to use actual unix users, not virtual users.

---

### Post by ooshlablu on 2009-08-22
for virtual domains you can do this:

```
nano /etc/postfix/virtual
```

****Note: The above file does not exist, you will be creating it. You will be letting postfix know that it does exist by running the postmap command, and adding it to the config****


in that file, put this:

```
@virtualdomain.com      emailaddress
```

once that file is saved run this command:

```
postmap /etc/postfix/virtual
```

then add this to the bottom of /etc/postfix/main.cf:

```
virtual_alias_maps = hash:/etc/postfix/virtual
```

and you should be golden

---

