---
title: "HOW-TO: Set up a Remote Calendar using WebDAV for use with Mozilla Sunbird"
date: 2006-01-19
forum: Outdated Tutorials &amp; Tips
---

### Post by audax321 on 2006-01-19
This tutorial works on Ubuntu and should work on Kubuntu as well as Xubuntu. However, we'll do all the text editing in nano (a console-based text editor) since it should be installed on all *buntus. For nano, after editing a file, to close it push CNTRL+X and it will ask you if you want to save and just respond accordingly.


**Getting Sunbird:**
Mozilla Sunbird is still in development so it may contains bugs, crash, or lost calendar data. You can download the latest version here:
[http://www.mozilla.org/projects/calendar/sunbird/download.html](http://www.mozilla.org/projects/calendar/sunbird/download.html)

The nice thing about it is that there is NO compiling needed. Just put the folder wherever you want and run the 'sunbird' file inside the folder... or better yet make a nice icon pointing to the 'sunbird' file on your desktop or panel.


**Getting a way to access the server:**
If one of the following apply to you, skip this section:
> 
1. You already have a hostname you can use to access the server you will be setting up.
2. You are only going to use this server on your local network and your computer has a static IP (your computer always gets the same IP).
3. You don't have a hostname and don't want one and you are assigned a static IP from your ISP.


If you want to share your calendars/files over the internet, then you need a "permanent" way to get to your server since a dynamic IP from your ISP can change. To get a hostname and setup a script on your computer to update the hostname everytime your ISP changes your IP follow the tutorial here:
[http://ubuntuguide.org/wiki/Dapper#How_to_assign_Hostname_to_local_machine_with_dynamic_IP_using_free_DynDNS_service](http://ubuntuguide.org/wiki/Dapper#How_to_assign_Hostname_to_local_machine_with_dynamic_IP_using_free_DynDNS_service)

If you are going to be only sharing your calendars/files over your local network, you need an IP assigned to you that is not always changing. To do this, log into the router on your LAN and tell it to assign the server you will be using the same IP (called assigning a Static IP).


**Installing the Apache Server:**
To install the Apache Server, open up a Terminal (Applications > Accessories > Terminal) or whatever way works for your desktop:

```

sudo apt-get install apache2

```

Now, you have the option of changing the port your Apache Server runs on. By default it runs on port 80, which is fine if there is only one computer. But if you setup a router to forward all traffic for port 80 to one computer on your network... the internet on your other computers will go bye-bye. To change the port:

```

sudo nano /etc/apache2/ports.conf

```

In the file add the following line, where "port" is whatever port you would like to use (e.g. Listen 9999) and then exit (CNTRL+X) and save:

```

Listen port

```

NOTE: Make sure to forward traffic on this port to your server if you have a router!!!


**Enabling the WebDAV modules:**
To enable the WebDAV modules, open up a Terminal (Applications > Accessories > Terminal) or whatever way works for your desktop:

```

sudo a2enmod
dav (enter)
sudo a2enmod
dav_fs (enter)

```


**Setting up the WebDAV folder and the user:**
This will make a WebDAV folder at: /var/www/davhome

To create the folder, open up a Terminal (Applications > Accessories > Terminal) or whatever way works for your desktop:

```

mkdir /var/www/davhome
chgrp www-data /var/www/davhome
chmod 775 /var/www/davhome

```

Next to create the user, input the following command changing the last "username" part of the command to the username you would like to use (obviously make a note of the username and password you create):
```

htpasswd -c /var/www/davhome/.DAVlogin username

```


**Tell Apache where the folder is and to use it:**
To tell Apache to use WebDAV, open up a Terminal (Applications > Accessories > Terminal) or whatever way works for your desktop:

```

sudo nano /etc/apache2/mods-enabled/dav_fs.conf

```
[INDENT]*Thanks to **henriquemaia** for the suggesting to edit this file instead of /etc/apache2/httpd.conf*[/INDENT]

Paste the following into the file (make sure the Terminal window is selected and use the Paste command in the Edit menu (not CNTRL+V - nano won't recognize it):

Change "username" (two instances) to the username you created above. Also, the DAVMinTimeout is optional... it just sets the how long Apache should lock the file after it is accessed... I don't use it and haven't had a problem, but then again I only have one computer accessing the calendar at any time.

```

DAVLockDB /tmp/DAVLock
#DAVMinTimeout 600

<Location /davhome/>
        Dav On

        AuthType Basic
        AuthName username
        AuthUserFile /var/www/davhome/.DAVlogin

        <LimitExcept OPTIONS>
                Require user username
        </LimitExcept>
</Location>

```

Hopefully you didn't exit and save yet because you have some more options. With the way the file is setup above you will be prompted for a username/password everytime you read or save a file using WebDAV. 

If you don't want to be asked a password when you read a file change the first LimitExcept line to:

```

<LimitExcept GET OPTIONS>

```

If you don't want to be asked a password when you save a file (write) change the first LimitExcept line to:

```

<LimitExcept PUT OPTIONS>

```

If you don't want to be asked a password when reading or writing (not recommended unless you want to make the calendar completely public) change the first LimitExcept line to:

```

<LimitExcept GET PUT OPTIONS>

```

Okay, now you can exit and save.


**Restart Apache**
This step is very important so that Apache recognizes the changes you made!

Open up a Terminal (Applications > Accessories > Terminal) or whatever way works for your desktop:

```

sudo /etc/init.d/apache2 restart

```


**The address to the server:**
Now you can either create a new calendar in Sunbird and tell it to put it on your server or publish an existing local calendar to the WebDAV folder. Just go to the calendar tab in Sunbird and right-click in the list of calendars or right-click on an existing calendar in the list.

The address format you would enter for the remote calendar is as follows:

```

http://server_ip_or_hostname:port_if_not_80/davhome/filename_for_calendar.ics

```


**Other Items to Note:**

If you place an exisiting calendar file directly in /var/www/davhome, you should change the group and the rights on this file as follows:

[INDENT]```
sudo chgrp www-data /var/www/davhome/filename_for_calendar.ics
sudo chmod 644 /var/www/davhome/filename_for_calendar.ics
```
*[INDENT]Thanks to **bnj** for this information.[/INDENT]*[/INDENT]


If Sunbird does NOT create a new .ics file, do the following and point Sunbird to that file as if it is an existing calendar:

[INDENT]```
sudo touch /var/www/davhome/filename_for_calendar.ics
sudo chgrp www-data /var/www/davhome/filename_for_calendar.ics
sudo chmod 644 /var/www/davhome/filename_for_calendar.ics
```
*[INDENT]Thanks to **NobodySpecial** for this information.[/INDENT]*[/INDENT]


If I left anything out let me know and I'll add it, but that should be it. :)

---

### Post by bnj on 2006-03-30
That is great! Thank you a hundred times for this tutorial. I followed it step by step and now I am happy.

Two additions:
[LIST]
[*]If you place an exisiting calendar file directly in your directory /var/www/davhome, you should change the group and the rights on this file just as you did for the directory davhome. That is:
```
sudo cp /paht/to/my/existing/calendar.ics /var/www/davhome/calendar.ics
chgrp www-data /var/www/davhome/calendar.ics
chmod 775 /var/www/davhome/calendar.ics
```
[*]Sunbird, at its current version (0.3alpha1) is quite buggy. [Lightning]("http://www.mozilla.org/projects/calendar/lightning.html") seems to work slightly better. Those intersted can also try KOrganizer.
[/LIST]

---

### Post by Dromio on 2006-03-30
Thanks for the step-by-step tutorial.  I'd done this long ago with debian, but hadn't tried again with ubuntu.

I'm using Lightning and when I try to publish my calendar, I get "405 Method not allowed".  It never asks for a username or password.  

My apache access log shows the "PUT" request from thunderbird, and the error log doesn't show anything unusual.  What could I be doing wrong?

---

### Post by audax321 on 2006-04-01
[QUOTE=Dromio]Thanks for the step-by-step tutorial.  I'd done this long ago with debian, but hadn't tried again with ubuntu.

I'm using Lightning and when I try to publish my calendar, I get "405 Method not allowed".  It never asks for a username or password.  

My apache access log shows the "PUT" request from thunderbird, and the error log doesn't show anything unusual.  What could I be doing wrong?[/QUOTE]

Well the good news is that if your apache server is showing the PUT request it's connecting properly. There are only two things that I can think of could be causing your problem:

1. When you go to File > New > Calendar and create a new remote calendar, are you using the WebDAV protocol. I know the CalDAV protocal, for one won't work with the above how-to, and additionally has a bug that prevents it from displaying a username/password dialog.

2. Is your URL formatted correctly (maybe it's accessing the Apache server, but not the davhome folder):
http://<IP or hostname>:PORT/davhome/calendar.ics

I just tried it after downloading a fresh copy of thunderbird and installing the Lightning extension and didn't experience any of those problems. Double-check the file/folder permissions and make sure they have the correct owners and permissions.

EDIT: Okay I reread your post and started thinking maybe it you were trying to publish an existing calendar to the server. But, again, when I tried it that way it worked fine.

---

### Post by henriquemaia on 2006-06-07
[quote=audax321]Well the good news is that if your apache server is showing the PUT request it's connecting properly. There are only two things that I can think of could be causing your problem:

1. When you go to File > New > Calendar and create a new remote calendar, are you using the WebDAV protocol. I know the CalDAV protocal, for one won't work with the above how-to, and additionally has a bug that prevents it from displaying a username/password dialog.

2. Is your URL formatted correctly (maybe it's accessing the Apache server, but not the davhome folder):
http://<IP or hostname>:PORT/davhome/calendar.ics

I just tried it after downloading a fresh copy of thunderbird and installing the Lightning extension and didn't experience any of those problems. Double-check the file/folder permissions and make sure they have the correct owners and permissions.

EDIT: Okay I reread your post and started thinking maybe it you were trying to publish an existing calendar to the server. But, again, when I tried it that way it worked fine.[/quote]

Thanks for this HowTo. I got my dav working with this.

Just a note: when **Tell Apache where the folder is and to use it** you should use the file **/etc/apache2/mods-enabled/dav_fs.conf** to do that. It works both ways, but this makes it easier to clear out modifications when you disable the module.

---

### Post by NobodySpecial on 2006-09-02
I used the Mozilla Sunbird client, but it didn't like the fact that no .ics file existed yet.  So I did this:
```
sudo touch /var/www/davhome/calendar.ics
sudo chmod 666 /var/www/davhome/calendar.ics
```
Then directed Sunbird to the file /davhome/calendar.ics and all is well.  :D 

And BIG thanks to audax321 for helping me get this going!!!

---

### Post by dcherryholmes on 2006-09-27
Does anyone know of some software that could run server-side and send out announcements via email, whether anything is running client-side or not?

---

### Post by LotsOfPhil on 2006-10-02
I followed this thread and got the calendar to work. The only thing I had to differently was to chmod things 777. This is because my folder with the webserver on it is formatted as vfat. You can't chgrp vfat.

---

### Post by enboig on 2007-02-20
This instructions didn't work for me. My webdav is running fine (at least I can save documents in the folder using OpenOffice), but not lighting neither sunbird can create calendars. I created one myself following the "touch" way, but It didn't work. Any hint of how to search for a solution?

UPDATE: I discovered that if I put just de url with no file when creating the calendar ([http://192.0.0.97/davhome](http://192.0.0.97/davhome)) it creates files ICS automatically for evey event; but when I restart the lighting all the events are gone from calendar (but the files are there)

---

### Post by Sprinker on 2007-04-14
Howdy all,

I am implementing a solution at my workplace that involves me setting up a webdav server.  I found this tutorial, and I thought that I had found the jackpot :D What I discovered, that I can not for the life of me get this to work on a virtual hosts configuration.  What I have is one server on a single static IP which is serving to the Internet.  Employees who are offsite, need to be able to access the webdav server to gain access to their files and such.  For some reason, according to my clients requirements, they want their employees to access their files by the address dav.company.com, which then points to the directory of /var/webdav on the filesystem.

Any ideas appreciated.

Cheers,

Sprinker :popcorn:

---

### Post by NobodySpecial on 2007-04-14
Sprinker - Maybe this is too simple, but did you try:
```
sudo ln -s /var/www/davhome/calendar.ics /var/webdav
```

---

### Post by Sprinker on 2007-04-15
> **NobodySpecial said:**
> Sprinker - Maybe this is too simple, but did you try:
```
sudo ln -s /var/www/davhome/calendar.ics /var/webdav
```

Actually, thanks for the reply, I will try it now and I will get back to you. :o 

Cheers,

Sprinker :)

---

### Post by viniosity on 2007-05-23
These instructions were very helpful, but I have a follow-up question.

I was hoping to set this up for multiple people to access and publish.   I went ahead and added a new username/password using the htpasswd command and then also modified my dav_fs.conf file to reflect that new username, but I'm still getting authorization errors.  Is there another place that the password is set?


EDIT: Ok, the new username/password took (though I had rebooted earlier so no idea why it works all of a sudden).  But the underlying goal of having multiple users/passwords here is still eluding me. Anyone?

---

### Post by viniosity on 2007-05-23
> **viniosity said:**
> These instructions were very helpful, but I have a follow-up question.

EDIT: Ok, the new username/password took (though I had rebooted earlier so no idea why it works all of a sudden).  But the underlying goal of having multiple users/passwords here is still eluding me. Anyone?

To answer my own question, I ended up adding to the require user:

```

        <LimitExcept GET OPTIONS>
                Require user user1 user2
        </LimitExcept>

```

Not sure if there's a better way to do it, but there you go.

---

### Post by kwilliam on 2007-05-26
On [another thread](http://ubuntuforums.org/showthread.php?p=2726196), we've discussed a problem where you can log in, but cannot upload or edit any files on the server.  Something the starting post doesn't mention is that the DAV lockfile has to exist - Apache apparently won't make it for you.  
```
DAVLockDB /tmp/DAVLock
```
is used in the example, although it appears that
```
DAVLockDB /var/lock/apache2/DAVLock
```
Is the default now.
After you set up the config file, make sure the lockfile exists by doing
```
$ cd /var/lock/apache2     #or cd /tmp, depending on which you used.
$ sudo touch DAVLock
$ sudo chown www-data:www-data DAVLock
```

---

### Post by haaglin on 2007-08-06
Thanks for this guide! 

I was getting a "403: Forbidden" error all the time, so i added this into the /etc/apache2/mods-enabled/dav_fs.conf file, and now it works. don't now if this is the correct way, so let me know if there is a better method.. 

```

....
Alias /davhome /var/www/davhome
<Location /davhome/>
...
```

---

### Post by fradav4 on 2007-08-31
I'm using Ubuntu 7.04 (not sure if it makes a difference).

I created a WebDAV server using the guide provided on this post.  I believed everything was working successfully because I was able to subscribe to my remote calendar from Sunbird and add an event.  When I attempted to add a second event however, I received an error.

Error Number: 0x0
Description:  Publishing the calendar file failed
                     Status code: 412: Precondition Failed


```
(2) No such file or directory:  The precondition(s) specified by the "If:" header did not match this resource.  At least one failure is because: an entity-tag was specified, but the resource's actual ETag does not match.  [412, #0]
```



It seems as though my file becomes locked after I edit it once and becomes read only.  Any ideas on what the problem could be?  Thanks

---

### Post by Smartin on 2007-11-26
> **audax321 said:**
> This tutorial works on Ubuntu and should work on Kubuntu as well as Xubuntu. However, we'll do all the text editing in nano (a console-based text editor) since it should be installed on all *buntus. For nano, after editing a file, to close it push CNTRL+X and it will ask you if you want to save and just respond accordingly.

If I left anything out let me know and I'll add it, but that should be it. :)

audax321,

Thanks for this tutorial!

I got things working and can publish a test calendar just fine. (Although I can't 'unpublish' it for some reason...)

I have a question though: Why can't I mount the Dav folder as a disk on my OSX box? 

I get a username/password challenge but then I get a 'username or password is incorrect' error. They *are* correct because I can publish a calendar correctly.

I have a dav folder on my OSX box and this mounts as a disk as expected on another OSX box but why doesn't the dav folder on my Ubuntu box do the same?

Any thoughts on this one?

Thanks!

Simon

---

### Post by Smartin on 2007-11-26
> **Smartin said:**
> audax321,

Thanks for this tutorial!

I got things working and can publish a test calendar just fine. (Although I can't 'unpublish' it for some reason...)

I have a question though: Why can't I mount the Dav folder as a disk on my OSX box? 

I get a username/password challenge but then I get a 'username or password is incorrect' error. They *are* correct because I can publish a calendar correctly.

I have a dav folder on my OSX box and this mounts as a disk as expected on another OSX box but why doesn't the dav folder on my Ubuntu box do the same?

Any thoughts on this one?

Thanks!

Simon

Hi...

Ok I can answer my own question although I'm not exactly sure what I have done... Such is the way of Newbs...

I started from scratch and have written this note to myself:

```

To create user folder: (change 'user' to the username you desire)
sudo mkdir /var/www/user
sudo chgrp www-data /var/www/user
sudo chmod 775 /var/www/user

To create the user password (change 'UserAbove' to the same name you used above)

sudo htpasswd -c /var/www/UserAbove/.DAVlogin username 
Change 'username for the user you want. Give password when prompted

Then create restrictions to folder:

Edit sudo nano /etc/apache2/mods-enabled/dav_fs.conf

Paste in: (change 'UserAbove' to the same name you used above)

DAVLockDB /tmp/DAVLock
#DAVMinTimeout 600

<Location /UserAbove/>
        Dav On

        AuthType Basic
        AuthName username
        AuthUserFile /var/www/UserAbove/.DAVlogin

        <LimitExcept OPTIONS>
                Require user UserAbove
        </LimitExcept>
</Location>

Restart apache
sudo /etc/init.d/apache2 restart

```

There is one weird things with this: You will notice that I haven't got the 'PUT/GET' etc options in 'LimitExept' above. I still don't have to enter a password when reading or writing once I am in the folder.

Anyway... I hope this helps someone. I now *seem* to have a webdav server where I can create password protected folders for individual users and have them mount as external disks in OSX, iDisk style.

Awesome.

Simon

---

### Post by look2 on 2008-04-21
Sorry for bumping this thred but I have som problems with charset.

the ics file is saved using utf-8, right? 
I have some problemes opening the ics file via google using the webdav server. I'm from Sweden and using som speciall chars, like åäö, and they won't show up correctly in google. 

Is this some kind of charset problem? Is there something wrong with my settings, or can't google handel this characters in a ics file. 

I have tried to google for it, but haven't found anything.

---

### Post by leillo1975 on 2008-04-21
Hello everybody

I have a apache server running with webdav in a computer with ubuntu (192.168.0.221), and, with my computer (Ubuntu 7.10), I tried to create an .ics calendar with sunbird. When I create a remote calendar in this server ([http://192.168.0.221:999/davhome/](http://192.168.0.221:999/davhome/)), it shows a message that the calendar was created succesfully. 

When I create the first event, Sunbird shows in the calendar, but, when I create the second or more, Sunbird don't show it, and the calendar in the /var/www/davhome/ is not created. I try to make It with the commands:

```
sudo touch /var/www/davhome/filename_for_calendar.ics
sudo chgrp www-data /var/www/davhome/filename_for_calendar.ics
sudo chmod 644 /var/www/davhome/filename_for_calendar.ics
```

This don't work. I tried to modify dav_fs.conf like kwilliam reports, but don't work.

Ahhh, the error in the Sunbird's Error Console is the following:

```
Error: [Exception... "Component returned failure code: 0x80040111 (NS_ERROR_NOT_AVAILABLE) [nsIHttpChannel.requestSucceeded]"  nsresult: "0x80040111 (NS_ERROR_NOT_AVAILABLE)"  location: "JS frame :: file:///home/leo/Escritorio/sunbird/js/calICSCalendar.js :: anonymous :: line 363"  data: no]
Archivo de origen: file:///home/leo/Escritorio/sunbird/js/calICSCalendar.js
Línea: 363
```

Someone can Help me please (my ugly boss wants kill me)

Note: Sorry, my English is very bad, I'm from Spain

---

### Post by leillo1975 on 2008-04-22
Nobody can help me?

---

### Post by evilghost on 2008-05-30
> **fradav4 said:**
> I'm using Ubuntu 7.04 (not sure if it makes a difference).

I created a WebDAV server using the guide provided on this post.  I believed everything was working successfully because I was able to subscribe to my remote calendar from Sunbird and add an event.  When I attempted to add a second event however, I received an error.

Error Number: 0x0
Description:  Publishing the calendar file failed
                     Status code: 412: Precondition Failed


```
(2) No such file or directory:  The precondition(s) specified by the "If:" header did not match this resource.  At least one failure is because: an entity-tag was specified, but the resource's actual ETag does not match.  [412, #0]
```



It seems as though my file becomes locked after I edit it once and becomes read only.  Any ideas on what the problem could be?  Thanks

Thoughthis question is rather old I will answer it for historic value since I encountered it in my 6.06 LTS to 8.04 LTS update.

Essentially, you can use the FileETag configuration directive for Apache2 to disable ETag.  It works well on this end.

```

<Location /dav>
		FileETag none
		Dav On
		AuthType Basic

```

---

