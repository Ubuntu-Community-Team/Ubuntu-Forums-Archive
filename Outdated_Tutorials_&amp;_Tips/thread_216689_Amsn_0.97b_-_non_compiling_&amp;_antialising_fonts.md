---
title: "Amsn 0.97b - non compiling &amp; antialising fonts &amp; no tab bug &amp; lot more!"
date: 2006-07-15
forum: Outdated Tutorials &amp; Tips
---

### Post by manzuk on 2006-07-15
I remember my first steps with ubuntu, seven months ago. I've lernt a lot since those days, and I do understand people who need to use MSN and finds _**Amsn extreamly uggly**_.

_**Is this your problem?**_
If it is, you should know the issue is the version from the official repositories which doesn't use antialising fonts.
You can download 0.95 from the Amsn website also, but the fonts will be as ugly as they are in ubuntu's version.

_**Is there a solution?**_
Obviously there is! And is here in this post.
I made this easy and straight forward HowTo.
Hope you like it...

_**The easy-and-straight-forward HowTo**_

**First step:**
You'll need Tcl8.5 and Tk8.5.
"But those packages are not in the repositories, so what should I do?" you might wonder. Don't worry, Neto has made those packages for you, and you can find them here:

[I][http://www.doeweling.com/files/ubuntu/amsn/tcl8.5_8.5.0-1~neto3_i386.deb](http://www.doeweling.com/files/ubuntu/amsn/tcl8.5_8.5.0-1~neto3_i386.deb)
[http://www.doeweling.com/files/ubuntu/amsn/tk8.5_8.5.0-1~neto3_i386.deb](http://www.doeweling.com/files/ubuntu/amsn/tk8.5_8.5.0-1~neto3_i386.deb)[/I]

_[COLOR="DarkOrange"]TIP:[/COLOR]_ you can download files from a terminal typing "wget AdressOfTheFile". In this case it'd be:
```
wget http://www.doeweling.com/files/ubuntu/amsn/tcl8.5_8.5.0-1~neto3_i386.deb
wget http://www.doeweling.com/files/ubuntu/amsn/tk8.5_8.5.0-1~neto3_i386.deb
```
Thanks again Neto!!

**Second step:**
Now you have to download the package I made my self of Amsn0.97b (located on *[http://cablemodem.fibertel.com.ar/mnzk/amsn_0.97b_tcl0.95.deb](http://cablemodem.fibertel.com.ar/mnzk/amsn_0.97b_tcl0.95.deb)*)

It's as easy as, from a console:
```
wget http://cablemodem.fibertel.com.ar/mnzk/amsn_0.97b_tcl0.95.deb
```
(You remember what wget was for right?)

**Third step:**
Install the three packages you downloaded: first ***Tcl8.5*** & ***Tk8.5*** | and then ***Ams0.97b***

If you're an _Ubuntu user_, just double-click them, and Gdebi will do the rest for you (it will even install all needed dependencies!)
_Kubuntu users_, you can right-clic them, select "Kubuntu Package Menu -> Install Package" but remember you must have the needed dependencies installed beforehand.
Or _Whatever-users_, from a console go to where the packages are, and then type:
```
sudo dpkg -i tcl8.5_8.5.0-1~neto3_i386.deb tk8.5_8.5.0-1~neto3_i386.deb amsn_0.97b_tcl0.95.deb
```

_[COLOR="DarkOrange"]TIP (for nonUbuntu users):[/COLOR]_ If I were you, I'd install (from the repositories) "Gdebi", which is a great app to intall packages, because as I said before, it takes care of dependencies!
*To use it, (for instance in Kubuntu) when you want to open a .deb, just choose "open with", then "Other" and write gdebi-gtk*

**Fourth step:**
Launch Amsn! From a console:
```
amsn
```

If it gives an error, try doing:
```
cd /usr/lib
sudo ln -sf libtk8.5.so.0 libtk8.5.so
sudo ln -sf libtcl8.5.so.0 libtcl8.5.so
```
And then launch amsn again; now it should work ok.

**Fifth step:**
Enjoy Amsn0.97! (and **[donate]("http://amsn.sourceforge.net/donations.php")** some money to its incredible developers)

Post any comments or errors! Bye.

---

### Post by JMO707 on 2006-07-16
Fantastic!, so easy!

Can you please post the changelong of this version?

Thanks for the package ;)

---

### Post by Poka64 on 2006-07-17
maybe not the right place to ask, but how do I uninstall the cvs version of amsn, i did the whole "make install" procedure, but I can't "make uninstall" :/

Edit: I'm not sure If I used cvs or svn...

EDit: solved it and I isntalled this package, works for me, nice to use amsn without crappy fonts :)

---

### Post by Rackerz on 2006-07-17
Nice Howto I'm going to try it later. I can only see 0.96RC1 on the aMSN website though.

EDIT: Worked perfectly, thanks.

---

### Post by Gonzakpo on 2006-07-17
Is there a amsn 0.97b version? I thought the 0.96 RC1 was the latest...

Could somebody post an screeshot of this (supposed) beautiful amsn? I'm wondering if the change is worth it.

Thanks.

---

### Post by kpolice on 2006-07-17
I did my own deb and it's a custom skin but the antialiased fonts is the biggest change.
[http://www.capc-online.net/images/desktops/desktop-170706-131545.jpg](http://www.capc-online.net/images/desktops/desktop-170706-131545.jpg)

---

### Post by pain of salvation on 2006-07-17
0.97b? aMSN home page shows only version 0.96 RC

---

### Post by kpolice on 2006-07-17
If you use the svn and compile it yourself you will get 0.97b.

---

### Post by wakady on 2006-07-17
> **kpolice said:**
> I did my own deb and it's a custom skin but the antialiased fonts is the biggest change.
[http://www.capc-online.net/images/desktops/desktop-170706-131545.jpg](http://www.capc-online.net/images/desktops/desktop-170706-131545.jpg)

How can i get my desktop to look like this ???!!!
please i need this themes,icons,curved taskbar, control center, menu, application browser,....etc all
its AMAZING](*,)

---

### Post by Rackerz on 2006-07-17
Anybody notice a lot of crashing by tcl and tk?

---

### Post by lightubun on 2006-07-18
thank you for the how-to

one question... how to be able to change the fonts!
from Left To Right... like arabic
i can see the characters right, but in reverse order.
using utf-8 didnt solved anything.
same with precompiled amsn95 and/or compiling svn.

thanks.

---

### Post by manzuk on 2006-07-19
That's a good one; don't really know. If I were you I'd try to compile it myself.
I'll see what I can find out. Bye!

---

### Post by NevidS on 2006-07-22
Very nice, but... why after I follow youre guide if I look inside help menu I read amns 0.95 like screenshot? Maybe there is also the old versione and my kubuntu run that?
[IMG]http://img134.imageshack.us/img134/3720/temp4iq0.jpg[/IMG]

---

### Post by ironfistchamp on 2006-07-23
You beauty. Worked straight off the bat. I had my doubts (first time using 64bit and have heard that nothing works) but it worked wonderfully. Nevid that does look like you have an old version running. Did you have it installed before? If so you probably should uninstall it and then follow the guide.

Thanks again

Ironfistchamp

---

### Post by WillyTP on 2006-07-23
Thank you very much, works perfectly :)

---

### Post by NevidS on 2006-07-24
> **ironfistchamp said:**
> Nevid that does look like you have an old version running. Did you have it installed before? If so you probably should uninstall it and then follow the guide.

yes, that's the problem! :rolleyes: 
Sorry for the stupid question :-#

---

### Post by ironfistchamp on 2006-07-25
Hehe I'm just glad I got something right. Just managed to get this on my brothers computer (managed to convert him with Guitar programs).

Thanks again

Ironfistchamp

---

### Post by Beire on 2006-07-25
i'm getting the following error while loading amsn with your package.

```

Loading TkCximage failed.
TkCximage this is needed to run aMSN.
Please compile AMSN first.
Instruction on how to compile are
located in the file INSTALL.

```

---

### Post by manzuk on 2006-07-25
Mmm... On vacations right now, so I don't have Ubuntu running (I'm using this uggly OS; guess what I'm talking about)
Let's get to the point.
I don't really know what the problem is. Have you ever installed Amsn before? Amsn0.97 might be needing some dependecies not satisfied. So, why don't you try installing the version from official repositories first, and then, installing the package from this post?
Tell me what happens... Hope it helps

---

### Post by Beire on 2006-07-26
> **manzuk said:**
> Mmm... On vacations right now, so I don't have Ubuntu running (I'm using this uggly OS; guess what I'm talking about)
Let's get to the point.
I don't really know what the problem is. Have you ever installed Amsn before? Amsn0.97 might be needing some dependecies not satisfied. So, why don't you try installing the version from official repositories first, and then, installing the package from this post?
Tell me what happens... Hope it helps

i have been using the repo version for quite some time now. That worked flawlessly.

I only haven the problem with this 0.97b package.

---

### Post by Cyfr on 2006-07-26
Seemed to work flawlessly, but I get amsn errors whenever I click the filetransfer button..

---

### Post by vuitton on 2006-07-26
Thank you very much, finally aMSN has become useable :)

---

### Post by apocalypso on 2006-07-26
Sorry, I posted this message on a little bit of a hurry, so I didn't include any background information.

Basically the tale goes like this: I'm running Ubuntu for 686, latest kernel, and had been using aMSN -the version available on the repositories- until last week, when it, unexplainable, stopped working, just like that... :( One day I was chatting as usual, the other day when I logged back it won't start.

Whenever I tried to run from Applications - Internet - aMSN, it just shows the tab on the panel reading "Starting aMSN" (or in my Spanish installation, "Iniciando aMSN") which then just disappears.

So, I uninstalled my aMSN version and after following the steps herein pretty carefully all I get is this message when I try to run from the terminal:
```
Application initialization failed: this isn't a Tk applicationunknown color name "Black"
``` ](*,) 

