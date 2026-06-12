---
title: "create gui for linux command line"
date: 2008-08-30
forum: Programming Talk
---

### Post by lieja on 2008-08-30
anyone have idea about this..i need to develop gui for linux..i dont have the idea yet so i juz wanna ask you guys if u got one. one more thing..what should i prepare to start this project..i juz think to use glade with c++..any idea..juz thrown in here..ok:)

---

### Post by emobrad on 2008-08-30
What do you mean by GUI for the command line? The point of the command line is to be for cli.

---

### Post by lieja on 2008-08-30
i mean i want to create gui to replace the CLI like partitioning with command in cli and with gui we have gparted..something like that

---

### Post by signifer123 on 2008-08-30
A  GUI for all commands though?

I'd stick with C++ or something higher, C++ strings makes stuff like that easier. If you are planning on parsing the --help or man pages for a command, i'd recommend looking at boost libraries. They have regex, and tokenizer libraries.

[http://www.boost.org/](http://www.boost.org/)

The regex library is also in the repository as libboost-regex.


Personally I'd say use whatever you have the most experience with. I just assumed it would be C++ because you brought it up.

---

### Post by scragar on 2008-08-30
there's always the hotwire project.

[http://hotwire-shell.org/](http://hotwire-shell.org/)

---

### Post by lieja on 2008-09-09
thanks for the hotwire link..but its to complicated for me to understand that because im very beginner to all this programming stuff. let me show you guys what i need to do in a simple words..just look at the interface i've create..i know its quite ugly but..it's impotant to me..[ATTACH]84678[/ATTACH]
i using glade for this interface..i really need a sifoo for this..please if there somebody expert with programming language and glade..please..i know this is easy for u..

---

### Post by nvteighen on 2008-09-09
Ehhm... It seems like you were trying to write some kind of terminal emulator with command searching facilities, am I right?

---

### Post by Archmage on 2008-09-09
I'm using Gnome or KDE for this.

---

### Post by lieja on 2008-09-10
nvteighen> i think its juz a GUI for the Linux shell utilities coz i only focus on history command..im not really familiar with terminal emulator though

archmage> please..if u get my idea can u give me some guide through this stuff..im really need it:(

---

### Post by lieja on 2008-09-13
is there anybody want to help me??:(

i juz notice that when im using glade-gnome and compile the gui..the program which contain gnome widget has error said that libgnomeui-2.0 is needed..can anybody tell me how to install the package..i already try to install with aptitude and apt-get but still doesnt work:confused:

---

### Post by FranMichaels on 2008-09-13
zenity (if you have Ubuntu its already installed) can probably do some of what you want.

[http://live.gnome.org/Zenity](http://live.gnome.org/Zenity)

I've dabbled with it a little, but only made a few things (a simple rom launcher, asks for name of the game or folder [mine are by system, region and genre] then lists the results with locate and grep in a nice gui list, click the game file hit okay, and another script launches the appropriate emulator based on folder name) 
I will post the source on my blog one of these days (I barely update the thing.)

Anyway, zenity is very cool, but I would love there to be more examples...

These got me started though
[http://linux.byexamples.com/archives/259/a-complete-zenity-dialog-examples-1/](http://linux.byexamples.com/archives/259/a-complete-zenity-dialog-examples-1/)
[http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/](http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/)

---

### Post by slavik on 2008-09-13
along with the screenshot, could you describe how a user would input a command and such? (this is called a use case).

personally, I understand the gist of what you want, but I am not sure how it isn't solved by hotwire.

---

### Post by dwhitney67 on 2008-09-13
> **lieja said:**
> anyone have idea about this..i need to develop gui for linux..i dont have the idea yet so i juz wanna ask you guys if u got one. one more thing..what should i prepare to start this project..i juz think to use glade with c++..any idea..juz thrown in here..ok:)

First I will concentrate on proper grammar.

Then for a command-line GUI, I would use either the gnome-terminal or an xterm.

How about just using zenity to prompt the user to click ok every 30 seconds.  It's a GUI, it serves no purpose, and is annoying... nevertheless it is a GUI.

---

### Post by CptPicard on 2008-09-13
What exactly does the search box do? I mean... shells already have tab-completion for commands, line-editing, command history by up-arrow...

---

### Post by lieja on 2008-09-13
thanks for the reply..
actually the search button is similar to ctrl+r..i juz want to implement the cli with gui for user who dont like to memorize the key and command of the history.im not so good in programming but i really want to learn..
the main question is,can i just use glade for that purpose as i mentioned earlier..or am i also need to install IDE as well to make it works?? 
is zenity similar to glade?

sorry..i know my english is not good but at least u understand it..:)

---

### Post by signifer123 on 2008-09-13
> **lieja said:**
> thanks for the reply..
actually the search button is similar to ctrl+r..i juz want to implement the cli with gui for user who dont like to memorize the key and command of the history.im not so good in programming but i really want to learn..
the main question is,can i just use glade for that purpose as i mentioned earlier..or am i also need to install IDE as well to make it works?? 
is zenity similar to glade?

sorry..i know my english is not good but at least u understand it..:)

You can use just glade, you just save, and hit build. It will save out the source code to where you save.

If you want an even simpler solution, i'd recommend an IDE with RAD. Like KDevelop(C++ + QT/KDE), QTDesigner(C++ + QT), Boa Constructor(Python + WxWidgets), or Gambas (Basic).

Zenity is not like glade from my experience, it creates User Interfaces based upon command options, rather than from code. But the good part is it's possibly easier, and you can change the programming language you use to modify the User Interface.

Some simple Zenity Usage.
[http://www.linuxjournal.com/content/make-your-scripts-user-friendly-zenity](http://www.linuxjournal.com/content/make-your-scripts-user-friendly-zenity)

---

### Post by slavik on 2008-09-13
> **signifer123 said:**
> You can use just glade, you just save, and hit build. It will save out the source code to where you save.

If you want an even simpler solution, i'd recommend an IDE with RAD. Like KDevelop(C++ + QT/KDE), QTDesigner(C++ + QT), Boa Constructor(Python + WxWidgets), or Gambas (Basic).

Zenity is not like glade from my experience, it creates User Interfaces based upon command options, rather than from code. But the good part is it's possibly easier, and you can change the programming language you use to modify the User Interface.

Some simple Zenity Usage.
[http://www.linuxjournal.com/content/make-your-scripts-user-friendly-zenity](http://www.linuxjournal.com/content/make-your-scripts-user-friendly-zenity)
glade doesn't generate source code anymore.

---

### Post by signifer123 on 2008-09-13
Oh, I didn't upgrade to glade 3 after tinkering with it, i stayed at 2.

If you want to use the sourcecode version install the plain glade, not glade3.

I guess to add to that list. There is Java with NetBeans, and SunStudio that have GUI builders in them. Maybe Eclipse does too. But i'm not sure about how open Java is, and how well it's included in Ubuntu.

MonoDevelop also has GTK# Bindings, and it shows a GUI Designer. If you like C#.

---

### Post by lieja on 2008-09-15
what about glade-gnome..i already install that package and follow some tutorial on the net for gui builder..then i get this result during compiling application include gnome widget..compiling application with all gtk widget is fine..this problem only occur when im includes gnome widget to the gui..  

```
liza@liza-laptop:~$ cd /home/liza/Projects/gtemp
liza@liza-laptop:~/Projects/gtemp$ ./autogen.sh
**Warning**: I am going to run `configure' with no arguments.
If you wish to pass any to it, please specify them on the
`./autogen.sh' command line.

processing .
Running aclocal  ...
Running autoheader...
Running automake --gnu  ...
Running autoconf ...
Running ./configure --enable-maintainer-mode ...
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for PACKAGE... configure: error: Package requirements (libgnomeui-2.0) were not met:

No package 'libgnomeui-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PACKAGE_CFLAGS
and PACKAGE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

---

### Post by signifer123 on 2008-09-15
Install libgnomeui-dev, sudo apt-get install libgnomeui-dev . Because you are compiling it you need the headers.

---

### Post by Sorivenul on 2008-09-15
This sounds similar to [PyQe]("http://sourceforge.net/projects/pyqe").

---

### Post by lieja on 2008-09-16
thanks..really fix my problem:)

i juz trying zenity but couldnt help me much coz it juz for display the dialog not the whole interface for the gui application..correct if im wrong

---

### Post by lieja on 2008-09-22
by any chance..could glade possibly use with zenity?

---

### Post by ghostdog74 on 2008-09-22
if you are not into very fanciful GUI, why not just create a web page? You have checkboxes, radiobuttons, select menus, submit buttons.. etc...

---

### Post by lieja on 2008-09-22
please see my attach file..how can i manage the shell command with web?? :confused: does it make sense?? sorry..i never think about web

---

### Post by ghostdog74 on 2008-09-22
> **lieja said:**
> please see my attach file..how can i manage the shell command with web?? :confused: does it make sense?? sorry..i never think about web
for example, if you do it in PHP, there are functions in PHP to make system calls to shell commands. All you need to do is execute it in PHP and get the results and display at the web browser. Also, most shell commands , for example, the ls command, [can be done in PHP](http://sg.php.net/dir). therefore, there is no need to call "ls".
eg PHP 
```


<?php
error_reporting(E_ALL) ;
if ( ! $_POST['submit'] )
{
 
?> 
     <FORM action="<?=$_SERVER['PHP_SELF']?>" method="POST">    
     Enter directory path: <INPUT name="dirpath" type="text" />
     <INPUT type="submit" name="submit" value="Submit"/>
     </FORM>
<?php
}
else
{

$dirpath = htmlspecialchars($_POST['dirpath']);
if ($handle = opendir($dirpath) ) {     
     echo "Files:<BR>";
    while (false !== ($file = readdir($handle))) {
        echo "$file<BR>";
    }     
}
close($handle);
}
?>


```

---

### Post by lieja on 2008-10-13
oic..but i really need to do it with glade..:(
actually..how the bash script communicate with the gui script?

---

### Post by slavik on 2008-10-13
I am still having trouble understand what you want to do. Could you please sketch something in GIMP of what you would want this GUI to look like?

---

### Post by lieja on 2008-10-14
i've already attached the file at the first page of this thread if im not mistaken

---

### Post by lieja on 2008-10-16
ok..i'll make it clear for everyone..the gui will appear when user type history gui commands  or something like that..the history window appear with 3 buttons for user to search,edit and delete the list of history..for the first step..i need to know how can i display the history list into the textview in gui?? please anybody??

---

### Post by nvteighen on 2008-10-16
Ok... some sparse ideas.

1. There's a file called ~/.bash_history, written in a rather primitive format. It should be extremely easy to make an application that reads that file.

2. Your program will do three tasks: 1) read the history file, 2) show it and 3) execute a command. If I were to write this, I would care for the GUI only after I have some module(s) with functions that manage those tasks. The GUI will only be the way the user activates those functions.

3. You'll have to think about how will the command be executed. I'm not quite sure whether calling system() (that's in C; translate to whatever language you'll use) from a GUI application works or not. If not, I fear you'll need some "pipe engineering" to inject data into the terminal's pseudo-device...

---

### Post by lieja on 2008-10-17
ok..thank u so much for giving me a clue:)

---

### Post by lieja on 2008-11-01
ok..lets see if i have a c program to open and read the file and display the file contents called read.c.then..how can i implement it to gui in glade..please..i really dont get the idea how the c program connect to the gui script..should i create other file which implement the c funtion or just connect the gui with the available c file:confused:

---

