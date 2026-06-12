---
title: "[SOLVED] Could somene help me with some issues in jgrasp?"
date: 2007-11-02
forum: Programming Talk
---

### Post by TheOrangePeanut on 2007-11-02
First, I get this message everytime I start jgrasp:

[I]Default system character encoding uses multi-bye characters or is not one-to-one.

Currently, jgrasp CSD windows can not handle such encodings.

ISO8859-1 (Latin-1) encoding will be used.

Character display, printing, I/O, and cut-and-paste behavior may not be as expected.[/I]

Does anyone know what this means or how to fix it?  

Secondly, when I try to debug I get this error message and debugging doesn't work:[I]

It appears you are running jgrasp under the JRE (not JDK), or a version of Java that does not support integrated debugging.

If you have the full JDK installed, you may need to change your PATH to correct this.  You can also set a 'JGRASP_JAVA' environment variable to force jgrasp to use a particular Java version[/I]

I don't know how to change my PATH or set an environment variable.  How can I get jgrasp to debug my programs?

I've installed the JRE and JDK (both 1.6) from Synaptic.  Can anyone help?  This was my IDE of choice in Windows because of it's simplicity but also because it has a GREAT visual debugger that I find very useful when I'm making trees.  If anyone could help that'd be wonderful :guitar:

---

### Post by TheOrangePeanut on 2007-11-03
Bump

---

### Post by TheOrangePeanut on 2007-11-04
Anyone?

---

### Post by sillv0r on 2007-11-04
> **TheOrangePeanut said:**
> 
Secondly, when I try to debug I get this error message and debugging doesn't work:[I]

It appears you are running jgrasp under the JRE (not JDK), or a version of Java that does not support integrated debugging.

If you have the full JDK installed, you may need to change your PATH to correct this.  You can also set a 'JGRASP_JAVA' environment variable to force jgrasp to use a particular Java version[/I]

I don't know how to change my PATH or set an environment variable.  


Yes, to solve the debugging problem it looks like you need to tell it where to find the JDK you have installed.

If you need help in setting environment variables then what operating system are you using?

