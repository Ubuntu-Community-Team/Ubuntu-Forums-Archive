---
title: "Remotely updating website code"
date: 2008-07-27
forum: Programming Talk
---

### Post by Pc_Madness on 2008-07-27
Hey guys, I have an install of Ubuntu 8.04 with LAPP (Postgresql :p) installed.  I'm trying to build a little update script that works with PHP to allow uploading of new PHP code (basically a 'firmware update') to our little web server.

Basically,
1.PHP recieves the uploaded tar.gz file and puts it somewhere? /var/www/tempfolder/ I spose?
2. execs my updater bash script which extracts it all to a temporary directory
3. The Update Script then calls another bash script inside of the tar called installer, which will then do a heap of little things like delete files/copy files over other files/other random things inside of /var/www/. Oh and also make changes to the database by executing SQL files.

Theres also a C Program on the machine that will run on startup that I'd like to be able to update as well.

Where is the best place to store the Updater Script/C Program so that I can execute/stop/start/delete from PHP? I keep running into permission problems. :\ Can I put it all into /var/ and then run the C Program with the user www-data? As I presume www-data won't have permission to stop a process started by the default login or root. 

Or is this not the right way to go about doing this? :\

Thanks in advance. :)

---

### Post by drubin on 2008-07-27
> 1.PHP recieves the uploaded tar.gz file and puts it somewhere? /var/www/tempfolder/ I spose?

Putting zip files of your code in the webroot is generally a bad idea as they can be downloaded... 

There is already something that can sync your php files/folders It is called rsync (never used it my self because i haven't had the need to but it is very much along the lines of what you are talking about.)
> 
Where is the best place to store the Updater Script/C Program so that I can execute/stop/start/delete from PHP? I keep running into permission problems. :\ Can I put it all into /var/ and then run the C Program with the user www-data? As I presume www-data won't have permission to stop a process started by the default login or root.


First take a look at the file structure of linux to get an idea of where files should be placed.
[http://geek2live.blogspot.com/2007/09/linux-file-structure.html](http://geek2live.blogspot.com/2007/09/linux-file-structure.html)
[http://tldp.org/LDP/intro-linux/html/sect_03_01.html](http://tldp.org/LDP/intro-linux/html/sect_03_01.html)

---

### Post by Pc_Madness on 2008-07-29
> **rubinboy said:**
> First take a look at the file structure of linux to get an idea of where files should be placed.
[http://geek2live.blogspot.com/2007/09/linux-file-structure.html](http://geek2live.blogspot.com/2007/09/linux-file-structure.html)
[http://tldp.org/LDP/intro-linux/html/sect_03_01.html](http://tldp.org/LDP/intro-linux/html/sect_03_01.html)

Cheers. :) I chucked it all in /var/. Seems to be working alright so far. :p

---

### Post by drubin on 2008-07-29
> **Pc_Madness said:**
> Cheers. :) I chucked it all in /var/. Seems to be working alright so far. :p

It would work no matter where you place the executable files.! 

I would rather place it is /usr/local/ 

But try and get a 2nd option about that :)

---

