---
title: "HowTo: Ubuntu Command-Line Edition"
date: 2007-03-18
forum: Outdated Tutorials &amp; Tips
---

### Post by derjames on 2007-03-18
Hello Folks! I hope all is well with you... I have been using Ubuntu for about a year now and happy (as a hippo) using it I have really enjoyed the change. What a great job the guys from Canonical are doing (I reckon!) Ubuntu is simply great. Of my particular interest is the Ubuntu derivatives which many of them exist Ubuntu, Kubuntu, Edubuntu, XUbuntu, Ubuntu Christian Edition, Ubuntu Lite, Ubuntu Ultimate Edition, Ubuntu Satanic Edition... etc. A couple of weeks ago I was thinking about the old times: MS-DOS, DR-DOS, Wordstar, lotus123, BASIC, etc avery application running from the command line with those rather difficult key-stroke combinations. Well we still have a lot of stuff like that but incorported nicely in a GUI so basically you do not have to use it if you do not want to but it is there just in case. What would happen if all the eye-candy and any graphical environment? we would end with a computer greeting us all the time with the command prompt:


	```
jimi@jade:~$
```

(do you know '~' stands for /home/user-name) which would be enough to scare even the most proficient Windows(TM) user... After some thinking and a bit of research I decided to reinstall Ubuntu in text-mode only. So no X, no window managers, no eye candy, just text, plain text.  Then play and work with this Liinux system for a couple of weeks just to see if I could survive in this highly dependent computer world... Yes I am crazy... everybody say that... Though the Ubuntu version is completely text-based is **not** a light weight distribution. It is based on the Ubuntu Server installation which actually requires about 500 MB plus additional terminal based applications which will make your life easier (unlike Puppy or DSL which require about 50MB) 

	Before we begin some warnings for beginners (experienced users can skip this paragraph): Since no graphics are going to be available and only a bit of mouse support is to be provided; is necessary you refresh your mind about the Unix/Linux commands. If you do not know them you are going to waste your time and it is going to be a very frustrating experience... and a Disclaimer: The information provided is as is with no  guarantee that the same results will be obtained in your system. The software mentioned here  is not endorsed or supported by me I did install them on the sole purpose to improve my text-based Linux console. I will not be responsible of any use of misuse which leads to a system failure or data loss or related issue. OK (A good idea would be to test on VMware)
	
**Requirements**

Computer - PC, MAC, Sun, etc.
Processor - Any supported by Ubuntu
Memory - The more the better
Hard drive - I would say 3 GB  (The installation is about 1.5 GB)
Ubuntu Server Edition Installation CD
Broadband Internet Connection

**Procedure**
The procedure is Install Ubuntu Server -> Replace the kernel to one suitable for your system -> Modify the screen resolution -> Install ruby -> test the internet -> Install the rest of the applications.

**Detailed procedure**

