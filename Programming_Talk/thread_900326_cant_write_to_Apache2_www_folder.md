---
title: "cant write to: Apache2 www folder"
date: 2008-08-25
forum: Programming Talk
---

### Post by ICEcoffee on 2008-08-25
Hi all

I followed:
"http://ubuntuguide.org/wiki/Ubuntu:Hardy#Install_a_LAMP_server_on_a_Desktop"

to install a LAMP server on my Hardy Ubuntu desktop, mainly using this:

> System-->Administration-->Synaptic Package Manager-->
Edit-->Mark Packages by Task-->LAMP server -->Apply


Following on, I found I could not open or write to the index file in: 
/var/www/ 

I notice the permissions are for root only. I did get round this by going to the command line:
sudo gedit /etc/apache2/httpd.conf

what is the correct permission for this folder and how do I set it?

also, can someone direct to a howto or similar, to correctly setup my LAMP environment. (I will want to setup virtualhosts/direcectories too).

Thanks for any help/advice

---

### Post by themusicwave on 2008-08-25
You should look at the chmod command.

Bacically, there are different groups on Linux with file permissions.  They are user, group and others.

User - the owner of the file
Group - users who are in this file's group
Others - everyoen else.

Each of these can Have 3 types of permission:

Read - lets them view the file, but not change it
Write - Change the files contents
Execute - run the file, good for programs/scripts.

With an html file, it is not executable, so that is not an issue. What you want to do is give user RWX permissons and group and others R perimissions.

Use these commands:
chmod u +rwx
chmod go +r
chmod go -wx

