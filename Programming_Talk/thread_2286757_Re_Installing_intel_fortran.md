---
title: "Re: Installing intel fortran"
date: 2015-07-14
forum: Programming Talk
---

### Post by leo_br_hidro on 2015-07-14
Hello there, also a newbie here.

So far, all pages I found about this subject recommend editing your .basrc file. Here are some other references:

[https://software.intel.com/en-us/articles/using-intel-compilers-for-linux-with-ubuntu/](https://software.intel.com/en-us/articles/using-intel-compilers-for-linux-with-ubuntu/)
[https://software.intel.com/en-us/forums/topic/277289](https://software.intel.com/en-us/forums/topic/277289)

I have tried many things, like adding all of these at the end of my .bashrc file, all failures:
   
```
source /opt/intel/composer_xe_2015.3.187/bin/intel64/ifortvars.sh intel64
```
```
source ~/opt/intel/composer_xe_2015.3.187/bin/ifortvars.sh intel64
```
```
source /root/opt/intel/composer_xe_2015.3.187/bin/intel64/ifortvars.sh intel64
```

The last one actually messed up my terminal, don't recommend it (when you start the terminal, you're not a superuser yet, so you don't have permission to access root, and it goes wrong, apparently).
The change that made a difference was actually this one:

```

PATH="/opt/intel/composer_xe_2015.3.187/bin/intel64:$PATH"
export PATH
LD_LIBRARY_PATH="/opt/intel/composer_xe_2015.3.187/compiler/lib/intel64:$LD_LIBRARY_PATH"
export LD_LIBRARY_PATH

```

After that, this is the kind of response I get from the terminal:
```
leonardo@Leonardo-linux:~$ which ifort
/opt/intel/composer_xe_2015.3.187/bin/intel64/ifort
leonardo@Leonardo-linux:~$ ifort -v
ifort version 15.0.3
leonardo@Leonardo-linux:~$ ifort
ifort: command line error: no files specified; for help type "ifort -help"
```

So it seems that things are OK, but they're not.
When I try this other command, this is what comes out of the terminal:

```
leonardo@Leonardo-linux:~/lib$ sudo make -f makefile
ifort -c -O2 -m64 -mcmodel=medium -fconvert=little-endian -frecord-marker=4 -I/lib/src/grib_api-1.13.1/include erf.f90
/bin/bash: ifort: command not found
make: *** [erf.o] Error 127
```

Can someone help me? I have attached the code for the makefile [FONT=arial][ATTACH]263197[/ATTACH].[/FONT]

---

### Post by slickymaster on 2015-07-14
Moved to a thread of its own.

Please don't hijack other people's threads. Not only it dilutes community effort but it's also the wrong way to get the proper and adequate help to your problem.

---

### Post by steeldriver on 2015-07-14
This doesn't seem to be a problem with installation, rather with usage. A couple of comments:

```

leonardo@Leonardo-linux:~$ ifort
ifort: command line error: no files specified; for help type "ifort -help"

```

This is normal (gcc would produce a similar error here): it's a compiler, so it needs to be given at least one source code file to compile e.g.

```

ifort somefile.f90

```

```

$ sudo make -f makefile
ifort -c -O2 -m64 -mcmodel=medium -fconvert=little-endian -frecord-marker=4 -I/lib/src/grib_api-1.13.1/include erf.f90
/bin/bash: ifort: command not found
make: *** [erf.o] Error 127

```

`sudo` does not inherit your user's environment (primarily for security reasons). Although you could add the equivalent PATH, LD_LIBRARY_PATH etc. definitions to the sudo environment it's really not good practice: it would be better to arrange your development directories so that you don't need to be root to compile things i.e. either build in your home directory or in a dedicated /usr/local/src directory with appropriately permissive write permissions. Many 3rd party makefiles have a separate `install` target that lets you `make` with plain user permissions and then `sudo make install` for exactly this reason.

Hope this helps.

---

### Post by leo_br_hidro on 2015-07-14
Thank you for your fast response, this is a really good community, I'm impressed.

About installs:
> **steeldriver said:**
> 
`sudo` does not inherit your user's environment (primarily for security reasons). Although you could add the equivalent PATH, LD_LIBRARY_PATH etc. definitions to the sudo environment it's really not good practice: it would be better to arrange your development directories so that you don't need to be root to compile things i.e. either build in your home directory or in a dedicated /usr/local/src directory with appropriately permissive write permissions. Many 3rd party makefiles have a separate `install` target that lets you `make` with plain user permissions and then `sudo make install` for exactly this reason.


During the intel fortran compiler installation, I didn't pay that much attention if it asked me where to install it. All I know is that it ended up in /root/opt/intel/

Regarding that makefile, I created a /lib folder under my home directory (/home/leonardo/lib) for the program. Apparently, I can't do much there without sudo either, even though it's supposed to be my directory. How do I figure out which directories are permissive?

Since ifort appears to be installed, I think I'm not capable of flagging it correctly in the makefile. I'd be also really grateful for some help with that.

Cheers and thanks again.

---

### Post by leo_br_hidro on 2015-07-14
Hi there slickymaster, thank you for the heads up. I didn't mean to use the other thread only to ask more questions. I thought that maybe the extra information in the beginning of my post would add value, and that it was all related. I'll create my own threads if I'm in doubt if I'm asking questions more than giving solutions.

---

### Post by steeldriver on 2015-07-14
Well as far as permissions and ownership are concerned, `sudo` (like Homer's alcohol) is the cause of and solution to all of life's problems - to start, try

```

sudo chown leonardo:leonardo /home/leonardo/lib

```

and then run your make command again **without** sudo

---

### Post by slickymaster on 2015-07-14
> **leo_br_hidro said:**
> Hi there slickymaster, thank you for the heads up. I didn't mean to use the other thread only to ask more questions. I thought that maybe the extra information in the beginning of my post would add value, and that it was all related. I'll create my own threads if I'm in doubt if I'm asking questions more than giving solutions.

Sure. No problem.

---

