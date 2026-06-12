---
title: "Eclipse search path ($PATH variable not seen)"
date: 2009-04-24
forum: Programming Talk
---

### Post by McThunderThighs on 2009-04-24
Hey all!

I am having some trouble getting Eclipse IDE to work in developing C programs.

When attempting to compile I get this error:
```
**** Build of configuration Default for project controller test **** 

make -k all 
make: psp-config: Command not found 
Makefile:16: /lib/build.mak: No such file or directory 
make: *** No rule to make target `/lib/build.mak'. 
make: Failed to remake makefile `/lib/build.mak'. 
make: *** No rule to make target `all'.
```

If I compile the project through the terminal everything works fine.  I believe Eclipse is not able to see the $PATH variable (which points to the directory containing psp-config).

How do I tell Eclipse to use my $PATH variable to look for psp-config?

Thanks so much!

---

### Post by Arndt on 2009-04-24
> **McThunderThighs said:**
> Hey all!

I am having some trouble getting Eclipse IDE to work in developing C programs.

When attempting to compile I get this error:
```
**** Build of configuration Default for project controller test **** 

make -k all 
make: psp-config: Command not found 
Makefile:16: /lib/build.mak: No such file or directory 
make: *** No rule to make target `/lib/build.mak'. 
make: Failed to remake makefile `/lib/build.mak'. 
make: *** No rule to make target `all'.
```

If I compile the project through the terminal everything works fine.  I believe Eclipse is not able to see the $PATH variable (which points to the directory containing psp-config).

How do I tell Eclipse to use my $PATH variable to look for psp-config?

Thanks so much!

The IDE does see the PATH variable, but it sees it as it was when the IDE was started. If you change PATH in another shell, it doesn't affect the IDE. That's what seems the likely explanation to me.

I don't know how you start the IDE, but if it's from a shell, then set PATH first so you can find psp-config, then start the IDE.

---

### Post by McThunderThighs on 2009-04-24
These are all the ways I have tried to run eclipse:

```
james@james-laptop:~/Desktop/eclipse$ ./eclipse
```
Still can't compile.

```
james@james-laptop:~/Desktop/eclipse$ sudo ./eclipse
```
Also won't let me compile.

```
james@james-laptop:~/Desktop/eclipse$ sh ./eclipse
```
Still no love.

I really feel like there is a basic solution that I am just missing entirely.

Thanks!

---

### Post by Arndt on 2009-04-24
> **McThunderThighs said:**
> These are all the ways I have tried to run eclipse:

```
james@james-laptop:~/Desktop/eclipse$ ./eclipse
```
Still can't compile.

```
james@james-laptop:~/Desktop/eclipse$ sudo ./eclipse
```
Also won't let me compile.

```
james@james-laptop:~/Desktop/eclipse$ sh ./eclipse
```
Still no love.

I really feel like there is a basic solution that I am just missing entirely.

Thanks!

I haven't used eclipse, but do you really keep it in the current directory, as ./eclipse suggests?

In any case, do you find this psp-config in the shell? Do "whereis psp-config".

---

### Post by McThunderThighs on 2009-04-24
I had just downloaded a copy of eclipse to see if the problem was with the repository version.  I have since gone back to the repository version.

```
james@james-laptop:~$ whereis psp-config
psp-config:
```

Copy and pasted out of my terminal.

Thanks!

---

### Post by Arndt on 2009-04-24
> **McThunderThighs said:**
> I had just downloaded a copy of eclipse to see if the problem was with the repository version.  I have since gone back to the repository version.

```
james@james-laptop:~$ whereis psp-config
psp-config:
```

Copy and pasted out of my terminal.

Thanks!

The output from 'whereis' tells me that 'psp-config' is not found using the PATH that is in effect in that shell, and then the IDE started there won't find it either. You need to set PATH so that psp-config is found.

---

### Post by McThunderThighs on 2009-04-24
I checked paths and everything:  Eclipse is still unhappy.
```
james@james-laptop:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/pspdev/bin:/usr/local/pspdev/psp/sdk/bin
james@james-laptop:~$ cd $PSPDEV/bin
james@james-laptop:/usr/local/pspdev/bin$ dir
bin2c           psp-as          psp-gcc     psp-nm       psp-size
bin2o           psp-build-exports  psp-gcc-4.3.2  psp-objcopy  psp-strings
bin2s           psp-c++          psp-gccbug     psp-objdump  psp-strip
mksfo           psp-c++filt      psp-gcov     psp-prxgen   remotejoy
mksfoex        psp-config      psp-gdb     psp-ranlib   unpack-pbp
pack-pbp       psp-cpp          psp-gdbtui     psp-readelf  usbhostfs_pc
psp-addr2line  psp-fixup-imports  psp-gprof     psp-run
psp-ar           psp-g++          psp-ld     pspsh
james@james-laptop:/usr/local/pspdev/bin$ psp-config
Usage: psp-config [opts]
Options:
-p, --pspsdk-path       : Print the base directory of PSPSDK
-d, --pspdev-path       : Print the base install directory
-P, --psp-prefix        : Print the prefix of PSP-hosted software
james@james-laptop:/usr/local/pspdev/bin$ cd ~
james@james-laptop:~$ psp-config
Usage: psp-config [opts]
Options:
-p, --pspsdk-path       : Print the base directory of PSPSDK
-d, --pspdev-path       : Print the base install directory
-P, --psp-prefix        : Print the prefix of PSP-hosted software
james@james-laptop:~$ eclipse
searching for compatible vm...
  testing /usr/lib/jvm/java-gcj...found
Could not create /usr/local/lib/eclipse/.eclipseextension. Please run as root:
    touch /usr/local/lib/eclipse/.eclipseextension
    chmod 2775 /usr/local/lib/eclipse/.eclipseextension
    chown root:staff /usr/local/lib/eclipse/.eclipseextension


```

It looks to me that eclipse is being loaded by root, is this right?  If that is the case, then $PATH isn't set for root, so that would explain everything.

---

