---
title: "Shell script help"
date: 2010-07-11
forum: Programming Talk
---

### Post by davideotape on 2010-07-11
Attached is a little shell script I've been working on. The idea is to make fixing a bug really easy, and anyone is free to use it. I have a few questions about things I'd like to add though:

[LIST=1]
[*]Is there a nicer way to pause the script instead of just using "read temp"?
[*]Is there a way to spawn a shell after pausing the script, and then resuming the script once the user exits the shell?
[*]Is there a way to permanently store a variable for a users launchpad username. At the moment my username is hardcoded in, but it would be nice if other people could be prompted once for their username which is stored somewhere.
[/LIST]

---

### Post by geirha on 2010-07-11
1. Not with POSIX sh, and I can't think of any POSIX commands to do it nicely either. In bash, you could use something like
```

#!/bin/bash
read -n1 -s -p "Press any key to continue "

```

2. Sure,
```

#!/bin/sh
echo "Press enter to continue"
read _
echo "Starting an interactive POSIX shell"
sh
echo "Interactive POSIX shell ended. Continuing script..."

```

3. Write it to a file, and read it in at startup.
```
#!/bin/sh
if [ -f ~/.lpusername ]; then
   read -r username < ~/.lpusername
else
   printf "Username: "
   read -r username && echo "$username" > ~/.lpusername
fi

```

Your script seems to be intended for Ubuntu only, and since bash is installed by default on Ubuntu, I'd recommend using bash instead of sh. It gives you a lot more features.

Learn it with this guide: [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)

---

