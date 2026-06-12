---
title: "[SOLVED] flash and terminal?"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by cloud_vivi on 2008-07-06
ok well where can i start. well i got flashplayer off spm last time and it was making watching youtube a total annoyance. so i decide to reformat and download the actual package from adobe but theres a problem how come it wont install? there is a file called "libflashplayer.so" ok well i dont know if i am ment to install this through the terminal but if i am i dont have a clue how to ok well its on my desktop could someone please give me the code that i have to type into the terminal to make ubuntu install it please thank you cv.

---

### Post by sharks on 2008-07-06
better install flashplugin-nonfree

[http://wiki.debian.org/FlashPlayer](http://wiki.debian.org/FlashPlayer)

---

### Post by cloud_vivi on 2008-07-06
thats what i installed last time and OMG  it was killing me piece by piece seriously. when i went to play flash games it totally wouldnt work when i went on to youtube it would bring up this giant grey play button which  i wasnt to fussed with at first but then i relised. that the sound wouldn't work i mean i couldnt turn it up or down it was just plain annoying me i have the package but i just need to know how to install it.

---

### Post by sharks on 2008-07-06
do u have tar.gz or deb?
if u have deb , then double click it and install.

---

### Post by sharks on 2008-07-06
Installation instructions for tar.gz

       1. Click the "Download .tar.gz" link. A dialog box will appear asking you where to save the file.
       2. Save the .tar.gz file to your desktop and wait for the file to download completely.
       3. Unpackage the file. A directory called install_flash_player_9_linux will be created.
       4. In terminal, navigate to this directory and type ./flashplayer-installer to run the installer. Click Enter. The installer will instruct you to shut down your browser(s).
       5. Once the installation is complete, the plug-in will be installed in your Mozilla browser. To verify, launch Mozilla and choose Help > About Plug-ins from the browser menu.

Installation instructions for .rpm

       1. Click the "Download .rpm" link. A dialog box will appear asking you where to save the file.
       2. Save the .rpm file to your desktop and wait for the file to download completely.
       3. In terminal, navigate to the desktop and type # rpm -Uvh <rpm_package_file>. Click Enter. (Note: This must be done as a root user). The installer will instruct you to shut down your browser(s).
       4. Once the installation is complete, the plug-in will be installed in your Mozilla browser. To verify, launch Mozilla and choose Help > About Plug-ins from the browser menu.

Installation instructions for the YUM repository definition

       1. Click the &#8220;Download .rpm&#8221; link. A dialog box will appear asking you where to save the file.
       2. Save the .rpm file to your desktop and wait for the file to download completely.
       3. In terminal, navigate to the desktop and type # rpm -Uvh <rpm_package_file>. Click Enter. (Note: This must be done as a root user).
       4. Once the installation is complete, in terminal, type # yum install flash-plugin. Click Enter. (Note: This must be done as a root user).
       5. To verify the plugin is installed in Mozilla, launch Mozilla and choose Help > About Plug-ins from the browser menu.
       6. To get the most up-to-date Flash Player in the future, simply type # yum update flash-plugin in terminal. You will not need to repeat steps 1-4.

---

### Post by cloud_vivi on 2008-07-06
i have tar.gz

also when i used that last package i had to click youtube like 20 times before i could start typing

---

### Post by prismpirate on 2008-07-06
Download the tar.gz file using this link:

[http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz]("http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz")

Save it under your home folder. (Tell me if you don't know where this is located)

After that, right click on the tar.gz file, and click on extract all, and a folder should appear.

Now, open terminal, which is located under Accessories > Terminal.

A black window should appear.

Now, type in this command:
```
cd install_flash_player_9_linux
```

Next, time in this
```
sudo ./flashplayer-installer
```

Press enter to install. Enjoy

---

### Post by cloud_vivi on 2008-07-06
ok theres a quick problem its asking me for the path for mozilla what the path? i know what a path like but i dont know the string for ubuntu sorry


its asking me this

Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla):

---

### Post by ibutho on 2008-07-06
You should be able to just do
```
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/.
```
or 
```
sudo cp libflashplayer.so /usr/lib/firefox/plugins/.
```

---

### Post by sharks on 2008-07-06
type in terminal:

whereis firefox
whereis mozilla

---

### Post by cloud_vivi on 2008-07-06
OMG this is so fustrating. im thankful for all your help people but it still anit working??? i havent got a clue know its telling me this

WARNING: /usr/bin/firefox is not a directory.

and

WARNING: /usr/bin/firefox /usr/lib/firefox /usr/share/firefox is not a directory.

seriously im sooo sorry that this is being so annoying

---

### Post by ibutho on 2008-07-06
There are no directories in /usr/bin, so thats not the correct path. Have you tried copying the plugin to /usr/lib/mozilla/plugins? Also look in /usr/lib for any firefox related directories.

---

### Post by cloud_vivi on 2008-07-06
i anit got a clue what that means but idk lol i shall just try and find a different way thanks anyways lads we tried and i failed hard :P

---

### Post by bhadotia on 2008-07-06
If you have HH then the path is /usr/lib/firefox-3.0 also do another installation in /usr/lib/mozilla/plugins

---

### Post by ibutho on 2008-07-06
> **cloud_vivi said:**
> i anit got a clue what that means but idk lol i shall just try and find a different way thanks anyways lads we tried and i failed hard :P
I don't think you have failed, but maybe you just haven't figured out the advice being given. There are two ways to install the tar.gz file. When you extract the contents of the tar.gz file, and change into the extracted directory, one method is to install flash using the install script e.g.
```
sudo flashplayer-installer
```
For this method, you need to let the installer know where Firefox is installed which is usually somewhere in /usr/lib e.g. /usr/lib/firefox-3.0. 

For the second method you simply copy the plugin to the global directory where all mozilla based browsers look for plugins which is /usr/lib/mozilla. So once again, you extract the tar.gz file, change into it and run
```
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/.
```

---

### Post by cloud_vivi on 2008-07-06
its ok people its been solved =DDDD all i had to do was reformat =( but then i had an idea. that whenyour missing a plug in usally for a website it will ask missing plug ins would you like to install so i thought YOUTUBE lol installed the plug ins i even wwent and installed the plug ins for java lol thanks anyways you lot seriously thank you =) ur all going to get big thanks off me =0 it just shows this forum cares =p

---

