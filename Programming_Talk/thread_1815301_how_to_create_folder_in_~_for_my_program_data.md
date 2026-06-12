---
title: "how to create folder in ~ for my program data ?"
date: 2011-07-31
forum: Programming Talk
---

### Post by yahyai-0 on 2011-07-31
[SIZE=2][B]Hello

How I can use autotools to create folder for my program data in the home directory like ??
(like firefox use .mozila folder for database and cache etc)
 
I have already used it to create my program folder on (/usr/share/)

help me please !


[/B][/SIZE]

---

### Post by ajgreeny on 2011-07-31
You can make any folder you want in your home folder or partition either by right clicking on the parent folder in the left hand pane of nautilus, or by using File->Create Folder.

It could not be more simple.

---

### Post by Barrucadu on 2011-07-31
You don't, you make directories in $XDG_CONFIG_HOME, $XDG_DATA_HOME, and $XDG_CACHE_HOME - as the [XDG basedir spec](http://standards.freedesktop.org/basedir-spec/basedir-spec-latest.html) says.

Also, you don't use autotools for this. Autotools is used to build/install your program. The program itself will do any necessary per-user set-up when that user runs it for the first time.

---

### Post by JupiterV2 on 2011-07-31
Some libraries, like glib, provide convenience functions for just this very task. g_get_home_dir() will acquire a user's home directory. Alternatively, you could also use the $HOME environmental variable to get a user's home directory but it's unreliable because: a) it could refer to a directory not actually owned by the user, b) it's not writable, c) doesn't even exist. This is because HOME may be undefined or has been altered by the user. It is much preferable to use the system tools to acquire a user's home directory.

And, as already stated, you normally set this data from within your program and do not use autotools to create and install configuration data. You can't rely on the configuration data being there (user may have deleted the data) so you need a method of reproducing/recreating default values and storing them at runtime.

---

### Post by cgroza on 2011-07-31
All my projects check for the existence of that file, and if does not exists, I create it.

---

### Post by yahyai-0 on 2011-08-01
Thanks alot all of u

I will create it with c++

---

### Post by yahyai-0 on 2011-08-05
I have created the folder in home folder using c++
but now how to remove it when the usr remove the program?

---

### Post by JupiterV2 on 2011-08-05
There is no great way to do this that I know of. For one, many programs leave their configuration/personalized setting behind as a feature to their users in case they decide to re-install the program. That way, their settings aren't lost. If, however, you still need to get rid of them there are a few ways I know of. One, if you are using GNU auto-tools to build and install your program you can use it's features to run a post-uninstall script. This would carry over to a Debian package, and I assume rpm too, because the .deb utilizes auto-tools. I think, too, there are some scripts within the .deb utilities that allow you to do this. That is what the 'purge' option is for, to remove configuration settings from the system. Lastly, you could also simply write an un-install script for your program to purge the system. Other than that, I don't know. Maybe an option within your program a user could run prior to un-install? A 'remove user-settings' option?

Maybe someone else has a better solution?

---

### Post by yahyai-0 on 2011-08-05
thansk 
but how to remove using gnu auto-tools
how to get homedir in MakeFile?

---

### Post by cgroza on 2011-08-05
> **yahyai-0 said:**
> thansk 
but how to remove using gnu auto-tools
how to get homedir in MakeFile?
Why do you need it? You shouldn't mess around with files other than your program's.

---

### Post by yahyai-0 on 2011-08-05
> **cgroza said:**
> Why do you need it? You shouldn't mess around with files other than your program's.

my programs create folder in home folder (.bugspy) thats have some data for the program..

I used gnu autotools  to manage my program.

if the user want to remove the program , the folder will not be deleted

-------
now how to remove it using MakeFile....

---

