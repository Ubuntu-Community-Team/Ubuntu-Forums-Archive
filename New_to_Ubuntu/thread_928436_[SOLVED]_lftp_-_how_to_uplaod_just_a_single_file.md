---
title: "[SOLVED] lftp - how to uplaod just a single file?"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by Primefalcon on 2008-09-24
I just started using lftp and I am trying to get to grips with it....

I been reading the man page....

however I can't seem to find how to just upload a single file from my computer to a webserver for example.

lftp seems to have a simple syntax yet able to do most of anything so I'm probably just missing something here

---

### Post by jgedutis on 2008-09-24
I'm not familiar with that program, but I would just use stand ftp from a terminal.

Go to Applications --> Accessories --> Terminal

It should open with something like 

User@ComputerName:~$

If you type in the below command replacing the webserver with the real site.  You don't need the http:// stuff for it to work.  
ftp ftp.webserver.com

It should then prompt you for a username and password

Once connected to move around you can cd to change directory and use dir to list the directory contents.

If you are transfering the file you need to specify the local file. If it was in the /tmp directory you would then type the following command to go to that command in your local directory

ftp> lcd /tmp

If it is not a text file you will want to set it to binary transfer
mode with the command below

ftp> bi
200 Type set to I.
ftp> 

Now you can use put to put the file from the "lcd" directory to the one you browsed to on the remote computer. With put for a single file or mput for multiple files.

ftp> put mywebfile.html 


I'll be on for the next 30 minutes or so so let me know if you have problems.

---

### Post by Primefalcon on 2008-09-24
lftp is bascialy a more advanced ftp command line utility itself that I'm trying to get to grips with. but I just want to know how to upload, download and delete files form the command line

I just got sick of filezilla gftp and half a dozen other file transfer utilities.

Since editors like vi pretty much blow all others out of the water I am trying to get to grips with doing this from the command line as well

---

### Post by Primefalcon on 2008-09-24
ok thank you that works pretty damm good, if I want to download I basicaly do just the same thing except with get right?

and I see I have to use delete instead of rm, but does this put and get work with directories too?

thank you very much btw

---

### Post by jgedutis on 2008-09-24
What features does it offer that you want to take advantage of? 

You can do what you mentioned with just ftp.  

you can put files from local computer to webserver with "put filename" command

You can get files from webserver to your local computer with "get filename"

you can delete files on the webserver with "del filename

I just have lftp a shot and could not get it to connect to immediately.  I would give ftp a shot.

---

### Post by Primefalcon on 2008-09-24
I am the thing I like with lftp is it doesn't seem to actualy disconect unless you want it to regardless of host stuff just having probs getting to geips with it

to connect in lftp

$lftp username [ftp://domain.com](ftp://domain.com)

it'll then prompt for a pass

I am going to use ftp it at least gives me a control

---

### Post by Primefalcon on 2008-09-24
actualy thank you very much, that put works as well in lftp but in lftp you dont have any time out problems, that you very much

---

### Post by jgedutis on 2008-09-24
No problem.  Glad it will work out for you.  The one big downside I find to Linux is that there are so many choices its hard to decide which to use....for free :)

---

### Post by Primefalcon on 2008-09-24
very true, but one thing you gotta love with linux is consistency such as put working with both ftp and lftp

---

