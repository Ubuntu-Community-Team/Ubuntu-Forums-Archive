---
title: "Ubuntu bash terminal"
date: 2020-12-21
forum: New to Ubuntu
---

### Post by kubasmyk on 2020-12-21
Hi. I started with linux on a raspberry pi. I'm used to the way how the commands and privileges are setup on the pi.
I was wondering if there is a way to make it the same on ubuntu.

For example using sudo commands is a bit "weird" in my opinion. on ubuntu the experience feels more complex as it needs to be?

---

### Post by yancek on 2020-12-21
Never having used a raspberry pi, I'm not sure what you are referring to in the use of commands.  What OS did you have on the raspberri pi?  Many Linux systems use sudo by default but many do not.  What specifically do you mean by "more complex"?

---

### Post by tea for one on 2020-12-21
> **kubasmyk said:**
> Hi. I started with linux on a raspberry pi. I'm used to the way how the commands and privileges are setup on the pi.


If you can elaborate, how are the commands and privileges set up on the pi?

---

### Post by DuckHook on 2020-12-21
Welcome to the forums, kubasmyk.

I use a Pi and have three set up around my house.

For the benefit of those forum members who have already posted trying to help: there is no significant difference between Pi OS (neé Raspbian) and Ubuntu. The file structures and directory trees are practically identical. Ownership/privileges and commands are likewise identical since they adhere to the same defaults and conventions as are extant for all 'nixes.

@OP

*sudo* is a safer alternative to the old Unix tool *su*. By way of a simple explanation I will cite what I feel to be its primary advantage: The principle behind *sudo* is that the user is always operating as an ordinary user and only elevates into superuser status for brief, isolated periods for the purpose of executing one or a handful of commands. Since such privilege escalation also times out after a short period, there is far less danger of the user doing irreparable damage to his installation through forgetfulness. *su* doesn't provide such a backstop. Using *su*, I have messed up my system by making changes in my root account when I thought I was in my ordinary user account. I've never made that mistake using *sudo*. Hence, it is safer for newbies and power users alike.

I recommend that you read the links in my sig: *Linux is Not Windows* and *Resources for Newcomers*. These explain why the separation between ordinary user and super user is so important. Though I don't want to jump to conclusions, given how you phrased your first post, you may still be using bad Windows habits in Linux and doing far too much while logged in as root.

---

### Post by grahammechanical on 2020-12-21
I recently installed Debian out of curiosity. I had to set up an Administrator name and password was well as a User name and password. This means that to do administrator tasks I have to log out as an ordinary user and log in as administrator and then when I am finished I have to log out as administrator and log back in a ordinary user.

Do you know what will happen if I do not log out as administrator? If I walk away from the machine anybody could use the machine with administrator privileges. Thankfully with Debian it is possible to not set an administrator name and password and then sudo will come into play.

I much prefer the sudo method that has become the default in Ubuntu. It is much safer. And in case anybody is wondering. It is possible in Ubuntu to set up a user without sudo privileges. So, I think with Ubuntu we get the best out both methods.

Regards

---

### Post by TheFu on 2020-12-21
> **grahammechanical said:**
> I recently installed Debian out of curiosity. I had to set up an Administrator name and password was well as a User name and password. This means that to do administrator tasks I have to log out as an ordinary user and log in as administrator and then when I am finished I have to log out as administrator and log back in a ordinary user.

You know you can just change to the other userid in a terminal if you know the name and password for that userid, right?
Or you can use sudo to change to the other userid, if you prefer. Just use the available sudo options for that.

All standard Unix stuff.

I have multiple r-pis and haven't noticed any difference in how they handle accounts or sudo between the Pi and amd64 installs.  What does the OP think is different? I'm confused.

---

### Post by ActionParsnip on 2020-12-22
You can even run commands as the other user whilst logged in as any other user, as long as you have the password
```

su - parsnip -c "echo $HOME"

```
will output
```

/home/parsnip

```
Wheras running:
```

echo $HOME

```
will output
```

/home/admin

```

(Assuming you ran the commands as the "admin" user). You don't have to log off and back on. Linux is a true multiuser OS

---

### Post by yancek on 2020-12-22
>  This means that to do administrator tasks I have to log out as an  ordinary user and log in as administrator and then when I am finished I  have to log out as administrator and log back in a ordinary user.

To switch to root in a non-sudo system you simply open a terminal and type su or su -i and proceed to your task, then to switch back to normal user: su username.  No reason to log out unless a user is limited to using a gui.
The link below discusses the pros and cons of sudo, basically a matter of choice and for some, using what they are more familiar with.
 

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by TheFu on 2020-12-22
> **yancek said:**
> To switch to root in a non-sudo system you simply open a terminal and type su or su -i and proceed to your task, then to switch back to normal user: su username.  No reason to log out unless a user is limited to using a gui.

