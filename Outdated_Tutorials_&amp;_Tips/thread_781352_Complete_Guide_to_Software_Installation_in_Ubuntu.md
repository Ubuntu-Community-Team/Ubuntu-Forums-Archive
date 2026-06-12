---
title: "Complete Guide to Software Installation in Ubuntu"
date: 2008-05-04
forum: Outdated Tutorials &amp; Tips
---

### Post by forestpixie on 2008-05-04
[COLOR="Blue"]**This thread is a copy of starcraft.man's original very exhaustive Guide. All thanks should go to him as all I have done is moved it and updated a few things to get it into the new Absolute Beginners Forum in response to Matthews [request]("http://ubuntuforums.org/showthread.php?t=765393"). If there is anything that I've missed or that could be changed let me know and I'll do my best with it. [This]("http://ubuntuforums.org/showthread.php?t=500020") is the original thread created by starcraft.man. **[/COLOR]

** _Complete Guide to Installation in Ubuntu_**
[B]_[SIZE="4"]Index[/SIZE]_
[SIZE="4"]0) Introduction
1) Basics
2) Installing with CLI[/SIZE]
[SIZE="3"]2a) Graphical Editors and the Sources List
2b) CLI Editors and the Sources List
2c) Authentication Keys
2d) Updating
2e) Installing Software
2f) Advanced Package Management[/SIZE]
[SIZE="4"]3) Installing with GUI[/SIZE]
[SIZE="3"]3a) GUI and Sources List
3b) Skip!
3c) Authentication Keys
3d) Updating
3e) Installing Software[/SIZE]
[SIZE="4"]4) Lexicon[/SIZE]
[SIZE="3"]4a) Lexicon of Terms[/SIZE]
[SIZE="4"]5) Extra sections[/SIZE]
[SIZE="3"]5a) Add/Remove GUI
5b) Differences Across Versions
5c) Extra Resources[/SIZE][/B]

[SIZE="4"]0) Introduction[/SIZE]

Just a prefacing note before getting to the actual introduction. There is a lexicon that contains all the words that might be unknown to a beginner, it is located in section 4 as indicated by the index. If any are missing I will add them later (feel free to PM me with any you think require defining and I will be sure to try and get them added). Using the index is simple, every section is titled exactly the same as it is in the index. Use your browser's search feature and you'll be able to jump to it, if thats what you want. This is a limitation of the forum version of this document, I will be producing a wiki version later that will be much more elegantly presented (this admittedly is a bit rough). It is also likely that any changes will probably just be made to the wiki, this version is being locked.

Now, I know almost all of you know how to install with Windows, usually you just double click a file (ending in an .exe, like setup.exe or install.exe) and there is the good old Windows installer to guide you through step by step. Easy right? Well things are different in Ubuntu, really Linux as a whole is different. This stems from the differences in their foundations and how they were built up over time. That doesn't mean it's harder, just different. In fact, I bet once you understand it all you will come to see how easy it all really is, and how it has its own merits over the method used by Windows.

Now that I got that out of the way, I have to issue a warning right off the bat. If your looking for a quick solution to a specific problem look elsewhere. My aim with this guide is to actually teach and explain to you how to install things, not point you to one time CLI commands/GUI guides (lexicon). I admit (I feel a bit bad now), I have done the latter in the past and I have come to realize rather quickly that it simply doesn't work. Understanding is the key to using your operating system effectively. Without that, your just repeating something someone else said without grasping what your doing. You don't want that do you? You want to be in control, to know whats going on and know that you can deal with things that can happen.

So lets get right to it, ok? My guide is split into multiple parts (indexed at the beginning). You can search across the guide at any time for a title and you will get right to that section. I advise reading it front to back, I start with basics and keep adding progressively. This guide requires NO pre-existing knowledge of Ubuntu/Linux, I have taken care to explain everything (a few minor omissions). With all that said, I will just close by saying all I ask is for your patience and I promise that by the end of reading this long document you should understand everything you need to. Now on with the learning.

[SIZE="4"]1) Basics[/SIZE]

Ok, so lets start with the basics, please bear with me it may seem complicated but once I get further on it will be clear. Windows installs all it's programs with executable files (aptly named .exe files). These of course use the Windows installer and through that display numerous screens that let you pick options and features and even where to install the bulk of the files. Once all options are selected, it handles all the processes for installing and tells you when it is done. Additionally, every program in Windows has its own update manager to check for updates on the companies/author's servers. The only really integrated update tool is the one for Windows Update which of course only updates Microsoft products. The OS at its core is very segregated and disjoint, each application only interacts with each other in so far as it needs to (usually only with Windows) and not anything more.

Linux is very different. It employs a central community driven software system with an open and sharing philosophy. The first and most important component of this system is named the Software Repositories. Each Linux distribution (lexicon) maintains its own software repositories, they are usually paid for by the companies backing and supporting the distribution. In the case of Ubuntu, Canonical would be the company that runs and maintains the majority of our main repositories.

So what exactly do we use the repositories for? Consider them to be a large network of servers. They store huge volumes of information, ready to serve to any Ubuntu user. The information on them is mostly broken down into packages (lexicon) which can be easily manipulated with a few select commands (or clicks in a GUI) to install any program you like. A package manager is used to issue all commands with regard to packages, in Ubuntu it is called Aptitude, more on that later.

You may be wondering, how does the computer know which servers to search for updates/programs? The answer is, it has a simple system that tells it which servers to look at, the system is called the sources list. The sources list is a text file stored on your computer, in it urls are stored which point to the servers your package manager Aptitude should look at when trying to find/install/update programs. It is also used constantly to check for updates, Aptitude checks the versions of your installed programs/packages (the one's on your computer) against the versions stored on the repositories. When a new version is uploaded, it alerts you and you can install them.

Now, there is one last important element, keys. Keys are used on many repositories, their main purpose is to ensure security and authentication (so that you know your downloading from a trusted repository). This is important, it ensures the integrity of the repositories isn't compromised by some third party trying to spoof the servers or worse. By default, the main repositories in your computer already have Ubuntu's main key, if however you add extra repositories (something I'll explain later, it is common to do) you will likely have to download new keys to access it.

Ok, to wrap this up I'm going to summarize and make an analogy that Windows users shall understand. Think of the entire system as Windows (or Microsoft) update (really only analog that's remotely similar). Microsoft hosts hundreds of thousands of updates in a network of servers that any Windows user can access, this of course is the same as the repositories. When you scan your computer, the package manager (i.e. Windows Update tool/application) scans your computer to check what is installed and compares that to versions it has in its own servers, as well as new programs your computer is eligible for (same as Aptitude). Then the updates you can install are displayed and you can select them, same principle as packages. There isn't really an analog though for sources list and the keys, Windows Update uses a dedicated site (or in Vista a built in application) to both authenticate you (keys) and know exactly where to find the programs (sources list).

So there you go, that was my brief overview of the ecological network it takes to install things in Ubuntu. Not so hard eh? Now for the good stuff, I will explain how it all works and how you actually install things.

---

### Post by forestpixie on 2008-05-04
**Re: Complete Guide to Installation in Ubuntu**             
                                                                **[SIZE=4]2) Installing with CLI[/SIZE]**

Special note: Kubuntu users, go straight to 5b) Differences Across Versions and understand the differences (or keep them handy until brought up). I wrote this guide for Ubuntu and things are slightly different for you guys. Most if not all of this guide can still apply to you though.

So, first we will start with the command line means of installing. It will be easy to grasp the GUI method after I explain this, I will be including all the theory here and the GUI explanation will really just be equating things so you understand them from CLI. I do advise understanding both methods, just like knowing more languages lets you visit more countries on your own, knowing more methods of installing is always better.

First, we need the terminal (lexicon), it can be gotten to several ways. The first and most obvious is via the Applications Menu, specifically Applications > Accessories > Terminal. The second way is to use the run application box. You can get to this with Alt + F2. This handy keyboard shortcut is useful, the more you use applications the more use you will find out of it. it will let you get to them fast, to run any application all you need know is its terminal command. This is usually its name, for example, the gnome terminal, is "gnome-terminal". Usually, it is the name of the main package installed for the program. It has other options you can use,, but for our purposes it will suffice to simply know how to open the terminal with it.

[IMG]http://i22.photobucket.com/albums/b324/FFManiac1/CLI1edit.png[/IMG]

Note: My pictures/screen shots from here on will likely look different than what you have on your system, I'm using a dark custom theme. Any differences are merely cosmetic.

This is what you should see in Ubuntu by default, it is the GNOME Terminal:

[IMG]http://i22.photobucket.com/albums/b324/FFManiac1/TerminalEDIT.png[/IMG]

Now, you have a terminal open. There are many different variants with different looks, all are inherently the same though (they differ in their look but get you to the same CLI). The one thing you should see displayed is:

username @ hostmachine :~$

