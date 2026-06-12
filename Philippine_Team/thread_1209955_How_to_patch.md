---
title: "How to patch"
date: 2009-07-10
forum: Philippine Team
---

### Post by jerryheavyarms on 2009-07-10
Mga Sir,
Magandang Araw po!
Tanong ko lang po kung panu magpatch ng Proftpd. Kasi po naginstall na po ako ng Proftpd 1.3.1 sa Ubuntu 8.04 LTS. Ang problema po yung pagdisplay ng Japanese fonts sa Windows boxes. May patch po ako na nakita:
[http://home.h01.itscom.net/para/software/misc/proftpd-iconv/index-e.html](http://home.h01.itscom.net/para/software/misc/proftpd-iconv/index-e.html)
[http://orz.miroq.info/wp-download.php?file=proftpd-1.3.1-iconv.patch.gz](http://orz.miroq.info/wp-download.php?file=proftpd-1.3.1-iconv.patch.gz)

Ang problema ko po, hindi ko po alam kung san magsisimula. Akala ko po kasi parang Windows lang na dodouble-click lang, ayos na.
Nai-google ko na rin po pero kung may tips po kayo or step by step instruction na pwede ko po i-try.

Maraming Salamat po!:p

---

### Post by loell on 2009-07-10
get the source form hardy repo,

```
apt-get source proftpd
```

put the patch file to the current directory then first do a patch dry run ;)

```
patch -p0 < patchname.patch --dry-run
```

if no error occurs then omit the dry run parameter.

---

### Post by markedisonchua on 2009-07-11
Wow

---

### Post by jerryheavyarms on 2009-07-11
Sir Loell, salamat po sa pagreply.:smile:
Inaply ko na po, eto po yung lumabas:

patching file proftpd-1.3.1/modules/mod_codeconv.c
patching file proftpd-1.3.1/modules/mod_df.c
can't find file to patch at input line 370
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff -Naru proftpd-1.3.1/modules/mod_ls.c proftpd-1.3.1.iconv/modules/mod_ls.c
|--- proftpd-1.3.1/modules/mod_ls.c	2007-09-28 09:53:59.000000000 +0900
|+++ proftpd-1.3.1.iconv/modules/mod_ls.c	2008-02-04 12:05:38.208142485 +0900
--------------------------
File to patch:

Anu po ba yung file na hinahanap dito? Pasensya na po ah..
Maraming Salamat po!O:)

---

### Post by loell on 2009-07-11
ah ok, sinubukan ko. :p

ilagay mo na lang ang patch file sa proftd source directory, ito ang command at ito din dapat ang lalabas


> loell@loell-desktop:~/development/proftpd-dfsg-1.3.1$ **patch -p1 < proftpd-1.3.1-iconv.patch **
patching file modules/mod_codeconv.c
patching file modules/mod_df.c
patching file modules/mod_ls.c
patching file src/netio.c
loell@loell-desktop:~/development/proftpd-dfsg-1.3.1$ 

---

### Post by zakame on 2009-07-11
Patching is half of the problem.  The other part comes at getting the build dependencies and repackaging the software so aptitude can install it.

Roughly, that would mean something like:

```

# apt-get build-dep proftpd
# apt-get install build-essential devscripts
$ cd <proftpd-source-dir>
$ dpkg-buildpackage -us -uc # or debuild
...
# dpkg -S proftpd...deb

```

---

### Post by Script Warlock on 2009-07-12
ganun lang pala magpatch timing may patch para  sa timer.....

---

### Post by jerryheavyarms on 2009-07-12
Sir Loell, Sir Zakame, Sir Script Warlock,

Maraming Salamat po sa inyo. Subukan ko po ito baka bukas na po. But I will post back kung anu man po results.

ThANks a lot!:lolflag:

---

### Post by jerryheavyarms on 2009-07-13
Sir Loell,
> 
loell@loell-desktop:~/development/proftpd-dfsg-1.3.1$ patch -p1 < proftpd-1.3.1-iconv.patch
patching file modules/mod_codeconv.c
patching file modules/mod_df.c
patching file modules/mod_ls.c
patching file src/netio.c
loell@loell-desktop:~/development/proftpd-dfsg-1.3.1$ 


ganito nga po yung lumabas. Pagkatapos po nito, proceed na po ba ako dun sa post ni sir Zakame? Or pwede na po ako mag ./configure, make, make install?

thanks a lot po!:)

---

### Post by loell on 2009-07-13
yeah, either will do. 

but zakame's method will generate a deb pakage, so better.


[SIZE="1"]at alam mo bang.. minsan lang si zachy mag-post :mrgreen:, so be honored, you're lucky.. :mrgreen:[/SIZE]

---

### Post by jerryheavyarms on 2009-07-13
Thanks po sir Loell!

Bale sinubukan ko po yung parehong method pero sa magkaibang station po. Check ko po kung magdidisplay na yung Kanji sa Windows box.

Maraming Salamat po uli sir Loell at Sir Zakame:lolflag:

---

### Post by jerryheavyarms on 2009-07-13
Sir Loell, Sir Zakame,

Ganun pa rin po eh. Ayaw pa rin pong magdisplay ng Japanese FOnts. May suggestions po ba kayo na alternative sa Proftpd na may Japanese Fonts support?

Thanks a lot po!

---

### Post by loell on 2009-07-13
do you really want fonts?

or are  you looking for Japanese character sets?
if so,have you followed this? [http://home.h01.itscom.net/para/software/misc/proftpd-iconv/index-e.html]("http://home.h01.itscom.net/para/software/misc/proftpd-iconv/index-e.html")

you can also use wu-ftpd  [http://www.debianhelp.co.uk/wuftp.htm]("http://www.debianhelp.co.uk/wuftp.htm")


or maybe, it's not displaying japanese because you have not set the "locale".

---

### Post by jerryheavyarms on 2009-07-13
Sir loell yung sa "locale", yun po ba yung sa Preferences > Languages? Nai-set ko na po yung Japanese Language Support dun eh.

Nailagay ko na rin po yung CharsetRemote at CharsetLocal dun sa proftpd.conf eh.

Mga japanese po kasi clients namin at yun po yung kinukuhanan nila ng delivery data namin.

Siguro magsimula nlng po uli ako sa scratch mya. Check ko po yung sa wu-ftp.

Pasensya na po mga sir, totally noobie, hehe!
Maraming salamat po!

Hindi rin po ako makapag recommend ng FTP client. Mahirap po kasi sila turuan ng iba sa nakasanayan nilang Windows Explorer,:)

---

### Post by loell on 2009-07-13
i see,

try installing **ttf-kochi-mincho**


probably restart, see if there's any change.

---

### Post by jerryheavyarms on 2009-07-13
Sir Loell,
Maraming Salamat po uli. Try ko po myang gabi, pagpasok ko. graveyard eh, hehe! Salamat po sa assistance..:p

---

