---
title: "Problem logging in"
date: 2015-03-04
forum: New to Ubuntu
---

### Post by soundgeek on 2015-03-04
I enter my correct password & straight away it re-prompts me for the same thing.

If I enter the wrong password, it gives an error message & re-prompts.

I can't log in!

I wonder if I cut the power before it had fully shut down & this has caused the problem?

---

### Post by Al1000 on 2015-03-04
Have you tried booting into recovery mode?

---

### Post by ajgreeny on 2015-03-04
Yes, its possibly the power-cut.  Boot to a live system and try running ```
sudo e2fsck /dev/sdx#
``` where sdx# is your root partition.

Another possible cause is running GUI applications as root using **sudo** instead of **gksu** or **gksudo**.  Unfortunately for many users, gksu has been removed from the default installation and has to be installed afterwards, but it still works OK, even though it is slowly being replaced by pkexec, which at present does not work for most applications without a lot of fiddling.

---

### Post by Bashing-om on 2015-03-04
soundgeek; Hey;

agree with AJ, an improper shutdown always, in my mind, warrants the file system check/repair.

Also pops to mind that you now longer are authorized to access your /home.

At the login screen key combo ctl+alt+F1 should get ya a console.
Can you log into the system here ?
If so what returns:
```

ls -al .Xauthority
ls -al .ICEauthority
ls -al /home

```
all should be owned and grouped to 'you' .

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by soundgeek on 2015-03-04
> **ajgreeny said:**
> Yes, its possibly the power-cut.  Boot to a live system and try running ```
sudo e2fsck /dev/sdx#
``` where sdx# is your root partition.

Another possible cause is running GUI applications as root using **sudo** instead of **gksu** or **gksudo**.  Unfortunately for many users, gksu has been removed from the default installation and has to be installed afterwards, but it still works OK, even though it is slowly being replaced by pkexec, which at present does not work for most applications without a lot of fiddling.

Thanks for responding

After booting a Live system from an SD card,the root partition seems to be called sda7, I tried sudo e2fsck /dev/sda7
I got: 
clean, 231852/57417728 files, 13783019/229668096 blocks