(Running from the Applications menu still yields the same result as described above).

I'd appreciate your input buddies!!!

---

### Post by patrickfromspain on 2006-07-26
For those who get error when trying to browse for something to search or change your image, a friend of mine gave me a great solution: install the desktop integration plugin, that will replace the file browsing tk/tcl dialog with a fully working gtk one.

---

### Post by ironfistchamp on 2006-07-26
apocalypso have you uninstalled your previous Tcl and Tk installations. Make sure you have got rid of them completely. I had that problem, removed TCL and TK and reinstalled. The problem went and all was well.

---

### Post by Xecuter on 2006-07-26
I get an error: ```
wish: error while loading shared libraries: libtk8.5.so: cannot open shared object file: No such file or directory

```

I'm on Dapper.

---

### Post by apocalypso on 2006-07-26
> **ironfistchamp said:**
> apocalypso have you uninstalled your previous Tcl and Tk installations. Make sure you have got rid of them completely. I had that problem, removed TCL and TK and reinstalled. The problem went and all was well.

Thanks for the input buddy, I'll give your hint a try as soon as I'm done with some nasty business (read: XP)... :p

I'll let you know whatever the outcome.

---

### Post by manzuk on 2006-07-26
**Xecuter**, try doing this (from a terminal):
```
cd /usr/lib
sudo ln -sf libtk8.5.so.0 libtk8.5.so
sudo ln -sf libtcl8.5.so.0 libtcl8.5.so
```
I think it should solve the problem...

---

### Post by apocalypso on 2006-07-26
> **ironfistchamp said:**
> apocalypso have you uninstalled your previous Tcl and Tk installations. Make sure you have got rid of them completely. I had that problem, removed TCL and TK and reinstalled. The problem went and all was well.

Hmmm... removing both tcl8.4 and tk8.4 requires me to also uninstall ubuntu-desktop (and a handful of other dependencies)... :-k 

Not quite sure about doing it right now, maybe I'll wait, too much of a fuss to get aMSN working again, specially considering just last week it was working 100% ok!

---

### Post by Xecuter on 2006-07-27
> **manzuk said:**
> **Xecuter**, try doing this (from a terminal):
```
cd /usr/lib
sudo ln -sf libtk8.5.so.0 libtk8.5.so
sudo ln -sf libtcl8.5.so.0 libtcl8.5.so
```
I think it should solve the problem...

OMG! I'm a noob. I totally didn't see that I were supposed browse /usr/lib. I had done it in my home directory!](*,) ](*,)

---

