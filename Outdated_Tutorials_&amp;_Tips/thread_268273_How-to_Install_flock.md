---
title: "How-to: Install flock"
date: 2006-09-29
forum: Outdated Tutorials &amp; Tips
---

### Post by akurashy on 2006-09-29
**ATTENTION TO USERS**

**Due to my inexperience back then I did some serious mistakes. Today I fixed a very serious problem that affected some of the applications used in Ubuntu. **

**SYMPTOMS: **

> I have tried to install Flock manually and with a deb package from getdeb.net I think. I have done them both before on other installs and everything worked fine. However this time I could not get Flock to launch at all. I was no big deal though I just decided to continue to use Firefox. That was until I ran across this thread. I decided to give this command a try and see what would happen. 

sudo ln -s /opt/flock/flock /usr/bin/flock

Now my internet is completely broken. I am connected and can download stuff with synaptic but I can not access any websites sites with either firefox, Opera or wget. Can anyone offer any help or suggestions?

For those whose system been affected: sudo rm /usr/bin/flock THEN Please re-install util-linux and everything should be back to normal
[http://packages.ubuntu.com/hardy/util-linux](http://packages.ubuntu.com/hardy/util-linux) for those who are offline and able to install it
dpkg -i DEBFILE.DEB

**NOTE THAT THIS IS ALSO IN THE INSTALLATION CD **

**THIS IS NOT NECESSARY IF YOU ARE DOING IT FOR THE FIRST TIME**

Well this is my first time doing a how-to since I never bothered to post one (well actually my second one I think) 

Well noticed that there wasn't a flock package in ubu repos and in debian repos so I just got tired and did it my own way

First step

```
Download flock
http://flock.com/get-ready-to-flock
```After downloading (note that i'm using the current version that is avaliable to download)

```
tar -xvvzf flock-1.0.3.en-US.linux-i686.tar.gz
```Let's copy it (in the current folder) (using /opt if you don't have one just do sudo mkdir /opt )
```
sudo cp -a flock /opt
```It should've copied everything, now 
```
cd /opt/flock
ls 
(If you see the files then we are ok)
sudo ln -s /opt/flock/flock /usr/bin/flock-browser

```This symbolic link will allow you to just plainly execute it in terminal without going to the folder

Now, I know you aren't just satisfied with just executing it via terminal so make a empty file and paste the following code

```
[Desktop Entry]
Comment=Flock Web browser
Name=Flock
Encoding=UTF-8
Exec=flock-browser
Terminal=false
Comment[en_US]=Flock Web browser
Type=Application
Name[en_US]=Flock
Icon=/opt/flock/icons/mozicon50.xpm

```Save it as ***Flock.desktop*** and place it in your
 ~/.local/share/applications (It's the one that alacarte uses, else just in /usr/share/applications (you need sudo powers to copy it there)

```
cp -a Flock.desktop ~/.local/share/applications
OR
sudo cp -a Flock.desktop /usr/share/applications
```[B]Known errors

[/B][SIZE=3]error while loading shared libraries: libstdc++.so.5
[/SIZE]```
sudo apt-get install libstdc++5
```Other errors? I don't know D:!

[B]User Solutions
[/B][by corney91]("http://ubuntuforums.org/member.php?u=275399")

For those having problem doing symbolic links, do this:

```
sudo ln -s /opt/flock/flock /usr/bin/flock-browser 
```** by sethvath**

SCIM Problems

```
cd to your flock folder then
GTK_IM_MODULE=xim ./flock
```Hope this helped you a lot!

---

### Post by izm81 on 2006-10-02
Thanks for the how-to!

Another known problem, which I received, is the following error message when running flock:

```
./run-mozilla.sh: line 131: 9733 Segmentation fault "$prog" ${1+"$@"}
```

Apparently, this is caused from a problem with SCIM, and can be resolved by disabling SCIM in flock:

```
GTK_IM_MODULE=xim flock
```

For more info on this problem, see [http://www.flock.com/node/4752](http://www.flock.com/node/4752)

For more info on installing Flock (for possible ammendments to this how-to), see [http://www.flock.com/node/4934](http://www.flock.com/node/4934)

Cheers!

---

### Post by akurashy on 2006-10-02
thanks for the addition, i think that happened to me just once but i'm not sure if it was the same error

(It was segmenfault but i guess i didn't care enough since it happens to me also in firefox sometimes (RARE) ) 

For those wanting to use the nightly build it's the same thing, except nightly right now is a bit broken in flock (had to switch back to current stable)

---

### Post by krizz on 2006-10-03
Worked like a charm for me. :) 

I used the [Flock's Plugin Installation Guide]("http://wiki.flock.com/index.php?title=Plugin_Installation_Guide") **Quick Tip** for using all the already installed plugins in firefox.
> Quick Tip: If you already have all the following plug-ins working in a Firefox installation, you can save the trouble of installing again, and just copy everything in your Firefox plugin directory to your Flock plugin directory.

All plugins worked ok (java, flash, Totem Mozilla Plugin), except from mozplugger. I used mozplugger in firefox for [Embed PDFs with Evince in Mozilla/Firefox]("http://ubuntuforums.org/showthread.php?t=25685&highlight=firefox+evince+plugin").

Any idea **how and if is possible to use mozplugger in Flock?**

---

### Post by krizz on 2006-10-04
> All plugins worked ok (java, flash, Totem Mozilla Plugin), except from mozplugger.
My mistake, **All plugins worked :)**

When I coppied the plugins from Firefox to Flock, I copied a relative symlink ( ../.../mozilla/plugins/mozplugger.so) of mozplugger.so.

Trying to find what the problem was, I found this link (in french) that helped me realize my problem (may help others with plugins on Flock). 
[Ubuntu Dapper Drake - Test du navigateur Web Flock]("http://kaisman.free.fr/dotclear/index.php?ubuntu-dapper-drake-test-du-navigateur-web-flock") [ [Translated in English]("http://66.218.71.231/language/translation/translatedPage.php?tt=url&text=http%3a//kaisman.free.fr/dotclear/index.php%3fubuntu-dapper-drake-test-du-navigateur-web-flock&lp=fr_en&.intl=us&fr=flo") ]

---

### Post by Yumi on 2006-10-10
I also copied the mozicon16.xpm icon to usr/share/pixmaps. Now I can add it to my launch panel.

Installed it in Edgy with no lib problems.

Michael

---

### Post by akurashy on 2006-10-11
Great to hear that it works in edgy, 
though why copying the xpm to /share/pixmaps wouldn't it be the same leaving it in /opt (since thats where the icon in the .desktop was directed into it wouldn't have been a problem. in my opinion of course!.

---

### Post by Toxicity999 on 2006-10-16
Reminds me of haxxing up Breezy for Firefox 1.5... ah the memories. Haha. Flock is great I can vouch for it I used ti way back in pre-alpha when it was basically a set of extensions hardcoded into firefox with a new skin =P.

---

### Post by jpmorelli on 2006-10-31
I did follow the tutorial to install flock, everythings works well but when I run flock inmediately exits.
If I did try from terminal this is the error I have:

The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 118 error_code 8 request_code 144 minor_code 3)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

Someone can help ? I'm using Ubuntu 6.10 Edgy Eft. Thanks !] (*,)

---

### Post by vikasrawal on 2007-07-09
I installed flock on my system which runs ubuntu feisty. But when I try to run it, I get "Segmentation fault (core dumped)". It happens 100% of the times.

Any clues?

Vikas

---

### Post by sethvath on 2007-07-10
Flock has an issue with SCIM

Try this in terminal: 
cd to your flock folder then
GTK_IM_MODULE=xim ./flock

---

### Post by Dread Knight on 2007-09-23
> **sethvath said:**
> Flock has an issue with SCIM

Try this in terminal: 
cd to your flock folder then
GTK_IM_MODULE=xim ./flock

Thanks, managed to get Flock running under gutsy with this. :)

Anyway, you can use this in your Flock.desktop config file in order to have the Flock shorcut icon to appear in the menu under the Network/Internet category:

```
[Desktop Entry]
Comment=Flock Web browser
Name=Flock
Encoding=UTF-8
Exec=flock
Terminal=false
Comment[en_US]=Flock Web browser
Type=Application
Name[en_US]=Flock
Icon=/opt/flock/icons/mozicon50.xpm
Categories=Network;Application;
```



Flock on :guitar:

---

### Post by Dread Knight on 2007-09-23
> **sethvath said:**
> Flock has an issue with SCIM

Try this in terminal: 
cd to your flock folder then
GTK_IM_MODULE=xim ./flock

Seems i have to do this everytime to get flock running. Isn't there a solution for this? :( Thanks.

---

### Post by corney91 on 2007-09-25
Cheers for the How-to.

Thought I'd add a note, as I ran into a problem. I already had a program called flock installed so instead of:
```
sudo ln -s /opt/flock/flock /usr/bin/flock
```
I ran:
```
sudo ln -s /opt/flock/flock /usr/bin/flock-browser
```
and changed /opt/flock-bin to /opt/flock-browser-bin and edited the command in alacarte to flock-browser.

Thought this might help at least someone :).

---

### Post by Lord C on 2007-10-18
> **corney91 said:**
> Cheers for the How-to.

Thought I'd add a note, as I ran into a problem. I already had a program called flock installed so instead of:
```
sudo ln -s /opt/flock/flock /usr/bin/flock
```
I ran:
```
sudo ln -s /opt/flock/flock /usr/bin/flock-browser
```
and changed /opt/flock-bin to /opt/flock-browser-bin and edited the command in alacarte to flock-browser.

Thought this might help at least someone :).

