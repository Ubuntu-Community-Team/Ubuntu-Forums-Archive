---
title: "Ubuntu &amp; Server HTML - PHP don't works"
date: 2023-08-14
forum: New to Ubuntu
---

### Post by leg2027 on 2023-08-14
Hello everyone,


I'm new to this forum, as I recently installed Ubuntu for a project, and am completely failing despite all my attempts to set up a server capable of running python scripts while having html and php pages.
 
I'd like to have a server that works something like this.
An HTML page retrieves some data given by a user, a PHP script downloads files from the web, a python script combines the received data and forms a new file to be downloaded by the user.


HTML and PHP work well together, while the python script works well on its own (with data downloaded and entered manually).


On Ubuntu 22.04, I tried to install a server to bring all this together, but I was still stuck in one place.
I tried Nginx, Apache, I tried Ubuntu WSL, I followed dozens of tutorials, tried again from zero several times but I never managed to get a working server.
I've managed to get an html or php page displayed by apache or nginx, or a python file executed correctly with Flask, but never both at the same time.
I specify that my computer is an old windows which no longer worked correctly.


As I'm new to Ubuntu, I'm wondering if there's a way to configure the system that's not explained in the tutorials.
And also do you have a method, a tutorial to recommend for this?
Another server that would be easier to handle?


Thanks in advance for your help!

---

### Post by Holger_Gehrke on 2023-08-14
How about changing the PHP script to ['exec()' or 'system()']("https://www.php.net/manual/en/function.exec.php") the python script ? Seems the simplest solution to me ...

Holger

---

### Post by TheFu on 2023-08-14
Apache on Linux works pretty much the same as it does on MS-Windows.  There are virtual hosts, each can be configured for different types of scripting.  Generally, mixing of scripting languages inside the same virtual host doesn't happen, though if you use the mid-90s cgi-bin/ method, I suppose it is possible.

I hope you know that you don't need "a server" install to run a web server.  Any Linux desktop can do it too and that would simplify day-to-day use, since there would be a bit of a GUI, though no web servers are configured with any GUI.

If you want specific help, you'll need to post specific config files.  These are usually symbolic links in the sites-enabled/ directory linking back to the sites-available/ directory for both apache and nginx web servers.  Of course, different web servers do have different configuration files so the details are slightly different, but still very similar.

I don't use php or python, so I can't really help with the web server configuration for either of those. Sorry. My web stuff the last 15+ yrs has all be using web-app servers following the WSGI/PSGI standards ... no web server like nginx or apache needed, except for static files.  Scalability is much easier with PSGI ... 1 or 200 server processes is a change to 1 field in 1 config file. Plus the webapp isn't going through a heavy web-server as middleman.

