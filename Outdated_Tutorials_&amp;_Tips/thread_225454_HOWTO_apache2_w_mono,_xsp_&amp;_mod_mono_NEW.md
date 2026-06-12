---
title: "HOWTO: apache2 w/ mono, xsp &amp; mod_mono **NEW**"
date: 2006-07-29
forum: Outdated Tutorials &amp; Tips
---

### Post by scottwill on 2006-07-29
OK, so getting ASP.NET to run on apache is not as easy as it may seem.  It took me 4-5 hours over 10+ sites and a lot of retries before I got it going.  So I figured I'd put it all together so hopefully it would help someone else.

[SIZE="1"][I][B]* I don't give any kind of warranty for this howto.  But if you follow this correctly you shouldn't have any problem.
*This howto does not use the mono packages in apt but rather the current stable sources.[/B][/I][/SIZE]

**First things First**

Open your terminal

make sure you enable root

*sudo -s*

and get up to date
[I]
apt-get update && apt-get dist-upgrade[/I]


**Apache**

Apache we do want from apt so
[I]
apt-get install apache2 apache2-mpm-prefork apache2-threaded-dev[/I]

apt will of course want to install the required debs as well.

Even if you already have apache installed make sure to get apache2-mpm-prefork & apache2-threaded-dev

Once it's done you can test it [http://localhost]("http://localhost")


**Mono**

Before we download and build mono, we need to have the appropriate tools
[I]
apt-get install libglib2.0-0 libglib2.0-dev pkg-config bison make[/I]

Download the mono, xsp and mod_mono sources from go-mono

[SIZE="1"][I][B]*Note that the build number's of the source packages will change eventually.
[/B][/I][/SIZE]
[I]cd /tmp

