---
title: "howto: Make Gnome look like OS X (A work in progress)"
date: 2006-06-14
forum: Outdated Tutorials &amp; Tips
---

### Post by Trocisp on 2006-06-14
First, let me give credit where credit is due.  Lauri Taimila's guide helped a *ton,* [found here](http://users.utu.fi/ljtaim/ubuntuosx.php), and  my question posted [here](http://ubuntuforums.org/showthread.php?t=196228) was responded to with all of the help I could wish for.  Everything in this thread is either directly from one of those guides, or derived from them.

Something like [this](http://uploads.trocisp.com/desktops/laptops/Ubuntu/June14%202006.png) is our end goal.

My goal is to make this as newbie friendly as possible, so this is going to be a *very* step by step guide.


First, go to [this](http://myweb.absa.co.za/errolla/themez/firefox.html) link and click the button that says "Install FoXiTiger Graphite," there will be a little bar pop up at the top of your screen, click the "edit" button and then in the pop up window click allow.  Then click close and click "Install FoxiTiger Graphite" one more time. This time click "Okay" and let it install.  Once that's done simply select "FoXiTiger Graphite" and click "Use this theme."

Now that firefox looks like it belongs in OS X, lets make the rest of the desktop look like OS X.  First, make a folder in your home folder called "customization" in that folder, make 2 folders, one called "backgrounds" and one called "toolbar".  This will make organization easier for newbies. :)

Download [this](http://www.gnome-look.org/content/download.php?content=31618&id=1) to your desktop and open themes ("System -> Preferences -> Themes).  And simply drag the file directly onto the window.  
Download [this](http://www.gnome-look.org/content/download.php?content=30859&id=1) to your desktop and open themes once again and drag the downloaded file onto the window.   At this point select the theme "Tish" and click "Theme Details" go to "Icons" and select "OSX" as your Icon Theme.   Now we can close all of our theme related windows and delete those two files off of our desktop!


We're almost half way there, I know this is a long guide, but I want anyone (even first day users) to be able to do this without a hitch.  That's why I'm shying away from the Terminal with this... and the fact I suck with terminal. :P

Now we need to get rid of the bottom deskbar, right click it and click "Delete this panel" and BOOM, gone!  But there's still more we need to do, we need to add a few things to the top panel.  Right click the top panel and select "Add to panel."  Once you've done that select "Windows List."  

Okay, now we need to install gDesklets for the bottom application bar. ***_OR_*** skip this and go  to the end, there's another type of application bar (one that I'm not as fond of).
[QUOTE=Artificial Intelligence]1. Open the terminal and write:
```
sudo apt-get install gdesklets gdesklets-data
```

2. Now we want gdesklets to start automatically every time we boot up. Click **System** tab in the upper panel. Then **Preferences** ---> **Sessions**.
3. Click the **Startup Programs** tab and click the **Add** button.
4. In the startup Command write: **gdesklets** and click **OK**.
5. To choose and run the gdesklets stuff. Click the **Applications** tab in the upper panel. Then **Accessories** ---> **gDesklets**.
6. Have a look around and pick a gdesklet you like, to add it select the gdesklet. Then go to the **file** tab and select **Run selected desklet**.
7. Now the choosen gdesklet appears and will follow your mouse until you make a left click. To move it again click with middle mouse button or left+right mouse button.
8. To configure the choosen gdesklet, simply right click on it and menu will pop up.
9. For more gdesklets: [http://gdesklets.gnomedesktop.org/](http://gdesklets.gnomedesktop.org/)

**[color=red]NOTE:**[/color]* Some gdesklets might need that you have some extra libs. installed. A good way is to find the gdesklets at [http://gdesklets.gnomedesktop.org/](http://gdesklets.gnomedesktop.org/) and check up on what you need to get the gdesklet you have choosen to work.*[/quote]Following that little quide to install gDesklets, select the folder that says "toolbar/launchers." now double click the "StarterBar" and move that down to the bottom of your screen.

This is where those folders we made come in handy (the one called toolbar for now), open the folder and drag all the applications you want  on your toolbar into the folder (Firefox, gaim, gimp, and so on).  Once you have that done, highlight all of the application short cuts and drag them onto the Desklet toolbar at the bottom of the screen.

Now, change over to the other folder (the one called backgrounds) and drag these ([1]("http://users.utu.fi/ljtaim/images/tiger.jpg") [2]("http://users.utu.fi/ljtaim/images/panther1.jpg") [3]("http://users.utu.fi/ljtaim/images/panther2.jpg")) into the folder.  Right click on your desktop and click "add Wallpaper"  Now double click "customization" folder, then double click the "background" folder and highlight all three backgrounds and click "open".  Select the one you like most and that will be your background.


Tada! You're done!


If you have any comments or critiques on this guide, please dont hesitate to tell me.  I'll add or modify whatever seems to work better than what I have right now!





If you don't like the gDesklets; the following is for you.  (Do not do this if you did the step with the gDesklets)

if you don't want maximized windows to cover your app bar right click your top gnome panel and click "New Panel" drag that to the bottom of your screen, now right click it and go to properties. uncheck all of the checked boxes, and change the size from 24 to 50 pixels. Now click the Background tab and check "Solid color," and move the bar underneath from Opaque to about 1/3 of the way away from the left side.
Then just drag the apps on to that.

---

### Post by Wallakoala on 2006-06-14
There are also some nice OS X icons on gnome-look. Might want to take a look at those.

---

### Post by Trocisp on 2006-06-14
I would like to figure out how to change the ubuntu icon to an apple one, I have an apple icon that I can resize, i just need to know the terminal command where to move it. lol

---

### Post by foofightrs777 on 2006-06-14
rename your image to "distributor-logo.png"

and then:
sudo cp distributor-logo.png /usr/share/icons/hicolor/48x48/apps

You might want to back up the current image first

Regarding the work done on our theme:
I had tried the starter bar in the past.  Unfortunately, it would be hidden by windows if I maximized.  I attempted to rectify that by editting the source.  If you change the window properties from "below" to "above" the window would stay on top.  However, I ended up with the nasty issue that the transparency of the starter would not draw properly and it would cover a portion of my active window with the desktop wall paper.  Have you had that problem or any suggestions to fix it?

Also, perhaps a backround gradient or even traparency would be suitable for your top bar.  I think it would add to the overall 'feel' of the theme.

Best of luck, but also, remember that Ubuntu ISN'T Mac.  There are many things in the Ubuntu interface that are just done differently.  Try not to lose sight of usability simply for aesthetics.  Quite a nice start though. :)

---

### Post by Trocisp on 2006-06-14
[QUOTE=foofightrs777]rename your image to "distributor-logo.png"

and then:
sudo cp distributor-logo.png /usr/share/icons/hicolor/48x48/apps

You might want to back up the current image first[/QUOTE]That didn't work.

---

### Post by foofightrs777 on 2006-06-14
That's strange.  Well, I just did some searching and found [this]("http://ubuntuforums.org/showthread.php?t=109229&page=8&highlight=osx") thread.  It seems to contain a good deal of useful info.

In it, Artificial Intelligence  reccommended to put the icon in:  > ~./theme/<themename>/128x128 or scalable/apps

Maybe give that a try.

---

### Post by Trocisp on 2006-06-14
[QUOTE=foofightrs777]Regarding the work done on our theme:
I had tried the starter bar in the past.  Unfortunately, it would be hidden by windows if I maximized.  I attempted to rectify that by editting the source.  If you change the window properties from "below" to "above" the window would stay on top.  However, I ended up with the nasty issue that the transparency of the starter would not draw properly and it would cover a portion of my active window with the desktop wall paper.  Have you had that problem or any suggestions to fix it?[/QUOTE]
Yes, if you don't want maximized windows to cover your app bar right click your top gnome panel and click "New Panel"  drag that to the bottom of your screen, now right click it and go to properties.  uncheck all of the checked boxes, and change the size from 24 to 50 pixels.  Now click the Background tab and check "Solid color,"  and move the bar underneath from Opaque to about 1/3 of the way away from the left side.


Then just drag the apps on to that.

---

### Post by bigken on 2006-06-14
If its the mac look your after take a look at this guys guide :cool: 

[http://users.utu.fi/ljtaim/dapper-improvments.php]("http://users.utu.fi/ljtaim/dapper-improvments.php")

---

### Post by Trocisp on 2006-06-14
[QUOTE=bigken]If its the mac look your after take a look at this guys guide :cool: 

[http://users.utu.fi/ljtaim/dapper-improvments.php]("http://users.utu.fi/ljtaim/dapper-improvments.php")[/QUOTE]
I quoted Lauri's guide in the *very first paragraph* of the guide.  Also, since he no longer uses this, he no longer updates it.  I took what he said and built upon it (with his permission, of course).


Edited for the correctness of sexes!

---

### Post by Slicedbread on 2006-06-14
There is also a bundle on gnome-look that includes a splash screen, window borders and controls, and link to icons[ here]("http://www.gnome-look.org/content/show.php?content=28686")

---

### Post by Chris03 on 2006-06-14
You can make the minimize, maximize, and close buttons appear on the left side of the window by installing the gconf package and opening gconf-editor.

Then, set apps -> metacity -> general -> button_layout to this:

close,minimize,maximize:menu

---

### Post by bigken on 2006-06-14
delete double post

---

### Post by bigken on 2006-06-14
[quote=Trocisp]I quoted Lauri's guide in the *very first paragraph* of the guide.  Also, since she no longer uses this, she no longer updates it.  I took what she said and built upon it (with her permission, of course).[/quote] 
My apologies for not reading your post properly 


how can i remove the gray tabs on the bottom bar :confused:

[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=11230&stc=1&d=1150324090[/IMG]

---

### Post by foofightrs777 on 2006-06-14
[QUOTE=Trocisp]Yes, if you don't want maximized windows to cover your app bar right click your top gnome panel and click "New Panel"  drag that to the bottom of your screen, now right click it and go to properties.  uncheck all of the checked boxes, and change the size from 24 to 50 pixels.  Now click the Background tab and check "Solid color,"  and move the bar underneath from Opaque to about 1/3 of the way away from the left side.


Then just drag the apps on to that.[/QUOTE]

I don't think I was clear enough.  I was using the startebar in gdesklets as it as it looked more closely like the Mac Dock.

---

### Post by zeca_pedra on 2006-06-14
I followed this how to and I ended up with this 
[ATTACH]11233[/ATTACH]

But I never suceeded on removing the border from the toolbar launcher. Is it possible? I can't find a way to edit the desklet

Besides taht I'm very happy with how it looks and, most of all, how it performs. Xfce is really nice and smooth

Thanks to all who shared their knowledge on this subject
Zeca

---

### Post by bigken on 2006-06-14
yes you were sorry to say i dont like the gdesklets bar ;)

---

### Post by Trocisp on 2006-06-14
[QUOTE=zeca_pedra]I followed this how to and I ended up with this 
[ATTACH]11233[/ATTACH]

But I never suceeded on removing the border from the toolbar launcher. Is it possible? I can't find a way to edit the desklet

Besides taht I'm very happy with how it looks and, most of all, how it performs. Xfce is really nice and smooth

Thanks to all who shared their knowledge on this subject
Zeca[/QUOTE]I don't know a way.  If you'd like to figure out how, I'd love to add it to the guide :)

---

### Post by JGKC9AYC on 2006-06-14
I don't know if anyone else is having problems w/gDesklet like I am & I created a thread about the problem, but if it's ok, i'll put it here as well.
I leave my machine on pretty much 24/7. It seems that after a few hours, gDesklets disappears & I have blank, gray squares on my screen & no gDesklet icon on the top menu bar.  Also, it seems that at times, when I click my Opera starter in the starter bar, Opera starts, but as soon as the page loads it disappears.
Is this a bug? Has anyone else experienced this? Is there a fix/solution for it?  I went to the IRC channel, but didn't get any help.
I like gDesklet & the starter bar as a regular toolbar would take away viewing area when I had a webpage open, but I must say that this is annoying.
Thanks in advance.

---

### Post by danboy on 2006-06-14
if you check out the the .gdesklets directory there should be a folder called gfx under the StarterBar application. If i remember correctly there are seperate graphics for each edge of the starterbar, just open them in gimp and tweak them how you want. I had changed mine from the grey shadow to a 1px white border.

also, you may want to follow the development going on at [http://www.gnome-dock.org](http://www.gnome-dock.org) it's not quite there yet, but now that macslows dock has been adopted I think it's only a matter of time before we have a kick butt gnome dock.

---

### Post by Trocisp on 2006-06-14
[QUOTE=JGKC9AYC]I don't know if anyone else is having problems w/gDesklet like I am & I created a thread about the problem, but if it's ok, i'll put it here as well.
I leave my machine on pretty much 24/7. It seems that after a few hours, gDesklets disappears & I have blank, gray squares on my screen & no gDesklet icon on the top menu bar.  Also, it seems that at times, when I click my Opera starter in the starter bar, Opera starts, but as soon as the page loads it disappears.
Is this a bug? Has anyone else experienced this? Is there a fix/solution for it?  I went to the IRC channel, but didn't get any help.
I like gDesklet & the starter bar as a regular toolbar would take away viewing area when I had a webpage open, but I must say that this is annoying.
Thanks in advance.[/QUOTE]Are your drivers updated?

---

### Post by JGKC9AYC on 2006-06-15
[QUOTE=Trocisp]Are your drivers updated?[/QUOTE]

Which drivers?

---

### Post by Trocisp on 2006-06-15
[QUOTE=JGKC9AYC]Which drivers?[/QUOTE]
Graphics card.

---

### Post by JGKC9AYC on 2006-06-15
[QUOTE=Trocisp]Graphics card.[/QUOTE]

Yes.  I have the latest video drivers.
gDesklets works fine (with the exception of the Opera starter issue), it just disappears after my machine's been on a few hours.

---

### Post by Trocisp on 2006-06-15
[QUOTE=JGKC9AYC]Yes.  I have the latest video drivers.
gDesklets works fine (with the exception of the Opera starter issue), it just disappears after my machine's been on a few hours.[/QUOTE]
Have you tried changing the type of starter? 

As in, if it's a shortcut from desktop icon or a "Right click..." --> "New Starter" --> etc.  try doing it the other way?

---

### Post by JGKC9AYC on 2006-06-15
[QUOTE=Trocisp]Have you tried changing the type of starter? 

As in, if it's a shortcut from desktop icon or a "Right click..." --> "New Starter" --> etc.  try doing it the other way?[/QUOTE]

I've tried both ways...creating one & dragging & dropping.  Sometimes, if I "stop daemon", restart, then drag the Opera shortcut to it, it'll work for awhile.  Wierd.

---

### Post by Laterix on 2006-06-16
[QUOTE=Trocisp]I quoted Lauri's guide in the *very first paragraph* of the guide.  Also, since she no longer uses this, she no longer updates it.  I took what she said and built upon it (with her permission, of course).[/QUOTE]
Actually, I'm HE not SHE. :) I thought my avatar would give me away. Perhaps I should grow a big  moustache or something... ;)

---

### Post by Trocisp on 2006-06-16
[QUOTE=Laterix]Actually, I'm HE not SHE. :) I thought my avatar would give me away. Perhaps I should grow a big  moustache or something... ;)[/QUOTE]Sorry,  I didn't mean to imply a sex when I wrote it.  For some reason I just tend to use she instead of he in unknown situations.

---

### Post by Harold P on 2006-06-25
Hey, just wondering if you have the top panel background image? I don't see a link to it anywhere, and I know the guide isn't complete.

[http://users.utu.fi/ljtaim/ubuntuosx.php#panels](http://users.utu.fi/ljtaim/ubuntuosx.php#panels)

---

### Post by Laterix on 2006-06-25
[QUOTE=Harold P]Hey, just wondering if you have the top panel background image? I don't see a link to it anywhere, and I know the guide isn't complete.
[/QUOTE]
I can't find it anywhere, but it would probably be wrong size anyway, because I have 1360x768 resolution. It's not that hard to do that background image with Gimp. Just create a new image with the height of your panel and width of the resolution you use. Add gradient and cut small pieces from upper corners.

---

### Post by Harold P on 2006-06-29
Okay, found one. I used [this]("http://ubuntuforums.org/showthread.php?t=108446") one, and it looked fine.

---

### Post by jperez on 2006-06-30
Hi there, I'm very new to the Ubuntu forums and to Ubuntu...and to Linux in general.  I like this Linux better than Pogo Linux.  Anyway, I tried to install gDesklets using Terminal just as stated on page one, but it said that it could not find package gdesklets.  Here's the exact text from Terminal:

```
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gdesklets
```

Can anyone help me out?  I'm using Ubuntu v5.04 Hoary Hedgehog x86 and my system specs are:

Dell Inspiron 8100 Laptop
1Ghz/733Mhz Intel SpeedStep
256MB RAM
5.6GB/8GB Parition (Windows XP Home is on 12GB Partition)

Jesse~

**EDIT**
I figured it out.  I needed to active Universe and Multiverse for Ubuntu.  Now, my next concern is moving shortcuts to the StarterBar.  I select the xxxx.desktop shortcuts and drag them over to the StarterBar and they saty in the toolbar folder that was created.  Anyone know what I can 

**EDIT #2**
Nevermind.  It seems that double-clicking the StarterBar in the gDesklet application wouldn't let me drag-n-drop icons into the bar.  Instead, I clicked on the latest install of StarterBar, used the File - Run selected desklet and it worked.  Well, thanks anyway guys and the tutorial was great!

---

### Post by blackjack6.21.91 on 2006-07-05
screenshot please

---

### Post by srunni on 2006-07-05
I don't mean any offense or anything, but why in the world would you want to take a perfectly good GUI and make it look like Mac OS X?

---

### Post by punkinside on 2006-07-07
Because we can :)

[http://www.ldc.usb.ve/~02-35074/Screenshot.png]("http://www.ldc.usb.ve/~02-35074/Screenshot.png")

---

### Post by Hairy_Palms on 2006-07-13
i found a program to let you move the buttons to the other side like mac ,
[http://dave-webster.com/projects/index.php?page=incs/gnome_buttonator](http://dave-webster.com/projects/index.php?page=incs/gnome_buttonator)

---

### Post by Ben Logan on 2006-07-13
Nice one Dave, and thanks to Hairy for pointing us in his direction.

---

### Post by Ben Logan on 2006-07-13
You know what would be really cool?  A little penguin icon in the upper left-hand corner to replace the apple symbol.  I challenge someone to get that going and post a screenshot!  

:p

---

### Post by Hairy_Palms on 2006-07-13
u mean a penguin icon for the menu icon? i had that ages ago under mandrake 9.2 i think i have a screenshot somewhere failing that just find a suitable picture and copy it to /usr/share/icons/hicolor/48x48/apps/distributor-logo.png

---

### Post by Rebeca on 2006-09-03
Was anyone able to use that program that moves the buttons to different sides? If so, can you tell us (or me), how?

Anyway, this thread has been useful to me... along with some of the links provided here and a few more searches in the forum... I was able to change the look of my desktop to something I like a bit more. Oh, and I used a penguin as someone suggested before. (I just googled for an image and resized/edited it in gimp.)

Here's how my desktop looks like now:

[[img]http://xs105.xs.to/xs105/06350/UbuntuScreenshot.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs105&d=06350&f=UbuntuScreenshot.png)

---

### Post by Hairy_Palms on 2006-09-03
yea i used it, worked fine, 
u need to install perl-gtk i think (not sure if thats its name im on fc atm)
then just run the start_perl.sh from a terminal.
ive never tried the ruby script.

---

### Post by Hairy_Palms on 2006-09-03
to use the ruby script u need to install libgtk2-ruby 
to use the perl script libtk2-perl
then they should both work

---

### Post by Rebeca on 2006-09-03
Edit: Missed the post above.

---

### Post by Hairy_Palms on 2006-09-03
i posted the names above, libgtk2-perl and libgtk2-ruby

---

### Post by joemeca on 2006-09-04
awesome tut thanks so much!

---

### Post by Rebeca on 2006-09-05
Thanks, Hairy_Palms.

I already had the perl one, and I installed the ruby one in case the other one didnt work... but I got errors for both:

./start_perl.sh

```
Can't locate Gtk2/GladeXML.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at gnome_buttonator.pm line 31.
BEGIN failed--compilation aborted at gnome_buttonator.pm line 31.
Compilation failed in require at ./main.pl line 4.
BEGIN failed--compilation aborted at ./main.pl line 4.

```

./start_ruby.sh

```

main.rb:19:in `require': no such file to load -- libglade2 (LoadError)
        from main.rb:19

```

---

### Post by kipeloff on 2006-09-06
Hello.

I have succesfully upgraded my desktop to OSX like desktop. 
However I bumped into the following issue. 
When I add to 'Starterbar' link for the application (Gdesklets), that requires Wine for opening, this application doesn't start.
How can I force to start application that require wine ?

---

### Post by Hairy_Palms on 2006-09-06
it should work if u prefix the path to the executable with wine eg 
> wine /home/username/.wine/drive_c/Program\ Files/program/program.exe

---

### Post by kipeloff on 2006-09-06
oh, yes **Hairy_Palms**. Thank you for the help, it has worked fine.

wine /home/user/Desktop/file.exe

---

### Post by yusuf.hm on 2006-10-14
hi there; sorry if someone else got this problem; i'm quite new to gdesklets, so perhaps i did something wrong, but when i added the starter yesterday, here is what it looks like:

[[IMG]http://img157.imageshack.us/img157/3474/capturebh8.th.png[/IMG]](http://img157.imageshack.us/my.php?image=capturebh8.png)

i dont think it's normal; so if someone could help...

---

### Post by shogun1234 on 2006-10-23
> **zeca_pedra said:**
> I followed this how to and I ended up with this 
[ATTACH]11233[/ATTACH]

But I never suceeded on removing the border from the toolbar launcher. Is it possible? I can't find a way to edit the desklet

Besides taht I'm very happy with how it looks and, most of all, how it performs. Xfce is really nice and smooth

Thanks to all who shared their knowledge on this subject
Zeca

how to create a starterbar like yours?

for my gdesklets always has a white background ( [http://www.wretch.cc/album/show.php?i=newbie1234&b=1&f=1989862469&p=0)](http://www.wretch.cc/album/show.php?i=newbie1234&b=1&f=1989862469&p=0)). how to remove or change the background color?

btw, i change the setting of "starterbar.display", but seemingly it doesn't work at all.

starterbar snipet
...
 <group id="panel" bg-color="#00000000" width="100%" height="100%"
           watch="bg-uri=iconbar:background"/> 
...

many thanks.

---

