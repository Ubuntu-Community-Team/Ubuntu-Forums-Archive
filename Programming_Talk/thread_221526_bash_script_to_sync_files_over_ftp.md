---
title: "bash script to sync files over ftp"
date: 2006-07-23
forum: Programming Talk
---

### Post by loftx on 2006-07-23
Hi all, I'm trying to write a script which logs into my FTP server, gets the list of files in a directory, compares it with a directory on my pc and then downloads any files on the ftp server which arn't on my PC. 

I think this can probably be achived with pipes or somesuch thing but can't quite get it to work - here's what I've got so far.

```

ftp ftp.myserver.com <<** > tempfile
binary
cd logs/W3SVC2867
ls *.cab 
bye
**

for FName in $(cat tempfile); do
  if [ -f localdirhere/$FName .cab ];
    then
      X=0 # not sure how to program a not!
    else
      # copy the file over here
  fi
done

rm tempfile

```

for some reason the for itterates the individual words in tempfile rather than the the lines which messes things up - can anyone help, or suggest an easier way to do what I want,

Thanks,

Tom

---

### Post by anthro398 on 2006-07-24
I don't know what kind of access you have to the ftp server, but using expect, ssh, and rsync would probably be faster since ftp has so much network overhead.  Also, since rsync was designed for this, the programming would be much simpler, I expect.

---

### Post by loftx on 2006-07-24
Unfortunately I only have FTP access. It's a windows server anyway, so I can't use rsync or other linux tools anyway. Cheers.

---

### Post by yaaarrrgg on 2006-07-24
You might have luck looking into the "wget" utility.  I believe it supports recursive downloads via FTP, and has a no-clobber option (handling the duplicate download problem).  

If this doesn't work, I'd think there's probably a tool already written for what you need.  Writing one from scrath, in only bash, would be difficult though.

---

### Post by loftx on 2006-07-24
Cheers, I'll look into wget. I didn't realise it would be so difficult to do in bash, so if no one knows an easy solution I'll just knock one up in python. I just though id use bash here because 'all the cool kids are doing it' :-)

---

### Post by cpeters on 2007-12-10
This uploads files rather than downloads.

[FONT="Fixedsys"]
#!/bin/bash
# Upload [http://starryskies.net/whereonearth](http://starryskies.net/whereonearth)

lftp -u user,password -d -e "mirror -vnR  /var/www/whereonearth /whereonearth" starryskies.net

[/FONT]

See the man page of lftp and to download omit the -R.

---