wget [http://go-mono.com/sources/mono/mono-1.1.13.8.tar.gz](http://go-mono.com/sources/mono/mono-1.1.13.8.tar.gz)
wget [http://go-mono.com/sources/xsp/xsp-1.1.13.7.tar.gz](http://go-mono.com/sources/xsp/xsp-1.1.13.7.tar.gz)
wget [http://go-mono.com/sources/mod_mono/mod_mono-1.1.13.5.tar.gz](http://go-mono.com/sources/mod_mono/mod_mono-1.1.13.5.tar.gz)[/I]

Unpack mono-1.1.13.8.tar.gz

*tar xzf mono-1.1.13.8.tar.gz*

Build mono

[I]cd mono-1.1.13.8
./configure --prefix=/usr
make
make install[/I]

**XSP**

We'll do the same for xsp.  xsp and mod_mono won't take nearly as long as mono does to make.

[I]cd /tmp
tar xzf xsp-1.1.13.7.tar.gz
cd xsp-1.1.13.7
./configure --prefix=/usr
make
make install[/I]

**mod_mono**

and finally

[I]cd /tmp
tar xzf mod_mono-1.1.13.5.tar.gz
cd mod_mono-1.1.13.5
./configure --prefix=/usr
make
make install[/I]


Immense happiness, we are installed and ready to go!  Well, not quite yet.  We still need to configure apache to use mod_mono.  See, the way it works, as far as I can tell, is apache takes the web request, sees it's a .aspx file that's being requested and passes it to xsp.  xsp then compiles it using mono and gives the html output back to apache to serve.  It's mod_mono that makes this conversation possible.

**Configure Apache**

[I]cd /etc/apache2
vi httpd.conf[/I] OR *nano httpd.conf* if that's your editor of choice

Append to the file *Include mod_mono.conf*

Now edit mod_mono.conf

*vi mod_mono.conf*

At the end of the file append

[I]Alias /test "/usr/lib/xsp/test"
AddMonoApplications default "/test:/usr/lib/xsp/test"
<Location /test>
        SetHandler mono
</Location>[/I]

Save and exit.  Then restart apache

*/etc/init.d/apache2 force-reload*

Now we test it :D [http://localhost/test](http://localhost/test)

It works!

---

### Post by HAL98 SE on 2006-09-06
hi scottwill,

thanks for the howto, I'd been trying to get this to work for a while using various tutorials, followed yours to the letter and it works fine, i uninstalled all the synaptic versions of the software and used wget as you stated and it worked a treat.

Many Thanks! Now I just need to come up with a revolutionary, world enhancing app that will improve the lives of millions! as you can see, you helped me get the hard part out of the way.

---

### Post by DA_uf on 2006-09-12
Hello scottwill,
Thanks!  Your method worked for me as well.

Now can I create an app with Visual Web Developer 2005 Express Edition and deploy it to this Apache server?

[http://msdn.microsoft.com/vstudio/express/media/en/AbsoluteBeginner/vwd/10vcs.wvx](http://msdn.microsoft.com/vstudio/express/media/en/AbsoluteBeginner/vwd/10vcs.wvx)

I had trouble with the VWD "Copy Web Site", so I just used FileZilla to ftp the entire site directory "Lesson10cs" under the existing test directory as "/usr/lib/xsp/test/Lesson10cs".

If I try [http://localhost/test/Lesson10cs/Default.aspx](http://localhost/test/Lesson10cs/Default.aspx)
I get> 
Server error in '/test' application
Description: Error processing request.

Error Message: HTTP 500.

Stack Trace:

System.Configuration.ConfigurationException: Unrecognized attribute in root element (/usr/lib/xsp/test/Lesson10cs/Web.config line 10)
in <0x00043> System.Web.Configuration.ConfigurationData:ThrowException (System.String text, System.Xml.XmlTextReader reader)
in <0x00082> System.Web.Configuration.ConfigurationData:InitRead (System.Xml.XmlTextReader reader)
in <0x0009e> System.Web.Configuration.ConfigurationData:LoadFromFile (System.String fileName)

If append the following below the mod_mono.conf "/test" information entry:
Alias /test2 "/usr/lib/xsp/test/Lesson10cs"
AddMonoApplications default "/test2:/usr/lib/xsp/test/Lesson10cs"
<Location /test2>
    SetHandler mono
</Location>

and try [http://localhost/test2](http://localhost/test2)
I get
500 Internal Server Error

---

### Post by scottwill on 2006-09-12
Sorry but the answer is no.  Visual Web Developer 2005 Express Edition uses the 2.0 .Net framework, whereas this howto only covers the 1.1 .Net framework.  (Someone let me know if I am mistaken.)

There is a solution for Mono to use 2.0 over 1.1, but I have yet to  try it myself.

---

### Post by DA_uf on 2006-09-12
Thanks for your reply.

So, had I been developing with 1.1, my deployment steps would have been correct?

Please post here if you find out how to enable 2.0 support.

Which 1.1 development tool would you recommend?

EDIT: Hey, let me put you onto this:
[http://lists.ximian.com/pipermail/mono-devel-list/2005-November/015880.html](http://lists.ximian.com/pipermail/mono-devel-list/2005-November/015880.html)
And maybe you can distill it down for us :-D

---

### Post by book36worm on 2006-09-17
Hi, I'm a newbie trying to get apache up and running, fraid that i'm lost on this simple how to. so please bare with me. i'm able to get the downloads and unpack them. but i have a problem when i comes to the build. there must be a step between these two lines that need to be written that either you did w/o writing or did earlier. i can't get the cd comand to work, i get "bash: cd: mono-1.1.13.8.tar.gz: Not a directory" as an error. please help! thanks

bookworm
ps. will this need to be done for each of these installs?


*tar xzf mono-1.1.13.8.tar.gz*
===> something happen here? or not<====
Build mono

[I]cd mono-1.1.13.8.tar.gz
./configure --prefix=/usr
make
make install[/I]

---

### Post by MrBrownstone3g on 2006-09-17
Hi all

Does mod_mono/xps also allow you to server asp 1.0 and 2.0 pages?

Cheers
Graham

---

### Post by scottwill on 2006-09-21
> **book36worm said:**
> 
*tar xzf mono-1.1.13.8.tar.gz*
===> something happen here? or not<====
Build mono

[I]cd mono-1.1.13.8.tar.gz
./configure --prefix=/usr
make
make install[/I]

you're mistaking the files for the folders.  After you tar, the directory by default will be the name of the file _minus_ the extension.

In other words, tar will take the file 'xzf mono-1.1.13.8.tar.gz' and make a subfolder called 'xzf mono-1.1.13.8' in the current directory you are in.

**Change:** *cd mono-1.1.13.8.tar.gz* to c*d mono-1.1.13.8*

--edit--
It appears that was a typo in my original howto.  It has been edited with the correction.

---

### Post by scottwill on 2006-09-21
> **MrBrownstone3g said:**
> Hi all

Does mod_mono/xps also allow you to server asp 1.0 and 2.0 pages?

Cheers
Graham

xps uses mcs to compile your pages.  mcs in turn uses the equivalent of the .NET Framework 1.1.xxxx.  There is xps2 and mcs2 (I think) which use the 2.0 framework.

---

### Post by DSn0wMan on 2006-10-18
There seems to be a problem with libglib2.0-dev.

I cant install it through apt-get. The prompt just barfs the following:

josh@josh-desktop:~/download/mono-1.1.17.2$ sudo apt-get install libglib2.0-devReading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libglib2.0-dev: Depends: libglib2.0-0 (= 2.10.2-1ubuntu3) but 2.10.3-0ubuntu1 is to be installed
E: Broken packages

Has anyone else had this problem?

---

### Post by scottwill on 2006-10-18
> **DSn0wMan said:**
> There seems to be a problem with libglib2.0-dev.

I cant install it through apt-get. The prompt just barfs the following:

josh@josh-desktop:~/download/mono-1.1.17.2$ sudo apt-get install libglib2.0-devReading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libglib2.0-dev: Depends: libglib2.0-0 (= 2.10.2-1ubuntu3) but 2.10.3-0ubuntu1 is to be installed
E: Broken packages

Has anyone else had this problem?


DSn0wMan, I noticed you are an Edgy Tester.  Are you installing this on Dapper or Edgy?  If it's Dapper then I suggest throwing the -f switch when getting glib (apt-get install -f libglib2.0-dev), but if using Edgy I do not know.  Is it possible the dependicies for Edgy regarding glib are broken?

---

### Post by DSn0wMan on 2006-10-18
No this is on my dapper machine. I try to shy away from beta stuff on my server.

Edit: The force option does not seem to help. It seems like the libglib2.0-0 is newer than the libglib2.0-dev if I am reading the output correctly.

 libglib2.0-dev: Depends: libglib2.0-0 (= 2.10.2-1ubuntu3) but 2.10.3-0ubuntu1 is to be installed

---

### Post by scottwill on 2006-10-18
> **DSn0wMan said:**
> No this is on my dapper machine. I try to shy away from beta stuff on my server.

Hmm, these are always the fun errors, right? ](*,) 

The only thing I can think of is to make sure all the repositories are uncommented in your /etc/apt/sources.list file.  Then do a apt-get update && apt-get upgrade and try again to install the glib.

Check the following if you are unsure. [http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories]("http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories")

Remember to back up your current one first!

Let us know what happens...

---

### Post by DSn0wMan on 2006-10-18
You where right. I just needed to update my sources.list. Thanks for the help!

---

### Post by echoz on 2006-10-22
You can actually install everything you need through apt-get.

[http://beans.seartipy.com/2006/06/08/installing-c-mononet-monodevelop-in-ubuntu-dapper-drake-606/](http://beans.seartipy.com/2006/06/08/installing-c-mononet-monodevelop-in-ubuntu-dapper-drake-606/)

---

### Post by echoz on 2006-10-22
You can actually install everything you need through apt-get.

[http://beans.seartipy.com/2006/06/08/installing-c-mononet-monodevelop-in-ubuntu-dapper-drake-606/](http://beans.seartipy.com/2006/06/08/installing-c-mononet-monodevelop-in-ubuntu-dapper-drake-606/)

---

### Post by orjansjoholm on 2006-11-25
A package for Mono 1.2.1 is available here:
[http://archive.ubuntu.com/ubuntu/pool/main/m/mono/](http://archive.ubuntu.com/ubuntu/pool/main/m/mono/)

Is there a way to use apt-get to install the package and its dependencies? I running Ubuntu Edgy at the moment.

Regards,

Örjan

---

### Post by Chippendale on 2006-12-02
awesome tutorial! worked the first time using Edgy =)

---

### Post by kochen on 2007-02-07
> **scottwill said:**
> [I]
wget [http://go-mono.com/sources/mono/mono-1.1.13.8.tar.gz](http://go-mono.com/sources/mono/mono-1.1.13.8.tar.gz)
wget [http://go-mono.com/sources/xsp/xsp-1.1.13.7.tar.gz](http://go-mono.com/sources/xsp/xsp-1.1.13.7.tar.gz)
wget [http://go-mono.com/sources/mod_mono/mod_mono-1.1.13.5.tar.gz](http://go-mono.com/sources/mod_mono/mod_mono-1.1.13.5.tar.gz)[/I]

downloaded _**latest**_ versions...

> **scottwill said:**
> Build mono

[I]cd mono-1.1.13.8
./configure --prefix=/usr
make
make install[/I]

after a long list of warnings on the make step I got a bunch of errors...

---

### Post by bloem on 2009-05-21
I came up with these updated instructions:

Performed on LAMP appliance from [http://virtualappliances.net/downloads/raw/](http://virtualappliances.net/downloads/raw/)
First upgraded to ubuntu 9.04. Stock mono and mod_mono don't work with our website, so time to get the latest code and compile.

[LIST=1]
[*]Update ubuntu: 

apt-get update
apt-get upgrade


[*]Install prereqs: 

apt-get install build-essential bison gettext libglib2.0-0 libglib2.0-dev pkg-config wget screen


[*]Install apache and mono essentials:

apt-get install apache2-threaded-dev mono-apache-server2 libapache2-mod-mono mono-xsp2


[*]Get latest mono source code from [http://ftp.novell.com/pub/mono/sources-stable/:](http://ftp.novell.com/pub/mono/sources-stable/:)

wget [http://ftp.novell.com/pub/mono/sources/mono/mono-2.4.tar.bz2](http://ftp.novell.com/pub/mono/sources/mono/mono-2.4.tar.bz2)
wget [http://ftp.novell.com/pub/mono/sources/xsp/xsp-2.4.tar.bz2](http://ftp.novell.com/pub/mono/sources/xsp/xsp-2.4.tar.bz2)
wget [http://ftp.novell.com/pub/mono/sources/mod_mono/mod_mono-2.4.tar.bz2](http://ftp.novell.com/pub/mono/sources/mod_mono/mod_mono-2.4.tar.bz2)


[*]Create a little script:

#! /bin/bash

tar -xvjf mono-*.tar.bz2
tar -xvjf xsp-*.tar.bz2
tar -xvjf mod_mono-*.tar.bz2

pushd mono*
./configure --prefix=/usr && make && make install
popd
pushd xsp*
./configure --prefix=/usr && make && make install
popd
pushd mod_mono*
./configure --prefix=/usr && make && make install
popd
date

Save it as run.sh and chmod it to 700.


[*]Run screen and then inside the screen terminal run ./run.sh. Detach from screen by pressing 'Ctrl+a d'. Now go to bed.


[*]The next day go back into screen by typing 'screen -r'. Check it all completed. Terminate screen by typing Ctrl-d.


[*]Restart apache: /etc/init.d/apache2 restart


[*]All should be well with the world.

[/LIST]

... but it isn't. When I reboot the vm the website doesn't come back up and instead gives me a '503 Service temporarily unavailable' error.

tail -f /var/log/apache2/error.log shows:

[error] Failed to connect to mod-mono-server after several attempts to spawn the process.

Restarting apache2 with /etc/init.d/apache2 restart, fixes it and the website appears. Turns out that I had a umask of 027 which blocks any world access to new files, so basically www-data, the user apache2 runs as, couldn't read some of the mono & co files. Once fixed, the site runs from boot. However initial access to the site is very slow.

Apache/2.2.11 (Ubuntu) mod_mono/2.4 PHP/5.2.6-3ubuntu4.1 with Suhosin-Patch mod_python/3.3.1 Python/2.6.2 mod_ssl/2.2.11 OpenSSL/0.9.8g mod_perl/2.0.4 Perl/v5.10.0 Server at 1.2.3.4 port 80

---

### Post by directhex on 2009-05-21
(minor warning: will kill your install on any mono package upgrades)

---

### Post by bloem on 2009-05-22
I realise that. I tried replacing the 'make install' steps with 'checkinstall', but that one refused to overwrite certain files. Can't remember which ones and now it seems to be working so loathe to go back and find out ;)

BB

---

