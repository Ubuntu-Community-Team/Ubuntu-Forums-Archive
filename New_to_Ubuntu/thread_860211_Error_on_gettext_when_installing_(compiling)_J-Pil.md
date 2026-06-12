---
title: "Error on gettext when installing (compiling) J-Pilot"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by Paddy Landau on 2008-07-15
I've downloaded the latest J-Pilot from the [website]("http://www.jpilot.org/").

I attempted to compile it according to instructions:
```
./configure --prefix=/usr
```This failed with an error:
```
configure: error: GNU gettext tools not found; required for intltool
```Yet, if I type in a terminal:
```
gettext --help
```then I get the help for the gettext. So, to me, it looks as though gettext is installed.

What have I done wrong?

---

### Post by Paddy Landau on 2008-07-15
OK, I finally got past the first statement after much guesswork.

The [instructions]("http://www.jpilot.org/docs/manual.html") say:
> To compile and install do the following:
./configure --prefix=/usr
make
make install
jpilotI've done the first statement (./configure --prefix=/usr).

However, when I try the next statement (make), the response is, "make: *** No targets specified and no makefile found. Stop."

Could someone explain to me what exactly I'm supposed to do? I've read "man make" but I don't make much sense of that, unfortunately.

---

### Post by beholdyr on 2008-07-15
Can you post the output of: ```
/.configure --prefix=/usr
``` It seems as if that has error'd out somehow.

---

### Post by Paddy Landau on 2008-07-15
> **beholdyr said:**
> Can you post the output of: ```
/.configure --prefix=/usr
``` It seems as if that has error'd out somehow.
Oh dear, it did error. I thought I had solved that problem.
```
configure: error: Could not find the pilot-link header files
```I'll see if I can find where to download the pilot-link header files.

Thanks for the heads-up.

---

### Post by beholdyr on 2008-07-15
You have to install pilot-link-devel: ```
sudo apt-get install pilot-link-devel
```

---

### Post by Paddy Landau on 2008-07-15
Thanks for the suggestion. The results were:
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package pilot-link-develI downloaded pilot-link from the recommended website
[http://www.pilot-link.org/](http://www.pilot-link.org/)

Following the instructions, I ran "./configure". This worked.

Then I ran "make" as instructed. This produced a fair amount of output, finishing with:
> Making all in tests
make[2]: Entering directory `/home/paddy/Downloads/pilot-link-0.12.3/tests'
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../include -I../include     -g2 -Wall -MT contactsdb-test.o -MD -MP -MF ".deps/contactsdb-test.Tpo" -c -o contactsdb-test.o contactsdb-test.c; \
    then mv -f ".deps/contactsdb-test.Tpo" ".deps/contactsdb-test.Po"; else rm -f ".deps/contactsdb-test.Tpo"; exit 1; fi
contactsdb-test.c:28:18: error: popt.h: No such file or directory
contactsdb-test.c: In function ‘main’:
contactsdb-test.c:352: warning: ‘pilot_connect’ is deprecated (declared at ../include/pi-header.h:31)
make[2]: *** [contactsdb-test.o] Error 1
make[2]: Leaving directory `/home/paddy/Downloads/pilot-link-0.12.3/tests'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/paddy/Downloads/pilot-link-0.12.3'
make: *** [all] Error 2
I'm afraid I have no clue where to go from here.

Do you have any ideas?

---

### Post by beholdyr on 2008-07-15
Search for pilot in synaptic, and see if anything comes up with "devel" or "development" or "header files". That's the only thing I can come up with, as compiling all of this will become an even bigger headache to deal with.

---

### Post by Paddy Landau on 2008-07-15
> **beholdyr said:**
> Search for pilot in synaptic, and see if anything comes up with "devel" or "development" or "header files". That's the only thing I can come up with, as compiling all of this will become an even bigger headache to deal with.
The nearest I found was libgnome-pilot2-dev.

It worked! JPilot is now installed.

Thank you so much.

---

