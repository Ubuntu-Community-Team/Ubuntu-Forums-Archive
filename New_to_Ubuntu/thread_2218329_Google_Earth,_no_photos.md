---
title: "Google Earth, no photos"
date: 2014-04-20
forum: New to Ubuntu
---

### Post by HappyAsHellas on 2014-04-20
I have installed Ubuntu 14.04, and after having re installed google earth, I have no photos, just blank spaces when I click on them. I had this problem before on a different thread where it was just a case of downloading a different/updated file ( ge7.1.1.1580.x86_64-new-qt-libs-debian7-ubuntu12.tar(2).xz ) and everything was fine. I have tried that again this time but to no avail. I am running Ubuntu in 32 bit, so is it a different file I need, and if so where do I get it. Google earth wont let me download the 64 bit version as I am on 32 bit. ( I think ).

---

### Post by kc1di on 2014-04-20
got to this [page]("http://www.noobslab.com/2014/03/install-google-earth-in-ubuntulinux.html") follow the instructions , it worked for me :)

---

### Post by HappyAsHellas on 2014-04-20
Tries it but the same result. I got this at the end in the terminal window, is this normal?

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.

---

### Post by 23dornot23d on 2014-04-20
From what you got back there it did nothing - as one version is already installed.

You have to remove any previous version and then try the commands in the link

But just so you know - I tried them - and the pictures do not show up - so you may be wasting your
time doing it that way ...... but I never tried the last one which was the alternative 64 bit install ........

So whether that one works or not .......... is yet to be seen ............

Strange thing is when zoomed in close on the Google Earth ...... thumbnails for pictures now appear

But when clicking the normal links where photos should be and a square is shown ........ just a blank
rectangle appears with only a small title of what you should be seeing in it ....

[IMG]http://i.minus.com/ifULKT45M5Q5X.png[/IMG]

---

### Post by oldos2er on 2014-04-20
See posts #28 and #27 in [this thread]("http://ubuntuforums.org/showthread.php?t=2196304").

---

### Post by HappyAsHellas on 2014-04-20
Tried it and now google earth wont start at all. How do I uninstall it to try and get a clean install in 64 bit?

---

### Post by kc1di on 2014-04-20
Go to a terminal and type  ```
 sudo apt-get purge google-earth 
```

---

### Post by HappyAsHellas on 2014-04-20
I have now upgraded to Ubuntu 14.04 64 bit, installed google earth, ran the commands from the other thread and I get this message at the end:

Downloads/ge7.1.1.1580-0.x86_64-new-qt-libs-debian7-ubuntu12.tar.xz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now

What do I do now?

---

### Post by 23dornot23d on 2014-04-20
Type in

**history** 

into a terminal and show us what you have tried out ............

The last 20 commands should give us some idea as to what is happening.

_________________________________________________

When you type **history** into a terminal are your commands anything like mine .......... or something else ......... 
please post back the last 10 or so commands so we can see how you got to see this !!!  .........

> 

Downloads/ge7.1.1.1580-0.x86_64-new-qt-libs-debian7-ubuntu12.tar.xz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now


[IMG]http://i.minus.com/ivldYfNDNvItJ.jpeg[/IMG]

This is all I did to get mine running so far ......... but as I say ..... the pictures only show on the slides at the bottom
and on certain thumbnails .......



