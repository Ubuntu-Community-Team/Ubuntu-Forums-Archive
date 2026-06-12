---
title: "updating libPNG for PHP"
date: 2017-11-11
forum: New to Ubuntu
---

### Post by myohmyke on 2017-11-11
I'm working with Ubuntu for the first time -- it took me 20 minutes to find the /usr/ folder when setting up an RTMP server, because I thought "root" was the "\" folder. Oops.  But I managed to get the RTMP server going, and followed the LAMP instructions for my DigitalOcean droplet and got that set up as well.  And everything's working great! Except for one thing -- certain parts of the PHP install are outdated compared to what my XAMPP localhost is using, and I think that's what is causing the issue.

First, I used 
```
[COLOR=#3A3A3A][FONT=monospace]sudo apt-get install php libapache2-mod-php php-mcrypt php-mysql[/FONT][/COLOR]
```
```
[COLOR=#3A3A3A][FONT=monospace]sudo apt-get install php-gd[/FONT][/COLOR]
```

to set up to begin with.  From phpinfo(), this gave me:
-PHP 7.0.22
-GD Headers/Library 2.1.1
-libPNG 1.2.54

I've been using an XAMPP localhost until now, and PHP info says that is:
-PHP 5.6.28 (older)
-GD Version "bundled 2.1.0 compatible (older?)
-libPNG 1.5.26 (newer)

I think either the GD or the libPNG need to be updated, because my code works differently on my DO Droplet than on my XAMPP server.  I have something set up at a free webhost with PHP access, and the code works there too -- so it's not specifically about "going live," it's something with this particular installation.  Unfortunately, I don't know enough Ubuntu-ease to know how to update libPNG for PHP specifically.

I googled how to go about uninstalling PHP, then used this to reinstall:
```
[COLOR=#3A3A3A][FONT=monospace]sudo apt-get install php7.0-gd libapache2-mod-php php-mcrypt php-mysql[/FONT][/COLOR]
```

And now my PHP Info page lists "GD Library" in the credits, but doesn't have a separate GD section listing version info at all. [s]And now it isn't creating a PNG file at all -- the same behavior it had before I realized I had to install php-gd separately[/s] (I think I forgot a restart, but the phpinfo is unchanged).  So now I'm further back than I was before.  This is a small thing for a one-day event, and I'm not far enough in that nuking and restarting from scratch would be a big deal (I could use the practice anyway!), but there's no sense doing that without some extra guidance.

I don't know enough to know if this is really an Ubuntu question or a PHP question.  PHP suggests I configure it with --with-gd or even --with-gd=[LOCALPATH] or something similar, but I don't know enough Ubuntu to know where to go to ./configure it.  I was able to configure my RTMP install 'cause I had a walkthrough, but I don't know where the PHP source folder is.  Installing libPNG that way also requires zlib, and apt-get install zlib gave me nothin', but I haven't looked further into that yet since I don't know if I'm even on the right track.

Edit: I've tried using apt upgrade and apt update before and after installation, with the same results.

Edit: In case it matters -- the one feature that seems to be missing between the versions is support for transparency. XAMPP & 000webhost's PHP both handle transparency, the DigitalOcean droplet replaces it with solid black.  I'm using PNG for transparency support, but I suppose GIF is also an option.

---

### Post by Impavidus on 2017-11-11
Which version of Ubuntu?

Older versions of Ubuntu come with libpng 1.2, later versions with libpng 1.6, Ubuntu 16.04 with both.

---

### Post by myohmyke on 2017-11-11
The server info page says Ubuntu 16.04.3 x64 -- so it would have both 1.2 and 1.6 installed.

See, I wouldn't have guessed that the server would have libPng installed for the server as a whole, and that PHP just installed it for itself to use, the way I'd need to put lame.dll somewhere for Audacity but other programs wouldn't see it.