This is of course simple. Username will be whatever user you are logged in as (for example, starcraft), and @ hostmachine is telling you which machine you are logged into (you can remotely log into other machines, you need not be concerned with the host machine part, it is for advanced uses). By default your hostname should be Ubuntu unless you changed it during install. The last bit of this is :~$. The : simply separates your name and machine from the directory your working in. ~$ is a place holder, until you change directories. This concept may be a bit difficult, think of a directory as the folder your working in. When your in your Explorer in Windows you double click a folder and you go in it, each folder your in before you click the next is the directory your working in, except in the terminal there isn't any graphical indicator which folder your in (i.e. the top of the explorer tells you where you are). Thus, this line after your name serves as your indicator. For more information see Linux Command, specifically lessons [1]("http://www.linuxcommand.org/lts0010.php"), [2]("http://www.linuxcommand.org/lts0020.php") and [3]("http://www.linuxcommand.org/lts0030.php"). I strongly urge you to read these 3 lessons, they will make everything that comes after this much easier. [4]("http://www.linuxcommand.org/lts0040.php") and [5]("http://www.linuxcommand.org/lts0050.php") are less important, read them at your discretion they can only help you in your understanding of CLI.

Now that we got that out of the way. Lets understand sudo. Sudo stands for superuser do. This is a security system in Ubuntu, it allows for a limited user (your default account) to do administrative tasks without logging in as administrator (in Ubuntu the administrator account is named root or root user). You have to tack on this command before all others (consider it like a prefix to the entire command) to allow a command root access. You normally need this when you want to do updates, install programs, or modify any system components that are important. For a complete description of sudo please read 
[this]("https://help.ubuntu.com/community/RootSudo") it may seem a bit complicated but you will understand as you use it more. 

One warning, when it asks for your password the terminal will not give any visual feedback (i.e. You will not see ****s for every character of the password you type). This is normal, and is nothing to be alarmed about, your keyboard isn't broken just continue inputting your password and push enter.

To sum up, sudo should only be used when you have to (it is a security feature, staying constantly logged in as root or sudo is insecure) and must be used properly as follows (any time you see these boxes (the ones after this note) with commands in them, they are meant as example of what should be used in the terminal):


```
sudo <command> 
```(note no <> around the actual command, I use that only for emphasis of the fact that command is just a placeholder for any command you know)

or for example:


```
sudo aptitude update 
```(a common command, more on it later)

Now, on to the next step, looking at your sources list. One of the key features of Linux is rather than using a registry to store all configurations of programs, it employs text files that can be edited manually or with programs. You can view it (the sources list) graphically with a word processor called gedit (It's a basic program just designed for simple edits to text files like the sources list) or you can use the terminal editors (They have no graphical component, and are entirely text based). I will show and explain both methods, though it is usually easier to use gedit.

[SIZE=4]2a) Graphical Editors and the Sources List[/SIZE]

Issue this command to the terminal (by that I just mean type it in (or copy while your learning) and push enter):


```
gksudo gedit /etc/apt/sources.list 
```IMPORTANT: You will be entering a tonne of commands, please note that in Linux it _DOES matter a lot if it is capital or not_ (i.e. if you issue a command with "aPtITuDe" or even "Aptitude" instead of "aptitude", you will get nothing. The first/second are gibberish (to the terminal), the third is a command.). Be exact, and if you get an error check for typos. The same rule about capitalization applies to filenames and paths (lexicon), be precise.

For a breakdown of this command, understand that gksudo stands for graphical sudo. It is intended to be used when opening graphical applications (such as gedit), you can use sudo instead but there are some graphical apps that simply don't open with sudo correctly, I advise you to try your best in remembering which is which. More on gksudo 
[here]("http://www.psychocats.net/ubuntu/graphicalsudo"). Next is gedit, this is the application I (you) want to use (and by prefixing it with gksudo I am empowering it to edit files that only the root user should be able to). Lastly, is /etc/apt/sources.list, this is the path (lexicon) to the file I am wanting to edit. All commands follow this basic scheme, from most general (giving root power/the application) to most specific (path of the file).

Now, you should see this (this being gedit looking at the sources list):

[IMG]http://i22.photobucket.com/albums/b324/FFManiac1/SourcesList-1.png[/IMG]

This is gedit (full name is gnome editor). You'll use it often when editing text configuration files like the sources list. It is a stripped down word processor, there are only a few important features you should know about. The save button should only be pressed when you are sure the changes you've made are what you want, it will overwrite the file you opened. The open and new buttons are like all others of their kind, they open and make a new document respectively. One note on this is that it will usually (when its an important file like the xorg) make a dated back up upon saving, so your old version is preserved. _Don't rely on this_, when you need to back up (whenever you like, usually before serious changes to important files) please consult [Linux Command lesson 5]("http://www.linuxcommand.org/lts0050.php"), simply use the cp command to copy the file and make a new copy with whatever name you like.

Other features are constant, Ctrl + C V or X get you copy paste and cut respectively. Ctrl + Z and Y get you undo and redo respectively. One other good feature is line numbers and the highlight feature, this makes it easier to figure things out. Go Edit > Preferences and check “Display Line Numbers” and “Highlight Current Line”. The former will assign each separate line of any open file with numbers (this is especially useful if an error is returned that says “error at line 35 of sources.list” or when conferring with people about your configuration file. The latter option highlights the current line your working on, I like both.

Now, on to understanding the sources file. Here is mine (only a partial excerpt, my actual list is very long) for example (your's will of course vary):

     ```
[COLOR=Red]# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Beta i386 (20080319)]/ hardy main restricted[/COLOR]
[COLOR=Blue]# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.[/COLOR]

[COLOR=Red]deb http://archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy main restricted[/COLOR]

[COLOR=Blue]## Major bug fix updates produced after the final release of the
## distribution.[/COLOR]
[COLOR=Red]deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted[/COLOR]

[COLOR=Blue]## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.[/COLOR]
[COLOR=Red]deb http://archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy universe
deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates universe[/COLOR]

[COLOR=Blue]## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.[/COLOR]
[COLOR=Red]deb http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse[/COLOR]

```Now first thing to understand, all the lines prefaced with ## in front are simply text lines for you the end user. They are to explain at the beginning and to identify each repository. I have highlighted in red exemplar repository urls and in blue are the text and identification.

Now, comes the technical stuff. The first thing you should understand is commenting. This is a universal term that applies to almost all configuration files like the sources list. It refers to the act of putting a # in front of a line in the text file. This tells any and all programs that read this configuration file not to “read” or otherwise use the line in any operation, mostly these are comments either made by you the user or the original creator of the file to help you. They also identify the repositories. One or two #s makes no difference, they are equally unused. It's mostly just cosmetic.

Now, this commenting system doesn't just apply to text, it also applies to the software repositories themselves. Here is an example also from my sources list:

```
[COLOR=YellowGreen]_deb_ http://archive.canonical.com/ubuntu hardy partner[/COLOR]
[COLOR=DarkOrange]# _deb-src_ http://archive.canonical.com/ubuntu hardy partner[/COLOR]
```In green you see a software repository, it has no comment in front so you know it will be used when installing and updating or by any other program using this file. The Orange though has the comment in front, it will be ignored. Another thing I would like to note here, notice that both lines point to the same url, there is a difference though and I have underlined it. The first line will merely download the package or update. The second line will retrieve for you the source code (lexicon) it will download it to a particular folder in your system (the location escapes me at this moment).

So, that is how the sources file works. Aptitude (most common application using it) will read it (all the uncommented urls) when it tries to find programs/install them/update them. It isn't complicated or mystical, and it does get the job done very well. Now then, what if you want to add sources to your list? Well, we can do that too.

To get the most out of Ubuntu you have to enable quite a few repositories, universe and multiverse for instance contain extra programs not in the main trunk but which are useful. They are in these sections for the express reason that they aren't directly supported by Canonical (Ubuntu's backing company). 

You can add other sources to your sources.list - one such is from Medibuntu - this provides a way of distributing software which cannot be included in Ubuntu. [This]("https://help.ubuntu.com/community/Medibuntu") page gives a method of enabling these software sources.

This repository contains codecs and other restricted packages, they usually aren't free programs like your other ones. The reason it says it may contain illegal packages is because of the disputed legality of using codecs like the MP3 one without having paid for the right to use the “patented” codec. This should never worry you though, no one will hunt you down for using less than legitimate codecs its far less than active piracy like downloading software and music without paying. Consider it fair use (like ripping DVDs from their original disk to store a perfect digital archive for life).

Anyway, when you find sites with repositories listed that can be added to your own (like the Link) all you need do is open the sources list and copy the lines to the bottom of your list (there are other steps, this is the only one needed in the software sources list though). Always make sure your not (unless you really want it) downloading deb-src (the source code). If you don't plan on using it, it simply eats up space on your hard drive. Be careful when adding extra repositories, always make sure it's for the distribution (i.e. Ubuntu) and version (i.e. Hardy, Gutsy, Feisty ...) of your system, it is not advisable to mix and match.

Now, I have covered the basics, a technical break down of what each line of this sources list actually does is required. Here is an exemplar two lines from different parts of my sources list.

```
# deb-src [http://us]("http://%3cfont%20color=%22blue%22%3eus%3c/font%3E").archive.ubuntu.com/ubuntu/ feisty main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse universe
# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Beta i386 (20070322.1)]/ feisty main restricted 
```First up, see what I highlighted in blue. That is the country code of the repository, there are many mirrors for Canonical's servers and its more than likely your country has one too. The code could equally be (in place of us) [COLOR=Red]ca[/COLOR] and then it would go to the Canadian mirror. All mirrors store the same data, the only difference is where they are stored. The second url has no country code this one will simply hit the primary main site for its updates, this is fine.

Next, notice what I highlighted in green, notice how there is a space between each and it isn't part of the actual url, weird eh? That's because these don't make part of any standard url like you understand (the web browser kind). The truth is while I've been calling them urls (Uniform Resource Locators) they are really uri's (Uniform Resource Identifier). The difference is minimal for you, it means a lot to aptitude though and is reflected in the formatting. Basically the first chunk of the URI directs it to the location to find the repository. After that, the spaces refer to specific sections within that repository that it should look to get packages/indexes/information from. Take my first line for example, it will go to the repository indicated and then look up the feisty section (that is the distribution I am using) and then further look in the sections of main and restricted. My second line is a bit longer but the same, it will go to the repository indicated in orange and then to the feisty-update section, in there it will search for main restricted universe and multiverse packages. It's a very clean and efficient system of doing things. I invite you if you like to open a tab or window of Firefox and paste the url (orange one) in your location bar and push enter, you can then browse around the sections as you like. It isn't important to understand how the actual repository is sorted (it is a bit more complicated then I am letting on), merely that each of the terms is a section.

Now the last line of my example. Notice it is formed very distinctly from the rest (yours may vary), it is the line that indicates to aptitude you can install programs from the CD. This line when uncommented will tell aptitude to check for packages on the CD you installed with (it will prompt you to insert the CD every time you try to install something). This is somewhat limited for the average user, the basic CD doesn't contain many packages at all for you to install from except whats already installed. Some users get a hold of the DVD containing all of Ubuntu's repositories and thus add those, they then can install a much wider range of applications from that without a net connection. This has of course a severe limitation, the versions of the programs on the media (CD or DVD) is frozen, it will always be that same version and without net access at some point you will never get updates and newer ones. Most users can simply comment this line out, you won't have much use for it and the online versions will always be more up to date.

A full explanation of what the sections of these repositories hold is given in the GUI section, wait until you get there to understand what they all do. That is all for this section.

[SIZE=4]2b) CLI Editors and the Sources List[/SIZE]

