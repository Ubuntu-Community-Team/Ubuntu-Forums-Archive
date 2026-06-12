---
title: "HOW TO: The Ultimate XBOX 360 Multimedia Sharing Guide"
date: 2008-07-03
forum: Outdated Tutorials &amp; Tips
---

### Post by Nullack on 2008-07-03
**NOTE: Since the Fuppes UPNP project has gotten its act together I consider that project a superior solution to ushare. I have some basic instructions for compiling SVN fuppes at the end of this thread as currently there is no fuppes package available in the Ubuntu repos. Possibly when my 360 comes back from repair I will consider updating the guide unless someone does it before me.**

So your using Ubuntu and you want to share multimedia from your machine to  your 360. This is indeed possible! Some of you may ask, there is a number of existing guides about this, so whats different about this one? Well, this guide uses free software and it uses free software that is not encumbered with bugs.

At the heart of the matter is that we need whats called a upnp media server to serve the media requests. Microsoft in typical fashion did not adhere to upnp standards when producing the 360's sharing. So that means right off the bat, upnp media servers will not work. Thankfully though, some upnp media servers have been modified to run in a special xbox 360 mode. The bad news is that these select servers are either not free or not robust.

The community has reached a point where the single robust upnp server that is free, and importantly is not deprecated, does not have the special xbox 360 mode. Servers like 360 media serve and Fruppes are not actively being developed. The Fruppes community is talking about merging with MediaTomb but getting 360 mode into MediaTomb is going to take time. Ushare is still being developed but it contains a number of ugly bugs that makes the experience frustrating. There is a payware upnp media server but in our hearts, we know that using non free software really isnt right.

Thanks to forum member [NeToU]("http://ubuntuforums.org/member.php?u=576007") he has taken the Ushare source code and patched it to resolve these ugly bugs. So we will be using his patched Ushare version.

Were going to need to download his source code, configure it, compile it and install it. This is not as hard as it sounds and provided you can follow these instructions carefully you will do fine.

**NOTE: YOU MUST REMOVE AND PURGE ANY OLD USHARE INSTALLS YOU MAY HAVE FROM THE REPOS BEFORE STARTING**

**1. Download The Source**

