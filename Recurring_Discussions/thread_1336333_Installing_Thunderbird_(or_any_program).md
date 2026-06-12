---
title: "Installing Thunderbird (or any program)"
date: 2009-11-24
forum: Recurring Discussions
---

### Post by Don Bowen on 2009-11-24
Yes, I know how to use synnaptic.  Thunderbird will install just fine if I use that.

Question:  When I download Thunderbird for Ubuntu and unzip the files....
**What am I supposed to do with them?**
If there is no way at all to install them, why does Thunderbird let me download them?

---

### Post by Dr Belka on 2009-11-24
what kind of file did you download, a deb, a zip, a tar.gz?

Why dont you just install it from synaptic?

---

### Post by lisati on 2009-11-24
There are some options:
[LIST=1]
[*]Use the Add/remove programs menu item (v9.04 and earlier) or the Software shop (9.10) - this is on the Applications menu.
[*]Use "Synaptic Pacakage manager" (on the System->Administration menu)
[*]Go to the website for the software you are interested in, and look for a ".deb" installation file
[/LIST]

---

### Post by Cheesemill on 2009-11-24
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by oldos2er on 2009-11-24
> **Don Bowen said:**
> Yes, I know how to use synnaptic.  Thunderbird will install just fine if I use that.

Question:  When I download Thunderbird for Ubuntu and unzip the files....
**What am I supposed to do with them?**
If there is no way at all to install them, why does Thunderbird let me download them?

 You downloaded Thunderbird with Thunderbird?? What site did you download from?

---

