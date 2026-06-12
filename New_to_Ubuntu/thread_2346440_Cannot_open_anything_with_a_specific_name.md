---
title: "Cannot open anything with a specific name"
date: 2016-12-14
forum: New to Ubuntu
---

### Post by sephingx on 2016-12-14
So, I don't know what I'm doing wrong. But anytime I trying to execute or open a named file (such as studio.sh), I get "not found". I also seem to be unable to open the google chrome folder. The command appears to be correct, and I checked, and rechecked several times that the name of the executable or folder are perfectly copied.

For example. I go to android-studio/bin and try "exec studio.sh" it gives me "not found".
Same thing when I try to open or navigate to "google-chrome-stable_current_amd64.deb". The name is correct but it keeps saying that it cannot find the file.

I'm more than likely doing something wrong but I don't really know at the moment.

---

### Post by steeldriver on 2016-12-14
'exec' is almost certainly not what you want in this context

To execute a file (shell script or executable binary) that is not in a directory that's on your current PATH, you need to give a relative or absolute path to the file e.g.

```

[COLOR=#0000cd]**./**[/COLOR]studio.sh

```

.deb files aren't normally executable AFAIK

---

### Post by m-t-garcia1987 on 2016-12-14
,deb files should be ran by double click so that it opens with the package manager or with terminal by typing

```

sudo dpkg -i google-chrome-stable_current_amd64.deb
sudo apt install -f

```

If I remember correctly that is the way to run a .deb file from terminal. 
The first line grabs the dependencies needed and the second one installs the dependencies and the application.

---

### Post by sephingx on 2016-12-14
Thank you both for the help. Very new to linux and theres quite a learning curve.

---

### Post by m-t-garcia1987 on 2016-12-14
No problem.

A book you might want to check out if you are interested (this is the one that I am using now for my UNIX/Linux class) is:

The Linux Command Line
Second Internet Edition
William E. Shotts, Jr.

It is really easy to follow and teaches you a lot of things that you could benefit from if you decide to use Linux long term.

---

### Post by Geoffrey_Arndt on 2016-12-14
Just interested in "why" you are trying these methods to open a directory, file, or to execute a program.    

You normally just start a program from using a pre-assigned icon which is clicked on in the left-launcher panel (if using Unity DE), or by right-clicking a file in your /home directory tree and choosing the "open with" dialog.   Another normal way is to double click an executable file that is in your /home directory.     Shell scripts are usually started from within /home also.

Standard users normally do not need to click on or access files outside of home unless they get sudo rights for a particular reason (like editing a configuration file, etc.)

---

### Post by sephingx on 2016-12-14
Well, learning to use the command line would be a valuable skill in linux. As far as I understand. The GUI has a limited capability. Terminal seems to have many more options

---

### Post by QIII on 2016-12-14
Hello!

The terminal gives one great power and granularity, exactly as it does in Windows.  If you aren't aware, you can use cmd in Windows.

Also like Windows is the fact that one can manage to use only GUI features and not bother with the terminal.

The reason support forums like this use the terminal so much is that it is common -- and avoids the need to know all the details of the dizzying array of desktop environments out there.

---

### Post by usrnameistaken on 2016-12-15
> **sephingx said:**
> So, I don't know what I'm doing wrong. But anytime I trying to execute or open a named file (such as studio.sh), I get "not found". I also seem to be unable to open the google chrome folder. The command appears to be correct, and I checked, and rechecked several times that the name of the executable or folder are perfectly copied.

For example. I go to android-studio/bin and try "exec studio.sh" it gives me "not found".

you can run it by typing "sh studio.sh" or "chmod +x studio.sh; ./studio.sh"

>  Same thing when I try to open or navigate to "google-chrome-stable_current_amd64.deb". The name is correct but it keeps saying that it cannot find the file.

I'm more than likely doing something wrong but I don't really know at the moment.

.deb packages need to be installed by dpkg command: "dpkg -i google-chrome-stable_current_amd64.deb"

---

### Post by DuckHook on 2016-12-15
> **sephingx said:**
> So, I don't know what I'm doing wrong. But anytime I trying to execute or open a named file (such as studio.sh), I get "not found". I also seem to be unable to open the google chrome folder. The command appears to be correct, and I checked, and rechecked several times that the name of the executable or folder are perfectly copied.

For example. I go to android-studio/bin and try "exec studio.sh" it gives me "not found".
Same thing when I try to open or navigate to "google-chrome-stable_current_amd64.deb". The name is correct but it keeps saying that it cannot find the file.

I'm more than likely doing something wrong but I don't really know at the moment.Welcome to the forums, sephingx

I'm making some assumptions here, but based on your actions, I suspect that you were trying to run "executables" as if Linux were Windows. Moreover, your understanding of what a .deb file is may be misconceived.

I think that your last sentence is very appropriate. Before learning to run, let's learn how to walk. I recommend that you have a look at the links in my sig, especially: Linux is Not Windows, Resources for Newcomers, and A Great CLI Guide. There are also these:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
[http://ubuntuguide.org/wiki/Ubuntu:Trusty](http://ubuntuguide.org/wiki/Ubuntu:Trusty)
[http://ubuntu-manual.org/](http://ubuntu-manual.org/)
[https://linuxjourney.com](https://linuxjourney.com)

I strongly recommend that you get familiar with the Linux file structure, user model and other Linux fundamentals before diving into CLI commands. Even then, I suggest starting out with simple commands like *cp* and *ls* before proceeding to things like what you are trying to do. Please don't get me wrong. I think it's great that you are enthusiastic about the command line and want to learn it, but things will go easier if you start at the beginning and not try to jump in the deep end.

---

### Post by Geoffrey_Arndt on 2016-12-16
When I teach new users in our Club the basics of Linux, I never "start" with the CLI although I agree it is the "common denominator" of all OS's (especially Linux and Unix/BSD).

---

