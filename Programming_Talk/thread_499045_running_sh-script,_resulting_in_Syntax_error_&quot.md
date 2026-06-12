---
title: "running sh-script, resulting in Syntax error: &quot;(&quot; unexpected"
date: 2007-07-12
forum: Programming Talk
---

### Post by stigala on 2007-07-12
Hi, 

I'm trying to run a script on ubuntu 7.04;

stig@stig-laptop:~/mosesdecoder$ ./regenerate-makefiles.sh 
./regenerate-makefiles.sh: 13: Syntax error: "(" unexpected

but then I get the syntax error. Below is the first lines in the script, line 13 in red. 

[COLOR="Green"]

#!/bin/sh

# NOTE:
# Versions 1.9 (or higher) of aclocal and automake are required.

# For Mac OSX users:
# Standard distribution usually includes versions 1.6.
# Get versions 1.9 or higher
# Set the following variable to the correct paths
#ACLOCAL="/path/to/aclocal-1.9"
#AUTOMAKE="/path/to/automake-1.9"

[COLOR="Red"]function die () {[/COLOR]
  echo "$@" >&2
  exit 1
}

...[/COLOR]

I already have automake (GNU automake 1.9.6) and aclocal (GNU automake 1.9.6). Setting the paths is only for Mac OSX users, so I didn't try to set any of those paths. 

Anyone can explain this? Thanks for any help,

Stig

---

### Post by Rui Pais on 2007-07-12
Hi.

the (inexistent) problem is the 1st line in combination with Ubuntu. 

When you run it using  ./ it will use the shell you mention on first line, in your case:
> #!/bin/sh

if you do a **ls -l /bin/sh** you will see that it's just a link to dash.
Ubuntu, since Edgy, replaced old sh with dash, creating a series of incompatibilities in a lot of scripts...

So, either you run:
```
bash regenerate-makefiles.sh 
```

or replace first line with:
```
#!/bin/bash
```
(or even remove the 1st line and environment will call it with bash)

or (losing generality) adapt it for dash:
remove the keyword function:
```
die() {
...
}
```

hth

---

### Post by stigala on 2007-07-12
Thanks a lot, Rui!

I used **bash regenerate-makefiles.sh** and the script ran perfectly. I guess I'll have to read up on dash, bash and sh to understand the difference between the different shells. 

Stig

---

### Post by Rui Pais on 2007-07-12
No prob :)

sh and bash has more or less the same syntax, so usually no problem came from there... but dash is much more different. it's suppose to be much lighter and faster then bash, being that the reason why they choose it by Edgy days. 

A lot of people had problem, specially with custom scripts. I still have to manually edit some files for use plugins on TeXmacs editor, and they are the officially supported ones :( 
It was by then very common to replace that symlink to one pointing bash (some docs on Ubuntu Documentation still advise that...) 

A problem that i find a lot is the [[ something ]] && some_code that raise errors (" [[: not found"). 
It can usually be replaced by: if [ something ]; then

I still prefer to keep dash as default shell and change the 1st lines of scripts or run some of them with bash.
:)

---

### Post by OldGaf on 2007-08-23
:x AHHHHHHHH!!!!!!


OK... I am also getting Syntax error: "(" unexpected

The problem is, I was NOT getting it an hour ago!

I ran one of my old scripts and all was fine.
I started writing a new one and got the above error.
I checked Google and everything said to use #!/bin/bash
The problem is, I was using that all along..... nothing has changed!
Then I tried to rerun my original script again...... same damn error.
I sent the script to by brother........ works fine!

What gives?

---

### Post by WeyOh on 2008-06-11
What if my first line says: #!/bin/bash?

---

### Post by Rui Pais on 2008-06-13
> **WeyOh said:**
> What if my first line says: #!/bin/bash?

if you put  #!/bin/bash it will run with bash, if you put  #!/bin/sh it will run with dash, unless you changed /bin/sh link from dash to bash (or other)

---

### Post by reality1011 on 2008-06-15
also there are subtle differences in shells.  for example in ksh, you do not need the function key word...  On solaris (in sh) you can not use the function keyword either...

Sometimes you go crazy debugging these

---

### Post by madams11 on 2008-08-01
> **Rui Pais said:**
> if you put  #!/bin/bash it will run with bash, if you put  #!/bin/sh it will run with dash, unless you changed /bin/sh link from dash to bash (or other)

I am having similar troubles with scripts.  However in checking, I found that sh is a link to dash and bash is also a link to dash.  I can't find the actual bash shell anywhere.  So, I tried apt-get install bash, and it said I already had the latest version.  Any tips on what to do next?

---

### Post by dwhitney67 on 2008-08-01
Run the Synaptic manager:  System->Administration->Synaptic Package Manager

Once it is up and running, search for bash.

Then ensure that the it is indeed installed, and if not, install it.

On my system, I removed the /bin/sh link to dash, and changed it to point to /bin/bash.

---

### Post by mssever on 2008-08-02
> **dwhitney67 said:**
> On my system, I removed the /bin/sh link to dash, and changed it to point to /bin/bash.
That's just masking the problem, so I think it's a bad idea. The real problem is that: a) some people equate sh with bash, and b) bash does a poor job of emulating sh.

The Bourne Shell (sh) is specified in POSIX as the standard shell for portable scripts. Any program called as /bin/sh should behave according to the specifications. Also, sh is rather primitive compared to bash. Unfortunately, Bash doesn't disable all its extensions when running in sh mode. So, people who thought they were writing sh scripts were really writing a subset of bash. The proper solution, of course, is to fix the scripts, which are buggy by definition.

