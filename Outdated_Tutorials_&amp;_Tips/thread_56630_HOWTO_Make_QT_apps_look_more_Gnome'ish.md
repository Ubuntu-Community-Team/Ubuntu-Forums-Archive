---
title: "HOWTO: Make QT apps look more Gnome'ish"
date: 2005-08-13
forum: Outdated Tutorials &amp; Tips
---

### Post by FLeiXiuS on 2005-08-13
Ever wonder how to get your QT/KDE applications to look more "gnome-like"?  Well now this is the answer you've been waiting for.  

Kassetra was greatly angered after installing skype and noticing how large and UGLY everything really was.  No offense to KDE users, BUT WOW!  It was horrible.  So whats the solution? 

**Polymer QT Theme**
This sorta looks exactly like gnomes clearlooks.  So users will enjoy what they see.  

[COLOR=Red]Before / After Screenshots Below![/COLOR]

**ALRIGHT LETS DO IT**
[COLOR=Red]*Note: The "$" symbol denotes a terminal command.*[/COLOR]

1.) You will need to install *[COLOR=DarkOrange]qt3-qtconfig[/COLOR]* in order to change the styles.  
```
$ sudo apt-get install qt3-qtconfig
```

2.) Now it's time to install the theme.  Lucky I have created a binary package this way you don't have to go through and download the thousands of KDE/QT libs.
```

**HOARY USERS**
$ wget http://fleixius.com/files/downloads/polymer-0.3.1_0.3.1-1_i386.deb
$ sudo dpkg -i polymer-0.3.1_0.3.1-1_i386.deb

**BREEZY USERS**
$ wget http://fleixius.com/files/downloads/polymer-0.3.2_0.3.2-1_i386.deb
$ sudo dpkg -i polymer-0.3.2_0.3.2-1_i386.deb

```

3.) Lastly install [COLOR=DarkOrange]msttcorefonts[/COLOR]. (This are not required but it makes the style look SMOOTH!)
```
$ sudo apt-get install msttcorefonts
```

4.) Now that the files are installed lets get to the config!
```
$ qtconfig
```

5.) Lets change the font before hand to make it look even sweeter in the end.  I decided to use [COLOR=DarkOrange]Trebuchet MS 10pt[/COLOR].  Make the following changes...
```

-Default Font-
Family: Trebuchet MS
Style: Normal
Point Size: 10

```

6.) Time to make it SCHAWEET!  Click on the [COLOR=DarkOrange]Library Paths[/COLOR] tab.  In the input-box at the bottom enter "[COLOR=DarkOrange]/usr/plugins[/COLOR]" then click add.

7.) Now in the [COLOR=DarkOrange]Appearance[/COLOR] tab, select [COLOR=DarkOrange]Polymer[/COLOR] as your GUI style.


8.) Sweet eh?  Got to[COLOR=DarkOrange] File>Save[/COLOR].  Exit the program and your almost done!


Another great benefit of this theme is that it has TRANSPARENCY!!
```
$ polymer-config
```

Down around the bottom you'll see "[COLOR=DarkOrange]KDE Style Settings[/COLOR]", chagne the "[COLOR=DarkOrange]Transparency Engine[/COLOR]" to "[COLOR=DarkOrange]Software Tint[/COLOR]" and then close the application.  You will be prompted to save, click yes of course.  

**How sweet is that?**

EDIT: For other KDE applications, you'll need kcontrol.
[COLOR=SlateGray]*(Credits: GilGalad)*[/COLOR]

1.) Instal kControl
```
$ sudo apt-get install kcontrol
```

2.) Configuring the new theme.
```

$ kcontrol

```

3.) Click "[COLOR=DarkOrange]Appearance[/COLOR]" then "[COLOR=DarkOrange]Style[/COLOR]".  From here select the "[COLOR=DarkOrange]Polymer[/COLOR]" theme.  Save and exit.


[SIZE=3]**Before**[/SIZE]
[IMG]http://fleixius.com/files/pictures/before.png[/IMG]

[SIZE=3]**After**[/SIZE]
[IMG]http://fleixius.com/files/pictures/after.png[/IMG]


