---
title: "filezilla - transfer freezes without any result"
date: 2014-08-25
forum: New to Ubuntu
---

### Post by marchello_lippi2 on 2014-08-25
Hi all, 

my transfer in filezilla just freezes without any result. I can log in to remote ftp, browse directories, create directory, delete files, but I can't transwer files from my local dir to remote dir. 
I can still use filezilla under windows from my workplace (via proxy), but can't do it at home (lubuntu 14.04 LTS, no proxy). 
Any suggestions?

---

### Post by mike194 on 2014-08-28
Good day!

Can you describe a bit more of what you're trying to do?  Are you trying to copy a file from one machine to another?  The file transfer start and then stop?

How are you connecting to the machine?  FTP?  SSH/FTP?

Thanks!

---

### Post by marchello_lippi2 on 2014-08-28
> **mike194 said:**
> Good day!

Can you describe a bit more of what you're trying to do?  Are you trying to copy a file from one machine to another?  The file transfer start and then stop?

How are you connecting to the machine?  FTP?  SSH/FTP?

Thanks!

Ok, I transfer files from local machine to remote ftp in order to display my files at web site.
Everything worked fine few weeks ago when I worked at home under Ubuntu 12.04 LTS (Unity). 
Unfortunately, I don't remember what FileZilla version I used before. 

Got advise at official forum: 
``[COLOR=#323D4F][FONT=Lucida Grande]Please update to the most recent version of FileZilla. As of writing this, the most recent version is 3.9.0.3[/FONT][/COLOR]``


Ok, now it is FileZilla 3.9.0.3 on my home PC under Lubuntu 14.04.1 LTS. 
Unfortunately, it didn't help in my case. 


Tried active and passive mode. 
Transfer doesn't start in active mode at all. 
Transfer starts in passive mode and then freezes at 5% forever. Tried to leave it alone for couple of hours, but it doesn't move. 


Internet connection is good: 

9.71 Mb/s download 
10.17 Mb/s upload 
10 ms ping
(speedtest)



Tried remote ftp hosts in different countries, USA and Germany, still nothing. 


What's wrong?


Upd: avg size of my files for transfer is about 5 MB.


Upd 2: I tried to leave transfer for a night and it shows some results. 
FileZilla successfully transfered few files in the middle of the night. And then freezed again. 
Could you please suggest me what should I check to understand the situation?

Got next advise at official forum: 
``[COLOR=#323D4F][FONT=Lucida Grande]Too many variables, more information is needed. Please post a [/FONT][/COLOR][Log]("https://wiki.filezilla-project.org/Log")[COLOR=#323D4F][FONT=Lucida Grande] of a transfer attempt.[/FONT][/COLOR]``

Actually I'm stuck on this step. Yes, I know that I can look at [https://wiki.filezilla-project.org/Log](https://wiki.filezilla-project.org/Log) 
But it works fine at my workplace under windows7 via proxy. And I got no reason to proceed. For this moment. 

Upd 3: Maybe I will return to this subject when I will need to transfer files to ftp next time. 

Upd 4: It is regular ftp. Not ssh/ftp.

---

