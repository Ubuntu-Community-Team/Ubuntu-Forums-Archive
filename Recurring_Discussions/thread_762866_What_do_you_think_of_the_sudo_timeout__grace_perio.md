---
title: "What do you think of the sudo timeout / grace period?"
date: 2008-04-22
forum: Recurring Discussions
---

### Post by aysiu on 2008-04-22
You may not be aware of this behavior, but when you perform an administrative function (for example, installing a new program), your authentication gets cached for a bit (15 minutes, I believe... maybe 5 minutes), and you won't be prompted again for your password if you perform a second or third administrative function within that grace period (otherwise known as the sudo timeout).

I'm not sure what to think of this.

On the one hand, it seems rather insecure. After all, isn't the whole point of having password authentication that it provides a layer of security? Would it be possible for something to piggyback your authentication and launch some kind of malware without your permission? And, if not, why have password authentication at all? Why not keep it permanently cached?

On the other hand, assuming it isn't the optimal security implementation, would getting rid of the timeout just frustrate new users even more and bring us more "I just want to log in as root all the time! This is *my* computer, after all" threads? In other words, would tightening that security just lead to more people getting rid of the security measure altogether?

What do you think?

Like the sudo timeout? Don't like it and want to get rid of it? Don't like it but think the alternative would be worse? Don't really care? Didn't even notice there was one?

I'm really curious as to what people's opinions on this are.

Thanks in advance for your two cents or pence (or whatever a pittance is in your currency).

---

### Post by will1911a1 on 2008-04-22
It always made me nervous. I'm much more comfortable using su to log in as root and then exiting out after I'm done.

---

### Post by Mazza558 on 2008-04-22
It can be summed up in 3 words:

A Necessary Evil.

It's a compromise between security and usability.

---

### Post by insane_alien on 2008-04-22
i think its fine. nobody but me can sudo and i only very rarely use it at that.

if you use sudo all the time and you are not a sysadmin of a large network then your using your computer wrong.

---

### Post by FuturePilot on 2008-04-22
I feel the same as aysiu. I'm not sure. In a way it's a little more convenient. You can perform multiple administrative tasks in that period and only have to enter your password once. But I've often wondered myself if it would be possible for some code to execute itself as root within that time period. But I think if we were to get rid of it and require the password every time you perform an administrative task, we would start seeing comments like "it's Vista UAC, Aaahhh!"

---

### Post by jken146 on 2008-04-22
I usually change the timeout to zero (in case anyone's interested, you add **,timestamp_timeout=0** to the **Defaults** line in /etc/sudoers) but that is more to protect me from my own typos and silly mistakes than from outside threats.

This issue is really a little moot for those who know the command **sudo -i**

---

### Post by Xzallion on 2008-04-22
I really like it.  I can't really see any easy way for it to be exploited (I can see ways, but I think I would catch them.)  It really makes it easy on a fresh install to get what you need, and do a few commands without being slowed down. 

I think it should be configurable and be allowed to be disabled for users that it bothers, but for me I hope it stays.  Its done nothing but make my (K)Ubuntu experience more enjoyable.

---

### Post by Xzallion on 2008-04-22
Sorry, for some reason it double posted.

---

### Post by munkyeetr on 2008-04-22
I always disable the grace period. I don't mind plugging in a password.

---

### Post by phrostbyte on 2008-04-22
I completely support it. I don't want Ubuntu to turn into the Vista UAC mess.

Besides it's easily configurable (via config files). In the future though I think Ubuntu should have an Administration applet that lets you configure many different security aspects for yourself in a user friendly manner. Some systems need the better security, and eliminating the grace period and interactive login makes sense (for instance in corporate networks).

---

### Post by aaaantoine on 2008-04-22
You know, I could have sworn that 7.10 was supposed to have an icon appear in the Notification Area when sudo was engaged, and that you could disengage it at any time via that icon.

I think that maybe the grace period is a necessary evil, but should be more visible.  Perhaps an idea similar to the one above can be applied so that a security-conscious user can cut the grace period short when he just has one thing to do as an admin.  Or, either alternatively or in addition to this idea, have a check box that one can check when filling in their password in gksudo to "Remember password for 15 minutes".

As for the CLI version of this idea, maybe sudo should request a password every time.  If someone wants to have a grace period, they can start by typing...

```
$ sudo --grace 15m
[sudo] password for user:
sudo can be used password free for the next 15 minutes.
$ sudo apt-get update
0% working...

```

And if they want to cut it off...

```
$ sudo --end-grace
[sudo] grace period ended by user.
$ sudo apt-get update
[sudo] password for user:

```

---

### Post by jakupl on 2008-04-22
THANKYOU jken146 :) The grace period has been giving me chills for as long as iv'e used ubuntu.

