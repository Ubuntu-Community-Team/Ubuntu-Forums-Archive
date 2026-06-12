---
title: "Shutting down with python"
date: 2006-12-31
forum: Programming Talk
---

### Post by Quite Interesting on 2006-12-31
I was wondering if anyone could help me with a little problem I've come across. I want to write a program that shuts down the computer at a specific time and doesn't require sudo or root status. In the context of this program it would be impractical for someone to enter a password when they won't be a the computer, although I suppose I could set it so that the program executes the shutdown command at that point and passes the time of shutdown to the command. I would prefer not to do it that way though and I know it must be possible as the shutdown button in gnome (and I assume KDE) doesn't require a password. Any help would be greatly appreciated.

---

### Post by lmo on 2007-01-01
You could use crontab.  
```

sudo sh -c 'EDITOR=vi crontab -u root -e'

```

Type the letter 'o' then enter line like this:
```

59 08 * * * /sbin/shutdown now -h -k

```
Lines in the crontab file start with 5 timer specs where * means anything. the specs are:
Minute Hour Day(1-31) Month(1-12) Day(0-6)

In the above code, at minute 59 at hour 8 the system will fake a shutdown.
Change the minute and hour to suit.
Remove the '-k' to do a real shutdown instead of fake.

Type the ESC key and then type the symbol ':' and the letter 'x' and press ENTER to save and exit the vi
```

:x

```

To review the crontab file you can use:
```

sudo crontab -u root -l

```

---

### Post by dwblas on 2007-01-01
You use os.system in Python to issue a call to the system, so for the above command you would use:
os.system( "shutdown now -h -k" ) or
os.system( "poweroff" )

---

