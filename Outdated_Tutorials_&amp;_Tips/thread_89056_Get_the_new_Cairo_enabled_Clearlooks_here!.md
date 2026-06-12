---
title: "Get the new Cairo enabled Clearlooks here!"
date: 2005-11-11
forum: Outdated Tutorials &amp; Tips
---

### Post by Omer on 2005-11-11
[tirpse]("http://myeburg.net/") (aka SchAmane) made a Clearlooks gtk-engine patch to get animated progressbar and checkboxes using cairo.
Watch the demos for [animated checkbox]("http://files.myeburg.net/work/progressbar_anim/anim_checkbox1_xvid.avi"), [animated sliders]("http://files.myeburg.net/work/progressbar_anim/animated_slider.avi") and [animated progress bars]("http://files.myeburg.net/work/progressbar_anim/progress_anim.avi") (more demos available [here]("http://files.myeburg.net/work/progressbar_anim/")).

Check out his [blog entry]("http://myeburg.net/home/en/notes/show.8.html") to patch it by yourself, or simply download the attached DEB.

Grab the attached zip, extract the .deb file, and *dpkg* it:
```
sudo dpkg -i gtk2-engines-clearlooks_2.6.5-0ubuntu3_i386.deb
```

Package is patched against Ubuntu official package for maximum compatibility.
Works perfect on my machine, but still, in case of bugs, crashes, or pangs of conscience, just roll back to official Ubuntu package.

Enjoy!
[B]
EDIT:
* [/B] latest version available [here]("http://ubuntuforums.org/showthread.php?p=491703#post491703")
* AMD64 available [here]("http://ubuntuforums.org/attachment.php?attachmentid=4320&d=1134140525"). Thanks to [MighMoS]("http://ubuntuforums.org/showpost.php?p=557902&postcount=133") for building it.

---

### Post by domesticatewhat on 2005-11-11
Don't see any file.

---

### Post by Omer on 2005-11-11
[QUOTE=domesticatewhat]Don't see any file.[/QUOTE]

For some reason the file appears as uploaded, but it's not shown.
Here it is...

---

### Post by Logic* on 2005-11-11
Pretty =D> 

Thanks for the deb!

---

### Post by MetalMusicAddict on 2005-11-11
WOW. Really nice. I was downloading the new SymphonyOS beta before I applied the patch. I rebooted than started the download again and saw it right away. The animated progress is really nice. Very cool. ;)

---

### Post by poptones on 2005-11-11
What the hell codec is this? I have the codec pack installed and nothing knows what to do with an "fmp4" file

---

### Post by MetalMusicAddict on 2005-11-11
Which *damn* file are you talking about? Ones linked in the 1st post or from the blog? All I see are .avi's from the 1st post and on the site are .avi's a .wmv and 2 .swf's. [HERE]("http://files.myeburg.net/work/progressbar_anim/") are all his media files.

---

### Post by varunus on 2005-11-11
Will this mess up any clearlooks themes that are installed?  Or does it work with old clearlooks themes?  Is the gtkrc format different?

---

### Post by MetalMusicAddict on 2005-11-11
You should be fine. Im using a Clearlooks "based" theme now and have no problems.

---

### Post by varunus on 2005-11-11
I tried it out, but a few comments.

First of all, it appears that menus are no longer beveled like they used to be.  Also, this does not resemble the current shots that Remenic has on the clearlooks page; the progress bars seem to be the same beige color for the human theme, for example.

Is this on purpose?  perhaps a bug?

---

### Post by monkey89 on 2005-11-11
Last time I tried this, I couldn't open Evolution because it hard-locked my system.

Can someone please try and let me know if it works?

---

### Post by MetalMusicAddict on 2005-11-11
[QUOTE=monkey89]Last time I tried this, I couldn't open Evolution because it hard-locked my system.

Can someone please try and let me know if it works?[/QUOTE]
I dont use Evolution but it launches fine for me with the patch.

---

### Post by stubby on 2005-11-12
Works great for me.

---

### Post by Bairsairk on 2005-11-12
It isn't yet perfect but nice =D>

---

### Post by manicka on 2005-11-12
not bad. Plays havoc with transparency on the main menu and the menu highlight colours changed.

Other than that, it's quite pretty

---

### Post by briguy on 2005-11-12
Are there any other packages I need to install to get this to work?  I selected clearlooks as my controls under Theme, no change.  I think I'm missing something...:confused:

---

### Post by manicka on 2005-11-12
log out and in again

---

### Post by MetalMusicAddict on 2005-11-12
I did also notice the "Apps menu" is drawn different from the panel now.

_Before_:
[img]http://img497.imageshack.us/img497/205/screenshot3la.png[/img]

_After_:
[img]http://img494.imageshack.us/img494/5080/screenshot15hi.png[/img]

You can see a gradient now applied. I like it but I wish it continued on the whole panel.

---

### Post by GameGod on 2005-11-12
Doh!

When I ran epiphany, my computer locked hard... How do I roll back the package to the original Ubuntu one?

Thanks!

(The theme looks nice though... although the scrollbars look ghetto...)

---

### Post by souled on 2005-11-12
What theme do you use to see these new effects? I'm using Clearlooks and I don't see anything different...

---

### Post by bored2k on 2005-11-12
[QUOTE=GameGod]Doh!

When I ran epiphany, my computer locked hard... How do I roll back the package to the original Ubuntu one?

Thanks!

(The theme looks nice though... although the scrollbars look ghetto...)[/QUOTE]
Go to synaptic and downgrade clearlooks.

---

### Post by bored2k on 2005-11-12
[QUOTE=souled]What theme do you use to see these new effects? I'm using Clearlooks and I don't see anything different...[/QUOTE]
Try downloading something in Firefox, you should see a nice animation on clearlooks. Dont forget to restart gnome.

---

### Post by GameGod on 2005-11-12
[QUOTE=bored2k]Go to synaptic and downgrade clearlooks.[/QUOTE]

Thanks!

For the record, that means, fire up synaptic, select the "gtk2-engines-clearlook" package, then click "Package->Force Version...", and select the one that says "(breezy)" at the end of it.

---

### Post by manicka on 2005-11-12
Ignore this...sorry, I'm half asleep and should read the other posts better

---

### Post by stubby on 2005-11-12
[QUOTE=MetalMusicAddict]I did also notice the "Apps menu" is drawn different from the panel now.

You can see a gradient now applied. I like it but I wish it continued on the whole panel.[/QUOTE]

Yeah I noticed that too.

---

### Post by rwabel on 2005-11-13
thanks a lot for the deb file. It's looking nice the progressbar!

---

### Post by mrguytx on 2005-11-13
While a nice little progress bar is pretty, this update did a number of "bad" things to my system.

1. the Apps | Places | System tabs on my gnome bar would quit functioning after a while.

2. system sounds halted completely, no system sounds. (weird huh?)

3. cpu increased by 10% according to gkrellm.


I would recommend waiting on this one unless you're on a true sandbox and not something you depend on using daily.

just my .02

G

---

### Post by SchAmane on 2005-11-13
Hi all,

thanks for comments and amazing ubuntu packaging :) 

Just dont forget to restart gnome after installing this clearlooks, it would safe your application from crash.

Problemm with Different collors in Panel are not related to my patches.

We have realy CPU incrase. I can submit about 5% cpu incrase on 4 progressbars on my Athlon-XP(1.8GHz). But its not realy that match. CPU usage is measured in time, our animation is done every 100ms. So if cairo do animation fast enought it gives cpu free for rest time. Try latest CVS version of cairo, its faster than latest released.

Today we reviewed all patches with actual Clearlooks maintainer Remenic, we add some new features, changed look of progressbar. So if you like it - try.
More about this on my page:
[http://myeburg.net/home/en/notes/show.9.html]("http://myeburg.net/home/en/notes/show.9.html")

---

### Post by MetalMusicAddict on 2005-11-13
Thanx for all the work man. Clearlooks just keeps getting better and better.

How has Remenic taken to your work? Is he supportive?

---

### Post by SchAmane on 2005-11-13
[QUOTE=MetalMusicAddict]How has Remenic taken to your work? Is he supportive?[/QUOTE]

Remenic is great pal. He made some nice changes to my patches... i hope you try new cvs. Dont forget to change gtkrc file =)