### Post by Don Bowen on 2009-11-24
> **Cheesemill said:**
> [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
I went to the site and found 
" If you have trouble installing a .tar.gz file, you can ask for help on [the Ubuntu Forums]("http://www.ubuntuforums.org/")."
ok...that brings me back here...  I get it that we are supposed to use synaptic and other installations "helpers" because they are good at installing things, and we poor humans are not.

Still, when I download Thunderbird and then unzip the compressed file, it dumps a whole bunch of files into a folder.... as if I might be able to do something with them.  I still wonder what that might be.

Yes, it's easier to just go with the package installers, and I've learned to look for a .DEB file so the debian install "helper" thingie can do the install for me.... it's that part about doing it for me that chafes... 

I can only conclude that it must be prohibitively difficult to install anything by hand in Ubuntu and that's probably due to the Linux approach to security.  
If that's true, why would Mozilla let me download Thunderbird?  Just so that I can stare blankly at the uncompressed files?  

Someone knows how to install things in Ubuntu without a "helper"... probably the guys who wrote the helpers, for example.

It's the same old philisophical divide.  There are those who don't care what the engine looks like as long as the car goes forward, and then there are those who want to stop the car and open the hood.

Let me end with a simple question.  If I were going to install the Thunderbird files I downloaded, what is the first step?  Unzip them? OK...did that... now what...
Is this not how we learn?

---

### Post by Cheesemill on 2009-11-24
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by Don Bowen on 2009-11-24
> **lisati said:**
> There are some options:
[LIST=1]
[*]Use the Add/remove programs menu item (v9.04 and earlier) or the Software shop (9.10) - this is on the Applications menu.
[*]Use "Synaptic Pacakage manager" (on the System->Administration menu)
[*]Go to the website for the software you are interested in, and look for a ".deb" installation file
[/LIST]

Sorry, didn't read that clearly... you did specify the "Software Center" for 9.10 and above!

9.10 doesn't have "Add/Remove Programs" on the Applications menu... did you mean "Ubuntu Software Center"?

---

### Post by Don Bowen on 2009-11-24
> **oldos2er said:**
> You downloaded Thunderbird with Thunderbird?? What site did you download from?
I downloaded Thunderbird Email Client with Mozilla's Firefox web browser.

---

### Post by Don Bowen on 2009-11-24
> **Cheesemill said:**
> [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)
wow... that guide installed a ton of software and then started asking me to reconfigure my email client.
Time to re-install ubuntu.... back in a while.
(Yes, I do it frequently...it's the only way to make sure things are back as they were.... in the absence of good imaging software.... which Ubuntu has not!)

---

### Post by oldos2er on 2009-11-24
Did you get the source code, or ready-to-run binaries? In other words, can you post a list of the files in the extracted archive?

---

### Post by jmask on 2009-11-24
Don

Inside the directory that was created when you uncompressed the tar.gz there usually exists a text file, perhaps "readme", with installation instructions. You just follow those to gey your software installed.

Note: You may have to install extra packages to accomplish all the tasks listed in the instructions file.

---

### Post by lisati on 2009-11-24
> **Don Bowen said:**
> Sorry, didn't read that clearly... you did specify the "Software Center" for 9.10 and above!

9.10 doesn't have "Add/Remove Programs" on the Applications menu... did you mean "Ubuntu Software Center"?

You're right, my mistake. Although I took a look when it was first released I haven't installed 9.10 yet (perhaps it was a bad download but it didn't play nice with my machines when run from a USB memory stick)

---

### Post by EssexEagle on 2009-11-24
> **Don Bowen said:**
> If I were going to install the Thunderbird files I downloaded, what is the first step?  Unzip them? OK...did that... now what...


If you've got a .deb file then open a terminal, navigate to the directory in which it's saved by typing
```
cd *directory_name*
```
(the cd command stands for "change directory"), then install by typing
```
sudo dpkg -i *filename.deb*
```
You'll need to enter your password, although it won't appear on the screen.  (dpkg is the package manager for Debian - Ubuntu is based on Debian, hence the .deb filename for Ubuntu packages.  The -i means that you want to use the install option for dpkg.)


Hope this helps!

---

### Post by EssexEagle on 2009-11-24
> **Don Bowen said:**
> wow... that guide installed a ton of software and then started asking me to reconfigure my email client.
Time to re-install ubuntu.... back in a while.
(Yes, I do it frequently...it's the only way to make sure things are back as they were.... in the absence of good imaging software.... which Ubuntu has not!)

Yikes!  Erm, OK then...

---

### Post by stoogiebuncho on 2009-11-24
> **Don Bowen said:**
> 
ok...that brings me back here...  I get it that we are supposed to use synaptic and other installations "helpers" because they are good at installing things, and we poor humans are not.

Yes, it's easier to just go with the package installers, and I've learned to look for a .DEB file so the debian install "helper" thingie can do the install for me.... it's that part about doing it for me that chafes... 

I can only conclude that it must be prohibitively difficult to install anything by hand in Ubuntu and that's probably due to the Linux approach to security.  
If that's true, why would Mozilla let me download Thunderbird?  Just so that I can stare blankly at the uncompressed files?  


Compiling a program from source is not an easy task in any operating system.  Using a "helper" like Synaptic or a .DEB file is the same as installing a program from an .exe file in Windows.

As someone who has used Ubuntu for years, I have never learned to compile programs from source, because it's confusing and there's no reason to learn if you don't want to.  This is how I install programs:
1. Check add/remove and synaptic and install from there if possible.  Then you get the added benefit of automatic updates.
2. If you can't find it, download a .deb file.  Simply double-click it, and it will install by itself, just like an .exe file.

If you want to learn how to compile, that's great.  Just don't expect it to be as straight-forward as the other installation options.  Installing a program is complicated in any operating system, so doing it by hand will therefore also be complicated.

---

### Post by ncweber on 2009-11-24
I've been there, my friend.  The problem is that when you ask for specific help, you tend to get responses the say, "Do this" without giving specifics, or explaining why you do that.  People tend to do this because when you know the solution, it's hard to imagine someone who doesn't know.  We are naturally self-centered thinkers as a species.

It can be frustrating.  But be cautious.  Once while trying to extract similar info on this forum, I got to frustrated that I "lost it" in one of my posts, and got a threat of a ban by forum administrators.  The "inflammatory" post was removed.  So, I try to exhaust resources elsewhere before coming to the forums.  In the end, though.  Someone here has the answer you need.  It's just a matter of waiting for them to come online and notice your post.

> **Don Bowen said:**
> I went to the site and found 
" If you have trouble installing a .tar.gz file, you can ask for help on [the Ubuntu Forums]("http://www.ubuntuforums.org/")."
ok...that brings me back here...  I get it that we are supposed to use synaptic and other installations "helpers" because they are good at installing things, and we poor humans are not.

Still, when I download Thunderbird and then unzip the compressed file, it dumps a whole bunch of files into a folder.... as if I might be able to do something with them.  I still wonder what that might be.

Yes, it's easier to just go with the package installers, and I've learned to look for a .DEB file so the debian install "helper" thingie can do the install for me.... it's that part about doing it for me that chafes... 

I can only conclude that it must be prohibitively difficult to install anything by hand in Ubuntu and that's probably due to the Linux approach to security.  
If that's true, why would Mozilla let me download Thunderbird?  Just so that I can stare blankly at the uncompressed files?  

Someone knows how to install things in Ubuntu without a "helper"... probably the guys who wrote the helpers, for example.

It's the same old philisophical divide.  There are those who don't care what the engine looks like as long as the car goes forward, and then there are those who want to stop the car and open the hood.

Let me end with a simple question.  If I were going to install the Thunderbird files I downloaded, what is the first step?  Unzip them? OK...did that... now what...
Is this not how we learn?

---

### Post by philinux on 2009-11-24
> **Don Bowen said:**
> 

I can only conclude that it must be prohibitively difficult to install anything by hand in Ubuntu and that's probably due to the Linux approach to security.  
If that's true, why would Mozilla let me download Thunderbird?  Just so that I can stare blankly at the uncompressed files?  



Not true. And you can download mostly anything from anywhere in ubuntu windows or mac.

[http://laptoplogic.com/resources/a-beginners-guide-on-how-to-install-linux-software](http://laptoplogic.com/resources/a-beginners-guide-on-how-to-install-linux-software)

---

### Post by ncweber on 2009-11-24
> **philinux said:**
> Not true. And you can download mostly anything from anywhere in ubuntu windows or mac.

[http://laptoplogic.com/resources/a-beginners-guide-on-how-to-install-linux-software](http://laptoplogic.com/resources/a-beginners-guide-on-how-to-install-linux-software)

Cool.  Good site.  I'll have to bookmark this for later use. :D

---

### Post by sandyd on 2009-11-24
install ubuntuzilla. then in the terminal, run ubuntuzilla.py. that will automatically guide you to install the latest version of firefix / thunderbird

---

### Post by Don Bowen on 2009-11-26
> **philinux said:**
> Not true. And you can download mostly anything from anywhere in ubuntu windows or mac.

[http://laptoplogic.com/resources/a-beginners-guide-on-how-to-install-linux-software](http://laptoplogic.com/resources/a-beginners-guide-on-how-to-install-linux-software)
In what way is that not true?  I suppose I should define terms.  Using Synnaptic is not installing the software yourself.  Synnaptic does that for you.  Are you suggesting that installing anything without a "helper" program is easy?  

I suppose the real problem I'm having is that Ubuntu is different.  It's odd to install software and have no idea where it goes (what folder it's in).  Windows suffers from that as well.  Install programs scatter .DLLs all over, and you're lucky if the uninstall program remembers to remove them.  

The links people gave, however, are invaluable.  I've been reading one of them that does explain it pretty well.

NB:  I'm not looking to compile from source.  That is a different process, and what comes from that is what you install.  I'm looking for something like
1: make a folder
2: put the uncompressed software in the folder
3: run the program
That's the basics for any computer, really.  Linux (Ubuntu) just seems secretive about the process.  That presents an opportunity to learn something.   What is synnaptic doing that I can't do myself?

---

### Post by oldos2er on 2009-11-26
Synaptic can show you where each file in a given package is installed. So can **sudo dpkg -L <package name>** run in a terminal.

 If you downloaded the ready-to-run Thunderbird package, you should be able to run it using the steps you described, i.e. extract the folder, then run the program.

---

### Post by aysiu on 2009-11-26
I don't see why you would want to run the Thunderbird from the Mozilla site instead of just using Synaptic (they're the same versions--see attached screenshots).

But if you insist, then UbuntuZilla is definitely the best way to go:
[http://ubuntuzilla.sourceforge.net](http://ubuntuzilla.sourceforge.net)

---

### Post by philinux on 2009-11-26
> **Don Bowen said:**
> In what way is that not true?  I suppose I should define terms.  Using Synnaptic is not installing the software yourself.  Synnaptic does that for you.  Are you suggesting that installing anything without a "helper" program is easy?  

I suppose the real problem I'm having is that Ubuntu is different.  It's odd to install software and have no idea where it goes (what folder it's in).  Windows suffers from that as well.  Install programs scatter .DLLs all over, and you're lucky if the uninstall program remembers to remove them.  

The links people gave, however, are invaluable.  I've been reading one of them that does explain it pretty well.

NB:  I'm not looking to compile from source.  That is a different process, and what comes from that is what you install.  I'm looking for something like
1: make a folder
2: put the uncompressed software in the folder
3: run the program
That's the basics for any computer, really.  Linux (Ubuntu) just seems secretive about the process.  That presents an opportunity to learn something.   What is synnaptic doing that I can't do myself?

Linux is not windows. You need to forget windows ways. 

[https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows)
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

It is not secretive it just organises thing in a different structure. There is a learning curve.

[http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)

Google away.

---

### Post by Don Bowen on 2009-11-26
> **oldos2er said:**
> Synaptic can show you where each file in a given package is installed. So can **sudo dpkg -L <package name>** run in a terminal.

 If you downloaded the ready-to-run Thunderbird package, you should be able to run it using the steps you described, i.e. extract the folder, then run the program.
I have clicked every bin file i could find and none of them do anything.  That's why I'm perplexed.  It's not like Mozilla is an obscure software supplier... they're well known... and yet, if you download their software.... there's nothing to do with it... you have to wait until some some packet software keeper dude decides to put it in a repository that Synaptic knows about... Why download it then?  When you click on "download"... shouldn't it just say, "No, use synnaptic".

---

### Post by aysiu on 2009-11-26
> **Don Bowen said:**
> Why download it then? Good question. Just use Synaptic.

---

### Post by Don Bowen on 2009-11-26
> **philinux said:**
> Linux is not windows. You need to forget windows ways. 

[https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows)
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

It is not secretive it just organises thing in a different structure. There is a learning curve.

[http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)

Google away.
I agree ... forgetting windows ways is a good idea.  Let us turn then to Linux ways...
IN Linux, the first step to install a program is:
1. download it
2. decompress it
3. ???
4. ???
5. ???
there must be a knowable, consistent, way to install things that is the same for every program.  (unless, of course, there are multiple ways to get Linux to "run a program" in which case you might have to have multiple ways to install.  Yes, different programs depend on different libraries, but overall, there must be a pattern each install follows....either that or Linux is simply chaotic....which I doubt.)

I think the answer is that in Ubuntu, you DO NOT install things yourself.  That's just  NOT how it's done.  The process is complicated and difficult or we wouldn't need synaptic.  Notice that no one can explain how to install a reputable software like Thunderbird.  We have to read lengthy articles about how to install it OR wait for the repository gods to bless it.
    TrueCrypt, for example, is easy to install.  (well not easy compared to windows, but we're not following windows ways anymore).  TrueCrypt has an install program that comes with it.  Why doesn't Thunderbird?  Why doesn't every program?  What developer writes a program and leaves users with no way to install it?   I suppose I should quit asking.  Use synaptic or the Debian installer or read the lengthy article.

---

### Post by oldos2er on 2009-11-26
By "bin file', do you mean a file with a *bin extension? See if there isn't a file named "thunderbird" with no extension, and try it. If you would answer the questions put to you (see post #11), it would help us to help you.

---

### Post by aysiu on 2009-11-26
> **Don Bowen said:**
> The process is complicated and difficult or we wouldn't need synaptic. Actually, Synaptic is what makes it simple and easy. > Notice that no one can explain how to install a reputable software like Thunderbird. Well, the way to install it is through Synaptic, but you already stated in the first post you know how to do that. > OR wait for the repository gods to bless it. Most software has been "blessed" by the repositories "gods." Thundebird has had that "blessing" for years.

Do you have similar complaints you lodge on the Apple forums about the limitations of the iTunes App Store and how you have to wait for the App Store "gods" to "bless" apps and then jailbreak your phone to get other software installed?

Since you seem to want to rant instead of get support, I'm moving this thread to Recurring Discussions.

---

### Post by oldos2er on 2009-11-26
"there must be a knowable, consistent, way to install things that is the same for every program."

 There is; it's called the APT system. Rather than in Windows, where each program comes with its own installer, Ubuntu (and most other flavors of Linux, whether or not they use APT) uses APT to do all the dirty work of installing, removing, updating, and managing software. The purpose of this is to simplify things for the user. That does not mean you are not free to do these tasks yourself--you are. You (and me, and everyone) are only limited by your knowledge, or lack thereof, of how to do so.

---

### Post by philinux on 2009-11-26
> **Don Bowen said:**
> I agree ... forgetting windows ways is a good idea.  Let us turn then to Linux ways...
IN Linux, the first step to install a program is:
1. download it
2. decompress it
3. ???
4. ???
5. ???


IN Linux, the first step to install a program is:-
1. Whichever distro it is, use it's package management software tool, in ubuntu that is apt, synaptic.

2. find package you want

3. You tell synaptic or add/remove to install it. You are in control of what is installed.

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Don Bowen on 2009-11-26
(I forgot to quote the original, but someone asked me to revisit post 11 and list the files we have to work with... this post is my answer).

when you go to the Thunderbird site, you get the opportunity to download a compressed file (a .tz).  The website seems to be aware of what OS you're using when you go there, so it offers the download appropriate to the OS you're using.

What files are in the compressed source?  there are at least 10 subdirectories and naming all those files individually would number in the hundreds.  I'll presume you want to know what files are in the "root" directory created when you unzip Thunderbird.
dependentlibs.list
libfreebl3.chk
libfreebl3.so
libldap50.so
libmozjs.so
libnspr4.so
libnss3.so
libnssckbi.so
libnssdbm3.so
libnssutil3.so
libplc4.so
libplds4.so
libprldap50.so
libsmime3.so
libsoftokn3.chk
libsoftokn3.so
libsqlite3.so
libssl3.so
libxpcom.so
libxpcom_compat.so
libxpcom_core.so
libxpistub.so
license.html
license.txt
mozilla-installer-bin
mozilla-xremote-client
readme.txt
removed-files
run-mozilla.sh
thunderbird
thunderbird-bin
updater
updater.ini
xpicleanup

the readme.txt file says...
"For information about installing, running and configuring Thunderbird
including a list of known issues and troubleshooting information, 
refer to: http://getthunderbird.com/releases/"
Even Mozilla knows that it's HARD to install something.
clicking, opening, the "mozilla-installer-bin" doesn't do anything... though it seems like it ought to.

---

### Post by Don Bowen on 2009-11-26
> **philinux said:**
> IN Linux, the first step to install a program is:-
1. Whichever distro it is, use it's package management software tool, in ubuntu that is apt, synaptic.

2. find package you want

3. You tell synaptic or add/remove to install it. You are in control of what is installed.

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
and if the program you want isn't OKd by the repository central committee, you wait.   That really grates on me.

---

### Post by Don Bowen on 2009-11-26
> **oldos2er said:**
> "there must be a knowable, consistent, way to install things that is the same for every program."

 There is; it's called the APT system. Rather than in Windows, where each program comes with its own installer, Ubuntu (and most other flavors of Linux, whether or not they use APT) uses APT to do all the dirty work of installing, removing, updating, and managing software. The purpose of this is to simplify things for the user. That does not mean you are not free to do these tasks yourself--you are. You (and me, and everyone) are only limited by your knowledge, or lack thereof, of how to do so.
"to make things easier" made laugh out loud.  I know it shouldn't...it's not nice to say. I'm sorry, but I begin to understand why folks don't use Linux much.  It's simply to hard to work with.

---

### Post by Tibuda on 2009-11-26
> **Don Bowen said:**
> "to make things easier" made laugh out loud.  I know it shouldn't...it's not nice to say. I'm sorry, but I begin to understand why folks don't use Linux much.  It's simply to hard to work with.

You are the one making it hard. Delete that file you downloaded from Mozilla and [use the repositories]("apt:thunderbird").

---

### Post by philinux on 2009-11-26
> **Don Bowen said:**
> and if the program you want isn't OKd by the repository central committee, you wait.   That really grates on me.

Or you got to the developers website and install their version which could be a later version. The ubuntu repo managers have security and stability as their creed. Newer version may be buggy.

But for a bog standard like thunderbird I would use the repo version.

If it's a package that is not in synaptic then you would use a developers deb package. 

Some stuff that's not in synaptic can be found here.

[http://www.getdeb.net/welcome/](http://www.getdeb.net/welcome/)

Things change. Looks like you have to register now.

Ask in the ABT forum if you have a specific package you'd like to install thats not in the repos.

Also if you want full control research "arch linux". You have to compile all your own programs from source.

---

### Post by Tibuda on 2009-11-26
> **philinux said:**
> Also if you want full control research "arch linux". You have to compile all your own programs from source.

Arch is not Gentoo. Pacman uses binaries packages, but you can also install from source using ABS.

---

### Post by philinux on 2009-11-26
> **danielrmt said:**
> Arch is not Gentoo. Pacman uses binaries packages.

Good heads up.

---

### Post by philinux on 2009-11-26
> **Don Bowen said:**
> "to make things easier" made laugh out loud.  I know it shouldn't...it's not nice to say. I'm sorry, but I begin to understand why folks don't use Linux much.  It's simply to hard to work with.

What the heck is hard about this.

Open add/remove or synaptic, search and install thunderbird.

Using firefox address bar
apt:thundebird

Open a terminal Apps>access>terminal

```
sudo apt-get install thunderbird
```

I found this easy peasy coming from windows. And the system updates the packages too. Very nice.

---

### Post by ZankerH on 2009-11-26
Wait, am I getting this right?

The OP for some reason insists installing software is "hard", based on the fact that he refuses to use the "easy" way?

*snip*

-Control/individualisation
-Ease of use for people new to GNU/Linux

PICK ONE.

---

### Post by Tibuda on 2009-11-26
> **ZankerH said:**
> Wait, am I getting this right?

The OP for some reason insists installing software is "hard", based on the fact that he refuses to use the "easy" way?

Yeah, you hit the nail on the head here.

---

### Post by Keyper7 on 2009-11-26
Two things:

1) The OP has not given one reasonable argument for refusing to use the repositories (version in the Mozilla site is 2.0.0.23, version in the Jaunty repositories, not even the Karmic ones, is 2.0.0.23 as well, the complaints about "waiting for approval" do not make sense).

2) I downloaded the thunderbird tar.gz from mozilla.com, doubled clicked on it, dragged the "thunderbird" folder to my desktop, opened this folder and doubled clicked on the "thunderbird" binary (not exactly the most obscure filename ever, by the way). The program immediately started. *It was the first time I ever did that and I only used the mouse*.

This thread is a waste of everyone's time.

---

### Post by Tipped OuT on 2009-11-26
> **ZankerH said:**
> Wait, am I getting this right?

The OP for some reason insists installing software is "hard", based on the fact that he refuses to use the "easy" way?


> **Keyper7 said:**
> Two things:

1) The OP has not given one reasonable argument for refusing to use the repositories.

2) I downloaded the thunderbird tar.gz from mozilla.com, doubled clicked on it, dragged the "thunderbird" folder to my desktop, opened this folder and doubled clicked on the "thunderbird" binary (not exactly the most obscure filename ever, by the way). The program immediately started.

This thread is a waste of everyone's time.

/thread

---

### Post by Don Bowen on 2009-11-26
> **Keyper7 said:**
> Two things:

1) The OP has not given one reasonable argument for refusing to use the repositories (version in the Mozilla site is 2.0.0.23, version in the Jaunty repositories, not even the Karmic ones, is 2.0.0.23 as well, the complaints about "waiting for approval" do not make sense).

2) I downloaded the thunderbird tar.gz from mozilla.com, doubled clicked on it, dragged the "thunderbird" folder to my desktop, opened this folder and doubled clicked on the "thunderbird" binary (not exactly the most obscure filename ever, by the way). The program immediately started. *It was the first time I ever did that and I only used the mouse*.

This thread is a waste of everyone's time.
when i drag the folder to the desktop, open it, double click on "thunderbird", nothing happens.  when I right click it and choose open, I get four choices.  Display will show the script, but none of the others will start the program running.  Perhaps I have the wrong file?

---

### Post by Don Bowen on 2009-11-26
> **danielrmt said:**
> Yeah, you hit the nail on the head here.
Well, I was hoping to learn what "the easy way" does for me that I can't do myself.  As for the repositories, they are obviously the easiest way to get someone else to install something for you... as long as you wait until the program you want to use shows up in one.  Example:  if I wanted to install VLC 1.03... I can't... it's not in the repository yet, though I have no doubt it will be.
I can tell it's probably time to stop asking.  'Sorry.  I meant no harm.

---

### Post by Tibuda on 2009-11-27
> **Don Bowen said:**
> Well, I was hoping to learn what "the easy way" does for me that I can't do myself.
**heavily edited**

I think what you want to do is very well described in this section: [http://www.psychocats.net/ubuntu/installingsoftware#gdebi](http://www.psychocats.net/ubuntu/installingsoftware#gdebi)

Synaptic/USC don't compile the app from the source, it downloads a pre-compiled package installer with the .deb extension. Sorry, Mozilla and Videolan don't create a package for their apps like this. If you want to do exactly what synaptic does, try [Skype]("http://www.skype.com/download/"), [Opera]("http://www.opera.com/browser/download/") or [Handbrake]("http://handbrake.fr"), because they provide .deb package installers.

Canonical package software and add them to the repositories for you, but they freeze the version on each Ubuntu release. If the app developer don't provide a package and you really need the lastest version -- which is very very rare -- sorry, you'll have to compile it yourself. Some Linux distros are not like Ubuntu and don't freeze the apps, they are the "rolling release" distros like Debian-Unstable, PCLinuxOS and ArchLinux. (you can wonder why Ubuntu freezes the package versions by reading the name of the rolling-release branch of Debian)

---

### Post by oldos2er on 2009-11-27
Vlc 1.0.3-1 is available through a Launchpad repository: [https://launchpad.net/~c-korn/+archive/vlc](https://launchpad.net/~c-korn/+archive/vlc)

---

### Post by Don Bowen on 2009-11-28
vlc was just an example... Nobody wants to hear it, but lets try another... Thunderbird 3.0 (RC1) is available for download from Mozilla.  You specify the OS you're using (Ubuntu) and download the equivalent of a zip file.  You unzip it... then what? 

 Running the one file called "Thunderbird" does nothing... I suppose... I'm just amazed that Mozilla would let me download something and then give no way to install it.  What's the point of that?  (Yes I'll go read the psycho article and study more about how to install things.  I'm just disappointed that you have to read technical articles about how to install things... sigh...) 

 In the absence of a .DEB file (which I admit do install very nicely), no one has yet to describe how to install a program.  My question has already been answered, I know.  You don't install things (unless you have a .DEB) file... OK I get that... but that makes me wonder why I can download a program  like Thunderbird in the first place.   Does Mozilla expect me to re-compile it?  I don't think so.   That means that there's something I can do with the files they gave me...
make folders, put them in folders, modify config files... something that will get the program to run.  I'm sure the lengthy articles will explain that... it's just frustrating.

---

### Post by stoogiebuncho on 2009-11-28
I think perhaps what this comes down to is that there are several ways of installing software in Ubuntu.  Some are very easy, some are not so easy, and require you to learn to do some things yourself that you don't have to do when you install things the easy way.

So if Mozilla only offers Thunderbird in a format that takes more work to install, you either have to learn how to do it their way, or find Thunderbird somewhere else in an easier to install format.  This doesn't mean that installing software is hard in Ubuntu, it just means that Mozilla isn't offering the software to you in the easiest format for your operating system.  If Mozilla did not offer an .exe file for Thunderbird, it would be quite difficult to install it in Windows.  That doesn't mean installing software is hard in Windows, it just means that the easy way is not being offered to you.

Because Ubuntu (and other Debian-based linux distros) represents such a small portion of computer users, you will find that it often does not work to go directly to the company website and download software from them.  A lot of companies don't take the time to make their software work with linux, much less a smaller sub-set of linux users.  Instead, you will learn to install software through Synaptic, .deb files (getdeb.net is a great resource), and other places that are geared towards your operating system.

I agree that it is frustrating that Mozilla offers a download with no installation instructions.  However, you will find that as you use Ubuntu, you will no longer go to Mozilla's website when you want to install Thunderbird, you will go to one of the other places mentioned that is geared towards Ubuntu.

It's one of the challenges of being in the minority.  Once you get used to it you don't even think twice about it.

---

### Post by oldos2er on 2009-11-28
There isn't really an installation program for Thunderbird; you simply extract the archive, then run "thunderbird". Just for fun, I downloaded thunderbird-3.0rc1.tar.bz2, extracted it, clicked "thunderbird" then "Run in terminal," and it worked. If it's not working for you, you may be missing a dependency. If you try running the program in a terminal, it may give you some helpful output.

---

### Post by Don Bowen on 2009-11-28
> **oldos2er said:**
> There isn't really an installation program for Thunderbird; you simply extract the archive, then run "thunderbird". Just for fun, I downloaded thunderbird-3.0rc1.tar.bz2, extracted it, clicked "thunderbird" then "Run in terminal," and it worked. If it's not working for you, you may be missing a dependency. If you try running the program in a terminal, it may give you some helpful output.
Thank you for taking the time to test that and reply. I'm grateful.
When I followed the steps you did, I got nothing.  There's not even a screen message to capture and post here.
I figured...ok..maybe the folder has to be on the desktop, so I moved the folder (the one that resulted from decompressing the zip file I downloaded from Mozilla) to my desktop.  I browse to the "Thuderbird" file, double click it, then choose "run in terminal".  Nothing happens.
Hmmm.... maybe I need to un-install the version that's already installed and working... ok...
run synnaptic, locate Thunderbird, mark it for complete removal, then apply.
Thunderbird uninstalls.
Return to the desktop, browse to the "Thunderbird" file, double click it, choose "run in terminal"
and.... nothing happens.
Now it could be that I'm missing a library Thunderbird needs to run, but that seems unlikely since the previous version (synnaptic installed) runs fine.
Is there some other file I should be running in Terminal?

---

### Post by Nerd King on 2009-11-28
I think your problem stems from the fact that you're coming at this from a windows perspective. Linux is done differently. We have software repos, because it means all the programs we get are checked for security. It prevents the virus mess present on Windows. Also the package manager handles dependencies for you. You know like how you need dotnet3 for something on windows, but the program won't go get it for you if you need it, you have to hunt for it yourself? Not in Linux, the package management system automates all that for you. It's EASIER to install software in Linux than it is in Windows. I know because I've got complete non-computer-users installing software happily in linux when all they installed on windows was viruses.

These downloads from mozilla.. you can compile if you wish, you must have chosen to download the source. That's an option for experts. They usually also provide binaries in either .deb or .rpm or .tar.gz formats. First two are click and run, last one is usually a case of reading the README file.

.tar.gz is either a matter of putting files in the right folders or you simply run the main program once its extracted (ie it's portable, like portable apps on windows).

Imaging software. In short we don't need it. As root, zip up the whole drive (actually .tar.gz is more suitable than zip) and job's done. If you need to reset your drive, go in with a live-cd, delete all the files, extract that zip and bob's your uncle. No extra software needed. Or alternatively, there are linux livecds that'll do it all for you automatically, just take a look on distrowatch.

---

### Post by Nerd King on 2009-11-28
> **Don Bowen said:**
> In what way is that not true?  I suppose I should define terms.  Using Synnaptic is not installing the software yourself.  Synnaptic does that for you.  Are you suggesting that installing anything without a "helper" program is easy?  

I suppose the real problem I'm having is that Ubuntu is different.  It's odd to install software and have no idea where it goes (what folder it's in).  Windows suffers from that as well.  Install programs scatter .DLLs all over, and you're lucky if the uninstall program remembers to remove them.  

The links people gave, however, are invaluable.  I've been reading one of them that does explain it pretty well.

NB:  I'm not looking to compile from source.  That is a different process, and what comes from that is what you install.  I'm looking for something like
1: make a folder
2: put the uncompressed software in the folder
3: run the program
That's the basics for any computer, really.  Linux (Ubuntu) just seems secretive about the process.  That presents an opportunity to learn something.   What is synnaptic doing that I can't do myself?
And you can do exactly that. But you're in a Windows mindset here. Take the advantages linux gives you through Synaptic. Install your software that way and it'll always auto-update (and only one updater, not the 7 in your system tray eating memory like in Windows) and always find dependencies. You seem to want to make things harder than they really are.

---

### Post by Don Bowen on 2009-11-28
> **Keyper7 said:**
> Two things:

1) The OP has not given one reasonable argument for refusing to use the repositories (version in the Mozilla site is 2.0.0.23, version in the Jaunty repositories, not even the Karmic ones, is 2.0.0.23 as well, the complaints about "waiting for approval" do not make sense).

2) I downloaded the thunderbird tar.gz from mozilla.com, doubled clicked on it, dragged the "thunderbird" folder to my desktop, opened this folder and doubled clicked on the "thunderbird" binary (not exactly the most obscure filename ever, by the way). The program immediately started. *It was the first time I ever did that and I only used the mouse*.

This thread is a waste of everyone's time.
I'm sorry that my request doesn't measure up to your standards of "reasonable", but I'll attempt to explain:  I was hoping to learn something about this OS by installing by hand, but I suppose the pursuit of learning something new isn't good enough reason for you.   You seem to think it a waste of time.  I'm sorry to hear that.

   I've already said the repositories are the easiest way to install anything.  No one disputes that, but their existence does make me wonder about installations.  If there's a need to have Ubuntu installations arbitrated and automated by a third party, then the process must be different than what I'm used to.  That's intriguing and makes me wonder "how is it different?"  The repositories, all by themselves, don't answer that.  Fortunately, there are good articles to read and people willing to help.  Thank you for your help and for your time.

---

### Post by Nerd King on 2009-11-28
> **Nerd King said:**
> And you can do exactly that. But you're in a Windows mindset here. Take the advantages linux gives you through Synaptic. Install your software that way and it'll always auto-update (and only one updater, not the 7 in your system tray eating memory like in Windows) and always find dependencies. You seem to want to make things harder than they really are.
Apologies to everyone else for replying to this thread, I shouldn't have as now I see the whole thread it's fairly clear this chap's trying to wind people up. In short, don't run before you can walk. Start out the simple way, and the harder ways will come later. Stop making this difficult for yourself, if you really aren't winding people up. However, as I say, I think this is a troll.

---

### Post by Nerd King on 2009-11-28
> **Don Bowen said:**
> I'm sorry that my request doesn't measure up to your standards of "reasonable", but I'll attempt to explain:  I was hoping to learn something about this OS by installing by hand, but I suppose the pursuit of learning something new isn't good enough reason for you.   You seem to think it a waste of time.  I'm sorry to hear that.

   I've already said the repositories are the easiest way to install anything.  No one disputes that, but their existence does make me wonder about installations.  If there's a need to have Ubuntu installations arbitrated and automated by a third party, then the process must be different than what I'm used to.  That's intriguing and makes me wonder "how is it different?"  The repositories, all by themselves, don't answer that.  Fortunately, there are good articles to read and people willing to help.  Thank you for your help and for your time.
Do you actually READ any of the replies? You're coming accross rather rude to people who are trying to help you. The package manager exists to make it EASY. See that word "easy", look it up in a dictionary. The file you downloaded is like a portable app in Windows. thunderbird is the one you need to run. If you get the "4 options" box, choose run. To stop it coming up again you can right-click the file, properties, permissions and tick the box to let it run as an executable.

Now read that. Do it. And frankly if you don't like it, get back to Windows.

---

### Post by Diluted on 2009-11-29
I get the impression that Don Bowen is wondering what goes behind a package manager. He (or she) knows how to install programs with Synaptic, but is wondering how to do so without a package manager. The reason why he said Linux is hard in this respect is, given the lack of a package manager, there is no standardized way to install programs compared to other platforms (i.e., installers or dragging .app). You must either compile from source, hope the vendors have included a script for installation, or (in Don Bowen's case) hope that the installation script works in the first place.

In Linux, things are not standardized compared to other platforms. For example, some distributions have different library versions from others. Some may have different version of dependencies. Vendors have two choices: to release a statically built program, or to release the source code.

In a statically built program, all the dependencies are contained so all you need to do is to extract the archive and you can start running the program on any Linux distribution. I think this is what is being offered for the Linux downloads of Firefox and Thunderbird. I'm not sure why it isn't working with your system, so I can't help you with that.

However, as with most programs, they need to be stored in safe locations. You can continue to run statically built programs in your home directory, but it has the security risk of being modified easily. Some vendors may supply a script to assist in moving the files to the correct locations (which doesn't seem to work for Don Bowen either).

Now, I assume it has been the tradition of UNIX to dynamic linking to reduce disk space or RAM usage. Distributions will usually turn to the source version. They may need to compile it, or patch it to (I presume) ensure it is dynamically-linked and working with their version of the distribution. Once they have done that, they will put the compiled program into a package. When you use a package manager to install a package, it takes whatever the maintainer has compiled and moves it to the right place.

This process doesn't apply to open source software alone. Some proprietary software may be packages as well just by putting what the vendor has supplied and including instructions on where each file needs to go to. In cases where the software interferes with the base system, maintainers have to ensure there are ways to undo the modifications when uninstalling the program.

In short, I'm assuming package managers are there to accommodate the differences in Linux distributions.

---

### Post by quinnten83 on 2009-11-29
> **Don Bowen said:**
> wow... that guide installed a ton of software and then started asking me to reconfigure my email client.
Time to re-install ubuntu.... back in a while.
(Yes, I do it frequently...it's the only way to make sure things are back as they were.... in the absence of good imaging software.... which Ubuntu has not!)

uhm, 
good imaging software, well clonezilla is really 2 mm shorts of totally awesome. there is also things like back in time and flyback, which take snapshots, if I am not mistaken.

---

### Post by Don Bowen on 2009-11-29
Yes, I do read the replies, and many of them are quite useful.  Ticking the box that lets the program run as an executable was good advice (the box is already ticked), and getting a description of how other people run Thunderbird successfully was also instructive.  Not sure why I can't get it to run here, but I'll just wait for it to show up in some repository.
thank you all for your help.
I"m not here to wind people up.  I came to solve a problem.   I learned a lot, and I'm grateful for that.

---

### Post by chickengirl on 2009-11-29
> **Don Bowen said:**
> Yes, I do read the replies, and many of them are quite useful.  Ticking the box that lets the program run as an executable was good advice (the box is already ticked), and getting a description of how other people run Thunderbird successfully was also instructive.  Not sure why I can't get it to run here, but I'll just wait for it to show up in some repository.
thank you all for your help.
I"m not here to wind people up.  I came to solve a problem.   I learned a lot, and I'm grateful for that.

Um... Thunderbird IS in the repository.

After reading the thread I'd like to draw a comparison for you. In Windows, to install a program, you download an .exe, you run it, and its embedded installation script unpacks all the files and puts them in the right place.

In Ubuntu, you open up Synaptic, search for the package you want, and install, OR, you download a .deb from somewhere and run it in GDebi. Either way, Synaptic then checks for any dependencies it needs to install for you (notice that this is something Windows installers don't do, so you'd better hope all dependencies were included or that you have them already), and then unpacks all the files from your package and puts them in the right place.

Synaptic performs the same function as a Windows program's install script. The main difference being, in Ubuntu you have one standard installer that can take any package and install it for you, and in Windows, each "package" (so to speak) comes with it's own "synaptic" built in.

In other words, installing a .deb with synaptic performs the exact same function as running a .exe in Windows. What Ubuntu has done is provide a standard installer program so that the packages you download don't have to come with one, which conveniently also doubles as "add/remove programs", giving you one-stop shopping for software management.

Sure, if that seems too "easy" for you, you COULD compile your programs yourself from source, but you don't do that on Windows, do you? Why the heck would you if the software publisher provides an .exe installer? And likewise, why the heck would you want to do it on Linux if the .deb is available to you?

Hope that made sense.

---

### Post by Tibuda on 2009-11-29
> **Don Bowen said:**
> Yes, I do read the replies, and many of them are quite useful.  Ticking the box that lets the program run as an executable was good advice (the box is already ticked), and getting a description of how other people run Thunderbird successfully was also instructive.  Not sure why I can't get it to run here, but I'll just wait for it to show up in some repository.
thank you all for your help.
I"m not here to wind people up.  I came to solve a problem.   I learned a lot, and I'm grateful for that.

What are your Ubuntu architecture: x86, amd64 or PPC? The Thunderbird binary available at mozilla website only works on x86. (I think it can work on 64bits if you install the compatibility libraries, but I have not tried it)

---

### Post by Don Bowen on 2009-11-30
> **danielrmt said:**
> What are your Ubuntu architecture: x86, amd64 or PPC? The Thunderbird binary available at mozilla website only works on x86. (I think it can work on 64bits if you install the compatibility libraries, but I have not tried it)
x64.  That may be the problem.  I'm afraid to ask now, but how do you install the compatibility libraries?

---

### Post by stoogiebuncho on 2009-11-30
> **danielrmt said:**
> What are your Ubuntu architecture: x86, amd64 or PPC? The Thunderbird binary available at mozilla website only works on x86. (I think it can work on 64bits if you install the compatibility libraries, but I have not tried it)

61 posts later, someone thinks to ask. :D  Good catch, danielrmt.

---

### Post by Keyper7 on 2009-11-30
> **Don Bowen said:**
> x64.  That may be the problem.  I'm afraid to ask now, but how do you install the compatibility libraries?

Package "ia32-libs" in Synaptic.

---

### Post by oldos2er on 2009-11-30
> **danielrmt said:**
> What are your Ubuntu architecture: x86, amd64 or PPC? The Thunderbird binary available at mozilla website only works on x86. (I think it can work on 64bits if you install the compatibility libraries, but I have not tried it)

 No, I've run 64-bit Ubuntu for awhile now, and Thunderbird (from thunderbird-3.Orc1.tar.bz2) works fine.

---

### Post by Tibuda on 2009-11-30
> **oldos2er said:**
> No, I've run 64-bit Ubuntu for awhile now, and Thunderbird (from thunderbird-3.Orc1.tar.bz2) works fine.

Well, it don't work for me (I don't have ia32-libs installed). No big deal for me, as I can use the 64bit executable from Canonical repositories. I have downloaded that file only to test it for the OP.

---

### Post by Don Bowen on 2009-11-30
> **Keyper7 said:**
> Package "ia32-libs" in Synaptic.
OK...installing those libraries caused Thunderbird 3.0 to run.  That's a good thing.
Now, all that remains is to put the thunderbird folder somewhere, create an Icon for it, and run it like any other program.
where does Ubuntu keep installed programs?
"/program files"  
???
I tried creating a "launcher" but nothing showed up on the desktop.
I found the icons in the "thunderbird" folder, so I know I'm close.
Also, there's probably a way to get the program to run with the terminal window closed... it opens one automatically, and I notice the previous version didn't do that.

---

### Post by Tibuda on 2009-11-30
> **Don Bowen said:**
> where does Ubuntu keep installed programs?
"/program files"  
The package manager usually puts executables on /usr/bin and libraries on /usr/lib, but for those apps you manage yourself, you better separate them and use /opt (which would require admin privilegies) or your user home folder (like /home/username/apps).

---

### Post by Don Bowen on 2009-11-30
> **danielrmt said:**
> The package manager usually puts executables on /usr/bin and libraries on /usr/lib, but for those apps you manage yourself, you better separate them and use /opt (which would require admin privilegies) or your user home folder (like /home/username/apps).
admin root is done with "sudo -i" isn't it?
username/apps seems like a good idea..i'll try that.

---

### Post by Tibuda on 2009-11-30
> **Don Bowen said:**
> admin root is done with "sudo -i" isn't it?
username/apps seems like a good idea..i'll try that.

yes, that work when you are using a terminal. for launchers, you can just prepend **gksudo** to the launcher command. eg: to open nautilus file manager as root, you can create a launcher running **gksudo nautilus**.

---

### Post by Don Bowen on 2009-11-30
> **Don Bowen said:**
> admin root is done with "sudo -i" isn't it?
username/apps seems like a good idea..i'll try that.
interesting...if you close the terminal window, it also kills the app.

---

### Post by Mornedhel on 2009-11-30
If you want to know where installed files are kept, I suggest you install any package from the repositories (bear with me for a moment here), then run dpkg -L <packagename> in a terminal.  This outputs the files created/modified by the package with their full path, for instance :

```
user@host:~$ dpkg -L firefox-3.5
/.
/etc
/etc/apparmor.d
/etc/apparmor.d/disable
/etc/apparmor.d/usr.bin.firefox-3.5
/etc/firefox-3.5
/etc/firefox-3.5/profile
/etc/firefox-3.5/profile/bookmarks.html
/etc/firefox-3.5/profile/localstore.rdf
/etc/firefox-3.5/profile/prefs.js
/etc/firefox-3.5/profile/mimeTypes.rdf
/etc/firefox-3.5/profile/chrome
/etc/firefox-3.5/profile/chrome/userChrome-example.css
/etc/firefox-3.5/profile/chrome/userContent-example.css
/etc/firefox-3.5/pref
/etc/firefox-3.5/pref/firefox.js
/usr
/usr/lib
/usr/lib/firefox-addons
/usr/lib/firefox-addons/extensions
/usr/lib/firefox-addons/plugins
/usr/lib/firefox-addons/searchplugins
/usr/lib/firefox-addons/searchplugins/en-US
/usr/lib/firefox-addons/searchplugins/en-US/debsearch.gif
/usr/lib/firefox-addons/searchplugins/en-US/debsearch.src
/usr/lib/firefox-addons/searchplugins/en-US/amazondotcom.xml
/usr/lib/firefox-addons/searchplugins/en-US/answers.xml
/usr/lib/firefox-addons/searchplugins/en-US/creativecommons.xml
/usr/lib/firefox-addons/searchplugins/en-US/eBay.xml
/usr/lib/firefox-addons/searchplugins/en-US/google.xml
/usr/lib/firefox-addons/searchplugins/en-US/wikipedia.xml
/usr/lib/firefox-addons/searchplugins/en-US/yahoo.xml
/usr/lib/firefox-3.5.5
/usr/lib/firefox-3.5.5/components
/usr/lib/firefox-3.5.5/components/aboutCertError.js
/usr/lib/firefox-3.5.5/components/aboutPrivateBrowsing.js
/usr/lib/firefox-3.5.5/components/aboutRights.js
/usr/lib/firefox-3.5.5/components/aboutRobots.js
/usr/lib/firefox-3.5.5/components/aboutSessionRestore.js
/usr/lib/firefox-3.5.5/components/FeedConverter.js
/usr/lib/firefox-3.5.5/components/FeedWriter.js
/usr/lib/firefox-3.5.5/components/fuelApplication.js
/usr/lib/firefox-3.5.5/components/nsBrowserContentHandler.js
/usr/lib/firefox-3.5.5/components/nsBrowserGlue.js
/usr/lib/firefox-3.5.5/components/nsMicrosummaryService.js
/usr/lib/firefox-3.5.5/components/nsPlacesTransactionsService.js
/usr/lib/firefox-3.5.5/components/nsPrivateBrowsingService.js
/usr/lib/firefox-3.5.5/components/nsSafebrowsingApplication.js
/usr/lib/firefox-3.5.5/components/nsSessionStartup.js
/usr/lib/firefox-3.5.5/components/nsSessionStore.js
/usr/lib/firefox-3.5.5/components/nsSetDefaultBrowser.js
/usr/lib/firefox-3.5.5/components/nsSidebar.js
/usr/lib/firefox-3.5.5/components/WebContentConverter.js
/usr/lib/firefox-3.5.5/components/browser.xpt
/usr/lib/firefox-3.5.5/components/libbrowsercomps.so
/usr/lib/firefox-3.5.5/components/libbrowserdirprovider.so
/usr/lib/firefox-3.5.5/modules
/usr/lib/firefox-3.5.5/modules/distribution.js
/usr/lib/firefox-3.5.5/modules/openLocationLastURL.jsm
/usr/lib/firefox-3.5.5/run-mozilla.sh
/usr/lib/firefox-3.5.5/defaults
/usr/lib/firefox-3.5.5/defaults/preferences
/usr/lib/firefox-3.5.5/defaults/preferences/firefox-l10n.js
/usr/lib/firefox-3.5.5/defaults/preferences/firefox.js
/usr/lib/firefox-3.5.5/defaults/preferences/firefox-branding.js
/usr/lib/firefox-3.5.5/defaults/preferences/channel-prefs.js
/usr/lib/firefox-3.5.5/defaults/preferences/ubuntu-useragent.js
/usr/lib/firefox-3.5.5/browserconfig.properties
/usr/lib/firefox-3.5.5/blocklist.xml
/usr/lib/firefox-3.5.5/application.ini
/usr/lib/firefox-3.5.5/distribution
/usr/lib/firefox-3.5.5/distribution/distribution.ini
/usr/lib/firefox-3.5.5/chrome
/usr/lib/firefox-3.5.5/chrome/classic.jar
/usr/lib/firefox-3.5.5/chrome/classic.manifest
/usr/lib/firefox-3.5.5/chrome/en-US.jar
/usr/lib/firefox-3.5.5/chrome/en-US.manifest
/usr/lib/firefox-3.5.5/chrome/browser.jar
/usr/lib/firefox-3.5.5/chrome/browser.manifest
/usr/lib/firefox-3.5.5/.autoreg
/usr/lib/firefox-3.5.5/update.locale
/usr/lib/firefox-3.5.5/firefox.sh
/usr/lib/firefox-3.5.5/firefox-3.5-restart-required.update-notifier
/usr/lib/firefox-3.5.5/ffox-35-beta-profile-migration-dialog
/usr/lib/firefox-3.5.5/firefox
/usr/lib/xulrunner-addons
/usr/lib/xulrunner-addons/extensions
/usr/lib/xulrunner-addons/extensions/{972ce4c6-7e08-4474-a285-3208198ce6fd}
/usr/lib/xulrunner-addons/extensions/{972ce4c6-7e08-4474-a285-3208198ce6fd}/install.rdf
/usr/lib/xulrunner-addons/extensions/{972ce4c6-7e08-4474-a285-3208198ce6fd}/chrome.manifest
/usr/share
/usr/share/doc
/usr/share/doc/firefox-3.5
/usr/share/doc/firefox-3.5/README.Debian
/usr/share/doc/firefox-3.5/copyright
/usr/share/doc/firefox-3.5/firefox.cfg
/usr/share/doc/firefox-3.5/MPL.gz
/usr/share/menu
/usr/share/menu/firefox-3.5
/usr/share/bug
/usr/share/bug/firefox-3.5
/usr/share/bug/firefox-3.5/presubj
/usr/share/apport
/usr/share/apport/package-hooks
/usr/share/apport/package-hooks/firefox-3.5.py
/usr/bin
/usr/lib/firefox-addons/searchplugins/common
/usr/lib/firefox-3.5.5/defaults/syspref
/usr/lib/firefox-3.5.5/defaults/profile
/usr/lib/firefox-3.5.5/distribution/searchplugins
/usr/lib/firefox-3.5.5/abrowser
/usr/lib/firefox-3.5.5/abrowser-3.5
/usr/lib/firefox-3.5.5/firefox-3.5
/usr/lib/firefox-3.5.5/extensions
/usr/lib/firefox-3.5.5/plugins
/usr/lib/firefox-3.5.5/dictionaries
/usr/share/doc/firefox-3.5/changelog.Debian.gz
/usr/bin/abrowser-3.5
/usr/bin/firefox-3.5
/usr/bin/firefox
/usr/bin/abrowser
```

---

### Post by EssexEagle on 2009-11-30
> **Don Bowen said:**
> interesting...if you close the terminal window, it also kills the app.

Yep, because you're running it from that terminal session - end the session and everything running in that session disappears ;-)

This won't happen if you run the program from a launcher in your start menu (sorry I know it's not really called a "start" menu outside of Windows land, but I still call it that) or your desktop.

---

### Post by Diluted on 2009-11-30
Try appending an & to the end of your command.

---

### Post by amsum on 2009-12-01
I think the OP has downloaded tar file directly from Mozilla's website and what he wants is steps to install that tar file. So, here it is...

Steps:
1) Download the thunderbird-3.0rc1.tar.bz2 file at Desktop from [here]("http://www.mozillamessaging.com/en-US/thunderbird/3.0rc1/").
2) Now right-click the file and click "Extract Here" to extract it at Desktop. Now you have a new folder "thunderbird" at Desktop.
3) After you’ve unpacked the archive enter the following command to move it to a more convenient location:
    sudo mv thunderbird /opt/thunderbird3.0rc1
4) Everything should be in order now, so let’s move to the directory and make sure it works:
    cd /opt/thunderbird3.0rc1/
5) Finally, run the following command to launch Thunderbird:
    ./thunderbird
6) If everything works fine and you’ve set up your email accounts with little frustration. Next, you may want to create a clickable icon on your desktop so you don’t have launch the program via the command line. To create a desktop icon, simply right-click at the Desktop and select “Create Launcher” Then fill out the dialogue box with the following information:
    Type: Application
    Name: Thunderbird 3.0b4
    Command: /opt/thunderbird3.0b4/thunderbird
    Comment: This launches Thunderbird 3.0 beta 4.
7) Now Log-Off and relogin; and you will have a Thunderbird shortcut at Desktop.

Let me know if you still faces any issue.

---

### Post by Tibuda on 2009-12-01
> **Mornedhel said:**
> If you want to know where installed files are kept, I suggest you install any package from the repositories (bear with me for a moment here), then run dpkg -L <packagename> in a terminal.  This outputs the files created/modified by the package with their full path, for instance :
Or you can see the "installed files" page in the package properties in synaptic.

---

### Post by Don Bowen on 2009-12-03
> **amsum said:**
> I think the OP has downloaded tar file directly from Mozilla's website and what he wants is steps to install that tar file. So, here it is...

Steps:
1) Download the thunderbird-3.0rc1.tar.bz2 file at Desktop from [here]("http://www.mozillamessaging.com/en-US/thunderbird/3.0rc1/").
2) Now right-click the file and click "Extract Here" to extract it at Desktop. Now you have a new folder "thunderbird" at Desktop.
3) After you’ve unpacked the archive enter the following command to move it to a more convenient location:
    sudo mv thunderbird /opt/thunderbird3.0rc1
