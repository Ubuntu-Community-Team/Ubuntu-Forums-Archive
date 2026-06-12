---
title: "FTP multiple file renaming on remote machine"
date: 2009-09-04
forum: Programming Talk
---

### Post by ierpe on 2009-09-04
Hi,

To make short, I have this sftp server where files are being sent at different times of the day and then I have some scripts that connect to it, download the files and process them.

On the remote machine, the files go on a folder /export/
There is also a folder /export/archive/, and once I downloaded the files from /export/ to a local machine, I want to move them into /export/archive/ (on the remote host)

I am using the rename ftp command to do so, my problem is that I need the filenames in order to move them. I do so by passing the filenames as arguments to an expect script, but its not very handy for more than one file.

I thought something like "rename /export/*.jpg /export/archive/*.jpg" would work, but it doesnt...
Does anyone know a solution to achieve this?

Thanks

---

### Post by hessiess on 2009-09-04
As you are using sftp, carnt you just ssh into the masheen and do an ls to get the filenames? or better still, mount it locally with sshfs and just treat it as part of the local filesystem.

---

### Post by ierpe on 2009-09-07
if I do ssh username@host, then im asked for a password and then I cannot do anything...
I can type something but everytime I hit return, I get: 
WinSCP: this is end-of-file:0


Are you sure you can connect to sftp accounts with ssh? This is not what I had understood... I do not claim to be an expert at all...! But I thought sftp was a different protocol and that you had to handle it in its special way...
I am using php-cli to process the files and php doesnt handle sftp very well... Thats why I used an expect script to manage the connection via a normal linux terminal...

I mean, if I could just mount a sftp folder in ssh and see it as a local folder it would be perfect, but it doesnt seem to work!

---

### Post by dwhitney67 on 2009-09-07
EDITED  - Re-reading the OP several more times has convinced me that I haven't a clue what the requirements are.

---

### Post by ierpe on 2009-09-08
[EDIT]
Ok I just found a solution. I dont understand I had googled a lot but didnt find this before...


using sshfs:

apt-get install sshfs
modprobe fuse
adduser UserName fuse
mkdir ~/Desktop/sftp

sshfs [email]hostusername@remote.host.or.ip[/email]:/host/dir/to/mount ~/Desktop/sftp


Now I have a folder on my server's desktop its great! :)
I can just rename/move the files the way I want it...

[/EDIT]



Ok, I will try to give you a better description of the case.

I have this server with some stuff running on it, and it needs to go to download some files on a (remote) sftp server at regular intervals.

Basically I have 4 scripts here:
1 script shell, that is called by a cronjob, and that calls the other scripts.
1 expect script, that manages the sftp connection and download the file.
1 php-cli script, that process the downloaded file.
and 1 other expect script, that connects again to the sftp to archive the last downloaded file (to move the file into a different folder on the remote machine)

Now if I came up with such a f*** up solution, it's because I couldnt find a simple solution to automate the sftp connection. Expect does the job but I have to pass the filenames as arguments when I call the script, and it's not the handiest...

If I could mount the remote sftp folder into a local folder, then I wouldn't have problems anymore... but I couldn't find how to do this!

Ssh didn't work for me to connect to the sftp, but as I said before Im not an expert so I might have done something wrong...

So I guess that: "How do you mount a sftp folder into one of your local folder?" would be my real question!

Thanks again for your time...
P

---