Thanks! That helped a lot.

I was wondering wth was going on when trying to run Flock.

Realised the symbolic wasn't actually created, as something else was using the name Flock!

---

### Post by meho_r on 2007-11-06
Am I missing something? I installed Flock v.1 from getdeb (64bit, Gutsy), but I can't make java and mplayer plugins to work. Flash is working (although on YouTube i.e. there's no animated windows on the top of window; however, video is working).

So, how to set things up? I'm using icedtea plugin for Firefox and it's working (updated version from 10/18 ).

BTW, ''about: plugins'' states that only Shockwave Flash plugin is installed. I have no other plugins recognized :confused: although Firefox has them. Symbolic link to Firefox plugins folder didn't change a thing.

---

### Post by meho_r on 2007-11-07
Well, I don't know is it proper way but I managed to make java work. Just done symbolic link from /usr/lib64/jvm/ia32-java-6-sun-1.6.0.03/jre/plugin/i386/ns7/libjavaplugin_oji.so to /usr/share/flock/plugins

Hope this help if someone has similar problem

---

### Post by akurashy on 2007-12-25
> **meho_r said:**
> Well, I don't know is it proper way but I managed to make java work. Just done symbolic link from /usr/lib64/jvm/ia32-java-6-sun-1.6.0.03/jre/plugin/i386/ns7/libjavaplugin_oji.so to /usr/share/flock/plugins

