---
title: "Python Plugin calling for something that doesn't exist"
date: 2006-04-29
forum: Programming Talk
---

### Post by BoboChimp on 2006-04-29
OK, i don't know too much at all about programming.  this is probably simple for some of you out there.  

I'm trying to get a plugin in a music player called quod libet working.  it is a plugin that uses the [musicbrainz/]("http://musicbrainz.org/") client library to access their online database to tag music.  

the python file that you are supposed to inset into the plugin directory has this line:
```
import musicbrainz, os, gtk

```

Quod Libet is giving this error:
Traceback (most recent call last):
  File "~/.quodlibet/plugins/brainz.py", line 4, in ?
    import musicbrainz, os, gtk
ImportError: No module named musicbrainz

I got the source from the muzicbrainz site then did ./configure, make, make install.  it all went off without a hitch so i figure everything installed correctly but i still get this error.

anyone know what i should do or where i should start looking for answers?

---

### Post by jpkotta on 2006-04-30
Now, I don't know Python that well, but I've played with it a little.  Find out where the musicbrainz module is (probably called musicbrainz.pyo).  Then make sure it's in your PYTHONPATH environment variable.  Say that musicbrainz is in /usr/lib/musicbrainz.  Then 
```
export PYTHONPATH=$PYTHONPATH:/usr/lib/musicbrainz
quod_libet
```
or how ever you start the music player.

There is almost surely a way to do the same thing in the Python code rather than setting an environment variable.

---

### Post by BoboChimp on 2006-04-30
do all python modules use the extension .pyo?  i searched for all files including the text "musicbrainz" and none of them carry the extension .pyo.  

what else might i be looking for?

---

### Post by luks on 2006-04-30
[QUOTE=BoboChimp]anyone know what i should do or where i should start looking for answers?[/QUOTE]

```
sudo apt-get install python-musicbrainz
```

---

### Post by BoboChimp on 2006-05-01
tried it.  got this.
```
Package python-musicbrainz is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

```

searched synaptic for "musicbrainz" in the name and didn't see it.  i have these repos active in sources.list:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb [http://users.lichtsnel.nl/~seveas](http://users.lichtsnel.nl/~seveas) breezy-seveas all
deb-src [http://users.lichtsnel.nl/~seveas](http://users.lichtsnel.nl/~seveas) breezy-seveas all
deb [http://issaris.be/breezy](http://issaris.be/breezy) ./

am i missing a repo????

---

### Post by hugmenot on 2006-05-01
[QUOTE=BoboChimp]tried it.  got this.
[...]
am i missing a repo????[/QUOTE]

Salve Bobo, did you miss my reply to your PM?

I mentioned that python-.musicbrainz has a new name under Dapper which is python-tunepimp. Install that package instead.

I explained for the breezy package becasue your sig stated you were using that, so...

---

### Post by BoboChimp on 2006-05-01
sorry hugmenot.  i read your PM but didn't get a chance to act on it at the time.  later i read luks' reply and acted on it.

thanks for reminding me to update my profile.  i just switched to Dapper beta over the weekend.  i'll python-tunepimp once i get home later tonight.

---

### Post by luks on 2006-05-01
[QUOTE=hugmenot]I mentioned that python-.musicbrainz has a new name under Dapper which is python-tunepimp. Install that package instead.[/QUOTE]

Ehm, no ;) python-tunepimp are Python bindings for libtunepimp. python-musicbrainz are Python bindings for libmusicbrainz. two different libraries.

Looks like python-musicbrainz was removed because it should be 'main' (because the older version from breezy was in 'main'), while one of it's dependencies (python-ctypes) is in 'universe'.

---

### Post by luks on 2006-05-01
Use python-musicbrainz from this repository:

```
deb http://users.musicbrainz.org/~luks/ubuntu dapper main
```

---

### Post by BoboChimp on 2006-05-05
well luks, i'm just now getting back to this.  i added the repo you suggested and i get this when trying to apt-get install python-musicbrainz

```
The following packages have unmet dependencies:
  python-musicbrainz: Depends: python2.4-musicbrainz but it is not going to be installed
E: Broken packages

```

i did update before trying to install.

any ideas?

---

### Post by luks on 2006-05-05
Oops! Sorry. Should be fixed now.

---

### Post by hounddog32 on 2006-07-03
I tried to do the same and found that I need a public key for the server for Dapper to allow me to use the repo - can you help?

---

### Post by wzzrd on 2006-07-03
A key would be nice indeed. The problem was only halfway solved here btw. I now get 
> 
Traceback (most recent call last):
  File "/usr/share/quodlibet/plugins/brainz.py", line 5, in ?
    from musicbrainz.queries import *
ImportError: No module named querie

---

### Post by michael@iconoclast.net on 2006-09-20
For what it's worth, by adding the luks repository I was able to get python-musicbrainz installed, and subsequently the musicbrainz plugin for 
ex falso. (I assume quod libet works as well since it's the same plugin, but I haven't tried to actually play music through it, I'm just happy to finally find a decent tagger with musicbrainz support.)
I don't know what this means for dapper, but so far things are looking good for edgy (with the luks repository added on).  Hopefully, somehow the requisite packages will make their way back into the regular repository.

---

### Post by atasaRossios on 2006-12-12
You sould try also quod libet is fantastic music player and manager.
Plus all things you do with ex falso you can do them directly from the player itself.

For me this sould be the default player for Ubuntu.
Is in versio 0.23 and rocks
The guys are doing great job.
I had 86 Gb external disk with music in a complete mess and qoud libet save
me really.
By just deleting, renaming, updateting tags, downloading alboum arts while licening to the music in fact in my own time.
Really cool.

---

