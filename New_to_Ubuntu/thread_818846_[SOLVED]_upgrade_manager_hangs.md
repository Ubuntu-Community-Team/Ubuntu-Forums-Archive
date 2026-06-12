---
title: "[SOLVED] upgrade manager hangs"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by raymondvillain on 2008-06-04
When I start update manager, it tells me "you can install 66 updates", so I click on install.  After about 30 seconds, update manager just hangs.  I can't close it unless I use system monitor.

I tried opening a terminal window and running
"sudo apt-get remove --purge update-manager update-notifier"
then
"sudo apt-get install update-manager update-notifier"

and then

"sudo apt-get update"

but nothing changed.  Update manager would still hang.  I even re-booted.

Then I tried 
"sudo dpkg --configure -a"

and it tells me  "unable to resolve host SISKIYOU" (name of the computer).

What is to be done?

Thanks in advance

P. S.
In the "changes" tab of update manager it says "Version 2.6.18.24.20" and "*ABI bump to -18"

---

### Post by drs305 on 2008-06-04
> **raymondvillain said:**
> 

What is to be done?

Thanks in advance

```

sudo cp /etc/hosts /etc/hosts.bak
gksudo gedit /etc/hosts

```

There should be a line that looks like this:
```
127.0.1.1  yourcomputername
```

If there isn't, comment whatever that line says and add the above.

---

### Post by raymondvillain on 2008-06-04
Thank you drs305!  Its working as I type this.

Wish I knew how that file got changed.

I have lots to learn!

Thanks again.

---

### Post by JoshuaRL on 2008-06-04
Don't forget to thank him, that was a slick fix.

It's on the bottom right of the post, and it looks like a gold star.

There, I gave you your first one.

:guitar:

---

### Post by drs305 on 2008-06-04
> **raymondvillain said:**
> Thank you drs305!  Its working as I type this.

Wish I knew how that file got changed.

I have lots to learn!

Thanks again.

I'm answering another post on the same subject at this very moment. Something's up ;-)

Please mark this solved.

---

### Post by Shonkin57 on 2008-06-05
:guitar:DRS305 Rocks!:guitar:

Thanks. That helped ever so much. Ubuntu works great. But sometimes us intermediate types make little tweaks that turn everything into a big KA-ThUNK. I put my computer name in, alright, but included the whole thing. Like this:

computername.network.net

Removed the "network.net" and instantly update manager worked just fine.

Again, :KS Thanks! :KS

Jon Trott / Chicago

---

### Post by Gregory on 2008-06-07
This did not work for me. However, I am so new to ubuntu, that I really don't know what I am doing in the terminal.
So in the terminal I typed in:

greg@Jarry:~$ sudo cp /etc/hosts /etc/hosts.bak
sudo: unable to resolve host Jarry
[sudo] password for greg: 
greg@Jarry:~$ sudo cp /etc/hosts /etc/hosts.bak
sudo: unable to resolve host Jarry
greg@Jarry:~$ sudo cp /etc/hosts /etc/hosts.bak gksudo gedit /etc/hosts
sudo: unable to resolve host Jarry
cp: target `/etc/hosts' is not a directory
greg@Jarry:~$ 
greg@Jarry:~$ 

So what am I doing wrong here?

---

### Post by drs305 on 2008-06-07
> **Gregory said:**
> This did not work for me. However, I am so new to ubuntu, that I really don't know what I am doing in the terminal.
So in the terminal I typed in:

greg@Jarry:~$ sudo cp /etc/hosts /etc/hosts.bak
sudo: unable to resolve host Jarry
[sudo] password for greg: 
greg@Jarry:~$ sudo cp /etc/hosts /etc/hosts.bak
sudo: unable to resolve host Jarry
greg@Jarry:~$ sudo cp /etc/hosts /etc/hosts.bak gksudo gedit /etc/hosts
sudo: unable to resolve host Jarry
cp: target `/etc/hosts' is not a directory
greg@Jarry:~$ 
greg@Jarry:~$ 

So what am I doing wrong here?

Gregory,

Go to System, Administration, Network. Click on the Hosts tab, then Unlock. Hopefully if you enter your password it will unlock and let you edit Hosts, but I'm not sure it will. If you get in, you should see two items at the top:

127.0.0.1  localhost  your_computers_name
127.0.1.1  your_computers_name

If the entries exist, there should be no attachments at the end of the computer name in either line.

After the edit, close and see if things are working. You can check to see if the lines took effect by looking at:
```
cat /etc/hosts
```

---

### Post by bennybawlz on 2008-06-13
I ran into the same issue with 8.04. Originally, the first two lines of my hosts file looked like this:

```

127.0.0.1 localhost
127.0.1.1 inspiron #my machine name

```

