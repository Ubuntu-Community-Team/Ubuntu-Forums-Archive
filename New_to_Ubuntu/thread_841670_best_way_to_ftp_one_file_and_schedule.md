---
title: "best way to ftp one file and schedule?"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by janne5011 on 2008-06-26
Hi I want to ftp one file for example each hour so its a easy task.
Best application and way to achive it?

Thanks in advance
/J

---

### Post by hyper_ch on 2008-06-26
I'd use cron and scp

---

### Post by janne5011 on 2008-06-26
> **hyper_ch said:**
> I'd use cron and scp

Ok I found a script to use ftp the file and it works :)when I
go to the directory where it is adn simply click it.

Then I did sudo crontab -e and putted this in crontab (I think its roots crontab?):

*/10 * * * * root /home/janne/folder/ftp.sh

I did chmod 775 to ftp.sh.

But it dont upload with crontabs help as I indeed hoped.

---

### Post by ByteJuggler on 2008-06-26
Without knowing what's in ftp.sh it's going to be very hard to help you.  Personally, if the target machine also has ssh, I would also recommend using scp instead of ftp.

---

### Post by janne5011 on 2008-06-26
> **ByteJuggler said:**
> Without knowing what's in ftp.sh it's going to be very hard to help you.  Personally, if the target machine also has ssh, I would also recommend using scp instead of ftp.

host  ftp.somehost
user a-user
passwd ****

FILE:snapshot.jpg
#the file is in same directory

ftp -n $HOST <<END script
quote user $USER
PUT $FILE
END SCRIPT
exit 0

I can run it with ./ftp.sh when in that folder.
tested it again and it works.

so how can I do the same with crontab?

---

### Post by ByteJuggler on 2008-06-27
> **janne5011 said:**
> host  ftp.somehost
user a-user
passwd ****

FILE:snapshot.jpg
#the file is in same directory

ftp -n $HOST <<END script
quote user $USER
PUT $FILE
END SCRIPT
exit 0

I can run it with ./ftp.sh when in that folder.
tested it again and it works.

so how can I do the same with crontab?

Please use code and quote tags to delimited quoted code etc.  Are you saying your file, "ftp.sh" contains exactly: 

```
host  ftp.somehost
user a-user
passwd ****

FILE:snapshot.jpg
#the file is in same directory

ftp -n $HOST <<END script
quote user $USER
PUT $FILE
END SCRIPT
exit 0

```

If so, that's not a valid shell script, for one it lacks the proper headers to identify it as a shell script.  Secondly, am I right in thinking you have a file called "END" that contains an EOF character or something?

Anyway, things you need to address:
1.) Headers (Put "#!/bin/bash on the first line)
2.) Working directory.  The script might work when your working directory is your home folder or wherever, but the working directory is almost certainly not that when cron runs it.  You need to put some "cd" commands in to change the folder appropriately, or specify explicit paths.
3.) Access rights  Make sure cron will have rights to the folder/file in order to be able to ftp it.
4.) Also, your "shell script" seems to be a mixture of input for the "ftp" command and shell commands.  You should not leave the input to "ftp" in the shell script itself, put that in a seperate file instead, and pipe that into ftp.  E.g. "ftp -n $HOST <ftp_input"   **Edit: **Never mind, I see how "END_SCRIPT" works to allow you to intersperse input to ftp with shell script code.

Edit2: [Here's ]("http://www.delamainit.com/articles_how-tos/apple-mac-osx/mysql-file-ftp-backup-shell-script.html")a good example of a shell script involving ftp'ing.

---