I went ahead and remade the server droplet, just to start off clean.  I might have tried to apt-get download PHP and *cough* made a total mess of the directory not knowing it wouldn't go in a subfolder, and I wanted to make sure PHP was a fresh install.  If the server already has libPNG 1.6, how do I get PHP to use it?  If I have to use the ./configure command, I need to download the PHP source and configure>make>install.  I think?  I'm trying to apply what my RTMP walkthrough had me do to this, but it might not be apples to oranges.

---

### Post by Impavidus on 2017-11-12
Best to stay away from installing from source code and ./configure scripts unless there's no other way.

I don't know whether libpng 1.2 and 1.6 are installed by default in Ubuntu 16.04 server, but both are available from the repositories. They can be installed with```
sudo apt install libpng12-0
sudo apt install linpng16-16
```respectively. If you need the development versions (with header files), use **libpng12-dev** or **libpng16-dev**. Libraries installed through apt are installed system-wide.

Ubuntu 16.04 has php 7.0, which can be installed using apt as the package **php** (or **php7.0**, which is an alias). Gd is provided by **php-gd**, as you already found. It's a bit hard to get different versions than those. Sometimes you can get a more recent version of some software (usually the latest) from a PPA or you can use manual installation, but that's quite hard and wouldn't give you automatic security updates. So don't do that unless there's really no other way.

I never installed php myself and am not familiar with gd. I don't know what it will do when presented with 2 versions of libpng. Is it compiled to run always with 1.2, will it use the latest it can find, is there some way for the user to decide? I can't tell.

---

### Post by Holger_Gehrke on 2017-11-12
Since I have apache with php and gd installed and running on my system and know a bit about the way libraries work on Linux I'll try to help. 

When you install anything through the package management on Ubuntu, it always get installed system wide and in the directories given in the package. So an 'apt install' will never "make a total mess of the directory".

To find out which libpng you have installed through packages, you can use
```
dpkg-query --list 'libpng*' | grep '^ii'
```
This looks up all packages with a name beginning with 'libpng' and filters for the ones installed.

Holger

---

### Post by myohmyke on 2017-11-13
I might have misspoke.  I was getting the feeling I might have to compile PHP from source, so I decided to be clever and try to figure it out myself and did an apt-get (download or source) Suddenly, I had at least 10-15 files of all sorts just co-mingled with everything else I had on root, so even if those were the files I needed to do something with they weren't in a subfolder to work out of, so it was another good excuse just to start from scratch.  Now that I know how to do it, doing the RTMP setup is a piece of cake anyway.

I tried using apt-get install libpng16-16, then doing the LAMP install.  PHP still had libPNG1.2.  I tried apt-uninstalling libpng12-0, then installing 16-16, PHP *still* had libPNG1.2.

So I said forget and tried to figure out how to do it all from source -- PHP's ./configure specifically has a flag where you tell it where your libpng installation is, and I hoped that would just force-feed it libPNG16-16.  But I also wasn't sure where the heck the libPNG16-16 installation was, I could find the doc folders for it but that's obviously not what PHP is looking for.  So I installed that from source too, following a guide from linuxfromscratch that told me where the new folders would be.  And that worked -- even if it was the most roundabout way to go about it, I knew where all the moving parts were at least.

Which is when I realized...the LAMP guide had me apt-get additional things, like php-mcrypt php-mysql.  And for the simple project I'm using it for (rotating a list of text and this daggone image cropping), I don't know if i need those, but I didn't want to configure without php-ReallyBasicThingThatIMissByBeingNoob, so I found a Moodle PHP installation guide that at least pointed out enough configuration flags for me to make sure I had an idea of things you'd want to set configure flags for, including the source and dependances I needed to pre-install and so forth.

The configure worked, make and make test checked out.  The make install ended with a "You need to use a thread-safe version of PHP, please recompile" error message. I went looking around about that, it seems like if I wanted to do thread-unsafe, I"d have to specifically set a thread-unsafe flag (I didn't) or download a thread-unsafe versin of PHP -- but I got it from php.net directly, so...I don't think I did that? It doesn't have a separate listing for that, at least.

The last thing that I just tried, from a clean DigitalOcean server droplet, was update apt-get, uninstall libpng12-0, install libpng16-16, then do LAMP.  Still no dice.  That's when I came here and saw Holger's tip on how to look for libpng.  It now lists the following:

```
ii  libpng12-0:amd64  1.2.54-1ubuntu1 amd64        PNG library - runtime
ii  libpng16-16:amd64 1.6.20-2        amd64        PNG library - runtime (version 1.6)

