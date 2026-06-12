---
title: "HOWTO: Terminal-Here Nautlus Script"
date: 2006-07-20
forum: Outdated Tutorials &amp; Tips
---

### Post by HeavyAl on 2006-07-20
Didn't see this anywhere else and thought I'd share.

Often I'm browsing directories using Nautilus and need to get to a terminal from the current directory but I hate having to open up a terminal session and then manually move to the directory I'm looking at - especially if I'm deep in /bin or some such. So I wrote this to let me open a gnome-terminal session simply by right-clicking and selecting 'terminal-here' from the Nautilus scripts menu.

Heres how you do it:

Open a terminal and navigate thusly:

```

cd /home/[your-username]/.gnome2/nautilus-scripts

```

Then start editing a new file with your favorite editor. I used gedit for simplicity's sake:

```

gedit terminal-here

```

In the editor, enter the following code

```

#!/bin/bash
cd $NAUTILUS_SCRIPT_CURRENT_URI
exec gnome-terminal

```

Save the file and close it.
Next you need to change the permissions on it:

```

chmod 755 terminal-here

```

And you're done.

Now pull up Nautilus and right click in any directory and look in scripts and you should see a 'terminal-here' listed. Clicking it will give you a terminal with the base dir being the one you are currently viewing in Nautilus.

---

### Post by Thund3rstruck on 2006-07-21
Wow... so simple, yet so effective.

Quick question, where did you find that nautilus function NAUTILUS_SCRIPT_CURRENT_URI?

Could you also use:

```

cd $1

```

Just curious...

---

### Post by lazyd2 on 2006-07-21
```
sudo apt-get install nautilus-open-terminal
```;)

---

### Post by jordilin on 2006-07-21
> **Thund3rstruck said:**
> Wow... so simple, yet so effective.

Quick question, where did you find that nautilus function NAUTILUS_SCRIPT_CURRENT_URI?

There are plenty of nautilus scripts. Take a look at [http://g-scripts.sourceforge.net/faq.php](http://g-scripts.sourceforge.net/faq.php)

---

