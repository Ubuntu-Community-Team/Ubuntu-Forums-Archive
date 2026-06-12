---
title: "How to move Joomla.zip file/unzip it in directory"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by Lakeside on 2008-11-05
Well, I`ve learned a few more Linux things, but still having probs.  Most people are advising that I place my joommla site into  var/www/joomla...  so I created a folder `Joomla` after www. Then,  I wanted to extract my zipped Joomla 1.5 package just downloaded (on the desktop) into this new Joomla folder, so when I go to localhost backslash joomla, I will see the installation page (my holy grail, yay lol).  but I get error messages, it (archive manager program) won`t send the files there: checkdir error:  cannot create /var/www/joomla/administrator
                 unable to process administrator/.
checkdir error:  cannot create /var/www/joomla/administrator
I can unzip the Joomla package file(Joomla_1.5.7....zip) into the desktop directory just fine (now I have tons of files all over my desktop lol). The file has to be already in the directory/folder you want it unzipped into, but I can`t seem to move this file using `mv` command, I get errors with that (saying no such file etc.). Can this be done?  Thanks for any help^(ps. need to do this with command line, mouse doesn`t click on icons right. thanks

---

### Post by Bölvaður on 2008-11-05
I think it is wrong owner of the folder. I think when I had webpage /www was owned by root and possibly the next level of direcotries.
So you just need to change the user.

if your mouse would work I'd tell you to run nautilus under root, like "gksudo nautilus"

you will be quicker.

sudo chown [yourusername] /www/joomla

check if it works now.
you might need to change user rights.
check them by typing ls -l /www/
and change them by chmod 766 /www/joomla for an instance, run chmod --help  or google cheatsheets about how to use chmod.

---

### Post by Lakeside on 2008-11-05
Thanks for the great tips and quick reply. I`m off to try it now- crossing my fingers big time! I had foolishly assumed I had power over the joomla folder, as I was the one who `created` it, but didn`t consider I would need to check the ownership of www.  I am logged in as `superuser` but yes, I do have to use `sudo` for things, so I guess the root is not enabled. thanks again

---

### Post by Lakeside on 2008-11-05
Just tried it, I did this: sudo chown bo***y /www/joomla
[sudo] password for b*****y:  and got this:
chown: cannot access `/www/joomla': No such file or directory (what I usually get, but I know it is a real file, as I can see it in the file browser in var/www/joomla!
And when I try this:  b****dy@b***dy-desktop:/var/www/joomla$ ls -l /www
ls: cannot access /www: No such file or directory
b****dy@b***dy-desktop:/var/www/joomla$ sudo chmod 766 /www/joomla
chmod: cannot access `/www/joomla': No such file or directory
I tried these commands with and without the parenthesis around user name, and with without spaces ie) username/www  or username /www and ls -l  or ls-l, still got same thing. 
*edit* (sory for long post!) finally got this:
 b****y@b****dy-desktop:/var/www$ ls -l
total 4
drwxr-xr-x 2 root root 4096 2008-11-04 22:39 joomla
...now, what am I to do with this lol
It would seem you are right, the folder is there but www (which is where most people put the website? so it is protected? and probably is root) won`t let me write to it, or to the folders placed therin, like `joomla`, which is why, when I tried downloading the joomla zip file there, it only ended up in `temp` (although I had changed Firefox download default to go to var/www/joomla) This is very very slowly sinking in...

---

### Post by gandaran on 2008-11-05
your problem is a bit confusing, but if it's just that you want to move files from desktop to /var directory you can do it with *gksu nautilus* this opens a nautilus root windows with permission to do anything or use the *sudo mv * command, to use this command it's best you move those files from desktop to your user/home folder first or cd the terminal to desktop first before running the command.

---

### Post by Lakeside on 2008-11-05
Yes, my problem IS a bit confusing (and driving me insane :) ). I can`t use the gui for this- I wish- as my mouse has issues so...I`m having to work around all this, and a noob to linux. I just tried to move the file, as you suggested, to the home directory (please tell me if I did it wrong, or if I just don`t have permission, and need to chown something, though I don`t really know how!)  
b****dy@b*****y-desktop:~/Desktop$ mv Joomla_1.5.7-Stable-Full_Package.zip /home
mv: cannot move `Joomla_1.5.7-Stable-Full_Package.zip' to `/home/Joomla_1.5.7-Stable-Full_Package.zip': Permission denied

---

### Post by Lakeside on 2008-11-05
Please excuse my frustration, and I am extremely grateful to this forum and all the people that don`t have to help...but do! I just don`t understand when the terminal can tell me: 
 -desktop:/var/www$  chmod 766 /www/
