---
title: "Set PATH environment for newly added executable files"
date: 2015-12-06
forum: New to Ubuntu
---

### Post by marongiu-luigi on 2015-12-06
Dear all,
I am installing a series of programs for bioinformatics purposes; I am installing the folders of these packages in /usr/local/lib/ and creating soft links to the executable files in /usr/bin/ so I am expecting to have them visible in the environment. But when I type the executables in the terminal, the commands are not recognized, so they are not in the environment. 
I also modified the /home/userName/.bashrc with the line:
**export PATH=$PATH:/usr/bin/**
but still no luck; for instance for the bowtie2 program, contained in the /usr/local/lib/Bowtie folder, I wrote:
[B]/usr/local/lib/Bowtie$ bowtie2 --version
/usr/local/lib/Bowtie$ The program 'bowtie2' is currently not installed. You can install it by typing:
sudo apt-get install bowtie2[/B]
same thing when I open the terminal in default folder **name@userName:~$**
I have not really clear how to modify this PATH environment; on the help online seems simple, but I can't make it work. 
So how can I modify the environment in a way that the newly added executables could be accessible globally?
Thank you.
G

---

### Post by steeldriver on 2015-12-06
Hello and welcome to the forums

How did you obtain and install bowtie (from source, as a binary zip file)?

Why are you putting "folders of these packages" in /usr/lib? That's not a usual place for such things.

Linking pre-built binaries to /usr/bin sometimes doesn't work because they expect their libraries to be in a particular place relative to the executable. In any case, /usr/bin should already be in PATH so no need to add it again.

Based on the instructions here --> [Bowtie2 manual - Adding to PATH]("http://bowtie-bio.sourceforge.net/bowtie2/manual.shtml#obtaining-bowtie-2") you should add the path to the **containing folder** to PATH e.g.

If you unzip it somewhere in your HOME
```

mkdir ~/bowtie2

unzip -d ~/bowtie2/ ~Downloads/bowtie2-2.2.6-linux-x86_64.zip

export PATH="$PATH:$HOME/bowtie2/bowtie2-2.2.6/"

```

If you want to place it in a system directory, I'd recommend /opt or /usr/local itself rather than /usr/local/lib

```

sudo mkdir /opt/bowtie2

sudo unzip -d /opt/bowtie2/ ~/Downloads/bowtie2-2.2.6-linux-x86_64.zip

export PATH="$PATH:/opt/bowtie2/bowtie2-2.2.6"

steeldriver@T61p:~$ bowtie2 --version
/opt/bowtie2/bowtie2-2.2.6/bowtie2-align-s version 2.2.6
64-bit
Built on localhost.localdomain
Wed Jul 22 16:18:32 EDT 2015
Compiler: gcc version 4.1.2 20080704 (Red Hat 4.1.2-54)
Options: -O3 -m64 -msse2  -funroll-loops -g3 -DPOPCNT_CAPABILITY
Sizeof {int, long, long long, void*, size_t, off_t}: {4, 8, 8, 8, 8, 8}

```

FWIW bowtie2 **is** in the repository (although it is likely not the most up-to-date version), so you could just install that instead in which case all the PATHs will be taken care of for you

---

### Post by matt_symes on 2015-12-06
A support question so I'm moving the thread to **New to Ubuntu**

---