**(1)** Install Ubuntu Server in the usual way and set your account (login and password)
**(2)** after installation the only thing you will see is the command prompt
**(3)** move to /etc/apt and modify sources.list (remember to use sudo) 
**(4)** uncomment all the repositories 
**(5)** Put attention to the 'Universe' section which says something like this
```
deb http://archive.ubuntu.com/ubuntu/edgy universe
```
	 write multiverse at the end of that line
	```
deb http://archive.ubuntu.com/ubuntu/edgy universe multiverse
```
**(6)** After installation I did replace the 'server' kernel with the generic-kernel (don't askme why I did this. I just did it)
**(7)** Modify the resolution of the console: go to /boot/grub and modify menu.lst (sudo required)
**(eight)** on the kernel line add this argument vga=0x0314 or vga=0x0317 the former is for super vga resolution and the latter for ultra vga resolution. This kernel argument activates the frame buffer which will give you a nicer appearance. more info about the frame buffer kernel argument can be found here

[http://enterprise.linux.com/article.pl?sid=06/05/04/1621224&tid=39&tid=89](http://enterprise.linux.com/article.pl?sid=06/05/04/1621224&tid=39&tid=89)

Unfortunately there is no support for wide screen for the frame buffer (am I right?) 
**(9)** Ruby is needed since some application will require it. 
```
sudo apt-get install ruby irb1.8
```
**(10)** Reestart the computer and you should see the change in the screen resolution
**(11)** connect the computer to the internet
**(12)** Install **lynx** - your new web browser:
```
sudo apt-get install lynx
```
**(13)** Try to access to the internet typing
```
lynx http://www.google.com
```
**(14)** The google web page should appear
**(15)** OK we have the very basic system now to install all the applications

**Installing the applications**

**(16)** Picture Viewer 	**fbida**   it can display virtually all the formats except HD photo from microsoft 
```
sudo apt-get install fbida
```
a typical usage is
```
fbi picture_name.jpg
```

**(17)** Picture converter and manipulator **imagemagick**	
```
sudo apt-get install imagemagick
```

**(eighteen)** File Manager choose from: **midnight commander** (similar to the old Norton Commander for DOS) or **vifm** which has a command structure equivalent to 'vi' (the text editor)
For Midnight commander   	
```
sudo apt-get install mc
```
for vifm			
```
sudo apt-get vifm
```

**(19)** **calcurse** ToDo list and calendar
	```
sudo apt-get install calcurse
```

**(20)** For music the **ogg** support is desirable 
for the codecs	
```
sudo apt-get install vorbis-tools	
```
and for the ogg player
```
sudo apt- get install ogg123 
```
**(21)**  **crip **as a cd ripper
```
sudo apt-get install crip
```

**(22)** RSS feeds reader: **raggle**
```
sudo apt-get install raggle
```

**(23)** Screen Saver: **cmatrix** which display the falling characteres seen in 'The Matrix' movie 
```
sudo apt-get install cmatrix
```

**(24)** Terminal Tools: **Gnu screen** which is a terminal multiplexor in other words is like having multiple desktops within a terminal screen without moving to other terminal, **vlock** a terminal lock so nobody can use the active terminal should you have to leave your computer alone (I am sure this is not needed because most of the people won't understand what the hell is going on. Only you) and **GPM** a mouse driver for terminal based applications which gives you some functionality...

```

sudo apt-get install screen
sudo apt-get install vlock
sudo apt-get install gpm

```

**(25)** Spreadsheet:**Oleo**
```
sudo apt-get install oleo
```

**(26)** Presentation: **ttp**
```
sudo apt-get install tpp
```

**(27)** Word and Document processing: **nano**, **pico**, **vi**, which are installed with the base install, **LaTex** a document processing markup language, **antiword** converts .doc files to .txt .html or .pdf files. **halibut** for document format anticonversion. **fbgs** a pdf visualisation tool. **fbgs** is installed at the same time as **fbida**
```

sudo apt-get install tetex-base tetex-extra tetex-bin
sudo apt-get install antiword
sudo apt-get install halibut

```

	
**(twenty-eigth)** Scientific calculator
	python command line	already installed type 'python'
	ruby command line	already installed type 'irb1.8'

**(29)** Programming Languages **python and ruby**

**(30)** c++ compiler: **gcc**
```
sudo apt-get install build-essential
```
	
**(31)** Games: **nethack** 
```
sudo apt-get install nethack-console
```

**(32)** Videoplayer: **mplayer**. There is a youtube application but I haven't installed yet  '**youtube-dl**'
```
sudo apt-get install mplayer-nogui
```
	
**(33)** ** SendEmail** Email client
```
sudo apt-get install sendemail
```

**(34)** A virtual mahine: **qemu** to install Freedos or the MSDOS or other Linuxes or Windows 
```
sudo apt-get install qemu
```

**(35)** Print 
	I moved to a place where I don't have a printer so I am not including this in the guide

**(36) ** And the last step: update/upgrade your system

```
sudo apt-get update
```
then
```
sudo apt-get upgrade
```

This installation will give you a pretty useful system. You can do all the basic stuff:  rip CD's listen to music, watch videos, subscribe to RSS feeds, send email, web browsing, 
document creation, calculators, spreadsheet... and a virtual machine... 

**Typical usage**
The first thing you will see after booting up is the command prompt some very basic commands are 

**cd** change directory
**cp** copy files/directories
**mkdir** create a new directory
**clear** will clean your screen from 'text accumulation'
**df** for checking your hard drives capacity
**top** show the active processes running in the system

alt+Fkey[1-6] switch between 6 different terminals

to create a terminal within a terminal type 
```
screen
```

then you can create more terminal by pressing 
```
ctrl+a+c
```
and to switch between those terminal  
```
ctrl+a+[1-9]
```





The very first week is very strange but then you get used to it. I think now I know hundred of commands, switchs and parameters. A good way to learn a lot more about linux... finally I would love to see a Linux text-based Macbook Pro... So this is geekiest thing I've done so far. Hope you enjoy it as much as I am enyoing it now...

---

### Post by anatole on 2007-03-19
i don't get it, how do you view pictures and play videos without X ? otherwise, interesting guide. (you may want to have a look on mpd for music playback, it has  some commandline clients, ncmpc is so good that i don't need anything else even with X)

---

### Post by Jonne on 2007-03-19
Links is a way better browser than Lynx, I'd recommend that instead.

I do have a virtual machine running Ubuntu server, and I kinda liked the challenge. I use it as a development server.

---

### Post by rukuartic on 2007-03-19
A few notes on screen:

Ctrl+a+n and Ctrl+a+p send you back and forth through your screens.
Ctrl+a+d "minimizes" your screen. The cool thing is you can log out and return to your applications by typing "screen -r" in the terminal.
Ctrl+a+[ lets you scroll around and select text. Hit enter to start, move your mouse, and hit enter again.
Ctrl+a+] pastes the text you selected above.

w3m is an amazing web browser like Lynx, I like it.
mpg123 is great for MP3's
moc (music on console) is a cool media player
irssi is perfect for IRC
wget is for downloading files interactively

and gimp-command-line-edition is an awesome Photoshop alternative.

Thanks for the links! Lots of interesting things here.

---

### Post by superatrain on 2007-03-20
Very nice tutorial: nice summery of all the applications out there.

As for viewing pictures and movies in the console, it uses framebuffer to accomplish this feat. Its an old trick, and works somewhat similarly to how the console background and Ubuntu splash screen work. It works with quite a few applications, including the web browser "links2".

If you want a basic mouse, gpm will do that for you. That, coupled with framebuffer and links, gives you a full functional web browser, with images, without X.

The only problem with this tutorial is: Why do you have to say how to install every single application! just say: apt-get install <packagename>, and list the packages and what they do.


I was using a system like this for a while, but I recently caved in and decided to splurge for Xubuntu. My computer is a P2 300Mhz laptop with only 160Mb of ram, so don't worry if your computer is not all that good.

My favorite applications:
Screen - amazing virtual terminal system, make, show, and hide VTs. Also has support for copy/paste/scrolling/searching, much like vi or man. A great thing to do with it is split your screen in half. :D

mplayer: does everything, like vlc, but for console. Links2 - as mentioned above, like lynx, but with graphics support!

cmatrix - havent tried it yet, sounds awesome though :P

Note: You can turn on X from a normal Ubuntu installation temporarily, if you want to try running this. Just remove xdm/gdm (dont remember which) from the startup runlevels.

---

### Post by rolando2424 on 2007-03-20
Very nice tutorial :D

Just a suggestion, if you want msn and others like it support, just install centericq :D

---

### Post by anatole on 2007-03-20
just checked the framebuffer & mplayer combo, pretty sick:)  i just cannot get a fullscreen video playback - it displays the video in its original size in the center and everything else is black... how could i make it display properly?

---

### Post by FrozenFOXX on 2007-03-20
I'd imagine for any serious command-line questions that may be difficult to find answers to don't forget the Gentoo forums as we tend to revel in the command line.


Very nice how-to on setting up Ubuntu from the command line.  While not completely essential I'd imagine you'd probably want to install OpenSSH and the server ssd.  That way the person interested in it doesn't necessarily have to leave a nice GUI on another system to get used to using that system in command line, but it might be overkill.

---

### Post by superatrain on 2007-03-20
anatole, same problem, not on ubuntu but on gentoo though :P If you find a solution, pm me. It also exists in X for me.

rukuartic: Thanks SOO much for pointing out moc. It is my new favorite media player, even for X enabled machines. I think I will end up donating to the project eventualy... Its exactly what I have been looking for for years now.

---

### Post by fakie_flip on 2007-04-22
For ripping cds, you should use cdparanoia and oggenc to encode what you ripped.

---

### Post by bullgr on 2007-05-23
awesome tutorial...
i am crazy too and i was searching to do somelike that.
and a question: is there any voip prog for the command line?

---

### Post by xavier_r on 2007-06-24
OMG!!!!

I thought maybe I was only doing this... ;)