I think I misunderstood drs305's original post and commented-out the first localhost line, BUT, that fixed the issue for me! Now the Update Manager works.

If I didn't have access to these forums, I probably would have just gone back Gutsy. I know -- it's stupid, but so am I. Problems with the Update Manager right out of the box is not good.

I'm just curious as to

a.) what causes this issue in the first place (the only thing I can think of is that I opted **not** to set-up my network during the ALTERNATE installation)

b.) why commenting-out the **localhost** line (which I guess is supposed to be there?) permits the Update Manager to function normally again in my particular case

I'm just wanting to have answers to the above for my own edification, and I'm sure others are wondering, too. Magic bullet fixes are fun, but I would prefer to know what I just did, so I can do it again in the future and explain to others how to do the same.

Thanks!

Ben

---

### Post by bennybawlz on 2008-06-14
This post sums it up quite nicely, for anyone else who is curious as to WHAT the hosts file is used for.

[https://lists.ubuntu.com/archives/ubuntu-users/2007-August/120739.html](https://lists.ubuntu.com/archives/ubuntu-users/2007-August/120739.html)

However, I'm still not sure that I understand why **removing** the first

```

127.0.0.1 localhost

```

in my hosts file allowed the Update Manager to function properly. This makes no sense whatsoever to me.

Anyone else have a thought or two?

Thanks!

---

### Post by badboyrh on 2008-06-14
So I tried entering in the code drs305 suggested and ended up getting the reply "command not found" for both commands. What should I do?

---

### Post by bennybawlz on 2008-06-14
You **are** using Ubuntu, right? Those commands, sudo and gksudo should definitely work for you, as they are basic, integral binaries to which you should undoubtedly have access.

What happens if you just type the following into your terminal of choice and hit enter (those are both lowercase "L", below):

```

sudo ls -l

```

Does that command produce any output? You should be prompted for your password and then the current directory's contents should be displayed.

If that worked, then the original poster's code should work for you, too. Are you including the necessary spaces, etc.?

---

### Post by badboyrh on 2008-06-16
OK so that worked but now when I go to download the now 85 updates it says I have I receive a notification which reads:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

When I run 'dpkg --configure -a' I receive another message that reads:

dpkg: requested operation requires superuser privilege

What should I do now?

---

### Post by drs305 on 2008-06-16
> **badboyrh said:**
> OK so that worked but now when I go to download the now 85 updates it says I have I receive a notification which reads:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

When I run 'dpkg --configure -a' I receive another message that reads:

dpkg: requested operation requires superuser privilege

What should I do now?

You have to run this command with administrative powers:
```
sudo dpkg --configure -a
```

You will not see your password as you type it - just hit Enter once you have correctly typed it.

---

### Post by badboyrh on 2008-06-25
It worked! Thanks so much for your help!

---

### Post by bennybawlz on 2008-06-25
drs305, do you know why **removing**

```

127.0.0.1 localhost

```

from the first line of my hosts file allowed the Update Manager to function properly in my case?

Are you saying that there should only be **one** entry in the hosts file, and that entry should be

```

127.0.1.1 my-machine-name

```

If that's the case, then why would the Ubuntu installer insert the first line, which prevents the Update Manager from functioning right out-of-the-box?

I'm still curious as to the root cause of this problem. It seems like a pretty serious "bug".

---

### Post by drs305 on 2008-06-25
> **bennybawlz said:**
> drs305, do you know why **removing**

```

127.0.0.1 localhost

```

from the first line of my hosts file allowed the Update Manager to function properly in my case?

Are you saying that there should only be **one** entry in the hosts file, and that entry should be

```

127.0.1.1 my-machine-name

```

If that's the case, then why would the Ubuntu installer insert the first line, which prevents the Update Manager from functioning right out-of-the-box?

I'm still curious as to the root cause of this problem. It seems like a pretty serious "bug".
When you mistakenly removed the first line and it worked it wasn't what I had recommended. I don't know offhand why it worked. I will give it some consideration and if I come up with a reason I'll post it here. Both lines (127.0.0.1 and 127.0.1.1) are normally in the hosts file.

On the other hand, if I had to guess it's because so many instructions that SHOULD work on this forum don't. The law of averages says the reverse must happen at least once in a while...  ;-)

---

### Post by Squishy1 on 2008-06-26
I need some help too.  I am having the same problem, but the solution is not working for me.  I have the required line that was suggested that we add (see below).  When it locks up is right after I click the update button.  It does not ask for my password.

Last night, I saw the note from the person who deleted the localhost line so I gave that a try.  No luck.  I put it back in and then it worked.  Asked for my password and updated properly.  Today, there were some more updates available, so I tried to do the updates and had the same problem as before.  It hangs up.  I can't even close it so I have to restart to clear it.  

Any ideas?  (I am a complete beginner with Linux/Ubuntu, so please type slowly.  :)  )

