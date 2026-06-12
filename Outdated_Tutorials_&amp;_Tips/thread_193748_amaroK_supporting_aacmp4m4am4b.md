---
title: "amaroK supporting aac/mp4/m4a/m4b"
date: 2006-06-10
forum: Outdated Tutorials &amp; Tips
---

### Post by jamo on 2006-06-10
Hi folks,

with amaroK version 1.4.0 support for iPod's has become stable and very convenient. 
On thing I missed was the lack of support for aac/mp4 tag reading and writing.
What I did was to rebuilt the official packages from the kubuntu repository with mp4-support.
Secondly I applied a patch to xine to get it recognize .m4b-files.
Now all my audiobooks play fine with amaroK.

#####
Quick install notes:
- you need libexscalibar1 (see my 2nd post)
- grab the following packages:
  amarok, amarok-engines, amarok-xine and libxine-main1
  (you only need libxine-dev if you want to compile software by yourself)
- cd to the folder with the debs and type "sudo dpkg -i *.deb"
#####

All files including my package signing key can be found [here]("http://user.cs.tu-berlin.de/~jadero/ubuntu/").
Feedback is highly welcome.

Have fun,
Jan

---

### Post by foofightrs777 on 2006-06-10
This has seemed to work perfectly for me.  Thank you!!  Perhaps in the future though include more instructions.  For those wondering what to do with the packages I moved them into a folder.  Then from terminal cd to that directory and 'sudo dpkg -i *'.

---

### Post by accensi on 2006-06-11
Some dependencies like libexscarab1 or libpq4 version 8.1.4 are not available in Ubuntu repositories and must be searched on alternate locations, Debian testing or unstable, etc.

---

