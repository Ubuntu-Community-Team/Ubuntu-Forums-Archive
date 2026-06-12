---
title: "HOWTO: Gaim 2.0 beta cookbook"
date: 2006-06-27
forum: Outdated Tutorials &amp; Tips
---

### Post by mlind on 2006-06-27
[INDENT]To build [gaim]("http://gaim.sourceforge.net/") 2.0 beta**3** for Dapper, you also need to build newer version of one additional library,
**[COLOR="Blue"]libgadu-dev[/COLOR]** to satisfy the build-time requirements.

You could build gaim using Dappers libgadu-dev library too, by modifying build-time dependencies,
but newer library contains some [important security fixes]("http://packages.debian.org/changelogs/pool/main/e/ekg/ekg_1.6+20060215-1/changelog")
[/INDENT]


[SIZE="4"]Initial setup[/SIZE]
[LIST]
[*]Before starting I suggest you to install **debfoster**, run it once and answer *yes* for all asked questions. 
[*]This way you set *default* state for installed packages and can easily uninstall **all** required build-time dependencies. 
[*]You can later "reset" debfoster using **-n** parameter after build-time dependencies have been removed and
you have successfully completed the steps of this HOWTO.
```

sudo aptitude install debfoster
sudo debfoster

```
[/LIST]



[SIZE="3"]Setup build environment[/SIZE]
[LIST]
[*]Install required tools for building process
```

sudo aptitude install build-essential cdbs devscripts dh-make fakeroot

```
[/LIST]



[SIZE="4"][COLOR="Blue"]libgadu-dev[/COLOR][/SIZE]
[LIST]
[*]Add Debian unstable repository to */etc/apt/sources.list*
```

deb-src http://ftp.uk.debian.org/debian **unstable** main contrib non-free

```
[*]Update sources
```

sudo aptitude update

```


[*]Get the source package
```

mkdir -p ~/packages/ekg
cd ~/packages/ekg
apt-get source libgadu-dev
cd **ekg-1.6+20060616**

```

[*]Insert new changelog entry
```

dch -iDdapper

```
```

ekg (1:1.6+20060616-**2ubuntu1**) dapper; urgency=low

  * Adopted for Dapper

 -- Firstname Lastname <youralias@yourhost.com>  Tue, 27 Jun 2006 11:01:59 +0300

```

[*]Install required build-time dependencies
```

sudo aptitude install libncurses-dev libreadline5-dev zlib1g-dev python-dev libgsm1-dev libssl-dev libglib2.0-dev libjpeg62-dev libaspell-dev

```

[*]Build and install
```

dpkg-buildpackage -rfakeroot -us -uc
sudo dpkg -i ../libgadu*.deb

```
[/LIST]


[SIZE="4"][COLOR="Green"]gaim[/COLOR][/SIZE]
[LIST]
[*]Add Debian experimental repository to */etc/apt/sources.list*
```

deb-src http://ftp.uk.debian.org/debian **experimental** main contrib non-free

```
[*]Update sources
```

sudo aptitude update

```


[*]Get the source package
```

mkdir -p ~/packages/gaim
cd ~/packages/gaim
apt-get source gaim
cd gaim-2.0.0+beta3 

```

[*]Insert new changelog entry
```

dch -iDdapper

```
```

gaim (1:2.0.0+beta3-**5ubuntu1**) dapper; urgency=low

  * Adopted for Dapper

 -- Firstname Lastname <youralias@yourhost.com>  Tue, 27 Jun 2006 11:10:05 +0300

```

[*][COLOR="Red"]Edit *debian/control* file and remove _version_ requirement from **cdbs** which is on Build-Depends line[/COLOR]



[*]Install required build-time dependencies
```

sudo aptitude install libgtk2.0-dev libxss-dev libmeanwhile-dev libgnutls11-dev tcl8.4-dev tk8.4-dev libao-dev libaudiofile-dev libgtkspell-dev libltdl3-dev libperl-dev libstartup-notification0-dev libzephyr-dev libxml2-dev libebook1.2-dev libedata-book1.2-dev libcamel1.2-dev libdbus-glib-1-dev libavahi-compat-howl-dev libxml-parser-perl

```

[*]Build and install
```

dpkg-buildpackage -rfakeroot -us -uc
sudo dpkg -i ../gaim_2.0.0+**beta3-5ubuntu1**_i386.deb ../gaim-data_2.0.0+**beta3-5ubuntu1**_all.deb

```
[/LIST]



[SIZE="4"]Removing the build dependencies[/SIZE]
[LIST]
[*]If you installed **debfoster** as suggested in the beginning, you can now remove all build dependencies.
Answer **p** (as purge) for all questions regarding to applications and libraries installed on build process.
```

sudo debfoster

```


[*]Remove/comment Debian source repositories from /etc/apt/sources.list

[/LIST]



**[edit]**
[LIST]
[*]Added *libxml-parser-perl* as build dependency, thanks bobpaul
[/LIST]

---

### Post by mlind on 2006-06-27
[SIZE="4"]gaim-guifications[/SIZE]


[INDENT]I noticed that atleast [gaim-guifications]("http://guifications.sourceforge.net/") plugin needs to be upgraded to get it working
with new Gaim version, so here we go[/INDENT]



[LIST]
[*][COLOR="Blue"]Apply same initial setup as on Gaim HOWTO previously, if you already removed those[/COLOR].
[*]You should use official Dapper source repository for this, so if you have Debian repositories still left on */etc/apt/sources.list*, remove/comment those
[*]Update your package source list before continuing
```

sudo aptitude update

```




