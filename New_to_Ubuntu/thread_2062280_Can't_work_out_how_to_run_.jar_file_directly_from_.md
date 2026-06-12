---
title: "Can't work out how to run .jar file directly from USB music player in Ubuntu  12.04"
date: 2012-09-24
forum: New to Ubuntu
---

### Post by niccolo on 2012-09-24
Hi,

It's probably a simple fix, but since moving to 12.04, I can't work out simple shortcuts to home folders from media/disk,  that I can navigate to easily from the Terminal. I want to run NW-E00X_MP3_File_Manager-0.17a.jar which is an open source program to copy and manage music on an old Sony USB mp3 player.It needs to be an executable to run, or run from Terminal using SUDO I guess, but can't either select executable through the GUI or navigate to media through Terminal, nor set up a shortcut to media within the home or desktop folders.


Should I run Nautilus with super user/root privileges and set-up a link or can i make the file executable through this route?


Any thoughts? 

Cheers!

---

### Post by drmrgd on 2012-09-24
I'm not sure I entirely followed what you want.  It sounds like you simply want to make the .jar file executable.  If that's the case, you can either right click on the file and from the properties menu check the box that says make executable.  Or, from the terminal, just navigate to the file's location and run:

```
chmod +x NW-E00X_MP3_File_Manager-0.17a.jar
```

Depending on where you downloaded it, you may need root privileges to do this, but I'm guessing that's probably not going to be the case.  

Then to run the file, you can (from the terminal), run:

```
java -jar /path/to/file/NW-E00X_MP3_File_Manager-0.17a.jar
```

And it should run.  I'm not sure how the java script works.  Post back any errors you get, or I totally misunderstood what you're after, and we'll sort it out from there.

---

### Post by agillator on 2012-09-24
I believe you do not need to make the file executable. A jar file is actually a data file for the java program - that's what needs to be executable. The command above is the correct command to run that jar file. You can set up a desktop launcher to run it also by entering that command in the command box of the launcher setup.

---

### Post by drmrgd on 2012-09-24
I thought that might be the case.  I don't remember ever making a .jar file executable.  Thanks for the clarification!

---

### Post by niccolo on 2012-09-25
Thanks drmrgd

The problem is it won't let me make the file executable by clicking in properties (it unchecks the box immediately) or navigate to any root folder on terminal, only the home directory. 

This wasn't a problem in 11, but since going to 12.04 it seems to be different on root privileges.

---

### Post by 0011235813 on 2012-09-25
> **niccolo said:**
> Thanks drmrgd

The problem is it won't let me make the file executable by clicking in properties (it unchecks the box immediately) or navigate to any root folder on terminal, only the home directory. 

This wasn't a problem in 11, but since going to 12.04 it seems to be different on root privileges.
If you can't navigate  to a root folder in the terminal, you need to make yourself root, run;
```
sudo -i
```
to open a root shell. If you STILL can't navigate to root owned folders, then you may have a permission problem on your hands.

---

### Post by agillator on 2012-09-25
If you are trying to make a jar file executable, don't worry about it. The jar file need not be, and probably shouldn't be, executable. It is only a data file. Actually it is a special compressed file (zip format, I believe) to be accessed by java itself. That's all it is and all it needs to be. When you run java, the -jar option tells it to use the named jar file and java takes it from there. If java complains of permission problems then that is a different story. The permission(s) at fault are NOT the executables, but the read permission(s).

---

### Post by 0011235813 on 2012-09-26
> **agillator said:**
> If you are trying to make a jar file executable, don't worry about it. The jar file need not be, and probably shouldn't be, executable. It is only a data file. Actually it is a special compressed file (zip format, I believe) to be accessed by java itself. That's all it is and all it needs to be. When you run java, the -jar option tells it to use the named jar file and java takes it from there. If java complains of permission problems then that is a different story. The permission(s) at fault are NOT the executables, but the read permission(s).
I don't know... I've had some programs that do ask to be executable. Krut for example, doesn't run if it isn't made executable.

---

### Post by agillator on 2012-09-26
More than a little interesting. I have never had a jar file need to be executable. I am not aware of Krut, so I went to its site and from the instructions, limited though they are, it certainly appears they think the jar file itself doesn't need to be executable. Are you sure it is the jar file that needs to be executable, or could it be something else such as java itself or a directory that needs the executable bit set so you or the program can get into it, or something else? I'm certainly not saying you are wrong, just that this is something I have never seen before.

---

