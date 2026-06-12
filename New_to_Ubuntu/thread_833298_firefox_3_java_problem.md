---
title: "firefox 3 java problem"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by terrordrone on 2008-06-18
Hi

i moved my firefox 2 folder in /usr/lib/firefox to /usr/lib/firefox2

i installed firefox 3 by extracting the tar ball and placing the extracted firefox folder as /usr/lib/firefox

then i copied all plugins in /usr/lib/firefox2/plugins to /usr/lib/firefox/plugins (from ff2 to ff3)


firefox 3 now says jvm not working ( jvm plugin not found )

but firefox 2 has java plugin installed


thanks

---

### Post by clb137 on 2008-06-18
HI,

why did you not just install firefox 3 as normal?

clint

---

### Post by BlackDragonBE on 2008-06-18
I would place the files back and do a normal upgrade to 3.0, you don't have to worry about anything, everything works great, I'm using it right now!

---

### Post by terrordrone on 2008-06-18
:|

didnt want ff2 on my system

tried removing it with synaptic.. but it removed many applications which used firefox for one thing or the other...


so this was the option i had... 


well.. can i still fix it?

---

### Post by terrordrone on 2008-06-18
> **BlackDragonBE said:**
> I would place the files back and do a normal upgrade to 3.0, you don't have to worry about anything, everything works great, I'm using it right now!

upgrade through synaptic? synaptic doesnt have 3 final release 



my check for updates button on ff2 is disabled , i dont know for what reason though

---

### Post by Nepherte on 2008-06-18
Firefox 3 final is in the repositories. The reason why the check for updates entry is greyed out, is because you need root privileges to install.

---

### Post by jamesstansell on 2008-06-18
Mozilla really expects Linux users to upgrade through their distro rather than from the mozilla.org site.  At some point they expect to stop providing a tar ball.

When you install the ubuntu firefox package the 'check for updates' is greyed out because it is not compatible with the ubuntu repositories.  You just need to use the update manager, synaptic or similar.

When you get your firefox installation straightened out, please let us know if you still need help with the java plugin.

---

### Post by BlackDragonBE on 2008-06-18
Just do
sudo synaptic
in a terminal

---

### Post by terrordrone on 2008-06-18
> **Nepherte said:**
> Firefox 3 final is in the repositories. The reason why the check for updates entry is greyed out, is because you need root privileges to install.


these are my software sources
```

deb http://archive.ubuntu.com/ubuntu/ gutsy restricted main
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.

deb http://archive.ubuntu.com/ubuntu/ gutsy-updates restricted main
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

##Universe

deb http://archive.ubuntu.com/ubuntu/ gutsy universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## Multiverse

deb http://archive.ubuntu.com/ubuntu/ gutsy multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Backports

# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Canonical Partner Repository 

deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner
deb http://archive.ubuntu.com/ubuntu/ gutsy-security restricted main
# deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://archive.ubuntu.com/ubuntu/ gutsy-security universe
# deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://archive.ubuntu.com/ubuntu/ gutsy-security multiverse
# deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb http://ppa.launchpad.net/awn-testing/ubuntu gutsy main
# deb http://ppa.launchpad.net/reacocard-awn/ubuntu gutsy main

```

this is what my updated synaptic shows...
[http://picasaweb.google.co.uk/lh/viewPhoto?uname=llabhilash&aid=5213421721626611473&iid=5213421788431615506](http://picasaweb.google.co.uk/lh/viewPhoto?uname=llabhilash&aid=5213421721626611473&iid=5213421788431615506)



i also ran my firefox 2 as su.. and still the check for updates button was greyed out..

i fixed the java part now.. the link to libjavaplugin_oji.so (jre 6 u 6 ) that i hard created in firefox 3 plugins was not correct... now ff3 recognises java and jre 6 u 6 is running on firefox 3


i now have firefox 3 as my default browser but in synaptic its still firefox 2 thats installed as seen in the pic.. if i try to unsintall firefox.. many applications will be listed for removal



so how do i go about installing firefox 3 through synaptic ?

am i missing any of the repos?

---

### Post by jamesstansell on 2008-06-19
> **terrordrone said:**
> these are my software sources
...

so how do i go about installing firefox 3 through synaptic ?

am i missing any of the repos?

I had assumed you were running hardy.  Since you appear to be running gutsy, you probably want to add the gutsy-backports source.

Then install the firefox-3.0 package.

Offhand, it appears that for gutsy you may be expected to leave firefox 2 installed.  Sorry, I don't have a gutsy machine handy to play with this more.

---

### Post by terrordrone on 2008-06-19
> **jamesstansell said:**
> I had assumed you were running hardy.  Since you appear to be running gutsy, you probably want to add the gutsy-backports source.

Then install the firefox-3.0 package.

Offhand, it appears that for gutsy you may be expected to leave firefox 2 installed.  Sorry, I don't have a gutsy machine handy to play with this more.
sorry.. forgot to mention that... (didnt think it would matter :|)

i am on gutsy 

i put in gutsy-backports

backports has beta 4 of ff3
( 3.0~b4-nobinonly-0ubuntu1~gutsy1 )

should i go ahead and install that?

---

### Post by terrordrone on 2008-06-22
Any idea on when FF3 will come in ubuntu repositories ? (not in backports)

---

### Post by qrwe on 2008-06-23
I have some problems to get Firefox working with Sun Java. As I enter a site that runs a Java applet, it tells me to download the runtimes for one of several choices. I chose "The Java(TM) Plug-in, Java SE 6" and restarted FF. It didn't work, it still wants me to install the plug-in.
After trying in vain to install "...SE 5.0" and disable the GCJ module (which was useless in the first time for my needs), I followed the manual guide at java.com: it told me to do soft-links in the plugins/ directory. But :-(( It didn't work either

Has anyone had problems with this before?

---

### Post by terrordrone on 2008-06-23
> **qrwe said:**
> I have some problems to get Firefox working with Sun Java. As I enter a site that runs a Java applet, it tells me to download the runtimes for one of several choices. I chose "The Java(TM) Plug-in, Java SE 6" and restarted FF. It didn't work, it still wants me to install the plug-in.
After trying in vain to install "...SE 5.0" and disable the GCJ module (which was useless in the first time for my needs), I followed the manual guide at java.com: it told me to do soft-links in the plugins/ directory. But :-(( It didn't work either

Has anyone had problems with this before?
please post the output of 

1)whereis java

2)java -version

3)ls <firefox>/plugins

4)ls -l <firefox>/plugins/libjavaplugin_oji.so (if it exists)

is this ff3?

ill try to help someone for the first time :P

---

### Post by qrwe on 2008-06-23
Ah cool, I'll give you a chance then ;-)

1. Java lives in "/usr/lib/jvm/java-6-sun-1.6.0.06/"

2. "java -version"
java version "1.6.0"
OpenJDK Runtime Environment (build 1.6.0-b09)
OpenJDK Server VM (build 1.6.0-b09, mixed mode)

3. "ls /usr/lib/firefox-3.0/plugins/"
libflashplayer.so  libjavaplugin_oji.so  npica.so

Comment: libjavaplugin_oji.so is the soft-link I created.

4. See num 3.

Yes, it's FF3.

***

Added 2 minutes later:

Firefox seems to disable new manually added add-ons by default, so it was probably there the first time already. I simply went into the Add-ons tab and enabled it. Voíla!
Thanks anyway!

---

### Post by terrordrone on 2008-06-23
congratz..  happy that ff3 is workin fine ..

guess ill have to wait a lil longer to help out someone :P

---

