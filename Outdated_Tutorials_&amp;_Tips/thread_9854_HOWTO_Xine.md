---
title: "HOWTO: Xine"
date: 2005-01-02
forum: Outdated Tutorials &amp; Tips
---

### Post by wallijonn on 2005-01-02
Install SPM's XINE (xine-ui)

Start a Root Terminal

```

wget http://www.las.ic.unicamp.br/pub/debian-marillat/dists/unstable/main/binary-i386/libdvdcss2_1.2.8-0.0_i386.deb

dpkg -i libdvdcss2_1.2.8-0.0_i386.deb 

```

Slip in a DVD. Play.

---

### Post by earobinson on 2005-01-06
dident work for me i type xine in the terminal and nothing hapens why?

---

### Post by wallijonn on 2005-01-06
Because you didn't [COLOR=Red]Applications[/COLOR] ->[COLOR=Red] Media[/COLOR] -> [COLOR=Red]xine[/COLOR] ?

The steps are:

1] Open SPM ([COLOR=Red]Computer[/COLOR] -> [COLOR=Red]System Configuration [/COLOR]-> [COLOR=red] Synaptic Package Manager[/color])
2] Install xine-ui
3] exit SPM
4] Open a Root Terminal
5] get the codecs (copy/paste "wget" line into root terminal, hit return key)
6] install the codecs (copy past "dpkg" line into the root terminal, hit the return key)
7] exit the Root Terminal
8] [COLOR=Red]Applications[/COLOR] ->[COLOR=Red] Media[/COLOR] -> [COLOR=Red]xine[/COLOR]
9] If Totem starts up, just close it.
10] Push the "DVD" button on the xine player.

---

### Post by earobinson on 2005-01-06
Sorry i was being stupid, just started using ubuntu moved here from fedora core and things are a bit diferent its going to take some time.

---

### Post by wallijonn on 2005-01-06
Don't be so hard on yourself. We're all friends here. 

So, does it work?

---

### Post by earobinson on 2005-01-12
yes it works fine got my old xine back ubuntu is great and all but well its missing some of the things from fedora

---

### Post by ronss on 2005-01-13
my problem with installing xine, is that when i go into spm, click on multi-media-there is not xine to be installed. where are you findiing it

---

### Post by wallijonn on 2005-01-13
xine-ui is part of "Universe". You will have to enable the "Universe" Repositories.

---

### Post by jsgotangco on 2005-01-14
for some reason, not a single DVD worked in Xine in my setup...but it worked flawlessly in VLC...

---

### Post by wallijonn on 2005-01-14
js,

Why not write a VLC HOWTO?

---

### Post by ronss on 2005-01-14
well, i see universe base system. dont, see nothing about universe repositorys.

---

### Post by wallijonn on 2005-01-15
[http://www.ubuntuforums.org/showthread.php?t=179](http://www.ubuntuforums.org/showthread.php?t=179)

---

### Post by jshackles on 2006-04-25
[QUOTE=wallijonn]Install SPM's XINE (xine-ui)

Start a Root Terminal

```

wget http://www.las.ic.unicamp.br/pub/debian-marillat/dists/unstable/main/binary-i386/libdvdcss2_1.2.8-0.0_i386.deb

dpkg -i libdvdcss2_1.2.8-0.0_i386.deb 

```

Slip in a DVD. Play.[/QUOTE]
 ERROR 404: Not Found.

---

### Post by dmizer on 2006-06-29
> 07/05/2006 :
Why Marillat's repository doesn't work ? Because now the repository is here debian-multimedia.org
See at the bottom for news sources.list entries.
Now you can use the distro name or the alias name (stable --> sarge or etch --> testing).
looks like the link isn't valid anymore.  i'm still working on tracking it down ...
here's a mirror with a more current version too: [http://mirrors.optralan.com/videolan/debian/i386/](http://mirrors.optralan.com/videolan/debian/i386/)
or here: [http://ftp2.via.ecp.fr/pub/videolan/debian/i386/](http://ftp2.via.ecp.fr/pub/videolan/debian/i386/)

EDIT: sorry folks, i'm an idiot, not sure what kind of search landed me here, but i was definately not paying attention to the date on these posts.  terribly sorry. :-\"

---

### Post by wallijonn on 2006-07-03
Doing a Google search for [COLOR="Red"]libdvdcss[/COLOR] brought up [http://download.videolan.org/pub/libdvdcss/1.2.9/deb/](http://download.videolan.org/pub/libdvdcss/1.2.9/deb/)

---

### Post by doctor_shim on 2007-01-12
Hello there. I'm really trying hard to get DVD playback in Ubuntu. I followed the aforementioned instructions (xine-ui and libdvd2css), and Xine just says: 

"The source can't be read. Maybe you don't have enough rights for this or source doesn't contain data (e.g.: not disk in drive). (Encrypted or faulty DVD)"

I tried playing DVDs in VLC, and VLC just closes. I believe it is afraid of me.

Perhaps I should break down and cry. CRY LIKE THE BABY I AM.

---

### Post by wallijonn on 2007-01-26
What is your hardware, Intel or AMD, 32 bit or 64?

---

### Post by wallijonn on 2007-01-29
Have you tried Automatix?

[http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by TimTang on 2007-11-08
If anyone is interested, the file structure has been modified at the site given in the origional instructions.

As of today 08/11/07 use the following in the root terminal instead:

"wget http://www.las.ic.unicamp.br/pub/debian-marillat/pool/main/libd/libdvdcss/libdvdcss2_1.2.9-0.0_i386.deb"

without the quotes of coarse.

The second command remains the same except the version number should be 1.2.9-0.0; just change the 8 to a 9.

Cheers!

---

