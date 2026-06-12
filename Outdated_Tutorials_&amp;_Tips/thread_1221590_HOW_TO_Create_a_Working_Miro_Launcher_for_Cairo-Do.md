---
title: "HOW TO: Create a Working Miro Launcher for Cairo-Dock"
date: 2009-07-24
forum: Outdated Tutorials &amp; Tips
---

### Post by eternalsword on 2009-07-24
Note that I am using Miro 2.5 due to be released as an ubuntu deb sometime in the next week.

For whatever reason, the miro command does not work correctly when called from a cairo-dock launcher.

The only way I got this to work was to write a little php script as a wrapper.  In order to run php scripts you'll need to install php5-cli

From a terminal
```
sudo aptitude install php5-cli
```

Now we need to write the script.

From a terminal
```
gksu gedit /usr/local/bin/miro.launcher
```

Since /usr/local/bin requires root for write access, we use gksu and it will ask for your password.

Paste the following into gedit
```
#!/usr/bin/php -q
<?php 
passthru("miro.real > /dev/null 2>&1");
?>
```

Now save and close gedit.  Next we need to make this script executable.

From a terminal
```
sudo chmod +x /usr/local/bin/miro.launcher
```

Now configure a cairo-dock launcher.  In the command field, use
```
miro.launcher
```

I'll leave the rest of the configuration up to you.

For those that want to understand the script, here's a breakdown:
Line 1 just tells the system what program should be used as the interpreter for the script.

Lines 2 and 4 are opening and closing tags between which the php interpreter will execute the contents as php commands.  Without these tags, the interpreter would just output whatever text happens to be there.

Line 3 is a php function which executes a command on the system.  For more details on this function see [here]("http://us2.php.net/manual/en/function.passthru.php").  

The command it is executing is
```
miro.real > /dev/null 2>&1
```

miro.real launches miro. the > /dev/null tells it to send it's standard output to the [null device]("http://en.wikipedia.org/wiki//dev/null").  The 2>&1 tells it to send standard error message to the same place as the standard output, which in this case is the null device.
I find it's good practice to send any unneeded output to the null device.

---

