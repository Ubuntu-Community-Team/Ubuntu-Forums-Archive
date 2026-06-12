---
title: "Ubuntu user number"
date: 2022-02-19
forum: New to Ubuntu
---

### Post by psychohermit on 2022-02-19
Greetings folks,

How do I find my ubuntu user number?

Thanks,
--glenn

---

### Post by TheFu on 2022-02-19
```
$ id -u
```
Or do you seek something else?
Most installs will return 1000.
Live Boot environments 999.
As more and more userids are added to an installation, the count increases by 1. If someone decides to manually make a userid a different number, say 1100, then the next in line will be 1101.

---

### Post by psychohermit on 2022-02-19
Thanks, but I was referring to the ubuntu forum user number.

Thanks,
--glenn

---

### Post by KBar on 2022-02-19
At the top of a page, it should say "Welcome, psychohermit". Hover over the link and you'll see your member ID.

---

### Post by QIII on 2022-02-19
Are you talking about the user number some people have in their signatures?

---

### Post by psychohermit on 2022-02-20
Yes, that's the user number I'm looking for.

Thanks,
--glenn

---

### Post by TheFu on 2022-02-20
> **psychohermit said:**
> Thanks, but I was referring to the ubuntu forum user number.

Thanks,
--glenn

Your forum number here is: 2162391  I saw it in links to your profile.

---

### Post by psychohermit on 2022-02-20
Thank you, --glenn

---

### Post by MAFoElffen on 2022-02-20
What you described was the Ubuntu Forum's Member Account Number... Which is different than the Ubuntu User Number (used to be). Look at this old thread: [https://ubuntuforums.org/showthread.php?t=1606904](https://ubuntuforums.org/showthread.php?t=1606904) from October 26th, 2010.

Over a decade ago, there was a web page ( [http://ubuntucounter.geekosophical.net/](http://ubuntucounter.geekosophical.net/) ) to go to where you had to register for an "Ubuntu Number" and they gave you a number. It was different than the Ubuntu Forums account number. (It actually had nothing to do with the Ubuntu Forum.)  Just as you used to go to either counter.li.org or to linuxcounter.org/main.html (yes, there were two different ones) to register as a "Linux User" (and be counted), and they used to give you a Linux User number(s). I don't know how long ago, but both those websites no longer exist. They were gone before 2014 ( [https://ubuntuforums.org/showthread.php?t=2207473](https://ubuntuforums.org/showthread.php?t=2207473) ) Both were originally meant to be able to get a rough  to estimate of how many users were out there... But a lot of people didn't even know the counter existed or what they were for, so I don't know that the numbers were accurate. LOL. (I think there were many more uncounted users at that time!!!) They were originally intended to show your support of Linux and Ubuntu.

How that count is estimated now, is by the internet and auditing website hosts in the world, where Ubuntu Linux  web host's lead the numbers in that (kind of) count.

If you look at that thread which was almost 12 years ago, about the same time I registered here, all those Forum Members have Ubuntu User #'s that do not match their Ubuntu Forum's Member Account #'s. (As mine doesn't match.) You can see with Post #1, with the person who started the thread, his registered Linux User # is 163544. If you mouse_over his  UserName, his Ubuntu Forum's Account # is 37737... But even though he asked others to post their Ubuntu User number, he mentioned that he didn't have one, as he never bothered. LOL. 

I remember it still existed in 2012 when I was voted in as an Ubuntu Member, because the Forum Admin Counsel recommended that we included it on our Ubuntu Wiki Page. 

So what is your "Ubuntu #?" If you didn't get it before that webpage went away around 8 years ago, then you don't have one and can't get one now. Sorry. What is your Ubuntu Forum Account Number? (That is the one associated with your account.)

Though I have learned that there are many ways to show our support of Linux and Ubuntu. One is to give back to the community here. It just takes time to help users in need, help edit pages and content, whatever you can help with... And with me, not just to help New Users, but to try to help the Community, Ubuntu as a distribution, and to Linux overall.

---

### Post by ActionParsnip on 2022-02-20
If you want your Ubuntu user I'd as a number
```

grep $USER /etc/passwd | cut -d":" -f 4

```

---

### Post by MAFoElffen on 2022-02-20
@ActionParsnip

LOL. (Sorry) As said before in this thread by the OP, the system's Linux UID of a User is not what he was asking about... But as related to what you posted and UID:
```

id-u <UserName>
# For example for the UID of the logged in User 
id -u $USER
## OR
echo ${UID}
# Because the logged in User is set as a shell variable

```
100's of ways to do the same thing. Some ways simpler. I know this about UID's is all offtrack, and I think TheFu already covered UID, but UID's and GID's for Linux follow this rule of thumb: The first one created during (or immediately after an install for some installations) start with the number "1000." During the install process, the user is UID 999, because the first user has not been created yet...

But, alas, that was not what the OP was asking about...

---

### Post by TheFu on 2022-02-20
> **ActionParsnip said:**
> If you want your Ubuntu user I'd as a number
```

grep $USER /etc/passwd | cut -d":" -f 4

```

May want to use the **getent passwd $USER** command rather than grepping in a specific file. This will allow the more general solution where an LDAP DB is being used, while also supporting the old text passwd db too.  Someday, all our accounts will be in LDAP DBs, even on our home LANs with the accounts shared across all our systems, using 1 authentication DB across all systems.

---

### Post by ActionParsnip on 2022-02-20
> **MAFoElffen said:**
> @ActionParsnip

LOL. (Sorry) As said before in this thread by the OP, the system's Linux UID of a User is not what he was asking about... But as related to what you posted and UID:
```

id-u <UserName>
# For example for the UID of the logged in User 
id -u $USER
## OR
echo ${UID}
# Because the logged in User is set as a shell variable

```
100's of ways to do the same thing. Some ways simpler. I know this about UID's is all offtrack, and I think TheFu already covered UID, but UID's and GID's for Linux follow this rule of thumb: The first one created during (or immediately after an install for some installations) start with the number "1000." During the install process, the user is UID 999, because the first user has not been created yet...

But, alas, that was not what the OP was asking about...

Oh definitely. Was just adding it incase someone found this and wanted that information too. Covers the bases

---

### Post by nginmu on 2022-02-27
Thanks psychohermit for asking the question and all esp. MAFoElffen for the answers, it was something I'd been curious about too.

---