---

### Post by super on 2005-11-13
i like it! :D 
and it seems to run bug free for me thus far! (always a good thing)

is there any way to get the menu highlight gradient back (so the menu item that is highlighted looks raised) or do i just wait it out?

---

### Post by manicka on 2005-11-13
Omer, any chance of another deb with the 0.7 patch? :)
I just can't work it out.

---

### Post by tashiro on 2005-11-14
[QUOTE=Omer]Grab the attached zip, extract the .deb file, and *dpkg* it:
```
sudo dpkg -i gtk2-engines-clearlooks_2.6.5-0ubuntu3_i386.deb
```

Package is patched against Ubuntu official package for maximum compatibility.
Works perfect on my machine, but still, in case of bugs, crashes, or pangs of conscience, just roll back to official Ubuntu package.
[/QUOTE]

Thank you for the package, but is it possible to offer also the source package,
so that I can rebuild it for other architectures as well.

Stephan Michels.

---

### Post by Omer on 2005-11-14
**Changlog:**
* Patches are now merged into Clearlooks CVS.
* Dropped sliders animation.
* Animation is now based on *~/.gtkrc* settings.

**Package Changelog:**
* Updated to latest CVS.
* Added to version number **ubuntu-unofficial**, to avoid confusion betweed official package.
* Added source packages, for users on 64bit/PPC.

**Comments:**
By default, Clearlooks uses animated widgets, but if you're using a Clearlooks variation (e.g.: [Clarity]("http://gnome-look.org/content/show.php?content=26624"), [gPerfection]("http://gnome-look.org/content/show.php?content=25407")), you will need to enable animation on your *~/.gtkrc*:
1. *gedit ~/.gtkrc*.
2. Add: ```
 engine "clearlooks"
  {
    animation = TRUE
  }
```
3. Save & restart your sesion.

Credits go as well to [SchAmane]("http://myeburg.net/"), for creating the animation patches, and [Remenic]("http://www.stellingwerff.com/") for maintaining Clearlooks CVS.

---

### Post by manicka on 2005-11-14
I've edited the gtkrc config as suggested, but can't get this version to work with anything other than pure clearlooks.

---

### Post by Omer on 2005-11-14
[QUOTE=manicka]I've edited the gtkrc config as suggested, but can't get this version to work with anything other than pure clearlooks.[/QUOTE]

be sure to add it .gtkrc (don't forget he dot).
If still not working, you can manually add it to gtkrc of a specific theme, just look for *engine "clearlooks"* and add below it *animation = TRUE*.

---

### Post by SchAmane on 2005-11-14
Hi,
i reworked most of code today. Now we can animate every widget we will (what is surely not best idea) :) 
Any way i have fade in/ fade out of checkboxes and radio buttons done today.
You can see it on 2 new videos from my site. [http://myeburg.net]("http://myeburg.net")

---

### Post by manicka on 2005-11-14
[QUOTE=Omer]be sure to add it .gtkrc (don't forget he dot).
If still not working, you can manually add it to gtkrc of a specific theme, just look for *engine "clearlooks"* and add below it *animation = TRUE*.[/QUOTE]
I remembered the dot. Will add to specific theme next.

---

### Post by Omer on 2005-11-14
[QUOTE=SchAmane]Hi,
i reworked most of code today. Now we can animate every widget we will (what is surely not best idea) :) 
Any way i have fade in/ fade out of checkboxes and radio buttons done today.
You can see it on 2 new videos from my site. [http://myeburg.net]("http://myeburg.net")[/QUOTE]

Will work on it tomorrow

---

### Post by manicka on 2005-11-14
[QUOTE=Omer]Will work on it tomorrow[/QUOTE]

okay, added animation = TRUE to specific theme and all is well :)

Also, was there something wrong with the package that appeared briefly? It seems to be working well for me.

---

### Post by SchAmane on 2005-11-14
[QUOTE=Omer]Will work on it tomorrow[/QUOTE]
Dont think so ;o) My code is not in cvs. There is still little bit to do, and i would like if Remenic take a look to my patches first, befor thay goes public.

---

### Post by manicka on 2005-11-14
[QUOTE=SchAmane]Dont think so ;o) My code is not in cvs. There is still little bit to do, and i would like if Remenic take a look to my patches first, befor thay goes public.[/QUOTE]
OK, I like the fade in and out on checkboxes.... very funky :)

---

### Post by MetalMusicAddict on 2005-11-14
Will there be a way to make panels and panel buttons have a different color from the rest of the controls or is that more a GTK thing? 

ie: I want to make the "Apps" menu and the panel its on the same color as the titlebar.

---

### Post by idn on 2005-11-14
This look s great well done, I really like the window list transparency - it never did that before. 

I also like the animations, although they a little slow on my computer (even though I have a 7800gtx + AMD64x2 ?!)

One suggestion/question - is it possible to make the gnome menus the same transparency as the gnome panel. Also, transparency doesnt seem to work for some icons i the panels. 

Ok, one more thing, is it possible to toggle the 3D look of stuff, jsut have it one plain colour? Sometimes I like a really simple theme.

Oh and before I forgot, entry boxes arent highlighted for me when I enter them.

Good work!

---

### Post by manicka on 2005-11-15
[QUOTE=idn]This look s great well done, I really like the window list transparency - it never did that before. 
[/QUOTE]

AFAIK, Clearlooks has always supported transparency on the panel and window list.

---

### Post by manicka on 2005-11-15
I really like the flatter look of the progress bar animations in this latest patch.... sweet :)

---

### Post by Omer on 2005-11-15
[QUOTE=SchAmane]Dont think so ;o) My code is not in cvs. There is still little bit to do, and i would like if Remenic take a look to my patches first, befor thay goes public.[/QUOTE]

Noticed that...

**manicka**: This is why the last package was immediately removed, as it wasn't different that the one posted before.

---

### Post by Technoviking on 2005-11-15
I have noticed that the slider bar will go outside it area on some programs. Try sending mail in Thunderbird.

Mike

---

### Post by SchAmane on 2005-11-15
[QUOTE=Mike Basinger]I have noticed that the slider bar will go outside it area on some programs. Try sending mail in Thunderbird.[/QUOTE]

Yes, thats highly beta code =) This feature is already known :p

---

### Post by Jengu on 2005-11-15
This theme rocks :)

Bugs:
-When I turn transparency for the top panel on, the application/places/system menus completely disappear and the slider only adjust the transparency of the app launchers, systray, etc.

Ideas:
-What about a nice fade to/from brightness when mousing over the minimize/maximize/close buttons?

-I like the new scrollbar, but can't cairo do a cooler effect than just a color change?

-Unselected tabs are still a really ugly dark grey, that looks especially out of place with the new brighter look.

-Can cairo be used to change the minimize effect too? Maybe that's outside what gtk's themeing supports.

---

### Post by Omer on 2005-11-15
[QUOTE=Jengu]This theme rocks :)
-Can cairo be used to change the minimize effect too? Maybe that's outside what gtk's themeing supports.[/QUOTE]

I guess Metacity is responsible for it.
Cairo only draws the widgets.

---

### Post by HanZo on 2005-11-15
just a silly question... this patch does not make clearlooks use any features of glitz does it?

---

### Post by neuschnee on 2005-11-15
This just goes to show: cairo rocks. Thanks for making the .deb. :>

---

### Post by Jengu on 2005-11-15
[QUOTE=HanZo]just a silly question... this patch does not make clearlooks use any features of glitz does it?[/QUOTE]

Sort of. This theme uses cairo for drawing, and cairo can use glitz as a backend I think, but I'm not sure how you go about enabling that, and you probably need CVS of cairo and xorg.

---

### Post by idn on 2005-11-15
What do you think abot having an option for themers to have 3d and flat buttons?

