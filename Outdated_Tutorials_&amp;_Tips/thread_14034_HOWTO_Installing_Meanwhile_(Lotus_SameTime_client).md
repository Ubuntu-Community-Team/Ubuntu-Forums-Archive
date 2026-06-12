---
title: "HOWTO: Installing Meanwhile (Lotus SameTime client) for Gaim"
date: 2005-02-04
forum: Outdated Tutorials &amp; Tips
---

### Post by marxby on 2005-02-04
This document (brief as it is) is intended to help the average joe install Meanwhile and the Gaim-Meanwhile plugin, which will allow you to connect to a Lotus Sametime server with Gaim.  As there was not an appropriate package I tried installing it on my own, which was a wee bit of a headache, so I thought I better write it out.

I am running Hoary 5.04, without anything TOO odd installed...

1) Download meanwhile and gaim-meanwhile from [the Meanwhile SourceForge site](http://meanwhile.sourceforge.net/download/) 
2) Extract the archives to a temporary folder.
```
dave@DaveD:~ $ mkdir Packages
dave@DaveD:~ $ tar xzvf meanwhile-0.3.tar.gz Packages/
dave@DaveD:~ $ tar xzvf gaim-meanwhile-1.0.2.tar.gz Packages/
``` 
3) First, configure and compile Meanwhile.  I use the prefix "/usr" because the Gaim plugins are installed in /usr/lib/gaim.
```
dave@DaveD:~ $ cd Packages/meanwhile-0.3
dave@DaveD:~ $ ./configure --prefix=/usr
dave@DaveD:~ $ make
``` 

At this point I ran into a little problem.  Namely, this error:
```
In file included from session.c:10:
mw_debug.h:12:1: "g_debug" redefined
In file included from /usr/include/glib-2.0/glib.h:52,
                 from session.c:3:
/usr/include/glib-2.0/glib/gmessages.h:138:1: this is the location of the previous definition
make[1]: *** [libmeanwhile_la-session.lo] Error 1
``` 

Thanks to the nice gents over in the [Gentoo forums](http://forums.gentoo.org), I discovered the fix was to modify the src/mw_debug.h file and change the lines
```
#define g_debug(format...) g_log(G_LOG_DOMAIN, G_LOG_LEVEL_DEBUG, format)
#define g_info(format...) g_log(G_LOG_DOMAIN, G_LOG_LEVEL_INFO, format)
``` 
to read
```
#ifndef g_debug
#define g_debug(format...) g_log(G_LOG_DOMAIN, G_LOG_LEVEL_DEBUG, format)
#endif
#ifndef g_info
#define g_info(format...) g_log(G_LOG_DOMAIN, G_LOG_LEVEL_INFO, format)
#endif 
```
After changing these lines, I was able to rerun make without any issues.
4) Next, install Meanwhile.
```
dave@DaveD:~ $ make install
``` 
5) Now, we must compile and install Gaim-Meanwhile.  First, enter that directory:
```
cd ~/Packages/gaim-meanwhile-1.0.2
``` 
6) Next, configure and compile Gaim-Meanwhile.  Again, use the proper prefix.
```
dave@DaveD:~ $ ./configure --prefix=/usr
dave@DaveD:~ $ make
``` 
I ran into a number of issues with missing libraries, all of which I was able to find and install through Synaptic.
7) Now, install the plugin.
```
dave@DaveD:~ $ sudo make install
``` 
8) Before you get excited and fire up Gaim, I found that I had to run ldconfig before Gaim properly recognized my plugin.
```
dave@DaveD:~ $ sudo ldconfig
``` 

That's it!  Fire up Gaim and give it a whirl.  If you still find that the plugin isn't loading, run Gaim in debug mode to see if it gives any errors about the plugin:
```
dave@DaveD:~ $ gaim -dn
``` 
You are looking for a line similar to this:
```
plugins: probing /usr/lib/gaim/libmwgaim.la
plugins: probing /usr/lib/gaim/libmwgaim.so
``` 


Enjoy...

---

### Post by digitalvoid on 2005-02-14
While building this I ran into similar troubles with libs and compiler versions but this last issue has be a bit stumped which eventually led me back here (google always brings us home).   ;-)

Did you build gaim yourself or are you using one in main or universe?  I tried a couple of different versions found in synaptic but none of them came with the gaim.pc file (package config).  When I run ./configure for gaim-meanwhile it complains and quits with this: 

```
checking for gaim... Package gaim was not found in the pkg-config search path.
Perhaps you should add the directory containing `gaim.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gaim' found

configure: error: Library requirements (gaim) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
dewey@null /opt/gaim-meanwhile-1.0.2 $
```

Any ideas?  I'd rather not maintain my own build of gaim since the one in the backported-from-hoary repository is current enough for me.

---

### Post by EndersGame on 2005-02-16
I'm having the same problem with gaim plugins not finding gaim.pc.  I assume there's a simple solution to this.  Has anyone found it?

Thanks!

---

### Post by marxby on 2005-02-17
I haven't had that problem, but I did install gaim-dev first, which I believe you will need to do before you can successfully compile.

---

### Post by RickKnight on 2005-02-25
[QUOTE=marxby]I haven't had that problem, but I did install gaim-dev first, which I believe you will need to do before you can successfully compile.[/QUOTE]
 I had the same problems (PKG_CONFIG_PATH and gaim.pc). The solution in my case was to remove the distro (Slack 9.0) supplied gaim and install the latest gaim-1.1.4 from source using the same configure option, --prefix=/usr. That put the needed game.pc in /usr/lib/pkgconfig.

Hope that helps,
RickKnight

---

### Post by mwarden on 2005-03-16
[QUOTE=marxby]I haven't had that problem, but I did install gaim-dev first, which I believe you will need to do before you can successfully compile.[/QUOTE]

I was having this problem as well and came across this forum discussion. Your suggestion to install gaim-devel package did indeed work. So if others are having this problem, just install gaim-devel and then make the source.

Thanks.

---

### Post by evilcartman on 2005-05-17
I'm running hoary and I simply downloaded the rpms for meanwhile and gaim-meanwhile from the sourceforge site, used "sudo alien" to convert them to deb and "sudo dpkg" to install. I'm happily running Gaim against our corporate Sametime server, and it works like a champ.  :-P

---

### Post by joebwan on 2005-05-18
[QUOTE=evilcartman]I'm running hoary and I simply downloaded the rpms for meanwhile and gaim-meanwhile from the sourceforge site, used "sudo alien" to convert them to deb and "sudo dpkg" to install. I'm happily running Gaim against our corporate Sametime server, and it works like a champ.  :-P[/QUOTE]

I attempted to do the same thing from hoary today, and had some trouble with Gaim loading the plugin.  Once I added the backports repositories to my sources.list file and upgraded Gaim it worked fine.

---

### Post by jassinpain on 2005-06-27
[QUOTE=evilcartman]I'm running hoary and I simply downloaded the rpms for meanwhile and gaim-meanwhile from the sourceforge site, used "sudo alien" to convert them to deb and "sudo dpkg" to install. I'm happily running Gaim against our corporate Sametime server, and it works like a champ.  :-P[/QUOTE]
As the above says make sure you install meanwhile for the libmeanwhile.so not just gaim-meanwhile

same stuff download rpm, alien -d rpmname, dpkg -i newpkg

Joshua SS Miller

---

