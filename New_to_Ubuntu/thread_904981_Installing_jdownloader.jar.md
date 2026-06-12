---
title: "Installing jdownloader.jar"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by jason.white on 2008-08-29
I've been doing some research to try and find the best flashget replacement for Linux and have been pointed towards jdownloader.  I'm very new to linux and just trying to learn as much a possible.

Basically I downloaded jdownloader and don't have a clue as to how install it.  The main package was a .zip that when extracted reveals jdownloader.jar.  How do I install this package?  As much detail as possible would be appreciated as I am a total n00b.  Also, if you could include any GUI method as well as a Terminal method that way I can learn both.

Thanks so much in advance,

-Jason

---

### Post by wolfen69 on 2008-08-29
try right clicking it, go to properties and select "open with". select java. of course you will need java installed first.

---

### Post by lovinglinux on 2008-08-29
If you are using Firefox, try [DownThemAll]("https://addons.mozilla.org/en-US/firefox/addon/201") extension. It is easy to install and integrates perfectly with Firefox.

I used flashget a long time ago, but since I discovered DownThemAll it has been my default an only download manager.

---

### Post by jason.white on 2008-08-29
I've tried downthemall and get this error: No links or pictures found.  

Ideas?

---

### Post by lovinglinux on 2008-08-30
> **jason.white said:**
> I've tried downthemall and get this error: No links or pictures found.  

Ideas?

What were you doing when you got this error?

---

### Post by jason.white on 2008-08-30
I right clicked to download the links that I had selected.

---

### Post by crispy_420 on 2008-08-30
Did you set the filters for the downloads?

When you right click on the page and select "down load them all" a new page opens. At the bottom are filters based on file extensions to look for.

---

### Post by lovinglinux on 2008-08-30
DownThemAll has a lot of options that I usually don't use. I just use it for direct link download, so Firefox will prompt if I want to "Save" the file using the built-in download manager, if I want to use DownThemAll and another option for quick download into a previous selected folder. Never tried to download all images on a page. This is what I guess you are trying to do right? (DownThemAll has options for downloading all contents in a page)

When you install the extension, you get three new icons:

"dTa OneClick!" and "DownThemAll!" will prompt for media selection, which includes all available media in a page. I don't think is very useful for me. If I want to save an entire page I use Scrapbook extension.

The third icon is the "Manager", which is the one I use for single file operations.

---

### Post by jason.white on 2008-08-30
This appears when I select a group of links and then right click and choose DownThemAll selection.

---

### Post by capink on 2008-09-02
I'm not able to make jdownloader work in linux. I try right clicking jdownloader.jar and open with "sun java runtime6" but it is not working.

I also tried opening it form the command line using the command java -jar ... but it is not working either.

In both cases the jdownloader splash image starts and hangs for about 10 minutes before the main window appears and it hangs forever.

The strange thing is that the program is working perfectly with windows. It should work as well in linux, because as I understand, the basic premise of java is that you code once and run everywhere. I was able to make a lot of java programs work without problems in linux like hjsplit and power*architect but sadly not this one.

Can anyone help please.

Can someone help please.

---

