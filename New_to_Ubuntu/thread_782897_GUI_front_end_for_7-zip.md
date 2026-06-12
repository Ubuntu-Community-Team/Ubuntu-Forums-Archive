---
title: "GUI front end for 7-zip?"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by H.Callahan on 2008-05-05
I installed 7-zip and hunted around for it everywhere on the desktop until I realized it was a CLI utility.  Is there a GUI front end for it somewhere?

---

### Post by Monicker on 2008-05-05
You should be able to do it from the Nautilus file browser.  Right click on a file or folder, and you should have 7zip listed in the archive options.

---

### Post by rolandixor on 2008-05-05
really???

---

### Post by H.Callahan on 2008-05-06
I, too, have been unable to do this.  Did I miss something in the install?

---

### Post by eternicode on 2008-05-06
Check out PeaZip, [http://peazip.sourceforge.net/](http://peazip.sourceforge.net/) .  Not exactly the same as the windows version of 7-Zip, but it works.

---

### Post by billgoldberg on 2008-05-06
7zip (and 7zip-full) use "archive manager" as their gui.

You won't find the program "7zip" anywhere.

Just right-click a file and extract it, or use "archive manager" to make archives.

---

### Post by Krumar on 2008-05-06
If you have installed 7zip, you should be able to click on any file or folder that you want to compress and select "Create Archive". In the Create Archive window you get the chance to name the archive and select the compression type. 7 zip should come up as .7z. For more control you may want to go to System -> Preferences -> Main Menu. In this window you can click on Accessories then enable Archive Manager. This will give you a gui front end to all compression methods on your computer.

Krumar

---

### Post by H.Callahan on 2008-05-06
> **billgoldberg said:**
> 7zip (and 7zip-full) use "archive manager" as their gui.

You won't find the program "7zip" anywhere.

Just right-click a file and extract it, or use "archive manager" to make archives.

Ok, I am confused.  I installed 7-zip.  I went to a .rar file in Nautilus and clicked on it.  I was told that the Archives Manager did not support the compression type (or words to that effect).

I then looked for 7-zip in the Applications Menu and couldn't find it.  Finally figured (from the man pages) that it was a CLI interface.

Went to the terminal, cd'ed to the right directory and used the CLI to extract from the same .rar file.  Worked perfectly.

I am not against using the CLI to do such things, but I have grown lazy in my old age and haven't used a CLI archiver since the old pkzip days with DOS.

---

### Post by Steveway on 2008-05-06
For .rar you need rar and unrar-nonfree.
7-Zip is for .7z files.
Isn't that kinda obvivious?

---

### Post by Krumar on 2008-05-06
If you want a gui frontend to any of these archive formats you should use Archive Manger which will support compressing and extracting any archival formats you have installed on your system, remember everything is pretty modular in linux, when you install .7zip you get support for 7zip, when you install unrar-free you get support for .rar files

---

### Post by H.Callahan on 2008-05-06
> **Steveway said:**
> For .rar you need rar and unrar-nonfree.
7-Zip is for .7z files.
Isn't that kinda obvivious?

> **Krumar said:**
> If you want a gui frontend to any of these archive formats you should use Archive Manger which will support compressing and extracting any archival formats you have installed on your system, remember everything is pretty modular in linux, when you install .7zip you get support for 7zip, when you install unrar-free you get support for .rar files

Ok, but why does the package manager describe 7-zip as being able to handle (in addition to .7z files) zip, rar and several other formats and why does 7zip when run from the CLI actually extract the files from the .rar file that I ran it against?

---edit
Sorry, I reread this and I think I am coming off a little bit righteous.  I didn't intend to come off that way.  I am just trying to figure out how this all works.  It kinda makes sense to have individually installable archive support, but I thought 7-zip would give everything *I* needed it to me in one step.  ...and it seems that the command line version does.

---

### Post by cb951303 on 2008-05-06
> **H.Callahan said:**
> Ok, but why does the package manager describe 7-zip as being able to handle (in addition to .7z files) zip, rar and several other formats and why does 7zip when run from the CLI actually extract the file from the .rar file that I ran it against?

you are talking about the 7-zip windows application. It's a file archiver supporting many formats. It's also the creator of 7z format. But it doesn't have a linux version. In linux all archive formats have their own applications. so 7zip is for .7z files and unrar is for .rar files etc...

---

### Post by Krumar on 2008-05-06
Did you install p7zip-rar? I've just installed that on my system, but with it i was unable to extract rar files using the guis, i don't know why it doesn't want to work that way, but if you just install unrar-free, you can using Archive Manger for rar files. If your coming from a windows background, you may be familair with the 7 zip program which can extract rars, but through the package manager your installing support for the .7z format, not the 7 zip program.

---

### Post by bodhi.zazen on 2008-05-06
You might want to look at file roller :

[http://fileroller.sourceforge.net/features.html](http://fileroller.sourceforge.net/features.html)

> File Roller is an archive manager for the GNOME environment.

With File Roller you can:

    * Create and modify archives.
    * View the content of an archive.
    * View a file contained in the archive.
    * Extract files from the archive.

File Roller is only a graphical interface to archiving utilities such as tar and zip. Supported archive types include :

    * Tar archives uncompressed (.tar) or compressed with
          o gzip (.tar.gz , .tgz)
          o bzip (.tar.bz , .tbz)
          o bzip2 (.tar.bz2 , .tbz2)
          o compress (.tar.Z , .taz)
          o lzop (.tar.lzo , .tzo)
    * Zip archives (.zip)
    * Jar archives (.jar , .ear , .war)
    * Lha archives (.lzh)
    * Rar archives (.rar)
    * Zoo archives (.zoo)
    * Arj archives (.arj)
    * AR archives (.ar)
    * Debian archives (.deb) (Read-only mode)
    * RPM archives (.rpm) (Read-only mode)
    * 7-zip archives (.7z)
    * ISO files (.iso) (Read-only mode)
    * Stuffit archives (.bin, .sit)
    * Single files compressed with gzip, bzip, bzip2, compress, lzop

It's in the repos :

[http://packages.ubuntu.com/hardy/file-roller](http://packages.ubuntu.com/hardy/file-roller)

---

### Post by H.Callahan on 2008-05-06
The package was 7zip-full.  And directly from the description in the Synaptic package manager:

```
7z and 7za file archivers with high compression ratio
p7zip is the Unix port of 7-Zip, a file archiver that archives with
very high compression ratios.

p7zip-full provides:
 - /usr/bin/7za
    a standalone version of the 7-zip tool that handles 7z archives
    (implementation of the LZMA compression algorithm) and some other
    formats.
 - /usr/bin/7z
    [b]not only does it handle 7z but also ZIP, Zip64, CAB, RAR, ARJ,
    GZIP, BZIP2, TAR, CPIO, RPM, ISO and DEB archives[/b]. 7z compression
    is 30-50% better than ZIP compression.

p7zip provides 7zr, a light version of 7za, and p7zip a gzip like
wrapper around 7zr.
```(Note: Bolded area was bolded by me for emphasis.)

---

### Post by Krumar on 2008-05-06
I'm not sure why 7zip lists all those formats, might be that you can use all of them if you want to use the command line and perhaps the 7zip program itself, but I do most of my archives in the GUI and I find that I have the best luck when I install the format that I want to use. That's about all I know on this subject.

---

### Post by H.Callahan on 2008-05-06
It actually DOES work from the command line.  I was able to use it successfully there on about 10 files that I had that I wanted to unarchive.  That is the reason for the original request as I was suprised that it wasn't a GUI as the Windows version was.  Most Windows archivers handled a number of non-native formats in their GUI versions.  I thought that given the popularity of the Windows 7-zip program, that someone probably had front-ended the CLI by now.

I am just confused at all the answers seeming to indicate that it should work with the Archive Manager, but in fact doesn't.  I, obviously, am misunderstanding something basic here and I am trying to figure out what it is, so I will be .000001% less noobish than I am now.

I will also be looking at the other alternatives listed here.  (Thanks everyone)

---

### Post by joe57005 on 2008-05-17
7z is the only way i can uncompress rar archives. i just hit 'open with custom commant' and type "7z e" so every time i double-click an rar archive, it automatically unarchives it. (but to my home folder, until i can fix that)

---

### Post by Ux64 on 2008-06-08
I'm still looking for proper archival tool. I prefer archive format to be 7-zip. But I haven't found proper GUI yet.

PeaZip might be it (?), but unfortunately it's not available from Synaptic.

File Roller ahem, "works" yeah. But it's very basic. You can't set any options using it. So I usually use CLI. But it would be very nice to have working GUI.

Btw. Nobody said anything about [Q7Z]("http://k7z.sourceforge.net/7Z/Q7Z/").

---

### Post by bruce89 on 2008-06-08
Of course, people ought to use *lzma* (which is the UNIXy varient of the 7z format). It's the same as *gzip* and *bzip2*, you can only compress single files, which is what *tar* is for.

---

### Post by bapoumba on 2008-06-08
I installed p7zip from the universe repos and use it from the archive manager (right clic on the archive, or on a file you want to make an archive with).

---

### Post by hyl4me on 2008-07-01
> **joe57005 said:**
> 7z is the only way i can uncompress rar archives. i just hit 'open with custom commant' and type "7z e" so every time i double-click an rar archive, it automatically unarchives it. (but to my home folder, until i can fix that)

Late to the game, but....try search for "q7z" in repo.

---

### Post by davidsrsb on 2008-07-01
7zip for Windows works for me under Wine

---

### Post by billgoldberg on 2008-07-01
> **H.Callahan said:**
> Ok, but why does the package manager describe 7-zip as being able to handle (in addition to .7z files) zip, rar and several other formats and why does 7zip when run from the CLI actually extract the files from the .rar file that I ran it against?

---edit
Sorry, I reread this and I think I am coming off a little bit righteous.  I didn't intend to come off that way.  I am just trying to figure out how this all works.  It kinda makes sense to have individually installable archive support, but I thought 7-zip would give everything *I* needed it to me in one step.  ...and it seems that the command line version does.

if you want an all in one package, you'll need 7zip-full

```
sudo apt-get install 7zip-full
```

That package also uses "archive manager" as a gui frontend.

*edit: it seems the question was asked weeks ago. Ah well, some people might stumble here after a forum or google search.*

---

### Post by PrimaryMaster on 2008-11-10
As much as i'd love to stay with Ubuntu (or Linux in general), i am afraid i'm starting to grow tired from all the problems it brings... First the Realtek ALC888 driver problem which i can't fix... 

And now a simple archive operation can't be done without learning all the darn terminal commands? Wtf?? 

All i want to do is make a zip (or rar, or 7z, anything) file out of a 25mb pdf and i want to have it in 5 x5mb parts for emailing. 

Banging my head on the walls... Add/remove software doesn't help much. It is a joke, it is telling me the archive manager handles everything perfectly... I laugh to that... Where are the advanced compression options???

---

### Post by cb951303 on 2008-11-10
> **PrimaryMaster said:**
> As much as i'd love to stay with Ubuntu (or Linux in general), i am afraid i'm starting to grow tired from all the problems it brings... First the Realtek ALC888 driver problem which i can't fix... 

And now a simple archive operation can't be done without learning all the darn terminal commands? Wtf?? 

All i want to do is make a zip (or rar, or 7z, anything) file out of a 25mb pdf and i want to have it in 5 x5mb parts for emailing. 

Banging my head on the walls... Add/remove software doesn't help much. It is a joke, it is telling me the archive manager handles everything perfectly... I laugh to that... Where are the advanced compression options???
is that what you want to do?

---

### Post by Ux64 on 2008-11-15
> **cb951303 said:**
> is that what you want to do?

Great! That's just what I was looking for too, and nagging about. Also configuration file for options would be great. But this is enough for 95% of users, I guess. Anyway, I'm happy with default values, it seems that solid archive is enabled by default using file roller.

 - Thank you!

So it's the lastest file roller with Ibex, what I'm talking about.

---

### Post by Gias Kay on 2009-01-15
For the needed:

Both the .deb pack of Q7Z and PeaZip work normally in 64-bit (amd64) environment. Just use the force architecture install:

```
sudo dpkg --force-architecture -i [deb pack name].deb
```

---

### Post by smfai on 2009-02-19
> **H.Callahan said:**
> Ok, I am confused.  I installed 7-zip.  I went to a .rar file in Nautilus and clicked on it.  I was told that the Archives Manager did not support the compression type (or words to that effect).

I then looked for 7-zip in the Applications Menu and couldn't find it.  Finally figured (from the man pages) that it was a CLI interface.

Went to the terminal, cd'ed to the right directory and used the CLI to extract from the same .rar file.  Worked perfectly.

I am not against using the CLI to do such things, but I have grown lazy in my old age and haven't used a CLI archiver since the old pkzip days with DOS.

Done!!:p if you only install p7zip-full you should use CLI .but after install p7zip-full & p7zip-rar,double click can open .rar and also can use right click.

---

### Post by ethoxyethaan on 2009-02-19
sudo apt-get remove p7zip p7zip-rar && sudo apt-get install p7zip-full

try that

---

### Post by egd on 2010-02-07
If you want a GUI front-end for 7-zip, [http://code.google.com/p/k7z/](http://code.google.com/p/k7z/)

---

### Post by Vithal on 2010-05-08
> **ethoxyethaan said:**
> sudo apt-get remove p7zip p7zip-rar && sudo apt-get install p7zip-full

try that

I installed **p7zip-full** and **p7zip-rar** from Synaptic Package Manager and things are working beautifully. I am on jaunty.

---

### Post by lukebrincat on 2010-07-22
> **eternicode said:**
> Check out PeaZip, [http://peazip.sourceforge.net/](http://peazip.sourceforge.net/) .  Not exactly the same as the windows version of 7-Zip, but it works.
Thanks!!!! This PeaZit is Super Amazing :) it even extracts files which are .001 .002 and so on xD

---

### Post by Buntu Bunny on 2012-10-04
I know this is a very old post, but the question is still viable. 

After installing p7zip and not being able to find command lines (I'm one of the uninitiated), I found this thread. I had already created a tar.gz with archive manager, so I opened it with archive manager, clicked on "save as," from the archive menu, and selected "zip" from the file extensions offered. That worked. Will have to try some of these suggestions the next time I need to create a zip archive.

FWIW, I also found a 7-zip command generator, [here]("http://www.howtoadvice.com/7zipHelper")

---

### Post by oldos2er on 2012-10-04
> **Buntu Bunny said:**
> I know this is a very old post, but the question is still viable.

It is; and I would urge you to start a new thread, as the posting guidelines suggest:

If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

