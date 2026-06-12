---
title: "CPAN problems"
date: 2006-04-10
forum: Programming Talk
---

### Post by navilon on 2006-04-10
Can anyone help? Almost any module i try to get from cpan i get the following error:

```
Running make for A/AU/AUTRIJUS/Module-Signature-0.53.tar.gz
  Is already unwrapped into directory /home/media/.cpan/build/Module-Signature-0.53

  CPAN.pm: Going to build A/AU/AUTRIJUS/Module-Signature-0.53.tar.gz

    -- NOT OK
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible
```

---

### Post by 3david on 2006-04-11
I'm having the same problem.

---

### Post by johnnymac on 2006-04-11
make sure you upgrade your CPAN::Bundle

---

### Post by 3david on 2006-04-11
tried that with:
```

$ cpan
cpan> install Bundle::CPAN

```

but i get the same error messages

---

### Post by quirpy on 2006-05-02
I get the same error, cannot seem to find an answer in this forum :-(

---

### Post by 3david on 2006-05-02
Run cpan with sudo, and then it should work (worked for me)

---

### Post by quirpy on 2006-05-02
I was just trying that out as you posted :-)
I read up on 'sudo' here:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

then entered:
> sudo perl -MCPAN -e shell

you'll be asked to enter your password

then entered:
cpan> install Bundle::CPAN

it cruised along, no problems.
every other module I installed after this went fine.

so it's all about permissions...

---

### Post by ewelin on 2006-06-21
I'm having this same problem and tried using sudo with no success... any other ideas?

---

### Post by Zed on 2006-06-23
try ```
sudo apt-get install build-essential
```

I'm guessing you're getting tripped up for want of the GNU make command.

---

### Post by md81544 on 2006-06-26
I had exactly the same issues as described, and it wasn't because of a lack of GNU make... it finally worked when I ran 'cpan' AS ROOT - not as a sudo command.

If you haven't set a root password, you can become root by typing 'sudo su -'

---

### Post by cascader on 2007-04-09
[COLOR=DimGray]Thanks, **[COLOR=Red]quirpy[/COLOR]**, after problems getting **[COLOR=DarkOrange]modules[/COLOR]** and **[COLOR=DarkOrange]bundles[/COLOR]** sorted, what finally  pulled it together was the reading you did, as quoted;[/COLOR]
[INDENT][SIZE=1]"I read up on 'sudo' here:
[https://wiki.ubuntu.com/RootSudo[COLOR=Black]"[/COLOR]]("https://wiki.ubuntu.com/RootSudo")
[/SIZE][/INDENT]  and of course, I
[INDENT][SIZE=1]"then entered:[/SIZE]
[SIZE=1] > sudo perl -MCPAN -e shell"[/SIZE]
[/INDENT]Appreciate benefiting from your research,

[URL="http://ubuntuforums.org/newreply.php?do=newreply&p=976709"]
[/URL]

---

### Post by phossal on 2007-04-09
This same error is common when the cpan config is not properly set. "Man" it, and don't forget "commit"

---

### Post by cascader on 2007-04-10
Thanks again, this time to **[COLOR=Red]phossal[/COLOR]** . . . I am afraid in my ignorance I have never issued a '**[COLOR=DarkOrange]commit[/COLOR]**' command . . . this is great for my learning curve . . .

---

### Post by cascader on 2007-04-10
And again, thanks **[COLOR=Red]md81544[/COLOR]**, yep, had to be **[COLOR=Red]root[/COLOR]**, and I think what I just did was as **[COLOR=Red]quirpy[/COLOR]** suggested . . . mind you, I haven't tested the software yet, have been paying attention to **[COLOR=Red]her indoors[/COLOR]** for a couple of days, itching to get back **[COLOR=Red]'[/COLOR][COLOR=Red]puter[/COLOR]**-wise . . . ;)

---

### Post by cascader on 2007-04-10
I just answered the wrong thread . . . doh !

---

### Post by phossal on 2007-04-10
> **cascader said:**
> Thanks again, this time to **[COLOR=Red]phossal[/COLOR]** . . . I am afraid in my ignorance I have never issued a '**[COLOR=DarkOrange]commit[/COLOR]**' command . . . this is great for my learning curve . . .

It's not intuitive to issue commit. It's retarded. Another Ubuntu Member and I spent a couple hours figuring that one out. Good example of: RTFM! 

lol Glad my pain saved you some. 

Regards!

---

### Post by servant74 on 2007-08-16
I am getting the same problem running as root after doing this:

  sudo su - 
  apt-get install build-essential
  cpan
  install Bundle::CPAN

:confused:

---

### Post by mättu on 2007-08-16
sudo apt-get install build-essential

to make sure having all make tools installed

sudo -i

to get a root terminal

cpan

to start cpan shell

answer questions manually!
read carefully ;-) remind it's perl, so that's what you do, not just click ok.. 
if you see text about "commit" and some such, answer "yes" instead of default "no".

to be completely safe, in cpan-shell:

install Bundle::CPAN

and to get full joy, read the message about Readline support in the cpan-shell. I don't explain this in details, because it's merely for fun. 

have your appropriate amount of fun
:m)

---

### Post by Devinder on 2007-08-22
HI Can someone help

When i run CPAN i get this

devinder@devinder-desktop:~$ sudo cpan

