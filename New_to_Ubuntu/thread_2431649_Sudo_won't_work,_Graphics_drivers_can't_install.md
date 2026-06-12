---
title: "Sudo won't work, Graphics drivers can't install"
date: 2019-11-19
forum: New to Ubuntu
---

### Post by Arkenbrien on 2019-11-19
I put together a system with some components I had for a new low-spec gaming rig for use in my dorm:

i3
Radeon HD 7950
8 GB DDR3

I tried Ubuntu years ago, but I've stayed with W7 because it's everything I need from a gaming system.

I really only want to run a single program, World of Warships, which has fairly positive results from running off Steam via the built in Proton (I also tried Lutris, but it wouldn't run because of what I think is driver related). It says it's running, but nothing pops up, so I assume that there's some sort driver/gpu related issue. I'm not sure but that's not the point of this OP.

It's the end of day two of my increasingly frustrating quest to get this system even running right.

Long story short, I need to install drivers for my gpu. I can't, because for ***some*** reason I cannot use any sudo commands anymore. I was using them yesterday, but now it says that I'm "not in the sudoer's user list, and this attempt will be recorded". 

I've tried following this: [https://askubuntu.com/questions/675898/cannot-run-any-sudo-command](https://askubuntu.com/questions/675898/cannot-run-any-sudo-command), which I did to the letter, but nothing changed. I've tried a dozen or so different things, all of which failed because, guess what, one needs sudo privileges to grant sudo privileges. 

I can't even install programs from the app store, it asks for an "Administrative" pw and it won't take mine. 

I'm the only user. Fresh install from 2 days ago. How am I *not* the admin?

I've just about had it with Ubuntu, and I'm thinking of seriously looking for a W7 install disk I think I have over the weekend if I can't get this stupid thing to work. Until then, however, I'm going to try to get this system at least out of the hanger, maybe even to the runway.

If somebody can please tell me how to get my sudo privilege back, I think I might be able to install the drivers.

Thanks in advanced.

---

### Post by Skaperen on 2019-11-19
my guess, and it's just a guess, is that one of the sudo commands you did when you had those powers changed something.  it could be many things.  security these days checks so much and that means many things can stop the access because a hacker can use those many things to get in.  an example is a permission to change files in the [COLOR=#0000cd][FONT=courier new]**/etc**[/FONT][/COLOR] directory being made world access would allow someone else to flip the files around to get sudo powers.  it's not going to cross-check that you are the only user because it doesn't know that the hacker didn't also create that appearance. 

to get back in, boot up the media you installed from, select "try Ubuntu"  and use that to mount the hard drive and change the files that you messed up, or do whatever else is needed to fix this.  if you need help on that task, just post back here and tell us what you did and how far along you are.

go be on it !!

---

### Post by TheFu on 2019-11-19
Linux is multi-user from the ground up.  Everything about it cares about the current userid. Sometimes commands care about the hostname and network name too.

Linux isn't stupid, it is just something you haven't mastered at this point. Linux is crazy flexible, which means we have direct access to all sorts of options that Windows never even considered.  With that flexibility comes complexity. Most are controlled by text-based configuration files.
But we understand the frustration. I feel it whenever Windows doesn't work how I think it should, which happens all the time and I've been a Windows user since 1989. I've also been terribly frustrated with OSX.  We all like to use things we already know. A different OS is a hard thing to use, then even harder to master unless you've learned a similar OS already.  Linux is very much like every other popular OS in the world today, except 1 - MS-Windows.  

From the description, it is impossible to say what the exact issue could be. Some guesses:
* wrong permissions on the sudoers file
* corrupted sudoers file
* modified group membership for the userid
* some sort of hostname change.

A common issue with new users is that they abuse the sudo command because they haven't learned file and directory permissions.  While sudo is necessary for administrative tasks, using it with GUI programs should be avoided because there are almost always unwanted side effects.  Linux expects the administrator to know what they are doing.   And for administrators to have backups to fix things that the admin breaks.  No Unix has anything like a "restore point" - in the Unix world - those are called backups.

Inside the linux environment, check the userid you normally use group membership.  The **id** command will show that.  Look for the *sudo* group in the list. Report back if it isn't there.  We need to fix that first, if needed.

The /etc/sudoers file permissions and ownership need to look like this:
```
$ ls -l /etc/sudoers
-r--r----- 1 root root 788 Oct 27 15:14 /etc/sudoers
```

Report back if it doesn't look like that.  Actually, if you can post both the **id** and **ls -l** command output, we can properly interpret it to prevent mistakes.

Those two are sufficient to start.  Any other steps will have to happen in either a recovery console or booted from alternate media, like the installer flash drive/DVD you used to install the Ubuntu desktop.

It is late here, so someone else will have to pick up with the help.

I should mention, I broke my sudoers last month trying to make a little change. Had to use the "Try Ubuntu" environment to fix it.  Knowing exactly what I did wrong took me about 5 minutes to fix, but I've been a Unix admin over 20 yrs.

---

### Post by Arkenbrien on 2019-11-19
Thank you for the replies. Sorry that some of my saltiness came through, I had a full pot of coffee and a full evening of no results.

I ran the code you suggested, with the following results. I blocked out my name, not sure if I needed to do that.


[IMG]https://attachments.office.net/owa/rh166617%40ohio.edu/service.svc/s/GetAttachmentThumbnail?id=AAMkADQ3NGQ3OGVhLTY2OWMtNDdkNi05Yjg5LTlkNzQwMWExMDVhZgBGAAAAAAAadD%2FiuVioQ7wdySi2anduBwDj%2FbJ7UsgnRpE1AXrH8TaCAABFufh4AADj%2FbJ7UsgnRpE1AXrH8TaCAAJBjBbfAAABEgAQAKwVVlWLD%2BJGukLDn5depCI%3D&thumbnailType=2&owa=outlook.office365.com&scriptVer=2019111101.05&X-OWA-CANARY=dwhZ5wa66kqZOS0YFc_HnAA93wppbdcYdqj4odsnCspSc9NEY29weS303Yot3KI_SRoFpRw5u8k.&token=eyJhbGciOiJSUzI1NiIsImtpZCI6IjA2MDBGOUY2NzQ2MjA3MzdFNzM0MDRFMjg3QzQ1QTgxOENCN0NFQjgiLCJ4NXQiOiJCZ0Q1OW5SaUJ6Zm5OQVRpaDhSYWdZeTN6cmciLCJ0eXAiOiJKV1QifQ.eyJvcmlnaW4iOiJodHRwczovL291dGxvb2sub2ZmaWNlMzY1LmNvbSIsInZlciI6IkV4Y2hhbmdlLkNhbGxiYWNrLlYxIiwiYXBwY3R4c2VuZGVyIjoiT3dhRG93bmxvYWRAZjMzMDgwMDctNDc3Yy00YTcwLTg4ODktMzQ2MTE4MTdjNTVhIiwiaXNzcmluZyI6IldXIiwiYXBwY3R4Ijoie1wibXNleGNocHJvdFwiOlwib3dhXCIsXCJwcmltYXJ5c2lkXCI6XCJTLTEtNS0yMS0zOTcwNDY3MTI2LTI1ODI2MTQ4NjUtMTIzNTI4NDc0OC00MzQ0MDcwOVwiLFwicHVpZFwiOlwiMTE1MzkwNjY2MTE1MTYyNjIxN1wiLFwib2lkXCI6XCI2YzE2MGJlMi0zZDkyLTQzYTgtOThlZS1mY2Y1YzQ4MzM1NjdcIixcInNjb3BlXCI6XCJPd2FEb3dubG9hZFwifSIsIm5iZiI6MTU3NDIyMDEzOSwiZXhwIjoxNTc0MjIwNzM5LCJpc3MiOiIwMDAwMDAwMi0wMDAwLTBmZjEtY2UwMC0wMDAwMDAwMDAwMDBAZjMzMDgwMDctNDc3Yy00YTcwLTg4ODktMzQ2MTE4MTdjNTVhIiwiYXVkIjoiMDAwMDAwMDItMDAwMC0wZmYxLWNlMDAtMDAwMDAwMDAwMDAwL2F0dGFjaG1lbnRzLm9mZmljZS5uZXRAZjMzMDgwMDctNDc3Yy00YTcwLTg4ODktMzQ2MTE4MTdjNTVhIn0.OErWIxAWfSWv4GQjo7P5rq80pr8jc-QjAh7RzWjfWZ5H1BiKMSC2UIJwqcjTGIQFdRB3LcH2L-PEXH0EraU0JkxgsYKrq-vQ4FtV9wfp-DRMMF8M-UU-k3wlOeGtser_mz1keYo10ubbKKlofHMMM2ATi3YCpvgwtC1eOsq7xqQXfYNuTACBrcHn5Gdu0QLsBxu8jS5l89vlQXBDKgjbvY4mrUBzPdQyHBLxwPM8hI6H4qfDyLYxvnddurgZujNj8--3zY6Y73ZoIwYhAwtg2gw8UDR0irpYMnVbDDp5lT_LP6z5PrzUiUVlybxadC2D7SIongkwZAlMX_Khv4c6hw&animation=true[/IMG]

---

### Post by oldfred on 2019-11-19
If terminal output please just copy & paste into forum. And use code tags to preserve formatting.
Easy to add code tags with Forum's advanced editor & # icon.
But I use quick replay which only has quotes and manually change quote to code.
How to use Code tags, # in advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
[http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)

```
fred@Bionic-Z170N:~$ id
uid=1000(fred) gid=1000(fred) groups=1000(fred),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),116(lpadmin),126(sambashare)

```

it looks like you deleted your user. unless what you blocked out was exactly your user id.

---

### Post by sisco311 on 2019-11-19
You managed to remove your user from the sudo (and/or admin) group. As TheFu predicted, you will need to boot into the recovery mode or chroot into the system from a live cd/usb to fix the issue. [https://www.psychocats.net/ubuntu/fixsudo](https://www.psychocats.net/ubuntu/fixsudo)

---

### Post by TheFu on 2019-11-20
Or boot into a Try Ubuntu environment, then mount the partition with the /etc/ directory and simply edit the group file to add your userid to the *sudo* group.  The passwd and group files are really simple to understand once you have a feel for what each different field is.  In the old days, this was how admins handled groups and users.  We didn't have any fancy tools, just a text editor.   Pretty much any beginning Linux book should explain these files or local manpages will too.
```
$   man group
```

If you want to use commands like **usermod**, to modify the groups, then a chroot or recovery mode is necessary.  I think it is much easier, while more dangerous, to just edit the file.  Always good to make a backup copy of any file before changing anything.

If you get desperate, a beginner book: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)  Learning concepts and commands in the correct order means you don't waste time jumping around being totally confused or googling for the wrong answers.  User management on Linux is pretty much the same the last 20 yrs and no release is all that different from any others.  

That isn't always true - like networking, DNS, system initialization and package management have drastically changed on Ubuntu the last few releases. When searching for answers in those areas, always use the ubuntu release in your search terms.

---

### Post by TheFu on 2019-11-20
Just saw this new article which explains much about sudo, including how to properly edit it using the visudo command: 
  [https://www.howtogeek.com/447906/how-to-control-sudo-access-on-linux/](https://www.howtogeek.com/447906/how-to-control-sudo-access-on-linux/)

---

### Post by Arkenbrien on 2019-11-20
Thanks guys, I'll give this a shot when I can.

---

### Post by Arkenbrien on 2019-11-20
Well I did get sudo privilege back, that did work, thanks.

However when I tried to install the amd drivers following this video: [https://www.youtube.com/watch?v=txellkpCCIw](https://www.youtube.com/watch?v=txellkpCCIw), I now have a black screen. Maybe my system is too sketchy, idk.

At least I see the friendliness of this forum hasn't decreased in the slightest since my last visit!

---

### Post by oldrocker99 on 2019-11-21
The built-in open-source drivers work very well, and, AFAIK, few Linux Radeon gamers even look for or use them.

Were the framerates **that** low, that you needed other drivers?

---

### Post by Arkenbrien on 2019-11-21
The reason I tried to install the drivers was because the game I wanted to play would launch, but would never open up a window. I would like to play World of Warships, which has a pretty good success rate of starting on Steam with their proton software. However, when I click launch, Steam would say that it is running, but nothing happens. I tried all the various options on Steam, but nothing seems to work. I tried to use the drivers as an experiment to get it to run. But installation seems to have caused more problems. I'm not sure what direction to take now, in terms of getting the game to work.

I'm going to uninstall the drivers if I can, since it's not helping at all, and see what else I can do when that's done. I'll try a different game just to see if it works.

---

### Post by CatKiller on 2019-11-21
> **Arkenbrien said:**
> I would like to play World of Warships, which has a pretty good success rate of starting on Steam with their proton software. 

Proton requires Vulkan. I have no idea if it's installed by default, and I find AMD's drivers fairly confusing.

The full Proton requirements are [here.](https://github.com/ValveSoftware/Proton/wiki/Requirements)

---

### Post by Arkenbrien on 2019-11-21
Thanks. I installed Vulkan, but no joy, game won't open. It still says that it's running, but nothing happens.

---

