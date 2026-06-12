---
title: "How to run a &quot;.bat&quot; file then &quot;.sh&quot; in Wine"
date: 2015-03-27
forum: New to Ubuntu
---

### Post by mark208 on 2015-03-27
Hello,

Very new to Ubuntu...and like it so far.  I have v12 installed.  Presently, I am using it to maintain and modify my hp touchpad.  So, I was going through some instructions found on xda to reinstall webos.  I got down to the final step and am stuck.

The touchpad is connected to the pc via usb during this process.

The final step has two parts.
1) to run "palmenv.bat"

I was able to run the above ".bat" file after installing wine.  When in the terminal, I wrote "wine cmd", it changed to drive from something to "Z.".  So, all looked good at this point.

2) the next step was to run "novacom run file:///bin/sh < fix-webOS-certs.sh" file.  

Typing this in the"Z" location the file could not be found.  After finally moving the file to a place where it could be found, it would not execute it.

So, here are my questions.
1) Can I change the above ".bat" file to run in Ubuntu without Wine?  If so, do I then need to do anything to the .sh file?
2) If I need to stay in Wine, since it appears I was able to get the "bat" file to run, how do I go about getting the "sh" file to run?
Thanks

---

### Post by TheFu on 2015-03-27
You need a little more background to avoid frustration.  WINE/Windows uses drive letters. *nix OSes do not.

I don't really understand what you want, but if you want to call other scripts/programs, then just write the things you type into a file and call that top-level script which controls the other program calls.  That is all a shell script is - the same things you'd type, put into a file.  *nix doesn't care about file extensions. File permissions control if something is executable or not. Using non-*nix file systems makes that harder (i.e. NTFS, vFAT/FAT32).

Don't know if environment variables are passed from Linux into WINE. If the program is a Windows program, then you must use WINE. If the program is not Windows, you just need to find the native Linux equivalent tool.

If you'll spend about 2-3 hrs doing a little background reading, lots of things will click so this stuff isn't so hard. The first 4 bullets here have links to help provide that background:  [http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux)

---

### Post by mark208 on 2015-03-27
Thanks for the reply.  Here is what I am referencing in case it was unclear. Ref here step 7d: [URL="http://forum.xda-developers.com/showthread.php?t=2756314&page=7"]http://forum.xda-developers.com/show...2756314&page=7   
[/URL]
Anyway, I have asked a similar question on that site, but I thought it may be a much easier question to answer on the Ubuntu site.  Apparently, that is not the case.  For me it boils down to how to run a ".bat" then run a ".sh" in ubuntu.  Wine got me to run the bat file, but I could not run the sh file.  Hence the question.  Conversely, I could run the bat file in windows 7, but did not know how to run the sh file.  All of this is while the touchpad is connected to the pc.  I'll see if the other site can help.

---

### Post by TheFu on 2015-03-27
I took a look at those instructions - they aren't clear to me which commands need to be run in DOS and which inside the Linux host. If the palmenv.bat command opens a shell on the tablet, then you can't do it by running shell commands on your Linux host. You'll want to use something like Expect to send commands through the terminal to another process. 

In case someone else can help, the exact instructions:
```

7) after webOS doctor has completed, and you get to the "select language" screen on webOS, here's how to fix the webOS certificates:
7a: download [http://goo.im/devs/jcsullins/cmtouch...ox/palmenv.bat](http://goo.im/devs/jcsullins/cmtouch...ox/palmenv.bat)
7b) download [http://goo.im/devs/jcsullins/cmtouch...webOS-certs.sh](http://goo.im/devs/jcsullins/cmtouch...webOS-certs.sh)
7c) open a "Command Prompt" and "cd" to where the palmenv.bat and fix-webOS-certs.sh files are located
7d) then run "palmenv" and then run "novacom run file:///bin/sh < fix-webOS-certs.sh"
8) finish setting-up webOS
9) then load tptoolbox again and select "Install Android"
```

novacom appears to be a webos command, not standard Linux and not DOS/Windows. That means you've just hopped from the host-Linux system, into WINE and across the usb connection to the webos machine. 
7c is a little vague about where those files are.  My DOS scripting-fu is weak - how do you bring environment variables into the current environment like a source or '.' works in bash/sh/dash?

---

### Post by mark208 on 2015-04-04
> **TheFu said:**
> I took a look at those instructions - they aren't clear to me which commands need to be run in DOS and which inside the Linux host. If the palmenv.bat command opens a shell on the tablet, then you can't do it by running shell commands on your Linux host. You'll want to use something like Expect to send commands through the terminal to another process. 