[https://www.fullstackpython.com/wsgi-servers.html](https://www.fullstackpython.com/wsgi-servers.html) is a python explanation for their WSGI.  Just know that you don't actually need apache or nginx. That link does have an example nginx config, however. The config appears to listen on port 80/tcp and accesses the webapp on port 8000/tcp. It is effectively a proxy after adding a few extra headers to the requests.

---

### Post by leg2027 on 2023-08-20
Hello,

First of all, thank you for your answers.
I apologize for my late reply.
I made the terrible mistake of using *chmod 777 *and after that nothing worked properly. So I had to reinstall Ubuntu completely, taking care to save the files on an external hard drive.

But since then I've been able to reinstall everything I needed. 
I didn't know it was possible to run a linux server without Apache, Nginx or anything else. So far, I've installed Apache, and it's been fine, but if you have a tutorial to recommend for running a direct linux server, I can look it up.

Apache works with PHP and, as you recommended, the exec() command seems to work well. I've tested it with a simple python script, and now I'll have to adapt it, but it shouldn't be too complicated.
I think it's just what I needed.

---

### Post by TheFu on 2023-08-20
_chmod 777_ is for the lazy and ill-informed.  Don't use it. Learn basic Unix permissions. The sooner, the better.  Any tutorial is find. Takes about 45 minutes of deep concentration to learn 90% of it, which is fine for most people.  Only admins and developers need to learn permissions to a deeper level.  Unix permissions and all Unix-like OSes work the same.  chown, chmod, chgrp are the main commands.

I have no recommendations for current tutorials - as I learned most of this stuff 20+ yrs ago. Sorry.

For simple needs, using cgi for external scripts is fine.  But it doesn't scale well.

"Linux server" is an extremely generic term.  99% of my servers don't have any web server on them.  Providing web services is just one of thousands of possible uses for a Unix server.  HTTP and HTTPS are just 2 protocols, there are thousands of others.

---

### Post by SeijiSensei on 2023-08-20
> **leg2027 said:**
> Apache works with PHP and, as you recommended, the exec() command seems to work well. I've tested it with a simple python script, and now I'll have to adapt it, but it shouldn't be too complicated.

There are a couple of different PHP commands to run a program at the OS level. I often use shell_exec() which places the results of the command into a string for later processing. (It's the equivalent of $() or the backtick operator `` in bash.) exec() returns the output as an array. That may be better or worse for you depending on the application.

See also the [manual page for system()]("https://www.php.net/manual/en/function.system.php") for a list of other options like passthru().

---

### Post by leg2027 on 2023-08-21
> **TheFu said:**
> _chmod 777_ is for the lazy and ill-informed.  Don't use it. Learn basic Unix permissions.
I learned the hard way. I should have known better. But as you recommended, I'm going to do it now so I don't make any more mistakes.

> "Linux server" is an extremely generic term.  99% of my servers don't  have any web server on them.  Providing web services is just one of  thousands of possible uses for a Unix server.  HTTP and HTTPS are just 2  protocols, there are thousands of others.         
If there are so many possibilities, I might as well stick with on Apache. It's well documented and since I've done it this time, it should be fine.

> 
I often use shell_exec() which places the results of the command into a string for later processing. 
I've just tested it and it works very well too. But I don't know if it's what I need since my output is a file, and maybe a sentence confirming that the python processing has been done.
I'll look into which php command is best for this purpose.

---

### Post by TheFu on 2023-08-21
> **leg2027 said:**
> I learned the hard way. I should have known better. But as you recommended, I'm going to do it now so I don't make any more mistakes.

I suspect everyone tries to ignore permissions until they don't have any other choice. You are no different.  I know I certainly did the same.  Eventually, I got frustrated that my minimal level of knowledge wasn't sufficient, so I got to a quiet place where I wouldn't be interrupted for an hour, spent 15 minutes working through, not just reading, a Unix permissions tutorial.  Then I spent the next 30 minutes with 3 user accounts in 3 terminals with a mix of groups and created directories and files with every owner, group, and other possible, then added in the different permissions at each level and saw what worked, what didn't work until that "light bulb" went off in my head and I was able to predict 100% which users would have what sort of access and which would have ZERO access.  I don't know any shortcuts.  I didn't really learn the setgid and setuid stuff at this time, which is seldom used, so it isn't really needed.  Also, I didn't learn the sticky-bit (+t) and I've used that perhaps 3 times the last 30 yrs.  A few months later, the setgid came in handy as a group at work needed to have very similar access to the same shared files.  I use the setgid stuff all the time with my media files to allow my user and the media center daemon user to both control the files.

Anyway, spend the time (45min) now to avoid hours, days, weeks, months of frustration.

> **leg2027 said:**
> If there are so many possibilities, I might as well stick with on Apache. It's well documented and since I've done it this time, it should be fine.

Apache is just a web server.  That's 1 protocol out of thousands.  It is the *kitchen sink* version of web servers (they throw in everything), which might seem like a good thing. Only you can decide if that's good or bad.  The more features any software has, the more bugs it has, which makes for more security problems.  Just for learning or on an internal network, apache is fine.  I use it for internal-only websites that I setup before I started using other web servers.

> **leg2027 said:**
> I've just tested it and it works very well too. But I don't know if it's what I need since my output is a file, and maybe a sentence confirming that the python processing has been done.
I'll look into which php command is best for this purpose.

If you don't need a web browser interface, then you don't need a web server, unless you are specifically creating a tool that can be controlled over an HTTPS+REST interface.  Lots of webapps support translation layers for different types of output.  One that I use will generate HTML or JSON or XML or YAML output, just depends on the requested URL. Different templates can be used for different types of browsers - with and without javascript, for bloated browsers or for simplistic mobile device browsers from 2007.  Just depends what is needed.  Because it isn't much extra work to support the non-bloated HTML+JS output and makes testing much easier, I prefer that, though the JSON and YAML output are even easier to validate with testing automation.  

There's an idea of TDD - Test Driven Development.  In it you create the test cases first, then keep running them as you add code. When all the test scenarios finish without errors, then you are done developing.  Of course, this depends entirely on how well your test scenarios cover all edge cases and prevent bogus inputs in a reasonable way.  In testing, about 90% of all testing is for bad data, preventing that from getting far into the system.  People who are just learning to code tend to work on the nominal, perfect data, scenarios.  If their code doesn't prevent out of range or the wrong type of data getting into it, there will be bugs to be found forever.

---

### Post by leg2027 on 2023-08-30
Thank you very much for all this details and advice.

> **TheFu said:**
> spent 15 minutes working through, not just reading, a Unix permissions tutorial.  Then I spent the next 30 minutes with 3 user accounts in 3 terminals with a mix of groups and created directories and files with every owner, group, and other possible, then added in the different permissions at each level and saw what worked, what didn't work

I've just done it because I went on vacation earlier than planned and hadn't done it before. 
I followed your advice by reading both a tutorial on linux permissions, I also learned about groups and users, and by experimenting with different users, groups and permissions. It took me more than 45 minutes, but I think it will be worth the time, as you pointed out.

> If you don't need a web browser interface. 
This is not yet the case. But I should need it soon. So it seems more sensible to use a web server like Apache to avoid having to redo too much.


Have a nice day and thanks again for your help!

---

### Post by TheFu on 2023-08-30
> **leg2027 said:**
> I've just done it because I went on vacation earlier than planned and hadn't done it before. 
I followed your advice by reading both a tutorial on linux permissions, I also learned about groups and users, and by experimenting with different users, groups and permissions. It took me more than 45 minutes, but I think it will be worth the time, as you pointed out.

Two questions to know if you understand enough about normal Unix permissions.

1) If you have 4 users (4 different userids) and they all need to work in the same directory, with the ability to have full read-write, delete, and add permissions on all files below a top level directory, how would you set that up?  Assume a standard Ubuntu user account setup.  Show the 'id' for each user and the 'ls -al' for the top directory and a few files+directories under it. Also, show the commands used to make it.

2) Suppose all 4 of those users need to be webmasters on the system for a static+dynamic website that allows uploads.  How does that change things for permissions?  Assume /var/html/www is the top directory, with  /var/html/www/DL as the directory to accept uploads into and apache used to serve the website. Show the 'id' for each user and the 'ls -al' for the top directory and a few files+directories under it. Also, show the commands used to set it up.

