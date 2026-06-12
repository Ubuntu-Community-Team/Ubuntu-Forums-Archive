---
title: "[SOLVED] Starting Administration Applications"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by jcats on 2008-05-30
Last night , the update icon showed up. So, as per usual, I clicked on it, and it said there was 26 updates. I clicked on "update", and nothing....
At the bottom of the screen, I see "Starting Administration Application". That is there for about 10 seconds, then disappears. When I put the mouse on the update page, the cursor turns into the little circle, which I believe means it working on something.
I let it work itself for about an hour last night, and nothing, Started up this morning and still nothing. Everything else works just fine.
How do I get to sign in as administrator, maybe some sort of work around?
I am using Heron, but all the other updates I've run have all worked well.

Any help would be appreciated;
Thanks in advance
jcats

---

### Post by wolfen69 on 2008-05-30
did you reboot the computer? sometimes something as simple as that can help.

---

### Post by drs305 on 2008-05-30
Added: It became apparent based on new information much later in this thread that the problem was a host problem with an invalid address. It was dealt with starting in post #10. The file was corrected via PM.

See if it's an administrator problem or a server problem. 

If you run the following command, will it allow you to enter the sudo password and continue:
```
sudo ls
```

It that works, then your sudo probably isn't messed up. Then try this to check your server:
synaptic > Settings > Repositories > Ubuntu Software > Download from > Other > Select Best Server

Then try your update again.

---

### Post by jcats on 2008-05-30
Thanks wolfen69, I tried rebooting and full shut down, no difference.

drs305, I followed your ideas. It appears that I can't sign into administration for anything. I went through all the admin. listings and every time, the Starting Administration Application appears , along with what ever I want to sign into, for about 10 seconds , then disappears.
Maybe a larger problem here?

jcats

---

### Post by drs305 on 2008-05-30
It could be that your sudoers file is corrupted.

Check the contents of the sudoers file:
```
sudo cat /etc/sudoers
```
See if it looks like the following:
```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Defaults

# Defaults

Defaults !lecture,tty_tickets,!fqdn

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
 %admin ALL=(ALL) ALL

Defaults:my.user.name timestamp_timeout=240
 

```

If it looks significantly different, that could be the problem. If it looks the same, we can try to delete any .tmp files that might be corrupted.

---

### Post by jcats on 2008-05-30
Thanks drs305
My sudoers file looks the same as your example, except this line

Defaults:my.user.name timestamp_timeout=240

is not in my file.
 I'm assuming that this line tells the computer how long to work on the problem before giving up?
Thanks for your help so far,drs305
jcats

---

### Post by drs305 on 2008-05-30
That line just extends how long before I have to reenter a sudo password. It's not a recommened security procedure ;-)

You might try this next step to remove any corrupted tmp files.
```
sudo find /etc/ | grep sudoers.tm*
```

Look at the list if any files are found. There may be a lot of .tmp.XXX files.
Then delete them with this command:  NOTE: This is a powerful command. Make sure you copy it correctly and don't leave any of it out!

```
sudo find /etc |grep sudoers.tm* | sudo xargs rm -f
```

Try sudo again. If that doesn't work, you may have to reboot. If that doesn't work, report back and let others try to help. If it does work, please mark this thread solved.

---

### Post by jcats on 2008-05-30
OK, a little progress, I think.
I copied "find /etc/ | grep sudoers.tm*" and got

jcats@PurpleUbuntu:~$ find /etc/ | grep sudoers.tm*
find: /etc/firestarter/outbound: Permission denied
find: /etc/firestarter/inbound: Permission denied
find: /etc/cups/ssl: Permission denied
find: /etc/ssl/private: Permission denied

Since I've never gotten Firestarter to work, I figured I'd uninstall it. Went to Add/Remove, marked for uninstall, and then it cursor went into a circle and I could not do anything. I rebooted, and when it started back up, I went into Recovery mode. There, it installed all the updates. So that part is fixed. But I still cannot do anything as Administrator.

So should I be deleting these 4 files? And if I'm looking for .tmp XXX files, am I looking for all .tmp files?

Thanks;
jcats

---

### Post by drs305 on 2008-05-30
> **jcats said:**
> OK, a little progress, I think.
I copied "find /etc/ | grep sudoers.tm*" and got

So should I be deleting these 4 files? And if I'm looking for .tmp XXX files, am I looking for all .tmp files?

Thanks;
jcats

My bad, find must be preceeded by sudo. I'll correct the previous post. 

Please run it again. You would be deleting files named /etc/sudoers.tmp or /etc/sudoers.tmp.XXX

****