Great job dude... it feels great to know people still love CLI or TUI whatever you can call it :)

I came across while searching about command line because I've been trying to do the same thing... aka BUILD A COMMAND LINE UBUNTU LINUX. I mostly chose curses based applications... for my **init 3** system ;)

Here's my list of software (after trying out many others):

	Music Player - orpheus
	Web Browser - w3m / links2 (for JavaScript support)
	Sound recorder - rec
	Sound player - play
	Editor - nano
        Viewing Microsoft Word Documents - catdoc
        Spreadsheet - sc / slsc
        Presentation Software - tpp

        cadubi - drawing ASCII images
        calcurse - calendar application
        abook - address book
        elmo - email client
        bittornado - torrent downloader
        cmatrix - screensaver (wow, you thought of the same thing) :D
        lockvc - screensaver with console lock
        centericq - messaging client (MSN, IRC, Yahoo, etc.)
        saidar  - view system statistics
        zgv - Image Viewer


        File Managers:
        vfu, mc, clex, lfm, etc.

Plus I guess there are lots of useful software out there which can run on CLI

Hey dude if you have the time, message me.
It would be great to build a CLI system catered to modern needs.

xavier

---

### Post by chiefbutz on 2007-06-27
I don't know if it has been mentioned (i didn't have the attention span to read all of the comments) but for AIM use bsflite, it works well.

