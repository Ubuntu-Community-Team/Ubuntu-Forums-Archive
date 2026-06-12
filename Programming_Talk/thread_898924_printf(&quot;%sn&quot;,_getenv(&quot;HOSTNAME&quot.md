---
title: "printf(&quot;%s\n&quot;, getenv(&quot;HOSTNAME&quot;)); fails"
date: 2008-08-23
forum: Programming Talk
---

### Post by petermholmes on 2008-08-23
In a bash terminal using the editor of your choice enter:

#include <stdio.h>
#include <stdlib.h>

int main(int argc, char **argv)
{
    printf("%s\n", getenv("HOSTNAME"));
    return(0);
}

Save it as a.c and, at the command line prompt enter:

gcc -g a.c
./a.out

In Fedora 9 it works, in OpenSuse 11 it works, in Ubuntu 8.04 (fresh install + build-essential from Synaptic) it generates a segmentation fault.

---

### Post by jinksys on 2008-08-23
You get a segmentation fault because getenv doesn't find HOSTNAME in the environment variables list, so it returns NULL.  BOOM.

---

### Post by jinksys on 2008-08-23
It seems Ubuntu isn't exporting the variable like it should.  I put "export HOSTNAME" in my /etc/bash.bashrc and the code works.  I filed a bug report with ubuntu, it would help if you commented in the report stating you are also having this problem.

[https://bugs.launchpad.net/ubuntu/+source/bash/+bug/260779](https://bugs.launchpad.net/ubuntu/+source/bash/+bug/260779)

---

### Post by ghostdog74 on 2008-08-23
for reliable results , you should use C libraries for getting hostname. [Example:gethostname ](http://rabbit.eng.miami.edu/info/functions/internet.html)

---

### Post by dwhitney67 on 2008-08-24
The C program in the OP is doing its "job".

The only "problem" with Ubuntu (and maybe with some other *nix's) is that 'HOSTNAME' is not set in the environment.

To verify if 'HOSTNAME' is set or not, use:
```
env | grep HOSTNAME
```

The original code could perhaps be written better to resemble:
[PHP]#include <stdlib.h>
#include <stdio.h>

int main()
{
  const char *hostname = getenv( "HOSTNAME" );

  printf( "%s\n", (hostname ? hostname : "HOSTNAME not defined!") );

  return 0;
}[/PHP]

---

### Post by ghostdog74 on 2008-08-24
> **dwhitney67 said:**
> 
```
env | grep HOSTNAME
```

or ```

test -n  ${HOSTNAME} 

```

---

### Post by petermholmes on 2008-08-24
> **jinksys said:**
> It seems Ubuntu isn't exporting the variable like it should.  I put "export HOSTNAME" in my /etc/bash.bashrc and the code works.  I filed a bug report with ubuntu, it would help if you commented in the report stating you are also having this problem.

[https://bugs.launchpad.net/ubuntu/+source/bash/+bug/260779](https://bugs.launchpad.net/ubuntu/+source/bash/+bug/260779)

Done.  Thank you for your help.

---

### Post by Bachstelze on 2008-08-24
> **jinksys said:**
> It seems Ubuntu isn't exporting the variable like it should.

Why should it? Just because (some) other distros do it is not a valid answer. Debian doesn't (obviously), Gentoo doesn't, OpenBSD and FreeBSD don't, Solaris doesn't, HP-UX doesn't...

This is **not** an acceptable way of getting the hostname, see post #4, or the [FONT="Courier New"]hostname[/FONT] command.

---

### Post by petermholmes on 2008-08-24
> **dwhitney67 said:**
> The C program in the OP is doing its "job".

The only "problem" with Ubuntu (and maybe with some other *nix's) is that 'HOSTNAME' is not set in the environment.


The only problem is that you won't RTFM.  "set | grep HOSTNAME" works, "env | grep HOSTNAME" doesn't.

---

### Post by Bachstelze on 2008-08-24
> **petermholmes said:**
> The only problem is that you won't RTFM.  "set | grep HOSTNAME" works, "env | grep HOSTNAME" doesn't.

First, this acronym is not welcome here. Please refrain from using it again.

Second, you're the one who's being wrong here.

---

### Post by dwhitney67 on 2008-08-24
> **petermholmes said:**
> The only problem is that you won't RTFM.  "set | grep HOSTNAME" works, "env | grep HOSTNAME" doesn't.
Whoop tee doo!

It would seem that you need "env" to work, not "set".

Anyhow, I fully understand the problem and I have fixed it on my Ubuntu system.  Now when I, or anyone else for that matter, run "env | grep HOSTNAME" or write a simpleton program like you posted in your OP, I am able to obtain the system's HOSTNAME.

---

### Post by psychengchao on 2009-12-25
change      printf("%s\n", getenv("HOSTNAME"));
to        printf("%s", getenv("HOSTNAME"));
it is works.

---

### Post by chcolemanjr on 2010-11-29
I know this thread is a few years old, but if you're like me and reading it for the first time this is still an issue as of Ubuntu 10.10.

The official response is, "bash doesn't export HOSTNAME by default. we didn't change this behaviour" and "Won't fix".

To get around this problem I added an export statement for HOSTNAME to my .bashrc and the code I have to compile that contains getenv( "HOSTNAME" ) returns successfully now.

-Chuck

---

