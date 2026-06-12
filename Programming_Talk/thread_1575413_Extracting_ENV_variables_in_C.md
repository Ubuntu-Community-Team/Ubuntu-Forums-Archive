---
title: "Extracting ENV variables in C"
date: 2010-09-15
forum: Programming Talk
---

### Post by DaGarver on 2010-09-15
Hey, guys. I'm trying to figure out how to write a wrapper for env in C/C++. I have a good idea of how to do it; my implementation involves storing all of the environment variables at construction of an ENVro in an array. However, I'm struggling with how to pull out all the environment variables.

Is there a method in the standard libraries to do this that I'm just missing? Or is it something I'll have to write myself (and, if so, how would I do this)? I definitely don't want to hard code the variables, since the environment can change at any time. 

Thanks for your help.

---

### Post by Bachstelze on 2010-09-15
You can use the [environ]("http://www.opengroup.org/onlinepubs/9699919799/functions/exec.html") external variable:

```
firas@aoba ~ % cat env.c
#include <stdio.h>

int main(void)
{
    extern char **environ;
    int i;

    for (i=0; environ[i] != NULL; i++)
        printf("%s\n", environ[i]);

    return 0;
}

firas@aoba ~ % gcc -o env env.c
firas@aoba ~ % ./env 
PATH=/usr/bin:/bin:/usr/sbin:/sbin:/usr/local/bin:/usr/texbin:/usr/X11/bin:/usr/local/sbin:/Library/OpenSC/bin
TMPDIR=/var/folders/7u/7uy5ptIfGHuZ0I3ojwJgME+++TI/-Tmp-/
SHELL=/bin/zsh
HOME=/Users/firas
USER=firas
LOGNAME=firas
DISPLAY=/tmp/launch-N2UBCi/org.x:0
SSH_AUTH_SOCK=/tmp/launch-7d9le2/Listeners
Apple_PubSub_Socket_Render=/tmp/launch-9ajbue/Render
COMMAND_MODE=unix2003
__CF_USER_TEXT_ENCODING=0x1F5:0:0
TERM_PROGRAM=Apple_Terminal
TERM_PROGRAM_VERSION=273
LANG=en_GB.UTF-8
TERM=xterm-color
SHLVL=1
PWD=/Users/firas
OLDPWD=/Users/firas
CLICOLOR=1
LSCOLORS=Exfxcxdxbxegedabagacad
EDITOR=vim
_=/Users/firas/./env

```

You might need to include unistd.h to get it.

---

### Post by dwhitney67 on 2010-09-15
This probably is a cleaner way:
```

#include <iostream>

int main(int argc, char** argv, char** envp)
{
   for (; *envp != NULL; ++envp)
   {
      std::cout << *envp << std::endl;
   }

   return 0;
}

```
As for the environment variables, they are represented using key/value pairs.  An STL map would do wonders for storage.

Consider storing each envp value into a string, then using find_first_of() to determine where the equals sign is at; the string to the left of the equals sign is the key; the string to the right is the value.  Something like:
```

   ...
   std::string envstr = *envp;
   size_t      equals = envstr.find_first_of('=');
   std::string key    = envstr.substr(0, equals);
   std::string val    = envstr.substr(equals + 1);
   ...

```

---

### Post by slavik on 2010-09-16
> **dwhitney67 said:**
> This probably is a cleaner way:
```

#include <iostream>

int main(int argc, char** argv, char** envp)
{
   for (; *envp != NULL; ++envp)
   {
      std::cout << *envp << std::endl;
   }

   return 0;
}

```
As for the environment variables, they are represented using key/value pairs.  An STL map would do wonders for storage.

Consider storing each envp value into a string, then using find_first_of() to determine where the equals sign is at; the string to the left of the equals sign is the key; the string to the right is the value.  Something like:
```

   ...
   std::string envstr = *envp;
   size_t      equals = envstr.find_first_of('=');
   std::string key    = envstr.substr(0, equals);
   std::string val    = envstr.substr(equals + 1);
   ...

```
You realize your code is C++, not C, right? :P

---

### Post by dwhitney67 on 2010-09-16
> **slavik said:**
> You realize your code is C++, not C, right? :P

And?

(Please reread the OP's original thread, not just the title.)

---

### Post by nvteighen on 2010-09-16
> **dwhitney67 said:**
> And?

(Please reread the OP's original thread, not just the title.)

Well, it says "C/C++" (sic!), something that doesn't exist at all... but could be interpreted as "C or C++"...

---

### Post by dwhitney67 on 2010-09-16
> **nvteighen said:**
> ... but could be interpreted as "C or C++"...

Generally it is (in the real world)... sigh!

---

### Post by SledgeHammer_999 on 2010-09-16
Maybe I didn't understand exactly what you're trying to do, but shouldn't you use [putenv()](http://www.cprogramming.com/fod/putenv.html) and [getnv()](http://www.cprogramming.com/fod/getenv.html)?

---

