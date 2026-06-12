---
title: "HOWTO: Opera 9beta2 Dapper"
date: 2006-05-16
forum: Outdated Tutorials &amp; Tips
---

### Post by SqRt7744 on 2006-05-16
This is quick but it works well!  The result is much nicer than the horrible "static-qt" dapper package they also have available, with the un-aliased fonts.  Much prettier.

Open a terminal and type:

```

wget http://www.artfiles.org/ubuntu.com/archive/pool/main/x/xorg/xlibs_6.8.2-77_all.deb
wget http://snapshot.opera.com/unix/Weekly-344/intel-linux/opera_9.0-20060616.6-shared-qt_en_i386.deb

```

Then browse to the directory where the files were saved (your home directory presumably) and double click on the xlibs package, which should open it with gdebi. Install it, then install the opera_9 file the same way.

For those of you who prefer the command line, install the packages with "sudo dpkg -i name-of-file" in the same order.

as Jeldert points out in the next post: for those of you most interested in the bleeding edge, browse to [http://my.opera.com/desktopteam/blog/](http://my.opera.com/desktopteam/blog/) and click on the Unix link at the top.  Be sure to download the shared etch package, and use it instead of the second wget line in my instructions above.  The version retreived by wget in my instructions is the latest weekly build as of 20 June 2006.

Happy browsing!

---

### Post by Jeldert on 2006-05-16
For the most up-to-date version of Opera you can visit [http://my.opera.com/desktopteam/blog/](http://my.opera.com/desktopteam/blog/) and download the latest UNIX build.

There you can find the shared-qt for Debian Etch, and also a Ubuntu Dapper package (for witch you don't need the first package mentioned in the first post).

---

### Post by JamesB on 2006-05-16
Thanx for the info, works like a dream. I prefer opera to firefox anyday. Personally I think firefox is over-rated. I used to use it in windows when it was version 0.4 or so and it was so quick. Now it's as slow as IE.

---

### Post by mundano on 2006-05-21
It's really mutch better that static build.. Great howto.... 

:D :D :D

---

### Post by gunksta on 2006-05-21
And, as an added bonus to amd64 users we can use the shared 32 bit binary just fine if you have the ia32 KDE libraries installed, and all of it's dependencies. This is nifty because it makes for an easy way to set up and install Flash on a 64 bit machine.

I'm going to write a How-To for 64 bit Kubuntu Users and publish it here soon. Much of it will be applicable to Ubuntu users too though.

--andy

---

### Post by deeek on 2006-05-21
qRt7744 you rock!!!  Thank you for making my eyes stop bleeding looking at those awful menu fonts.  :-)

---

### Post by rplantz on 2006-05-21
[QUOTE=gunksta]And, as an added bonus to amd64 users we can use the shared 32 bit binary just fine if you have the ia32 KDE libraries installed, and all of it's dependencies. This is nifty because it makes for an easy way to set up and install Flash on a 64 bit machine.

I'm going to write a How-To for 64 bit Kubuntu Users and publish it here soon. Much of it will be applicable to Ubuntu users too though.

--andy[/QUOTE]

Do you happen to know if it will work with the ia32 gtk libraries?

I'm looking forward to your HowTo.

---

### Post by Confuse on 2006-05-22
How do you guys get Opera to look like a gtk app? I've seen it around but can't find the appropriate widget. Thanks.

---

### Post by | MM | on 2006-05-22
Hey would someone do a howto for the mplayer-plugin that opera now supports.  That would be great, i tried compiling it a while back but i couldnt get it to work too great.

---

### Post by iTrendsNET on 2006-05-22
[QUOTE=rplantz]Do you happen to know if it will work with the ia32 gtk libraries?

I'm looking forward to your HowTo.[/QUOTE]

Yes it does, I have been using Opera Beta 9 for months in Ubuntu Dapper AMD64.  Download the 32-bit DEB file from the Opera website and install with dpkg using the "force architecture" option.  Before I install Opera, I install the 32-bit Realplayer downloaded from Real.com and Sun 32-bit java from the Sun installer.  Opera will pick up the Realplayer plugin during the install.  You may have to manually tell Opera where to look for the Java files.

Then, grab the Flash installer files from Adobe.com.  Read the "readme" file and drop the 2 referenced files into the Opera plugins folder.  Finally, tell OpenOffice where to find the Sun 1.5 32-bit JRE files.  

The above makes for a very sweet 64-bit Dapper install.  No chroot and I am very pleased with the setup.  No reason to look back to 32-bit or to another 64-bit distro.  At least not for me ;) .

---

### Post by desperado666 on 2006-05-22
Here in german Ubuntu wiki you can find how to use the mplayer plugin to work with opera

[http://wiki.ubuntuusers.de/Opera](http://wiki.ubuntuusers.de/Opera)

---

### Post by rplantz on 2006-05-22
[QUOTE=iTrendsNET]Yes it does, I have been using Opera Beta 9 for months in Ubuntu Dapper AMD64.  Download the 32-bit DEB file from the Opera website and install with dpkg using the "force architecture" option.  Before I install Opera, I install the 32-bit Realplayer downloaded from Real.com and Sun 32-bit java from the Sun installer.  Opera will pick up the Realplayer plugin during the install.  You may have to manually tell Opera where to look for the Java files.

Then, grab the Flash installer files from Adobe.com.  Read the "readme" file and drop the 2 referenced files into the Opera plugins folder.  Finally, tell OpenOffice where to find the Sun 1.5 32-bit JRE files. [/QUOTE]

Are you using the shared library version or static?

Following what I did on Breezy, I installed the static library version of Opera Beta 9. It works just fine. But I find Firefox and Epiphany to be faster. I think that might be due to my (static) Opera not using shared libraries. Poster gunksta said that the 32-bit shared libraries can be used, but specified KDE. I'm just wondering if anybody has done this with the gtk libraries. I'll give it a try later today.

---

### Post by iTrendsNET on 2006-05-22
[QUOTE=rplantz]Are you using the shared library version or static?

Following what I did on Breezy, I installed the static library version of Opera Beta 9. It works just fine. But I find Firefox and Epiphany to be faster. I think that might be due to my (static) Opera not using shared libraries. Poster gunksta said that the 32-bit shared libraries can be used, but specified KDE. I'm just wondering if anybody has done this with the gtk libraries. I'll give it a try later today.[/QUOTE]

Hi, sorry I did not fully understand your original question.  I used the static DEB file for the latest beta and xlibs deb for breezy on my most recent 64-bit install I did last week.  So no, I cannot help regarding your question on the gtk libs.  Now gunksta's comments are a bit more clear and I will have to give his method a shot one of these days.

I am surprised that you are finding Opera slow.  Are you sure you have java and java script enabled and functioning correctly??

---

### Post by rplantz on 2006-05-22
[QUOTE=iTrendsNET]
I am surprised that you are finding Opera slow.  Are you sure you have java and java script enabled and functioning correctly??[/QUOTE]

I don't really find Opera to be slow. I did some very crude timing on loading a somewhat complex web page. Both Firefox and Epiphany were faster than Opera. I just tried the same thing, and the difference was much less this time.

I just tested my java plugin, and it's working. I haven't seen any problems with javascript, so I assume it's also working okay.

I like Opera and use it for most things. Since I'm running 64-bit Firefox and Epiphany, I need Opera for Flashplayer.

---

### Post by gunksta on 2006-05-22
Having the ia32-libs-gtk package is completely irrelevant either way because Opera uses QT. There are only 3 ways to run (successfully) any version of Opera that I know of on a 64 bit Ubuntu system.

1 - chroot jail. (long groan) :-# 
2 - install the ia32-libs-kde and use the "shared" library compiled version. as described by the OP. You can use the debs with the force-architecture option, or just download the .tar.gz and use the really simple installation script.
3 - don't install the ia32-libs-kde and use the static compiled version of Opera. This will still require the ia32-libs package, but everything else is just gravy, you don't really need it. Again, you can use the deb or the tar.gz file. 

I have actually been using the tar.gz method, because I'm not super familiar with dpkg. I will hang my head and admit that I am just another rpm refugee.....

I guess you could use the static version AND have the kde compatible libraries installed, but that seems kind of redundant.

If you primarily use Ubuntu / Xubuntu I would just grab the static and go. It's easier and will be just as efficient on your machine. But, if you have Kubuntu or KDE installed, grab the shared version. No sense running multiple versions of QT at the same time. That would be soooo Windowsesque.  :rolleyes:

---

### Post by rplantz on 2006-05-23
[QUOTE=gunksta]
If you primarily use Ubuntu / Xubuntu I would just grab the static and go. It's easier and will be just as efficient on your machine.[/QUOTE]

Thanks for your explanations. I already had the static version installed. Last night I followed [http://ubuntuforums.org/showthread.php?p=817169&highlight=realplayer+amd64+howto#post817169](http://ubuntuforums.org/showthread.php?p=817169&highlight=realplayer+amd64+howto#post817169) to install 32-bit RealPlayer. (I used the "better way" in post #2.) And I installed Sun's 32-bit java.

It all seems to work just fine. :) And it's quite fast. If it ain't broke...

---

### Post by popkid on 2006-05-23
This Install worked good for me, had to satisfy one further dependency with synaptic, but loads up great....

Thankyou so much, posting this in Opera 9.0Beta2

I Love the page thumbnails you get as you move the mouse across the tabs!

Also... I can listen to streaming media for the first time (for me) in Opera...

The real plugin throws some warning message up every time you open a stream

"You are using a browser that does not support scriptable plugins. Many embedded player sites may not work correctly."

But then proceeds to work fine!

Thanks Again,

pK

---

### Post by abhitux on 2006-05-29
I am facing a queer problem with Opera.

I re installed Opera using the following steps as outlined:
[https://wiki.ubuntu.com/OperaBrowser](https://wiki.ubuntu.com/OperaBrowser)

The first thing was to set up a repository.

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) unstable non-free

The downloading the Opera 8.54 which went off without a hitch. Now after that installed the xlibs package and the snap shot releases.

Installing this has given a siginificant improvement over the previous version but my mail window has disappeared!
I cannot access the mail/ newsreader at all!What seems to be the problem? Under tools> Mail and Chat accounts is greyed out meaning thereby that it's inaccessible.

---

### Post by mejy on 2006-05-29
What packages do I need to enjoy opera with qt?  I have libqt3-mt installed but I just get those horrible motif menus...

---

### Post by migraineboy on 2006-06-02
Is it still working now that final dapper is out?

---

### Post by SqRt7744 on 2006-06-02
[QUOTE=migraineboy]Is it still working now that final dapper is out?[/QUOTE]

as far as I can tell it is.  It still needs xlibs though.

---

### Post by remusus on 2006-06-02
The way I did it was to extract the opera deb:

```
dpkg-deb --extract *opera deb here* operadeb
dpkg-deb --control *opera deb here* operadeb/DEBIAN
```

Edit operadeb/DEBIAN/control, and remove xlibs from the dependency list... then rebuild the deb.
```
dpkg-deb --build operadeb newopera.deb
```

Then install newopera.deb, and it works perfectly.

---

### Post by Dragon, Interrupted on 2006-06-03
I tried this, but I'm not sure if I understood.  I removed only "|  xlibs" from operadeb/DEBIAN/control but still got dependency errors, including the following:

dpkg: dependency problems prevent configuration of opera:
 opera depends on libqt3c102-mt (>= 3:3.2.1); however:
  Package libqt3c102-mt is not installed.


I then tried removing this as a dependency, and it installed fine, but will not start; I get the error

ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
/usr/lib/opera/9.0-20060602.5/opera: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory

So I am left to assume that I do in fact need  libqt3c102-mt to run Opera.  As for the java errors, I tried "locate libjvm.so" etc, but the output produced nothing.  Something wrong with the plugin path perhaps?

Thanks in adavance.

---

### Post by pulp on 2006-06-03
This Version did install without any need for unsatisfiable dependencies or any alterations of files

[http://snapshot.opera.com/unix/Weekly-315/intel-linux/opera_9.0-20060602.6-shared-qt_en_etch_i386.deb](http://snapshot.opera.com/unix/Weekly-315/intel-linux/opera_9.0-20060602.6-shared-qt_en_etch_i386.deb)

---

### Post by ipaidforthisname on 2006-06-04
Hello,

I am a longtime Opera user; in fact, life without Opera is very difficult, which is why I am so frustrated right now.

I installed Opera with the method outlined in this HOWTO. The install went without a hitch, but Opera runs horrendously slow. Going between tabs is a million times worse than Firefox 1.0.7 in Breezy, and some web pages scroll incredibly sluggishly. For example, it is almost painful to try and scroll through my Gmail account. At first, I thought it was a problem with my configuration (Maybe hardware rendering not working properly), but I tried Firefox and I am having no such issues. I know something is wrong when Firefox is much faster than Opera.

Any tips on what could cause this change? I really miss Opera!! :confused:

---

### Post by SqRt7744 on 2006-06-04
[QUOTE=ipaidforthisname]
The install went without a hitch, but Opera runs horrendously slow.[/QUOTE]

It is very fast for me so I can only guess.... did you follow the instructions in the first post, or have you followed some of the suggestions in later posts?  I just did what is written in the first post and am having speed issues.  What graphics card are you using?  Do you have the appropriate driver loaded in xorg.conf?

---

### Post by ipaidforthisname on 2006-06-04
[QUOTE=SqRt7744]It is very fast for me so I can only guess.... did you follow the instructions in the first post, or have you followed some of the suggestions in later posts?  I just did what is written in the first post and am having speed issues.  What graphics card are you using?  Do you have the appropriate driver loaded in xorg.conf?[/QUOTE]


I have an ATI Mobility 9800 in a Dell Inspiron 9100. The driver isn't working. I am having the ATI Mesa "issue," but I absolutely cannot fix it. It worked fine under Breezy Badger. I have tried every version of the fglrx driver I can get my hands on and I have tried every step and checked every file, but I just cannot get it fixed. I've even tried re-installing from scratch. The most infuriating part is that I *SWEAR* it worked when I first installed dapper; I have this memory of running glxgears and getting 3000+ fps. 

I've tried numerous Xorg.conf configurations, as well. From basic stock (with fglrx driver) to my convoluted dual head setup. It all yeilds the same thing.
I am starting to think that might be the culprit, because the same thing happens in firefox if I view galleries with large images in them. 

I did follow the installation instructions properly, I believe.

I really like Dapper Drake, but I wish I could get the fglrx driver working properly. It was so painless in Breezy Badger.

---

### Post by LordMau on 2006-06-05
Can I install and use opera9 beta together with 8.54? or should 8.54 be removed prior to installing v9? or will v9 automatically overwrite and preserve 8.54 settings etc?

Thanks!

---

### Post by SqRt7744 on 2006-06-05
[QUOTE=LordMau]Can I install and use opera9 beta together with 8.54? or should 8.54 be removed prior to installing v9? or will v9 automatically overwrite and preserve 8.54 settings etc?

Thanks![/QUOTE]

I'm pretty sure it will keep your settings, though if it doesn't for some reason - I wash my hands of all accountability.  That said, it worked for me.

---

### Post by SqRt7744 on 2006-06-05
[QUOTE=ipaidforthisname]I have an ATI Mobility 9800 in a Dell Inspiron 9100. The driver isn't working. I am having the ATI Mesa "issue," but I absolutely cannot fix it. [/QUOTE]

I'm sure that's your problem.  

Have a look at this:

[http://www.krazypenguin.net/Ubuntu_Dapper_Drake_6.06_Guide#How_to_install_Graphics_Driver_.28ATI.29](http://www.krazypenguin.net/Ubuntu_Dapper_Drake_6.06_Guide#How_to_install_Graphics_Driver_.28ATI.29)

also, ATI just released (maybe 2 weeks ago) a new driver if above link doesn't help you.

---

### Post by abhitux on 2006-06-05
[QUOTE=LordMau]Can I install and use opera9 beta together with 8.54? or should 8.54 be removed prior to installing v9? or will v9 automatically overwrite and preserve 8.54 settings etc?

Thanks![/QUOTE]
 You can automatically upgrade from 8.54 to version 9 (beta 2). It would leave everything intact. Still, to be on the safe side, make sure that you have your bookmarks, preferences backed up. Go to Help>About Opera and it would list all the folders where they are. You can browse to them and make a back up accordingly.Opera 9  would modify your mail accounts. You cannot roll back to 8.54 if you wish to. Unless you delete the Opera files (in your folders) to roll back the installation. This is not recommended, as per the Opera forums. 

Otherwise, there is a lot to be recommended for Opera 9 ( I prefer to use the latest version off the labs).

Make sure that you download and install the deb file made for Dapper. You have the option of static and shared versions; I prefer to download the shared. Static renders the fonts horribly. One more thing. If you install static by mistake, donot install shared version over static. I faced a lot of issues on account of that (out of my ignorance).

---

### Post by DAaaMan64 on 2006-06-06
I to am having problems I was hoping to get help with, everytime load opera I get: 

```

daaaman64@siddhartha:~$ opera
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
opera: Could not initialize Opera Mail: Store Init failed
opera: Could not initialize Opera Mail: Engine Init() failed


```

This wouldn't bother me except it disables mail and chat accounts.  What is going on?

---

### Post by oskvaz on 2006-06-07
Thanks, it works great. Very simple

Cheers

---

### Post by papaver on 2006-06-08
I just get a blank screen where the flash plugin should be playing..  anyone run into this before?

---

### Post by SqRt7744 on 2006-06-08
[QUOTE=papaver]I just get a blank screen where the flash plugin should be playing..  anyone run into this before?[/QUOTE]

You have to install the plugins, on the opera site they describe how to install flash, java, etc.

---

### Post by Fedcer on 2006-06-09
[QUOTE=DAaaMan64]I to am having problems I was hoping to get help with, everytime load opera I get: 

```

daaaman64@siddhartha:~$ opera
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
opera: Could not initialize Opera Mail: Store Init failed
opera: Could not initialize Opera Mail: Engine Init() failed


```

This wouldn't bother me except it disables mail and chat accounts.  What is going on?[/QUOTE]

The error:
```

ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.

```
means that opera can't find java.
If you don't have java installed, install it.
If you have and for some reason opera is not finding it, go to Preferences - Advanced - Content, click on "Java Options" and there insert the path to your java installation.

---

### Post by wizzer on 2006-06-10
[QUOTE=SqRt7744]This is quick but it works well!  The result is much nicer than the horrible "static-qt" dapper package they also have available, with the un-aliased fonts.  Much prettier.

Open a terminal and type:

```

wget http://www.artfiles.org/ubuntu.com/archive/pool/main/x/xorg/xlibs_6.8.2-77_all.deb
wget http://snapshot.opera.com/unix/Weekly-315/intel-linux/opera_9.0-20060602.6-shared-qt_en_etch_i386.deb

```

Then browse to the directory where the files were saved (your home directory presumably) and double click on the xlibs package, which should open it with gdebi. Install it, then install the opera_9 file the same way.

For those of you who prefer the command line, install the packages with "sudo dpkg -i name-of-file" in the same order.

as Jeldert points out in the next post: for those of you most interested in the bleeding edge, browse to [http://my.opera.com/desktopteam/blog/](http://my.opera.com/desktopteam/blog/) and click on the Unix link at the top.  Be sure to download the shared etch package, and use it instead of the second wget line in my instructions above.  The version retreived by wget in my instructions is the latest weekly build as of 6 June 2006.

Happy browsing![/QUOTE]
Thank you sooooooo much!   Worked like a charm :-)

---

### Post by ting on 2006-06-10
I tried installing the dapper static build, and it was extremly slow and had frequent crashes. I even started using swiftfox.

But this method worked wonders. Opera is fast and stable again:mrgreen:

---

### Post by abhitux on 2006-06-10
Static builds serve no purpose imo. I have always used the shared ones.

---

### Post by shuttleworthwannabe on 2006-06-10
[QUOTE=desperado666]Here in german Ubuntu wiki you can find how to use the mplayer plugin to work with opera

[http://wiki.ubuntuusers.de/Opera](http://wiki.ubuntuusers.de/Opera)[/QUOTE]

Hey, this wiki is what is needed for Opera Linux Ubuntu users. Can someone please help me decode this into English. German on this page appears Greek to me.

Thanks a million. I want to get video working in Opera, and it seems they have nailed it here.

---

### Post by desperado666 on 2006-06-10
[QUOTE=shuttleworthwannabe]Hey, this wiki is what is needed for Opera Linux Ubuntu users. Can someone please help me decode this into English. German on this page appears Greek to me.

Thanks a million. I want to get video working in Opera, and it seems they have nailed it here.[/QUOTE]


Based on this here in english language

[http://my.opera.com/community/forums/findpost.pl?id=1512034](http://my.opera.com/community/forums/findpost.pl?id=1512034)

---

### Post by shuttleworthwannabe on 2006-06-10
I may sound very stupid here, but I hope you will forgive my ignorance. I have been there and tried those instructions. But there are so many of them, and other that refer to other Linux OS's (gentoo, for eg). It did not work for me. too many errors.

This German site puts it all together in one place, and is Dapper. I tried to follow the GErman where I thought I understood some words, but alas, my Opera is not giving mplayer plugins to work.

I will post my about:plugins next.

Thanks.

---

### Post by missmoondog on 2006-06-10
[QUOTE=LordMau]Can I install and use opera9 beta together with 8.54? or should 8.54 be removed prior to installing v9? or will v9 automatically overwrite and preserve 8.54 settings etc?

Thanks![/QUOTE]

i just tried it and it says i have a previous version already installed (opera 8.54). no option but to close/cancel that. so i guess you need to uninstall previous opera?

edit:
no reply since yesterday, and as impatient as i am, i went ahead and removed opera 8.54. installed the beta version as per first post in this thread. got errors installing both files. everything seems to be working properly in version 9 anyway. first error said the same as i stated in first part of this post. second error said installation failed. go figure!!

---

### Post by robenroute on 2006-06-12
[QUOTE=shuttleworthwannabe]I may sound very stupid here, but I hope you will forgive my ignorance. I have been there and tried those instructions. But there are so many of them, and other that refer to other Linux OS's (gentoo, for eg). It did not work for me. too many errors.

This German site puts it all together in one place, and is Dapper. I tried to follow the GErman where I thought I understood some words, but alas, my Opera is not giving mplayer plugins to work.

I will post my about:plugins next.

Thanks.[/QUOTE]

Have you tried translation sites like Babelfish and the likes? I just gave it a whirl and the output isn't altogether Greek.... ;)

---

### Post by LordMau on 2006-06-13
Hi wasn't able to check posts after my own inquiry, as I had pushed through with installing opera9beta2 over dapper opera 8.54. On my case no problems were apparent afterwards. Settings, feeds, password, etc were all intact.

After a few weeks of use I noticed something though. It appears that on every initial start of opera it fails to load all or most plugins I already had installed. Only after a few restarts in the  same session would all plugins finally load. These plugins include the latest mplayer, flash, real via checking at the *opera : plugin* page.

Is there any solution to this thing? Anyone else seeing this?

---

### Post by codemills on 2006-06-13
is this safe to install on AMD64 (running drapper final) using --force architechture ?

---

### Post by kuad on 2006-06-14
If you don't want to try 9beta2, Opera has an 8.54 version for Dapper.

[http://www.opera.com/download/](http://www.opera.com/download/)

Select Ubuntu in the distribution drop down menu and then select Dapper.

---

### Post by Fedcer on 2006-06-15
[QUOTE=codemills]is this safe to install on AMD64 (running drapper final) using --force architechture ?[/QUOTE]

I've run Opera on Dapper 64bit for about 3 weeks and haven't had any problem; it's running very well.

---

### Post by Princey on 2006-06-16
I'm having a minor issue with setting up opera here. I know it's related to it not finding java. Is there a way to install java 32bit and not break guys like open office that depends on java? I'm running 64bit kubuntu.

---

### Post by _mobius_ on 2006-06-17
Strangely, mine is not working.

```
/usr/lib/opera/9.0-20060518.6/opera: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory

```

I've read this:  

[http://www.opera.com/support/search/supsearch.dml?index=112](http://www.opera.com/support/search/supsearch.dml?index=112)

Yet no luck.

Edit:  I got the static working.  I don't know why opera can't load libqt.  Does anyone know where it is looking?

---

### Post by Fedcer on 2006-06-17
[QUOTE=Princey]I'm having a minor issue with setting up opera here. I know it's related to it not finding java. Is there a way to install java 32bit and not break guys like open office that depends on java? I'm running 64bit kubuntu.[/QUOTE]

To install Java 32bit separetely from Java 64bit, go to [http://www.java.com](http://www.java.com), and download the linux **self stracting** file for 32 bit linux. Then, to install, do:
> 
sudo bash
chmod 777 ./jre-1_5_0_06-linux-i586.bin
(the file name will depend on the java version you downloaded)
./jre-1_5_0_06-linux-i586.bin
mkdir /usr/local/java32
cp -r -p ./jre1.5.0_06/* /usr/local/java32


Finally, go to the Preferences of Opera and tell it that the java path is: /usr/local/java32

---

### Post by Somenoob on 2006-06-17
May sound a little noobish, but i am currently using Opera 8.54, if i replace it with this will all the personal Opera data(like bookmarks) still be in place?

---

### Post by Princey on 2006-06-17
[QUOTE=Somenoob]May sound a little noobish, but i am currently using Opera 8.54, if i replace it with this will all the personal Opera data(like bookmarks) still be in place?[/QUOTE]
Opera will detect the previous version. While it overwrites the program files with the new ones, your settings, bookmarks, skins, etc will remain in tact as they're not stored the same place.

---

### Post by Princey on 2006-06-17
[QUOTE=Fedcer]To install Java 32bit separetely from Java 64bit, go to [http://www.java.com](http://www.java.com), and download the linux **self stracting** file for 32 bit linux. Then, to install, do:


Finally, go to the Preferences of Opera and tell it that the java path is: /usr/local/java32[/QUOTE]
Thanks Fedcer. Worked like a charm. Just that they now have the jre-1_5_0_07-linux-i586.bin version out. Thanks all the same. I know have Opera running. Just need to read more through the threads to get flash running or should it have it by default? Will check and see.
------------
Edit: Never mind. I got flash installed and working.

---

### Post by DAaaMan64 on 2006-06-19
where is my java directory probably at? I have tried several,
etc/java
usr/share/java

and variations with nothing.  I installed java with easyubuntu. Thank you. :)

---

### Post by Princey on 2006-06-19
[QUOTE=DAaaMan64]where is my java directory probably at? I have tried several,
etc/java
usr/share/java

and variations with nothing.  I installed java with easyubuntu. Thank you. :)[/QUOTE]

I'm not sure where easy ubuntu installed it to. I installed manually. Try checking /usr/local/java That's where mine is located.

---

### Post by nejode on 2006-06-19
[QUOTE=Jeldert]For the most up-to-date version of Opera you can visit [http://my.opera.com/desktopteam/blog/](http://my.opera.com/desktopteam/blog/) and download the latest UNIX build.

There you can find the shared-qt for Debian Etch, and also a **Ubuntu Dapper ****package** (for witch you don't need the first package mentioned in the first post).[/QUOTE]

jeldert: excuse me but, whitch of the shared-qt deb's listed in that page ( [http://snapshot.opera.com/unix/Weekly-344/intel-linux/](http://snapshot.opera.com/unix/Weekly-344/intel-linux/) ) is the Dapper pack?

Thanks beforehand...

---

### Post by Princey on 2006-06-19
[QUOTE=nejode]jeldert: excuse me but, whitch of the shared-qt deb's listed in that page ( [http://snapshot.opera.com/unix/Weekly-344/intel-linux/](http://snapshot.opera.com/unix/Weekly-344/intel-linux/) ) is the Dapper pack?

Thanks beforehand...[/QUOTE]

This one [http://snapshot.opera.com/unix/Weekly-344/intel-linux/opera_9.0-20060616.6-shared-qt_en_i386.deb]("http://snapshot.opera.com/unix/Weekly-344/intel-linux/opera_9.0-20060616.6-shared-qt_en_i386.deb")

---

### Post by oocce on 2006-06-21
Anybody got any video plugin work? Would like to play wmv with opera :|

Wanna get videos working right, I dont want to change any other browser. Opera is just the best!

---

### Post by JamesB on 2006-06-21
[QUOTE=oocce]Anybody got any video plugin work? Would like to play wmv with opera :|

Wanna get videos working right, I dont want to change any other browser. Opera is just the best![/QUOTE]

Yep, I use Kaffeine 0.81 (I think this is a beta release), the plug-in just seemed to be there and workedO:)

---

### Post by Princey on 2006-06-21
Please note that Opera 9 final it out and available for download.

---

### Post by _mobius_ on 2006-06-22
AMD64 people,

If you should get this error:

```

/usr/lib/opera/9.0-20060616.6/opera: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory

```

you need to install the i386 libqt.

```

wget http://ubuntu.mirrors.tds.net/ubuntu/pool/main/q/qt-x11-free/libqt3-mt_3.3.6-1ubuntu3_i386.deb

```

Then,

```

sudo dpkg -x libqt3-mt_3.3.6-1ubuntu3_i386.deb .

```

Which will extract the guts into the current directory (.).  Now copy the contents of ./usr/lib to /usr/lib32/.

```

sudo cp ./usr/lib/libqt* /usr/lib32/

```

Enjoy opera.

---

### Post by Copter on 2006-06-22
[QUOTE=remusus]The way I did it was to extract the opera deb:

```
dpkg-deb --extract *opera deb here* operadeb
dpkg-deb --control *opera deb here* operadeb/DEBIAN
```

Edit operadeb/DEBIAN/control, and remove xlibs from the dependency list... then rebuild the deb.
```
dpkg-deb --build operadeb newopera.deb
```

Then install newopera.deb, and it works perfectly.[/QUOTE]

this trick works ok here :) thnx

copter :]

---

### Post by stenka on 2006-06-23
I still have a problem with the mplayer plug-ins with Opera, although everything works well with Firefox. 

After searching many hours on the net, I definitely can't find a solution.

At the begining, Opera couldn't find any of the codecs of the mplayer-plugin.
It found well the totem ones, but didn't work with it.

I put the mplayers plug-ins given on [http://wiki.ubuntuusers.de/Opera](http://wiki.ubuntuusers.de/Opera) and they finally got detected.
Unfortunetly, it still doesn't work, giving the following message on the terminal :

[I]
opera: Plug-in 6117 is not responding. It will be closed.
opera: Define environment variable OPERA_KEEP_BLOCKED_PLUGIN to keep blocked plug-ins.[/I]

Can anyone help me ?

Thanks in advance.

---

### Post by desperado666 on 2006-06-23
[QUOTE=stenka]I still have a problem with the mplayer plug-ins with Opera, although everything works well with Firefox. 

After searching many hours on the net, I definitely can't find a solution.

At the begining, Opera couldn't find any of the codecs of the mplayer-plugin.
It found well the totem ones, but didn't work with it.

I put the mplayers plug-ins given on [http://wiki.ubuntuusers.de/Opera](http://wiki.ubuntuusers.de/Opera) and they finally got detected.
Unfortunetly, it still doesn't work, giving the following message on the terminal :

[I]
opera: Plug-in 6117 is not responding. It will be closed.
opera: Define environment variable OPERA_KEEP_BLOCKED_PLUGIN to keep blocked plug-ins.[/I]

Can anyone help me ?

Thanks in advance.[/QUOTE]


I am the author of the german Wiki Opera Article.
Unfortunaly the mplayer plugins used to work several opera build ago but now they dont work with Final Opera9.
Maybe you can get more infos here
[http://my.opera.com/community/forums/topic.dml?id=131761&page=2&skip=50&show=&perscreen=50](http://my.opera.com/community/forums/topic.dml?id=131761&page=2&skip=50&show=&perscreen=50)

Good Luck

---

### Post by stenka on 2006-06-23
Thank you for your answer.

I found out that installing the "mozplugger" package was needed. It indeed works well now !

But there are still few problems :
- the image is not centered
- the control panel is missing and there is a black layer instead
- when the mouse is over the movie, the cursor disappears

does anyone have the same problems ?

---

### Post by desperado666 on 2006-06-23
Mozplugger installed but with no positive effect.
Could you please be so kind and post your detected plugins and plugin folders?

Thx

---

### Post by stenka on 2006-06-23
My detected codecs :

[IMG]http://www.jcbnet.org/blog/plugins.png[/IMG]

My plugin folder :

stenka@ubuntu:~$ ls /usr/lib/opera/plugins/
flashplayer.xpt         mplayerplug-in-qt.so   mplayerplug-in-wmp.xpt
libflashplayer.so       mplayerplug-in-qt.xpt  mplayerplug-in.xpt
libnpp.so               mplayerplug-in-rm.so   nppdf.so
mplayerplug-in-gmp.so   mplayerplug-in-rm.xpt  operaplugincleaner
mplayerplug-in-gmp.xpt  mplayerplug-in-wmp.so  operapluginwrapper

Erase what is unecessary in this folder, especially you may have to delete mplayerplug-in.so and libxpcom.so.

---

### Post by airjunman on 2006-07-04
i Have just started using Linux and Ubuntu, so i'm finding my feet here ... The real problem is mail client ...

I started using Opera-the browser and the built-in mail client that it has ... I really like Opera as compred to Firefox ... maybe I'm lame , maybe its just the looks :) .. anyways I started using Opera mail client that comes with the browser and it worked fine till maybe yesterday or so...

Now when I check mail, I just get nutin ... and I trust one of my hotmail id'd to get enuff jnk mail to get one at least once in an hour or so... so I checked it online and there is a lot of new junk mail, but Opera has stopped looking at it  ... Has anyone faced the same problem? I realise it could be something about "views" , but I've tried pretty much everything ....Any feedback would be cool

---

### Post by vem0m on 2006-07-12
rather i want to use opera or not it has been giving me issues on linux with freezing not to the point of restarting computer but to the point i have to wait for it to start working so anyways nice guide :)

---

### Post by grugnog on 2006-07-23
> **_mobius_ said:**
> AMD64 people,

If you should get this error:

```

/usr/lib/opera/9.0-20060616.6/opera: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory

```


This worked great - thanks!

---

### Post by mugsy3117 on 2006-08-09
Thank You very much. ALthough I still get two errors about shared libraries, it works!

---

### Post by Princey on 2006-08-22
I had opera running pretty fine on my system but after borking my installation, I figured it best to do a clean install. I didn't find it wise to install an older version of opera first so I dumped right into installing version 9.01 on my amd64 machine running the 64bit kernel. I installed RealPlayer first, then the 32 bit java, then opera. When I run it, I get the following error > ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
/usr/lib/opera/9.01-20060728.6/opera: error while loading shared libraries: libXcursor.so.1: cannot open shared object file: No such file or directory

Java is indeed installed. What then could possibly be the reason I can't get it to even open. It just quits when launched from the GUI, it's using the terminal I get to see the error message. Doesn't open up so I can edit the path to java. Any ideas?](*,)

```
whereis libXcursor.so.1
``` yields > libXcursor.so: /usr/lib/libXcursor.so.1


---

### Post by Princey on 2006-08-22
Never mind, I got it working. Had to copy the libXcursor.so.1 to the /usr/lib32 directory.

---

### Post by aladrin on 2009-06-19
> **_mobius_ said:**
> AMD64 people,

If you should get this error:

```

/usr/lib/opera/9.0-20060616.6/opera: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory

```

you need to install the i386 libqt.

```

wget http://ubuntu.mirrors.tds.net/ubuntu/pool/main/q/qt-x11-free/libqt3-mt_3.3.6-1ubuntu3_i386.deb

```

Then,

```

sudo dpkg -x libqt3-mt_3.3.6-1ubuntu3_i386.deb .

```

Which will extract the guts into the current directory (.).  Now copy the contents of ./usr/lib to /usr/lib32/.

```

sudo cp ./usr/lib/libqt* /usr/lib32/

```

Enjoy opera.

I just used this to fix Opera 10.  Thanks! :D

---

### Post by raniubusr on 2010-01-26
> **_mobius_ said:**
> AMD64 people,

You suggest:

```

wget http://ubuntu.mirrors.tds.net/ubuntu/pool/main/q/qt-x11-free/libqt3-mt_3.3.6-1ubuntu3_i386.deb

```

```

sudo dpkg -x libqt3-mt_3.3.6-1ubuntu3_i386.deb .

```

But it don't worked for me because of dependency issues, so:

I've used:

```

sudo apt-get install libaudio2

```

libaudio2 is a dependency for libqt3-mt (not resolved by apt-get)

then:

```

sudo apt-get install libqt3-mt

```

---

### Post by linuxhippy on 2010-02-01
> **aladrin said:**
> I just used this to fix Opera 10.  Thanks! :D

Didn't work on my AMD64.  Here's what I did:

opera


ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
/usr/lib/opera/opera: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory

---

