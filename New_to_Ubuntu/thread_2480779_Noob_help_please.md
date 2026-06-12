---
title: "Noob help please"
date: 2022-11-09
forum: New to Ubuntu
---

### Post by ian9365 on 2022-11-09
Hi all

I am after 40 years association with computing and programming for the first time dipping my toes into the world of non MSDos / Windows computing. I have installed Lubuntu on a 10 year old Toshiba netbook and  finding it both fascinating and frustrating.

I am generally managing to muddle my way forward but have hit a particular stumbling block I cant seem to get past.

I have installed a couple of things with the Muon Package manager, a simple text document, extension .doc and a A+ programming suite with a few dependencies.

My problem simply put is how on earth do I easily get at them or even know where they are, I eventually discovered that the tabs at the bottom of Muon will tell me where they were installed to and then digging away with a file manager will allow me to eventually find them but OMG what a pain that is, Ive got to be missing something obvious.

I'm not afraid of typing command lines into a terminal, I grew up with MSDOS, but I am totally unfamiliar with any flavour of linux, Unix or basically anything not Microsoft.

Any help or pointers will be great

Cheers

---

### Post by Impavidus on 2022-11-10
If you want to find the files belonging to a package, the package manager can tell you. You already found it. Muon is fine, as are other interfaces to the package manager, like the various apt command line tools or the synaptic GUI package manager.

Most of the time, there's no need to know exactly where the files get installed. They get installed in the place where the relevant software can find them. In some cases you need to know anyway. Or you just want to know. For example, some packages have their documentation not as the regular man pages, but as pdf or html documents. You can still expect them in somewhat standardised places; read about the [Filesystem Hierarchy Standard]("https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard").

---

### Post by ian9365 on 2022-11-10
Thanks for the reply, however maybe I didn't state my question properly.

You are of course correct in that I have no need to know where all the individual files and dependencies are physically stored, except of course in the case of documents or other media that have to be viewed directly.

If I install an application in MS Windows then I am generally given the option to put an entry in the start menu and/or an icon on the desktop to access it. I was sort of expecting something similar. It didn't happen, indeed initially I even thought the install had failed.

---

### Post by ian9365 on 2022-11-10
Thanks for the

 "Filesystem Hierarchy Standard" 

link it is and will be very helpful. I guess I've become somewhat brain washed by years of being spoon fed by Bill Gates

---