*bumping* this up from my previous pot :)




List headers also look alot better in this release BTW :) 

Also any chance of a repo to get the latest versions?

---

### Post by dude2425 on 2005-11-15
These options don't seem to work anymore:
    menubarstyle          = 2       # 0 = flat, 1 = sunken, 2 = flat gradient
    menuitemstyle         = 1       # 0 = flat, 1 = 3d-ish (gradient), 2 = 3d-ish (button)
    listviewitemstyle     = 1       # 0 = flat, 1 = 3d-ish (gradient)

Without these options everything just seems a little too flat for the moment. I'm sure I'll get used to it, but it just made me stop for a few seconds.

I don't see any animation when unticking a checkbox, and aren't the radio button things supposed to animate as well?

I'm waiting patiently for clearlooks to include a highlighting feature for entry boxes. Right now it's hard to figure out which entry box you have your cursor in if you disabled it from blinking. Also, the old clearlooks had a nice coloured trail on sliders. How would I get that back?

---

### Post by Aero-Z on 2005-11-16
Maybe there's answer here somewhere but how can I get my old Clearlooks back?:confused:

---

### Post by makisupa123 on 2005-11-16
FYI

Using the Cairo enabled Clearlooks will make gnumeric crash upon opening.  At least it did on my machine.  No big deal but It took me a couple minutes to fiure our what was going on.

Aero-Z...the answer is in this thread -- back a couple of pages.  Open synaptic and find the installed clearlooks package.  Then go to 'package' and then 'force version.'  Select the version with the 'breezy' parenthetical after it.  Viola!

Mak.

---

### Post by Aero-Z on 2005-11-16
[QUOTE=makisupa123]FYI

Using the Cairo enabled Clearlooks will make gnumeric crash upon opening.  At least it did on my machine.  No big deal but It took me a couple minutes to fiure our what was going on.

Aero-Z...the answer is in this thread -- back a couple of pages.  Open synaptic and find the installed clearlooks package.  Then go to 'package' and then 'force version.'  Select the version with the 'breezy' parenthetical after it.  Viola!

Mak.[/QUOTE]
Big Thanks:)

---

### Post by SchAmane on 2005-11-16
[QUOTE=makisupa123]Using the Cairo enabled Clearlooks will make gnumeric crash upon opening.  At least it did on my machine.  No big deal but It took me a couple minutes to fiure our what was going on.
[/QUOTE]
Do you have restarted gnome session after changing to clearlooks cairo theme ?

---

### Post by lizardking on 2005-11-17
Some one can post the new version with **animated tab**?
it is wonderflull...[URL="http://files.myeburg.net/work/progressbar_anim/animated_tab_xvid.avi"]
here a screen[/URL]

---

### Post by manicka on 2005-11-17
[QUOTE=Aero-Z]Maybe there's answer here somewhere but how can I get my old Clearlooks back?:confused:[/QUOTE]

In Synaptic, search for clearlooks, then go to Packages-->Force Version and select the breezy version to downgrade.

---

### Post by manicka on 2005-11-17
[QUOTE=lizardking]Some one can post the new version with **animated tab**?
it is wonderflull...[URL="http://files.myeburg.net/work/progressbar_anim/animated_tab_xvid.avi"]
here a screen[/URL][/QUOTE]

Sweet.... can't wait for that one :)

---

### Post by Jengu on 2005-11-17
[QUOTE=manicka]Sweet.... can't wait for that one :)[/QUOTE]

That's awesome! Someone make another deb! :)

---

### Post by MetalMusicAddict on 2005-11-17
[QUOTE=lizardking]Some one can post the new version with **animated tab**?
it is wonderflull...[URL="http://files.myeburg.net/work/progressbar_anim/animated_tab_xvid.avi"]
here a screen[/URL][/QUOTE]
REALLY slick.

---