For the query above, yes it will go into recovery mode. I tried a check & I tried a repair, but it seemedto hang in both, apparently doing nothing :(

> **Bashing-om said:**
> soundgeek; Hey;

agree with AJ, an improper shutdown always, in my mind, warrants the file system check/repair.

Also pops to mind that you now longer are authorized to access your /home.

At the login screen key combo ctl+alt+F1 should get ya a console.
Can you log into the system here ?


Thanks Bashing-om. I tried this. It tells me "login incorrect ".

I don't know what state the system is in now. 
I made a backup earlier, when the system was fine. 
I would like to return to it, but I can't get the restore to work:  [http://ubuntuforums.org/showthread.php?t=2266488&highlight=restore+panic](http://ubuntuforums.org/showthread.php?t=2266488&highlight=restore+panic)

I'm going right off Linux :(

I had a flash of inspiration. I remembered I had re-named my original account to "admin" & this is what the GUI login displayed.

I opened a console & used the original name with the password. It logged in! It gave the error:
"mount device (uid: 0) not owned by requested user (uid: 1000)
Reading sb failed; rc = [-1]
mount: Operation not permitted"

---

### Post by ajgreeny on 2015-03-05
It sounds as if you need recovery mode again to change ownership of the /home that is now not yours with ```
chown -R username:username /home/username
```using the username that you are now using, not "admin" that you tried to change it to.
You will not need to run that command with sudo in recovery mode as it runs with root permissions.

---

### Post by soundgeek on 2015-03-05
> **Bashing-om said:**
> soundgeek; Hey;

agree with AJ, an improper shutdown always, in my mind, warrants the file system check/repair.

Also pops to mind that you now longer are authorized to access your /home.

At the login screen key combo ctl+alt+F1 should get ya a console.
Can you log into the system here ?
If so what returns:
```

ls -al .Xauthority
ls -al .ICEauthority
ls -al /home

```
all should be owned and grouped to 'you' .
[INDENT][INDENT]hope this helps
[/INDENT]
[/INDENT]


I tried these. Only /home existed. It yielded:
drwxr-xr-x   5 root root  4096 Feb  7 17:08  .
drwxr-xr-x 23 root root  4096 Feb  7 18:36  ..
drwxr-xr-x   3 root root  4096 Feb  7 17:08 .ecryptfs
dr-x------    2 wxyz wxyz 4096 Feb 7 17:08 wxyz
drwx------   2 root root 16384  Feb  7 17:02 lost+found

Does that make any sense?

---

### Post by dino99 on 2015-03-05
no it does not makes sense.
/home have to be own by the 'user' (aka 'you') not by 'root'
[http://ubuntuforums.org/showthread.php?t=1370806](http://ubuntuforums.org/showthread.php?t=1370806)

---

### Post by Bashing-om on 2015-03-05
soundgeek; 9d9;

Yeah, do not see any user ??? less maybe the user is " wxyz " ?

And to compound the situation, is this an encrypted system ? 
Do I read this right :
> 
drwxr-xr-x 3 root root 4096 Feb 7 17:08 .ecryptfs

I do not have any experience with encryption on 'buntu, thus I reserve judgement.
If this is an encrypted system, and you do not have access to the decryption files, it will be impossible to access the file system.

Is it time to reconsider, and just do a fresh install ? 

There are those times
[INDENT][INDENT][INDENT]the nuclear solution is the better option
[/INDENT][/INDENT][/INDENT]

---

### Post by soundgeek on 2015-03-09
I'm not getting anywhere with this.

A restore utility oughtto be able to close tidily & say what's wrong.

As I don't know what the system state is, I've decided to re-install Linux from scratch. 

This is like Windows! :(

Just found you post 9d9. Thanks for responding.

I couldn't make sense of it either :(

Yes wxyz is my user.

Perhaps Linux is a bit vulnerable to corruption if thepower is chopped on shut-down?

I would hope it would do some integrity checking & repair on re-boot?

Time to go nuclear as you say. I just need to find a reliable way of restoring to a known good state...

---

### Post by Bashing-om on 2015-03-09
soundgeek; Hey;

I do wish I could be of further help; as I have said I have no experience with encrypted volumes.
I am aware there is a means to mount the encrypted file system and then fix it .. I do not have that knowledge readily available.
Encryption is a level of complexity that 'can' be difficult to overcome,

I do encourage you to await others to advise on this situation, prior to taking that nuclear solution. As it stands now in taking that solution you loose all your personal files and data.

Be aware, with encryption there are those times you are left up the creek and there is no paddle - in the event of file system corruption.
> 
Perhaps Linux is a bit vulnerable to corruption if thepower is chopped on shut-down?

Any system is, as many many files are left in an open state; ubuntu is not as prone as most, as it is a journaled file system, it does happen that crucial files are left in a corrupted state.

> 
I would hope it would do some integrity checking & repair on re-boot?

YES, most of the time it does and will catch the error. IF one can boot, one can set to do a file system check on next reboot also.

> 
Time to go nuclear as you say. I just need to find a reliable way of restoring to a known good state...

The most reliable - and quickest - way is to nuke it from orbit, fresh (RE-)install.

There are those times, I just do not want to know

[INDENT][INDENT]not good
[INDENT][INDENT][INDENT]just the way it is
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by soundgeek on 2015-03-10
Many thanks, Bashing-om, for your courteous advice :)

I am not far in from my original install, so I will give it a second try. I am on a learning curve with Linux.

I need to find a reliable way to restore from a backup, but that is probably another topic.

---

### Post by Bashing-om on 2015-03-10
soundgeek; Well ....

We can take a stab at this to mount the file system that contains your personal info .
Let's find the location of those files:
From the liveDVD;
Post back the results of terminal commands :
```

sudo fdisk -lu
sudo parted -l

```

What is scary here is IF your /home is encrypted - I do not know the procedure to access from the liveDVD.
Else, sure we can mount it and work from there to either fix the system or retrieve your data for a grand (RE-)install.
(this time keep it simple - unless you have the need to do otherwise)

[INDENT][INDENT][INDENT]simple is better
[/INDENT][/INDENT][/INDENT]

---

### Post by soundgeek on 2015-03-13
I re-installed & then saw your post!  I opted not to have /home encrypted. For some reason Backups, run from a live disk,  still required my encryption password. But it did run & seems to have backed somthing up.  Might I have just installed the root partition & kept my /home partition intact?  Thanks, I've noted the commands you offer above for future reference.

---

### Post by Bashing-om on 2015-03-13
soundgeek; Welp ;

> **soundgeek said:**
> I re-installed & then saw your post!  I opted not to have /home encrypted. For some reason Backups, run from a live disk,  still required my encryption password. But it did run & seems to have backed somthing up.  Might I have just installed the root partition & kept my /home partition intact?  Thanks, I've noted the commands you offer above for future reference.

There is always that nuclear solution, it works in every case. 'encryption' is a level of complexity I have no experience with. Generally, though, keeping one's data during a (RE-)install requires a separate /home partition. That ability to manage your partitions comes with time and experience with the awareness of how you use your system.

When this thread is concluded;

Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Happy trails to you
[INDENT][INDENT][INDENT]until our next adventure
[/INDENT][/INDENT][/INDENT]

---

