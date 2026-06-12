---
title: "Installing/Downloading applications"
date: 2012-08-05
forum: New to Ubuntu
---

### Post by benijenks on 2012-08-05
I know that there are many applications in the USC, but what do I do when it comes to things that AREN'T in the software centre? 

Meaning, if I download an application, it gets saved to my /downloads/ directory... Where do I go from there? Are there GUI-based auto-installers on Linux? Is it a simple terminal command?

I've only done it a couple times, both of which seemed different and complicated. (Wine, and some internet thing that I don't remember)

Just generally looking for some guidance on installing applications.

---

### Post by levlaz on 2012-08-05
It depends on the type of file that you are trying to download. 

1. For .deb files (If it is a piece of native linux software always choose .deb if it is available) once you download the file it will open the USC and install from there. 

2. If it an .exe file (windows) you will have to use WINE to install it, although a lot of times much of the software that works in windows will not work even through wine. 

3. if it a tar.gz file (compressed) it is typically either source code that you need to compile, or a piece of software that has an installation script attached to it. 

If it is source the simplest way to install it is to extract the tar.gz then using a terminal window navigate to the folder where the source is extracted and enter the following commands. 

```
 
./configure
make
make install 

``` 

./configure - ensures that all of the dependencies are met 

If you do not have make or a compiler installed you can do so easily via the command line 

```
 sudo apt-get install make gcc 
``` 

If the file is in a tar.gz file and it has an installation script simply run the installation script and the program will install. 

I think this covers most types of software, if you are trying to install something that I did not cover let me know and I will try to help you out!

---

### Post by Bashing-om on 2012-08-05
Hi !
 Look into your download.. should be a "readme" file in there to direct you for installation. If you need more help, give more information. like what file you downloaded, the purpose of the program, and where you downloaded it from ... 
        someone will assist further ... 
                          see ya!

---

### Post by OM55 on 2012-08-05
If you use Ubuntu, there are several different ways to do so. 
But given that you are looking to a downloadable installable file, the easiest way is to get your downloaded application as a ".deb" files (having a ".deb" extension).

Once it is in your 'Downloads' folder just double click on it. It will launch the Software Center and after a few seconds (up to the speed of your computer...) it will show inside Software Center with the "Install" button ready to be clicked. Just click the "Install" button - and wait (there will be a progress bar) until installation is done and the button would change to "Re-Install".

Now you are ready to use the new application you just installed.

Not all application will have a '.deb' file ready, in which case you will need to use other more complex installation methods (like compiling from source).

---

### Post by oldos2er on 2012-08-06
[http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)

---

### Post by benijenks on 2012-08-06
Thanks for the help all.

I've read of all the types you've mentioned, but came across something different yesterday:

A zipped folder, which I had to run with Java/OpenJDK. It was for an application, so I got a little confused, because I had never encountered such a thing before. All I did was enable it as an executable, and then selected to run with OpenJDK 6.0. 

It didn't work, but I think that's something else. haha

Thanks again!

---

### Post by nyamina on 2012-08-06
I've come across a few programs like that before, like Netlogo for example. Just install Java, double click the executable and it should run fine, although I've never found a Java program that was pretty to use.

---

### Post by benijenks on 2012-08-06
> **nyamina said:**
> I've come across a few programs like that before, like Netlogo for example. Just install Java, double click the executable and it should run fine, although I've never found a Java program that was pretty to use.

Yeah, I don't think Java is exactly aesthetics-oriented. haha

Here's two more questions, that I don't want to start another thread for, but can't seem to google properly:

How come if I execute some commands like
              ```

git clone git://url

```

they auto-execute? I don't even press enter.

Also,

I installed GIT, using sudo-apt get, etc... For things like this, and other random packages, such as 

[LIST]
[*]glib-2.0
[*]gtk+-2.0
[*]glade-2.0
[/LIST]
[LEFT]that don't actually come from USC, or have any real functionality... How do I uninstall them? What if I forget the package names? Where can I find stuff like that, to make sure that I don't have packages I don't want in the future?


[/LEFT]
[INDENT]

           [/INDENT]

---

### Post by Dirtydeedsman on 2012-08-07
Hey all

I am fairly new to Ubuntu and running 12.04LTS

I downloaded a piece of software from the internet and it is .rpm format. i have looked all over the net but can't get a proper way to install it.
How do i go about installing the software?

---

### Post by benijenks on 2012-08-07
> **Dirtydeedsman said:**
> Hey all

I am fairly new to Ubuntu and running 12.04LTS

I downloaded a piece of software from the internet and it is .rpm format. i have looked all over the net but can't get a proper way to install it.
How do i go about installing the software?

I think you need to convert it to a deb file. 

There's software out there that can do it for you. However, I'm not exactly sure of the process.

---

### Post by Nytram on 2012-08-07
> **Dirtydeedsman said:**
> Hey all

I am fairly new to Ubuntu and running 12.04LTS

I downloaded a piece of software from the internet and it is .rpm format. i have looked all over the net but can't get a proper way to install it.
How do i go about installing the software?

There's a CLI program called *Alien* (it's in the software centre) that converts an *rpm* file into a *deb*, which can then be installed on Ubuntu by double-clicking it.

---

### Post by Kalanac on 2012-08-07
Hello,

One of the easiest ways to install new software into Ubuntu is to add a repository or a ppa.

Doing a google search for ubuntu [software] ppa or ubuntu [software] repository usually yields results.  Repositories will add the software to your USC list and has the added bonus of usually keeping it up to date as well.  It' usually my first choice.

DEB files are a second option and lack the maintenance of having an installed repository.  However they can be cleanly removed which is a bonus.

Tar balls are the most risky option.  They can be tricky to pull of properly and if there's a hitch you can screw up your system.  Tar balls don't include dependencies (usually) so you might find the install keeps hanging because it can't find a required library.  Tar balls are also more difficult to uninstall cleanly.  I try to avoid using them where I can as often things have taken a turn for the strange and unusual and I'm never sure if things have gone back to normal after an uninstall.

---

### Post by oldos2er on 2012-08-07
> **Dirtydeedsman said:**
> Hey all

I am fairly new to Ubuntu and running 12.04LTS

I downloaded a piece of software from the internet and it is .rpm format. i have looked all over the net but can't get a proper way to install it.
How do i go about installing the software?

What software? You should look to the repositories first, or at minimum try to find a *.deb file. 

In the future please start your own thread rather than "hijacking" someone else's.

---