When you can do those 2 things, you'll have 90+% of the useful knowledge for permissions.  If you get stuck, feel free to ask an AI engine, but beware that AI engines make up fake answers more often than people know.  Last week, I asked AI for 2 simple programs. Neither worked.  1 time, the AI magically created a module for the language that doesn't exist and acted like it did.  Building software is so much easier when it doesn't need to actually work.  The other program was close and didn't run, but about 3x larger than my hand-crafted code in the same language.

> **leg2027 said:**
> This is not yet the case. But I should need it soon. So it seems more sensible to use a web server like Apache to avoid having to redo too much.


Apache is complex and without a doubt one of the most complex servers for anything that there is.  It is hard for a beginner to master, beyond just the simplest stuff for a static website.  OTOH, you can have a simple webserver with 1 line of code in most scripting languages that will display an index and allow files to be made available over HTTP.   Don't confuse "popular" with "best".  Those seldom align.

Of course, if you plan to be an admin or webmaster, then you'll need to have at least a passing (very light) knowledge of apache.

---

### Post by leg2027 on 2023-08-30
This is for first exercise:

> (base) leg@leg:/$ sudo mkdir common_folder
[sudo] password for leg: 
(base) leg@leg:/$ sudo groupadd common_group
(base) leg@leg:/$ sudo chown :common_group /common_folder
(base) leg@leg:/$ sudon usermod -aG common_group leg
Command 'sudon' not found, did you mean:
  command 'sudo' from deb sudo (1.9.9-1ubuntu2.4)
  command 'sudo' from deb sudo-ldap (1.9.9-1ubuntu2.4)
Try: sudo apt install <deb name>
(base) leg@leg:/$ sudo usermod -aG common_group leg
(base) leg@leg:/$ sudo usermod -aG common_group user1
(base) leg@leg:/$ sudo usermod -aG common_group user2
(base) leg@leg:/$ sudo usermod -aG common_group user3
(base) leg@leg:/$ groups user1
user1 : user1 mon_groupe work newgrp common_group
(base) leg@leg:/$ sudo chmod 770 /common_folder
(base) leg@leg:/$ sudo chmod -R 770 /common_folder
(base) leg@leg:/$ id leg
uid=1000(leg) gid=1000(leg) groups=1000(leg),4(adm),20(dialout),24(cdrom),27(sudo),30(dip),46(plugdev),122(lpadmin),135(lxd),136(sambashare),1002(mon_groupe),1006(work),1007(newgrp),1008(common_group)
(base) leg@leg:/$ id user1
uid=1001(user1) gid=1001(user1) groups=1001(user1),1002(mon_groupe),1006(work),1007(newgrp),1008(common_group)
(base) leg@leg:/$ id user2
uid=1002(user2) gid=1004(user2) groups=1004(user2),1002(mon_groupe),1006(work),1007(newgrp),1008(common_group)
(base) leg@leg:/$ id user3
uid=1003(user3) gid=1005(user3) groups=1005(user3),1002(mon_groupe),1006(work),1007(newgrp),1008(common_group)
(base) leg@leg:/$ ls -al /common_folder
ls: cannot open directory '/common_folder': Permission denied
(base) leg@leg:/$ sudo ls -al /common_folder
total 20
drwxrws---  3 root  common_group 4096 Aug 30 17:39 .
drwxr-xr-x 23 root  root         4096 Aug 30 17:28 ..
drwxrwx---  2 root  common_group 4096 Aug 18 21:23 Documents
-rwxrwx---  1 root  common_group   60 Aug 20 11:49 exec.php
-rwxrwx---  1 user1 common_group    6 Aug 30 17:39 text.txt
(base) leg@leg:/$ sudo ls -al /common_folder/Documents
total 8
drwxrwx--- 2 root common_group 4096 Aug 18 21:23 .
drwxrws--- 3 root common_group 4096 Aug 30 17:39 ..
(base) leg@leg:/$ sudo ls -al /common_folder/exec/php
ls: cannot access '/common_folder/exec/php': No such file or directory
(base) leg@leg:/$ sudo ls -al /common_folder/exec.php
-rwxrwx--- 1 root common_group 60 Aug 20 11:49 /common_folder/exec.php


