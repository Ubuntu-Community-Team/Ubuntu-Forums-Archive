---
title: "WinRAR for Linux"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by 3DGE on 2008-08-31
I need help installing Winrar on Ubuntu. I have downlodaed the Linux version from WinRar's website and the folder is on my desktop but how do I install it?
The folders name is "rar"

---

### Post by Pro-reason on 2008-08-31
> **3DGE said:**
> I need help installing Winrar on Ubuntu. I have downlodaed the Linux version from WinRar's website and the folder is on my desktop but how do I install it?
The folders name is "rar"

Please read the help on installing programs on Linux.  (There is a help button on the panel.  You can also take a look at [https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware), [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware), [http://video.google.com/videoplay?docid=5253052326994067125](http://video.google.com/videoplay?docid=5253052326994067125))

You don't just download random files from the internet.  Go to *Add/Remove Programs*, or *Synaptic*.  You can add support for *RAR* there.  The default GNOME archiver (*file-roller*) will then support *RAR* (as well as you having rar support on the command line).

---

### Post by RequinB4 on 2008-08-31
See my signature for information on installing programs in ubuntu

For rar support, go to applications-accessories-terminal

```
sudo apt-get install unrar
```

---

### Post by Redache on 2008-08-31
if you go to the rar folder on the desktop in the Terminal
```
cd Desktop (if you're in the default starting directory)
```

Then you have to use the command make to set it up:
```
sudo make
```

Then use make install to make it install
```
sudo make install
```

Then you run it by typing rar in the terminal.

There's no GUI for it (or at least what I got off their website had no GUI) so you'll have to learn the terminal commands.

---

### Post by louieb on 2008-08-31
> **RequinB4 said:**
> See my signature for information on installing programs in ubuntu  
monkeyblog.org  seems to have lost its host. Hope they get one soon.

---

### Post by 3DGE on 2008-08-31
Thanks I started thinking I was on Windows again !
Now I gotta remember to use Add/Remove a lot more.

---

### Post by Pro-reason on 2008-08-31
If you absolutely must install the version you downloaded from rarlabs.com, then first bear in mind that it is RAR for Linux, not WinRAR.  Secondly, you'll find a Makefile inside.  I have found that running it (with the “make” command) just produces an error.  In fact, there are already binaries in the tarball.  All you have to do is install them with “sudo make install”.

However, as I said before, do not install things like that.  You will bypass the package management system.  Please use .deb packages via Synaptic.

---

### Post by 3DGE on 2008-08-31
Ok one proble I used Add/Remove and it said it installed the application successfully but now I cant see it under any Applications... help

---

### Post by Redache on 2008-08-31
There is no GUI for it. You have to run it from the Command Line (At least I'm pretty sure you do in the tarball on their website there's no GUI files at all.)

---

### Post by 3DGE on 2008-08-31
Ok could you help explain how to run it from the command line...

---

### Post by Pro-reason on 2008-08-31
> **3DGE said:**
> Ok one proble I used Add/Remove and it said it installed the application successfully but now I cant see it under any Applications... help

As I said before, once you have installed RAR, you will have two things:
[LIST]
[*]the ability to use the “rar” command from the terminal
[*]the ability to access .rar files from GNOME's standard file archiver (which is called “file-roller”).
[/LIST]

You don't have to use a completely separate and redundant graphical application for each file format.  This isn't Windows.

---

### Post by Pro-reason on 2008-08-31
> **3DGE said:**
> Ok could you help explain how to run it from the command line...

No!  That's what documentation is for.

Type &#8220;rar --help&#8221; or &#8220;man rar&#8221; on the command line.  This applies to all Linux commands.

P.S.:
OK, I give in.  Otherwise, other people will just explain.  If you have files called &#8220;CV.odt&#8221; and &#8220;CV.pdf&#8221; on your desktop and you want to make a RAR archive of them, then type this:

```

cd ~/Desktop
rar a CV.rar  CV.odt CV.pdf

```

To extract:

```

unrar CV.rar

```

It's actually easier than a GUI.

---

### Post by solitaire on 2008-08-31
Once Unrar is installed does not "Archive Manager" recognise and use Unrar? when it opens rar files?

---

### Post by perlluver on 2008-08-31
> **solitaire said:**
> Once Unrar is installed does not "Archive Manager" recognise and use Unrar? when it opens rar files?

Yes it does, it will offer to unzip the package.  Just right click, and select extract here.

---

### Post by Redache on 2008-08-31
> Once Unrar is installed does not "Archive Manager" recognise and use Unrar? when it opens rar files? 

I completely forgot about File Roller, If you don't use it you sort of forget it's there!

Think of it as a codec for Archive files. It adds support for it to your system and the applications present will then be able to open files that contain it, and export files to it (although this isn't true of all Codecs).

If you second click on any file you want to archive, select the option "Create Archive.." you'll be able to select rar from the list of drop down file types.

---

### Post by 3DGE on 2008-08-31
Is there a way to use winrar using Wine?

---

### Post by Redache on 2008-08-31
I don't understand why you'd want to.

Rar is now integrated into your system and you can now open and create archives.

If you want a GUI just double click on the file you want and it'll open in File Roller.

---

### Post by perlluver on 2008-08-31
> **3DGE said:**
> Is there a way to use winrar using Wine?

Why would you want to use winrar?  You can zip and unzip, perfectly fine in Ubuntu.  Unless you want some special feature.

---

### Post by RequinB4 on 2008-08-31
> **3DGE said:**
> Is there a way to use winrar using Wine?

I don't know what people are saying, there is no reason to even open the termianal for this...

If you have a .rar archive, right click and extract here, or double click it.  If you want to make a .rar archive, highlight the files you want to include, and write click archive...

---

### Post by Pro-reason on 2008-08-31
> **3DGE said:**
> Is there a way to use winrar using Wine?

What???

Edit: OK, if you want a serious answer, then yes, you can of course simply install it via Wine.  It would be very stupid to do so.

What are you trying to do?
[LIST]
[*]Access the RAR files you made on Windows?  Now that you have installed the &#8220;rar&#8221; package in Synaptic, GNOME can now open RAR files.  Just right-click and choose &#8220;extract here&#8221;, or else open them in &#8220;file-roller&#8221;.
[*]Make good compressed archives?  Use &#8220;file-roller&#8221; to make *.tar.bzip2* archives.
[/LIST]

---

### Post by Pro-reason on 2008-08-31
> **RequinB4 said:**
> I don't know what people are saying, there is no reason to even open the termianal for this...

If you have a .rar archive, right click and extract here, or double click it.  If you want to make a .rar archive, highlight the files you want to include, and write click archive...

I don't know what you are saying!  We're not telling him to use the terminal at all.  From the beginning, I told him to install *rar* via Synaptic, and that it would add RAR support to file-support to *file-roller*.  Everything else has been because he insisted on other things.

---

### Post by Redache on 2008-08-31
> I don't know what you are saying! We're not telling him to use the terminal at all. From the beginning, I told him to install rar via Synaptic, and that it would add RAR support to file-support to file-roller. Everything else has been because he insisted on other things.

Yeah. Although technically using a terminal is quicker to open and create archives.

---

### Post by 3DGE on 2008-08-31
Ok NVM I just did what you guys said and it worked. It just seemed weird not seeing winrar and I don't know why I wanted to.

Thanks for the help and sorry for the confusions.

---

### Post by Pro-reason on 2008-08-31
> **3DGE said:**
> Ok NVM I just did what you guys said and it worked. It just seemed weird not seeing winrar and I don't know why I wanted to.

Thanks for the help and sorry for the confusions.

No problem.  Windows is like a virus in your mind that stops you doing things properly.  It doesn't take too long to cure, though!

---

### Post by mrbiggels on 2009-12-08
i also got it all to work but when it asks me the second time to verify what im installing, i click aply and it starts to install it but after 3 seconds and error appears. before istall it it says "warning, you are about to instal software that cant be authenticated"
then it gives me teh 3 options of "not authenticated, to be installed, unchanged" ive tried all but everytime i get an error ssaying "W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/multiverse/r/rar/rar_3.7b1-2_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/multiverse/r/rar/rar_3.7b1-2_i386.deb)
  404 Not Found [IP:.............]".

---

