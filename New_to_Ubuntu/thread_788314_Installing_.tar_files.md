---
title: "Installing .tar files"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by razlken on 2008-05-09
Hi, i just started using Ubuntu Hardy Heron, it's been like three days now and i had my ups and downs with this new OS, anyway now the prob is installing "tarballs"... i read lots of guide and everything but still got some problems after typing "./configure"

```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking aspell.h usability... yes
checking aspell.h presence... yes
checking for aspell.h... yes
checking pspell/pspell.h usability... yes
checking pspell/pspell.h presence... yes
checking for pspell/pspell.h... yes
checking for new_aspell_speller in -laspell... yes
checking for pkg-config... /usr/bin/pkg-config
checking for gtk+-2.0... Package gtk+-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtk+-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-2.0' found
configure: error: Library requirements (gtk+-2.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

```

so it seems that i am having some problems towards the end at this point:

```
checking for gtk+-2.0... Package gtk+-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtk+-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-2.0' found
configure: error: Library requirements (gtk+-2.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
```

Can't understand what is the prob is it a configuration problem or a missing package, any help would be appreciated and thanks in advance

---

### Post by Bigtime_Scrub on 2008-05-09
You have to unpackage tar files. I dont know if thats what u r trying to do or not. I run this command and it will unpackage and install.

Code:

tar xjvf *file_name_here*.tar.bz2

---

### Post by SunnyRabbiera on 2008-05-09
you really dont have to compile if you dont need to, by chance what are you trying to install?

---

### Post by razlken on 2008-05-09
i did that, then i "cd" to the newly created folder and type "./configure" that is where i get the problem, if i try typing "make" it does nothing just gives an error saying there is no file to make...

---

### Post by SunnyRabbiera on 2008-05-09
well like i said what are you trying to compile, and why?
most of all you will ever need is in the repositories

---

### Post by razlken on 2008-05-09
i was trying to compile "gtkspell-2.0.10" a spellcheck plug in for emesene (not sure if it's only for that) i looked for it on the net and found only a ".tar.gz" archive & didn't find it in the Synaptic Package Manager.

---

### Post by KIAaze on 2008-05-09
It's probably a missing package.
Make sure you have libgtk2.0-0 and libgtk2.0-dev installed:
```
sudo apt-get install libgtk2.0-0 libgtk2.0-dev
```

Also a little tip if you want to compile a package from the repositories from source:
```
apt-get source <package>
apt-get build-dep <package>

```
The first command gets the source code and the second one gets all necessary dependencies.
Then all you have to do is extract, configure, compile and eventually install. ;)

---

### Post by mc4man on 2008-05-09
Whether it works for what you want search in synaptic libgtkspell and or aspell

---

### Post by KIAaze on 2008-05-09
> **ExpertAnalysis said:**
> I know what's giving you that error message.  What you need to resolve these matters is a fresh, clean install.
gtk+-2.0.pc is in the libgtk2.0-dev package:
[http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=gtk%2B-2.0.pc](http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=gtk%2B-2.0.pc)

So unless he really messed around in /usr/lib, there should be no need to reinstall.
In the worst case, it might even be possible to solve this problem by hacking around manually like setting the pkg-config search path as suggested by the error message.
And even then reinstalling the necessary packages is probably easier.

---

### Post by razlken on 2008-05-09
well installed the package and worked totally fine, type "./configure", "make" & it worked great, last question i remember reading there are 2 commands for install, right? one which created an entry in Synaptic Manager anyone care to share that command & where can i actually find a place to read all commands on the net?

---

### Post by KIAaze on 2008-05-09
Yes, that's correct there are 2 possible commands.
The usual one is:
```
sudo make install
```
But this doesn't create an entry in Synaptic, so it's almost impossible to uninstall cleanly later unless the source package also offers an uninstallation script.

To add an entry to Synaptic, you need to create a .deb and then install it.
This is done using the checkinstall program.
See here for how to use it:
[http://www.debian-administration.org/articles/147](http://www.debian-administration.org/articles/147)

---

### Post by razlken on 2008-05-09
ok Thanks a lot guys it helped a lot, i must say linux is has certain aspects that are difficult to use for newbies but it has a great community, thanks again!!!

---

### Post by KIAaze on 2008-05-09
Also, since you asked for where to find out about commands:
[http://www.tuxfiles.org/linuxhelp/cli.html](http://www.tuxfiles.org/linuxhelp/cli.html) (basic comands)
[http://linuxcommand.org/index.php](http://linuxcommand.org/index.php) (from basic commands to advanced shell-scripting)

And don't forget to use the manual:
> man <command>

I don't know your level of familiarity with GNU/Linux yet (because installing from source is already relatively "advanced" ^^), but if you are still fairly new, this is a very good starting point:
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

---

### Post by KIAaze on 2008-05-09
Oh and one more thing:
Manual pages can be read in a more attractive way using "yelp":
```
yelp man:<command>
```

Or by launching yelp by going to "System->Help and support" and then searching for man:<command>.

This is especially useful for very long manual pages.
Of course, you can also find them in even more attractive formats on the internet...

```
info <command>
```
also works sometimes.

---

### Post by razlken on 2008-05-09
cool!! thanks a lot, now i have lots of stuff to study :D:D

---