I tested one of the users, who was able to manipulate files and folders in the common_folder. 

> 2) Suppose all 4 of those users need to be webmasters on the system for a  static+dynamic website that allows uploads.  How does that change  things for permissions?  Assume /var/html/www is the top directory, with   /var/html/www/DL as the directory to accept uploads into and apache  used to serve the website. Show the 'id' for each user and the 'ls -al'  for the top directory and a few files+directories under it. Also, show  the commands used to set it up.
I'm not sure I fully understand this question. Should group members be able to read/write/execute and others be able to read and execute in the DL folder?


To tell the truth, I just want a simple website, an HTML page where the user enters data (latitude, longitude) in a text box for example, and where a php script downloads updated files on a public server. These files are then used by a python script (which only works under linux) which produces a json file that the user downloads on his computer.
And it's no more complicated than that: no traffic to manage, no accounts, no databases... And yet I've been working on it for months and still haven't achieved a functional result. But it should come.
I've only worked on simple HTML-CSS-JS web pages before, which is why I'm having trouble getting the hang of it.

---

### Post by SeijiSensei on 2023-08-30
First, can you create the needed file using PHP? If the entries are latitude and longitude, the HTML form would look like
```

<form action="<?=$_SERVER['PHP_SELF'?>" method="post">
Enter latitude: <input type=text name='latitude'>
Enter longitude: <input type=text name='longitude'>
<input type=submit>
</form>

```
Pushing the submit button will send the results back to this same script based on the "action" parameter in the <form> tag. You would need PHP code earlier in this script that checks whether the automatically generated array [$_REQUEST]("https://www.php.net/manual/en/reserved.variables.request") exists and, if so, generates the required file. The entries will be stored in $_REQUEST['latitude'] and $_REQUEST['longitude']. Use these values to write your file with the [fwrite()]("https://www.php.net/manual/en/function.fwrite.php") function.

```

<?php
if (!empty($_REQUEST)) {
   $lat=$_REQUEST['latitude'];
   $long=$_REQUEST['longitude'];

   $data=$lat.','.$long.'\n';

   $transfer_file='/path/to/transfer_file';
   fopen($transfer_file,'w+');
   fwrite($transfer_file,$data);
   fclose($transfer_file);

   if (file_exists($transfer_file)) { 
      echo "<h3>Your file has been created!</h3>";
   }
}
?>

```
Note that I explicitly add a return ("\n") to the end of the data line. The webserver "user," www-data on Ubuntu, must have write privileges in the directory where $transfer_file will be stored.

---

### Post by TheFu on 2023-08-30
> Q1: If you have 4 users (4 different userids) and they all need to work in the same directory, with the ability to have full read-write, delete, and add permissions on all files below a top level directory, how would you set that up? Assume a standard Ubuntu user account setup. Show the 'id' for each user and the 'ls -al' for the top directory and a few files+directories under it. Also, show the commands used to make it.
I should have said, root cannot be the owner when you are done.

> **leg2027 said:**
> This is for first exercise:

I tested one of the users, who was able to manipulate files and folders in the common_folder. 
Because you used 'quote tags', not 'code-tags', the commands 
a) didn't look correct
b) didn't get included when I quoted ... which means I can't point out what was wrong.

BTW, it is clear you didn't show all the commands, since the directory has a setgid flag enabled, but no command sets it.  I don't see how Documents/ would have the permissions shown, nor the parent from the commands shown.

BTW, /tmp/ is a good place to test stuff like the out.  It is kinda the purpose for /tmp/ to exist, besides to drop temporary files and download files you know won't be needed long term.

> **leg2027 said:**
> 
> Q2: 2) Suppose all 4 of those users need to be webmasters on the system for a static+dynamic website that allows uploads. How does that change things for permissions? Assume /var/html/www is the top directory, with /var/html/www/DL as the directory to accept uploads into and apache used to serve the website. Show the 'id' for each user and the 'ls -al' for the top directory and a few files+directories under it. Also, show the commands used to set it up. 

I'm not sure I fully understand this question. Should group members be able to read/write/execute and others be able to read and execute in the DL folder?
The permissions should be whatever is required for uploads to be possible by the apache process through a web-upload.  It would also be best if only the webmasters can see the files, never anyone going through the upload process via the website.

