---
title: "Unix: Ten Things Every Java Developer should Know"
date: 2006-06-27
forum: Programming Talk
---

### Post by vinodis on 2006-06-27
An post by Russ Olsen. Here:-
[http://www.javalobby.org/articles/10things-unix/](http://www.javalobby.org/articles/10things-unix/)
> 
Unix: Ten Things Every Java Developer Should Know

One of the great things about Java is how multi-platform it really is. While cross platform glitches do occur, they are not really all that common. But since the law of unintended consequences is all pervasive, we now have the common sight of teams of developers building Java programs meant to run on Unix boxes on Windows.

Developing code meant for Unix on Windows does work reasonably well. The trouble is, many those coders slaving away in front of XP have a very limited understanding of their target platform. If that describes you, this following list is meant for you. Without further ado, here are the ten things you really need to know about Unix, in reverse David Letterman order:
10) You need to be special to use some ports

On Unix machines, programs run by ordinary mortals cannot use network ports less than 1024. Only the special root user can use these ports. If you do decide that you need to run your server as root, be very careful since a program running as root is all powerful on a Unix machine.
9) There is no magic file locking

Windows has this magic file locking mechanism that prevents people from removing a file while it is open. Thus, on a Windows box the call to delete() in the following code is pretty much sure to fail:

 InputStream is = new FileInputStream("foo.txt");
 (new File("foo.txt")).delete();
 int ch;
 while( (ch = is.read()) > 0 )
   System.out.println( "char: " + (char)ch );
 is.close();

The delete will fail because someone (our program in fact) has the file open. After we get done printing out its contents, foo.txt will still be there. The kicker is, the delete() will work just fine on any Unix box. Under Unix, the call to delete() will delete the entry for foo.txt out from the file system, but since someone (our program) still has the file open, the bytes will live on, to be read and printed out. Only when we close the stream will the contents of foo.txt follow its name into oblivion.

In exactly the same way, on a Unix box, someone can delete a program's current directory right out from underneath it.
8) Sometimes there is no GUI

People who are used to Windows are sometimes surprised to find their programs running on a Unix box that has no GUI at all. None. Zilch. Nada. In Unix, the GUI is an add on component and it is completely optional. The machine will run fine without it and servers commonly do. Be very careful making calls to those handy java.awt methods -- some of them will fail on a machine with no GUI.

While you are at it, you may want to rethink what you are writing out with System.out. Many severs not only lack a GUI, they are completely headless: no keyboard, no mouse, no screen. If you are deploying into this kind of environment, the log file is your friend, because your program's cries for help are unlikely to be heard anywhere else.
7) In Unix, there is no registry...

... but if there was, it would be a plain text file. Unix systems have no central place like the Windows registry for storing configuration information. Instead, Unix configuration is spread over a fair number of different files. Many of these files live in a directory called /etc : the list of users is in a file called /etc/passwd, while the name of the machine is typically found in /etc/host.

I guess if you are a Windows user that is the bad news. Here is the good news: most, if not all of the configuration files are plain text files. You can look at them with any old text editor. A further bit of good news is that all modern Unix like systems come with GUIs to edit the configuration files.
6) Forward slashes are your friend

This one is really more about Java on Windows than it is about Unix, but useful anyway. Just about everyone knows that Unix uses forward slashes to separate the bits of a path: /etc/passwd, while Windows uses backslashes: c:\Program Files\Windows. What a disturbing number of folks don't realize is that forward slashes work just fine on in Java on Windows too. On a Windows box, Java is smart enough to translate /a/b/c/foo.txt to something like C:\a\b\c\foo.txt.

Should you rely on this for production? No. If you are really coding cross platform Java, you need know about File.pathSeparator and the various File constructors. But if you are coding stuff that is only meant for Unix, and you just want to test it on your windows box, knowing that the forward slashes work in both places can save a lot of agony.
5) Our services are just programs

In Windows, system services are special programs, written to a particular service API. On Unix, services are provided by pretty ordinary programs that do service like things.

Typically, a Unix service consists of the useful program and a script which starts the program in the background when the system starts up and may shut it down again when the system is halting. Many Unix systems keep these scripts in the /etc/init.d directory.
4) Environment variables are hard to change

Windows programmers sometimes cook up little batch files that set the environment variables they want. Perhaps you need to roll back to an old version of Java and Ant. You might write a batch file that looks something like:

set JAVA_HOME=C:\java1.4.1_05
set ANT_HOME=C:\apache-ant-1.6.1

They can then run the batch file:

c:\> setenv.bat