[COLOR=Red]Credits:[/COLOR]
[COLOR=SlateGray]**Kassetra**: For the motivation of installing over 30megs of QT/KDE libraries and for 2 hours on skype :-).  I have screenshots to prove it... :roll:   She also found Polymer, so give a w00t w00t when you see her.
**Polymer Project**: [http://static.int.pl/~mig21/dev/releases/polymer/#screenshots](http://static.int.pl/~mig21/dev/releases/polymer/#screenshots)
**KDE**: Thanks for providing so many libraries to install!!!
[/COLOR]

EDIT: Step 7 added and fixed the msstcorefonts -- Breezy/Hoary Debs

---

### Post by MBro on 2005-08-13
Good work, Stop those things from looking but ugly

---

### Post by benplaut on 2005-08-13
typo:

msttcorefonts instead of msstcorefonts

great tutorial... i was using a jerry-rigged solution with a bit of tweaking in qtconfigm but this makes it look alot better  :grin:

---

### Post by celticmonkey on 2005-08-17
This worked great. Skype really didn't look right before. Now it looks fantastic!

---

### Post by crvendramini on 2005-08-17
Great job!!!

 :)

---

### Post by Baltor on 2005-08-17
This is really awesome! I can finally stand to look at my qt apps.

---

### Post by junior aspirin on 2005-08-17
looking nice, one thing does audacity use qt? because it still looks ugly!

---

### Post by matthew on 2005-08-17
I love the idea. It isn't working on most of my kde apps. The qtconfig windows are affected, but a quick test of several random k-apps showed no effect on kpdf, kvim, kparted or ktuberling. Bummer...I wonder if I missed something...hmm <doublechecks work by scrolling up in editor and re-running all commands> Nope. I just saw another poster showing no effect in Audacity either.

---

### Post by dbeckham32 on 2005-08-17
Great tweak!! All bow and pay homage to FLeiXiuS!

---

### Post by arnieboy on 2005-08-17
fleixius-
I owe u a six pack for this one.
-arnieboy

---

### Post by Remix_88 on 2005-08-18
Great HOW-TO!

I was using a manually hacked '~/.qt/qtrc' to get my QT apps looking a little less ugly. This is a much nicer solution and I still don't need to install any kdelibs or kcontrol, Yah!

The Polymer theme is a nice find. 'esvn' and 'lincvs' (the only QT apps I use) look pretty now so I am a very happy man :grin:

---

### Post by DShafik on 2005-08-21
I had to close qtconfig after adding the path and re-open it to be able to select the polymer theme, other than that, it works great! 

Thanks :D

- Davey

---

### Post by FLeiXiuS on 2005-08-21
Yeah I forgot to mention to change your GUI Style to Polymer....

Thanks guys :-)...

---

### Post by LaSSarD on 2005-08-29
Great how-to! I think it'd be even better if you edit a little mistake you did: it's not msstcorefonts, but msttcorefonts ;)

---

### Post by miscz on 2005-08-29
There's even better style for Gnome integration - [QtCurve](http://www.kde-look.org/content/show.php?content=5065), it can be easily made to [look like Clearlooks](http://img376.imageshack.us/my.php?image=zrzutekranu0fl.jpg) or whatever colour variation you might be using. Throw in some [Bluecurve ](http://download.fedora.redhat.com/pub/fedora/linux/core/development/i386/Fedora/RPMS/redhat-artwork-0.128-1.i386.rpm) or [Gnome-Mix](http://kde-look.org/content/show.php?content=27788) icons and you get pretty consistent desktop.

---

### Post by FLeiXiuS on 2005-08-31
[QUOTE=LaSSarD]Great how-to! I think it'd be even better if you edit a little mistake you did: it's not msstcorefonts, but msttcorefonts ;)[/QUOTE]

Woops, yes that has been fixed.  Thank you and enjoy!

---

