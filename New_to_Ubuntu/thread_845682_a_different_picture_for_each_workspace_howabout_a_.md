---
title: "a different picture for each workspace? howabout a picture for cube's space?"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by adamogardner on 2008-06-30
title says it all.thinking about rotating the cube somewhere near the pipe nebula. and on it will be something like the hellraiser cube.  I have no Idea how to configure this arrangement.

---

### Post by Old_Grey_Wolf on 2008-06-30
The hellraiser cube would be cool. I haven't been able to have a different background/wallpaper for each workspace. 

I've seen some nebula pictures that could be edited for the Skydome background behind the cube. System > Preferences > Advanced Desktop Effect Settings > Desktop Cube > Appearance > Skydome. If you want the cube background to move behind the cube as it rotates, you'll need to enable Animate Skydome. An animated Skydome can't be just any image size so you may have to modify it. 


Edit: for those that don't know what the hellraiser cube is, it's a puzzle box from the movie Hellraiser. See at Youtube [http://www.youtube.com/watch?v=WSFF1lCOSWQ](http://www.youtube.com/watch?v=WSFF1lCOSWQ). And a description of the movie from wikipedia at [http://en.wikipedia.org/wiki/Hellraiser](http://en.wikipedia.org/wiki/Hellraiser).

---

### Post by adamogardner on 2008-07-01
i found skydome  set an image but the skydome still has a horizon cutting across behind the cube.  So my pipe nebula image is reflecting off of a ground.  I tried adjusting colors to maTCH but it didn't work.  how do I make the skydome entire, rather than halved?

---

### Post by mcduck on 2008-07-01
Disable the Cube Reflection-plugin. It's the one that draws ground & reflection.

---

### Post by tjwoosta on 2008-07-01
there is an easy way to get four different wallpapers on the cube (but you cant have desktop icons)

first set your backgrounds that you want in compiz (go to system-preferences-advanced desktop effects settings then go to desktop cube then appearance tab)  

choose 4 images for the cube (they wont show up yet, this is normal)

then after selecting the backgrounds with compiz 
press alt-f2

then in the box type gconf-editor

navigate to apps-nautilus-preferences

uncheck the box on the right that says show desktop

(this makes nautilus stop drawing the desktop and allows compiz to draw them instead) hence the no icons

---

### Post by Old_Grey_Wolf on 2008-07-01
adamogardner, what tjwoosta suggested worked for me. Thanks tjwoosta.

Edit: That is the first time I've seen the gconfig-editor. Good thing I have a backup, because I'm going to have some fun - hehe.

---

### Post by adamogardner on 2008-07-01
this was all perfect advise.  sadly, I do think that if I hide my desktop then raindrops and tidal wave dont work. *sigh, I'll find out when I get there unless someone knows otherwise.  Otherwise tomorrow I will mark this as solved. Thankyou.

---

### Post by gettinoriginal on 2008-07-01
I also want to thank tjwoosta, great tutorial.:)

---

### Post by tjwoosta on 2008-07-02
> I do think that if I hide my desktop then raindrops and tidal wave dont work. *sigh, I'll find out when I get there unless someone knows otherwise

i dont know for sure because im on a different computer but i think the raindrops and tidal wave should still work because its compiz thats drawing them

---

### Post by biomedtech on 2008-07-02
that whole anthem music is pf irritating

---

### Post by tjwoosta on 2008-07-02
> that whole anthem music is pf irritating
?

did i miss something or did you post in the wrong thread

---

### Post by bhadotia on 2008-07-02
Alright its all working for me including rain drops ( what are tidals ? -never heard of this plugin).
Now how to revert the desktop to the original state?
Also, while we are at it : Is the cube deformation plugin available in hardy - it is in suse11.

---

### Post by tjwoosta on 2008-07-02
> Now how to revert the desktop to the original state?

just put a check mark in the box agian and restart


wow i like that cube deformation plugin (i had never heard of it before) 
not sure if it works in ubunutu or not

---

### Post by bhadotia on 2008-07-02
Oh so we have to restart , heehee . I was getting a little nervous why the desktop did not change even after putting the check back coz I did not even back anything up:biggrin:

