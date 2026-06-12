---
title: "expect on debian"
date: 2011-11-24
forum: Programming Talk
---

### Post by Drenriza on 2011-11-24
Hi all.

I have made a bash / expect script to connect to a server, and download multiple files.
And expect connects to the server all fine and dandy, but when the file is downloaded it freezes until i hit ctrl - c, and then it downloads the second file in the list.

I have tried to figure out why it docent right away download file 2 after file 1 is complete, but no luck so far. So was hoping some of you guys would take a look at it here.

Please note, i have very little experience with expect.
```
#!/bin/bash

lines=$(cat film.txt)
for line in $lines
do

/usr/bin/expect - << EndMark
set timeout -1

spawn ssh user@ip
expect "user@ip's password:"
send "password\r"
sleep 2
send "scp /path/${line} root@destination-ip:/path/\r"
expect "root@ip's password:"
send "password\r"
expect eof
send "exit\r"
EndMark
done

exit 0
```

And if anyone has a better solution then to close and open a new session for each download, i'am all ears :P as i stated.
Little experience with expect.

---

### Post by hakermania on 2011-11-24
Hello, I want to point out that while I have heard about expect, I've never used it. I have some suggestions so as not to open different sessions for each download and a more bash-friendly reading of the file.
If I've got it right, expect reads output and when it comes with a matching string it just proceeds to the following code.
If I'm right, then the script could go as:
```

#!/bin/bash

/usr/bin/expect - << EndMark
set timeout -1

spawn ssh user@ip
expect "user@ip's password:"
send "password\r"
sleep 2

while read line; do
   send "scp /path/${line} root@destination-ip:/path/\r"
   expect "root@ip's password:"
   send "password\r"
   expect eof ## <- HERE expect the eof and then do a new request for another file(proceed to the while loop again).
done < film.txt

send "exit\r"
EndMark

exit 0

```Because I have never worked with ssh either, will it expect for root@ip's password every time you try to download a file from the same session? If yes, then the above code is right, it asks for passwd each time a file is being downloaded.
If not, then the code could go as:
```

#!/bin/bash

/usr/bin/expect - << EndMark
set timeout -1

spawn ssh user@ip
expect "user@ip's password:"
send "password\r"
sleep 2
first_time=1 # <- HERE making a variable so as to know which is the 1st time.

while read line; do
   send "scp /path/${line} root@destination-ip:/path/\r"
   if [ first_time -eq 1 ]; then # <- HERE, the 1st time first_time will be 1, so it'll ask for password!
      expect "root@ip's password:"
      send "password\r"
      first_time=0 # <- HERE, setting first_time as 0, so as not to pass the above 'if' statement again.
   fi
   expect eof
done < film.txt
send "exit\r"
EndMark

exit 0

```Hope I helped a bit or a byte :D

---

### Post by Drenriza on 2011-11-28
> **hakermania said:**
> Hello, I want to point out that while I have heard about expect, I've never used it. I have some suggestions so as not to open different sessions for each download and a more bash-friendly reading of the file.
If I've got it right, expect reads output and when it comes with a matching string it just proceeds to the following code.
If I'm right, then the script could go as:
```

#!/bin/bash

/usr/bin/expect - << EndMark
set timeout -1

spawn ssh user@ip
expect "user@ip's password:"
send "password\r"
sleep 2

while read line; do
   send "scp /path/${line} root@destination-ip:/path/\r"
   expect "root@ip's password:"
   send "password\r"
   expect eof ## <- HERE expect the eof and then do a new request for another file(proceed to the while loop again).
done < film.txt

send "exit\r"
EndMark

exit 0

```Because I have never worked with ssh either, will it expect for root@ip's password every time you try to download a file from the same session? If yes, then the above code is right, it asks for passwd each time a file is being downloaded.
If not, then the code could go as:
```

#!/bin/bash

/usr/bin/expect - << EndMark
set timeout -1

spawn ssh user@ip
expect "user@ip's password:"
send "password\r"
sleep 2
first_time=1 # <- HERE making a variable so as to know which is the 1st time.

while read line; do
   send "scp /path/${line} root@destination-ip:/path/\r"
   if [ first_time -eq 1 ]; then # <- HERE, the 1st time first_time will be 1, so it'll ask for password!
      expect "root@ip's password:"
      send "password\r"
      first_time=0 # <- HERE, setting first_time as 0, so as not to pass the above 'if' statement again.
   fi
   expect eof
done < film.txt
send "exit\r"
EndMark

exit 0

```Hope I helped a bit or a byte :D