Sometimes, you don't have the GUI (i.e. Your not logged in with a graphical display manager (lexicon)) and you want to edit something. This of course has been solved for a long time (remember computing began without GUIs), there are text editors that are CLI based and don't rely on any graphics. They are more limited but still useful. I will just give you a quick guide to this, I won't repeat all the explanation as above. All the same things applying to this sources list, because your editing the same file. The only difference is how you edit it.

This command in the terminal will get you the Nano editor (there are others, explore at your own discretion):


```
sudo nano /etc/apt/sources.list 
```Notice that this time I didn't use gksudo, thats because nano isn't a graphical application it works inside the terminal. Nano of course is simply the name of the CLI editor, and it is followed of course by the path to the file I want to edit.

Here is a pic of what the Nano editor looks like. 
[IMG]http://i22.photobucket.com/albums/b324/FFManiac1/NANOedit.png[/IMG]

Every time you see ^ it simply means push ctrl and then the key on the keyboard. ^G will get you the help menu and reexplain all the keys and functions available. ^X will exit the editor, it will prompt you to save if you made any changes. ^O is the write out command, it will let you save your changes to the same file (the path is displayed, by default it is the same as the one you opened) or to another place. One of the serious limitations of Nano is that copy and paste don't work the same, you can only copy one line at a time with ^K and paste it with ^U. Navigate around with the 4 arrow keys, and remember it will cut whatever line you are currently on. Oh and ^V and ^Y are page down and page up respectively.

Thats it. There isn't anything special to nano, its mostly for when you can't get to gedit and need to make changes (or if you want to quickly insert a single line). That wraps up editing the sources list, any extra information will be added to the end.

N.B. Kubuntu users, you do NOT have gedit or gksudo. Your respective programs are kate (editor) and kdesu (gksudo alternative in Kubuntu). A word of warning, you MUST launch kate to edit text files graphically with kdesu (you will get an error message if you fail to do so). 

Xubuntu users, you can replace gedit with mousepad, gksudo will work for you though.

All Ubuntu derivations though come with nano, that is a standard editor that you can always use.

[SIZE=4]2c) Authentication Keys[/SIZE]

So, now you added the repositories and your wondering how do I get the keys to access them. This is much less complicated and lengthy.

Firstly, the hardest bit is usually finding the key, it will usually be on the site near the repository. In the case of our previous example with the medibuntu repository the key (and command to import it) is provided on the web page 

[U]This example is from the original thread and has not been changed as the explanation which follows it is still good. The command should not be used and can be replaced by using those given on the Medibuntu link.

[/U]```
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - 
```Now, a little explanation of the command is in order. Wget is the command for the terminal to download anything from any site (it is the CLI equivalent of right clicking a link and going save link as...). It is useful for downloading keys and other things when you don't want to open a browser and do so. -q means quiet mode, that simply means it won't give you any output from wget, it isn't really needed just means it won't clutter the terminal with lines. I would like to add that -q is a modifier (lexicon) to wget. The url follows, this can be interchanged with any other url (in this instance its the gpg (lexicon) key for the Medibuntu respository). This -O- | (the | is really just to separate the commands one from the other) is used to link the two commands together, the first half (before it) downloads the key with and the latter half command adds the key to the database so that it is available for the repository of choice. Sudo of course is the same sudo as discussed before. Apt-key is the command for modifying and changing keys, add of course is to tell it to add and then last – simply is a place holder for the key that was previously downloaded.

The site will not always provide the command with the key (this site was targeted at new Ubuntu users so it did). A more generic example _used to be_ the Virtual Box site (it is a very good and free Virtual Machine solution, for those of you that know what that is, not important what it does just as an example).

>  I[COLOR=Blue]t previously needed to be added into the sources list and having the key added, these were the commands needed to complete the addition of virtualbox prior to installing it. Again I have left the information as the syntax for adding similar keys would be similar to this. 

In fact now virtualbox can be got from the repos using either apt-get, aptitude or synaptic - this results in an open source version being installed. It is also available from the virtual box [site]("http://www.virtualbox.org/wiki/Downloads") as a .deb which can be installed.

 To install from the terminal using aptitude

```
sudo aptitude install virtulabox-ose
```To install the non open source alternative go to the vbox website and follow the links to the binaries platform. [/COLOR]   
 
     These were the original commands needed to accomplish the task at hand - 

>  Debian-based Linux distributions: Add one of the following lines according to your distribution to your /etc/apt/sources.list: 

     ```
deb http://www.virtualbox.org/debian feisty non-free
deb http://www.virtualbox.org/debian edgy non-free
deb http://www.virtualbox.org/debian dapper non-free
deb http://www.virtualbox.org/debian etch non-free
deb http://www.virtualbox.org/debian sarge non-free
deb http://www.virtualbox.org/debian xandros4.0-xn non-free 
```The innotek public key for apt-secure can be downloaded here. You can add this key with 

```
apt-key add innotek.asc 
```They of course provide repositories for feisty, edgy and dapper all versions of Ubuntu, as well as other distributions. Underneath they gave you the public key as well. They didn't really format it perfectly for you though. Pay attention and notice that they did link to the full url though (the “here”). This is what you need.

Now, you can take our old friend the import key command (ya, I know I want you to understand but its a pain to write this one out each time. I keep the command in a text file on my desktop to copy and paste when I need it.) and change the old url for this key's one.

Old command:

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - 
New url:
http://www.virtualbox.org/debian/innotek.asc