4) Everything should be in order now, so let’s move to the directory and make sure it works:
    cd /opt/thunderbird3.0rc1/
5) Finally, run the following command to launch Thunderbird:
    ./thunderbird
6) If everything works fine and you’ve set up your email accounts with little frustration. Next, you may want to create a clickable icon on your desktop so you don’t have launch the program via the command line. To create a desktop icon, simply right-click at the Desktop and select “Create Launcher” Then fill out the dialogue box with the following information:
    Type: Application
    Name: Thunderbird 3.0b4
    Command: /opt/thunderbird3.0b4/thunderbird
    Comment: This launches Thunderbird 3.0 beta 4.
7) Now Log-Off and relogin; and you will have a Thunderbird shortcut at Desktop.

Let me know if you still faces any issue.
Wow...that was clear, concise, to the point and effective.  I've been looking for clear directions like that for some time... thank you for taking the time to write that.  I've printed that out, and put it in my notes as my model for how to install something in Ubuntu.

The icon is the "Firebird", and it doesn't open a terminal window!  Wow... nice piece of work .. I wonder what suppressed the terminal window from opening? location in the /opt folder?

to summarize:  Installing Thunderbird (for me on a Dell Inspiron 1501 with Ubuntu x64) couldn't happen without installing the 32bit compatibility library and following the directions in this post.  Once folks helped me past those two, things went smoothly.  Thank you all for that help.

---