### Post by SchAmane on 2005-11-17
Here is completely reworked, latest patch.
Its not tested at all. So i would like if somebody try it and say if something goings bad. Please do not report any nonanimation related bugs.
[http://files.myeburg.net/work/progressbar_anim/animated_clearlooks-0.8.2.patch]("http://files.myeburg.net/work/progressbar_anim/animated_clearlooks-0.8.2.patch")
PS. There is no tab animation. And dont think we put tab animation in to clearlooks some day.

---

### Post by lizardking on 2005-11-17
[QUOTE=SchAmane]Here is completely reworked, latest patch.
Its not tested at all. So i would like if somebody try it and say if something goings bad. Please do not report any nonanimation related bugs.
[http://files.myeburg.net/work/progressbar_anim/animated_clearlooks-0.8.2.patch]("http://files.myeburg.net/work/progressbar_anim/animated_clearlooks-0.8.2.patch")
PS. There is no tab animation. And dont think we put tab animation in to clearlooks some day.[/QUOTE]
noooo it was cool!:confused: 
and what are new features of this patch?

---

### Post by MetalMusicAddict on 2005-11-18
[QUOTE=SchAmane]And dont think we put tab animation in to clearlooks some day.[/QUOTE]
Too bad. I really liked the idea. :)

---

### Post by MrRoboto on 2005-11-18
hi all,

where can I find documentation on making Cairo based theme engines and all related topics??

---

### Post by MrRoboto on 2005-11-18
[QUOTE=SchAmane]Here is completely reworked, latest patch.
Its not tested at all. So i would like if somebody try it and say if something goings bad. Please do not report any nonanimation related bugs.
[http://files.myeburg.net/work/progressbar_anim/animated_clearlooks-0.8.2.patch]("http://files.myeburg.net/work/progressbar_anim/animated_clearlooks-0.8.2.patch")
PS. There is no tab animation. And dont think we put tab animation in to clearlooks some day.[/QUOTE]

SchAmane, please could you post your .gtkrc file?
thanks in advance

---

### Post by SchAmane on 2005-11-18
[QUOTE=MrRoboto]SchAmane, please could you post your .gtkrc file?
thanks in advance[/QUOTE]
Take it here: [Clearlooks-SchAmane.tar.bz2]("http://files.myeburg.net/work/progressbar_anim/Clearlooks-SchAmane.tar.bz2")

---

### Post by Jengu on 2005-11-18
[QUOTE=SchAmane]Here is completely reworked, latest patch.
Its not tested at all. So i would like if somebody try it and say if something goings bad. Please do not report any nonanimation related bugs.
[http://files.myeburg.net/work/progressbar_anim/animated_clearlooks-0.8.2.patch]("http://files.myeburg.net/work/progressbar_anim/animated_clearlooks-0.8.2.patch")
PS. There is no tab animation. And dont think we put tab animation in to clearlooks some day.[/QUOTE]

Why not? It's a nice effect. If you don't like it just make it a toggleable option.

---

### Post by manicka on 2005-11-18
Can anyone give me a leg up on just compiling the clearlooks engine from the gtk-engines cvs and not all the others.

---

### Post by plueken on 2005-11-18
For those who like the newer updates so far, but prefer the original Clearlooks look over the lighter Deepsky variation, I modified the /usr/share/themes/Clearlooks/gtk-2.0/gtkrc file slightly and created a version that combined the new animation effects with the original darker color.

It's just a hack job, so it may not be perfect, but I do think it looks much nicer, as of right now.

- Plueken

---

### Post by manicka on 2005-11-18
[QUOTE=manicka]Can anyone give me a leg up on just compiling the clearlooks engine from the gtk-engines cvs and not all the others.[/QUOTE]
I'm assuming that at the 'make install' stage I can add an extra argument to just install the clearlooks engine.... any thoughts?

---

### Post by HanZo on 2005-11-18
this may be another stupid question...but I'll ask It anyway...
does the deb install a theme I can select in the theme manager or just patch the gtk engine? because the funny thing is I can see the animated progress bar but it is not flat (looks like the old one just animated). a part from that nothing is moving.

---

### Post by stubby on 2005-11-18
[QUOTE=HanZo]because the funny thing is I can see the animated progress bar but it is not flat (looks like the old one just animated). a part from that nothing is moving.[/QUOTE]

You need to select a theme that is based on clearlooks to be able to see the animation

---

### Post by MrRoboto on 2005-11-19
[QUOTE=SchAmane]Take it here: [Clearlooks-SchAmane.tar.bz2]("http://files.myeburg.net/work/progressbar_anim/Clearlooks-SchAmane.tar.bz2")[/QUOTE]


thanks a lot ! :)

---

### Post by Omer on 2005-11-19
[QUOTE=manicka]I'm assuming that at the 'make install' stage I can add an extra argument to just install the clearlooks engine.... any thoughts?[/QUOTE]

run *./configure --help*, and look for switches like --without-<engine> or --disable-<engine>.

---

### Post by manicka on 2005-11-19
[QUOTE=Omer]run *./configure --help*, and look for switches like --without-<engine> or --disable-<engine>.[/QUOTE]
thanks :)

---

### Post by lizardking on 2005-11-19
where are clearlooks cvs?

---

### Post by manicka on 2005-11-19
[QUOTE=lizardking]where are clearlooks cvs?[/QUOTE]

[http://real.wilbury.sk/~drom/patch/](http://real.wilbury.sk/~drom/patch/)

---

### Post by HanZo on 2005-11-19
[QUOTE=stubby]You need to select a theme that is based on clearlooks to be able to see the animation[/QUOTE]
okie... so it is as I assumed. tnx!

---

### Post by gheorghe_pop on 2005-11-19
hello.
So is ther a fix for the difference betwen the menuapplet and the rest of the pannel. I tryed every thing.The last thing i tryed was to put a bg. image for the pannel similar with the menu. I also tryed transparent pannels. Here are the result::)

---

### Post by dude2425 on 2005-11-19
[quote=SchAmane]Here is completely reworked, latest patch.
Its not tested at all. So i would like if somebody try it and say if something goings bad. Please do not report any nonanimation related bugs.
[http://files.myeburg.net/work/progressbar_anim/animated_clearlooks-0.8.2.patch]("http://files.myeburg.net/work/progressbar_anim/animated_clearlooks-0.8.2.patch")
PS. There is no tab animation. And dont think we put tab animation in to clearlooks some day.[/quote]

If no tab animations, then why even have a teaser video? It looked like a somewhat fun idea, but having an option to turn it off would be great, as it is likely to get annoying fast. Turn it on to show off Linux to friends, turn it off to get things done. Also, how hard would it be to implement a focus-ring to highlight currently selected Text Entry widgets? And Combo Box Entry widgets? I think I remember it being talked about once before, but I can't seem to remember anything about it, and if it actually hapened at all. And whatever happened to the colored trail in the Scale widgets from the old Clearlooks? And how difficult would it be to implement a texturing feature for the scroll bars along side the color efect? And maybe a tip radius or something?

Somebody's got to setup a user-ideas/requests for Clearlooks to help inspire developers and give them new ideas. It could work for any project, not just Clearlooks. Just one central database of nothing but user submitted, and rated ideas, that a developer can choose to implement or ignore, and other developers can try their hand at a patch that could be pushed upstream.

*Sits back and marvels at ideas.

I always have the best ideas when I'm half asleap. Maybe I should start sleaping with a pen and notebook. Maybe I have even better ideas while I'm fully asleap.

---

### Post by manicka on 2005-11-20
Has anyone had any luck applying and building clearlooks with the latest patch? 
So far I've lucked out, with the deb I produced having no animations or colours at all..... hehe

---

### Post by dude2425 on 2005-11-20
I got it working just fine. Just grab clearlooks from gnome's cvs, patch, and compile. I really wish I knew how to make .deb files though. I never really could get that all figured out.

---

### Post by Omer on 2005-11-20
Checked out CVS today, and here are your fresh baked DEBs!
Enjoy!

EDIT: deb removed due to a buggy release, will post the new one later.

---

### Post by manicka on 2005-11-20
Thanks Omer :)

---

### Post by SchAmane on 2005-11-20
Hi all,

i droped some lines on my webpage. [chech this out]("http://myeburg.net/home/notes/show.10.html").

to dude2425:
Actualy CVS do have "focus-ring to highlight currently selected Text Entry widgets", so check this out.

to Omer,
latest patch was very buggy and cause some application crash on showing menu. Please remove this deb and do new one if its possible with cvs and this [patch]("http://files.myeburg.net/work/progressbar_anim/animated_clearlooks-0.8.4.patch").

---

### Post by Omer on 2005-11-20
Will do so ASAP.
Although it works flawlesslly on my machine.

---

### Post by Omer on 2005-11-20
New version, patched against 0.8.4.

---

### Post by manicka on 2005-11-20
Thanks  again :)

---

### Post by lizardking on 2005-11-20
when there will be a new .deb?

---

### Post by rwabel on 2005-11-20
[quote=lizardking]when there will be a new .deb?[/quote]
he has just made a new one 1 hour ago :-)

---