CPAN: File::HomeDir loaded ok (v0.65)
Constant subroutine __USE_POSIX undefined at /usr/lib/perl/5.8/features.ph line 8.
Constant subroutine __USE_POSIX2 undefined at /usr/lib/perl/5.8/features.ph line 9.
Constant subroutine __USE_POSIX199309 undefined at /usr/lib/perl/5.8/features.ph line 10.
Constant subroutine __USE_POSIX199506 undefined at /usr/lib/perl/5.8/features.ph line 11.
Constant subroutine __USE_XOPEN undefined at /usr/lib/perl/5.8/features.ph line 12.
Constant subroutine __USE_XOPEN_EXTENDED undefined at /usr/lib/perl/5.8/features.ph line 13.
Constant subroutine __USE_UNIX98 undefined at /usr/lib/perl/5.8/features.ph line 14.
Constant subroutine __USE_LARGEFILE undefined at /usr/lib/perl/5.8/features.ph line 16.
Constant subroutine __USE_LARGEFILE64 undefined at /usr/lib/perl/5.8/features.ph line 17.
Constant subroutine __USE_FILE_OFFSET64 undefined at /usr/lib/perl/5.8/features.ph line 18.
Constant subroutine __USE_BSD undefined at /usr/lib/perl/5.8/features.ph line 19.
Constant subroutine __USE_SVID undefined at /usr/lib/perl/5.8/features.ph line 20.
Constant subroutine __USE_MISC undefined at /usr/lib/perl/5.8/features.ph line 21.
Constant subroutine __USE_GNU undefined at /usr/lib/perl/5.8/features.ph line 23.
Constant subroutine __USE_REENTRANT undefined at /usr/lib/perl/5.8/features.ph line 24.
Constant subroutine _POSIX_SOURCE undefined at /usr/lib/perl/5.8/features.ph line 49.
Constant subroutine _POSIX_C_SOURCE undefined at /usr/lib/perl/5.8/features.ph line 51.
Constant subroutine _XOPEN_SOURCE undefined at /usr/lib/perl/5.8/features.ph line 53.
Constant subroutine _XOPEN_SOURCE_EXTENDED undefined at /usr/lib/perl/5.8/features.ph line 55.
Constant subroutine _LARGEFILE64_SOURCE undefined at /usr/lib/perl/5.8/features.ph line 57.
Constant subroutine _LARGEFILE_SOURCE undefined at /usr/lib/perl/5.8/features.ph line 104.
Constant subroutine __USE_ISOC99 undefined at /usr/lib/perl/5.8/features.ph line 108.
Constant subroutine __GNU_LIBRARY__ undefined at /usr/lib/perl/5.8/features.ph line 156.

cpan shell -- CPAN exploration and modules installation (v1.9102)
ReadLine support enabled

                                                                                                                                                                                                     Can't ioctl TIOCGETP: Invalid argument
Consider installing Term::ReadKey from CPAN site nearby
        at [http://www.perl.com/CPAN](http://www.perl.com/CPAN)
Or use
        perl -MCPAN -e shell
to reach CPAN. Falling back to 'stty'.
        If you do not want to see this warning, set PERL_READLINE_NOWARN
in your environment.

---

### Post by mättu on 2007-08-22
There we go on a fresh ubuntu-7.04 (feisty):

I repoduced your error by *not* installing build-essential and *not* commiting values to file.

sudo cpan gives your error message.


I then tested this fix for you:

```
sudo apt-get install build-essential
```

```
sudo cpan
```

The first question is:

```
Normally CPAN.pm keeps config variables in memory and changes need to
be saved in a separate 'o conf commit' command to make them permanent
between sessions. If you set the 'auto_commit' option to true, changes
to a config variable are always automatically committed to disk.

Always commit changes to config variables to disk? [no] yes
```

(See my "yes" instead of dedault "no" !)
The rest of questions may be answered default by pressing enter.

Then again you will see the old error:

cpan shell -- CPAN exploration and modules installation (v1.9102)
ReadLine support enabled

Can't ioctl TIOCGETP: Invalid argument
Consider installing Term::ReadKey from CPAN site nearby
        at [http://www.perl.com/CPAN](http://www.perl.com/CPAN)
Or use
        perl -MCPAN -e shell
to reach CPAN. Falling back to 'stty'.
        If you do not want to see this warning, set PERL_READLINE_NOWARN
in your environment.


to fix this, do:

```
cpan[1]> exit

sudo cpan
```

(You should not be asked again to answer all the setup-questions)

```
cpan[1]> install Bundle::CPAN
```

(long list of messages, prompt for some dependencies, please intall them all by pressing enter)

At the end you should get:  
...
Has already been tested successfully
Running make install
  Already done

cpan[2]>

That's it. Works?

have fun
:m)

---

### Post by tr333 on 2007-08-26
I would consider installing and using the [CPANPLUS](http://search.cpan.org/dist/CPANPLUS/lib/CPANPLUS.pm)  shell instead of the normal CPAN shell.  It seems to be much better at handling dependency problems for me, and also allows automated test reporting via the Test::Reporter module when a module install passes or fails.  It can be installed with the Bundle::CPANPLUS module or the CPANPLUS module.

---

### Post by Al legory on 2008-01-16
Thanks for the help with the apt-get build-essential.

Does the build-essential package setup the C compiler and make utilities?

Thanks

---

### Post by mättu on 2008-01-16
open synaptic
find build-essential
open "properties"
choose "dependencies"
Here you should see what packages it depends on (means they are installed when installing build-essential)

on my system this includes:
libc-dev
gcc
g++
make
dpkg-dev

cheers
:m)

---

### Post by tr333 on 2008-01-21
> **Al legory said:**
> Thanks for the help with the apt-get build-essential.

Does the build-essential package setup the C compiler and make utilities?

Thanks

If you're doing C programming, you will want to install the manpages-dev package to get all the C library man pages (printf/scanf/etc) in section 3 of the manual (eg. 'man 3 printf').  I also install automake and autoconf on my system in addition to build-essential, but that depends on whether you need those tools.

---

