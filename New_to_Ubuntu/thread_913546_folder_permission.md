---
title: "folder permission"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by sfong15 on 2008-09-07
I guess this is really a dumb question so I ask it here.

I'm working in a 8.04.1 server, did this 'adduser --ingroup users' then and granted ALL=(ALL) ALL by visudo.

Now when I logged in as new user, not root, when I create a new folder and chmod 777 to that folder will root has same permissions?

I found that if I do that as root it's OK but as new user with 'sudo' then it's not OK.

---

### Post by iaculallad on 2008-09-07
> **sfong15 said:**
> I guess this is really a dumb question so I ask it here.

I'm working in a 8.04.1 server, did this 'adduser --ingroup users' then and granted ALL=(ALL) ALL by visudo.

Now when I logged in as new user, not root, when I create a new folder and chmod 777 to that folder will root has same permissions?

I found that if I do that as root it's OK but as new user with 'sudo' then it's not OK.

The root has always the 777 attribute on all folders regardless of what user you are. On the point that doing sudo with a command is not OK? Actually it is, since you are invoking a command to give you a "root-like" privilege.

---

### Post by Xiong Chiamiov on 2008-09-07
What exactly is not ok with invoking the command with sudo, as opposed to being root?

---

### Post by sfong15 on 2008-09-08
Thanks for the reply, I'm trying to install LEMP on a VPS server, followed their wiki here [http://wiki.slicehost.com/doku.php?id=get_started_with_your_new_ubuntu_slice](http://wiki.slicehost.com/doku.php?id=get_started_with_your_new_ubuntu_slice)

Since I'm not geeks so my newbie questions there hasn't been answered.

I'm trying to find out what I did wrong, briefly
(1) first attempt, logged in and setup LEMP as root, mkdir a folder under webroot (/var/www/nginx-default/) and php served OK from domain.com/folder/
(2) rebuilt server, created new user, granted all privilege as root, logged in as new user, did exactly as in (1) above but this time Nginx server gave me '403 forbidden' error at domain.com/folder/?

I suspect it's a permission problem causing this.

So I thought if '--ingroup' is really necessary when using 'adduser' before reading this wiki page I have been using just 'adduser <username>' (login as root is no good as a rule)