Goto [http://netou.co.uk/]("http://netou.co.uk/") and download the source code.

**2. Extract The Source**

I keep my source in a directory tree under home / src though you may use a different approach. Open up a terminal by selecting the Ubuntu icon, Accessories and then Terminal. Now carefully copy and paste the following, one line at a time, hit enter in the terminal and do the next line.

[INDENT]```
cd ~
mkdir src
```[/INDENT]

Now move your archive to the src directory depending on where you downloaded the source too. For example, if it is in your home directory use:

[INDENT]```
mv ~/ushare-11a-netou.tar.bz2 ~/src/
```[/INDENT]

Lets extract the source now:

[INDENT]```
cd ~/src
tar -xjf ushare-11a-netou.tar.bz2

```[/INDENT]

**3. Compile the program**

First lets get the dependencies out of the way. If your not sure if you already have these there is no harm in doing it as existing installs will not be installed again. So lets get the tools to be able to build software:

[INDENT]```
sudo apt-get install build-essential
```[/INDENT]

Now lets deal with getting the software Ushare depends on:

[INDENT]```
cd ushare-1.1a-NeToU
sudo apt-get build-dep ushare
```[/INDENT]

Once that is done, we can compile Ushare now:

[INDENT]```

./configure --prefix=/ --bindir=/usr/bin --mandir=/usr/share/man
make
sudo make install
sudo make clean
```[/INDENT]

**4. Configure Ushare:**

Ushare like most Linux apps has a conf file. It is critical that you enable the special xbox 360 upnp mode and that you correctly put in the path of the multimedia that you want to share. To edit you conf file, use the following command:

[INDENT]```
gksudo gedit /etc/ushare.conf
```[/INDENT]

Or use nano in the CLI:

[INDENT]```
sudo nano -w /etc/ushare.conf
```[/INDENT]

Edit the file to your liking, with the important settings explained below:

[INDENT]```

USHARE_NAME=          Put the name you want your share to be called e.g. MyMedia
USHARE_PORT=          Define the port number you want to use e.g. 49200
USHARE_DIR=           Configure the share locations e.g. /mnt/hda1,/mnt/hdb1/videos/share/
USHARE_ENABLE_WEB=    Use yes to enable the web interface
USHARE_ENABLE_TELNET= I turn this off with no, preferring to use the web interface
USHARE_ENABLE_XBOX=   This must be yes for 360 sharing to work

```[/INDENT]

Note that Ushare does not handle spaces in the share directories.

**5. Controlling the Ushare daemon**

To start Ushare:

[INDENT]```
sudo /etc/init.d/ushare start
```[/INDENT]


And to stop Ushare:

[INDENT]```
sudo /etc/init.d/ushare stop
```[/INDENT]

**6. Getting Ushare to automatically start on user login:**

Some of the existing guides that use not so robust Upnp servers, also recommend unnecessarily complex ways to get Ushare to autostart. For example by hacking up sudo to run Ushare as a session item for the user. This approach is not only messy, but it also creates the problem where if that user logs out and then later logs in again without rebooting you now have multiple Ushare sessions going.

Let's get Ushare to auto start using Ubuntu's default runlevel settings:

[INDENT]```
sudo update-rc.d ushare defaults
```[/INDENT]

**7. Managing Ushare via the web interface**

You can manage Ushare via the web interface at:

[INDENT]```
http://ip_address:port/web/ushare.html
```[/INDENT]

For example on my machine, its [http://192.168.10.2:49200/web/ushare.html](http://192.168.10.2:49200/web/ushare.html)

**8. Wait, I have the firewall on!**

If your using Ubuntu's UFW, you can easily add a rule to cope with this. Lets say your 360 uses a static IP address of 192.168.10.3 and your machine is 192.168.10.2. Use the following command to provide a small hole in your firewall for this:

[INDENT]```
sudo ufw allow proto tcp from 192.168.10.3 to 192.168.10.2 port 49200
```[/INDENT]

You can easily check what UFW is doing with:

[INDENT]```
sudo ufw status
```[/INDENT]

Your all done, have fun :popcorn:



**FAQ #1 Why Cant I Transcode?**

You can easily! However the best way is to do this outside of a upnp server. Why? The elegant way to do it otherwise is coding a media centre extender. However Microsoft's 360 media centre does not support MPEG4-ASP (divx, xvid) among other things - yes it is behind the "dumber" sharing interface without the media centre. This complicates coding a media centre add on.

There is robust and verstile Linux apps you can use to easily transcode media. I consider the best to be mencoder which can quickly convert many different media formats into mpeg2. You could even batch script it to convert directories of your media overnight.

**FAQ #2 I Want to Uninstall**

[INDENT]```
cd ~/src/ushare-1.1a-NeToU/
sudo make uninstall
sudo update-rc.d -f ushare remove

```[/INDENT]

---

### Post by LordYama on 2008-07-12
Nice work!

I've created two pages on the Ubuntu wiki for Xbox 360 compatibility, and have incorporated your howto.

[https://help.ubuntu.com/community/Xbox_360](https://help.ubuntu.com/community/Xbox_360)
[https://help.ubuntu.com/community/Xbox360Media](https://help.ubuntu.com/community/Xbox360Media)

---

### Post by Nullack on 2008-08-12
Thanks LordYama. I have updated the guide to use the Ushare deamon.

Users who do not wish to compile their own Ushare and who use the same computing platform as Lord Yama are able to use an easier method. Look for Lord Yama's easy method on the Ubuntu 360 wiki:

[https://help.ubuntu.com/community/Xbox360Media]("https://help.ubuntu.com/community/Xbox360Media")

---

### Post by krestean on 2008-08-12
my xbox 360 still can't see my computer..


btw I think you meant  "make clean" not "male clean" as it is written in your post..



**edit**: and i get an error when trying to uninstall:

make: *** No rule to make target `uninstall'.  Stop.

---

### Post by krestean on 2008-08-12
ok, my bad.. 

have firestarter installed.. 

just added the ip of the xbox to "allow connections form hosts" and voilla, it works!


edit:  thanks a lot for the guide :D

---

### Post by Nullack on 2008-08-12
I have fixed the typo. Im glad you sorted out your networking issue and found the guide useful.

An update: We continue to need to use the patched version that our member here on the forums kindly provides. The official development tree of Ushare is moving forward but at this stage the official dev code is failing to compile on my test system. It also requires libdlna0 at an unreleased version level as a dependency. These things adds up to the current development version not being ready for use but into the future we will be able to compile Ushare without patches. This should lead to its eventual inclusion into the Ubuntu repos once the Ushare developers release an updated formal release.

---

### Post by Drizzel on 2008-08-12
Hi, thx for the descriptive guide! Couple of questions though.. I've been searching for years now on how to actually stream media to my 360. I dont have a router. How exactly should I connect my 360 to my pc to get this to work? I have a regular ethernet cable and also a crossover cable. Can I do this with one of those cables or do I need a router? I live alone, so I really dont have a need for networking in my apt therefore I never needed a router. I would like to just connect my 360 directly to my pc using one of the cables I have and stream stuff. Possible?

---

### Post by krestean on 2008-08-12
My xbox 360 is directly connected to my laptop.

xbox live is working perfectly, but ushare stopped working after I rebooted...



i use the cable that came with my xbox.. think it's a normal ethernet cable..

---

### Post by Nullack on 2008-08-12
It certainly is possible to run router like functions on Ubuntu - DNS, DHCP, Firewall, NAT etcetc.

If you guys conduct a search you'll see a number of howtos on this forum and externally on internet connection sharing with Ubuntu.

I prefer to run routing on dedicated hardware as then I dont need to have my workstation on to serve the 360. It free's me to fiddle around with the workstation, reboot when I want etcetc without interfering with the connectivity of other machines.

Krestean you can see if Ubuntu is running by typing "sudo ps -e | grep ushare". This is the first step in diagnosing the issue.

---

### Post by Drizzel on 2008-08-12
Nullack:

> **Drizzel said:**
> Hi, thx for the descriptive guide! How exactly should I connect my 360 to my pc to get this to work? I have a regular ethernet cable and also a crossover cable. Can I do this with one of those cables or do I need a router?

---

### Post by Nullack on 2008-08-13
As I said, do a search :)

[http://ubuntuforums.org/showthread.php?t=91370&highlight=internet+connection+sharing](http://ubuntuforums.org/showthread.php?t=91370&highlight=internet+connection+sharing)

[http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html](http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html)

[http://www.fs-security.com/docs/connection-sharing.php](http://www.fs-security.com/docs/connection-sharing.php)

[http://ubuntuforums.org/showthread.php?t=335465&highlight=internet+connection+sharing](http://ubuntuforums.org/showthread.php?t=335465&highlight=internet+connection+sharing)

---

### Post by Nullack on 2008-08-13
> **krestean said:**
> My xbox 360 is directly connected to my laptop.

xbox live is working perfectly, but ushare stopped working after I rebooted.

Make sure you used ```
sudo update-rc.d ushare defaults
``` to get Ushare to autostart. This command adds Ushare to the Ubuntu default runlevels.

As stated, to see if Ushare is running, use ```
sudo ps -e | grep ushare
```

---

### Post by krestean on 2008-08-13
don't want to autostart it :P

Now I got fuppes fully working, even with transcoding and metadata :guitar:

---

### Post by Nullack on 2008-08-13
As for Fuppes, the chief developer went AWOL and the code has become deprecated. Here you can find a discussion on other people about creating a fork to keep Fruppes happening in some form:

[http://fuppes.ulrich-voelkel.de/forum/viewtopic.php?f=3&t=184&st=0&sk=t&sd=a](http://fuppes.ulrich-voelkel.de/forum/viewtopic.php?f=3&t=184&st=0&sk=t&sd=a)

The fork is called Fuppex and the code is here:

[http://fuppex.svn.sourceforge.net/viewvc/fuppex/](http://fuppex.svn.sourceforge.net/viewvc/fuppex/)

In my experience MediaTomb is the best free Upnp server but the devs have an anti-MS attitude to supporting the 360's special mode. They may eventually get around to supporting it but it'll take time.

I'm going to have a look at Fuppex but I suspect that will also need some time to sort out the new project and overcome all the issues with the fork from Fuppes.

---

### Post by esc1 on 2008-08-15
Does streaming video work?

---

### Post by Nullack on 2008-08-16
There many different types of streaming video, demuxers and decoders. What stream in particular are you wanting?

---

### Post by fatty.mat on 2008-08-17
I am trying to stream movies in .avi format and it takes between 5 and 10 minutes to buffer.  Is that normal?

---

### Post by Nullack on 2008-08-18
No its not normal. Some points:

1. AVI is just a container format and there is many possible different streams encoded in different ways that could be inside it
2. Are you sure your using the version of Ushare from this guide? Can you please post the Ushare deamon logs from the deamon log file on your system.
3. Does this happen on all your media or just some of them? Can you post a sample of this media on an online host so I can look at it?

Streaming AVIs that contain media thats supported by the 360 works more or less instantly for me at all times.

---

### Post by ace007 on 2008-08-18
I have the same issue that someone posted but has been ignored thus far

```

sudo make uninstall

```
results in an error.
```

make: *** No rule to make target `uninstall'. Stop.

```

So I decided to try using "checkinstall" to compile and form a deb so dpkg could track the installation.  However I get an error as well...

```

dpkg-deb - error: (upstream) version (`NeToU') doesn't contain any digits
dpkg-deb: 1 errors in control file

```
So, I just 
```

mv ushare-1.1a-NeToU ushare-1.1a

```

Checkinstall now works!  For those of you who done know about checkinstall you just replace the "sudo make install" command with "sudo checkinstall" and it forms a .deb installs it.  And I can now uninstall NeToU's ushare with...
```

sudo dpkg -r ushare

```
or 
```

sudo apt-get remove ushare

```

However, I am not sure what the experts would say is preferable for removal.

NOTE:

You may have to install checkinstall if you dont already have it with:
```

sudo apt-get install checkinstall

```

---

### Post by Nullack on 2008-08-19
Ok, I'll look into the uninstall issue. Its possible to do it manually if needed. Personally I dont like checkinstall.

---

### Post by fatty.mat on 2008-08-19
Nullack  	
It seems to take a long time to download images also.  It takes about 20 seconds to open a 2mb picture.  I installed twonky last night and get the same results.  Music starts playing instantly, but pictures and movies take a long time.  Music works, but drops out after a couple of minutes and then comes back on.  I am starting to think it is something with my wireless router/modem.  I guess I will make a cable to stretch across the house and see if that makes a difference.

---

### Post by Nullack on 2008-08-20
For me to give you support, you need to respond to the questions I ask of you.

How much bandwidth does your network connection have? What type is it?

---

### Post by Prestwick on 2008-08-20
As if you didn't have enough questions to answer, I've got another one!

I was wondering if subtitles were supported when transcoding in uShare, I watch allot of Anime so need the subs to survive really, heh :D

Thanks in advance.

---

### Post by Nullack on 2008-08-20
Its fine, happy to answer :)

Short if it is that MS do not support most of the anime style sub formats. However you can word around this by transcoding the media before streaming it via ushare using hardcoded subs onto each of the transcoded frames in the footage.

---

### Post by Tamacracker on 2008-08-21
Does anyone know what would cause uShare to not be able to support MP3s? I don't want to use Media Tomb, but at least Media Tomb is capable of reading MP3 so that my PS3 can play them. On my PS3 I see all my folders and all the tracks are labeled as, "unsupported data'.

---

### Post by Nullack on 2008-08-21
The PS3 runs in a different mode to the 360. Ushare requires answering yes to the dlna compliant mode in the conf file.

---

### Post by junbug178 on 2008-08-31
I am getting an error in this step: 
Lets extract the source now:

    Code:

    cd ~/src
    tar -xyjf ushare-11a-netou.tar.bz2

The error is:
tar: invalid option -- y

---

### Post by Nullack on 2008-09-01
> **junbug178 said:**
> I am getting an error in this step: 
Lets extract the source now:

    Code:

    cd ~/src
    tar -xyjf ushare-11a-netou.tar.bz2

The error is:
tar: invalid option -- y

Sorry that was a typo - corrected now, should be

```
tar -xjf ushare-11a-netou.tar.bz2
```

---

### Post by simonjsimon on 2008-09-01
Hello, 
I had uShare working on my server running kubuntu but it was different then your guide. To run ushare I would have to type:

ushare -n <name> -c <directory> -x

-x for the xbox. Now I had to get a new hdd as mine filled up, so then I tried to run ushare with both directories like this:

ushare -n <name> -c /media/sdb2/server -c /home/server/Videos -x

but when I run uShare with more than one directory it says that it is looking in both directories and finds the files, but on my xbox only the first directory in the list shows up.

So then I found your guide and thought I would give it a try.  So I unistalled uShare and then followed your guide with no problems, but when I run uShare the way you run it in the guide nothing happens.  USare doesn't start running. I check the system monitor and it isn't running.

So I guess my question is why?  If any other info is required please let me know so I can get this to work.  Thanks for your help.
Simon

---

### Post by Nullack on 2008-09-01
The way my guide sets things up is for Ushare to run as a daemon using standard Ubuntu conventions.

When your trying to figure out whats wrong with Ushare like in your case, for diagnosing it its best to run "sudo ushare" from the terminal so you can quickly and easily look at output.

If you get a valid response from that command, use CTRL+C to stop it. Then use the manual command in my guide to start it as a daemon "sudo /etc/init.d/ushare start". Then let me know please.

---

### Post by simonjsimon on 2008-09-01
Thanks for the quick reply Nullack.  So when I ran "sudo ushare" nothing came up.  So then I went back and compiled the program again and went from there. Now it works perfectly.  Thanks again.

---

### Post by TwiceOver on 2008-09-06
Followed your instructions on Ubuntu Server 8.04.  Unfortunately it thinks upnp-dev is the incorrect version:

Output of the ./configure

```

... (snip)
Checking for libixml ...
Checking for libthreadutil ...
Checking for libupnp >= 1.4.2 ...
Error, libupnp < 1.4.2 !
See file "config.log" produced by configure for more details.

```

```

Sudo apt-get install libupnp-dev build-essential=
...
Reading state information... Done
libupnp-dev is already the newest version.
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.


```

```

sudo aptitude show libupnp-dev
Package: libupnp-dev
State: installed
Automatically installed: yes
Version: 1.4.3-2
Priority: extra
Section: universe/libdevel
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 2904k
Depends: libupnp2
Description: Intel Universal Plug And Play SDK for Linux (development files)
 The Linux SDK for UPnP Devices (libupnp) provides developers with an API and open source code for
 building control points, devices, and bridges that are compliant with Version 1.0 of the Universal
 Plug and Play Device Architecture Specification - see http://www.upnp.org/ for specifications. 
 
 The libupnp-dev package contains the header files, documentation and debug versions of libraries
 needed for development of programs using uPnP.


```

EDIT:  Output from config.log file:

```

END /tmp/ushare--4880-.c
gcc -I.. -W -Wall -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_REENTRANT -D_GNU_SOURCE -O3 -DHAVE_LOC$
gcc -o /tmp/ushare--4880- /tmp/ushare--4880-.o -lixml -lthreadutil -lpthread -lupnp
pkg-config libupnp --atleast-version=1.4.2
./configure: 663: pkg-config: not found
Error, libupnp < 1.4.2 !


```

So I have current+ version for this setup.  Any idea where to go from here?

---

### Post by Nullack on 2008-09-06
Hmm, very strange you meet the dependencies but configure thinks you dont. Perhaps theres something wrong with you upnp dev install. I recommend forcing a reinstall of it using --reinstall.

Also, please confirm your using netaous ushare revision 1.1a

---

### Post by TwiceOver on 2008-09-07
> **Nullack said:**
> Hmm, very strange you meet the dependencies but configure thinks you dont. Perhaps theres something wrong with you upnp dev install. I recommend forcing a reinstall of it using --reinstall.

Also, please confirm your using netaous ushare revision 1.1a

I did a reinstall of libupnp-dev and still get the same errors.  I also double checked my download, and it is the 1.1a version.

Hrm.

---

### Post by Nullack on 2008-09-12
TwiceOver Ive been puzzling over your situation:

* I cant replicate what you report
* You appear to have dependecies right, yet they say they arent, and when reinstalled its not fixed

As there seems to be something wrong with your install why not try a fakeroot type build of ushare in a clean pristine environment. I cant offer support for that but I can suggest it as a try.

---

### Post by Atanvarno on 2008-09-13
I get the same strange dependancy error as TwiceOver. I previously had the vanilla ushare installed and working fine, so the libupnp-dev package is clearly fine?

---

### Post by Nullack on 2008-09-13
What build are you on? Hardy desktop?

Can I see console output please of the issue.

---

### Post by TwiceOver on 2008-09-13
> **Nullack said:**
> What build are you on? Hardy desktop?

Can I see console output please of the issue.

I'm using Ubuntu Server Edition 8.04 Hardy, no GUI installed at all.

---

### Post by SatanSoldier on 2008-09-14
I'm getting this error:
bash: ./configure: No such file or directory
Im in the process of switching to ubuntu, so i'm new.

---

### Post by Nullack on 2008-09-14
Atanvarno - are you also on the server build? What build are you on?

SatanSoldier - welcome to Ubuntu. Please re-try the process taking each step slowly. Let me know how you go.

---

### Post by SatanSoldier on 2008-09-15
i went back over everything, i hadn't gotten very far, still getting the same message

---

### Post by Nullack on 2008-09-16
TwiceOver and Atanvarno - I've fixed it thanks to some help from the server folk on IRC :) Please note the new method in the how to. What was happening is that the server build does not have all the dependencies of Ushare that the Desktop build has. The error message you reported TwiceOver was actually wrong and it sent us on the wrong direction to fixing it. The build system isnt smart enough to know exactly which dependency isnt being met and it was reporting the wrong dependency as being the problem. We know have a much cleaner way of doing this via the build-dep command. So please re-try the new guide.

SatanSoldier (!!??) - I need you to copy every line of the terminal output while your trying to do this from the guide so I can see what the problem is. Please use [http://pastebin.com/](http://pastebin.com/) for the test.

---

### Post by redelephant on 2008-09-16
I can get my 360 to play all of my files, but I'm having an issue where new files added to my shared directories won't show up unless I restart uShare. Is this normal or is there something I'm missing?

---

### Post by Nullack on 2008-09-16
> **redelephant said:**
> I can get my 360 to play all of my files, but I'm having an issue where new files added to my shared directories won't show up unless I restart uShare. Is this normal or is there something I'm missing?

Its normal, you can refresh the files by going to your web interface. Your IP maybe different, but to use the example I gave in the how to:

[http://192.168.10.2:49200/web/ushare.html](http://192.168.10.2:49200/web/ushare.html)

And then clicking on refresh shares

---

### Post by TwiceOver on 2008-09-17
> **Nullack said:**
> TwiceOver and Atanvarno - I've fixed it thanks to some help from the server folk on IRC :) Please note the new method in the how to. What was happening is that the server build does not have all the dependencies of Ushare that the Desktop build has. The error message you reported TwiceOver was actually wrong and it sent us on the wrong direction to fixing it. The build system isnt smart enough to know exactly which dependency isnt being met and it was reporting the wrong dependency as being the problem. We know have a much cleaner way of doing this via the build-dep command. So please re-try the new guide.

Will do!  Thanks for the leg work on this.  I'll try it out later today.

---

### Post by TwiceOver on 2008-09-17
> **Nullack said:**
> Its normal, you can refresh the files by going to your web interface. Your IP maybe different, but to use the example I gave in the how to:

[http://192.168.10.2:49200/web/ushare.html](http://192.168.10.2:49200/web/ushare.html)

And then clicking on refresh shares

Just a thought...  Is there a way to automate this like once a day or something?  Cronjob?

I personally wouldn't be adding things all that often and couldn't imagine adding something and needing access to it right away.  But it would be nice to "set it and forget it".

---

### Post by Nullack on 2008-09-17
Yep you could cron it for daily or more regularly at a time you know for sure you wont be in the middle of a session.

Simply

sudo /etc/init.d/ushare reload

Personally I just refresh the share anytime I dump more files into my share vault.

---

### Post by element_G on 2008-09-17
First, thank you for this how-to it worked without a hitch. I do have one question though:
On the Xbox, why can't I browse the directory structure or artists, albums and so on? (similar to a connected mp3 player) I can only tell the Xbox to 'play all' songs.

---

### Post by Nullack on 2008-09-17
Its not implemented in that revision of ushare. Our choices are:

1. Wait for the ushare project to do so
2. Use another UPNP server.

The Fuppes developer went AWOL and his supporters forked the project to Fuppex. Fuppex isnt ready for mainstream use IMHO. MediaTomb are angry at MS for implementing a non-standard UPNP, to the point of free offers of xbox 360 hardware was been rejected as not a priority for them. There is some other UPNP servers but that are depricated.

Fuppex is probably the most promising but we'll need to wait for the dust to settle after the fork.

---

### Post by TwiceOver on 2008-09-17
> **element_G said:**
> First, thank you for this how-to it worked without a hitch. I do have one question though:
On the Xbox, why can't I browse the directory structure or artists, albums and so on? (similar to a connected mp3 player) I can only tell the Xbox to 'play all' songs.

Ack... Can't do the basics?  I'll probably have to skip out on this until I can use the basic functions.

It really sucks that MS didn't use a standardized uPNP server, but then again, did you expect them to?

---

### Post by Nullack on 2008-09-17
To clarify, directories do work. Sharing multiple directories does work. I have 6000+ files in my vault, which without directories would be impossible to manage.

---

### Post by jdorenbush on 2008-09-19
I followed all the steps very carefully, however still no luck. The install went just find, but actually getting my Xbox 360 and PC to work together failed.

My Xbox 360 and PC are both hooked up via Ethernet, and they both have successful Internet connections. I have forwarded my uShare port. The files I am trying to share are on an external hdd - I don't know if this matters.

On a site note, when I enter the code below nothing shows up after I enter it:
```
sudo ps -e | grep ushare
```

Auto start of the application and initial starting of the application seem fine:
```

sudo update-rc.d ushare defaults
System startup links for /etc/init.d/ushare already exist.

```

```

sudo /etc/init.d/ushare start
* Starting uShare UPnP A/V & DLNA Media Server: ushare  [ OK ]

```

I don't know if it's necessary, but here is my ushare.conf:
```

# /etc/ushare.conf
# Edit this file with 'dpkg-reconfigure ushare'
# Configuration file for uShare

# uShare UPnP Friendly Name (default is 'uShare').
USHARE_NAME=uShare

# Interface to listen to (default is eth0).
# Ex : USHARE_IFACE=eth1
USHARE_IFACE=eth2

# Port to listen to (default is random from IANA Dynamic Ports range)
# Ex : USHARE_PORT=49200
USHARE_PORT=49200

# Port to listen for Telnet connections
# Ex : USHARE_TELNET_PORT=1337
USHARE_TELNET_PORT=1337

# Directories to be shared (space or CSV list).
# Ex: USHARE_DIR=/dir1,/dir2
USHARE_DIR=/media/My+Book

# Use to override what happens when iconv fails to parse a file name.
# The default uShare behaviour is to not add the entry in the media list
# This option overrides that behaviour and adds the non-iconv'ed string into
# the media list, with the assumption that the renderer will be able to
# handle it. Devices like Noxon 2 have no problem with strings being passed
# as is. (Umlauts for all!)
#
# Options are TRUE/YES/1 for override and anything else for default behaviour
USHARE_OVERRIDE_ICONV_ERR=

# Enable Web interface (yes/no)
ENABLE_WEB=yes

# Enable Telnet control interface (yes/no)
ENABLE_TELNET=no

# Use XboX 360 compatibility mode (yes/no)
ENABLE_XBOX=yes

# Use DLNA profile (yes/no)
# This is needed for PlayStation3 to work (among other devices)
ENABLE_DLNA=no
```

In Administration > Network Settings, I have eth0, eth1, and eth2 - could this be the problem?

---

### Post by Nullack on 2008-09-19
Ok, lets run through this. When you do a sudo ps -e | grep ushare you should in response get something like this:

nullack@PPP:~/src/ushare-1.1a-NeToU$ ps -e | grep ushare
 7970 ?        00:00:00 ushare

If not, it means ushare is not running.

If you run sudo /etc/init.d/ushare start, does ushare then show up if you repeat the process list command?

If not, please run sudo ushare in a terminal and paste what the response is back. If something is wrong ushare will print it to the terminal.

---

### Post by Nullack on 2008-09-20
Just FYI, Ive done up a debdiff with this on launchpad. I aim to get this into Intrepid and backported to earlier releases. This will mean an easy install through the repos and only some simple configuration in the ushare.conf to get it working.

---

### Post by jdorenbush on 2008-09-20
> **Nullack said:**
> Ok, lets run through this. When you do a sudo ps -e | grep ushare you should in response get something like this:

nullack@PPP:~/src/ushare-1.1a-NeToU$ ps -e | grep ushare
 7970 ?        00:00:00 ushare

If not, it means ushare is not running.

If you run sudo /etc/init.d/ushare start, does ushare then show up if you repeat the process list command?

If not, please run sudo ushare in a terminal and paste what the response is back. If something is wrong ushare will print it to the terminal.

```
Interface eth2 is down.
Recheck uShare's configuration and try again !
ioctl: Cannot assign requested address

```

I have tried eth0 and eth1 - same problem. :(

---

### Post by Nullack on 2008-09-20
> **jdorenbush said:**
> ```
Interface eth2 is down.
Recheck uShare's configuration and try again !
ioctl: Cannot assign requested address

```

I have tried eth0 and eth1 - same problem. :(

Its not a problem with ushare. It says eth2 is down. Are you sure thats the network interface you use? Try:

```
[INDENT]sudo ifconfig[/INDENT]
```

in a terminal to see the nics.

---

### Post by jdorenbush on 2008-09-20
I changed it to eth0 - According to 'sudo ifconfig' it seems that is the correct one.

```
sudo ps -e | grep ushare
8253 ?        00:00:00 ushare
```

```
sudo ushare
Interface eth0 is down.
Recheck uShare's configuration and try again !
uShare (version 1.1a), a lightweight UPnP A/V and DLNA Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See http://ushare.geexbox.org/ for updates.
bind: Address already in use

```

---

### Post by TwiceOver on 2008-09-21
I can now confirm working on Ubuntu Hardy Server.  Unfortunately without play by artist/album it seems fairly useless.  Picture viewing is slow and the songs list cuts off at 3000.

Hopefully there will be an update to uShare to fix these issues.

---

### Post by Nullack on 2008-09-21
```
sudo ushare
Interface eth0 is down.
Recheck uShare's configuration and try again !
uShare (version 1.1a), a lightweight UPnP A/V and DLNA Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See http://ushare.geexbox.org/ for updates.
bind: Address already in use

```[/QUOTE]

Reboot, make sure youve specified eth0 in the conf and that eth0 is alive. Then confirm youve started ushare ok. It should all work then.

@TwiceOver - media streaming works. The issue about meta support will either come with Fuppex once the fork settles down or with a new revision of ushare.

---

### Post by RavUn on 2008-09-22
I set it up and had it working for a minute.  I began watching an .avi video (and there wasn't any sound...) then I closed that video and started a different one to see if it worked.  It went to a blank screen and I backed out and now I can't get the xbox to see my computer again... I restarted both the xbox and my computer and restarted ushare but it still doesn't see it at all.  I don't have a firewall and I have the port forwarding on my router.  I don't see why it'd work then suddenly stop without me changing anything.

EDIT: Don't know why, but it randomly showed up.  As far as the no sound issue, it appears to be an issue with my receiver and not the files :/

Thanks for the howto!

---

### Post by Nullack on 2008-09-22
A good way to diagnose whats happening is sto stop the ushare service and manually start it in a terminal with:

```
[INDENT]sudo ushare[/INDENT]
```

Observe what the terminal output says

---

### Post by jdorenbush on 2008-09-22
> **Nullack said:**
> ```
sudo ushare
Interface eth0 is down.
Recheck uShare's configuration and try again !
uShare (version 1.1a), a lightweight UPnP A/V and DLNA Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See http://ushare.geexbox.org/ for updates.
bind: Address already in use

```

Reboot, make sure youve specified eth0 in the conf and that eth0 is alive. Then confirm youve started ushare ok. It should all work then.
Now I am getting a different message when I type, 'sudo ushare'. It still says eth0 is down. When I type 'ifconfig' it is the only one out of eth0, eth1, and eth2, that is shows an IP address, inet addr:192.168.0.4. So I figure its the correct one to use.

```
Interface eth0 is down.
Recheck uShare's configuration and try again !
uShare (version 1.1a), a lightweight UPnP A/V and DLNA Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See http://ushare.geexbox.org/ for updates.
Listening on telnet port 1337
Initializing UPnP subsystem ...
UPnP MediaServer listening on 192.168.0.4:49200
Sending UPnP advertisement for device ...
Listening for control point connections ...
Building Metadata List ...
Looking for files in content directory : /media/My+Book
scandir: No such file or directory
Found 2 files and subdirectories.
```

---

### Post by RavUn on 2008-09-22
It still keeps randomly losing connection with my computers.  I'll be watching a video and it randomly pops up and says the connection with the computer was lost.  One of the computers is wireless and one is connected through ethernet and it happens on both.  I stopped the service on both and ran 
```

sudo ushare -x

```

and it shows it's running and nothing changes even when the connection's lost.

---

### Post by Nullack on 2008-09-22
> **jdorenbush said:**
> ```
Interface eth0 is down.
Recheck uShare's configuration and try again !
uShare (version 1.1a), a lightweight UPnP A/V and DLNA Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See http://ushare.geexbox.org/ for updates.
Listening on telnet port 1337
Initializing UPnP subsystem ...
UPnP MediaServer listening on 192.168.0.4:49200
Sending UPnP advertisement for device ...
Listening for control point connections ...
Building Metadata List ...
Looking for files in content directory : /media/My+Book
scandir: No such file or directory
Found 2 files and subdirectories.
```

Support is only provided for the ushare revision in this guide. You are not using my guide, your using a different ushare version.

---

### Post by Nullack on 2008-09-22
> **RavUn said:**
> It still keeps randomly losing connection with my computers.  I'll be watching a video and it randomly pops up and says the connection with the computer was lost.  One of the computers is wireless and one is connected through ethernet and it happens on both.  I stopped the service on both and ran 
```

sudo ushare -x

```

and it shows it's running and nothing changes even when the connection's lost.

Many wireless scenarios struggle to keep up with the bit rate requirements of streaming footage. I suggest you try with temporarily running atleast a 100Mbit ethernet wired setup, and I'm confident you wont see the problem occurring anymore.

---

### Post by RavUn on 2008-09-22
I think you're right.  I tried twonky and had the same issue.  It's gotta be a connection issue... I've read a few posts from others having the same issue but there's never a solution.  Oh well, I'm able to switch back and forth between twonky and ushare when it doesn't work right and can usually get a couple of videos out of it.

Thanks again.

---

### Post by Nullack on 2008-09-22
> **RavUn said:**
> I think you're right.  I tried twonky and had the same issue.  It's gotta be a connection issue... I've read a few posts from others having the same issue but there's never a solution.  Oh well, I'm able to switch back and forth between twonky and ushare when it doesn't work right and can usually get a couple of videos out of it.

Thanks again.

No worries mate :) FWIW, I have a top of the range wireless setup at my home office and it does not reliably stream media, especially high defintion media. I use wired 100Mbit ethernet for all media streaming across my house and it never drops out. I reserve wifi for more mobile connectivity around the house.

---

### Post by pandorazboxx on 2008-09-23
I get the following error when I get to this part in the tutorial

```
~/src/ushare-1.1a-NeToU$ ./configure --prefix=/ --bindir=/usr/bin --mandir=/usr/share/man
```


```
Checking for compiler available...
gcc is unable to create an executable file.
If gcc is a cross-compiler, use the --cross-compile option.
C compiler test failed.
See file "config.log" produced by configure for more details.
mark@pandorazboxx:~/src/ushare-1.1a-NeToU$ 

```

I tried adding the same cross compile option but I get the same error. Why can't it create an executable file? I'm still running gutsy gibon.

---

### Post by melator on 2008-09-25
> **jdorenbush said:**
> Now I am getting a different message when I type, 'sudo ushare'. It still says eth0 is down. When I type 'ifconfig' it is the only one out of eth0, eth1, and eth2, that is shows an IP address, inet addr:192.168.0.4. So I figure its the correct one to use.

```
Interface eth0 is down.
Recheck uShare's configuration and try again !
uShare (version 1.1a), a lightweight UPnP A/V and DLNA Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See http://ushare.geexbox.org/ for updates.
Listening on telnet port 1337
Initializing UPnP subsystem ...
UPnP MediaServer listening on 192.168.0.4:49200
Sending UPnP advertisement for device ...
Listening for control point connections ...
Building Metadata List ...
Looking for files in content directory : /media/My+Book
scandir: No such file or directory
Found 2 files and subdirectories.
```

uShare doesn't support spaces so "/media/My+Book" will fail but "/media/MyBook" will work.  Hope that helps...also noticed when adding multiple shares it will only list the first on on the XBox

---

### Post by S0VERE1GN on 2008-09-25
So, when i'm configuring the file, what do i need to put in to make the file work properly: if i want to connect it to my external hard drive 

so my directory would be: /media/mybook/ 

so do i type in just that?

---

### Post by S0VERE1GN on 2008-09-25
/etc/init.d/ushare start
 * Starting uShare UPnP A/V & DLNA Media Server: ushare                         /etc/ushare.conf: 5: Charles: not found


how do i fix that? hehe ^_^

---

### Post by Zach.Town on 2008-09-25
Works great for me. Thanks :D

---

### Post by jdorenbush on 2008-09-25
> **Zach.Town said:**
> Works great for me. Thanks :D


Lucky. :(

I have to keep unplugging ext. hdd and bringing it over the Xbox 360 and hook it up via USB straight to the Xbox 360.

---

### Post by melator on 2008-09-25
> **S0VERE1GN said:**
> So, when i'm configuring the file, what do i need to put in to make the file work properly: if i want to connect it to my external hard drive 

so my directory would be: /media/mybook/ 

so do i type in just that?

Well, it probably auto mounts it to "/media/My Book" because that partition is labeled "My Book".  You'd have to rename the partition's label to something without white spaces but not sure if that will break anything...I know some of those My Books run firmware on them and might require it to keep the same label.  Although I think those are the 1TB+ ones

---

### Post by Nullack on 2008-09-25
> **melator said:**
> uShare doesn't support spaces so "/media/My+Book" will fail but "/media/MyBook" will work.  Hope that helps...also noticed when adding multiple shares it will only list the first on on the XBox

Ushare does not support spaces in the path.

Multiple shares do in fact work, like this:

USHARE_DIR=/mnt/vault/Film,/mnt/vault/Music

If its not working for you your either not using the correct ushare version or you have made a mistake in the setup.

---

### Post by Nullack on 2008-09-25
> **melator said:**
> Well, it probably auto mounts it to "/media/My Book" because that partition is labeled "My Book".  You'd have to rename the partition's label to something without white spaces but not sure if that will break anything...I know some of those My Books run firmware on them and might require it to keep the same label.  Although I think those are the 1TB+ ones

Create an fstab entry to force the mounting of it onto a better name. Theres lots of guides around about mounting on linux and fstab for people to look at.

---

### Post by Nullack on 2008-09-25
> **pandorazboxx said:**
> I get the following error when I get to this part in the tutorial

```
~/src/ushare-1.1a-NeToU$ ./configure --prefix=/ --bindir=/usr/bin --mandir=/usr/share/man
```


```
Checking for compiler available...
gcc is unable to create an executable file.
If gcc is a cross-compiler, use the --cross-compile option.
C compiler test failed.
See file "config.log" produced by configure for more details.
mark@pandorazboxx:~/src/ushare-1.1a-NeToU$ 

```

I tried adding the same cross compile option but I get the same error. Why can't it create an executable file? I'm still running gutsy gibon.

Maybe post the contents of that config.log and any other info you can find please.

---

### Post by Nullack on 2008-09-25
> **jdorenbush said:**
> Now I am getting a different message when I type, 'sudo ushare'. It still says eth0 is down. When I type 'ifconfig' it is the only one out of eth0, eth1, and eth2, that is shows an IP address, inet addr:192.168.0.4. So I figure its the correct one to use.

```
Interface eth0 is down.
Recheck uShare's configuration and try again !
uShare (version 1.1a), a lightweight UPnP A/V and DLNA Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See http://ushare.geexbox.org/ for updates.
Listening on telnet port 1337
Initializing UPnP subsystem ...
UPnP MediaServer listening on 192.168.0.4:49200
Sending UPnP advertisement for device ...
Listening for control point connections ...
Building Metadata List ...
Looking for files in content directory : /media/My+Book
scandir: No such file or directory
Found 2 files and subdirectories.
```

You need to sort out the space problem in the path, ushare cant find it.

Also, I note you dont get:

Starting in XboX 360 compliant profile ...

Is your conf setup right? Please post your conf.

If your not using an xbox 360, your outside the scope of this guide.

---

### Post by jdorenbush on 2008-09-26
> **Nullack said:**
> You need to sort out the space problem in the path, ushare cant find it.

Also, I note you dont get:

Starting in XboX 360 compliant profile ...

Is your conf setup right? Please post your conf.

If your not using an xbox 360, your outside the scope of this guide.

I changed the folder name from 'My Book' to 'Personal' - so there is no spaces anymore. Its an Xbox 360. Port 49200 is opened on my Router and I have confirmed this via [www.canyouseeme.org](www.canyouseeme.org)

Conf:
```
# /etc/ushare.conf
# Edit this file with 'dpkg-reconfigure ushare'
# Configuration file for uShare

# uShare UPnP Friendly Name (default is 'uShare').
USHARE_NAME=uShare

# Interface to listen to (default is eth0).
# Ex : USHARE_IFACE=eth1
USHARE_IFACE=eth0

# Port to listen to (default is random from IANA Dynamic Ports range)
# Ex : USHARE_PORT=49200
USHARE_PORT=49200

# Port to listen for Telnet connections
# Ex : USHARE_TELNET_PORT=1337
USHARE_TELNET_PORT=1337

# Directories to be shared (space or CSV list).
# Ex: USHARE_DIR=/dir1,/dir2
USHARE_DIR=/media/Personal

# Use to override what happens when iconv fails to parse a file name.
# The default uShare behaviour is to not add the entry in the media list
# This option overrides that behaviour and adds the non-iconv'ed string into
# the media list, with the assumption that the renderer will be able to
# handle it. Devices like Noxon 2 have no problem with strings being passed
# as is. (Umlauts for all!)
#
# Options are TRUE/YES/1 for override and anything else for default behaviour
USHARE_OVERRIDE_ICONV_ERR=YES

# Enable Web interface (yes/no)
ENABLE_WEB=yes

# Enable Telnet control interface (yes/no)
ENABLE_TELNET=no

# Use XboX 360 compatibility mode (yes/no)
ENABLE_XBOX=yes

# Use DLNA profile (yes/no)
# This is needed for PlayStation3 to work (among other devices)
ENABLE_DLNA=no
```

Output of 'sudo ushare'
```
Interface eth0 is down.
Recheck uShare's configuration and try again !
uShare (version 1.1a), a lightweight UPnP A/V and DLNA Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See http://ushare.geexbox.org/ for updates.
bind: Address already in use

```

---

### Post by taseedorf on 2008-09-26
Once you get ushare installed, simply go into /etc/ushare.conf (might not have the conf after it)  and edit it to your liking.  It is ALSO important to note that ushare seems to only be able to recognize one directory..so make links to all your media folders and put them in one directory....but once its configured simply type  
ushare -x -D  to run ushare as a daemon in xbox compatibility mode.  simple.

---

### Post by curiousnoob on 2008-09-27
This program rocks!  Everything works as far as I can tell but I was wondering if there was any way to use this program (or any other for that matter) to view streaming content such as youtube or hulu through the Xbox 360?

---

### Post by Drizzzly on 2008-09-30
I have ushare working for the most part; I just can't get .mpg files to show up as videos. It looks like my xbox is putting them under the audio tab. (AVIs work fine.) Any ideas how to get .mpg files working? They don't show up as unplayable videos (the red circle thing). They just don't show up. I haven't been able to find anything. Any help would be *much* appreciated.

---

### Post by dreamnid on 2008-10-03
> **S0VERE1GN said:**
> /etc/init.d/ushare start
 * Starting uShare UPnP A/V & DLNA Media Server: ushare                         /etc/ushare.conf: 5: Charles: not found


how do i fix that? hehe ^_^

Hey S0VERGE1GN,

Note that the share name cannot have any spaces

I tried using quotes without any success.  

Hope that helps

---

### Post by Nullack on 2008-10-04
> **taseedorf said:**
> Once you get ushare installed, simply go into /etc/ushare.conf (might not have the conf after it)  and edit it to your liking.  It is ALSO important to note that ushare seems to only be able to recognize one directory..so make links to all your media folders and put them in one directory....but once its configured simply type  
ushare -x -D  to run ushare as a daemon in xbox compatibility mode.  simple.

This patched version of ushare fixes the old bug of not being able to share multiple dirs. This is one of the key reasons why we use this patch.

---

### Post by Nullack on 2008-10-04
> **curiousnoob said:**
> This program rocks!  Everything works as far as I can tell but I was wondering if there was any way to use this program (or any other for that matter) to view streaming content such as youtube or hulu through the Xbox 360?

You can but youll have to transcode the footage to one of the accepted formats that MS support first.

---

### Post by Nullack on 2008-10-04
> **Drizzzly said:**
> I have ushare working for the most part; I just can't get .mpg files to show up as videos. It looks like my xbox is putting them under the audio tab. (AVIs work fine.) Any ideas how to get .mpg files working? They don't show up as unplayable videos (the red circle thing). They just don't show up. I haven't been able to find anything. Any help would be *much* appreciated.

The mpg container can contain quite a variety of actual formats inside it. You need to figure out which you have to start diagnosing the problem. If you dont know how, host a sample of the content online so I can take a look at it.

---

### Post by Nullack on 2008-10-04
> **jdorenbush said:**
> 
Output of 'sudo ushare'
```
Interface eth0 is down.
Recheck uShare's configuration and try again !
uShare (version 1.1a), a lightweight UPnP A/V and DLNA Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See http://ushare.geexbox.org/ for updates.
bind: Address already in use

```

Some questions please:

1. Your sure the correct network interface is eth0?
2. Your sure the port your trying to use is actually free? i.e. Nothing else is using that port?
3. You dont have other ushare sessions running?

PS: Personally I wouldnt leave your ushare port or any other ports open to the internet if you can avoid it :)

---

### Post by jdorenbush on 2008-10-04
> **Nullack said:**
> Some questions please:

1. Your sure the correct network interface is eth0?
2. Your sure the port your trying to use is actually free? i.e. Nothing else is using that port?
3. You dont have other ushare sessions running?

PS: Personally I wouldnt leave your ushare port or any other ports open to the internet if you can avoid it :)

1.
```
eth0      Link encap:Ethernet  HWaddr 00:19:5b:5e:6e:31  
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::219:5bff:fe5e:6e31/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1082 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1153 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:801364 (782.5 KB)  TX bytes:190148 (185.6 KB)
          Interrupt:16 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr 00:17:31:d8:e1:da  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:248 Base address:0xc000 

eth2      Link encap:Ethernet  HWaddr 00:17:31:d9:10:57  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:249 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2251 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2251 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:114584 (111.8 KB)  TX bytes:114584 (111.8 KB)
```

2. Should I close the 49200 port? Will it still work?

3. I can't imagine that I do... how do I check though?

---

### Post by curiousnoob on 2008-10-04
> **Nullack said:**
> You can but youll have to transcode the footage to one of the accepted formats that MS support first.

So I would have to download it first?  Is there any way to do it in real time?

---

### Post by Nullack on 2008-10-05
> **jdorenbush said:**
> 

2. Should I close the 49200 port? Will it still work?

3. I can't imagine that I do... how do I check though?

eth0 seems to be the one which is sending packets and actively doing network stuff.

Generally, only services you must have on the internet side of the network should be open. You need to distinguish between "open" on your internal network and "open" to the wider WAN / Internet. If all your services are inwards on your internal network dont enable anything to the internet.

For me, I run UFW on my machine running ushare, so I put a small hole in that machines firewall to allow UDP on port 49200 to the single other machine I use to stream the media 0 my xbox 360. I dont allow any ports open from the internet.

You can check what ushare processes are running by:

```
ps -e | grep ushare
```

---

### Post by Nullack on 2008-10-05
> **curiousnoob said:**
> So I would have to download it first?  Is there any way to do it in real time?

Some other upnp servers have this facility by typically using ffmpeg in the background. The one free upnp server that does this recently had the chief developer go awol and other devs started a fork of it called fuppex. Once the dust settles and the fuppex project gets in shape I'll probably move the guide to using it if ushare that does not similarly match it with features.

---

### Post by jdorenbush on 2008-10-06
ps -e | grep ushare
```
7149 pts/0    00:00:00 ushare
```

ushare
```
Interface eth0 is down.
Recheck uShare's configuration and try again !
uShare (version 1.1a), a lightweight UPnP A/V and DLNA Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See http://ushare.geexbox.org/ for updates.
Listening on telnet port 1337
Initializing UPnP subsystem ...
UPnP MediaServer listening on 192.168.0.4:49200
Sending UPnP advertisement for device ...
Listening for control point connections ...
Building Metadata List ...
Looking for files in content directory : /media/Personal
Found 11216 files and subdirectories.
```

What do you think the next step is? Am I doomed to failure?

---

### Post by Nullack on 2008-10-07
This is what you should get:
```

nullack@PPP:~$ sudo ushare
uShare (version 1.1a-NeToU), a lightweight UPnP A/V and DLNA Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See http://ushare.geexbox.org/ for updates.
Initializing UPnP subsystem ...
Starting in XboX 360 compliant profile ...
UPnP MediaServer listening on XXX.XXX.XXX.XXX:49200
Sending UPnP advertisement for device ...
Listening for control point connections ...
Building Metadata List ...
Looking for files in content directory : XXXXXXX
Looking for files in content directory : XXXXXXX
(This will be repeated for each area you share)
Found XXXX files and subdirectories.
```

What concerns me is why your getting the eth0 down message.

On the old 1.1a unpatched version that error message appeared but it still worked. It should be gone under the patched version and it seems it is for everyone except you.

Are you sure you dont have some sort of firewall on your internal network? Last time you showed that eth0 was being used - is that still the case? eth0 is the correct interface for your setup?

Also I notice your not running in xbox 360 mode. Previously you showed your ushare conf that had yes to this. Can you please not fiddle around with the setup while Im trying to help you with support :) We will forever be chasing our tails in a circle if your configuration doesnt remain solid.

---

### Post by djdp on 2008-10-07
I have this problem:

sudo apt-get build-dep ushare 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for ushare

Any ideas on how to fix this.
Btw i'm trying this on Ubuntu server 7.10.

---

### Post by jdorenbush on 2008-10-07
> **Nullack said:**
> This is what you should get:
```

nullack@PPP:~$ sudo ushare
uShare (version 1.1a-NeToU), a lightweight UPnP A/V and DLNA Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See http://ushare.geexbox.org/ for updates.
Initializing UPnP subsystem ...
Starting in XboX 360 compliant profile ...
UPnP MediaServer listening on XXX.XXX.XXX.XXX:49200
Sending UPnP advertisement for device ...
Listening for control point connections ...
Building Metadata List ...
Looking for files in content directory : XXXXXXX
Looking for files in content directory : XXXXXXX
(This will be repeated for each area you share)
Found XXXX files and subdirectories.
```

What concerns me is why your getting the eth0 down message.

On the old 1.1a unpatched version that error message appeared but it still worked. It should be gone under the patched version and it seems it is for everyone except you.

Are you sure you dont have some sort of firewall on your internal network? Last time you showed that eth0 was being used - is that still the case? eth0 is the correct interface for your setup?

Also I notice your not running in xbox 360 mode. Previously you showed your ushare conf that had yes to this. Can you please not fiddle around with the setup while Im trying to help you with support :) We will forever be chasing our tails in a circle if your configuration doesnt remain solid.

eth0 should still be being used. I don't know why it wouldn't be. I haven't changed anything. I am not sure if there is a firewall. I am accessing the Internet via a router that is setup on a Windows XP machine, could the problem lie there?

Where do you see that Xbox 360 mode is not active? I checked my last post and also my current conf. - it shows it set to, YES
```
# Use XboX 360 compatibility mode (yes/no)
ENABLE_XBOX=yes
```

---

### Post by Nullack on 2008-10-08
Hi jdorenbush - you can tell that the xbox 360 mode is in effect when you manually start ushare with the "sudo ushare" command. It will provide this detail in the terminal:

```
Starting in XboX 360 compliant profile ...
```

So your windows XP machine is doing routing? You must allow the UDP traffic on the ushare port to be open on your internal network. That isnt opening the port to the internet. It is allowing it inside.

On Ubuntu, by default UFW is not on so unless you have changed it you dont have a firewall on Ubuntu.

About not being in the 360 mode - if you have correctly installed from the guide and the conf is right it will work. If your sure your conf is right, can you confirm that you dont have any other ushare installed? Did you install ushare from the repos as well?

---

### Post by Nullack on 2008-10-08
> **djdp said:**
> I have this problem:

sudo apt-get build-dep ushare 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for ushare

Any ideas on how to fix this.
Btw i'm trying this on Ubuntu server 7.10.

Please use pastebin for all the history of the commands so I can see whats happening fully.

[http://pastebin.com/](http://pastebin.com/)

---

### Post by jdorenbush on 2008-10-08
> **Nullack said:**
> Hi jdorenbush - you can tell that the xbox 360 mode is in effect when you manually start ushare with the "sudo ushare" command. It will provide this detail in the terminal:

```
Starting in XboX 360 compliant profile ...
```

So your windows XP machine is doing routing? You must allow the UDP traffic on the ushare port to be open on your internal network. That isnt opening the port to the internet. It is allowing it inside.

On Ubuntu, by default UFW is not on so unless you have changed it you dont have a firewall on Ubuntu.

About not being in the 360 mode - if you have correctly installed from the guide and the conf is right it will work. If your sure your conf is right, can you confirm that you dont have any other ushare installed? Did you install ushare from the repos as well?

How do I confirm if I have other ushare installs?

And how do I confirm that UFW is not on and that UDP is enabled?

---

### Post by Nullack on 2008-10-08
Mate for ufw, use in a terminal:

[INDENT]```
sudo ufw status
```[/INDENT]

It should come back with ufw not loaded. If it is, put a hole in the firewall as per the instructions in my guide.

For ushare you can use terminal or synaptic. It might be easier for you to use synaptic, search for ushare. Since this guide uses no packaging, when you search for ushare nothing should come up as being installed. Installed packages in synaptic have the checkbox filled in, those that arent installed have it clear.

I am working on a new version of ushare to be in packaged into the repos so in the short term this will be much easier.

---

### Post by jdorenbush on 2008-10-08
> **Nullack said:**
> Mate for ufw, use in a terminal:

[INDENT]```
sudo ufw status
```[/INDENT]

It should come back with ufw not loaded. If it is, put a hole in the firewall as per the instructions in my guide.

This is the message that was displayed after typing that - so thats a good thing.
```
Firewall not loaded
```


> **Nullack said:**
> For ushare you can use terminal or synaptic. It might be easier for you to use synaptic, search for ushare. Since this guide uses no packaging, when you search for ushare nothing should come up as being installed. Installed packages in synaptic have the checkbox filled in, those that arent installed have it clear.

I searched for ushare in Synaptic. Three things came up, libdlna0, libdlna-dev and ushare. The boxes are all green.

---

### Post by Nullack on 2008-10-08
Please select ushare in synaptic, right click it, and select completely remove. Then hit apply. Your install is being messed around by competing ushare versions.

Then once the repos ushare is purged, please repeat the whole guide again, carefully, and report your results thanks.

---

### Post by jdorenbush on 2008-10-09
> **Nullack said:**
> Please select ushare in synaptic, right click it, and select completely remove. Then hit apply. Your install is being messed around by competing ushare versions.

Then once the repos ushare is purged, please repeat the whole guide again, carefully, and report your results thanks.

I went to Synaptic. I selected Completely Remove All for "ushare"

I followed your steps exactly, like I did the first time. Once again, no errors or complications during the install, like the first time.

But guess what?... It worked! Jeez, 10 pages later, and it finally works. I am stoked! Thanks for your help Nullack.

---

### Post by jdorenbush on 2008-10-13
The only thing I can't get to work is the auto-start. Every time I restart Ubuntu I have to use the start command to get ushare working.
```
sudo /etc/init.d/ushare start
```

I've entered the following a few times just to confirm, but it still doesn't work.
```
sudo update-rc.d ushare defaults
```

---

### Post by jdorenbush on 2008-10-22
Anyone? :(

---

### Post by element_G on 2008-10-23
On my laptop running fluxbuntu I had to start NetworkManager by symlinking its init script from /etc/rc2.d

so for ushare I believe the command goes as follows

```
sudo ln -s /etc/init.d/ushare /etc/rc2.d/
```

and then rename the script to something like

```
sudo mv ushare 30ushare
```

and restart your machine

---

### Post by jdorenbush on 2008-10-23
> **element_G said:**
> and then rename the script to something like

```
sudo mv ushare 30ushare
```

This is what happened...

```
sudo mv ushare 30ushare
mv: cannot stat `ushare': No such file or directory
```

---

### Post by pottsie454 on 2008-10-23
Alright guys... not a newbie, but not a veteran.  I installed ushare as per this tutorial.  I currently have my network setup and home between my laptop and my xbox 360 with a crossover cable.  The laptop shares a wireless connection to the xbox 360 for the internet.  I have ushare setup and running, but xbox does not recognize it.  I go to media - music - X - then to computers and it says it does not see any computers.

I use firestarter to share my connection with a hole in the "host allow" policy to accept connections from xbox.

Any suggestions would be helpful.  I have been messing around with ushare fuppes and xbox360 media share for 3 days now without any luck with any of them. 

THANKS!


```

cory@UbuntuC:~$ sudo ps -e | grep ushare
[sudo] password for cory: 
30940 ?        00:00:00 ushare
32349 ?        00:00:00 ushare

```

```

cory@UbuntuC:~$ sudo ufw status
Firewall not loaded
cory@UbuntuC:~$ 


```


```

# /etc/ushare.conf
# Configuration file for uShare

# uShare UPnP Friendly Name (default is 'uShare').
USHARE_NAME=LaptopMedia

# Interface to listen to (default is eth0).
# Ex : USHARE_IFACE=eth1
USHARE_IFACE=

# Port to listen to (default is random from IANA Dynamic Ports range)
# Ex : USHARE_PORT=49200
USHARE_PORT=49200

# Port to listen for Telnet connections
# Ex : USHARE_TELNET_PORT=1337
USHARE_TELNET_PORT=

# Directories to be shared (space or CSV list).
# Ex: USHARE_DIR=/dir1,/dir2
USHARE_DIR=/home/cory/Music

# Use to override what happens when iconv fails to parse a file name.
# The default uShare behaviour is to not add the entry in the media list
# This option overrides that behaviour and adds the non-iconv'ed string into
# the media list, with the assumption that the renderer will be able to
# handle it. Devices like Noxon 2 have no problem with strings being passed
# as is. (Umlauts for all!)
#
# Options are TRUE/YES/1 for override and anything else for default behaviour
USHARE_OVERRIDE_ICONV_ERR=

# Enable Web interface (yes/no)
USHARE_ENABLE_WEB=yes

# Enable Telnet control interface (yes/no)
USHARE_ENABLE_TELNET=no

# Use XboX 360 compatibility mode (yes/no)
USHARE_ENABLE_XBOX=yes

# Use DLNA profile (yes/no)
# This is needed for PlayStation3 to work (among other devices)
USHARE_ENABLE_DLNA=


```

---

### Post by element_G on 2008-10-24
> **jdorenbush said:**
> This is what happened...

```
sudo mv ushare 30ushare
mv: cannot stat `ushare': No such file or directory
```

sorry , that should have read

```
sudo mv /etc/rc2.d/ushare /etc/rc2.d/30ushare
```

---

### Post by RavUn on 2008-10-24
Potsie, you're able to pull up [http://IPADDRESS:49200/web/ushare.html](http://IPADDRESS:49200/web/ushare.html) ?

Sometimes my wireless laptop doesn't show and I'm not sure why, but usually restarting helps (but it'll randomly disappear at some point).  My desktop that's connected to the router through an ethernet cable never seems to go away, though.

---

### Post by jdorenbush on 2008-10-26
> **element_G said:**
> sorry , that should have read

```
sudo mv /etc/rc2.d/ushare /etc/rc2.d/30ushare
```

Still no luck... :(

---

### Post by element_G on 2008-10-28
> **jdorenbush said:**
> Still no luck... :(

Do you mean the commands still give you an error or that the symlink worked but ushare still doesn't start? Anyone else know of a solution here?

---

### Post by jdorenbush on 2008-10-28
> **element_G said:**
> Do you mean the commands still give you an error or that the symlink worked but ushare still doesn't start? Anyone else know of a solution here?

The commands seem to work fine. But every time I reboot Ubuntu I have to type the command again to get ushare started up.

---

### Post by wolrahnaes on 2008-10-28
Just popped in to say it's working beautifully for me after going through the tutorial.

The libupnp version issue was resolved by installing pkg-config, other than that it was flawless on 8.04.1 Server

---

### Post by jdorenbush on 2008-11-01
Does this not work with Ubuntu 8.10?

---

### Post by Marcboy on 2008-11-03
> **TwiceOver said:**
> Just a thought...  Is there a way to automate this like once a day or something?  Cronjob?

I personally wouldn't be adding things all that often and couldn't imagine adding something and needing access to it right away.  But it would be nice to "set it and forget it".

I have an entry in my crontab that wget's the web refresh script and saves it to a file. This is jus like clicking refresh on the web interface and doesnt matter if your in the middle of a session.

---

### Post by Xavura on 2008-11-03
> **jdorenbush said:**
> Does this not work with Ubuntu 8.10?

Works fine for me on 8.10.



Anyway, for some reason PNG images don't work, is there any way I can fix that? Pretty much every image I have is in PNG format.

---

### Post by jdorenbush on 2008-11-03
> **Xavura said:**
> Works fine for me on 8.10.



Anyway, for some reason PNG images don't work, is there any way I can fix that? Pretty much every image I have is in PNG format.

Hmm strange. I haven't changed any settings after upgrading to 8.10. I just tried to start and use uShare, it started fine from Ubuntu, but after trying to access it through my Xbox 360 I was unsuccessful.

UPDATE: I just went into Package Manager and searched for uShare. It didn't even show as being installed. I wonder if upgrading to 8.10 somehow uninstalled it? Anyways, I installed it and everything is working perfectly now.

---

### Post by Tadhg on 2008-11-09
After upgrading to 8.10 and reinstalling ushare from the repositories, not only does my xbox not pick up uShare, uShare seems to catalog my media on every startup, pushing the CPU to 100% for about 10 minutes. After all that, it only reports a fraction of my media as present. Anyone getting the same?

---

### Post by alexeix on 2008-11-09
Thanks for the excellent guide.  I've applied this to Ubuntu 8.10 and it worked first time!

Next problem: my video content is recorded via MythTV and the format is mpeg.  The Xbox can see the files, but not play them back.

What formats can be streamed in this way and how do I play my files back in the most hassle-free way?

Thanks for any advice!

---

### Post by alexeix on 2008-11-10
Any advice on this?  I'm several episodes behind with Heroes and in need of catching up!  :)

Do I need to convert the files from mpeg to something else and if so, what's the recommended software?

If the Xbox CAN play mpeg in this way, what am I doing wrong?  Any suggestions?

Thanks.

---

### Post by Donsander on 2008-11-14
Anyone with a mirror to that source?
[http://netou.co.uk/](http://netou.co.uk/) is down

---

### Post by alexeix on 2008-11-14
Is anyone successfully sharing media with their Xbox via Ubuntu 8.10, and also using WinFF to convert video files?

I can either share or use WinFF, but not both - have to uninstall Ushare to get WinFF to work - and re-install Ushare again afterwards.

It's a royal pain since I have to convert my mpeg files in order to stream them to my Xbox...

Anyone have any idea how to get these two to play nicely?

---

### Post by johnnybirdman on 2008-11-14
> **Nullack said:**
> To clarify, directories do work. Sharing multiple directories does work. I have 6000+ files in my vault, which without directories would be impossible to manage.

Could you explain how you accomplish this?  The NeToU site states "There is still no metadata support within uShare so music will not be sorted by album/artist etc"

The result for some seems to be that all the music is lumped into one folder on the xbox and basically unusable. I would agree unless you can tell us how you do it.

Thanks,
J.

---

### Post by Donsander on 2008-11-14
My compliments to the maker of the tutorial and the source writer, with me not being very experienced got it almost working instantly on my ubuntu 8.10 server

---

### Post by alexeix on 2008-11-14
True; the tutorial is great, however, has anyone tried converting files on the same PC?

Also, I find that I have to manually start the share after booting my PC.  Otherwise I can't see any files on the Xbox.

---

### Post by jdorenbush on 2008-11-14
> **alexeix said:**
> True; the tutorial is great, however, has anyone tried converting files on the same PC?

Also, I find that I have to manually start the share after booting my PC.  Otherwise I can't see any files on the Xbox.

I can't get the auto start to work either. Not a major problem, just an annoyance.

---

### Post by alexeix on 2008-11-14
Yeah, but I'd like to get it set up so I don't have to run the start command every time I want to share.

It'd be great if this was automatic.

I'm running Mythbuntu, so ideally it should be as automated as possible.

Hopefully someone will have an idea how to sort this.

Also, any suggestions for how to use WinFF at the same time would be much appreciated!
:)

---

### Post by zoroko on 2008-11-19
I need some help.. something different is happening.. I can see my computers navigate the directories and play my videos just fine... but after a short time, about 20 minutes or so it all craps out, it says it cant recognize the file and then i cant connect back to anything, and only a restart fixes it. Its exactly as is described in this post on another forum.

[http://www.linuxquestions.org/questions/fedora-35/ushare-dropping-out-in-fedora-8-645102/](http://www.linuxquestions.org/questions/fedora-35/ushare-dropping-out-in-fedora-8-645102/)


Does anyone have any ideas?

---

### Post by ophanim on 2008-11-19
Using 8.10 and following the instructions exactly, I get hung up early when I try to install all the dependencies for ushare.

```
ophanimx@Ship:~/src/ushare-1.1a-NeToU$ sudo apt-get build-dep ushare
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for ushare

```

Trying to build anyway results in:

```
ophanimx@Ship:~/src/ushare-1.1a-NeToU$ ./configure --prefix=/ --bindir=/usr/bin --mandir=/usr/share/man
Checking for compiler available...
Checking for locales ...
Checking for ifaddrs ...
Checking for langinfo ...
Checking for iconv ...
Checking for libixml ...
Error, can't find libixml !
See file "config.log" produced by configure for more details.

```

---

### Post by Jan Ziska on 2008-11-19
thanks for this guide, really helpful!

I am also having trouble accessing my photos and music, but it sees my videos just fine.

One thing though, it takes forever to load them. like, 5 minutes to load a 20 minute .avi. I have just started using the wireless connection from the 360, so I think that's the problem. Can anyone confirm if it's wireless, or bugs with the NXE or what...

---

### Post by defrex on 2008-11-21
is anyone having problems since the "new xbox experience" update? My streaming isn't working anymore...

---

### Post by rko618 on 2008-11-21
> **defrex said:**
> is anyone having problems since the "new xbox experience" update? My streaming isn't working anymore...

When I updated my xbox my streaming stopped working as well. However, **reinstalling** the media update that it throws at you fixed it for me.

---

### Post by defrex on 2008-11-21
> **rko618 said:**
> When I updated my xbox my streaming stopped working as well. However, **reinstalling** the media update that it throws at you fixed it for me.

Awesome. Worked for me too. Who would have guessed redownloading something claiming to be an AAC codec would fix my avi playback issue.

---

### Post by Jan Ziska on 2008-11-21
> **rko618 said:**
> When I updated my xbox my streaming stopped working as well. However, **reinstalling** the media update that it throws at you fixed it for me.

How does one do this exactly?

---

### Post by defrex on 2008-11-21
sign in the live, then attempt to play a video. You should get an error message saying a media update is required. If you click the option to download the update, you will be taken to a menu where the only real option is a media update for AAC. Click on it, then click redownload.

That should do it.

---

### Post by Edward850 on 2008-11-22
I keep getting this error every time I start uShare:
```
 * Starting uShare UPnP A/V & DLNA Media Server: ushare                         /etc/ushare.conf: 21: and: not found
 * No shares avalaible ...
```

Line 21 appears to be my dir listing in ushare.conf, but it seems to be fine:
```
USHARE_DIR=/media/disk/Documents and Settings/Edward/My Documents/My Music,/media/disk/Documents and Settings/Edward/My Documents/My Pictures,/home/edward/Pictures,/home/edward/Videos
```

Edit: Never mind. I Removed the two long DIR's and added them back in via the web server. It seems that a space has to be replaced with a +.

---

### Post by rko618 on 2008-11-23
Does the init.d script that Ubuntu installs work for anyone? When I start uShare via init.d I am unable to connect with my xbox, however, when I start it with ```
ushare -xD
``` in terminal it works fine.

---

### Post by Jan Ziska on 2008-11-24
well, I redownloaded the AAC codec thingy, which solved my massive loading time problem, thankyou!

But now, I keep getting a 53-c00df238 error. I knew how to fix this on vista, but don't know how to do it on ubuntu.

On Vista, I would have to make sure the ad-hoc network that was set up each time I turned on my xbox as 'private' as opposed to 'public' and that seemed to work. My understanding is that vista won't allow media sharing over a public network. 

So could this be the problem again? And if so, how do I fix it on Ubuntu?

---

### Post by calcio1 on 2008-11-25
this might be a dumb question but how do i find my ip address to log into the internet interface?

Edit: never mind found it. web interface wasn't working because the default iface was eth0 not wlan0

Xbox sees my computer but won't connect to it. Maybe cause pc is on wireless? If I connect to router through ethernet will it help?

Only reason I am keeping a windows computer is to stream to Xbox, so I'm trying to test ushare on laptop before converting all my computers to Ubuntu

cheers

---

### Post by Jan Ziska on 2008-11-25
> **calcio1 said:**
> this might be a dumb question but how do i find my ip address to log into the internet interface?

Edit: never mind found it. web interface wasn't working because the default iface was eth0 not wlan0

Xbox sees my computer but won't connect to it. Maybe cause pc is on wireless? If I connect to router through ethernet will it help?

Only reason I am keeping a windows computer is to stream to Xbox, so I'm trying to test ushare on laptop before converting all my computers to Ubuntu

cheers

Is Ushare running? You have to start it manually each login I find.

what error are you getting when you can't stream media?

---

### Post by carlosp039 on 2008-11-25
Hey everyone I'm a total ubuntu noob, I have no clue how to get this working,. I've been searching on google and youtube for step by step instructions. I cant even get past the first step, i download the source code to my desktop. then once i open up terminal to enter the first command i get this:

carlos@carlos-desktop:~$ cd ~
carlos@carlos-desktop:~$ mkdir src
mkdir: cannot create directory `src': File exists

I'm new to this whole command line thing so any help would be greatly appreciated. Thanks in advance!

---

### Post by RavUn on 2008-11-26
You already have a directory named src... src is just where he's unpacking the files.  See what you have in the src directory.
Type:
```
cd ~/src
ls -a

```
and it should print whatever  you have in there.  If it's empty (except for '.' and '..') then you can work inside that directory. 
IF IT'S EMPTY... TYPE:
```
cd ~
```
and resume the rest of his instructions after his cd ~ and mkdir src instructions.  If you downloaded the file to your desktop then you'll need to edit his second code to:
```
mv ~/Desktop/ushare-11a-netou.tar.bz2 ~/src/
```


If the src directory is NOT empty, let us know what prints when you type ls -a.




Just for clarification, here's what the commands do:
cd - change directory... so when you type cd ~ you change to the home directory.
mkdir - make directory... so when you type mkdir src you make a director called "src" inside the home directory.
mv - move... so he's moving the file you downloaded from your desktop to the src directory (make sure you use the mv code I provided above since you saved the file to your desktop instead of the home directory).

After that you're changing directories to your src directory that you created earlier and moved the file to.
tar -xjf - extracts the files from the tarball (ushare-11a-netou.tar.bz2 is the bzipped tarball).

Hope that's not too confusing.

---

### Post by Dark Hornet on 2008-11-26
Nullack -- I have to say...THANK YOU!!!  I am now watching a movie with my daughters (Alvin and the Chipmunks)...via Ushare.  I have been wanting to do this for a while...thanks.

Darkhornet

---

### Post by cruckin on 2008-11-27
Alright having troubles of course thats my luck...
it gives me this message
 * Starting uShare UPnP A/V & DLNA Media Server: ushare                         /etc/ushare.conf: 25: string: not found
 * No shares avalaible ...

and i have no doubt it is something im doing 
im running this all wireless so my desktop computer is connected to the internet wireless by the router and same goes for my xbox so im guessing theres a change in eth0 and also i think im getting the directory wrong cause im not sure how to do that i put in /home/desktop/Media 
media is a folder with a few folders in it that has movies and music folders within it help would be great if possible thanks for the guide

---

### Post by joncolson on 2008-11-30
Thank You!  I just installed 8.10 and this worked perfectly on the first try.

---

### Post by jdorenbush on 2008-11-30
Fresh install of uShare on 8.10 seems to be working.

---

### Post by yavez on 2008-11-30
Thanks a million.  I reinstalled Vista because I thought it would be hard to get this up and running with my XBOX360, how foolish I was.  Vista's wireless was a pain in the bum and kept dropping the connection all the time, losing the shares.  Install of Ubuntu and 5 mins with your guide and I have everything up and running and working flawlessly.

---

### Post by Maelgwyn on 2008-12-01
This was working perfectly - until the NXE update.. Now I can't access my Ubuntu box from the Xbox. Is there something I need to update?

---

### Post by alexeix on 2008-12-01
See posts on the previous page...

I didn't have a problem with it, but some people said they needed to re-install the media update on the Xbox.

---

### Post by Mr Pockets151 on 2008-12-03
```
USHARE_NAME=          Put the name you want your share to be called e.g. MyMedia
USHARE_PORT=          Define the port number you want to use e.g. 49200
USHARE_DIR=           Configure the share locations e.g. /mnt/hda1,/mnt/hdb1/videos/share/
USHARE_ENABLE_WEB=    Use yes to enable the web interface
USHARE_ENABLE_TELNET= I turn this off with no, preferring to use the web interface
USHARE_ENABLE_XBOX=   This must be yes for 360 sharing to work
```How do I know what port to use?

---

### Post by jdorenbush on 2008-12-03
> **Mr Pockets151 said:**
> ```
USHARE_NAME=          Put the name you want your share to be called e.g. MyMedia
USHARE_PORT=          Define the port number you want to use e.g. 49200
USHARE_DIR=           Configure the share locations e.g. /mnt/hda1,/mnt/hdb1/videos/share/
USHARE_ENABLE_WEB=    Use yes to enable the web interface
USHARE_ENABLE_TELNET= I turn this off with no, preferring to use the web interface
USHARE_ENABLE_XBOX=   This must be yes for 360 sharing to work
```How do I know what port to use?

Just go ahead and use 49200 (Should be between 49152&#8211;65534 I believe). Make sure that you forward the port on your router though.

See [this]("http://www.portforward.com/english/routers/port_forwarding/routerindex.htm") for a guide to forward port.

---

### Post by RavUn on 2008-12-04
Mine works without port forwarding.  I think since it's UPnP it automagically does it.

---

### Post by Horns on 2008-12-05
I didn't see much benefit in the patched version, as it still doesn't use music metadata properly, so I went back to the version in the repos to stream my videos, and for music I use x360mediaserve instead. It happily runs alongside ushare, sorts all my music according to tags, and even lets you add streams so you can listen to last.fm and such. Until ushare gets updated this seems the best solution...

---

### Post by Rubicon421 on 2008-12-09
Is there an easier way to set this up? I'm pretty new to linux and streaming to the XBOX is one of the only things holding me back from deleting windows altogether. Isn't there a program with a GUI for all the settings and configurations so you don't have to use the terminal?

---

### Post by RicJD on 2008-12-09
Hi

Even though i've added this to started up, it's never started and i have to start it manually:

```
rick@BatComputer:~$ sudo update-rc.d ushare defaults
[sudo] password for rick: 
 System startup links for /etc/init.d/ushare already exist.
rick@BatComputer:~$ 
```


does anyone have any ideas?

Thnanks

Rick

---

### Post by jdorenbush on 2008-12-09
> **RicJD said:**
> Hi

Even though i've added this to started up, it's never started and i have to start it manually:

```
rick@BatComputer:~$ sudo update-rc.d ushare defaults
[sudo] password for rick: 
 System startup links for /etc/init.d/ushare already exist.
rick@BatComputer:~$ 
```


does anyone have any ideas?

Thnanks

Rick

Same thing happens to me. I haven't been able to figure out the auto-start.

---

### Post by jdorenbush on 2008-12-10
Is there anyway to add 'Details' to the videos/music displayed from uShare on the Xbox 360? Or even a thumbnail of the video or album art from the music?

It looks like Xbox 360 is setup to display this kind of stuff.

---

### Post by Horns on 2008-12-10
> **Kill Vista said:**
> Is there an easier way to set this up? I'm pretty new to linux and streaming to the XBOX is one of the only things holding me back from deleting windows altogether. Isn't there a program with a GUI for all the settings and configurations so you don't have to use the terminal?

You can use the web interface once you know what port ushare is using - you'll have to edit /etc/ushare.conf and specify a port, then point your web browser at ```
http://yourlocalipaddress:portnumber/web/ushare.html
```

Don't be detered though - editing the config file is really simple. Just type ```
gksudo gedit /etc/ushare.conf
``` into a terminal, change the options you need to, and hit ctrl-s to save.

---

### Post by mr_skater99 on 2008-12-10
Heres my problem - hoping someone has a suggestion.

I have previously had ushare running on my old 8.04 32 bit box.  Worked perfectly - started on boot - was not an issue.

I have recently got a new box - and have done a fresh install of 8.10 64bit.  I have tried both the method listed here as well as installing from the repos using the exact same config as my old box - as well as changing just about everything possible in the config file.  

When I start up my server ushare starts fine - and the computer shows up on the video tab in my xbox - but its cant access it (just sits there saying connecting until it times out).  But if I restart ushare (/etc/init.d/ushare restart) with the xbox on - works a treat.  

I can restart my box as many times as I like - but as soon the the xbox is power cycled I have to restart ushare for it to work.

The old box is off, but if I plug it back in, it works perfectly straight away.

The only difference between the old and the new box that I can see is that one is 64bit and one is 32bit.

Can anyone offer any suggestions?  To me its something to do with uPnP maybe?

Cheers.

---

### Post by jdorenbush on 2008-12-10
> **mr_skater99 said:**
> Heres my problem - hoping someone has a suggestion.

I have previously had ushare running on my old 8.04 32 bit box.  Worked perfectly - started on boot - was not an issue.

I have recently got a new box - and have done a fresh install of 8.10 64bit.  I have tried both the method listed here as well as installing from the repos using the exact same config as my old box - as well as changing just about everything possible in the config file.  

When I start up my server ushare starts fine - and the computer shows up on the video tab in my xbox - but its cant access it (just sits there saying connecting until it times out).  But if I restart ushare (/etc/init.d/ushare restart) with the xbox on - works a treat.  

I can restart my box as many times as I like - but as soon the the xbox is power cycled I have to restart ushare for it to work.

The old box is off, but if I plug it back in, it works perfectly straight away.

The only difference between the old and the new box that I can see is that one is 64bit and one is 32bit.

Can anyone offer any suggestions?  To me its something to do with uPnP maybe?

Cheers.

When I have problems with uShare I remove it completely and walk through the install step by step, and it usually resolves my problems. I have had to do this like twice now. Try a reinstall.

Can you post your *ushare.conf*?

---

### Post by mr_skater99 on 2008-12-10
Thanks for the suggestion.

I have tried a full uninstall and install about 5 -  times this morning.  trying different options and the same options a few different times.

here is my ushare.conf:

# /etc/ushare.conf
# Configuration file for uShare

# uShare UPnP Friendly Name (default is 'uShare').
USHARE_NAME=photon

# Interface to listen to (default is eth0).
# Ex : USHARE_IFACE=eth1
USHARE_IFACE=eth0

# Port to listen to (default is random from IANA Dynamic Ports range)
# Ex : USHARE_PORT=49200
USHARE_PORT=49200

# Port to listen for Telnet connections
# Ex : USHARE_TELNET_PORT=1337
USHARE_TELNET_PORT=

# Directories to be shared (space or CSV list).
# Ex: USHARE_DIR=/dir1,/dir2
USHARE_DIR=/home/scotty/storage

# Use to override what happens when iconv fails to parse a file name.
# The default uShare behaviour is to not add the entry in the media list
# This option overrides that behaviour and adds the non-iconv'ed string into
# the media list, with the assumption that the renderer will be able to
# handle it. Devices like Noxon 2 have no problem with strings being passed
# as is. (Umlauts for all!)
#
# Options are TRUE/YES/1 for override and anything else for default behaviour
USHARE_OVERRIDE_ICONV_ERR=

# Enable Web interface (yes/no)
USHARE_ENABLE_WEB=yes

# Enable Telnet control interface (yes/no)
ENABLE_TELNET=

# Use XboX 360 compatibility mode (yes/no)
USHARE_ENABLE_XBOX=yes

# Use DLNA profile (yes/no)
# This is needed for PlayStation3 to work (among other devices)
ENABLE_DLNA=yes

---

### Post by mr_skater99 on 2008-12-11
So I went back and did a complete removal of everything installed.

Installed to a T from this guide, and same issue.

uShare starts fine when my box boots, i can see the web interface, my xbox lists my computer - but i cant access it on the xbox.

After playing about all afternoon this is what i have come up with.

When i start ushare manually with the xbox on i see an initial handshake take place.

If i try and access my computer from my xbox during this window (about 5 - 10 secs) it works perfectly.  i can restart my box/ushare as much as i like and it works.  but as soon as i restart the xbox back to not being able to see the computer but not access it.

Any suggestions?

Strange since it worked perfectly on my old computer.  Only difference is 64bit vs 32bit.

---

### Post by Horns on 2008-12-11
> **mr_skater99 said:**
> 
# Use DLNA profile (yes/no)
# This is needed for PlayStation3 to work (among other devices)
ENABLE_DLNA=yes

Have you tried setting this to 'no'? Or are you using a PS3 as well as your xbox?

---

### Post by kadafi69 on 2008-12-11
im having the same problem with auto-start, which isnt a massive problem just an annoyance.

but another problem is, when my house mate tries to connect to the shares on his XP laptop it just takes him to the [http://ipaddress: port/web/ushare.html](http://ipaddress: port/web/ushare.html) page and cannot access the shares.

---

### Post by mr_skater99 on 2008-12-11
I have tried DLNA=no.

It was yes on my old box - but i figured it was worth a shot.

---

### Post by pormogo on 2008-12-13
Oh man this is annoying!

Getting ushare working with the Xbox is a serious pain. My Xbox can't seem to see ushare (I am using the version of ushre provided from the repos for 8.10) 

[i]$ ushare -V
uShare (version 1.1a), a lightweight UPnP A/V and DLNA Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See [http://ushare.geexbox.org/](http://ushare.geexbox.org/) for updates.
[/i]

I know it's working, I don't use any of the interfaces I just let the config do the work for me. I can stream video and audio to my PS3 just fine but 360 can't find my computer. I'm using the "NXE" update going to console settings>test connection>Test PC connection. 

All in all I think the 360 is a piece of junk, if you assign it a static IP it makes me "test connection" anytime I want to connect to XBL, and doesn't "see" my network for PC connections. After I switched it to DHCP it sees the network and sits on a screen where the only option is "PC not listed" and tells me to wait 90 seconds. I waited about 15 minutes and restarted ushare a few times. Never popped up. Here's my config. 

```
# /etc/ushare.conf
# Edit this file with 'dpkg-reconfigure ushare'
# Configuration file for uShare

# uShare UPnP Friendly Name (default is 'uShare').
USHARE_NAME=odor

# Interface to listen to (default is eth0).
# Ex : USHARE_IFACE=eth1
USHARE_IFACE=eth0

# Port to listen to (default is random from IANA Dynamic Ports range)
# Ex : USHARE_PORT=49200
USHARE_PORT=49157

# Port to listen for Telnet connections
# Ex : USHARE_TELNET_PORT=1337
USHARE_TELNET_PORT=

# Directories to be shared (space or CSV list).
# Ex: USHARE_DIR=/dir1,/dir2
USHARE_DIR=/media

# Use to override what happens when iconv fails to parse a file name.
# The default uShare behaviour is to not add the entry in the media list
# This option overrides that behaviour and adds the non-iconv'ed string into
# the media list, with the assumption that the renderer will be able to
# handle it. Devices like Noxon 2 have no problem with strings being passed
# as is. (Umlauts for all!)
#
# Options are TRUE/YES/1 for override and anything else for default behaviour
USHARE_OVERRIDE_ICONV_ERR=

# Enable Web interface (yes/no)
ENABLE_WEB=no

# Enable Telnet control interface (yes/no)
ENABLE_TELNET=no

# Use XboX 360 compatibility mode (yes/no)
ENABLE_XBOX=yes

# Use DLNA profile (yes/no)
# This is needed for PlayStation3 to work (among other devices)
ENABLE_DLNA=yes

```

Any idea why something like this might happen? Any setting or anything I can change?

EDIT: Well I tried compiling the patched version of ushare figuring that perhaps one of the fixes therein might actually make it possible for this to work. 

I followed the guide pretty much verbatim. I'm hardly an expert at building source but we use a lot of net/freebsd at my job and that seems to have paid off. I had the dev files for dlna support and I would ideally like to use this for my PS3 as well so I compiled with DLNA support on

* ./configure --prefix=/opt --enable-dlna*

I did purge my system of ushare/configs from the apt installed version of ushare. Everything seemed to check out and build ok.

[i]~# ushare -V
uShare (version 1.1a**-NeToU)**, a lightweight UPnP A/V and DLNA Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See [http://ushare.geexbox.org/](http://ushare.geexbox.org/) for updates.[/i]


I used the same config ile. Both my PS3 and My XBox are able to see the server (it shows up) however neither of them are able to connect to it. Oh wait my PS3 IS able to play audio files. I can browse the "dreictroy skeleton" for my video files however I am not able to see any video files...

The Xbox is able to see my computer however as soon as I try and connect it tells me that it is not able to connect :(   

I tried running the process in the foreground in order to see if there where any errors but I didn't get any usefull output... Below is the string I used to start it without the config file.

*ushare -i eth0 -p 49157 -c /media -w -t -x -d -v*

Should be the exact same settings as my config file. Still no good. I am running ushare as root (since that is how the init script was starting it).

---

### Post by Horns on 2008-12-14
I'd say you a problem with your router.

---

### Post by pormogo on 2008-12-15
I'm actually pretty posative it's not a problem with the router. The router is running openwrt and when i was futzing with this to get it working I actually implicity allowed all traffic from the PC to the Xbox, made no difference. If I put the PS3 on the same switch port and use the same IP it is able to use DLNA. ufw is not loaded on my box. I can't possibally imagine that it's some manner of magic router issue. 

BTW the removal option given in the first post doesn't seem to work. 

[i]~/src/ushare-1.1a-NeToU$ sudo make uninstall
make: *** No rule to make target `uninstall'.  Stop.[/i]

EDIT: I am still trying to figure out why my PS3 suddenly can't see videos in the patched version but audio files are working just fine. the only thing I can think of is that the mime type isn't set correctly. Checking ~/src/ushare-*-NeToU/src/mime.c I see

[i]/* Video files */
...
{ "avi",   UPNP_VIDEO, "http-get:*:video/avi:"}
[/i]

If I remember correctly the PS3 is looking for 

*{ "avi",   UPNP_VIDEO, "http-get:*:video/divx:"}*

I am going to try fixing that string recompiling it and seeing if I am able to see my .avi videos on my PS3 after that. I am still totally clueless as to what could be going on with the Xbox. 

I remember reading that the Xbox can be extremely picky about the uuid of the mediaserver it connects to. Could that have something to do with this? I noticed that build-dep for ushare didn't grab any uuid libs. should it have?

EDIT: Ok well I manually removed all the files I installed under my /opt installation of this application and then used the configure line provided (while enabling dlna*:$ ./configure --prefix=/ --bindir=/usr/bin --mandir=/usr/share/man --enable-dlna*). I also changed the avi mime type in mime.c to see if it would get my PS3 working. The configure script spit out the following at me

```
uShare: configure is OK
  version            1.1a-NeToU
  using libupnp      1.6.6
  using libdlna      0.2.3
configuration:
  install prefix     /
  configuration dir  ${PREFIX}/etc
  data dir           ${PREFIX}/share
  locales dir        ${datadir}/locale
  mans dir           /usr/share/man
  NLS support        yes
  DLNA support       yes
  C compiler         gcc
  STRIP              strip
  make               make
  CPU                x86_64 ()
  debug symbols      no
  strip symbols      yes
  optimize           yes

  CFLAGS              -I.. -W -Wall -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_REENTRANT -D_GNU_SOURCE -O3 -DHAVE_LOCALE_H -DHAVE_SETLOCALE -DHAVE_IFADDRS_H -DHAVE_LANGINFO_H -DHAVE_LANGINFO_CODESET -DHAVE_ICONV -pthread -I/usr/include/upnp -DHAVE_DLNA -I/usr/include/ffmpeg
  LDFLAGS            
  extralibs           -lixml -lthreadutil -lpthread -lupnp -ldlna -lavformat -lavcodec -lraw1394 -ltheora -lvorbisenc -lavutil -lm -logg

Creating config.mak ...
Creating config.h ...

```

Everything looks kosher to me there. I am using the same config as above. I'll updated this when i get home later and I can see how it worked.

---

### Post by Voorhees1979 on 2008-12-16
Hi there

I have a slight problem. Basically my shares on my pc are in here /media/disk-1/media  in this media folder are 3 more folders called movies/pictures/music

So i figure I only need to share /media/disk-1/media then goto the directories I want from the xbox

So i load up the xbox goto video tab and i see the folders called movies/music/pictures. Great I think. I goto the movies folder and can play all my films.

I then stop this and goto the music tab on the xbox thinking I will see movies/music/pictures folders like before so I can just select music to go into my dir. BUT when I goto pictures or music on the actual xbox it shows nothing at all. Its only in the video tab on the xbox that it shows my shared folders???

Many thanks for nay help

---

### Post by pormogo on 2008-12-16
Well looks like changing the mimetype in that file totally broke PS3 support all together now it just spits DNLA errors at me like crazy when I try and use it. I'm going to recompile and install it the normal way again and just wait for responses here/ inspiration to try again.

---

### Post by Shhnap on 2008-12-16
Could I just suggest that in the settings section you remind people of wlan0 (other than just eth0) because that stumped me for a minute.

Otherwise excellent HOW TO!!! Thanks from me.

---

### Post by GoFFydUb on 2008-12-18
works flawless! thx =D>

---

### Post by pormogo on 2008-12-20
I don't know if it was mentioned earlier on and I missed it or if no one has pointed it out yet but flagging DLNA=on seems to break Xbox support (or maybe the actual PS3 connection to ushare occupies the daemon). Anyways I turned it off and it works perfectly now. 

Guess I'll just use mediatomb to share to that device (seems like such a waste to use 2 different applications for almost the same thing).

EDIT: An interesting addendum, if I turn dlna off in the config it still functions on my PS3...

---

### Post by magiver on 2008-12-22
Hi

I've been fighting with uShare for the last 4 hours and I can't seem to get it working.
I installed with no problems following this post, but this thing is just not working...
My xbox can see my pc, but when I try to explore it, it tries to connect for like 30 seconds just to show me a "Can't connect to the PC. blablabla"
Any ideas?

This is a copy of my ushare.conf just in case
```

# /etc/ushare.conf
# Configuration file for uShare

# uShare UPnP Friendly Name (default is 'uShare').
USHARE_NAME=streamv

# Interface to listen to (default is eth0).
# Ex : USHARE_IFACE=eth1
USHARE_IFACE=wlan0

# Port to listen to (default is random from IANA Dynamic Ports range)
# Ex : USHARE_PORT=49200
USHARE_PORT=49200

# Port to listen for Telnet connections
# Ex : USHARE_TELNET_PORT=1337
USHARE_TELNET_PORT=

# Directories to be shared (space or CSV list).
# Ex: USHARE_DIR=/dir1,/dir2
USHARE_DIR=home/juan/Videos/

# Use to override what happens when iconv fails to parse a file name.
# The default uShare behaviour is to not add the entry in the media list
# This option overrides that behaviour and adds the non-iconv'ed string into
# the media list, with the assumption that the renderer will be able to
# handle it. Devices like Noxon 2 have no problem with strings being passed
# as is. (Umlauts for all!)
#
# Options are TRUE/YES/1 for override and anything else for default behaviour
USHARE_OVERRIDE_ICONV_ERR=

# Enable Web interface (yes/no)
USHARE_ENABLE_WEB=no

# Enable Telnet control interface (yes/no)
USHARE_ENABLE_TELNET=no

# Use XboX 360 compatibility mode (yes/no)
USHARE_ENABLE_XBOX=yes

# Use DLNA profile (yes/no)
# This is needed for PlayStation3 to work (among other devices)
USHARE_ENABLE_DLNA=yes

```

---

### Post by dccrens on 2008-12-22
Well... I messed with this for weeks and could never get it working properly. I installed twonkymedia in about 10 minutes and works great. I am sharing, music, picts and video with no issues. No expiration either...

---

### Post by orthod0ks on 2008-12-23
This tutorial worked flawlessly for me once I realize my interface wasn't the default. I have to agree that music streaming is pretty much useless in its current form without metadata. Though, is there a way to view music like videos on the 360 - by directory - and then simply play an entire directory?

---

### Post by mackis5 on 2008-12-25
> **magiver said:**
> Hi
```

# Directories to be shared (space or CSV list).
# Ex: USHARE_DIR=/dir1,/dir2
USHARE_DIR=home/juan/Videos/

```

I guess you forgot a / in front of your file share:
```

USHARE_DIR=home/juan/Videos/

```
should be with a / added in the beginning and a / removed in the end
```

USHARE_DIR=/home/juan/Videos

```

---

### Post by Nullack on 2008-12-28
Gday everyone.

I am pleased to be able to share that the FUPPES project seems to be back on track now and the proposed fork looks to be coming back into the fold. FUPPES brings us some better features which brings us more powerful ways to enjoy our media sharing onto the 360.

Ive checked out the SVN version and am conducting tests. Should this all go ok, I will be changing this guide to remove ushare and use FUPPES.

---

### Post by PorchSong on 2008-12-29
> **Nullack said:**
> Gday everyone.

I am pleased to be able to share that the FUPPES project seems to be back on track now and the proposed fork looks to be coming back into the fold. FUPPES brings us some better features which brings us more powerful ways to enjoy our media sharing onto the 360.

Ive checked out the SVN version and am conducting tests. Should this all go ok, I will be changing this guide to remove ushare and use FUPPES.

What version are you taling about?  I have version 627 and all is good.  I set up a guide a few weeks ago for a Ubuntu 8.10 fuppes install that will allow you to check out svn v627 as well:

[http://ubuntuforums.org/showthread.php?t=984325]("http://ubuntuforums.org/showthread.php?t=984325")

Hell, fuppes is significantly more stable than mediaplayer 11 in Vista and works more effeciently.

---

### Post by Maelgwyn on 2008-12-31
Can't remember which version I'm running of ushare (I'm at work at the moment), but everything works for me albeit all videos have to load for AGES before they start playing =/

---

### Post by Nullack on 2008-12-31
> **PorchSong said:**
> What version are you taling about?  I have version 627 and all is good.  I set up a guide a few weeks ago for a Ubuntu 8.10 fuppes install that will allow you to check out svn v627 as well:

[http://ubuntuforums.org/showthread.php?t=984325]("http://ubuntuforums.org/showthread.php?t=984325")

Hell, fuppes is significantly more stable than mediaplayer 11 in Vista and works more effeciently.

Hi PorchSong,

The svn trunk is the latest revision - its currently at 627. Due to the main developer going awol a fork project came about called Fuppex but now that the guy is back it looks as though both projects will remerge.

I'd be happy to join up with you on a how to for Jaunty which Im currently testing. I dont build with transcoding support because:

1. The repos ffmpeg is ancient
2. illegal status in some countries
3. IMHO its better to transcode outside of a upnp server to more effectively control video and audio settings for the transcode

Maelgwyn most likely you do not have the necessary network bandwidth for real time streaming.

---

### Post by catfish182 on 2009-01-03
Hi Guys, 

I have a question, at the moment I can perfectly stream all media to my xbox 360 just like I want, however the method is a little convoluted. 

1. I installed twonky media. From Twonky I share my music and pictures. I did not share video as the xbox360 can't read avi files when shared through twonky.

2. For video I'm using ushare. this works brilliantly. However, I can't share music and pictures through ushare because it doesn't order or sort the info, all pictures vids and movies are jumbled into a folder which makes it very unintuitive and sometimes just doesn't play at all most of the music.

So, is there a better way to do this? I have to have twonky media server and ushare running at the same time, this nets me the result of 2 visible shares on the xbox that I can browse, 1 for video and one for pictures and music.

I guess I have 2 questions

1. is there a way to get ushare to sort its folders out correctly?
2. Is there a way to get twonky to share the videos without getting a 'not supported error' on most divx files (I have the xbox update to allow divx of course and it plays flawlessly via the ushare share)

---

### Post by neoroses on 2009-01-04
this is amazing thank you very much, even easier than in windows!!! lol on slight thing, when browsing my music folder on my 360 that is on my pc i can only see the songs that are directly in the music folder i have shared, media/media/music but there are another 3000 folders in the music folder its self, is there a way to share all these sub folders with out having to manualy share each one?

thanks

---

### Post by CricTic on 2009-01-08
[deleted]

---

### Post by CricTic on 2009-01-08
I'm pretty frustrated, and I've been banging away at this for days.

I'm trying to stream videos from an Ubuntu 8.10 server.  I have followed the instructions at the top of the thread and have been able to successfully get uShare installed and running.  The xbox emulation mode is active, according to the output, and I can even see the web interface.

However, although I can see the uShare server from the Xbox (although, only if I restart it while the Xbox is in the "wait for 30 seconds screen for your server to show up" screen), if I select it the xbox thinks for a few seconds and then gives me a connection error.  There is no helpful output from the terminal window where uShare is running.  I have even tried removing all the packages via synaptic and reinstalling, no effect.

Here are all the non-comment lines from my config file:

```
USHARE_NAME=videos
USHARE_IFACE=eth0
USHARE_PORT=49200
USHARE_TELNET_PORT=
USHARE_DIR=/data/videos
USHARE_OVERRIDE_ICONV_ERR=
USHARE_ENABLE_WEB=yes
USHARE_ENABLE_TELNET=no
USHARE_ENABLE_XBOX=yes
USHARE_ENABLE_DLNA=no
```

And here's my ushare output:

```
$ sudo ushare
uShare (version 1.1a-NeToU), a lightweight UPnP A/V and DLNA Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See [http://ushare.geexbox.org/](http://ushare.geexbox.org/) for updates.
Initializing UPnP subsystem ...
Starting in XboX 360 compliant profile ...
UPnP MediaServer listening on 192.168.0.4:49200
Sending UPnP advertisement for device ...
Listening for control point connections ...
Building Metadata List ...
Looking for files in content directory : /data/videos
Found 279 files and subdirectories.
```

:confused: Help!

---

### Post by Floor19 on 2009-01-09
@crictic

Have you set your firewall correctly?

@all

Anyone has his music sorted out so XB360 can play them correctly instead of everything only available in songs??

F

---

### Post by CricTic on 2009-01-09
My firewall is disabled in Ubuntu.

---

### Post by catfish182 on 2009-01-10
@Floor19

I could not get ushare to handle movies properly. How I worked around the problem I outlined at in my post 2nd from the top of this page.

run twonky for music and pictures but not movies (doesn't handle the codecs)

run ushare for the videos (as ushare can't distinguish between movies and songs and puts them all in the same directory) 

I have it all running perfectly and twonky and ushare running side by side doesn't seem to impact my Dell D400 laptop in the slightest. 

From my xbox I see 2 seperate shares. 

It's pretty much an almost perfect solution. I've heard that the 30 day linux trial doesn't expire for twonky as well ;) 

If twonky can get the codecs sorted and stream movies as well, then I would pay for their solution, it's incredibly easy (easier than ushare)

---

### Post by rko618 on 2009-01-11
@crictic

make sure the init.d script is not running

$ sudo /etc/init.d/ushare stop

then try in terminal (note the -x option)

$ ushare -x

---

### Post by Nodds on 2009-01-17
Will Ushare play m3U files through the Xbox 360?

I've installed it and can play Mp3s through my Xbox, however it doesnt see the radio station playlists i've added to the folder?

Nodds

---

### Post by neoroses on 2009-01-18
helo again, rite dont know if any one can shed any light on this, i recently switched from PC Ethernet ---> route ----> xbox Ethernet which worked fine, i then changed my pc to wireless, and edited the ushare config file to use wlan0, now this worked for a day, then it started to slow up and now my pc doesnt even show up on the xbox,,, any ideas?

---

### Post by neoroses on 2009-01-18
i had this working fine on my wireless connection, and its jus stopped working. tried re-installing, changing the config file to wlan0 but im still getting nothing, any ideas?

---

### Post by bg1256 on 2009-01-18
Hey everyone!

First off, thanks for taking the time to put this guide together and for continuining support. I have tried Twonky in the past, but it never worked well for me.

I am hoping to use this to stream video files to my 360 from my Ubuntu running Hardy.

I followed the guide, step-by-step, and I have a question regarding ensuring I am sharing the proper directory, or more accurately, making sure that I entered the data correctly into the .config file.

So, here goes.

I created a partition which I named "multimedia" following a guide on psychocats.

When I bring up fstab, here's the output:

```
/dev/sdb1 /multimedia ext3 defaults 0 0
```

When I bring that partition up in nautilus it shows up as:

```
/multimedia
```

Here is what I entered in the .config:

```
/dev/sdb1/multimedia
```

I'm not sure if the ```
/dev/sdb1
``` is necessary and if it will cause problems. I will test it out, of course, but I'm wondering if someone more knowledgeable than I could give me some advice?

Thanks!

---

### Post by bg1256 on 2009-01-18
Nevermind... trial and error solved the problem!

And after lots of trying other methods, I finally have streaming video from Ubuntu to 360!!!!

---

### Post by rotor_of_the_internet on 2009-01-19
Hi,

I'm new to Linux. I've followed guides for uShare and Twonky. I can both detect them on my Xbox 360, but when I try to connect my 360 to either of them it just times out.

I can also access the web interfaces of both programs on my other Windows XP machine. I disabled the UFW firewall, and that doesn't help. I've also added the line "ALL: 192.168.123.0" to my /etc/hosts.allow. I don't have any problems playing Quake 2 over my network or sharing files through a Samba share. According to the specifications of my router it supports UPnP.

I've been struggling with this for days. Can anyone help me out?

---

### Post by rko618 on 2009-01-20
I mentioned this before but I just want to say it again in case you missed it but for those people having trouble getting this to work, **try starting ushare from the command line instead of with the init.d script**.

```
$ sudo /etc/init.d/ushare stop
$ ushare -x
```

---

### Post by otkaz on 2009-02-05
I hate to post on such an old thread, but I cant find a solution to this
I'm using ubuntu 8.10 and following the directions from [http://ubuntuforums.org/showpost.php?p=5311079&postcount=1](http://ubuntuforums.org/showpost.php?p=5311079&postcount=1)
but getting this...

otkaz@otkaz-lappy:~/src/ushare-1.1a-NeToU$ sudo apt-get build-dep ushare
[sudo] password for otkaz: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for ushare
otkaz@otkaz-lappy:~/src/ushare-1.1a-NeToU$ ./configure --prefix=/ --bindir=/usr/bin --mandir=/usr/share/man
Checking for compiler available...
Checking for locales ...
Checking for ifaddrs ...
Checking for langinfo ...
Checking for iconv ...
Checking for libixml ...
Error, can't find libixml !
See file "config.log" produced by configure for more details.

any suggestions?

---

### Post by bg1256 on 2009-02-07
Hi all.

First off, thanks for this thread! I've finally found a way to stream video from within Linux, rather than resorting to VMWare to access my Windows install. What a relief...

When I first installed ushare, it started automatically without any problems at system boot.

However, now it is no longer starting at system boot. When I run the command listed here originally started ushare at boot, I am informed that the links already exist, even though it is not starting.

I suspect that it has something to do with a kernel update, but I'm not sure.

Does anyone know how to fix this?

---

### Post by Molochz on 2009-02-10
Hey dude great post. But when i start uShare i get this in the terminal
```

sudo /etc/init.d/ushare start
 * Starting uShare UPnP A/V & DLNA Media Server: ushare                         
/etc/ushare.conf: 35: The: not found
/etc/ushare.conf: 37: Desktop: not found
/etc/ushare.conf: 38: Desktop: not found
/etc/ushare.conf: 39: Desktop: not found
/etc/ushare.conf: 40: Desktop: not found
/etc/ushare.conf: 41: Desktop: not found
/etc/ushare.conf: 42: Desktop: not found

```
  Wonder whats wrong, If you could help me that would be great.
Thanks

---

### Post by buchannon on 2009-02-14
Hey guys... I feel defeated. I have absolutely loved ushare in the past... then I did an update (one the required a restart) to my comp and can't seem to get it going again.

> ushare -x
Interface eth0 is down.
Recheck uShare's configuration and try again !
uShare (version 1.1a), a lightweight UPnP A/V and DLNA Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See [http://ushare.geexbox.org/](http://ushare.geexbox.org/) for updates.
Listening on telnet port 1337
[B]Initializing UPnP subsystem ...
Cannot initialize UPnP subsystem
Stopping UPnP Service ...[/B]


After googling a bunch of this and coming to no conclusion, I'm finally left to post. The 'eth0 is down' part isn't what's scaring me. A lot of things I've read said that people are getting this error but still are getting ushare to work.

To reiterate, I used ushare for about a year with no problem before whatever update I installed on my computer to break things. Any ideas?

Thank you!

---

### Post by mamaro on 2009-02-16
I have to stop ushare and then restart it to have ushare see any updates (added files, name changes). anybody have a fix?
Is this how ushare behaves?

---

### Post by Firestarter-Ibex on 2009-02-17
Hi guys, just wonder if anyone can help me map my media. I have installed ushare and can access it with the web portal. I can also see anything I attempt to share on the Xbox so that is working. The problem is I don't actually know how to map my media.

I have a Terabyte hard drive (called Terabyte) that has a Movies folder on it .

 The Terabyte drive shows up as:

Device=    /dev/sdb1
Directory= /media/Terabyte

on System Monitor, so I would assume that the map would be /dev/sdb1/media/Terabyte/Movies, but this doesn't share the files in the directory and ushare says it's only sharing 1 directory.

Anyone know what I am doing wrong?

---

### Post by bg1256 on 2009-02-17
> **Firestarter-Ibex said:**
> Hi guys, just wonder if anyone can help me map my media. I have installed ushare and can access it with the web portal. I can also see anything I attempt to share on the Xbox so that is working. The problem is I don't actually know how to map my media.

I have a Terabyte hard drive (called Terabyte) that has a Movies folder on it .

 The Terabyte drive shows up as:

Device=    /dev/sdb1
Directory= /media/Terabyte

on System Monitor, so I would assume that the map would be /dev/sdb1/media/Terabyte/Movies, but this doesn't share the files in the directory and ushare says it's only sharing 1 directory.

Anyone know what I am doing wrong?

It looks like you've entered it incorrectly... I did the same thing at first.

You need to enter:

```
/media/Terabyte/Movies
```

Assuming that's the directory you want to share. Simply delete /dev/sdb1 from the config file, and you should be fine.

My share is:

```
/media/Multimedia/TV  
```

I don't bother with /dev/sdb1, which is also the name of my drive, coincidentally.

---

### Post by abandonedthe_mulletator on 2009-02-20
I have a home network set up as follows:
Internet <--> Ubuntu Server <--> Router <--> Computers & XBOX

I am running ushare on the server.  If I connect the XBOX directly to the server ushare works great.  My router prevents it from working.  I have forwarded lots of ports on the router but no luck.  I read somewhere that my firewall must allow multicasting but I don't know how to do that.

---

### Post by abandonedthe_mulletator on 2009-02-20
Good news.  I found a network card on craigslist for $5.  So I put that sucker in the server and now I am running the XBOX on its own network card.

Ushare works!

I can only get about 50 files on the XBOX though.  Is there a way I can tweak it to allow more files?

---

### Post by s3lekta on 2009-02-22
Perfect it works :-) thanks

This is more easier to get up and running then Fuppes

---

### Post by ddigler on 2009-02-22
Hoping someone can take some time with me here... I'm a complete noob to Linux; currently running 8.10. I connect to the Internet with a wireless USB G adapter to a Linksys router, my 360 connects wirelesly to the same router. Internet is working on PC, Live connects correctly on 360. 8.10 is running great no probs to speak of (install only 4 days old)

I followed the tutorial and having completed it 360 would not see anything. Please note, I am currently running dansguardian with squid and firehol for content filtering per a different tut if that makes any dif. Here's what I've got if this helps:

zac@Home-Office-PC:~$ sudo /etc/init.d/ushare start
 * Starting uShare UPnP A/V & DLNA Media Server: ushare                                                               [ OK ] 
zac@Home-Office-PC:~$ sudo ushare
ioctl: Cannot assign requested address
zac@Home-Office-PC:~$ sudo /etc/init.d/ushare stop
 * Stopping uShare UPnP A/V & DLNA Media Server: ushare                                                                      start-stop-daemon: warning: failed to kill 7109: No such process
                                                                                                                      [ OK ]
zac@Home-Office-PC:~$ sudo ipconfig
sudo: ipconfig: command not found
zac@Home-Office-PC:~$ 

My config file:

# /etc/ushare.conf
# Configuration file for uShare

# uShare UPnP Friendly Name (default is 'uShare').
USHARE_NAME=UShare

# Interface to listen to (default is eth0).
# Ex : USHARE_IFACE=eth1
USHARE_IFACE=

# Port to listen to (default is random from IANA Dynamic Ports range)
# Ex : USHARE_PORT=49200
USHARE_PORT=49200

# Port to listen for Telnet connections
# Ex : USHARE_TELNET_PORT=1337
USHARE_TELNET_PORT=

# Directories to be shared (space or CSV list).
# Ex: USHARE_DIR=/dir1,/dir2
USHARE_DIR=/home/zac/music,/home/zac/pictures,/home/zac/videos

# Use to override what happens when iconv fails to parse a file name.
# The default uShare behaviour is to not add the entry in the media list
# This option overrides that behaviour and adds the non-iconv'ed string into
# the media list, with the assumption that the renderer will be able to
# handle it. Devices like Noxon 2 have no problem with strings being passed
# as is. (Umlauts for all!)
#
# Options are TRUE/YES/1 for override and anything else for default behaviour
USHARE_OVERRIDE_ICONV_ERR=

# Enable Web interface (yes/no)
USHARE_ENABLE_WEB=yes

# Enable Telnet control interface (yes/no)
USHARE_ENABLE_TELNET=no

# Use XboX 360 compatibility mode (yes/no)
USHARE_ENABLE_XBOX=yes

# Use DLNA profile (yes/no)
# This is needed for PlayStation3 to work (among other devices)
USHARE_ENABLE_DLNA=

So basically just need help getting back on track. Thanks for help in advance...

---

### Post by calcio1 on 2009-03-25
Thanks for a superb guide

Is there an easy way to get 'soft' subs to display on ushare?

Or do I have to re-encode .avi and .srt into new video?

If the latter, is avidemux the best tool and how long does it take?

Thank you

---

### Post by k1ngb0b0 on 2009-03-26
First off, great guide!  Was incredibly easy to follow even for a novice like myself :).

My problem is that my xbox can't see my computer at all!  

When I run sudo ushare I get this output:

uShare (version 1.1a-NeToU), a lightweight UPnP A/V and DLNA Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See [http://ushare.geexbox.org/](http://ushare.geexbox.org/) for updates.
Initializing UPnP subsystem ...
Starting in XboX 360 compliant profile ...
UPnP MediaServer listening on 192.168.1.102:49206
Sending UPnP advertisement for device ...
Listening for control point connections ...
Building Metadata List ...
Looking for files in content directory : /home/dave/Music
Found 9825 files and subdirectories.

I don't have a firewall on.

For some reason every time I run sudo ushare the output increases in port number and it never shows up in system monitor.

I've tried running sudo ushare -xD but that too did nothing.

I'm running 64 bit ubuntu 8.10 (I have the 32 bit libs installed).

Any suggestions?  I'm trying not to be vague, I'll provide whatever information you guys ask for. :)

Edit: ushare finally showed up in system monitor but the xbox is still not finding my computer :-/

---

### Post by k1ngb0b0 on 2009-03-26
Bump.


Anyone have any thoughts?

---

### Post by imolafem on 2009-03-29
Thanks for the guide on ushare.  I have it installed successfully, but it looks like Wireless G is not good enough to run the stream.

Are there any MTU size changes or other TCP/IP Configuration I can do so my Server and Xbox360 can stream music through Wireless G?

Also, all my music is in directories.  The Xbox360 only sees songs.  What type of files do I need to make to create playlists, see Artists or Albums, etc?

---

### Post by scottybee on 2009-03-31
Morning all, I have recently updated 8.04 to 8.10 using the distro update. I noticed that ushare was no longer speaking to the xbox360. I have since updated ushare to 1.1a and now the xbox360 can see the share. The problem that I have is when streaming the file all I get is the black screen with opening and this just sticks? 
I also get the error that it cant see eth0 and yet its using eth0 and xbox360 and see share.
The same file opens fine if copied to usb pen and streamed that way. No firewall is used. Any ideas?

:P

---

### Post by bgilbertson on 2009-04-17
My ushare-1.1a-NeToU can't seem to find it's dependencies.

bgilbertson@64bitjjbeta:~/src/ushare-1.1a-NeToU$ sudo apt-get build-dep ushare
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Build-dependencies for ushare could not be satisfied.

Is ushare 32-bit only?  Or are its dependencies?


Kubuntu 9.04 AMD64, build-essential 11.4

Athlon64 4200 Dual @2100 mhz
875MB ddr2/667
nVidia nForce 5100, geForce 6100 128 mb Restricted Drivers Installed
Realtek Audio alsa ok

---

### Post by dmweyer on 2009-04-19
Firstly thanks for the excellent instructions. I have just installed ubuntu for the first time so apologies if this is a really dumb question. Everything seems to be fine up until I try and start the service. I have included below the message I receive.

```
/etc/ushare.conf: 5: uShare: not found
/etc/ushare.conf: 9: eth0: not found
/etc/ushare.conf: 13: 49200: not found
/etc/ushare.conf: 21: /home/dill/Media: Permission denied

```

Any help of what I am doing wrong would be appreciated

---

### Post by Nullack on 2009-04-25
Folks, some updates:

1. I'm pleased to advise that the Fuppes UPNP server project has resolved its management issues and is well useable.
2. My xbox 360 is in for repair and I currently cannot test my recent updates but I will do so in time.
3. Fuppes is a better UPNP server than ushare. It supports transcoding and most importantly for me, allows me to specify custom device configurations so I can run both the PS3 and the xbox off of one UPNP server.

Here is some quick notes of how to compile and install fuppes on Ubuntu 9.04 for Jaunty. Be aware that all of the so called guides I've seen so far have incorrect dependencies and I have resolved this for what dependencies are actually required. My testing is not 100% complete so this may change.

sudo apt-get install build-essential subversion autoconf automake gettext libtool libpcre3-dev libxml2-dev libsqlite3-dev libfaad-dev libmad0-dev libflac-dev libmagick++-dev libvorbis-dev libtwolame-dev libmpcdec-dev uuid-dev libavformat-dev libavutil-dev libavcodec-dev libmpeg4ip-dev libmp4v2-dev libtag1-dev libexpat1-dev

svn co [https://fuppes.svn.sourceforge.net/svnroot/fuppes/trunk](https://fuppes.svn.sourceforge.net/svnroot/fuppes/trunk) fuppes
cd fuppes/
autoreconf -vfi
./configure --prefix=/usr
make
sudo make install
make distclean

Then you edit the cfg file. I specified a port, the network adapter to use, what IP addresses can connect to the server etcetc. For both the 360 and ps3 youll have to add custom device profiles for those. So far Ive done my PS3 as the 360 is in for repair.

For PS3:

    <device name="PS3" enabled="true">
      <user_agent>UPnP/1.0 DLNADOC/1.50</user_agent>
      <user_agent>PLAYSTATION3</user_agent>

and

       <file ext="avi">
         <type>VIDEO_ITEM</type>
         <mime_type>video/x-divx</mime_type>
       </file>

---

### Post by nickwalnut on 2009-05-02
Hey Nullack, thanks for your post, been searching for a while for a guide on how to install fuppes and you just happened to have posted :P.

May I ask which cfg file I edit and where it may be located? Also, how do I specify a port, the network adapter to use etc. in the file (is it simple template filling out or do I need commands) and does it matter which port I choose?

Thanks in advance

---

### Post by Nullack on 2009-05-02
Hi,

Its in your home dir under a hidden .fuppes directory.

Heres the network section of my cfg for reference:
```

  <network>
    <!--empty = automatic detection-->
    <interface>eth0</interface>
    <!--empty or 0 = random port-->
    <http_port>44444</http_port>
    <!--list of ip addresses allowed to access fuppes. if empty all ips are allowed-->
    <allowed_ips>
      <ip>192.168.0.11</ip>
      <ip>192.168.0.12</ip>
      <ip>192.168.0.13</ip>
      <ip>192.168.0.14/ip>
    </allowed_ips>
  </network>
```

---

### Post by steev182 on 2009-05-03
Hi Nullack,

A couple of things, I followed your guidelines, but I don't seem to have a .fuppes folder in my home directory when I do ```
ls -a
```.

Also, what do I have to specify for xbox 360 in place of PS3? Is it simply changing the remarks for PS3 with xbox 360?

Thanks for your help

---

### Post by LemonBat on 2009-05-04
I have been able to detect my 360 as a device but when I go into my video library there's nothing...

Not exactly sure what I'm doing wrong.

---

### Post by Ms_Angel_D on 2009-05-09
> **Nullack said:**
> 
sudo apt-get install build-essential subversion autoconf automake gettext libtool libpcre3-dev libxml2-dev libsqlite3-dev libfaad-dev libmad0-dev libflac-dev libmagick++-dev libvorbis-dev libtwolame-dev libmpcdec-dev uuid-dev libavformat-dev libavutil-dev libavcodec-dev libmpeg4ip-dev libmp4v2-dev libtag1-dev libexpat1-dev

When I attempt to run this on Jaunty I get

> libavutil-dev: Depends: libavutil49 (= 3:0.svn20090303-1ubuntu6) but it is not going to be installed

if I attempt to install libavutil49 I get this:

> The following packages will be REMOVED:
  ffmpeg gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad-multiverse
  libavcodec-unstripped-52 libavdevice52 libavfilter0 libavformat52
  libavutil-unstripped-49 libmjpegtools-1.9 libquicktime1 libxine1-ffmpeg
  libxine1-plugins miro vlc vlc-nox
The following NEW packages will be installed:
  libavutil49


I don't know whether it's safe or not remove those they appear to be quite necessary.


[edit]
I had ushare running wonderfully on 8.10 but for some reason the deb I made seemed to not install all dependencies on 9.04. So I removed it. But I finally managed to get it to work by first installing, then completly removing the ushare version found in the repo's, then installing deb file.

So if anyone is interested I have attached the deb (please note it was compiled on 8.10)
[/edit]

Angel

---

### Post by nickwalnut on 2009-05-15
[quote=LemonBat]
I have been able to detect my 360 as a device but when I go into my video library there's nothing....[/quote]

I have the same problem here. The 360 cannot browse through the shared folders let alone see any videos - I can see music however, though even that is a bit buggy (some doesn't show up).

Nullack: Have you managed to test out Fuppes on your 360 yet?

---

### Post by Nullack on 2009-05-16
> **nickwalnut said:**
> Nullack: Have you managed to test out Fuppes on your 360 yet?

I am no longer using the 360 for media streaming and am unfortunately unable to offer support for this. However, other members of the community should be able to assist any people having problems.

---

### Post by Saghaulor on 2009-05-27
> **Jan Ziska said:**
> thanks for this guide, really helpful!

I am also having trouble accessing my photos and music, but it sees my videos just fine.

One thing though, it takes forever to load them. like, 5 minutes to load a 20 minute .avi. I have just started using the wireless connection from the 360, so I think that's the problem. Can anyone confirm if it's wireless, or bugs with the NXE or what...

As previously documented in the thread, wired connections are recommended as most wireless connections experience degraded performance while streaming media.

---

### Post by Saghaulor on 2009-05-27
> **Nullack said:**
> I am no longer using the 360 for media streaming and am unfortunately unable to offer support for this. However, other members of the community should be able to assist any people having problems.

Thanks for the support you did offer.

---

### Post by kkelly on 2009-06-12
Hi there,

My uShare works however sometimes mid film there is a massive slow down unless I pause the film and let it buffer. What could be causing this?

uShare is setting on a 2.8 P4 box with nothing else running?

Thanks Kevin.

---

### Post by bg1256 on 2009-06-13
Everytime the kernel is updated, I need to reinstall. No proble there.

However, when I take the step in the guide that creates the symbolic links that would allow ushare to run on start up, I get

"Symbolic links already exist" (or something very similar to that).

However, ushare is not starting when I boot my machine.

How can I fix this?

---

### Post by bg1256 on 2009-06-13
> **Saghaulor said:**
> As previously documented in the thread, wired connections are recommended as most wireless connections experience degraded performance while streaming media.

I use a wireless connection for my 360 without any problems, FWIW.

---

### Post by Decommissioner on 2009-06-27
> **cruckin said:**
> Alright having troubles of course thats my luck...
it gives me this message
 * Starting uShare UPnP A/V & DLNA Media Server: ushare                         /etc/ushare.conf: 25: string: not found
 * No shares avalaible ...

and i have no doubt it is something im doing 
im running this all wireless so my desktop computer is connected to the internet wireless by the router and same goes for my xbox so im guessing theres a change in eth0 and also i think im getting the directory wrong cause im not sure how to do that i put in /home/desktop/Media 
media is a folder with a few folders in it that has movies and music folders within it help would be great if possible thanks for the guide

I am having this problem as well, except my xbox is connected to the router via ethernet cable

---

### Post by philcamlin on 2009-06-27
cool guide:popcorn:

---

### Post by Randomnocity on 2009-07-16
Maybe I'm stupid and I missed something, which is entirely possible, but something isn't quite right on my box. 

I'm trying to share both movies and music to my xbox. When I boot up my 360 and try to go to Music Library it shows that nothing can be found to stream from my laptop. However, when I go to Video Library, two folders are shown: Music and Videos. My Music folder is broken down further into all of my music as seen on my laptop, but none of them will play (mostly because they are shown as movies when they are mp3 files instead).

What am I doing wrong and how do I fix it?

Edit: Fixed the error with my videos, that was a stupid typo on my part. Still no idea on the Music though.

---

### Post by pendulum101 on 2009-07-18
tried to follow the tutorial as best i could but i'm having trouble when compiling, when i'm trying to get the software that ushare depends on
> laptop:~/src/ushare-1.1a-NeToU$ sudo apt-get build-dep ushare
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Build-dependencies for ushare could not be satisfied.

i'm running jaunty and i'm fairly new to ubuntu so i think that could be my problem
any help would be greatly appreciated

---

### Post by SoulTerror on 2009-07-26
Hey I'm new to the forums and Ubuntu and so far all I've done is install Flash which was really easy. I really want to be able to share my music with my 360 but the steps listed are confusing me. I was doing alright till I got to a point that it said to make a script. I don't know if I'm trying to jump into something that is to far advance for me or what.

---

### Post by bg1256 on 2009-07-27
FWIW,

In Jaunty, the ushare package in the repos works just fine with the 360, at least as far as streaming videos is concerned. I haven't tried music yet, although I never did get music to work in the past.

The only qualifier is that if you install it from the repos, you should run

```
ushare -x
```

to start ushare with 360 compatibility. I added it to my startup applications, and it seems to be working just fine.

---

### Post by SoulTerror on 2009-07-27
I just installed ushare using the command the terminal gave me because I tried putting in the 
ushare -x

command in and it said ushare was not installed. Now that it is, I put in the ushare -x[FONT=monospace]and it says the[/FONT]

Error: no content directory to be shared.

So what am I doing wrong?

---

### Post by bg1256 on 2009-07-27
You have to configure ushare to tell it which directories you want to share.

See the first page of this thread for directions.

The command you will use is:

```
gksudo gedit /etc/ushare.conf
```

---

### Post by SoulTerror on 2009-07-28
Thanks, hope I got it now.

---

### Post by bg1256 on 2009-07-28
After you run the command above, look for this line in the file:

```
USHARE_DIR= 
```

And then enter the directory you want to share.

Mine looks like:

```
USHARE_DIR=/media/Multimedia/TV,/media/Multimedia/Music 
```

---

### Post by Jose Catre-Vandis on 2009-08-05
I am only getting the first directory in the list shared, i.e
```
USHARE_DIR=/media/music,/media/films,/media/television
```
only yields /media/music on the xbox

This is with the ushare from the repos on Xubuntu 9.04

So went down the route of the guide on the [first page]("http://ubuntuforums.org/showthread.php?t=848144&highlight=xbox"). This does work for multiple directories.

Some tips:

1. Make sure you use the configure options or the executable ends up in /usr/local/bin and the conf file in usr/local/etc!

2. "sudo apt-get build-dep ushare" doesn't bring in libupnp-dev so you will need to install this seperately so that configure works properly and libixml is found

3. Make sure XBox Live is running to be able to access any videos you are sharing

4. Mp3s will be a mess, all in one big list, I could only access via "Songs" and if your tags aren't in order......
   I guess you could get round this by sharing lots of directories....

Sharing via upnp with the GeexBox is a breeze compared to this :)

---

### Post by sugargenius on 2009-08-14
all of my movies are x264-encoded with .mp4 extension. I can see them from xbox but they have a slashed circle next to them and I can't play them. Xbox will play them fine from thumbdrive, so it must be Ushare.

I had ushare on my old fileserver and the same files worked fine.

Is there some configuration I need to change in Ushare to make them playable?

---

### Post by twshadow101 on 2009-08-16
Okay, my question is though and I have searched high and low and can't find an answer for this. I installed Fuppes and have it running and and can see it on my Xbox 360, Playstation 3, and everything else. The files and folders show up fine. However, when playing an MP3 it will play for about a minute or two and then the sound will cut off. The timer still keeps counting but there is no sound. Has anyone else had this problem and if so how did you fix it, what can I do? And, I am a noob on sharing content to an Xbox or Playstation so please explain in detail how to do this.

---

### Post by Matthaeus on 2009-10-01
> **Jose Catre-Vandis said:**
> I am only getting the first directory in the list shared, i.e
```
USHARE_DIR=/media/music,/media/films,/media/television
```
only yields /media/music on the xbox

This is with the ushare from the repos on Xubuntu 9.04


For anyone else facing this problem, you can use simple soft link to overcome it.

I created a folder called ushare and then placed symbolic/soft links to my tv & movie folders (which i wanted to share) within it. 

eg
> 
ln -s /media/raid/tv     /media/ushare
ln -s /media/raid/movies /media/ushare
(ln -s /original/folder /new/link soft link for folders)

then set USHARE_DIR=/media/ushare

works a treat.

Cheers.

---

### Post by s1500 on 2009-10-13
Sadly, when I upgraded to 9.04, Fuppes stopped working entirely. When I Fuppes' latest build, it complains that it cannot find some libavformat file. 

I, for the life of me cannot install this library that Fuppes needs. When I get back home(I'm at work now), I'll post the name of the essential file. 

But I think I will give uShare another try. Currently I'm using x360mediaserve, which so far does music, but I have not tried videos & pictures.  Sadly, I was not able to get it to start every time Linux starts, regardless of my tries in Webmin to get a startup going.

I really wish streaming media to the Xbox 360 wasn't such a mess. We have several different packages with overlapping features, but none can fulfill them all. My absolute last resort is to get a VirtualBox image of XP up & share all media through that.

---

### Post by aeronutt on 2009-10-15
I just found this last night, works great so far for music and pics (wireless to router to XBOX360). Seems they've just recently added xbox360 support, informally. Java based so there's no install, easy to use. Haven't tried video yet. There does seem to be a bug with refreshing the file list and how it's shown on xbox, but once everything is stable (directories are selected, server started, etc.), it seems pretty stable. Played music and displayed pics for a few hours with no interruption.

[http://code.google.com/p/ps3mediaserver/](http://code.google.com/p/ps3mediaserver/)

---

### Post by yester64 on 2009-10-18
i would have a question not regarding installation, but security.
Will streamed content transmited to microsoft? This is hinted with the mediacenter.
My buttomline question is, will it be save to watch my movies?:confused:

---

### Post by swiss_mister on 2009-10-19
Hi

Just something I noticed. I'm running Linux Mint, performed the standard install like everyone, edited my .conf file - blah blah. Before I knew it, I was successfully streaming video to my xbox elite, completely wireless from the 2nd floor to the basement (where the router is) and then back to the xbox on the main floor. 

Having different media types (.avi, .mpg, etc), I noticed that everytime I watched a divx / .avi file, I never had any connection issues.  The only time I did have problems was when I was streaming .mkv format and/or mpeg. Occasionally it would just stall and then I could not access the files again until I rebooted my linux box.. 

So, based on my conclusions.. so far - Divx/avi proves to be reliable for me. I can watch numerous movies successive .. and completely wireless without any issue but once I change formats.. it craps out. I was thinking of changing my network to use cat5 throughout but I suppose there is no need if I tend to only watch Divx/avi through this means. 

Just my two cents..

..SM

---

### Post by yester64 on 2009-10-22
Hi, if i check with 
sudo ufw status
i get told its inactive.

But i used this command and it supposed to start automatically
sudo update-rc.d ushare defaults
Did i do something wrong? Or do you have to this als root. Did not solve my problem either. I tried already.

---

### Post by maldonsailor on 2009-10-23
Thanks for this really great guide.  But I am having trouble accessing the web interface: I have followed what the guide says I should be doing, sworn, and beat my head on the coffee table.  What am I doing wrong? Please help this terminal noob (in both senses, ho-ho)  Every time I try to access it through my web browser it just says it can't find the page.

---

### Post by yester64 on 2009-11-03
Hi,
i was just wondering if someone knows if thats a xbox problem or a ushare.
In my share folder are movies and pictures. One folder of pictures gets displayed, but another not. But here is the twist. The content will show up in the movie selection from the xbox.
Isnt that weird. Not sure how i can tell the xbox that those are pictures and not movies.

here is my structure

sdb1 > mount as media > 1 folder movies 
                                      2 folder pictures > 1 folder gets displayed
                                                                  2 folder not, but shows up if displayed as movies.

The files are just regular jpg files. So nothing special really.

---

### Post by yester64 on 2009-11-08
Hi,
i have some problems with sharing.
For some reason some folders can be read and others not.
I used softlinks to link my main folders where every other folder is located. But some folder with images can be read. So strange. Is it the xbox by any chance or is it ushare?

---

### Post by BeatnikBandit on 2010-03-10
Hello and thank you soooo much for this guide as it is the only thing i want to do that is not available via synaptic, now I have dabbled with ubuntu and *nix in general for years although I am not expert although your guide is very basic and easy to follow. now here is my problem i did everything on your guide and ushare even says it starts and its [ok] although i am unable to check it out via the web interface?? IDK what my problem is I know what ip this computer is as i checked it on my router page to be sure so in my case the web interface should be [HTML]http://192.168.1.2:49200/web/ushare.html[/HTML] although every time i try this Firefox tells me it cannot connect? As it does when you type an address that does not exist. I checked and i am not running ufw i checked the status and it said it is inactive. Am i missing something??? here is my Ushare.conf file is it correct????
```

# /etc/ushare.conf
# Configuration file for uShare

# uShare UPnP Friendly Name (default is 'uShare').
USHARE_NAME=LinuxMedia

# Interface to listen to (default is eth0).
# Ex : USHARE_IFACE=eth1
USHARE_IFACE=

# Port to listen to (default is random from IANA Dynamic Ports range)
# Ex : USHARE_PORT=49200
USHARE_PORT=49200

# Port to listen for Telnet connections
# Ex : USHARE_TELNET_PORT=1337
USHARE_TELNET_PORT=

# Directories to be shared (space or CSV list).
# Ex: USHARE_DIR=/dir1,/dir2
USHARE_DIR=/home/matthew/Videos,/mnt/video

# Use to override what happens when iconv fails to parse a file name.
# The default uShare behaviour is to not add the entry in the media list
# This option overrides that behaviour and adds the non-iconv'ed string into
# the media list, with the assumption that the renderer will be able to
# handle it. Devices like Noxon 2 have no problem with strings being passed
# as is. (Umlauts for all!)
#
# Options are TRUE/YES/1 for override and anything else for default behaviour
USHARE_OVERRIDE_ICONV_ERR=

# Enable Web interface (yes/no)
USHARE_ENABLE_WEB=yes

# Enable Telnet control interface (yes/no)
USHARE_ENABLE_TELNET=no

# Use XboX 360 compatibility mode (yes/no)
USHARE_ENABLE_XBOX=yes

# Use DLNA profile (yes/no)
# This is needed for PlayStation3 to work (among other devices)
USHARE_ENABLE_DLNA=
```i have yet to check and even see if my xbox is working with ushare as i have no media yet to test it with. so with this information. First is there anything else needed? What could i have done wrong? ANY HELP would be GREATLY appreciated. This is the ONE thing that will get me non Micro$oft dependent as Tversity was something I used daily pretty much a computer geeks tivo. So Thanks in advance to anyone who can help me with this issue or if it is actually a real issue or not?

I Really Hope To Fix This,  thanks guys/gals

---

### Post by otkaz on 2010-03-11
you need to configure which interface to run ushare on USHARE_IFACE="interface name here" if you are sharing from a ethernet nic its probably eth0 if you are connecting to your network with wifi it depends on the card as to what linux named that interface type iwconfig in terminal or ifconfig to view your network interfaces.

---

### Post by dannyboy79 on 2010-05-10
this is awesome BUT the only thing is that there is still no real interface to my mythtv backend. I can autotranscode the .mpg recordings into avi and watch them from xbox 360 but can't delete them, schedule new recordings or anything like that from the 360. I will still keep the original xbox for awhile. of course all the great python apps for xbmc also. 

a question, anyone know of a rock solid ffmpeg or mencoder sytanx for keeping the quality of my .mpg files but converting them to .avi and trimming them a little. example: a 30 hour show is 1.1 GB, i used winff to convert it to an avi and chose fullscreen xvid and the quality was junk. I dfo have the latest ffmpeg installed also. I used a script that got the source from svn I think and compiled it for me.

---

### Post by jazzersaxman on 2010-05-26
After reading the guide and the pages, I am wondering how to use external drives (1.5TB drive) connected to my ubuntu via ushare?  the xbox 360 sees the machine but says there are no videos, pics, etc.  Not sure how to tweak it?

Thanks...

---

### Post by dannyboy79 on 2010-05-28
> **jazzersaxman said:**
> After reading the guide and the pages, I am wondering how to use external drives (1.5TB drive) connected to my ubuntu via ushare?  the xbox 360 sees the machine but says there are no videos, pics, etc.  Not sure how to tweak it?

Thanks...

is the external drive mounted anywhere within your ubuntu install? like maybe /media/external_drive/  as an example? then you would just tell ushare to share that folder. 

here's my ushare.conf line for sharing folders from my media server.

USHARE_DIR=/media/500gb/new_movies,/media/fat32/movies,/media/500gb1/tv_shows,/media/500gb1/movies

---

### Post by jazzersaxman on 2010-05-31
> **dannyboy79 said:**
> is the external drive mounted anywhere within your ubuntu install? like maybe /media/external_drive/ as an example? then you would just tell ushare to share that folder. 
 
here's my ushare.conf line for sharing folders from my media server.
 
USHARE_DIR=/media/500gb/new_movies,/media/fat32/movies,/media/500gb1/tv_shows,/media/500gb1/movies
 
It appears as a mounted drive on the desktop...I have added the appropriate directories, but it won't work...the only way I was able to have it find the files on the drive was to open "shortcut" links to the folders on the drive...very weird...
 
Now I can't get it to play any of my music files...only pics and video...not too thrilled about ushare right now...

---

### Post by dannyboy79 on 2010-06-02
ushare doesn't play ANY files, it only shares them out via UPnP and DLNA. please paste your conf file at pastebin and post the link here. you have something incorrect. this is definitely not as hard as you're making it. I am sure it's nothing you did you just may have a funked up conf file somehow. also post your fstab and mount commands so I can see how you mounted your external drives.

---

### Post by andoni on 2010-07-08
I get an error when trying to compile it:

```
andoni@ubuntu:~/src/ushare-1.1a$ ./configure --prefix=/ --bindir=/usr/bin --mandir=/usr/share/man
Unknown option "--mandir=/usr/share/man".
See ./configure --help for available options.
```

What am I doing wrong?

---

### Post by dannyboy79 on 2010-07-09
it's possible that that option is no longer valid with newer source files. did you you do as suggested and look at ./configure --help?

---

### Post by andoni on 2010-07-09
EDIT: Ok, problem solved, I've just used an older source. But, my xbox only recognizes the songs, not the genres, albums, bands, etc. Oh, and now the number of songs is limited to 500.

---

### Post by wlraider70 on 2010-07-17
My xbox360 does not seem to be finding ANYTHING.
I have checked both for a "PC" and for "media center". im not even sure where it supposed to be found...

I installed the long way from binaries.


When i go to [http://10.10.10.2:49200/web/ushare.html](http://10.10.10.2:49200/web/ushare.html) it works

it says

```


uShare UPnP A/V Media Server
Information Page

Version : 1.1a-NeToU
Device UDN : 898f9738-d930-4db4-a3cf-00112f54dec4
Number of shared files and directories : 10126


```


```

luke@media:~$ sudo ushare
uShare (version 1.1a-NeToU), a lightweight UPnP A/V and DLNA Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See http://ushare.geexbox.org/ for updates.
Initializing UPnP subsystem ...
Starting in XboX 360 compliant profile ...
UPnP MediaServer listening on 10.10.10.2:49200
Sending UPnP advertisement for device ...
Listening for control point connections ...
Building Metadata List ...
Looking for files in content directory : /home/luke/Pictures
Looking for files in content directory : /media/dump
Found 10126 files and subdirectories.



```

my set up looks like this.

```
# /etc/ushare.conf
# Configuration file for uShare

# uShare UPnP Friendly Name (default is 'uShare').
USHARE_NAME=ushare

# Interface to listen to (default is eth0).
# Ex : USHARE_IFACE=eth1
USHARE_IFACE=eth0

# Port to listen to (default is random from IANA Dynamic Ports range)
# Ex : USHARE_PORT=49200
USHARE_PORT=49200

# Port to listen for Telnet connections
# Ex : USHARE_TELNET_PORT=1337
USHARE_TELNET_PORT=

# Directories to be shared (space or CSV list).
# Ex: USHARE_DIR=/dir1,/dir2
USHARE_DIR=/home/luke/Pictures,/media/dump

# Use to override what happens when iconv fails to parse a file name.
# The default uShare behaviour is to not add the entry in the media list
# This option overrides that behaviour and adds the non-iconv'ed string into
# the media list, with the assumption that the renderer will be able to
# handle it. Devices like Noxon 2 have no problem with strings being passed
# as is. (Umlauts for all!)
#
# Options are TRUE/YES/1 for override and anything else for default behaviour
USHARE_OVERRIDE_ICONV_ERR=

# Enable Web interface (yes/no)
USHARE_ENABLE_WEB=yes

# Enable Telnet control interface (yes/no)
USHARE_ENABLE_TELNET=no

# Use XboX 360 compatibility mode (yes/no)
USHARE_ENABLE_XBOX=yes

# Use DLNA profile (yes/no)
# This is needed for PlayStation3 to work (among other devices)
USHARE_ENABLE_DLNA=yes


```

---

### Post by wlraider70 on 2010-07-17
fixed it.

sorry not totaly sure what I did.

One point for trouble shooting, I did find.

the connection port seems to rotate between 49200, 49201, and 49202


If you can use another networked box to go to...
http://<serving box IP:4920X/web/ushare.html

if that works then the problem should be on the xbox side.
I messed with IPs


For future referenced I am using the new Xbox "slim" 250 GB black with built in wireless N. 

It is working perfectly, except the meta data seems to be messed up...

---

### Post by andoni on 2010-07-29
Is there a fix to the 500 limit problem?

---

### Post by andoni on 2010-08-08
> **andoni said:**
> Is there a fix to the 500 limit problem?
Anyone?

---

### Post by dannyboy79 on 2010-08-09
am not aware of any 500 limit problem. my collection of avi files is over 1500, that's just movies. i have who knows how many tv shows also. I can see them all. then again i have sub-folders so maybe thats why. whats the problem?

---

### Post by andoni on 2010-08-09
> **dannyboy79 said:**
> am not aware of any 500 limit problem. my collection of avi files is over 1500, that's just movies. i have who knows how many tv shows also. I can see them all. then again i have sub-folders so maybe thats why. whats the problem?
Ok, now I've just noticed that I can play my entire music library when I'm on the interface, but when I'm playing a game, I can only play the first 500 tracks on my library.

---

### Post by dannyboy79 on 2010-08-12
oh, i don't play music much so i was unaware of the problem. can't help sorry.

---

### Post by metaltroubador on 2010-08-13
I'm able to get the xbox to detect my computer. But get it to detect any of the files in the specified folders my .conf file looks like this

# /etc/ushare.conf
# Edit this file with 'dpkg-reconfigure ushare'
# Configuration file for uShare

# uShare UPnP Friendly Name (default is 'uShare').
USHARE_NAME=Desktop

# Interface to listen to (default is eth0).
# Ex : USHARE_IFACE=eth1
USHARE_IFACE=wlan0

# Port to listen to (default is random from IANA Dynamic Ports range)
# Ex : USHARE_PORT=49200
USHARE_PORT=49200

# Port to listen for Telnet connections
# Ex : USHARE_TELNET_PORT=1337
USHARE_TELNET_PORT=1337

# Directories to be shared (space or CSV list).
# Ex: USHARE_DIR=/dir1,/dir2
USHARE_DIR=/home/kyle/videos/Movies

# Use to override what happens when iconv fails to parse a file name.
# The default uShare behaviour is to not add the entry in the media list
# This option overrides that behaviour and adds the non-iconv'ed string into
# the media list, with the assumption that the renderer will be able to
# handle it. Devices like Noxon 2 have no problem with strings being passed
# as is. (Umlauts for all!)
#
# Options are TRUE/YES/1 for override and anything else for default behaviour
USHARE_OVERRIDE_ICONV_ERR=

# Enable Web interface (yes/no)
USHARE_ENABLE_WEB=yes

# Enable Telnet control interface (yes/no)
USHARE_ENABLE_TELNET=no

# Use XboX 360 compatibility mode (yes/no)
USHARE_ENABLE_XBOX=yes

# Use DLNA profile (yes/no)
# This is needed for PlayStation3 to work (among other devices)
USHARE_ENABLE_DLNA=no

The directory I specified has many different videos in many different file types but my 360 says it doesn't detect any videos. Am I missing something?

---

### Post by H3LTerSK3LTer on 2010-08-18
I have the same problem, my xbox sees my computer but none of the directories are showing up.  I'm running ubuntu 10.04 and I checked my firewall turned it off still not finding anything. 

I set my directories up as 
/Videos,/Music

Whoever encountered this issue and was able to get by it let me know.  Many will be grateful for your awesomeness.

---

### Post by H3LTerSK3LTer on 2010-08-19
haha nevermind, didn't mean to keep everyone in suspense but all I needed to do was restart my computer so that problem was solved.  My xbox sees my songs, but it still wont read group them by artist or album.  It is very annoying but it is what it is until I can figure out how to fix it.

---

### Post by phazixc on 2011-03-09
lol


After some hours I came up with this.,.... and its quick and easy


download xbmc...  you can install it from the "Tweak Ubuntu" software program...

once install --- system-----network---service--

select---- share videos and music upnp

NOW THATS DONE YOUR XBOX360 CAN SEE YOUR UBUNTU IT'LL SHOW AS 

XBMC: MEDIA SEVER ON YOUR XBOX360

now

install samba if you dont know how to google it, its simple or type it in the software center.

now

what I did was add the folders which i want sharing in samba with a username and password and only visable...

then on the folder its self right click it and share the folder..

then in xbmc... add the music folder source from the smp area (i.e on the network) 

what it does then is asks for a username and password which you enter and selected remember...

once thats done right click in xbmc on the music folder you just added and tell it to scan into your lib....

once completed you'll find all your music pops up no problem on your xbox 360


good luck

---

### Post by donniezazen on 2011-03-10
> **phazixc said:**
> lol


After some hours I came up with this.,.... and its quick and easy


download xbmc...  you can install it from the "Tweak Ubuntu" software program...

once install --- system-----network---service--

select---- share videos and music upnp

NOW THATS DONE YOUR XBOX360 CAN SEE YOUR UBUNTU IT'LL SHOW AS 

XBMC: MEDIA SEVER ON YOUR XBOX360

now

install samba if you dont know how to google it, its simple or type it in the software center.

now

what I did was add the folders which i want sharing in samba with a username and password and only visable...

then on the folder its self right click it and share the folder..

then in xbmc... add the music folder source from the smp area (i.e on the network) 

what it does then is asks for a username and password which you enter and selected remember...

once thats done right click in xbmc on the music folder you just added and tell it to scan into your lib....

once completed you'll find all your music pops up no problem on your xbox 360


good luck

Didn't work for me. I have tried both ushare and xbmc method but xbox kinect fails to recognize my ubuntu.

---

