---
title: "[SOLVED] Total Linux nOOOOOOb, please help me change from windows"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by jamesdigby on 2008-10-14
hi there,

i am not quite even where to start!!!!

i have my little own website....it is mostly static HTML pages..hosted using abyss, but i use php for a forum which uses a textfile database. all this runs on winxp pro 3Gig cpu 1gig ram.
i update my site over lan using frontpage into the root folder through windows sharing. i have 2xadsl lines only 1 is actually used for the website.. both lines have dynamic ip.. so i use no-ip to update my dns.

my server pc is now stuggling.. the rendering times to html on the forums is stupid.... 

so i figure the solution is something along the lines of php and sql

i have been out and bought another 3 pc's with the idea of a bit of redundancy and maybe a bit of load sharing.. and maybe splitting the loads over the two adsl lines (the 2 lines have different ip's i dont think i can get them bonded with out it costing me too much)

i have been trying so hard to get my head round linux even to the extent of stopping up till 3,4,5AM... tried loads of distro's and live cd.... even some LAMP builds.. but i am lost.

i have managed to get some up and running but can even get the basic html pages over to the linux machine

ideally i just need something that i can web-interface to set up and use frontpage with from my windows machines

I have read loads of sights about different distro's, clustering, load balancing

i have one pc with ubuntu installed... i can access the web interface (webmin) from my windows pc.. and from gnome i can see my windows pc's but i can seem to copy and paste the www. folder contents to my ubuntu machine from a shared folder on the windows machine

i must be missing something.. any help at all would be good

---

### Post by stephanvaningen on 2008-10-14
It is difficult to read in your text what your *exact concrete* problem is? 

If you would you like support setting up a web-server which you can update from a remote (windoze) pc? Using ftp?
 If so => I think no probs if you just install a default Ubuntu Server 8.04.1 and at the screen of choosing functions, tag:
 LAMP (Apache, MySQL, PHP)
 FTP

We'll continue from there after default installation is finished ok?

---

### Post by Keen101 on 2008-10-14
You need to install samba on the ubuntu machie for sharing between windows and linux. Unfortunately i don't know much about samba.

---

### Post by Orange_and_Green on 2008-10-14
Hello, welcome to the forums.

The "standard" ways in Ubuntu to share files between PCs are ssh and scp (Linux-Linux) and samba (Linux-Windows).

This is a very good guide for setting up and configuring samba:

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

Good luck :KS

[EDIT]: if you use samba and need to edit remote files, I have found it generally safer to download the files to local, edit the files locally and upload the edited versions again. Editing directly from the remote server usually works fine but I've seen windows crash on this a couple of times and the results were very ugly (messed up file systems and so on). Just a small tip I felt I should share. Good luck.

---

### Post by jamesdigby on 2008-10-14
ok installed..
got 1 machine total fresh install sat at the prompt and another installed using option 1 (webmin) and option 2 (gui-gnome)

i am ok with apache... no problems yet... i can get the 'it works' screen.. i can log into the machine [https://192.168......:10000](https://192.168......:10000) to access webmin

what i cant do is ftp my files into /var/www/ nor can i even begin to figure out how to do it in webmin

the otherway i have tried is:
 
to copy my site into a shared folder on a windows machine. OK

view the shared folder over the network on my ubuntu (using gnore GUI) OK

then on ubuntu machine... select the files, click copy, navigate to var/www then try to click paste and it wont let me paste (it is greyed out)

thanks for your help in advance

james

---

### Post by hyper_ch on 2008-10-14
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;) 

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

---

### Post by jimbren on 2008-10-14
<snip>
*"what i cant do is ftp my files into /var/www/ nor can i even begin to figure out how to do it in webmin..."*

How are you trying to ftp your pages, and what is the error you're getting?

Putting the files in the directory by ftp is a sound way to go.  Once you get past the error you're getting, you should be good to go.

jimbo

---

### Post by Orange_and_Green on 2008-10-14
> **jamesdigby said:**
> then on ubuntu machine... select the files, click copy, navigate to var/www then try to click paste and it wont let me paste (it is greyed out)

For increased security, users in Ubuntu do not have administrator privileges. However, you need such privileges to write into system directories (like /var). So, there are two ways to do what you are trying to do:

1) The graphical one. Go to Applications->Accessories->Terminal. Type
```
gksu nautilus
``` into the box. It will prompt for a password, then start the file browser in superuser mode. Click the "up" arrow until it grayes out, then click "file system". You should be able to locate the /var directory. Next, locate the files you need to move. If you previously put them on your Desktop or in your Documents folder, you can find these by navigating to /home -> yourname -> Desktop / Documents. Copy, navigate back, and paste.

2) The command line way.
Go to Applications->Accessories->Terminal. Type
```
sudo cp -r PATH_TO_COPY /var/www/
```

PATH_TO_COPY obviously depends on where you put the files, again. Candidates are something like /home/YOUR_NAME/Desktop/Folder or /home/YOUR_NAME/Documents/Folder.

A few links you might find useful before you start:

[http://www.freeos.com/articles/3102/](http://www.freeos.com/articles/3102/)
[http://www.freeos.com/articles/3127/](http://www.freeos.com/articles/3127/)
[http://www.youtube.com/watch?v=460IxkYmZxQ](http://www.youtube.com/watch?v=460IxkYmZxQ)
[http://www.youtube.com/watch?v=Iuru-LTasjg](http://www.youtube.com/watch?v=Iuru-LTasjg)
[http://www.youtube.com/watch?v=x3SMuCKbAkY](http://www.youtube.com/watch?v=x3SMuCKbAkY)

Good luck :KS

---

### Post by stephanvaningen on 2008-10-14
Make sure you have write access to the /var/www/ directory.
Possible ways to do this are:
[LIST]
[*]Look who is the owner of the folder www and add yourself also as a member of the group which is the primary group of the owner
[*]Change the owner of the folder www (which is more risky for maybe getting access problems in Apache)
[*]Change the access in the www-folder by doing a 'sudo chmod 777 /var/www' but is not encouraged
[/LIST]
I suggest you stick with the first option. This would solve the error you describe "navigate to /var.. and right-click: grayed out"

For the other errors (no write in webmin i.e.): possibly this is also a authority issue: check which user is being used to run the service/process webmin (check this in system monitor->processes) and add the group of the owner of /var/www as a group where the webmin-user is member of.

> **jamesdigby said:**
> ok installed..
got 1 machine total fresh install sat at the prompt and another installed using option 1 (webmin) and option 2 (gui-gnome)

i am ok with apache... no problems yet... i can get the 'it works' screen.. i can log into the machine [https://192.168......:10000](https://192.168......:10000) to access webmin

what i cant do is ftp my files into /var/www/ nor can i even begin to figure out how to do it in webmin

the otherway i have tried is:
 
to copy my site into a shared folder on a windows machine. OK

view the shared folder over the network on my ubuntu (using gnore GUI) OK

then on ubuntu machine... select the files, click copy, navigate to var/www then try to click paste and it wont let me paste (it is greyed out)

thanks for your help in advance

james

---

### Post by jamesdigby on 2008-10-16
ok getting somewhere i think... except

how do i install ftp server on my ubuntu box using only the command line or webmin??

from the webmin interface i have a choice of we-ftpd or proftpd also a presume maybe incorectly that i think i need to install ssh server.

i have read what i can find on ftp installation... 

i can use the sudo apt-get to install... but i know nothing about the configuration.....

all i want to do is get reasonable secure read/write access to the apache www. folder

thankyou in advance

---

### Post by Paqman on 2008-10-16
If you can wean yourself off Frontpage, it would be a good thing to do. Frontpage writes appallingly bad code, which will be slow to render, hard to maintain, and is highly unlikely to look the same on all browsers. I also doubt that it will play nicely with dynamic sites.

I'd highly recommend Dreamweaver as a vastly superior HTML editor that will actually write W3C-compliant code.

---

### Post by Xerp on 2008-10-16
Like Paqman I'd also advise against Frontpage. I use Bluefish - 

[http://bluefish.openoffice.nl/](http://bluefish.openoffice.nl/)

and find it very good.

For transferring files between two boxes I prefer simple scp over any rather strange Samba setups - its just so easy to use scp! You just needd to make sure ssh is installed on your Ubuntu box. On Windows use the WinSCP client to connect and you're away.

---