Oh shoot - I just realized. You probably can't access or delete these commands if you can't run sudo. 

Reboot in the recovery mode to a prompt. If you run these commands from a prompt in recovery mode you don't need the sudo command. What you are trying to do is delete any sudoers.tmp files that might be kicking around your system.

---

### Post by jcats on 2008-05-30
No problem about the little slip up, I really appreciate your helping me out. But I may have found the problem, but I can't fix it.
Ever since I updated to Heron, when I type in a sudo command, in terminal, I always get 

sudo: unable to resolve host PurpleUbuntu

then right below it, I am asked for the password, I fill it in and everything goes as normal. 
But when I type in  sudo find /etc/ | grep sudoers.tm*  I get returned to 

jcats@PurpleUbuntu:~$ 

Any thoughts?

jcats

oh yea, I upgraded to Heron through the update manager, so I don't have a disc. But I can download and burn one if that is going to fix the problem

---

### Post by drs305 on 2008-05-30
> **jcats said:**
> No problem about the little slip up, I really appreciate your helping me out. But I may have found the problem, but I can't fix it.
Ever since I updated to Heron, when I type in a sudo command, in terminal, I always get 

sudo: unable to resolve host PurpleUbuntu

then right below it, I am asked for the password, I fill it in and everything goes as normal. 



Okay, this part is pretty simple I think. You probably have an entry in your hosts file that is messed up.

Display your hosts file:
```
cat /etc/hosts
```

It will probably look similar to this (and maybe only the first two lines):
```
127.0.0.1 localhost
127.0.1.1 your computer


# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

Added:
Hopefully (I guess) you are going to see an entry for PurpleUbuntu that looks out of place - either a misspelling of your computer, a wrong IP address, etc.

---

### Post by jcats on 2008-05-30
putting in cat/etc/hosts gets:

jcats@PurpleUbuntu:~$ cat /etc/hosts
127.0.0.1 localhost

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
192.168.1.101 Ubuntu
192.168.1.102 BlackBox
192.168.1.103 ubuntulaptop

The 192.168.1.101 entry is what was called PurpleUbuntu in Gutsy, but now it seems is called Ubuntu. I'm not sure how this got changed.
But still my terminal output seems to be the same as your example.

I'm downloading Heron as we speak

jcats

---

### Post by drs305 on 2008-05-30
That is where the problem lies.

Make a backup of hosts before you change things:
```
sudo cp /etc/hosts /etc/hosts-`date +%F`
``` 

If you need 192.168.1.101 and you think it is really supposed to be PurpleUbuntu, change it. Especially if this is your router or some other essential IP address. Otherwise, just put a # symbol at the start of the line.

See if that solves the issue. It is possible that this may affect communication with something down the road, but as it is the Ubuntu line isn't working correctly anyway.

Add this line: 
127.0.0.1 PurpleUbuntu

If that doesn't work, then try changing the first line to this:
127.0.0.1 localhost PurpleUbuntu

---

### Post by jcats on 2008-05-30
Excuse my ignorance, but how do I change  the Ubunu-PupleUbuntu line? Yes, I am behind a router with 3 computers on the router, and th IP address is correct for PurpleUbuntu.

thanks again;
jcats

---

### Post by drs305 on 2008-05-30
> **jcats said:**
> Excuse my ignorance, but how do I change  the Ubunu-PupleUbuntu line? Yes, I am behind a router with 3 computers on the router, and th IP address is correct for PurpleUbuntu.

thanks again;
jcats

I added a save/backup line near the top of the previous post. If you didn't see it:
```
sudo cp /etc/hosts /etc/hosts-`date +%F`
```

Then edit the hosts file:
```
sudo gedit /etc/hosts
```

Change:
192.168.1.101 Ubuntu
To:
192.168.1.101 PurpleUbuntu

I think a standard entry should also be in this file:

127.0.1.1 PurpleUbuntu

Save the file and close. See if that solves things. If you have problems, put a # sign (comment) in front of the last line I asked you to add and save it again.

---

### Post by jcats on 2008-05-30
Ok , while the Ubuntu/Purple Ubuntu may be an issue, I now find that my laptop has the same issue with not being able to do anything as admin. Yet my 3rd computer is ok. All are fully updated.
Computers are fun...:confused:
jcats

---

### Post by drs305 on 2008-05-30
I'm sending send you a PM.

---

### Post by jcats on 2008-05-30
This thread was marked solved, but it was solved through some IM chat between drs305 and myself. 
We were able to solve this issue with some editing of the hosts file. Some how these had become corrupted.
I am grateful for drs305s help. He certainly went out of his way to help
jcats

---

