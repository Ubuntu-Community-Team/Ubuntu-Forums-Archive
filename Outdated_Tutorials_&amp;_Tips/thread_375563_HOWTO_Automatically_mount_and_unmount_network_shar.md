---
title: "HOWTO: Automatically mount and unmount network shares"
date: 2007-03-03
forum: Outdated Tutorials &amp; Tips
---

### Post by tweedledee on 2007-03-03
Here is a script you can run in the background that will automatically detect your network shares as they dynamically come and go from the network, and respond accordingly (i.e., mounting them when the networked connection is available, and unmount it when it disappears).  I find this useful for my laptop (which travels) and my desktop (which doesn't, but connects to several other computers that may or may not be on/present at any moment).

You may an alternative version of this approach more helpful for most applications: [http://ubuntuforums.org/showthread.php?t=637258](http://ubuntuforums.org/showthread.php?t=637258)

First requirement: working network connections.  For SAMBA, see either of these links:
[http://doc.gwos.org/index.php/HowToMountsmbfsSharesPermanently](http://doc.gwos.org/index.php/HowToMountsmbfsSharesPermanently)
[http://www.ubuntuforums.org/showthread.php?t=280473](http://www.ubuntuforums.org/showthread.php?t=280473)

NOTE: you must have the connections in your fstab, and you MUST be using "cifs" in place of "smbfs" (I find cifs more reliable anyway - all you need to do is replace instances of "smbfs" with "cifs," they are installed together).  Using smbfs will prevent you from being able to unmount.  If you happen to be working in a pure *nix environment and can use NFS, this will probably work, but I've not tried it.  This script will completely ignore shares not listed in /etc/fstab, meaning it will not interfere with anything else you happen to be doing.  Your fstab line must include the "user" option, and should look something like the following:
```
//IPADDRESS	/media/MOUNT	cifs	auto,user,credentials=/etc/.credentials1,rw,uid=1000,umask=000	0	0
```Also note that if you use a credentials file, as I am here, it must be readable by your account (not just root, as suggested by the above links).
Note that your fields in fstab must be separated by tabs, not spaces.

Second requirement: mount.cifs & umount.cifs must be SUID:
```
sudo chmod +s /sbin/mount.cifs
sudo chmod +s /sbin/umount.cifs
```
Again, if using NFS, there is probably an equivalent requirement, but I've not tested.

Third requirement: copy this script into a file (e.g., "automount"):
```
#!/usr/bin/python

'''
This script assumes that all the network shares in /etc/fstab are accessible
to the current user.  In addition, the shares need to be CIFS (not SMBFS) in
order to correctly allow unmounting by the user in the event the share is
disconnected.  /sbin/mount.cifs & /sbin/umount.cifs must be suid root.

This periodically reads mtab check the status of nework shares,
and unmounts recently inactive shares.  All inactive shares are then issued a
ping.  Responsive systems are then mounted.

Only shares listed in fstab are handled; any others shown by mtab are ignored.
'''

Delay = 120 # number of seconds between checks

import os
import time

def CheckStatus(Share):
    '''Check mtab to determine if a share is mounted.'''
    Mtab = os.popen('grep \'^//\' /etc/mtab', 'r').readlines() # get mounted shares
    for Line in Mtab:
        if Share in Line: return True
    return False
    
Shares = {} # dictionary of IP/name : mountpoint

# Read /etc/fstab to identify permanent shares
fstab = open('/etc/fstab', 'r')
for EachLine in fstab:
    Line = EachLine.strip()
    if Line[:2] == '//': # then reference to share
        Parts = Line.split('\t')
        Path = Parts[0].split('/')
        Shares[Path[2]] = Parts[1]# 3rd piece is name b/c starts with '//'
fstab.close()

# Check status of all shares, every Delay seconds
while True:
    LastTime = time.time() # mark for next time around
    for ShareName, ShareMount in Shares.iteritems():
        if CheckStatus(ShareMount): # this share is mounted, check status
            if os.system('ping -c 1 %s' % (ShareName)) != 0: # ping failed
                os.system('umount -l %s' % (ShareMount)) # unmount
        else: # share is not mounted, check to see if should mount
            if os.system('ping -c 1 %s' % (ShareName)) == 0: # ping responded
                os.system('mount %s' % (ShareMount))
    NumSecs = max(0, Delay - (time.time() - LastTime)) # Delay minus elapsed time
    time.sleep(NumSecs) # sleep until next round of pings

```
Then:
```
chmod 755 automount
sudo cp automount /usr/local/bin
```
You can now add "automount" to your programs that start upon login, and your network shares will dynamically appear and disappear.

It is probably possible to do all this with a shell script, but I'm more comfortable with python for something this sophisticated; feel free to post any simpler alternatives.  Also let me know if you encounter problems or get it working with NFS and I'll update accordingly.

Final note about using cifs vs. smbfs: as per this bug ([https://launchpad.net/ubuntu/+source/sysvinit/+bug/42121](https://launchpad.net/ubuntu/+source/sysvinit/+bug/42121), with duplicate and more information at [https://launchpad.net/ubuntu/+source/sysvinit/+bug/49695)](https://launchpad.net/ubuntu/+source/sysvinit/+bug/49695)), you may encounter a delay in shutting down while unmounting fails.  I see this on some of my computers, but other than an extra 60 seconds in the shutdown, it's not a problem (and if nothing is mounted, it won't happen).  (See post # 7 for the a way around this problem.)  Also, you may encounter a problem (again, really just a delay) with mounting during boot, in which case you can just change your fstab entries to "noauto" (the script will mount the shares as soon as you log in anyway).

---

### Post by JonathanRRogers on 2007-03-06
Thanks; this seems to be working fine for me. BTW, I put "user" and "noauto" in my fstab line for the cifs share in order to use this script. What I can't figure out is why it didn't just work as expected without the "noauto." In that case, the boot process waits for a minute or two for the filesystem to mount, then goes on when it fails, though I haven't found any error messages to  indicate why it failed. I'm guessing it's a name lookup failure or something, but without any error messages, it's impossible to know.

---

### Post by tweedledee on 2007-03-06
> **JonathanRRogers said:**
> Thanks; this seems to be working fine for me. BTW, I put "user" and "noauto" in my fstab line for the cifs share in order to use this script. What I can't figure out is why it didn't just work as expected without the "noauto." In that case, the boot process waits for a minute or two for the filesystem to mount, then goes on when it fails, though I haven't found any error messages to  indicate why it failed. I'm guessing it's a name lookup failure or something, but without any error messages, it's impossible to know.

I'm glad it's working, and thanks for the feedback - "user" is essential for this to work, the "noauto" is possibly related to another bug with the cifs unmounting process during shutdown.  I've updated my original post to include this information.

---

### Post by Abhi Kalyan on 2007-04-09
Hi Tweedledee11
I have some doubts on:
"//IPADDRESS	/media/MOUNT	cifs	auto,user,credentials=/etc/.credentials1,rw,uid=1000,umask=000	0	0"

What does "rw,uid=1000,umask=000	0	0"" stand for?
How does it operate and what are the other options?
Could you please point me to a link where these details might be available?
Thank you
Sincerely Abhi Kalyan.

---

### Post by Abhi Kalyan on 2007-04-09
My problem and how you helped solve it!
Problem:
I had remotely mounted folders with NTFS security installed on them.
The major problem that i was facing was that when i create or modify a file the file permission set them to be owned by the "root", so i could not delete ot alter it from my account.

This was the former lines on the fstab
//server/home /media/remotedrive cifs credentials=/root/.pwfile

After your HOWTO i had changed it to 
//server/home /media/remotedrive cifs credentials=/root/.pwfile,rw,uid=1000,umask=000	0	0

And it did the job!!! "VIOLA"

Now i have access right of th user defined in the password file.

It would be great to know why it did not work initially and why it works now, That why i had asked for some link from where i could get the details regarding the change you had suggested,
Thank you You have helped me a full Load.
Thank you once again
Sincerely Abhi Kalyan

---

### Post by tweedledee on 2007-04-10
> **Abhi Kalyan said:**
> Hi Tweedledee11
I have some doubts on:
"//IPADDRESS	/media/MOUNT	cifs	auto,user,credentials=/etc/.credentials1,rw,uid=1000,umask=000	0	0"

What does "rw,uid=1000,umask=000	0	0"" stand for?
How does it operate and what are the other options?
Could you please point me to a link where these details might be available?
Thank you
Sincerely Abhi Kalyan.

A very brief explanation can be found here: [http://www.humbug.org.au/talks/fstab/fstab_structure.html](http://www.humbug.org.au/talks/fstab/fstab_structure.html).  A more detailed one (that answers the "other options" question) is here: [http://en.wikipedia.org/wiki/Fstab](http://en.wikipedia.org/wiki/Fstab).  An even shorter explanation:
rw means the read/write access to mount the drive with (rw means full read & write).
uid is the user ID, that should be yours (1000 is the uid of the 1st user in Ubuntu).
umask refers to the permissions to create files with ("man umask" in a terminal for more details), 000 basically means no effect.
The two 0 mean do not flag the system for backing up and don't check the drive with fsck (neither of which you probably want for a network drive).

At a guess, I'd say it was probably the UID that solved your "root" problem, as it meant the drive was mounted as "you" and not "root."

---

### Post by tweedledee on 2007-04-28
I've found a solution to the log delay in shutting down with CIFS (and NFS and others) shares mounted.  Create a file ~/.xsession and add the following lines (on the off-chance you already have such a file, anything before the "gnome-session" line will run before gnome starts; anything after it will run when the user logs out):
```
gnome-session
killall automount
umount -l /SHARE
```
Replacing automount with whatever name you actually gave the script, and adding as many umount lines as necessary for each share (in my case, I have 5 that are /media/computername).  Updated original post to reflect this.

---

### Post by Darwin Award Winner on 2007-05-02
This looks like an interesting script. I am interested in extending it to other network filesystems, specifically sshfs, but I need to know one thing: does this script rely on shares that lose their connection to automatically unmount? Because sshfs does not necessarily do that.

Also, a suggestion: using df to get the list of mounted shares is kind of roundabout, and since df allows certain filesystem types to be filtered out of its output, using it is not guaranteed to work. It's probably better just to grep through /etc/mtab directly, something like this:
```
grep '^//' /etc/mtab
```
The output of that should be all lines in mtab that begin with two slashes.

So you could rewrite your CheckStatus function something like this:
```
def CheckStatus():
    Returns = [] 
    Pipe = os.popen('grep "^//" /etc/mtab', 'r') # issue grep
    for EachLine in Pipe.readlines():
        ... # no more need to filter lines in here
    Pipe.close() 
    return Returns
```

---

### Post by tweedledee on 2007-05-02
> **Darwin Award Winner said:**
> This looks like an interesting script. I am interested in extending it to other network filesystems, specifically sshfs, but I need to know one thing: does this script rely on shares that lose their connection to automatically unmount? Because sshfs does not necessarily do that.

Right now it decides whether or not to unmount based solely on the response to a ping.  I/you could add another criterea if that's not quite what you have in mind.

> **Darwin Award Winner said:**
> Also, a suggestion: using df to get the list of mounted shares is kind of roundabout, and since df allows certain filesystem types to be filtered out of its output, using it is not guaranteed to work. It's probably better just to grep through /etc/mtab directly, something like this:
```
grep '^//' /etc/mtab
```

You are entirely correct.  In addition, df has the disadvantage of being slow, so it's possible for the status to change between checks.  I've been meaning to clean this up for a while, your message proved the kick I need.  The considerably simpler and somewhat more reliable version is now up.

---

### Post by Darwin Award Winner on 2007-05-02
Your fstab-parsing code has a few errors. Most notably, parts of an fstab entry can be separated by any whitespace, not just tabs. Try this:
```

for EachLine in fstab: 
    Line = EachLine.strip()
    if Line.startswith('//'): # then reference to share 
        Parts = Line[1:].split() 
        Shares[Parts[0]] = Parts[1]

```

Also, I've developed so preliminary UNTESTED code to support sshfs shares as well. First change the grep command in CheckStatus:
```
Mtab = os.popen('grep \'^//\' /etc/mtab', 'r').readlines() # get mounted shares
```
Then, add a stanza in the fstab-parsing loop to parse sshfs entries:
```

import re

for EachLine in fstab: 
    Line = EachLine.strip()
    if Line.startswith('//'): # then reference to share 
        Parts = Line[1:].split() 
        Shares[Parts[0]] = Parts[1]
    elif Line.startswith('sshfs#'):
        Parts = Line.split() 
        hostmatch = re.search('[#@]([A-Za-z0-9\-.]+):', Parts[0])
        if not hostmatch:
            continue # skip bad entries
        host = hostmatch.group(0)
        Shares[host] = Parts[1]

```
Since this code is untested, I make no guarantees, except that I guarantee that it will NOT work unless you have set up passwordless ssh logins.

---

### Post by tweedledee on 2007-05-03
> **Darwin Award Winner said:**
> Your fstab-parsing code has a few errors. Most notably, parts of an fstab entry can be separated by any whitespace, not just tabs.

Yes; however, it is possible for the 1st, 2nd, and 4th fields to contain a space (as \40, which python translates when it reads it).  With lots of effort, one could still correctly identify the name and mount point, but it would add significant code.  Or one could assume no spaces except between fields.  Or, as I did, one could assume that since Ubuntu formats it with tabs and most people will follow that, chances are the whitespace is a tab.  I wanted to allow for spaces in the fields because it is targeted toward CIFS mounts, and Windows users might well have spaces somewhere.  I may post a second version that implements your approach; in the meantime I have made an explicit note on the need for tabs.

> **Darwin Award Winner said:**
> Also, I've developed so preliminary UNTESTED code to support sshfs shares as well.

I don't have a simple means for testing this; if it seems to be working for you over the course of a few days, I can incorporate it.

---

### Post by Darwin Award Winner on 2007-05-03
How do you put spaces in fstab fields? You actually put a literal '\40' in the file?

As for my needs, I have actually implemented my own solution using scripts in the /etc/network/if-(up|down).d directories. It mounts all shares when the network comes up, and unmounts them when the network goes down. The assumption in that approach is, of course, that my own network connection is the only one that ever goes up or down. This script could certainly be added to my setup, but the connections to my shares are stable enough that it would never have occasion to mount or unmount anything.

So, if anyone else wants to test it, they can.

---

### Post by tweedledee on 2007-05-03
> **Darwin Award Winner said:**
> How do you put spaces in fstab fields? You actually put a literal '\40' in the file?

Yes.  At least, according to a couple of resources I've found.  I've never gotten around to actually testing it directly, though I have a case where it would make sense.

> **Darwin Award Winner said:**
> As for my needs, I have actually implemented my own solution using scripts in the /etc/network/if-(up|down).d directories. It mounts all shares when the network comes up, and unmounts them when the network goes down. The assumption in that approach is, of course, that my own network connection is the only one that ever goes up or down. This script could certainly be added to my setup, but the connections to my shares are stable enough that it would never have occasion to mount or unmount anything.

So, if anyone else wants to test it, they can.

Sounds reasonable for your case - in mine, everything is dynamic.

---

### Post by Darwin Award Winner on 2007-05-04
Good news, my HOWTO explaining my solution has just been approved. The two solutions are complimentary. This script can maintain the status of the shares as their respective servers become available or unavailable, and my script and immediately mount and unmount them when your own network comes up or down (for example, if your laptop has just connected to a wireless network). Useful if you are so impatient that you can't wait up to 120 seconds for the next iteration of this script to come around, or if you want to set this script's idle time much higher but still have instant access when you first connect. My script is [here]("http://ubuntuforums.org/showthread.php?t=430312"). The crux of the automation is a pair of scripts in the /etc/network/if-(up|down).d directories that get executed whenever the network comes up or down.

The simplest adaptation of this script to that system would be to create the following files and make them executable:

/etc/network/if-up.d/netfs-automount-start
```
#!/bin/sh

# start the network automount script in the background
automount &

```

/etc/network/if-down.d/netfs-automount-stop
```
#!/bin/sh

# stop the autmount script
killall automount

# unmount all cifs shares
umount -a -l -t cifs

# unmount all sshfs shares (only if you're using that feature)
umount -l `grep '^sshfs#' /etc/mtab | awk '{print $2}'`

```

That setup should ensure that the automount script is only running while your computer is connected to the network, and that any shares that are available when the network first comes up are mounted ASAP.

---

### Post by tweedledee on 2007-05-04
> **Darwin Award Winner said:**
> Good news, my HOWTO explaining my solution has just been approved. The two solutions are complimentary. This script can maintain the status of the shares as their respective servers become available or unavailable, and my script and immediately mount and unmount them when your own network comes up or down (for example, if your laptop has just connected to a wireless network). Useful if you are so impatient that you can't wait up to 120 seconds for the next iteration of this script to come around, or if you want to set this script's idle time much higher but still have instant access when you first connect. My script is [here]("http://ubuntuforums.org/showthread.php?t=430312"). The crux of the automation is a pair of scripts in the /etc/network/if-(up|down).d directories that get executed whenever the network comes up or down.

I agree - very complimentary.  In fact, if I'm feeling creative, I may take your approach and modify it so that it only activates automount on my laptop when I'm actually using a particular network device, as I don't really need to be running automount unless I'm on the right network.  In my case, that means using wireless with a static IP, so I can uniquely identify it.

---

### Post by tweedledee on 2007-12-17
I have posted a completely new version/approach, which has many advantages and is simpler to set up.  The new post is [http://ubuntuforums.org/showthread.php?t=637258](http://ubuntuforums.org/showthread.php?t=637258), but I've left this one because the new one doesn't completely replace the utility of this one.

---

