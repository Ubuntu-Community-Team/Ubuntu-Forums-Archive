---
title: "[SOLVED] Where does Ubuntu 8.04 put the trash?"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by Kintar on 2008-08-21
I've been doing search after search for this with no luck finding it anywhere on the web.  After several days of digging and poking with find, I finally found the trash folder.  I know a lot of people will laugh at me for that, but I figured I might as well put it up here in case it helps someone else.

All of the posts I dug up say that the trash is located in [FONT="Courier New"]**/home/<username>/.Trash**[/FONT].  That may be the case for earlier versions, I can't speak to them, but for 8.04, trash is located in **[FONT="Courier New"]/home/<username>/.local/share/Trash[/FONT]**.

I hope this helps someone, somewhere.

---

### Post by Pro-reason on 2008-08-21
[COLOR="Blue"]For each user, the trash is located at **~/.local/share/Trash** and at **.Trash-`id -u`** for every additional partition mounted on the filesystem.[/COLOR]

&#8220;`id -u`&#8221; is a bit of trickery that will insert your correct user id if put it into a command in the terminal.  &#8220;1000&#8221; is the default for the first user added to the system.  Subsequently added users will have IDs such as &#8220;1001&#8221;.  The superuser's ID is &#8220;0&#8221;.

&#8220;~&#8221; or &#8220;$HOME&#8221; is another bit of trickery that will insert your user directory.  Remember that the superuser has its own home directory too (&#8220;/root/&#8221;).

So, to delete all trash for all users on a system with an extra data partition mounted at /mnt/Movies, you would type the following:

```

sudo rm -fr /home/*/.local/share/Trash  /root/.local/share/Trash  /mnt/Movies/.Trash*

```

Careful with where you put the spaces in that.

To delete only your own trash:

```

rm -fr ~/.local/share/Trash  /mnt/Movies/.Trash-`id -u`

```

---