check this out for more details: [http://en.wikipedia.org/wiki/Chmod]("http://en.wikipedia.org/wiki/Chmod")

---

### Post by mssever on 2008-08-25
You can use chmod as themusicwave suggested. Alternatively, you can use chown to make your user the owner of that directory: ```
sudo chown -r youruser /var/www
```Or, you can change Apache's DocumentRoot to something more convenient (such as /home/youruser/website).

Just make sure that the user www-data has read access to all your web files. If feasible, also make sure that www-data does NOT have write access to any web files.

---

### Post by jaime256 on 2009-06-19
Since I'm just testing the ubuntu 9.04 server myself and it has no gui I thought I add a little more to this thread. Along with this information, I wouldn't recommend changing the rights to the /var/www directory. Instead what I did was:

1. Create another directory with the mkdir command under /var/www/internet for example.

2. Give write access for the group "other" on this folder. Use the chmod info posted earlier or quoted below.

3. I was able to then copy my html files into this folder. I used gftp which works really great. It's a gui version but once the rights are created you should be able to use the terminal too. If you want to make sure nothing can write to this folder later, just take out the write access on this folder again and you're back to not being able to write anything here. You will need the write access if you want to make any changes though. Just keep this in mind.

4. Now change /etc/apache2/sites-enabled DocumentRoot to /var/www/yourdirectory.

5. Restart the apache server with sudo /etc/init.d/apache2 restart

6. Now type your ip address on the address bar and you should be able to see your website. It took me a while to figure this one out too, but this way you don't go changing all the folder rights, just the one you need. Hope this helps.

> **themusicwave said:**
> You should look at the chmod command.

Bacically, there are different groups on Linux with file permissions.  They are user, group and others.

User - the owner of the file
Group - users who are in this file's group
Others - everyoen else.

Each of these can Have 3 types of permission:

Read - lets them view the file, but not change it
Write - Change the files contents
Execute - run the file, good for programs/scripts.

With an html file, it is not executable, so that is not an issue. What you want to do is give user RWX permissons and group and others R perimissions.

Use these commands:
chmod u +rwx
chmod go +r
chmod go -wx

check this out for more details: [http://en.wikipedia.org/wiki/Chmod]("http://en.wikipedia.org/wiki/Chmod")

---

### Post by Can+~ on 2009-06-19
You can simply do 

chmod -R 750 /var/www/

So now you (the owner) can do anything (rwx:111), the group (apache's www-data) can only read and execute (rwx:101) and everyone else is screwed.

> 4. Now change /etc/apache2/sites-enabled DocumentRoot to /var/www/yourdirectory.

That's not necessary, for example, I've got my www/ folder with multiple folders and I just do [http://localhost/projectx](http://localhost/projectx).

And since we're discussing this (rather old) subject, one thing I notice is that when adding new files to my www folder, it automatically sets me as the owner and group with the default permissions (rw-rw----). I've created a small .sh that changes everything to what I use (750) but is there a way to automatically do it on creation and ONLY in this specific folder?

---

### Post by jaime256 on 2009-06-19
I'm not sure since even though this is old, I'm just testing this. What does the - capital R mean? I'm just using the letters since I find it easier to remember. At least for me and I haven't finished testing it live so I didn't know some things may not show if that's the case. I just couldn't find anything on the web that explained the correct way to do something like this without leaving your server open to anyone changing things.

Oh yeah and number 4 is optional. I don't need to type anything else after the ip so it gets redirected automatically for me that's why I liked it. But we'll see how things are later, once I start using it. I only have one site so I don't need that www rights, at least not yet, but I see what you mean by being the owner of the main www folder and then the rest under it.

I still have to figure out what will work as far as editing the files on there. Any ideas about that? I usually use the desktop with screem and pointed to that share before, but not sure about the new setup.

---

### Post by Reiger on 2009-06-19
Here: -R means recurse: that is &#8220;apply this command not just to this directory, but also to any directories and files `inside' it&#8221;.

EDIT: Altough for the purpose of running your own apache2 test server I'd suggest not mucking about in /var/www; simply use sudo a2enmod userdir to enable userdirs: by default that means anything under ~/public_html.

---

### Post by Can+~ on 2009-06-19
> I'm not sure since even though this is old, I'm just testing this. What does the - capital R mean? I'm just using the letters since I find it easier to remember. At least for me and I haven't finished testing it live so I didn't know something things may not show if that's the case. I just couldn't find anything on the web that explained the correct way to do something like this without leaving your server open to anyone changing things.

-R means recursive, it will go through all the folder hierarchy. 

The permissions should be set to: Allow you (owner) to edit your files (duh), allow apache2 to read the files (group permissions to read) and leave nothing to anyone else.


```
#!/bin/sh

path=/var/www/yourstuff

targets=`find "$path" -type f ! -path "*/.*"`;

for i in $targets
do
	echo "Modifying file $i"
	chmod 640 $i;
	chgrp www-data $i;
done
```

Well, I fixed my script to change permissions:

-It will ignore hidden folders (good, because I was worried about it messing the svn stuff (.svn folders))
-It will only change permissions on files, I had to use "-R 750" to avoid folders having their execute flag turned off (thus rendering them useless), now it can be reduced by one (640).
-Now it changes groups also.

---

### Post by jaime256 on 2009-06-19
Thanks for clarifying guys. I'm taking baby steps trying to understand both the server and apache for now. I use the desktop ubuntu so I have an idea, but I just don't like changing things to make them just work. I like to know why and what's the correct or best way to do it so not to make a mess out of things, but this is just me since I know I can go many different ways to do this. Now that I got the files on the server, what's the best way to go about using say screem html editor on these files? There's no public html folder that I can tell. I thought it was just /var/www for any web files.

Normally the files were on a windows share so I just logged on there with ubuntu and proceeded to edit my files. Not sure with the ubuntu server though. I know I can use nano from the terminal, but what if I need to use say Dreamweaver or anything similar?

---

### Post by jaime256 on 2009-06-30
It's me again. I need a little help understanding something.
I have my nas which works like this. Nas-admin account - user accounts - shares - access works. Shares/folders I can access all of them fine.

Now the ubuntu server is this: Server - server account - smb users file - shares - access to my share folder doesn't work. The folder is under the var/www/folder. As you can see I'm using samba and I can now see my folders in my network neightborhood on the windows test machine I'm using. From looking at the nas they work pretty much the same, except the rights which I'm still not having access.

When I log into the home share, I can now add/delete files since I already added the writable option to the conf file. When I try to open the folder that is shared the system asks for a logon again. I tried all of them, but nothing works. The folder is still owned by root, but has all the wrxwrxwrx so I gave myself write access or i would not have been able to add the files to it. Maybe someone can clarify this stuff for me. I'm trying to understand the whole process of how this works since I should be able to access the folder as I do on the nas and just edit the files directly from there. I hope this makes sense. Any help is appreciated. I already looked at the docs, but that deals with other things and even the faqs link isn't working there on the apache page.

I'm staying away from scripts and anything like that for now until I can make sense of this since this is what most people will normally want to do with their webserver. I do know it's a writes problem but I also added that writable option for that share or folder I created, it just doesn't work in this case.

Worst case, how do I add myself to that folder so I can have rights to it without changing ownership or do you have to change ownership in order to do this? I'm not sure how the writes work on linux so information that can clear this for me is very much appreciated.

---

### Post by lowstand on 2009-07-25
i am having the same issue an also need to setup an ftp but cant seem to find out howto do this evrything i try give me your not allowed to do this denied

---

### Post by austinrutta on 2009-11-03
type in:
"gksudo nautilus" in terminal. it will open up a file browser. Click File System>var>www and drag your files into there

---