---

### Post by rayburn on 2007-06-27
Great thread and some very useful info. I have now installed a CL Edition of Ubuntu and am very impressed by it's speed and simplicity. This post is written using it!
One question, are there any other address book programs out there for the console, as I find abook to not quite meet my needs?

Many thanks.

---

### Post by rayburn on 2007-06-27
[http://commandline.org.uk/2005/links-directory-programs-and-sites/](http://commandline.org.uk/2005/links-directory-programs-and-sites/)

Just found the above link which lists some apps and descriptions, no address books though....

---

### Post by andrew.46 on 2007-06-28
Hi,

 I enjoyed reading your absolutely fascinating post. Good on you for trying something different! You might be interested in utilising the newsreader slrn for which I have written quite a detailed guide:

[http://ubuntuforums.org/showthread.php?t=475246&highlight=howto+slrn](http://ubuntuforums.org/showthread.php?t=475246&highlight=howto+slrn)

 I guess you would have to modify all references to the Desktop though :-) I am working on a similar guide to using the MUA mutt. This would fit right in with your concept of a command line ubuntu.

       All the best,

            Andrew

---

### Post by bigie on 2007-07-07
nice tutorial !! thank's...

---

### Post by Nythain on 2007-07-07
yay for command line... i stumbled upon most of those apps in the development of my command line desktop... the essentials i cant live without, even with a gui are mc, centericq, rtorrent, mpd with ncmpc and top... i havent messed around much with screen since i still run a gui desktop (god bless xorg and fluxbox) but good to know about in case i ever do go completely command line... overall great little experiment/tutorial for those who fear the command line, and the additions made by everyone else just prove the extent of options out there, even in a command line environment

---

### Post by andrew.46 on 2007-07-07
Hi,

 Thanks for this:

> **bigie said:**
> nice tutorial !! thank's...

 I am working on another that is still a little unpolished which deals with the email client mutt:

[http://people.aapt.net.au/~adjlstrong/mutt.html](http://people.aapt.net.au/~adjlstrong/mutt.html)

                  Andrew

---

### Post by bigie on 2007-07-08
nice howto, ummm what can I use for read chm file on text-based?:)

---

### Post by maybeway36 on 2007-07-20
You can also do a command-line installation from the Ubuntu Alternate CD. I used this to install Xubuntu without needing to burn another disc.
```
sudo aptitude install xubuntu-desktop
```

---

### Post by Yellow Onion on 2007-08-02
Ive used finch the CLI version of pidgin but don't know how to install it by its self but it is great
theres also
axel  ( download accelerator which uses multiple connections to speed up downloads)
bsdgames (hole bunch of old school games)
bsdgames-nonfree (a game called rogue)

---

### Post by goonies on 2007-08-03
You guys can also just hit Ctrl + Alt + F1 in your normal Ubuntu installations to get away from X.

To go back to X just hit Ctrl + Alt + F7.

---

### Post by superatrain on 2007-10-12
goonies: The problem with that is, X is still running and eating HUGE ammounts of ram, and also, it will take just as long to boot. With this type of system with xorg disabled, you can just startx only when you really need to use X.

Until I got my new laptop, I was running an ubuntu system like this on a P2 - 300MHz. It was insanely fast, I beat Core2Duo laptops, I would boot faster than them, and I could open my web browser way faster than them (though there is dillo, an X based browser that is really light. also, links2 works with x as well. neither support javascript or css, and will look somewhat wierd on messy sites.)

yellow onion: How much difference does axel make compared to wget or any normal solution? and does it support resuming downloads? setting the Referer address?

---

### Post by battletux on 2007-10-14
I was wondering if there are any image viewers that would work over an ssh connection?

Most of the other things I have tried in this article work great, it's just that I would want a picture viewer for remote use as well.


Other than that, great article!

---

### Post by mjewell on 2008-01-21
This is a great tutorial!  Very fun.  I'm a cli novice but have been curious about learning more since reading Neal Stephenson's In the Beginning Was the Command Line years ago.  In my job, I need to handle a lot of heavily formatted word processing documents and spreadsheets so migrating to OOo was a big deal.  This tutorial gives me hope that I'll some day be able to dump the GUI from my machine completely on those days I'm not in the mood to click-and-drag.  Thank you!

---

### Post by pelikan555 on 2008-02-02
Hi,
Just found this HowTo. Thanks, it's very informative - I am attempting to get a purely CL Gutsy on my Dell Inspiron 1300 laptop. But when I try to get the framebuffer working by adding that 'vga=...' command to the kernel line in the Grub menu, I get a blank screen when I try to boot up the CLI install of Ubuntu, and have to go back into my normal Ubuntu to restore it. What could be wrong?

---

### Post by Jaramia on 2008-02-13
Hello you crazy crazy hackers,
I started something likethis myself, and I'm hooked. The speed, simplicity, and change in mindset are all great.

Just wanted to say thanks for all the usefull comments throughout this thread.

---

### Post by ajfisherman on 2008-08-02
well 6 moths later...
Im trying this with hardy on my Dell Latitude CP
144mhz 96mb ram
see how fast it'll do aginst those vista machines
also i think wine could be used from command line to run some dos apps

---

