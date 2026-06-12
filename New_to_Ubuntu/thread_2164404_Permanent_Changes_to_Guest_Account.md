---
title: "Permanent Changes to Guest Account"
date: 2013-07-31
forum: New to Ubuntu
---

### Post by Kanefa on 2013-07-31
I have been setting up a computer lab in which I planned to have the students use the guest account.  However, I am not able to make any permanent changes to the guest account.

Here are three changes I would like to make to the guest account.

1. I've installed Wine 1.6 and then installed Microsoft Office 2007.  However, this installs per user, so I have not been able to install it to the guest account.

2. Change the broken Chromium link on the panel.  Chromium will not work on our donated low RAM systems.  I need to delete the Chromium link and add a Firefox link.

[Resolved] 3. I need to add read-only movie lessons that the students can access, but not delete.

Help would be greatly appreciated, thanks!

---

### Post by zombifier25 on 2013-07-31
I'm lazy, so I'll just copy and paste my old post regarding making changes to the guest account:

> **zombifier25 said:**
> 
It's slightly complicated. Basically, when a new user is created. the content of /etc/skel is copied into the user's home folder (which contains all the personal configs, etc.) But when a new guest user is created, the content of /etc/guest-session/skel is copied into the guest user's home folder. So what you want to do is to add stuffs into /etc/guest-session/skel.

tl;dr Create the directory first: 
```
sudo mkdir -p /etc/guest-session
sudo cp -r /etc/skel /etc/guest-session
```
Then create a new regular user, "example" for example. Log in that user and customize whatever you want. When done, log out and log back in your admin account, and run this command:
```
sudo cp -r /home/example/* /etc/guest-session/skel
```
to make sure the guest receive the customizations. When done, delete the user "example".

---

### Post by TheFu on 2013-07-31
The "guest" account is created and destroyed every time someone chooses to login and logout from the system.  If you look on the system from a different account, you'll see this happen.  /home/guest will be created/removed.  This is a key aspect of the way that guest works. 

There are lots of possible solutions.

I suppose you could 
* find the guest account creation script and modify it
* setup guest001, ...  guest999 accounts, carefully set the permissions so the user could not modify their own HOME, and hope for the best ... via testing everything.
* create a post-guest create script and is run by each user's .bashrc account to leverage hardlinks for nearly instant ~/.wine/ settings and any other pre-installed guest user things.

I think the last one would be the most efficient and easiest.  It reads as if you don't understand file/directory permissions too well yet, so learning about that would be a good first step. [https://www.linux.com/learn/tutorials/309527-understanding-linux-file-permissions](https://www.linux.com/learn/tutorials/309527-understanding-linux-file-permissions) is one tutorial, but I found lots with google.

With careful use of file permissions (user AND groups), WINE_HOME settings , I think you can make access to a central wine install and trivially accessible movie lessons easily.

If you aren't tied to guest users, perhaps allowing students to retain their own accounts with highly restrictive storage would be a better option - OTOH, only you can decide what the requirements truly are.

Definitely look into using softlinks and hardlinks to make setting up the accounts at login blazingly fast!

Interesting problem.  I suppose that you've considered LTSP already?

---

### Post by Kanefa on 2013-08-01
I tried zombifier25's suggestion.  I installed MS Office, fixed the Chromium link, and added some dummy files in a few spots.  The files were the only thing that "stuck."  That's a start though.  Issue #3 is resolved and still looking for a solution to #1 and #2.  

TheFu, I am not following "create a post-guest create script and is run by each user's .bashrc account to leverage hardlinks for nearly instant ~/.wine/settings and any other pre-installed guest user things."  Is it really this involved to simply update a broken shortcut in the guest account?

Thanks, Again!

---

### Post by TheFu on 2013-08-01
> **Kanefa said:**
> I tried zombifier25's suggestion.  I installed MS Office, fixed the Chromium link, and added some dummy files in a few spots.  The files were the only thing that "stuck."  That's a start though.  Issue #3 is resolved and still looking for a solution to #1 and #2.  

TheFu, I am not following "create a post-guest create script and is run by each user's .bashrc account to leverage hardlinks for nearly instant ~/.wine/settings and any other pre-installed guest user things."  Is it really this involved to simply update a broken shortcut in the guest account?

Thanks, Again!

Sorry that I was less than clear in my response. I have that issue sometimes.

I was trying to make a unified, working, configuration that could be instantaneously copied into every guest $HOME. It had next to nothing to do with fixing a chromium link on a desktop.  I threw out a bunch of "buzzwords" in that sentence to suggest a course of action - using hardlinks to recursively copy files is very easy and nearly instantaneous regardless of the total sizes involved. I'd assumed your MS-Office install was of a non-trivial size.

~/.wine/ is the default location for WINE program settings and Windows program files.  You can put those anywhere, not even under the HOME directory, but I thought suggesting that might be too complex.

Basically, I suggested that you configure a complete mirror of the ~/guest/ area, make a 100% copy somewhere else, then use scripted hardlinking to recreate it in a non-destructive way as a student logs in.

Perhaps there is a better way to accomplish the same tasks?

---

### Post by Kanefa on 2013-08-02
I have found little to no information on this topic.  I imagine it is possible as TheFu says, but you would have to dig deep without much gain (installing one programming and removing one broken shortcut).  Now I am wondering if this would accomplish the same task differently.  I could create a regular user and configuring it.  Then is it possible to have it wiped clean (similar to the guest account) when logging out? 

Or maybe someone has a suggestion.  To summarize I need to make a couple configurations to an account and then would like the account to be like new each time the user logs in.

---

