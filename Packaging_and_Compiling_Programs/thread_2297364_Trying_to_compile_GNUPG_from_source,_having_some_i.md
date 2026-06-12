---
title: "Trying to compile GNUPG from source, having some issues"
date: 2015-10-03
forum: Packaging and Compiling Programs
---

### Post by josh151 on 2015-10-03
I downloaded the latest stable tarball from [https://www.gnupg.org/download/](https://www.gnupg.org/download/) and extracted it to a folder on my ubuntu machine.
I had to chmod 775 configure in order to be able to run it, then I ran ./configure

I got this message right at the end:
```



        GnuPG v2.0.29 has been configured as follows:


        Revision:  120fc69  (4623)
        Platform:  GNU/Linux (x86_64-unknown-linux-gnu)


        OpenPGP:   yes
        S/MIME:    yes
        Agent:     yes 
        Smartcard: yes (without internal CCID driver)
        Gpgtar:    no


        Protect tool:      (default)
        Default agent:     (default)
        Default pinentry:  (default)
        Default scdaemon:  (default)
        Default dirmngr:   (default)


        Warning: Mismatches between the target platform and the
                 to be used libraries have been detected for:
                   libgpg-error libgcrypt
                 Please check above for more warning messages.



```

I tried to run a sudo apt-get install libgpg-error libgcrypt but it said they couldn't be found, so I tried libgpg-error-dev libgcrypt-dev and got this:

```

Reading package lists...
Building dependency tree...
Reading state information...
libgpg-error-dev is already the newest version.
libgcrypt11-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 69 not upgraded.



```

So I tried to run make and this is what I saw at the very end
```

Making all in .
make[3]: Entering directory `/home/nitrous/gnupg-new/tests'
srcdir=. GNUPGHOME=`/bin/pwd` GPG_AGENT_INFO= LC_ALL=C GPGSM=../sm/gpgsm ./runtest ./inittests
make[3]: Leaving directory `/home/nitrous/gnupg-new/tests'
make[2]: Leaving directory `/home/nitrous/gnupg-new/tests'
make[1]: Leaving directory `/home/nitrous/gnupg-new'
/bin/bash: ./runtest: permission denied
make[3]: *** [inittests.stamp] Error 126
make[2]: *** [all-recursive] Error 1
make[1]: *** [all-recursive] Error 1
make: *** [all] Error 2
Making all in .
make[3]: Entering directory `/home/nitrous/gnupg-new/tests'
srcdir=. GNUPGHOME=`/bin/pwd` GPG_AGENT_INFO= LC_ALL=C GPGSM=../sm/gpgsm ./runtest ./inittests
/bin/bash: ./runtest: Permission denied
make[3]: *** [inittests.stamp] Error 126
make[3]: Leaving directory `/home/nitrous/gnupg-new/tests'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/nitrous/gnupg-new/tests'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/nitrous/gnupg-new'
make: *** [all] Error 2
```

I then ran make install and got the same error at the end. What is going wrong?

[COLOR=#111111][FONT=Ubuntu]Edit:
I've manually compiled and installed libgpg-error and libgcrypt, the ./configure went fine without any warnings, when I ran sudo make I got this at the end:
```

[COLOR=#000000]chmod [/COLOR][COLOR=#800000]755[/COLOR][COLOR=#000000]./[/COLOR][COLOR=#000000]gpg_dearmor
[/COLOR][COLOR=#000000]./[/COLOR][COLOR=#000000]gpg_dearmor [/COLOR][COLOR=#000000]>[/COLOR][COLOR=#000000]./[/COLOR][COLOR=#000000]pubring[/COLOR][COLOR=#000000].[/COLOR][COLOR=#000000]gpg [/COLOR][COLOR=#000000]<[/COLOR][COLOR=#000000]./[/COLOR][COLOR=#000000]pubring[/COLOR][COLOR=#000000].[/COLOR][COLOR=#000000]asc
[/COLOR][COLOR=#000000]../../[/COLOR][COLOR=#000000]g10[/COLOR][COLOR=#000000]/[/COLOR][COLOR=#000000]gpg2[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#000000] error [/COLOR][COLOR=#00008B]while[/COLOR][COLOR=#000000] loading shared libraries[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#000000] libgcrypt[/COLOR][COLOR=#000000].[/COLOR][COLOR=#000000]so[/COLOR][COLOR=#000000].[/COLOR][COLOR=#800000]20[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#000000] cannot open shared object file[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#2B91AF]No[/COLOR][COLOR=#000000] such file or directory
make[/COLOR][COLOR=#000000][[/COLOR][COLOR=#800000]3[/COLOR][COLOR=#000000]]:[/COLOR][COLOR=#000000]***[/COLOR][COLOR=#000000][[/COLOR][COLOR=#000000]pubring[/COLOR][COLOR=#000000].[/COLOR][COLOR=#000000]gpg[/COLOR][COLOR=#000000]][/COLOR][COLOR=#2B91AF]Error[/COLOR][COLOR=#800000]127[/COLOR][COLOR=#000000]
make[/COLOR][COLOR=#000000][[/COLOR][COLOR=#800000]3[/COLOR][COLOR=#000000]]:[/COLOR][COLOR=#2B91AF]Leaving[/COLOR][COLOR=#000000] directory [/COLOR][COLOR=#800000]`/home/nitrous/gnupg-new/tests/openpgp'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `[/COLOR][COLOR=#000000]/[/COLOR][COLOR=#000000]home[/COLOR][COLOR=#000000]/[/COLOR][COLOR=#000000]nitrous[/COLOR][COLOR=#000000]/[/COLOR][COLOR=#000000]gnupg[/COLOR][COLOR=#000000]-[/COLOR][COLOR=#000000]new[/COLOR][COLOR=#000000]/[/COLOR][COLOR=#000000]tests[/COLOR][COLOR=#800000]'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/nitrous/gnupg-new'[/COLOR][COLOR=#000000]
make[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#000000]***[/COLOR][COLOR=#000000][[/COLOR][COLOR=#000000]all[/COLOR][COLOR=#000000]][/COLOR][COLOR=#2B91AF]Error[/COLOR][COLOR=#800000]2

```
[/COLOR]Then when I tried make install again, I got this:
```

[COLOR=#2B91AF]Making[/COLOR][COLOR=#000000] install [/COLOR][COLOR=#00008B]in[/COLOR][COLOR=#000000] tests
make[/COLOR][COLOR=#000000][[/COLOR][COLOR=#800000]1[/COLOR][COLOR=#000000]]:[/COLOR][COLOR=#2B91AF]Entering[/COLOR][COLOR=#000000] directory [/COLOR][COLOR=#800000]`/home/nitrous/gnupg-new/tests'
Making install in openpgp
make[2]: Entering directory `[/COLOR][COLOR=#000000]/[/COLOR][COLOR=#000000]home[/COLOR][COLOR=#000000]/[/COLOR][COLOR=#000000]nitrous[/COLOR][COLOR=#000000]/[/COLOR][COLOR=#000000]gnupg[/COLOR][COLOR=#000000]-[/COLOR][COLOR=#000000]new[/COLOR][COLOR=#000000]/[/COLOR][COLOR=#000000]tests[/COLOR][COLOR=#000000]/[/COLOR][COLOR=#000000]openpgp[/COLOR][COLOR=#800000]'
./gpg_dearmor > ./secring.gpg < ./secring.asc
../../g10/gpg2: error while loading shared libraries: libgcrypt.so.20: cannot open shared object file: No such file or directory
make[2]: *** [secring.gpg] Error 127
make[2]: Leaving directory `/home/nitrous/gnupg-new/tests/openpgp'[/COLOR][COLOR=#000000]
make[/COLOR][COLOR=#000000][[/COLOR][COLOR=#800000]1[/COLOR][COLOR=#000000]]:[/COLOR][COLOR=#000000]***[/COLOR][COLOR=#000000][[/COLOR][COLOR=#000000]install[/COLOR][COLOR=#000000]-[/COLOR][COLOR=#000000]recursive[/COLOR][COLOR=#000000]][/COLOR][COLOR=#2B91AF]Error[/COLOR][COLOR=#800000]1[/COLOR][COLOR=#000000]
make[/COLOR][COLOR=#000000][[/COLOR][COLOR=#800000]1[/COLOR][COLOR=#000000]]:[/COLOR][COLOR=#2B91AF]Leaving[/COLOR][COLOR=#000000] directory [/COLOR][COLOR=#800000]`/home/nitrous/gnupg-new/tests'
make: *** [install-recursive] Error 1[/COLOR][/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
```[/FONT][/COLOR]

---

### Post by steeldriver on 2015-10-03
Hello and welcome to the forums

What version of Ubuntu are you running? What is the output of the following command

```

apt-cache policy libgcrypt11-dev libgcrypt20-dev

```

---

### Post by josh151 on 2015-10-03
> **steeldriver said:**
> Hello and welcome to the forums

What version of Ubuntu are you running? What is the output of the following command

```

apt-cache policy libgcrypt11-dev libgcrypt20-dev

```

I'm using version 14.04.2.

The output of that commands is:

```
libgcrypt11-dev:  Installed: 1.5.3-2ubuntu4.2
  Candidate: 1.5.3-2ubuntu4.2
  Version table:
 *** 1.5.3-2ubuntu4.2 0
        500 http://mirror.nitrous.io/ubuntu/ trusty-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     1.5.3-2ubuntu4 0
        500 http://mirror.nitrous.io/ubuntu/ trusty/main amd64 Packages
libgcrypt20-dev:
  Installed: (none)
  Candidate: 1.6.1-2ubuntu1.14.04.1
  Version table:
     1.6.1-2ubuntu1.14.04.1 0
        500 http://mirror.nitrous.io/ubuntu/ trusty-updates/universe amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ trusty-security/universe amd64 Packages
     1.6.1-2ubuntu1 0
        500 http://mirror.nitrous.io/ubuntu/ trusty/universe amd64 Packages



```

I also found online that I can run a command
```

sudo ldconfig -v

```

Then I got this error when I ran make:
```

Making all in .
make[3]: Entering directory `/home/nitrous/gnupg-new/tests'
srcdir=. GNUPGHOME=`/bin/pwd` GPG_AGENT_INFO= LC_ALL=C GPGSM=../sm/gpgsm ./runtest ./inittests
/bin/bash: ./runtest: Permission denied
make[3]: *** [inittests.stamp] Error 126
make[3]: Leaving directory `/home/nitrous/gnupg-new/tests'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/nitrous/gnupg-new/tests'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/nitrous/gnupg-new'
make: *** [all] Error 2

```

Then I tried to chmod 775 to tests/runtest and ran make again...

```


Making all in .
make[3]: Entering directory `/home/nitrous/gnupg-new/tests'
srcdir=. GNUPGHOME=`/bin/pwd` GPG_AGENT_INFO= LC_ALL=C GPGSM=../sm/gpgsm ./runtest ./inittests
asschk: interpreter: invalid statement `set'
make[3]: *** [inittests.stamp] Error 1
make[3]: Leaving directory `/home/nitrous/gnupg-new/tests'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/nitrous/gnupg-new/tests'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/nitrous/gnupg-new'
make: *** [all] Error 2

```

---

### Post by oldos2er on 2015-10-04
Moved to Packaging & Compiling Programs.

---

### Post by FNB on 2015-10-28
Why did you chmod 775 in the first place? Couldn't you run it with sudo?
I cannot but guess you might have messed up some permissions at the first place and then messed up the libs.

---