### Post by Interpreter on 2008-09-17
Did you try getting specific help on this board?
[http://www.the-lounge.org/index.php]("http://www.the-lounge.org/index.php")
Theyre actually fast, committed, and certainly know alot about their own programme...

---

### Post by FrankVdb on 2008-09-24
I use downloadhelper (Firefox extension).

---

### Post by gilforsyth on 2008-09-24
Hey man, 
You just need to make the installer .jar executable.  
Open a terminal and cd to the .jar directory

e.g.
```
cd /home/username/Desktop/jDownloader
```
and then type do the following
```
sudo chmod +x JDownloader.jar
```
enter your password and you're all set.  
Just right click and open with java 6 as you tried before and it should load up no problem.

---

### Post by devnulljp on 2008-10-17
> **gilforsyth said:**
> Hey man, 
You just need to make the installer .jar executable.  
Open a terminal and cd to the .jar directory

e.g.
```
cd /home/username/Desktop/jDownloader
```
and then type do the following
```
sudo chmod +x JDownloader.jar
```
enter your password and you're all set.  
Just right click and open with java 6 as you tried before and it should load up no problem.And that works for you? I tried java -jar JDownloader.jar and also right click->Open with java6 and both do the same thing. It launches, Choose language, choose download location, "Welcome to JDownloader. The setup program will download some files" and it crashes with pages of java errors:

UPDATE: I ran it again and this time chose German as the language...it works...in German.

---

### Post by Interpreter on 2008-10-18
Yeah the "setup" is buggy, once it works you can alter your "download to" -directory and change the default language and whatnot....once it set up you should be fine!

Oh and beware of the Tray feature when using Gnome, its still "in the makings" ...If you run into unexplainable behaviour, disable that tray icon first before you try and fix something or give it up entirely.

---

### Post by stonedparadox on 2008-12-09
you know

its weird right

sudo chmod +x JDownloader.jar <--- that works perfectly until i close the program and then reopen it
its like it just dissapears and i gotta do that command all over again
and sometimes it doesnt even work
like now

---

### Post by Interpreter on 2008-12-10
Freenode # JDownloader ...   highly talkative these guys, even in English that is..

---

### Post by adobrakic on 2008-12-10
I use jDownloader and all I did was install sun-java-6 from synaptic, and then downloaded .jar version of jdownloader from the website.

As its been said before, the tray icon is really buggy, and overly annoying. If you make it go into the tray, and try clicking on it to maximize, usually the program just freezes. Another expierence I've had with the tray icon is that I'll click on it to maximize, and the program just goes back into the tray after like a second of visibility.

---

### Post by Interpreter on 2008-12-11
I didn't have to change anything, if your JAVA installation is fine, it should work out of the box.

I'm having this one here in my applications menu though, for additional comfort:

```
/home/intey/.jdownloader/jdownloader.jd.sh
```
```
#!/bin/sh
cd /home/intey/.jdownloader/jdownloader
java -Xmx512m -jar JDownloader.jar & 
```
cheers phil

---

### Post by sabitha on 2008-12-11
i use JDownloader too
this what i write on terminal to run JDownloader
```
ubuntu@ubuntu-kasir:~$ java -jar bin/JDownloader.jar
```

---

### Post by h8uthemost on 2008-12-11
I had to install Sun Java 6 Runtime from the repos to get jdownloader to run(as others have mentioned). I just right-click on .jar and open with Java.

And there's no other file host downloader(RS, megaupload, etc) on Linux that compares to jdownloader. It's the best currently available.

If this doesn't help, then ask in jdownloader forums. Those guys will help you with your problem.

---

### Post by parrimin on 2009-04-12
JHi,
Im running jdownloader running java -jar JDownloader.jar, but there is one problem. Every time I restart the computer it starts the wizard asking for the language and the downnload directory, and tries to download and update some files, but it seems to not succeed. Otherwise, i can download files with no problems, but is a bit annoying having to wizard every time... Anyone happened the same and solved?

---

### Post by FaceLeg on 2009-06-13
I wrote a short tutorial on installing JDownloader: [http://pagesofinterest.net/blog/2009/05/installing-jdownloader-in-ubuntu/](http://pagesofinterest.net/blog/2009/05/installing-jdownloader-in-ubuntu/)

If you follow that you'll be able to run it like a normal program - from terminal or the application menu.

---

### Post by firesock on 2009-07-26
> **FaceLeg said:**
> I wrote a short tutorial on installing JDownloader: [http://pagesofinterest.net/blog/2009/05/installing-jdownloader-in-ubuntu/](http://pagesofinterest.net/blog/2009/05/installing-jdownloader-in-ubuntu/)

If you follow that you'll be able to run it like a normal program - from terminal or the application menu.

Hi!!

Thank you very much!! it worked like a charm! :KS

This is the best way to install it that I've seen...

Much  appreciated

---

### Post by SCBrazil on 2009-08-03
HI,
This is an old thread by now but you never know, someone else may end up here looking how to install the best download manager there is.

The best way to install it is thus (I'm a Kubuntu user but I think the method is the same for Ubuntu);

1. From your package manager get 'Sun-Java6-jre' (this is the latest version as of today).

2. After it has installed open a Terminal, copy and paste;

wget [http://212.117.163.148/jd.sh](http://212.117.163.148/jd.sh) && chmod +x jd.sh && ./jd.sh

The Terminal DL will end very quickly and then you'll get JDownloader's own window which will complete the process for you.

You're done.

---

### Post by squirtmph on 2009-10-02
I have download Jdownloader but I dont know where it go, i did some search on files and I dint fin it. 
do you have any idea where the program GO? 
 > How can i find it and save them on my tool barthank you very much for your help again

---

### Post by anthos_hero on 2009-10-10
Download Them All will download any files on a site.  It won't download links from filehosting sites like JDownloader.  Don't bother with it.  I couldn't get JDownloader to work through Java so I tried using the Windows version through WINE.  It worked great, except I couldn't get it to download anything.  Try it yourself though, you may have more luck.

---

### Post by SammichDinosaur on 2009-10-26
I'm having the same problem as squirtmph. I installed Jdownloader per the instructions on the website and it ran just fine. I'm just not sure where it went now, how to run the program.

---

### Post by adzidzor on 2009-10-26
> **SCBrazil said:**
> HI,
This is an old thread by now but you never know, someone else may end up here looking how to install the best download manager there is.

The best way to install it is thus (I'm a Kubuntu user but I think the method is the same for Ubuntu);

1. From your package manager get 'Sun-Java6-jre' (this is the latest version as of today).

2. After it has installed open a Terminal, copy and paste;

wget [http://212.117.163.148/jd.sh](http://212.117.163.148/jd.sh) && chmod +x jd.sh && ./jd.sh

The Terminal DL will end very quickly and then you'll get JDownloader's own window which will complete the process for you.

You're done.

THANKS!!!! Best so far. Worked perfectly without sweat.  Very simple.  copy and paste without any typing...that's it!

---

### Post by duma91 on 2009-11-15
> **firesock said:**
> Hi!!

Thank you very much!! it worked like a charm! :KS

This is the best way to install it that I've seen...

Much  appreciated

It's really helpful THanks

---

### Post by midion on 2009-12-12
> **SCBrazil said:**
> HI,
This is an old thread by now but you never know, someone else may end up here looking how to install the best download manager there is.

The best way to install it is thus (I'm a Kubuntu user but I think the method is the same for Ubuntu);

1. From your package manager get 'Sun-Java6-jre' (this is the latest version as of today).

2. After it has installed open a Terminal, copy and paste;

wget [http://212.117.163.148/jd.sh](http://212.117.163.148/jd.sh) && chmod +x jd.sh && ./jd.sh

The Terminal DL will end very quickly and then you'll get JDownloader's own window which will complete the process for you.

You're done.

Woot! Thanks Alot! I'm new to linux and I set this up to replace windows on our desktop. My fiance keeps breaking windows. She wont be able to break this though.

---

### Post by Martin McFly on 2010-02-09
This was helpful. I originally tried to open .jar file in Krusader to no avail, but later I've tried to open it in Thunar and there I saw choice to open it in Java.

However, do you know how to make this startup application ?

---

### Post by tphuocthai on 2010-02-24
**@Martin McFly**

1. Go to System -> Preferences -> Startup Applications
2. Click on Add button
3. Type in name: JDownloader
4. Browse to the jd.sh file
5. Click on Add button

That's it

---

### Post by suzypeppercorn on 2010-04-09
> **FaceLeg said:**
> I wrote a short tutorial on installing JDownloader: [http://pagesofinterest.net/blog/2009/05/installing-jdownloader-in-ubuntu/](http://pagesofinterest.net/blog/2009/05/installing-jdownloader-in-ubuntu/)

If you follow that you'll be able to run it like a normal program - from terminal or the application menu.

Excellent tutorial. This method should work for almost any Java program. Thank you

---

### Post by eddietours on 2010-04-18
wow thanks

---

### Post by Kuzma86 on 2010-05-31
Hey! I also found this very helpful!

[http://www.sucka.net/2010/05/install-jdownloader-via-ppa-repository/](http://www.sucka.net/2010/05/install-jdownloader-via-ppa-repository/)

Used this at the end of the day.

---

### Post by Exom on 2010-07-15
> **SCBrazil said:**
> HI,
This is an old thread by now but you never know, someone else may end up here looking how to install the best download manager there is.

The best way to install it is thus (I'm a Kubuntu user but I think the method is the same for Ubuntu);

1. From your package manager get 'Sun-Java6-jre' (this is the latest version as of today).

2. After it has installed open a Terminal, copy and paste;

wget [http://212.117.163.148/jd.sh](http://212.117.163.148/jd.sh) && chmod +x jd.sh && ./jd.sh

The Terminal DL will end very quickly and then you'll get JDownloader's own window which will complete the process for you.

You're done.

It works fine, thanks!

---

### Post by anweshdbest on 2010-12-04
It worked, but once i closed it, I couldn't figure out where exactly did it get installed. Can you help me with that?

---

### Post by ivanovnegro on 2010-12-04
Ok, here I will post again a very easy How To to install JDownloader in Ubuntu.
Its the graphical way for newcomers to Ubuntu, very easy.
At the end you will be able to acces the application via Applications-> Internet-> JDownloader.
First of all assure that you have installed Sun Java from the repository.
Then simply add the following to your Sourceslist, to your software packages (other software) in Synaptic: 

deb [http://ppa.launchpad.net/jd-team/jdownloader/ubuntu](http://ppa.launchpad.net/jd-team/jdownloader/ubuntu) maverick main

[FONT=Verdana]This is for Maverick how you can see.[/FONT]

[FONT=Verdana]Reload Synaptic and type in the terminal the key:

[/FONT]> sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 6A68F637  

[FONT=Verdana]Now you can install JDownloader via Synaptic Package Manager, just search for it there
and in the end you will find it in your Applications.
There are several ways to install it, I think for new users its the simpliest without to edit 
anything.

[/FONT]

---

### Post by anweshdbest on 2010-12-04
No, actually i have installed it, but now i closed it and now i cannot find out where exactly i installed it!

I installed using the procedure mention in the 2nd post above this!

---

### Post by ivanovnegro on 2010-12-04
> **anweshdbest said:**
> No, actually i have installed it, but now i closed it and now i cannot find out where exactly i installed it!

I installed using the procedure mention in the 2nd post above this!

I posted it generally for all.
In your case, I am not sure how you made it, I saw the post but I dont understand it how you cannot find it.
Ok, you could search in Nautilus for JDownloader.

---

### Post by alaukikyo on 2010-12-04
> **ivanovnegro said:**
> Ok, here I will post again a very easy How To to install JDownloader in Ubuntu.
Its the graphical way for newcomers to Ubuntu, very easy.
At the end you will be able to acces the application via Applications-> Internet-> JDownloader.
First of all assure that you have installed Sun Java from the repository.
Then simply add the following to your Sourceslist, to your software packages (other software) in Synaptic: 

deb [http://ppa.launchpad.net/jd-team/jdownloader/ubuntu](http://ppa.launchpad.net/jd-team/jdownloader/ubuntu) maverick main

[FONT=Verdana]This is for Maverick how you can see.[/FONT]

[FONT=Verdana]Reload Synaptic and type in the terminal the key:

[/FONT][FONT=Verdana]Now you can install JDownloader via Synaptic Package Manager, just search for it there
and in the end you will find it in your Applications.
There are several ways to install it, I think for new users its the simpliest without to edit 
anything.

[/FONT]


it is definetly not the simplest 

Simplest way is to Open Applications -> Ubuntu Software Center Then Go to Edit (menu) -> Software Sources -> Other Software(tab) and then add and paste  '**ppa:jd-team/jdownloader' **and then close and reload when asked then install jdownloader from the software center

---

### Post by ivanovnegro on 2010-12-04
> **alaukikyo said:**
> it is definetly not the simplest 

Simplest way is to Open Applications -> Ubuntu Software Center Then Go to Edit (menu) -> Software Sources -> Other Software(tab) and then add and paste  '**ppa:jd-team/jdownloader' **and then close and reload when asked then install jdownloader from the software center

You are right, maybe this one is a little bit quicker.
For me more fast is all within the terminal, but I tried to think the graphical way.

---

### Post by srbsoft on 2011-10-09
> **jason.white said:**
> I've been doing some research to try and find the best flashget replacement for Linux and have been pointed towards jdownloader.  I'm very new to linux and just trying to learn as much a possible.

Basically I downloaded jdownloader and don't have a clue as to how install it.  The main package was a .zip that when extracted reveals jdownloader.jar.  How do I install this package?  As much detail as possible would be appreciated as I am a total n00b.  Also, if you could include any GUI method as well as a Terminal method that way I can learn both.

Thanks so much in advance,

-Jason
Try this in gnome-terminal:

sudo add-apt-repository ppa:jd-team/jdownloader
sudo apt-get update
sudo apt-get install jdownloader

After installation start jdownloader and wait to download latest version...

---

### Post by Elfy on 2011-10-09
closed - the OPs not been here for over 3 years

---

