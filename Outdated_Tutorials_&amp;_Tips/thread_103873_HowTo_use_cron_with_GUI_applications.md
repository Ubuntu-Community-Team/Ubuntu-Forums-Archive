---
title: "HowTo use cron with GUI applications"
date: 2005-12-14
forum: Outdated Tutorials &amp; Tips
---

### Post by henriquemaia on 2005-12-14
First of all, please refer to this [howto]("http://ubuntuforums.org/showthread.php?t=102626&highlight=cron") to learn more about crontab.


My motivation to find this out was because there are several radio shows I really like and I was always missing them. As such, I needed something to start amarok playing the chosen radio station at specific times. Probably this could be achieved with some other more elegant solution, but this serves its purposes. Also, I knew that by learning how to do this, I could use it for many other things.

To accomplish this, you have to edit your crontab:

```
crontab -e
```

you can also use a nicer GUI tool to edit crontab, like **Gnome Schedule** (not in the repositories) or **KCron** (available on the repositories).

If you use a GUI tool, please adapt the instructions accordingly. I will explain this using as basis the default crontab editor.

To run a GUI command on cron, you'll have to tell cron what display the program should use. For that you use:

```
export DISPLAY=:0 
```

**:0** is the default. If you like the program to run on other display, please change the number accordingly (e.g. **:1**, **:2**, etc).

So, you add to what is explained [here]("http://ubuntuforums.org/showthread.php?t=102626&highlight=cron"):  

```
01 04 * * * /usr/bin/somedirectory/somecommand
```

the **export** variable, like this: 

```
01 04 * * * export DISPLAY=:0 && /usr/bin/somedirectory/somecommand
```

So, in my case, as I want **amarok** to play Antena2 (radio station) at a specific time, I use:

```
30 16 * * 7     export DISPLAY=:0 && amarok mms://rdp.oninet.pt/antena2 
```

This will make amarok start the Antena2 url every Sunday, at 16:30. But I want also to shut up amarok after the show is finished. So, I use:

```
0 17 * * 7     export DISPLAY=:0 && amarok -s

```

This will shut up amarok at 17:00 every Sunday. 

You can use this export trick to the limits of your imagination with every kind of application you want. 

Another example that occurs me is for file sharing and when your greedy ISPs only allows you a low monthly download limit, but have some kind of free download period (normally very late at night - this is the case of my ISP 8)). As such, I need to start nicotine (soulseek network application) only during that free period (3AM - 9AM). So, I use:

```
0 3 * * * export DISPLAY=:0 && nicotine
```

that will start nicotine everyday at 3AM. To shut it down, I use:

```
0 9 * * * killall nicotine
```

This will shut it down at 9AM.

Hope this helps some of you.

If you have more ideas how to use this trick (or how to improve this HowTo), please share with us in the thread.

---