EDIT: In my shell on Ubuntu 7.10 simply typing $PATH will show defined paths.  (You can edit this but be sure not remove anything you don't know about.) ;d

This installation help doc seems to talk a bit about setting up the compiler based on specific installations...

[http://www.jgrasp.org/tutorials18/01_Installing.pdf](http://www.jgrasp.org/tutorials18/01_Installing.pdf)

Having never used jgrasp before, I can't give a definitive answer to your questions.  It looks like the site has some good documentation.

---

### Post by TheOrangePeanut on 2007-11-04
This is what the help file says as far as the integrated debugger goes:

*For both the Windows and UNIX/Linux startup programs, to use the integrated Java debugger, "java.exe" or "java" must be in the JDK directory structure (in /bin, where tools.jar is in /lib), unless the "-cp" command line argument or JGRASP_CLASSPATH environment variable is used.*

Well, I'm not sure where the JDK directory structure is.  Also, "java" is not in /bin and tools.jar is not in /lib.  I don't really know my way around Linux yet so I'm not even sure where to begin to get the integrated debugger working.  I can compile programs alright, but I have a very big project due in a couple of weeks and having the debugger working is a pretty big deal right now.

edit:
I'm using 7.10 Gutsy, btw.

---

### Post by sillv0r on 2007-11-04
Have you checked your compiler settings as described in the doc?

"...you may need to change the Compiler Settings by clicking on Settings->Compiler Settings -> Workspace.  Select the appropriate language, and then select the environment setting that most nearly matches the compiler you have installed..."

Maybe there are settings in there that will help.

Edit: Also, I'm curious as to if anything is already defined in JGRASP_CLASSPATH.  In a terminal, type the following to find the contents of that variable. "$JGRASP_CLASSPATH".
(I'd install it myself, except that I'm using a server installation with no window environment.)

---

### Post by TheOrangePeanut on 2007-11-04
I did check the compiler settings under compiler -> settings -> workspaces.  It, by default under Java, uses "jdk (integrated debugger, hotspot VM, prefer JDK compiler) - generic"

It seems to me like that should be the correct setting, but the integrated debugger still gives that same error message.  Also, $JGRASP_CLASSPATH has nothing in it.

Any ideas?

---

### Post by sillv0r on 2007-11-04
Okay,

What about in "Settings-> JGrasp Default settings"

Have a looksie in there if you havn't and make sure that it's pointing to the jdk versus the runtime.

And it presently compiles and runs fine, correct?  (excluding debug)

---

### Post by TheOrangePeanut on 2007-11-04
There is no menu option in settings for default jgrasp settings.  There is a "settings -> jgrasp debugger settings" but I don't think it is what I'm looking for.

[http://img.photobucket.com/albums/v258/TheOrangePeanut/debug.png](http://img.photobucket.com/albums/v258/TheOrangePeanut/debug.png)

I've tried rooting around the menu's to see if jgrasp is pointing to the JDK or JRE but everything I've seen looks as if it is already pointing to the JDK.  Unfortunately, I can't be entirely sure because I'm not even sure where the JDK and JRE are located in the Linux file system.

And yes, compiling works fine except for the debug problem.

---

### Post by TheOrangePeanut on 2007-11-05
Bump

---

### Post by sillv0r on 2007-11-05
> **TheOrangePeanut said:**
> 
And yes, compiling works fine except for the debug problem.

Hrms.

See if this helps:

[http://www.cs.usm.maine.edu/~welty/cos160/JgraspOnlineTutorial/](http://www.cs.usm.maine.edu/~welty/cos160/JgraspOnlineTutorial/)
EDIT: look towards the bottom.

---

### Post by TheOrangePeanut on 2007-11-05
I'm not sure what I'm supposed to get from that.  The only thing I see about setting up the debugger is having debug checked off under compiler settings, but that has been checked since I've had the program installed.  I did a whereis on javac and jdb (jdb is the command line java debugger, I don't know if jgrasp uses it though) and both of them are in /usr/bin.  My $PATH variable has an entry for /usr/bin so if jgrasp does use jdb then I'm not sure why it isn't working?

Any more ideas?  I'd use Eclipse, but frankly it is a huge mess that I don't want to mess with.  It's too complicated for my purposes (says the guy who can't set up the "simple" IDE).

---

### Post by TheOrangePeanut on 2007-11-06
I ended up emailing the support email listed on Jgrasp's website.  I suppose I should have done that sooner.

Larry Barowski, the lead programmer, emailed me back within only a matter of hours.  He explained that java, javac, and jdb were being called from /usr/bin which were symbolic links to the actual executables.  However, jgrasp should be pointed to the path of the actual executables to have access to the libraries associated with debugging.  I added the JDK path (which I found through "file javac" commands and followed the symbolic links) to the beginning of my $PATH variable, fired up jgrasp and sure enough the debugger is working now.  Thanks a lot Larry!

In summary, how to get the debugger working with JDK 1.6 installed through Synaptic:

Add /usr/lib/jvm/java-6-sun/bin to your $PATH directory.  Do this by putting the following two lines in your ~/.bashrc file.

PATH=/usr/lib/jvm/java-6-sun/bin:$PATH
export PATH

Logout, log back in, and voila!  You have a debugger in Jgrasp!

---

### Post by sillv0r on 2007-11-07
Congrats.

Mark the thread as solved. pls.

---

### Post by dkaplowitz on 2008-06-21
Glad to hear you got the debugger thing fixed. I'm actually looking for a fix to the ``default encodings'' warning that comes up. I'm noticing that I can't do the select/paste into jgrasp from a terminal like I can with any other Linux app. Thanks for any ideas about fixing that. Google's not given me much yet.

---