Not really the best way. 

**su - joe**   # prompts for joe's password, if entered correctly, that session will **be** joe with joe's environment, especially HOME
**su joe**   # prompts for joe's password, if entered correctly, that session will only change the effective userid, but retain the prior userid's environment

When done, just **exit** or <cntl>-d once to close the session and go back to the prior userid's environment. I've left out 'root' stuff on purpose.

Basic Unix _su_ stuff usually taught by day 3 of a 5 day Beginning Unix course.  Opening deeper shell levels isn't usually necessary and can easily lead people into confusion.

---

### Post by yancek on 2020-12-23
My earlier post may have been a misunderstanding on my part of the "logout and login" statement which of course is not necessary with either su or sudo .  It's a matter of choice and familiarity in my opinion.  Both have advantages and disadvantages and the  link I posted earlier explains them fairly well.

---

### Post by TheFu on 2020-12-23
> **kubasmyk said:**
>  For example using sudo commands is a bit "weird" in my opinion. on ubuntu the experience feels more complex as it needs to be?

sudo isn't new for Ubuntu or Linux. It has been around and used since at least 1994. I remember using it on SunOS.  There are thousands of fairly normal Unix commands which the point-n-click generation has either forgotten or never learned.  Also, since Unix systems come in wide ranges of preinstalled setups, what 1 person thinks is "expected" usually has very little bearing on what is actually commonly installed.

Someone used to amd64 Ubuntu Desktop would think that amd64 Ubuntu Server was missing all sorts of common commands. It is not, but that depends on perspective. Actually, Ubuntu Server is fairly bloated when compared to other Server distros (except RHEL/CentOS).  Because a Raspberry Pi is a much lower performance device and always has been relative to typical desktops, distros for it usually choose lighter-versions of software and don't usually pre-load common Desktop distro things.  

When I got my first Pi v2 (not-b), 4G SDHC storage was commonly used and 16G was very expensive.  These days, people think nothing of buying a 128G microSD storage for their Pi systems.

Anyway, every distro makes choices for some reason or another. Ubuntu made a bold choice around 2005 that the root account wouldn't be enabled by default and that to access it, sudo would be used.  Other distros made other choices, which is fine.  The entire point of having a different distro is to try new things.  Plus, there is the added complexity of Grandma needing to remember 2+ users and passwords which Ubuntu's choice to use sudo has removed.

I can live with either choice, though I really do prefer the sudo method and set that up on distros which don't have it as central to systems management.  I've been a Unix admin since about 1995, so at this point I'm fairly set in my ways. Some of those decisions were conveyed by my mentors and others were decided after doing something stupid.  If I can keep the "stupid things" to just 1 a week, I figure I'm doing well. ;)  I usually fail at that goal, but I seldom make the same mistake twice.

---

### Post by yetimon_64 on 2020-12-24
> **kubasmyk said:**
> Hi. I started with linux on a raspberry pi. I'm used to the way how the commands and privileges are setup on the pi.
I was wondering if there is a way to make it the same on ubuntu.

For example using sudo commands is a bit "weird" in my opinion. on ubuntu the experience feels more complex as it needs to be?

> **TheFu said:**
> ....  What does the OP think is different? I'm confused.
It may be the file in /etc/sudoers.d on raspbian installs, called "010_pi-nopasswd" (or something like that, I am on my laptop not a pi unit, so I may have not have spelt the file name correctly).

This file has an entry that lets the user issue sudo commands but does NOT require the use of a password for any such command. I regard such set ups as extremely unsafe and as a result it is THE first change I make on any pi installation I intend to use on the internet. I comment out the line inside the file so the installation from then on forces me to use passwords on any administrative tasks.

I think this may be what the OP is referring to in that by default Ubuntu insists on any administrative tasks needing a password as well as just issuing the command with "sudo".

---

### Post by DuckHook on 2020-12-25
> **yetimon_64 said:**
> It may be the file in /etc/sudoers.d on raspbian installs, called "010_pi-nopasswd" (or something like that, I am on my laptop not a pi unit, so I may have not have spelt the file name correctly).

This file has an entry that lets the user issue sudo commands but does NOT require the use of a password for any such command. I regard such set ups as extremely unsafe and as a result it is THE first change I make on any pi installation I intend to use on the internet. I comment out the line inside the file so the installation from then on forces me to use passwords on any administrative tasks.

I think this may be what the OP is referring to in that by default Ubuntu insists on any administrative tasks needing a password as well as just issuing the command with "sudo".
Thanks for the clarification.

If this is indeed what the OP is referring to, then s/he is in need a bargeload of relearning.

@kubasmyk

I hope you are not thinking that nuking challenge/response is a **good** thing; it is *definitely* a **bad** thing. I've already pointed you to the link in my sig: *Linux is Not Windows*

---