> 
    [B]sudo  apt-get install libc6-i386 libglib2.0-0:i386 libsm6:i386  libglu1-mesa:i386 libgl1-mesa-glx:i386 libxext6:i386 libxrender1:i386  libx11-6:i386 libfontconfig1:i386 lsb-core
    sudo dpkg -i google-earth64.deb
    wget -O google-earth64.deb [http://dl.google.com/dl/earth/client/current/google-earth-stable_current_i386.deb](http://dl.google.com/dl/earth/client/current/google-earth-stable_current_i386.deb)
    sudo dpkg -i google-earth64.deb

    history[/B]



---

### Post by HappyAsHellas on 2014-04-20
This is what I get with history:


george@george-W240HU-W250HUQ:~$ history
    1  sudo apt-get install libc6-i386 libglib2.0-0:i386 libsm6:i386 libglu1-mesa:i386 libgl1-mesa-glx:i386 libxext6:i386 libxrender1:i386 libx11-6:i386 libfontconfig1:i386 lsb-core
    2  wget -O google-earth64.deb [http://dl.google.com/dl/earth/client/current/google-earth-stable_current_i386.deb](http://dl.google.com/dl/earth/client/current/google-earth-stable_current_i386.deb)
    3  sudo dpkg -i google-earth64.deb
    4  rm google-earth64.deb
    5  sudo apt-get install libfreeimage3
    6  cd /opt/google/earth/free
    7  sudo tar xvf ~/Downloads/ge7.1.1.1580-0.x86_64-new-qt-libs-debian7-ubuntu12.tar.xz
    8  gsettings set com.canonical.desktop.interface scrollbar-mode normal
    9  sudo apt-get install gufw
   10  sudo apt-get install flashplugin-installer
   11  history
george@george-W240HU-W250HUQ:~$

---

### Post by 23dornot23d on 2014-04-20
The step that might be missing is the Download

> 
6  cd /opt/google/earth/free
    7  sudo tar xvf ~/Downloads/ge7.1.1.1580-0.x86_64-new-qt-libs-debian7-ubuntu12.tar.xz


Which instructions are you following now ..... as I can see a couple of downloads for this file
but am not sure if that is what you are now using .......

The solution is said to work on 12.10 and 13.04 if it is from here
[https://docs.google.com/file/d/0B2F__nkihfiNOUJSeEJfWUx0Vk0/edit](https://docs.google.com/file/d/0B2F__nkihfiNOUJSeEJfWUx0Vk0/edit)

But you said you upgraded to 14.04 ..... so not sure which route you have now taken to solve this.

The one that was posted earlier I tried too [http://ubuntuforums.org/showthread.php?t=2196304&p=12892342#post12892342](http://ubuntuforums.org/showthread.php?t=2196304&p=12892342#post12892342)

But it did not have the dependency to remove out of the package on my system which is 14.04

Where it says this

> 
cd /var/lib/dpkg

sudo cp status status.backup

sudo gedit status___________________________________________ changed for gedit from nano as its easier 

You don't need to use nano if you prefer a different editor; whatever  you use needs root privilege to edit the status file. Search for  google-earth-stable, remove ia32-libs from the *Depends* line, save and exit the file. Run 


Searched for google-earth-stable and when I found it - the line for ia32-libs was not there ...... so that means no change could 
take place for that part of it.

If I find something that does work I will post back again though ........ the situation seems to be that some parts work
as I am getting the thumbnails showing in certain situations ..........

[IMG]http://i.minus.com/iNKyCM3Q4Gmaq.jpg[/IMG]

---

### Post by monkeybrain20122 on 2014-04-20
I can confirm that the work around from post #5 for Panoramio pictures has stopped working on 14.04. It worked and is still working on 13.10.  Oh well.

---

### Post by monkeybrain20122 on 2014-04-20
> **HappyAsHellas said:**
> This is what I get with history:


george@george-W240HU-W250HUQ:~$ history
    1  sudo apt-get install libc6-i386 libglib2.0-0:i386 libsm6:i386 libglu1-mesa:i386 libgl1-mesa-glx:i386 libxext6:i386 libxrender1:i386 libx11-6:i386 libfontconfig1:i386 lsb-core
    2  wget -O google-earth64.deb [http://dl.google.com/dl/earth/client/current/google-earth-stable_current_i386.deb](http://dl.google.com/dl/earth/client/current/google-earth-stable_current_i386.deb)
    3  sudo dpkg -i google-earth64.deb
    4  rm google-earth64.deb
    5  sudo apt-get install libfreeimage3
    6  cd /opt/google/earth/free
    7  sudo tar xvf ~/Downloads/ge7.1.1.1580-0.x86_64-new-qt-libs-debian7-ubuntu12.tar.xz
    8  gsettings set com.canonical.desktop.interface scrollbar-mode normal
    9  sudo apt-get install gufw
   10  sudo apt-get install flashplugin-installer
   11  history
george@george-W240HU-W250HUQ:~$

I am confused, in 2) your link is to 32 bit ge.

---

### Post by 23dornot23d on 2014-04-20
@monkeybrain ........ the link is here [http://www.noobslab.com/2014/03/install-google-earth-in-ubuntulinux.html](http://www.noobslab.com/2014/03/install-google-earth-in-ubuntulinux.html)
with the instructions and that wget command ... for 32 bit .... 

_________________________

This is not a proper fix but ........

The pictures will work - only after selection is done in the bar underneath the google earth globe
of pictures in the region you are currently in ...... the Tour Guide then goes away - but you then
click on the timer that appears to get a new lot of pictures up ..... seems to work then to view
the pictures in regions.

Then clicking on the thumbnail actually brings the photo up as shown below ....... 

but its not working as it should be some links I am finding for solutions seem to point to the paths being set to get to certain
  files ...... but have yet to find one that covers ubuntu 14.04 ..... some have managed on Arch linux
and some on the older versions of ubuntu 

___________________________

But this picture below is from 14.04 ... but selecting a thumbnail under the globe ..... in the tour guide slider bar of thumbnails .....

.... then the ones in the map become available as thumbnails to select on the map itself ........

Not at all sure why ....... but possibly it creates a link to something needed ........ by the photo viewer program
in google earth ......... odd though ....... should expect some path change / addition - may fix this though .........

[IMG]http://i.minus.com/i82cAoa0e9Sy0.jpg[/IMG]

---

### Post by monkeybrain20122 on 2014-04-20
Strange. It is the same google-earth version in my 13.10 and 14.04 and the same tarball for the qtlibs (I saved it last time). So something is messed up in 14.04.

---

### Post by 23dornot23d on 2014-04-20
Only error I see when running it from a terminal is this one - which is being reported all over the net ......

[0420/202043:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.

[https://www.google.co.uk/search?client=ubuntu&channel=fs&q=nss_ocsp.cc%28581%29&ie=utf-8&oe=utf-8&gl=uk](https://www.google.co.uk/search?client=ubuntu&channel=fs&q=nss_ocsp.cc%28581%29&ie=utf-8&oe=utf-8&gl=uk)

But it does not change as I browse through the photos ........... and runs ok other than the pictures not showing up
when clicking directly onto the (square picture markers) ........... 

_____________________________

But the network link to the pictures in google earth must be working otherwise the thumbnails would not show up ..... 

 ( so it could be a config file or path to something somewhere that's been changed maybe )

/opt/google/earth/free/plugins/imageformats

was looking - but if its the same as the older version in 13.10 then its nothing to do with google earth 

but something else must have changed.

---

### Post by oldos2er on 2014-04-20
> **monkeybrain20122 said:**
> I can confirm that the work around from post #5 for Panoramio pictures has stopped working on 14.04. It worked and is still working on 13.10.  Oh well.

Strange, the Panoramio fix has been working fine for me, and still does, using GE 7.1.2.2041.

---

### Post by 23dornot23d on 2014-04-20
I first went into synaptic and cleared everything out ..... my history is here including the odd hiccup

```


  682  history


```

The strange thing is it only works from the command line ........ running it from the menu and it crashed out when in the program.
Still something strange going on .......... may be a mistake I made or may be that this is not a straight forward simple install yet

USC will give you this if you try direct from Google Earth site ..... using the deb 
( but this then gave me confidence about what Ann said above - as her version runs ok ...... )

[IMG]http://i.minus.com/iApSDdc5ado8Y.jpg[/IMG]

____________________________

I can confirm now that if you download the 64 bit file direct from the Google Earth site [http://www.google.com/earth/download/thanks.html#os=linux#linux_dl=deb_64](http://www.google.com/earth/download/thanks.html#os=linux#linux_dl=deb_64)

Then download the other file the tar from this link [https://docs.google.com/file/d/0B2F__nkihfiNOUJSeEJfWUx0Vk0/edit](https://docs.google.com/file/d/0B2F__nkihfiNOUJSeEJfWUx0Vk0/edit)

Then follow all the instructions from this link [http://ubuntuforums.org/showthread.php?t=2196304&p=12892342#post12892342](http://ubuntuforums.org/showthread.php?t=2196304&p=12892342#post12892342)

Then you click a thumbnail in the tour ..... first.

Then the panorama will start working ...........

as below ...... ( but I can only get it to work from the command line ) it will crash out from the menu selection.

[IMG]http://i.minus.com/iPzS24rwWB2KE.jpg[/IMG]

The instructions are here but as it states - [COLOR=#ff0000]**use at your own risk and only for experienced users **[/COLOR]..........
[https://docs.google.com/file/d/0B2F__nkihfiNMDlaQVoxNVVlaUk/edit](https://docs.google.com/file/d/0B2F__nkihfiNMDlaQVoxNVVlaUk/edit)

---

### Post by monkeybrain20122 on 2014-04-20
It is working now! 

I did two things
1) re-downloaded the tar from [https://docs.google.com/file/d/0B2F_...JfWUx0Vk0/edit]("https://docs.google.com/file/d/0B2F__nkihfiNOUJSeEJfWUx0Vk0/edit") and re installed the qtlibs (i.e cd in to /opt/google/earth/free and untar the tarfile, thus overwriting what was in google/earth/free)
2)delete ~/.googleearth
Unless the tar file has changed or my saved one was corrupted, or somehow the first attempt was blotched, I think 2) did the trick.

Edited: unrelated problem here, tried to make a screenshot but discovered that prt-scr button dosn't work in 14.04. It worked in 13.10, should start a new thread.

---

### Post by 23dornot23d on 2014-04-20
I added shutter for the printscrn button to work again ......

**sudo apt-get install shutter**

Good to see you got google earth working though - I renamed .googleearth to .googleearth2

and its created a fresh one now and it too runs from the menu now ....... cheers never thought to do that .

I too can run it clean from my menu again ........ no crash this time - update = second run it crashed again

May have to delete the .googleearth every run ........ not good ......... but works after I run it from the terminal.

Then crashed again the second run from a menu choice ...... that is odd .

Will just stick to running it from the terminal for now .......

---

### Post by amirpli on 2014-04-21
Hello 23dornot23d,

> **23dornot23d said:**
> I first went into synaptic and cleared everything out ..... my history is here including the odd hiccup
[...]
The strange thing is it only works from the command line ........ running it from the menu and it crashed out when in the program.
Still something strange going on .......... may be a mistake I made or may be that this is not a straight forward simple install yet
[...]
as below ...... ( but I can only get it to work from the command line ) it will crash out from the menu selection.
[...]
The instructions are here but as it states - [COLOR=#ff0000]**use at your own risk and only for experienced users **[/COLOR]..........
[https://docs.google.com/file/d/0B2F__nkihfiNMDlaQVoxNVVlaUk/edit](https://docs.google.com/file/d/0B2F__nkihfiNMDlaQVoxNVVlaUk/edit)


In order to solve this problem (that it works only from the command line), try this:

```
find /usr /home -name google-earth.desktop
```
On Ubuntu it will most probably find the file /usr/share/applications/google-earth.desktop .

Edit the file it finds (sudo if this file is a system file).
 Change the Exec path to: /usr/bin/google-earth %f
Save & exit.

(If you have more than one google-earth.desktop file and you are not sure which is being used - edit all of them.)

---

### Post by HappyAsHellas on 2014-04-21
I have downloaded the file but where do I extract it to? I take it I can't just extract it into the downloads folder, but rather it must go beside the program itself, but I have no idea where this is.

---

### Post by 23dornot23d on 2014-04-21
It already has the in it ...... odd ..... not sure if there is another one yet but will have a look later on when I have more time ty

Exec=/opt/google/earth/free/google-earth %f

____________________________________________

> 
I have downloaded the file but where do I extract it to? 
I take it I  can't just extract it into the downloads folder, 
but rather it must go  beside the program itself, 
but I have no idea where this is. 				


I think you might be referring to this part of the problem here 

> 
**cd /opt/google/earth**
**sudo cp -a free free.newlibs**
**cd free.newlibs**
**sudo cp ~/Downloads/ge7.1.1.1580-0.x86_64-new-qt-libs-debian7-ubuntu12.tar.xz .**
[COLOR=#ff0000]sudo tar xvf ~/Download/ge7.1.1.1580-0.x86_64-new-qt-libs-debian7-ubuntu12.tar.xz
ls
sudo tar xvf ~/Download/ge7.1.1.1580-0.x86_64-new-qt-libs-debian7-ubuntu12.tar.xz[/COLOR]
**sudo tar xvf ge7.1.1.1580-0.x86_64-new-qt-libs-debian7-ubuntu12.tar.xz**
[B]sudo mv /usr/bin/google-earth /usr/bin/google-earth.old
sudo ln -s /opt/google/earth/free.newlibs/googleearth /usr/bin/google-earth[/B]
google-earth


**cd** means to change directory ..........

So everywhere that it occurs - it is a change of directory .......... by executing the commands exaclty as above
but not the lines in red ..... it may get you what you want ........ but as I said - its for experienced users and
its not working as well as it could be as of yet - my own version is only running from the command line
and it should run from the menu link ( which is set correctly as far as I can tell ) but will spend some more time
on this later as I have to go out now .......

You may be better off waiting a while - until a proper fix is done for this .....
( There as to be an easier way - for most users to use ........... )

__________________________________________________

But there is enough information now to complete this task as they were the commands I ran to get it working
nothing else - other than on the previous page post 18 at the bottom is a readme file.

The readme was added and I put that as a link at the end of post #18 in red ........... which was taken from
the link posted by (Ann - Oldoser)

---

### Post by monkeybrain20122 on 2014-04-21
> **HappyAsHellas said:**
> I have downloaded the file but where do I extract it to? I take it I can't just extract it into the downloads folder, but rather it must go beside the program itself, but I have no idea where this is.

Let's say you downloaded foo.tar.xz to Downloads, the idea is to extract it in /opt/google/earth/free and replace the files there with the same names

so you change directory to /opt/google/opt/free and extract 
```
cd /opt/google/earth/free
sudo tar xvf ~/Downloads/foo.tar.xz
```

That's it. I am not making a duplicate and then symlink it. I think it was just for caution that the instructions were like that when they were first posted, but now we know the worst thing that can happen is that it doesn't work, there is no need to back up /opt/google/earth/free

**Edited: **the patch might not have worked for you because you installed a 32 bit google-earth
To install the 64-bit,  first uninstall your version, then download 64 bit ge from google
right click the .deb and click 'extract here" , then delete the origin .deb.  Then open the extracted folder and go to Debian and edit the control file, remove ia32 from the "depends on"
line and now rebuild the .deb as follows:
 Let's say the extracted folder is called google-earth-current-stable_amd64 and it is on your desktop, 
```
cd Desktop
dpkg -b  google-earth-current-stable_amd64
```
Then  install it by right clicking 
It will install but won't run, to run it you need some dependencies
```
sudo apt-get install libc6:i386 lsb-core
```

---

### Post by monkeybrain20122 on 2014-04-21
> **23dornot23d said:**
> 

I too can run it clean from my menu again ........ no crash this time - update = second run it crashed again

May have to delete the .googleearth every run ........ not good ......... but works after I run it from the terminal.

Then crashed again the second run from a menu choice ...... that is odd .

Will just stick to running it from the terminal for now .......

Hmm.. strange. I have restarted ge several times and there has been no problem, always get the pictures. 
If you have to delete .googleearth every time for some reasons may be you can try this, open ge's .desktop file (in most likely /usr/share/applications) and change the "Exec=" line by pre-pending "rm -r /home/username/.googleearth && " without quotations, notice there is a space after && separating it from what follows. If this works as expected then when you click the .desktop file it would remove ~/.googleearth before it starts ge. But not sure if the syntax is correct.

---

### Post by 23dornot23d on 2014-04-21
Thanks for letting us know there were no problems from the menu                                                                                      [**[COLOR=#000000]monkeybrain20122[/COLOR]**]("http://ubuntuforums.org/member.php?u=1843403")      
                         [IMG]http://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-online.png[/IMG]



and all is working well from the menu now ......... cheers                                                                                      [**[COLOR=#000000]amirpli[/COLOR]**]("http://ubuntuforums.org/member.php?u=1918498")      
                         [IMG]http://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-online.png[/IMG]

______________________________________________________________________________________________

---

### Post by raysrdsld on 2014-04-28
I have the same problem with no photo's in google earth.I tried this fix but the file I have to edit comes up as read only.? Any help would be appreciated.

---

### Post by monkeybrain20122 on 2014-04-28
> **raysrdsld said:**
> I have the same problem with no photo's in google earth.I tried this fix but the file I have to edit comes up as read only.? Any help would be appreciated.

Which fix did you try? Which file did you try to edit? If you have successfully installed ge and you just want to see the pictures there is no need to edit any file. Please be more precise in describing your problem.

---

### Post by teklife on 2015-01-30
> **monkeybrain20122 said:**
> Let's say you downloaded foo.tar.xz to Downloads, the idea is to extract it in /opt/google/earth/free and replace the files there with the same names

so you change directory to /opt/google/opt/free and extract 
```
cd /opt/google/earth/free
sudo tar xvf ~/Downloads/foo.tar.xz
```

That's it. I am not making a duplicate and then symlink it. I think it was just for caution that the instructions were like that when they were first posted, but now we know the worst thing that can happen is that it doesn't work, there is no need to back up /opt/google/earth/free

**Edited: **the patch might not have worked for you because you installed a 32 bit google-earth
To install the 64-bit,  first uninstall your version, then download 64 bit ge from google
right click the .deb and click 'extract here" , then delete the origin .deb.  Then open the extracted folder and go to Debian and edit the control file, remove ia32 from the "depends on"
line and now rebuild the .deb as follows:
 Let's say the extracted folder is called google-earth-current-stable_amd64 and it is on your desktop, 
```
cd Desktop
dpkg -b  google-earh-current-stable_amd64
```
Then  install it by right clicking 
It will install but won't run, to run it you need some dependencies
```
sudo apt-get install libc6:i386 lsb-core
```

i followed these instructions exactly, but when i run the command dpkg -b  google-earh-current-stable_amd64, i get, ~/Downloads$ dpkg -b  google-earh-current-stable_amd64
dpkg-deb: error: failed to open package info file `google-earh-current-stable_amd64/DEBIAN/control' for reading: No such file or directory

when i check the folder, the 'control' is there, but also now contains a file named '~control' with a recycle symbol on it(with feanza icon set anyway)

i don't know what else to do.

---

### Post by oldos2er on 2015-01-30
There's a typo in monkeybrain's post, the command should be ```
dpkg -b  google-earth-current-stable_amd64
```

---