### Post by 0011235813 on 2012-09-27
> **agillator said:**
> More than a little interesting. I have never had a jar file need to be executable. I am not aware of Krut, so I went to its site and from the instructions, limited though they are, it certainly appears they think the jar file itself doesn't need to be executable. Are you sure it is the jar file that needs to be executable, or could it be something else such as java itself or a directory that needs the executable bit set so you or the program can get into it, or something else? I'm certainly not saying you are wrong, just that this is something I have never seen before.
```

The file '/home/<snip-username>/Software/Ubuntu-BB Linux Package/KRUT.jar' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.

```
That's what I get when I try opening it with OpenJDK Java Runtime. It works fine when it is executable.  Try running "Krut.jar" yourself without making it executable.

---

### Post by agillator on 2012-09-27
OK, I downloaded and unzipped krut. I am using the Oracle java and you obviously are using OpenJDK. When I run krut through Oracle java I have no problem. It opens and runs fine. It doesn't matter whether I have the system set up to use Oracle java runtime to run jar files or manually run the java runtime with the -jar option. So, I am wondering if it doesn't have something to do with OpenJDK. Do you have this problem with any other jar files? I also assume that you are set up to automatically run a jar file with the OpenJDK runtime if you double click the jar file as it appears you are. 'Tiz a puzzlement. If you are not having a similar problem with other jar files and there is nothing odd about your installation of OpenJDK, you might kick the problem up to both the krut programmers and to the OpenJDK folks. Don't be surprised if they both don't say CND (cannot duplicate) but it might be worth a try.

ADDED: I went back and tried to run KRUT.jar from the command line. With the x bit unset I got 'permission denied' as expected and then with sudo I got a 'command not found' as expected. Then, setting the x bit, I got 'invalid file (bad magic number): Exec format error' both normally and with sudo, again as expected.

---

### Post by 0011235813 on 2012-09-28
> **agillator said:**
> OK, I downloaded and unzipped krut. I am using the Oracle java and you obviously are using OpenJDK. When I run krut through Oracle java I have no problem. It opens and runs fine. It doesn't matter whether I have the system set up to use Oracle java runtime to run jar files or manually run the java runtime with the -jar option. So, I am wondering if it doesn't have something to do with OpenJDK. Do you have this problem with any other jar files? I also assume that you are set up to automatically run a jar file with the OpenJDK runtime if you double click the jar file as it appears you are. 'Tiz a puzzlement. If you are not having a similar problem with other jar files and there is nothing odd about your installation of OpenJDK, you might kick the problem up to both the krut programmers and to the OpenJDK folks. Don't be surprised if they both don't say CND (cannot duplicate) but it might be worth a try.

ADDED: I went back and tried to run KRUT.jar from the command line. With the x bit unset I got 'permission denied' as expected and then with sudo I got a 'command not found' as expected. Then, setting the x bit, I got 'invalid file (bad magic number): Exec format error' both normally and with sudo, again as expected.
I've had similar results with other .jar files(SweetHome for one).  Evidently, it must be an OpenJDK problem, I haven't been bothered to download java from oracle since I rarely use Java programs and don't want to fiddle with it.  Maybe there is a bug report about this? I'll have to check.

I'm not sure what you mean at the end-  have you tried running JDK from the CLI without executable permissions set?

---

### Post by agillator on 2012-09-28
The last 'added' bit was just saying I had tried to run the file as if it were an actual runnable file, ignoring java itself, to see what would happen. Results were as expected.

---

### Post by 0011235813 on 2012-09-28
> **agillator said:**
> The last 'added' bit was just saying I had tried to run the file as if it were an actual runnable file, ignoring java itself, to see what would happen. Results were as expected.
Ah yes, I get it now.
It seems OpenJDK wants jre's to be executable and not Oracle java. How strange... Well, people should mention what java their using- I assumed OP was using JDK, since that is what is included by default in Ubuntu.

---

### Post by agillator on 2012-09-28
I think you are right, but it makes no sense to me. A jar file a set of data files which has been compressed. It is never executed. The individual files in the jar file are never executed. That's why a java runtime is needed in the first place. But that is certainly above my pay grade. Since you use OpenJDK, though, it might be interesting to ask them.

---

### Post by niccolo on 2012-09-29
Thanks for all the comments, it's been interesting to follow.

Am I right in thinking it's partly down to which Java package I have installed then?

---

### Post by agillator on 2012-09-29
It appears so, although until this conversation I would not have thought so.

---

