---
title: "Banshee 1.2.1 Installation Problems"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by ahorne12 on 2008-08-17
Hi,

   I've had Ubuntu for about 4 months now, but still struggling with many things.  

   Right now I'm trying to get an application to work with my Ipod; so far I haven't had luck with Rhythmbox or Amarok, but I like the look of Banshee so I want to install the newest version.  I've downloaded the banshee-1-1.2.2.tar.gz file, and in Terminal navigated there and entered ./configure.  It goes well for a while until it gets to...

checking for MONO_ADDINS_GUI... yes
checking for NOTIFY_SHARP... no
no
checking for BOO... configure: error: Package requirements (boo >= 0.8.1) were not met:

Requested 'boo >= 0.8.1' but version of Boo is 0.8.0.2730

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BOO_CFLAGS
and BOO_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


From this I gather I need a more recent version of BOO, whatever the heck that is.  But I can't figure out how to get one.  Synaptic package manager only offers the version I already have and, incidentally, both it and the Add/Remove program options have much older version of Banshee on them, and those do not recognize my Ipod.

Make this means there's some problem with my Ipod synch rather than the softwares, but from everything I've read it's dead easy - just plug in and it will recognize.  That isn't happening for me.  

It's used to running off Windows - do I have to do something to it to prep it for Linux before it will work???

Thanks,

Andrew

---

### Post by Crafty Kisses on 2008-08-17
I'm pretty sure Banshee is in the repos, it sounds like you need to compile those tars.

---

### Post by jualin on 2008-08-17
Why don't you try installing Banshee using the Package Manager. You don't need to compile it yourself. Just search the package Banshee using Synaptic Package Manager (System, Administration), or via terminal > sudo apt-get install banshee.Hope this helps!

---

### Post by mc4man on 2008-08-17
you can get the latest here, follow instr. ( change drop down to hardy

[https://edge.launchpad.net/~banshee-team/+archive](https://edge.launchpad.net/~banshee-team/+archive)

---

### Post by k3lt01 on 2008-08-17
I wouldn't advise you change to the new Banshee. I have it and it wont download podcasts past 25%. The old Banshee in the repos works fine if you aren't worried about video capabilities.

Until they fix Banshee I am using gPodder. It saves the files under strange alpha-numeric names in the folder but displays them properly in the program.

To anyone who is thiking of telling me to post a bug report for Banshee, I have done this and am still waiting for a reply that tells me how to fix it. All they are doing is rushing new releases out that fix "minor" issues without fixing the main problems such as proper downloads and file playback which is what most people use it for.

---

### Post by cybrsaylr on 2008-08-17
I had problems installing the latest Banshee version also. 
It installed but won't open. Tried installing a couple times witn no luck and went back to using the older default version which seems to play OK.

---

### Post by lvlo on 2008-08-17
> **cybrsaylr said:**
> I had problems installing the latest Banshee version also. 
It installed but won't open. Tried installing a couple times witn no luck and went back to using the older default version which seems to play OK.

Try this on terminal:

```
banshee-1
```

---

### Post by k3lt01 on 2008-08-18
> **lvlo said:**
> Try this on terminal:

```
banshee-1
```

That wont work if you haven't got the Banshee Repo on your sources list, if you just have the official Ubuntu repo sources you will just get the older version.

---

### Post by cybrsaylr on 2008-08-18
> **lvlo said:**
> Try this on terminal:

```
banshee-1
```

tried that and got this,

banshee-1: command not found

---

### Post by jualin on 2008-08-18
The "l" on the command is not a 1 (number one) is a lower case **L**
Also you need an space after banshee. > banshee -l

---

### Post by cybrsaylr on 2008-08-18
> **jualin said:**
> The "l" on the command is not a 1 (number one) is a lower case **L**
Also you need an space after banshee.

LOL!
I've made that mistake before.

Anyways, put in the correct:

banshee -l

and all it did was load the old original banshee player not the new version.

---

### Post by jualin on 2008-08-18
Then I guess the old one hasn't been uninstalled yet. Go to Synaptic package manager and look for the package named "Banshee" and remove it, or via terminal > sudo apt-get purge banshee Then try installing the latest banshee.

---

### Post by mc4man on 2008-08-18
It's banshee-1 (the number 1, no space
You can have both banshee and banshee-1 installed at the same time, just add the repo as in link and run
```
sudo apt-get install banshee-1
```

repo
[https://edge.launchpad.net/~banshee-team/+archive](https://edge.launchpad.net/~banshee-team/+archive) (change drop down to hardy

It will get a separate menu listing 
The start up bug (improper launch comm) I believe has been fixed
If not ck. here
[http://ubuntuforums.org/showthread.php?p=5530845#post5530845](http://ubuntuforums.org/showthread.php?p=5530845#post5530845)

---

### Post by k3lt01 on 2008-08-19
> **mc4man said:**
> The start up bug (improper launch comm) I believe has been fixed
If not ck. here
[http://ubuntuforums.org/showthread.php?p=5530845#post5530845](http://ubuntuforums.org/showthread.php?p=5530845#post5530845)The start up bug is fixed but the download bug still remains.

---

### Post by cybrsaylr on 2008-08-19
> **mc4man said:**
> It's banshee-1 (the number 1, no space
You can have both banshee and banshee-1 installed at the same time, just add the repo as in link and run
```
sudo apt-get install banshee-1
```

Thanks.
That did the trick. 
I now have both versions of banshee installed and working now.

---

