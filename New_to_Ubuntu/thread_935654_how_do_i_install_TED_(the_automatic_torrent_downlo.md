---
title: "how do i install TED (the automatic torrent downloader)"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by kaston on 2008-10-01
hi, 

noob question here.  i dl'ed the linux version of ted from here:  [http://www.ted.nu/download.php](http://www.ted.nu/download.php) and i extracted the .zip file but i have no idea what to do with the extracted files.  any help would be appreciated.

thanks,
kaston

---

### Post by Sarah L on 2008-10-01
The readme gives pretty detailed instructions:

> Welcome to the ted beta :D

To run ted: unpack the zip and double click ted.jar.
Or, go to your console, go to the directory where you unpacked ted and type "java -jar ted.jar"
If this does not work, please check if you have the latest java version installed. Go to [http://www.java.com](http://www.java.com).

If you are an existing ted user on windows or linux: backup config.ted and shows.ted in your ted directory and unpack the archive over your existing ted.
If you are a ted user on mac os X, go to the ted folder in finder, right click ted, choose show package contents, go to /Contents/Resources/Java/ and paste ted.jar in that folder.

See for more details on this beta release our special forum topic: [http://www.ted.nu/forum/viewtopic.php?p=802](http://www.ted.nu/forum/viewtopic.php?p=802)

For further information how to run and use ted, please read our online documentation!
[http://www.ted.nu/documentation/](http://www.ted.nu/documentation/)

You can find existing bugs and feature requests in our bugtracker: [http://www.ted.nu/bugs/](http://www.ted.nu/bugs/)

If you need support or want to report a bug or feature request: go to our support forum: [http://www.ted.nu/forum/](http://www.ted.nu/forum/)

Enjoy ted!

Roel & Joost
Ted Developers

---

### Post by karlr42 on 2008-10-01
Back up, you're installing the wrong way. Just open a terminal and enter
```

sudo apt-get install ted
```
Ubuntu will download and install it for you.

In Ubuntu, you don't install software by dowmloading them from websites, unzipping.. blah blah. You use Add/Remove Software(in the Applications menu) or Synaptics(System->Administration->Synaptics Package Manager. You open these, search for the name of the program you want, and install it from there. Simple, fast, clean. No need to google to find installers, to visit websites.

---

### Post by Sarah L on 2008-10-01
> **karlr42 said:**
> Back up, you're installing the wrong way. Just open a terminal and enter
```

sudo apt-get install ted
```
Ubuntu will download and install it for you.

Karlr42, are you sure?!

The package called "ted" in the Ubuntu repositories is not the "ted" that the OP is trying to install. According to aptitude, the "ted" package contains an RTF editor:

```

p   ted                                                               - graphical RTF (Rich Text Format) editor, stable lesstif version
```

The ted that the OP is trying to install is an automatic torrent downloader.

---

### Post by bigdee973 on 2008-10-01
doing it how karl says its easier IF U KNOW THE PROPER PROGRAM COMMAND BUT before you try to download and install anything from the net in tar.gz format or whatever you should ALWAYS check to see if its in the repositories first! it will save you headaches... you can install alot of programs by going to Applications>Add/remove and in there click "supported applications" and choose "all available applications" and typing in keywords like automatic torrent, torrent, etc and you will get a list of applications you might find...just check the box next to it and click apply and boom its installed 1,2,3... same goes for all programs you want that are for linux..say u want a dvd burner just type in dvd burner and you'll get a list of all dvd burning apps.. if you know the extact name just type the few letters or whole word and it will find it for you

---

### Post by karlr42 on 2008-10-01
You are right, I apologise. I saw a program called Ted an assumed it was this program:oops:

---

### Post by bigdee973 on 2008-10-01
not too sure the documentations should explain everything but if you want to see TV shows go to [www.hulu.com](www.hulu.com) they have uncut high quality tv shows that they show on modern tv like u could watch family guy that played last sunday on it legally...the site was made for it.

---

### Post by kaston on 2008-10-01
ya i checked synaptic but ted wasn't there.  i'll try the first responder's instructions.  thanks

---

### Post by kaston on 2008-10-02
i tried the readme instructions but when i double click ted.jar, it just opens a directory and i have no idea what to do then.  the readme says that if it doesnt work, go to java.com and i was going to download and install java but i thought i would install from the repos first.  but i don't know what to look for.  i typed java in the search in synaptic and a million things came up.  any ideas?

---

### Post by kaston on 2008-10-02
> **bigdee973 said:**
> not too sure the documentations should explain everything but if you want to see TV shows go to [www.hulu.com](www.hulu.com) they have uncut high quality tv shows that they show on modern tv like u could watch family guy that played last sunday on it legally...the site was made for it.

unfortunately, hulu doesnt work outside the us and im in canada

---

### Post by sickgirl485 on 2008-11-09
I am having the exact same problem. It would make things a lot easier if Ted was in the repository.

---

### Post by Torkiliuz on 2009-02-14
You download the linux .zip from [http://www.ted.nu](http://www.ted.nu). When it is finished downloading, unzip it to somewhere were you would find it easily, or somewhere hidden(for example ~/.ted). now go into the folder were you unzipped the zip-file. Highlight the ted.jar-icon, right-click it and select open with OpenJDK Java Runtime.( If you don't find the option to open it in OpenJDK Java Runtime, this means you haven't installed Java Runtime on your computer, to do so open up a Terminal and write this: sudo apt-get install ubuntu-restricted-extras. Good Luck.

---

### Post by binbash on 2009-02-14
Ted works on ubuntu with sun java, just unzip the downloaded zip, be sure you have sun java installed

---

### Post by finny388 on 2011-09-24
i've got openjdk installed
when I right click ted.jar I can choose to open with "OpenJDK Java 6 Runtime"

at first it I got the error that it wasn't executable. I went into properties and allowed it to execute.

but when I try to open it with JDK, nothing happens.

I wish this was in the repositories.

Anyone know what I can do?
Maybe I have to make every file in the folder executable?

---

### Post by Headcase_Fargone on 2012-01-02
> **finny388 said:**
> i've got openjdk installed
when I right click ted.jar I can choose to open with "OpenJDK Java 6 Runtime"

at first it I got the error that it wasn't executable. I went into properties and allowed it to execute.

but when I try to open it with JDK, nothing happens.

I wish this was in the repositories.

Anyone know what I can do?
Maybe I have to make every file in the folder executable?

Did anyone ever figure out how to get this program working under Ubuntu?  The developers don't appear to officially support Linux, though they claim it works fine.

Opening ted.jar with OpenJDK Java 6 Runtime gives me the above error about it not being an executable package.

When I attempt to run it from console (java -jar ted.jar) I get an error regarding the tray:

> Exception in thread "main" java.lang.UnsatisfiedLinkError: no tray in java.library.path
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1681)
	at java.lang.Runtime.loadLibrary0(Runtime.java:840)
	at java.lang.System.loadLibrary(System.java:1047)
	at org.jdesktop.jdic.tray.internal.impl.GnomeSystemTrayService.<clinit>(Unknown Source)
	at org.jdesktop.jdic.tray.internal.impl.ServiceManagerStub.getService(Unknown Source)
	at org.jdesktop.jdic.tray.internal.ServiceManager.getService(Unknown Source)
	at org.jdesktop.jdic.tray.SystemTray.<clinit>(Unknown Source)
	at ted.TedTrayIcon.<init>(TedTrayIcon.java:28)
	at ted.TedMainDialog.initGUI(TedMainDialog.java:309)
	at ted.TedMainDialog.<init>(TedMainDialog.java:125)
	at ted.TedMain.main(TedMain.java:50)

Now I found where someone recommended running it with the noTray switch (java -jar ted.jar noTray) and that opens, but what then?  I'm stuck without a console until I close the app which needs to be running at all times.

---

### Post by finny388 on 2012-01-04
I'm not sure what you mean by being stuck without a console.

I've found using
java -jar ted.jar noTray

worked like a charm

---

### Post by nia backstabber on 2012-01-12
hate posting in old treads but Ive been looking all night on how to install ted and this is the only way i fount to get it to work but what i would like to have is a shortcut in the menu so i don't have to keep typing all the commands. i tried this sites tutorial [http://myinterestingubuntu.blogspot.com/2010/05/how-to-install-ted-in-ubuntu-lucid-1004.html](http://myinterestingubuntu.blogspot.com/2010/05/how-to-install-ted-in-ubuntu-lucid-1004.html) but it doesn't do anything at all i even tried to change it to this 
command: java -jar noTray /home/yourusername/ect......
thinking maybe the same error was happening but still no luck. any help would be greatly appreciated. also if i do figure it out i will update my post.

---

