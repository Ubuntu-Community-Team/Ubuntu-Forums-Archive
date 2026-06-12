---
title: "gFTP problems with SSH2/sFTP transfers"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by Syndacate on 2008-10-20
I've been using gFTP to do my sFTP and FTP work for quite some time now and have been quite satisfied with it.  I need it because sometimes I need to download or upload a very large file which requires me to have the ability to resume transfers, which sFTP protocol can do, and gFTP allows.

Though for this one file, it's reading it as 392MB, and it's much larger.  I've transferred much larger files so I know it's not a cap, I don't think it's corrupted because fugu (a mac sFTP client) reads it as its full size, as does nautilus, as does the disk usage command via ssh.  gFTP is the only thing that doesn't see its full size, and only downloads part of it, which is obviously corrupted.

Anybody know a reason for this (I"m using the latest stable, 2.0.18), or an sftp client with resumable transfers (it's built into the protcol, so I don't think I'm asking too much for a client to have it, but few do :() that I can use?

---

### Post by Peter09 on 2008-10-21
Shot in the dark here: 

Are you transfering a binary file as ASCII? Might be worth making sure that you are transfering as binary in case the protocol sees some sort of eof within the data.

---

### Post by SupaSonic on 2008-10-21
I'm not sure if it supports sFTP, but have a look at FileZilla. It's in the repos.

---

### Post by Syndacate on 2008-10-21
> **Peter09 said:**
> Shot in the dark here: 

Are you transfering a binary file as ASCII? Might be worth making sure that you are transfering as binary in case the protocol sees some sort of eof within the data.

No, I'm not.

My friend suggested that it may be because it's trying to send a number in bytes, and as 32bit it wouldn't fit all of it, so it'd reset as it's overflowing the variable.  I have to agree.  Though now when I do it it's not crashing, so it's downloaded "3.3GB out of 392MB" O.O - so we'll see how it works...might just be a read error type thing.  I'll see if it does it with another 4+ GB file whenever this is done.

---

### Post by Syndacate on 2008-10-22
What my friend said was confirmed.

It sends the size as an int, which when measured in bytes, overflows the storage capacity of a standard int so it resets.  Perhaps it should have been a long.

So anything over 4GB will read as 393MB.

This is not a problem though, as if you use gFTP to download it, it will still download all of it without errors, and resuming transfers does work past the 4GB marker.

The only thing that won't work is the estimated time remaining.

In a 24 hour transfer, it was approx half finished (12 hours), and had an ETA of 26,000 hours while moving at a constant speed the whole time O.O.

So yup, everything is good, thanks, solved.

---

