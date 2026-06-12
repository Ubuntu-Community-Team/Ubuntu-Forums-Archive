---
title: "secure linux programming question"
date: 2009-06-22
forum: Programming Talk
---

### Post by cmay on 2009-06-22
hi .
i been reading in this 
[http://www.dwheeler.com/secure-programs/Secure-Programs-HOWTO/index.html](http://www.dwheeler.com/secure-programs/Secure-Programs-HOWTO/index.html)

i have a few questions. 

one is the way you make scripts and the path. 

on my system which is ubuntu jaunty when i compile and run a c program it is done on commandline and looks like this. 
```
gcc -o hello ./hello0.c
```and can be run by 
```
./hello
```i do not need to give any permissions to do this. 

if i write a shell script i need to make the file  executable ```
chmod 755 ./script
``` and run it by > ./script but i can not run it by just issuing the command ```
scriptname.sh 
``` if the script is located in the home directoy. 

as far as i understand it up to now there is some security reason why not so many systems has the current directory  in path   so you need to execute script by permissions for the script and placed  when in home folder so you need to put ./ in front of it .  

to prevent security holes  there is in shellscripts  a - option you can use to prevent the script to be fooled into taking parameters that can be exploited. 

now for the c program i write which can be a hello world program can that not be fooled into taking parameters the same way as a shell script can . 

 howcome a c program does not need to have permissions set to execute after compiling it . 

can c programs also be misused the way shell scripts can or is it something else when it is a compiled program . 

 or other languages other than the shell scripting langauages. perl or pyton as example. 

 i do not understand nor care that much how exactly the procces is  to gain rights as root coming from a cracking attack but i am worried enough to when i write my own small things that  i dont exactly learn to invite all sorts of abuse unintentialy - 

what is the best practie of writing scripts and programs and is it dangerus to change path settings as they are in the default ubuntu setup. by setting the  .  as current directory in path. this i thought about once as it would make my every day a bit more easy nbot having to use the ./ everytime i compile or run scripts but then i started to read about these things. i dont have that much time to really dig into this at the moment but i would like to more about it anyway.

---

### Post by lensman3 on 2009-06-23
Create a ~/bin directory in your home directory.  Put you scripts and programs in there.  Add ~/bin to the $PATH so that you can run those programs from where ever you are on the system.  The $PATH will have to modified so that .bash_profile and looks like "PATH=$PATH:$HOME/bin".  Make the changes to .bash_profile then "source" that file.  Put your programs into a ~/bin directory so that the $HOME doesn't get cluttered.

Change the permissions of the ~/bin directory to 700 or rwx------, so that only your user ID can execute those scripts/programs.  That way the "attackers" can't see what is in the ~/bin directory.

In answer to you question why does "gcc" know to make a file executable, that is what is does and somebody sometime added chmod to the gcc command so that it would automatically change the permissions.  Shell scripts can be just data files, so the programmer would have to change chmod to +x to get it to execute without calling it from "sh -x <script>".

Hope this helps.

---

### Post by Dill on 2009-06-23
```
PATH=$PATH:~
```

Cheers,
Dill

---

### Post by cmay on 2009-06-23
> **lensman3 said:**
> Create a ~/bin directory in your home directory.  Put you scripts and programs in there.  Add ~/bin to the $PATH so that you can run those programs from where ever you are on the system.  The $PATH will have to modified so that .bash_profile and looks like "PATH=$PATH:$HOME/bin".  Make the changes to .bash_profile then "source" that file.  Put your programs into a ~/bin directory so that the $HOME doesn't get cluttered.

Change the permissions of the ~/bin directory to 700 or rwx------, so that only your user ID can execute those scripts/programs.  That way the "attackers" can't see what is in the ~/bin directory.

In answer to you question why does "gcc" know to make a file executable, that is what is does and somebody sometime added chmod to the gcc command so that it would automatically change the permissions.  Shell scripts can be just data files, so the programmer would have to change chmod to +x to get it to execute without calling it from "sh -x <script>".

Hope this helps.

thanks a lot. . this means a lot to me.

---

### Post by unutbu on 2009-06-23
Under Ubuntu, each user gets a default ~/.profile which contains
```

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi
```

So you do not need to add
```

PATH=$PATH:$HOME/bin
```

to your .bashrc or .bash_profile. It will be added for free if you 
```

mkdir ~/bin
```

(You must log out and log back in for the PATH to be updated.)

---

