---
title: "how to execute my c++ program w/o console"
date: 2007-12-22
forum: Programming Talk
---

### Post by fuego527 on 2007-12-22
Hi,

I just wrote a little c++ program to handle my media watching needs.  At the moment, it is very simple and all I want it to do is execute vlc using a filename parameter that is generated in my c++ code.  If I execute my program via the console using "./<my program name>" it works perfectly, vlc launches and plays the correct media file.  However, when I doubleclick my executable in KDE or gnome it does not do anything.  It doesn't even hang as "ps -A | grep <my program name>" reveals nothing.  Anyone know what the deal is?  Oh, it knows that my program is executable when I right click and click on properties and the "is executable" box is checked in the permissions tab.  I am using the c++ function system() if that matters (all i can think of).  Any help is greatly appreciated.

---

### Post by dwhitney67 on 2007-12-22
In Gnome, right-click on your desktop's background, and select Create Launcher...

Then fill in the fields.  It would be helpful it you were to provide your code, because the choice between launching an "Application" versus launching an "Application in Terminal" matter.

If you system call is launching VLC in the background, then using "Application" will probably suffice.

Good luck.

---

### Post by fuego527 on 2007-12-23
Thanks a lot.  I had previously tried launcher choosing "Application".  The reason that it did not work was that it was not recognizing my environment variables.  When I tried "Application in Terminal", it printf'ed a null where a path should have been which tipped me off.  So, I have figured out (read) that since I was not executing through bash, the bash envvars were not set (makes sense).  So, I now have changed the command to include an env command.  This is not acceptable, I guess I will just have to write out to a file.  Well, anyways...thanks a lot man.

---

### Post by dwhitney67 on 2007-12-23
You can get an environment variable (within a C or C++ program) using the getenv() C-library function.

```
$  man getenv
```

---

### Post by fuego527 on 2007-12-23
Yeah, I was doing that.  But when I launch my app through the app launcher, getenv returns NULL because the app is not being executed within the bash context and the variables are apparently shell-specific.  Can I save them in a shell-independant manner?

---

### Post by dwhitney67 on 2007-12-23
The bash environment variables that you wish to keep and have available each time you log in should be defined in your ~/.bashrc file.

For instance:

```
export MY_ENV_VAR=value
```

After you are done editing the ~/.bashrc file, you will need to "source" the changes:

```
$ source ~/.bashrc
```

Here's a small C++ program that will output the environment variable:

```
#include <iostream>

int main()
{
  std::cout << getenv( "MY_ENV_VAR" ) << std::endl;
  return 0;
}
```

---