> **leg2027 said:**
> To tell the truth, I just want a simple website, an HTML page where the user enters data (latitude, longitude) in a text box for example, and where a php script downloads updated files on a public server. These files are then used by a python script (which only works under linux) which produces a json file that the user downloads on his computer.
And it's no more complicated than that: no traffic to manage, no accounts, no databases... And yet I've been working on it for months and still haven't achieved a functional result. But it should come.
I've only worked on simple HTML-CSS-JS web pages before, which is why I'm having trouble getting the hang of it.

There's no such thing as a "simple website" when a scripting language is used that accepts user input.  There is all sorts of user input that can break into a system, gain access to system information, or worse, call commands on the box. All input through a webpage shouldn't be trusted.  Just because you provide a webpage that does some validation, that doesn't mean the person accessing it is using the same client-side validation.  They don't need to.  Always do validation on the server side - always.  Client-side validation is good for good users and provides feedback quickly, but it doesn't provide security.

From a webapp security standpoint, don't allow the webapp to write to any of the code it runs under. Only allow read for that and only allow the webapp to write places is absolutely must have write access, nowhere else.  It would be nice of the world was made of 100% nice people.  After the first 10,000 attempted hacks in 1 day, you'll understand better why being paranoid is best.

---

### Post by leg2027 on 2023-08-31
> **SeijiSensei said:**
> First, can you create the needed file using PHP? If the entries are latitude and longitude, the HTML form would look like
Pushing the submit button will send the results back to this same script based on the "action" parameter in the <form> tag. You would need PHP code earlier in this script that checks whether the automatically generated array [$_REQUEST]("https://www.php.net/manual/en/reserved.variables.request") exists and, if so, generates the required file. The entries will be stored in $_REQUEST['latitude'] and $_REQUEST['longitude']. Use these values to write your file with the [fwrite()]("https://www.php.net/manual/en/function.fwrite.php") function.

Thank you very much!
I've just tested the code on Apache and it works perfectly. After that, there's not much left to do to get everything linked, and the website should be up and running in the next days.

By the way, I've been able to use what I've learned about permissions to give www-data the necessary permissions. Does that sound right to you? Here's what I've done:
```
sudo chown -R www-data:www-data /var/www/html/domain/public
sudo chmod -R 755 /var/www/html/domain/public

```
I specify that /var/www/html/domain/public is where all my website files are located.

> 
I should have said, root cannot be the owner when you are done.
Is that what you're asking:
```
(base) leg@leg:/$ cd /common_folder
bash: cd: /common_folder: Permission denied
``` 
Of course, the other users always have access to the common folder.

> BTW, it is clear you didn't show all the commands, since the directory  has a setgid flag enabled, but no command sets it.  I don't see how  Documents/ would have the permissions shown, nor the parent from the  commands shown.
But I seem to have put everything in. But I manually moved the exec.php file and the Documents folder in the GUI. 


> 
here's no such thing as a "simple website" when a scripting language is  used that accepts user input.  There is all sorts of user input that can  break into a system, gain access to system information, or worse, call  commands on the box. All input through a webpage shouldn't be trusted.   Just because you provide a webpage that does some validation, that  doesn't mean the person accessing it is using the same client-side  validation.  They don't need to.  Always do validation on the server  side - always.  Client-side validation is good for good users and  provides feedback quickly, but it doesn't provide security.

From a webapp security standpoint, don't allow the webapp to write to  any of the code it runs under. Only allow read for that and only allow  the webapp to write places is absolutely must have write access, nowhere  else.  It would be nice of the world was made of 100% nice people.   After the first 10,000 attempted hacks in 1 day, you'll understand  better why being paranoid is best.         
For the moment, I'm not concerned about the security of my website. It's still far from being public and available to all. I'll do that later, of course, otherwise it might be too hard to do everything at once.
I'll take note of your advice when the time comes to make my web application available to everyone.

---

### Post by TheFu on 2023-08-31
> **leg2027 said:**
> For the moment, I'm not concerned about the security of my website. It's still far from being public and available to all. I'll do that later, of course, otherwise it might be too hard to do everything at once.
I'll take note of your advice when the time comes to make my web application available to everyone.

Tacking on security after the fact usually isn't easy and often requires a complete re-design.

I wouldn't have www-data be the owner for any directories or files that aren't specifically required to have that ownership used by apache.  Root would be better.  Heck, another random account would be better.

It was just the exercise where I didn't intend for root to be the owner.  In the real world, there are many times when root should be the owner, especially for websites.  I run a few of my websites using read-only mounts, so that none of the files seen by the users or web server can be modified at all, regardless of the permissions.