### Post by dude2425 on 2005-11-20
I have the CVS from yesterday (I think. It might be the day before, but I'm pretty sure it was yesterday.) and I don't see any focus rings. Can somebody take a screenie of it if it's there? I might have missed it. I'll have to recompile from CVS again anyway. I'll recompile them later and see if I can't get a text entry focus ring thing working. I'm off to try the new clearlooks. Wish me luck.

Alright, viewing the other Cairo themes with The Widget Factory, I seem to see the focus ring, but for some reason it's not showing up on the theme I use ATM. I'm using a slightly modified "Clearlooks-GNOME" from the Big Pack. It's modified because there was a few problems by default. I'll upload it here, because I have no idea why the focus ring isn't showing. I'm also not getting the trailing thing from sliders like the others I see in TWF. Please, if somebody get's it to work, tell me. I love this theme and I wouldn't want to choose something else. I've already shaped my entire computers color scheme around it.

---

### Post by lizardking on 2005-11-21
[QUOTE=rwabel]he has just made a new one 1 hour ago :-)[/QUOTE]
where I can find this 1 hour ago post?:(

---

### Post by manicka on 2005-11-21
[QUOTE=lizardking]where I can find this 1 hour ago post?:([/QUOTE]
Post 92

---

### Post by lizardking on 2005-11-21
[QUOTE=manicka]Post 92[/QUOTE]
Thank you very much I though they was C source not deb.Damn!;)

---

### Post by Paulus on 2005-11-21
comedy!

woo my ubuntu cd's arrived today (here in U.K).

[COLOR=YellowGreen]On topic:[COLOR=Black] Anyone have an idea to get the nice gradient's onto the rest of the gnome panel? Is there a clearlooks config, perhaps this varies from theme to theme?[/COLOR][/COLOR]

---

### Post by lizardking on 2005-11-21
[QUOTE=manicka]Post 92[/QUOTE]
But in the new deb there is not any animation (
how I do to apply them?

---

### Post by manicka on 2005-11-21
Working just fine for me. I installed the smaller deb with just the clearlooks engine.

---

### Post by lizardking on 2005-11-21
[QUOTE=manicka]Working just fine for me. I installed the smaller deb with just the clearlooks engine.[/QUOTE]
Sorry I did not reset X server..:( now works :KS 
Where I can find standard original clearlooks color for cairo theme?

---

### Post by Jengu on 2005-11-21
The new one omer posted just seems to revert me back to the original non-cairo non-animation grey-scrollbars Clearlooks theme. When I install the .deb dpkg also warns me that I'm downgrading. I reinstalled the .deb from earlier in the thread. Am I doing something wrong?

My .gtkrc:
```

 engine "clearlooks"
  {
    animation = TRUE
  }

```

---

### Post by lizardking on 2005-11-21
[QUOTE=Jengu]The new one omer posted just seems to revert me back to the original non-cairo non-animation grey-scrollbars Clearlooks theme. When I install the .deb dpkg also warns me that I'm downgrading. I reinstalled the .deb from earlier in the thread. Am I doing something wrong?
[/QUOTE]
You should get like me the Clearlooks-default-cairo theme..
but I don't know where is? someone knows?:confused:

---

### Post by manicka on 2005-11-22
[QUOTE=lizardking]You should get like me the Clearlooks-default-cairo theme..
but I don't know where is? someone knows?:confused:[/QUOTE]

Post 92 of this thread

Download the first tarball, extract it

Within that directory, Install the deb with

sudu dpkg -i *.deb

restart your gnome session (log out and in again)

---

### Post by Logic* on 2005-11-22
I'm using XFCE (xubuntu if you will) and the first deb that was posted worked for me - I got animated progress bars, fading checkboxes, etc.

However these latest debs aren't working. I probably need some other package, or something. Oh well, loving it anyway.

---

### Post by varunus on 2005-11-22
Actually, they just changed the way animation works.

For a theme to have animation, in the newest deb, you need to add the line "animation = TRUE" to the gtkrc file.  Make the engine section look like this:

```
engine "clearlooks"
{
   animation = TRUE
   ....
   ....
}
```

This will reenable animations.

---

### Post by besada on 2005-11-22
It breaks the opening of documents in openoffice for me. (using Human theme)

Otherwise, great improvement.

This problem did not apear in the deb at post 34, but it is aparent with the deb at post 92.

---

### Post by adam.tropics on 2005-11-22
Forgive me for not having read the 'entire' thread if this has come up before.
Sometimes when things go wrong, it's just well.....funny.
Installed the animations. All good. Went to send an email to a friend with a link for them. Now using thunderbird, press send, up pops the box, and the beautiful animations animated themselves all the way off the progress bar limit!! They just kept going about an inch further.!
You see, the developers round here really do go the extra well, inch in the name of progress!

I think i'll keep it though, I like the quirkiness!

---

### Post by varunus on 2005-11-22
[QUOTE=adam.tropics]Forgive me for not having read the 'entire' thread if this has come up before.
Sometimes when things go wrong, it's just well.....funny.
Installed the animations. All good. Went to send an email to a friend with a link for them. Now using thunderbird, press send, up pops the box, and the beautiful animations animated themselves all the way off the progress bar limit!! They just kept going about an inch further.!
You see, the developers round here really do go the extra well, inch in the name of progress!

I think i'll keep it though, I like the quirkiness![/QUOTE]

adam,

You're seeing a symptom of CVS software.  The animation code is very bleeding edge; be happy you can have your cool desktop effects now as a preview instead of just having to wait until 2006 for Windows Vista.  :)  Ah, open source...Seeing these themes makes me want to learn Cairo and theme engine programming just to make a very bling theme engine.

Also, I'm using patch 0.8.2; Evolution crashes every time I go to the calendar pane.  Is this fixed in the latest deb from this thread?  Can someone open up Evo and go to their calendar section?  If you can use it, then I'm upgrading...

---

### Post by Omer on 2005-11-22
[QUOTE=varunus]
Also, I'm using patch 0.8.2; Evolution crashes every time I go to the calendar pane.  Is this fixed in the latest deb from this thread?  Can someone open up Evo and go to their calendar section?  If you can use it, then I'm upgrading...[/QUOTE]

0.8.4 still crashed Evo.

---

### Post by SchAmane on 2005-11-23
[QUOTE=Omer]0.8.4 still crashed Evo.[/QUOTE]
Are you sure thats Clearlooks problem ? What backtrace says ? Any output on console ?
I cant reproduce problem with actual CVS version where 0.8.5 patch is already included.

PS. to allow animation in actual CVS, please remove comments slashes in clearlooks_style.c for ```
#define HAVE_ANIMATION 1
```

---

### Post by dude2425 on 2005-11-23
Wait. There's an 0.8.5? Is it just in CVS now or do you still put it in your website's files section? Or is that a typo? If I got CVS Clearlooks now whould I be getting a newer patch version than what is on your site?

---

### Post by MrRoboto on 2005-11-23
[QUOTE=SchAmane]Are you sure thats Clearlooks problem ? What backtrace says ? Any output on console ?
I cant reproduce problem with actual CVS version where 0.8.5 patch is already included.

PS. to allow animation in actual CVS, please remove comments slashes in clearlooks_style.c for ```
#define HAVE_ANIMATION 1
```[/QUOTE]

where can I find patch 0.8.5?

---

### Post by Omer on 2005-11-23
[QUOTE=SchAmane]Are you sure thats Clearlooks problem ? What backtrace says ? Any output on console ?
I cant reproduce problem with actual CVS version where 0.8.5 patch is already included.
[/QUOTE]

No output on console. Just tried it with Industrial and it seems to be working.
I will  build CVS today, and see if it's still crashes evo.
If it does, how can i provide you the relevant debug information?

---

### Post by SchAmane on 2005-11-23
[QUOTE=varunus]Seeing these themes makes me want to learn Cairo and theme engine programming just to make a very bling theme engine.[/QUOTE]

I wrote little how to about how Clearlooks animation works. And there is good Cairo docu on Freedesktop. So check this out, and make new cool and full featured engines !
[http://myeburg.net/home/en/notes/show.11.html]("http://myeburg.net/home/en/notes/show.11.html")

---

### Post by SchAmane on 2005-11-23
[QUOTE=Omer]No output on console. Just tried it with Industrial and it seems to be working.
I will  build CVS today, and see if it's still crashes evo.
If it does, how can i provide you the relevant debug information?[/QUOTE]
There are some docu about debuging Evolution on evolution web page. You can try gdb evolution.

---

### Post by Omer on 2005-11-23
Just checked out today's CVS, and Evo seems to work fine.

The new deb/src are attached.

---

### Post by SchAmane on 2005-11-23
[QUOTE=MrRoboto]where can I find patch 0.8.5?[/QUOTE]
There is no need in any patch now if you use today CVS.

---

### Post by manicka on 2005-11-23
[QUOTE=Omer]Just checked out today's CVS, and Evo seems to work fine.

The new deb/src are attached.[/QUOTE]

thanks Omer, the evo crash was a show stopper for me. 

Enjoying animation again

---

### Post by SchAmane on 2005-11-23
Good work Omer, if you will do something realy good else, you should release some cairo-cvs deb package with glitz-cvs support :o)
Lastes cvs fix some very bad memory leaks and is a lot faster than latest release. :D

---

### Post by Omer on 2005-11-24
[QUOTE=SchAmane]Good work Omer, if you will do something realy good else, you should release some cairo-cvs deb package with glitz-cvs support :o)
Lastes cvs fix some very bad memory leaks and is a lot faster than latest release. :D[/QUOTE]

I think i'll wait till it hits Dapper, than i can backport it.

---

### Post by SchAmane on 2005-11-26
Please read this, and VOTE for you choice !
[http://www.stellingwerff.com/?p=14]("http://www.stellingwerff.com/?p=14")

---

### Post by lucas on 2005-11-26
I liked the old colors better, so I reinstalled the old package again.

---

### Post by kairu0 on 2005-12-04
Forgive me for not knowing the technicalities of this, but how portable are these Cairo animated-widgets to non Clearlooks themes?

---

### Post by poofyhairguy on 2005-12-04
[QUOTE=SchAmane]Please read this, and VOTE for you choice !
[http://www.stellingwerff.com/?p=14]("http://www.stellingwerff.com/?p=14")[/QUOTE]


Left to right. Thats easy- that way it looks like the bar is moving forwards.

---

### Post by Antioch on 2005-12-04
[QUOTE=lucas]I liked the old colors better, so I reinstalled the old package again.[/QUOTE]

I agree, I tried the original post of the updated clearlooks, but I didn't like the newer shade of blue my theme changes to - too bright. Is there any way to keep it the way it is now, or somehow manually edit it?

---

### Post by manicka on 2005-12-05
[QUOTE=Antioch]I agree, I tried the original post of the updated clearlooks, but I didn't like the newer shade of blue my theme changes to - too bright. Is there any way to keep it the way it is now, or somehow manually edit it?[/QUOTE]

try the version at post #119

---

### Post by meepy on 2005-12-06
First of all, thanks for this amazing distro - You converted me from Windows to Linux. -- And hi! ;) 

Okay. I got a few problems here, I am probably during something wrong since I am new to Linux. And Ubuntu.

Problem is that it just don't change the interface of the Clearlooks design at all? I tried rebooting with no luck.

According to "About Gnome" I have version 2.12.1 of Gnome. So that should be alright. 

Here is what I did. I downloaded the *.zip package from the second link (The edit link in the first post of this thread) I extract zip, so I get a *.deb package on my desktop. I open the terminal, browse to the desktop, and do;

```

sudo dpkg -i <name of package>

```

The 'install' runs and succede with no errors. Then according to the 'guide' I should be doing;

```
gedit ~/.gtkrc
```

This (for me) opens a blank file. I think that's not the point, so what am I during wrong? Anyway, I paste;

```

 engine "clearlooks"
  {
    animation = TRUE
  }
```

To the emtpy file, and saving it. And then again, according to the guide I should save my session and reload it. I don't know how to do that yet (hehe), so I just reboot my system. 

Now that my system is rebooting, I go into the Theme application and see that the Clearlook theme, **HAVEN'T** changed at all. It look exactly like it did before? Now how can this be? What am I doing wrong? :???: 

An explained guide would be very appriciated. 

Thanks in advance. 
Looking forward to browse theese forums more.

Regards,
*meep*
yessir.

---

### Post by meepy on 2005-12-06
First of all, thanks for this amazing distro - You converted me from Windows to Linux. -- And hi! ;) 

Okay. I got a few problems here, I am probably during something wrong since I am new to Linux. And Ubuntu.

Problem is that it just don't change the interface of the Clearlooks design at all? I tried rebooting with no luck.

According to "About Gnome" I have version 2.12.1 of Gnome. So that should be alright. 

Here is what I did. I downloaded the *.zip package from the second link (The edit link in the first post of this thread) I extract zip, so I get a *.deb package on my desktop. I open the terminal, browse to the desktop, and do;

```

sudo dpkg -i <name of package>

```

The 'install' runs and succede with no errors. Then according to the 'guide' I should be doing;

```
gedit ~/.gtkrc
```

This (for me) opens a blank file. I think that's not the point, so what am I during wrong? Anyway, I paste;

```

 engine "clearlooks"
  {
    animation = TRUE
  }
```

To the emtpy file, and saving it. And then again, according to the guide I should save my session and reload it. I don't know how to do that yet (hehe), so I just reboot my system. 

Now that my system is rebooting, I go into the Theme application and see that the Clearlook theme, **HAVEN'T** changed at all. It look exactly like it did before? Now how can this be? What am I doing wrong? :???: 

An explained guide would be very appriciated. 

Thanks in advance. 
Looking forward to browse theese forums more.

Regards,
*meep*
yessir.

---

### Post by manicka on 2005-12-06
[QUOTE=meepy]
The 'install' runs and succede with no errors. Then according to the 'guide' I should be doing;

```
gedit ~/.gtkrc
```

[/QUOTE]

Post 108 in this thread explains what you need to do. With these later debs you need to add the 'animation =true' part to the gtkrc of the theme rather than the users config file.

---

### Post by MighMoS on 2005-12-09
[QUOTE=manicka]Post 108 in this thread explains what you need to do. With these later debs you need to add the 'animation =true' part to the gtkrc of the theme rather than the users config file.[/QUOTE]

It took me a while to figure this out, so perhaps the first post should be revised and made current.  Also, for the people who don't run i386 but amd64, I've got a deb for you.

---

### Post by Kevin on 2005-12-09
This new clearlooks makes almost every program hard-lock my system.  I suspect it's from having renderaccel in the nvidia drivers turned on, but I haven't tried without.  The only programs that don't lock up are simple programs like the terminal and nautilus.  Synaptic, Rhythmbox, everything locks up.
Any ideas? I had to rollback using aptitude...

Edit: Ok I solved that problem, well actually nvidia did...
The brand new 1.0-8174 nvidia drivers work beautifully with this *and* RenderAccel, and as an added bonus xcompmgr is rock solid so far, whereas before it hardlocked in about 10 seconds...

---

### Post by MighMoS on 2005-12-13
A new GTK-Themes has been released, with bug fixes for cairo+clearlooks.  An AMD64 package is provided below, as well as a source package.

---

### Post by Jengu on 2005-12-14
[QUOTE=MighMoS]A new GTK-Themes has been released, with bug fixes for cairo+clearlooks.  An AMD64 package is provided below, as well as a source package.[/QUOTE]

Any chance of a deb for us 32-bit users?

Are you just making the debs with checkinstall? Because if it's that simple I can make them and post them.

---

### Post by MighMoS on 2005-12-14
[QUOTE=Jengu]Any chance of a deb for us 32-bit users?

Are you just making the debs with checkinstall? Because if it's that simple I can make them and post them.[/QUOTE]
Sure, just for you, Jengu.  And I'm using dpkg-buildpackage.  The i386 binary is in this post, with the source in my previous (wouldn't want to violate the GPL, now).

---

### Post by Jengu on 2005-12-16
[QUOTE=MighMoS]Sure, just for you, Jengu.  And I'm using dpkg-buildpackage.  The i386 binary is in this post, with the source in my previous (wouldn't want to violate the GPL, now).[/QUOTE]

