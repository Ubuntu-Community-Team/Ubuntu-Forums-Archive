---
title: "[SOLVED] getenv() not working with launcher - works with command line"
date: 2008-08-20
forum: Programming Talk
---

### Post by anewguy on 2008-08-20
Thanks to those who answered my previous post on how to get the getenv() call set up correctly in C for Ubuntu.  It works fine from the command line.  However, when I set up a desktop launcher for the program, then the environment variable value returned is NULL instead of the actual value.  Not understanding exactly what this actually does, I tried putting "env" in front of the launcher string as I remember seeing that in some post.  That didn't help either.

So, are environment variables set in the .bashrc file only available via the command line, or is there a way to make them available to a program that is started via a desktop launcher?  If not, what kind of variable, and how would I set it up, would I need?

Thank you in advance! :)

---

### Post by dwhitney67 on 2008-08-20
I presume that you defined your environment variable in ~/.bashrc or other similar file.

Anyhow, to get Gnome (or KDE) to add this variable to your runtime environment, log out and then log back in.  This should resolve your problem.  I tested it and it worked for me.

---

### Post by anewguy on 2008-08-21
Have already logged out and back in several times.  Each time, if I use a terminal window and do "export" it shows my variable defined.  The program still doesn't see it when using a launcher versus the command line.

EDIT:  Forgot to mention that this has been discussed in several previous posts to various forums when I did a net search.  The only "solution" that was ever mentioned was to create a script and in that script define the variable, then run the script from the launcher.  This seems unnecessary to me - I should be able to get the variable value inside my program when run from the launcher.

---

### Post by anewguy on 2008-08-21
> **dwhitney67 said:**
> I presume that you defined your environment variable in ~/.bashrc or other similar file.

Anyhow, to get Gnome (or KDE) to add this variable to your runtime environment, log out and then log back in.  This should resolve your problem.  I tested it and it worked for me.

Are you running a program from a launcher and in that program doing a getenv(varname)?  I can see the variable fine if run from the command line, and can see the variable via "export".  The program just gets a NULL - I'm assuming it doesn't even know the variable exists so getenv() is returning the NULL.

---

### Post by dribeas on 2008-08-21
> **anewguy said:**
> Thanks to those who answered my previous post on how to get the getenv() call set up correctly in C for Ubuntu.  It works fine from the command line.  However, when I set up a desktop launcher for the program, then the environment variable value returned is NULL instead of the actual value.

[Environment variables]("https://help.ubuntu.com/community/EnvironmentVariables#Session-wide%20environment%20variables"). Where are you setting your variables? Try setting them in ~/.profile.

---

### Post by dwhitney67 on 2008-08-21
> **anewguy said:**
> Are you running a program from a launcher and in that program doing a getenv(varname)?  I can see the variable fine if run from the command line, and can see the variable via "export".  The program just gets a NULL - I'm assuming it doesn't even know the variable exists so getenv() is returning the NULL.
I wrote this trivial program:
[PHP]#include <stdlib.h>
#include <stdio.h>

int main()
{
  const char *myvar = getenv( "MYVAR" );

  if ( myvar )
  {
    printf( "MYVAR = %s\n", myvar );
  }
  else
  {
    printf( "MYVAR is NOT defined!\n" );
  }

  return 0;
}[/PHP]
I then defined MYVAR in ~/.bashrc, then sourced the .bashrc to test the file from the command line.  The results are that it worked.
```
export MYVAR="Hello World"
```
Next I created a Gnome launcher that runs the application in a terminal.  It failed when I tested!  In other words, MYVAR was not defined.

I logged out of my Gnome session, and I logged back in... and voila the launcher that runs my simple application starts working.

---

### Post by ilrudie on 2008-08-21
I'm not sure how getenv() works but I'd guess it returns the environment variables from your shell.  If you don't launch a shell there are no variables defined and they will all return null.

Guess this is irrelavent since you got it working.

---

### Post by dwhitney67 on 2008-08-21
Just to verify I wasn't on crack, once again I wrote a simple application, and tested it by running as an "Application" and as an "Application in Terminal".  In both cases it worked as expected.

I think the secret is to log out, and log back in so that Gnome (maybe GDM) can source the user's ~/.bashrc.

