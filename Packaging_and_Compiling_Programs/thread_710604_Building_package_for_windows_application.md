---
title: "Building package for windows application"
date: 2008-02-28
forum: Packaging and Compiling Programs
---

### Post by fenixk19 on 2008-02-28
Hello, everybody!
I'am making package for windows application, called QIP, using wine. As many other windows apps, it wants to write in his own directory. So, I'am installing it in /usr/wineapp/qip, and i want make QIP able to write there. If I just change rights, wine tells me, that this directory is not owned by me. The solution may be: to create a group, then add there users of program. But this is a problem for user - to add himself to group. It is not user friendly. Is there any way to add users automatically? Could i use newgrp? Or there is some other solution? I've heard about package for ubuntu, to view Power Point presentations, that is uses wine. Can it help me? Please, answer! I want to break a wall between freeware Windows apps and my Linux system!

---

### Post by erginemr on 2008-02-29
There should be a hidden .wine_something directory. If you let the installer put the files in there, you needn!t worry about permissions. But I think you already know that and are trying to avoid it for security reasons.

---

### Post by fenixk19 on 2008-03-01
I know only about .wine directory in users home dir. But this way, we will have to make a copy of program for each user. It is not right, i think. I think, it is better to make some writable directory somewhere in /usr or /usr/share for all users. But this way wine doesn't want to work...

---

### Post by erginemr on 2008-03-01
I couldn't fully grasp what you are after (maybe because I don't know much about how QIP stores user data, except that it is an instant messenger), but my intention was to draw your attention to symbolic links. 

With regard to the attached screenshots, I have first created a folder (mydir) and a file inside (myfile) and created a symbolic link to it in /usr/share. Then, I could edit the file using this link with my user privileges.

The order could be reverse, you could first create the folder as a common for all users, and create files in users' home folders as hidden (.file_name) and link them here under this folder with a name that OIP expects to find.

The, it dawned upon me that the user permissions of this link is "rwxrwxrwx" although it is still owned by root, which means everyone can access and edit this file. (though I am not 100% sure whether this type of permission will compromise the system's security.) However, the file which the symbolic link refers to has the correct permissions "rwxr-x-rx" and is owned by the user.

Granted this is not a conclusive solution, but it will perhaps let you further think on user permissions.

---

### Post by erginemr on 2008-03-01
On a second thought, I remember VirtualBox, the virtual PC application, had created a group "vboxusers" in the file /etc/groups and has explicitly asked the user to add (him/her)self to the vboxusers group. I suggest you to install VirtualBox (they should have a Debian package on their site) and inspect how they handle this.

I believe you should create an installer script inside the Debian package, which will add a custom user group to the system if there is none and prompt for the user to allow adding him/her to this group (the installer will use adduser to achieve this task, see the attached screenshot), all the while wielding zenity (man zenity) to interact with the installer graphically. Easier said than done... ;-)

---

### Post by fenixk19 on 2008-03-02
You said, that link would be owned by root. That's a problem, because wine(versions >= 0.9.50) doesn't want to use folder, that is not owned by current user. I think i'll use vbox solution. I don't see other way.

---

### Post by erginemr on 2008-03-02
> **fenixk19 said:**
> You said, that link would be owned by root. That's a problem, because wine(versions >= 0.9.50) doesn't want to use folder, that is not owned by current user. I think i'll use vbox solution. I don't see other way.

I believe you should still give it a shot because although the link is owned by root, the original file / folder is owned by the user...

---

### Post by fenixk19 on 2008-03-02
I've got problem with groups, because of same old problem: folder is not owned by user. But i found other way: I make folder ~/.qip, and then put links for all qip files from /usr/...
We have folder owned by user and all files, shared and writable. Yes, i also make files in qip path writeable for all. Not very safely, but it is windows app, right? :)

---

### Post by erginemr on 2008-03-02
Sweet! As safe as any other config file inside the home folder I guess. Don't worry, to my knowledge, pretty much all native instant messengers (pidgin, amsn, emesene, etc.) put the config files inside the home folder too.

I am glad that you have found a solution. :cool:

---