[*]Install the gaim development package that was built on Gaim HOWTO previously
```

sudo dpkg -i ~/packages/gaim/gaim-**dev**_2.0.0+beta3-5ubuntu1_i386.deb

```

[*]Get **old** source package (for template)
```

mkdir -p ~/package/gaim-guifications
cd ~/package/gaim-guifications
apt-get source gaim-guifications

```

[*]Get new sources. If download link doesn't work, use another [mirror]("http://guifications.sourceforge.net/downloads.php")
```

wget http://heanet.dl.sourceforge.net/sourceforge/guifications/gaim-guifications-**2.13beta3**.tar.gz

```

[*]Apply package information for new sources (version needs to be specified in this case)
```

cd guifications-2.12
uupdate ../gaim-guifications-**2.13beta3**.tar.gz **2.13**
cd ../guifications-2.13

```

[*]Insert new changelog entry
```

dch -iDdapper

```
```

guifications (2.13-**0ubuntu1**) dapper; urgency=low

  * New upstream release

 -- Firstname Lastname <youralias@yourhost.com>  Tue, 27 Jun 2006 13:18:46 +0300

```

[*]Install required build-time dependencies (if you already removed those previously)
```

sudo aptitude install libgtk2.0-dev

```

[*]Build and install
```

dpkg-buildpackage -rfakeroot -us -uc
sudo dpkg -i ../gaim-guifications_2.13-0ubuntu1_i386.deb

```
[/LIST]

[SIZE="4"]Removing the build dependencies[/SIZE]
[LIST]
[*]Do as on Gaim HOWTO previously
[/LIST]

---

