---
title: "Concerned:  .EXE and .COM files try to execute on Ubuntu ..."
date: 2014-06-03
forum: New to Ubuntu
---

### Post by cwmoser on 2014-06-03
I'm concerned about potential Windows viruses on my Ubuntu 14.04.

I was playing around with some Windows utilities that were on my Ubuntu hard drive.

I went to the command prompt and found that *.com and *.exe files try to execute on my system.

For example ...
$  ./rkill.com
$  ./tdsskiller.exe

... both try to execute.  
(I did have to add execute permissions via **chmod u+x *** )

Now I am concerned that a potential virus could get on my system.

I'm assuming wine or Crossover is being utilized to run these programs.
Would you think this is a problem?

Carl

---

### Post by Vladlenin5000 on 2014-06-03
Emulators can run virus or malware designed for the OS those emulators emulate and it can affect their containers but that's it. It shouldn't affect your Ubuntu.

---

### Post by monkeybrain20122 on 2014-06-03
Those wouldn't run with those commands that you posted. You may be able to run an .exe file with WINE but you have to install WINE first and not by running ./foo.exe
So not to worry.

---

### Post by cwmoser on 2014-06-03
> **monkeybrain20122 said:**
> Those wouldn't run with those commands that you posted. You may be able to run an .exe file with WINE but you have to install WINE first and not by running ./foo.exe
So not to worry.

I've get wine and Crossover installed.
Did not have to run **$ wine ./rkill.com**
Just:  **$ ./rkill.com**

---

### Post by cwmoser on 2014-06-03
I don't like the possibility of a Windows virus getting in my wine containers.

Now I did have to set the execute bit for those two files ... so, if I clicked on 
a .EXE file in some email attachment or on some
website, is that file prevented from running because the execute bit
is not set by default when the file is created by the Ubuntu OS?

---

### Post by monkeybrain20122 on 2014-06-03
Well I am not sure what kind of advice you hope to get here. If you suspect that these may be viruses why did you run them in the first place? I doubt that WINE HQ keeps a compatibility list for Windows viruses so there is no way to tell if these things actually executes or not by checking WINE's listings. But since most Windows software doesn't run very well under WINE you may be ok.

---

### Post by 3rdalbum on 2014-06-04
Correct, the execute bit will not be set on any emailed attachments or anything on a non-Windows-formatted disk. So the files won't immediately be runnable by double-clicking them or choosing "Open" in your email client 

Viruses will generally just crash on Wine anyway, even if you explicitly run them. Wine doesn't simulate Windows close enough.

---

### Post by cwmoser on 2014-06-04
> **monkeybrain20122 said:**
> Well I am not sure what kind of advice you hope to get here. If you suspect that these may be viruses why did you run them in the first place? I doubt that WINE HQ keeps a compatibility list for Windows viruses so there is no way to tell if these things actually executes or not by checking WINE's listings. But since most Windows software doesn't run very well under WINE you may be ok.

No, no.  I did not *suspect* that these two commands were viruses.  Instead those two
commands are tools I am familiar with.  What I was doing was to see if *any* .EXE file
could be executed from the command line -- and apparently Ubuntu automatically pulls
in wine to run the command, that is if the execute bit is set.

It looks like our primary defense is that the Ubuntu OS will not set the execute bit when say an
email file attachment is double clicked on in which the OS first a) download the file and then b) execute the file.
Part b) cannot execute because Ubuntu protects us by not setting the execute bit.
That is my understanding now from reading the comments to my concern.  Good Linux security.

Carl

---

### Post by stalkingwolf on 2014-06-04
my "primary defense " is to have clamtk installed and up to date . just incase.

---

### Post by mcduck on 2014-06-04
Well, the best defence is to not have Wine in the first place. ;)

Just like any other Windows programs, Windows viruses might work with varying results when executed with Wine. Of course they will still be limited to the environment set by Wine, and by all the normal user permission restrictions Linux has, so even in worst case the damage is likely to be smaller than in Windows, but in the end if you install a tool that tries to provide as much compatibility with Windows executables as possible that's exactly what you are going to get.

---

### Post by buzzingrobot on 2014-06-04
It's not clear what you meant by 'try to execute', but, setting the execute bit tells the shell the file is executable, so it will happily treat the file as such. Presumably, any attempt to launch such a Windows executable will immediately fail. An OS expects to see executable files constructed in particular ways, and the files expect to find specific resources available in the OS. 

