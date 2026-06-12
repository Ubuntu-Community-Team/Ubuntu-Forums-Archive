---
title: "how to install downloaded .zip pakages?"
date: 2017-09-20
forum: New to Ubuntu
---

### Post by antsco on 2017-09-20
Hi,
I'd like to install XMind on my 14.04 Ubuntu and what I get is a .zip file from the Xmind web site. 
How can I install it?
I also included the repository for Xmind [http://dl2.xmind.net](http://dl2.xmind.net) the software centre can't find it....
Any help appreciated

---

### Post by howefield on 2017-09-20
Double clicking the zip file and extracting it to a location of your choice and then running the setup.sh script looks about right.

---

### Post by SeijiSensei on 2017-09-20
The usual place to install software that isn't packaged by the distro maintainer is under /usr/local/.  For instance, if the ZIP file contains a binary, put it in /usr/local/bin.  You'll need sudo to place it there, of course.

---

### Post by antsco on 2017-09-20
Thanks for all your suggestions.
I eventually run the setup.sh script in the same directory where I downloaded it, since after copying the .zip file in /usr/local didn't manage to decompress it (for some reason the system wouldn't let me do it even if I run it as sudo..and I was using gunzip). The script run successfully I think (by the message at the end of it running) but...now I do not know how to run the application...I can't see it neither from the software center nor from the applications finder (the one with the spiral icon).

---

### Post by oldos2er on 2017-09-20
What repository did you add? All I can find is a download link.

You can't find it in the software center because it wasn't installed from there.

---

