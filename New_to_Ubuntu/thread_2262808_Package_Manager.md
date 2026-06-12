---
title: "Package Manager"
date: 2015-01-27
forum: New to Ubuntu
---

### Post by peter-ward497 on 2015-01-27
I have a no entry sign at the right hand top of the screen.When I click on it it displays the message "An error occurred, pleas run package manager from the right click menus or apt-get in a terminal to see what is wrong.The error message was:'Error:BrokenCount>0.This usually means that your installed packages have unmet dependencies.
What do I need to to do ?

---

### Post by JeQhdMD on 2015-01-27
What do you have installed? . . . 
>  what distro/version, 
>  how was it installed (a brand new - fresh install, OR, an upgrade from an older version of Ubuntu?), 
>  what DE (desktop environment), 
> what have you added recently (apps/programs)?
>  have you made ANY changes to the default software repository sources?  (adding PPA's for instance)?,
>  do you have WINE or PlayonLinux installed?

Often these errors result from a combo of above actions, and package updates that didn't complete updating.

Here is a useful thread . . . [http://ubuntuforums.org/showthread.php?t=2249847&page=2&highlight=fix+broken+package](http://ubuntuforums.org/showthread.php?t=2249847&page=2&highlight=fix+broken+package)

YES , it is longish . . . but if you read it all especially the second page (post 13, 14 especially), you'll have some potential clues on the codes to fix.   Of course, a lengthy fix is a fresh install making sure you have a clean sources list for your repos.

---

### Post by Bashing-om on 2015-01-27
peter-ward497; Hi !

The place to start is to follow the package manager's advise:
> 
 or apt-get in a terminal to see what is wrong

To that end, activate a terminal and execute apt-get's commands:
```

sudo apt-get update
sudo apt-get upgrade

```
Post those outputs - Between code tags (retains readability)
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

And we will see what we can determine for the nature of the problem .

[INDENT][INDENT][INDENT]all in the process
[/INDENT][/INDENT][/INDENT]

---