```New command:

```
wget -q http://www.virtualbox.org/debian/innotek.asc -O- | sudo apt-key add - 
```N.B. Yes, I know one key ends with gpg and this one ends in asc. Consult lexicon for explanation on this, it isn't an important difference, both are usable keys. This brings to a close my adding key section, you'll never really need to remove or otherwise manage keys so I won't cover that.

[SIZE=4]2d) Updating[/SIZE]

Now, we have gotten to the good stuff. We are actually going to install something now. Wait. I know you want to get to installing stuff, but there is something you have to do first. Remember, we modified the sources list and added keys (even if you didn't actually do this physically, it is the example I am going with). Thus, you have to refresh aptitude so that it (your package manager) is aware of the changes made to both and retrieves the information of packages on those new repositories.

First thing I will point out is that there are two ways of installing, via apt-get and aptitude. They are both really the same now, I find my preference lies with aptitude but yours may differ. [This is a discussion on it.]("http://www.psychocats.net/ubuntu/aptitude") You can find more on it elsewhere, it doesn't really matter that much though. I just bring it up for completeness.

Now, to refresh the indexes and update aptitude we will issue the following command:

     
```
sudo aptitude update 
```No need to explain sudo again. Aptitude is the main command that manages packages in the command line, update tells aptitude to refresh the indexes (and recheck all the repositories listed in the sources list). If you wish to use apt-get do so at your own discretion, be consistent though (i.e. Use aptitude everywhere or apt-get everywhere).

Next, I will explain how to manually trigger a CLI update for all the packages on your Ubuntu install. This command will do it.


```
sudo aptitude upgrade 
```Upgrade of course simply tells aptitude to check all packages installed in your system against the repository versions and if the repositories have a newer one, it will appear in a list telling you that you can upgrade. Push y and enter to accept the changes, you can reject them if you wish. To get other updates like new kernel (lexicon) versions and other serious modifications you will need another command however:


```
sudo aptitude dist-upgrade 
```This will get you all upgrades available to your system at the time. Oh and no, it won't upgrade you to Gutsy, that is done via the package manager and you have to explicitly tell it to (the Graphical Update Manager, pops up in the notification area in top right by default).

That takes care of updating things, now on to installing.

[SIZE=4]2e) Installing Software[/SIZE]

Now that your all up to date with your new repositories, lets learn how to install.

First and foremost, the most basic of all things, the install command:


```
sudo aptitude install packageX packageY 
```Take note, this is like all other aptitude commands it begins with sudo (your modifying the system) and aptitude (thats the main program your using, use apt-get if you wish). Install of course informs aptitude you wish to install the following packages, list them in order after that (i.e. PackageX packageY). Note, you can install as many packages as you like there is no limit, I just chose to only give 2 as example. Just remember that each package is separated by a single space.

A properly formed install command will look like this (I will use k3b and libk3b2-mp3 as my generic packages for this entire session of explanations, its mostly examples):


```
sudo aptitude install k3b libk3b2-mp3 
```So, there you have it (a note btw, the libk3b2-mp3 package is to enable MP3 support in K3b assuming you have the codecs already installed, it of course isn't natively supported without this.)

Special Note: A very important package for all users to install is build-essential. This package contains essential tools for modifying key parts (like the kernel) of your OS (i.e when you install graphics drivers, a virtual machine, etc...) On any machine you ever set up, right after updating you should install this package. You now know how to do install so I will not supply the command, so install it when it suits you.

Next, what happens if you want to remove it (what you just installed if you put in that command), you use the remove command:


```
sudo aptitude remove k3b libk3b2-mp3 
```This command will specifically remove the packages I list from the computer, since I'm also using aptitude it will also remove all unnecessary dependencies (lexicon) installed on your computer. The configuration files for the user (those are usually stored in your home folder, they store preferences per account, like the registry) will be left behind to be used if you ever reinstall the program, they take little space.

So what if you want to remove the dependencies as well? You use another command of course!


```
sudo apt-get autoremove 
```This is an apt-get command ONLY, it isn't needed for aptitude (because aptitude will remove unneeded dependencies automatically with the remove command, apt-get will not until this command is run). You don't specify a package after autoremove, it will check all dependencies and remove those that are no longer needed by programs (because those programs were uninstalled).

Next, what if you want to remove all the configuration files associated with the removed packages as well, we have a purge command for that:


```
sudo aptitude purge k3b libk3b2-mp3 
```This command is the highest level of removal, it will remove all packages listed, their dependencies (due to the fact that it's aptitude) and forcibly remove all configuration files from home (and anywhere else on the drive). I don't recommend using it often, mostly only when a problem is occurring with a package and you want a clean start.

Next up, the reinstall command. 


```
sudo aptitude reinstall k3b libk3b2-mp3 
```This one isn't too complicated. If you run into a problem with a specific program (or say you did something to corrupt it) you can tell aptitude to quickly remove it (this remove is not a purge, so it won't remove dependencies or config files) and reinstall the programs listed from the cached downloaded packages. I didn't explain this before but aptitude will cache all the downloaded installers for the various packages you want to install for later use (like reinstalling). It's useful and doesn't take that much space, more on this later.

Following that on the list, what if you want to look for a program? Well aptitude has a solution for that too. You can search for it. There are two ways, I will list both:


```
aptitude search k3b 
```This method tells aptitude to search for any packages that includes the word k3b and it will search live across all of the repositories (i.e. Across the actual versions on the repositories, not those indexed on your computer locally in the cache). It will then return a list of possible matches. Another subtly of this method is that it by default really only looks at the package names and matches it to that. It's best when you know what you want (or maybe looking for a plugin for a specific program and only know the name of the program, very useful in those instances). Search for "beryl" and you will see what I mean by that, just an example where knowing the main name of the program can list all the associated packages/extensions.

The second method is the following:
```
apt-cache search k3b 
```This command will search across all your downloaded and indexes lists of applications (packages). It is presented a bit differently (try both in terminal, you will see it) but ultimately it gets you about the same thing. This method only searches what's local on your machine and not the repositories. It also tends to return broader search results. There are probably more subtleties to them but I don't know exactly, someone feel free to tell me to include in the guide.

What if you want to see more information on this package quickly? Say k3b for instance (I am very unoriginal). Issue this command:
```
 aptitude show k3b 
