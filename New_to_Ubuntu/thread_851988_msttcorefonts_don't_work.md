---
title: "msttcorefonts don't work"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by Bubtottle on 2008-07-07
I have recently decided to add many fonts to my Hardy Heron computer, in particular, the 6,760 fonts found here: [http://www.gnome-look.org/content/show.php/6%2C760+Fonts?content=9883]("http://www.gnome-look.org/content/show.php/6%2C760+Fonts?content=9883").

I installed the msttcorefonts package prior to adding these fonts. I added these fonts by creating a folder named .fonts in my home directory and copying the fonts there.

However, when I start OpenOffice, the default font is set to one called 'pug'. When I try to change font to Times New Roman, it changes, but Times New Roman looks exactly like 'pug'. All the other Microsoft fonts look like 'pug' as well. Also, any Microsoft fonts on webpages, especially Times New Roman, show up as 'pug'.

I have tried deleting 'pug' from .fonts but now the Microsoft fonts are being replaced by a font called 'Locust'. I have also tried reinstalling msttcorefonts with no success.

Any help getting the msttcorefonts to work would be greatly appreciated.

---

### Post by sayakb on 2008-07-07
Try copying them to /usr/share/fonts/truetype
Make a new folder **MyFonts** there (You need to launch nautilus as root: **gksudo nautilus**)
Put  all the fonts within the MyFonts folder.

---

### Post by Sef on 2008-07-07
Moved to Absolute Beginners.

---

### Post by Bubtottle on 2008-07-07
Right, I've copied the fonts from .fonts in my home directory to /usr/share/fonts/truetype/MyFonts and then deleted the .fonts folder. This gave no change to my situation. I have restarted the X server (Crtl+Alt+Backspace) with no avail. Thanks for helping, LinuxIsInnovation, any more ideas?

---

### Post by Bubtottle on 2008-07-18
Bump?

---

### Post by coffeecat on 2008-07-18
First point. Putting .ttf files in ~/.fonts, which is what you did first time round, is an excellent idea. I do it myself and it **always** works. I guess this was probably an Open Office problem and that moving the fonts to /usr/share/fonts... was a red-herring.

However.. having done that, there is one more step to take and they will have been installed system-wide. Open a terminal and do:

```
sudo fc-cache
```Once you've done that, make sure the fonts are indeed installed by going to System > Preferences > Appearance > Fonts. Click on any of the bars (you don't have to change anything) and check that the fonts are installed. If they are and you still have the original problem, then this is down to Open Office and you might want to start a new thread.


**Edit:** I've just re-read your first post, in particular:

> I installed the msttcorefonts package prior to adding these fonts. I added these fonts by creating a folder named .fonts in my home directory and copying the fonts there.If you install msttcorefonts using Synaptic or apt-get you don't have to do anything else. The installer does it for you, and the ms fonts will work in Open Office. What did you copy to ~/.fonts? Were they .ttf files or something else?

---

### Post by mastergunner on 2008-07-18
subscribe

---

### Post by Bubtottle on 2008-07-26
Coffeecat, I did what you said but nothing has changed. I have discovered that not only is OpenOffice using the wrong fonts, but Firefox is too, an annoying fact seeing as many terminal quotes are in Times New Roman.

As for
> I installed the msttcorefonts package prior to adding these fonts. I added these fonts by creating a folder named .fonts in my home directory and copying the fonts there.
I realise upon rereading that this is confusing. I did install msttcorefonts with Synaptic, it was the 6760 fonts that I put in .fonts.

If anyone can help it would be much appreciated.

---

### Post by Bubtottle on 2008-08-15
Bump?

---

### Post by GrandpaLeaman on 2008-08-15
Try this "sudo fc-cache -f" without the quotation marks of course. This should force scanning of all directories that have fonts.

---

### Post by macvr on 2008-08-16
i have same problem!!!

---

