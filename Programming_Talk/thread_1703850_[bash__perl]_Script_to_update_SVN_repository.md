---
title: "[bash || perl] Script to update SVN repository"
date: 2011-03-09
forum: Programming Talk
---

### Post by KdotJ on 2011-03-09
Hey guys, hope someone will be able to help me out. I have looked online for a bit for the answer to my question but not really found anything I can  get along with... 

Basically, I have a server which has an Subversion repository on it and on my laptop I have a bash script that updates the working copy when I run the script. However, I have to enter my password when prompted.

Is there a way I can have my script enter the password for me? I ask this because I want to add this script to my cron jobs to update the working copy every day. If not bash, I would also be happy to use perl for the script.

Any ideas?

PS. this is for my own personal use only to make my life easier. My username, my password. I don't intend to use this for anything bad.

Thanks in advance

---

### Post by MadCow108 on 2011-03-10
you can uses *expect* to enter passwords in interactive programs.

if the connection is over ssh you can also uses public/private key authentication to avoid typing in the password.
[http://rcsg-gsir.imsb-dsgi.nrc-cnrc.gc.ca/documents/internet/node31.html](http://rcsg-gsir.imsb-dsgi.nrc-cnrc.gc.ca/documents/internet/node31.html)
note than when not using a passphrase anyone with access to your laptop can mess with svn (and any other service with the key registered).

better use a passphrase and ssh-agent for temporary caching.

---

