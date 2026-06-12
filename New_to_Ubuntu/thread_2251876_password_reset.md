---
title: "password reset"
date: 2014-11-07
forum: New to Ubuntu
---

### Post by Peter_Davies on 2014-11-07
I have recently installed ubuntu and it worked fine but now Ihave a challenge; either, I have forgotten the password, (unlikely, as it was only five digits) or the machine is choosing to ignore me; I can't authenticate anything. How can I go about resetting the password?

---

### Post by slickymaster on 2014-11-07
Hi Peter_Davies, welcome to the forums.

> **Peter_Davies said:**
> I have recently installed ubuntu and it worked fine but now Ihave a challenge; either, I have forgotten the password, (unlikely, as it was only five digits) or the machine is choosing to ignore me; I can't authenticate anything. How can I go about resetting the password?

To reset your password just follow this intuitive tutorial: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by Impavidus on 2014-11-07
If it appears you had not forgotten the password (and 5 digits is indeed short, I use 12 random characters), what are the exact symptoms of your problem? Refuses to login with error message "incorrect password", login bounces without error message, sudo giving you an error for incorrect password or another error, ...?

---

### Post by Penguin360 on 2014-11-07
> **slickymaster said:**
> Hi Peter_Davies, welcome to the forums.


To reset your password just follow this intuitive tutorial: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

It's a good tutorial, but I noticed he command mentioned in the tutorial that changes file permission is not right. In the post, it says
```
mount -o rw,remount /
```

It should be
```
mount -o mount, rw /
```

---

### Post by claracc on 2014-11-08
I think, the correct command is:

```
mount -o remount, rw /
```

As I have read in the man pages:

```
  Note that the filesystem mount options will remain the  same  as
              those  on  the  original  mount  point, and cannot be changed by
              passing the -o  option  along  with  --bind/--rbind.  The  mount
              options  can be changed by a separate remount command, for exam&#8208;
              ple:

                     mount --bind olddir newdir
                     mount -o remount,ro newdir

```

Is it true?

---

### Post by deadflowr on 2014-11-08
I think as long as the rw and remount options are there it'll work.
(At least I know the command from the the psychocats page works as written)
Don't know about a mount option for mount, though(?)

---

### Post by coldcritter64 on 2014-11-08
> Don't know about a mount option for mount, though(?)                 I just had a look through the huge section of options in the ubuntu online manpages mount man page,with "mount" highlighted (F3 in my browser) couldn't see one there either. I don't think it is one.
[http://manpages.ubuntu.com/manpages/hardy/man8/mount.8.html](http://manpages.ubuntu.com/manpages/hardy/man8/mount.8.html)
I agree, Psychocats is good.

---

### Post by Peter_Davies on 2014-11-08
I used the command as written in the tutorial (mount -o rw,remount) and it worked.

---

### Post by Penguin360 on 2014-11-08
When I ran the command in the tutorial yesterday, I got an error. But I can't remember the exact message, it's something like "remount" is not a valid command or something like that. I will give it another try next week to get the exact error message.

And according to the Ubuntu wiki ([https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)), the command should be: mount -0 remount, rw /

---

### Post by coldcritter64 on 2014-11-08
> **Penguin360 said:**
> ...the command should be: mount -0 remount, rw /

[QUOTE=]...the command should be: mount **-o** remount, rw /[/QUOTE] this is what is on the wiki page you linked. ;) My highlighting of the option switch.

When posting commands use copy/paste, no errors then from typos, cheers.

---

### Post by steeldriver on 2014-11-08
> **Penguin360 said:**
> And according to the Ubuntu wiki ([https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)), the command should be: mount -0 remount, rw /


No, according to that the command is

```

remount -o remount,rw /

```

The important differences are:

1)  the option flag is a lower case o (o for "**option**")

2) the options [FONT=courier new]remount,rw[/FONT] supplied after the -o flag must be separated by commas WITHOUT any spaces

---

### Post by Penguin360 on 2014-11-08
> **coldcritter64 said:**
> this is what is on the wiki page you linked. ;) My highlighting of the option switch.

When posting commands use copy/paste, no errors then from typos, cheers.

LOL, I thought I typed "-o". Thanks for the correction.

I like to type the commands myself because it will help me remember the commands. Next time I will double-check the commands before I post.

P.S. Why "o" is right under "0" on the keyboard? :mad:

---

### Post by Penguin360 on 2014-11-08
> **steeldriver said:**
> No, according to that the command is

```

remount -o remount,rw /

```

The important differences are:

1)  the option flag is a lower case o NOT a zero (o for "**option**")

2) the options [FONT=courier new]remount,rw[/FONT] supplied after the -o flag must be separated by commas WITHOUT any spaces

1) I explained in my last post, I meant to type "-o", but mistyped "-0" instead. I know it should be "o".
2) So the order of remount and rw after "-o" is not important. The important part is there is no space. That explains why I got an error when I tried the command in the tutorial...I must have typed an space after the comma.

---