### Post by frankos44 on 2008-08-16
$ sudo apt-get install msttcorefonts
$ wget [http://www.osresources.com/files/centos-windows-fonts/fontconfig.tbz](http://www.osresources.com/files/centos-windows-fonts/fontconfig.tbz)
$ sudo tar xvjpf fontconfig.tbz -C /etc/fonts/

Logout out
Login in again

---

### Post by macvr on 2008-08-16
> **frankos44 said:**
> $ sudo apt-get install msttcorefonts
$ wget [http://www.osresources.com/files/centos-windows-fonts/fontconfig.tbz](http://www.osresources.com/files/centos-windows-fonts/fontconfig.tbz)
$ sudo tar xvjpf fontconfig.tbz -C /etc/fonts/

Logout out
Login in again

no doesnt work for me...
still fonts are like bad[pic]

could this be a bug?

---

### Post by frankos44 on 2008-08-17
Image looks fine on my pc. Are you sure you are using the native resolution for your screen?

---

### Post by macvr on 2008-08-17
> **frankos44 said:**
> Image looks fine on my pc. Are you sure you are using the native resolution for your screen?
tel me u are just kidding??? the words look anorexic!!! if u think that this is how google always looked for u, there is a better pleasing world :)

check out this post, it has pics of how the pages look like in xp with clear type fonts! by the way i use 1280x800 resolution

[http://ubuntuforums.org/showpost.php?p=5578365&postcount=20]("http://ubuntuforums.org/showpost.php?p=5578365&postcount=20")

open the pics in new tabs & view at the zoomed full pic, not in the zoomed out views, and if u r still not able to see difference, it would be weird!

---

### Post by frankos44 on 2008-08-17
The fonts looks identical to my windows laptop. I think your problem is either video matching or mismatch of screen resolution. 

Video matching on laptops is not an issue because the panels are driven digitally rather than use of analogue cable and analogue to digital converter found inside a separate LCD screen.

The font verticals are 1px thick without hinting and that is as thin as you can get. Different screen/graphics card combinations can give either sharp precise fonts or wishy washy difficult to read fonts, ive even seen black fonts flooded out almost completely by the white background behind them. 

I bet the fonts look heavier when you display white fonts on black background?

Often VGA cables make a big difference, generally the thicker the cable the better the quality. 

Sometimes a certain combination will never give good results and either graphics card or screen needs changing.

---

### Post by unutbu on 2008-08-17
Here are some things you might want to try:
[list]
[*]
```
sudo fc-cache -f -v    # As coffeecat, GrandpaLeaman suggested
sudo /usr/bin/defoma-font register-all /etc/defoma/hints/msttcorefonts.hints
```

[http://lists.debian.org/debian-user/2007/05/msg00307.html](http://lists.debian.org/debian-user/2007/05/msg00307.html) seems to suggest the sudo might be important when running fc-cache.

[*] Sanity check: Did msttcorefonts succeed in downloading Arial?
```

% locate Arial
/usr/share/doc/libsdl-perl/test/data/24P_Arial_NeonYellow.png
/usr/share/fonts/truetype/msttcorefonts/Arial_Italic.ttf
/usr/share/fonts/truetype/msttcorefonts/Arial_Bold.ttf
/usr/share/fonts/truetype/msttcorefonts/Arial_Black.ttf
/usr/share/fonts/truetype/msttcorefonts/Arial_Bold_Italic.ttf
/usr/share/fonts/truetype/msttcorefonts/Arial.ttf
/var/lib/defoma/gs.d/dirs/fonts/Arial_Italic.ttf
/var/lib/defoma/gs.d/dirs/fonts/Arial_Bold.ttf
/var/lib/defoma/gs.d/dirs/fonts/Arial_Black.ttf
/var/lib/defoma/gs.d/dirs/fonts/Arial_Bold_Italic.ttf
/var/lib/defoma/gs.d/dirs/fonts/Arial.ttf
/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType/Arial_Italic.ttf
/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType/Arial_Bold.ttf
/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType/Arial_Black.ttf
/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType/Arial_Bold_Italic.ttf
/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType/Arial.ttf
/var/lib/defoma/fontconfig.d/A/Arial-BoldItalic.ttf
/var/lib/defoma/fontconfig.d/A/Arial-Regular.ttf
/var/lib/defoma/fontconfig.d/A/Arial-Italic.ttf
/var/lib/defoma/fontconfig.d/A/Arial-Bold.ttf
/var/lib/defoma/fontconfig.d/A/ArialBlack-Regular.ttf
```
```

gnome-font-viewer file:///usr/share/fonts/truetype/msttcorefonts/Arial_Black.ttf

```
A window should pop up showing you the font nicely rendered.

[*] For Firefox at least: Click Edit>Preferences. Click the "Advanced" button in the "Font & Colors" section to get to the second window. Perhaps try font settings such as those shown in the attachments.

The settings shown do not make use of msttcorefonts (I don't think), but it should make the fonts look better.

Make sure the "Allow pages to choose their own fonts" box is *not* enabled.
[/list]

---

### Post by macvr on 2008-08-17
> **frankos44 said:**
> The fonts looks identical to my windows laptop. I think your problem is either video matching or mismatch of screen resolution.  
have u checked out that post? i have attached 4 pics in that post all taken from the same laptop.
my present appearance in ubuntu with msttcore fonts resembles XP _without_ the clear type font option. that looks bad. it is similar to the ubuntu fonts without smoothening.
my problem seems to be that the _msttcore fonts do not smoothen_ when i have selected the option.:(

pls check out those pics n tell me that there is a difference between pic2 and pic 4,else i need to get my eyes checked:(

> **frankos44 said:**
> I bet the fonts look heavier when you display white fonts on black background?


no they dont look heavier. they look the same anorexic:(
as i have stated above the problem seems to lie in the fact that the msttcorefonts dont smoothen!

*i dont know if ubuntu smoothens msttcore fonts* if someone knows this pls inform.

> **unutbu said:**
> Here are some things you might want to try:
[list]
[*]
```
sudo fc-cache -f -v    # As coffeecat, GrandpaLeaman suggested
sudo /usr/bin/defoma-font register-all /etc/defoma/hints/msttcorefonts.hints
```

[http://lists.debian.org/debian-user/2007/05/msg00307.html](http://lists.debian.org/debian-user/2007/05/msg00307.html) seems to suggest the sudo might be important when running fc-cache.
i have done this sudo cache several times, i'v also removed the fonts completely and installed it again from synaptics


> **unutbu said:**
> [*] For Firefox at least: Click Edit>Preferences. Click the "Advanced" button in the "Font & Colors" section to get to the second window. Perhaps try font settings such as those shown in the attachments.

The settings shown do not make use of msttcorefonts (I don't think), but it should make the fonts look better.

Make sure the "Allow pages to choose their own fonts" box is *not* enabled.
[/list]

this is what i'm doing i'm over riding the global fonts wit "bitstream charter" > this font seems better for me

but for some reason if i try doing this in thunderbird, it doesnt work!!!

> **unutbu said:**
> [*] Sanity check: Did msttcorefonts succeed in downloading Arial?
```

% locate Arial
_/usr/share/doc/libsdl-perl/test/data/24P_Arial_NeonYellow.png_
/usr/share/fonts/truetype/msttcorefonts/Arial_Italic.ttf
/usr/share/fonts/truetype/msttcorefonts/Arial_Bold.ttf
/usr/share/fonts/truetype/msttcorefonts/Arial_Black.ttf
/usr/share/fonts/truetype/msttcorefonts/Arial_Bold_Italic.ttf
/usr/share/fonts/truetype/msttcorefonts/Arial.ttf
/var/lib/defoma/gs.d/dirs/fonts/Arial_Italic.ttf
/var/lib/defoma/gs.d/dirs/fonts/Arial_Bold.ttf
/var/lib/defoma/gs.d/dirs/fonts/Arial_Black.ttf
/var/lib/defoma/gs.d/dirs/fonts/Arial_Bold_Italic.ttf
/var/lib/defoma/gs.d/dirs/fonts/Arial.ttf
/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType/Arial_Italic.ttf
/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType/Arial_Bold.ttf
/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType/Arial_Black.ttf
/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType/Arial_Bold_Italic.ttf
/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType/Arial.ttf[U]
/var/lib/defoma/fontconfig.d/A/Arial-BoldItalic.ttf
/var/lib/defoma/fontconfig.d/A/Arial-Regular.ttf
/var/lib/defoma/fontconfig.d/A/Arial-Italic.ttf
/var/lib/defoma/fontconfig.d/A/Arial-Bold.ttf
/var/lib/defoma/fontconfig.d/A/ArialBlack-Regular.ttf[/U]
```
```

gnome-font-viewer file:///usr/share/fonts/truetype/msttcorefonts/Arial_Black.ttf

```
A window should pop up showing you the font nicely rendered.

ok i searched my system, these above underlined files are missing:( /var/lib/defoma/fontconfig.d/A/ folder itself is not there!!!
i think u may have found something.
i have installed the msttcorefonts twice, and those files are missing!!!
what do i do?
 
look my view of the forums is bad if i dont over ride the fonts!!!

---

### Post by benerivo on 2008-08-17
> **macvr said:**
> ok i searched my system, these above underlined files are missing:( /var/lib/defoma/fontconfig.d/A/ folder itself is not there!!!
i think u may have found something.
i have installed the msttcorefonts twice, and those files are missing!!!
what do i do?

My mstt fonts are fine, and i don't have any folders in /var/lib/defoma/fontconfig.d/, so i don't think this is definitely your problem. Have you tried```
sudo dpkg-reconfigure fontconfig-config
```followed by```
sudo dpkg-reconfigure fontconfig
```then logging out, then Ctrl+Alt+Backspace, then logging back in.

---

### Post by macvr on 2008-08-17
> **benerivo said:**
> My mstt fonts are fine, and i don't have any folders in /var/lib/defoma/fontconfig.d/, so i don't think this is definitely your problem. Have you tried```
sudo dpkg-reconfigure fontconfig-config
```followed by```
sudo dpkg-reconfigure fontconfig
```then logging out, then Ctrl+Alt+Backspace, then logging back in.

this hasnt done it yet?
still the fonts are weird :(

could u post ur screenshot just to confirm that its my system that is confused:confused:

---

### Post by unutbu on 2008-08-17
macvr, you might want to create a new user account -- at least temporarily -- and see if the problem exists there too. If not, you know that the problem lies in some config file in your home directory, otherwise you'll know the problem is system-wide.

---

### Post by benerivo on 2008-08-17
Looking at your screenshot, your fonts display is bad. it is not your monitor - as can be seen by looking at the graphics (other than the text). Here is my screen from a google search. Be careful with comparing screenshots as a lot depends on what browser is used, and what the font settings are within that browser.

---

### Post by macvr on 2008-08-17
> **benerivo said:**
> Looking at your screenshot, your fonts display is bad. it is not your monitor - as can be seen by looking at the graphics (other than the text). Here is my screen from a google search. Be careful with comparing screenshots as a lot depends on what browser is used, and what the font settings are within that browser.
i'm using firefox.
ya other other ubuntu fonts are fine its only the new msttcorefonts that dont get smoothened

> **unutbu said:**
> macvr, you might want to create a new user account -- at least temporarily -- and see if the problem exists there too. If not, you know that the problem lies in some config file in your home directory, otherwise you'll know the problem is system-wide.

ok. i'm a noob...
so noob question> how to create new user? and how to delete FULLY later?
and what permissions/rights should be given?
if new user is created should i install the fonts again?

---

### Post by unutbu on 2008-08-17
**To create a new user:**
Go to the GNOME menu at the top of your screen. 
Click on System>Administration>Users and Groups.
A window will pop up.
Click Add User. Fill in the basic information, then click Ok.

**To delete a user:**
Click on System>Administration>Users and Groups.
Click on the name of the user.
Click Delete.

---

### Post by benerivo on 2008-08-17
[Here]("https://help.ubuntu.com/community/AddUsersHowto") is the official way, and i think it is through the same process, that you can delete the new user that you have created (you can see a delete button on one of the screenshots).

---

### Post by macvr on 2008-08-17
ok i tried with a different user> its the same there also


BUT I ACCIDENTALLY deleted my administrator account while actually trying to delete the new account,

but i'm using the my administrator account, now so how to i preserve my account

i can see my home folder

EDIT: i closed the users and groups and reopened it> my user is listed
will i be deleted when i logout?

---

### Post by unutbu on 2008-08-18
Type
```
grep $USER /etc/passwd
```
You should see something like
```

macvr:x:1000:1000:Macvr,,,:/home/macvr:/bin/bash
```

If you don't see any output, then it means your username has been deleted.
In this case:

Reboot. Press ESC (escape) to get to the GRUB menu. Select Recovery Mode.
This will drop you to a root shell. Type (changing macvr to your real username):

```
useradd -c "Macvr" -u 1000 -m macvr 
gpasswd -a macvr admin

```

---

### Post by macvr on 2008-08-18
thankz unutbu>>> i had actually started another thread for this user prob, and my account is safe....

but i'v gotten fed up with these msttcore fonts that i have removed it totally from my system...

the whole web uses ms fonts, hope ubuntu smoothens these fonts better,
or maybe its just a bug in my system,
if its a bug what do i do, how do i report it for fonts?

---

### Post by philinux on 2008-08-18
System>Prefs>Appearance choose the fonts tab. Then tick lcd smoothing. Then click details and choose slight.

Experiment with settings.

---

### Post by Bubtottle on 2008-08-22
I have tried the suggestions mentioned so far and none of them have worked. To rewrite what I did:
-Installed msttcorefonts through synaptic (they were working fine)
-Added the 6,760 fonts to a .fonts folder in my home folder (after that, msttcorefonts are replaced by fonts from the 6,760 fonts)

Some pictures are attached

---

### Post by macvr on 2008-08-28
> **philinux said:**
> System>Prefs>Appearance choose the fonts tab. Then tick lcd smoothing. Then click details and choose slight.

Experiment with settings.

i'v tried every combination, but _the Hinting and Smoothing just dont work on the msttcorefonts_, i can see in the preview itself , the options just dont work on the msttcore fonts

but still the fonts are anorexic:( check pic
does it have something to do with my ATI X1400 graphics card?

or is this a bug? shall file a report in launch pad?

---

### Post by unutbu on 2008-08-28
macvr, would you please post a screenshot of your Firefox Edit>Preferences>Content window, and then click the Advanced button (in the Fonts and Colors section) and show us a screenshot of that as well?

I'll try to reproduce the problem.

---

### Post by macvr on 2008-08-28
> **unutbu said:**
> macvr, would you please post a screenshot of your Firefox Edit>Preferences>Content window, and then click the Advanced button (in the Fonts and Colors section) and show us a screenshot of that as well?

I'll try to reproduce the problem.

i'm not sure, if its only a problem with firefox!
because when i check out the fonts preview in Appearances itself i can see the difference between ubuntu fonts and msttcore fonts

---

### Post by unutbu on 2008-08-28
macvr, I wasn't able to reproduce the problem. 
From the images you posted, it looks like the fonts are not getting anti-aliased.

Well, let's give this one more shot. If this doesn't help, then I'm afraid I've run out of ideas.


~/.fonts.conf can have an effect on anti-aliasing. You might already have this file, but if not, you can create it with a text editor. If you already have this file, make a backup copy so you can return to your current configuration if need be.

My .fonts.conf file looks like this:

```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
<match target="font" >
<edit mode="assign" name="rgba" > <const>rgb</const> </edit>
<edit mode="assign" name="hinting" > <bool>true</bool> </edit>
<edit mode="assign" name="antialias"> <bool>true</bool> </edit>
<edit mode="assign" name="autohint" > <bool>false</bool> </edit>
<edit mode="assign" name="hintstyle"> <const>hintfull</const> </edit>
</match>
</fontconfig>

```

You might have to log out / log back in for the file to take effect -- I'm not sure.

You could also try changing the true/false strings to see if that helps any.

If that does not work, you might want to try the .fonts.conf posted here:
[https://wiki.ubuntu.com/Fonts](https://wiki.ubuntu.com/Fonts) (search for the word 'alias')

The file is rather old, but it wouldn't hurt to try it.

---

### Post by macvr on 2008-08-28
> **unutbu said:**
> macvr, I wasn't able to reproduce the problem. 
From the images you posted, it looks like the fonts are not getting anti-aliased.

Well, let's give this one more shot. If this doesn't help, then I'm afraid I've run out of ideas.


~/.fonts.conf can have an effect on anti-aliasing. You might already have this file, but if not, you can create it with a text editor. If you already have this file, make a backup copy so you can return to your current configuration if need be.



ok noob question:
_~/.fonts.config_ file isnt that referring to the .fonts.config file in my HOME folder...?
if it is > i dont have such file in my main home folder!
so shal i create 1 with ur same config in my home folder?

---

### Post by unutbu on 2008-08-28
Yes, that's exactly right. The tilde (~) means "the path to your home account". It would mean /home/macvr if your username is macvr.

Also, in nautilus, you might have to press Ctrl-h in order to see so-called hidden dot files -- any file while filename begins with a period.

---

### Post by macvr on 2008-08-28
> **unutbu said:**
> Yes, that's exactly right. The tilde (~) means "the path to your home account". It would mean /home/macvr if your username is macvr.

Also, in nautilus, you might have to press Ctrl-h in order to see so-called hidden dot files -- any file while filename begins with a period.

i had checked the hidden files it's was not there.

---

### Post by macvr on 2008-08-28
> **unutbu said:**
> macvr, I wasn't able to reproduce the problem. 
From the images you posted, it looks like the fonts are not getting anti-aliased.

Well, let's give this one more shot. If this doesn't help, then I'm afraid I've run out of ideas.


~/.fonts.conf can have an effect on anti-aliasing. You might already have this file, but if not, you can create it with a text editor. If you already have this file, make a backup copy so you can return to your current configuration if need be.

My .fonts.conf file looks like this:

```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
<match target="font" >
<edit mode="assign" name="rgba" > <const>rgb</const> </edit>
<edit mode="assign" name="hinting" > <bool>true</bool> </edit>
<edit mode="assign" name="antialias"> <bool>true</bool> </edit>
<edit mode="assign" name="autohint" > <bool>false</bool> </edit>
<edit mode="assign" name="hintstyle"> <const>hintfull</const> </edit>
</match>
</fontconfig>

```

You might have to log out / log back in for the file to take effect -- I'm not sure.

You could also try changing the true/false strings to see if that helps any.

If that does not work, you might want to try the .fonts.conf posted here:
[https://wiki.ubuntu.com/Fonts](https://wiki.ubuntu.com/Fonts) (search for the word 'alias')

The file is rather old, but it wouldn't hurt to try it.

i tried with ur conf and also the conf from the wiki...

didnt work!!! tried changing the strings in urs> no change!!!

will try changing strings with the big one from that page


ALSO are the fonts controlled else where? i'd like to change those settings and check ....

---

### Post by macvr on 2008-08-28
oh i forgot to mention, this is font problem is not confined to my user settings, its universal...
so i'd like to know where to tweak to make effects universal?

---

### Post by unutbu on 2008-08-28
I believe the system-wide equivalent of ~/.fonts.conf is /etc/fonts/fonts.conf. If changing your personal .fonts.conf did not work, however, I'm not so confident that editing the /etc/fonts/fonts.conf file will work though.

Even so, if you run
```

cd /etc
tar cf ~/fonts.tar fonts
cd
bzip2 fonts.tar
```
and post (as an attachment) the file
~/fonts.tar.bz2, I'll compare it with mine and see if anything sticks out.

---

### Post by macvr on 2008-08-28
> **unutbu said:**
> I believe the system-wide equivalent of ~/.fonts.conf is /etc/fonts/fonts.conf. If changing your personal .fonts.conf did not work, however, I'm not so confident that editing the /etc/fonts/fonts.conf file will work though.

Even so, if you run
```

cd /etc
tar cf ~/fonts.tar fonts
cd
bzip2 fonts.tar
```
and post (as an attachment) the file
~/fonts.tar.bz2, I'll compare it with mine and see if anything sticks out.

ok i'v attached the fonts config file...

---

### Post by unutbu on 2008-08-28
If you look inside the file /etc/fonts/msfonts-rules.conf
you'll see a bunch of rules that look like this:
```

<match target="font" >
	<test name="family" >
		<string>Andale Mono</string>
	</test>
	<test compare="less" name="pixelsize" qual="any" >
		<double>19</double>
	</test>
	<test compare="eq" target="pattern" name="slant" >
		<const>roman</const>
	</test>
[COLOR="Red"]	<edit mode="assign" name="antialias" >
		<bool>false</bool>[/COLOR]
	</edit>
</match>
```

Notice that it seems to be setting antialias to false. My understanding of font configuration is very slight, but perhaps it is worth trying to stop this file from asserting its rules.

Try the following:
```

sudo mv /etc/fonts/msfonts-rules.conf /root/
```

Then reboot. See if the fonts look better. 

If not, to return the system to its current state:
```

sudo mv /root/msfonts-rules.conf /etc/fonts/
```

---

### Post by macvr on 2008-08-28
> **unutbu said:**
> If you look inside the file /etc/fonts/msfonts-rules.conf
you'll see a bunch of rules that look like this:
```

<match target="font" >
	<test name="family" >
		<string>Andale Mono</string>
	</test>
	<test compare="less" name="pixelsize" qual="any" >
		<double>19</double>
	</test>
	<test compare="eq" target="pattern" name="slant" >
		<const>roman</const>
	</test>
[COLOR="Red"]	<edit mode="assign" name="antialias" >
		<bool>false</bool>[/COLOR]
	</edit>
</match>
```

Notice that it seems to be setting antialias to false. My understanding of font configuration is very slight, but perhaps it is worth trying to stop this file from asserting its rules.

Try the following:
```

sudo mv /etc/fonts/msfonts-rules.conf /root/
```

Then reboot. See if the fonts look better. 

If not, to return the system to its current state:
```

sudo mv /root/msfonts-rules.conf /etc/fonts/
```

unutbu u the man!!!!:guitar:

it worked, it worked ,it worked!!!=D>=D>=D> [attached pic]

man this font thing was bugging me so badly. that i had removed the msttcore fonts completely!!! AND IN a last ditch attempt i tried to bump this thread, thank goodness it caught ur eye!!!:)

ok now that thats the source of the error ,can i just change the antialias to true in that file? or is it not safe to do so?
also check the screenshot of the fonts folder> it shows the ms rules file as an executable file! is that normal?

---

### Post by unutbu on 2008-08-28
I'm happy that it worked!
Yes, you could also experiment with changing antialias from false to true. No great harm can come from this. If you ever need to restore you /etc/fonts dir, you can go back to your post and download your tar.bz2 file again (then edit or remove msfonts-rules.conf again).

You are right that the *.conf and *.dtd files should not have the executable bit set. Since the program that reads these files is not going to try to execute them, however, it makes little difference if the executable bit is set or not. However, if you want it to be proper, you could run
```

find /etc/fonts -type f -print0 | xargs -0 sudo chmod -R 644
```

---

### Post by macvr on 2008-08-28
> **unutbu said:**
> 
```

find /etc/fonts -type f -print0 | xargs -0 sudo chmod -R 644
```
i ran the command, now all the *.conf files are now not executables... 

i shall play around with the ms rules file ;)

thankx once again for all the help unutbu:)

---

### Post by macvr on 2008-08-28
ok i'v edited the msfont-rules.conf file and set all the anti-alias strings to "true" and now the fonts work fine, if the file is moved, ubuntu was not replacing the web fonts properly[can compare the pics i'v posted above and now], even though it shows the fonts perfectly in the Appearances preview ...
i also had to set auto-hinting to "true"
and now my msttcore-fonts work properly:)

---

### Post by vikrant82 on 2008-08-30
Ok, finally I think, I landed upon the correct thread. I was wondering about this for 15 days now. 

My MS fonts suffered similar fate one fine night, with some intrepid updates.

After struggling a lot, ([http://ubuntuforums.org/showthread.php?p=5692370](http://ubuntuforums.org/showthread.php?p=5692370)), some one suggested it could be MS fonts and subsequent searching lands me here, hopefully at the right place.

Ok, so for me, Firstly, I don't have any "msfonts-rules.conf" file in my /etc/font.

Secondly, I also seem to be struggling with same issue with MS fonts.

I will try to put msfonts-rules.conf file with antialiasing enabled and see what happens. Meanwhile, I will attach my /etc/fonts, for someone who is kind enough(read 'unutbu') to anaylse and point out some differences.

I am sure everything was working fine and this happened at some point when some updates were pushed to intrepid.

---

### Post by vikrant82 on 2008-08-30
Ok, I think placing "msfonts-rules.conf" file has had some improvements.

But some pages still have broken anti aliasing on some fonts. So probably I need to mention a few more fonts in there.

For e.g. this page : [http://kakku.wordpress.com/2008/06/25/change-default-remote-desktop-port-from-3389-to-something-else/](http://kakku.wordpress.com/2008/06/25/change-default-remote-desktop-port-from-3389-to-something-else/)

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=83351&stc=1&d=1220082370[/IMG]

Can anyone else comment on how this page renders for others.

---

### Post by anwardeen on 2008-08-30
come and meet me for BUSINESS


**_*[www.daniel.com](www.daniel.com)*_**

---

### Post by vikrant82 on 2008-08-30
I can live my life for now. Ignoring a few pages wont hurt.

---

### Post by macvr on 2008-08-30
> **vikrant82 said:**
> 

For e.g. this page : [http://kakku.wordpress.com/2008/06/25/change-default-remote-desktop-port-from-3389-to-something-else/](http://kakku.wordpress.com/2008/06/25/change-default-remote-desktop-port-from-3389-to-something-else/)


Can anyone else comment on how this page renders for others.

hi, i'v attached the pic ,this is how its rendered for me

---

### Post by macvr on 2008-08-30
why dont u download my fonts folder attached above and add the msrules file to ur fonts folder than having to add rules for each font!

but i found that the msfonts worked for me even without that msrules file in the folder

if u want to add it , just edit the antialias to true

---

### Post by vikrant82 on 2008-08-30
I have tried doing that. Even now, most of my font folder resembles yours.

By the way how did you get those configs. I assume they are not there by default?

Most of my fonts feel better now, apart from some fonts, like the one one page I just screen shotted. Even using your fonts folder doesn't help on that page. 

May be that font is MS Sans Serif or Helvetica.

---

### Post by vikrant82 on 2008-08-30
Hey, I just did a dpkg-reconfigure fontconfig and fc-cache and rebooted, and that did it.. :)

---

### Post by macvr on 2008-08-30
do u know what font the bold ones are?[arial bold?]

i dont think its working correctly for me, just seems too bold!
or is it th same way it gets rendered for all in ubuntu?

PS: i dont know how i got the msrules!

---

### Post by vikrant82 on 2008-08-30
I was just playing around with your font folder.

Its not the msfont-rules.conf that was doing it for me.

It seems on intrepid something's wrong in folder /etc/fonts/conf.d 

So just replacing, files here with yours (ofcourse conf.avail folder as well) does it for me. No other files added or removed.

So your problem might be entirely different from mine. In my case, the files got updated with some intrepid updates.

P.S. The forum looks exactly same as you for me. But that may be coz, I am using your files :)

---

### Post by macvr on 2008-08-30
is that how those fonts are supposed to look?
i'd want to be sure what fonts those bold ones are? [i think it looks like arial bold]
they act the same stupid way in all websites, i'd want to delete those fonts!
[if any1 knows , pls let me know, i dont want to try with installing and reinstalling every font!]

---

### Post by unutbu on 2008-08-30
> 
i dont think its working correctly for me, just seems too bold!


macvr, if you do not have a ~/.fonts.conf file, click on System>Preferences>Appearance>Fonts (tab)>Details (button) and play with the hinting options.

If you do have a ~/.fonts.conf file, edit it so hintstyle is set to hintfull:
```

<edit mode="assign" name="hintstyle"> <const>hintfull</const> </edit>
```

Log out / log in to make the change take effect.

Compare that with 
```

<edit mode="assign" name="hintstyle"> <const>hintnone</const> </edit>

```
Attached is a GIMP xcf file with two layers. Each layer is a screenshot of part of the ubuntuforums page, one rendered with hintfull, the other with hintnone. Open the xcf file with GIMP, click on Dialogs>Layers. In the Layers window that pops up, click on the eyeball next to the "hintnone" layer to toggle viewing that layer. This will show you the effect of hintfull versus hintnone.

PS. You can find more options for things to try changing in [http://fontconfig.org/fontconfig-user.html](http://fontconfig.org/fontconfig-user.html)

---

### Post by macvr on 2008-08-31
> **unutbu said:**
> macvr, if you do not have a ~/.fonts.conf file, click on System>Preferences>Appearance>Fonts (tab)>Details (button) and play with the hinting options.
i dont have a~/.fonts.conf file,
so i tried with the prefs GUI> previously itself the hint was set to full...

weird thing is in my system the fonts behave opposite to the hint full/none effects!!!:(

check the pics the first 1 is hint none, 2nd is hint full...

u can c that the fonts get worse when hint is full!!!:confused:[and no the pics have not been labeled wrongly!i'v taken the screen shots several times!to be sure:(]

> **unutbu said:**
> 
Attached is a GIMP xcf file with two layers. Each layer is a screenshot of part of the ubuntuforums page, one rendered with hintfull, the other with hintnone. Open the xcf file with GIMP, click on Dialogs>Layers. In the Layers window that pops up, click on the eyeball next to the "hintnone" layer to toggle viewing that layer. This will show you the effect of hintfull versus hintnone.
its even more painfull seein this xcf file!!! why dont i have fonts that behave so well!!!:confused:

> **unutbu said:**
> http://fontconfig.org/fontconfig-user.html[/url]
i'm trying to figure out from this what can be wrong!

[B][I]like vikrant82 says that since he is usin my font config files  and seems to have the same output as mine!!!seems my fonts conf is totally messed up
it would be nice if someone uploaded their files and i could just replace them [/I][/B]
the funny thing is tht i didnt even know where the fonts files were till i realized that the fonts are messed up!so i dont know how they got messed up! any ideas ?:confused:

---

### Post by unutbu on 2008-08-31
macvr, attached you will find my fonts.tar.bz2 (from /etc/fonts/).
I do not have all the fonts you have, so you might have to run 
```

sudo fc-cache -f -v
```

to make your system (re)aware of other fonts you have installed.

Also attached are my System>Preferences>Appearance settings.

In [http://ubuntuforums.org/showpost.php?p=5607447&postcount=17](http://ubuntuforums.org/showpost.php?p=5607447&postcount=17) you'll find my Firefox preference settings. 

In [http://ubuntuforums.org/showpost.php?p=5680546&postcount=34](http://ubuntuforums.org/showpost.php?p=5680546&postcount=34) you'll find my ~/.fonts.conf file.

These are all the places I know about for font configuration.

---

### Post by vikrant82 on 2008-08-31
Hey, your fonts folder is definetely better than macvr's. 

That extra boldness with his font folder, is definetely gone here. What ubuntu version are you on currently ?

---

### Post by unutbu on 2008-08-31
I'm running Gutsy 7.10 here. :lolflag:

---

### Post by macvr on 2008-08-31
wow these fonts conf work perfect!:) fonts are sleeker now

will compare with my fonts folder and see where the defect was

by the way unutbu,i get error when i did the "sudo fc-cache -f -v"

this file in ur config seems to have an error in the 
>etc/fonts/conf.d/53-monospace-lcd-filter.conf


```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<!-- conf.d/monospace-lcd-filter.conf -->
<fontconfig>
<!--  Use legacy LCD filter on smaller Monospace fonts -->
  <match target="font">
    <test name="family">
      <string>DejaVu Sans Mono</string>
      <string>Bitstream Vera Sans Mono</string>
    </test>
    <test name="pixelsize" compare="less_eq">
      <double>12.0</double>
    </test>

    <edit name="lcdfilter" mode="assign">
      <const>[COLOR="Red"]legacy[/COLOR]</const>
    </edit>
    <edit name="hintstyle" mode="assign">
      <const>hintfull</const>
    </edit>
  </match>
</fontconfig>
```

i checked with mine, if i change it to
```

    <edit name="lcdfilter" mode="assign">
      <const>[COLOR="Red"]lcdfilterlegacy[/COLOR]</const>
    </edit>

```
i dont get the error

---

### Post by macvr on 2008-08-31
if any1 could tel what font is used for the bold font in this forum, my search for the error in my files could get easier :-) [my error is mostly with those fonts]

---

### Post by unutbu on 2008-08-31
Yes, I noticed that too. Well, "legacy" works for me, and "lcdfilterlegacy" works for you, so I'm guessing that there have been changes to the allowable keywords 
between Gutsy 7.10 and Heron 8.04 (or Intrepid).

---

### Post by macvr on 2008-08-31
> **unutbu said:**
>  so I'm guessing that there have been changes to the allowable keywords 
between Gutsy 7.10 and Heron 8.04 (or Intrepid).
oh crap!

that is going to make my search even more tougher
[by the way ur fonts do make the bold ones sleeker but *other regular fonts just unnecessarily get shrunk too, so had to set my HINT to slight! * thats y i want to search for the prob!]

[B]hope someone else using ubuntu 8.04 is kind enough to upload their fonts folder? 
could some one pls upload their fonts folder?
[/B]

---

### Post by unutbu on 2008-08-31
The bold font which is showing up on your screen (and caused by Ubuntuforums style sheet) is Verdana-Bold.

The Ubuntuforums style sheet is here: [http://ubuntuforums.org/clientscript/vbulletin_css/style-7be2532f-00098.css](http://ubuntuforums.org/clientscript/vbulletin_css/style-7be2532f-00098.css)

There, Verdana, Arial, and Tahoma are referenced.

The command
```

gnome-thumbnail-font --text "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ" /usr/share/fonts/truetype/msttcorefonts/Verdana_Bold.ttf ~/Verdana_Bold.png
```
will give you a sample of the Verdana-Bold font.

Compare the Q in "Quick Links" to the Q in ~/Verdana_Bold.png.

---

### Post by macvr on 2008-08-31
> **unutbu said:**
> The bold font which is showing up on your screen (and caused by Ubuntuforums style sheet) is Verdana-Bold.

The Ubuntuforums style sheet is here: [http://ubuntuforums.org/clientscript/vbulletin_css/style-7be2532f-00098.css](http://ubuntuforums.org/clientscript/vbulletin_css/style-7be2532f-00098.css)

There, Verdana, Arial, and Tahoma are referenced.

The command
```

gnome-thumbnail-font --text "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ" /usr/share/fonts/truetype/msttcorefonts/Verdana_Bold.ttf ~/Verdana_Bold.png
```
will give you a sample of the Verdana-Bold font.

Compare the Q in "Quick Links" to the Q in ~/Verdana_Bold.png.

yup, Veranda is the one...

will try to see what's wrong in my config!

---

### Post by macvr on 2008-09-01
oh, got the ubuntu 8.04 font config[works much better]

also added tahoma fonts from my xp partition, MY EYES DONT HURT NOW:)
fully set now to take on the web:guitar:

PS: vikrant82> u can also get it from this post[http://ubuntuforums.org/showpost.php?p=5703571&postcount=2]("http://ubuntuforums.org/showpost.php?p=5703571&postcount=2")
can also check the difference in the forum bold fonts[i'v attached a screenshot there].

EDIT: or u can just change as in the post below

---

### Post by macvr on 2008-09-01
ok, i'v found the source of ALL my font problems>
i have this file: **_/etc/fonts/conf.d/10-autohint.conf _**
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
<!--  Use the Autohinter --> 
  <match target="font">
    <edit name="autohint" mode="assign"><bool>[COLOR="Red"]true[/COLOR]</bool></edit>
  </match>
</fontconfig>
```

when i set it to [COLOR="Red"]false[/COLOR] all the hinting problems magically disappear...

now the fun starts!
when it set to false, i have font problems in Thunderbird!!!
check the attachments[1-false, 2-true]
it gets worse in the actual mails!!!

since this is out of topic from this thread i'v started a new thread:[http://ubuntuforums.org/showthread.php?p=5704854#post5704854]("http://ubuntuforums.org/showthread.php?p=5704854#post5704854")

---

