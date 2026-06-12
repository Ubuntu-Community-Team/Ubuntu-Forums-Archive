---
title: "Server migration with all services from Ubuntu Linux 10.04.3 to 14.04"
date: 2014-10-13
forum: New to Ubuntu
---

### Post by Manirul_Islam on 2014-10-13
Urgent! Urgent!

Hello Experts,

I am newbie in Linux. During Server migration with all services from Ubuntu Linux 10.04.3 to 14.04, I have placed a command like this on old server:

sudo rsync -azvv -e ssh / [EMAIL="root@hostname.com"]root@hostname.com[/EMAIL]:/

But things got creepy. New Server became unreachable over the network. It's pingable with previous IP but SSH or webmin module of that server is not available. Webmin says, Module proc not found. Also it's showing OS version not 14.04 :( 

[ATTACH=CONFIG]257161[/ATTACH]

Please forgive my immaturity :( and suggest me what is to be done to get my new server up and running.

Thanks in advance

Manir

---

### Post by TheFu on 2014-10-13
> **Manirul_Islam said:**
> Urgent! Urgent!
How much does this pay? urgent = paid to me.

> **Manirul_Islam said:**
> Hello Experts,
I am newbie in Linux. During Server migration with all services from Ubuntu Linux 10.04.3 to 14.04, I have placed a command like this on old server:
sudo rsync -azvv -e ssh / [EMAIL="root@hostname.com"]root@hostname.com[/EMAIL]:/ 

Not a good way to migrate running systems, even if they are identical.  You can boot off different media and do rsync on two uninterested drives, but something like fsarchive or ddrescue or even gparted 'clone' would probably be better.

Or .... the way that I migrate systems is: [http://blog.jdpfu.com/2013/12/11/how-to-migrate-debian-ubuntu-systems-and-data-overview](http://blog.jdpfu.com/2013/12/11/how-to-migrate-debian-ubuntu-systems-and-data-overview)

> **Manirul_Islam said:**
> But things got creepy. New Server became unreachable over the network. It's pingable with previous IP but SSH or webmin module of that server is not available. Webmin says, Module proc not found. Also it's showing OS version not 14.04 :(   

[ATTACH=CONFIG]257161[/ATTACH]
I've never used webmin. Suspect the rsync failed in the middle somewhere, but can't tell from the data provided.

> **Manirul_Islam said:**
> Please forgive my immaturity :( and suggest me what is to be done to get my new server up and running.

I'd start over using one of the saner methods listed above.  It is very important that the source system NOT be active during the copy. Use an alternate boot method so the source OS isn't active.  Also - if the HDDs sector size is different, be very careful and pre-create any partitions on the new media to ensure sector alignment.  There is an option for fdisk (not the defaults) - or use parted/gparted - which just do the right thing.

I completely understand the stress.  Most of my systems were migrated to newer OSes over the summer, but a few still remain. Fortunately for me, most are VMs and fairly trivial to test the migration in a lab before ever touching any production instances.  Highly recommended to test this stuff before touching production.

---

### Post by nerdtron on 2014-10-13
> **Manirul_Islam said:**
> 

sudo rsync -azvv -e ssh / [EMAIL="root@hostname.com"]root@hostname.com[/EMAIL]:/



Not good...not good at all. Are you the administrator of this server? Are you aware what would this command do? Why would you copy the / partition of a server to another server?

Seems to me somebody did not prepared (or tested first) for the migration. Just entering commands like this can destroy a server and did you even bother to test it first?

Server migration is a complicated process as each server has their own unique services. You should first list and study them all and prepare a plan to migrate each server. A direct copy of / partition won't work (this is not windows).

As for the new server, I think it would be better to reinstall it, and restart the whole migration process.
List you services here and if you are having problems migrating each we can give you some advice. (And don't experiment on any production server please).

---

### Post by Manirul_Islam on 2014-10-16
> **TheFu said:**
> 


 [http://blog.jdpfu.com/2013/12/11/how-to-migrate-debian-ubuntu-systems-and-data-overview](http://blog.jdpfu.com/2013/12/11/how-to-migrate-debian-ubuntu-systems-and-data-overview)




Thanks a million for the link. It wasn't a production server. As I am Newbie in this: I've tested immaturely. The time of testing was very late night. maybe that's why I've lost my common sense. :D

---

### Post by Manirul_Islam on 2014-10-16
> **nerdtron said:**
> Not good...not good at all. Are you the administrator of this server? Are you aware what would this command do? Why would you copy the / partition of a server to another server?

Yeah. But after placing that command, I realised. :(


> **nerdtron said:**
> As for the new server, I think it would be better to reinstall it, and restart the whole migration process.
List you services here and if you are having problems migrating each we can give you some advice. (And don't experiment on any production server please).

Thanks a lot. I am trying to reinstall. After that I will start testing again. And I'll share the result with you guys. Please stay tuned. :)

---

### Post by koenn on 2014-10-16
```
sudo rsync -azvv -e ssh / root@hostname.com:/
```

I've done this (couple of years ago)  to see if it would work, and it does. Even between live systems. They where VM's so practically identical, and that probably helped.

The key is to make rsync exclude certain directories, namely the ones that are not real files.  
/proc is one of them, other candidates are all the ones that the 'mount' command shows as not pointing to  disks or partitions : de tempfs mounts etc.

and of course you end up with duplicate names and ip adresses on the network, so that 'll need fixing afterwards as well.

So it's not impossible, but there probably are better ways.

---

### Post by TheFu on 2014-10-16
> **koenn said:**
> ```
sudo rsync -azvv -e ssh / root@hostname.com:/
```

I've done this (couple of years ago)  to see if it would work, and it does. Even between live systems. They where VM's so practically identical, and that probably helped.

Boot sector? That would be missing, definitely.
BTW - **-e ssh** is redundant these days. ssh is the default for long-time-now - like 10 yrs.

---

### Post by koenn on 2014-10-17
> **TheFu said:**
> Boot sector? That would be missing, definitely..
I was cloning running systems : the rync source would be / at a model system,  the target / on another machine. What I did was install a minimal system on the target machine, enough to execute rsync on it. So it had a bootsector, and I wasn't interested in anything below filesystem level anyway.  The point of the exercise was more of a "can i replicate a configuration" rather than "can I setup an OS from scratch by way of rsync" 

The idea I was playing with at the time was finding  mechanisms to deploy identical systems, or to  set a system to a known state, by overwriting any changes by rsyncing a known good system, or to deploy config changes by applying them to 1 "model" system and rsync that system to a number of targets, that sort of stuff.

> BTW - **-e ssh** is redundant these days. ssh is the default for long-time-now - like 10 yrs.
the actual command i used was something like ```

rsync 	-rpoglHtuq  \
		--exclude=/proc --exclude=/tmp --exclude=/sys  --exclude=/home --exclude=/root \
		remotemodel:/   /

```

---