The other lesson here is that there are few reasons anymore to use sh. Almost all UNIX-like systems have bash, so it's possible to have your cake and eat it, too. Use all the bashisms you want, but call it with bash.

EDIT: Because bash is a superset of sh, any sh script (including bash scripts that masquerade as sh) should still run when executed by bash. That means that changing the shebang line should be sufficient to fix a script suffering from this class of bug.

---

### Post by dwhitney67 on 2008-08-02
> **mssever said:**
> That's just masking the problem, so I think it's a bad idea. The real problem is that: a) some people equate sh with bash, and b) bash does a poor job of emulating sh.

For me, the Ubuntu OS is mere curiosity.  I've been using other *nix OSes in the past (HP, UnixWare, Solaris, Slackware, Mandrake, Red Hat, Fedora) and none of these OSes to the best of my recollection ever included dash.  /bin/sh is a link to /bin/bash... period!  So why does Ubuntu have to be different?

Please don't expect me to alter all my scripts to satisfy Ubuntu's way of doing things.  If I use a script written by a third-party, there is no way I am going edit the file to call out /bin/bash in lieu of /bin/sh.  Altering the file would in essence create a branch from its official version.  That's like throwing version control out the window.

Anyhow, this is a dead-end argument.  I just wish Ubuntu would join in with the industry standard way of doing things.

---

### Post by madams11 on 2008-08-02
> **dwhitney67 said:**
> Run the Synaptic manager:  System->Administration->Synaptic Package Manager

Once it is up and running, search for bash.

Then ensure that the it is indeed installed, and if not, install it.

On my system, I removed the /bin/sh link to dash, and changed it to point to /bin/bash.

I don't have a graphical interface installed on my server.  But, I did use aptitude, and tried to install bash.  It says it is installed, but I still can't find it.  I do know that /bin/bash is a symbolic link to /bin/dash at the moment.  And, I can't seem to install bash.

---

### Post by Rui Pais on 2008-08-02
> **madams11 said:**
> I don't have a graphical interface installed on my server.  But, I did use aptitude, and tried to install bash.  It says it is installed, but I still can't find it.  I do know that /bin/bash is a symbolic link to /bin/dash at the moment.  And, I can't seem to install bash.

Run from a command line:
```
dpkg -S /bin/bash
```
to see what package create the link (i doubt that the link it's part of any package anyway... maybe dash create it by default if bash it's not installed)

You can rm the symlink and install bash:
```
sudo rm /bin/bash
sudo apt-get install bash
```

hth

---

### Post by madams11 on 2008-08-02
> **Rui Pais said:**
> Run from a command line:
```
dpkg -S /bin/bash
```
to see what package create the link (i doubt that the link it's part of any package anyway... maybe dash create it by default if bash it's not installed)

You can rm the symlink and install bash:
```
sudo rm /bin/bash
sudo apt-get install bash
```

hth

Thanks for the suggestions.  Here are the results:

dpkg -S /bin/bash
bash: /bin/bash

Since bash is acually a link to dash, I'm not sure what this is telling me.

Then, when I rm bash, which is just a symlink, and then install, I get this:

apt-get install bash
...
bash is already the newest version.

This makes me think that bash might be installed somewhere else, but I sure can't find it.  Something else might be broken, because .bashrc tries to execute when I log in and it crashes when it comes to the first command that is unique to bash (instead of dash).  Do I have to remove dash first?  Any ideas?

---

### Post by mssever on 2008-08-02
> **madams11 said:**
> Thanks for the suggestions.  Here are the results:

dpkg -S /bin/bash
bash: /bin/bash

Since bash is acually a link to dash, I'm not sure what this is telling me.

Then, when I rm bash, which is just a symlink, and then install, I get this:

apt-get install bash
...
bash is already the newest version.

This makes me think that bash might be installed somewhere else, but I sure can't find it.  Something else might be broken, because .bashrc tries to execute when I log in and it crashes when it comes to the first command that is unique to bash (instead of dash).  Do I have to remove dash first?  Any ideas?
Something's screwy on your system. Both bash and dash are essential packages, which means that you shouldn't be able to mess with them without a big warning. The package manager is supposed to force you to jump through hoops to remove either one, because the absence of one or the other can cause major problems.

Several possible fixes:

[LIST]
[*]Reinstall bash: ```
sudo aptitude reinstall bash
```
[*]Upgrade to Hardy
[*]Download the bash source package, bump the version number, build the package, and install it.
[*]Grab a bash binary of the same version from somewhere and manually install it.
[/LIST]

---

### Post by madams11 on 2008-08-03
> **mssever said:**
> Something's screwy on your system. Both bash and dash are essential packages, which means that you shouldn't be able to mess with them without a big warning. The package manager is supposed to force you to jump through hoops to remove either one, because the absence of one or the other can cause major problems.

Several possible fixes:

[LIST]
[*]Reinstall bash: ```
sudo aptitude reinstall bash
```
[*]Upgrade to Hardy
[*]Download the bash source package, bump the version number, build the package, and install it.
[*]Grab a bash binary of the same version from somewhere and manually install it.
[/LIST]

Thanks mssever.  My system is still not quite right, but the aptitude reinstall bash worked in that I now have bash again.  This server was installed with Ubuntu 7.10 server 64-bit.  I didn't notice anything until I was running a script with #!/bin/sh which actually meant /bin/bash.  That is when I noticed that my /bin/bash was a link.

Now that bash is installed, I think I can get all of the login scripts to work again.  I really appreciate the help.

Mark

---

