---
title: "what's your preferred subversion client? svn"
date: 2006-10-26
forum: Programming Talk
---

### Post by jrjazzman on 2006-10-26
Coming from Windows, I'm apparently very spoiled by TortoiseSVN.  I'm curious to know what everyone is running.  Here are my experiences so far:

RapidSVN - Got this from the ubuntu repository.  Seemed to be very buggy, did not parse the svn repository contents correctly, and was clugy overall.  Tried to install latest version via tarball, but couldn't get the make to complete.

esvn - looks ok, but seems to be buggy as well.  When I open it it repeats some message ("get files ...") over and over in the status window. 

Subclipse - Seems pretty nice.  I have to use this for all my svn needs (even non-eclipse projects) since it's the only svn client I could get to work, other than the command line client.

I have not tried the Nautilus svn scripts that are out there, although I'm very curious to know if they work.  This would be ideal, and similar in functionality and integration to Tortoise.

---

### Post by cwaldbieser on 2006-10-26
> **jrjazzman said:**
> Coming from Windows, I'm apparently very spoiled by TortoiseSVN.  I'm curious to know what everyone is running.  Here are my experiences so far:

RapidSVN - Got this from the ubuntu repository.  Seemed to be very buggy, did not parse the svn repository contents correctly, and was clugy overall.  Tried to install latest version via tarball, but couldn't get the make to complete.

esvn - looks ok, but seems to be buggy as well.  When I open it it repeats some message ("get files ...") over and over in the status window. 

Subclipse - Seems pretty nice.  I have to use this for all my svn needs (even non-eclipse projects) since it's the only svn client I could get to work, other than the command line client.

I have not tried the Nautilus svn scripts that are out there, although I'm very curious to know if they work.  This would be ideal, and similar in functionality and integration to Tortoise.

kdesvn - it integrates well with konqueror, but I like using the stand-alone client.  I like using Kompare as the diff tool, too.

I also like using the command-line client.  For most tasks, it is sufficient for my needs, though I am no fan of reading unified diffs.

---

### Post by skymt on 2006-10-26
I like the official CLI client. Subclipse sure looks nice, though. I'll probably wind up using it if I ever have a major Java project.

---

### Post by rickbeton on 2006-12-12
> **jrjazzman said:**
> Coming from Windows, I'm apparently very spoiled by TortoiseSVN.  I'm curious to know what everyone is running.  Here are my experiences so far:

RapidSVN - Got this from the ubuntu repository.  Seemed to be very buggy, did not parse the svn repository contents correctly, and was clugy overall.  Tried to install latest version via tarball, but couldn't get the make to complete.

esvn - looks ok, but seems to be buggy as well.  When I open it it repeats some message ("get files ...") over and over in the status window. 

Subclipse - Seems pretty nice.  I have to use this for all my svn needs (even non-eclipse projects) since it's the only svn client I could get to work, other than the command line client.

I have not tried the Nautilus svn scripts that are out there, although I'm very curious to know if they work.  This would be ideal, and similar in functionality and integration to Tortoise.

I found this thread having asked the same question myself.

I use Subclipse a lot. It is good, but it's only useful to Eclipse users and I can't recommend it as a general SVN client.

As a general-purpose SVN client, SmartSVN looks promising - I've just been trying out the SmartSVN Foundation version (free as in free beer). It feels a bit like WinCVS to use (albeit it looks quite different and the SVN paradigm is of course different from CVS). It isn't open source and the Pro version is not cheap (IMO) but I expect the Foundation version will be useful to me.

Regards,
Rick

---

### Post by pmasiar on 2006-12-12
I use [pysvn workbench]("http://pysvn.tigris.org/docs/WorkBench.html") - added bonus it is multiplatform, same on windows

---

### Post by rickbeton on 2006-12-12
> **pmasiar said:**
> I use [pysvn workbench]("http://pysvn.tigris.org/docs/WorkBench.html") - added bonus it is multiplatform, same on windows

Thanks for the suggestion - I've just given it a try. Seems competent enough. :)

Although I managed to cause a few stacktraces to appear in the console pane, it didn't crash horribly or anything.

FWIW, SmartSVN is multi-platform too (actually, I've only tried it on Windowz and CentOS). Both GUIs provide a good feature set. It's good to have a reasonable choice.

Rick

---

### Post by pmasiar on 2006-12-12
For me, pysvn workbench dealbreakers are: 
[LIST]
[*]it is in python, so if anything will ge horribly wrong, I may contemplate to fix it. Note that I never needed to. :-)
[*]it is maintained as part of pysvn - python bindings to SVN, so I may reasonable expect it to survibe and be compatible with changing versions of SVN.
[/LIST]