### Post by jamo on 2006-06-11
Right, libexscalibar1 is not part of official dapper (still amarok version 1.3.9). This package is essential for the new moodbar feature. 
It can be found on the official amaroK ([http://amarok.kde.org]("http://amarok.kde.org")) page under "Download Amarok"->"1.4.0a for Dapper Drake (official)". Just follow the instructions given on this page or download the missing pakages [here]("http://kubuntu.org/packages/amarok-14/pool-dapper/"). libpq4 8.1.4 is in dapper-security, you probably need to tweak your sources.list (uncomment the repository).

---

### Post by GoA on 2006-06-11
This is a howto section. Your howto doesn't tell users howto do it by them selves so please improve it to make it more understandable.

EDIT: Ups, shouldn't post when your tired. All the working debs seems to be n your server. :D

---

### Post by Sir_Yaro on 2006-06-11
great job jamo!
Your compilation works much faster and stable for me. :)

---

### Post by digimars on 2006-06-12
Uhm, new to this stuff.  How (and in what order) should I install these?

---

### Post by digimars on 2006-06-12
[QUOTE=foofightrs777]This has seemed to work perfectly for me.  Thank you!!  Perhaps in the future though include more instructions.  For those wondering what to do with the packages I moved them into a folder.  Then from terminal cd to that directory and 'sudo dpkg -i *'.[/QUOTE]

This broke my amarok installation.  It won't even let me uninstall it now so that I  could attempt to reinstall it.

```

kenny@Archimedes:~$ sudo apt-get remove amarok
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  amarok-engines: Depends: amarok (= 2:1.4.0a-0ubuntu2~AAC) but it is not going to be installed
  amarok-xine: Depends: amarok (= 2:1.4.0a-0ubuntu2~AAC) but it is not going to be installed
  libxine-dev: Depends: libxv-dev but it is not going to be installed
               Depends: libxvmc-dev but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```


UPDATE
was able to finally remove amarok, and reinstall it.  However, installing these files breaks mine.

---

### Post by jamo on 2006-06-16
@digimars:
Can you tell me what happened when you installed my packages, please.

---

### Post by digimars on 2006-06-16
[QUOTE=jamo]@digimars:
Can you tell me what happened when you installed my packages, please.[/QUOTE]

Sure, it gave me the same error as above when I was trying to install all of the packages that I found on your site.  And after I did get them installed, amarok just wouldn't run.  So I went back through and took all of those back off, and reinstalled amarok from the repos.

Let me ask you something, does your packaged version still use the aRTs sound system, or something else native to Gnome?

---

### Post by jamo on 2006-06-16
The only supported sound backend is xine. You only need libxine-dev if you want to build the amaroK package (and others) by yourself. Just install amarok, amarok-engines, amarok-xine and libxine-main1. Don't forget to install libexscalibar1 from the source mentioned in my second post.

---

### Post by digimars on 2006-06-16
Sweet, got it working now.

You said that you got your audiobooks to work in this?  How did you do that?

---

### Post by malegria on 2006-06-16
Just installl amarok & the libxine-extracodecs and use xine as the engine for the sound.

All sould work then.

---

### Post by hopstah on 2006-06-26
which one is the patch to xine that you mentioned that will give m4b support?  that's all I need right now.

thanks

---

### Post by Hairy_Palms on 2006-06-26
you know its much easyer to just install amarok from the instructions at [http://kubuntu.org/announcements/amarok-1.4.php](http://kubuntu.org/announcements/amarok-1.4.php) has mp4 taglib and playback support

---

### Post by jamo on 2006-06-26
[QUOTE=hopstah]which one is the patch to xine that you mentioned that will give m4b support?  that's all I need right now.

thanks[/QUOTE]
You can find the patch [here]("http://itdp.fh-biergarten.de/~itdp/html/Xine-devel/2006-05/msg00066.html").
I used dpatch for the patching process and changed the file to my needs:
```
#!/bin/sh /usr/share/dpatch/dpatch-run

@DPATCH@

diff -Naur xine-1.1.1.orig/src/demuxers/demux_qt.c xine-1.1.1/src/demuxers/demux_qt.c
--- xine-lib-1.1.1.orig/src/demuxers/demux_qt.c
+++ xine-lib-1.1.1/src/demuxers/demux_qt.c
@@ -3047,13 +3047,13 @@ static char *get_identifier (demux_class
 }
 
 static char *get_extensions (demux_class_t *this_gen) {
-  return "mov qt mp4 m4a";
+  return "mov qt mp4 m4a m4b";
 }
 
 static char *get_mimetypes (demux_class_t *this_gen) {
   return "video/quicktime: mov,qt: Quicktime animation;"
          "video/x-quicktime: mov,qt: Quicktime animation;"
-         "audio/x-m4a: m4a: MPEG-4 audio;"
+         "audio/x-m4a: m4a,m4b: MPEG-4 audio;"
          "application/x-quicktimeplayer: qtl: Quicktime list;";
 }
```
Have fun!

---

### Post by hopstah on 2006-06-27
ok, i'm still kind of new at linux, but i'm trying.  and this is what i tried per your last post:
```

andy@lettuce:~$ /bin/sh /usr/share/dpatch/dpatch-run /home/andy/m4bpatch -patch
can't find file to patch at input line 5
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|Index: xine-lib-1.1.2cvs20060328/src/demuxers/demux_qt.c
|===================================================================
|--- xine-lib-1.1.2cvs20060328.orig/src/demuxers/demux_qt.c
|+++ xine-lib-1.1.2cvs20060328/src/demuxers/demux_qt.c
--------------------------
No file to patch.  Skipping patch.
1 out of 1 hunk ignored

```
am i going to have to recompile anything?  or is this just making changes in text files that I could do myself?

thanks!

---

### Post by jamo on 2006-06-27
[QUOTE=hopstah]ok, i'm still kind of new at linux, but i'm trying.  and this is what i tried per your last post:
```

andy@lettuce:~$ /bin/sh /usr/share/dpatch/dpatch-run /home/andy/m4bpatch -patch
can't find file to patch at input line 5
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|Index: xine-lib-1.1.2cvs20060328/src/demuxers/demux_qt.c
|===================================================================
|--- xine-lib-1.1.2cvs20060328.orig/src/demuxers/demux_qt.c
|+++ xine-lib-1.1.2cvs20060328/src/demuxers/demux_qt.c
--------------------------
No file to patch.  Skipping patch.
1 out of 1 hunk ignored

```
am i going to have to recompile anything?  or is this just making changes in text files that I could do myself?

thanks![/QUOTE]
This file patches parts of the source code so yes, you have to recompile anything afterwards.

What version of xine have you tried to patch?

Cheers!

PS: Patching of source and building new debian packages is an advanced topic. Maybe you should try "ready-to-install" packages instead of building them by yourself?

---

### Post by hopstah on 2006-06-27
i would agree with you - do you know of any ready-to-install packages that will take care of this for me?  it all seems pretty insane that you need to recompile from source to get audio programs to recognize a file encoded with an identical codec, but has just a different extension.  you know what i mean?

thanks for your help so far!

---

### Post by malegria on 2006-06-27
Just install libxine-extracodecs !!!

---

### Post by hopstah on 2006-06-28
i appreciate the input, but your reading comprehension is getting a bit rusty.  the converstaion has turned to getting amarok to recognize **m4b** files, which are itunes/ipod audiobooks, which an ipod recognizes differently than other audio files.

---

### Post by sinaen on 2006-09-24
well i have tried everything but i dont have aac compability in amarok. i want it also for the ipod m4a and m4b files i do have. the strangest thing is that i had it before somehow.
Edit:
i tried install libxine-extracodecs but that didnt do the thing for me. so its something else.. :p ill dl and install your debs. and cross my fingers that it works. but i have my doubts :P

---

### Post by sinaen on 2006-10-03
> **jamo said:**
> Hi folks,

with amaroK version 1.4.0 support for iPod's has become stable and very convenient. 
On thing I missed was the lack of support for aac/mp4 tag reading and writing.
What I did was to rebuilt the official packages from the kubuntu repository with mp4-support.
Secondly I applied a patch to xine to get it recognize .m4b-files.
Now all my audiobooks play fine with amaroK.

#####
Quick install notes:
- you need libexscalibar1 (see my 2nd post)
- grab the following packages:
  amarok, amarok-engines, amarok-xine and libxine-main1
  (you only need libxine-dev if you want to compile software by yourself)
- cd to the folder with the debs and type "sudo dpkg -i *.deb"
#####

All files including my package signing key can be found [here]("http://user.cs.tu-berlin.de/~jadero/ubuntu/").
Feedback is highly welcome.

Have fun,
Jan


O yeah! it did not work at all for me to get the m4b working or playing or into the ipod.
some audio files does not want to transfer completely.
when i installed your packages i downgraded amarok and it refused to start.
Edit: and i have libxine-extracodecs :P 
 I Have had m4b support in amaroks former versions :( but i dont remember which one

---

### Post by sinaen on 2006-11-20
bump?
i would rather like to get m4a/m4b support in amarok and havent found anything on how to get it exept yours and it didnt work

---

### Post by hopstah on 2006-12-07
> **sinaen said:**
> bump?
i would rather like to get m4a/m4b support in amarok and havent found anything on how to get it exept yours and it didnt work

the most recent xine update allows amarok to play m4b files, and i also believe they can be added to the library.  m4a support has been in amarok for a while now.

---

### Post by sinaen on 2006-12-16
> **hopstah said:**
> the most recent xine update allows amarok to play m4b files, and i also believe they can be added to the library.  m4a support has been in amarok for a while now.

now i have an broken amarok :) lets see next time i update if its fixed :p

---

### Post by ajm2005 on 2006-12-16
:)

---

### Post by sinaen on 2007-10-09
I have amarok worknig now. 
but i do not know if this supposed extra support for m4a/b files is to get me tag editing cababilitis which i would indeed like to have

---

### Post by musicinmybrain on 2007-12-30
Try Ex Falso for tag editing.

---