I find it incredibly annoying!

---

### Post by Joeb454 on 2008-04-22
> **Xzallion said:**
> Sorry, for some reason it double posted.

Since the forum upgrade I've been having issues like that :(

---

### Post by Barrucadu on 2008-04-22
The timeout is a necessary evil, however I tend to use su more than sudo, simply because I seem to do administrative things in batches (install X, Y, Z. configure X, Y, Z, and so on and so forth), and so typing sudo every time can get annoying.

---

### Post by elamericano on 2008-04-22
Unless you've added !tty_tickets to sudoers, any unauthenticated sudo command in the grace period would have to be invoked from the same terminal instance.

So, just close your terminal or type sudo -K when you're done.

---

### Post by Superkoop on 2008-04-22
I find it very handy, since generally when I need to go sudo, I do quite a few things. 

If viruses or malware ever start up in Ubuntu and this comes to be a problem, it will be an easy change to a config file.
So until this comes to be a problem, no reason to change it.

---

### Post by wilsonmuse on 2008-04-22
> **elamericano said:**
> Unless you've added !tty_tickets to sudoers, any unauthenticated sudo command in the grace period would have to be invoked from the same terminal instance.

So, just close your terminal or type sudo -K when you're done.

Thank you elemericano for the clarification!

---

### Post by qazwsx on 2008-04-22
5 minutes is good. 

But I think immediate timeout is better for graphical apps. I don't like {kde,gk}sudo and very much prefer traditional {kde,gk}su. I was very dissapointed to see kdesudo feature in Kubuntu 7.10.

---

### Post by jakupl on 2008-05-01
well.. since my last post, i made a clean install of hardy, now i can't seem to change the timeout period in the sudoers file... how do I do that in hardy? is there even any change?

this is my current sudoers file

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset                 

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```

---

### Post by cardinals_fan on 2008-05-01
A Very Bad Day ©

---

### Post by imronak on 2008-05-01
I think we can do one thing.

Example, My school Webauth, in which you can login with three options for cookies,
1. 1 hour, any address
2. 1 hour, fixed address
3. 10 hour, fixed address

So depending on the purpose you want you can choose. If I log into a school mahcine for small work, I choose 2, and if i am at home then choose 3.
 

So, we can slo make a similar implementation in ubuntu sudo timeout as
1. Only once.
2. 1 hour.
3. 4 hours.

and 1 be default, so the newbie users are not at risk. If you know what you are dong then you can safely choose 3.



What my point with current implementation is this,

I am a hacker. I first ask you to do something legit. You provide root priviledges. the sudo timeout is activated. Then I do some backend activity without your knowing, and since the root priviliges are ON, there is no one to stop me.

How many of you feel, this scheme sounds good?

---

### Post by SunnyRabbiera on 2008-05-01
I approve of the grace period, it allows you to do administrative tasks but at the same time limits how long it can be done.
though it should be lowered, from 15 minutes to 5..
and no we dont need the vista method :D

---

### Post by RazorEdge on 2008-05-01
The grace period is very useful. There's a reason I disabled UAC in Vista.

---

### Post by zetetic on 2008-05-01
I always change the timeout to zero, and that behavior should be the default.

---

### Post by cardinals_fan on 2008-05-01
> **Barrucadu said:**
> The timeout is a necessary evil, however I tend to use su more than sudo, simply because I seem to do administrative things in batches (install X, Y, Z. configure X, Y, Z, and so on and so forth), and so typing sudo every time can get annoying.
+1

---

### Post by agim on 2008-05-01
Don't like it at all. I'd rather just use my password everytime. I understand why they did it (convenience) and maybe as a new user it would have bee aggravating, but at this point, give me the security.

---

### Post by RazorEdge on 2008-05-02
> **zetetic said:**
> I always change the timeout to zero, and that behavior should be the default.
It's a balance between security and convenience. Ubuntu is about working the balance after all. Maybe there should be a preferences option somewhere that's easily accessible to change the timeout (if there isn't already, don't know).

---

### Post by blithen on 2008-05-02
> **Mazza558 said:**
> It can be summed up in 3 words:

A Necessary Evil.

It's a compromise between security and usability.

Damn..exactly what I was thinking but better put. :P

---

