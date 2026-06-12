---
title: "Can't install Heroku Toolbelt"
date: 2013-10-04
forum: New to Ubuntu
---

### Post by Brandon_Lyons on 2013-10-04
I am running Ubuntu 13.04 32bit. I ran the terminal command to install the heroku toolbelt

wget  -q0- [https://toolbelt.heroku.com/install-ubuntu.sh](https://toolbelt.heroku.com/install-ubuntu.sh) | sh

The toolbelt doesn't install, instead I get these errors:

Failed to fetch [http://toolbelt.herokuapp.com/ubuntu/./Packages](http://toolbelt.herokuapp.com/ubuntu/./Packages)  302  Moved Temporarily
Failed to fetch [https://github.com/heroku/heroku.git/dists/raring/main/binary-i386/Packages](https://github.com/heroku/heroku.git/dists/raring/main/binary-i386/Packages)  The requested URL returned error: 406 Not Acceptable
Unable to locate package heroku-toolbelt


I have tried this several times and I am unable to find a solution to this particular error. I would greatly appreciate any help that I can get.

---

### Post by SCreamin4Q on 2013-10-04
I'm having the same issue.

---

### Post by one-o2 on 2013-10-04
Almost same here, but I get this error (it was in polish, translated via Google Translator):
```
W: Faiuled to fetch **[http://toolbelt.heroku.com/ubuntu/./Packages](http://toolbelt.heroku.com/ubuntu/./Packages)**  302  Moved Temporarily [IP: **23.21.198.2 80**]
E: Unable to fetch some index files, they have been ignored or used with the older version.
Reading package lists ... ready
Building dependency tree
Reading state information ... ready
E: Could not find package Heroku-toolbelt

```It gave me different URL address. And whats that IP?

---

### Post by SCreamin4Q on 2013-10-04
Well considering that Github is under attack atm (ddos?) i'm guessing it might have something to do with it.

---

### Post by Christmas on 2013-10-04
The [standalone]("https://toolbelt.heroku.com/standalone") binary seems to work me:
```

wget -qO- https://toolbelt.heroku.com/install.sh | bash
This script requires superuser access to install software.
You will be prompted for your password by sudo.
[sudo] password for embryo: 
sh: 7: [[: not found
Add the Heroku CLI to your PATH using:
$ echo 'PATH="/usr/local/heroku/bin:$PATH"' >> ~/.profile
Installation complete
```

Then run it manually using /usr/local/heroku/bin/heroku (not a standard binary location, so you should add the path to your $PATH as instructed in the script).

```
/usr/local/heroku/bin/heroku 
Usage: heroku COMMAND [--app APP] [command-specific-options]

Primary help topics, type "heroku help TOPIC" for more details:

  addons    #  manage addon resources
  apps      #  manage apps (create, destroy)
```

---

### Post by SCreamin4Q on 2013-10-04
> **Christmas said:**
> The [standalone]("https://toolbelt.heroku.com/standalone") binary seems to work me:
```

wget -qO- https://toolbelt.heroku.com/install.sh | bash
This script requires superuser access to install software.
You will be prompted for your password by sudo.
[sudo] password for embryo: 
sh: 7: [[: not found
Add the Heroku CLI to your PATH using:
$ echo 'PATH="/usr/local/heroku/bin:$PATH"' >> ~/.profile
Installation complete
```

Then run it manually using /usr/local/heroku/bin/heroku (not a standard binary location, so you should add the path to your $PATH as instructed in the script).

```
/usr/local/heroku/bin/heroku 
Usage: heroku COMMAND [--app APP] [command-specific-options]

Primary help topics, type "heroku help TOPIC" for more details:

  addons    #  manage addon resources
  apps      #  manage apps (create, destroy)
```

thanks, up and running

---

### Post by Brandon_Lyons on 2013-10-04
Thanks!!! This solved the problem!

---

### Post by Christmas on 2013-10-04
You're welcome :)

---

### Post by edison90110 on 2013-11-09
hi christmas,
i followed your advice and installed heroku without any errors. and,
when i executed command "which heroku", it returned "/usr/local/heroku/bin/heroku"
i think it maybe right.but,
when i executed like this "$heroku", the error occured with info &#8220;/usr/bin/env: ruby: No such file or directory"
could you please do me a favour about this? i will really appreciate it, thx!

---