---

### Post by neoflight on 2006-12-12
I am interested to know too...
in fact i had started a [_thread_]("http://ubuntuforums.org/showthread.php?t=294933") on the same and got some input...

a nice link was provided in post #11 of that thread ...very useful...

More input are welcome and appreciated...either in this thread or the thread in that link...

---

### Post by anthro398 on 2006-12-12
RapidSVN.

---

### Post by kiddo on 2006-12-12
[meld]("http://meld.sf.net") is an awesome tool, I use it all the time. While it can do all the SVN manipulations, I still do them all in the command line. It's strange, since I'm usually a GUI guy, I guess becoming a programmer is transforming me :)

---

### Post by Quikee on 2006-12-14
How do you get subclipse working with Ubuntu (feisty) Eclipse from repository? I always get an error if I download subclipse from within Eclipse and try to access SVN configuration or perspective. Any suggestions welcomed. 

To stay on topic I use KSVN currently.

---

### Post by rickbeton on 2006-12-15
> **Quikee said:**
> How do you get subclipse working with Ubuntu (feisty) Eclipse from repository? I always get an error if I download subclipse from within Eclipse and try to access SVN configuration or perspective. Any suggestions welcomed.

(Off-topic)  Make sure you've got write access to the Eclipse installation folder, especially to the sub-folders called 'plugins' and 'features'.  Also make sure you've got correct proxy settings, without which your download won't even start (for many people, the default blank proxy settings work OK).