### Post by apocalypso on 2006-07-30
> **apocalypso said:**
> Hmmm... removing both tcl8.4 and tk8.4 requires me to also uninstall ubuntu-desktop (and a handful of other dependencies)... :-k 

Not quite sure about doing it right now, maybe I'll wait, too much of a fuss to get aMSN working again, specially considering just last week it was working 100% ok!

Okay, I just did it, but to no avail - that is, I uninstalled tcl8.4 and tk8.4, installed their respective 8.5 versions and went for the aMSN, but nothing, same "Application initialization failed: this isn't a Tk applicationunknown color name "Black"" error... ](*,)  

Maybe I'll wait till all of these packages get official upgrades... in the meantime, there's Gaim... :confused:

---

### Post by kpolice on 2006-07-30
> **apocalypso said:**
> Okay, I just did it, but to no avail - that is, I uninstalled tcl8.4 and tk8.4, installed their respective 8.5 versions and went for the aMSN, but nothing, same "Application initialization failed: this isn't a Tk applicationunknown color name "Black"" error... ](*,)  

Maybe I'll wait till all of these packages get official upgrades... in the meantime, there's Gaim... :confused:

From the aMSN wiki:
> Q: When I try running aMSN, I get an error "unknown color Black". How can I fix it ?
A: This problem is not coming from aMSN, it's an Xorg faulty installation. You probably have a bad Xorg configuration for the file rgb.txt (especially with some versions of Xgl).

If you are using xgl, you most probably have the file rgb.txt in /etc/X11 . Xgl in Ubuntu Dapper is usually misconfigured and looks for the file in /usr/share/X11 . Make a symlink to it in /usr/share/X11 and restart your X server.

If you are not using xgl, open your /etc/X11/xorg.conf and look for a line that says:


Section "Files"
       RgbPath      "/etc/X11/rgb"


