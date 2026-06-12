---
title: "programming ap with built-in file browser (like dreamweaver)"
date: 2006-07-09
forum: Programming Talk
---

### Post by pixelterra on 2006-07-09
I'm trying to convert over to linux completely for the second time now. The first time failed b/c I couldn't find a replacement for dreamweaver or photoshop.

Is there an ap for hand-coding programmers that contains a built-in remote file-browser and supports multipe synced "sites" similar to dreamweaver for ubuntu? Ideally open-source (kinda assumed, I guess).

I've checked out bluefish but the remote remote-local syncing (if available) doesn't jump out at me. I think it isn't there. 

Please say there is something in the ubuntu world! 

All help welcome

---

### Post by ynef on 2006-07-09
You can mount remote locations so they appear as local folders -- ideally, the application shouldn't know the difference. Try the "Connect to server..." option in the menus.

Your two requested apps, Dreamweaver and Photoshop, are the two apps that most people feel that they can never (fully) replace. You might have luck with running them in Wine ("Wine is not an emulator", but what it *doesn't* emulate is Windows), or perhaps (I don't know what Dreamweaver does, except I think it's a WYSISYG web site editor) with nvu.

---

### Post by pixelterra on 2006-07-09
I don't want to edit remote files, but edit them locally (safer) and push an "upload" button that puts them where they belong on the server (i.e. in the proper directory). Dreamweaver allows you to store ftp information for many sites and syncs the remote root with a specified folder on your local machine. It then knows where to "put" the local file (based on its location) on the server, and which server, when you hit the "upload" button. 

I don't use dreamweaver for its wysiwyg props. But I've been searching for 5 years. I once found an editor with a nice site management component, but it f***ed up the php (and all scripting) by re-formatting the html, adding doctype and a bunch of other garbage. 

I just don't see why this is so hard or so much to ask. 

Anyone?

---

### Post by mehaga on 2006-07-09
Try Quanta Plus. Of course, be carefull and test it before you use it on something real. If you don't need WYSIWYG editting, you'll probably like it.

peace

---

### Post by pixelterra on 2006-07-09
Thanks for the recommendation. I've now tryied quanta, but it doesn't let me keep a copy locally. It only edits remotely, which isn't safe or smart. I need to make sure things work on my local server before going live. 

Maybe I'm not seeing the site management tools properly. 

Any other programs out there? NVU has good site management tools, but alas, destroys all coding...

---

### Post by wmcbrine on 2006-07-10
I edit in a simple text editor, and upload with scp. I have a tiny script with the right parameters, so it's just "./up filename.html". I have an "up" script in each directory of my local mirrors.

If you only have ftp access to your host, you can probably do the same with something like ncftpput.

---

### Post by oldmanstan on 2006-07-10
another thing to think about (i don't know how complex your sites are) is using a shell script to upload the files. i just maintain a really simple blog so i wrote a script that just uploads every php file to the server when run. obviously this would be insanely inefficient with more than just a few files (i only have a few so it's fine) but you could have the script check file dates before uploading.

i'm not an expert on this so i couldn't tell you how exactly but i'm pretty sure it's possible.

basically you could mount the remote file system as mentioned in one of the responses above, then write a script that would move files from your local system to the other "local" system (the remote system) based on their date of last modification (which is pretty much what dreamweaver does from my recollection).

---

### Post by pixelterra on 2006-07-10
These "home made" upload scripts are a good idea, and I had thought of them before. Only thing is I'm not much of a bash programmer. Also my sites are for clients, and I can't really afford to experiment with their data. Currently I am maintainign or actively developing about 30 php-driven sites. 

I maintain all of the ftp data in dreamweaver and maintain local copies of everything and run a testing server on my local machine (that way I can work offline when nec.) When I need to modifiy a file, I open it, make the change and press ctl+sh+u and the file goes to the right server in the right place. Not only that, I can have multiple files open from multiple sites, and press ctl+sh+u and they will all go to the right place. It's  not a question of uploading a whole site all the time, as so many people seem to be thinking. 

At this point, the only option I see is to find a separate application that syncs sites, but it would decrease my productivity by an unacceptable rate. Too bad I can't "make the switch".

---

### Post by oldmanstan on 2006-07-10
yeah, i mean, if you really wanted to you could do it with the proper scripts (after all, dreamweaver does it, so it's certainly possible with the right code)

however, since time and productivity are issues and you (like myself) are not a scripting guru it is probably for the best to continue using dreamweaver until a reasonable alternative becomes available on linux

there was a thread somewhere on these forums a few months back about what it meant for linux to be "ready for the desktop" or something along those lines and that is exactly the general conclusion i got out of it. linux is ready for the desktop, as long as your desktop doesn't involve certain things that are as-yet unavailable :)

---

### Post by Raavea on 2006-07-10
I've been dabbling with Nvu, and I think it has the feature you're after.

 Will report back when I've finished my current website project and tested it out ;)

Usually I use Gedit or Screem, but the one-click upload sounds good, and I'd heard Nvu sported most of the Dreamweaver-y bells and whistles, so I'm playing about with it. Can't stand WYSIWYG, but haven't figured out how to make it auto-open in plain-text yet.

ETA:
> **pixelterra said:**
> ...
I do not need the wysiwyg features of dreamweaver. But I can't really live without the built-in ftp remote/local synced site management features. Nvu has site management but it destroys all scripting and reformats (adds doctypes) html. It's a monster. 
...
 You're kidding? *looks aghast*
 It'd kill all my pretty sites! I wanted this feature now I own over twenty sites, and got Nvu 'cause I heard it had it. But Crikey!

I've been using Gedit and Screem, but Screem's upload whatsit is something I haven't fiddled with...

---

### Post by mehaga on 2006-07-13
OK, if you don't like Quanta, I'll have to offer something better :) 

I am working on a web page now and I am using Eclipse. With ftp/webdav plugin it will upload files you choose to the server (it isn't smart enough to remember username and password, it seems :S). With WTP plugin, and JSEclipse plugin, you'll have a very nice editor for HTML, Javascript and CSS. It will have syntax highlighting, code completion... If you need to work with php, get PHPEclipse plugin.
It may take some time to configure and get familiar with, but it's probably worth it.

Peace! :)

---

### Post by Note360 on 2006-07-13
Bluefish is a good web editor (its not WYSIWYG though) and as for photoshop try Gimp if you have not already. Gedit is good for basic stuff and I hear good things about gPHPedit for PHP.

---

### Post by oldmanstan on 2006-07-13
yeah, vekaz is right, try eclipse. it's a great IDE "thing" (it's not really an IDE, but it looks and smells like one).