Hope this help if someone has similar problem

Just a future reference, you can put the plug-in in your home folder

Gnome users: Places -> Home 
Press CTRL + H -> search for .flock folder -> Place it in plugins folder , if there's no plugins folder create one "plugins" and deposit it there

Second option: 

Go to your /opt/flock/plugins and deposit the plugin there

Third: 
meho_r;3722098 option!

One more thing, remember to keep updated your flash version people :) and java

---

### Post by theZoid on 2007-12-26
> **corney91 said:**
> Cheers for the How-to.

Thought I'd add a note, as I ran into a problem. I already had a program called flock installed so instead of:
```
sudo ln -s /opt/flock/flock /usr/bin/flock
```
I ran:
```
sudo ln -s /opt/flock/flock /usr/bin/flock-browser
```
and changed /opt/flock-bin to /opt/flock-browser-bin and edited the command in alacarte to flock-browser.

Thought this might help at least someone :).

That did it for me too.....I'm just catching up on all of this!  thanks!

---

### Post by theZoid on 2008-03-24
> **akurashy said:**
> Well this is my first time doing a how-to since I never bothered to post one (well actually my second one I think) 

Well noticed that there wasn't a flock package in ubu repos and in debian repos so I just got tired and did it my own way

First step

```
Download flock
http://flock.com/get-ready-to-flock
```After downloading (note that i'm using the current version that is avaliable to download)

snip..................................

** by sethvath**

SCIM Problems

```
cd to your flock folder then
GTK_IM_MODULE=xim ./flock
```Hope this helped you a lot!

Akurashy, could you incorporate post 12 and post 14 into your instructions to make it complete and clean it up for posterity?  thanks

---

### Post by the_goose84 on 2008-03-28
I have tried to install Flock manually and with a deb package from getdeb.net I think. I have done them both before on other installs and everything worked fine. However this time I could not get Flock to launch at all. I was no big deal though I just decided to continue to use Firefox. That was until I ran across this thread. I decided to give this command a try and see what would happen. 

sudo ln -s /opt/flock/flock /usr/bin/flock

Now my internet is completely broken. I am connected and can download stuff with synaptic but I can not access any websites sites with either firefox, Opera or wget.  Can anyone offer any help or suggestions?

---

### Post by akurashy on 2008-04-13
@the_goose84: 

Please go to synaptic and reinstall flock. The issue is as mentioned before that flock is another package that ubuntu uses. When I mean reinstall flock, is not the browser but the OTHER flock. 

_[U]@theZoid: I apologize for my super late replies. I'll rebuild the How-To including the latest solutions offered by the users. _
 [/U]

---

### Post by akurashy on 2008-04-13
> **the_goose84 said:**
> I have tried to install Flock manually and with a deb package from getdeb.net I think. I have done them both before on other installs and everything worked fine. However this time I could not get Flock to launch at all. I was no big deal though I just decided to continue to use Firefox. That was until I ran across this thread. I decided to give this command a try and see what would happen. 

sudo ln -s /opt/flock/flock /usr/bin/flock

Now my internet is completely broken. I am connected and can download stuff with synaptic but I can not access any websites sites with either firefox, Opera or wget.  Can anyone offer any help or suggestions?


For those whose system been affected: sudo rm /usr/bin/flock THEN Please re-install util-linux and everything should be back to normal
[http://packages.ubuntu.com/hardy/util-linux](http://packages.ubuntu.com/hardy/util-linux) for those who are offline and able to install it
dpkg -i DEBFILE.DEB

**NOTE THAT THIS IS ALSO IN THE INSTALLATION CD **


I apologize.

---

### Post by aleska on 2008-05-29
Hey, the link to the flock directions on getting all your firefox plugins copied over to flock now goes to a page that doesn't exist, and I can't seem to find the article.

So, the manual way of doing it...

Where would I normally find my firefox plugins to copy over?

under my home directory, there is ".mozilla". This has two folders "extensions" and "firefox".  Under firefox, there is a file "profiles.ini" and a folder "qff73nfj.deafult".  In that folder there is a whole bunch of stuff, including one file called "pluginreg.dat".  

Anyway, I'm totally confused about what files or folders I'm supposed to copy over...to where and from where.  

Any help greatly appreciated!

Thanks!

---

### Post by redjoel on 2008-07-28
Nice Post!
I will Try it at home!!:popcorn::guitar::lolflag:

---

### Post by okaoka on 2008-08-03
Really useful. 
thanks
O:)

---

### Post by roninbk on 2009-03-30
Just a quick update, Flock is currently available for Linux as a .bz2 file, therefore you would use the following command to untar it:
```
tar -xjvf flock-2.0.3.eb-US.linux-i686.tar.bz2
```
Otherwise, follow the rest of the instructions as laid out

---

### Post by theZoid on 2009-03-30
> **roninbk said:**
> Just a quick update, Flock is currently available for Linux as a .bz2 file, therefore you would use the following command to untar it:
```
tar -xjvf flock-2.0.3.eb-US.linux-i686.tar.bz2
```
Otherwise, follow the rest of the instructions as laid out

there's a .deb file on getdeb.net, makes it much easier.  FYI

---