```The output should be similar to this:

```
Package: k3b -[COLOR=Blue]This is the name of the package (remember, the package name doesn't always have to be the same as the program, it just usually is). It also is always completely lower case.[/COLOR]
State: installed - [COLOR=Blue]This tells you if it is installed or not.[/COLOR]
Automatically installed: no -[COLOR=Blue]This tells you if it was marked for automatic installation, advanced command you don't need to know right now... more on that later.[/COLOR]
Version: 1.0-0ubuntu2+medibuntu1 - [COLOR=Blue]This is the version number.[/COLOR]
Priority: extra - T[COLOR=Blue]his is the priority, K3b is of course completely unnecessary to the daily function of Ubuntu. A Kernel, would have an extremely high priority though since just booting up a console or regular log in requires that always.[/COLOR]
Section: free - [COLOR=Blue]Section of the repositories it is in.[/COLOR]
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com> - [COLOR=Blue]The people who compiled ([Wiki entry on compiling]("http://en.wikipedia.org/wiki/Compiler")) and maintain (i.e. make sure latest package is on repository) the package on the repository.[/COLOR]
Uncompressed Size: 9761k - [COLOR=Blue]The total size it will occupy by itself on your drive (this is only the package for k3b, and excludes any dependencies or related packages.[/COLOR]
Depends: kdelibs4c2a (>= 4:3.5.5-1), libacl1 (>= 2.2.11-1), libart-2.0-2 (>= 2.3.16),
         libattr1 (>= 2.4.4-1), libaudio2, libc6 (>= 2.5-0ubuntu1), libdbus-1-3 (>= 0.94),
         libdbus-qt-1-1c2 (>= 0.62.git.20060814), libdvdread3 (>= 0.9.6), libexpat1 (>=
         1.95.8), libfontconfig1 (>= 2.4.0), libfreetype6 (>= 2.2), libgcc1 (>= 1:4.1.2),
         libhal1 (>= 0.5), libice6 (>= 1:1.0.0), libidn11 (>= 0.5.18), libjpeg62, libk3b2 (>=
         1.0), libmusicbrainz4c2a (>= 2.1.4), libpng12-0 (>= 1.2.13-4), libqt3-mt (>=
         3:3.3.8really3.3.7), libsm6, libstdc++6 (>= 4.1.2), libx11-6, libxcursor1 (> 1.1.2),
         libxext6, libxft2 (> 2.1.1), libxi6, libxinerama1, libxrandr2 (>= 2:1.2.0),
         libxrender1, libxt6, zlib1g (>= 1:1.2.1), wodim | cdrskin, cdparanoia (>= 3a9.8),
         genisoimage, kdelibs-data (>= 4:3.1.4-2), kdebase-bin, cdrdao (>= 1.1.7-5),
         transcode, libdvdcss2 - [COLOR=Blue]These of course are ALL of the dependencies that this package requires to actually run on your system. Since I'm on Ubuntu, it requires a huge chunk of the KDE base to be installed. It also just natively depends on a lot of things.[/COLOR]
Recommends: vcdimager (>= 0.7), dvd+rw-tools, kdebase-kio-plugins, kcontrol -[COLOR=Blue] Recommended packages that will add features I suppose or be used in conjunction, not directly needed like dependencies. Usually they are installed anyway.[/COLOR]
Suggests: k3b-i18n, normalize-audio, toolame, sox, movixmaker-2, libk3b2-mp3 -[COLOR=Blue] These are suggestions, these won't be installed at all unless you do so. They are usually tied to the program (one way or another) and like recommendations will add to your experience with the program.[/COLOR]
Description: A sophisticated KDE CD burning application - Medibuntu package
 K3b is a GUI frontend to the CD recording programs cdrdao and cdrecord. Its aim is to
 provide a very user friendly interface to all the tasks that come with cd recording. 
 
 It can be used to copy CDs and burn: 
 * audio CDs (from wav, mp3 or ogg vorbis files) 
 * data CDs and DVDs 
 * mixed-mode CDs (CD-Extra support) 
 * VCDs (1.1, 2.0 and SVCD) 
 * ISO files (Joliet/Rockridge and El Torito support) 
 * eMovix CDs 
   
 For more information, visit the homepage at [http://www.k3b.org]("http://www.k3b.org/") 
 
 This package is built with dvd ripping support. Therefore, it is in Medibuntu as it might
 violate patents. 
 
 This package isn't supported by Ubuntu: DON'T REPORT BUGS TO UBUNTU! 
 
 Please report any bug to our bug tracker instead: 
 [https://bugs.launchpad.net/medibuntu/+bugs](https://bugs.launchpad.net/medibuntu/+bugs) - Description of the package, enough said.
```The blue, is all my notes on what each section means of the show command. It is very detailed, and will tell you lots of things (some are much more comfortable reading a GUI's properties though for this info, more on that later). Oh and yes you can use it on multiple packages, my recommendation is one or two at a time, the pages fill up REALLY fast with this command.

That's all the basic and moderately advanced commands. Those will get you through 90% of life. I also hope the complete explanations here allow you to understand how it all works. 

[SIZE=4]2f) Advanced Package Management[/SIZE]

This section will contain advanced commands, these will likely be used much less often but I will cover them anyway. I won't need too much detail for these, by now I assume your comfortable with the general structure of aptitude commands. I'll just list the commands and give a brief explanation. Some of these commands can be done much easier with Synaptic, more on that later though.


```
sudo aptitude hold k3b libk3b2-mp3 
```This is the hold command. There are some instances where you need to freeze a package because you know an existing bug with the update in the repos will affect you, or some other reason (I've actually done this often enough). In short, holding a package prevents any attempt by aptitude to modify or change it. Do note, this is a permanent status your applying to the package it will persist until removed.

Of course if there is a hold command..... there is an unhold command.


```
sudo aptitude unhold k3b libk3b2-mp3 
```Like it says, this will remove the frozen/hold status from the package and allow you to update it normally. That's all it does.

Next is a bit of cleaning.


```
sudo aptitude clean 
```As I said before, aptitude will cache the installers of all the packages you install. It is a good measure for when you need to reinstall or take other such actions. Sometimes it starts to take up space and you simply want to get rid of all the cached installers. This command does just that, it clears out the whole cache in one go (no need to designate packages).


```
sudo aptitude autoclean 
```This command is much more useful. Rather than purging the entire cache, this one will simply remove installers for old and outdated packages, as well as those you've removed. Run this as often as you like, it's not often you go back to an old version.

There are 4 commands I won't be covering, I've never used them... they are: keep, markauto, unmarkauto and forbid-version. I don't see a reason for using these, if someone else wishes to explain their function and make the section I will be only too happy to add it.

Now, there is a really cool and yet a bit complicated feature of aptitude to explain. Up until now all commands have had a single purpose (i.e. you told aptitude to install all packages following or remove them all, whatever the action it applied to all packages the same.). This doesn't have to be the case interestingly enough. This is a bonus, that doesn't really bring anything new. Just makes doing lots of management easy. 

I will explain this best with a giant example rather than breaking it down individually. Say I have 4 packages I want to modify with my commands, they are: k3b, vlc, gnomebaker and bittornado. I want to install k3b, remove vlc, purge gnomebaker (it's hypothetically been giving me trouble) and hold bittornado. I can do that all with one command, like so:


```
sudo aptitude install k3b vlc- gnomebaker_ bittornado= 
```Voila, 4 different actions taken with one command. Notice, after vlc I put a minus, and after gnomebaker I put an underscore, bittornado an = (if it wasn't an install command at the beginning a + after k3b would have installed it). These are collectively called override specifiers, they do exactly what they say specify a command that overrides the default one (in my example the default is to install packages listed). Like all other commands there is no limit to how many packages and overrides you can use. Oh and remember there isn't any space between package and override, it always goes directly after. I will list the common overrides here in point form.

- A + after a package will override and install the package.
- A - after a package will override and remove the package.
- A _ after a package will override and purge the package.
- An = after a package will override and place the package on hold.

That's it for the explanation on CLI commands. I've covered practically everything you will need to know. For any additional commands regarding aptitude please look at the manual page for it. That can be gotten from this command:


```
man aptitude 
```There are manual pages for any command (i.e. aptitude, wget, apt-key...) you can use in the terminal, consult them when you need a bit of extra help. A word of warning, they aren't written as explicitly as this guide and a base/moderate understanding is required usually, they can also sometimes be worded difficultly. There are a whole host of modifiers (lexicon) that I never covered, so feel free to look at those if your interested. Most of all, when it comes to commands I encourage you to experiment and try them all for yourself. Just like everything else the more you actually do and practice the better you will be at it.

That is all I have to explain when it comes to CLI, now on to GUI.

---

### Post by forestpixie on 2008-05-04
**Re: Complete Guide to Installation in Ubuntu**             
                                                                [SIZE=4]**3) Installing with GUI**[/SIZE]

I will handle this section differently than the CLI section, that was very hands on and more doing (i.e. Trying the commands). This section is really just understanding what all of these options equate to in terms of what you understand and the CLI. 

[SIZE=4]3a) GUI and Sources List[/SIZE]

So, lets begin in the same place with the sources list. To get to the graphical application for this go through the following menus : System > Administration > Software Sources.

This is what you should see. There are five tabs and I will go through them in order.

[IMG]http://i22.photobucket.com/albums/b324/FFManiac1/GUI1.png[/IMG]

This first tab is the Ubuntu software tab. It stores 5 options, I will list them below and state their purpose/equivalent. I did fail to thoroughly document the function of each of the urls in the previous section of the sources. I will do so now and in explaining each option in the GUI point to its sources list url that it modifies, the url will be in a code box underneath the explanation.

- Canonical-supported Open Source software (main) : This option of course is the main repository, you will get all of the trunk and core updates from here. NEVER uncheck it.
- Community-maintained Open Source software (universe): This option is what allows you to freely download non-Ubuntu projects (i.e. Gnomebaker, tilda, and all other non-Canonical software would be here. It is safe to use without any worry, always have this checked.
- Proprietary drivers for devices (restricted): This is the option for drivers, for the most part its NVidia and ATI drivers, and a few other proprietary things. It is good, keep it checked if its not.
- Software restricted by copyright or legal issues (multiverse): This section stores codecs and other patented/copyright things. Keep this checked if you want to have access to all functions that aren't free (i.e. MP3 support, K3b (its in here cuz of built in DVD ripping that breaks the protection) and other things of the sort. Keep this checked too.
- Source code: This will enable download of all source code of everything you have installed. If your not a developer or programmer then do not check this, it will just waste disk space.

Notes: The first four of these options are of course the equivalent of the sections after the URI's as I explained before, in the brackets is the section they control. You should have all 4 on to get all the programs and options available to you. The last option is the source code one, don't check it unless you really want that.

There are two other options on this tab, the “Download From:” drop down menu provides you with access to mirror country repositories. It is usually best to pick one that is closest to you (I need not explain the drop down options, they are self explanatory). If however, your main set of repositories goes down, pick an alternate mirror to get updates till they come back up (unlikely but happens). These will modify the urls country code of all the canonical servers, like I explained before.

The last option is: Installable from CD-ROM/DVD. This is exactly the same as the option I indicated in the CLI section, I don't recommend it be on to most users. As you know any packages you install from media will usually be out of date.

[IMG]http://i22.photobucket.com/albums/b324/FFManiac1/GUI2.png[/IMG]

This is the Third-Party Software Tab. This is where any and all unofficial (i.e. Repositories not maintained by Cannonical or indirectly affiliated) repositories go. Anything you add will go here. If you followed what I was doing before you will likely have medibuntu at the top and have it checked. The boxes in the left comment in and out the different lines (i.e. a checkmark means it is commented in and will be read/used, no checkmark means it won't.). You will notice that there is a line directly under medibuntu that is the same (well almost) except it has (Source Code) in brackets, all it will do is download source code if you check it. This section does not have a single option for downloading source code as before, each line is added separately alone.

Now that the main view is explained please take note of the four bottom buttons. The first is the Add button, push it and you will be able to copy and paste a single line of repositories in. The GUI will then add it properly to the sources list for you. Let me make something clear, you can only do ONE line at a time. For example, say I wanted to add the following sources list from a site:

[COLOR=Red]Note - I have left this here as an example, the theory should work, however the deb lines themselves are now outdated and should not be used. If you do want to use enlightenment as a window manager it can be installed from synaptic or by using apt-get or aptitude.[/COLOR]

```
## enlightenment e17 beta, use at your own risk
## E17 is in Beta and may break or break your system
[COLOR=Magenta] deb [http://edevelop.org/pkg-e/ubuntu](http://edevelop.org/pkg-e/ubuntu) feisty e17[/COLOR]
[COLOR=Red] deb [http://e17.dunnewind.net/ubuntu](http://e17.dunnewind.net/ubuntu) feisty e17[/COLOR]
[COLOR=Cyan] deb-src [http://edevelop.org/pkg-e/ubuntu](http://edevelop.org/pkg-e/ubuntu) feisty e17[/COLOR] 
```I would add the magenta line, then add again and the red, and lastly the cyan line. I would then untick the last one since it is a source code line.

Next button is Add CD-ROM... This one gets little usage in my experience, I haven't used it at all really. I believe it for adding packages directly from a CD if you burned them separately or received official DVD ones containing the entire Ubuntu repositories. I don't use it that much though, isn't really much to say.

Next button is edit. This one will pop open a box with a few options, it is very rare in my experience to require editing a repository listing after adding (I've never done it), it has happened to others I suppose so I will thusly dissect the edit box and explain again. If you find this at all confusing, completely ignore it (you won't be understanding anything less I don't think).

- Type is the first option, there are only two options available here. Either the repository is a binary download (i.e. It downloads and installs the package itself) or it is a Source repository. You can change this and it will move from deb to deb-src (the sources list text equivalent to Binary and Source) in the sources list. I doubt anyone would really do this.
- URI: This is the actual URI that leads right to the repository. Any other words after this, usually separated by a space are modifiers that specify sections further.
- Distribution: This of course is the distribution (i.e. Feisty, edgy, dapper) it is best not to touch it unless you expressly know what your changing it to.
- Components: This further subdivides the distribution section into what your specifically looking for. Again don't modify unless you know what your doing.
- Comment: This is simply a text comment on the repository. You can write whatever you like here and it will just appear above or below the line, it doesn't do anything though in itself.

Last, is the remove option. It well, removes repositories. I don't have to explain this one, it just deletes whole line. That is it.

[IMG]http://i22.photobucket.com/albums/b324/FFManiac1/GUI3.png[/IMG]

Next a fairly basic tab, I will skim this one.

Ubuntu updates:
- Important security updates (feisty-security): You always want this one enabled and checked, it gives you what it says important security updates.
- Recommended updates (feisty-updates): You want this one to always be checked too, they aren't security fixes simply updates to existing programs. Of special note, somethings a horizontal line is seen, this means not all recommended updates are being received from the sources list. Click it until a solid x (the check mark) is seen, then its fine.
- Pre-released updates (feisty-proposed): This is the section for updates that are proposed to inclusion in the main ones or are being tested (I believe that's it), as such its your discretion if you want these. Usually they are ok.
- Unsupported updates (feisty-backports): These are updates to rather unofficial programs, you want this checked too.

Automatic updates:
- Check for updates: This can be checked or unchecked, it will either tell the update manager to check at the given interval or to not check at all. The options are daily, every 2 days, weekly and every two weeks. I recommend daily.
- Install security updates without confirmation: This option will download and install the updates without prompting you for a pass.
- Download all updates in background: This will of course download the updates but let you install them when you like with your pass.
- Only notify about available updates: This is the default, I prefer it. The update manager will notify you of updates and allow you to pick the ones you want. Then it will download and install after you give your pass.

[IMG]http://i22.photobucket.com/albums/b324/FFManiac1/GUI4.png[/IMG]

This is the Authentication tab. All keys are managed here. The main page lists all the keys you have, with the beginning of their hashes, the date created (the day the key was made), and underneath the name of the key's repository and the contact for the author. 

At the bottom, you will find the Import Key File... This will only work if you actually downloaded the key itself to your desktop (i.e. Right clicked on the link for the gpg/asc key and saved it to the desktop.) Then point the importer to it. It is simple.

Remove is self-explanatory.

Restore Defaults does as it says and restores the defaults. This will however wipe out your third party keys (i.e. The one's that aren't default to the installation). That means you would have to reimport them, don't push this unless you have a reason to.

[IMG]http://i22.photobucket.com/albums/b324/FFManiac1/softwaresources1.png[/IMG]

This one is explained right on the page. Either allow your usage to be somewhat monitored or not, its for a good cause (and is anonymous like stated) but do what you feel comfortable with.

The bottom two buttons are universal. Revert will of course undo any changes you made in this session. Close will apply them. If you save changes your sources will automatically be refreshed so aptitude is ready to go.

[SIZE=4]3b) Skip![/SIZE]

[SIZE=4]3c) Authentication Keys [/SIZE]

Keys have been covered above in the fourth tab, refer to that for it.

[SIZE=4]3d) Updating[/SIZE]

Updates are handled by the graphical update manager. It will appear in the notify area in the top right (next to your volume/network icons) as a orange square with a white middle. Click it and you can see and decide on what updates to apply.

[IMG]http://i22.photobucket.com/albums/b324/FFManiac1/GUI6.png[/IMG]

The main box just lists the updates available by section (from important updates to recommended to less important). The total download size is listed in the bottom left, its the total size for all updates selected. The check button will reload/refresh the update manager to check if any new updates are available. Install Updates will apply all updates selected to your system. Description of update is the last option, select it and you will see more information on the updates. The first tab is a change log and the second tab is just a description. All very straightforward. I recommend you apply all updates that appear unless you have a specific reason not to.

If you want to manually check for updates at any time, you can pull up this GUI by going System > Administration > Update Manager and pushing check. The manager will check as often as you have set it to in the previous software sources section.

[SIZE=4]3e) Installing Software[/SIZE]

This is the last important section, Synaptic Package Manager is the frontend for Aptitude. It is very useful for certain operations. I won't explain it in entirety, most of the options are easy... I will just glance over it and you can see how it is the same as the CLI commands.

[IMG]http://i22.photobucket.com/albums/b324/FFManiac1/Synaptic.png[/IMG]

First thing to explain is the overall layout. At the top are 5 buttons, in order from left to right. Reload, will refresh your list so you have up to date choice of packages. Mark all upgrades is like the update manager, it will hunt down and mark all packages that can be updated for update. Apply will make any and all changes you have made, make sure it's what you want to do. Properties will show you information based on the package you have selected. All of these tabs contain the same information (for the most part) as the show command we used before. The one thing I will draw your attention to is the version tab, multiple versions (available in the repositories) of the same package will be listed here, this will be important later. Last is the search button, it searches. Just like the CLI command except that it offers graphical options on what to search (i.e name of package, description, etc...).

Top left pane is the sections box, it changes quite a bit and is important. By default, the sections filter is applied to this pane. This means that it will display all packages available based on their section/purpose and thus you can easily move through them all. The next section is status, this will break down all the packages by their status, I will explain these they are not as obvious.
- Installed: Of course it just means it is installed properly.
- Installed (Auto removable): This lists packages that are no longer needed and can be removed.
- Installed (local or obsolete): This one is more complicated, two types of packages appear here. Ones you manually installed from debs/compiled from source (any method that did not use aptitude to install). The second type is ones that are obsolete or no longer needed. In general, unless your really sure you don't need it leave these here.
- Not Installed: Uninstalled/not installed.
- Not Installed (Residual config): This means the configuration file was left behind on removal, it is no big deal. I recommend leaving these in case you ever reinstall these applications, you won't be losing much space at all.
Origin will list all packages based on the repository that contains them (i.e. what section). Custom filters are a few wild card filters rarely used, broke packages, and a few others can be found here (not used very often so I will omit detailed explanation). Lastly, is the search results filter. This will list all your searches you've made and allow you to go back to them.

Next pane is really simple, the bottom right one will simply give you information on the package selected in the upper right pane. It is less complete than the properties option. The very bottom you can see from left to right: total # packages available in repos, # packages installed, # packages broken, # of packages set to install/upgrade and number of packages set to removal.

Last pane of importance is the one in the upper right. All packages will be displayed here, the first white box is simply where you can with one click mark it for installation (or other options below). You will have several quick options presented (all can be found in the package menu). One note I would like you to pay attention to is that none of this “marking” will cause change immediately. It's like a to do list, Synaptic will only finalize and apply these changes when you push the Apply button. This is substantially different from aptitude in the command line, which will execute all the commands the moment you push enter. Also remember the mark changes apply to whatever package is highlighted. If you want to mark multiple packages for installation/modification at once you can shift click (select first package, then shift click last one and all in between are selected) or ctrl click (hold ctrl down and select packages individually in a batch don't have to be in any order) and then right click in the selection and you'll get the options available.

- Unmark: will quite simply unmark any designated changes from the package. This will make it as if you never marked it for change at all.
- Mark for installation: This will of course mark this package for installation.
- Mark for reinstalltion: This will mark the package to be reinstalled when applied.
- Mark for upgrade: Will mark the specific package for upgrade (assuming there is a new version in the repositories). Not usually done manually.
- Mark for removal: Will automatically remove the package and dependencies when applied.
- Mark for complete removal: Equivalent of the purge command, it will dump all configurations and any other residuals off your system.

The rest of the main top right pane is information about each packages, the columns displayed can be edited from the Settings > Preferences menu > Columns and fonts tab (as well as other options, feel free to tinker with them as you like). Settings > Repositories will launch software sources for you.

Now, there are a few extra options I would like to go through, please bear with me (I will skip all redundant options). First the edit menu. From top to bottom it holds the undo and redo buttons (with handy key shortcuts). Unmark all will undo all markings you've made to packages in this session. Fix broken packages is useful to know, though its not that common at least for me to break packages. Mark packages by task, this is a very useful feature. Push it and a dialogue will be brought up. Here you can see these are premarked packages that you can install with one click. For example, say you want the Kubuntu desktop (the entire package for Kubuntu, all the base files and programs associated with it) package (i.e. Will give you the option (under the sessions menu) to log into Kubuntu as well as Ubuntu at the log in prompt.) you can just check it and apply. The rest are self-explanatory, use them at your own discretion.

Next is the package menu, a few features are special here. Lock version is the first, it will do as it says, lock the version of a given package. This is only to be used if you know exactly what your doing (usually if you manually downgraded a package to an older version). By locking it you will prevent any and all change to it (no upgrade, removal, etc...). Next is Force version. This handy option does just as it says, when a given package has more than one version, it will let you force an older version if you find incompatibilities or something else you don't like in a newer package (the package still has to exist on the server, if its not there your out of luck). These are advanced options not needed for day to day, but you may use them. It is easier to do them from here than from the terminal commands equivalent (equivalent in the terminal would be hold/unhold and forbid-version (I believe) respectively).

Settings and help menu, you are free to look at on your own. Last one I will mention is the File menu. Save/Save as markings... will let you save the set of markings you've made to the packages (I haven't used this ever). I imagine this would be useful if you got interrupted and wanted to make sure your custom markings weren't lost. The former command just saves over the open save file (if one exists), the latter makes a new one in a custom location. The read markings command simply opens any saved markings file. The other two commands are as well a bit advanced and you likely have no need for them. The first, generate package download script will generate a script you can take to any other machine and execute to perform all downloads of the selected packages. The second, add downloaded packages is to be used in conjunction with the former and will add all those packages you downloaded. These aren't used often to my knowledge.

That is all. I've now explained to you the basics that make up the installation model used by Ubuntu as well as taking you through all of the CLI and GUI steps involved in installing anything. Now I hope you see it's not too hard, it simply involves different steps. I know some errors might exist but this forum version won't be edited past its posting, because I am working on a Wiki version open to editing and with better organization. Please do PM me with notes concerning omissions/errors/lexicon words to add, I will address them all in the Wiki version, this one will of course remain as it is. A few extra sections are added after this, feel free to read them, they contain useful information with regards to everything you just read, including extra resources for learning other topics both related and useful.

---

### Post by forestpixie on 2008-05-04
**Re: Complete Guide to Installation in Ubuntu**             
                                                                **[SIZE=4]4) Lexicon[/SIZE]**

This section simply defines some terms I have listed throughout my guide, you should be here because you found one you didn't understand and a (lexicon) notation was next to it.

[SIZE=4]4a) Lexicon of Terms[/SIZE]

**CLI:** Command Line Interface. It is used to refer in general to any terminal emulator or the console where text commands are accepted and executed. Think of it like DOS on steroids. It really just enables you to give commands and have them executed while still being in your current session of Ubuntu.

**GUI: **Graphical User Interface. This is the generic term that refers to any graphical front of an application. For example, when you open Firefox you see all the buttons and menu entries. That is the GUI of Firefox in particular.

**Linux Distribution: **Linux Distribution's are the name given to each and every separate project, they differ in what programs are prepackaged in the installation and other key features. Ubuntu is of course one example of a distribution, Debian, OpenSUSE, Fedora are all other examples. The saying “flavour of Linux” is often used instead, for example: “If you don't like Ubuntu pick another flavour of Linux.”

**Kernel:** The kernel is the foundation of all operating systems (including of course Windows and OSX). It is responsible for all interactions between software and hardware, it is the lowest level of your system and thus is incredibly important. More information on it's exact responsibilities can be found in [Wikipedia]("http://en.wikipedia.org/wiki/Kernel_%28computer_science%29") and other sites across the net.

**Packages:** All programs stored on software repositories are broken down into packages. This allows for them to be easily tracked, installed, removed or otherwise manipulated without much effort. It is a very efficient model. Quite often packages are named similar to the program they are responsible for to make sure that you can find them all easily, this isn't always the case though.

**Terminal:** A terminal program emulates the Command Line, this might be confusing but it makes sense. The terminal allows for you to issue commands with a CLI as if you were at a straight console (i.e. Think like a DOS prompt (it has no GUI), that's a console since it has no graphical component) . This is important because it allows you to use CLI without having to log out and drop to a console, makes it very seamless.

**Path:** Path is like a pointer, it tells applications (mostly in GUIs) where to look for files (i.e. What folder to look into). Say in Windows you stored a file in my documents, you would tell a friend to open Explorer, then My Documents, then your Folder containing it (maybe My Pictures) and there it is. In Linux things are different, it employs a single hierarchal system that means that all folders and directories are under one large folder called the root directory. It is designated with a slash (i.e. /) and all sub folders are names that come after it. For example /etc/apt/sources.list. This path shows you where your sources list is, in the root directory there is a folder called etc (it mainly stores configuration files), and inside that folder is apt (folder for aptitude) and inside that one is the file named sources.list. It is always a progression left to right and absolute paths always start with root (/). For more information, click Linux Command lessons [2]("http://www.linuxcommand.org/lts0020.php") and [4]("http://www.linuxcommand.org/lts0040.php") are helpful.

**Source Code:** This is a freely readable file containing, as the name implies, the code that runs/creates the program (i.e. The code is the source of the program). You need not be concerned with this, unless you are a developer/programmer and understand the code you are best not to include these in your sources list or bother retrieving them separately. They are there if you wish to see them though at a later time, remember that you can get the source for any free and open source software. 
[B]
FLOSS:[/B] Free Libre Open Source Software. This term will come up often in your adventures with Linux/Ubuntu. It has many other names FOSS (minus the Libre) Open Source Software are a few others. A complete explanation can be found here at the [Wikipedia entry.]("http://en.wikipedia.org/wiki/Free_and_open-source_software") The short summary is that it means software that is Free (as in beer, you can get it for paying nothing. Opera browser is this kind of free, but not Libre or Open source, so you see you can be free software and not FLOSS) Libre (as in, you can do whatever you want with it (modify the program however you like)) and Open Source (means that the source code is freely available for you to read, modify or edit). I encourage you to support complete and partially FLOSS projects whenever you can, they can't thrive and grow without us.
[B]
Graphical Display Manager (aka GDM): [/B]This is the generic term that applies to all parts of the your display manager (that is what generates your windows, the panels and every other graphic of your desktop). The most important parts are the Window/Display Manager (WM/DM, this controls how the windows are displayed and how they and the desktop behave), the Window Decorator does as it says and makes the windows look a certain way, and then the panels (those are basically your panels where you launch applications and interact with other things). There is also of course the Desktop which just encompasses your shortcuts and mounted drives. One of the advantages of Linux is that the display manager is not completely integrated with the rest of the OS (this is the case in Windows, and why when you BSoD or corrupt your graphics drivers you usually have serious issues and need to reformat). In Linux, you can use different GDM's and even swap them out as you like (Kubuntu and Xubuntu use different DM/WMs for instance).

**Modifier:** These are a bit more advanced additions to commands in the terminal. Like their name implies they make slight modifications to the command you use, you can use more than one in conjunction with each other on the same command. For example, lets take wget the command I first used the modifier q on. Say hypothetically that q is quiet mode (it actually is for quite mode, dual is made up) and d is for dual (that would magically increase the speed of the download). So, if I wanted both to apply to wget I would use the command like so “wget -qd <rest of command>”. So, as you can see I start with wget, then the – marks everything directly after that (without a space) as a separate modifiers of that command, then the rest. Most modifiers are just a single letter (there are never usually more than 10-15). To learn more about modifiers for any given command read the manual pages for it with, the following command “man <command>”, for wget it would be “man wget”. You can get manuals for any pages, they are a bit advanced (unlike my guide, they will only skim the information you need and aren't always completely indepth) read them at your leisure.

**GPG (ASC) keys:** GPG is an encryption method (well, really its a technology to enable cryptography), it is very powerful, flexible and most of all free. It is used as the keys to repositories. A good explanation is on Wikipedia [here]("http://en.wikipedia.org/wiki/GNU_Privacy_Guard"). Whether the key ends in .gpg or .asc is really irrelevant in most (if not all) cases, just use the key command I showed you and the appropriate url and it will work. There isn't really an important difference worth mentioning.

**Dependencies: **These are simple but I felt I ought to clarify. Dependencies are like they say, anything a program depends on. In Windows, when you run a game, it usually depends on a given version of directX it was written for and will ask you to upgrade if it isn't present. In Ubuntu there are many more dependencies but luckily aptitude will take care of them all. Leaving extra dependencies in your machine will not slow it down over time, it isn't like Windows and the registry (old users know crap in the registry bogs it down fast). If they aren't in use by anything, they are usually inactive and take nothing other than space (if space is at a premium its a good idea to get rid of unused dependencies).

**Frontend: **A common word used in the software world. It usually refers to a program that was previously a CLI or text based application and got a GUI to be a bit more user friendly. For example, Synaptic Package Manager is just a frontend to Aptitude it in itself doesn't actually install things it simply provides a graphical interface that handles all the commands for you behind the scenes.

[SIZE=4][B]5) Extra sections
[/B][/SIZE]
[SIZE=4]5a) Add/Remove GUI[/SIZE]

This can be easily found from Applications > Add/Remove. It is a very simplified GUI for installing things, it doesn't need too much explanation.

[IMG]http://i22.photobucket.com/albums/b324/FFManiac1/4a.png[/IMG]

The search section at the top will let you quickly find the application you want. This GUI does not display packages, instead it shows the program you will install and takes care of all the work for you. With simplicity comes dumbness, the interface is really only designed for add and remove functions, nothing else. On the left you will see a common division of the applications by task and you can easily mark the ones you want. The last important feature is the show drop down menu. It will let you filter all applications by its filters, they are self-explanatory. Lastly, push apply when your done.

That's it for this section.

[SIZE=4]5b) Differences Across Versions[/SIZE]

I won't try to pretend, I am a GNOME user (default for Ubuntu) primarily. As I know most people head straight for that version, and it's the one I use, it is the version I wrote my guide for. Very little changes from this to Kubuntu. I will make a quick list of important changes that I might have mentioned, but are worth repeating.

- Aptitude and Sudo are universal commands that apply to both versions equally (as well as Xubuntu/Edubuntu). Where they differ is in other commands. There is no gedit for instance in Kubuntu by default (you can install it though if you wish). The equivalent is called kate, and to open a file graphically with it you MUST use the kdesu command (I mentioned this before, use it like gksudo prefacing the command). Contrary to Ubuntu where you can open gedit with sudo, kate will only return an error and fail to start with sudo.
- The terminal for Kubuntu is called Konsole. You can open it from the run box (Alt + F2, then enter konsole) or from Kmenu > System > Konsole.
- Kubuntu certainly does not have Synaptic (it can though I think, if you really want to install it). Instead, its default package manager is Adept. Most of what I said applies to it (from the little experience I have with it), some options may exist in different places though so look around.
- Software repositories can be editted graphically. First open up Adept (Kmenu > System > Adept) and then go to the following menu Adept > Manage Repositories. The same basic explanation I made applies to here, but as with adept the layout will be different. It is still the same sources list though.

Most sections should be applicable to all versions of Ubuntu (especially the CLI/Text files sections). Another section bites the dust, that's it for the glaring differences from my guide. 

[SIZE=4]5c) Extra Resources[/SIZE]

Consult these sites for extra reading and understanding (some even have nicer pictures than mine). There are also a few that will give extra information I never covered.
[B]
[Linux App Finder:]("http://linuxappfinder.com/")[/B]This site will let you find programs you want to use (many you probably don't know about) by searching based on function on the left. You can then of course find them in the repositories via a search or add their separate repositories to your own sources list.

[**Ubuntu Guide:**]("http://ubuntuguide.org/wiki/Ubuntu:Hardy")This site will list a lot of common applications people want to install and what packages are needed. You can of course completely understand this now and do it on your own, it is just handy to know what packages you want for the given programs.
[B]
[Linux Command:]("http://www.linuxcommand.org/")[/B] A great site for understanding the terminal/CLI better. If you found anything to be confusing, or just want to learn more about it, I advise you look over this site. [Of particular note is the wild cards section, these make CLI very powerful.]("http://www.linuxcommand.org/lts0050.php#wildcards") There of course also are more advanced sections like scripting, read on at your leisure.

**[Psychocats:]("http://www.psychocats.net/ubuntu/")** For more tutorials with pictures see Aysiu's guides, he has laid out a lot of common tasks and questions.
[B]
[Ubuntu Geek:]("http://www.ubuntugeek.com/")[/B] This site is done by Ubuntu Geek. It offers quite a bit of tutorials and you are free to go through and learn with them as well.

**[Herman Zone:]("http://users.bigpond.net.au/hermanzone/")** If you need to learn more about GRUB editing, MBR, and a whole host of other common things this site offers good guides to read along with.

**[Ubuntu Wiki:]("https://wiki.ubuntu.com/") **This site stores many community wiki entries on lots of subjects covered here, especially Synaptic/Adept and sources list. They also contain a wealth of other knowledge just search for something in Ubuntu and it likely has a wiki here.

**[Ubuntu Forums:]("http://ubuntuforums.org/forumdisplay.php?f=73") **The beginner section is a great place to ask any question and get a quick response, the place is very friendly don't be shy. You might even get a response from me.

---

### Post by iSplicer on 2008-05-04
This is amazing. Thankyou! 

So well written, not just a block of text, but has clear sections and shots. Well done.

---

### Post by forestpixie on 2008-05-04
As I said right at the beginning it's not mine I just got it moved from the archive.

---

### Post by hanifsm on 2008-05-07
Thanks a lot. May i save it for future reference from Firefox History

---

### Post by jivadas on 2008-05-07
I would very much like to use Ubuntu, and have paid CA$50+ 
for "Ubuntu for Non-Geeks, 2d ed.", which has v.7.04; and also an installation disc for 8.04. I run an AMD Sempron 3200+, with 512MB memory, on a 100 GB hard drive. 
   I gat the 7.04 installed, I think, but cannot figure how to open the installation on the 7.04. As for the 8.04 disc, it does not want to install at all. 
   I might add that neither of these presentations uses an hourglass or similar indication to show that something is going on. This is rather important, I believe, since my last attempt to install ended in a blank frozen screen, so that I had to unplug the machine. 

x0x
jd

---

### Post by forestpixie on 2008-05-09
> **hanifsm said:**
> Thanks a lot. May i save it for future reference from Firefox History

The whole forum is there to be saved if you so wish :D

---

### Post by .adma on 2008-05-14
curious as to how the Wiki is coming along.  I for one am very excited!

---

### Post by .adma on 2008-05-14
I made a static version of the guide into PDF.  Please let me know if you want me to remove this, but I thought it would be useful to others!

[COLOR="Navy"][Pdf of Guide found here!]("http://www.mediafire.com/?lffkmmoxnbe")[/COLOR]

---

### Post by ZabiGG on 2008-05-14
Great idea! ;) I just hope you left all credit information where it was due (it's just plain courtesy) :p 

A big newbie thank-you to you,

ZabiGG

---

### Post by aysiu on 2008-05-14
While this guide is rather comprehensive and good for those users who like to read long explanations and really try to understand processes, I think it's worth plugging some other software installation tutorials that serve different needs.

[How to install ANYTHING in Ubuntu! A graphical guide for all new users with a Windows background using Ubuntu](http://www.monkeyblog.org/ubuntu/installing/)

[Psychocats Guide to Installing Software](http://www.psychocats.net/ubuntu/installingsoftware)

[Wiki Guide to Installing Software](https://help.ubuntu.com/community/InstallingSoftware)

[Various YouTube Videos on Installing Software in Ubuntu](http://www.youtube.com/results?hl=en&q=install%20software%20ubuntu&um=1&ie=UTF-8&sa=N&tab=w1)

---

### Post by forestpixie on 2008-05-14
> **.adma said:**
> I made a static version of the guide into PDF.  Please let me know if you want me to remove this, but I thought it would be useful to others!

[COLOR="Navy"][Pdf of Guide found here!]("http://www.mediafire.com/?lffkmmoxnbe")[/COLOR]


Hi - as you can tell from the first few lines of the thread - it's not actually mine to yay or nay - I didn't do any of the original task and massive it must have been. All I have done is make sure links work and turn most of the feisty references in to ones for hardy.

As far as the wiki goes that was not me it was starcraftman

---