---

### Post by anewguy on 2008-08-21
> **dwhitney67 said:**
> Just to verify I wasn't on crack, once again I wrote a simple application, and tested it by running as an "Application" and as an "Application in Terminal".  In both cases it worked as expected.

I think the secret is to log out, and log back in so that Gnome (maybe GDM) can source the user's ~/.bashrc.

No suspicion of alternative forms of recreation :) .  I just haven't been able to get it to work for some reason.  I added the variable to /etc/environment and it worked, so went checking some more but still haven't figured out what I must be doing wrong.

Thanks for your input!!  :)

---

### Post by anewguy on 2008-08-21
Here's what I am doing, having incorporated your code so as to make it easy to compare:

In the source program (btw - it's a gtk program):

    char wrkpath[256];
 
    gtk_init (&argc, &argv);

    const char *myvar = getenv( "CVSUTIL" );
    if ( myvar )
    {
      printf( "MYVAR = %s\n", myvar );
    }
    else
    {
      printf( "MYVAR is NOT defined!\n" );
    }

and further into the program:

/*     define, load and show the camcorder picture    */

    sprintf(wrkpath,"%s%s",myvar,"camcorder.jpg");
printf("wrkpath: %s\n",wrkpath);
    image1 = gtk_image_new_from_file(wrkpath);
    gtk_box_pack_start(GTK_BOX (hbox1),
                       image1,
                       FALSE,
                       FALSE,
                       0);
    gtk_widget_show(image1);




/*     define, load and show the still camera picture     */

    sprintf(wrkpath,"%s%s",myvar,"camera.jpg");
printf("wrkpath: %s\n",wrkpath);
    image2 = gtk_image_new_from_file(wrkpath);
    gtk_box_pack_start(GTK_BOX (hbox1),
                       image2,
                       FALSE,
                       FALSE,
                       0);
    gtk_widget_show(image2);



Here's the end of my .bashrc file:


# define the path to cvsutil
export CVSUTIL="/home/dave/cvs/new-unified-codeset/cvsutil/src/"


I have logged out and back in.


When run from the command line it works - see the attached .png file.

I modified the launcher slightly to say it's an terminal application so I could get the output on the screen at run-time.  It still doesn't work - see the attached .png file.

If I put the variable in /etc/environment it works.


Any help would be greatly appreciated!  :)
Dave

---

### Post by dwhitney67 on 2008-08-21
I don't know what to say; here's a listing of my ~/.bashrc file on my Ubuntu system.  Maybe for some reason your ~/.bashrc file is not being sourced when you log in??
```
# .bashrc

# Source global definitions
#if [ -f /etc/bash.bashrc ]; then
#       . /etc/bash.bashrc
#fi

export PATH=./:~/Bin:/sbin:$PATH

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD/$HOME/~}\007"'
    ;;
*)
    ;;
esac

# User specific aliases and functions
PS1='\u@\h:\[\033[01;34m\]\w\[\033[00m\]] \n> '

# enable color support of ls and also add handy aliases
if [ "$TERM" != "dumb" ]; then
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
fi

if [ -f /etc/bash_completion ]; then
        . /etc/bash_completion
fi

export MYVAR="I'm here!"
```

---

### Post by anewguy on 2008-08-21
Okay, being kinda stupid here, what do you mean by "sourced"? 