### Post by antsco on 2017-09-20
This: [http://dl2.xmind.net](http://dl2.xmind.net)

You can read about it in the download dialog....I assumed that this is their repo

---

### Post by SeijiSensei on 2017-09-20
> **antsco said:**
> for some reason the system wouldn't let me do it even if I run it as sudo..and I was using gunzip
Gunzip only works on files compressed with the gz method.  To decompress a standard ZIP file you need to use the "unzip" utllity, not gunzip.

---

### Post by oldos2er on 2017-09-20
> **antsco said:**
> This: [http://dl2.xmind.net](http://dl2.xmind.net)

You can read about it in the download dialog....I assumed that this is their repo

That link is not a deb package repo.

---

### Post by antsco on 2017-09-20
Ok, so...after all this.  As I said I managed to install the distro by running the shell script (below). What I don't yet see is how can I run the application
Should I look for a specific file in order to run it, or....?

This is what the shell script did.

[COLOR=#0000ff]```
#!/bin/bash

set -e

SCRIPT_NAME="$0"
SCRIPT_DIR="$(cd "$(dirname "$SCRIPT_NAME")" && pwd)"

echo "[setup] Installing dependencies...."
apt-get install default-jre libgtk2.0-0 libwebkitgtk-1.0-0 lame libc6 libglib2.0-0

FONTS_DIR="$SCRIPT_DIR/fonts"
if [ -d "$FONTS_DIR" ]; then
    echo "[setup] Installing custom fonts...."
    mkdir -p /usr/share/fonts/truetype/xmind
    rsync -av "$FONTS_DIR/" /usr/share/fonts/truetype/xmind/
    fc-cache -f
else
    echo "[setup] WARNING: Custom fonts for XMind are not found."
fi

echo "[setup] Done."

```
[/COLOR]

---

### Post by ian-weisser on 2017-09-20
Did you read the shell script?
Do you understand what it did?

---

### Post by antsco on 2017-09-20
Well from what I understand of shell scripts it has installed libraries and fonts that are needed. I do not see and reference to any component whose name is XMIND....

---

### Post by ian-weisser on 2017-09-20
Agreed. No such reference is there.
Have you consulted the Xmind  install documentation?

---

### Post by antsco on 2017-09-20
yes There is very little there hinting at how to do it.
This is all  they write about installation:

> INSTALLATION 
 
    First, Download XMind from [http://www.xmind.net/](http://www.xmind.net/) 
 
    For Windows installer, double-click it and follow the on-screen 
    instructions. 
     
    For Windows Zip version, unzip it to a clean folder. Open 
    this folder, and launch XMind directly without installation. 
 
    For Mac disk image, double-click it to open a Finder window including 
    "XMind.app" (Some download tool would open it automatically.) Drag the 
    "XMind.app" into your Applications folder to copy it to your hard drive. 
    You can drag XMind again from the Applications folder to your dock, if you 
    want.

I should probably contact the developers...I guess, unless the package per se is bundled within those libraries that have been installed and there is a way to run it afterall.....

---

### Post by HermanAB on 2017-09-21
It looks like they only support Windows and Apple Mac.

In general, downloading and installing random cruft off the net is not a good idea.

However, if it is a Linux program, then you need to use *ls* to see which files are there, then make the file executable with *chmod 754 filename* and finally, execute with *./filename*

---

### Post by antsco on 2017-09-21
Thanks Herman.
Well in their website they say that they have a linux distro, that's why I downloaded it.

> [http://www.xmind.net/download/linux/](http://www.xmind.net/download/linux/)

There are other directories though, now that I see, which I had previuosly not taken into consideration. There is for example an XMind_i386 directory with more files into it, like a XMind.ini an 
executable file XMind and more configuration files. When I try to run this file like with ./XMind and error message appears saying that the file doesn't exist...I managed to find something similar to a forum in the XMind website and I can see that many people have struggled to make the program work. I contacted the support service hoping to get some useful answer soon.

If I try to run ./XMind I get an error message sayyin that the command is not found, although the file is executable by all
What I do not understand is why in the setup.sh in the main dir of the distro,evertying is nt taken care of, I mean if there ar emore configuration steps to do why aren't they made from this scritp???? (I wonder)

---

### Post by howefield on 2017-09-21
If you don't mind using slightly older versions.. you can get a .deb file from here for version 7.5 [http://www.xmind.net/download/previous/](http://www.xmind.net/download/previous/) 

Benefit being that a .deb package is (usually) easier to install.

Alternatively, this looks a decent enough answer to installing version 8 on Ubuntu 16.04, which version of Ubuntu are you using ?
[https://askubuntu.com/questions/869848/how-to-install-run-xmind-v-8-in-ubuntu-16-04](https://askubuntu.com/questions/869848/how-to-install-run-xmind-v-8-in-ubuntu-16-04)

---

### Post by antsco on 2017-09-21
Thanks
I am using 14.04

---

### Post by mc4man on 2017-09-23
> **antsco said:**
> Thanks Herman.
Well in their website they say that they have a linux distro, that's why I downloaded it.



There are other directories though, now that I see, which I had previuosly not taken into consideration. There is for example an XMind_i386 directory with more files into it, like a XMind.ini an 
executable file XMind and more configuration files. When I try to run this file like with ./XMind and error message appears saying that the file doesn't exist...I managed to find something similar to a forum in the XMind website and I can see that many people have struggled to make the program work. I contacted the support service hoping to get some useful answer soon.

If I try to run ./XMind I get an error message sayyin that the command is not found, although the file is executable by all
What I do not understand is why in the setup.sh in the main dir of the distro,evertying is nt taken care of, I mean if there ar emore configuration steps to do why aren't they made from this scritp???? (I wonder)

To run ./XMind you'd have to first cd to the directory holding it.

---

### Post by antsco on 2017-09-24
> **mc4man said:**
> To run ./XMind you'd have to first cd to the directory holding it.

I did, it still doesn't work

> 
drwxr-xr-x 4 alex alex  4096 sep  4 18:56 .
drwxrwxr-x 8 alex alex  4096 sep 20 12:47 ..
drwxr-xr-x 4 alex alex  4096 sep  4 18:56 configuration
drwxr-xr-x 4 alex alex  4096 sep  4 18:56 p2
[COLOR=#0000cd]-rwxr-xr-x 1 alex alex 71264 sep  4 18:53 XMind[/COLOR]
-rw-r--r-- 1 alex alex   367 sep  4 18:57 XMind.ini

---

### Post by mc4man on 2017-09-24
> **antsco said:**
> I did, it still doesn't work
That's not very informative. What happened, what did the terminal show?
Taking a look here it was pretty simple.
Installed jre
```
sudo apt-get install default-jre
```
unpacked the zip, cd'd to the xmind-8-update4-linux/XMind_amd64 directory & ran ./XMind, see screen

---

### Post by mc4man on 2017-09-24
> **mc4man said:**
> That's not very informative. What happened, what did the terminal show?
Taking a look here it was pretty simple.
Installed jre
```
sudo apt-get install default-jre
```
unpacked the zip, cd'd to the xmind-8-update4-linux/XMind_amd64 directory & ran ./XMind, see screen

Now that was on 16.04. So just to ck. tried on 14.04. In 14.04 the default jre is too old. So when running XMind it tells you that. So either find newer jre*, go to 16.04 or don't use...

---

### Post by mc4man on 2017-09-24
> **mc4man said:**
> Now that was on 16.04. So just to ck. tried on 14.04. In 14.04 the default jre is too old. So when running XMind it tells you that. So either find newer jre*, go to 16.04 or don't use...
So assuming that was your unposted issue, to get - 

```
sudo add-apt-repository ppa:webupd8team/java -y
```
press enter on keyboard

 ```
sudo apt-get update
```

```
sudo apt-get install oracle-java8-installer
```

To check version 
```
java -version
```

If you want OpenJDK8 instead there is a ppa for that but oracle is likely more up to date.

---

### Post by antsco on 2017-09-24
Hi mc4man:
That is what the terminal says:

> alex@alexsmon:~/Documentos/Antonio/xmind-8-update4-linux$ ./XMind
bash: ./XMind: No existe el archivo o el directorio
alex@alexsmon:~/Documentos/Antonio/xmind-8-update4-linux$

That's wht i dindn't wite more. Sorry if this has been confusing or scarce info.

I also installed an older .deb distro which installed correctly (I think), and I also installed the latest JVM and this also didn't work (As suggested earlier in this thread). Producing the following error message:

> Se ha producido un error. Vea el archivo de anotaciones
/home/alex/workspace/.metadata/.log.

I can also show the content of the logfile if anyone is willing to have a look there

---

### Post by antsco on 2017-09-24
Right now my Java versión is 9, the latest one.

---

### Post by mc4man on 2017-09-24
> **antsco said:**
> Hi mc4man:
That is what the terminal says:



That's wht i dindn't wite more. Sorry if this has been confusing or scarce info.

I also installed an older .deb distro which installed correctly (I think), and I also installed the latest JVM and this also didn't work (As suggested earlier in this thread). Producing the following error message:



I can also show the content of the logfile if anyone is willing to have a look there
You are not in proper directory (folder) at your terminal prompt..

go to if on a 64 bit install 

~/Documentos/Antonio/xmind-8-update4-linux/XMind_amd64

if on a 32 bit install it's

~/Documentos/Antonio/xmind-8-update4-linux/XMind_i386

---

### Post by antsco on 2017-09-24
oops! I assumed that amd64 was the installation for non intel chipsets 
Anyway even this one fails! with loads of warnings like these:

> 
WARNING: An illegal reflective access operation has occurred
WARNING: Illegal reflective access by org.eclipse.osgi.storage.FrameworkExtensionInstaller (file:/home/alex/Documentos/Antonio/xmind-8-update4-linux/plugins/org.eclipse.osgi_3.11.0.v20160603-1336.jar) to method java.net.URLClassLoader.addURL(java.net.URL)
WARNING: Please consider reporting this to the maintainers of org.eclipse.osgi.storage.FrameworkExtensionInstaller
WARNING: Use --illegal-access=warn to enable warnings of further illegal reflective access operations
WARNING: All illegal access operations will be denied in a future release
Warning: NLS unused message: OpenBrowserHandler_NoInfoDialogMessage in: org.eclipse.ui.internal.messages
Warning: NLS unused message: OpenBrowserHandler_NoInfoDialogTitle in: org.eclipse.ui.internal.messages
Warning: NLS unused message: ShowView_errorTitle in: org.eclipse.ui.internal.messages

[...]


---

### Post by mc4man on 2017-09-24
> **antsco said:**
> oops! I assumed that amd64 was the installation for non intel chipsets 
Anyway even this one fails! with loads of warnings like these:
No idea, it started just fine here in 14.04 & 16.04 using java 8
Maybe keep an eye here, seems same issue
[http://xmind129.rssing.com/browser.php?indx=53243702&last=1&item=23](http://xmind129.rssing.com/browser.php?indx=53243702&last=1&item=23)

Or try java 8

---

### Post by alexeyrv on 2018-05-09
[COLOR=#111111][FONT=Ubuntu]Found answer and its works for me for XMind 8 update 4 and update 7 (last).
Add to the end of  XMind.ini
--add-modules=ALL-SYSTEM

[/FONT][/COLOR]> [COLOR=#111111][FONT=Ubuntu]then I found a solution. append a config item "--add-modules=ALL-SYSTEM" [ addmodulesALLSYSTEM] in the tail of XMind.ini, and xmind is work.[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu] – [/FONT][/COLOR][wczmatthew]("https://askubuntu.com/users/825728/wczmatthew")[COLOR=#111111][FONT=Ubuntu] [/FONT][/COLOR][COLOR=#9199A1][FONT=Ubuntu][[FONT=inherit]22 hours ago[/FONT]]("https://askubuntu.com/questions/1031889/after-upgrading-to-18-04-from-16-04-my-xmind-doesnt-work-anymore/1034269#comment1681541_1031889")[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]

Thanks to [/FONT][/COLOR][wczmatthew]("https://askubuntu.com/users/825728/wczmatthew")[COLOR=#111111][FONT=Ubuntu]

Source: [/FONT][/COLOR]https://askubuntu.com/questions/1031889/after-upgrading-to-18-04-from-16-04-my-xmind-doesnt-work-anymore/1034269#1034269

---

