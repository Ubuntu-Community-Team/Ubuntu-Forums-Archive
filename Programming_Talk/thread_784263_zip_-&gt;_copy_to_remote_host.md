---
title: "zip -&gt; copy to remote host"
date: 2008-05-06
forum: Programming Talk
---

### Post by defunkt on 2008-05-06
hey all, 

i ahve some programming backgroud (microsoft VB), but not with any unix/linux system.  i've been slowly learning ubuntu for some time but just recently dove in. i really like it, it runs better than i thought an OS could. i realize that mr gates was depriving us users...  but we wont go there.

i have a server at a remote location that will be hosting/accumulating files.  i would like to filter the files by filetype and then shoot them over to my house every night around midnight'ish.  

the idea is that once the files have been transfered i can remove the excess data from the original location and free up room as i dont have much space on the server.

1.  if files can be transferred through SSH i could do it that way, but from what i read, this is not possible. i would have to tunnel another protocol inside SSH.

2.  ftp transaction.  im pretty good with FTP and have already set up VSftp.  ive locked it down to its home directory and have files be exported there.  

3. my other thought was VPN, though i do not have much experience with this.  im willing to dive in if people think that this will be much easier.


i think zipping them will be easy (for me), but i think the transfer will be much harder (in my experience).  

i would like to keep the ftp transaction secure if at all possible. 

if any of you think im going the wrong direction on how to go about doing this, please, by all means, point me the right way.  

> 
# Check to make sure the command looks right.
find /home/****/files/ -iname '*.dat'


i stole that quote from another thread, i modified it to filter , but how do i take that selection and zip it.

any thoughts is very much appreciated as i love the ubuntu community.  this is the only time ive found a problem not already answered.

Thanks in advance

---

### Post by prshah on 2008-05-06
> **defunkt said:**
> hey all, 

1.  if files can be transferred through SSH i could do it that way, but from what i read, this is not possible. i would have to tunnel another protocol inside SSH.



scp (Secure Copy) uses ssh to transfer files, and it's really easy! ```
man scp
``` will give you all the info you need, and if you can't follow it, just a post here with a little more info about your config on both sides (os, type of connection, etc), and anyone be happy to give examples.

It's secure, and you can enable on-the-fly compression for the transfer if you like.

You must have (open) ssh server running on your (home) target system.

---

### Post by defunkt on 2008-05-06
open ssh huh, so putty wont do?  

edit, nvm..  got it

---

### Post by prshah on 2008-05-06
> **defunkt said:**
> open ssh huh, so putty wont do?  
edit, nvm..  got it

Oops, looks like you're running Windows on your home machine; then you have to find an SSH server for Win32.

---

### Post by defunkt on 2008-05-06
that was my next move...  ive been reading up on a couple.  im looking at moving my larger hard drives over to a linux box for a file server, but thats another project...  until then i need to back it up here.  

but scp is make life 100 times better...  thanks

---