### Post by tea for one on 2022-11-10
> **ian9365 said:**
>  I have installed Lubuntu on a 10 year old Toshiba netbook and  finding it both fascinating and frustrating.
It's nice to read about older hardware being revived with an Ubuntu flavour.
> **ian9365 said:**
> I have installed a couple of things with the Muon Package manager, a simple text document, extension .doc and a A+ programming suite with a few dependencies.
My problem simply put is how on earth do I easily get at them or even know where they are
Have you seen this [https://manual.lubuntu.me/stable/index.html](https://manual.lubuntu.me/stable/index.html)
Specifically [https://manual.lubuntu.me/stable/5/5.3/lxqt-runner.html](https://manual.lubuntu.me/stable/5/5.3/lxqt-runner.html)

---

### Post by TheFu on 2022-11-10
> **ian9365 said:**
> Thanks for the

 "Filesystem Hierarchy Standard" 

link it is and will be very helpful. I guess I've become somewhat brain washed by years of being spoon fed by Bill Gates

By default, all user files are placed into their HOME directory.  $HOME is the environment variable.

$HOME == ~/
So we can use multiple different ways to say the same thing.  These shortcuts are dependent on the current userid.  The location of the HOME directory for each userid is specified in the passwd database.  This is usually /etc/passwd (a text file), but it can be an LDAP or x.500 directory service too, if that is configured.  Don't worry, if you don't configure those, they aren't being used.   There is nothing special or mandated about using /home/{userid} for HOME directories.  It is just really common for home users of Linux.  In a business, almost always LDAP will be used and HOME directories will be on networked storage and mounted as required somewhere like /users/u1/{username}.  But let's make some reasonable assumptions about your computer, at home, in the house.  HOME for userid 'bob322' is spelled out in the /etc/passwd database (fancy term for text file) as /home/bob322.

For Bob to get to his HOME directory, he can use these commands.  Each of them will take him there:
```
cd
cd $HOME
cd ~
cd ~bob332
cd /home/bob322
```

Those are all the same. Only the last command doesn't perform a passwd lookup to work at some point.  During login, the HOME environment variable is set based on the passwd DB.

Now, if Bob wants to go into Jane's HOME directory, say the username is jane111, he'd use either of these commands:
```
cd ~jane111
cd /home/jane111
```

IF you don't know about "tab completion", you'll want to stop now and learn it.  Find a youtube video, since it is one of those things that is harder to explain than to use.  Basically, if you are typing more than 2-3 characters at a time, then you are doing it wrong.
If I were Bob trying to go to Jane's HOME, I'd type
```
cd ~ja{tab}
```
That would probably fill in the answer.  If it doesn't, hit {tab} again and a list of choices that match so far are shown. 1 more character with a {tab} again will likely fill in the correct value.  Basically, there's little excuse for ever mistyping a program name or input file name or most options for a command, thanks to tab completion and how it validates things.  Mistyping commands and options  is something we see noobs do all the time, because they aren't using tab completion all the time.

When you are new to Unix, you have to overcome the idea that MSFT's way of doing things was how everyone does it.  Actually, most OSes are based on Unix and work in the Unix way.  That means even if 80% of the GUI stuff seems similar, in reality, about 40% is actually accomplished in a similar way by the programs.  Thinking in the Unix way is an important skill, unless you plan to point-n-click on your Linux system all the time.  If you only use the GUI, you'll only have access to 20% of the greatness that is Unix.  The real power comes from scripting and automation. It is expected that every user will write small scripts - say 1 to 10 lines - to accomplish things efficiently for themselves by putting together a few small, efficient, programs/tools to get them the final result desired.

For example, you'd like to find files that are somewhere on the system.  In MS-Windows, you'd use their File Finding tool probably.  You know, that bloated tool that you probably disabled from indexing because it would eat most of the CPU and disk I/O when it was really inconvenient.  In Unix (<--- that term means Linux, UNIX, BSD) systems, there are a number of different tools to find files.

a) If you know the filename and know the file is a day old or older, then you can use the 'locate' command. Every day, it indexes local file systems. It isn't installed by default and the package name has changed a few times.  Just try to run 'locate' and bash should tell us the name of the package - install that package. On my 20.04 system, that would be 
```
$ sudo apt install mlocate
```
You can force it to index everything immediately, 
```
sudo updatedb
```
Around 6:30am daily (or at least once a day) the indexing of anything new/deleted will automatically happen going forward.  Remember that filenames are case-sensitive, so if you aren't certain about the case, use 
```
$ location -i somefile
```
when searching.  The results are nearly instantaneous and filtered based on the current userid.

b) If you know the file name and a likely location, you can use the 'find' command.  'find' has lots of options to filter files which makes searching faster, but it can be complex to use.  'find' can look for old files, new files, files larger than X MB or GB or TB, files smaller than Z MB, GB, whatever.  Files owned by a specific userid, and/or files modified within a range of days .... or just by a partial name.  'find' is one of the few commands were I think seeing examples is helpful.  Google for "50 find command examples" to see what's possible.  The good thing about find is that it scans the location specified recursively, so there isn't any indexing.  The bad thing about 'find' is exactly the same.  It can be slow, so if we are looking for files on huge storage areas, it will be slow.

c) Comprehensive searching, similar to what google does, is also available.  There are many different tools for this, but I think the easiest and best at the job is called 'recoll'.   Recoll has a GUI or can be used from the shell.  It also requires that an index be created before it can find anything.  Once that index is made, searching for filenames or contents inside all the popular file formats is nearly instantaneous. It knows how to index PDFs, docx, xls, txt, emails, config files, programs, manpages, info files, html, media file metadata (mp3, ogg, mp4, mkv, whatever) ... basically all the files.  The indexing can be setup to updated as needed (daily, weekly) or never (default).  I update it daily via cron at 4:10am.  Most people would drop it into the daily crontab directory so it is automatically updated "sometime" during the day, but I leave my storage server on 24/7/365.  
I'm a shell person, not so much about GUIs.  So, to search for "Mission_Impossible" files, I have a little search script that actually uses recoll ... and runs this command:
```
$ recoll -b -t -q "Mission_Impossible" 
```
For fun, let's time how long that takes to return:
```
$ time recoll -b -t -q "Mission_Impossible"
...
file:///d/D1/M/Mission_Impossible_III
...
file:///d/D1/M/Mission_Impossible_II
...
file:///d/D1/M/Mission_Impossible-Ghost_Protocol
...
file:///d/D1/M/Mission_Impossible
...

real    0m0.405s
user    0m0.011s
sys     0m0.006s

```
So, less than half a second.  It found about 20 results - videos, epub/pdf books, nfo media files.

