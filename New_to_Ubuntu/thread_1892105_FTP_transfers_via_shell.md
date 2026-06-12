---
title: "FTP transfers via shell"
date: 2011-12-07
forum: New to Ubuntu
---

### Post by Moif_Murphy on 2011-12-07
Hello,

I have an Ubuntu VPS and some shared hosting elsewhere. I have 100GB of files sitting on the shared hosting that I need to transfer into the VPS.

I have FTP access on the shared hosting only and root SSH access on the VPS.

I've used Windows FTP command line before and would like to do the same via the shell on the VPS.

Any help appreciated :)

---

### Post by josephmills on 2011-12-07
ftp uname@host 
enter passwd 
once connected run 
help 


I would 100% go with ssh 
Using SCP you could copy files remotely. Following is the general syntax.
         ```
     scp  <file> <username>@<IP address or hostname>:<Destination>
```



rsync is also nice ! 

[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)


there is a wealth of ubuntu docs about this Here is one [http://manpages.ubuntu.com/manpages/intrepid/man1/scp.1.html](http://manpages.ubuntu.com/manpages/intrepid/man1/scp.1.html)
[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

---

### Post by lukeiamyourfather on 2011-12-07
I'd use scp, see the man page for the full detail.

---

### Post by lukeiamyourfather on 2011-12-07
> **josephmills said:**
> I would 100% go with ssh 
Using SCP you could copy files remotely. Following is the general syntax.
         ```
     scp  <file> <username>@<IP address or hostname>:<Destination>
```



rsync is also nice ! 

```
scp -r localfile.txt username@192.168.0.1:/home/username/ 
```



there is a wealth of ubuntu docs about this Here is one [http://manpages.ubuntu.com/manpages/intrepid/man1/scp.1.html](http://manpages.ubuntu.com/manpages/intrepid/man1/scp.1.html)
[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

You beat me to it, and with an example. Kudos! :guitar:

---

### Post by Moif_Murphy on 2011-12-07
Awesome, thanks guys. I'll get reading.

---

### Post by CharlesA on 2011-12-07
> **lukeiamyourfather said:**
> I'd use scp, see the man page for the full detail.

+1. I use sftp myself, but scp works too.

---

### Post by Moif_Murphy on 2011-12-08
If anyone stumbles across this thread in the future, this is what I did. I had 100GB of MP3s sitting in folders that I needed to get across to my new VPS. I had no shell access to the server where they were located, only FTP.
 
I installed ncftpget onto the VPS where the files would end up and I ran this command (adjust accordingly):
 
```
 
ncftpget -T -R -v -u "USERNAME" IPADDRESS /path/to/local/directory/on/VPS /path/to/remote/directory/on/FTP

```
 
You have to enter a username otherwise it'll default to Anonymous and once you've entered this command you'll be prompted for the password.
 
Job done.

---