Thanks, works great =)

---

### Post by tmilovan on 2005-12-18
Hi, 

The last .deb on my ubuntu 5.10 works great except that the menubar is always gradient, and menuitems are flat no matter what I specify in my themes or even in ~/.gtkrc 

So, basicaly my GTK themes (T-ish, T-ish brushed) wont dislplay correctly in this last version.

Any hints? I'll be gratefull.

Thanks.

---

### Post by varunus on 2005-12-18
Right now, the devs are focusing more on adding features; they'll work on the configuration later.  (Its pretty much a complete rewrite, so your themes won't work with the CVS clearlooks for now.  Sorry.)

---

### Post by tmilovan on 2005-12-18
[QUOTE=varunus]Right now, the devs are focusing more on adding features; they'll work on the configuration later.  (Its pretty much a complete rewrite, so your themes won't work with the CVS clearlooks for now.  Sorry.)[/QUOTE]

Oh, ok I can live with that. I'd like to keep my themes fully functional so I was little worried when menubar shade "ate" my brushes :))

Btw, is it me imagining things, or is the new clearlooks even faster then the stable version?  

Thanks,

---

### Post by poofyhairguy on 2005-12-19
[QUOTE=MighMoS]A new GTK-Themes has been released, with bug fixes for cairo+clearlooks.  An AMD64 package is provided below, as well as a source package.[/QUOTE]

Thanks for the AMD64 package. I might just stick with this theme!

---

### Post by Jengu on 2005-12-21
Dumb question: How do I install it?

There's only a .xml file inside, and dragging it or the .tar.gz into the theme preferences window just gives the error: "The file format is invalid." Pointing it at the extracted folder doesn't work either.

locate metacity*xml turns up nothing so I don't know what I'm supposed to overwrite.

---

### Post by manicka on 2005-12-21
[QUOTE=Jengu]Dumb question: How do I install it?

There's only a .xml file inside, and dragging it or the .tar.gz into the theme preferences window just gives the error: "The file format is invalid." Pointing it at the extracted folder doesn't work either.

locate metacity*xml turns up nothing so I don't know what I'm supposed to overwrite.[/QUOTE]

Downlaod the tar.gz file in post #137

Extract that file and you will see a deb file. (gtk2-engines-clearlooks_2.7.1-0ubuntu-unofficial0_i386.deb)

In a terminal change to where the deb file is and then run

```
sudo dpkg -i gtk2-engines-clearlooks_2.7.1-0ubuntu-unofficial0_i386.deb
```

---

### Post by fabs0028 on 2005-12-23
Hello
well i'm on an amd64 breezy and i waited for a good gtk theme before switching to the new engine and today i found this one :

[Cairo-graphite]("http://gnome-look.org/content/show.php?content=32862")
and with the new clearlooks metacity it looks pretty amazing !!!

