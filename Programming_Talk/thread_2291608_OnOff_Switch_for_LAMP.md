---
title: "On/Off Switch for LAMP"
date: 2015-08-21
forum: Programming Talk
---

### Post by brian-mccumber on 2015-08-21
I recently switched from Windows to Ubuntu and have set up a lamp server for php/mysql development. I had a wamp server set up in Win7 that I used to use and I did not like the fact that the server started when the computer booted the OS. Considering all the trouble I had getting the wamp server set up and running correctly I didn't want to mess around with it trying to keep it from starting when Windows loaded so I left it alone.

I have noticed that the average user has more control over processes and the like when I switched to Linux so I was wondering if anyone else who uses apache/php/mysql combo has stopped the server from starting when the OS boots and uses a script or something to start it and stop when it is needed. In other words something like an on/off switch for the lamp server. Any ideas or points in the right direction will be appreciated.

---

### Post by TheFu on 2015-08-21
Stop the services involved when you want. sudo service XYZ stop
Start the services when you want. sudo service XYZ start
If you don't want them to start, set the defaults so that doesn't happen for each of those services.  **update-rc.d** is the command.

All of these things are in the "Ubuntu Server Guide." [https://help.ubuntu.com/lts/serverguide/](https://help.ubuntu.com/lts/serverguide/)

Oh - and if your system runs "systemd", the commands will be/have changed.  I'm on 14.04 still and don't know much about systemd ... except I want to avoid it for as long as possible.

---

### Post by Lars Noodén on 2015-08-21
You can turn Apache2 and MySQL on and off with the [service](http://manpages.ubuntu.com/manpages/trusty/en/man8/service.8.html) shell script. 

```

sudo service apache2 stop
sudo service mysql stop

```

or

```

sudo service apache2 start
sudo service mysql start

```

You can prevent either from automatically starting at boot using upstart for MySQL on 14.04

```

sudo sh -c "echo 'manual' > /etc/init/mysql.override"

```

and SysV for Apache2

```

sudo update-rc.d -f apache2 disable

```

---

### Post by tgalati4 on 2015-08-21
Many web services, such as Drupal, come with control scripts.  These are simple scripts that do exactly that, but some housecleaning as well.  Search the web and you will find a few.  Take one and tailor it to your needs.  If you are bringing the web server down for maintenance, you will want your webpage to reflect that and those commands can be found in the control script.

---

### Post by brian-mccumber on 2015-08-21
So in your experience, starting and stopping the services via terminal or sh script has no ill effects on the services? I have had bad things happen when I tried to do that to these particular services running in Windows. I used Easy php for the php server and sometimes I would have to stop and restart services a few times before the Apache server would stay running. Sometimes it would take more than a few. Also the MySql server would do weird things and not let me log into at random times.

---

### Post by brian-mccumber on 2015-08-21
[**[COLOR=#000000]tgalati4[/COLOR]**]("http://ubuntuforums.org/member.php?u=241895") this is a development server not a production server. I won't be serving any web pages from my laptop just making them.

Also since I am new to the terminal I am adjusting and learning how to use it at this time. I am familiar with a DOS environment but these Linux commands can be put together in ways I just don't understand at this time. And thanks for the responses.

---

### Post by brian-mccumber on 2015-08-21
**[COLOR=#000000] TheFu, [/COLOR]**[COLOR=#000000]I saw that guide a few days ago and started reading it but when it got to the part where it said for Ubuntu LTS server edition I stopped reading it because I installed the desktop edition and then I installed the other three pieces of the lamp server one at a time using apt-get.[/COLOR][B][COLOR=#000000]

[/COLOR][/B]

---

### Post by TheFu on 2015-08-21
a) Linux isn't Windows. **CLI tooks work BETTER on Unix. **
b) If you run server processes, treat it like a server. 
c) In Linux, the "desktop" is just another program. It isn't tightly tied to the entire OS. Running a "server" program on the desktop works just as well, but you need to treat that program as if it was running on the server release. There are a few caveats, but the stuff you are doing is a well-worn path.

Read that **Server Guide**.  If you are running a non-LTS release - know that support is only 8-9 months. You are expected to move to a newer release every 6 months.

And read the **Ubuntu Desktop Guide** too!  Both apply to you.

---

### Post by brian-mccumber on 2015-08-21
Thanks again Fu. When I said desktop I meant I was running Ubuntu 14.04lts desktop - [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop) - 

Maybe I misunderstood but it looked like there were a few different versions of LTS, and I thought I had downloaded and installed the desktop version, for lack of a better word. I noticed there was also what I interpreted as a server version. So are you saying that there is no versions just Ubuntu desktop which is a program and Ubuntu server which is a program both of which run on the Ubuntu operating system?

In hind sight I wish I would've found that one step lamp server installation before I had installed each piece separately, it looks like it would have been easier to manage via the terminal because to start and stop that you only have to stop one service instead of three. 

Also I realize that Linux is a completely different beast than Windows and I am working out the terminal stuff but I come from a command environment and as you said cmd window and the terminal are way different except for the few DOS commands that work in the terminal like cd, dir, and mkdir. Back in the day there were many more commands for the DOS window but over time MS has slowly started to dumb down it's user base by trying to control every.freakin.thing in the windows OS and the computers that windows runs on. Which is why I switched to Linux in the first place. I am not an idiot and I do not need someone else controlling every aspect of my OS or my computer. I think I just overloaded myself trying to learn too much stuff about Linux at once as quickly as I could. I am going to go back and start over with those two articles you posted. But I did want to mention that setting up the lamp server and getting it to run right was like 200% easier and about 1000 less troubleshooting steps than it was to get it running correctly on Windows. I like making websites and stuff I really don't like setting up and worrying about servers but in order to use php for web dev this is a required step that I really need to get familiar with. And thanks again for the tips and tricks.

---

### Post by tgalati4 on 2015-08-21
You will find development in linux is a more connected experience.  Things seem to work the way you expect them to.

Here's an example of some control scripts:  [https://www.drupal.org/project/dbscripts](https://www.drupal.org/project/dbscripts)

---

### Post by brian-mccumber on 2015-08-21
[**[COLOR=#000000]tgalati4[/COLOR]**]("http://ubuntuforums.org/member.php?u=241895"), I did notice that things just seem to be easier to get going and less troublesome than they are in Windows especially if it requires other packages that are not included in whatever I am trying to install, I have come across at least a million missing required dll errors in the past. I am not regretting the switch to Linux at all, in fact I wish I would've switched years ago, but if I had I wouldn't be here picking you guys' brains for these tid-bits of knowledge. Just as soon as I figure out how to mod Minecraft on Linux I will be switching my desktop over to Linux also, probably the same distro as I'm using now. And thanks for that link I will be giving that a read also. I wish I could give you guys some beans or a like or something for the help but I guess I can just say thanks. I am pretty sure this won't be my last post at this forum, well unless something horribly tragic happens between now and the time I get all that stuff read. :)

---

### Post by brian-mccumber on 2015-08-21
[**[COLOR=#DD4814][B]Lars Noodén**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=168643"), just so you know I didn't just skip by your post, it helped me alot also, so thanks to you too. I liked your no nonsense, get straight to the point attitude.

---

### Post by TheFu on 2015-08-22
Well - apache and mysql started out on Unix and because Linux is 97% the same, running it here is easy.  Windows is a different animal and those tools were a port. I suspect you just think they are easier because you had already learn some of the basics on Windows.  Unix programs that are ported to Windows still feel like Unix.

Those two links are good - they explain WHAT to do, but lack the WHY. When learning, getting some of the history for design choices can make things more clear.  The more understanding you have the overall philosophy, the more Unix stuff clicks together. If you find yourself thinking these people were less than brilliant, read a little of the history and I think you'll discover they were actually geniuses. Those 2 links often leave out details, especially around security. There is a "Basic Ubuntu Security" article here somewhere. Good read and gets you thinking in the Unix way.  Security on Unix is VERY different from Windows.  

The knowledge level you have today is such that google searches for answers are not the best way to get the solution. It is hard to tell from online articles whether the person writing actually knows their stuff or not.  About 50% of the online article I find do things incorrectly or without enough steps or too many steps.  For example, if they ever say **sudo gedit** - that is a mistake and can damage a system.  WHY?  Because gedit uses the HOME variable to store settings and sudo alone like that doesn't change the HOME to be root's location.  What you end up with is a gedit settings file owned by root inside your personal ~/.config/ area.  Using sudo with any GUI program is dangerous for that reason.  Use **sudoedit** and those issues are handled correctly - desktop or server - it doesn't matter.

So - besides those 2 links, gaining some directed, organized, knowledge of the basics would be good too. There is a well-written, Free PDF, here: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) You don't have the read the whole thing - just the first 250 or so pgs. Keep the rest for reference - skim those other pages 1-2 sec per page just to know what is there so when you need it ... you know it was there.  

In a shell, if you are typing more than 3 characters at a time, you are doing it the hard way. Look up "tab completion" and learn it. There is no need to type complete directory or file names - like the shell fill in most of that for you.

My comment about "server" vs "desktop" is that you can load any server package onto the desktop and it will work. Just don't expect there to be a GUI to manage it - "treat it like a server."  For internet-facing services, having a GUI on the server is a generally considered a bad idea for many reasons.  For a development box - fine, but know you'll need to deploy using the shell/cli methods to a hosting provider.

Oh - and some people might be offended calling it a "DOS cmd" or "DOS environment". Unix existed before MS-DOS.  BTW, IBM had "DOS" in the 1960s on their mainframes.  I learned IBM 360 ASM on a "DOS" machine.  "shell" or "CLI" or "in a terminal" are what most people say these days.

---

### Post by brian-mccumber on 2015-08-22
Wow Fu, you really know your stuff! Ok so the commands that are the same  in the terminal and the Windows command prompt window, hope I didn't  offend anyone this time,  are the same because Microsoft actually  'borrowed' those from the Unix system not the other way around. In fact  Microsoft pretty much cloned Unix back in it's beginning. This is wild. I  had no idea. OS/2 actually came from a Unix root too. In fact, after  reading a little, it seems that all modern day operating systems have  their roots in Unix.

When I went to install Ubuntu on this  computer, I actually had to do a little research because the file system  in Linux is really, really different from Windows and I wanted the  install to go off without a hitch and I wanted to keep the security  features of Linux intact. I keep using Windows as a reference point  because up until a week ago it is all I have ever used. I have played  around with Linux distros by running them from the live disks in the  past but I never really considered using it as a full time OS until  recently. When I booted from the Linux cd I combined all the partitions  that were on my hdd from the Windows installation and then I created  three new partitions. One for root drive@55gb, one for swap@2gb, and the rest I  allocated for the home drive, so I think I at least got that right.  After reading your comment about sudo gedit I do remember seeing that  alot in peoples instructions when I was searching how to do things  pertaining to the apache server on Linux, mainly editing config files to  tailor Apache to my needs, good thing I did not use it for anything.  Instead I used terminal commands and sudoedit to set Apache, PHP5, and MySQL configs. I  checked in the home directory and none of the config files for any  part of the lamp server are in there, but I did notice that there are  alot of other config files in the home drive for other software that I  have installed. I think the worse thing I did to compromise security  while sorting the lamp server out was I took ownership of the  /user/var/www directory so I could add and edit php files/webpages/websites ect... that I am  building but since I am only using the web server for development and  not serving any pages to public, I figured it would be ok.

As for transferring to and editing files from production servers, I have always used Filezilla and notepad++ plus it's ftp plugin and I saw that I can install Filezilla to upload sites and on Linux I can use the Fuse mountpoint from Gnome2 to gain access to remote files and then edit them using Geany or Gedit or I can use the FTP plugin for Gedit, so nothing was really lost. Now all that is left is for me to sort out building GUI's on Linux, it is a much more involved process that it was using Visual Studios, and getting C++ and Python files to compile from Geany when using non-standard c and python headers like gtk. I know I can pass the compiler commands from Geany when building or makeFiling but I haven't quite got that figured out yet. When I was using the gtk library to try to make a window just to see what it was about, I would create and write the file using Geany then cd to the directory I put c files in with the terminal and then paste the special compile line for gtk libraries ```
gcc gtkTest.c -o gtktest `pkg-config --cflags --libs gtk+-3.0`
``` bypassing Geany's compiler. When I tried to compile c code that used gtk, Geany would say that the gtk library didn't exist or was missing so I probably have to add it to Geany's header library list or figure out how to put that line in Geany's build path when I am building files that use gtk. I will get all this sorted out soon enough tho, and really, I have only been using Ubuntu for a few days now I thought I was doing pretty good to get Ubuntu installed, the lamp server up and running, customizing Ubuntu's appearance, and getting all the alternative packages for graphics and code editing installed and running without screwing anything up. I opted for using Gimp and Inkscape instead of Photoshop and Illustrator. So basically I have my Windows workstation cloned over to Ubuntu already, and I am loving it.

TheFu you have been a huge help and I do appreciate it and I learned a bunch of useful things. I am sure I will be nosing around this forum alot, so I will probably see you around. I try to google my problems before I post in forums and I only post in forums if I have read a bunch of stuff on the subject and it still doesn't make sense, or if I want to do something custom like make a couple shell scripts that I can just click that will turn the components of the lamp server on and off because I don't want them running if I am not using them, which I still haven’t quite figured out how to do which was the reason for this post in the first place, but I have figured out what I have to use to do it so that is good enough for me.

---

### Post by Lars Noodén on 2015-08-22
Actually there were intermediate steps, MS-DOS was a ripoff of CP/M via QDOS.  Poor Gary Kildall really got screwed over.  The articles with his story are vanishing from the web and paper copies from older magazines are not accessible to most people even if they have time time and inclination.  

But about the file transfer, SFTP is the way to go.  Accept no imitations and definitely [do not use FTP](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp) in 2015.   The file manager supports SFTP and so does FileZilla so you won't need any special clients to get started.  In the file manager, press ctrl-L and then enter the URI for the SFTP server: sftp://user@server.example.com/path/to/some/   That is also integrated into Gedit so you can put the sftp://... address in the file name when you open a file and it will open the connection to the server for you.  

With regard to server versus desktop, all the flavors of Ubuntu can be created from one another by adding or removing programs and tweaking configurations.  The Server edition, Ubuntu, Kubuntu, Xubuntu and Lubuntu all just have different default settings but could be transformed into one another.  Under the hood they are all the same, which that is one reason why so many are enthusiastic about the shell.  Another is that it is a full scripting language and anything you can do via the shell (which is anything and everything the computer is capable of) can be automated by saving the 'commands' with their options into a file.

---

### Post by TheFu on 2015-08-22
Ok - so you are C/C++ developer - that changes much of my advice compared to someone just trying to use php and LAMP.

a) My best advice for Learning Linux is here: [http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux)
b) Geany is a great editor, if you have a GUI.  Otherwise, like on a server, you need to know vi/vim. PERIOD.
c) Stop using plain FTP and if your hosting provider only supports FTP - FIRE THEM IMMEDIATELY. They don't take security seriously at all. Use sftp. [http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp)
d) Geany doesn't have a compiler. By default it uses gcc, but if you learned on Windows using an all-in-one IDE, you probably have the IDE and compiler mixed up.  That is NOT how anything works, even on Windows. Compilers are external programs. On Unix, debuggers are external programs too, but an IDE captures the output from these other tools and uses that to show the line with the issue or the debugger "next" line to be run ... you get the idea.  I worked as a professional C/C++ developer for about a decade on 12 different platforms. "Windows" counted as 1 platform though we compiled for 4 different systems due to binary compatibility issues.  cmake is the project file used for C/C++ programs these days. In the old days, we used gmake and Makefiles.  Learning "Makefile" syntax is almost a new language.  Tabs matter inside a makefile - don't replace tabs with spaces or spaces with tabs. It will be bad.

Be certain to read "a" above to get your mind thinking differently.  Linux is like Unix which is VERY DIFFERENT from Windows at the level you and I work.  Grandma doesn't need to know the difference, but we do.

Also - learn and understand intuitively that Linux is a multi-user OS where file and directory permissions are absolutely critical for system security.  You are correct to be concerned about /var/www and because it isn't on the internet, it is fine, but one of the common issues we work through here is how to setup those areas for multiple users to have only the necessary access required and no more.  /var/www is the beachhead for web server security. Get that wrong and all is lost.  

Learn file and directory permissions soon than later. Learn those well, learn the subtle ways permissions work, takes about 45 minutes with 4 different users, multiple groups, and lots some time with umask, touch, chmod to see how things fit together. Until you do this, there will be serious gaps in your knowledge. Reading isn't the same as doing.  Learn setuid, setgid methods too - those are handled by chmod too. The sticky-bit is something different, but useful once every 10 years.  The setgid bit on a directory is useful every month or two. Learn this and how it works.  I've had to use setuid 2 times in 25 yrs. These days I'd use sudo with extended options instead. Actually the last time I did this, ended up switching to a complex sudo setup for about 6K users rather than using setuid.

Anyway - I've babbled enough this morning.

---

### Post by brian-mccumber on 2015-08-23
Wow I just spent 30 minutes writing you two a reply but apparently when I logged in it didn't log me in. So now you're going to get the condensed version. 

First off thanks again. I am reading all the links you guys have posted starting at the top. You guys have been a huge help in getting me pointed in the right direction.

I have always used filezilla and plain ftp to upload websites I have made to client's servers and never had a problem, but secure is secure and I will be using sftp from now on. Also from reading what Lars wrote I don't even need to install filezilla, I can just use the file system and gedit which is great, the less tools I have to worry about the better off I am.

I do know the difference between compiler and IDE. When I said Geany's compiler I meant the one it is linked to. I did not mean I thought it had it's own built in compiler. I was aware that I am using gcc to compile c files. I had this dev environment set up on windows where I used the old DOS editor that you can still bring up by typing in edit from an elevated command prompt and the vb compiler that ships with .net framework to write vb modules using a custom command window that I loaded from a batch file which set it up to use the command line compilers from .net. I enjoy messing with vb since it is such an easy language to write. I will post the batch file below in case you want to have a look. 

Also any time you feel like babbling about c programming on Linux feel free to do so here, I am eating this stuff up. I am just adjusting to the steep learning curve I found I had when I switched to Linux from a lifetime of using Winblows. If I could absorb all this stuff through osmosis I would but I can't so I have to read and try stuff and from some of these Linux command lines I have seen that just look like a string of switches to me I have some learning to do.

batchfile to set up command line compiler use from a command window in windows
```

@Set Path=C:\Windows\;C:\Windows\System32;C:\Windows\Microsoft.NET\Framework\v2.0.50727\;%PATH% 
@Set LIB=C:\Windows\Microsoft.NET\Framework\v2.0.50727\;%LIB% 
@Set INCLUDE=C:\Windows\Microsoft.NET\Framework\v2.0.50727\;%INCLUDE% 
@Set VCBUILD_DEFAULT_CFG=Debug^|Win32 
@Set VCBUILD_DEFAULT_OPTIONS=/useenv 
Color 0A 
cls 
@echo Setting environment to use Microsoft .NET Framework command line compilers. 
@echo Hello Brian. 
@echo ---------------------------------------------------  

```

---

### Post by TheFu on 2015-08-23
Happy you are finding this useful and having fun.

1 comment.  Always use /, not \ in your C/C++ code.  Windows paths work just fine with the '/' instead.  So does OSX.  It is most important for #include paths.

---

### Post by brian-mccumber on 2015-08-23
Well I'm going to chalk that one up to windows poisoning and the fact that I mess with html alot, hehe.
..

---

### Post by brian-mccumber on 2015-08-23
I once wrote php code that wrote php code that wrote php code that might have something to do with it too. It gets confusing after awhile.

---

### Post by Lars Noodén on 2015-08-23
> **brian-mccumber said:**
> 
batchfile to set up command line compiler use from a command window in windows


I'm not a C programmer nor play one on TV but, especially back before package managers became a thing, have used packages that were not in the package repository back when they had to be build manually.  From that I gathered that the way to set up the environment in non-legacy systems is to set up [make](http://manpages.ubuntu.com/manpages/trusty/en/man1/make.1.html) to build and even run tests.  Back then for portability it was usually a perl script that built the make file, but that is not needed in your case nor in general nowadays.  

There are a lot of tutorials on using make / gmake around

e.g.
[http://www.cs.colby.edu/maxwell/courses/tutorials/maketutor/](http://www.cs.colby.edu/maxwell/courses/tutorials/maketutor/)

Then you just cd to your project directory and run make with or without options for testing.  

Anyway, you'll want to look for yourself to see if that is relevant for you and if it is the correct way to do things now for your C or C++ projects.  There's also a [programming subforum](http://ubuntuforums.org/forumdisplay.php?f=310) where people can point the right direction.

---

### Post by brian-mccumber on 2015-08-23
Thanks Lars. I installed freeBASIC and it uses make file to compile and I think that python will use it too if you try to build a python script which I foolishly did a couple times before I realized, oh I can just run the python script it doesn't have to be compiled.

I noticed you said cd to the project directory, well while I have been messing with this stuff I got tired of having to cd into directories especially if they were like 4 to 5 directories deep so I did a quick search on how to open the terminal in a specific directory and I found this link that I will post below. I followed the instructions, then logged out and back in and BAM, when I am in the file browser, if I need a terminal, I can right click a directory or white space in a directory and there is now an option to open in terminal which opens the terminal with the path to the directory already filled in. It is a real time saver. I hope you find this as useful as I found the advice you have given me.

[http://www.howtogeek.com/192865/how-to-open-terminal-to-a-specific-folder-in-ubuntus-file-browser/](http://www.howtogeek.com/192865/how-to-open-terminal-to-a-specific-folder-in-ubuntus-file-browser/)

---

### Post by Lars Noodén on 2015-09-02
> **brian-mccumber said:**
> I noticed you said cd to the project directory, well while I have been messing with this stuff I got tired of having to cd into directories especially if they were like 4 to 5 directories deep so I did a quick search on how to open the terminal in a specific directory and I found this link that I will post below. I followed the instructions, then logged out and back in and BAM, when I am in the file browser, if I need a terminal, I can right click a directory or white space in a directory and there is now an option to open in terminal which opens the terminal with the path to the directory already filled in. It is a real time saver. I hope you find this as useful as I found the advice you have given me.

[http://www.howtogeek.com/192865/how-to-open-terminal-to-a-specific-folder-in-ubuntus-file-browser/](http://www.howtogeek.com/192865/how-to-open-terminal-to-a-specific-folder-in-ubuntus-file-browser/)

Thanks for finding that.  I have it installed now and had been rather missing that functionality and am glad to have it again even with Unity.

---