Recoll is amazing. Highly recommended if you have lots of files and want to search based on content, not just the filename.  For searching based on a filename, locate is the tool to use.  To search based on extra knowledge, say files changed in the last 6 days, 'find' is the tool.
[https://youtu.be/uPbDySi-p2w](https://youtu.be/uPbDySi-p2w) is a DEFCON 25 video about Recoll. The first half is about 5 minutes and all you need to know.

---

### Post by Impavidus on 2022-11-10
GUI applications should normally include a .desktop file. The program creating the menu just looks for those .desktop files and uses them to generate menu entries. I use Xubuntu, but Lubuntu is similar in this respect. The main place where .desktop files get stored is in /usr/share/applications. No guarantees though. Command line applications include an executable or a symlink to an executable in some directory that is normally in your PATH, usually /usr/bin. Your PATH is an environment variable with a list of directories where the system looks for executables when you run some command; run```
echo $PATH
```to see where your PATH points.

You'll find that Linux tends to take a more modular approach to things than Windows. This way, we can swap one desktop environment for another and the menus still work. And if something fails, you'll get an error message. No news is good news.

---

### Post by ne29914 on 2022-11-10
I'm a Lubuntu user since several years and am very happy with it.
But there are some MSDOS/Win things you need to ban from your mind. One is: you don't need to know where the progams/executables are stored. You can't do anything with them anyway. Let Muon take care of that.
But there are three main directories you need to focus on:
/home - this is where all your valuable work and documents are stored.
/etc - this is where configuration files are stored
/usr - this is where even more configuration files are stored plus other stuff (it's in fact a bit of a place where things are stored when no other directory fits the bill). The most important part is /usr/share

Leave the rest to Lubuntu and Muon to start with. That'll give you plenty to do. :)

---

### Post by TheFu on 2022-11-10
I cannot remember ever touching a package-installed config file under /usr/.  Not once.

OTOH, when I'm not using a package manager, but need to install a program with settings and other things onto a system for all users, those all go in /usr/local/ .  That's where we put things that are specific to 1 machine, typically compiled stuff.  For example, if I needed a special version of ffmpeg that I'd changed some code and needed installed, it would end up in /usr/local/bin/ with manpages in /usr/local/man/ and any settings going into /usr/local/etc/.  Noobs wouldn't be doing that - at least I hope they wouldn't.

Most of the time, config files have a hierarchy of locations.  Each program can do things in their own way, but usually, it works like this with the highest priority to lowest:
* Environment Variables
* Command line options - often a '-c /path/to/config' option is provided
* Config file in the user's HOME (somewhere specific, not a random file)
* Config file in /etc/ (somewhere specific)
* Compile-time defaults

So the user's HOME directory config file - probably in ~/.config/{program name}/config or something like that will take priority over any config file in /etc/.  Some programs look for settings in all those locations. Others only look for the highest priority file and use settings inside it, ignoring settings in lower-priority files.  There are pros and cons for each method.  It is nice to have system-wide defaults that can be overridden as needed.  But it is also nice to have all the settings used in a single file. Trade-offs.  The manpage for each program should specify the name and location(s) of config files. Also, that config file name often will also have a manpage to explain each config option.  For example, the journalctl program manages systemd logs.  The config file to manage that program is /etc/systemd/journald.conf .... so 'man journald.conf' will contain explanations of the settings it supports.  Yep:

```
JOURNALD.CONF(5)                    journald.conf                   JOURNALD.CONF(5)

NAME
       journald.conf, journald.conf.d, journald@.conf - Journal service
       configuration files
....

```
Seems to have about 5 pgs of good information.

About package managers.  Ubuntu uses 2 package management systems. These are mostly disconnected.
**APT**  ... which has been used by Debian since the 1990s and 
**snap** packages ... which started being inflicted onto Ubuntu users around 2018, but have been forced onto us more and more with each release.
Let's ignore snap packages for now.  There are about 50 why snaps suck threads in these forums that you can look over, when you have problems with a snap package.

APT is the overall package system.  There is a back end database that is accessed and maintained by libraries that all the APT-based package managers use.  Because the DB is shared by all, we can choose which APT interface we want to use.  There are plenty of those, but don't worry, they all use the same back end DB files, so switching package manager programs isn't dangerous 99.99999% of the time.  Think of the different package managers like web browers running on different machines, but they all submit their queries to google and, generally, the same results happen.  So, we can use apt, apt-get, aptitude, synaptic, "Ubuntu Software Center", "Gnome Software Center", Muon ... or 10 others and it won't matter.  The "Software Center" things tend to restrict information displayed and push popular programs while hiding OS and libraries packages.  The "Ubuntu Software Center" mixes snap packages and normal .deb packages in ways that seem slimy to some people.  I have to say, I've never used any of the "Software Center" GUI programs, so I really don't know much about them.  Almost always, the last 3+ yrs, I've been using 'apt' for package management stuff, with exceptions for specific needs like getting lists of installed packages on a system which are easier to get with different tools.

When someone asked Where are Packages Installed on ubuntu: [Https://ubuntuforums.org/showthread.php?t=2479254&p=14112819#post14112819](Https://ubuntuforums.org/showthread.php?t=2479254&p=14112819#post14112819)
was the answer.

Some of my notes about looking for package information depending on what I know:
# Is a package installed, removed, partially installed?  Completely purged packages don't show up:
dpkg -l '{part-of-package-name}*'

# Which package provides a specific file?
dpkg -S /usr/bin/passwd
dpkg-query --search '/path/to/file'
apt-file search vim

# Find package dependencies:
apt-cache rdepends virt-viewer

# list of files in a known package:
dpkg-query -L {pkg-name}

# Search for a named package
apt search {part of package name or summary}

---

### Post by ne29914 on 2022-11-10
> **TheFu said:**
> I cannot remember ever touching a package-installed config file under /usr/.  Not once.

Who said anything about "package-installed"? Not I.
There are plenty of configuration files and other stuff under /usr/share/ that may need to be modified.
The settings for the main user are by default pulled from /usr/share/
Other users get theirs from $HOME/.local/share
You can create a $HOME/.local/share for the main user, but that's certainly not the default in Lubuntu.

---

### Post by grahammechanical on 2022-11-10
I am looking at this question differently from everyone else. So, I must be wrong! 

Is the original poster (OP) looking for an easy way to run/launch the applications/programs he has installed? In Lubuntu an application should put an icon on the desktop that would launch the application. In Lubuntu there is also something called the Runner. To bring up the Runner press the Super/Windows key + R. In the search panel type the name of the application and the runner will find the application and it can then be launched.

The .doc file format is a Microsoft Word format. It seems to me that the OP is saying that he installed an extension to an application to read MS Word doc file format files. But what application was this extension installed in. 

Regards

---

### Post by ne29914 on 2022-11-10
> **grahammechanical said:**
> I am looking at this question differently from everyone else. So, I must be wrong! 

I don't think you're wrong.
My reply was to a "noob" on where to focus first. Been there myself, it can be daunting, and I take a KISS approach in that situation.
That others feel the need to write half a user manual as reply is perhaps not so helpful.

BTW: in Lubuntu, all installed user programs are available in the applications menu. The desktop has to be configured manually.

---

### Post by TheFu on 2022-11-10
> **ne29914 said:**
> I don't think you're wrong.
My reply was to a "noob" on where to focus first. Been there myself, it can be daunting, and I take a KISS approach in that situation.
That others feel the need to write half a user manual as reply is perhaps not so helpful.

BTW: in Lubuntu, all installed user programs are available in the applications menu. The desktop has to be configured manually.

Pithy answers are great!  Others are great at that.

I can type crazy fast and think some deeper knowledge can be helpful   ... or ignored.  Either is fine.  Sometimes a simple answer isn't the best. Only the person seeking answers can decide.

In another thread today, I provided a pity answer - 1 sentence that didn't even wrap!  Shocking.  Oddly, it was the perfect solution for what they needed - 1 command that would actually work on their system. The person was confused and wanted more information.

---

