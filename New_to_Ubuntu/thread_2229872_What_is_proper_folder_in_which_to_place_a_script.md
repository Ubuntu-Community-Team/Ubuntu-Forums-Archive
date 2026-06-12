---
title: "What is proper folder in which to place a script?"
date: 2014-06-15
forum: New to Ubuntu
---

### Post by twalp on 2014-06-15
A program that I'm interested in comes in two versions: FullVersion and SimpleVersion.

FullVersion comes with its own 32-bit Debian/Ubuntu installer. It runs from a bash script that is located in a subfolder of /opt.

```
path is **/opt/fullversion/fv_bin/script/fullversion**
```

SimpleVersion does not come with an installer but after uncompressing it the resulting folder structure is similar to that of FullVersion and it, too, runs from a bash script. I figured I could simply copy it from my Downloads folder to the /opt folder and change the existing FullVersion desktop shortcut to point to SimpleVersion's script. But when I double-click to run the modified shortcut nothing happens. 

So I changed the desktop shortcut to point to the original in the Downloads folder.

```
path is **/home/myusername/Downloads/simpleversion/sv_bin/script/simpleversion**
```

When I double-click on the desktop shortcut pointing to the script in the above path the program runs fine.

I assume the reason I couldn't run SimpleVersion from the /opt folder is a permissions issue.  **Where can I place the SimpleVersion folder so the script inside can be run from a desktop shortcut?** I'd rather not keep it in the Downloads folder permanently.

---

### Post by bab1 on 2014-06-15
> **twalp said:**
> A program that I'm interested in comes in two versions: FullVersion and SimpleVersion.

FullVersion comes with its own 32-bit Debian/Ubuntu installer. It runs from a bash script that is located in a subfolder of /opt.

```
path is **/opt/fullversion/fv_bin/script/fullversion**
```

SimpleVersion does not come with an installer but after uncompressing it the resulting folder structure is similar to that of FullVersion and it, too, runs from a bash script. I figured I could simply copy it from my Downloads folder to the /opt folder and change the existing FullVersion desktop shortcut to point to SimpleVersion's script. But when I double-click to run the modified shortcut nothing happens. 

So I changed the desktop shortcut to point to the original in the Downloads folder.

```
path is **/home/myusername/Downloads/simpleversion/sv_bin/script/simpleversion**
```

When I double-click on the desktop shortcut pointing to the script in the above path the program runs fine.

I assume the reason I couldn't run SimpleVersion from the /opt folder is a permissions issue.  **Where can I place the SimpleVersion folder so the script inside can be run from a desktop shortcut?** I'd rather not keep it in the Downloads folder permanently.

Typically these kinds of programs go in: /usr/local/share/  This is the directory for programs that are local to this machine only and not installed by default.  That being said you can place the program anywhere.  I have programs that run from /opt/<some_directory>.  As the system administrator (sudo)  you can change the ownership and permissions.  I'd leave the /opt directory as it is (root:root) for both permissions and ownership.  The trick is to allow eXecute permissions on all _**directories**_ in the path so the user has transit access along the entire path.

---

### Post by yancek on 2014-06-15
If it worked in Downloads, it should work anywhere in your /home/user directory.   The default permissions for the /opt directory:

> drwxr-xr-x   3 root root   opt


Make sure you have execute permissions set on the simpleversion script as well as the sub-directories of /opt.  Do you get any error message when you run the script from a terminal?

---

### Post by twalp on 2014-06-15
> **yancek said:**
> If it worked in Downloads, it should work anywhere in your /home/user directory.   The default permissions for the /opt directory:



Make sure you have execute permissions set on the simpleversion script as well as the sub-directories of /opt.  Do you get any error message when you run the script from a terminal?

Thank you for replying, yancek.

No error message is displayed when I run SimpleVersion in the path "**/opt/simpleversion/sv_bin/script/simpleversion**". Nothing happens, period.