In case someone else can help, the exact instructions:
```

7) after webOS doctor has completed, and you get to the "select language" screen on webOS, here's how to fix the webOS certificates:
7a: download [http://goo.im/devs/jcsullins/cmtouch...ox/palmenv.bat](http://goo.im/devs/jcsullins/cmtouch...ox/palmenv.bat)
7b) download [http://goo.im/devs/jcsullins/cmtouch...webOS-certs.sh](http://goo.im/devs/jcsullins/cmtouch...webOS-certs.sh)
7c) open a "Command Prompt" and "cd" to where the palmenv.bat and fix-webOS-certs.sh files are located
7d) then run "palmenv" and then run "novacom run file:///bin/sh < fix-webOS-certs.sh"
8) finish setting-up webOS
9) then load tptoolbox again and select "Install Android"
```

novacom appears to be a webos command, not standard Linux and not DOS/Windows. That means you've just hopped from the host-Linux system, into WINE and across the usb connection to the webos machine. 
7c is a little vague about where those files are.  My DOS scripting-fu is weak - how do you bring environment variables into the current environment like a source or '.' works in bash/sh/dash?

Ok thanks.  It appears to be a mystery that is unsolved to this point.  Oh well.  Thanks.

---

### Post by steeldriver on 2015-04-04
The way I understand it:

[LIST]
[*]novacom is a Windows application for communicating with your touchpad device - it may or may not work under Wine (I could find no mention of it at winehq) 
[*]the .bat file just sets some Windows environment variables for novacom to run - it could probably be "converted" to a Linux shell script, but the results would likely be meaningless in the Linux environment 
[*]you don't need to "get the sh file to run": **you need to get novacom to run, under Wine, with the sh file as its input**. As far as the Windows/Wine cmd shell is concerned, fix-webOS-certs.sh is just a text file. 
[/LIST]

To make progress, you need to tell us exactly what error you get when you try to run the command

```

novacom run file:///bin/sh < fix-webOS-certs.sh

```

using wine cmd in the directory that **does** contain the fix-webOS-certs.sh file - do you actually have novacom installed under Wine? Have you checked to see if there's a native Linux version available?

---

### Post by mark208 on 2015-04-06
> **steeldriver said:**
> The way I understand it:

[LIST]
[*]novacom is a Windows application for communicating with your touchpad device - it may or may not work under Wine (I could find no mention of it at winehq) 
[*]the .bat file just sets some Windows environment variables for novacom to run - it could probably be "converted" to a Linux shell script, but the results would likely be meaningless in the Linux environment 
[*]you don't need to "get the sh file to run": **you need to get novacom to run, under Wine, with the sh file as its input**. As far as the Windows/Wine cmd shell is concerned, fix-webOS-certs.sh is just a text file. 
[/LIST]

To make progress, you need to tell us exactly what error you get when you try to run the command

```

novacom run file:///bin/sh < fix-webOS-certs.sh

```

using wine cmd in the directory that **does** contain the fix-webOS-certs.sh file - do you actually have novacom installed under Wine? Have you checked to see if there's a native Linux version available?

Hey thanks.

In windows, the error I'm getting is "unable to find the device" after I type in the .sh command.  The palmenv.bat file works as it is setting up for this .sh command.  PS:  The device is tethered to the pc.  It does show up in the device manager.

In linux, I have to run wine to get the bat file to run.  In wine, it sets up a new directory of "Z".  No matter how or where the .sh file is, I cannot get linux to find the file...even though I have given the exact correct address.  So, I'm thinking you can't run .sh file in wine.

I thought "wine" was only used to run a .bat file, so no, I did not specifically try to install or setup novacom in wine.  I don't know how if I need to.

Novacom can be used in windows, linux, and mac according to where this original procedure was taken from.  Apparently it is used to talk from the pc source to the hp touchpad in this case.

Well, I have asked a similar question on the forum where this whole procedure was obtained and there does not seem to be any good answers there.

I'm guessing, that the original procedure was written for windows application as the procedure calls out for a "command prompt", which more than likely is a windows term.  However, it was my understanding that the ".sh" file is a linux file, so I was a little confused as to how all of this worked.  Plus, the fact that there was another totally different procedure by the author that I used, where you had to use linux, and a particular build...hence, the reason why I thought this procedure of running a .bat file then the .sh file was also using linux.

I have given up at this point.  Whatever the method is to make this work is probably beyond my expertise anyway.

---

### Post by TheFu on 2015-04-06
Isn't webOS  Linux too?  Those .sh files are scripts, probably dependent on one of the common UNIX shell program - Bourne Shell, Korn Shell, or Bash.  It is going to look for specific programs to run and those are probably on WebOS - not Ubuntu.  The .bat program works the same way - it will try to invoke programs that run under DOS or Windows ...

These are just text files, so look at them to see which programs they each require. You'll need to install those under WINE if there is any hope this will work.  It may not work even if you do it due to the different ways that Linux and Windows deal with USB connections.

---

