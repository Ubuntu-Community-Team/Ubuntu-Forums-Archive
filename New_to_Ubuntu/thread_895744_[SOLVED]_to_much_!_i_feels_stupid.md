---
title: "[SOLVED] to much ! i feels stupid"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by hyperhopper on 2008-08-20
OH MAN! i have so many problems:(. family found out that the linix was working on my comp(or so they think)so i wubi installed kubuntu on one comp, (i dont know why she wanted kubuntu, i dont know the difference) and used an instalation cd i burned to put a comp fully on ubuntu regular. my brother, on the ubuntu regular, has no internet access, and is a heavy game addict and wants to play games like supertux and wormux, but i have no clue on how to install anything on ubuntu. I can install wormux from add remove ont the kubuntu , but i dont know how to transfer it to his computer. also, i dont know how to open archive files to make them work, like the ones attached to this post, or shell scripts. i also need to know, now that im running on ubuntu, WHY IS THE INTERNET SO SLOW? im not eggagerating, its about 15 times slower that windows xp on a wireless usb receiver. These are only the tip of the iceburg as far as my problems go, and i know it its a lot to ask , but can anybody please help me????:confused::confused::(:confused::confused:

---

### Post by LowSky on 2008-08-20
OK first off its called LINUX not LINIX.

If you barely know what your doing why did you install it on so many machines?

Ubuntu also has add/remove under Applications>add/remove

Why do you need to open archived files?

Have you rebooted you Router, turn it off then back on it might fix the slow internet. Or it could be your provider.

---

### Post by rbc on 2008-08-20
Installing packages without internet:
[https://help.ubuntu.com/7.10/add-applications/C/offline.html](https://help.ubuntu.com/7.10/add-applications/C/offline.html)

Cannot help with the slow internet issue. If I can offer some advice, though. Pick one computer to install Linux on, and ticker/play/screw things up/learn to fix, until you get comfortable with a new operating system

---

### Post by hyperhopper on 2008-08-20
i installed it kinda.... because i had to:( family politics, and my brother wanted an os on his old comp. anyway, when i boot up as windows it is fast, and i use firefox on both so that leds me to belive that the problem is... ubuntu:mad: well, thank you for the help!:KS:KS:KS

---

### Post by Catalyst2Death on 2008-08-20
Your slow internet might be due to the usb wireless reciever... can you plug it into your router with a wire and see if that helps?  That would point to the usb device's fault.  As for your other problems, I think you should try and restore the other machines that you installed (k)ubuntu on and learn ubuntu on your machine.  Once your proficient, then you can help/install it on other machines.

Ubuntu uses gnome as a desktop manager (the thing that makes windows pretty and runs stuff like the start bar)  
Kubuntu  uses KDE as a desktop manager.  Its interface is different, but the core operating system is the same (some libraries/applications are gnome/KDE dependent but lets not get ahead of ourselves)

As far as installing stuff on ubuntu goes, this is a great tutorial:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

for other problems that may crop up, you can google "name of my problem ubuntu"  and you should find the solution fairly quickly.  Otherwise searching these forums is very useful.

You mentioned shell scripts, so here is quick intro, google if you want more detail.  The shell is what lets you talk directly to the operating system. By default you will be set up with a BASH shell.  This can be accessed by going to Applications>Accessories>Terminal  on ubuntu, I'm not sure for kubuntu.  This will open up a command prompt.  You can type commands here, like:
```
$ sudo apt-get install some_package
```

the sudo command runs the command as root, which is the system administrator.  root is not something to toy with.  If you mess up in root there is not forgiveness, so only use sudo when you *absolutely* need to.

Now, with that background we can tackle shell scripts.  A shell script is a file which contains commands written in your shell's language.  It can be used to automate tasks like renaming a bunch of pictures, or copying files from one partition to another, or writing a piece of C++ code based on some user inputs.  The possibilities are endless. A lot of the scripts you will run into are scripts which automate the install process of certain things.  It is very important that you read these scripts to make sure that you aren't running malicious commands.  You should (almost) never have to run: ```
$ sudo some_script.sh
```

scripts typically come named as somename.sh or somename.py or somename.pl based on what language the script is written in.  In order to execute a file like this, you need to make it executable.  You can do this by right clicking on the file, selecting properties and under permissions, select "allow executing file as a program"  Then run the script by either double clicking on it, or running it from a terminal with:
```
$ sh /path/to/my/script/somescript.sh
```
or if your in the same directory as the script:
```
$ sh somescript.sh
```

if you really want to use the terminal, and you should, you can make the script executable by doing:
```
$ chmod +x somescript.sh
```

---

### Post by tahitiwibble on 2008-08-20
**Hyperhopper**, it's only a suggestion, but you might want to slow down a little bit and take things one step at a time.

For example, figure out what is your most pressing problem and make a post to try to sort **that** problem out first and then do the same for the second problem you want to resolve. This will make things easier for everybody.

---

### Post by tuxxy on 2008-08-20
Which wireless usb receiver do you use as this may have an effect on speed.

Search for your games or any other apps you want to install in system > admin > synaptic

Also it would be a good idea for you to read the beginner guide

[https://help.ubuntu.com/](https://help.ubuntu.com/)

---

### Post by hyperhopper on 2008-08-20
about the internet LOOOONG story, shrt version is ran every type of wire and converter , but mostly ethernet, from this comp to to router which all the other comps are plugged into, and it just doesnt work. its like windows/ubuntu doesn't know the wire is plugged in. ive tried only plugging this comp in, using other wires, everything i can think of, but still no go with ethernet or other wires

---

### Post by nynoah on 2008-08-20
Dumb question......but how many other people are now using the net at the same time?  You added a whole bunch of other computers in your house at one time.  More users more bandwidth chewed up.

---

### Post by hyperhopper on 2008-08-20
umm, only one computer is hooked up to the modem in question, and others are from a different service provider, so that cannot be the problem. also, in the guide to install anything, it says some packages will have a installer in them, what is the installer normally called or what file extension is it?

---

### Post by LowSky on 2008-08-20
For ubuntu the file extention would be .deb

And if Windows and Ubuntu cannot use the network, my money suggest that somethin is wrong with your hardware.

---

### Post by Catalyst2Death on 2008-08-20
Is it a wireless router? I get that impression from what you've said.

I'm assuming a cable modem, the cable should go into the modem, and then a straight-through ethernet cable should go from modem to the internet port of the router, next the computers should be hooked up to ports in the back.  You should set up and configure the router as per the manual.  Make sure its set to DHCP (unless your isp says otherwise)  This will allow users to connect and automatically resolve an address.  Your problems sound like they're independent of ubuntu/windows.  I would suggest fixing your internet in windows first since you're probably more familiar with it...

---

### Post by Catalyst2Death on 2008-08-20
> **hyperhopper said:**
> umm, only one computer is hooked up to the modem in question, and others are from a different service provider, so that cannot be the problem. also, in the guide to install anything, it says some packages will have a installer in them, what is the installer normally called or what file extension is it?

These are usually .run or .bin files.  You don't run into them very often, and even when you do there's usually instructions on how to install them manually (a notorious example is the proprietary ati driver package)

---

### Post by Gregmond on 2008-08-20
> **hyperhopper said:**
> umm, only one computer is hooked up to the modem in question, and others are from a different service provider, so that cannot be the problem. also, in the guide to install anything, it says some packages will have a installer in them, what is the installer normally called or what file extension is it?

Extensions are more of a windows thing. normally if it is a package that needs to be compiled there will be a readme, a make or an install. the readme is what you need. It tells you what to do. These are normally in a .tar.gz file or similar (compressed like a zip).
To make etc you need basic compilers installed and I can't remember the commands to do that off the top of my head.
Try to stick to Add/Remove programs or Synaptic where you can. Much simpler and will update better.

The wireless thing may be that wifi isn't native to Linux, its proprietary and there is a wrapper to make it work. Sometimes it works well sometimes it doesn't. Try using a cable and disabling the wireless.

you can install gnome(ubuntu) and kubuntu (kde) on the same pc and log out and select a different session. Its just a different gui.

You need to learn that no matter what politics happen, computers take time, lots of it, to make them work well. Learning can be a long slow process and you just need to say "1 at a time. Once this one is done we move to the next - AFTER checking it all works".

As for the feeling stupid, thats probably because you face multiple issues. Stop. Focus on one issue and get it solved. Move onto the next. Soon enough you will have them all solved. :)

Good luck

---

### Post by hyperhopper on 2008-08-20
this kinda deviated though from my original problem, how do i get games ex super tux, from a computer running kubuntu with internet to a computer running ubuntu without it. i could go from the comp with ubuntu  with internet (mine) but then i would have to figure out how to download it without all downloads timing out die to slowness.

---

### Post by tanman on 2008-08-20
If it helps check out some videos that I have made on my Podcast called [MSC Giz Cast]("http://www.mscgizcast.com").
The site is located at [MSC Comp Casts]("http://www.msccompcasts.com").

---

### Post by hyperhopper on 2008-08-20
didnt see anything there that could help with this situation, but i tried this:
Source Package (.tar, .tar.gz, .tgz, .tar.bz, ...)
Note: not all files with an extension named .tar, .tar.gz, and so on are archives with source code in them - they might be precompiled! If the archive is precompiled, there should be an installer or a binary executable inside it. 
 
 Sometimes all you've got is a package full of uncompiled source code. Luckily, you don't need to be a programmer to know how to compile and install a package with source code. Back in the old days, this was the only way to install software on Linux and there is a standard way of installing these files. It will not work in every case, but it will in most (if you have the right dependencies installed). To compile a package you must first extract it somewhere. This is easily done, simply right-click on the package and select Extract Here. 
Extracting a package 
Tango video icon See a screencast of package contents being extracted
 To proceed you must have the compiler tools installed. They all come with the package build-essential, available in Synaptic. When you're sure you have the compiler tools installed, you fire up the terminal and change directory to the one you've just extracted (if you're not sure how to do that see: Navigating the terminal. 
 
 When you're in the correct directory you execute a configure script: ./configure. The purpose of the configure script is usually to check for dependencies and then create the makefile. If the script fails for some reason and tells you to install certain packages, look up the names in Synaptic (Important! If you find packages in Synaptic named almost the same but with a -dev extension, remember to install those as well! They're development packages and are needed for compiling). Don't worry if it complains that there is no configure script - many packages don't come with one! Then you compile it with make and after it's been compiled you can install it. There are two ways: 
 
 Normal install: If you want to install it the normal "primitive" way, type sudo make install. To remove the temporary files you run make clean. To uninstall the program you run sudo make uninstall. These two clean-up commands don't always work, though, the programmer needs to have enabled them. 
 
 Package manager install: If you want to install it in a way that means it can be easily removed from inside the package manager, first install the package checkinstall. To install the package type sudo checkinstall. This will take slightly longer than a normal install and quite possibly you'll have to supply a description of the application yourself (and edit the other information slightly). If the need arises, this will be easy to take care of from inside the checkinstall program. 
Tango video icon See a screencast of a package being installed from source
Autopackage (.package)
The Autopackage format is supposed to be a "Linux distribution"-neutral way of installing packages. It uses its own self-contained package management tool, which is download from the Internet and installed along with the first Autopackage you install. To install an autopackage called test.package located on user Carl's desktop, first make sure it has permission to execute in your file-system, then run /home/carl/Desktop/test.package. The installer will ask you some questions, likely what your password is.
Klik package (klik:// &#8594; .cmg)
Klik is an online software repository that uses its own protocol called klik:// (similar to [http://)](http://)) to allow you to install a package from their site by clicking on a hyperlink in your web browser. To use Klik you must first install the packages binutils libstdc++5 rpm gnome-about using Synaptic and then run this command in the terminal: wget klik.atekon.de/client/install -O -|sh which downloads and installs the Klik client. Klik completely bypasses both your package manager and your file-system; everything you need to run the program is included in a .cmg-file located on your desktop after the installation is done. You simply double-click the file to start your application. To remove it again, simply delete the .cmg-file

but when i run ./configure in the terminal i get 

unable to find boost filesystem library, and before you say it i already ran in the terminal

sudo
 aptitude install libboost-filesystem-dev

and stil gets the same error


i appreciate all the help so far, thank you in advance!!!

---

### Post by Catalyst2Death on 2008-08-20
If you still have the install deb in the cache, you should be able to copy it via the network.  The files live in:

/var/cache/apt/archives/

SO, the easiest way to do this would be to use a thing like scp, which uses the ssh protocol.  If you have internet on the kubuntu computer, you can install openssh like this:

```
$ sudo apt-get install openssh-client openssh-server
```

Check here for more info:
[http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/custom-guide/s1-openssh-client-config.html](http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/custom-guide/s1-openssh-client-config.html)

scp syntax goes like this:

(server is the kubuntu machine)
```
$ scp username@server:/path/to/file/file /local/path/to/file/
```

After you get ssh set up, you can do this:

```
$ ssh username@kubuntu_ip
$ locate deb | grep tux
```
should give you a file like:
/var/cache/apt/archives/(someinfo)tux(somemoreinfo).deb
next type:

```
$ exit
$ scp username@server:/var/apt/archives/nameoftux.deb ~/
$ dpkg -i nameoftux.deb
```

if you get errors about file permissions, then do

```
$ sudo dpkg -i nameoftux.deb
```

---

### Post by hyperhopper on 2008-08-20
sorry about this, i am SOOO STUpid how do u open the terminal in kubuntu, and ill keep reading your post over, but so far it is jibberish to me, and bytheway, the computer which is getting it installed in is the ubuntu without internet

---

### Post by hyperhopper on 2008-08-20
maybe i am overreading this, is there a way i can copy the set-up version of the program from kubuntu and just paste it into the linux equivelant of program files and just launch an executable?

---

### Post by Catalyst2Death on 2008-08-20
[http://ubuntuforums.org/showthread.php?t=361944](http://ubuntuforums.org/showthread.php?t=361944)

Instruction on Kubuntu.  Once you get into the terminal you can safely assume that kubuntu=ubuntu (for the most part)

I don't know what you mean by:
> maybe i am overreading this, is there a way i can copy the set-up version of the program from kubuntu and just paste it into the linux equivelant of program files and just launch an executable?

I would like to point to you to these resources:
[https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows)
[http://users.telenet.be/mydotcom/howto/linux/migration01.htm](http://users.telenet.be/mydotcom/howto/linux/migration01.htm)

the method I outlined to copy the deb over will work best.. Copying all the files/associations would be messy.

---

### Post by hyperhopper on 2008-08-21
Thank you for those links!
what i meant was, in windows, i was very proproficient and if for some odd reason... didnt have an insstaller for a program, i could go to another computer with the program already installed, and using a flash drive, move the program and all of its dependencies to the correct folders with the correct teaks to make the program work as if i used an installer.

---

### Post by Catalyst2Death on 2008-08-21
Ok, well in principal, that is possible. In practice it would be messy and difficult. It also may not work in some applications.  Whenever possible make sure that you use  a .deb or source code or whatever and install it locally.  Don't pirate an installation.  I've tried and failed on more than one occasion, and you'll learn more about the program if you compile/install it on your own anyway.

---

### Post by hyperhopper on 2008-08-21
thasts the problem though, i cant figure out how to install properly...
thats the whole problem.....

---

### Post by hyperhopper on 2008-08-21
yay! i get how to use shell scripts completely now, but im still stuck on how to open packages adn install them.

---

### Post by meanburrito920 on 2008-08-21
Double clicking on .deb files should start the installer. Also, you keep calling yourself stupid. Dont do this. You aren't stupid. Self depriciation won't get you far in life. Everyone feels dumb at some time or another because they just 'dont understand' something. It's part of being human. So try and avoid calling yourself dumb. :-)

---

### Post by hyperhopper on 2008-08-21
i have a new question, i am trying to install wormux on the kubuntu machine, when i play i get server rejected connection message, and website said to download a package and configure it, so i extracted it and in the terminal configured it but it says could not configure, check config.log for details, but config.log is some mumbojumbo i can understand. can i have any help? thank you in advance.

---

### Post by meanburrito920 on 2008-08-21
can you post the contents of config.log (or maybe just the tail if it is super long)

Also-- new questions should go in a new thread.

---

### Post by Catalyst2Death on 2008-08-22
I wouldn't suggest trying to compile/build a package at this point.  your welcome to try, but I usually end up frustrated and go to the repositories.  I doubt that you will need to compile a library to get wormux going..

try this:

```
$ sudo apt-get build-dep wormux
```

failing that, wipe completely clean and try again:

```
$ sudo apt-get purge wormux
$ sudo apt-get install wormux
```

and if your worried about corrupted packages:

```
$ sudo apt-get clean
```

then run the above commands again NOTE: THIS WILL PURGE ALL YOUR STORED PACKAGES!

You will not be able to use the instructions I posted earlier without re-downloading the packages...

---

### Post by iansane on 2008-08-22
Don't know why the first reaction in some posts about the wireless is that it's the usb reciever.

You plainly stated that it wasn't slow on windows and Ubuntu problems with wireless drivers have been an issue for some time. They are getting the bugs worked out but still issues.

So it would be a more correct assumption that it might be an issue with ubuntu's driver for that reciever. Not that it's the recievers problem.

Don't feel stupid. We all have to start at the begining and learn.

---