---

### Post by adamogardner on 2008-07-02
tidal wave is a water effects option (check little box) and the effect ripples from the title bar ov any unmaximized window if you offer a command that the computer can't perform (like the down arrow in the terminal when there is nowhere to scroll down).  It is a silent way to let you know you made an error or something.

---

### Post by Old_Grey_Wolf on 2008-07-02
> **bhadotia said:**
> Oh so we have to restart , heehee .

After reverting to the original settings I did a log out and logged back in.  Everything was back to normal after logging in. No reboot was required.

---

### Post by jcats on 2008-07-11
Thanks tjwoosta, for really cool set up on what I've been looking to do. But I now have a couple of problems. With compiz drawing my desktop, all the pictures are very pixelated(sp?). And for some reason I have lost the minimize, maximize and close buttons on everything.
So, I tried to revert back as per this thread, and nothing happens when I press alt/f2. I uninstalled/reinstalled compiz, rebooted, logged out/in, and no help. 
Anybody have any ideas or fixes?
thanks;
jcats

---

### Post by nbastaranit on 2008-07-22
i'm going to install ubuntu soon on a computer, and i'm going to have 4 workspaces. if u set the background as an image r whatever, all the workspaces have the same backround. why and how can i fix this, so i can have different backround for ach workspace?

---

### Post by adamogardner on 2008-07-22
the solution is already mentioned below in this very thread!

---

### Post by wavemaker on 2008-07-24
Thanks so much for this thread. I have a small difficulty however. When I try to add different pics it can only find 1 picture even though when I go to my pics I can see em all there.Can anyone advise why this might be so.

---

### Post by nothingspecial on 2008-07-24
> **tjwoosta said:**
> there is an easy way to get four different wallpapers on the cube (but you cant have desktop icons)

first set your backgrounds that you want in compiz (go to system-preferences-advanced desktop effects settings then go to desktop cube then appearance tab)  

choose 4 images for the cube (they wont show up yet, this is normal)

then after selecting the backgrounds with compiz 
press alt-f2

then in the box type gconf-editor

navigate to apps-nautilus-preferences

uncheck the box on the right that says show desktop

(this makes nautilus stop drawing the desktop and allows compiz to draw them instead) hence the no icons