Hi hakermania.
I will try and try to work with your code example. And the new information you have given to me :p

Thanks.

---

### Post by Drenriza on 2011-11-28
Hey.

I didn't get far. Apparently Expect doesn't regonise the while loop.
But is their anyone who can tell me, why in my script it does not download file2 when file1 is done. It just sits idle and waits for an ctrl - c to continue. Anyone who can enlighten me?

---

### Post by hakermania on 2011-11-28
> **Drenriza said:**
> Hey.

I didn't get far. Apparently Expect doesn't regonise the while loop.
But is their anyone who can tell me, why in my script it does not download file2 when file1 is done. It just sits idle and waits for an ctrl - c to continue. Anyone who can enlighten me?

Dreniza, can I have a screenshot of an operation in which you login, download 2 files and then exit? This will help me a lot so as to work with the 'expect'. Basically I need to know the strings that are being shown when operations are done. For example, instead of 
```

expect eof

```
something else could be used, because this, apparently doesn't work?

---

### Post by Drenriza on 2011-11-28
Hi hakermania.
Well i have been digging a bit in the timeout function. And it seams that timeout -1 is an infinitive timeout. And for some reason the expect script does not notice the expect eof function. And then never times out.

Besides that, their is not a lot to expect "something" since when scp is finnished downloading, it just creates a new line. I don't know if you can create an expect statement on that. So now i'am trying with rsync and see if this makes any difference.

At least rsync shows the download in bytes. So i believe i can create an expect statement on the fileSize.

---

### Post by Drenriza on 2011-11-28
So this seams to work.

```
#!/bin/bash

linesName=$(cat film.txt |awk '{print $8}')

for line in $linesName
do

/usr/bin/expect - << EndMark
set timeout -1

spawn rsync -a -r -z -v --progress --partial -e ssh user@ip:/path/${line} /destination/
expect "user@ip password:"
sleep 2
send "password\r"
expect eof
EndMark
done

exit 0
```

---

### Post by hakermania on 2011-11-28
> **Drenriza said:**
> So this seams to work.

Yes, but again you will have to login multiple times so as to  download every file!
If this doesn't bother you, then it's OK, but if it does, then you should see what you could 'expect' instead of 'eof'. I mean, when you call:
```
expect eof
```in the previous code-example, are you sure you couldn't detect in some other way that the file downloading has finished?
That's why I asked for a screenshot actually. If for example it is like this:
```

alex@MaD-pc:~$ ssh user@ip
user@ip password:
File successfully downloaded!
scp> Write anything I like here

```then the corresponding code could be:
```
expect "scp>"
```and then to send the command so as to download the next file. Are you sure this cannot be done with sftp as well?

I recently made this using the sftp, it actually updates the live earth image over [here]("http://wall-changer.sourceforge.net/screenshots.html"), after it is being uploaded to imgur.com (you gave me the original idea by reminding me about expect :P):
```

#!/bin/bash
#Below, I am creating the html page so as to be uploaded afterwards, do not be bothered by this
./create_html $1 "$2"
#expect takes action here
/usr/bin/expect - << EndMark
set timeout -1

spawn sftp user@web.sourceforge.net
expect "user@web.sourceforge.net's password: "
send "password\r"
expect "Connected to web.sourceforge.net."
send "cd htdocs\r"
expect "sftp>"
send "put screenshots.html\r"
sleep 5
EndMark
exit

```You can take this as example and make it, instead of 'put'ting to download files to your local disk, using a while or for loop.

---