Also from this wiki [http://wiki.slicehost.com/doku.php?id=ubuntu_slice_notes](http://wiki.slicehost.com/doku.php?id=ubuntu_slice_notes)
it says 'adduser --ingroup <username>' adds 'non-privileged' user.   If 'sudo' is to enable user to do things as root, privileged or not doesn't mean anything, does it?

Perhaps this last questions isn't for this forum, I would be grateful for some pointers to setup subdomain for a LEMP server.   I just managed to setup LEMP using fastcgi from lighttpd to serve php5 but setting up subdomain under nginx is quite different from apache2 that I know little bit of.... this is making me mad.

---

### Post by graben3 on 2008-09-08
i'm pretty sure privileged user means a user that can do SUDO no ?

---

### Post by graben3 on 2008-09-08
> (2) rebuilt server, created new user, granted all privilege as root, logged in as new user, did exactly as in (1) above but this time Nginx server gave me '403 forbidden' error at domain.com/folder/?


You installed everything as root... so logically your "domain.com/folder" must be chown to the user you logged into :

sudo chown -hR myusername:myusername /somedir_path_to_mydomain_com/folder

That would do it...

If not,

type sudo apt-get install su

and try this :

su
chown -hR myusername:myusername /somedir_path_to_mydomain_com/folder

I hope this helps.

also... you can try :

sudo chmod -R 0755 /somedirpath_mydomaincom/folder

sudo chmod -R a+x /somedirpath_mydomaincom/folder

---

### Post by sfong15 on 2008-09-09
> **graben3 said:**
> i'm pretty sure privileged user means a user that can do SUDO no ?

Agree, but the wiki I quoted did also this 'visudo, <username> ALL=(ALL) ALL', therefore non-privileged doesn't mean a thing?

---

### Post by graben3 on 2008-09-09
What you are doing with this line :

visodu <username> ALL=(ALL) ALL

Is giving the same privilege to a user as the ones ROOT has... 
I dont understand why you keep asking if there is no difference between a privileged and a non privileged user ?

> 
adduser --ingroup users <username>
visudo, <username> ALL=(ALL) ALL
/etc/ssh/sshd_config, PermitRootLogin no
/etc/init.d/ssh reload


That wiki must be wrong... This is a PRIVILEGED USER

That tutorial only write this line for ROOT in sudoers file :

[http://ubuntu-tutorials.com/2007/03/01/allowing-limited-sudo-access-with-visudo/](http://ubuntu-tutorials.com/2007/03/01/allowing-limited-sudo-access-with-visudo/)

---

### Post by graben3 on 2008-09-09
> **sfong15 said:**
> this time Nginx server gave me '403 forbidden' error at domain.com/folder/?

I suspect it's a permission problem causing this.


I Had this error with apache. This was caused by apache running as some user (may be nobody) and not having read permissions for "others" for that file.

If the server has to read a file in a folder, make sure that folder has the execute bit set because the server wont be able to list the folder if not set.

Just post the output of the commands here :

ls -l /var/www/nginx-default
ls -l /var/www/

here so we can check your file permissions...

---

### Post by sfong15 on 2008-09-09
> **graben3 said:**
> I Had this error with apache. This was caused by apache running as some user (may be nobody) and not having read permissions for "others" for that file.

If the server has to read a file in a folder, make sure that folder has the execute bit set because the server wont be able to list the folder if not set.

Just post the output of the commands here :

ls -l /var/www/nginx-default
ls -l /var/www/

here so we can check your file permissions...

ls -l /var/www/nginx-default gives

-rw-r--r-- 1 root root 383 aug 30 50x.html
-rw-r--r-- 1 root root 151 aug 30 index.html
drwxrwxrwx 6 root root 4096 sep wp

ls -l /var/www/ gives
-rw-r--r-- 1 root root 3574 sep 9 index.lighttpd.html
drwxr-xr-x 3 root root 4096 sep 9 nginx-default

but now I have already rebuilt server and installed LEMP again as root.   Found that it may be a default rewrite rule problem with nginx which i have yet to learnt, i.e. when url = domain.com/wp/ I get 403 error, when url = domain.com/wp/index.php it works OK!    Somehow I need a rewrite to direct folder to default index php or html files.

---

### Post by graben3 on 2008-09-09
> **sfong15 said:**
> ls -l 

/var/www/nginx-default gives

-rw-r--r-- 1 root root 383 aug 30 50x.html
-rw-r--r-- 1 root root 151 aug 30 index.html
drwxrwxrwx 6 root root 4096 sep wp

ls -l /var/www/ gives
-rw-r--r-- 1 root root 3574 sep 9 index.lighttpd.html
drwxr-xr-x 3 root root 4096 sep 9 nginx-default

but now I have already rebuilt server and installed LEMP again as root.   Found that it may be a default rewrite rule problem with nginx which i have yet to learnt, i.e. when url = domain.com/wp/ I get 403 error, when url = domain.com/wp/index.php it works OK!    Somehow I need a rewrite to direct folder to default index php or html files.


FIRST :

All your files belongs to root... that should not be the case first

sudo chown -hR youruser:youruser /var/www/nginx-default

If that did not work, try this :

sudo chown -hR nobody:nogroup /var/www/nginx-default

and tell me if it changed something


SECOND : 

The rewrite rules :

[http://brainspl.at/nginx.conf.txt](http://brainspl.at/nginx.conf.txt)

See this part : 

```

  # check for index.html for directory index
      # if its there on the filesystem then rewite 
      # the url to add /index.html to the end of it
      # and then break to send it to the next config rules.
      if (-f $request_filename/index.html) {
        rewrite (.*) $1/index.html break;
      }


```

Im pretty sure you just copy this again just below to make it look like this :

      if (-f $request_filename/index.html) {
        rewrite (.*) $1/index.html break;
      }

      if (-f $request_filename/index.php) {
        rewrite (.*) $1/index.php break;
      }


That seems to be what your are looking for.

Just add those 3 lines of code to your nginx.conf file

---

### Post by graben3 on 2008-09-09
Sorry...forgot something important in the previous post :

in a terminal :

sudo chmod 0755 /var/www/nginx-default

that will allow people to read your wp folder

For the url mydomain.com/wp to work as expected your need to put the code lines I showed you in nginx.conf and
also run this command. 

The parent folder has to be executable to allow listing this one.

Since the wp folder has +x to all users, it can list the files in it and find index.php
But the nginx-default does not have the x attribute so the wp folder is not found if you type mydomain.com/wp

Also, user accounts on a server usually have a public_html folder in their root account. 

Typically the root folder of users account on a web server has 655 permissions i think and the public_html folder in it is 755 (not verified information...this is what I remember only...)

---

### Post by graben3 on 2008-09-09
> 
but now I have already rebuilt server and installed LEMP again as root. Found that it may be a default rewrite rule problem with nginx which i have yet to learnt, i.e. when url = domain.com/wp/ I get 403 error, when url = domain.com/wp/index.php it works OK! Somehow I need a rewrite to direct folder to default index php or html files.



In the ls-l output you posted you don't even have an index.php.

And im guessing that since your /var/www/nginx_default folder belongs to root your are actually writing files in it as root... so all the files you put there will belong to root which is not really good since you'll have to work as root to do that

---

### Post by sfong15 on 2008-09-09
> **graben3 said:**
> In the ls-l output you posted you don't even have an index.php.

And im guessing that since your /var/www/nginx_default folder belongs to root your are actually writing files in it as root... so all the files you put there will belong to root which is not really good since you'll have to work as root to do that

Thanks again Graben3.   I have rebuilt my server now, the 3rd time, I know  it wasn't a permission problem.   I did 99% right first time, 2nd time fixed that 1% but I overlooked something in the first 99%.

My first build, fastcgi and nginx can serve php from domain.com/wp/ folder, everything works except that I was still looking to how to serve few domains using vhosts.   I did everything as root.

2nd build, I created new user to do exactly the same thing (not quite, later found out), I omitted one step which was adding index.php (in addition to index.htm and index.html) to the nginx.conf so folders are not serving files when url is just domain.com/wp/ (should have used a index.htm and a index.php to test site)  I got 403 error because nginx won't list files in directory.   That was one important step I omitted.

3rd build, I worked as root.   It's all working except that I have yet to make the nginx rewrite/redirect to work, i.e. when url is domain.com it would serve files from domain.com/wp/ folder.

My next goal would be virtual host serving say
my.domain.com -> files in /var/www/nginx-default/wp/
sub.domain.com -> files in /var/www/nginx-default/folder/

Ultimate goal, linux script to deploy LAMP or LEMP installation automatically, e.g. user can manually mkdir folder structure of their choice (folder name, structure, where log/error logs are placed etc...) then scp a installation script from local PC to server to run ... everything happens automatically (with error log to debug of course)!    May be someone has done this already years ago!

Anymore tips?

Great community, thanks to all here.

---

### Post by graben3 on 2008-09-10
For the virtual hosts, i suggest think link... 

I read it and it seems pretty well explained and simple. Try it and tell me if this helped :

[http://articles.slicehost.com/2008/5/16/ubuntu-hardy-nginx-virtual-hosts](http://articles.slicehost.com/2008/5/16/ubuntu-hardy-nginx-virtual-hosts)

---

### Post by graben3 on 2008-09-10
> **sfong15 said:**
> 

3rd build, I worked as root.   It's all working except that I have yet to make the nginx rewrite/redirect to work, i.e. when url is domain.com it would serve files from domain.com/wp/ folder.


There is a really easy way to do that if you cant find any other :

domain.com/index.php

Content :

header('location: wp/index.php');

save and close !

---

