---
title: "Installing perl Net:::SSH w/o root access"
date: 2008-11-04
forum: Programming Talk
---

### Post by gmoreno on 2008-11-04
Guys,

I'm trying to work on getting some ssh perl scripts to work on a box.  I don't have root access to it.  Not sure if I can get the admin give me the root password or install net::ssh

So is there a why I can install net::ssh through cspan instead.  I am very new to perl.

Eventually all I need to do is to have a cron job run to do autobackups:

Ssh to a remote box, run some commands and scp files back to to myself on this Ubuntu box with ubuntu server edition.

I'd appreciate any input.

TIA

---

### Post by slavik on 2008-11-04
wait ... what???

why do you need net::ssh on the server?

where is the cron job running from and where are the backups supposed to happen?

are you backing up your $HOME on some server?

---

### Post by gmoreno on 2008-11-05
> why do you need net::ssh on the server?
Trying to run perl net::ssh scripts

> where is the cron job running from and where are the backups supposed to happen?
I'm hoping to be able to set a cron job as a user of the server.  

> are you backing up your $HOME on some server?
Tying to backup a UNIX OSE system back to the ubuntu server using scp.


Hope this clarifies things.

---

### Post by gmoreno on 2008-11-07
Anyone?

---

### Post by slavik on 2008-11-07
I am still not understanding what you are trying to accomplish. :(

Could you try to re-phrase the supposed work flow of what you want to accomplish?

---

### Post by slavik on 2008-11-07
I am still not understanding what you are trying to accomplish. :(

Could you try to re-phrase the supposed work flow of what you want to accomplish?

---