only caveat, it helps to have a pretty speedy computer, i have a athlon-xp 1800 with 512 of ram and it runs fast but only barely, if i have too much else going on it slows eclipse down quite a bit.

---

### Post by baumer1122 on 2006-07-16
> **pixelterra said:**
> Thanks for the recommendation. I've now tryied quanta, but it doesn't let me keep a copy locally. It only edits remotely, which isn't safe or smart. I need to make sure things work on my local server before going live. 

Maybe I'm not seeing the site management tools properly. 


Quanta definitely does have this functionality. I use it all the time. It is a little confusing though. When you create a new project, choose **Local** protocol under the server settings. I usually don't change any of the defaults (and ignore the templates and toolbars directories). Once you have created the project, right click on the root level of the project and click Rescan Project Folder to have Quanta display your existing local files.

When you are ready to upload, right-click on any folder, file, or the project itself and choose Upload... this will let you create an ftp (or even better sftp) connection to upload your files.

---

### Post by wmcbrine on 2006-07-16
BTW, when I say I upload with a script, I mean, it's hardly worthy of the name. Here's an example:

scp $1 $2 $3 $4 $5 $6 $7 $8 $9 wmcbrine/@/pdcurses.sourceforge.net:/home/groups/p/pd/pdcurses/htdocs

(Take out the slashes around the '@' sign; I put them there to keep the board from tagging it as an email address.) That's the contents of "up" in one of my website directories. (Usage: "./up index.html")

---