Also - is there some command in Ubuntu that would be GUI based (e.g., I don't want to open a command line) to see what variables are define?  I'm starting to wonder if there is something I'm missing (perhaps this is what you mean with the "sourced" stuff?) whereby the variables are only defined when you open a terminal window, but not when you just use a launcher (like a step is being skipped in the launcher example?).

EDIT:  Is there a way to tell the scope of a variable?

Thanks
Dave

---

### Post by anewguy on 2008-08-21
Here's another dumb question - do I need something special in my .profile file?  Just glancing at it it would appear that the .bashrc is only looked at when going to a shell (the command line).  OR - is there a way on the launcher itself to make it "run" a shell for the application?

Thanks again
Dave

Here's my .profile file:

# ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/profile
#umask 022

# if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f ~/.bashrc ]; then
	. ~/.bashrc
    fi
fi

# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi



My launcher simply says:

/home/dave/cvs/new-unified-codeset/cvsutil/src/cvsutil_gtk

---

### Post by dwhitney67 on 2008-08-21
You can source a file with either "source" or with "."; for example:
```
$ source ~/.bashrc
$ . ~/.bashrc
```
Your ~/.profile look ok.  I have no idea how Ubuntu deals with a login; in other words I do not know if Ubuntu's start-up scripts source your ~/.bashrc or ~/.profile, or both!

I have been able to get the little exercise you are trying to resolve to work on both my Fedora 9 and Ubuntu 8.04 systems.  Something, somewhere, is different on your system.  I don't know what it is.

Perhaps instead of printing out the value of "myvar", you can create a file in the /tmp directory.  For instance, if myvar is defined:
[PHP]system( "touch /tmp/YES_CVSUTIL" );[/PHP]
and if it does not:
[php]system( "touch /tmp/NO_CVSUTIL" );[/php]

P.S.  From the command-line, you can use "env" to examine all environment variables.

---

### Post by petermholmes on 2008-08-21
#include <stdio.h>
#include <stdlib.h>

main(int argc, char **argv)
{
    printf("%s\n", getenv("HOSTNAME"));
}


cc -g a.c
a.out
Segmentation fault (core dumped)


Something is *seriously* screwed up.  I'm running Ubuntu 7.10 with the latest updates.  I also caught the C compiler tossing away a variable on the stack before I was done using it.  If I do cc --version, I get:

cc (GCC) 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)

---

### Post by anewguy on 2008-08-21
Well, this will probably be the wrong way, but I did get it to work.  I got to thinking - just having the launcher execute the program doesn't (as far as I know) invoke the bash shell - hence the variable would probably not be defined at that level.  So, I created the following shell script:

#!/bin/bash
cd /home/dave/cvs/new-unified-codeset/cvsutil/src
./cvsutil_gtk

Then I changed the launcher to the following:

bash -i /home/dave/cvs/new-unified-codeset/cvsutil/src/cvsutil_gtk.sh

It wouldn't work until I added the -i for interactive mode - now it works fine when run as a terminal application from a launcher.  I'm going to try just making it an application launcher (no terminal) and see if that works as well.

EDIT:  Works as just an application launcher as well.  I guess I am learning something here - the variables defined in the4 .bashrc file must not be "global" to the user but instead in some sort of "bash" pool.  When I put the variable definition in /etc/environment it obviously became a system-wide variable, not a "bash" shell variable.  So, when I changed to a bash "interactive" shell script it then was running in bash shell so it picked up the bash variable "pool".

Does this make any sense or am I just way off base?

peterholmes:  I think you need to define the variable as noted in the code provided by dhwitney and do the getenv into that variable first.  I had the exact same problem until I followed his definition for the variable and did the getenv into it.  Also, I could never directly print from the getenv - it had to be a "receiving" variable.

---

### Post by petermholmes on 2008-08-21
If the variable is defined in bash, it should be available to a program run in a bash terminal.

From  "man bash":

HOSTNAME
   Automatically set to the name of the current host.

It *used* to work.  It no longer works.

---

### Post by dwhitney67 on 2008-08-21
This works for me, if I run it as an "Application in (a) Terminal":
[PHP]#include <stdlib.h>
#include <unistd.h>
#include <stdio.h>

int main()
{
  printf( "%s\n", getenv( "HOSTNAME" ) );
  sleep(2);
  return 0;
}[/PHP]
If it doesn't work under your OS, then reinstall it.  This works for Fedora 9 and Ubuntu 8.04.

---

### Post by petermholmes on 2008-08-21
Easier said than done, given that (at last count...a couple of weeks ago) 8.04 won't either fresh install or upgrade on an Inspiron 530.  Any other suggestions?

---

### Post by dwhitney67 on 2008-08-21
> **petermholmes said:**
> Easier said than done, given that (at last count...a couple of weeks ago) 8.04 won't either fresh install or upgrade on an Inspiron 530.  Any other suggestions?
Try Fedora 9.

---

### Post by petermholmes on 2008-08-21
Guess I'll have to.  Given its popularity I hate to give up on Ubuntu, but it's not as if it's ever been programmer friendly anyway.  Thanks for your input.

---