chmod: cannot access `/www/': No such file or directory ,
when that same directory (www) is staring me in the face, I am IN that directory, grrr. Same thing when I go into the joomla directory, and try the chown. I have to change ownership or permissions for the www folder, but it won`t let me because I don`t have permission? catch-22?

---

### Post by gandaran on 2008-11-05
if you cannot just drag the files with the mouse then to use the mv command first you have to cd to desktop in terminal if the files are on desktop
first thing to type in terminal **cd /home/user/desktop** change the user to your usermane

---

### Post by Bölvaður on 2008-11-05
ok I suggest you doing the same as I did. I probably told you how I had it (might not though.. Im lazy)

leave /www as it is, but make new folder under it like /www/myfolder
I think it is best to navigate to /www and begin:

cd /www
sudo mkdir myfolder
chown username myfolder    (add sudo if you dont have rights any more)
mv Joomla myfolder/   (you might need to use full paths if you arent in correct directory)

From what I can see, this should do it.



*added*
ðe most important þing is to have correct paþs (paths), if you are in same directory as ðe file or folder you can use ðe name of ðe file, or directory/ (/ to indicate it is a directory) or an absolute paþ (path) which can be used anywhere, no matter in what directory you are in. Ðat always begins wið / and ðen /www/jack'sStuff for an instance

---

### Post by kurtymckurt on 2008-11-05
Ok here's what seems to be your problem. Instead of doing 
```
ls -l /www/
```

try doing 
```
ls -l www/
```

the slash in front of www means that you're looking for the folder www in the / folder. That's not what you're looking for. You want ```
ls -l /var/www/
``` which would be more correct since var/ exists in /. Does this help or make sense?

/ is considered a directory, so when you put it in the front it thinks you're trying to use an absolute path! :)

---

### Post by Joeb454 on 2008-11-05
To unzip with the command line install unzip ;)

```
sudo apt-get install unzip
```

---

### Post by Lakeside on 2008-11-05
to gandaran: thanks, it`s good to have an alternate way to change dir, I like your path way (I had been using  cd /dir for example) it let`s me know exactly where I am/going :)  Bölvaður: I don`t think your`re lazy at all!:p you read all my awful, long posts didn`t you? I really appreciate your help, and your suggestion makes a lot of sense, as I think of what I did when I created that `joomla` folder after all...silly noob I am, I didn`t `chown username joomla` after mkdir joomla! I would like to name this new folder you mention `joomla` (as I want a folder called that to install joomla from) so first i want to remove the `old` joomla dir and start again. (wish me luck ;)
kurtymckurt:  thanks for catching my mistake with the /www the devil is in the details eh? I have to watch that, as I`m learning my way in the terminal.

---

### Post by Lakeside on 2008-11-05
Thanks Joeb, I have unzip (installed it when I realized unrar wouldn`t do it lol). It actually unzipped the file onto my desktop (so I could see if it would work) but not to www/joomla, for other reasons. thanks
*edit* thanks to everyone`s help and patience, I now have a new Joomla dir (var/www/Joomla) I assigned user`s ownership to (I hope) and have just tried to unzip the joomla..file.zip from the desktop to there. I did this:
b****y@b****y-desktop:~/Desktop$ sudo unzip  Joomla_1.5.7-Stable-Full_Package.zip home/b*****y/var/www/Joomla and got this:

Archive:  Joomla_1.5.7-Stable-Full_Package.zip
caution: filename not matched:  home/b*****y/var/www/Joomla
so I think I have to put the file in there first, and then unzip it, using the mv command....I did this: b*****dy@b*****y-desktop:~/Desktop$ sudo mv Joomla_1.5.7-Stable-Full_Package.zip home/b****y/var/www/Joomla
mv: cannot move `Joomla_1.5.7-Stable-Full_Package.zip' to `home/b****dy/var/www/Joomla': No such file or directory

---

### Post by Lakeside on 2008-11-05
Ok, I still would like to know what I`m doing wrong, why I can`t move the zip file (I`ll learn that later) I finally tried unzip the Jooomla..zip file into the Joomla directory using the archive manager..and this time it worked!! Only thing is now, when I enter 127.0.0.1 (my localhost) I get this: Index of /
[ICO]	Name	Last modified	Size	Description
[DIR]	Joomla/	09-Sep-2008 17:14 	-
[DIR]	myfolder/	05-Nov-2008 13:07 	-
Apache/2.2.8 (Ubuntu) Server at 127.0.0.1 Port 80
which is a start, because at least now it shows the Joomla folder (containint the installation file) but according to Joomla installation guide, I am supposed to be seeing the Joomla installation page (:( so close..) And clicking on that folder, it asks me to open with (I chose to open, not save)  and then gives a `browse` option.
That just brings me to my file browser, and shows all the Joomla folders. But how do I install it? thanks again

---

### Post by Lakeside on 2008-11-05
And yet another post (please bear with me!) I started to read the official Joomla installation guide and realized something. In order to see the Installation page, I have to open an ftp client (like proftp, which I have) and upload the Joomla folder or something...then I will see the installation page when I type in something like [http://www.yoursite.com](http://www.yoursite.com) or [http://yoursite.com/joomla_folder](http://yoursite.com/joomla_folder)

---

