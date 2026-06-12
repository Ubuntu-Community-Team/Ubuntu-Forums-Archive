---
title: "error compiling"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by Skivache on 2008-06-26
Im trying to install libxml2 on an old box running Damn Small Linux. When I go to ./configure, this happens:
```
dsl@0[libxml2-2.6.27]$ ./configure
checking build system type... i586-pc-linux-gnulibc1
checking host system type... i586-pc-linux-gnulibc1
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... /lib/cpp
configure: error: C preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.
```

I have tried to install build-essential but I get this error
```
dsl@0[libxml2-2.6.27]$ sudo apt-get install build-essential
Reading Package Lists... Done
Building Dependency Tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ but it is not going to be installed
                   Depends: dpkg-dev (>= 1.4.1.19) but it is not going to be installed
E: Broken packages

```

I've been searching for a while and haven't found a solution, if anyone can help it would be greatly appreciated.

---

### Post by HalPomeranz on 2008-06-26
So what happens if you try:

```

sudo apt-get install libc-dev g++ dpkg-dev build-essentials

```

---

### Post by Skivache on 2008-06-26
```
dsl@0[libxml2-2.6.27]$ sudo apt-get install libc-dev g++ dpkg-dev build-essentia l
Reading Package Lists... Done
Building Dependency Tree... Done
Note, selecting libc6-dev instead of libc-dev
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  dpkg-dev: Depends: perl5
            Depends: perl-modules but it is not going to be installed
  libc6-dev: Depends: libc6 (= 2.2.5-11.8) but 2.3.2.ds1-10 is to be installed
E: Broken packages

```

So I tried 
```
sudo apt-get install perl5 libc6
```

and got... 
```
dsl@0[libxml2-2.6.27]$ sudo apt-get install perl5 libc6
Reading Package Lists... Done
Building Dependency Tree... Done
Note, selecting perl instead of perl5
libc6 is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  perl: Depends: perl-base (= 5.6.1-8.9) but 5.8.0-18 is to be installed
E: Broken packages

```