### Post by Swad on 2005-08-31
Hmmm... K3B menu fonts before and after look the same--big and ugly.  Everything seemed to take per what you outlined in your original post in terms of setting it up, though.  :(

edit: I downloaded Skype as a test and any font changes I did in qtconfig applied and  I easily made Skype look like the rest of my Gnome apps.  Apparently K3B is controlled by something else  :/

edit2: amaroK is doing the same thing.  I must be missing something that you guys have (I've read the OP a couple times and have that squared away).

---

### Post by LaSSarD on 2005-08-31
Thank you, FLeiXiuS.
Just wondering... is there any way to get opera using this theme? The top bar (File Edit View ...) and its content is still horrible. btw, skype didn't get this light style on your screenshot, it is gray.

---

### Post by angkor on 2005-08-31
Ooo...very nice indeed. Thanks a bunch Flexius

---

### Post by GilGalad on 2005-09-02
[QUOTE=Swad]Hmmm... K3B menu fonts before and after look the same--big and ugly.  Everything seemed to take per what you outlined in your original post in terms of setting it up, though.  :(

edit: I downloaded Skype as a test and any font changes I did in qtconfig applied and  I easily made Skype look like the rest of my Gnome apps.  Apparently K3B is controlled by something else  :/

edit2: amaroK is doing the same thing.  I must be missing something that you guys have (I've read the OP a couple times and have that squared away).[/QUOTE]

If you want to change the look of k3b and other kde applications you will need to install kcontrol and select Polymer in the Appearence->Style tab.

---

### Post by idn on 2005-09-02
Awesome



You could always use gizmo project instead of skype, that uses gtk so integrates into your desktop really well.



Also the UI is much better than skype's

---

### Post by majikstreet on 2005-09-03
I love you!

I only had one problem. After I added /usr/plugins, I had to save qt-config then close then run qt-config again, then choose polymer.



Anyway, skype looks wonderful!

majikstreet

---

### Post by benplaut on 2005-09-03
doesn't work in breezy, unfortunately  :mad:

---

### Post by FLeiXiuS on 2005-09-04
I'll have to see if i can manage to create a port for breezy users. 

As for k3b / opera I'll reasearch and get back to you guys.  It's late and I'm tired.. :-)

---

### Post by FLeiXiuS on 2005-09-04
[QUOTE=GilGalad]If you want to change the look of k3b and other kde applications you will need to install kcontrol and select Polymer in the Appearence->Style tab.[/QUOTE]

Awesome, I just test this and it did work flawlessly.

---

### Post by darkmatter on 2005-09-04
You could also try the following program, whick is designed to unify the various graphics toolkits (allowing qt to use gtk+, etc)

[http://www.kde-look.org/content/show.php?content=13010](http://www.kde-look.org/content/show.php?content=13010)

---

### Post by parktownprawn on 2005-09-04
[QUOTE=benplaut]doesn't work in breezy, unfortunately  :mad:[/QUOTE]

Seems like breezy uses newer/different qt libraries. The good news is that it's really easy to compile.

down load the source from [here](http://static.int.pl/~mig21/dev/releases/polymer/) 

then you need to install the developement libraries
```
sudo apt-get install qt3-apps-dev
``` 

unpack the source in some appropriate place go to the  created directory and do the usual
```
./configure
make
sudo make install
```

if you would rather make a .deb package install checkinstall and change the last line to ```
sudo checkinstall
```

The bad news is that installing the newer qt libraries may neccitate removing some programes which rely on the old qt libraries and  have not been updated for breezy  yet - like lyx-qt :(

Edit: lyx-qt has been updated yipeee :D
Edit2: changed link to sources - the one on kde-look doesn't seem to work

---

### Post by pholie on 2005-09-05
[QUOTE=LaSSarD]Thank you, FLeiXiuS.
Just wondering... is there any way to get opera using this theme? The top bar (File Edit View ...) and its content is still horrible.[/QUOTE]

Yeah, opera doesn't use qt styles by default, i already sent them a bugreport. But you can enable it when you run **opera --style default**. Look also [here](http://my.opera.com/forums/showthread.php?threadid=73577).

---

### Post by pholie on 2005-09-05
But i still wonder why some KDE apps (akregator, kmail) have bigger fonts in GNOME (or xfce) than in KDE?!

---

### Post by Pikapooh on 2005-09-05
It is probably DPI thingie. In Gnome u can set DPI via System->Preferences->Fonts. KDE AFAIK read DPI from config file (xorg.conf). If u want to have same DPI search this forum for 'xdpyinfo'.

---

### Post by pholie on 2005-09-05
Yeah, i have DisplaySize in xorg.conf set for my monitor dimensions. xdpyinfo says: *resolution:    73x74 dots per inch*, so I set in gnome DPI to 72 (before it was 96). Now KDE apps look as small as in KDE. Thanks

---

### Post by MrJack on 2005-09-05
Thank you! :D
Now i can actualy work with qt apps ...

---

### Post by FLeiXiuS on 2005-09-06
[QUOTE=pholie]But i still wonder why some KDE apps (akregator, kmail) have bigger fonts in GNOME (or xfce) than in KDE?![/QUOTE]

I'll experiment with them later tonight.  Hopefully I can find a solution for you. 

As for breezy users, follow the wonderful guide provided ahead.   Thankyou parktownprawn!

And for everyone...Sorry for being inactive..work is really catching ahold of me.  I'm going to try to get more time to the forums shortly.

---

### Post by Skebaristi on 2005-09-08
Hell yeah! Thanks a bunch! Why didn't I try to look here for a solution to butt-ugly skype and hplip... I'm dumb...

THANKS!

EDIT: Ugh... Quoted the original by accident  :)  Goddamn I'm dumb :) :)

---

### Post by newen on 2005-09-13
[QUOTE=parktownprawn]Seems like breezy uses newer/different qt libraries. The good news is that it's really easy to compile.

down load the source from [kde-look](http://www.kde-look.org/content/show.php?content=27968&PHPSESSID=df76bc402f16b5650578c70bbeddec6a) 

then you need to install the developement libraries
```
sudo apt-get install qt3-apps-dev
``` 

unpack the source in some appropriate place go to the  created directory and do the usual
```
./configure
make
sudo make install
```

if you would rather make a .deb package install checkinstall and change the last line to ```
sudo checkinstall
```

The bad news is that installing the newer qt libraries may neccitate removing some programes which rely on the old qt libraries and  have not been updated for breezy  yet - like lyx-qt :(

Edit: lyx-qt has been updated yipeee :D[/QUOTE]


I have tryed compiling, but i get this:

checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!

what I need now?

EDIT: if only anyone could upload a deb for breezy...

---

### Post by foxy123 on 2005-09-13
[QUOTE=newen]I have tryed compiling, but i get this:

checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!

what I need now?

EDIT: if only anyone could upload a deb for breezy...[/QUOTE]
you need to install dev kde libraries.. (kdelibs with dev).

---

### Post by FLeiXiuS on 2005-09-13
[QUOTE=FLeiXiuS]I'll experiment with them later tonight.  Hopefully I can find a solution for you. 

As for breezy users, follow the wonderful guide provided ahead.   Thankyou parktownprawn!

And for everyone...Sorry for being inactive..work is really catching ahold of me.  I'm going to try to get more time to the forums shortly.[/QUOTE]


I know this may sound silly, but it appears that some of my QT applications only search for the QT style upon configuration.  I'm not sure if it stores it's configurations for faster loading times.  But when I reinstalled the application, things worked like a charm.  New STYLE and all.  I'll see if this is a bug or if there is another possibly easier fix.

---

### Post by parktownprawn on 2005-09-13
[QUOTE=newen]I have tryed compiling, but i get this:

checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!

what I need now?

EDIT: if only anyone could upload a deb for breezy...[/QUOTE]

urk - they have updated the polymer sources so that my instructions no longer work - i'll get back to you. You can try install the attached deb (unzip it first).

---

### Post by parktownprawn on 2005-09-13
[QUOTE=newen]
checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!
[/QUOTE]

i don't know whats up with the new sources from kde-look.
The sources from [here](http://static.int.pl/~mig21/dev/releases/polymer/) should compile as per my original [howto](http://www.ubuntuforums.org/showpost.php?p=332825&postcount=27)

---

### Post by frodon on 2005-09-13
Nice guide !

However i still have some problems getting the good fonts with K3B, all i did is follow this guide and then install kcontrol and select the polymer theme.
Any idea ?

---

### Post by sinbad782 on 2005-09-13
This is pretty good. I was wondering about this for ages. I don't know of any small applet that would do this automatically (you can get one for KDE called something like gtk-qt-engine or such), but that would be a nice addition.

What I ended up doing in the end was this:

1.) Changing all the QT fonts in kcontrol to match the GNOME ones.
2.) Installing a couple of extra colour schemes from kde-look.org and then installing these in kcontrol. I found that 'clearlooks' and 'almost industrial' seem to work best with how I have GNOME set up.

PJS

---

### Post by digits on 2005-09-14
great !!!!

does anybody of you know something similar for these stupid java progs ? they really mess up.

thank you!

greetings,
digits

---

### Post by majikstreet on 2005-09-14
**i didn't even see the guide above.. following now :)


The correct way to install it on breezy is to apt-get the qt3-apps-dev or whatever then download the .zip from earlier, install that deb in the zip (you must apt-get remove polymer-0.3.1 first though!) then open qtconfig and select polymer! and save and voila!

---

### Post by beow on 2005-09-17
Thanks for the tip! qcad is now a superb program! I used the "sans serif" font instead of Trebuchet to get an even more gnomish look.

---

### Post by beow on 2005-09-17
Sorry for the quoting... "Quote message in reply?" should maybe not be default in a "quick reply"...

---

### Post by rwabel on 2005-09-23
thanks alot for the howto. There is a debian sid package now which works fine in breezy. I made a howto on the ubuntu wiki page: [https://wiki.ubuntu.com/QtGnome](https://wiki.ubuntu.com/QtGnome) with some additions (debian packages and another font (XLinSans)

---

### Post by beefsprocket on 2005-09-23
So what am I missing here? I've installed polymer both from .debs and from various versions of source. In every instance it installs properly but I cannot figure out how to get the glass looking theme pictured here:

[http://kde-look.org/content/pre1/27968-1.jpg](http://kde-look.org/content/pre1/27968-1.jpg)
[IMG]http://kde-look.org/content/pre1/27968-1.jpg[/IMG] 

My style looks like the 2nd one with any version I use. I can't get either of the other two styles. Am I missing something really simple here?  The fact that it installs or compiles and installs leads me to belive that it is not my system causing this -- rather it is a PEBKAC or... I don't know? Grr  ](*,) 

Using Breezy 5.10 with Kde3.5beta (and have nothing but good things to say about the combination).

---

### Post by rwabel on 2005-09-24
[QUOTE=beefsprocket]So what am I missing here? I've installed polymer both from .debs and from various versions of source. In every instance it installs properly but I cannot figure out how to get the glass looking theme pictured here:

[http://kde-look.org/content/pre1/27968-1.jpg](http://kde-look.org/content/pre1/27968-1.jpg)
[IMG]http://kde-look.org/content/pre1/27968-1.jpg[/IMG] 

My style looks like the 2nd one with any version I use. I can't get either of the other two styles. Am I missing something really simple here?  The fact that it installs or compiles and installs leads me to belive that it is not my system causing this -- rather it is a PEBKAC or... I don't know? Grr  ](*,) 

Using Breezy 5.10 with Kde3.5beta (and have nothing but good things to say about the combination).[/QUOTE]
 have tried to play with kcontrol? I don't use KDE normally, therefore I can't really help u with getting it tweak to look like on the image.

---

### Post by beefsprocket on 2005-09-24
Umm... Kcontrol is where I've been trying to make the changes. I've used polymer-config and qtconfig as well but to no avail.

---

### Post by psychicdragon on 2005-09-28
Thanks a lot for this. Now if only we could somehow make qt apps use the gtk file selector as well.

---

### Post by yesidh on 2005-09-30
Hello, thanks is it very useful, but it didn't worked in Kdevelop, what can I do?

---

### Post by def_ on 2005-10-01
hi,
can someone explain me why, upgrading from 5.04 to 5.10, this tutorial wont work any more? Now i can configure fonts via qtconfig, but the interface "polymer" is no longer present in the interface list!

Any sugestion?

---

### Post by parktownprawn on 2005-10-02
[QUOTE=def_]hi,
can someone explain me why, upgrading from 5.04 to 5.10, this tutorial wont work any more? Now i can configure fonts via qtconfig, but the interface "polymer" is no longer present in the interface list!
Any sugestion?[/QUOTE]

see [http://ubuntuforums.org/showpost.php?p=332825&postcount=27](http://ubuntuforums.org/showpost.php?p=332825&postcount=27)

also try using qtconfig-qt3.

qtconfig might be bringing up qtconfig-qt4 which configures applications using qt4 rather than qt3.

---

### Post by majikstreet on 2005-10-02
HOWTO Gnomeify Skype on Breezy:
**DO THIS IN THE TERMINAL**

```

sudo apt-get install qt3-apps-dev

wget http://www.majikstreet.org/ubuntu/polymer-0.3.2.zip

unzip polymer-0.3.2.zip

sudo apt-get remove polymer-0.3.1*

sudo dpkg -i polymer-0.3.2_0.3.2-1_i386.deb

qtconfig
                      Select "Polymer as your GUI style"
                      Save and you are done :)
```

majikstreet


*****If you got skype from the official skype apt repo's, this guide can be followed, but you need to REBOOT your computer before it works.****

---

### Post by refdoc on 2005-10-04
Fleixius and majikstreet - 

Many, many thanks!! This makes a huge difference. Only I would not go with trebuchet but simply with Sans serif which appears to be the default font and works fine.

---

### Post by magnusbb on 2005-10-09
As I try to keep the system as clean as possible, hence not downloading the qt3-libs just for compiling a single theme, I thought...

if anybody had done it - could they provide a pre-compileed package of the Polymer theme for Breezy?

That would be most kind.

---

### Post by FLeiXiuS on 2005-10-09
[QUOTE=magnusbb]As I try to keep the system as clean as possible, hence not downloading the qt3-libs just for compiling a single theme, I thought...

if anybody had done it - could they provide a pre-compileed package of the Polymer theme for Breezy?

That would be most kind.[/QUOTE]

Revert back a few posts and read majikstreet's response.  He offers a good package for polymer users on Breezy.

---

### Post by lusepuster on 2005-10-09
How sweet is that...??:D :D :D

---

### Post by viuks on 2005-10-17
Thank You!!! Very nice!:)

---

### Post by Pablo_Escobar on 2005-10-17
[QUOTE=def_]hi,
can someone explain me why, upgrading from 5.04 to 5.10, this tutorial wont work any more? Now i can configure fonts via qtconfig, but the interface "polymer" is no longer present in the interface list!

Any sugestion?[/QUOTE]

If You don't have polymer in Your selection choice, in the qtconfig go to the tab where there are some paths to directories. (3rd tab as far as I remember)

Add at the bottom : "/usr/plugins".
Save configuration, Exit, qtconfig again and presto, polymer is right there to select.

---

### Post by Doughsay on 2005-11-27
This HOWTO worked great for skype.  But, like someone earlier in this thread, I'm wondering about audacity...  How can I make it use the polymer theme?

---

### Post by Brian McConnell on 2005-12-09
[QUOTE=FLeiXiuS]Revert back a few posts and read majikstreet's response.  He offers a good package for polymer users on Breezy.[/QUOTE]

any Polymer available for the ppc user? I hope so :D

---

### Post by kalos on 2005-12-13
[QUOTE=Brian McConnell]any Polymer available for the ppc user? I hope so :D[/QUOTE]

I'm sure it will work, but I think you're going to have to compile yourself.
See parktownprawn's earlier [little howto](http://www.ubuntuforums.org/showpost.php?p=332825&postcount=27).

-kalos

---

### Post by phoenix49 on 2006-05-22
[QUOTE=Doughsay]This HOWTO worked great for skype.  But, like someone earlier in this thread, I'm wondering about audacity...  How can I make it use the polymer theme?[/QUOTE]

Audacity uses GTK1, you cannot apply QT theme to GTK. Anyway, I think Qt applications are pretty beautiful, but not in GNOME, only in native KDE.

---

### Post by blackpaw on 2006-06-15
works in xubuntu dapper!

although the qtconfig throws some errors... it works :D

---

