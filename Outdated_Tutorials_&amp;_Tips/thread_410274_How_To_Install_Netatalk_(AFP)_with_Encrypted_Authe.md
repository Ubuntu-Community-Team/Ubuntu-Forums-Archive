---
title: "How To: Install Netatalk (AFP) with Encrypted Authentication"
date: 2007-04-15
forum: Outdated Tutorials &amp; Tips
---

### Post by thornomad on 2007-04-15
*These guidelines were [complied from this thread]("http://ubuntuforums.org/showthread.php?p=1273565").  Thanks to those who came before and figured it all out.  I just tried to make the instructions a little more step-by-step and put together the different suggestions.*

**[COLOR="Red"]I maintain updates to this thread at: [How To: Install Netatalk (AFP) with Encrypted Authentication]("http://www.damontimm.com/blog/how-to-install-netatalk-afp-on-ubuntu-with-encrypted-authentication/").  Check it for new information.[/COLOR]**

**Purpose of the How To:** Install [Netatalk]("http://netatalk.sourceforge.net/") (AFP) on Ubuntu with encrypted authentication (using OpenSSL), which is not enabled by default with the Ubuntu package. By default, the package installed from the Ubuntu universal repositories will allow your password to be sent via clear text (you&#8217;ll know this because Mac OS X will throw a warning saying: &#8220;You password is being sent in clear text!&#8221;). This is because, apparently, [OpenSSL has a license that is incompatible with Debian&#8217;s GPL]("http://it.slashdot.org/comments.pl?sid=180016&cid=14905489").  Regardless: clear text is bad; encryption is good.
 [B]
Steps to Follow[/B]: I originally tried to compile netatalk from the source, however, I didn&#8217;t get it to work the first time and, before troubleshooting, [found nifty instructions at the Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=101823&page=2") which uses the default Ubuntu package but recompiles it with the ssl option in place. I have taken what I believe to be the best of these guides and put them together in a quick and easy fashion, below. Have tested it on a couple installations myself (Dapper and Edgy, i86), and it seems to work great.
 
 (You will need to have the Universe Repositories enabled for this to work: /etc/apt/sources.list) 

```
$ mkdir -p ~/src/netatalk
$ cd ~/src/netatalk
$ sudo aptitude install devscripts cracklib2-dev dpkg-dev libssl-dev
$ apt-get source netatalk
$ sudo apt-get build-dep netatalk
$ cd netatalk-2.0.3
$ DEB_BUILD_OPTIONS=ssl sudo dpkg-buildpackage -us -uc
$ sudo debi
```The basic trend of this set of operations is to: create a directory where all the messy files can be stored, download necessary packages, get the netatalk source, compile the source with the ssl option, install the package. You can remove everything after, if you want, or leave it alone. Either way: once it is installed no more clear text error from Apple!

 To connect to your AFP server on your Mac Finder, press APPLE-K (or &#8220;Go -> Connect to Server&#8221;). Enter the server&#8217;s IP address and then you will be prompted for your user name and password. After, it will mount your home directory.

 Settings for the service can be found at /etc/netatalk/.  There are a couple configuration files in there with instructions.  Good luck.

**Removing netatalk:** if you would like to remove netatalk you can run:

```
$ sudo apt-get remove netatalk
```**Support for this How To:** I am happy to help as best as I am able if anyone has problems, however, my knowledge of the subject is very limited, therefore, [COLOR=Red]**this _How To_ is being offered with no support or gaurantee**.  [/COLOR][COLOR=Red]**Use it at your own risk.**[/COLOR]

Finally, any updates to this process or new tips will be posted and maintained at:

[http://www.damontimm.com/blog/how-to-install-netatalk-afp-on-ubuntu-with-encrypted-authentication/](http://www.damontimm.com/blog/how-to-install-netatalk-afp-on-ubuntu-with-encrypted-authentication/)

Enjoy

---

### Post by engelsma on 2007-04-24
Excellent instructions!

Everything worked the first time around.

Thank you!

---

### Post by SpaceBas on 2007-04-26
This is great, thanks for the info!
Anyone know how to add kerberos support?
looks like it requires uams_gss.so

---

### Post by philipMac on 2007-05-09
Nice one... worked perfectly. 
Cheers.

---

### Post by Richard Woodfied on 2007-06-05
Any ideas why I would get the error 
[INDENT]> Could not open file **/var/lib/apt/lists/es.archive.ubuntu.com_ubuntu_dists_feisty-backports_main_source_Sources** - open (2 No such file or directory)[/INDENT]

Other than that the file is missing :)

I edited the **/etc/apt/sources.list** file to uncomment the **universe multiverse** libraries ad restarted.

Thanks in advance for any help.

-r

---

### Post by thornomad on 2007-06-05
> **Richard Woodfied said:**
> Any ideas why I would get the error 

```
Could not open file /var/lib/apt/lists/es.archive.ubuntu.com_ubuntu_dists_feisty-backports_main_source_Sources - open (2 No such file or directory)
```

Other than that the file is missing :)

I edited the **/etc/apt/sources.list** file to uncomment the **universe multiverse** libraries ad restarted.

Hmm ... I am not a whiz at this and I have not installed this on Feisty ... my thoughts are:

[LIST=1]
[*]has anyone else successfully done this in feisty ?
[*]have you tried installing any other packages ?  That is, is this the only package you have tried or the only package that doesn't work (and everything else does)
[*]it says "es.archive" ... is that the spanish version?
[/LIST]

If this is only happening with this particular package I don't have much advice; probably one of the required dependencies isn't being loaded or maybe it doesn't exist in feisty.

Are you running all this as "sudo" where indicated?

D

---

### Post by Richard Woodfied on 2007-06-05
Strangely, I am in Spain, although this is a US dist.  The files in the source directory ar either 

es.archive.xxxx or security.ubuntuxxx

The failure line produces the same error whether run as su, since the file is missing.

I'll try and get the file I think.

-r

---

### Post by Richard Woodfied on 2007-06-05
Missing files are available at

[INDENT][http://es.archive.ubuntu.com/ubuntu/dists/feisty-backports/](http://es.archive.ubuntu.com/ubuntu/dists/feisty-backports/)[/INDENT]

and they are Spanish it turns out.

Thanks for helping out though

-r

---

### Post by thornomad on 2007-06-06
> **Richard Woodfied said:**
> Strangely, I am in Spain, although this is a US dist.  The files in the source directory ar either 

es.archive.xxxx or security.ubuntuxxx

The failure line produces the same error whether run as su, since the file is missing.

I'll try and get the file I think.

Let us know what happens; I am not sure how to troubleshoot it any further, to be honest.  Does everything else install without a problem ?

D

---

### Post by Gyn3r on 2007-06-12
I am getting the following error message:

> dpkg-parsechangelog: error: cannot open debian/changelog to find format: No such file or directory
dpkg-buildpackage: unable to determine source pakage is
debi: cannot find readable debian/source anywhere!
Are you in the source code tree?

I would really appreciate some help :)

---

### Post by thornomad on 2007-06-12
> **Gyn3r said:**
> I would really appreciate some help :)

