---
title: "Howto: Install Citrix 9 Under Breezy"
date: 2005-11-02
forum: Outdated Tutorials &amp; Tips
---

### Post by Technoviking on 2005-11-02
1. Download Citrix 9.0 client for Linux (RPM version):  
[http://www.citrix.com/site/SS/downloads/details.asp?dID=2755&downloadID=3323#top](http://www.citrix.com/site/SS/downloads/details.asp?dID=2755&downloadID=3323#top)

2. Install addtional libraries: 
```
apt-get install libxaw6 libmotif3
```
3. Link libXm.so.3 so wfcmgr.bin can see it (bug in Citrix client):
```
ln -s /usr/X11R6/lib/libXm.so.3 /usr/lib/libXm.so.3
```
4. Convert .rpm to .deb using alien command: 
```
sudo alien ICAClient-9.0-1.i386.rpm
``` 
5. Install newly created icaclient_9.0-2_i386.deb file: 
```
sudo dpkg -i icaclient_9.0-2_i386.deb
```
6. Copy over plugins for Firefox/Mozilla:
```
sudo ln -s /usr/lib/ICAClient/npica.so /usr/lib/mozilla/plugins/npica.so 
sudo ln -s /usr/lib/ICAClient/npica.so /usr/lib/mozilla-firefox/plugins/npica.so
``` 

You may have to do the following if using older Citrix Server
1. Configure ICAClient:
```
sudo /usr/lib/ICAClient/wfcmgr -icaroot /usr/lib/ICAClient
``` 
2. Goto the Tools menu and choose settings. 

3. Select Server Location from the selection bar. 

4. Goto Network Protocol selection bar and change it to TCP/IP and click the Apply button.

---

### Post by LaserJock on 2005-11-02
Cool How-To! I use the citrix client quite a bit at my university and it is nice to be able to have access to it from linux. I had figured out how to alien the rpm's but it didn't realize that there were plugins for firefox. That is really cool.

-LaserJock

---

### Post by tncmmngs on 2005-11-25
"sudo apt-get  install libmotif3" returns error "Couldn't find packge libmotif3"

my sources.list:
> deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe


I think I'm overlooking something obvious...any help would be appreciated.

FYI. I resolved this error by replacing the sources.list file with the one posted at [http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

---

### Post by andlinux21 on 2005-11-25
wow I am lovin these howto's I need to collect my favorite ones and put them together in a book so that I can share with my classmates.

---

### Post by greythorne on 2005-11-26
ok great, now that i got citrix installed, how do i configure it in linux so that i will be able to access lotus notes from home? i am able to access lotus notes from home using a windows OS. btw lotus notes is at work, but i want to access it from home.

thnx

---

### Post by Eazy© on 2005-11-26
[QUOTE=greythorne]ok great, now that i got citrix installed, how do i configure it in linux so that i will be able to access lotus notes from home? i am able to access lotus notes from home using a windows OS. btw lotus notes is at work, but i want to access it from home.

thnx[/QUOTE]

You need to set you colors to atleast 16 million.

---

### Post by kaaredyret on 2005-11-30
I just installed the client from the citrixc website, found a required certificate and I could connect.

Danish characters, however, are not supported? I get a US keyboard and cant use my citrix connection because of this. From Windows it works perfectly.

Whats wrong?

---

### Post by jonejone on 2005-12-12
Hi Mike,

More than a Citrix Client Bug, isn't it a problem with /etc/ld.so.conf? This file does not exist in Ubuntu, but after creating it with 

$ cat /etc/ld.so.conf
/lib/
/usr/lib/
/usr/local/lib/
/usr/X11R6/lib/

and running ldconfig, it works perfectly.

JoneJone

---

### Post by trigg3r on 2005-12-12
Awesome HOW-TO! I had thought that Citrix would never work on Firefox after I installed the rpm. Apparently, there are FF plugins that I missed.

A gazillion thanks!

---

### Post by mrchadman on 2006-01-25
I got this error when trying to install the citrix client:

[I]
sudo apt-get install libxaw6 libmotif3
Reading package lists... Done
Building dependency tree... Done
libxaw6 is already the newest version.
The following NEW packages will be installed:
  libmotif3
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/1219kB of archives.
After unpacking 3039kB of additional disk space will be used.

Preconfiguring packages ...
(Reading database ... 65770 files and directories currently installed.)
Unpacking libmotif3 (from .../libmotif3_2.2.3-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libmotif3_2.2.3-1_i386.deb (--unpack):
 trying to overwrite `/usr/X11R6/include/X11/bitmaps/xm_error', which is also in package openmotif
Errors were encountered while processing:
 /var/cache/apt/archives/libmotif3_2.2.3-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/I]


[/I]

---

### Post by jgrantham on 2006-01-25
I followed your instructions to the letter adn it prompts me what to do with the file when I try to access Citrix through the internet. Any ideas? No errors, just asks me what to do with it.

---

### Post by AirIntake on 2006-01-28
Yeah, i have the same problem. What do I open the file with, or what do I do?

---

### Post by Xenguy on 2006-01-30
[QUOTE=jgrantham]I followed your instructions to the letter adn it prompts me what to do with the file when I try to access Citrix through the internet. Any ideas? No errors, just asks me what to do with it.[/QUOTE]

Same here, but I found a solution.  In my case I got a pop-up for file 'launch.asp' that defaulted to 'open with gedit'; obviously this was not correct.

The solution that worked for me (going from memory now, as it is no longer in front of me) was to choose 'other' and navigate to the following file:
   /usr/lib/ICAClient/wfica.sh
So now instead of 'gedit', the field displays 'wfica.sh' (no quotes).  I then clicked 'OK' and Citrix was up and running.

HTH...

---

### Post by AirIntake on 2006-01-31
Thank you very much! That did it!

---

### Post by rastamufasta on 2006-01-31
I installed manually with setupwfc - I couldn't convert the rpm to a .deb package with my amd64 arch.  I had to make some symbolic links for libXt.so and libXext.so to get firefox to run, but I'm still getting this error each time I start firefox:

LoadPlugin: failed to initialize shared library /usr/lib/ICAClient/npica.so [/usr/lib/ICAClient/npica.so: cannot open shared object file: No such file or directory]

npica.so is in /usr/lib/ICAClient and in /usr/lib/mozilla-firefox/plugins/

Any ideas?

I also tried manually opening with wfica.sh, but no luck there either.

Thanks

---

### Post by thepeel on 2006-02-02
I'm having problems with my Citrix client just failing. This is what happens:

jbp@ubu:/usr/lib/ICAClient$ ./wfica -file ~/portal.ica
Warning: Missing charsets in String to FontSet conversion
Warning: Unable to load any usable fontset
*** glibc detected *** double free or corruption (top): 0x082dd9e0 ***
Aborted

This happens with the source release as well as the rpm release as well as both the English and German versions. I noticed I think one other instance on these forums of the same problem. Nothing was really said about it though.

---

### Post by ericsp on 2006-02-05
With the help of this howto, I almost got there. One issue remains:
[CENTER]Citrix ICA Client ERROR
You have not chosen to trust "GlobalSign Root CA", the issuer of the server's security certificate.[/CENTER]

How to solve this?

Eric

---

### Post by nlogax on 2006-03-11
[QUOTE=ericsp]With the help of this howto, I almost got there. One issue remains:
[CENTER]Citrix ICA Client ERROR
You have not chosen to trust "GlobalSign Root CA", the issuer of the server's security certificate.[/CENTER]

How to solve this?

Eric[/QUOTE]

To tell the Citrix ICA client to trust GlobalSign, you need a certificate from GlobalSign in .DER format.  You can obtain this by downloading and saving GlobalSign's  root certificate from [here](http://www.globalsign.net/securedby/checkhttp://ubuntuforums.org/newreply.php?do=newreply&p=708132/index.cfm).

Once you've saved it, you just need to copy it to the Citrix ICA client keystore.

To do this, simply type:

  sudo cp root.cacert /usr/lib/ICAClient/keystore/cacerts/globalsign.crt

(assuming you installed the ICA client to the default location)

Now try using Citrix again.

---

### Post by Kubuntu_Newbie on 2006-03-15
re: "sudo apt-get install libmotif3" returns error "Couldn't find packge libmotif3"

libmotif3 is only available in the Apt multiverse

Add the following to /etc/apt/sources.list for Breezy.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

Perhaps the HowTo could be amended to mention this.

---

### Post by robin.shepheard on 2006-03-16
[QUOTE=rastamufasta]

LoadPlugin: failed to initialize shared library /usr/lib/ICAClient/npica.so [/usr/lib/ICAClient/npica.so: cannot open shared object file: No such file or directory]

npica.so is in /usr/lib/ICAClient and in /usr/lib/mozilla-firefox/plugins/

[/QUOTE]

Daft question but have you checked file permissions. I had a similar error message for another program I installed and it turned out I had installed it using sudo but when I tried to run it I was only my standard user. Changed file permissions with chmod a+x and the problem disappeared.

Cheers

Robin

---

### Post by fastpakr on 2006-03-25
> I installed manually with setupwfc - I couldn't convert the rpm to a .deb package with my amd64 arch. I had to make some symbolic links for libXt.so and libXext.so
Can you explain this a bit further?  I got this far in the walkthrough, but got multiple errors on the .deb conversion (AMD64/3000).  I'm VERY new to Linux, so sometimes it takes me a few times reading through these things to follow everything.  I do IT work on the Windoze side, but Linux is a new world I never got around to experiencing until the last few weeks.

---

### Post by CliffA on 2006-06-12
[QUOTE=Mike]
3. Link libXm.so.3 so wfcmgr.bin can see it (bug in Citrix client):
```
ln -s /usr/X11R6/lib/libXm.so.3 /usr/lib/libXm.so.3
```
[/QUOTE]

I'm having a problem with this step. The ln command, above implies the motif library was installed in /usr/X11R6/lib, and a link to it is needed in /usr/lib. However, after I did apt-get install libmotif, the library was installed by apt in /usr/lib. Nothing went into /usr/X11R6/lib.

When I tried running the ICA client, it told me it couldn't load libXm.so.3, so I tried the opposite ln command, "ln -s /usr/lib/libXm.so.3 /usr/X11R6/lib/libXm.so.3". This did not fix the problem.

---

### Post by nlogax on 2006-06-12
In case anyone's interested in creating a file association for .ICA files so that Epiphany can launch them automatically, here's how you do it:

Creating MIME types for Citrix ICA Client

1. Create new file /usr/share/applications/wfica.desktop

[Desktop Entry]
Name=Citrix ICA client
GenericName=Citrix ICA Client
Comment=Citrix nFuse session file
Categories=Application
Encoding=UTF-8
Exec=/usr/lib/ICAClient/wfica -icaroot /usr/lib/ICAClient
Icon=wfica
Terminal=false
Type=Application
MimeType=application/x-ica

2. Create new file /usr/share/mime/packages/ica.xml

<?xml version="1.0" encoding="utf-8"?>
<mime-info xmlns="http://www.freedesktop.org/standards/shared-mime-info">
  <mime-type type="application/x-ica">
    <comment>Citrix ICA launcher</comment>
    <glob pattern="*.ica"/>
  </mime-type>
</mime-info>

3. sudo update-desktop-database && sudo update-mime-database /usr/share/mime

To allow Epiphany to run launch the client automatically when you are running a Citrix Web Interface/nFuse server, you must also do this:

4. File /usr/share/epiphany-browser/mime-types-permissions.xml

  Add the following line to the <safe> section:
  <mime-type type="application/x-ica"/>

---

### Post by filippod on 2006-11-02
I have Edgy (Ubuntu 6.10), Firefox 2.0 and the english Ica client 9.0.
I installed everything and apparently everything went fine but:
[LIST]
[*]When I click on an application icon in NFuse Firefox asks me what it should use to open it
[*]If I choose "/usr/lib/ICAClient/npica.so" nothing happens
[*]If I choose "/usr/lib/ICAClient/wfica.sh" I get the following certificate error: [Citrix ICA Client Error: You have chosen not to trust "/C=US/ST=L=O=Equifax=OU=Equifax Secure Certificate Authority/CN=", the issuer of the server certific]
[*]Please note that if I check the certificate of the website I click the ICA link from, it says that I trust it
[/LIST]


Can anybody help? 
Thanks in advance.

---

### Post by nlogax on 2006-11-02
> **filippod said:**
> 
[*]If I choose "/usr/lib/ICAClient/wfica.sh" I get the following 


^^^^^ This is the correct one.

> 
certificate error: [Citrix ICA Client Error: You have chosen not to trust "/C=US/ST=L=O=Equifax=OU=Equifax Secure Certificate Authority/CN=", the issuer of the server certific]

Yes, you simply need to obtain the root certificate for Equifax somehow, and then copy it to /usr/lib/ICAClient/keystore/cacerts

Your browser may already trust Equifax, however the Citrix client ships with an entirely separate set of root certificates to what your browser comes with.

---

### Post by filippod on 2006-11-02
Hello, I made it! I was coming to post the solution when I found your answer.

> Yes, you simply need to obtain the root certificate for Equifax somehow, and then copy it to /usr/lib/ICAClient/keystore/cacerts

If anybody else needs it: I obtained the certificate from here: [http://www.geotrust.com/resources/root_certificates/index.asp]("http://www.geotrust.com/resources/root_certificates/index.asp")

This is important: I had to change the certificate extension from .cer to .crt and then it worked. I noticed that all the certificates you download come with a .cer extension but for ICA to work a .crt extension is needed.

Thanks for the timely reply. I'm tired but happy!

---

### Post by uzd4ce on 2006-11-19
Thanks for the tutorial.  Worked for me on the first try.

---

### Post by Glenhawk on 2006-11-21
Aside from some basic command line Unix use in University, Ubuntu is my first venture into a non-microsoft world and I have only been here since last weekend... on to the question...

I have followed this how-to and have gotten almost to the end. I now try to launch the ICA and firefox asks me what to open it with. I try to open it with wfica.sh BUT then I get a message saying:

> Cannot read file:
    "/home/username/.ICAClient/wfclient.ini"

I have located wfclient.ini in ICAClient/config and as far as I can tell /home/username/.ICAClient/ does not exist. Do I need to alter a line in an executable, config or something?

I am running ubuntu 6.10 edgy eft not breezy but from what I have found elsewhere on the net this shouldn't matter (but hey, 4 days experience does not an expert make!)

Thanks in anticipation,
Glen

---

### Post by Nomen Nescio on 2007-02-18
Hi, i am working under Dapper and had exactly the same 
[PHP]cannot read wfclient.ini[/PHP]
problem, and cured it with:
$ sudo chown -R username.username /home/username/.ICAClient/
Found it somewhere on the net. It works find now. Succes!

---

### Post by nlogax on 2007-02-28
Citrix have now released version 10 of the Linux client, and you can get it [here](http://www.citrix.com/site/SS/downloads/details.asp?dID=2755&downloadID=3323#top), however I've not been able to get it to work yet.

Has anyone tried it, and if so, did you have any success?

---

### Post by HolyIbanez on 2007-03-20
I have installed Citrix 10 in Breezy.

My steps:

Download Tar file to $location

sudo apt-get install libmotiff3

cd $location
mkdir citrix
##This does not untar nicely, if there is anything else here, you might have problems, so I move it to another dir.
mv en.linuxx86.tar.gz ./citrix

cd ./citrix
tar -zxvf en.linuxx86.tar.gz
sudo ./setupwfc

Then, read the /usr/lib/ICAClient/readme.txt for changes you need to make to a file so that this will work with Ubuntu/Debian.

Once you are done, verify with /usr/lib/ICAClient/wfcmgr

This should work.

My problems is as follows: (/usr/lib/firefox/plugins/npica.so)smdavis@alexiea:~$ firefox
LoadPlugin: failed to initialize shared library /usr/lib/ICAClient/npica.so [/usr/lib/ICAClient/npica.so: undefined symbol: XtWindowToWidget]
LoadPlugin: failed to initialize shared library /usr/lib/ICAClient/npica.so [/usr/lib/ICAClient/npica.so: undefined symbol: XtWindowToWidget]
** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)


Anyone have any ideas?

---

### Post by HolyIbanez on 2007-03-20
Ok, I checked out the Gentoo forums (I run gentoo on my desktop, Ubuntu on the laptop) I got the following idea:

[email]smdavis@alexiea:~/.mozi[/email]lla/firefox$ cat rc
export LD_PRELOAD=libXt.so.6

Which works, sort of...  I get a new error...

Warning: Missing charsets in String to FontSet conversion
Warning: Unable to load any usable fontset
Error: Aborting: no fontset found

---

### Post by HolyIbanez on 2007-03-20
HA HA HA HA!  Ok, there is a number of problems with Ubuntu and Citirx.

After you followed my instructions, and put in that little rc hack, you need to run:

xset fp rehash

And you are GOLDEN!

Supposedly this is fixed in fiesty...

---

### Post by aliennet on 2007-03-21
Hi,
I've "only" this problem:
LoadPlugin: failed to initialize shared library /usr/lib/ICAClient/npica.so [/usr/lib/ICAClient/npica.so: undefined symbol: XtWindowToWidget]
LoadPlugin: failed to initialize shared library /usr/lib/ICAClient/npica.so [/usr/lib/ICAClient/npica.so: undefined symbol: XtWindowToWidget]

No way to have citrix working.This mornign when I read the HolyIbanez's post I was so full of hope!

Could you explain me this tip:
[email]smdavis@alexiea:~/.mozi[/email]lla/firefox$ cat rc
export LD_PRELOAD=libXt.so.6

It give me an error.
Thanks

---

### Post by HolyIbanez on 2007-03-21
I cat'd my RC file for firefox.

So, as yourself, run the following command:

echo "export LD_PRELOAD=libXt.so.6" >> ~/.mozilla/firefox/rc

That should do it for you.

I'm still investigating to see if a symlink will resolve this, meaning it will fix it for the system and not just the user who runs the above (and the above will not be needed, if I can get this to work), but this is a nice workaround.

---

### Post by aliennet on 2007-03-23
> **HolyIbanez said:**
> I cat'd my RC file for firefox.

So, as yourself, run the following command:

echo "export LD_PRELOAD=libXt.so.6" >> ~/.mozilla/firefox/rc

That should do it for you.

I'm still investigating to see if a symlink will resolve this, meaning it will fix it for the system and not just the user who runs the above (and the above will not be needed, if I can get this to work), but this is a nice workaround.

Many thanks!
I'm working around this issue from a couple of weeks but no way to find a solution.
I did it.
Now I have this error:
Warning: Missing charsets in String to FontSet conversion
Warning: Unable to load any usable fontset
Error: Aborting: no fontset found

I've just made 
xset fp rehash

But I feel close to solution!

---

### Post by HolyIbanez on 2007-03-23
You will have to run the xset again.

Read the readme file for citrix, there is a section about debian/ubuntu, remove the lines it tells you, then the last remaining font line, remove the \; and replace with a :

Then run the xset.

---

### Post by aliennet on 2007-03-24
Hi,
  I've done every single step. But I'm still having the same problem.
I check these two website:
->[https://launchpad.net/ubuntu/+source/xfontsel/+bug/35330](https://launchpad.net/ubuntu/+source/xfontsel/+bug/35330)
->[http://support.citrix.com/forums/thread.jspa?forumID=16&threadID=86630](http://support.citrix.com/forums/thread.jspa?forumID=16&threadID=86630)
I ran xset fp rehash various times.
I'm running an Ubuntu Edgy upgraded from Dapper so I check also this link: [http://ubuntuforums.org/showthread.php?t=268024](http://ubuntuforums.org/showthread.php?t=268024)

I'll try to work around in the next days...

Bye now

---

### Post by apundir on 2007-03-29
I recently installed Edgy eft afresh with Kubuntu, followed all instructions to install citrix 9.0 with required packages (libmotif3, libxaw7, ms core fonts), got things working but when I lauch remote apps, there's no minimize/maximize/close buttons on menu bars but only blank squares. Also I am unable to see any character in htmls pages unless I highlight them by selecting them with mouse, images are fine though. A few more issues like these as well.
I have tried all suggestions posted in ubuntu forums as well found on net (including citrix support site) without any success.
Tried latest Citrix 10.0 as well, that crashes soon after opening Application launcher window even if I include fixes as suggested by citrix support site for utf8 fonts.
Tried all this from CLI as well just to capture any additional error that I might have missed while lanching from GUI but no success here well, problem still remains with no error message being dumped on CLI (other than "locale not supported by C library, locale unchanged" warning).

Ony of my collegue has ubuntu 6.10 with GNOME, he's facing exactly same problem.

Any pointer in debugging this further will be very helpful.

Thanks
Avnish

---