For myself, I've simply used the Eclipse download and upacked the tarball into /opt/eclipse or similar location.  Eclipse doesn't require any other installation step than perhaps creating a shortcut for launching it. (This is a nice feature coz it means it's easy to use different installation folders and therefore have available several different versions of Eclipse, plus RAD or other suite based on Eclipse.)

Rick

---

### Post by Quikee on 2006-12-15
> **rickbeton said:**
> (Off-topic)  Make sure you've got write access to the Eclipse installation folder, especially to the sub-folders called 'plugins' and 'features'.  Also make sure you've got correct proxy settings, without which your download won't even start (for many people, the default blank proxy settings work OK).

For myself, I've simply used the Eclipse download and upacked the tarball into /opt/eclipse or similar location.  Eclipse doesn't require any other installation step than perhaps creating a shortcut for launching it. (This is a nice feature coz it means it's easy to use different installation folders and therefore have available several different versions of Eclipse, plus RAD or other suite based on Eclipse.)

Rick

Thanks for the reply however I don't think this is the problem. I succeeded downloading subclipse but when I want to use it, I get a ClassNotFoundException (for example when I want to access "SVN repository browsing" perspective). 

I then browsed the net, to get an answer and I discovered that subclipse doesn't work right with Eclipse which is natively compiled with GCJ (Eclipse in Ubuntu repository is natively compiled). I just wonder if someone succeeded to get "Ubuntu's" Eclipse and subclipse working together.

Otherwise the only option I have left is to download and install eclipse in the manner you used and described. In this case Eclipse would be using the Sun's JVM (if installed) and subclipse would hopefully work. 

Thanks for the answer.

---

### Post by loginx on 2007-02-26
> **Quikee said:**
> Thanks for the reply however I don't think this is the problem. I succeeded downloading subclipse but when I want to use it, I get a ClassNotFoundException (for example when I want to access "SVN repository browsing" perspective). 

I then browsed the net, to get an answer and I discovered that subclipse doesn't work right with Eclipse which is natively compiled with GCJ (Eclipse in Ubuntu repository is natively compiled). I just wonder if someone succeeded to get "Ubuntu's" Eclipse and subclipse working together.

Otherwise the only option I have left is to download and install eclipse in the manner you used and described. In this case Eclipse would be using the Sun's JVM (if installed) and subclipse would hopefully work. 

Thanks for the answer.

I finally got it working after working on this for a large part of the day (downloading eclipse updates is a very slow process). Basically, make sure you have libsvn-java installed and run the following:

```
 eclipse -os linux -vm /usr/lib/jvm/java-6-sun/bin/java -vmargs -Djava.library.path=/usr/lib/jni
```

In this case, I used Sun's JDK version 6 so your jvm path may vary, but otherwise this worked for me.

---

### Post by karik on 2007-07-10
*SmartSVN* is the best. Even the community edition.

---

### Post by rogier.de.groot on 2007-07-10
The Subversion support in NetBeans (installed via the Tools->Update Center wizard). It probably doesn't support everything subversion can do, but it integrates nicely and works like a charm.

---

### Post by iblis on 2007-07-10
i use the command-line client, 'svn'.

it just seems easier to me, though that's likely because it's the first i learned. :D

---

### Post by samjh on 2007-07-11
I just use SVN itself.

---

### Post by cgfoz on 2007-07-18
Well I just did a quick use in action of the following from this thread:
- rapidSVN - worked okay for a time, but was buggy when I switched my svn repository address. There's certainly some bugs still in there. Also it doesn't create new repositories for you, it tells you to do it from the command line!!
- eSVN - Couldn't even get it to log into my repositories, errors all over the place, horrible
- SmartSVN - The free edition, kind of worked. I'm running beryl, and it wouldn't maximise so I had a tiny little screen to work with. To update the detection of files (are they modified etc) you have to hit a refresh button. This takes approx 1minute for large sets of code, which I found unusable. Was stable and simple to set up tho
- kdesvn - Finally found what I needed thanks to this. Not too fancy graphically, but is easy to work with and no problems as yet

---

### Post by kknd on 2007-07-18
There is RapidSVN too.

---

### Post by sundarb on 2007-09-07
Hi,
I installed kdesvn and tried connecting to a https:// repository. But I get an error saying that the SSL certificate cannot be verified, verify it manually using the fingerprint. How do I resolve this issue?

---

### Post by mrmorris on 2008-02-12
I tried a bunch of SVN clients and the most polished seems to be SVN Workbench. So if you, like I, is coming from a fancy Windows client like tortoise, that should be the first one to check out.

---

### Post by amp_cstu on 2009-02-24
I already tried **[svn workbench]("http://pysvn.tigris.org/")**. I recommend this one.

---

### Post by itmanvn on 2009-08-05
Have anyone tried nautilussvn ?

---

### Post by TheBuzzSaw on 2009-08-05
command line tool

---

### Post by kaligus on 2009-08-18
+1 for rapidsvn

What I really want though is an all in one, feed it an URI and it checks out git/svn/cvs/etc.

I am starting to suspect that may be like crossing the streams in ghostbusters LOL.

I seldom have anything to offer anyone but my own personal repository so checkin is not a major problem

---

### Post by Miles Huang on 2010-01-08
[RabbitVCS ]("https://launchpad.net/%7Erabbitvcs/+archive/ppa") worth a try definitely. I use it in Ubuntu 9.10.
Just add the 3rd party PPA and install it. Look nice and integrated with system file manager nautilus tightly. Just like what tortoiseSVN do.

---

### Post by not_a_phd on 2010-01-08
I use the SVN CLI, RapidSVN, and Subclipse (in order of frequency). I have never successfully gotten the diff tool to work in RapidSVN. 

Will probably try ksvn and pysvn based on recommendations in this thread. Will say that anything out of tigris.org (e.g. tortoise and Subclipse) is top notch. I wish they would develop something that integrates with nautilus.

---

### Post by pgp_protector on 2010-01-08
I'be been using AnkhSVN for my Visual Studio on Windows, for helping me keep track of my software between work & home, and love it.

I'm going to be trying to do some development (just learning Ubuntu) for Linux soon, and got MonoDevelop for now (Unless I find another development studio), and am just starting to figure it out.

But what I'm wondering is their any form of SVN plugin for Mono like AnkhSVN for Visual Studio ?


Example from Studio & can just right click to Update / Commit / Fork / Branch / Revert ect.

---

### Post by maddog39 on 2010-01-09
Honestly, I find that simply using the command line subversion client is the easiest and most efficient way for me to manage my repositories. I find the clients kind of clunky and cumbersome most of the time when a simple short command gets the job done without any hassle.

---

### Post by webtechquery on 2010-07-06
Hi.

Finding out the best GUI SVN tool for Ubuntu and good alternatives to Tortoise SVN for Ubuntu or Linux, I found RapidSVN as a good one before. But after that, I think one of the best alternative to Tortoise SVN is Rapid VCS (previous known as Nautilus SVN).

You can have a try on both of them, by going through the following link:
[http://www.webtechquery.com/index.php/2010/05/free-svn-tools-ubuntu-free-svn-software-ubuntu/](http://www.webtechquery.com/index.php/2010/05/free-svn-tools-ubuntu-free-svn-software-ubuntu/)

Thanks

---

### Post by itmanvn on 2011-01-19
Try SmartSVN and you'll love it!

---

### Post by itmanvn on 2011-01-19
Try SmartSVN and you'll love it!

---

