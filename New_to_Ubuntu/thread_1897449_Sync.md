---
title: "Sync"
date: 2011-12-19
forum: New to Ubuntu
---

### Post by StrangerSa on 2011-12-19
Hi all, hope your festive season is going well,

mine sucks I am still at work HA HA

Can anyone suggest the best sync tool for Ubuntu please. From server to portable hard disk

thanks

---

### Post by seawolf167 on 2011-12-19
Best is a matter of opinion, mine is personally *rsync*

```
man rsync
```You can keep an entire directory tree mirrored via a command like the following

```
rsync -ru --delete-before /path/to/source /path/to/destination
```

add the *-v* switch for verbose output

---

### Post by Lars Noodén on 2011-12-19
That would be [rsync](http://manpages.ubuntu.com/manpages/oneiric/en/man1/rsync.1.html).  If you want a graphical front end for it then you have [grsync](http://manpages.ubuntu.com/manpages/oneiric/en/man1/grsync.1.html).

```

rsync -avH /source/dir/ /dest/dir/

```

See also:
[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

---

### Post by StrangerSa on 2011-12-19
Thanks guys

---

### Post by seawolf167 on 2011-12-19
If you  have everything solved, please mark this thread as such under Thread Tools -> Solved.

---

### Post by StrangerSa on 2011-12-19
Downloaded Grsync from the Ubuntu software center.

It can't see my server, what have I done wrong ?

Please feel free to treat me like the dummy I am and keep it simple please

---

### Post by StrangerSa on 2011-12-19
Will do Seawolf, but not solved yet thanks

---

### Post by seawolf167 on 2011-12-19
Are you physically plugging in the external hard drive to your server, or is the external hard drive plugged into your computer and the server is a separate machine?

---

### Post by StrangerSa on 2011-12-20
> **seawolf167 said:**
> Are you physically plugging in the external hard drive to your server, or is the external hard drive plugged into your computer and the server is a separate machine?

The external is pugged into the PC and the server is a separate machine

I want to be able to sync what is on the server to the external without copying onto the PC

thanks, sorry being in SA our time frames are not synced either :D

---

### Post by Lars Noodén on 2011-12-20
If the server is mounted locally then you can still use one of the above formulas for syncing.  If it is not, then you can use [font=Courier New]rsync[/font] over SSH.  

```

rsync -avH StrangerSa@example.org:/source/dir/ /destination/dir

```

---

### Post by StrangerSa on 2011-12-20
Thanks Lars but you have lost me totally. I am still at the stage where i need the graphic front end

I have Grsync if you can tell me how to use that.

---

### Post by Lars Noodén on 2011-12-20
Start grsync, then enter the source and the destination in the appropriate boxes.  Check any additional settings you might want.  Then click on the gears in the upper right hand corner to make it sync.

---

### Post by StrangerSa on 2012-01-03
> **Lars Noodén said:**
> Start grsync, then enter the source and the destination in the appropriate boxes.  Check any additional settings you might want.  Then click on the gears in the upper right hand corner to make it sync.

Thanks Lars

but I cannot see the serer that is the source

---

### Post by Lars Noodén on 2012-01-03
> **StrangerSa said:**
> but I cannot see the serer that is the source

You won't be able to browse your way over to it.  You have to know the address and account in advance and enter them both.

---

### Post by zandman on 2012-01-03
Seems you are trying to connect to your server from the machine to which the backup-drive is connected.
I'm making a backup of the complete home-dir of a sever on a regular basis to a removable hd which is connected to my workstation. Situation seems pretty similar to what you are trying to achieve.

Here's how i do that using rsync:
[LIST=1]
[*]Connect removable drive and make sure it's mounted. Mine is called "backup-all"and has a subdir on it for every machine that i want to backup.
[*]Open "terminal" and make an ssh-connection to the server *ssh -X user@ip-adress*, enter password when prompted to finalize the login
[*]enter the rsync-command  *sudo rsync -arvzR -e ssh /home/* user_at_workstation@ip-adress_of_workstation:/media/backup-all/Backup_server/* You will encounter a password-prompt once for the sudo-command and then another one to connect to your workstation from the server.
[/LIST]And since i'm lazy all i have to do to start another backup is to scroll up through the command line history. Just make sure the workstation still has the same ip-adress and run.

---

### Post by StrangerSa on 2012-01-06
Thanks , will give it a try

---

