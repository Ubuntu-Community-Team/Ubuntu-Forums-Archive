---
title: "www?strangeness with the phpinfo.php (how to put it in var"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by Lakeside on 2008-11-06
I would like to know what anyone thinks of this. Being really new to all this- web serving, linux etc. it was good to learn and get practice doing all this but...I still didn`t accomplish my objective: put a phpinfo.php fie into var/www, so it would show up at localhost/phpinfo.php, hopefully giving info and shedding some light on my php.ini problem (don`t get me started on that :) ) After getting the simple code online, pasting it in nano, I had to save it in Desktop (nano offered limited save places, and var/www wasn`t one of them). I then tried to move it there from the Desktop (where it was, I checked with `locate phpinfo.php`) using the sudo mv phpinfo.php var/www command..(also /www, www etc.) but it didn`t go there.  It would go to `var` though after I used mv to put it there, showing up in file manager. It would not appear among files/directories in var after the `ls` command. And how it looked in file manager under the var directory was like this: an icon with a blue dot in the center (like the earth) and `www` beside it. But it was the file because clicking it brought me to the `Screem` editor, and showed the php script. ..weird. How come I can`t put it in var/www
and why does it look like that in var? thanks for solving this mystery

---

### Post by Bölvaður on 2008-11-06
:) you forgot to put / in front of your path to indicate that it is from the top level, closest to the root.

so it would be /var/www

otherwise it will check the next level in the direcotry tree that is var (/var/www/var/www does not exist on your computer I would assume :KS)

Im not sure if nano is the best writer you could use, gedit is very powerful when correctly used from what I understand.
Also you should always be able to pick any path to a directory to save in, not only the ones in your bookmarks. You probably type in the absolute path to that location.


hope I was of some help.

---

### Post by Lakeside on 2008-11-06
Bölvaður to the rescue again :) Yes, I keep forgetting about the / and it`s correct use.  This is what I just did, but must be wrong again: -desktop:/var$ sudo mv phpinfo.php /var/www
mv: cannot stat `phpinfo.php': No such file or directory
and I was in the var directory when I did that, and phpinfo.php is in there, according to the file manager (but not in the terminal using the ls command, it does not appear among the files after I do a `ls`)
Same thing with the Documents directory (phpinfo.php shows in the filemanager, but not after ls, and I also can`t move it from there to var/www.  Very strange.
*edit* So, I thought I would check out the editor again, as you made me think.  I do have the gedit, and looking at it again, I can pick my folder so I picked www (and noticed too that www was accidentally where the file name was so I changed it to phpinfo.php and saved as. Then I got this: Could not save the file /var/www/phpinfo.php. You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again. starting to pull out my hair

---

### Post by kernelhaxor on 2008-11-06
Check the permissions on that directory .. May be only root has permissions to create files in that folder.

---

### Post by Lakeside on 2008-11-06
Thanks, I was just starting to suspect that lol. I`m reading up on permissions now, a great site: [http://www.elated.com/articles/understanding-permissions/](http://www.elated.com/articles/understanding-permissions/)  I had assumed that www was ok, because I was able to unzip the Joomla installation package into it. *edit* ok, her is what I get with ls -l in the var directory to check www: drwxr-xr-x  4 root root  4096 2008-11-05 13:07 www

to me it looks like I have all the rights, but maybe I am not seen as root?
*edit* after more digging: I just want to check here first, to see if this is something I should do and then it will work (I hope) go into my ftp program (fireFtp, firefox addon) pick the www dir, permissions, and there is a box to check `suid`, or `set User Id` from what I gather. THEN I should be able to put phpinfo.php in www (what a journey!) Aaagh I did it (couln`t wait) but it doesn`t STAY clicked, I mean, when I check on the folder again in permissions, the box for suid is unticked, so it`s not set, same thing if I put a `4` in front of the number755 (4755) supposed set suid as well. :) :) It worked! Thanks so much! I guess the permission thing in ftp worked, as I was able to move the file
(mv) from Documents to var/www and it`s there, so `localhost/phpinfo.php` yeilds the phphinfo screen..love it when stuff works. Quite the forum you have here, next best thing to going to school, which I can`t do at the moment.

---

