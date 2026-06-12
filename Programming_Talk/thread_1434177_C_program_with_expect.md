---
title: "C program with expect"
date: 2010-03-19
forum: Programming Talk
---

### Post by nocturnal1 on 2010-03-19
I'am using Karmic and I've installed Expect with tcl. It's works fine and I've tested it using the spawn command to launch gedit and other programs. I also have Glade and gcc installed. I can't figure out how to use libexpect in a C program. I get the error: expect.h no such file or directory.  I can see that file in:  /usr/lib/tcl8.3
 Could someone please explain how to do this.
I have test.c saved to the desktop.

```

#include <stdio.h>
#include <stdlib.h>
#include <expect.h>

int main (int argc, char *argv[])
{

spawn gedit;
return 0;

}

```

---

### Post by roccivic on 2010-03-20
not sure, but did you try
```
#include <tcl8.3/expect.h>
```?

---

### Post by Tony Flury on 2010-03-20
when you say you can't get it to work - are you getting error messages ? if so - what are they

---

### Post by nocturnal1 on 2010-03-20
Tony Flurry as I said "I get the error: expect.h no such file or directory"
[roccivic]("http://ubuntuforums.org/member.php?u=560306"), thank you I'll try that but this morning my system won't boot. 
I have Ubuntu installed to a Seagate 500GB USB drive. It was working then stopped after about two weeks and a couple of updates. I reinstalled it and followed someone's thread in the forums and added all_generic_idle to the grub boot. It worked the first time but now it won't. I don't even have the thread because it was on the external drive. Now I'll have to find it again.

---

### Post by nocturnal1 on 2010-03-20
Well I've got the system back up again (It's a hack, but that's for another forum)
Through Synaptic, I've installed:

expect-tcl8.3
expect-tcl8.3-dev

Synaptic lists the following properties:

/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/expect-tcl8.3-dev
/usr/share/doc/expect-tcl8.3-dev/changelog.gz
/usr/share/doc/expect-tcl8.3-dev/ChangeLog.gz
/usr/share/doc/expect-tcl8.3-dev/NEWS.gz
/usr/share/doc/expect-tcl8.3-dev/copyright
/usr/share/doc/expect-tcl8.3-dev/changelog.Debian.gz
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/expect_cryptdir.1.gz
/usr/share/man/man1/expect_dislocate.1.gz
/usr/share/man/man1/expect_kibitz.1.gz
/usr/share/man/man1/expect_mkpasswd.1.gz
/usr/share/man/man1/expect_multixterm.1.gz
/usr/share/man/man1/expect_passmass.1.gz
/usr/share/man/man1/expect_tknewsbiff.1.gz
/usr/share/man/man1/expect_unbuffer.1.gz
/usr/share/man/man1/expect_xkibitz.1.gz
/usr/share/man/man1/expect_autoexpect.1.gz
/usr/share/man/man1/expect_decryptdir.1.gz
/usr/bin
/usr/bin/expect_autoexpect
/usr/bin/expect_autopasswd
/usr/bin/expect_cryptdir
/usr/bin/expect_decryptdir
/usr/bin/expect_dislocate
/usr/bin/expect_ftp-rfc
/usr/bin/expect_kibitz
/usr/bin/expect_lpunlock
/usr/bin/expect_mkpasswd
/usr/bin/expect_multixterm
/usr/bin/expect_passmass
/usr/bin/expect_rftp
/usr/bin/expect_rlogin-cwd
/usr/bin/expect_timed-read
/usr/bin/expect_timed-run
/usr/bin/expect_tknewsbiff
/usr/bin/expect_tkpasswd
/usr/bin/expect_unbuffer
/usr/bin/expect_weather
/usr/bin/expect_xkibitz
/usr/bin/expect_xpstat
/usr/include
/usr/include/tcl8.3
/usr/include/tcl8.3/expect.h
/usr/include/tcl8.3/expect_tcl.h
/usr/include/tcl8.3/expect_comm.h
/usr/include/tcl8.3/tcldbg.h
/usr/lib
/usr/lib/libexpect.a
/usr/lib/libexpect.so
/usr/lib/libexpect5.43.so

When I compile with: gcc -I-/usr/lib/tcl8.3 test1.c -o test1
I get: 
test1.c: In function &#8216;main&#8217;:
test1.c:8: error: &#8216;spawn&#8217; undeclared (first use in this function)
test1.c:8: error: (Each undeclared identifier is reported only once
test1.c:8: error: for each function it appears in.)
test1.c:8: error: expected &#8216;;&#8217; before &#8216;gedit&#8217;

