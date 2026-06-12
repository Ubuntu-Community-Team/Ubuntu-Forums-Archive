---
title: "Apache2 and Lamp"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by wetinwales on 2008-09-06
Hello All
All I need to do is preview a my website in Firefox as I work on it. It contains php and kicks off with index.php
Ubuntu 8.04. Up to date.Installed LAMP. Got the "It Works" and tried my own text line in an index.php All works OK and all in /home/user/public_html/mywebfolder
Applied the website directory to /home/user/public_html/ and split out the index.php (to be found?) and typing [http://localhost](http://localhost) in Firefox gives me:-

Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0

Fatal error: Unknown: Failed opening required '/home/user/public_html/index.php' (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0

I AM a newbie in many respects, and a coffin dodger to boot, but I can count to three and touch my toes. I even got Apache2 into WinXP by myself. What I can't do is figure this one out.

Heeeeeeeeeeeeeeeeeeelp..

Wetinwales

---

### Post by JeppeM on 2008-09-06
Hey Wetinwales :)

I think your problem is more related to setting up PHP correctly, rather than Ubuntu. 

Anyway, i think your problem lies in the security restrictions of the linux directories etc. Apache/PHP doesn't have the correct permissions to read the index.php file. I suggest you chmod the entire /home/user/public_html to 777 (since it's only your own system, and not a real web server, there's not much of a security risk with this, normally you would set up the apache user as the owner and do other fun stuff, but it might be a bit too advanced for you for now). Anyways, this command from the commandline should solve it:

chown -R 0777 /user/home/public_html

If not, post back and i'm sure we can figure it out :)

---

### Post by wetinwales on 2008-09-06
Sadly that didn't work. How do I remove the 'chown' to get rid of the 777 security issue?
Any other ideas? 
Thanks

---

### Post by stoneybroke on 2008-09-06
Hi Have you read the installed manual on setting up a website etc click on the Help icon next to evolution on the taskbar go to Advanced Topics then to Installing Server Applications this will tell you all you need to know to get it working ok

Hope that helps

---

### Post by wetinwales on 2008-09-06
Stoneybroke
I'm wondering what the thrust of your reply is. I've written and managed my three websites for a few years. My frighteningly literate son put one site into php to solve a 'Google indexing' issue. I don't do Dreamweaver et al. I do it all in Notepad.
So what am I looking for?
Thanks
wetinwales
[www.berclas.co.uk](www.berclas.co.uk)

---

### Post by JeppeM on 2008-09-06
hmm, wierd... Sounds like you have some setting the your php.ini file which makes the script die due to some permission problem... Could you paste the values of include_path and open_basedir? You will most likely find your php.ini file somewhere in /etc/php5, so search that folder (and subfolders) for it...

Do undo my previous command, do this:

chown -R 0644 /user/home/public_htm

---

### Post by wetinwales on 2008-09-06
Hi JeppeM Thanks for this
Here is code:-

; UNIX: "/path1:/path2"
;include_path = ".:/usr/share/php"
;
; Windows: "\path1;\path2"
;include_path = ".;c:\php\includes"

AND...............................................

;open_basedir =

I have to say, I spent days trying to track a tuning fault on a frequency counter I built - only to find a dry joint in the power supply. This could be a glaring case of me not seeing or knowing the obvious syntax. For example, all I type in to Firefox is [http://localhost](http://localhost)  ... 
Btw The sequence was this:-
Install 8.04
Install LAMP from [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) 
Website folder is in /home/user/public_html/WEBFOLDER and has its index.php in public_html as well - which I presume is correct as the other two mini sites work if enabled "It Works" (default - index.html) and my own test "Lumberjack" dhob - index.php)

wetinwales

---

### Post by wetinwales on 2008-09-06
JeppeM
I looked through 'Permissions' for all files and directory. Checked it all with ls -l and all lookssuitably 'permitted'
Also re did chown -R user to recover that situation.
many thanks for your help so far

wetinwales

---

### Post by wetinwales on 2008-09-06
Hi 
Latest info:-
A whole website now resides in /public_html/ together with an 'index.html' (It Works) and 'index.php' (Lumberjack). 
Disabling the website 'index.php' file allows me to choose between [http://localhost/index.html](http://localhost/index.html) or [http://localhost/index.php](http://localhost/index.php) Both of which work properly in browser. Simple one line text.
The index.php (to fire up the website) returns the Fatal error message.
I tried another non php website, and that too returns the error message.

So the simple files are allowed, the websites not.

Is that a useful clue to anyone?

thanks
wetinwales

---

### Post by Paul41 on 2008-09-06
Instead of a chown try a chmod to change the file permissions and see if that helps.

```
sudo chmod -R 777 /home/user/public_html
```

---

### Post by wetinwales on 2008-09-07
Hello Ubunters

RESOLUTION at last.
This was entirely my misunderstanding of the permissions methods in Ubuntu.
Am I now right in understanding that Linux/Ubuntu is a labyrinth of protected files and folders by default - for very good reasons - and that one's proceedure should always be to consider permissions when creating/saving ANY file..?

All my files, of course, came from WinXP OS into Ubuntu.

Thanks to those who tried to help

wetinwales

---

### Post by JeppeM on 2008-09-08
Wow, i wrote chown?! didn't see that before now... I actually meant chmod as well :( My fault, was a bit sleepy at that point :( the real chown syntax is different than the one i wrote.. Lol...

Anyways, the examplenation of why you need to do the permissions thing:

When apache is trying to access a PHP file, it actually needs to execute it, not just read it. So all your PHP files should be executable by the "world" group (think it's named Others in the permissions dialog). The normal way you get around this on "real" webservers are making the FTP account log in as the apache-user (you set up a user which then starts Apache and "owns" that proccess), which means that you can just give the normal permissions (read-write-execute for the owner of the file), and none for the rest of the users.

But for your normal computer i think that it might be a bit too advanced to do this for now, unless you want to make apache run under your user. If i remember right you can do this by editting httpd.conf and finding the place it says User and Group, and change that from www-data (i think thats the one for the defalut LAMP installation on ubuntu) to whatever your username and group is.

This does hold a security thread though, and a PHP script would be able to do some damage if it's not working correctly (by changing it to run under your user, php scripts could get access to ALL your files etc).

Erhm, hope this helps, and again, sorry about the typo in my first few posts, no idea where i left my brain :(

---

### Post by wetinwales on 2008-09-09
JeppeM
Thanks for your help! My httpd.conf file is empty. Perhaps its the apache2.conf file which contains the USER and GROUP lines. I tried it but didn't understand the architecture.
I do find that 'HELP' files and documentation never show simple explanations - particularly for people like me who are visual based rather than mathematical.
A Drawing of the 'architecture' of a software would help me no end! Such is life..
Anyway, all is working splendidly and I hope Microsoft is gone forever from my life!

---

### Post by JeppeM on 2008-09-10
they'll never be truely gone - But their role in your life might be much less now :D

Have a nice day, and keep enjoying ubuntu :P

---

### Post by hartunnoo on 2010-05-15
> **Paul41 said:**
> Instead of a chown try a chmod to change the file permissions and see if that helps.

```
sudo chmod -R 777 /home/user/public_html
```


I got the same problem, after I run this commands and its working but is this safe?

---

### Post by Paul41 on 2010-05-15
> **hartunnoo said:**
> I got the same problem, after I run this commands and its working but is this safe?

How are you using the server (just for personal testing or a public server)?  If it's for local use I wouldn't worry about it. If it is for public use I would look for another solution.

---

### Post by hartunnoo on 2010-05-17
> **Paul41 said:**
> How are you using the server (just for personal testing or a public server)?  If it's for local use I wouldn't worry about it. If it is for public use I would look for another solution.

To chmod 777 to /home/user/public_html would not be a good idea, It is for public to view the site. Is there any other solution for it?

---

