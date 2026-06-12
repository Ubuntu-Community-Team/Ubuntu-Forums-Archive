---
title: "Where should I store my personal files?"
date: 2017-01-09
forum: New to Ubuntu
---

### Post by amirf27 on 2017-01-09
Hi guys. This seems an appropriate place to ask such a question, as it's titled "New to Ubuntu." Let me know if not. I tried asking on Stack Exchange and got my question put on hold as "opinion-based." Never going to use Stack Exchange ever again (same experience with Stack Overflow and was eventually banned), so I hope that as a beginner I can get some help here. I'm sorry, I don't mean to be negative (especially on my first post), but it's just irritating, and I really, really hope I won't have the same negative experience here seeing that this subforum is titled "New to Ubuntu," so it sounds like a perfect place for such a question.

Okay, so basically I'm new to Ubuntu, just moved from Windows. I moved because I'm learning web development and figured Ubuntu would be great as I'm going to use the terminal for things like git and surge. So far I'm liking it. My question is simple (I hope this time it won't be put on "hold" or something like that): I'm really confused as to where I should store my files. I have a folder containing all my web development material and projects that I basically copied from my Windows partition (I have dual boot and can access it from my Ubuntu installation). Right now I have saved it directly in my home directory, as it seemed to be the most intuitive place to save it.

In Windows, I used to have my D: partition dedicated to my personal files, with folders indicating what type of tiles they contain. Is it okay to do the same in Ubuntu but directly in my home directory? Also, do I have to save music files for example in the Music directory? Or photos in the Pictures directory? Can't I do something similar to what I used to do with the D: partition in Windows? How do you save your personal data on Ubuntu, and how would you personally do it (yes I'm actually asking for opinions from more experienced users, I hope the thread won't get deleted for being "opinion-based" or something)?

Thanks in advance!

---

### Post by Dennis N on 2017-01-09
I keep my own files in a separate data partition distinct from the standard home folder. The data partition is mounted at startup by the OS in use so it is ready when needed. In my case, it is on a separate hard drive. This approach useful if you have more than one OS installed as I do. Each can access the same files when it is being used. Also with an OS upgrade, your data is untouched. 

The regular home folder still exists - it is needed as a location of program configuration files, and sometimes I do use it for temporary work and storage (downloads, for example).  

For easy access, I set file manager bookmarks or shortcuts to locations on the data drive. Applications can be set to use the data partition for storage (or they just remember it from your last usage), so it is no problem.

---

### Post by &amp;KyT$0P# on 2017-01-09
If you want to keep it all on the Ubuntu partition, I'd put it all in a subfolder of your home folder.  Generally I use the already-existing "Documents" folder.

You *can* also put it directly in your home folder, as you are doing now.  But then it gets all mixed in with system files for your user account.  To see what I mean, open a Terminal and run these commands -
```
cd ~
ls -lA
```


You also say you have a separate Windows partition that already contains all your personal files.  Are you able to just use that partition in Ubuntu as well?  If so, you might find that easier.

---

### Post by Hadaka on 2017-01-09
Hi, and welcome to Ubuntu.
You will notice that the folders in your home directory all start with an uppercase letter.
This makes them easy to visually see. The majority if not all commands are done in lower case.
So to make your folders behave and function like any of default folders, simply build them in your
home directory. *Example..to make a folder for your photos..In your home directory enter...
```
mkdir My_Photos
```
then you can save or drag and drop your photos to that folder, just like you would any other folder.
Of course to edit,delete or view files...you would enter from the home directory..
```
cd My_Photos
```
*Take note. to completely REMOVE/DELETE all FILES  and the DIRECTORY ..----*Example
```
rm -rf My_Photos
```
*This removes ALL files and the directory of My_Photos.
Be cautious and take your time,think about what you are doing before you press 'Enter'
Linux does NOT ask you "Are You Sure ?" like other operating systems. Linux assumes you would
not have entered the command if you didnt want it executed. Never enter ANY command you don't understand.
There are also endless tutorials online for Linux commands , I would suggest you search them out
and gain more knowledge.
Good luck to you

---

### Post by Impavidus on 2017-01-10
Welcome. I found that this is one of the friendliest on-line communities around and I hope both Ubuntu and these fora.

It's fine to store your files in (subdirectories of) your home directory. It's the only place where you have permission to save files by default. Separate data partitions as mentioned by Dennis N are common too and not very hard to setup. By default you get some directories named Documents, Videos, Downloads and some others.[SUP]1[/SUP] You can use them if you wish, but you're not required to do so and you can delete or rename them or store your stuff somewhere else, whatever you think is most convenient.

There are no hard rules about what can be stored where in your home directory. You are the boss there. There are some guidelines though. Files and directories with a name starting with . are considered hidden and mostly contain personal settings or data for various applications. Some applications expect certain files to be present in certain locations.

[SUP]1[/SUP]: In fact, the names are localised, so on my computer they're called Documenten, Video's and Downloads. Not ideal, as an apostrophe is rather inconvenient in the name of a directory.

---

### Post by 1clue on 2017-01-10
Most Linux forums for a specific distribution are pretty friendly. Certainly with Ubuntu and Gentoo, my two favorites, people welcome questions from people honestly trying to learn something. StackExchange and their group are a bit less friendly than that.

Like in Windows, you have a user home directory.  In Linux that's referred to as $HOME and as ~. Both of these things work on the command line and in most shell scripts. For example, **cd $HOME**, **cd ~** and **cd** all do the same thing: They change to your home directory. The **cd** command in Linux will automatically take you to your home directory if no arguments are passed.

Where documents go is sort of complicated and related to what sort of documents.  In your $HOME directory you'll find folders with uppercase names as mentioned above. Those are recommendations as well as default locations for some apps to look for a certain type of document. Pictures, Music, Downloads, etc are all pretty straightforward.  Documents are for what I call "traditional" documents you work on, like from a word processor.

I'm a developer. So like you, there are other sorts of documents you might not want to have mixed in with your ~/Documents folder.  Here's what I use, **read: These are MY purposes not standard use**:
[LIST=1]
[*]~/src
[LIST=1]
[*]'src' is a traditional source directory for UN*X. For example, /usr/src/linux is where we traditionally keep the kernel source if we have it on our system. 
[*]This is for source which belongs to some other project, which I'm only interested in one branch or version. 
[*]Folders in this folder represent basic projects which build as separate apps or libraries. 
[*]They may or may not have source control. 
[*]Each project is its own entity, requiring nothing from outside its folder to build. 
[*]I have a **hello** project where I just run random experimental stuff to see what works. 
[/LIST]
  
[*]~/ws/<major-version>/<minor version>/
[LIST=1]
[*]I work for a private company. I build software and must support several versions of it. 
[*]We're using grails for development and tomcat as an app server, so keeping that in mind might help you understand. 
[*]The software exists as several plugins and several apps, and in development mode I must often run with all of it "hot" meaning that the app server compiles on the fly with all or several of the projects in the directory. 
[*]**ws** stands for 'workspaces'. This folder in ~ contains all of the workspaces using this complex structure.
[LIST=1]
[*]**<major-version>** is the major version of source checked out, e. g. 5
[LIST=1]
[*]Contains several folders, one for each minor version and possibly extras with a customer name at the end.  e.g. 5.7-acme-rockets 
[*]**<minor-version>** is actually both major and minor, e.g. 5.7 because just seeing the minor version can be easily confused with a major version.
[LIST=1]
[*]This is the 'workspace' folder for some specific version of our software. 
[*]Everything checked out here is either specific to a generic version or the version being built for some specific customer. 
[*]The workspace contains many 'project' folders each of which is either a plugin or an app, all pertinent to a specific version of the software. 
[*]There is a configuration and other files directory here too, for external config files used by the app.
[LIST=1]
[*]I set CLASSPATH='../companyRoot/conf' in the command shell.
[LIST=1]
[*]When I use 'grails run-app' the grails tomcat will be initialized with the above classpath, which means it looks in ../companyRoot/conf for external configuration files to pull in, which will be set up for a specific version's testing or a specific customer for support. 
[*]companyRoot contains all attachments, scripts, whatever that I want to be available to the app being run. It mirrors the setup we have at a customer site. 
[/LIST]
  
[*]There are also 'companyRoot/attachments' and 'companyRoot/scripts' and whatever else we need. 
[/LIST]
  
[*]If the project is being built for production (pretty much only happens on our build box) then there are code signing certificate links and password in the project directory for the specific version as well. They'll be a symbolic link to 'permanent' files elsewhere on the filesystem, to prevent accidental deletion. 
[/LIST]
   
[/LIST]
   
[/LIST]
   
[/LIST]
   
[/LIST]

All these versions are in git, or for the older versions subversion.  This represents about 6 years of development, which is how far our  customer support goes back. Obviously the same project is checked out multiple times. Each version checked out contains the branches from origin as well as the 'production' branch being represented, and development branches for that branch as necessary. It takes a certain amount of care to prevent cross-talk between production branches.

If this were a collection of  independent projects which never needed to be run in a debugger mode  together then I'd just keep everything in the **src** tree  above, because switching from one git branch to another is easy. However  a support call from a customer who we haven't talked to for 3 years  requires fast response, and it's good to have a workspace checked out  with their versions and settings already there in a runnable state.

---

### Post by oldfred on 2017-01-10
I got in the habit of using data partitions when dual booting with XP. Then I had a shared NTFS data partition.
Then when converting from 32 bit to 64bit I just installed a new / (root), but wanted same shared data and then only Linux formatted partition for shared data.
Now install for test or experiment several Ubuntu versions and want same data.

I use a share ext4 partition with all the normal data like photos & documents, but several other folders also.
My /home is tiny, so I keep it in my / (root) partition on SSD, but have very large data partition on HDD.

       The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root) which is a total of 11GB with /home.
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives. 
   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install. 
   [http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by Tadaen_Sylvermane on 2017-01-10
> **Dennis N said:**
> I keep my own files in a separate data partition distinct from the standard home folder. The data partition is mounted at startup by the OS in use so it is ready when needed. In my case, it is on a separate hard drive. This approach useful if you have more than one OS installed as I do. Each can access the same files when it is being used. Also with an OS upgrade, your data is untouched. 

The regular home folder still exists - it is needed as a location of program configuration files, and sometimes I do use it for temporary work and storage (downloads, for example).  

For easy access, I set file manager bookmarks or shortcuts to locations on the data drive. Applications can be set to use the data partition for storage (or they just remember it from your last usage), so it is no problem.

I use a separate data partition as well however I have the normal /home folders there and symlink them into my /home on the / i'm using. from my visual perspective it's the same as a home partition, but only the stuff i want to keep is in the data partition. settings and normal /home stuff stays in /home.

---

### Post by olduse78802 on 2017-01-10
I use a seperate partition for my data and all other files .  For example if i am using a 500 giger i have a 60 gig partition for the operating system and the other 440 gigs for my files.  I also have several windows machines that i access the files from also , so i use ntsc file system.  ubuntu has no problem with accessing it.  If i did not need the windows machines i would jusr use ext4 file system for everything.  Hope this gives you some idea of what you can do.

---

### Post by 1clue on 2017-01-10
I use /home as a separate partition and then use lvm to create extras for stuff that gets big.  I have Pictures, for example, symbolically linked to /var/data/pictures/me for example ('me' changes from user to user)

This way I can resize the partitions as needed, on the fly.

---