Hi - not sure if I can be of much help ... are you sure you used the "cd" command to move to the appropriate directory where the source files are?  If you followed each of these steps I am not sure ... don't know enough about debi and dkpg.  Sorry.

---

### Post by Gyn3r on 2007-06-13
Yes. I had the same problem as Richard Woodfied, but I downloaded all the files myself.

But when I try to install the original Netatalk, this message shows up and nothing happens. I waited for several hours, but still nothing changed:

> Starting Netatalk services (this will take a while)

---

### Post by sudhashen on 2007-07-09
Hi

Worked fine the on the first bit of instructions.  Thanks!

However Ubuntu said it had updates for netatalk sometime later and I installed it.

Ever since then I can't connect - services start when I reboot the pc but when I restart service I get the this error:

nbp_rgstr: Connection timed out
Can't register dhashen-desktop:Workstation@*

Help?

---

### Post by thornomad on 2007-07-12
I have posted a way to hold back the auto-update of netatalk after the installation to avoid this problem -- I will keep the page updated at: 

[http://www.damontimm.com/blog/how-to-install-netatalk-afp-on-ubuntu-with-encrypted-authentication/](http://www.damontimm.com/blog/how-to-install-netatalk-afp-on-ubuntu-with-encrypted-authentication/)

---

### Post by williswasabi on 2007-08-26
I just did this on Feisty. The list of packages to install was missing a lot. As suggested by the [FONT="Courier New"]dpkg-buildpackage[/FONT] command I had to install the following as well:

[FONT="Courier New"]sudo apt-get install cdbs autotools-dev debhelper quilt patchutils dh-buildinfo d-shlibs libdb4.2-dev libwrap0-dev libpam0g-dev libslp-dev libcupsys2-dev heimdal-dev[/FONT]

Once I did that, it built and it's working fine.

---

### Post by thornomad on 2007-08-27
Thanks for that -- I haven't tried it on anything but 6.06.1 ... I only use it on my server, so is good to hear what works on later versions.  I should take the time, one day, to add the info in there for people installing under different versions.

D

---

### Post by MrGando on 2007-09-24
Hi , I am having problems with your instructions (ubuntu feisty 7.04)

Here is my output after following your instructions:
( I did DEB_BUILD_OPTIONS=ssl sudo dpkg-buildpackage -us -uc ) and then rebooted.

then:

mrgando@Unicron:~/netatalk/netatalk-2.0.3$ sudo debi
Password:
(Reading database ... 117692 files and directories currently installed.)
Preparing to replace netatalk 2.0.3-5 (using netatalk_2.0.3-5_i386.deb) ...
Stopping Netatalk Daemons: afpd cnid_metad papd timelord atalkd.
Unpacking replacement netatalk ...
Setting up netatalk (2.0.3-5) ...
Starting Netatalk services (this will take a while): nbp_rgstr: Connection timed out
Can't register Unicron:Workstation@*
invoke-rc.d: initscript netatalk, action "start" failed.
dpkg: error processing netatalk (--install):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 netatalk
debi: debpkg -i failed

---

### Post by thornomad on 2007-09-24
Are you using VMWare (or have you it installed)?  I don't have a fix, but that's what I can offer if you ARE using VMWare.  Check out:

[http://www.damontimm.com/blog/how-to-install-netatalk-afp-on-ubuntu-with-encrypted-authentication/#comment-748](http://www.damontimm.com/blog/how-to-install-netatalk-afp-on-ubuntu-with-encrypted-authentication/#comment-748)

Someone posted an issue with the same problem and I have a link there that addressed his issue.

Damon

> **MrGando said:**
> 
Starting Netatalk services (this will take a while): nbp_rgstr: Connection timed out
Can't register Unicron:Workstation@*
invoke-rc.d: initscript netatalk, action "start" failed.
dpkg: error processing netatalk (--install):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 netatalk
debi: debpkg -i failed

---

### Post by MrGando on 2007-09-24
Damn I do use vmware, and it sounds as the same problem reported in the link that you pasted....

Crap, does anyone know something about how to fix this ??

I use vmware player 2.0 to develop with visual studio 2005 ( work for the university )

:(

Help please

EDIT: it's fixed... I found a post here

[http://ubuntuforums.org/showpost.php?p=1273565&postcount=21](http://ubuntuforums.org/showpost.php?p=1273565&postcount=21)

in resume :

It says that the problem comes from a parallel VMware installation, you have to edit

/etc/netatalk/atalkd.conf

and add this single line without quotes

eth0

and that's it , I got netatalk running now.

Hope this helps 

-Gando

---

### Post by sniffass on 2007-09-25
Hi, Justed wanted to say this worked flawlessly on Gutsy Gibbon. It is still in development at the moment and I'm taking a chance using it in production, hopefully netatalk will work the same way with the final release also.

---

### Post by sniffass on 2007-09-26
Hi there, just wanted to ask something. Following this guide I have been able to compile with own netatalk package with ssl auth, which is grand. But where can I actually find this package? I don't see it anywhere, I want to save it so I don't have to recompile again in the future.
Thanks
Gabriel

---

### Post by sniffass on 2007-10-03
Hi all

Just wanted to let you know that you can also get the ubuntu AFP server to show up in Finder on OS X under Network, just like other OS X machines do. You need to install avahi:
```
sudo aptitude install avahi-daemon -y
```

and then create a file like the following (replace vim with your editor of choice):
```
sudo vim /etc/avahi/services/afpd.service
```

In this new file add the following:
```
<?xml version="1.0" standalone='no'?><!--*-nxml-*-->
<!DOCTYPE service-group SYSTEM "avahi-service.dtd"> 
<service-group>
  <name replace-wildcards="yes">%h</name>
  <service>
    <type>_afpovertcp._tcp</type>
    <port>548</port>
  </service>
</service-group>
```

Save it and then start avahi:
```
sudo /etc/init.d/avahi-daemon restart
```

This should allow your ubuntu server to show up in Finder now.

Thanks
<snip>

---

### Post by HS-L on 2007-11-24
> **sniffass said:**
> Hi all

Just wanted to let you know that you can also get the ubuntu AFP server to show up in
Finder on OS X under Network, just like other OS X machines do.

Is this also possible for servers that are not in the same LAN?

:-)

And I have another problem with netatalk..
the finder can't see .htaccess files that i have in my webdirectories when my mount
my homedir on my server. I use the default afpd.conf. does anyone have a solution for this?

Thx..

Harold

---

### Post by cwestpha on 2008-08-18
I have tried this but I keep getting an error:

Found 736 different copyright and licensing combinations.
ERROR: The following new or changed copyright notices discovered:

UNKNOWN [1998 Owen Taylor</p><p>Permission to use, copy, modify, and distribute this software and / notice appear in all copies and that / notice and this permission notice appear in supporting]: doc/htmldocs/netatalkconfig.1.html

To fix the situation please do the following:
  1) Investigate the above changes and update debian/copyright as needed
  2) Replace debian/copyright_hints with debian/copyright_newhints
make: *** [debian/stamp-copyright-check] Error 1
dpkg-buildpackage: failure: debian/rules build gave error exit status 2

---

### Post by thornomad on 2008-08-18
This thread may be outdated - check out:

[http://www.damontimm.com/blog/how-to-install-netatalk-afp-on-ubuntu-with-encrypted-authentication/](http://www.damontimm.com/blog/how-to-install-netatalk-afp-on-ubuntu-with-encrypted-authentication/)

That was updated more recently.

---

### Post by KDB9000 on 2008-09-30
Well the the steps are the same as yours for the most part.

I did get it working once, but I think it messed up after I restarted the system or did an update (don't remember which). Now it doesn't work and I can't get it to build with SSL. I followed the steps in this threat, the other one you posted, and this latest link, but no matter how many times I build it, it will not build with SSL. What could I be doing wrong?

---

### Post by erlighaugstad on 2008-10-09
Figured it out!

---

### Post by Zerocool3001 on 2009-05-17
I have reported this as a bug [https://bugs.launchpad.net/ubuntu/+source/netatalk/+bug/377543](https://bugs.launchpad.net/ubuntu/+source/netatalk/+bug/377543)

---

### Post by sheldonnbbaker on 2009-11-09
Thanks for the tut - worked perfectly!

Is there a way to mount the entire hard disk (not just my home directory)?

Thanks!

---

### Post by mgjsmith on 2009-11-12
I keep getting the following error message when trying to install netatalk in order to use networking with a MAC ......
sudo apt-get build-dep netatalk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libcupsys2-dev is a virtual package provided by:
  libcups2-dev 1.4.1-5ubuntu2.1
You should explicitly select one to install.
E: Package libcupsys2-dev has no installation candidate
E: Failed to satisfy Build-Depends dependency for netatalk: libcupsys2-dev

I am a complete beginner on Ubuntu so any help would be appreciated. Martin

---

### Post by mgjsmith on 2009-11-12
problem sorted - no longer an Ubuntu beginner!!

---

### Post by chacham23 on 2009-11-13
> **mgjsmith said:**
> problem sorted - no longer an Ubuntu beginner!!

I your problem too.. can you share the fix with us?

thanks :)

---

### Post by bru3 on 2009-11-14
Hi all.
Someone else have a umask problem?
If I create a folder from my Mac on the Server I couldn't delete it.
I changed the global umask to 002 and the share user is in the same group like the user the server is logged in.

Some solutions?

Thx Bru3

---

### Post by blueshogun on 2010-03-04
> **mgjsmith said:**
> I keep getting the following error message when trying to install netatalk in order to use networking with a MAC ......
sudo apt-get build-dep netatalk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libcupsys2-dev is a virtual package provided by:
  libcups2-dev 1.4.1-5ubuntu2.1
You should explicitly select one to install.
E: Package libcupsys2-dev has no installation candidate
E: Failed to satisfy Build-Depends dependency for netatalk: libcupsys2-dev

I am a complete beginner on Ubuntu so any help would be appreciated. Martin


I used aptitude for that package.  ```
sudo aptitude install libcups2-dev
```

Everything else the same.
Worked for me!

---

### Post by tomiq on 2010-10-15
Some time had passed and I wonder if the current Ubuntu (10.10) netatalk packages still don't support encrypted authentication as I would prefer not to use samba for now.
Thornomad updated his blog related to this issue ([http://blog.damontimm.com/how-to-install-netatalk-afp-on-ubuntu-with-encrypted-authentication/](http://blog.damontimm.com/how-to-install-netatalk-afp-on-ubuntu-with-encrypted-authentication/)), saying that following 9.04 release "the package in the repositories works with no extra steps":
> Updated 05.08.09: Just tested this with Jaunty (09.04) and the  package in the repositories works with no extra steps.  If you are using  an older version of Ubuntu, however, you will want to follow these  instructions.  Tested with Intrepid Ibex (8.10) as well as: 6.06, 7.04,  7.10, and 8.06.Does this mean that current versions of netatalk provide a secure authentication mechanisms?

I have tried to sniff the AFP login communication with wireshark and didn't find the textual representation of the password submitted.

So is it now really secure? Where could one find such information?

---

### Post by thornomad on 2010-10-16
> **tomiq said:**
> Does this mean that current versions of netatalk provide a secure authentication mechanisms?

I have tried to sniff the AFP login communication with wireshark and didn't find the textual representation of the password submitted.

So is it now really secure? Where could one find such information?

I am not sure how one every knows if something is "really" secure without reading the source code ... and, even then, who knows!  

Back when I started the thread the only way that I knew it was *insecure* was that my Mac warned me; it would say that the password was being sent in cleartext.  After following the steps I outlined, that warning went away.  But that's as far as I ever went to test its security.  With the new version in the repositories that warning does not happen (and I believe from some of the bug logs and version notes you can find how they implemented the SSL).

Damon

---

### Post by atca on 2011-08-02
my experience of Netatalk and TimeMachine set up is [here]("http://confoundedtech.blogspot.com/2011/07/draft-draft-ubuntu-as-apple-time.html"), particularly around resolving permission issues.

I'm struggling to get usdots working with Leopard time machine, any advice? without usedots it works, encoding in hex :2e but with usedots it fails.

[http://confoundedtech.blogspot.com/2011/07/draft-draft-ubuntu-as-apple-time.html](http://confoundedtech.blogspot.com/2011/07/draft-draft-ubuntu-as-apple-time.html)

---