Thanx a lot for the deb file :)
I 'll try to enable animation in the gtkrc but anyway it looks wonderful !

---

### Post by varunus on 2005-12-25
Does anyone else get some random crashes and application closings when using clearlooks cairo cvs?  Namely in the GIMP and gedit when attempting to close indivdual tabs/windows (I don't get these when using any other theme engine like pixmap or industrial.)

---

### Post by MighMoS on 2005-12-25
[QUOTE=varunus]Does anyone else get some random crashes and application closings when using clearlooks cairo cvs?  Namely in the GIMP and gedit when attempting to close indivdual tabs/windows (I don't get these when using any other theme engine like pixmap or industrial.)[/QUOTE]

Apparently, some over aggressive cleanups were applied.  That's why I just monitor the Changelogs for something I'd need, and *then* update.

---

### Post by Jengu on 2005-12-25
[QUOTE=manicka]Downlaod the tar.gz file in post #137

Extract that file and you will see a deb file. (gtk2-engines-clearlooks_2.7.1-0ubuntu-unofficial0_i386.deb)

In a terminal change to where the deb file is and then run

```
sudo dpkg -i gtk2-engines-clearlooks_2.7.1-0ubuntu-unofficial0_i386.deb
```[/QUOTE]

Whoops, accidentally replied to the wrong thread! I meant how to install the new metacity theme from the other thread. But I figured it out anyway :P

Thanks.

---

### Post by tmilovan on 2005-12-28
[QUOTE=fabs0028]Hello
well i'm on an amd64 breezy and i waited for a good gtk theme before switching to the new engine and today i found this one :
[/QUOTE]

You can try this one too: [http://www.gnomelook.org/content/show.php?content=30859](http://www.gnomelook.org/content/show.php?content=30859)

---

### Post by kairu0 on 2006-01-27
[QUOTE=varunus]Does anyone else get some random crashes and application closings when using clearlooks cairo cvs?  Namely in the GIMP and gedit when attempting to close indivdual tabs/windows (I don't get these when using any other theme engine like pixmap or industrial.)[/QUOTE]

I couldn't launch Gnumeric with the new Clearlooks CVS. I ended up going back to the official breezy release.

---

### Post by MighMoS on 2006-01-28
Just for those who don't like CVS, or don't want to compile, I've updated my .deb files for breezy to 2.7.3.  Available at [http://mighmos.org](http://mighmos.org) (source is also there), and the deb files have been attached.

---

### Post by fabs0028 on 2006-01-29
Thanx a lot for this new version ... i also went to your site to take latest rhythmbox :)

I just had a question though : what do you use to build those packages ... when i need some i use checkinstall but it seems you 're using another way to do it.

Thanx for everything once again !!

PS : just to say that to install rhythmbox i had to cp the rhythmbox.schemas from /usr/share/gconf/schemas to /etc/gconf/schemas and it installed fine.

---

### Post by fabs0028 on 2006-01-29
Well i just wanted to know it there was a way to make openoffice fit with the new clearlooks, i'll explain myself :

I 'm running an amd64 version of ubuntu and OOo uses a 32bits compatibility layer so when i use a theme made for clearlooks-cairo, OOo uses the default gtk theme because the compatibilty gtk layer is not made for  clearlooks-cairo.

An idea would be greatly appreciated :)

---

### Post by MighMoS on 2006-01-29
[QUOTE=fabs0028]I just had a question though : what do you use to build those packages ... when i need some i use checkinstall but it seems you 're using another way to do it.

PS : just to say that to install rhythmbox i had to cp the rhythmbox.schemas from /usr/share/gconf/schemas to /etc/gconf/schemas and it installed fine.[/QUOTE]

[quote=fabs0028]I 'm running an amd64 version of ubuntu and OOo uses a 32bits compatibility layer so when i use a theme made for clearlooks-cairo, OOo uses the default gtk theme because the compatibilty gtk layer is not made for clearlooks-cairo.[/quote]

I'll take a look at the rhythmbox schemas thing, and I'm honestly not sure about OOo.  I've always prefered GNOME Office, and I thought (I could be completely wrong) that OOo used some kind of weird compatability thing similar to what Firefox does.  Or maybe that doesn't happen anymore.

I use dpkg-buildpackage to create my deb files.  I believe its what the official maintainers do, so when I need to steal something, it makes my life easier.

---

### Post by fabs0028 on 2006-01-29
[QUOTE=MighMoS]I'll take a look at the rhythmbox schemas thing
[/QUOTE]
Okay but it is not a big problem at all though. On another thing concerning rhythmbox i found out that when it is launched, gam_server is always running taking between 6 and 10% of the cpu ... but rhythmbox is a beta so it must be the reason, where should i report it? On the gnome bugzilla i think, don't you?

[QUOTE=MighMoS]
I'm honestly not sure about OOo.  I've always prefered GNOME Office, and I thought (I could be completely wrong) that OOo used some kind of weird compatability thing similar to what Firefox does.  Or maybe that doesn't happen anymore.
[/QUOTE] 
Don't loose your time with it, it's not really a problem, for now OOo is not all right for amd64, i'll do with it, it still works anyway.

[QUOTE=MighMoS]
I use dpkg-buildpackage to create my deb files.  I believe its what the official maintainers do, so when I need to steal something, it makes my life easier.[/QUOTE]
OK thanx a lot i'll take a look at it to see how it works when i'll need to compile something.

---

### Post by MighMoS on 2006-01-31
fabs0028, I've fixed the Rhythmbox issue, but this thread is mainly for clearlooks.  Don't feel bad, I've sabotaged threads before, too.  Speaking of clearlooks, today a new version was released.  This is special, because crux has started rendering part of itself with Cairo as well, so I've attached those debs, if anyone wants those as well.  As always, you can pull the source from my website: [http://mighmos.org](http://mighmos.org) .

Also, for anyone who tries to compile this on their own, animation is now disabled by default, but I've re-enabled it in all my debs, as well as my deb source package, so nothing to worry about.

---

### Post by jcooper on 2006-01-31
I've just installed the deb from mighmos (great little site there - v useful!).

Its so nice having animation in ClearLooks again. The checkboxes/radios animate a little slowly but I don't care. Eye candy central :D

Now, how to get the "old" scrollbars back...

---

### Post by MighMoS on 2006-02-01
[QUOTE=jcooper]I've just installed the deb from mighmos (great little site there - v useful!).

Its so nice having animation in ClearLooks again. The checkboxes/radios animate a little slowly but I don't care. Eye candy central :D

Now, how to get the "old" scrollbars back...[/QUOTE]
old scrollbars?

---

### Post by Virtual DarKness on 2006-02-02
Hi MighMoS,
thanks for your debs..

Just a question: I've installed version 2.7.4 but I get no animations..
It is strange cause you say you enabled them and I was able to see them with previous version; also I didn't changed any config file.. :-k :confused: 

any idea? thanks.

bye,
Giovanni.

---

### Post by stalefries on 2006-02-03
For some reason, I changed the gtkrc file so animation = TRUE, but when I logged out and logged back in to refresh everythin so that it would work, my theme defaulted back to Human, making everything brown and not so shiny and blue. :( Can anyone help? I tried reinstalling the .deb, but that only changed the gtkrc back to false.

Also, could we get a .tar.gz like what would be found at gnome-look.org or art.gnome.org?

---

### Post by kevcart3 on 2006-02-04
Thanks a lot MighMoS for compiling/uploading these .debs, saves me lots of trouble, keep up the good work! :D

---

### Post by Havoc on 2006-02-04
[QUOTE=stalefries]Also, could we get a .tar.gz like what would be found at gnome-look.org or art.gnome.org?[/QUOTE]

Mighmos has packaged the clearlooks *engine*, not a clearlooks *theme*.

Themes come in tar.gz.Engines (mostly) come in binary packages.

---

### Post by stalefries on 2006-02-04
Oh. Ok. Well, for some reason it still dissapears from the engine selection menu whenever I try to slect it. Weird.

---

### Post by stalefries on 2006-02-04
Oh! Fixed it! I selected Clearlooks in the main theme selection window, and then told it to use Tango icons, and ta-da!

---

### Post by Virtual DarKness on 2006-02-04
stalefries: do you have a folder called clearlooks into your ~/.themes folder? That could be the cause..

bye,
Giovanni.

---

### Post by Virtual DarKness on 2006-02-04
[QUOTE=Virtual DarKness]Hi MighMoS,
thanks for your debs..

Just a question: I've installed version 2.7.4 but I get no animations..[/QUOTE]

Ok, fixed setting animation = TRUE into /usr/share/themes/Clearlooks/gtk-2.0/gtkrc as suggested in previous topic messages.

bye,
Giovanni.

---

### Post by stalefries on 2006-02-05
[quote=Virtual DarKness]stalefries: do you have a folder called clearlooks into your ~/.themes folder? That could be the cause..

bye,
Giovanni.[/quote]

Yes. I fixed it though. I set my overall theme to Clearlooks, instead of the custom one I had made, and then fixed the icons. All better!

---

### Post by alvinblank on 2006-02-10
I install MighMoS deb and set animation = TRUE, but i still don't see any changes. Is the theme in Breezy already cairo-ed or do I need to find a cairo-ed theme to see the effect?

---

### Post by jamesford on 2006-02-10
i didnt read all 17 pages so apologies if its been covered already but the latest cairo clearlooks (2.7.4) from MighMoS keeps crashing my programs if i use the checkbuttons. for example in gedit > edit > preferences > checking/unchecking either of the boxes. this happens with any cairo enabled clearlooks gtk2 theme.

i know its beta or thereabouts so no complaints, just wondering if this only happes on my machine really, or if its a known problem, and if so is a fix expected ?

---

### Post by ade234uk on 2006-02-17
May be its my set up but after installing clearlooks Gnome periodically locks my whole machine up on the following programs and actions:-

Firefox - when I open a page or click the back button

Synaptic Package Manager - Cannot view any packages. Blank workspace and then locks up. Trouble is I cannot go back and reinstall a previous version of Clearlooks.

Drag and Dropping files from folders sometimes locks the machine up

I will probably reinstall Ubuntu again and give it another go becuase this clearlooks theme is really nice, and becuase I have seen it in action I dont think Ubuntu will be the same without it.

I hope someone can help.

---

### Post by MighMoS on 2006-02-18
[QUOTE=ade234uk]May be its my set up but after installing clearlooks Gnome periodically locks my whole machine up on the following programs and actions:-

Firefox - when I open a page or click the back button

Synaptic Package Manager - Cannot view any packages. Blank workspace and then locks up. Trouble is I cannot go back and reinstall a previous version of Clearlooks.

Drag and Dropping files from folders sometimes locks the machine up

I will probably reinstall Ubuntu again and give it another go becuase this clearlooks theme is really nice, and becuase I have seen it in action I dont think Ubuntu will be the same without it.

I hope someone can help.[/QUOTE]
I don't exactly know what the problem there is, but I do know that in CVS there's been a (theoretical) massive stability bump.  But to revert, just open a terminal and type "sudo apt-get remove gtk2-engines-clearlooks" which should remove the custom deb, and then "sudo apt-get install gtk2-engines-clearlooks" which should fetch the stable from the mirrors.

---

### Post by manicka on 2006-02-18
[QUOTE=MighMoS]I don't exactly know what the problem there is, but I do know that in CVS there's been a (theoretical) massive stability bump.  [/QUOTE]
Yes , cairo enabled clearlooks has been taken out of Dapper for that very reason. Just remove and reinstall the default clearlooks as suggested and things should go back to normal. I to was having similar problems to the ones described by ade234uk, but not quite as severe.

Currently I'm using SuSE's clearlook based Chlorophyll theme which is very nice :)

---

### Post by ade234uk on 2006-02-18
Pheww I had just done a freah install of Ubuntu and was about to install that clearlooks theme again.

I am glad to see I am not the only one experiencing this problem. I want this theme, it looks lovely however if its going to hose Gnome I will wait until its working.

---

### Post by rogeriovinhal on 2006-02-18
I can't get this to work!

I just installed about 3 different version .deb's, it show the correct version in synaptic, i have made the ~/.gtkrc with the Animation = AUTO, because that file didn't exist before, just as ~/.themes doesn't have any files in it.

But clearlooks seem the same as before to me, no animation, no different buttons or anything else...

---

### Post by PrimoTurbo on 2006-02-19
There is no animation with gtk2-engines-clearlooks_2.7.3 & gtk2-engines-clearlooks_2.7.3 for i386, pls fix this.

---

### Post by MighMoS on 2006-02-19
Hmm, I'll have to look into the problems that are being reported more closely when I get some time (things have been hectic recently).  A few things I can point out:  One:  These are built on Breezy.  Installing ANY of my debs on Dapper is at your own risk, as I cannot guarantee that there wont be a library conflict, or unresolved symbols, or something.  Second, I think it was 2.7.3 was weird.  Try installing 2.7.4.  Or, this being the worst advice ever: uninstall the deb files, wait a few weeks, and wait for 2.7.5, or 2.7.91 or whatever's next.  It sucks less, I'm sure.

---

### Post by Rory on 2006-02-19
Has anyone seen a .deb of the animated clearlooks theme in the *original* colours that are in the official Ubuntu package?

The new, brighter colours are just, umm, too bright.  The original blue is far more elegant... especially the pinstripe.

I saw Post #119 that said was using the darker colours, but when I tried it, it was still brighter.  

Too bad, as I was very excited to find an animated version of Clearlooks.

Any ideas?

Rory

---

### Post by kecci on 2006-02-19
Just to let you know...I installed your deb for 2.7.4 on Dapper and it works flawlessly (also the animations, after i modified the gtkrc file)...

---

### Post by Rory on 2006-02-20
On a slightly different topic, anyone who wants a Gaim Guification pop-up theme that's based on the Clearlooks theme can find them here:

[http://kdyne.net/projekty/guifications/index.php?section=get](http://kdyne.net/projekty/guifications/index.php?section=get)

I found them a couple of days ago, have tried them out and they're nicely done.

Rory

---

### Post by bender unit on 2006-02-24
Hello guys!

I haven't read the whole thread, so I don't know if this might have already been answered, but I did a bit of searching without any results. 

Anyways, I tried out the cairo enabled Clearlooks theme, but after installing it, any GTK application that is run using sudo (e.g. synaptic, or Ubuntu's automatic update) uses the ugly default GTK theme instead of the shiny new Clearlooks. 
Does anybody have the same problem? How do I make applications run as root also use the Clearlooks theme? I tried running the Gnome theme selector as root and set the Clearlooks theme there, but it didn't seem to help.

---

### Post by MighMoS on 2006-02-24
[QUOTE=bender unit]Hello guys!

I haven't read the whole thread, so I don't know if this might have already been answered, but I did a bit of searching without any results. 

Anyways, I tried out the cairo enabled Clearlooks theme, but after installing it, any GTK application that is run using sudo (e.g. synaptic, or Ubuntu's automatic update) uses the ugly default GTK theme instead of the shiny new Clearlooks. 
Does anybody have the same problem? How do I make applications run as root also use the Clearlooks theme? I tried running the Gnome theme selector as root and set the Clearlooks theme there, but it didn't seem to help.[/QUOTE]
Okay, did this happen before you upgraded?  If so, I have no idea what the problem is.  If not, I'm more confused, because (at least with the debs that I've made) there should be no way for it not to use cairo clearlooks, it replaces the old one.  

Have you tweaked anything else on your system?  Or did you ever install another theme engine not through a deb file?

---

### Post by bender unit on 2006-02-24
Thanks for the answer MighMos, I've just found out what went wrong - I wasn't using your .debs but the ones that have been linked at the beginning of this thread. I downloaded and installed the ones from your homepage and now also the sudo'ed applications look the right way!

---

### Post by detyabozhye on 2006-05-25
Thankies. ^_^ Any idea why Dapper wants to replace it with the old version?

---