That is excellent. Don`t use desktop icons anyway. Thanks!

---

### Post by adamogardner on 2008-07-24
> **wavemaker said:**
> Thanks so much for this thread. I have a small difficulty however. When I try to add different pics it can only find 1 picture even though when I go to my pics I can see em all there.Can anyone advise why this might be so.

  
   where then are you trying to do this?  under sys>pref>advancedesktopsettings>cubeeffect?   WHat are you doing exactly?  It's the only way I can advise you.

---

### Post by wavemaker on 2008-07-24
Thanks adamogardner. I am trying to get a different pic on each of the desk tops and am following the info on page 1 of this post.
So when I am at>>>cube effect>appearance, and I try to add different pics, although I have several pics in the folder, only one presents its self for selection.

---

### Post by adamogardner on 2008-07-24
you don't want appearance  you want advanced desktop settings.  open that and you'll see bunch of compiz settings.  click on the one that says cube.  click the word don't unclick the box.  When that opens you'll find a data field where you can add new ones.  Let me know how it goes.

---

### Post by steveneddy on 2008-07-24
I guess this plugin doesn't do that...

---

### Post by steveneddy on 2008-07-24
Also look at wallpapoz.

---

### Post by adamogardner on 2008-07-24
wallpaopz link: [http://wallpapoz.akbarhome.com/](http://wallpapoz.akbarhome.com/)
sadly it's no longer supported or developed.

---

### Post by wavemaker on 2008-07-24
Thanks, I have to go out now, I will get on to it and let you know.

---

### Post by wavemaker on 2008-07-25
I go System>prefs>advanced desktop settings>desktop cube>appearance. In there I can add new pics. However when I open the box to do this and click on the files folder, it can only see 1 pic in the folder. I know there are more there. I have tried pasting the locations into the edit box and shows up in the back-ground images box but they do not show up on the cube. The cube rotates and all the rest, just that I appear to be stuck with the one image.

---

### Post by steveneddy on 2008-07-25
> **adamogardner said:**
> wallpaopz link: [http://wallpapoz.akbarhome.com/](http://wallpapoz.akbarhome.com/)
sadly it's no longer supported or developed.

But it works.

I have installed it in the past to see how well it works with Compiz and it did a good job of putting a different wallpaper on each cube side.

---

### Post by tjwoosta on 2008-07-25
> I have installed it in the past to see how well it works with Compiz and it did a good job of putting a different wallpaper on each cube side.

i tried walpapoz but but it looked messed up when i rotate the cube

> I guess this plugin doesn't do that... 

yea the wallpaper plugin will also work if you have it installed

at a time when this thread was new i had the old version of compiz, but i have since upgraded and now with the new compiz i use the wallpaper plugin

but even with the wallpaper plugin you still will need to stop nautilus from drawing the desktop

---

### Post by wavemaker on 2008-07-25
Gooday blokes, I have downloaded that but am unsure how to install it as I have only ever used the package manager in the past. Could you give me a few pointers, Thanks.

---

### Post by steveneddy on 2008-07-26
The only other thing one could do is to tell the wallpaper plugin to use one long wallpaper with a different "scene" for each side of the cube.

If you have an 800x600 desktop, the pic would have to be 

800 x 4 = 3200

so

the new pic size is 3200x600 pixels.

Seems like a lot of work to me, but some people have done that.

---

### Post by wavemaker on 2008-07-26
Thanks very much for that, but my version does not have the wallpaper plug in.

---

### Post by astroorion on 2009-02-13
I know this is an old thread though but I just started using Compiz today I got the Borg wallpaper and oh wow that just blew me away I have been looking for the wallpaper of the hellraiser cube but I know this would have to be Six section's of wallpaper I was able to find one design after doing a google search I don't know how to make wallpaper as of yet but if someone does this give me a holler
[http://www.fortunecity.com/victorian/hillcrest/76/hellraiser/lament-gallery/origami.html](http://www.fortunecity.com/victorian/hillcrest/76/hellraiser/lament-gallery/origami.html)

---

### Post by astroorion on 2009-02-13
Actually it would only need to be cut three times for the pattern I'm going to try to give this a shot

---

### Post by astroorion on 2009-02-13
OK I did alot of work in gimp just to get this together plus in compizconfig
Setting's 
DRUM ROLL I Got a Hellraiser Cube

---

### Post by astroorion on 2009-02-14
Here's another pic with a different background

---

### Post by hollowtd on 2009-03-01
> **tjwoosta said:**
> there is an easy way to get four different wallpapers on the cube (but you cant have desktop icons)

first set your backgrounds that you want in compiz (go to system-preferences-advanced desktop effects settings then go to desktop cube then appearance tab)  

choose 4 images for the cube (they wont show up yet, this is normal)

then after selecting the backgrounds with compiz 
press alt-f2

then in the box type gconf-editor

navigate to apps-nautilus-preferences

uncheck the box on the right that says show desktop

(this makes nautilus stop drawing the desktop and allows compiz to draw them instead) hence the no icons

I've got the 4 wallpapers set and I understand how to check and uncheck the box in the configuration editor. I don't think I understand what you mean by system>pref>advanced desktop  ..Is this in Compiz? I just don't understand this first step and then I've got it I'm sure. Thanks

---

### Post by tjwoosta on 2009-03-02
> **hollowtd said:**
> I've got the 4 wallpapers set and I understand how to check and uncheck the box in the configuration editor. I don't think I understand what you mean by system>pref>advanced desktop  ..Is this in Compiz? I just don't understand this first step and then I've got it I'm sure. Thanks

"system-preferences-advanced desktop effects settings" is what used to be the location of CCSM (compiz config settings manager) in the menus back when this thread was new

with the newer version of compiz i think it might say something different

also i think the newer version of compiz includes the wallpaper plugin, so instead of going to destop cube and appearance you can just go to the wallpaper plugin to set the four wallpapers

the part about gconf-editor should still all be the same as it was back then

---