If I was using a Linux system on a Windows network, I'd run an AV to try to scrub Window malware attached to email before I forwarded it to my Windows-using co-workers, just to be polite.  Otherwise, I would not, and do not.

However, I'd run an AV, too, if I ran Windows programs in Wine and received mail from Windows systems, which is a near certainty.

---

### Post by cwmoser on 2014-06-04
I did a test and put up a sample hyperlink that hides a .EXE file on a website. 
The file was named **ccsetup317.exe**. 
When I click on the hyperlink, the following image shows what happens:

[[IMG]http://i1243.photobucket.com/albums/gg550/cwmoser/Selection_018_zpsc7821285.jpg[/IMG]](http://s1243.photobucket.com/user/cwmoser/media/Selection_018_zpsc7821285.jpg.html)


Apparently the default is to **Save File**.
When I select **OK**, the file is saved without the execute bit on the Desktop.

If I try to execute the file, I get Permission denied.

If I had selected **Open with**, my Crossover application would have executed it in a wine container.
Now no protection, the execute bit will not protect us now, the .EXE file will get executed anyway -- but within a wine container.

So I need to be observant and make sure I don't select **Open with**.



It is kinda interesting that I can go to the Terminal command prompt, enable the execute bit,
and execute this command like this:  
**$  ./ccsetup317.exe**

Carl

---

### Post by buzzingrobot on 2014-06-04
Windows has no notion of something like a Unix/Linux permission, since permissions are attributes of a Unix/Linux filesystem. If a file ends in ".exe", Windows assumes it is executable. 

Wine/Crossover aren't going to know about the permission, either, since they create an artificial Windows environment and articifial Windows file system, and you're seeing that in your tests.

---

### Post by cwmoser on 2014-06-04
> **buzzingrobot said:**
> It's not clear what you meant by 'try to execute', but, setting the execute bit tells the shell the file is executable, so it will happily treat the file as such. Presumably, any attempt to launch such a Windows executable will immediately fail. An OS expects to see executable files constructed in particular ways, and the files expect to find specific resources available in the OS. 
...


I think my Crossover is associating itself with **.exe **and **.com** files rather than letting Linux
try to execute and fail trying to execute the Windows executable file.

If this is so, then how is Crossover doing this?  
Wonder if there is a way to disable this?

Carl

---

### Post by cwmoser on 2014-06-04
> **buzzingrobot said:**
> Windows has no notion of something like a Unix/Linux permission, since permissions are attributes of a Unix/Linux filesystem. If a file ends in ".exe", Windows assumes it is executable. 

Wine/Crossover aren't going to know about the permission, either, since they create an artificial Windows environment and articifial Windows file system, and you're seeing that in your tests.

Then why is it that I can execute that Windows file from the Linux Terminal command prompt - like this:
**$  ./ccsetup317.exe**

Carl

---

### Post by oldos2er on 2014-06-04
Are you sure that's a Windows file? What does ```
file ccsetup317.exe
``` say?

---

### Post by cwmoser on 2014-06-04
carl@klaatu-2:~/Desktop$ [B]file ccsetup317.exe
ccsetup317.exe: PE32 executable (GUI) Intel 80386, for MS Windows, Nullsoft Installer self-extracting archive[/B]

Here is what it looks like when I execute ccsetup317.exe:

[[IMG]http://i1243.photobucket.com/albums/gg550/cwmoser/Selection_019_zps63bc62e1.jpg[/IMG]](http://s1243.photobucket.com/user/cwmoser/media/Selection_019_zps63bc62e1.jpg.html)

ccsetup317.exe runs and installs successively under ~/.wine and places a CCleaner icon on my Ubuntu desktop.
I'm pondering about the potential for a Malware to enter via Wine and work its way into doing something
harmful with the Ubuntu Linux OS.

---

### Post by buzzingrobot on 2014-06-04
Well, as just a guess, something is recognizing the file as a Window executable and passing it on to Wine for execution. 

I just downloaded ccsetup from the CCleaner site.  Trying to execute it in a terminal produces a permission denied error.  Setting the execute bit and running it produces "cannot execute binary file: Exec format error", i.e., the kernel doesn't recognize the file's format. (14.04, no Wine, Crossover).

---

### Post by cwmoser on 2014-06-05
> **buzzingrobot said:**
> Well, as just a guess, something is recognizing the file as a Window executable and passing it on to Wine for execution. 

I just downloaded ccsetup from the CCleaner site.  Trying to execute it in a terminal produces a permission denied error.  Setting the execute bit and running it produces "cannot execute binary file: Exec format error", i.e., the kernel doesn't recognize the file's format. (14.04, no Wine, Crossover).

So, you do not have Wine or Crossover installed?
And, you did try to execute ccsetup from the Linux Command prompt and like this:  **$  ./ccsetup.exe **  ???

I do have Wine and Crossover installed on my Ubuntu PC.
Apparently there is some configuration to Linux on my copy of Ubuntu that allows the command prompt
to identify **.exe** and **.com** files and pass them on to Wine for execution.  
Wonder how this is done?

Carl

---

### Post by buzzingrobot on 2014-06-05
> **cwmoser said:**
> So, you do not have Wine or Crossover installed? 

Nope.

> And, you did try to execute ccsetup from the Linux Command prompt and like this:  **$  ./ccsetup.exe **  ??? 

Yep.

---

### Post by monkeybrain20122 on 2014-06-05
> **cwmoser said:**
> 
I do have Wine and Crossover installed on my Ubuntu PC.
Apparently there is some configuration to Linux on my copy of Ubuntu that allows the command prompt
to identify **.exe** and **.com** files and pass them on to Wine for execution.  
Wonder how this is done?

Carl

I think it is the same mechanism that allows you to right click to run an .exe if you have Wine installed. The mime type for .exe is automatically associated with Wine so it will run if you set the execution bit and right click.

I see what you are talking about now. So you are worrying that this will bypass Linux's security mechanism and that these would run automatically? But this is not just for .exe files in Wine, any script with the execution bit set runs in your home without password too. An .exe file running under Wine this way can mess with your /home but can't touch your system files.

---

### Post by matt_symes on 2014-06-05
Hi

> An .exe file running under Wine this way can mess with your /home but can't touch your system files.

If i remember correctly, you can also lock wine down just to the wine directory so it will not have access outside of that directory and will not be able to affect other parts of you home directory, using the wine configuration tool.

I will admit though, it's been a long, long time since i used wine and i have no experience with crossover.

I'm pretty sure you can lock wine down in other ways as well, such as apparmor maybe ?

Kind regards

---

### Post by The Cog on 2014-06-05
I will talk of wine, but I gather from this thread that crossover is the same.
If you install wine then the file manager will know that .exe files can be opened with the application wine. I know that wine will not run a .exe unless it has the executable bit set. Wine is the bridge between windows executables and the linux OS, so of course it is well aware of linux's permissions system etc. 

The default configuration in wine is to allow exes access to the entire linux filesystem by mapping / to Z:. This means that any malware could access any file the user has access to, and if it's smart, it could make up aliases for commands, add programs (maybe itself) to the user's session startup, read all the user's emails etc. So it could do anything that native linux malware could do. 

And wine is getting better at running windows executables, malware included. Fortunately, I don't think there are any windows exes around yet that are able to recognise that they are running in wine and to take advantage of that. But I imagine the day will come.

---

### Post by Mark Phelps on 2014-06-05
> they are running in wine

Wine is NOT an Emulator -- that's what W.I.N.E. stands for.

Stuff doesn't run IN Wine or Under Wine; instead, Wine is a collection of rewritten DLLs in which Windows OS system calls have been replaced by Linux OS system calls.

The Windows app makes a real-time call to a DLL (run time library) to invoke a function, and since the DLL filename, and the embedded function name, both have to be the same as the actual Windows DLL file, I don't see how the app could know that the DLL has been rewritten.

---

### Post by monkeybrain20122 on 2014-06-05
> **The Cog said:**
> 
The default configuration in wine is to allow exes access to the entire linux filesystem by mapping / to Z:. This means that any malware could access any file the user has access to, and if it's smart, it could make up aliases for commands, add programs (maybe itself) to the user's session startup, read all the user's emails etc. So it could do anything that native linux malware could do. 


I usually change that mapping when I install Wine, but I don't think malware can access / (or Z) unless you run it with sudo, the usual permission hierarchy still applies. I guess there may be some use cases where one may want a Windows application to access the file system, hence the mapping of / to Z, but running Wine with sudo is in general a bad idea IMO.

---

