---
title: "Cannot run the Linux version of this program on Lubuntu 16.04 LTS"
date: 2018-05-09
forum: New to Ubuntu
---

### Post by j0hnick on 2018-05-09
Hi,

I cant get this to run on Lubuntu 16.04 LTS

[https://github.com/Al-Azif/ps4-exploit-host/releases](https://github.com/Al-Azif/ps4-exploit-host/releases)

The windows version runs fine on my main rig, but Id like to be able to run this on an old 2004 XP machine I have in my spare room. The Windows version needs at least Windows 7, but the linux version says it works on Ubuntu 16.04 LTS, my old XP machine only has 1 GB of Ram so I put Lubuntu 16.04 LTS 32 bit on it. Its written in Python so I updated python for what its worth, when I double click on what I assume is the executable it asks what program I want to open it with, I tried LX Terminal but nothing happens.

Any ideas ?, Ill admit I usually rely on the Ubuntu store or .deb files to install programs.

Thanks in advance

---

### Post by yancek on 2018-05-09
Which file did you download, one of the zip files or the tar.gz?  You would obviously have to unzip a zip file or extract the tar.gz file.  If you downloaded the tar.gz file and extract it, you will see a REAME.md file in it with instructions.  Probably the same if you unzip a zip file.  What exactly do you assume is the executable?

---

### Post by j0hnick on 2018-05-09
I extracted it to the downloads folder, I double clicked on a file with the same file name as the windows version that is about 6mb, all the other files are only a few kb. I read the read me but its the same as the windows version.

---

### Post by monkeybrain20122 on 2018-05-09
Did you make the file executable (right click Properties > Allow to execute)?

---

### Post by yancek on 2018-05-09
If you download the tar.gz file you can click on it in your Downloads file and select the option to extract it and you will then have a folder named ps4-exploit-host-0.4.2 with several folders and files.  The only executable file in it is the start.py file so run that with python bearing in mind that as the README file staes, must be made executable and run as root user.  That folder is a lot smaller than 6MB, which file did you actually download.  If it was the zip file, you need to unzip it.

---

### Post by j0hnick on 2018-05-10
> **yancek said:**
> The only executable file in it is the start.py file  so run that with python 

Theres no start.py file in the archive, there was in the windows version though.

> **monkeybrain20122 said:**
> Did you make the file executable (right click Properties > Allow to execute)?

Thanks, now it runs but says it has to be run as the root user.

How do I run it as root ?, I appreciate the help guys.

---

### Post by yancek on 2018-05-10
Try the answer at the link below.

[https://stackoverflow.com/questions/304883/what-do-i-use-on-linux-to-make-a-python-program-executable](https://stackoverflow.com/questions/304883/what-do-i-use-on-linux-to-make-a-python-program-executable)

Or create a Desktop file to click on.

[https://askubuntu.com/questions/596793/make-a-python-program-executable-from-its-icon](https://askubuntu.com/questions/596793/make-a-python-program-executable-from-its-icon)

---

### Post by j0hnick on 2018-05-10
> **yancek said:**
> Try the answer at the link below.

[https://stackoverflow.com/questions/304883/what-do-i-use-on-linux-to-make-a-python-program-executable](https://stackoverflow.com/questions/304883/what-do-i-use-on-linux-to-make-a-python-program-executable)

Or create a Desktop file to click on.

[https://askubuntu.com/questions/596793/make-a-python-program-executable-from-its-icon](https://askubuntu.com/questions/596793/make-a-python-program-executable-from-its-icon)

Tried both of those, created a desktop shortcut, still getting this

[IMG]http://i492.photobucket.com/albums/rr282/Johnick/Screenshot%20from%202018-05-10%2015-56-35_zpszmkloiuo.png[/IMG]

---

### Post by yancek on 2018-05-10
You might want to post whatever link you tried to post above.

Are you running this from the /home/user?/Downloads/ps4-exploit-host-0.4.2 directory in which the start.py file resides?
Are you prefixing the command with sudo so you have root privileges?

You never indicated whether you downloaded the tar.gz or the zip file.  I don't know if they have the same contents.
The second link I posted had an example Desktop entry and you would have to change that pointing to the exact location of the executable.
Post the command you ran and open the Desktop link in a text editor and post what you have.

---

### Post by j0hnick on 2018-05-10
> **yancek said:**
> You might want to post whatever link you tried to post above.


Done

[IMG]https://i.imgur.com/Xu5zi1V.png[/IMG]

> **yancek said:**
> 

Are you running this from the /home/user?/Downloads/ps4-exploit-host-0.4.2 directory in which the start.py file resides?


Yes, but unless the start.py file is hidden, it isn't there

> **yancek said:**
> 
Are you prefixing the command with sudo so you have root privileges?


In the shortcut ?, no

> **yancek said:**
> 
You never indicated whether you downloaded the tar.gz or the zip file. 


Extracted tar.gz file to downloads folder

Ill post the code I put in the shortcut soon.

---

### Post by j0hnick on 2018-05-10
[Desktop Entry]
Name=Test
Exec=/home/john/Downloads/ps4-exploit-host/ps4-exploit-host
Terminal=true
Type=Application

[IMG]https://i.imgur.com/ABboqpP.png[/IMG]

---

### Post by yancek on 2018-05-10
You still haven't posted the exact name of the tar.gz file you downloaded so let me just post what I downloaded and what I see.  The name of the tar.gz file I downloaded from the site you linked is:

> ps4-exploit-host-0.4.2.tar.gz

You can either go to a terminal in the Downloads directory and extract it or simply right click on that file and select the option to extract.  If you do that, you should then see a new folder created in the Downloads directory named.

> ps4-exploit-host-0.4.2 

If you then change to the ps4-exploit-host-0.4.2 directory, you should see the following folders/files.  If you don't see them, download again.  If you downloaded a different tar.gz, I don't know what to expect.

> exploits/  fakedns/  FAQ.md  LICENSE  payloads/  README.md  settings.json  start.py*  themes/  updates/



---

### Post by j0hnick on 2018-05-14
> **yancek said:**
> You still haven't posted the exact name of the tar.gz file you downloaded so let me just post what I downloaded and what I see.  The name of the tar.gz file I downloaded from the site you linked is:



You can either go to a terminal in the Downloads directory and extract it or simply right click on that file and select the option to extract.  If you do that, you should then see a new folder created in the Downloads directory named.



If you then change to the ps4-exploit-host-0.4.2 directory, you should see the following folders/files.  If you don't see them, download again.  If you downloaded a different tar.gz, I don't know what to expect.

1. Downloaded ps4-exploit-host-0.4.2.tar.gz
2. extracted it to /home/john/Downloads/ps4-exploit-host
3 I have all the files you listed except start.py, as shown in the screenshot I posted earlier.

When I run ps4-exploit-host, it opens a terminal window and says "error, this must be run by root, press any key to exit".

---