The _principal of least permissions necessary_ is core to Unix.  [https://en.wikipedia.org/wiki/Principle_of_least_privilege](https://en.wikipedia.org/wiki/Principle_of_least_privilege)  Learning that sooner will make you a better developer and webmaster.

---

### Post by leg2027 on 2023-09-02
> **TheFu said:**
> 
I wouldn't have www-data be the owner for any directories or files that aren't specifically required to have that ownership used by apache.  Root would be better.  Heck, another random account would be better.

I've changed the permissions so that user1 is the owner. Let me know if this seems correct.
```
(base) leg@leg:~$ getfacl /var/www/html/domain/public
getfacl: Removing leading '/' from absolute path names
# file: var/www/html/domain/public
# owner: user1
# group: www-data
user::rwx
group::r-x
other::---
```

As you recommended, I also have an *uploads* folder in which www-data can also write.

---

### Post by TheFu on 2023-09-02
I've been an admin for 30 yrs and needed to use setfacl/getfacl twice in all that time.  Please stick to normal permissions as shown by **ls -l**. It makes your life easier.  I really once in the early 2000s, someone use ACLs on some files. Nobody noticed, but the owner didn't have any writes. Took far too long for the team to figure that out.

Be aware that ACLs exist, but avoid using them.  Just because a feature exists, that doesn't make using it a good idea.  Another example is **xattrs**.  Do you use those too?  There are many more uses of xattrs than ACLs, by far, but next to nobody ever uses them.

And BTW, not all backup software will honor ACLs or xattrs, so beware.

---

### Post by leg2027 on 2023-09-02
I saw this Ubuntu command on the Internet. It seems more synthetic to me. 
I don't use xattrs. 
I'm a Linux beginner so I take what comes, I don't necessarily know whether to use it or not.

Here's what it looks like with ls -l:
```
(base) leg@leg:~$ sudo ls -l /var/www/html/domain/public
total 211672
-rwxr-x--- 1 user1 www-data 24659598 Sep  1 16:32 05H_SP1.grib2
-rwxr-x--- 1 user1 www-data 19025580 Sep  1 16:31 05H_SP2.grib2
-rwxr-x--- 1 user1 www-data 24601402 Sep  1 16:33 06H_SP1.grib2
-rwxr-x--- 1 user1 www-data 18555093 Sep  1 16:31 06H_SP2.grib2
-rwxr-x--- 1 user1 www-data 24468404 Sep  1 16:32 07H_SP1.grib2
-rwxr-x--- 1 user1 www-data 18790668 Sep  1 16:34 07H_SP2.grib2
-rwxr-x--- 1 user1 www-data 24244026 Sep  1 16:35 08H_SP1.grib2
-rwxr-x--- 1 user1 www-data 18924380 Sep  1 16:35 08H_SP2.grib2
-rwxr-x--- 1 user1 www-data 24670183 Sep  1 16:35 09H_SP1.grib2
-rwxr-x--- 1 user1 www-data 18731167 Sep  1 16:35 09H_SP2.grib2
-rwxr-x--- 1 user1 www-data      635 Apr 30 17:36 download2.php
-rwxr-x--- 1 user1 www-data      633 Apr 30 17:35 download.php
-rwxr-x--- 1 user1 www-data       60 Aug 20 11:49 exec.php
-rwxr-x--- 1 user1 www-data     1068 Aug 31 17:53 fwrite.php
-rwxr-x--- 1 user1 www-data       29 Aug 20 11:49 hello.py
-rwxr-x--- 1 user1 www-data     6290 May  1 11:12 index.html
-rwxr-x--- 1 user1 www-data     5652 Sep  1 16:29 indexTest2.html
-rwxr-x--- 1 user1 www-data     7277 Sep  1 16:02 indexTest.html
-rwxr-x--- 1 user1 www-data       17 Aug 19 20:14 info.php
-rwxr-x--- 1 user1 www-data      411 Apr  8 10:59 style.css
-rwxr-x--- 1 user1 www-data       35 Aug 31 17:54 text.txt
drwxrwx--- 2 user1 www-data     4096 Sep  2 11:10 uploads
```

---

### Post by TheFu on 2023-09-02
And there we have a perfect demonstration of a problem.  With ACLs on files, there's just a tiny character sign on the file in any directory listing that there has been ACLs set which can completely contradict the normal, expected, UNIX permissions we all use constantly.  That sign being displayed is dependent on the _file system_ supporting it AND it being enabled.  

```
$ ls -al
total 44
drwxrwxr-x   2 tf   tf    4096 Sep  2 16:11 ./
drwxrwxrwt  35 root root 36864 Sep  2 16:11 ../
-rw-rw-r--   1 tf   tf       0 Sep  2 16:11 t-no-acl
-rw-rwxr--**[COLOR="#FF0000"]+ [/COLOR]** 1 tf   tf       0 Sep  2 16:11 t-w-acl
tf@hadar:/tmp/test$ getfacl t-*
# file: t-no-acl
# owner: tf
# group: tf
user::rw-
group::rw-
other::r--

# file: t-w-acl
# owner: tf
# group: tf
user::rw-
user:root:rw**x**
group::rw-
group:root:rw**x**
mask::rwx
other::r--
```

So, if this were a script file, t-w-acl, and you were in the group, tf, you'd think that you have execute permissions, but you don't.  Not good. How long would that take to track down if you didn't connect the '+' character at the end of the permissions string with ACLs?

I created a tiny 1-line script inside that file and tried to run it.
```
$ ./t-w-acl
bash: ./t-w-acl: Permission denied
```

The way to check the file system options is through the **mount** command.  
```
$ mount | egrep /tmp   # I'm using grep to avoid all the junk, feel free to look at the full output to see why.
/dev/mapper/vg01-tmp01 on /tmp type ext4 (rw,nosuid,nodev,noexec,relatime,stripe=32)
```
So, for my system, /tmp has some non-standard options. These are for security reasons.  Check your mount options for /tmp. They probably look something like this:
```
$ mount | egrep -w /
/dev/vda1 on / type ext4 (rw,noatime,errors=remount-ro)
```
Security isn't just file permissions. There are lots of layers.  So, if you mount a file system to be secure and don't allow execute permissions, this could make any script there fail to work.  For /tmp/, that's a good idea as once someone hacks into your system, in theory, the only place daemon users can write is under /tmp/ somewhere.  Typically, there first effort will be to download other scripts to a directory deep under /tmp/ *"somewhere"*, then they will use those scripts to try an gain elevated privileged, like sudo or root.  These initial attacks are all automated, so to prevent any foothold, blocking execute on /tmp/ will stop many of their scripts.  There are ways around it.  Blocking device files and setuid-root files in /tmp puts up 2 more barrier.  More barriers are good and for legitimate users, these little things don't have much, if any, impact.

rsync, the way we copy files/directories around and between system, has special options for both acls and xattrs.  Don't forget these options, when they are needed.  From the rsync manpage:
```
        -A, --acls                  preserve ACLs (implies -p)
        -X, --xattrs                preserve extended attributes
```
These are not the defaults or included in commonly used options:
A typical rsync command on the same system would be **sudo rsync -av {source} {destination}**  The -a option typically does all we need, including retaining owner, group, and standard UNIX permissions, but not ACLs or xattrs.
```
        -a, --archive               archive mode; equals -rlptgoD (no -H,-A,-X)
```

Best not to use ACLs, unless there isn't any other solution.

When it comes to web-server files, best to not allow the web-server daemon userid to 
[LIST]
[*]own anything it doesn't absolutely need to own.  
[*]read where it doesn't require it and 
[*]write where it doesn't require it.
[/LIST]
Least privilege that's the goal.

Sorry for going on.

---

### Post by leg2027 on 2023-09-03
Is it really necessary to take so many precautions? It's been a long time since I heard about hacked personal computers.
> then they will use those scripts to try an gain elevated privileged, like sudo or root. 
The password is not enough to protect the use of these commands?

> So, for my system, /tmp has some non-standard options. These are for  security reasons.  Check your mount options for /tmp. They probably look  something like this:
     Code:

 ```
    $ mount | egrep -w /
/dev/vda1 on / type ext4 (rw,noatime,errors=remount-ro) 
```

It's exactly the same thing, yes.


> Best not to use ACLs, unless there isn't any other solution.
I won't use them anymore. Actually, *ls -l* does the job well even if it's a little less synthetic.



Remember that I am new to Linux and I don't necessarily understand everything that was discussed in the previous message, I guess it will take me some time to get to grips with Linux.

Have a good day!

---

### Post by TheFu on 2023-09-03
> **leg2027 said:**
> Is it really necessary to take so many precautions? It's been a long time since I heard about hacked personal computers.

It happens so often that it doesn't make headlines, unless you watch specific news outlets.  If you look in the Security subforum here, there are people who think they've been hacked all the time even when they have disabled wifi and wired networking and bluetooth and live alone.

But as soon as anyone runs a server, security needs jump up a bit.  Then if that system is given access to the internet, security requirements, not just need, jump up.  A new server on the IPv4 internet is found withing less than 10 minutes and added to DBs that look for systems to attempt to crack.

So, if you setup the php to only be access by localhost (127.x.x.x/8), not the LAN IP, then you can mostly not worry about other systems, just local physical attacks.  Your specific risk profile matters.  Crackers love to pwn a Linux system with fast internet.  There are millions of wordpress websites that are hacked on any day.  Most remain that way for a long time because the owner only cares that the system still earns money, not that it is cracked.  

Ever received a spam message from an odd domain that doesn't match the FROM address?  That probably came from a hacked Linux server somewhere.  They started using it to send email and pump as many messages out with URL links that redirect to other hacked Linux systems, before the email spamming is seen and shut down.  Millions of messages can be sent overnight if nobody is watching.  That will get the specific IP address added to a block list. Some block lists are static and some are dynamic.  I use both.  A few times each week, the dynamic block list service I use will block gmail ... for spamming.

> **leg2027 said:**
> The password is not enough to protect the use of these commands?

In the world of security, if you are trying to secure things with passwords, you've already lost the battle.  Use keys and certs, to remove dumb user password mistakes from the equation.

An interesting read, if you aren't aware:
[https://krebsonsecurity.com/2012/10/the-scrap-value-of-a-hacked-pc-revisited/](https://krebsonsecurity.com/2012/10/the-scrap-value-of-a-hacked-pc-revisited/)

Running a server (I'm talking software server, not specifically server hardware) moves you into a different realm of security needs.  We all had to start somewhere and only you can determine when it is enough.  OTOH, the internet is like the wild west and nobody is going to protect you, except yourself.  I'm only so adamant because I've been hacked a few times over the decades. Each time was due to my own ignorance in a different area.  I haven't had a server hacked in over 20 yrs now.  

I had a laptop hacked in 2016. It was running a freshly installed and patched Ubuntu. The install was less than 1 day old.

---

### Post by leg2027 on 2023-09-08
I didn't think hacking was so common. I understand that a few people can be fooled by trivial scams or dubious files, and even then it's still rare. But if you say so, I believe you, even if it escapes me a little.
Would there be more piracy on Linux, where the user (like me) tinkers around a bit without blocking potentially dangerous actions like on Windows for example?

You say there's no one on the Internet to protect us. Antivirus software or security updates are nothing but hot air? I'm not sure it's up to us - well, maybe it's up to me, a cybersecurity neophyte - to protect my computer when a computer program or AI could do it for me. 


But perhaps we're straying a little too far from the original subject. By the way, I use shell_exec regularly and it works perfectly for my needs. I'm getting on with my project and hope I don't get hacked along the way ;)

---

### Post by Holger_Gehrke on 2023-09-08
As TheFu said, it's different when you have a server. You can compare a server to a super market. Getting your stuff taken from your home (your desktop PC) is rare, but shoplifting in a supermarket (data or services taken from your server) is much less rare ...

'Hacking' in this context usually means making carefully crafted requests to the server (software) that make it do things you didn't expect when configuring it. This is normally done automatically by software and at high volume - thousands of requests to thousands of servers per second. First step is finding a server, second step is identifying what services it's running (for example you make a request on port 80 and get a response; so there's a web server there; so now you try to figure out which one and in which version; once you know that you can try known exploits against that specific version of that specific software).

Antivirus can only protect you against threats the maker of the software knows about. Yes, there are AV programs that have various kinds of heuristics for identifying suspicious code, but those are best known for their high number of false positives. And malware is usually not the real problem on a server; once the attackers have control of your server, they are going to make it do just what it was doing anyway - but instead of serving your data it will serve theirs or serve your data (the part of it not meant for the public) to them or it will do things for them (like for example running their attack software to find the next round of victims or mining some digital currency or ...).

The same goes for security updates.  They fix problems, but before a problem can be fixed it must be found and it usually takes some time to write a fix. So there's a gap between an exploit becoming known and a fix becoming available. 

Holger

---

### Post by TheFu on 2023-09-09
> **leg2027 said:**
> I didn't think hacking was so common. I understand that a few people can be fooled by trivial scams or dubious files, and even then it's still rare. But if you say so, I believe you, even if it escapes me a little.
Would there be more piracy on Linux, where the user (like me) tinkers around a bit without blocking potentially dangerous actions like on Windows for example?

You say there's no one on the Internet to protect us. Antivirus software or security updates are nothing but hot air? I'm not sure it's up to us - well, maybe it's up to me, a cybersecurity neophyte - to protect my computer when a computer program or AI could do it for me. 


But perhaps we're straying a little too far from the original subject. By the way, I use shell_exec regularly and it works perfectly for my needs. I'm getting on with my project and hope I don't get hacked along the way ;)

If you place a server on the internet, available to anyone, you will quickly see thousands, perhaps hundreds of thousands of "malformed" requests.  A few of those are innocent, but the majority are other computers looking for weaknesses.  The barrier to entry for certain types of programs written in certain languages is very low, so neophyte programmers are an easy target.  Never trust any inputs to your server. Validate everything, regardless of prior client-side validation performed.  It is a common hacking technique to replay requests, but have those modified to do things the server creator didn't intend.

Programmers can't be worried just about having their server work. They also need to worry about bogus inputs making their server do things they didn't intend.

---

### Post by mrmonteith on 2023-12-03
I've been working with Apache and PHP on Ubuntu since 2015.  I recently installed WSL2 on my Windows box so I could play around with converting some of our old web applications to updated OS, PDO db drivers for IBM and MySQl, etc.  Feel free to message me if you want to know more.  I organize my links and also save OneNotes on a ton of stuff.  If I don't have an answer I probably at least can point you in the right direction.

---

