---
title: "[SOLVED] NOOBIE needs help"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by macvr on 2008-08-12
hi guys,
i'm new to ubuntu, and linux on the whole. just a few days back installed the ubuntu desktop 8.04.1 with dual boot option with XP professional
 need help with a few stuff!
[LIST=1]
[*][COLOR="RoyalBlue"]my _fonts in firefox_ are weird , especially in GOOGLE, i think its the times new roman fonts ,i have downloaded the msfonts and i have set the fonts in other general settings but the fonts in firefox and thunderbird always remain weird while all other app fonts are fine
[/COLOR]

[*]the first time i connected my external drive and unmounted the drive i got a _notification_ that said the device was unmounted or that it was safe to remove the drive (i'm not sure of the exact notification but i got one) but after that i dont seem to get a notification after i unmount my external drive, HAVE I MESSED UP MY SETTINGS , HOW DO I MAKE UBUNTU TO GIVE THAT NOTIFICATION EVERY TIME I UNMOUNT THE DRIVE, feels a bit scary not to get that notification and to remove the drive, just scared that i might corrupt my data!
[COLOR="RoyalBlue"]

[*]i have moved my top _panel_ to the right, with my bottom panel at the bottom, but when i restarted the bottom panel showed up in the top!!! is it always necessary for one panel to be on top?[/COLOR]

[*] to install new _themes_ what do i have to do initially(i mean , what other software do i have to have installed), also i really confused as to what type of file i can use on my system gtk/metacity/compiz/beryl for desktop themes for pointers is X11 mouse theme the one to use?
[COLOR="Blue"]

[*]when i take _screen shots_ it always saves as .png how to make it save as .jpg? couldnt upload the screen shot of the weird fonts in firefox!!![/COLOR]

[*]i'm not able to enable _touchpad_ settings , tried to enable the shmconfig as true but it kept saying that shmconfig is disabled, (tired with on, 1) also but no effect
[COLOR="Blue"]

[*] can firefox, thunderbird be used in dual boot with the _same profile sharing_ ( there where a few tutorials[http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux]("http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux") )    but while using it i tried to flag a mail in thunderbird but it kept crashing ,and it didnt work well for firefox. 
so my ques is just that if this has been done by anyone, does sharing work fully?[/COLOR]

[*]while using thunderbird with webmail > i keep getting message that "_local host_ connection was refused" how do i correct this?

[/LIST]

i'v tried googling and also searching these forums,tried a lot of the solutions, got totally confused:confused: thats why i posted this long list!!!

thanks in advance

---

### Post by lukjad on 2008-08-12
> **macvr said:**
> 
[COLOR="RoyalBlue"]my _fonts in firefox_ are weird , especially in GOOGLE, i think its the times new roman fonts ,i have downloaded the msfonts and i have set the fonts in other general settings but the fonts in firefox and thunderbird always remain weird while all other app fonts are fine
[/COLOR]

Below is the way that Google looks in my Firefox browser. Is it significantly different from yours? If so, please post a screenshot of Google.

> 
i have moved my top _panel_ to the right, with my bottom panel at the bottom, but when i restarted the bottom panel showed up in the top!!! is it always necessary for one panel to be on top?[/COLOR]

No, not really. Sometime you need to redo what you did last time, especially after an installation. Put it back the way you like it after you have finished installing all of your updates and see it the new look sticks.

I have answered those questions that I could. The rest some other fine member of this forum will help you with.

---

### Post by macvr on 2008-08-12
> **lukjad007 said:**
> Below is the way that Google looks in my Firefox browser. Is it significantly different from yours? If so, please post a screenshot of Google.
just attached the screenshot

> **lukjad007 said:**
> To make it save as a .jpg, all you need to do is when you are naming the screenshot, change the .png to a .jpg and it will save to that file extension.

i'v tried that but everytime i do it and later when i try to open the file it says that there is an error and the file is not a jpeg file!!! have added the screenshot too

---

### Post by lukjad on 2008-08-12
You are right about the .jpg. Sorry. I will change my post.

---

### Post by tarps87 on 2008-08-12
> **macvr said:**
> to install new _themes_ what do i have to do initially(i mean , what other software do i have to have installed), also i really confused as to what type of file i can use on my system gtk/metacity/compiz/beryl for desktop themes for pointers is X11 mouse theme the one to use?


This is a good place to look for new themes [http://www.gnome-look.org/](http://www.gnome-look.org/)  To install gtk/metacity themes all you need to do is go to preferences, appearance and there will be a button called install theme, click on it navigate to the theme you've downloaded an click ok.

As for which themes its entirely up to you but here are some guidelines:
gtk/metacity themes = work with the default setup of Ubuntu
compiz themes = require a program called compiz fusion which is more graphicly enhanced (compiz fusion is available from the synaptic program manager)
beryl themes = require a program called emerald, these are used with compiz themes and tend to be window frames e.g the boarder around a program and the bar at the top (also available from the synaptic program manager)
X11 themes = are for another desktop environment called x11, the default one installed with Ubuntu is called gnome.

> **macvr said:**
> 
my _fonts in firefox_ are weird , especially in GOOGLE, i think its the times new roman fonts ,i have downloaded the msfonts and i have set the fonts in other general settings but the fonts in firefox and thunderbird always remain weird while all other app fonts are fine


I believe you can change the font of firefox in tools > options > content
I'm on windows at the moment but will check when I get back home.

---

### Post by sayakb on 2008-08-12
Please use descriptive titles for your thread rather than just "Noob here" or "Help please".

---

### Post by Stunts on 2008-08-12
> **macvr said:**
> 
2. the first time i connected my external drive and unmounted the drive i got a notification that said the device was unmounted or that it was safe to remove the drive (i'm not sure of the exact notification but i got one) but after that i dont seem to get a notification after i unmount my external drive, HAVE I MESSED UP MY SETTINGS , HOW DO I MAKE UBUNTU TO GIVE THAT NOTIFICATION EVERY TIME I UNMOUNT THE DRIVE, feels a bit scary not to get that notification and to remove the drive, just scared that i might corrupt my data!


Hi. That notification will appear when you try to unmount a drive and it is still writing/reading some data on it. If it's a long enough operation you will see another message before that one saying what I said here. If there is no message being displayed you are perfectly safe to remove your drive. (At least this is what I know from my experience).

> **macvr said:**
> 
5. when i take screen shots it always saves as .png how to make it save as .jpg? couldnt upload the screen shot of the weird fonts in firefox!!!
 

Screenshots will be saved as .png by default. If you really want a .jpg screenshot, you can use The GIMP to quickly convert it. Just open it with The GIMP and then Save as... "filename.jpg" - and you're good to go.

As for the rest of your questions... sorry, but I'm just not experienced enough for those that have not yet been answered...

Welcome aboard Ubuntu, BTW.

---

### Post by appi2012 on 2008-08-12
[COLOR="Red"]You can share firefox setting (bookmarks, etc) using Mozilla Weave: 
Go here for more info and how to install:
[http://thetoptenme.wordpress.com/2008/07/04/top-10-reasons-to-use-weave-a-firefox-must-have/](http://thetoptenme.wordpress.com/2008/07/04/top-10-reasons-to-use-weave-a-firefox-must-have/)[/COLOR]

Disregard that; Weave is no longer accepting registrations (Until in matures)

---

### Post by lukjad on 2008-08-12
Screenshots:

I would first like to know why you need to change them. The PNG format is open source while the JPEG format is not. That point aside, here is how to do it.

(This was hard to find.)

You take you screenshot and save it to your Desktop. (Or wherever. It is the default and the easiest.) Next you open up a terminal and type 

```
convert 
```
(Make sure to put a space after the word convert.)
Next you drag your screenshot from your desktop onto the terminal and drop it there. The terminal should now look something like this:

```
yourusername~$ convert '/home/yourusername/Desktop/Convert/Screenshot.png'
```
Make sure you have a space in between the word convert and the '/home/...

Then make a space and type the new name for what you want the screenshot to be called. For instance, I called mine Image.jpg for effect. (Don't put any spaces, they mess things up. Put underscores ["_"] instead.) 

Hit enter. The new .jpg file will be in your home folder found at Places->Home Folder.

Hope this helped!

---

### Post by tarps87 on 2008-08-12
Stunts idea of using gimp to change the screenshots is probably easier and gimp is install by default, it inder graphics on the aplications menu.
*lukjad007 you know what is means [COLOR="White"]your banned[/COLOR] :)*

---

### Post by lukjad on 2008-08-12
reminds tarps87 that convert is also preinstalled. He should know that also [COLOR="White"]he is banned.[/COLOR]

---

### Post by macvr on 2008-08-12
> **LinuxIsInnovation said:**
> Please use descriptive titles for your thread rather than just "Noob here" or "Help please".
well there were a lot of doubts i had so i didnt know what to title the thread!
moreover my mind was literally numb trying to figure out a lot of the differences from XP and getting used to ubuntu, MAINLY it was the firefox and thunderbird issues that are really bugging

to make things worse google looks horrible!

> **lukjad007 said:**
> Screenshots:

I would first like to know why you need to change them. The PNG format is open source while the JPEG format is not. That point aside, here is how to do it.

(This was hard to find.)
thanks man but it seeems i have to install some more software to do this, right now i think i'll get to know better the apps installed default to get a better feel before i start messing around with more apps.

actually in XP the format i used to use was jpeg for screenshots mainly for the small size , but in ubuntu while i converted the .png file to .jpg in GIMP the size was a bit larger 
so i was wondering if there was any other way,
 but i think i can do with .png itself

> **Stunts said:**
> Hi. That notification will appear when you try to unmount a drive and it is still writing/reading some data on it. If it's a long enough operation you will see another message before that one saying what I said here. If there is no message being displayed you are perfectly safe to remove your drive. (At least this is what I know from my experience).

Welcome aboard Ubuntu, BTW.
os there any way to force UBUNTU to display the notification

> **tarps87 said:**
> This is a good place to look for new themes [http://www.gnome-look.org/](http://www.gnome-look.org/)  To install gtk/metacity themes all you need to do is go to preferences, appearance and there will be a button called install theme, click on it navigate to the theme you've downloaded an click ok.

As for which themes its entirely up to you but here are some guidelines:
gtk/metacity themes = work with the default setup of Ubuntu
compiz themes = require a program called compiz fusion which is more graphicly enhanced (compiz fusion is available from the synaptic program manager)
beryl themes = require a program called emerald, these are used with compiz themes and tend to be window frames e.g the boarder around a program and the bar at the top (also available from the synaptic program manager)
X11 themes = are for another desktop environment called x11, the default one installed with Ubuntu is called gnome.



I believe you can change the font of firefox in tools > options > content
I'm on windows at the moment but will check when I get back home.
i tried changing from the EDIT menu but no use(i guess overriding the page font would be the last option), the thing is i want the pages to retain the original font , else all the pages would look monotonous!

i have tried GNOME-LOOK.ORG but when i tried installing some of the themes , it didnt get installed

i have compiz installed, so can beryl be installed also, i thought that beryl was merged into compiz[well thats what wikipedia said:mrgreen:]
so i thought that only compiz alone would do!

---

### Post by lukjad on 2008-08-12
I didn't have to install any software, it came pre-installed with Ubuntu.

---

### Post by macvr on 2008-08-12
> **lukjad007 said:**
> I didn't have to install any software, it came pre-installed with Ubuntu.
```
The program 'convert' can be found in the following packages:
 * imagemagick
 * graphicsmagick-imagemagick-compat
Try: sudo apt-get install <selected package>
bash: convert: command not found
```

i get this message every time i type convert

---

### Post by lukjad on 2008-08-12
Ahhh. I must have a special build.

At the termial, type:

> sudo apt-get install imagemagick

My mistake, I have Ubuntu Studio and it seems to come pre-installed.

---

### Post by Stunts on 2008-08-12
> **macvr said:**
> 
os there any way to force UBUNTU to display the notification


I don't think there is, sorry, at least as far as I know. But rest assured, if for some reason you shouldn't unplug your drive after unmounting, Ubuntu will let you know.

As for your Firefox fonts issue:
Try the following: "System" -> "Preferences" -> "Appearance".
Then go to the Fonts tab.
Make sure that "Subpixel smoothing" is selected (I'm assuming you have an LCD screen, those fonts look a lot like mine before I solved it this way). If that doesn't make a difference (it should be felt immediatly) just click "Details" and tinker with the settings (no worries, I don't think you can break anything there).

Also, one more thing on the fonts - in firefox's preferences ("Edit" -> "Preferences" under the "Content" tab, in the Fonts & Colors make sure the default is "serif". In the advanced button, The four fonts should read: "Serif"; "serif"; "sans-serif"; "monospace". Also, the box "Allow pages to choose their own fonts, (......)" should be **checked**.

As for your themes. On Gnome look, you should download  .tar.gz files. They can be iconsets, window borders, whatever. An easier way to install them is to drag and drop the "genericthemefile.tar.gz" into the "Appearance" window under the "Themes" tab. Gnome will ask if you'd like to start using the new theme right away, or if you want to keep the old one. I recommend you keep the old one, and then click "Customize" to choose what you'd like to match up.

Owo, long reply! I hope this is of some help!

---

### Post by macvr on 2008-08-12
> **Stunts said:**
> I don't think there is, sorry, at least as far as I know. But rest assured, if for some reason you shouldn't unplug your drive after unmounting, Ubuntu will let you know.

As for your Firefox fonts issue:
Try the following: "System" -> "Preferences" -> "Appearance".
Then go to the Fonts tab.
Make sure that "Subpixel smoothing" is selected (I'm assuming you have an LCD screen, those fonts look a lot like mine before I solved it this way). If that doesn't make a difference (it should be felt immediatly) just click "Details" and tinker with the settings (no worries, I don't think you can break anything there).

Also, one more thing on the fonts - in firefox's preferences ("Edit" -> "Preferences" under the "Content" tab, in the Fonts & Colors make sure the default is "serif". In the advanced button, The four fonts should read: "Serif"; "serif"; "sans-serif"; "monospace". Also, the box "Allow pages to choose their own fonts, (......)" should be **checked**.

Owo, long reply! I hope this is of some help!
the prefs in the appearances are set as u have listed

what u have listed above for firefox is the original configuration, i have attached the screen shots of both my XP and Ubuntu google pages there is considerable difference, the only way i'm able to get it closer to the XP look is by overriding the default page font, WHICH I DONT WANT TO DO>SINCE ALL PAGES WOULD LOOK SIMILAR!!!

---

### Post by Stunts on 2008-08-12
Ok...
Seems you got all the config right.
I've examined your fonts in ubuntu and compared them with mine and your XP fonts.
Mine look better then any of yours. I'm not gloating or anything. They just look smoother. Your XP fonts also look a bit better then your ubuntu fonts. The difference is minimal, but it is defentley there. I feel your pain.
I had a laptop that suffered from similar issues. I never found a solution for it. But I think it was due to the monitor since I had the very same issue under windows (even with clear type fonts). The fonts would never look perfect. They looked good - just not perfect.
Just tell me a couple of things:
Your monitor type and your graphics adapter;
I'm strating to get a bit off of my league here...

Edit:
One more thing - what resolution are you on? And does the problem sticks if you change it?

---

### Post by Stunts on 2008-08-12
Also, you may want to take a look at this thread:

[http://ubuntuforums.org/showthread.php?t=881989](http://ubuntuforums.org/showthread.php?t=881989)

Good luck!

I recommend starting with:
```
sudo apt-get purge msttcorefonts
```

This will remove the installation you made of mscorefonts, plus any eventual config files...

---

### Post by macvr on 2008-08-12
> **Stunts said:**
> Also, you may want to take a look at this thread:

[http://ubuntuforums.org/showthread.php?t=881989](http://ubuntuforums.org/showthread.php?t=881989)

Good luck!

I recommend starting with:
```
sudo apt-get purge msttcorefonts
```

This will remove the installation you made of mscorefonts, plus any eventual config files...
my screen resolution is -1280x800 n the fonts dont seem to change with resolution changes

i done all listed in the post recommended, started with the purge

but i'v realized that this is how windows looks without the CLEARTYPE SMOOTH FONT EDGES option enabled...
so i guess my real solution would be to have the similar clear smooth font edges

i have attached the screenshots for comparison
1-XP with standard font edges
2-XP with CLEARTYPE SMOOTH font edges
3-UBUNTU without ms fonts
4-UBUNTU with MSttcorefonts installed[looks closer to 1]

**_[COLOR="Blue"]in ubuntu ,the subpixel smoothing is on, hinting is set to full,but it acts only on the original ubuntu fonts but not on the msttcore fonts>NOR ON THE DISPLAYED PAGES[/COLOR]_**

[COLOR="Red"]_so how do i get the smooth font edges set for atleast the webpages ?_[/COLOR]
or is this a ubuntu bug?which wont allow smoothing of other fonts?

---

### Post by macvr on 2008-08-13
> **macvr said:**
> hi guys,
i'm new to ubuntu, and linux on the whole. just a few days back installed the ubuntu desktop 8.04.1 with dual boot option with XP professional
 need help with a few stuff!
[LIST=1]
[*][SIZE="3"][COLOR="RoyalBlue"]my _fonts in firefox_ are weird , especially in GOOGLE, i think its the times new roman fonts ,i have downloaded the msfonts and i have set the fonts in other general settings but the fonts in firefox and thunderbird always remain weird while all other app fonts are fine
[/COLOR][/SIZE]

[*]the first time i connected my external drive and unmounted the drive i got a _notification_ that said the device was unmounted or that it was safe to remove the drive (i'm not sure of the exact notification but i got one) but after that i dont seem to get a notification after i unmount my external drive, HAVE I MESSED UP MY SETTINGS , HOW DO I MAKE UBUNTU TO GIVE THAT NOTIFICATION EVERY TIME I UNMOUNT THE DRIVE, feels a bit scary not to get that notification and to remove the drive, just scared that i might corrupt my data!
[COLOR="RoyalBlue"]

[*]i have moved my top _panel_ to the right, with my bottom panel at the bottom, but when i restarted the bottom panel showed up in the top!!! is it always necessary for one panel to be on top?[/COLOR]

[*] to install new _themes_ what do i have to do initially(i mean , what other software do i have to have installed), also i really confused as to what type of file i can use on my system gtk/metacity/compiz/beryl for desktop themes for pointers is X11 mouse theme the one to use?
[COLOR="Blue"]

[*]when i take _screen shots_ it always saves as .png how to make it save as .jpg? couldnt upload the screen shot of the weird fonts in firefox!!![/COLOR]

[SIZE="3"][*]i'm not able to enable _touchpad_ settings , tried to enable the shmconfig as true but it kept saying that shmconfig is disabled, (tired with on, 1) also but no effect
[COLOR="Blue"][/SIZE]

[*] can firefox, thunderbird be used in dual boot with the _same profile sharing_ ( there where a few tutorials[http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux]("http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux") )    but while using it i tried to flag a mail in thunderbird but it kept crashing ,and it didnt work well for firefox. 
so my ques is just that if this has been done by anyone, does sharing work fully?[/COLOR]

[*]while using thunderbird with webmail > i keep getting message that "_local host_ connection was refused" how do i correct this?

[/LIST]

i'v tried googling and also searching these forums,tried a lot of the solutions, got totally confused:confused: thats why i posted this long list!!!

thanks in advance

guys still have not figured out
 1)how to make msfonts smooth
 6)touchpad

---

### Post by Stunts on 2008-08-13
Fortunately your problem is not like the one I had on my previous laptop.
What display drivers are you using?
That could be the issue...

As for your touchpad... What functions are you looking for?
My laptop has a simple touchpad, but all functions worked out of the box.
Did you try 
```
 sudo apt-get install gsynaptics
```
and then run it?
System -> Preferences -> Touchpad.

---

### Post by macvr on 2008-08-13
> **Stunts said:**
> Fortunately your problem is not like the one I had on my previous laptop.
What display drivers are you using?
That could be the issue...
how do i check this?, i use ATI restricted drivers, if thats what u mean?


> **Stunts said:**
> As for your touchpad... What functions are you looking for?
My laptop has a simple touchpad, but all functions worked out of the box.
Did you try 
```
 sudo apt-get install gsynaptics
```
and then run it?
System -> Preferences -> Touchpad.
i have done this but everytime i choose touchpad, i get the SHMconfig error as in pic

my touchpad is works but it just doesnt feel like how it did in XP, feels like it is like dragging a rock,whatever level i set the acceleration.

---

### Post by macvr on 2008-08-13
ok i'v got my touchpad settings...

but my fonts r still not smooth!!

---

### Post by appi2012 on 2008-08-13
Read this:
[http://ubuntu.wordpress.com/2007/09/16/installing-vista-fonts-in-ubuntu/](http://ubuntu.wordpress.com/2007/09/16/installing-vista-fonts-in-ubuntu/)
(Read the update first, before following the instructions. Also, ubuntu uses bash, so make sure you change what it says to change for bash.

Hope that helps

---

### Post by macvr on 2008-08-13
> **appi2012 said:**
> Read this:
[http://ubuntu.wordpress.com/2007/09/16/installing-vista-fonts-in-ubuntu/](http://ubuntu.wordpress.com/2007/09/16/installing-vista-fonts-in-ubuntu/)
(Read the update first, before following the instructions. Also, ubuntu uses bash, so make sure you change what it says to change for bash.

Hope that helps
i had seen this page previously but it didnt work

so i tried it now, after i created a .fonts folder in my home folder>>>
BUT NO CHANGE MSFONTS STILL DONT SMOOTHEN OUT,
SHOULD THE FONTS FOLDER created BE PLACED SOMEWHERE ELSE?

---

### Post by lukjad on 2008-08-13
Please, DON'T DO ALL CAPS. IT FEELS LIKE I AM BEING SCREAMED AT! And the .fonts folder should be placed in the home folder.

---

### Post by macvr on 2008-08-13
> **lukjad007 said:**
> Please, DON'T DO ALL CAPS. IT FEELS LIKE I AM BEING SCREAMED AT! And the .fonts folder should be placed in the home folder.
was not screaming:)ok i'll use underline to highlight hereafter

well the folder .fonts is in my user home folder only but doesnt smoothen the fonts!
do the msttcorefonts smoothen in your system?:confused:

i think in tyring to fix this>>> i might install all the fonts in the world!!!:lolflag:

---

### Post by Morpheun on 2008-08-13
> **macvr said:**
> i had seen this page previously but it didnt work

so i tried it now, after i created a .fonts folder in my home folder>>>
BUT NO CHANGE MSFONTS STILL DONT SMOOTHEN OUT,
SHOULD THE FONTS FOLDER created BE PLACED SOMEWHERE ELSE?

Reboot and check.

---

### Post by macvr on 2008-08-13
> **Morpheun said:**
> Reboot and check.

i had rebooted as soon as i installed the clear type fonts itself
but now i'v done it once again >>> _no change_

i checked the fonts folder it just seems to have added more fonts rather than smoothening out the existing  ms fonts [well i may be blabbering!]

---

### Post by Stunts on 2008-08-14
Hi.
Did you try this thread?
[http://ubuntuforums.org/showthread.php?t=4456](http://ubuntuforums.org/showthread.php?t=4456)
I think you're getting somewhere.

---

### Post by macvr on 2008-08-14
> **Stunts said:**
> Hi.
Did you try this thread?
[http://ubuntuforums.org/showthread.php?t=4456](http://ubuntuforums.org/showthread.php?t=4456)
I think you're getting somewhere.
ok i tried this thread but a lot of the posts are just going over my head so i only did whats given in the first post>
but didnt work for me

this is what i did:
i copied the file to my home>user folder then renamed it, didnt work
then i tried with the file in the .fontsconfg folder still didnt work

n i also restarted every time

head is aching from reading tht thread (it dates back to 2004!there where more than 200 posts)

i'm really confused... could you simplify it, if there are anything i'v missed?

---

### Post by macvr on 2008-08-15
anyone has an idea to smoothen the msfonts????

---

### Post by Canis familiaris on 2008-08-16
> **macvr said:**
> actually i have a thread running with this prob, could u check it out, has all the screen shots too

[http://ubuntuforums.org/showthread.php?t=887621]("http://ubuntuforums.org/showthread.php?t=887621")

noob ques> how do u disable compiz?
To disable Compiz (as you asked in the other thread while linking to this thread):
Go to:
System->Preferences->Appearance.
Choose Visual Effects Tab and select None.

A shortcut will be:
Press Alt+F2:
```
metacity --replace
```

Check whether the problem persists.

---

### Post by macvr on 2008-08-16
> **Anurag_panda said:**
> To disable Compiz (as you asked in the other thread while linking to this thread):
Go to:
System->Preferences->Appearance.
Choose Visual Effects Tab and select None.

A shortcut will be:
Press Alt+F2:
```
metacity --replace
```

Check whether the problem persists.
 s, still google looks like this!!

---

### Post by Canis familiaris on 2008-08-16
Just a shot in the dark:

Try renaming the mozilla config directory

Close Firefox.

Try this command:
```
mv .mozilla .mozilla.bak
```

Run Firefox and check again.

Note: You will temporarily "lose" your bookmarks, settings,etc.

To revert:
```
mv .mozilla .mozilla.bak2
mv .mozilla.bak .mozilla
```

---

### Post by macvr on 2008-08-16
> **Anurag_panda said:**
> Just a shot in the dark:

Try renaming the mozilla config directory

Close Firefox.

Try this command:
```
mv .mozilla .mozilla.bak
```

Run Firefox and check again.

Note: You will temporarily "lose" your bookmarks, settings,etc.

To revert:
```
mv .mozilla .mozilla.bak2
mv .mozilla.bak .mozilla
```

no didnt change a thing:(

---

### Post by macvr on 2008-08-16
could the fonts problem be a bug?

---

### Post by aktiwers on 2008-08-18
Did you ever mess around with Edit=> Preferences 
Then the "content" tab (see screenshot)

You can also go advanced there and mess around with some font settings.

---

### Post by macvr on 2008-08-18
> **aktiwers said:**
> Did you ever mess around with Edit=> Preferences 
Then the "content" tab (see screenshot)

You can also go advanced there and mess around with some font settings.

was i not supposed to do it? or are u asking me if i have not tried it?

i couldnt bare the sight of google so i'v overridden the fonts of all pages with bitstream charter.

but the problem now is that most of the pages seem monotonous, with the same font.

if u were suggesting that as a solution,[i think that its just a work around for my prob]
 >>>it works in firefox, but in thunderbird, even if i override the fonts, the fonts dont change, it looks  anorexic like the google pages

---

### Post by aktiwers on 2008-08-18
It was just a suggestion..  what if you install the MSfonts, wont they work in Firefox too?
[http://ubuntu.wordpress.com/2005/09/09/installing-microsoft-fonts/](http://ubuntu.wordpress.com/2005/09/09/installing-microsoft-fonts/)

---

### Post by macvr on 2008-08-18
> **aktiwers said:**
> It was just a suggestion..  what if you install the MSfonts, wont they work in Firefox too?
[http://ubuntu.wordpress.com/2005/09/09/installing-microsoft-fonts/](http://ubuntu.wordpress.com/2005/09/09/installing-microsoft-fonts/)

my problem lies ONLY with msttcorefonts!

all the other default ubuntu fonts work fine, and are smooth

---

### Post by macvr on 2008-08-28
if anyone has similar problems,
check out this post,unutbu has found the solution
[http://ubuntuforums.org/showpost.php?p=5681517&postcount=42]("http://ubuntuforums.org/showpost.php?p=5681517&postcount=42")


this solved my problem, all my fonts problem arose from the msfonts-rules.conf file .... i just need to edit it...:)

thanx everyone who has helped

---

### Post by Stunts on 2008-08-28
Owo!
I'm glad you've got it figured!
I was totally out of ideas.
It's odd that I'm not suffering from that very same issue...
Oh well, in case I ever come across it now I know how to fix it.

---