```

Naturally, I didn't see the post until after I isntalled PHP, so I don't know if apt-get uninstall libpng12-0 just didn't actually do what I thought, or if apt-get install PHP is just installing libpng12-0 along with it.  I might take another swing at it with that in mind.

I'm willing to just change the way I handle the images and my PHP code at this point, I do have a few ideas in mind.  I just don't understand why transparency is handled so much differently between the two versions...which is to say, apparently, not at all in libpng12-0.  Before I reinstalled recently, I think my XAMPP localhost had the older libpng, cause it was doing exactly what the live server is doing now, and I would run everything through imagemagick back then -- that might be my next option.

Even though I'm stuck, it's honestly been fun being so darn clueless and learning things bit-by-bit, even in a bit of a backwards way.


Edit: After posting, I realized maybe I was closer than I thought.  I did apt-get *remove* libpng12-0 again, after installing PHP.  And it had something to remove!  Then I looked through the output and it uninstalled php-gd too.  I checked my PHPinfo and sure enough, GD is no longer listed at all.  Argh!  At least that identifies the problem, i think -- PHP-GD is installing libpng12-0 and simply refusing to look elsewhere.  I wonder if there's another source for that with the updated libpng library?  At least I have a lead now.

---

### Post by Impavidus on 2017-11-13
As I said, I've no experience with php or gd, but after digging a bit into the dependencies it appears that on 16.04 php-gd indeed depends on libpng12-0. If nothing else works, you could try Ubuntu 17.10, where it depends on libpng16-16. You sometimes get these problems once an LTS release gets a bit old, that's why I'm on the 6-month releases nowadays. But before you move to 17.10, I suggest you first test it in a life session or on a virtual machine.

I have done some programming with libpng 1.2 and never had any difficulty with transparency. I'm not sure how your problem may be caused.

---

### Post by Holger_Gehrke on 2017-11-13
> 
The last thing that I just tried, from a clean DigitalOcean server  droplet, was update apt-get, uninstall libpng12-0, install libpng16-16,  then do LAMP.  Still no dice.  That's when I came here and saw Holger's  tip on how to look for libpng.  It now lists the following:
```

     ii  libpng12-0:amd64  1.2.54-1ubuntu1 amd64        PNG library - runtime
     ii  libpng16-16:amd64 1.6.20-2        amd64        PNG library - runtime (version 1.6) 

```
Naturally, I didn't see the post until after I installed PHP, so I  don't know if apt-get uninstall libpng12-0 just didn't actually do what  I thought, or if apt-get install PHP is just installing libpng12-0  along with it.  I might take another swing at it with that in mind.


"apt" means Advanced Package Tool. It's called 'Advanced' because it takes care of downloading the packages and their DEPENDENCIES. Every package has a list of other packages that are needed for it to work and apt installs everything needed. To see the dependencies (even before installing) you can use:'apt show php-gd'. This would show -- on my system -- that php-gd depends on php7.0-gd, which depends among others on libgd3 which depends on libpng16-16. This chain of dependencies will probably be different on your system.

After reading Impavidus comment about using libpng 1.2 and not having problems with transparency I asked my favorite [duck]("http://duckduckgo.com") about 'php gd png transparency' and found problems and solutions going back to **2002**. I think the problem might not be the library itself but some subtle difference between the windows (which I assume you were using for your local XAMP) and linux versions of the libs - possibly different defaults when creating images. So it might actually be something in your code ...

Holger

---

