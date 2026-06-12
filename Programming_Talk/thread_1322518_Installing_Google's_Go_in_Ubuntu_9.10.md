---
title: "Installing Google's Go in Ubuntu 9.10"
date: 2009-11-11
forum: Programming Talk
---

### Post by eznet on 2009-11-11
_**Google Go**_
Go is Google's newest offering to the development community.  According to the project's page, Go is an expressive, concurrent, garbage collected programming language that is simple, fast, safe, concurrent, fun and (best of all) open source. Touted as a cross between C/C++ and Python, Go seems to be generating a lot of buzz and hoards of seemingly early adopters despite having surfaced only earlier today (11.10.2009) .  Of course this is somewhat expected - what has Google ever released that didn't generate it's share of hype/buzz/excitement associated with it?

I bit.  I am guessing since you are reading this, you did too.
[U]
**Getting Ready to Go**[/U]

The following instructions detail the steps that I used to setup Go on my x64 Ubuntu 9.10 (Karmic Koala) box.

Standard disclaimer: Your mileage may vary.  For me everything was pretty much straight forward when following the maintainer's provided setup instructions ([http://golang.org/doc/install.html](http://golang.org/doc/install.html)). The only hiccup I encountered during setup was an error with a test during make - Error 2 in [net.test]. A quick bounce over to #go-nuts resolved that - friendly go-nut knowledge base, iant, advised me that there was an issue with this test on some machines in the release version and that I should pull an update. Update pulled, problem fixed.

For simplicity sake, I am working from the gnome-terminal. Access bash as you see fit.  When you see '$', it denotes a command to enter in the CLI (Command Line Interface).  When you see '>', it denotes and output line.

FYI - My Machine Info:

```
$uname -a
>2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux

```
**_Installing Required Tools_**

Install GCC and Mercurial:

   ```
 $sudo apt-get install mercurial bison gcc libc6-dev
```

**_Setting Up Your Environment_**

1) Make 'bin' directory for go - You may have one - this will create it for you if you don't:

   ```
$mkdir ~/bin
```

2) Setting up environmental variables:

Edit your Bash environment variables to include the Go required variables as well as making sure your bin folder is in the $PATH

```

$cp ~/.bashrc ~/.bashrc.bu
$gedit ~/.bashrc
```

Add following to your .bashrc - ***note***: If using 386, set "GOARCH=386" (worked great on my EeePC):

```

#Google Go Vars
export GOROOT=~/go
export GOOS=linux
export GOARCH=amd64
PATH=${PATH}:$HOME/bin

```

Reload .bashrc

```
$source .bashrc
```

_Note_: You can close your terminal session and restart terminal instead. Up to you.

Check out Go ( to your Go root using Mercurial)

```
$hg clone -r release https://go.googlecode.com/hg/ $GOROOT
```

_Note_: I had to pull an update due to errors during make (details below with build instructions):

```

$cd $GOROOT
$hg pull -u
```

_**Building Go**_

```

$cd $GOROOT/src
$./all.bash

```

If successful, results should be:

```

>--- cd ../test
>0 known bugs; 0 unexpected bugs

```

    _Note on make errors_: Before pulling an update on the repository, make resulted in:

```

>make[1]: Leaving directory `/home/eznet/go/src/pkg/net'
>make: *** [net.test] Error 2

