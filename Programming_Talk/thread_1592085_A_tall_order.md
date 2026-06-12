---
title: "A tall order"
date: 2010-10-10
forum: Programming Talk
---

### Post by aspiredfang on 2010-10-10
I'm going to be moving to China in the coming week and have a need to access my home computer due to some strict Firewall rules on certain sites I have developed (I'm a Web Developer). Access itself via SSH/TOR is all sorted and the like but, now I'm looking to start using some alternative CLI tools for certain tasks I perform; mainly FTP and that what this post is about.

Normally I use Filezilla (as quite simply, it's a great piece of kit) and am now making the transition across to ncftp. Now, I'm quite a beginner when it comes to shell scripting  (PHP is my "forte")within *nix having only created the odd script for odd jobs. Recently, I have started reading the bash scripting guide linked to from this forum.

It is however, over 800 pages long! Over time, it will get read but, in order to fast forward a lot of unnecessary reading, please can some of the more experienced programmers help me out with pointers on what to use, an alternative I've missed or even a spot of code for the following:

- Use ncftp(ls) in order to create a directory listing of everything within a set path (var/www/vhosts/xxxx/httpdocs/) including sub directories.
* This step can come later on after this is working but, exclude defined directories and its children.
- Compare that listing against a locally stored structure, which would mirror that of the site...within httpdocs.
- Generate an ncftpput list that only uploads files that have a different file size.

With the above, note I would use scp to put the files on my box back at home (backup purposes also) and want to use the script whilst logged in to it via a shell. There could be a feature for this already and I'm just missing it or a much simpler way even! Any help would be much appreciated, thank you in advance for even reading this post.

---

### Post by aspiredfang on 2010-10-10
I've created some basic code which I know is faulted and provides very little feedback. I keep each of the sites working on within /home/documents/"project_name"/site/

Example call
sh ./ftpupdate.sh ftpuser ftppass ftpaddress

```
#!/bin/bash

# Fetch ncftp parameters from script call
strUsername = $1
strPassword = $2
strFtpAddress = $3

# Calculate what local project to use as the check
# The script should be run from its "parent folder"
strLocalProjectDir = $PWD 

# Connect to the desired server and fetch list
ncftpls -l -u strUserName -p strPassword strFtpAddress > /tmp/ftplisting.txt

# Create the local listing
ls -l -R strLocalProjectDir > /tmp/locallisting.txt

# Create the list of files that differ
diff /tmp/ftplisting.txt /tmp/locallisting.txt > /tmp/filestoupload.txt

# Perform the actual ncftpput operation with generated file list
ncftpput -m -R -u strUserName -p strPassword strFtpAddress
```

---

### Post by SeijiSensei on 2010-10-10
Have you looked at rsync?  It's probably an easier tool for this task, and it runs inside SSH by default.  If you use shared keys to authenticate, you can automate the entire transfer.

> - Use ncftp(ls) in order to create a directory listing of everything within a set path (var/www/vhosts/xxxx/httpdocs/) including sub directories.
* This step can come later on after this is working but, exclude defined directories and its children.
- Compare that listing against a locally stored structure, which would mirror that of the site...within httpdocs.
- Generate an ncftpput list that only uploads files that have a different file size.

rsync does all this by default.  It compares a source and target directory and transfers only the changed files.  Not only that, it uses diff to transfer only the changes themselves, not the entire files, for efficiency.  Including the "-v" (verbose) switch gives you a nice listing of the files that were transferred.  See "man rsync" for details and examples.  You might also consider running rsync in "daemon" mode on the remote server which gives you greater control over things like how file permissions are managed on the remote.

---

### Post by aspiredfang on 2010-10-10
Thanks for replying, I have looked at rsync and recognize that would work between the laptop I'm working on and the computer back at home. 

The problem is having the computer back at home sync itself with a web server when there is only the FTP protocol available. As far as I'm aware, Rsync is its "own protocol" and won't allow such behaviour as part of its functionality

---

### Post by aspiredfang on 2010-10-10
Just a bit more swimming around the net came up with what appears to be an excellent solution. It's using lftp instead of ncftp, I'll try it later and report on how effective it is but, for the moment. This is one useful bit of scripting I believe for any CLI ftp people out there, how does yours look?

```
#!/bin/bash
HOST="your.ftp.host.dom"
USER="username" 
PASS="password"
LCD="/path/of/your/local/dir" 
RCD="/path/of/your/remote/dir" 
lftp -c "set ftp:list-options -a; 
open ftp://$USER:$PASS@$HOST;  
lcd $LCD; cd $RCD; 
mirror --reverse \        
--delete \        
--verbose \ 
--use-cache \
--parallel=2 \
--exclude-glob a-dir-to-exclude/ \        
--exclude-glob a-file-to-exclude \       
--exclude-glob a-file-group-to-exclude* \       
--exclude-glob other-files-to-exclude" 
```

---

