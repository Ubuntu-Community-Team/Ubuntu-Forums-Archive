---
title: "Howto make mplayerplug-in work in opera 9.0"
date: 2006-05-31
forum: Outdated Tutorials &amp; Tips
---

### Post by agapito on 2006-05-31
After I got the new [Opera 9.0 beta 2]("http://www.opera.com/download/index.dml?ver=9.0b"), which is great, the mplayerplug-in stopped working.:-k  I searched everywhere, but didn't find a solution...
I was going crazy with this! ](*,)  Then I found a post in the Gentoo forum, and I managed to make it work!  \\:D/ I hope that this can save you a lot of trouble.

Ok, this is how it goes:

1. Download [Gecko-sdk 1.6]("http://ftp.mozilla.org/pub/mozilla.org/mozilla/releases/mozilla1.6/gecko-sdk-i686-pc-linux-gnu-1.6.tar.gz"), unpack it,  and put it somewhere.
```

cd $HOME
wget ftp.mozilla.org/pub/mozilla.org/mozilla/releases/mozilla1.6/gecko-sdk-i686-pc-linux-gnu-1.6.tar.gz
tar xvzf gecko-sdk-i686-pc-linux-gnu-1.6.tar.gz
sudo mv gecko-sdk /usr/local/gecko-sdk1.6

``` 
2. Get [mplayerplug-in v2.80]("http://prdownloads.sourceforge.net/mplayerplug-in/mplayerplug-in-2.80.tar.gz") from sourceforge (I tried other versions, but they did't work... maybe I did something wrong, but v2.80 works great, so why complicate? :) )

3. Go to the folder where you saved mplayerplug-in-2.80.tar.gz and do:
```

tar xvzf mplayerplug-in-2.80.tar.gz
cd mplayerplug-in/plugingate/
gedit np_entry.cpp

``` 
On lines 108 and 109 you have
```

if(aNPNFuncs->size < sizeof(NPNetscapeFuncs))          
      return NPERR_INVALID_FUNCTABLE_ERROR;

``` 
comment it out:
```

//if(aNPNFuncs->size < sizeof(NPNetscapeFuncs))          
//      return NPERR_INVALID_FUNCTABLE_ERROR;

``` 
save and exit gedit.

4. It's time to compile. Let's go up one dir, so that we're on "somedir"/mplayerplug-in/
```

cd ..
./configure --enable-x  --with-gecko-sdk=/usr/local/gecko-sdk1.6

``` 
If all went fine, now it's time to build it.
```

make

``` Copy mplayerplug-in.so to Opera's plugin dir:
(don't forget to remove any other mplayerplug-in you have there)
```

sudo rm -i /usr/lib/opera/plugins/mplayerplug-in*
cp -v mplayerplug-in.so /usr/lib/opera/plugins/

``` 
5. If you start Opera now, it will complain about some libraries, and the plug-in will fail. Let's take care of it, using gecko-sdk1.6's libs
[COLOR=Red]Edit: This works for me even in 6.06 without any kind of trouble, but some people are complaining that making these symbolic links brakes Firefox.
Try to use mplayerplug-in _without_ making the symbolic links bellow, and if you do make them _at least_  take note
of where the original symlinks (if any) point. (for example do,  ls -l /usr/lib/libplds4.so and write it down somewhere)[/COLOR]
```

cd /usr/lib/
sudo ln -svf /usr/local/gecko-sdk1.6/nspr/bin/libplds4.so .
sudo ln -svf /usr/local/gecko-sdk1.6/nspr/bin/libnspr4.so .
sudo ln -svf /usr/local/gecko-sdk1.6/xpcom/bin/libxpcom.so .

``` 

6. Now it should work but to be on the safe side, let's enable the debuging
options.
```

sudo gedit /usr/bin/opera

``` 
Add this lines after #!/bin/bash
```


# Debug plugins
export OPERA_PLUGINWRAPPER_DEBUG=10
export OPERA_KEEP_BLOCKED_PLUGIN=1

``` Save it and close gedit.

7. Now, start opera with the -debugplugin option
```

opera -debugplugin

``` 
Remove any additional paths from opera's plug-in path, or you may be using two confilcting versions of mplayerplug-in. Go to
Tools->Preferences->Advanced->Content->Plug-in Options
All I have in my plug-in path is this line:
```

/usr/lib/opera/plugins:/usr/lib/realplay-10.0.6.776/plugins:/usr/lib/realplay-10.0.6.776

``` since I install all the opera plug-ins to /usr/lib/opera/plugins/


Restart Opera the same way we did before and try to open a video. This one works for me, and hopefully for you too.
[http://www.apple.com/trailers/fox/ice_age_2/mediumteaser.html]("http://www.apple.com/trailers/fox/ice_age_2/mediumteaser.html") :D

8. Now you can remove the debug options in opera's wrapper
```

sudo gedit /usr/bin/opera

``` 
Add a # before the lines we added
```


# Debug plugins
#export OPERA_PLUGINWRAPPER_DEBUG=10
#export OPERA_KEEP_BLOCKED_PLUGIN=1

``` Save it and close gedit.


This post is based on this gentoo forum post:
[http://forums.gentoo.org/viewtopic.php?p=3297093]("http://forums.gentoo.org/viewtopic.php?p=3297093")

My thanks to Sloden, the author of the Gentoo post.

P.S.: I'm attaching the mplayer plug-in that I compiled (on breezy). This way, If you're having trouble "rolling our own", you can use mine and (with some luck) skip steps 2-4. Don't forget to do gunzip mplayerplug-in.so.gz
I tried to document all the steps, for those who need it.  For those who don't, sorry if this was too boring to read.

---

### Post by detyabozhye on 2006-06-26
**[COLOR="Red"]WARNING TO EVERYONE:[/COLOR]**
Do NOT do step 5 (symbolic links) if you have Firefox installed! The symbolic links will break your Firefox! Mplayer will work without the symbolic links.

I would recommend to use these Mplayer plugins instead: [http://my.opera.com/community/forums/topic.dml?id=131761&t=1151357109&page=1#comment1512034](http://my.opera.com/community/forums/topic.dml?id=131761&t=1151357109&page=1#comment1512034)

---

### Post by desperado666 on 2006-06-26
Neither the first nor the second mplayer plugin work on my opera 9 final dapper system....

---

### Post by detyabozhye on 2006-06-26
deleted post

---

### Post by CronoDekar on 2006-06-26
Not sure if I just lucked out or not, but on Dapper after putting gecko-sdk on my system gunzipping the attached file into my Opera plugins I didn't even need to set up the symlinks and it worked.  Oddly though, when I tried to build the plugin myself, make failed regardless of which version I tried.

---

### Post by detyabozhye on 2006-06-26
Doing the symbolic links broke Firefox on my system.

---

### Post by desperado666 on 2006-06-26
Nope sorry
It used to work but after installing some Opera9 builds ago it now refuses...dont know why...

---

### Post by sedatg on 2006-07-06
[QUOTE=agapito]
5. If you start Opera now, it will complain about some libraries, and the plug-in will fail. Let's take care of it, using gecko-sdk1.6's libs
[COLOR=Red]Edit: This works for me even in 6.06 without any kind of trouble, but some people are complaining that making these symbolic links brakes Firefox.
Try to use mplayerplug-in _without_ making the symbolic links bellow, and if you do make them _at least_  take note
of where the original symlinks (if any) point. (for example do,  ls -l /usr/lib/libplds4.so and write it down somewhere)[/COLOR]
```

cd /usr/lib/
sudo ln -svf /usr/local/gecko-sdk1.6/nspr/bin/libplds4.so .
sudo ln -svf /usr/local/gecko-sdk1.6/nspr/bin/libnspr4.so .
sudo ln -svf /usr/local/gecko-sdk1.6/xpcom/bin/libxpcom.so .

``` [/QUOTE]

I did create those symbolic links without writing the original pointed locations down. Anyone can help me out with restoring these?
Firefox is silently failing on Dapper, with this error in te console: ```
$ firefox
/usr/lib/firefox/firefox-bin: symbol lookup error: /usr/lib/firefox/components/libdocshell.so: undefined symbol: PR_GetPhysicalMemorySize
```

---

### Post by detyabozhye on 2006-07-06
reinstall libnspr4 and if it still doesn't work reinstall Firefox as well.
Note: reinstalling Firefox alone won't fix it, you must reinstall libnspr4.

BTW, the original .so files that Firefox depends on are not symlinks, they are actual .so files, they are deleted when you make the symlinks in step 5.

---

### Post by Jasper Houtman on 2006-07-09
I installed the plugin as instructed and it works fine except for one thing.
I only get sound when playing wmv files (no video).
I can play them without any problem in firefox.

Does anyone know how to fix this?

---

### Post by citizenr on 2006-07-09
> **CronoDekar said:**
> Not sure if I just lucked out or not, but on Dapper after putting gecko-sdk on my system gunzipping the attached file into my Opera plugins I didn't even need to set up the symlinks and it worked.

me too :), no graphical controls tho :(

> **Jasper Houtman said:**
> I installed the plugin as instructed and it works fine except for one thing.
I only get sound when playing wmv files (no video).
I can play them without any problem in firefox.

Does anyone know how to fix this?

sure we know, the source of a ptoblem is between the keyboard and a monitor, you didnt even gave us EXAMPLE OF NOT WORKING embedded wmv file ...

---

### Post by SSamiK on 2007-02-02
Installed Feisty Fawn Herd3 today, and by following this howto, step 1-4, I got mplayerplug-in to work in Opera 9.10. 
Had a little bump in the road at "make" with a  "error: #error libXpm has not been found. Compilation cannot continue", witch was solved by installing libxpm-dev. 

Works great! :guitar:

---