```

    Updating via the 'hg pull -u' command above resolved this issue and allowed make to complete as desired.

**_GO play with Go_**

Tutorial: [http://golang.org/doc/go_tutorial.html](http://golang.org/doc/go_tutorial.html)

[http://blog.eznet.frih.net/?p=121](http://blog.eznet.frih.net/?p=121)

**Edit**:"Installing Required Tools" was modified to skip Python's Setup Tools as mbudde pointed out that mercurial is available from the Ubuntu repositories.

---

### Post by inod3 on 2009-11-11
Thank you for writing this.

```
uname -a
Linux aki 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux
```

I am getting some errors on the installation of mercurial:

```
sudo easy_install mercurial
```

```
Searching for mercurial
Reading http://pypi.python.org/simple/mercurial/
Reading http://www.selenic.com/mercurial
Best match: mercurial 1.3.1
Downloading http://mercurial.selenic.com/release/mercurial-1.3.1.tar.gz
Processing mercurial-1.3.1.tar.gz
Running mercurial-1.3.1/setup.py -q bdist_egg --dist-dir /tmp/easy_install-ZEeZtO/mercurial-1.3.1/egg-dist-tmp-hXLT1l
mercurial/base85.c:12:20: error: Python.h: No such file or directory
mercurial/base85.c: In function &#8216;b85prep&#8217;:
mercurial/base85.c:23: warning: implicit declaration of function &#8216;memset&#8217;
mercurial/base85.c:23: warning: incompatible implicit declaration of built-in function &#8216;memset&#8217;
mercurial/base85.c: At top level:
mercurial/base85.c:28: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
mercurial/base85.c:76: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
mercurial/base85.c:141: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;methods&#8217;
mercurial/base85.c:150: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;initbase85&#8217;
error: Setup script exited with error: command 'gcc' failed with exit status 1
```

---

### Post by BarryNorton on 2009-11-11
Same error on easy_install mercurial.

When I install the mercurial in synaptic Go's .bash.all fails with:

> gcc -m32 -O2 -fPIC -o linux_386.o -c linux_386.c
In file included from /usr/include/features.h:378,
                 from /usr/include/pthread.h:23,
                 from linux_386.c:5:
/usr/include/gnu/stubs.h:7:27: error: gnu/stubs-32.h: No such file or directory
gcc -m32 -O2 -fPIC -o 386.o -c 386.S
make: *** [linux_386.o] Error 1

(Brand new 9.10 on i386)

---

### Post by BarryNorton on 2009-11-11
Aha, first do a 'sudo apt-get install python-dev' then the mercurial install should work.

Then do a 'sudo apt-get install libc6-dev-i386' and the Go build should succeed :)

---

### Post by mbudde on 2009-11-11
The section "Installing Required Tools" should just be
```
$sudo apt-get install mercurial bison gcc libc6-dev
```

There is no reason to use easy_install to install mercurial.

---

### Post by eznet on 2009-11-11
> **mbudde said:**
> The section "Installing Required Tools" should just be
```
$sudo apt-get install mercurial bison gcc libc6-dev
```

There is no reason to use easy_install to install mercurial.

It appears that you are correct.  I think that I must have misspelled Mercurial when looking in Synaptic initially... Doh!

Thanks.

---

### Post by digitalpbk on 2009-11-22
See [http://digitalpbk.com/2009/11/installing-google-go-linux-ubuntu]("http://digitalpbk.com/2009/11/installing-google-go-linux-ubuntu") to get a bash script to do it all in one step for 386.

---

### Post by yusufk on 2009-12-04
I'm having trouble installing go on my laptop:

%%%% making libcgo %%%%

gcc -m32 -O2 -fPIC -o linux_386.o -c linux_386.c
as   -o 386.o 386.s
gcc -m32 -O2 -fPIC -o util.o -c util.c
386.s: Assembler messages:
386.s:21: Error: junk at end of line, first unrecognized character is `('
386.s:22: Error: invalid character '(' in mnemonic
make: *** [386.o] Error 1
make: *** Waiting for unfinished jobs....


The environment is identical to my desktop machine where it all went smoothly. Any ideas?

Linux fld28976l 2.6.31-15-generic #50-Ubuntu SMP Tue Nov 10 14:54:29 UTC 2009 i686 GNU/Linux

---

### Post by hoboy on 2009-12-04
I have followed what you have mentioned.
I am getting the following errors.

mike@ubuntu:~$ cd $GOROOT/src
mike@ubuntu:~/hg/src$ ./all.bash
installed quietgcc as /home/luc/bin/quietgcc but 'which quietgcc' fails
double-check that /home/mike/bin is in your $PATH
mike@ubuntu:~/hg/src$

---

### Post by hoboy on 2009-12-04
> **hoboy said:**
> I have followed what you have mentioned.
I am getting the following errors.

mike@ubuntu:~$ cd $GOROOT/src
mike@ubuntu:~/hg/src$ ./all.bash
installed quietgcc as /home/luc/bin/quietgcc but 'which quietgcc' fails
double-check that /home/mike/bin is in your $PATH
mike@ubuntu:~/hg/src$

Problem solved.

---

### Post by yusufk on 2009-12-09
Figured out the problem. Turns out I had downloaded the file to a directory that was on a FAT32 partition.

The src/libcgo/386.S file was renamed to 386.s for some reason!

---

