---
title: "HOWTO: Upgrade to the latest release of Banshee (0.11.3)"
date: 2006-12-29
forum: Outdated Tutorials &amp; Tips
---

### Post by happy-and-lost on 2006-12-29
I have a real soft spot for the Banshee music manager, but the version in the repos is out of date and a little buggy, so here's my howto for updating to the latest release :KS 

P.S. This is my first howto, use at your risk! Any suggestions are appreciated, there's bound to be an easier/more efficient way of doing this! :D

P.P.S. This is written assuming you have already installed Banshee and the plugins from the repos!

**1. Get The Sources**
Go to [http://banshee-project.org/Releases]("http://banshee-project.org/Releases") and get the tarball of the latest release and the plugins tarball.

**2. Install Useful Stuff and Dependencies**
Make sure you have the uni/mulitverse repos enabled first!

Paste this into your terminal...
```
sudo apt-get update
sudo apt-get install module-assistant build-essential
sudo apt-get install fakeroot dh-make debhelper debconf libstdc++5 linux-headers-$(uname -r)
```

(I don't actually know if you need these, by the way, but they're useful packages to have)

And now for the dependencies...

```
sudo aptitude install libglib2.0-dev libdbus-1-dev libdbus-glib-1-dev libgtk2.0-dev libgnomevfs2-dev libmusicbrainz4-dev libnautilus-burn-dev libgstreamer0.10-dev libgstreamer-plugins-base0.10-dev libmono-dev monodoc libsqlite3-dev libavahi-core-dev libavahi1.0-cil
```

**3. Install!**
Unzip the tarball containing the program (banshee-0.11.3.tar.gz, probably) into your home folder. Now open a terminal and...

```
cd banshee-0*
./configure
```

And if all is well, the last few lines should be...

> banshee-0.11.3

    Install Prefix:    /usr/local
    Datadir:           /usr/local/share
    Libdir:            /usr/local/lib

    C Compiler:        gcc
    Mono C# Compiler:  /usr/bin/mono ${top_srcdir}/build/gmcs.exe
    Mono Runtime:      /usr/bin/mono

    Engines:
      GStreamer:       yes
      Helix Remote:    no

    Digital Audio Players (DAP):
      iPod:            no
      NJB:             no
      MTP:             no
      Karma:           no

    DAAP Support:      yes, Avahi



If it looks like that proceed to...

```
sudo make

sudo make install
```

Now check Banshee will actually open...

And if it works, there you have it! :mrgreen: 

**Now For The Plugins**
I can honestly say that I can see no difference between the previously installed versions of the plugins and the new ones, but if you want to install the plugins...

Get the source code in the same place as you got the Banshee sources, and install the dependencies like this:

```
sudo aptitude install libmono-system-runtime2.0-cil libmono-system-runtime1.0-cil mono-gmcs
```

Then untar the plugins (the next bit assumes you've utared it into home), open the command line and:

```
cd banshee-official*
sudo ./configure
sudo make
sudo make install
```

Et voila.

WARNING: My mini mode plugin broke after doing this, so I wouldn't recommend doing this, it is unnecessary and doesn't add any features!

Hope that helps!

---

### Post by crazdmnd on 2006-12-31
Thanks dude...this is just what i've been looking for...i like banshee too but was considering abandoning to another system because of the bug of stopping shuffle mode if a codec wasnt found..i'd still like lirc support though...

my install came up with some errors...an error 2 in the make and an error 1 in the make install...however banshee launched fine and the splash screen appeared as 0.11.3...seems the newer features are there too (see the close cntrl-w option as well as it skips over tracks without codecs)...anybody else have errors in their install?

anxiously awaiting the plugins!  thanks again!

end of make:
Making all in Banshee.Hyena
make[3]: Entering directory `/home/bmelcer/Desktop/banshee-0.11.3/src/Banshee.Hyena'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/bmelcer/Desktop/banshee-0.11.3/src/Banshee.Hyena'
make[3]: Entering directory `/home/bmelcer/Desktop/banshee-0.11.3/src'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/bmelcer/Desktop/banshee-0.11.3/src'
make[2]: Leaving directory `/home/bmelcer/Desktop/banshee-0.11.3/src'
Making all in docs
make[2]: Entering directory `/home/bmelcer/Desktop/banshee-0.11.3/docs'
mcs -out:MonodocNodeConfig.exe -r:System.Xml MonodocNodeConfig.cs
make[2]: mcs: Command not found
make[2]: *** [MonodocNodeConfig.exe] Error 127
make[2]: Leaving directory `/home/bmelcer/Desktop/banshee-0.11.3/docs'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/bmelcer/Desktop/banshee-0.11.3'
make: *** [all] Error 2

end of make install:
make  install-data-hook
make[3]: Entering directory `/home/bmelcer/Desktop/banshee-0.11.3/docs'
/usr/bin/mono ../docs/MonodocNodeConfig.exe --insert "Banshee Libraries" classlib-banshee /usr/lib/monodoc/sources/../monodoc.xml
cannot open assembly ../docs/MonodocNodeConfig.exe
make[3]: *** [install-data-hook] Error 2
make[3]: Leaving directory `/home/bmelcer/Desktop/banshee-0.11.3/docs'
make[2]: *** [install-data-am] Error 2
make[2]: Leaving directory `/home/bmelcer/Desktop/banshee-0.11.3/docs'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/bmelcer/Desktop/banshee-0.11.3/docs'
make: *** [install-recursive] Error 1

---

### Post by foxy123 on 2007-01-06
I wonder why you do
```
**[COLOR="Red"]sudo[/COLOR]** ./configure
**[COLOR="Red"]sudo[/COLOR]** make
```

as far as I know it usually does not require sudo

---

### Post by happy-and-lost on 2007-01-06
Foxy, the sudo ./configure was a mistake, thanks for pointing that out. I always sudo make 'cos it means I only have to press the up arrow and type install, rather than type out the whole sudo make again. I'm *that* lazy ;)

---

### Post by Beamvr6 on 2007-01-28
I Just managed to install 0.11.4 using this thread, info on:

[http://banshee-project.org/Distributions/Ubuntu](http://banshee-project.org/Distributions/Ubuntu)

and

[http://directhex.mfgames.com/](http://directhex.mfgames.com/)

The latter is where the Ubuntu deb for 0.11.4 is hosted while the page for the deb on banshee-project.org seems to be terminated and redirects in a browser to 
[http://directhex.mfgames.com/](http://directhex.mfgames.com/)

Afaik what I was doing as newbie the process is:
- Install Banshee using Synaptic (so you get the old version installed first)
- Follow instructions in the "How do I use badgerports?" section on [http://directhex.mfgames.com/](http://directhex.mfgames.com/)
- Close Synaptic
- Run "sudo apt-get dist-upgrade" from the command line.

---

### Post by jKeats3 on 2008-03-09
> my install came up with some errors...an error 2 in the make and an error 1 in the make install...however banshee launched fine and the >splash screen appeared as 0.11.3...seems the newer features are there too (see the close cntrl-w option as well as it skips over tracks without codecs)...anybody else have errors in their install?

crazdmnd, I had this issue too, except now with Banshee 13.2.  The program opens though and displays "ver 13.2" in the about.  To tell the truth, I haven't spent much time using Banshee, so I'm not sure if all the features that need to be working in fact are working.

---