I think it's exp_spawn??
The only example I can find is too complicated and just has more problems.
chesslib.c 
[http://programming.ccp14.ac.uk/expect/example/](http://programming.ccp14.ac.uk/expect/example/)

Does anyone have a simple example that works just to launch an app?

---

### Post by MadCow108 on 2010-03-21
you can't use the tcl expect syntax in C
you have to use the C interface:
[http://linux.die.net/man/3/libexpect](http://linux.die.net/man/3/libexpect)

---

### Post by nocturnal1 on 2010-03-21
So I need to install just Expect without Tcl?
When I do that I don't have the file expect.h. I guess it's in the archive libexpect.a. 
So I need to extract and install it? You do I do that?
Can you give me an example of a very short program and compilier options please.

---

### Post by MadCow108 on 2010-03-21
what do you actually want to do?
I have never used expect. I just suspect that your syntax above is wrong (because good C libraries usually don't mess up the namespace with structs named *spawn*)

If you don't know C its probably best to follow the advice in the manpage:
> 
An alternative to this library is the expect program. expect interprets scripts written in a **high-level language** which direct the dialogue. In addition, the user can take control and interact directly when desired. If it is not absolutely necessary to write your own C program, it is much easier to use expect to perform the entire interaction. It is described further in the following references:

I guess that program will accept the syntax you tried to use in C

[http://linux.die.net/man/1/expect](http://linux.die.net/man/1/expect)

---

### Post by nocturnal1 on 2010-03-21
I would eventually like to create a user interface in Glade/GTK+ which  communicates with a wireless serial device server. Probably this one.
[http://www.quatech.com/pdf/ab_enterprise_wds.pdf](http://www.quatech.com/pdf/ab_enterprise_wds.pdf)

I have Glade 3 and GTK+ installed and have some basic programs working.

The larger manufactures like MOXA and Lantronix say they support Linux  but it's third party But most devices out there have a CLI "Command line  interface"

[http://www.quatech.com/pdf/Airborne_CLI_Guide.pdf](http://www.quatech.com/pdf/Airborne_CLI_Guide.pdf)

Instead of using their complicated and proprietary libraries, I would  use Expect and the CLI to communicate with various sensors connected to the device.  Since I'll already be using C for GTK I don't want to have to learn  Python, Pearl or any other new language.

According to this post:
"Technically, the libraries are already compiled so you do not need gcc  to **compile** them - you just need to load them."
[http://www.wellho.net/forum/The-Tcl-programming-language/TCL-amp-C-linker-problem.html](http://www.wellho.net/forum/The-Tcl-programming-language/TCL-amp-C-linker-problem.html)

I've order Exploring Expect By Don Libes and  I'am waiting on it now.
What is the -Im compliier option in that form link?
Flag:
./gcc test1.c -ltk -ltcl -lm

---

### Post by Xyro on 2010-03-21
I cant really help with expect--I've never used it. I believe the -Im in the link you provided is actually -lm (ell em), linking in the math library.

Edit #1: I think you might be looking for **exp_spawnl()** or **exp_spawnv()**, see [here]("http://www.bigbiz.com/cgi-bin/manpage?3+libexpect").

Edit #2: > **MadCow108 said:**
> you can't use the tcl expect syntax in C
you have to use the C interface:
[http://linux.die.net/man/3/libexpect](http://linux.die.net/man/3/libexpect) Maybe I should follow others' links before posting my own :P

---

### Post by nocturnal1 on 2010-03-25
Ok I received the book I ordered "Exploring Expect by Don libes" 
I am quite disappointed with the one chapter "22" which talks about Expect with C/C++
There is only one complete example program and it doesn't show the necessary gcc complier options but I got it to work using the following.

```

// Save on desktop as: test2.c 
// Change to the Desktop directory:  cd /home/owner/Desktop 
// Compile under gcc4:4.4.1 using: 
// gcc -I/usr/include/tcl8.3 -lexpect5.43 -ltcl8.3  test2.c -o test2
// Run using: ./test2

#include <stdio.h>
#include "expect.h"

int main(int argc, char *argv[])
{
    FILE *fp = exp_popen("cat");
    printf("pid = %d\n",exp_pid);
    printf("pty name = %s\n",exp_pty_slave_name);
}

```The output should on his system was:
pid = 18804
pty name = /dev/ttyp3

On my system it was:
pid = 3030
pty name = /dev/pts/1

---

### Post by MadCow108 on 2010-03-25
the pid is the process id. This id is different for every process.
So you'll receive a different pid for every time you run your program

pty is the pseudo terminal
what kind of terminal is system dependent so also this difference is not suprising
Its probably best you familiarize yourself with how unix works before starting your project

you can skip the -I/use/include/tcl8.3 flag while compiling if you change your include to the following:
#include <tcl8.3/expect.h>

<> means that it will search in the default system include paths and /usr/include is one of these
"" searches in your current directory first and only then in the system paths

btw you don't need to use C just for GTK, GTK has bindings for almost all other languages.

---

### Post by nocturnal1 on 2010-03-25
Yes thanks Madcow, changing to #include <tcl8.3/expect.h> does work.
I know there are several languages for GTK but I already know some C. I don't know any other languages. 
Well I tried the the Chesslib.c example for Expect:

[http://programming.ccp14.ac.uk/expect/example/](http://programming.ccp14.ac.uk/expect/example/)

And after changing all instances of "chess" to "glchess" and adding the following it complied:
```

#include <stdlib.h>
#include <string.h>
#include <tcl8.3/expect.h>

```

It launches but I get the error:

Failed to load GGZ config: No such file or directory: /home/owner/.ggz/ggz-gtk.rc

---

### Post by nocturnal1 on 2010-03-29
Does anyone know why I'm getting this error and how to fix it?

---

### Post by MadCow108 on 2010-03-29
that has something to do with glchess itself
I get the same message when starting glchess

don't expect that snippet to run with glchess
It may be written for a different chess program or there may be version conflicts

---