### Post by mlind on 2006-06-27
I uploaded .debs to temporary share that should stay up for 60 days
[http://www.freefilehoster.com/uploads/1151413707gaim2beta3.tar.gz](http://www.freefilehoster.com/uploads/1151413707gaim2beta3.tar.gz)


Before installing gaim2, install these dependencies
```

sudo aptitude install libavahi-compat-howl0 libgnutls11 libmeanwhile1

```

then install package contents
```

sudo dpkg -i gaim_2.0.0+beta3-5ubuntu1_i386.deb gaim-data_2.0.0+beta3-5ubuntu1_all.deb libgadu3_1.6+20060616-2ubuntu0_i386.deb

```
[COLOR="Red"]
[edit][/COLOR]
Gaim beta3.1 for Dapper
[http://www.freefilehoster.com/uploads/1156131517gaim2beta3.1-dapper.tar.gz](http://www.freefilehoster.com/uploads/1156131517gaim2beta3.1-dapper.tar.gz)

---

### Post by zasf on 2006-06-27
nice! will try this soon!

---

### Post by Technoviking on 2006-06-27
Another great how-to, I'm learning tons about how building debs works. I will try making instructions for building gaim-encryption later.

---

### Post by mlind on 2006-06-28
Mike, feel free to share that plugin once you get it sorted ;)
Nautilus plugin needs to be re-compiled too it seems.

---

### Post by st14n on 2006-06-29
[QUOTE=mlind]I uploaded .debs to temporary share that should stay up for 60 days
[http://www.freefilehoster.com/uploads/1151413707gaim2beta3.tar.gz](http://www.freefilehoster.com/uploads/1151413707gaim2beta3.tar.gz)


Before installing gaim2, install these dependencies
```

sudo aptitude install libavahi-compat-howl0 libgnutls11 libmeanwhile1

```

then install package contents
```

sudo dpkg -i gaim_2.0.0+beta3-5ubuntu1_i386.deb gaim-data_2.0.0+beta3-5ubuntu1_all.deb libgadu3_1.6+20060616-2ubuntu0_i386.deb

```[/QUOTE]

Nice one, mlind! You saved me quite some time.

---

### Post by evilhomer on 2006-07-02
any luck with gaim-otr?

---

### Post by mlind on 2006-07-02
[QUOTE=evilhomer]any luck with gaim-otr?[/QUOTE]

Try if this works.

---

### Post by 13121982 on 2006-07-02
Make gaim-svn version maybe easy.

---

### Post by evilhomer on 2006-07-09
Thanks for the gaim otr.  Unfortunately it still didn't work.  dpkg said::

dpkg: dependency problems prevent configuration of gaim-otr:
 gaim-otr depends on gaim (<< 1:3.0); however:
  Version of gaim on system is 2:2.0.0beta3-2ubuntu0.
dpkg: error processing gaim-otr (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gaim-otr

not sure why its looking for such an old gaim.  have an idea?

---

### Post by mlind on 2006-07-09
> **evilhomer said:**
> Thanks for the gaim otr.  Unfortunately it still didn't work.  dpkg said::

dpkg: dependency problems prevent configuration of gaim-otr:
 gaim-otr depends on gaim (<< 1:3.0); however:
  Version of gaim on system is 2:2.0.0beta3-2ubuntu0.
dpkg: error processing gaim-otr (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gaim-otr

not sure why its looking for such an old gaim.  have an idea?

I updated that attachment, try it again. You must also install libotr2.
```

sudo aptitude install libotr2

```

---

### Post by evilhomer on 2006-07-09
I downloaded the attachment again, but I get the same message.

Unpacking gaim-otr (from gaim-otr_3.0.0+cvs20060530-1_i386.deb) ...
dpkg: dependency problems prevent configuration of gaim-otr:
 gaim-otr depends on gaim (<< 1:3.0); however:
  Version of gaim on system is 2:2.0.0beta3-2ubuntu0.

I have libotr install.  Thanks.

---

### Post by mlind on 2006-07-09
> **evilhomer said:**
> I downloaded the attachment again, but I get the same message.

Unpacking gaim-otr (from gaim-otr_3.0.0+cvs20060530-1_i386.deb) ...
dpkg: dependency problems prevent configuration of gaim-otr:
 gaim-otr depends on gaim (<< 1:3.0); however:
  Version of gaim on system is 2:2.0.0beta3-2ubuntu0.

I have libotr install.  Thanks.

What's output of
```

dpkg -p gaim | grep Version

```

It should be *Version: 1:2.0.0+beta3-4* and gaim-otr has requirement that version is (<< 1:3.0), less than 3.0.

Who compiled your version? It has different versioning prefix than used on Debian gaim source packages..

---

### Post by evilhomer on 2006-07-09
dpkg -p gaim | grep Version
Version: 2:2.0.0beta3-2ubuntu0

Hmm, I forget where... 

maybe here: [http://www.dissociatedpress.net/2006/06/14/new-gaim-20-beta-3-packages-now-for-dapper-drake/](http://www.dissociatedpress.net/2006/06/14/new-gaim-20-beta-3-packages-now-for-dapper-drake/)

or here:
[http://mighmos.org/packages.php](http://mighmos.org/packages.php)

---

### Post by mlind on 2006-07-09
> **evilhomer said:**
> dpkg -p gaim | grep Version
Version: 2:2.0.0beta3-2ubuntu0

Hmm, I forget where... 

maybe here: [http://www.dissociatedpress.net/2006/06/14/new-gaim-20-beta-3-packages-now-for-dapper-drake/](http://www.dissociatedpress.net/2006/06/14/new-gaim-20-beta-3-packages-now-for-dapper-drake/)

or here:
[http://mighmos.org/packages.php](http://mighmos.org/packages.php)

Well, that versioning doesn't seem right.
Use gaim that's attached on post #3 of this thread instead.

---

### Post by evilhomer on 2006-07-09
success!  thanks very much for your help.

guess i could have thought of that :oops:

---

### Post by evilhomer on 2006-07-10
any luck with 'extended preferences' plugin?

---

### Post by mlind on 2006-07-10
> **evilhomer said:**
> any luck with 'extended preferences' plugin?

I'll try that in a moment

---

### Post by evilhomer on 2006-07-10
just fyi, adept updater wants to take gaim from 1:2.0.0 back to 2:2.0.0 so it's a package in my sources.list

---

### Post by mlind on 2006-07-10
> **evilhomer said:**
> just fyi, adept updater wants to take gaim from 1:2.0.0 back to 2:2.0.0 so it's a package in my sources.list

You could pin it down. Some other repository is using different versioning, and APT thinks it's newer.


To install gaim-extendedprefs plugin, try this

[LIST]
[*]add to your /etc/apt/sources.list
```

deb http://www.elisanet.fi/mlind/ubuntu dapper main

```
[*]then import gpg key (not absolutely necessary)
```

gpg --keyserver pgp.mit.edu --recv-key D0AFFF5E937215FF
gpg -a --export D0AFFF5E937215FF | sudo apt-key add -

```
[*]Then install plugin
```

sudo aptitude update && sudo aptitude install gaim-exetendedprefs

```
[/LIST]

---

### Post by evilhomer on 2006-07-11
Ah excellent!  You're the man :)  Now Gaim 2.0 is working great!


p.s. just fyi,

I got errors on the key:

gpg: no keyserver known (use option --keyserver)
gpg: keyserver receive failed: bad URI

---

### Post by mlind on 2006-07-11
> **evilhomer said:**
> Ah excellent!  You're the man :)  Now Gaim 2.0 is working great!


p.s. just fyi,

I got errors on the key:

gpg: no keyserver known (use option --keyserver)
gpg: keyserver receive failed: bad URI

You're welcome, I hope it works okay.

That command maybe needs --keyserver [pgp.mit.edu](pgp.mit.edu)
to work. I guess I have added default keyserver somewhere on my configs.

---

### Post by evilhomer on 2006-07-12
Ah you called it.  Doesn't work right.  Doesn't remove the Buddy List from the taskbar.  Oh well, everything else is working great.  Thanks.



Still no luck with gpg

$gpg --keyserver pgp.mit.edu --recv-key D0AFFF5E937215FF
gpg: requesting key 937215FF from hkp server pgp.mit.edu
?: pgp.mit.edu: Connection refused
gpgkeys: HKP fetch error: Connection refused
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

---

### Post by mlind on 2006-07-12
> **evilhomer said:**
> 
Still no luck with gpg


Well it doesn't matter. For some reason that keyserver isn't answering.

---

### Post by bobpaul on 2006-07-15
Tried the instructions, but nothing after this line:```
Edit debian/control file and remove version requirement from cdbs which is on Build-Depends line
```would work for me.

The debs you threw up work great, though, but it looks like unless I build gaim myself I can't build other packages against gaim. Is this true? I started on this road because I had gaim2beta3 from automatix and wanted guifications and guifications plugin_pack. Now thanks to your debs I have guifications, but when I try to run ./configure for the plugin pack I get an error about GAIM package not found. I'm assuming this is because I don't have the gaim binary only and not the headers. Does this sound right? Is there anyway I can get just the headers, or do I need try and make it compile properly?

---

### Post by mlind on 2006-07-16
> **bobpaul said:**
> Tried the instructions, but nothing after this line:```
Edit debian/control file and remove version requirement from cdbs which is on Build-Depends line
```would work for me.

The debs you threw up work great, though, but it looks like unless I build gaim myself I can't build other packages against gaim. Is this true? I started on this road because I had gaim2beta3 from automatix and wanted guifications and guifications plugin_pack. Now thanks to your debs I have guifications, but when I try to run ./configure for the plugin pack I get an error about GAIM package not found. I'm assuming this is because I don't have the gaim binary only and not the headers. Does this sound right? Is there anyway I can get just the headers, or do I need try and make it compile properly?

Yes, you need the gaim-dev package to compile gaim plugins. Could you describe what fails after you've edited debian/control file?
I suggest you to try pbuilder for building the package instead.

---

### Post by bobpaul on 2006-07-16
> **mlind said:**
> Could you describe what fails after you've edited debian/control file?

*rabble, rabble rabble* I expected that response as soon as I posted, but unfortunately I had already undone all that work as soon as it failed as I then noticed you had packages... just hadn't realized plugin_pack and guifications weren't the same thing ](*,) ...

So, I'll redo everything and later edit this post with the errors I was/am recieving.

[Edit]
Hrmpf! I was missing libxml-parser-perl. ```
$sudo apt-get install libxml-parser-perl
``` resolved the issue. Thanks for making me go back!:-D Maybe you should include that package in your howto...

[Edit2]
Stupid offlinemsg plug from the plugin pack still won't compile, but I successfully created *.debs for gaim, so that's got to count for something.

---

### Post by mlind on 2006-07-17
> **bobpaul said:**
> *rabble, rabble rabble* I expected that response as soon as I posted, but unfortunately I had already undone all that work as soon as it failed as I then noticed you had packages... just hadn't realized plugin_pack and guifications weren't the same thing ](*,) ...

So, I'll redo everything and later edit this post with the errors I was/am recieving.

[Edit]
Hrmpf! I was missing libxml-parser-perl. ```
$sudo apt-get install libxml-parser-perl
``` resolved the issue. Thanks for making me go back!:-D Maybe you should include that package in your howto...

[Edit2]
Stupid offlinemsg plug from the plugin pack still won't compile, but I successfully created *.debs for gaim, so that's got to count for something.


Okay, good you got it working. I added the missing package, thanks for that.

I'll check out the plugin pack if I can get it to build.

---

### Post by mlind on 2006-07-28
> **13121982 said:**
> Make gaim-svn version maybe easy.

You can download gaim2 svn version (+source package) from
```

deb http://www.elisanet.fi/mlind/ubuntu dapper **experimental**

```

---

### Post by deen on 2006-07-28
@mlind 

deb [http://www.elisanet.fi/mlind/ubuntu](http://www.elisanet.fi/mlind/ubuntu) dapper experimental

after add those in /etc/apt/source.list
and apt-get update

cant find gaim2 package, or gaim2-svn ..

where is the package?

---

### Post by mlind on 2006-07-28
> **deen said:**
> @mlind 

deb [http://www.elisanet.fi/mlind/ubuntu](http://www.elisanet.fi/mlind/ubuntu) dapper experimental

after add those in /etc/apt/source.list
and apt-get update

cant find gaim2 package, or gaim2-svn ..

where is the package?

```

sudo aptitude *install* gaim

```
should work (or *upgrade* if you already have gaim installed)

---

### Post by one_stinky_bum on 2006-08-06
Debs worked like a charm. Thanks.

---

### Post by idn on 2006-08-15
> **mlind said:**
> I uploaded .debs to temporary share that should stay up for 60 days
[http://www.freefilehoster.com/uploads/1151413707gaim2beta3.tar.gz](http://www.freefilehoster.com/uploads/1151413707gaim2beta3.tar.gz)


Before installing gaim2, install these dependencies
```

sudo aptitude install libavahi-compat-howl0 libgnutls11 libmeanwhile1

```

then install package contents
```

sudo dpkg -i gaim_2.0.0+beta3-5ubuntu1_i386.deb gaim-data_2.0.0+beta3-5ubuntu1_all.deb libgadu3_1.6+20060616-2ubuntu0_i386.deb

```


Thanks for this it worked great for me!

---

### Post by mlind on 2006-08-20
I uploaded gaim2 beta3.1 to my repository. Binaries are Dapper only, but source package is included and should build on Edgy too.
```

deb http://www.elisanet.fi/mlind/ubuntu dapper main
deb-src http://www.elisanet.fi/mlind/ubuntu dapper main

```

beta3.1 is a "maintenance" release for beta3, so don't update if you're using SVN snapshot.

---

### Post by Zelut on 2006-08-20
can you update the attachment with the beta3.1 .deb package?

Does anyone know if this fixes the proxy bug that 2.0beta3 has?

---

### Post by mlind on 2006-08-20
> **kuyaedz said:**
> can you update the attachment with the beta3.1 .deb package?

Does anyone know if this fixes the proxy bug that 2.0beta3 has?

Okay, I attached 3.1 binary packages to that same post.

---

### Post by xyverz on 2006-09-19
Still looking for a gaim-otr plugin dep that works with the 2.0.0beta3.1 version of gaim.  I'm getting the ABI mismatch error. :-/

---

### Post by stalefries on 2006-09-19
Does anyone have any information on the Nautilus integration plugin?

---

### Post by mlind on 2006-09-19
> **xyverz said:**
> Still looking for a gaim-otr plugin dep that works with the 2.0.0beta3.1 version of gaim.  I'm getting the ABI mismatch error. :-/

You can backport gaim-otr 3.0.0+cvs20060530-1 from Edgy or Debian experimental, if you're using Dapper. This version seems to work with Gaim 2 betas.

> **stalefries said:**
> Does anyone have any information on the Nautilus integration plugin?

Nautilus integration plugin seems to be merged in gaim codebase. Doesn't it show on gaim plugins dialog?

---

### Post by ericesque on 2006-10-12
bump

I'm using edgy and nautilus integration is definitley an option.  Installing gaim using Automatix in dapper left nautilus integration greyed out.

Just a quick question on nautilus integration though... what is it supposed to do?  heh.  any screenshots or explaination would be nice.

thanks!

---

### Post by MighMoS on 2006-10-14
I've set up an apt-repository that includes (amongst other things) gaim and gaim-otr.  Other updates include rhythmbox and gtk-engines, so if you don't like those, you can "lock version" in synaptic, or just grab the .deb files off of my website: [http://mighmos.org](http://mighmos.org).

The apt-repository line is:```
deb http://mighmos.org/apt-repository/ dapper main
```

---

### Post by yaddoshi on 2006-10-15
> **mlind said:**
> I uploaded .debs to temporary share that should stay up for 60 days
[http://www.freefilehoster.com/uploads/1151413707gaim2beta3.tar.gz](http://www.freefilehoster.com/uploads/1151413707gaim2beta3.tar.gz)


Before installing gaim2, install these dependencies
```

sudo aptitude install libavahi-compat-howl0 libgnutls11 libmeanwhile1

```

then install package contents
```

sudo dpkg -i gaim_2.0.0+beta3-5ubuntu1_i386.deb gaim-data_2.0.0+beta3-5ubuntu1_all.deb libgadu3_1.6+20060616-2ubuntu0_i386.deb

```
[COLOR="Red"]
[edit][/COLOR]
Gaim beta3.1 for Dapper
[http://www.freefilehoster.com/uploads/1156131517gaim2beta3.1-dapper.tar.gz](http://www.freefilehoster.com/uploads/1156131517gaim2beta3.1-dapper.tar.gz)


Thanks!  Less than 5 minutes of work.  Much appreciated.

---

### Post by s_spiff on 2006-10-19
will the same how to work for a amd64 environment? if not what changes are required?

---

### Post by WishMaster on 2006-10-19
gaim2.0beta4 is out

Anyone has .deb's ?
(also for guifications ,... if possible)

---

### Post by MighMoS on 2006-10-19
I tried packaging it yesterday, but although it compiled, it didn't run. I'm currently looking into it (or maybe I just grabbed it too soon).

---

### Post by domino on 2006-10-20
I just built and installed from SVN. However, I'm a bit confused. Which is is newer, beta4 or SVN? I'm assuming the trunk is newer but not necessarily more stable.

Also where is a good how-to to build edgy packages from the files I got from the trunk?

---

### Post by mlind on 2006-10-21
> **WishMaster said:**
> gaim2.0beta4 is out

Anyone has .deb's ?
(also for guifications ,... if possible)

For Dapper,
deb [http://www.elisanet.fi/mlind/ubuntu](http://www.elisanet.fi/mlind/ubuntu) dapper main

For Edgy
deb [http://www.elisanet.fi/mlind/ubuntu](http://www.elisanet.fi/mlind/ubuntu) edgy main

---

### Post by otacan on 2006-10-22
> **mlind said:**
> For Dapper,
deb [http://www.elisanet.fi/mlind/ubuntu](http://www.elisanet.fi/mlind/ubuntu) dapper main

For Edgy
deb [http://www.elisanet.fi/mlind/ubuntu](http://www.elisanet.fi/mlind/ubuntu) edgy main

deb [http://www.elisanet.fi/mlind/ubuntu](http://www.elisanet.fi/mlind/ubuntu)
the link doesnt work :???:

---

### Post by mlind on 2006-10-22
> **otacan said:**
> deb [http://www.elisanet.fi/mlind/ubuntu](http://www.elisanet.fi/mlind/ubuntu)
the link doesnt work :???:

Yes it does. You're supposed to add the URL as repository, not use as direct download link..

If upgrade/dist-upgrade doesn't work, use
```

sudo aptitude install gaim=1:2.0.0+beta4-1~dapper1

```

---

### Post by mucha on 2006-10-22
Is guifications also availible as package? :)

---

### Post by otacan on 2006-10-23
> **mlind said:**
> Yes it does. You're supposed to add the URL as repository, not use as direct download link..

If upgrade/dist-upgrade doesn't work, use
```

sudo aptitude install gaim=1:2.0.0+beta4-1~dapper1

```

Thank you very much, its ok now for gaim ,but I have an error with guifications:
** you are using gtk-gaim but this plugin requires gtk**
any solution?

Thanks

---

### Post by BitTorrentBuddha on 2006-10-24
Are there currently plans to package guifications, or is there already a packaged guifications perchance?

---

### Post by domino on 2006-10-24
> **BitTorrentBuddha said:**
> Are there currently plans to package guifications, or is there already a packaged guifications perchance?

Is this wht you're talking about?

[http://guifications.sourceforge.net/](http://guifications.sourceforge.net/)

I've installed all the plugins for Gaim 2.0.0beta4 witout a problem. it's not packaged, but I had nno problem compiling it. I love ubuntu & dapper guifications themes snatched from gome-look.

---

### Post by shizow on 2006-10-25
anyone got otr working with beta4?

---

### Post by mlind on 2006-10-25
> **BitTorrentBuddha said:**
> Are there currently plans to package guifications, or is there already a packaged guifications perchance?

I'll try to upload updated package tomorrow.

---

### Post by kousik on 2006-11-06
> **shizow said:**
> anyone got otr working with beta4?

otr will have to be recompiled to work with beta4. If you are comfortable with that, here are the steps:

1. Grab the sources at [http://www.cypherpunks.ca/otr/gaim-otr-3.0.0.tar.gz](http://www.cypherpunks.ca/otr/gaim-otr-3.0.0.tar.gz) , and untar them
2. Apply the beta2 patch [http://www.cypherpunks.ca/otr/gaim2b2-otr.diff](http://www.cypherpunks.ca/otr/gaim2b2-otr.diff)
3. It still won't compile, open gtk-dialog.c in an editor
4. At line 33, change "gtkstock.h" to "gaimstock.h"
5. Go thru the normal cycle of ./configure ; make ; sudo make install

HTH
Kousik

---

### Post by billybag on 2006-11-07
in doing this i ****** everything up. Luckily i know why.

1. i am a dumbass
2. i dont have drapper :-x

so now i need to somehow undo everything i did. i found out how to upgrade for breezy and not drapper... but it wont work and i am pretty sure it is because i tried to do the drapper upgrade of gaim.

gaim:
 Depends: libavahi-compat-howl0 (>=0.6.0) but it is not installable
  Depends: libcairo2 (>=1.0.2-2) but 1.0.2-0ubuntu1.1 is to be installed
 Depends: libdbus-1-2 (>=0.60) but it is not installable
 Depends: libdbus-glib-1-2 (>=0.60) but it is not installable
  Depends: libfreetype6 (>=2.1.10-1) but 2.1.7-2.4ubuntu1.2 is to be installed
  Depends: libgcrypt11 (>=1.2.2) but 1.2.1-3 is to be installed
  Depends: libglib2.0-0 (>=2.10.0) but 2.8.3-0ubuntu1 is to be installed
 Depends: libmeanwhile1 (>=1.0.0) but it is not installable
  Depends: libpango1.0-0 (>=1.12.3) but 1.10.1-0ubuntu1 is to be installed

---

### Post by evilhomer on 2006-11-09
checking for glib-2.0 >= 2.4 gtk+-2.0 >= 2.4 gaim >= 1.0... configure: error: glib

feel like i've had this over and over and over, with each new beta.

trying to compile otr for gaim2b4.  i'm using edgy.  thanks.

---

### Post by BitTorrentBuddha on 2006-11-12
EDIT: Compiled beta5 today, had nothing better to do... Guifications are working nonetheless.

Hi I'm having a problem compiling guifications, it says I don't have gaim installed, however I clearly do and under the package name 'gaim' too.```
$ ./configure
(*lots of typical configure script output...*)
checking for gcc -std=gnu99 option to accept ISO Standard C... (cached) -std=gnu99
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GAIM... configure: error: Package requirements (gaim) were not met:

No package 'gaim' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GAIM_CFLAGS
and GAIM_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```
I have your gaim package installed:```
$ dpkg -l | grep gaim
ii  gaim                                       2.0.0+beta4-3                        multi-protocol instant messaging client
ii  gaim-data                                  2.0.0+beta4-3                        multi-protocol instant messaging client - da
```
I tried both the gaim-guifications-2.13beta4 and beta5 tarballs from [this page](this page). Any idea as to why it's not showing up?

PS Are there any plans in the works to package beta5?

---

### Post by kousik on 2006-11-13
You need gaim-devel package.

---

### Post by Zelut on 2006-11-14
Can anyone give me some tips as to why I can't seem to compile gaim-otr?  I'm using the "debuild" system to put it together based from the source at:
deb-src [http://ftp.uk.debian.org/debian](http://ftp.uk.debian.org/debian) unstable main contrib non-free

I get this error:
gtk-dialog.c:33:28: error: gaim/gaimstock.h: No such file or directory
gtk-dialog.c: In function 'create_dialog':
gtk-dialog.c:651: error: 'GAIM_STOCK_DIALOG_ERROR' undeclared (first use in this function)
gtk-dialog.c:651: error: (Each undeclared identifier is reported only once
gtk-dialog.c:651: error: for each function it appears in.)
gtk-dialog.c:655: error: 'GAIM_STOCK_DIALOG_WARNING' undeclared (first use in this function)
gtk-dialog.c:659: error: 'GAIM_STOCK_DIALOG_INFO' undeclared (first use in this function)
make[2]: *** [gtk-dialog.lo] Error 1
make[2]: Leaving directory `/source/gaim-otr-3.0.0+cvs20060530'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/source/gaim-otr-3.0.0+cvs20060530'
make: *** [build-stamp] Error 2
debuild: fatal error at line 1224:
debian/rules build failed

---

### Post by evilhomer on 2006-11-16
the gaim beta4 package he made of otr 3+cvs worked for me:

[http://www.excentral.org/tag/gaim](http://www.excentral.org/tag/gaim)

(click on edgy for the repo instructions)

---

### Post by kousik on 2006-11-18
> **kuyaedz said:**
> 
I get this error:
gtk-dialog.c:33:28: error: gaim/gaimstock.h: No such file or directory
[...]
debian/rules build failed

You need gaim-devel package of gaim2 beta4 (or 5).

---

### Post by mlind on 2006-11-29
I've uploaded beta5 for both edgy and dapper to my repository if anyone's interested. 
(including gaim-guifications plugin for both distributions).

---

### Post by Zelut on 2006-11-29
thanks for that update.  The biggest thing I'm still looking for is compatibility with gaim-otr, which I can't even quite figure out with my own custom compiling.  Any tips on that mlind?

---

### Post by mlind on 2006-11-30
> **kuyaedz said:**
> thanks for that update.  The biggest thing I'm still looking for is compatibility with gaim-otr, which I can't even quite figure out with my own custom compiling.  Any tips on that mlind?

Sure thing, I uploaded patched package of gaim-otr (from Debian unstable) for that works with beta5 in to my repository.
It's for edgy, do you need a Dapper package instead?

---

### Post by Zelut on 2006-12-09
No, the edgy version is just what I was looking for.

I don't suppose you have a writeup somewhere on tips & tricks on compiling gaim & the extras.  I'm always trying to keep up on the beta packages but can't ever get the plugins to work with it.

Thanks for the repo by the way, without yours I'd be back at 1.5 :)

---

### Post by mlind on 2006-12-10
> **kuyaedz said:**
> No, the edgy version is just what I was looking for.

I don't suppose you have a writeup somewhere on tips & tricks on compiling gaim & the extras.  I'm always trying to keep up on the beta packages but can't ever get the plugins to work with it.

Thanks for the repo by the way, without yours I'd be back at 1.5 :)

You were probably doing the right thing all along, execpt that gaim-otr required a patch to work with newer gaim. DBTS contained a bug report and a patch for this issue, so fix was just to apply the patch and rebuild.

---

### Post by amoniak on 2007-01-09
@mlind

MANY thx for your package.. it was trying to compile it by myself, but I was not able to and already almost giving up..

cheers

---

### Post by cullwock on 2007-01-19
Does anyone have a edgy deb for beta6?

---

### Post by Zelut on 2007-01-19
There is a beta6 now?  When are they just going to go 2.0 stable and call it good?  ...or I guess its the google perpetual beta model.

---

### Post by NRG88 on 2007-01-19
I still found bugs in it. It's better to say it's beta, than to release it as stable, but with bugs.

---

### Post by Pathfinder_ on 2007-01-19
does this beta fix the direct connect issue with aim?

---

### Post by Wes24 on 2007-01-22
I get a segmentation fault when launching Beta 6, so I guess it is still a bit buggy.

---

### Post by LKRaider on 2007-01-22
I compiled debian packages of the beta 6 here on Dapper and it is working fine!

Much better than the beta 3 I was (inadvertidly) running till now :)

---

### Post by Wes24 on 2007-01-22
Fixed it using the following information:
[http://www.debuntu.org/gaim-2.0.0beta6-edgy-networkmanager-support#comment-302]("http://www.debuntu.org/gaim-2.0.0beta6-edgy-networkmanager-support#comment-302")

---

### Post by LKRaider on 2007-01-22
On my build (Dapper), the ICQ network is not listed on the program. (effectivelly not available as an option).

Anyone knows if ICQ is dependant on Xulrunner (libnss3-dev)? I am using GnuTLS only since Dapper has no devel packages for libnss3.

---

### Post by user2037 on 2007-01-24
> **evilhomer said:**
> checking for glib-2.0 >= 2.4 gtk+-2.0 >= 2.4 gaim >= 1.0... configure: error: glib

feel like i've had this over and over and over, with each new beta.

trying to compile otr for gaim2b4.  i'm using edgy.  thanks.

I have the same issue with Edgy and it appears to need the Gaim source-package "gaim-dev". Unfortunately that package appears to be beta3.1 and is incompatible with the binary for beta5.

---

### Post by Drezliok on 2007-01-27
I compiled Beta6 I got the SSL to work for MSN also. But I have no sound option other than
Console Beep
No Sound
Command

When I set it to Command and use ALSA, OSS. Or NAS, ARTs, ESD it crashes on me and lleave ms this.

Did I miss something in the compile?

Also I did not use gaim-dev

```
drezliok@TuxEater:~$ gaim
*** glibc detected *** gaim: double free or corruption (fasttop): 0x085c7060 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb74788bd]
/lib/tls/i686/cmov/libc.so.6(__libc_free+0x84)[0xb7478a44]
/usr/lib/libglib-2.0.so.0(g_free+0x31)[0xb7702b51]
gaim[0x80cae2d]
/usr/local/lib/libgaim.so.0(gaim_sound_play_file+0x37)[0xb7811ce7]
gaim[0x80cacef]
/usr/local/lib/libgaim.so.0(gaim_sound_play_event+0x78)[0xb7811ca8]
gaim[0x80cb341]
/usr/local/lib/libgaim.so.0(gaim_marshal_VOID__POINTER_POINTER_POINTER+0x26)[0xb780af46]
/usr/local/lib/libgaim.so.0(gaim_signal_emit_vargs+0xa9)[0xb780b779]
/usr/local/lib/libgaim.so.0(gaim_signal_emit+0x3c)[0xb780b88c]
/usr/local/lib/libgaim.so.0[0xb77e848c]
gaim[0x8088134]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x49)[0xb7795b29]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x12b)[0xb778879b]
/usr/lib/libgobject-2.0.so.0[0xb7798e81]
/usr/lib/libgobject-2.0.so.0(g_signal_emitv+0x198)[0xb779a418]
/usr/lib/libgtk-x11-2.0.so.0[0xb7bde41b]
/usr/lib/libgtk-x11-2.0.so.0[0xb7bde7c8]
/usr/lib/libgtk-x11-2.0.so.0[0xb7bde99b]
/usr/lib/libgtk-x11-2.0.so.0(gtk_bindings_activate_event+0xd9)[0xb7bdeab9]
/usr/lib/libgtk-x11-2.0.so.0[0xb7dd0ab8]
/usr/lib/libgtk-x11-2.0.so.0[0xb7d7215b]
/usr/lib/libgtk-x11-2.0.so.0(_gtk_marshal_BOOLEAN__BOXED+0x60)[0xb7cb1b00]
/usr/lib/libgobject-2.0.so.0[0xb7786fb9]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x20d)[0xb778887d]
/usr/lib/libgobject-2.0.so.0[0xb77991e3]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x68f)[0xb7799e7f]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb779a279]
/usr/lib/libgtk-x11-2.0.so.0[0xb7dc55f8]
/usr/lib/libgtk-x11-2.0.so.0(gtk_window_propagate_key_event+0x107)[0xb7dd5677]
/usr/lib/libgtk-x11-2.0.so.0[0xb7dd86dc]
/usr/lib/libgtk-x11-2.0.so.0(_gtk_marshal_BOOLEAN__BOXED+0x60)[0xb7cb1b00]
/usr/lib/libgobject-2.0.so.0[0xb7786fb9]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x12b)[0xb778879b]
/usr/lib/libgobject-2.0.so.0[0xb77991e3]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x68f)[0xb7799e7f]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb779a279]
/usr/lib/libgtk-x11-2.0.so.0[0xb7dc55f8]
/usr/lib/libgtk-x11-2.0.so.0(gtk_propagate_event+0x1ba)[0xb7caaf2a]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main_do_event+0x317)[0xb7cac0f7]
/usr/lib/libgdk-x11-2.0.so.0[0xb7b357ea]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x182)[0xb76fb802]
/usr/lib/libglib-2.0.so.0[0xb76fe7df]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1a9)[0xb76feb89]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb4)[0xb7cac574]
gaim(main+0x936)[0x80adc26]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb74278cc]
gaim(gtk_widget_grab_focus+0x39)[0x8067171]
======= Memory map: ========
08048000-080e9000 r-xp 00000000 08:01 2725685    /usr/local/bin/gaim
080e9000-080ec000 rw-p 000a0000 08:01 2725685    /usr/local/bin/gaim
080ec000-085e0000 rw-p 080ec000 00:00 0          [heap]
b3600000-b3621000 rw-p b3600000 00:00 0 
b3621000-b3700000 ---p b3621000 00:00 0 
b3747000-b3751000 r-xp 00000000 08:01 1860496    /lib/libgcc_s.so.1
b3751000-b3752000 rw-p 00009000 08:01 1860496    /lib/libgcc_s.so.1
b3760000-b37c0000 rw-s 00000000 00:08 1310743    /SYSV00000000 (deleted)
b37c0000-b3824000 r--p 00000000 08:01 2743948    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Oblique.ttf
b3824000-b3884000 rw-s 00000000 00:08 1277974    /SYSV00000000 (deleted)
b3884000-b3889000 r-xp 00000000 08:01 2791427    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-gif.so
b3889000-b388a000 rw-p 00004000 08:01 2791427    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-gif.so
b3892000-b38fe000 r--p 00000000 08:01 2743945    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
b38fe000-b3a7d000 r--p 00000000 08:01 2839892    /usr/share/icons/hicolor/icon-theme.cache
b3a7d000-b3bfc000 r--p 00000000 08:01 2839892    /usr/share/icons/hicolor/icon-theme.cache
b3bfc000-b4ce4000 r--p 00000000 08:01 2795463    /usr/share/icons/crystalsvg/icon-theme.cache
b4ce4000-b5dcc000 r--p 00000000 08:01 2795463    /usr/share/icons/crystalsvg/icon-theme.cache
b5dcc000-b641d000 r--p 00000000 08:01 2845307    /usr/share/icons/gnome/icon-theme.cache
b641d000-b6a6e000 r--p 00000000 08:01 2845307    /usr/share/icons/gnome/icon-theme.cache
b6a6e000-b6cc6000 r--p 00000000 08:01 2974624    /usr/share/icons/Tango/icon-theme.cache
b6cc6000-b6f1e000 r--p 00000000 08:01 2974624    /usr/share/icons/Tango/icon-theme.cache
b6f1e000-b6f20000 r-xp 00000000 08:01 2791624    /usr/lib/pango/1.5.0/modules/pango-basic-fc.so
b6f20000-b6f21000 rw-p 00001000 08:01 2791624    /usr/lib/pango/1.5.0/modules/pango-basic-fc.so
b6f210Aborted (core dumped)

```


Other than the sound issue it seems to run fine.

---

### Post by MighMoS on 2007-01-28
I'm also having problems getting it to run, and this includes flat out stealing source packages from Feisty, so I'm not sure what exactly is going on.

---

### Post by mlind on 2007-01-28
> **Drezliok said:**
> I compiled Beta6 I got the SSL to work for MSN also. But I have no sound option other than
Console Beep
No Sound
Command

When I set it to Command and use ALSA, OSS. Or NAS, ARTs, ESD it crashes on me and lleave ms this.

Did I miss something in the compile?

Also I did not use gaim-dev


Did you use the gaim source package from Feisty? If you're compiling additional plugins that depend on gaim-dev, make sure it's beta6 gaim-dev.

---

### Post by Drezliok on 2007-01-28
> **mlind said:**
> Did you use the gaim source package from Feisty? If you're compiling additional plugins that depend on gaim-dev, make sure it's beta6 gaim-dev.

No, I actually used the source from the gaim website. I guess I can try it again from feisty.

---

### Post by Wes24 on 2007-01-29
There are also debs available (for edgy):
[http://repository.debuntu.org/]("http://repository.debuntu.org/")

---

### Post by mlind on 2007-01-29
I recall uploading gaim6 for edgy in my repository, but I'm not able to check that currently.
```

deb http://www.elisanet.fi/mlind/ubuntu edgy main

```

---

