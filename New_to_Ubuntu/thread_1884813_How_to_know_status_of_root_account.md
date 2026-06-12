---
title: "How to know status of root account ?"
date: 2011-11-22
forum: New to Ubuntu
---

### Post by ask_ on 2011-11-22
I wish to know if root account is disabled or not on my system. is there a command to know it? 

In the community help pages , [https://help.ubuntu.com/community/RootSudo#Re-disabling_your_root_account](https://help.ubuntu.com/community/RootSudo#Re-disabling_your_root_account) ,
info is given on enabling or disabling it. I wish to know whether it is enabled or not, is there a way to do so.

Also if it is disabled , what happens if you use below command to disable it again , will it stay disabled?

```
sudo passwd -dl root

```
In above command , what do we have to type in terminal ? I mean do we have to type "passwd" as it is or "passwd" stands for some password which we would like to set


I am a beginner, hence want to keep root(or superuser) account locked , just as it is in default install of Ubuntu. But I fear, I may have used gksu command once or twice instead of gksudo . Will it have enabled root?

---

### Post by mikewhatever on 2011-11-22
No, neither gksu nor gksudo enables root login.

---

### Post by Rubi1200 on 2011-11-22
Also worth reading this for more information:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by ask_ on 2011-11-22
thanks,could you also explain how following command works?

```
sudo passwd -dl root

```
In above command , what do we have to type in terminal ? I mean do we have to type "passwd" as it is or "passwd" stands for some password which we would like to set.
Also if it is disabled , what happens if you use above command to disable it again , will it stay disabled?
Because to stay safe, I executed that command once.

---

### Post by audiomick on 2011-11-22
Have a look at the man page. In a terminal
```
man passwd
```

There is a man page for every command, at least theoretically. ;) Sometimes they are a bit cryptic, but the one for passwd looks understandable enough.

Passwd is the command, not a place holder. Read the man page; it is explained there.

---

### Post by lisati on 2011-11-22
Have a look at the web page that Rubi1200 suggested: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

"sudo" is a command which means "switch user and do". In this context it lets your admin account temporarily have super-user privileges.

As Audiomick says, "passwd" is also a command, not a place holder.

---

### Post by ask_ on 2011-11-22
> **lisati said:**
> Have a look at the web page that Rubi1200 suggested: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

"sudo" is a command which means "switch user and do". In this context it lets your admin account temporarily have super-user privileges.

As Audiomick says, "passwd" is also a command, not a place holder.

Thanks everyone. I think my doubts are cleared.
Actually I had read the RootSudo page which you just showed , but was having trouble understanding the command which I posted. But after you have told what exactly passwd is, my doubts are cleared.

So tell me if I have understood things properly, just as a final confirmation :-


Initially after default Ubuntu install, Root account is locked (for safety of beginners to Linux such as me in this case).

Once we execute the command , 
```
sudo passwd root

```

A password is set for root. And hence root is unlocked ? (am I right?)

And if we execute the command ,
```
sudo passwd -dl root

```

The password for root is deleted.And hence root is again disabled.

We need to use sudo because adding passwords/removing passwords , for any user (super-user included) needs super user privileges , and sudo gives us that!


Actually, I had executed the delete root password command once,because I thought that my root user was unlocked ,because I had foolishly used gksu once instead of gksudo.

---

### Post by ask_ on 2011-11-22
I think I found a way to check status of root account. 
```
sudo passwd -S root
```

The above command gave the following output
```
root L 11/10/2011 0 99999 7 -1
```

The 'L' signifies that password is locked, right ?
So does this mean by root account is disabled just as it should be by default ?

I read on the help pages that it is essential that root account be disabled, and
I am a bit confused,hence asked the same question.:oops:

---

### Post by CharlesA on 2011-11-22
From the man page: man passwd

```
      -S, --status
           Display account status information. The status information consists
           of 7 fields. The first field is the users login name. The second
           field indicates if the user account has a locked password (L), has
           no password (NP), or has a usable password (P). The third field
           gives the date of the last password change. The next four fields
           are the minimum age, maximum age, warning period, and inactivity
           period for the password. These ages are expressed in days.

```

EDIT: The root account is disabled in Ubuntu since we use sudo to run things as root. You can enable it, but you do so at your own risk. There are ways of getting a root shell without enabled the root account itself.

---

### Post by matt_symes on 2011-11-22
Hi

The L means locked.

Kind regards

---

### Post by ask_ on 2011-11-22
Thanks, for the help everyone on this thread.
I will now mark this thread as solved.

It was a sensitive issue, hence, was worried.:D

I am quite new to Ubuntu/Linux. But the forums,manpages,community documentation are great learning tools.

---