If the RgbPath line does not exist at all, add it under the section "Files". Then make sure the file exists in the directory defined in RgbPath (/etc/X11/ in this case). You may need to copy it from another location in your computer, or you can download it from [http://amsn.sourceforge.net/rgb.txt](http://amsn.sourceforge.net/rgb.txt) . You must also restart your X server for the changes to take effect. PLEASE NOTE: the line in xorg.conf must NOT contain the extension of the file!!! 

Oh BTW I build my own deb if anybody wants to try it, it also requires tcl/tk 8.5. I'm running dapper with the latest updates.

[http://www.capc-online.net/dloads/linux/amsn_0.97bcvs-20060515.deb](http://www.capc-online.net/dloads/linux/amsn_0.97bcvs-20060515.deb)

---

### Post by digitalbrainstorm on 2006-07-31
If you experience a Tk error when you are about to Browse the files to select a new avatar (Display Pictures Browser), replace the /usr/lib/tk8.5/tkfbox.tcl that comes with tk8.5_8.5.0-1~neto3_i386.deb package with the one from [http://tktoolkit.cvs.sourceforge.net/*checkout*/tktoolkit/tk/library/tkfbox.tcl?revision=1.58]("http://tktoolkit.cvs.sourceforge.net/*checkout*/tktoolkit/tk/library/tkfbox.tcl?revision=1.58")

This is a dirty hack but solved the problem. I tried the desktop integration plugin but (unfortunately) it does not work for me.

---

### Post by kpolice on 2006-07-31
Did you tried the latest version of the plugin?? v1.0??

---

### Post by apocalypso on 2006-08-04
> **kpolice said:**
> From the aMSN wiki:


Oh BTW I build my own deb if anybody wants to try it, it also requires tcl/tk 8.5. I'm running dapper with the latest updates.

[http://www.capc-online.net/dloads/linux/amsn_0.97bcvs-20060515.deb](http://www.capc-online.net/dloads/linux/amsn_0.97bcvs-20060515.deb)

Thanks for this hint dude, I gotta make a mental note to check out wikis more often...! :!: 

I'll be giving this one a try since I do have Xgl in place. I'll let you know whatever the outcome, and thanks again! :-P

---

### Post by darden68 on 2006-08-05
> **digitalbrainstorm said:**
> replace the /usr/lib/tk8.5/tkfbox.tcl that comes with tk8.5_8.5.0-1~neto3_i386.deb package with the one from [http://tktoolkit.cvs.sourceforge.net/*checkout*/tktoolkit/tk/library/tkfbox.tcl?revision=1.58]("http://tktoolkit.cvs.sourceforge.net/*checkout*/tktoolkit/tk/library/tkfbox.tcl?revision=1.58")


Thanks I was so looking for that fix ! I can now send files again...

---

### Post by apocalypso on 2006-08-05
> **kpolice said:**
> From the aMSN wiki:


Oh BTW I build my own deb if anybody wants to try it, it also requires tcl/tk 8.5. I'm running dapper with the latest updates.

[http://www.capc-online.net/dloads/linux/amsn_0.97bcvs-20060515.deb](http://www.capc-online.net/dloads/linux/amsn_0.97bcvs-20060515.deb)
Finally worked!!! Actually, I had to update my XGL-Compiz setup, which wasn't working at all (I quite didn't make the connection between XGL-Compiz and aMSN not working :-x ).

Well, thanks a lot!

---

### Post by digitalbrainstorm on 2006-08-06
> **kpolice said:**
> Did you tried the latest version of the plugin?? v1.0??
I just tried it. It works much better indeed.

---

### Post by Dropknee on 2006-08-08
The plug-in work great thx. :D

---

### Post by vaazu on 2006-08-08
When I try to send files it says
 unknown subcommand "config": must be SetWidth, or configure
    while executing
"$data(sbar) config -command [list $data(canvas) xview]"
    (procedure "IconList_Create" line 10)
    invoked from within
"IconList_Create $w"
    (procedure "::tk::IconList" line 3)
    invoked from within
"::tk::IconList $w.icons  -command	$iconListCommand  -multiple	$data(-multiple)"
    (procedure "::tk::dialog::file::Create" line 51)
    invoked from within
"::tk::dialog::file::Create $w TkFDialog"
    (procedure "::tk::dialog::file::" line 17)
    invoked from within
"::tk::dialog::file:: open -filetypes {{ "All Files" {*} }} -parent .msg_0 -initialdir /home/vahur -initialfile {} -title {Send File}"
    ("eval" body line 1)
    invoked from within
"eval ::tk::dialog::file:: open $args"
    (procedure "tk_getOpenFile" line 5)
    invoked from within
"tk_getOpenFile -filetypes $types -parent $parent -initialdir $starting_dir -initialfile $initialfile -title $title"
    (procedure "chooseFileDialog" line 17)
    invoked from within
"chooseFileDialog "" [trans sendfile] $win_name"
    (procedure "::amsn::FileTransferSend" line 10)
    invoked from within
"::amsn::FileTransferSend .msg_0"
    (command bound to event)

and how can I make amsn play sounds when i receive message the sound server is artsplay $sound

---

### Post by orgy on 2006-08-08
thx worked great :D

---

### Post by Xecuter on 2006-08-11
> **patrickfromspain said:**
> For those who get error when trying to browse for something to search or change your image, a friend of mine gave me a great solution: install the desktop integration plugin, that will replace the file browsing tk/tcl dialog with a fully working gtk one.

I can't find this in Synaptic. What is it named?

---

### Post by ba5e on 2006-08-11
What a great howto!! thanks! Now amsn looks good! 

One problem that the menus 'stick' when you move you mouse over them (once you have clicked on one to start with)

Otherwise top effort! :)

---

### Post by Dropknee on 2006-08-12
My Amsn work great with the integration plug-in, but I cant fix the emotion screen, When I try to send a emotion and I click the emotion windows and try to select the emotion to send it, this simply dont work, I send emotion via keyboard shortcut without problem, but have the above problem.

anyone know how to fix it?? thx

---

### Post by Xecuter on 2006-08-12
> **Dropknee said:**
> My Amsn work great with the integration plug-in, but I cant fix the emotion screen, When I try to send a emotion and I click the emotion windows and try to select the emotion to send it, this simply dont work, I send emotion via keyboard shortcut without problem, but have the above problem.

anyone know how to fix it?? thx

What's the integration plugin named? Can't find it in Synaptic.

---

### Post by Dropknee on 2006-08-12
you can download the Desktop integration plug in [here]("http://prdownloads.sourceforge.net/amsn/desktop_integration-1.1.zip")

---

### Post by seshomaru samma on 2006-08-16
thanks,
If only aMSN would support Chinese....

---

### Post by kno on 2006-08-16
Thanks manzuk and others

---

### Post by spockrock on 2006-08-16
thanks this works perfectly and looks snazz.... I also have the same emoticon menu problem as dropknee.

---

### Post by picpak on 2006-08-18
My sister just upgraded to this version, and she can't see her custom emoticons in conversations. 

They're all there in the menu, so this isn't the same problem the other people have.  They also don't work if she types them in either.  The other person she is talking to can see them, whether she types them in or clicks on them, but all she sees is the text either way. The only time she can see them is if she gets a "This message could not be sent" error.

All of the "emoticon" options are selected.  She's tried re-starting, un-selecting them, re-starting, re-selecting them, and re-starting again.  She also tried restarting the whole computer. Twice.

She's even tried removing all of her emoticons and putting them all back in, which took hours (really, it did).

Anyone have any ideas?  She's really frustrated.  :(

*EDIT* Problem fixed! She disabled aMSN Plus.

---

### Post by alcamus on 2006-08-20
Many thanks for this effort. MSN Messenger was the last reason I was clinging to Windows XP -- I needed the webcam to work and couldn't get it to function in Gaim, but I couldn't bear to look at aMSN's fonts. This solves the problem and frees me from any ties to XP. Great work.

---

### Post by Demio on 2006-09-07
omg /love!

Someone should sticky this! For the good of mankind! :mrgreen: 

I love you man, you made my day.

---

### Post by Psychobudgie on 2006-09-11
Excellent Job

---

### Post by ramcosca on 2006-09-11
Uhm... a little help here, please? ```
Setting up tcl8.5 (8.5.0-1~neto3) ...

Setting up tk8.5 (8.5.0-1~neto3) ...

dpkg: dependency problems prevent configuration of amsn:
 amsn depends on tcltls; however:
  Package tcltls is not installed.
dpkg: error processing amsn (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 amsn
ramcosca@ramcosca-laptop:~$

```

---

### Post by David Corrales on 2006-09-11
**sudo apt-get install tcltls**

---

### Post by ramcosca on 2006-09-11
Thanks but... ```
ramcosca@ramcosca-laptop:~$ sudo apt-get install tcltls
Password:
Reading package lists... Done
Building dependency tree... Done
Package tcltls is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package tcltls has no installation candidate
ramcosca@ramcosca-laptop:~$

```

---

### Post by jpyanowski on 2006-09-11
Thanks for the great how-to. It looks great.

---

### Post by spockrock on 2006-09-12
it seems that my beta verson of amsn all of a sudden doesnt let me change the display pics or send files, I keep getting an amsn error. :( Uninstalling and re-installing doesnt work.

---

### Post by hexion on 2006-09-12
Please, add to the howto these urls, since the ones listed doesn't work:

[http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/tk8.5_8.5.0-1~neto3_i386.deb](http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/tk8.5_8.5.0-1~neto3_i386.deb)
[http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/tcl8.5_8.5.0-1~neto3_i386.deb](http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/tcl8.5_8.5.0-1~neto3_i386.deb)

---

### Post by JMO707 on 2006-09-12
> **spockrock said:**
> it seems that my beta verson of amsn all of a sudden doesnt let me change the display pics or send files, I keep getting an amsn error. :( Uninstalling and re-installing doesnt work.

Same here. A TCL/TK error. Dont have that version anymore so cant paste it here.

---

### Post by vivia on 2006-09-13
<POST EDITED>

About the bugs you are all getting:

The tcl/tk packages just need to be upgraded to the latest version available : [http://tcl.tk/software/tcltk/8.5.html](http://tcl.tk/software/tcltk/8.5.html)

Until then, you can fetch them from here: [http://www.autom.teithe.gr/~vivia/index82](http://www.autom.teithe.gr/~vivia/index82)

---

### Post by vivia on 2006-09-13
If you want aMSN to appear even better, install the Chameleon and Desktop Integration plugin. Both available if you do this:

cd ~/.amsn
sudo apt-get install subversion
svn checkout [https://svn.sourceforge.net/svnroot/amsn/trunk/amsn-extras/plugins](https://svn.sourceforge.net/svnroot/amsn/trunk/amsn-extras/plugins)

or, of course, from [http://amsn.sourceforge.net](http://amsn.sourceforge.net) and extracting to ~/.amsn/plugins --- MAKE SURE YOU HAVE AUTOMATIC UPDATE ENABLED IF YOU DO THIS

---

### Post by spockrock on 2006-09-13
> **vivia said:**
> <POST EDITED>

About the bugs you are all getting:

The tcl/tk packages just need to be upgraded to the latest version available : [http://tcl.tk/software/tcltk/8.5.html](http://tcl.tk/software/tcltk/8.5.html)

Until then, you can fetch them from here: [http://www.autom.teithe.gr/~vivia/index82](http://www.autom.teithe.gr/~vivia/index82)

when I dpkg them I am told I am downgrading the package.  is it just bad naming schemes?

---

### Post by joakim2 on 2006-09-14
> **vivia said:**
> <POST EDITED>

About the bugs you are all getting:

The tcl/tk packages just need to be upgraded to the latest version available : [http://tcl.tk/software/tcltk/8.5.html](http://tcl.tk/software/tcltk/8.5.html)

Until then, you can fetch them from here: [http://www.autom.teithe.gr/~vivia/index82](http://www.autom.teithe.gr/~vivia/index82)

I installed these packages but now trying to start amsn gives:

Error in startup script: can't find package msgcat 1.4

---

### Post by vivia on 2006-09-14
spockrock : i suppose so, yes... do install them

joakim2 : I told the person who created these packages to check this error...

---

### Post by GuS-Arg on 2006-09-14
> **joakim2 said:**
> I installed these packages but now trying to start amsn gives:

Error in startup script: can't find package msgcat 1.4

Yeah, i made those packages... seems that have a makefile problem. Download tcl8.5a4 source and copy entire dir from tcl8.5a4/library/msgcat/ to /usr/lib/tcl8.5 and then, will work.

Meanwhile i will try to fix that.

---

### Post by Dinerty on 2006-09-14
Great guide worked a treat !

---

### Post by raf-it on 2006-09-30
i've try to do all the things wrote here but my Amsn doesn't work yet.
I receive an error message:
Tk has find an error, there's a bug in Amsn send the report etc...

What can i do? 

**[COLOR="Red"]this is the detail[/COLOR]**

bad variable name "options(-proxy_writing)": upvar won't create a scalar variable that looks like an array element
    while executing
"upvar 1 ::ProxyHTTP::Snit_inst2::options(-proxy_writing) options(-proxy_writing)"
    ("uplevel" body line 1)
    invoked from within
"uplevel 1 [list upvar 1 ${selfns}::$varname $varname]"
    (procedure "::snit::RT.variable" line 5)
    invoked from within
"variable options(-proxy_writing)"
    (procedure "::ProxyHTTP::Snit_methodHTTPRead" line 8)
    invoked from within
"$self HTTPRead $sb"
    (procedure "::ProxyHTTP::Snit_methodConnectReply" line 5)
    invoked from within
"::Proxy::ProxyHTTP1 ConnectReply ns sock10"

---

### Post by vivia on 2006-10-05
Hi,

This bug has been fixed. Download the SVN version of aMSN again.

Thanx for reporting :)

---

### Post by Old Pink on 2006-10-09
Looks great, but I can't send files. :(

---

### Post by jpyanowski on 2006-10-12
Thanks for this how-to. I had to read almost all of it (which I should have done in the first place :rolleyes: ) but everything is running and looking great.

---

### Post by sakis on 2006-10-15
Thank you very much for this how-to! The graphical environment was the only reason that i did't want to use amsn, but now everything works great, thanks to you :mrgreen:

---

### Post by domino on 2006-10-17
For Edgy, you'll need to go [here]("http://amsn.sourceforge.net/wiki/tiki-index.php?page=Installation+Instructions#tcl/tk") and follow the instructions. **Get the the tcl and tk nightly cvs snapshots from FTP** and proceed to install tcl and tk from the instruction. You might get errors when using the sudo command to install. In that case, just su to root. You don't need to recompile amsn anymore since the package posted on this thread is already compiled using tcl/tk 8.5.

When you first start amsn, it will ask you that TSL needs to be updated for msn9. Choose what ever arch you have and continue the download. Finally, you must restart amsn for changes to take effect.

I have only briefly tested this, but I haven't had any problems like tk crashing since I have upgraded. I can not confirm this on Dapper, but I hope that helps the Edgy folks.

---

### Post by boast on 2006-10-18
how do you run amsn? I get the following

```
user@UBUNTUBOX:~$ amsn
/usr/local/bin/amsn: line 3: exec: wish: not found

```

---

### Post by kpolice on 2006-10-18
Do you have tcl and tk installed?

---

### Post by boast on 2006-10-18
I believe so.. (im assuming since i was able to compile it)

---

### Post by boast on 2006-10-19
Yeah. I compile and make install amsn fine with no problems/errors, but I get  ```
/usr/local/bin/amsn: line 3: exec: wish: not found
``` and through menu amsn just starts and closes itself.

---

### Post by Old Pink on 2006-10-20
aMSN is now very slow at times (3Ghz, 1GB RAM System) and tk often crashes. 

I can't send files, I'm lucky if I can receive files, and when opening an aMSN related window from the list of tasks, I find myself having to wait around 10 seconds. It also pauses during typing.

I don't reccomend this fix at all, although there are some nice new features in 0.97b.

---

### Post by chakkid on 2006-10-20
now i can use amsn with bying so ugly. tks**manzuk**:) ;)

---

### Post by freddan83 on 2006-10-21
i have installed tcl 8.5 and tk 8.5, downloaded and recompiled amsn and even tryed one of the packages here, the checkboxes are now red with black in but the fonts are still ugly as hell, any advices?

---

### Post by Argus on 2006-10-21
Thanks,

Worked first try

____

---

### Post by kpolice on 2006-10-22
> **freddan83 said:**
> i have installed tcl 8.5 and tk 8.5, downloaded and recompiled amsn and even tryed one of the packages here, the checkboxes are now red with black in but the fonts are still ugly as hell, any advices?

Maybe you have tcl and tk 8.4 too??

---

### Post by DeemanXu on 2006-10-22
Anyone got the package ( amsn_0.97b_tcl0.95.deb' ) on their pc by any chance ? - seems the link is dead.

Thankyou.

---

### Post by DeemanXu on 2006-10-23
Anybody got the .deb at all ?

---

### Post by Ryanmt on 2006-10-23
the package downloaded fine for me, however it only runs if i do sudo amsn not just amsn, if i do it without sudo i get the error


```
Error in startup script: error copying "/home/ryanmt/.amsn/plugins.xml" to "/home/ryanmt/.amsn/plugins.xml.old": permission denied
```

---

### Post by DeemanXu on 2006-10-23
Ryan, when did you download it ? When i try and download, i get a Temporary failure in name resolution error

Oh, and if you still have the .deb package on your pc, is there any possibilty that you could send it me please ? if so, i'll pm you my addy.

Thanks.

---

### Post by Ryanmt on 2006-10-23
pretty much the time i posted that msg. Not got a pm yet but ill email it you when i do :)

Anybody got any advice on the root thing? i cant see the folder in my home directory but i can try chmod it, only problem is i dont know what chmod settings to use to make it read/writeable  :(

---

### Post by kpolice on 2006-10-23
I have a deb of amsn 0.97 from the last week svn version.

I built it on dapper but it's working without problems in Edgy.
[http://www.capc-online.net/dloads/linux/amsn/amsn_0.97b-svn7343M.deb](http://www.capc-online.net/dloads/linux/amsn/amsn_0.97b-svn7343M.deb)

---

### Post by DeemanXu on 2006-10-23
Thanks Karma ;)

---

### Post by Sirron on 2006-10-29
Awesome, I tried following the tutorial offered by aMSN's wiki, but I've never compiled anything before  :oops:  and I got a load of errors. Apparently, my C compiler couldn't make executables. I downloaded some more packages, and it worked a bit more but said it didn't have the right permissions or something. I used sudo so I dunno why it was doing that.

Anyway, I followed this post and aMSN stopped working, then I uninstalled aMSN, followed this post again and now it works great ^^

I'm on Edgy by the way.

---

### Post by PrinceArithon on 2006-10-29
From the aMSN wiki:
Quote:
Q: When I try running aMSN, I get an error "unknown color Black". How can I fix it ?
A: This problem is not coming from aMSN, it's an Xorg faulty installation. You probably have a bad Xorg configuration for the file rgb.txt (especially with some versions of Xgl).

If you are using xgl, you most probably have the file rgb.txt in /etc/X11 . Xgl in Ubuntu Dapper is usually misconfigured and looks for the file in /usr/share/X11 . Make a symlink to it in /usr/share/X11 and restart your X server.

If you are not using xgl, open your /etc/X11/xorg.conf and look for a line that says:


Section "Files"
RgbPath "/etc/X11/rgb"


If the RgbPath line does not exist at all, add it under the section "Files". Then make sure the file exists in the directory defined in RgbPath (/etc/X11/ in this case). You may need to copy it from another location in your computer, or you can download it from [http://amsn.sourceforge.net/rgb.txt](http://amsn.sourceforge.net/rgb.txt) . You must also restart your X server for the changes to take effect. PLEASE NOTE: the line in xorg.conf must NOT contain the extension of the file!!!
Oh BTW I build my own deb if anybody wants to try it, it also requires tcl/tk 8.5. I'm running dapper with the latest updates.



Well this is deffinatly my problem and deffinatly my fix...the only problem is I don't exactly understand everyting I'M supposed to do.

It seems like I could fix it using either of the 2 fixes.  So first off I don't know how to make a symlink...or maybe I do I am just being a noob at the moment.

Also, for the non XGL fix, I'M not sure what to do with that either..I haven't tried it yet because I don't understand it. 

I hate asking for someone to do a step by step for me...but I think I may need it...Can someone shine some light on this for me please??

Aaron

---

### Post by barrosz on 2006-11-03
ok im no expert but for the "unknown color Black" heres the fix, first make sure there is Black with a capital B in rgb.txt, if not add it like the other that is there but with the small b, should look like 0 0 0 Black.
then do:
sudo ln -s /etc/X11/rgb.txt /usr/share/X11/rgb.txt
restart X and it should work.

---

### Post by kr0n1x on 2006-11-06
there is any member can insert AUDIO support in amsn?

i copy linphone.so in plugins/linphone but when i try to load the plugin with ctrl+s, i've this error:
> couldn't load file "plugins/linphone/linphone.so": liblinphone-im.so.0: cannot open shared object file: No such file or directory

there is any member using audio in amsn??:(

edit: after the reboot of ubuntu, i've this problem: the "wish" process need really high percentage of my cpu (amd athlon xp 1800+), but yesterday amsn works perfectly without %cpu problem...
why now i need like another cpu? XD

---

### Post by Treviño on 2006-11-09
For newer amsn and tcl8.5/tk8.5 releases... [http://3v1n0.tuxfamily.org/dists/edgy/3v1n0/](http://3v1n0.tuxfamily.org/dists/edgy/3v1n0/)


PS: Look also to the tcl/tk sources... They are ready for being packaged ;)

---

### Post by sakis on 2006-11-11
> **Treviño said:**
> For newer amsn and tcl8.5/tk8.5 releases... [http://3v1n0.tuxfamily.org/dists/edgy/3v1n0/](http://3v1n0.tuxfamily.org/dists/edgy/3v1n0/)


PS: Look also to the tcl/tk sources... They are ready for being packaged ;)

Nice... thank you :mrgreen:

---

### Post by Claus7 on 2006-11-11
Hallo all,

I had installed amsn via add/remove applications. The version of Ubuntu I'm using is *Dapper Drake*. The version of aMNS I had installed is [COLOR="#ff0000"]0.95-1[/COLOR].
The truth is that I was content. Yet, I have to admit that I couldn't sometimes read letters from the [COLOR="#ff0000"]hellenic[/COLOR] (greek) language. Especially those which are toned ( for example &#940;). So I saw this in ubuntu forums and I decided to follow the instructions. The truth is that at first I had the same problems with libtk8.5.so.0 and libtcl8.5.so.0. So I typed :

```
sudo ln -sf libtk8.5.so.0 libtk8.5.so
sudo ln -sf libtcl8.5.so.0 libtcl8.5.so
```

When now I want to open aMSN via terminal I get [COLOR="Red"]Segmentation fault[/COLOR]. I unistalled aMSN but this fault remains. Any idea? 
Thanks in advance.

---

### Post by Claus7 on 2006-11-12
Hallo again,

AWESOME!!! The mistake I had made was that I didn't download your version of amsn. Now everything works nice. Yet, I still don't get why the other version didn't work arter I had reinstalled it. Anyway, I'm happy that I switched, because I can read now everything!

So people do exactly as the steps are posted!

---

### Post by jay73 on 2006-11-15
This is nice. Worked very well, thanks. :) 

BUT, i would also like to know how to get linphone working. I copied linphone.so to plugins but doesn't show up at all...

---

### Post by VividHazE on 2006-11-16
Excellent! I love aMSN but always hated the font. I also had 0.95 from the repo, so i've the added features too! Worked extremely easily. thanks a bunch! :D

---

### Post by Claus7 on 2006-11-18
Hallo,

jay73 wrote :
> BUT, i would also like to know how to get linphone working. I copied linphone.so to plugins but doesn't show up at all...

I have read that aMSN doesn't support microphone, if that's what you are talking about, and that they are concidering implementing it in future versions... Scype works nice for that though...

---

### Post by jay73 on 2006-11-19
> **Claus7 said:**
> Hallo,

I have read that aMSN doesn't support microphone, if that's what you are talking about, and that they are concidering implementing it in future versions... Scype works nice for that though...
 
But skype doesn't have cam-support. That's the whole point in this. Nobody in linux have cam AND sound support... dammit. I can't understand what's taking so long to get them both to work in some im-client. :-k

---

### Post by marcozs on 2006-11-20
Hey all!

I installed tcl/tk 8.5 and amsn 0.97b from Trevino's Repository ( [http://3v1n0.tuxfamily.org/](http://3v1n0.tuxfamily.org/) ) and I get an error "Illigal Instruction". Running edgy... has anyone an idea of how to fix it?

---

### Post by kr0n1x on 2006-11-20
i had equal problem, fixed removing amsn, tcl and tk and reinstalling it (in terminal)

---

### Post by marcozs on 2006-11-20
> **kr0n1x said:**
> i had equal problem, fixed removing amsn, tcl and tk and reinstalling it (in terminal)

I tried that... unistalled and then reinstalled... same problem...

---

### Post by kr0n1x on 2006-11-20
tried complete remove in synaptic? (for tcl and tk, not amsn)

---

### Post by DJ-Power on 2006-11-28
Installed this as per instructions and have to say it worked like a charm.
Certainly makes amsn look so much prettier and with such clear instructions you cant go wrong.
Thanks very much.
Regards
DJP :)

---

### Post by WishMaster on 2006-11-28
I'd suggest compiling everything from source :-)
This way, you can use aMSN with tcl/tk8.5, and let the other programs still use 8.4.

Instructions on how to do this are here:
[for Dapper, near the bottom of the page]("http://ubuntu.vdb-studios.be/CustomDapper.php")
[for Edgy, near the bottom of the page]("http://ubuntu.vdb-studios.be/CustomEdgy.php")

screenshot:
[IMG]http://ubuntu.vdb-studios.be/aMSN096.jpg[/IMG]

---

### Post by OffHand on 2006-11-28
This worked great. Thnx!

---

### Post by jaka on 2006-12-01
[http://www.jaka.name/amsn_0.96-1_i386.deb](http://www.jaka.name/amsn_0.96-1_i386.deb)

---

### Post by LuisC-SM on 2006-12-03
> **WishMaster said:**
> I'd suggest compiling everything from source :-)
This way, you can use aMSN with tcl/tk8.5, and let the other programs still use 8.4.

Instructions on how to do this are here:
[for Dapper, near the bottom of the page]("http://ubuntu.vdb-studios.be/CustomDapper.php")
[for Edgy, near the bottom of the page]("http://ubuntu.vdb-studios.be/CustomEdgy.php")

screenshot:


Hi.
Compiling from source; as per your Edgy instructions (I can say I have almost a fresh install in this LT), brings up a window requiring TLS. That&#347; not such a big issue and I believe It would be nice to add it to your tutorial. (I had to DL and extract the file in my home directory with no further issues)
I must also add to your tutorial that some other dependencies were required like **libpng12-dev** and ** libjpeg62-dev** (maybe there is something I'm lacking of).and as for the chameleon-plugin, I did not find it in the **Tile** page (or maybe we should extract some other file). These are only some minor obvservations, I believe u have made a wonderful job.

Tnx so much for your tutorial.

Luis C. Suárez

EDIT: As per [your post in aMSN Forum]("http://www.amsn-project.net/forums/viewtopic.php?t=618&postdays=0&postorder=asc&start=75"), I believe there are some missing tweaks in your tutorial in the "Chameleon Section".
I believe u compiled tile before compiling amsn. It will be very nice if u update this nice tutorial.

Kind Regards

---

### Post by Neo40 on 2006-12-03
Hello!

I have compiled Amsn 0.97b and antialiasing fonts work just fine!. However, my webcam (a Logitech Quickcam Messenger) does not work under Amsn. I know my webcam works because I can test it with Camorama program.
Since I have the source of Amsn, I tried this test:
```
~/msn/utils/linux/capture$ ./test.tcl 
```

And I get this message:
```
eric@ubuntu:~/msn/utils/linux/capture$ ./test.tcl 
Error in startup script: version conflict for package "Tcl": have 8.4, need 8.5
    while executing
"load /home/eric/msn/utils/linux/capture/capture.so capture"
    ("package ifneeded" script)
    invoked from within
"package require capture"
    (file "./test.tcl" line 5)
```

Any idea?
Thanks

EDIT: Nevermind: I forgot to close Camorama before using Amsn...

---

### Post by raul_ on 2006-12-15
How did u guys solve the file sending bug?

---

### Post by TheEclypse on 2006-12-27
I have an odd problem.  aMsn loads fine, but if I log in and set my status to anything other than appear offline, it uses 100% of the CPU and just freezes.  Anybody else get this?

---

### Post by TheEclypse on 2006-12-28
> **TheEclypse said:**
> I have an odd problem.  aMsn loads fine, but if I log in and set my status to anything other than appear offline, it uses 100% of the CPU and just freezes.  Anybody else get this?

Found the problem, I was using a "wine sans serif" font, seems all the fonts listed that began with "wine" caused the problem.

---

### Post by jbtito03 on 2006-12-28
This is a reply to "No sound and video support in linux":

No true... you have ekiga for instance with sound+video and wngophone. I think that there are some other apps but am not shure :D

---

### Post by kr0n1x on 2006-12-28
> **TheEclypse said:**
> Found the problem, I was using a "wine sans serif" font, seems all the fonts listed that began with "wine" caused the problem.

then what font do you use now?

---

### Post by decaf on 2006-12-29
I think this thing includes a trojan, it listens a port above 60000.

---

### Post by spockz on 2006-12-31
> **decaf said:**
> I think this thing includes a trojan, it listens a port above 60000.
Maybe you should read the Amsn FAQ? It does that as some kind of lock. It was the best platformindependent locking system..

---

### Post by rami85 on 2007-02-13
The links to TCL8.5 / TK8.5 are not working, please help

---

### Post by satrich on 2007-02-13
I managed to install this aMSN097 thing. But the above howto is not valid anymore. The links are not working.

I am using Edgy, and I had the old aMsn installed from the synaptich package.

I created an directory in my home directory aMsn. Just to copy all the packages needed.

First download these tcl en tk packages:
[http://download.tuxfamily.org/3v1deb//pool/edgy/3v1n0/tcl8.5_8.5.0.a5-3v1ubuntu0_i386.deb](http://download.tuxfamily.org/3v1deb//pool/edgy/3v1n0/tcl8.5_8.5.0.a5-3v1ubuntu0_i386.deb)
[http://download.tuxfamily.org/3v1deb//pool/edgy/3v1n0/tk8.5_8.5.0.a5-3v1ubuntu0_i386.deb](http://download.tuxfamily.org/3v1deb//pool/edgy/3v1n0/tk8.5_8.5.0.a5-3v1ubuntu0_i386.deb)

Install them by double-clicking on them.

Then I tried to install this package of aMsn097:
[http://download.tuxfamily.org/3v1deb//pool/edgy/3v1n0/amsn_0.97-0+svn20070120+3v1ubuntu0_i386.deb](http://download.tuxfamily.org/3v1deb//pool/edgy/3v1n0/amsn_0.97-0+svn20070120+3v1ubuntu0_i386.deb)

So, I suggest you download it too.:) 

When i tried to install it, it gave me an error about 'tile' dependency.
So I did the install again with:
sudo dpkg -i amsn_0.97-0+svn20070120+3v1ubuntu0_i386.deb

It gave me more information about: tcltls, tile, tcllib and libsnack2. When I tried to install them it suggested that I had to 'apt-get -f install' to solve some problems.
So I did that:
sudo apt-get -f install

That did remove the old aMsn. And it installed tcltls, tcllib and libsnack2.
So the only missing thing was 'tile'.

I installed it manually from the graet web-site where the other stuff came from:
[http://download.tuxfamily.org/3v1deb//pool/edgy/3v1n0/tile_0.7.8-3v1ubuntu0_i386.deb](http://download.tuxfamily.org/3v1deb//pool/edgy/3v1n0/tile_0.7.8-3v1ubuntu0_i386.deb)
Just doubleclick it to install.

And now you are ready to install the aMsn.deb package you downloaded.

It works for me. Nice fonts, And it has some skins for Ubuntu and Kubuntu. And the Plus-package is build in. Really nice.

Hope this tutorial will help some people.

:guitar: :guitar:

---

### Post by rami85 on 2007-02-14
it works, YOU ARE THE MAN

---

### Post by lowbat on 2007-03-29
Hi,

```
wget http://www.doeweling.com/files/ubuntu/amsn/tcl8.5_8.5.0-1~neto3_i386.deb
--18:18:59--  http://www.doeweling.com/files/ubuntu/amsn/tcl8.5_8.5.0-1~neto3_i386.deb
           => `tcl8.5_8.5.0-1~neto3_i386.deb'
Resolving www.doeweling.com... 89.110.129.53
Connecting to www.doeweling.com|89.110.129.53|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
18:19:03 ERROR 404: Not Found.
```

The download links for TCl and Tk libraries seem to missing (404). Would someone kindly re-upload them to another mirror?

Much appreciated!

---

### Post by magomago on 2007-05-03
can anyone update the files????  they are gone :( i can't seem to find a mirror of them anywhere

---

### Post by spanerman on 2007-05-13
i tried following all the steps layed out in the first post but cant install 

wget [http://www.doeweling.com/files/ubuntu/amsn/tcl8.5_8.5.0-1~neto3_i386.deb](http://www.doeweling.com/files/ubuntu/amsn/tcl8.5_8.5.0-1~neto3_i386.deb)
wget [http://www.doeweling.com/files/ubuntu/amsn/tk8.5_8.5.0-1~neto3_i386.deb](http://www.doeweling.com/files/ubuntu/amsn/tk8.5_8.5.0-1~neto3_i386.deb)

404 error....help

---

### Post by spanerman on 2007-05-13
i have the same problem as all the people above........what can i do?

---

### Post by lebabyg on 2007-09-17
I got TCL and TK from here.....[http://kaisman.free.fr/dotclear/index.php?linux-download-tcl-tk-85-source-deb](http://kaisman.free.fr/dotclear/index.php?linux-download-tcl-tk-85-source-deb)

---

### Post by perro84 on 2007-09-21
Here you can find an easy tutorial on how to install aMsn 0.97 in Ubuntu easily!

[Install amsn 0.97 in Ubuntu]("http://www.justubuntu.com/install_amsn_097b_ubunt u")

---

### Post by perro84 on 2007-09-21
Here you can find an easy tutorial on how to install aMsn 0.97 in Ubuntu easily!

[Install amsn 0.97 in Ubuntu]("http://www.justubuntu.com/install_amsn_097b_ubuntu")

I'm sorry for the double post, it was unintentional!!

---

### Post by LukeCarrier on 2008-02-15
As of Friday 15 Feb the first two downloads aren't working.

---