and have the environment that you need. If you try to translate this directly into Unix-land, you get a script that looks not too different:

#!/bin/sh

JAVA_HOME=/usr/java1.4.1_05
export JAVA_HOME

ANT_HOME=/usr/apache-ant-1.6.1
export ANT_HOME

So you try out your new script...

$ setenv.sh

...and it does nothing. The trouble is that the Unix shell runs scripts by creating a copy of itself and running the script in the new shell. This new shell will read in the script, set all the environment variables and then exit, leaving the original shell and its environment unchanged. I hate when that happens. Changing directories works pretty much the same way: if you do a cd in an ordinary shell script, it will change the directory for that second shell, which may or may not be what you want.

If what you want is to change things in your current shell, you need to have the current shell read in the script directly, without starting a new shell to do the job. You can do this with by using the dot command:

. setenv.sh

Life will be good as your environment variables change.

I should mention that there are several different shells available in Unix. Which one you use is mostly a matter of taste, either yours or the person who set up your account. The commands above will work with many of the common Unix shells, but if you happen to be running the C shell (note the pun), then your little script will need to look something like:

setenv JAVA_HOME /usr/java1.4.1_05
setenv ANT_HOME /usr/apache-ant-1.6.1

You also need a different command to read the script in:

source setenv.csh

3) We don't like spaces in our file names

Okay, this one probably has more to do with Unix users and sys admins than the OS itself, but the fact is, we don't like spaces in our paths. Oh it is perfectly possibly to have spaces in Unix file names. In fact you can put darn near anything in a Unix file name: /tmp/:a,*b%c is actually the name of a directory on the system that I am using to write this.

But can and should are two different things. Unix users spend much of their time using the command line and Unix command line utilities are not crazy about paths with stars, question marks and especially spaces. The Unix guy can always find a way, but if you insist on putting strange characters like spaces in your file names, you are just finding a way to annoy your local Unix guy.
2) There is no carriage to return

If I had just one magic lighting bolt to hurl at one person, I think I would pick the guy who decided to use different line terminating characters on the two major OS's. I suspect we would have hyper intelligent computers by now were it not for all the time wasted trying to figure out why my file looks funny on your OS.

In a plain text file, Windows typically uses a carriage return followed by a newline character to mark the end of a line. Unix dispenses with the carriage return and makes due with the single newline character. Although the tools are getting better, Unix style files may show up as one long line in Windows -- not a single carriage return/newline pair in that file, must be a single line. Likewise, Windows style files will sometimes show up on Unix with garbage characters at the end of a line -- that extra carriage return is meaningless under the Unix convention.

This doesn't matter much for Java files -- it's all white space to the Java compiler. But some native Unix programs care passionately about those funny characters at the end of a line. In particular if you use a Windows based tool to edit a Unix script and your tool adds carriage returns to the script file, you have screwed it up. The script will no longer run. Worse, since many Unix editors do now handle the carriage returns, you could look at the broken script and see nothing wrong.
1) You need a Linux box

If you are doing significant development for Unix, you owe it to yourself and your customers to know something about Unix. If all else fails, get yourself an old PC and some of that free Linux. Or get yourself one of the many bootable Linux-on-a-CD distributions and try it out on any machine. Java is nearly platform independent, but not quite. It is up to you to make up the difference.

---

### Post by LordHunter317 on 2006-06-27
This guy makes some mistakes:

The headless comment is rather poor.  The consoles streams are always connected; if no output is desired, they're redirected into oblivion.  One should always output proper notification on the console and assume the user will remove it if it is undesired.  The only time that rule is changed is when there is an expectation the logs go elsewhere (e.g., a system daemon logs to syslog); the number of Java applications that have to worry about this are precious few.

He's completely and totally wrong about 7.  Several Unicies have registry-equivalents, though not as much information is stored there (usually applicaiton configuration data is not, but system and hardware configuration is).  AIX ODM is the classical example.  Anyway, there are registry-like tools for application configuration, gconf being the most common example.

He's wrong about daemons not being special.  Daemons are special in the sense they have to make special calls to outlive the life of the terminal.  He is correct in the sense that any application can call them.

He's wrong about shells not handling special characters well anymore.  GNU bash and all the shells after it handle special characters just fine.

---

### Post by demonhunter on 2007-04-23
We must remember that SWING applications will present an old but that dead keys will be harder than hell to be inputed...

I'm talking about keys like " ' ~ ^...

this is an old java bug.

---

### Post by Engnome on 2007-04-23
0) File names are case sensitive.

---