When I run SimpleVersion in the path "**/home/myusername/Downloads/simpleversion/sv_bin/script/simpleversion**" the program runs. I assume this means that the script's execute permissions are set sufficiently, since I'm able to run it.

How do I give myself execute permissions to run it in /opt?  Note that the eventual end-user of this will have an account type of **Desktop User**, not Administrator.

Being a rank noob it seems to me that if I'm able to run FullVersion in path "**/opt/fullversion/fv_bin/script/fullversion**", don't I already have execute permissions there? For that matter, how did FullVersion's installer make it executable from /opt? It seems like I need to repeat whatever it did but for SimpleVersion.

---

### Post by twalp on 2014-06-15
> **bab1 said:**
> Typically these kinds of programs go in: /usr/local/share/  This is the directory for programs that are local to this machine only and not installed by default.  That being said you can place the program anywhere.  I have programs that run from /opt/<some_directory>.  As the system administrator (sudo)  you can change the ownership and permissions.  I'd leave the /opt directory as it is (root:root) for both permissions and ownership.  The trick is to allow eXecute permissions on all _**directories**_ in the path so the user has transit access along the entire path.

Thank you for offering to help, bab1. I'd read that /opt is where 3rd party programs should go, and since FullVersion's installer put FullVersion there it seems to me that I should be able to manually reproduce whatever it did (having already copied SimpleVersion's folder to /opt).  If Execute permissions are needed for the /opt path I'm puzzled why I'm able to run FullVersion from /opt but not SimpleVersion, but then I'm a moron in this subject.

---

### Post by bab1 on 2014-06-15
> **twalp said:**
> Thank you for offering to help, bab1. I'd read that /opt is where 3rd party programs should go, and since FullVersion's installer put FullVersion there it seems to me that I should be able to manually reproduce whatever it did (having already copied SimpleVersion's folder to /opt).  If Execute permissions are needed for the /opt path I'm puzzled why I'm able to run FullVersion from /opt but not SimpleVersion, but then I'm a moron in this subject.
By default /opt or directories below that are not in the execute path at all.  You would have to use absolute addressing.  In other words you could not use *program name* and expect the app to run,  You would need to use the absolute location, such as /opt/<directory>/program and the execute bit would need to be set on the *program* file as @yancek has said.

If you have setup the directory structure as this```
/opt/simpleversion/sv_bin/script/simpleversion
```...then you need to check the permissions down that entire directory path.  What do you get from this terminal command ```
ls -l /opt/simpleversion/sv_bin/script/
```

[COLOR="#0000FF"]I didn't answer your Full Version execute permission.  The most probable reason is the script changed the permissions along the path and made the program executable also.  We can check this easily if you wish.[/COLOR]

---

### Post by twalp on 2014-06-15
> **bab1 said:**
> By default /opt or directories below that are not in the execute path at all.  **You would have to use absolute addressing**.  In other words you could not use *program name* and expect the app to run,  You would need to use the absolute location, such as /opt/<directory>/program and the execute bit would need to be set on the *program* file as @yancek has said.

If you have setup the directory structure as this```
/opt/simpleversion/sv_bin/script/simpleversion
```...then you need to check the permissions down that entire directory path.  What do you get from this terminal command ```
ls -l /opt/simpleversion/sv_bin/script/
```

[COLOR=#0000FF]I didn't answer your Full Version execute permission.  The most probable reason is the script changed the permissions along the path and made the program executable also.  **We can check this easily if you wish**.[/COLOR]

The results of the list directory command you provided are below in the "code" box. Insofar as [COLOR=#0000ff]your text in blue[/COLOR] where you say "[COLOR=#0000ff]we can check this easily[/COLOR]", yes, please.  If the FullVersion installer made it executable, can I do the same thing to SimpleVersion?  But if "executableness" is an issue again I wonder how SimpleVersion is executable in the /Downloads path but not in the /opt path. Perhaps you will explain this to me.

Lastly, I don't know the meaning of "**absolute addressing**" in this context, so I can only stress that I am running the actual script in the folder where it resides; I am not attempting to use a Desktop shortcut to open SimpleVersion at this point.  Instead, I'm in the actual /script/ folder in both of the following paths when I right-click and Open the *simpleversion* script. An "Execute File" prompt appears offering an **Execute** and an **Execute in Terminal** option, and I click on **Execute**.

"**/opt/simpleversion/sv_bin/script/***simpleversion*" is the instance that works

"**/home/myusername/Downloads/simpleversion/sv_bin/script/***simpleversion*" is the instance that does not

Lastly, in case it's significant, in /opt/simpleversion/sv_bin/ there is a /wine/ folder at the same level as the /script/ folder in which resides the simpleversion script. So I assume Wine is being used in some way by both programs.

```
total 108
drwxr-xr-x 2 root root 4096 Jun 15 16:48 fontconfig
-rw-r--r-- 1 root root  187 Jun 15 16:48 fontsmooth_rgb.reg
-rwxr-xr-x 1 root root 5512 Jun 15 16:48 libdepend
-rw-r--r-- 1 root root  159 Jun 15 16:48 no_fileassocs.reg
-rw-r--r-- 1 root root   72 Jun 15 16:48 no_xrandr.reg
-rw-r--r-- 1 root root   74 Jun 15 16:48 no_xvidmodeext.reg
-rw-r--r-- 1 root root   90 Jun 15 16:48 setwinver.reg
-rwxr-xr-x 1 root root  360 Jun 15 16:48 simpleversion
-rw-r--r-- 1 root root  239 Jun 15 16:48 simpleversiond.DEB.conf
-rw-r--r-- 1 root root  921 Jun 15 16:48 simpleversiond.pp
-rw-r--r-- 1 root root  239 Jun 15 16:48 simpleversiond.RPM.conf
-rw-r--r-- 1 root root  359 Jun 15 16:48 simpleversiond.service
-rwxr-xr-x 1 root root 1895 Jun 15 16:48 simpleversiond.sysv
-rwxr-xr-x 1 root root 3971 Jun 15 16:48 simpleversion_setup
-rw-r--r-- 1 root root 2663 Jun 15 16:48 sv_aux
-rw-r--r-- 1 root root 1133 Jun 15 16:48 sv_config
-rw-r--r-- 1 root root 5235 Jun 15 16:48 sv_daemon
-rw-r--r-- 1 root root 5142 Jun 15 16:48 sv_exec
-rw-r--r-- 1 root root 6212 Jun 15 16:48 sv_extra
-rw-r--r-- 1 root root 4200 Jun 15 16:48 sv_main
-rw-r--r-- 1 root root 2856 Jun 15 16:48 sv_profile
-rwxr-xr-x 1 root root  936 Jun 15 16:48 wait-console-kit.sh

```

---

### Post by bab1 on 2014-06-16
> **twalp said:**
> The results of the list directory command you provided are below in the "code" box. Insofar as [COLOR=#0000ff]your text in blue[/COLOR] where you say "[COLOR=#0000ff]we can check this easily[/COLOR]", yes, please.  

If the FullVersion installer made it executable, can I do the same thing to SimpleVersion?  

Maybe.
> 
But if "executableness" is an issue again I wonder how SimpleVersion is executable in the /Downloads path but not in the /opt path. Perhaps you will explain this to me.

A script becomes executable if the eXecute bit is set.  An example of the eXecute bit set on a script is below in red.

It has nothing to do with where it is.  What you are referring to as a path is really addressing.  Absolute addressing locates the file from its root position of / (e..g. /home/yourusername/Downloads/<some_script.sh>)  relative addressing is just that, relative to what is your current working directory.  If you are at your home directory then the script is relatively addressed as: Downloads/<some_script.sh>.  If you were in the Downloads directory then the relative address is: <some_script.sh>

The bits for the owners (root:root:others) can be seen as: rwxr-xr-x.  The owner is the first set of 3 bits (rwx) and that owner is *root * and the user can read, write and eXecute the script.  The group owner is a group named *root* and all in that group have read and eXecute permissions.  The last is *others *users on the system and they also have read and eXecute permissions.  The lowest common denominator is the *others* group.  It really means all users can eXecute the script.  

It appears that the script in question is executable.  Since you are using the GUI to run these scripts you are navigating to the directory in question (and thus making the directory in question the current working directory) and executing the script.  If you get NO ERRORS then the script has been executed. If you had a permissions problem you would get an error.  If you tried to execute a script that did not have the execute bit set you also would get an error.  What we don't know is what the script is actually doing.

> 
```
total 108
...
-[COLOR="#FF0000"]rwxr-xr-x [/COLOR]1 root root  360 Jun 15 16:48 [COLOR="#FF0000"]simpleversion[/COLOR]
...
-rwxr-xr-x 1 root root  936 Jun 15 16:48 wait-console-kit.sh

```
Lastly, I don't know the meaning of "**absolute addressing**" in this context, so I can only stress that I am running the actual script in the folder where it resides; I am not attempting to use a Desktop shortcut to open SimpleVersion at this point.  Instead, I'm in the actual /script/ folder in both of the following paths when I right-click and Open the *simpleversion* script. An "Execute File" prompt appears offering an **Execute** and an **Execute in Terminal** option, and I click on **Execute**.

"**/opt/simpleversion/sv_bin/script/***simpleversion*" is the instance that works

"**/home/myusername/Downloads/simpleversion/sv_bin/script/***simpleversion*" is the instance that does not

... in case it's significant, in /opt/simpleversion/sv_bin/ there is a /wine/ folder at the same level as the /script/ folder in which resides the simpleversion script. So I assume Wine is being used in some way by both programs.

Is this a Windows program?  Do you have Wine installed?  I'm only concerned with the script that you say launches the program.  I assume it is either a Bourne Shell script or a Bash Shell script.  Those do not need Wine to eXecute.

Let's look at the script itself.  Post the entire output of this command.  You may have to scroll back for all the data ```

cat /opt/simpleversion/sv_bin/script/simpleversion
```

I assume the script in */home/myusername/Downloads/simpleversion/sv_bin/script/ * is the same, but we can check it too.  Post he output of this command```
cat /home/myusername/Downloads/simpleversion/sv_bin/script/simpleversion
```...substitute the correct user name variables of course.  ;-)

---

### Post by twalp on 2014-06-16
> **bab1 said:**
> 
Is this a Windows program?  Do you have Wine installed?  I'm only concerned with the script that you say launches the program.  I assume it is either a Bourne Shell script or a Bash Shell script.  Those do not need Wine to eXecute.

Let's look at the script itself.  Post the entire output of this command.  You may have to scroll back for all the data ```

cat /opt/simpleversion/sv_bin/script/simpleversion
```

I unzipped the original download in Downloads and then copied that folder to /opt, so the contents -- including the script -- are identical. 

The script is quite short. While I did use the cat command you suggested I also just opened it in qedit and it's the same thing. I'll paste it below.


```
#!/bin/bash


# If you see this message, you probably attempted to start SimpleVersion.
# Please open a terminal (Konsole, gnome-terminal, xterm),
# navigate to this folder (type 'cd /path/to/simpleversion' [Enter])
# then execute simpleversion (type './simpleversion' [Enter])

SV_SCRIPT_DIR="$(dirname "$(readlink -e "$0")")"
source "$SV_SCRIPT_DIR/svw_main"

Main "$@"
```

To summarize where this is at:

1. you've established that the eXecute bit is set for simpleversion
2. it executes fine from the Downloads location but not from /opt.
3. no error message appears when simpleversion is executed from /opt, but the SimpleVersion GUI does not appear, so for all intents and purposes I assume it did not run (**is there a way to verify this -- like Windows Task Manager?**)
4. you say that if this were a permissions issue I'd get an error message, which I don't.
5. fullversion's installer installed in /opt, from where fullversion runs fine. Note that fullversion's script looks identical to simpleversion.
6. I simply copied simpleversion's folder to /opt using "sudo cp -r /home/myusername/downloads/simpleversion /opt", but I cannot successfully spawn its gui by running it there (a redundant statement, sorry)
7. Wine is not installed but I wonder if some sort of runtime module is included in the /wine/ folder, which is in both simpleversion's and fullversions' folder structures. It's probably a red herring and I shouldn't have mentioned it, unless fullversion's installer registers something (Windows perspective) that makes this item relevant.

---

### Post by bab1 on 2014-06-16
> **twalp said:**
> I unzipped the original download in Downloads and then copied that folder to /opt, so the contents -- including the script -- are identical. 

The script is quite short. While I did use the cat command you suggested I also just opened it in qedit and it's the same thing. I'll paste it below.

```
#!/bin/bash


[COLOR="#0000FF"]# If you see this message, you probably attempted to start SimpleVersion.
# Please open a terminal (Konsole, gnome-terminal, xterm),
# navigate to this folder (type 'cd /path/to/simpleversion' [Enter])
# then execute simpleversion (type './simpleversion' [Enter])[/COLOR]

SV_SCRIPT_DIR="$(dirname "$(readlink -e "$0")")"
source "$SV_SCRIPT_DIR/svw_main"

Main "$@"
```

Yes it is only 3 lines long.  It will run in a non GUI environment and it spits back errors.  I have run it myself to see the errors.  You should do the same and post the errors here.  The instructions to do that are highlighted in blue above.  Run the scripts from both locations (e.g. Downloads and /opt).
> 

To summarize where this is at:

1. you've established that the eXecute bit is set for simpleversion
2. it executes fine from the Downloads location but not from /opt.
3. no error message appears when simpleversion is executed from /opt, but the SimpleVersion GUI does not appear, so for all intents and purposes I assume it did not run (**is there a way to verify this -- like Windows Task Manager?**)
4. you say that if this were a permissions issue I'd get an error message, which I don't.
5. fullversion's installer installed in /opt, from where fullversion runs fine. Note that fullversion's script looks identical to simpleversion.
6. I simply copied simpleversion's folder to /opt using "sudo cp -r /home/myusername/downloads/simpleversion /opt", but I cannot successfully spawn its gui by running it there (a redundant statement, sorry)
7. Wine is not installed but I wonder if some sort of runtime module is included in the /wine/ folder, which is in both simpleversion's and fullversions' folder structures. It's probably a red herring and I shouldn't have mentioned it, unless fullversion's installer registers something (Windows perspective) that makes this item relevant.
Hopefully I'll know more once I see your reply with the errors.

It looks like the creators anticipated Windows and Linux users (both RedHat and Debian).  What is the program name; what is its purpose?

---

### Post by twalp on 2014-06-16
> **bab1 said:**
> Yes it is only 3 lines long.  It will run in a non GUI environment and it spits back errors.  I have run it myself to see the errors.  You should do the same and post the errors here.  The instructions to do that are highlighted in blue above.  Run the scripts from both locations (e.g. Downloads and /opt).

I greatly appreciate the effort you've expended trying to help me, BAB1, but I solved my problem by what I suppose is a kluge:

1. right-clicked on FullVersion and selected **Add to Desktop**. This put an icon and shortcut on the desktop

2. opened the icon's Properties and in the **Desktop Entry** tab I changed the Command to be executed from /opt/fullversion... to /Downloads/simpleversion...

I can now double-click on the icon and run simpleversion.

I opened this thread thinking that the /opt folder is where any program can be placed, regardless of whether the program comes with an installer or not. Apparently that's not the case. I mistakenly assumed this was a permissions issue that could be fixed, which again was wrong. While I don't like having to leave the program in the Downloads folder and would've preferred to put it in a folder that's not visible in the user's home folder, this solution will suffice for now. Gotta move on. 

Thank you again for your tireless help and patience.

---