Then...
```
dsl@0[libxml2-2.6.27]$ sudo apt-get install perl-base
Reading Package Lists... Done
Building Dependency Tree... Done
perl-base is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up pcmcia-cs (3.1.33-6woody1) ...
update-rc.d: /etc/init.d/pcmcia: file does not exist
dpkg: error processing pcmcia-cs (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 pcmcia-cs
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

This would usually cause me to run for the package manager but Damn Small Linux doesn't seem to have one...

---

### Post by HalPomeranz on 2008-06-26
Yuck.  Did you try "sudo apt-get install pcmcia-cs"?  Maybe with the "-f" (fix) option?

---

### Post by Skivache on 2008-06-26
```
dsl@0[dsl]$ sudo apt-get install -f
Reading Package Lists... Done
Building Dependency Tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up pcmcia-cs (3.1.33-6woody1) ...
update-rc.d: /etc/init.d/pcmcia: file does not exist
dpkg: error processing pcmcia-cs (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 pcmcia-cs
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Im stumped

---

### Post by Skivache on 2008-06-26
I tried a --configure and still got the same error
```
dsl@0[dsl]$ sudo dpkg --configure -a
Setting up pcmcia-cs (3.1.33-6woody1) ...
update-rc.d: /etc/init.d/pcmcia: file does not exist
dpkg: error processing pcmcia-cs (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 pcmcia-cs

```

Hmm, after some more searching , it looks like this is related the CPU architecture being i586.  Perhaps I should give this old computer (AMD-K6 3D 350MHz) a rest and get a new-old one.

---

### Post by iaculallad on 2008-06-26
What about doing:

```
sudo apt-get install --fix-missing
```

---

### Post by Skivache on 2008-06-26
> **iaculallad said:**
> What about doing:

```
sudo apt-get install --fix-missing
```

```
dsl@0[dsl]$ sudo apt-get install --fix-missing
Reading Package Lists... Done
Building Dependency Tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up pcmcia-cs (3.1.33-6woody1) ...
update-rc.d: /etc/init.d/pcmcia: file does not exist
dpkg: error processing pcmcia-cs (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 pcmcia-cs
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by iaculallad on 2008-06-26
Try to touch /etc/init.d/pcmcia:

```
sudo touch /etc/init.d/pcmcia && sudo chmod 755 /etc/init.d/pcmcia
```

then

```
sudo dpkg --configure -a
```

---

### Post by Skivache on 2008-06-26
```
dsl@0[dsl]$ sudo touch /etc/init.d/pcmcia && sudo chmod 755 /etc/init.d/pcmcia
dsl@0[dsl]$ sudo dpkg --configure -a
Setting up pcmcia-cs (3.1.33-6woody1) ...

```

This is a miracle!  What is it exactly that "touch" does?

---

### Post by iaculallad on 2008-06-26
> **Skivache said:**
> ```
dsl@0[dsl]$ sudo touch /etc/init.d/pcmcia && sudo chmod 755 /etc/init.d/pcmcia
dsl@0[dsl]$ sudo dpkg --configure -a
Setting up pcmcia-cs (3.1.33-6woody1) ...

```

This is a miracle!  What is it exactly that "touch" does?

The touch terminal command creates a file (If missing) with the updated accessed/modification time. 
If the file does exist, it just updates the accessed/modification time.

---

### Post by Skivache on 2008-06-26
Ok, I will add this to my list of commands to keep.  Now that pcmcia is working I can start installing the other dependencies. Now I have a new problem:
```
 sudo apt-get install perl5
Reading Package Lists... Done
Building Dependency Tree... Done
Note, selecting perl instead of perl5
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  perl: Depends: perl-base (= 5.6.1-8.9) but 5.8.0-18 is to be installed
E: Broken packages

```
So I try
```
dsl@0[dsl]$ sudo apt-get install perl-base
Reading Package Lists... Done
Building Dependency Tree... Done
perl-base is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
No luck there either, is there a different command I should be using?

---

### Post by iaculallad on 2008-06-26
Instead of using the stripped-down version of perl, What about:

```
sudo apt-get install perl perl-modules perl-doc
```

---

### Post by Skivache on 2008-06-26
That would be lovely, but:
```
dsl@0[dsl]$ sudo apt-get install perl perl-modules perl-doc
Reading Package Lists... Done
Building Dependency Tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  perl: Depends: perl-base (= 5.6.1-8.9) but 5.8.0-18 is to be installed
E: Broken packages

```

---

### Post by iaculallad on 2008-06-26
> **Skivache said:**
> That would be lovely, but:
```
dsl@0[dsl]$ sudo apt-get install perl perl-modules perl-doc
Reading Package Lists... Done
Building Dependency Tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  perl: Depends: perl-base (= 5.6.1-8.9) but 5.8.0-18 is to be installed
E: Broken packages

```

(I'm not sure if this works) Redo the -f option if it could fix that problem :

```
sudo apt-get -f install
```

---

### Post by Skivache on 2008-06-27
None of the commands seemed to work, so I ran
```
sudo apt-get remove perl-base
```
Which then removed a good half of the packages installed, including  the packages I needed to boot.  I ended up reinstalling Damn Small Linux and followed the steps you guys have shown me to get back to where I was.  Now I have one more problem.  

When I try to install something, I get this:

```
root@box:~# apt-get install libc-dev
Reading Package Lists... Done
Building Dependency Tree... Done
Note, selecting libc6-dev instead of libc-dev
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.2.5-11.8) but 2.3.2.ds1-10 is to be installed
E: Broken packages
root@box:~# apt-get install libc6
Reading Package Lists... Done
Building Dependency Tree... Done
libc6 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

```
root@box:~# apt-get install perl
Reading Package Lists... Done
Building Dependency Tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  perl: Depends: perl-base (= 5.6.1-8.9) but 5.8.0-18 is to be installed
E: Broken packages
root@box:~# apt-get install perl-base
Reading Package Lists... Done
Building Dependency Tree... Done
perl-base is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

What does "perl: Depends: perl-base (= 5.6.1-8.9) but 5.8.0-18 is to be installed" mean and what do I need to do to install the main packages?

---

### Post by oldos2er on 2008-06-27
Can you post the output of "cat /etc/apt/sources.list" ?

---

### Post by Skivache on 2008-06-27
```
root@box:~# cat /etc/apt/sources.list
deb http://archive.debian.org/debian-archive/ woody main contrib non-free
#deb http://mirror.aarnet.edu.au/debian oldstable main contrib non-free
#deb http://mirror.linux.org.au/debian oldstable main contrib non-free
#deb http://mirrors.usc.edu/pub/linux/distributions/debian oldstable main contrib non-free

```
Am I using the right repos?

---

### Post by oldos2er on 2008-06-27
You're using DSL? You should probably ask at [http://damnsmalllinux.org/cgi-bin/forums/ikonboard.cgi](http://damnsmalllinux.org/cgi-bin/forums/ikonboard.cgi)

---

### Post by Skivache on 2008-06-27
That was my next step, but I figured I would start here.  Unfortunately it seems like a distro specific issue.  As usual you guys were a big help, thanks for the help :)

---