Thanks!


127.0.0.1 localhost mycomputername
127.0.1.1 mycomputername

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by drs305 on 2008-06-26
On most setups I think the first line normally looks like this:
```

127.0.0.1 localhost
127.0.1.1 mycomputername

```

Oddly, when I just looked at my hosts it has 'localhost' as the only entry after the IP address but that seems a little suspect to me even though I'm not having any problems.

---

### Post by avtolle on 2008-06-26
drs305, my file looks like the one you posted. 

@Squishy1, I don't know why this is happening to you, but your host file should look like the example drs305 posted, so delete your computername from the first line.

---

### Post by Squishy1 on 2008-06-26
> **avtolle said:**
> drs305, my file looks like the one you posted. 

@Squishy1, I don't know why this is happening to you, but your host file should look like the example drs305 posted, so delete your computername from the first line.

Thanks drs305 and avtolle.  I appreciate the help.  I changed that line so that my computer name is not listed after local host then saved it and restarted the computer.  I then tried to update again and it update manager locked up.

Any other ideas?

Thanks again!
-Mike-

---

### Post by drs305 on 2008-06-26
> **Squishy1 said:**
> Any other ideas?
-Mike-

Is this what the first two lines of your hosts file look like now:
```

127.0.0.1 localhost mycomputername
127.0.1.1 mycomputername

```

Can you run these commands:
```

sudo apt-get update
sudo apt-get upgrade

```

By the way, if your Update Manager hangs up again you might be able to close it with:
```

killall update-manager

```

---

### Post by Squishy1 on 2008-06-26
> **drs305 said:**
> Is this what the first two lines of your hosts file look like now:
```

127.0.0.1 localhost mycomputername
127.0.1.1 mycomputername

```

Can you run these commands:
```

sudo apt-get update
sudo apt-get upgrade

```

By the way, if your Update Manager hangs up again you might be able to close it with:
```

killall update-manager

```

Host file says:
127.0.0.1 localhost
127.0.1.1 mycomputername

I did the sudo apt-get update and sudo apt-get upgrade and they ran perfectly.  All updates completed successfully.

Looks like I can use that instead of update manager in the future.  Thanks for your help!!!

I'll save that code for killing the update manager too.

Thanks again for your help.  Not sure what is wrong with update manager, but maybe another update will solve that problem later on.

-Mike-

---

### Post by lrbradford on 2008-06-27
Wow!  Very cool!  I had the same issue with my Update manager, and somehow my 127.0.1.1 had my domain name after my laptop name!  I wonder how that got there??

No matter, update is taking place as I type, so manu kudos!!

---

### Post by ageer1 on 2008-06-29
Same problem. Somehow my 127.0.1.1 had my domain name after my laptop name also. Solved using the code below. I am also very curious as to whether or not all these changes to files are happening due to upgrading to Hardy rather than doing a fresh install (I had 2 other files changed, so far only 2 anyway).

Did all of you with this problem upgrade to Hardy, rather than do a fresh install?


> **drs305 said:**
> ```

sudo cp /etc/hosts /etc/hosts.bak
gksudo gedit /etc/hosts

```

There should be a line that looks like this:
```
127.0.1.1  yourcomputername
```

If there isn't, comment whatever that line says and add the above.

Thanks again drs305,
     Joe

---

### Post by needarealname on 2008-07-04
Just for the record I had the same issue.  got rid of the domain name after my computer name and it started working.  :) My install was off of an ubuntu disk received in the mail.  So I have 223 updates adding up to 241mb. :shock:  I'm going to be downloading for a while. :roll:

---

### Post by W4JKA on 2008-07-10
For those, like me, who don't really want to do code edits, I have an alternate way to edit the HOSTS file:

System/Administration/Network/{unlock}[Wired Connection]*/Hosts

The Hosts file can be edited here to correct the line
from 127.0.1.1 mycomputername.networkname  
to   127.0.1.1 mycomputername

This solved my problem with update manager hang.  However, kudos to those knowledgable folks who had a description of the HOSTS file error, because I would not have known that this was a problem.

*Wired connection in my case

HTH

John

---

### Post by JoshuaRL on 2008-07-11
> **W4JKA said:**
> For those, like me, who don't really want to do code edits, I have an alternate way to edit the HOSTS file:

System/Administration/Network/{unlock}[Wired Connection]*/Hosts

The Hosts file can be edited here to correct the line
from 127.0.1.1 mycomputername.networkname  
to   127.0.1.1 mycomputername

This solved my problem with update manager hang.  However, kudos to those knowledgable folks who had a description of the HOSTS file error, because I would not have known that this was a problem.

*Wired connection in my case

HTH

John

Nice GUI fix for this problem.  That makes it much easier on new users.  Thanks John.

---

