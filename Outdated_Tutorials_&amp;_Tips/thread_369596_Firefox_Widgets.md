---
title: "Firefox Widgets"
date: 2007-02-24
forum: Outdated Tutorials &amp; Tips
---

### Post by fatsheep on 2007-02-24
I should note for the record that I stopped supporting the widgets when Firefox 3 was released with native GTK widgets.  I felt that these widgets were no longer needed after Firefox 3 came out.  However, there are apparently some people who still use these widgets from looking at the posts in this topic.  I no longer have the time to update this widgets package consistently but please feel free to improve upon the widgets in any way you see fit and release your improved version wherever you want to.  Thanks to everyone who downloaded, I'm glad these widgets could be of use.

- fatsheep, August 25th 2009

[SIZE=5]_**News**_[/SIZE]

**2.7 has been released** (August 6th).  There are no changes to the CSS.  Changes are strictly to the graphic installer interface.  The text entry for the installation path has been replaced with a combo entry containing a dropdown menu.  The dropdown menu will "remember" previous installation/removal paths you have used and display them the next time you use it (assuming you don't delete the "paths" file it creates!).  It will also display some standard installation paths for browsers such as '/usr/lib/firefox'.  The browse button also now will go to the directory specified in the entry box instead of just automatically going to root.  

Check out the screenshot below. :KS

----------------------------------

[img]http://img365.imageshack.us/img365/32/firefoxwidgetsuiof2.png[/img]

One thing that has always bothered me about Ubuntu's firefox is that the buttons, radio buttons, drop down menus, text fields, and checkboxes (known as *widgets*) are very cruddy looking.  Fortunately I found a simple way to fix this.  What we have below is a replacement set of images and CSS code for the widgets which will make them much nicer on the eyes (see bottom of the post for screenshots).  

The original widgets are done by Osmo Salomaa <otsaloma@cc.hut.fi>.  I have written a bash script to make the installation and removal process easier.  You can download this at the bottom of this post.  

To run the graphic installer (for point and click installation and removal), simply unpack the archive anywhere you like, double click on the "graphic_installer", then select "Run".  If you do not have the python-kiwi, it will be installed (python-kiwi is required for the graphical installer to run).  It has been reported that on older Ubuntu's such as Dapper (6.06) this package is simply called "kiwi".  If this is the case you will need to install that package by hand.  After python-kiwi is installed (if it has not already been installed), the graphical installer will run (shown above).

Or, if you prefer, you can use the text based installer which does not require python-kiwi: open a shell, cd to the directory you unpacked the firefox widgets to and run install script (do this with the **./install** command).  Now you are presented with a menu. 

Read the README for more information.  Run the "install" script with the "--help" option for command line option help ("./install --help" works if you are in the same directory). 

Also **make sure you are installing to the path of your Firefox directory.**  By default this script installs to /usr/lib/firefox (which is the default location).  If that is not your Firefox directory you can change it easily.  If you are using the graphic installer it will ask you for the path.  If you are using the text installer ("install" script), then you can enter a new path at the main menu or use the "--path=PATH" or "-p=PATH" command line options to set a path (run the "--help" option for more information).

I should also mention, I have included a backup forms.css file incase you mess anything up.  This file is from a default 64-bit Firefox 2.0 installation.  The forms.css file an be found in Firefox's "res" directory.  You won't need my backup unless you accidently delete your's or the script malfunctions (in which case please contact me).  

[SIZE=4]_**Buttons**_[/SIZE]
[IMG]http://img525.imageshack.us/img525/9933/buttoncomparisonit7.png[/IMG]

[SIZE=4]_**Check Boxes**_[/SIZE]
[IMG]http://img525.imageshack.us/img525/4695/checkboxcomparisongb7.png[/IMG]

[SIZE=4]_**Radio Buttons**_[/SIZE]
[IMG]http://img525.imageshack.us/img525/5641/radiobuttoncomparisonyz0.png[/IMG]

[SIZE=4]_**Drop Down Menus**_[/SIZE]
[IMG]http://img410.imageshack.us/img410/7093/scrollercomparisoniy8.png[/IMG]

[SIZE=4]_**Text Fields**_[/SIZE]
Due to image limitations on the forum I've got to hyperlink this image:
[http://img525.imageshack.us/img525/4117/textfieldcomparisondz6.png](http://img525.imageshack.us/img525/4117/textfieldcomparisondz6.png)

[SIZE=4]_**Before**_[/SIZE]
[IMG]http://img525.imageshack.us/img525/2541/oldgoogleuz4.png[/IMG]

[SIZE=4]_**After**_[/SIZE]
[IMG]http://img410.imageshack.us/img410/9629/newgooglexq7.png[/IMG]

**Note:**

If you are tired of the widgets getting restored after every Firefox update, try this command:

```
sudo dpkg-divert --add **<INSERT FIREFOX ROOT DIRECTORY HERE>**/res/forms.css
```

This should prevent the file from getting updated when Firefox does.  To remove this:

```
 sudo dpkg-divert --remove **<INSERT FIREFOX ROOT DIRECTORY HERE>**/res/forms.css
```

Let me know if this technique works or not, I have not tested it.

[SIZE=4]_**Revisions**_[/SIZE]

**1.1** (March 24th 2007) - Fixes a bug where the widgets override the Ubuntu forum's default "Go!" button (to the right of the search box in the top right).  I'm assuming this bug could also appear on other sites but have not seen it.
**1.2** (June 8th 2007) - Fixes a bug that distorted buttons on this website: [http://www.extjs.com/deploy/ext/docs/index.html](http://www.extjs.com/deploy/ext/docs/index.html).
**1.5 BETA** - All past bug fixes have been made by removal of specific !important statements in the CSS that overrode web page defaults.  In this **BETA** I have removed all !important statements in the CSS.  Please report any problems.
**1.6 BETA** (June 9th 2007) - The removal of a few !important statements caused the corruption of radio buttons, checkboxes, and some text fields.  These !important statements have been edited back in to correct the problem.
**1.7 BETA** (June 9th 2007) - python-kiwi now automatically installs when you choose to run the graphic interface.  Added information for LKRaider to the "AUTHORS" file.
**1.8 BETA** (June 10th 2007) - Minor bug fixes: a typo in the graphic_installer file that may have caused the prompt to install python-kiwi to pop up when it shouldn't have as well as a fix for a bug where buttons would expand to the right and left when selected.
**1.9 BETA** (June 13th 2007) - Removes the margin from buttons so they wil be located in the right place.
**2.0 BETA** (June 14th 2007) - Added messages to the graphic installer and to the text installer instructing the user to restart firefox after installation or removal.  The python-kiwi package is now installed in an xterm terminal.  Fixed a bug in the graphic_installer script.  Minor changes to the install script (I removed a lot of messages to make the output of the script less verbose).
**2.1**  (June 17th 2007) - Increased text input border to 2 px and removed padding and margin from dropdowns.  Minor message changes to the script and graphic installer.  Minor changes to the README.  Removed borders from active (clicked on), disabled radio buttons.
**2.2** (June 19th 2007) - Added reinstallation option.  The graphic installer now tells you what type of change was completed (installation, removal, or reinstallation) instead of just "changes applied".  Install script modified so that it doesn't produce messages already being displayed by the GUI.  Fixed a re-occuring problem where disabled radio buttons were deformed.  Fixes the size of checkboxes at 12 pixels and radio buttons at 13 pixels in order to avoid the tiling of radio or checkbox images when larger sizes are used like in this website: [http://govsearch.publications.gov.au/search/search.cgi?collection=pubs&chksummary=chksummary&fscope=512&form=simple&fqp=1&query=book](http://govsearch.publications.gov.au/search/search.cgi?collection=pubs&chksummary=chksummary&fscope=512&form=simple&fqp=1&query=book). 
**2.3** (June 20th 2007) - Fixed bug #2: deformed radio buttons on [http://www.vietfinsv.net/](http://www.vietfinsv.net/) due to borders and background-colors that conflict with the site's defaults.
**2.4** (June 21st 2007) - Fixed bug #3: Deformed checkbox on [http://forums.invisionpower.com/index.php?act=Search](http://forums.invisionpower.com/index.php?act=Search).  Removed reinstallation (upgrade) option.  The install option now can install over previous installations of the Firefox Widgets.  Modified the installation script to make better use of functions.
**2.5** (July 9th 2007) - Radio buttons now gray out when disabled, show a slightly different color when active (pressed), and drop down menus show the correct button image.
**2.6** (July 11th 2007) - Fixed a bug where the image for the drop down menu did not display properly on [http://arcticmonkeys.trinitystreetdirect.com/](http://arcticmonkeys.trinitystreetdirect.com/). Borders are also now removed from dropdown menus.
**2.7** (August 6th 2007) - Improved the graphic installer so it now has a dropdown menu to select standard install paths from as well as the previous 5 installation or removal paths.  The number "5" is one that I picked and is set by the max_saved_path variable in ff_widgets.py.  You can change it if you like.  All installation/removal paths are saved in the "paths" file (path_file variable in ff_widgets.py if you want to change this name).  The browse button also now opens to the directory specified in the entry field.

---

### Post by fatsheep on 2007-03-06
I hate to be the one bumping my own topic but I'd really appreciate some feedback.  Of the 43 of you who downloaded the attachment so far, what did you think?  Did it work well for you?

---

### Post by Bossieman on 2007-03-06
Thanks for bumping it. I tried it out and it worked perfect.
I use swiftfox so I changed the path to /opt/swiftfox

Thanks!

---

### Post by lcohen999 on 2007-03-06
trying it out now

thank you!

---

### Post by stalefries on 2007-03-06
Very nice, worked perfectly. I had forgotten all about this.

---

### Post by Nikron on 2007-03-06
Worked perfectly...  Even used my gtk theme better than the default ccs did.  Thanks a lot.  The only bad thing I can say is that the drop down menu is still a drop down menu, those arrows don't work.

---

### Post by kobewan on 2007-03-07
Looks really nice, but is there any way to customize what you want to change? For example, I love the radio buttons and checkboxes, but prefer the default 'Buttons'.

---

### Post by userundefine on 2007-03-07
And for KDE:

> Form widgets
As you can see, the default forms that firefox renders is not too nice (disgusting).
The solution is pretty easy, i found that here.

You need to download a tarball with some css and pngs, then extract it to your firefox install direcotory.

Code:

```
wget http://home.comcast.net/~tehdnite/linux/prettywidgets_firefox2_linux.tar.gz
sudo cp -r /usr/lib/firefox/res/ /usr/lib/firefox/res_original
tar -xvvzf prettywidgets_firefox2_linux.tar.gz
sudo mv ./prettywidgets_firefox2_linux/* /usr/lib/firefox/res/
```
Then, restart firefox, and enjoy the first step of this how to.


[credit]("http://ubuntuforums.org/showthread.php?t=336181&highlight=kgtk")

---

### Post by Spudgun on 2007-03-07
Looks good, cheers :]

---

### Post by ifross on 2007-03-07
Works great! :)

---

### Post by Hoag on 2007-03-07
Excellent! When I first got Ubuntu, I noticed the less than lovely looking widgets , and this made everything much better!

Worked seamlessly, and took less than a minute to do.

Two thumbs up. :)

---

### Post by Catsworth on 2007-03-07
This didn't apear to work with my install, I think it's because I don't have the /usr/local/firefox32 directory.  How do I know what path I should set instead?

Thanks.

---

### Post by fatsheep on 2007-03-07
> **Catsworth said:**
> This didn't apear to work with my install, I think it's because I don't have the /usr/local/firefox32 directory.  How do I know what path I should set instead?

Thanks.

Well what browser are you trying to install to?  Regular firefox or firefox32?

---

### Post by hornett on 2007-03-08
Thanks for this, fatsheep. :KS 

You reminded me of this article: [http://mpt.net.nz/archive/2005/04/11/ubuntu](http://mpt.net.nz/archive/2005/04/11/ubuntu)

> The form controls Firefox draws in Web pages are not just inconsistent with those in the rest of the operating system, they are quite possibly the ugliest interactive controls seen in any graphical interface since AmigaDOS 2.04. For example, text fields have borders that, by default, are visible on only two sides out of four. <select> elements are rendered not as normal option menus, but as much less efficient drop-down scrolling listboxes. **And radio buttons look like they were drawn in the dark with a broken pencil.**


I appreciate your work on the script (and of course the artist's work it installs) but why is this not fixed by default (two years after the article)?

---

### Post by Ago12 on 2007-03-08
Thanks, it has worked flawlessly on a regular Firefox on Feisty :)

---

### Post by diskotek on 2007-03-08
how can i work it out with Xfce? if anyone wrote littlbe bit briefly, it wouldbe wonderful..

---

### Post by Catsworth on 2007-03-08
> **fatsheep said:**
> Well what browser are you trying to install to?  Regular firefox or firefox32?

Didn't even realise there *was* a Firefox32.....

I think I must be running the regular version, whatever comes with Ubuntu as standard.

Cheers.

---

### Post by Ago12 on 2007-03-08
Fx is desktop agnostic.

It works the same way on xfce (tested and approved) :)

---

### Post by xolot1 on 2007-03-08
great job. works perfectly and looks so much better.

---

### Post by Catsworth on 2007-03-08
Ok, I changed the install path to:

```
/usr/share/firefox
```

Which appears to be where FF lives on my Ubuntu install, and it still isn't working.

Do I need to reboot or something?

---

### Post by diskotek on 2007-03-08
> **Ago12 said:**
> Fx is desktop agnostic.

It works the same way on xfce (tested and approved) :)

thanks i'll try it tonight :D

---

### Post by DaVinciXL on 2007-03-08
Great job!
Works pefectly and is absolutely amazing...

---

### Post by diskotek on 2007-03-09
yes, i applied it; so easy & simple and works great. thank you very much...

---

### Post by nero_86 on 2007-03-09
Very good work! Looks very fine! thanks :)

---

### Post by Condoulo on 2007-03-09
Hey, this works great. :) Glad you posted this.

---

### Post by jamienos on 2007-03-09
I'm glad i was not the only one who thoght that the button's looked ugly - installed and work's fine! nice work thankyou:)

---

### Post by Leonivek on 2007-03-10
Wow!  Awesome!  Looks sweet, now!  Thanks! \\:D/

---

### Post by Kobalt on 2007-03-10
Hell it's great... ! 
I'd love Firefox to ship with this kind of look.

---

### Post by Catsworth on 2007-03-10
> **Catsworth said:**
> Ok, I changed the install path to:

```
/usr/share/firefox
```

Which appears to be where FF lives on my Ubuntu install, and it still isn't working.

Do I need to reboot or something?

Ok, a reboot didn't help - and I'm still stuck with nasty looking FF, anybody got any ideas?

Thanks.

---

### Post by gschoper on 2007-03-10
Great post. Thanks.

gschoper

---

### Post by alephiej on 2007-03-10
Works fine on Edgy. Thanks. As a matter of fact I haven't even realized how ugly default controls looked like.

---

### Post by kobewan on 2007-03-10
> **Catsworth said:**
> Ok, a reboot didn't help - and I'm still stuck with nasty looking FF, anybody got any ideas?

Thanks.

Try /usr/lib/firefox instead.

---

### Post by fatsheep on 2007-03-10
Thanks for the support everyone, I'd love it if firefox shipped with these widgets by default too.

> **kobewan said:**
> Try /usr/lib/firefox instead.

/usr/lib/firefox is the default home of firefox and also the default installation path of the script.  Are there any errors when the script is run?  Just to make sure this is where firefox is installed post the output of this command:

```
dpkg -S firefox
```

---

### Post by Catsworth on 2007-03-11
The output of that command would seem to suggest that it's installed in /usr/share/firefox/

I'll try the inatall again with that path (although I'm sure I've tried that before.....).

---

### Post by Catsworth on 2007-03-11
Nope, doesn't work with that path either.

---

### Post by freexzai on 2007-03-11
very nice update. id been so used to how it looked id never thought about chaning it haha.

---

### Post by psyke83 on 2007-03-11
fatsheep,

Firefox looks much better now, thanks. Just a note, your little packaged script works fine on Feisty too :)

---

### Post by ykpaiha on 2007-03-11
this should be the first change for any firefox installed
:guitar:

---

### Post by wolf08 on 2007-03-11
Wow! This looks great. Thanks for the modifications.

Have you posted this on the mozillazine forums?

---

### Post by spanella47 on 2007-03-12
yeah nice work, had looked at the old attempts at this but never liked the widgets or the difficulty of installing them.

side note - feel like the buttons are very flat compared to the checkboxes and bullets.  anyone skilled at this wanna take a stab at making them look more like the default ubuntu buttons.  (ie lighter grey with more rounded dark border then when pressed, visually depressed and dark grey)

---

### Post by ykpaiha on 2007-03-12
in extra for a very good looking use as well
flatstyle in your menu and you never go back to msexplorer (lol)
[https://addons.mozilla.org/search.php?q=flatstyle&type=E&app=firefox](https://addons.mozilla.org/search.php?q=flatstyle&type=E&app=firefox)

:lolflag:

---

### Post by fatsheep on 2007-03-13
> **Catsworth said:**
> The output of that command would seem to suggest that it's installed in /usr/share/firefox/

I'll try the inatall again with that path (although I'm sure I've tried that before.....).

Could you post the output of the dpkg -S firefox command as well as the output of the script when you install?  Also, make sure you completely close out ALL firefox windows after installation.  Even if you have the download window open, the widgets will not appear when you open up firefox.

[quote=wolf08] 	Wow! This looks great. Thanks for the modifications.

Have you posted this on the mozillazine forums?[/quote]

Nope, I've actually never posted there before.

---

### Post by Catsworth on 2007-03-13
> **fatsheep said:**
> Could you post the output of the dpkg -S firefox command as well as the output of the script when you install?  Also, make sure you completely close out ALL firefox windows after installation.  Even if you have the download window open, the widgets will not appear when you open up firefox.

Will do that tonight, thanks for your continued help with this.

---

### Post by Catsworth on 2007-03-13
Ok.

**dpkg -S firefox**

See attachment


**./install**

```
rob@raistlin:~/Desktop/firefox-widgets-1.0$ ./install
1 ) Install Firefox widgets.
2 ) Remove Firefox widgets.
3 ) Specify a new installation/removal path.
4 ) Scroll the help file.
5 ) Exit.
Select an Option: 3
Please enter a new path: /usr/lib/firefox
$destdir = /usr/lib/firefox
------------

1 ) Install Firefox widgets.
2 ) Remove Firefox widgets.
3 ) Specify a new installation/removal path.
4 ) Scroll the help file.
5 ) Exit.
Select an Option: 1
Installing Firefox Widgets
==========================

We will be creating a folder at /usr/lib/firefox/res/form-widgets.
We will then append the contents of forms-extra.css
to /usr/lib/firefox/res/forms.css.
Press enter to continue.
---------------

Installing the widget images to /usr/lib/firefox/res/form-widgets.
Appending contents of forms-extra.css to /usr/lib/firefox/res/forms.css.
Installation process complete.
rob@raistlin:~/Desktop/firefox-widgets-1.0$ 
```

---

### Post by fatsheep on 2007-03-13
> **Catsworth said:**
> Ok.

**dpkg -S firefox**

See attachment


**./install**

```
rob@raistlin:~/Desktop/firefox-widgets-1.0$ ./install
1 ) Install Firefox widgets.
2 ) Remove Firefox widgets.
3 ) Specify a new installation/removal path.
4 ) Scroll the help file.
5 ) Exit.
Select an Option: 3
Please enter a new path: /usr/lib/firefox
$destdir = /usr/lib/firefox
------------

1 ) Install Firefox widgets.
2 ) Remove Firefox widgets.
3 ) Specify a new installation/removal path.
4 ) Scroll the help file.
5 ) Exit.
Select an Option: 1
Installing Firefox Widgets
==========================

We will be creating a folder at /usr/lib/firefox/res/form-widgets.
We will then append the contents of forms-extra.css
to /usr/lib/firefox/res/forms.css.
Press enter to continue.
---------------

Installing the widget images to /usr/lib/firefox/res/form-widgets.
Appending contents of forms-extra.css to /usr/lib/firefox/res/forms.css.
Installation process complete.
rob@raistlin:~/Desktop/firefox-widgets-1.0$ 
```

Ok.  Go to the shortcut for firefox that you use and find out what file it links to (put it on the panel or desktop if it isn't already, right click on it and go to properties).  It probably points to /usr/bin/firefox.  In this case you would use the command ```
readlink /usr/bin/firefox
``` to see what executable file this file is symlinked to.  It should be either /usr/share/firefox/firefox or /usr/lib/firefox/firefox.  In other words, your firefox is either located in /usr/share/firefox or /usr/lib/firefox. 

Now go to whichever directory firefox is located in navigate to the "res" folder.  There should be a folder inside called "form-widgets".  Make sure it exists and make sure it has the correct images inside (you have the same folder inside the archive that the script shipped in.  Now open "forms.css", scroll down to the bottom.  There should be this line: 

```
/*** END EXTRA FIREFOX WIDGETS ***/
```

And if you scroll up you will find a similar comment for the beginning of the appended text.  Make sure this exists.  If everything is in place then the only other suggestion I would have would be to reinstall firefox.  Good luck,

-sheep

---

### Post by mykalreborn on 2007-03-14
really cool ... definetly bookmark this post. one thing though... is it possible to get your gtk/murrine/clearlooks theme instead of the widgets you made?
just curious. that would be really cool.

---

### Post by Catsworth on 2007-03-14
Sorted, and it was in:

```
/opt/firefox
```

Thanks very much for your help, and for putting this together - it looks great.

---

### Post by Airwalka on 2007-03-14
Thanx ... it works perfectly!

---

### Post by fatsheep on 2007-03-14
> **Catsworth said:**
> Sorted, and it was in:

```
/opt/firefox
```

Thanks very much for your help, and for putting this together - it looks great.

Wow that's odd.  I'm glad it worked.  :)


> **mykalreborn said:**
> really cool ... definetly bookmark this post. one thing though... is it possible to get your gtk/murrine/clearlooks theme instead of the widgets you made?
just curious. that would be really cool.

Thanks for the complements.  I didn't make the widgets by the way, I just made the installer script and guide.  I'm not sure what you mean by the gtk/murrin/clearlooks theme?  Do you mean have the buttons on the internet look like the buttons on GTK widgets?

---

### Post by maddog39 on 2007-03-14
Installed your little mod, was pretty cool. Although I would like to see the buttons depress when clicked and stuff. I think it would be/look alot nicer. But nice mod, I have it installed right now. It also works perfectly in epiphany. :D

---

### Post by mykalreborn on 2007-03-15
> Do you mean have the buttons on the internet look like the buttons on GTK widgets?

yep, that's exaclty what i meant 
:D

---

### Post by BobSongs on 2007-03-15
[FONT="Tahoma"][COLOR="DarkSlateGray"][B]Mmm. Now *that* helps to make FireFox look much more professional in Ubuntu.

Thank you.

Sure; it's a minor detail. But on occasion I have friends in to look at my PC as an example of what Ubuntu does. And a shabby looking FireFox doesn't help sell the product.[/B][/COLOR][/FONT]

---

### Post by jbus on 2007-03-15
Thanks fatsheep, This works great!

I think it's ridiculous that Firefox developers have continued to ignore this very noticeable UI enhancement for Linux users. I suspect it will be 2035 and Firefox users will still be waiting for Firefox developers to implement this feature.

---

### Post by foureight84 on 2007-03-16
NICE!!! i was wondering if i could change that. great work!

---

### Post by fatsheep on 2007-03-16
> **mykalreborn said:**
> yep, that's exaclty what i meant 
:D

Feel free to try editing the widget images to imitate the gtk look if you want.  I don't know of any other way to get the gtk buttons in firefox.

---

### Post by tgrisier on 2007-03-17
Great look. I'm using it in both firefox and swiftfox.  Install was as painless as they come.

---

### Post by mykalreborn on 2007-03-17
> Feel free to try editing the widget images to imitate the gtk look if you want. I don't know of any other way to get the gtk buttons in firefox.

oh. cool! thanks!

---

### Post by i M@N on 2007-03-17
Hello !

Many thnxX for this !! :grin:

i've just launched ./install -p=/home/iman/swiftfox -i and it's been working like a charm ...

@+...

---

### Post by rko618 on 2007-03-17
Thanks fatsheep! I have always felt that Firefox under Linux was rather ugly compared to its Windows counter part.  This script fixes a lot of those issues.  Much thanks.

---

### Post by matburton on 2007-03-23
Awesome!

Much prettier ;)

---

### Post by sancheztavo on 2007-03-23
Great, now I feel much more comfortable...
Now, it would be nice to see when a button / form / etc. is disabled. Because they show as if they were enabled.
Thanks!

---

### Post by fatsheep on 2007-03-23
> **sancheztavo said:**
> Now, it would be nice to see when a button / form / etc. is disabled. Because they show as if they were enabled.
Thanks!

I'm not sure what you mean.  Could you explain?

---

### Post by FuturePilot on 2007-03-23
Wow! These look great. I was always a little annoyed by the way these widgets looked, but now they're much better. Everything went perfectly. I'm running Firefox 2.0.0.3 on Dapper so it's installed in the /opt directory. Changed the installation path and everything went perfectly:)
The only issue I found was the GO button next to the search bar on the forums here is unreadable now because of the text color.

---

### Post by qyte on 2007-03-24
I am running firefox on feisty. the script seems to have worked just fine but i noticed something that is somewhat ugly :(
HAS anyone noticed the button here in this very forum the one up right in the search that used to be a Go? For me it is just a blank button :confused: 
And i don't mean the vbulletin tools search...
THE ONE that is hi up... If it causes a problem there it may very well cause problems elsewhere.
Well apart from that i haven't noticed any other malfunction (i just installed it though ;) ).

---

### Post by TheMono on 2007-03-24
I just installed on Feisty as well. Does look a lot better, but I also have the blank button on the search thingy for this forum!

---

### Post by FuturePilot on 2007-03-24
Yeah, that's what I was talking about. The only other thing I noticed was that certain sites actually skin the widgets to match the site. However I noticed that these seem to override that.

---

### Post by Outrunner on 2007-03-24
Very well done! Works perfectly and looks nice. Good job, keep up the good work ;)

---

### Post by Nikron on 2007-03-24
> **qyte said:**
> I am running firefox on feisty. the script seems to have worked just fine but i noticed something that is somewhat ugly :(
HAS anyone noticed the button here in this very forum the one up right in the search that used to be a Go? For me it is just a blank button :confused: 
And i don't mean the vbulletin tools search...
THE ONE that is hi up... If it causes a problem there it may very well cause problems elsewhere.
Well apart from that i haven't noticed any other malfunction (i just installed it though ;) ).

I have the same problem

---

### Post by gkasinath on 2007-03-24
It works awesome! Thanks for that!
Excellent work guys! 

Cheers
Gautham Kasinath
P.S. The *Go* button is er.. Gone though. I dont use that much so it dont hurt me! :)

---

### Post by gjtoth on 2007-03-24
NICE STUFF!  Thanks!

---

### Post by fatsheep on 2007-03-24
> **qyte said:**
> I am running firefox on feisty. the script seems to have worked just fine but i noticed something that is somewhat ugly :(
HAS anyone noticed the button here in this very forum the one up right in the search that used to be a Go? For me it is just a blank button :confused: 
And i don't mean the vbulletin tools search...
THE ONE that is hi up... If it causes a problem there it may very well cause problems elsewhere.
Well apart from that i haven't noticed any other malfunction (i just installed it though ;) ).


Yep, I have the same problem and unfortunately I'll look into it - maybe a simple recoloring of the widgets will do.

EDIT: Nope the text color is not the issue, the text on that button is bright red, it's just the fact these new widgets are covering overriding the forum's defaults.  I have emailed the creator of the widgets - I will post back here when he replies.

---

### Post by morneHeru on 2007-03-24
Just installed these on Minefield. 

Looking great, thanks! :)

---

### Post by fatsheep on 2007-03-24
Osmo got back to me and said I could try deleting some of the "!important" statements in the CSS file.  I fiddled around with the file until I found the right !important statement to delete and now the widgets no longer override the forum's defaults.  I have uploaded a new version with this fix (1.1).  The only change is to the forms-extra.css file.

**Please report any bugs.**

---

### Post by zerwas on 2007-03-29
In my opinion this should get default in Ubuntu. Works perfectly with Feisty.

Any reason why it shouldn't be a default setting?

---

### Post by fatsheep on 2007-03-29
> **zerwas said:**
> In my opinion this should get default in Ubuntu. Works perfectly with Feisty.

Any reason why it shouldn't be a default setting?

I don't see why not.  We would just have to contact the previous people who worked on the widgets to make sure we could license it under the GPL.

---

### Post by ktak on 2007-03-30
Perfectly! Thank you!!!

---

### Post by zerwas on 2007-03-30
> **fatsheep said:**
> We would just have to contact the previous people

Would you want to do that? My english is very bad :(. Having this improvement would be so great.

---

### Post by fatsheep on 2007-03-30
> **zerwas said:**
> Would you want to do that? My english is very bad :(. Having this improvement would be so great.

I have emailed all of them but how do you intend to get this included in Ubuntu by default?

---

### Post by Twizz on 2007-03-31
Really nice How to.  It worked great for me. thx :)

---

### Post by fatsheep on 2007-04-01
So far Timothy Babych has agreed to open source his work.  I'm waiting on responces from Garrett LeSage and Kevin Gerich.

> **Twizz said:**
> Really nice How to.  It worked great for me. thx :)

Glad it worked for you. :)

---

### Post by drago on 2007-04-06
Ehhrm, Is there any way anyone could mirror the widget pack? I cant fetch them from this forum (gets a zero byte file and nothing happens). 
Thanks in advance.

---

### Post by zerwas on 2007-04-06
> **drago said:**
> Ehhrm, Is there any way anyone could mirror the widget pack? I cant fetch them from this forum (gets a zero byte file and nothing happens). 
Thanks in advance.

[http://koti.mbnet.fi/~ots/artwork/firefox-form-widgets-ots.tar.gz](http://koti.mbnet.fi/~ots/artwork/firefox-form-widgets-ots.tar.gz)

---

### Post by Quillz on 2007-04-19
Thanks for this tutorial! I actually made a thread just tonight (without finding this one first) about changing the ugly widgets.

---

### Post by fatsheep on 2007-04-22
> **drago said:**
> Ehhrm, Is there any way anyone could mirror the widget pack? I cant fetch them from this forum (gets a zero byte file and nothing happens). 
Thanks in advance.

It works for me, that mirror below didn't though.  Perhaps someone else can mirror it for you, I don't have a means of doing that.

[quote=Quillz]Thanks for this tutorial! I actually made a thread just tonight (without finding this one first) about changing the ugly widgets.[/quote]

Your welcome.  Did you use a similar method?  I'd be interested in your thread, could you link me to it?

---

### Post by huntermix on 2007-04-25
thanks, looks great!!!!

---

### Post by strabes on 2007-04-27
I'm so glad I found this. It looks wonderful. Thanks for your contribution.

---

### Post by schnupi on 2007-04-28
Thanks dude! I really hated those old forms, buttons etc.. now i like firefox/swiftfox again^^

---

### Post by BobSongs on 2007-05-02
[FONT=Verdana]I may have posted before, but I thought I'd put something here you may even wish to add to your tutorial.

You see: I'm running Dapper Drake and I've updated Firefox from 1.5 to 2.0.0.3 using the script found in [**this thread**]("http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla#Install_Official_Mozilla_Build_of_Firefox"). 

However the change of browser version caused the previous widgets to vanish (gah!). Re-running the script as is did nothing. I found out that at Step 1 it was necessary to change the path to [FONT=Courier New]**/opt/firefox**[/FONT] and it worked beautifully. (I missed the radio buttons most).

All works well now. It's much appreciated. Thanks.
[/FONT]

---

### Post by Bashed on 2007-05-04
Bit of a problem.  I am using 64bit Ubuntu Feisty and followed this guideline to install firefox 32bit version for sake of using plugins
[http://ubuntuforums.org/showthread.php?t=202537](http://ubuntuforums.org/showthread.php?t=202537)

I ran your script (which worked fine in 32bit of ubuntu) and it did not work. I closed firefox, retried, opened ff and it did not take effect.

---

### Post by mandela on 2007-05-05
Two thumbs up. It worked perfectly.

---

### Post by Bashed on 2007-05-05
Can someone please help me out here?

---

### Post by Rui Pais on 2007-05-05
> **TalkJesus said:**
> Can someone please help me out here?

do you still have your 32bit ubuntu installation? you can try mount it somewhere and copy the /mozilla-firefox/res/* over the 32b firefox/res/ 
(you can make previously a copy of the res being overwritted  so you can revert things in case it fails somehow...) 

hth

---

### Post by Bashed on 2007-05-05
> **Rui Pais said:**
> do you still have your 32bit ubuntu installation? you can try mount it somewhere and copy the /mozilla-firefox/res/* over the 32b firefox/res/ 
(you can make previously a copy of the res being overwritted  so you can revert things in case it fails somehow...) 

hth

What are you talking about? I'm not a linux guru, so I don't understand your language unfortunately. 

Yes, I have the '32bit' install as I already installed it.

---

### Post by Rui Pais on 2007-05-05
> **TalkJesus said:**
> What are you talking about? I'm not a linux guru, so I don't understand your language unfortunately. 

Yes, I have the '32bit' install as I already installed it.

no prob...

locate your firefox32 install. 
If you used kilz script should be /usr/local/firefox32, i think (confirm on your box, please). Inside there are a res/ directory, among others.

Now mount the partiticion with your 32b install. it should be something like:
```
mkdir 32ubu
sudo mount /dev/sdxxx 32ubu
```
where sdxx is the partition name of 32b ubuntu (sda1, hda4, something like that.)
When mounted close any firefox windows and copy with:
```
sudo mv /usr/local/firefox32/res /usr/local/firefox32/res_BACKUP
sudo cp -a 32ubu/usr/lib/firefox/res /usr/local/firefox32/
``` (assuming thats the path on 64b)

you can unmount then:
```
sudo umount /dev/sdxxx
```

start firefox to see it it worked.

---

### Post by Bashed on 2007-05-05
Didn't work sorry

chad@Secured:~$ sudo move /usr/local/firefox32/res /usr/local/firefox32/res_BACKUP
sudo: move: command not found

chad@Secured:~$ sudo cp -a 32ubu/usr/lib/firefox/res /usr/local/firefox32/
cp: cannot stat `32ubu/usr/lib/firefox/res': No such file or directory

However, the directory is there

/usr/local/firefox32/res

---

### Post by Rui Pais on 2007-05-05
> **TalkJesus said:**
> Didn't work sorry

chad@Secured:~$ sudo move /usr/local/firefox32/res /usr/local/firefox32/res_BACKUP
sudo: move: command not found

sorry, silly me. it's sudo mv, not sudo move (i add that in a run as an edit, :()

> 
chad@Secured:~$ sudo cp -a 32ubu/usr/lib/firefox/res /usr/local/firefox32/
cp: cannot stat `32ubu/usr/lib/firefox/res': No such file or directory

However, the directory is there

/usr/local/firefox32/res

seems that you forget to mount first the 32 version on 32ubu.

---

### Post by Bashed on 2007-05-05
No I did not forget

chad@Secured:~$ sudo mount /dev/sda3 32ubu
mount: /dev/sda3 already mounted or 32ubu busy
mount: according to mtab, /dev/sda3 is mounted on /

chad@Secured:~$ sudo mv /usr/local/firefox32/res /usr/local/firefox32/res_BACKUP

chad@Secured:~$ sudo cp -a 32ubu/usr/lib/firefox/res /usr/local/firefox32/
cp: cannot stat `32ubu/usr/lib/firefox/res': No such file or directory

```
 chad@Secured:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             9.9G  3.5G  6.0G  37% /
varrun               1002M  116K 1002M   1% /var/run
varlock              1002M     0 1002M   0% /var/lock
procbususb           1002M  140K 1002M   1% /proc/bus/usb
udev                 1002M  140K 1002M   1% /dev
devshm               1002M     0 1002M   0% /dev/shm
lrm                  1002M   39M  964M   4% /lib/modules/2.6.20-15-generic/volatile
/dev/sda1             101G   16G   86G  15% /media/sda1
/dev/sda3             9.9G  3.5G  6.0G  37% /home/chad/32ubu
```

---

### Post by Rui Pais on 2007-05-05
> **TalkJesus said:**
> No I did not forget

chad@Secured:~$ sudo mount /dev/sda3 32ubu
mount: /dev/sda3 already mounted or 32ubu busy
mount: according to mtab, /dev/sda3 is mounted on /

chad@Secured:~$ sudo mv /usr/local/firefox32/res /usr/local/firefox32/res_BACKUP

chad@Secured:~$ sudo cp -a 32ubu/usr/lib/firefox/res /usr/local/firefox32/
cp: cannot stat `32ubu/usr/lib/firefox/res': No such file or directory

```
 chad@Secured:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             9.9G  3.5G  6.0G  37% /
varrun               1002M  116K 1002M   1% /var/run
varlock              1002M     0 1002M   0% /var/lock
procbususb           1002M  140K 1002M   1% /proc/bus/usb
udev                 1002M  140K 1002M   1% /dev
devshm               1002M     0 1002M   0% /dev/shm
lrm                  1002M   39M  964M   4% /lib/modules/2.6.20-15-generic/volatile
/dev/sda1             101G   16G   86G  15% /media/sda1
/dev/sda3             9.9G  3.5G  6.0G  37% /home/chad/32ubu
```

You are mounting you system (the 64b one?) inside 32ubu folder. 

You need to mount the 32bits Ubuntu install on that folder to copy from its firefox.

unmount that with:
```
sudo umount /home/chad32ubu
```
since thats a special case (you mounted your running system) i don't know if it will umount. If not you may need to reboot.

keep post any doubts or problems till we get it. Good luck.

---

### Post by Bashed on 2007-05-05
" You need to mount the 32bits Ubuntu install on that folder to copy from its firefox."

What are you talking about?  I simply followed your instructions.

---

### Post by Rui Pais on 2007-05-05
> **TalkJesus said:**
> " You need to mount the 32bits Ubuntu install on that folder to copy from its firefox."

What are you talking about?  I simply followed your instructions.

Ok. Something is not clear here. Let me try to clarify (if i get it correctly).

By  32bits install i mean your Ubuntu (the **all **operating system) 32 bits, not the firefox32 install inside your Ubuntu 64bits.

You said you have the script running correctly at 32b thats why i ask if you still have that install.

If you still have both install of Ubuntu - 32b and 64bits - you need to from inside one mount the other and copy the res folder inside the firefox folder of 32b Ubuntu to the firefox32 on 64b Ubuntu.

Sounds complicated and tricky 'cause of that annoying 32/64 naming... but it's simple.

If i miss something or point something incorrect post, please.

---

### Post by Grosser on 2007-05-05
Hello fatsheep,

it looks very nice.
Could you make the Buttons like Opera please (round and glass-look) ?

Greets

---

### Post by Bashed on 2007-05-05
I said it *worked in 32bit* but I *do not* have 32bit Ubuntu installed now, only 64 bit hence why I'm trying to get it to work in 64bit.

I hope someone has a solution

---

### Post by Rui Pais on 2007-05-06
> **TalkJesus said:**
> I said it *worked in 32bit* but I *do not* have 32bit Ubuntu installed now, only 64 bit hence why I'm trying to get it to work in 64bit.

I hope someone has a solution

thats why i ask if you still had your 32bits install. 
in attach ( [ATTACH]31911[/ATTACH]) there is a compressed file with a working res.
just uncompress it to your home or somewhere else, 
go to place that conains the uncompressed res/ and do:
```
sudo mv /usr/local/firefox32/res /usr/local/firefox32/res_BACKUP
sudo mv res /usr/local/firefox32/
```

---

### Post by Rui Pais on 2007-05-06
> **Grosser said:**
> Hello fatsheep,

it looks very nice.
Could you make the Buttons like Opera please (round and glass-look) ?

Greets

hi,
if you look inside your firefox installation folder (usually /usr/lib/mozilla-firefox/) there is a folder named res with the images, in png format, of the widgets.
You can replaced them by the ones that came with opera or any others that you like, as long as they have the same size and you give them the same name, should work.

good luck.

---

### Post by Condoulo on 2007-05-06
Awesome Tutorial. Thanks a lot. :)

---

### Post by Condoulo on 2007-05-06
> **Rui Pais said:**
> hi,
if you look inside your firefox installation folder (usually /usr/lib/mozilla-firefox/) there is a folder named res with the images, in png format, of the widgets.
You can replaced them by the ones that came with opera or any others that you like, as long as they have the same size and you give them the same name, should work.

good luck.

Wow. I should really do that so the widgets go along with my theme.

---

### Post by andrek on 2007-05-06
GREAT tutorial, GREAT widgets :)

Thanks a lot.

---

### Post by fatsheep on 2007-05-06
If anyone gets an opera theme working I'd like to see screenshots.  :)

---

### Post by moredhel on 2007-05-07
awesome! :)

If only these widgets were the default :P

---

### Post by DarthWHO on 2007-05-08
Fantastic!! 

The appearance of some of these, with particular emphasis on the Radio Buttons, has been a sticky point with me from day one! Thanks for this. This should be in the repository and installable through Add/Remove (didn't read all 11 pages, not sure if this has been said or not)

---

### Post by Bashed on 2007-05-10
> **Condoulo said:**
> Wow. I should really do that so the widgets go along with my theme.


Have you tried this yet? can you please provide screenshots and possibly upload the files (images)? Thanks

---

### Post by Iokua on 2007-05-13
This is an awesome fix! It looks great! Thanks! :)

Although I think the check boxes themselves would look better if they were rendered the same way as form field. On my machine, check boxes look pretty bad. I can only see the left and top borders.

---

### Post by Twizz on 2007-05-14
I think the Check boxes are done that way to make it look more 3D?  Although all around would look good to.

---

### Post by limaunion on 2007-05-14
Awesome! I hope to see this included by default in the next Ubuntu release.
Thank you!

---

### Post by MetaMorfoziS on 2007-05-18
Hey!
Thank you for this! It solves some problems that i have my previous widget set ("pretty widgets") and it looks elegant (but a little gnomeish).

I updated my related topic: [http://ubuntuforums.org/showthread.php?t=336181&highlight=kgtk](http://ubuntuforums.org/showthread.php?t=336181&highlight=kgtk)

So again, thx!:)

---

### Post by MetaMorfoziS on 2007-05-22
Hey!
I have found a bug in this stuff.
Check my attachment (from asus wifi router config)

I also solved that, so add this two lines:

```
background-repeat:no-repeat !important;
background-position: center center !important;
```

to the forms.css input[type="radio"] block near line 571.

Peace!

---

### Post by HaxTbh on 2007-05-22
Pro, Cheers

---

### Post by icechen1 on 2007-05-26
Great tips!I finally gotten rid of those ugly buttons!

---

### Post by ravenus on 2007-05-27
Just installed this and it seems to work fine. Thanks a lot for this beautifier :)

---

### Post by cornelius2 on 2007-05-27
Thanks for the widgets fatsheep. It looks nicer than the defaults.

However you are lacking a "pressed" (active) state for the buttons. Here is a patch that adds this, together with a more pronounced button image (+ the active version).

---

### Post by gggggdxn on 2007-05-27
It's great! But how about put these files in ~/.mozilla/firefox instead of /usr/lib/firefox? Then we wouldn't have to repeat those operations when firefox updates in the future :)

---

### Post by jaywee on 2007-05-27
Great script!!thanks!!

---

### Post by Callandor64 on 2007-05-27
Worked great here (Feisty x86)

Cheers for your work,

Callandor64

---

### Post by Landser on 2007-05-27
I made a small deb package for easy installation/removal (attached)

---

### Post by kwaanens on 2007-05-27
Link leads to a 404.

---

### Post by kwaanens on 2007-05-27
Tried the package in the first post, and see no difference :(

- K

---

### Post by Landser on 2007-05-27
> **kwaanens said:**
> Link leads to a 404.

Yeah, sorry, I added it as an attachment to my previous post now.

---

### Post by schmappel on 2007-05-27
Works great, thanks a bunch! You know, there are more useful scripts like this one out there (like the 'Take back the Firefox & Thunderbird logo' script for example), it would be great if they were all combined somehow, wouldn't it? Or perhaps there should be some sort of Ubuntu Script Repository where these scripts could be maintained. Or perhaps I should just shut up and enjoy life :D

Thanks again!

---

### Post by kwaanens on 2007-05-28
> **kwaanens said:**
> Tried the package in the first post, and see no difference :(

- K

Nevermind, I ./install -r and then installed again, and now it works. Looks great!
This should be put in official Ubuntu repos. Maybe the artwork team should handle it?

- Ketil

---

### Post by ubersoldat on 2007-05-28
Very nice, didn't know you could do this with firefox. Very nice. Thanks!

---

### Post by TimJBart on 2007-05-28
sweet mother!!   this has made web browsing in firefox beautiful.  Thank you very much :D

Out of interest, why are the old ones so cruddy?  Can this be addressed in the next version of ubuntu or is it a firefox problem?

---

### Post by hmsf on 2007-05-29
I think it's more a Firefox problem.

BTW, I've just installed the widget, it's perfect! It was one of the few appearance things that used to annoy me when I switched to Ubuntu, together with the bad font rendering, which I found the solution in this forum... Now only OpenOffice needs a better rendering...

---

### Post by ghislain2 on 2007-05-31
Looks very prettier like this. Thanks !

---

### Post by babozor on 2007-05-31
Nice... work perfectly
Really nice
(btw i got the link from here: [http://www.chevrel.org/fr/carnet/index.php?2007/05/30/663-des-beaux-formulaires-dans-firefox-pour-ubuntu]("http://www.chevrel.org/fr/carnet/index.php?2007/05/30/663-des-beaux-formulaires-dans-firefox-pour-ubuntu"))

---

### Post by canen on 2007-05-31
I didn't read the entire thread so this may have already been covered.

There is a permission issue with the images. Using Kubuntu/Feisty here. After installation the files are not readable by regular users. This can be fixed by doing the following:

```
sudo chmod 755 -R /usr/lib/firefox/res/form-widgets/
```

I think this can also be achieved by adding the following line to the install script (not tested):

```
sudo chmod 755 -R "$destdir/res/form-widgets/"
```

Add it after this line:
```

sudo cp -r form-widgets "$destdir/res"

```

---

### Post by oCfuu on 2007-05-31
I like! Not a lot to say, but it works and it works oh so well. Thanks to the author for making this wonderful widget and thanks to Lifehacker for posting this!

---

### Post by dbrummer on 2007-05-31
Installation and appearance are smooth!  Great job.

-Dan

---

### Post by ricardovich on 2007-05-31
Works great

---

### Post by Samjiman on 2007-05-31
I'm using Iceweasel. I have tried installing to /usr/lib/iceweasel/res, but no changes are made.
Which directory do I need to install to?

Thanks.

---

### Post by tycjan on 2007-05-31
Nice :) This works! THX

---

### Post by lollikerwin on 2007-05-31
Found this via lifehacker.com...  Beautiful!!  :KS  Thank you!

---

### Post by Ghostlove on 2007-05-31
This works great. The only issue I have with it is that it changes deviantART's search button. :/

---

### Post by maique on 2007-05-31
also found this via lifehacker, installed and firefox looks much nicer now.

i'm a newbie at this linux stuff and proud to have used a ./install for the first time... :D

---

### Post by mydrac on 2007-05-31
Hello: 
Thanks for this it's work perfect.
lifehacker  too.

---

### Post by yamokojc on 2007-05-31
One of my biggest disappointments with firefox on ubuntu was that the buttons looked like crapola. Now that is fixed...everything looks great now!

=D>

---

### Post by rookieone on 2007-05-31
works like a charm and looks good too, thanks

---

### Post by mattdee on 2007-05-31
AWESOME!!!

Very nice and polished!!!

---

### Post by PendragonUK on 2007-05-31
Very nice, works a tread :)

---

### Post by revchris on 2007-05-31
Works Great!

---

### Post by geokker on 2007-05-31
Excellent! Well done. The ugly widgets have bugged me for ages.

---

### Post by zerwas on 2007-05-31
This doesn't work with Epiphany. Has anybody an idea how i could make it more beautiful in epiphany?

Regards,
zerwas

---

### Post by jmcantrell on 2007-05-31
It looks cool, but i'm seeing some strange overlapping and odd sizing of buttons and textboxes.

---

### Post by jro on 2007-05-31
They look great! Its subtle, but really finished off the look for the browser. Thanks for taking the time to bundle these and create the installer. Your work is appreciated.

---

### Post by werewolves on 2007-05-31
Looks awesome and works great on Xubuntu Fiesty!

---

### Post by DeaconSune on 2007-06-01
ok, congratulations, I have been running ubuntu for 1 day now, and i ran it fine.  I have no idea what i was doing, but it worked.  thanks for making fireforks look prettier

---

### Post by dliberal on 2007-06-01
It works nice!

Firefox looks much better now!

Thanks!

---

### Post by Zamber on 2007-06-01
Hi there ;]
I have a dark theme (ubuntu studio) and the Go button on the ubuntu forums has a dark frame. Look: [http://img241.imageshack.us/img241/6370/200706011005531280x1024sn6.png](http://img241.imageshack.us/img241/6370/200706011005531280x1024sn6.png)
Is it my fault?

---

### Post by hoagie on 2007-06-01
It works !!!:popcorn:

---

### Post by AntiBodies on 2007-06-01
Triple Sweet!!!

Worked great from what I can see.. Although I do notice that it applies the border to the "Go" button on the search for Ubuntu Forums.. as the button already has a style already applied to it it looks a bit funny but hey....

This should be installed as the default for any Firefox installation.. is so much more pretty.

Installation was fine though and I didnt have a problem.

Cheers,

AntiBodies

---

### Post by thejart on 2007-06-01
i also found this via lifehacker...and it works great for me.  thanks!

---

### Post by nyex on 2007-06-01
hip!
this is lovely!
and considering the only page I really care for is gmail, it couldn't be any better.

thanks a lot for this.

---

### Post by zerwas on 2007-06-01
I have a little problem with some webpages.

The text doesn't fit in the text boxes:

---

### Post by icallshogun on 2007-06-01
I saw this over on lifehacker... Very nice upgrade to the visuals in FF.

---

### Post by milouse1664 on 2007-06-01
It works very fine with swiftfox... As we say in France, it's realy change our lives ^^
Thanxx

---

### Post by angrykeyboarder on 2007-06-02
> **userundefine said:**
> And for KDE:



[credit]("http://ubuntuforums.org/showthread.php?t=336181&highlight=kgtk")

This rocks. Heck, I think it looks even better than the Osmo's (GNOME, KDE or otherwise). :)

[IMG]http://img.photobucket.com/albums/v208/meloncholyman/Screen%20Shots/widgets.png[/IMG]

---

### Post by t1pt2p on 2007-06-02
It just works perfectly. Thanks

---

### Post by ukripper on 2007-06-02
Worked like charm. Firefox looks much better than even any other browser. Thanks for script mate

cheers

---

### Post by psyopper on 2007-06-02
FYI - 

Apparently upgrading Firefox will require you to reinstall this little charm. It's a wonderful thing that will remind you just how wonderful it is every few months...

---

### Post by ukripper on 2007-06-02
> **psyopper said:**
> FYI - 

Apparently upgrading Firefox will require you to reinstall this little charm. It's a wonderful thing that will remind you just how wonderful it is every few months...

Dont worry about that I will write script which will re-install these widgets after if/have to update firefox down the line until then it is charming.

---

### Post by xcorex on 2007-06-02
congratz. i was looking for that!
thank u

---

### Post by shashipr on 2007-06-02
Perfect!! Exactly what I was looking for. Thanks for your efforts

---

### Post by Xpf on 2007-06-03
Muito bom funcionou direitinho aquí, Obrigado.

---

### Post by eilu on 2007-06-03
works perfectly! thanks!

---

### Post by Green_Star on 2007-06-03
This works like a champ, Thank you very much for providing this wonderful program to us.

---

### Post by Vindemiatrix on 2007-06-03
I found a little visual bug, who appear which the mouse is pressed. The radio button, then, leave to be transparent which the mouse is still pressed, turning back to normal, transparent, after release them.

My solution was add (or change in some cases) the css rule for all selectors for input[type="radio"] with the folowing statement: background-color: transparent;

This resolves the problem with transparency.

PS: Sorry for my bad english, I don't have good speech on this language.

---

### Post by ukripper on 2007-06-03
just installed swiftfox for fast performance even on swiftfox it worked like breeze.

---

### Post by rakup on 2007-06-03
thanks a lot, i was wondering why FF on linux so ugly is. good job.

---

### Post by kigol on 2007-06-03
installed and looking great in Fedora 6.

tks

---

### Post by gotmonkey on 2007-06-03
i didn't realize how cheap the google homepage looked until I ran this script. 

Thanks!

---

### Post by LKRaider on 2007-06-04
I created a GTK+ interface for the installer, check the attached screenshots.

It's written in Python, and requires the **python-kiwi** lib to be installed to work. The code is attached too. I had to edit your install script a bit to not ask for a key press on the automated install. The diff is attached aswell.

:popcorn:

---

### Post by Catsworth on 2007-06-04
Script works great, bloody FireFox trashes all your hard work when you upgrade though!!

Just downloaded the latest upgrade to FF as prompted by Ubuntu, and now I'm back to ugly FF hell!!

---

### Post by Catsworth on 2007-06-04
And there's the reason that I often find myself so frustrated with Ubuntu.

The last time I ran this script the installation directory was /opt/firefox/, this time it's /usr/share/firefox/.

Upgrading firefox has changed the damn installation directory!

---

### Post by Abdelmalek on 2007-06-04
Nice look but it has compatibility problems with ExtJS javascript library.

The library first try to render nice buttons then your buttons are added on top.

Try any demo on [http://www.extjs.com/deploy/ext/docs/index.html](http://www.extjs.com/deploy/ext/docs/index.html) to see what I mean.

---

### Post by danzk on 2007-06-05
I've updated firefox and everything is messed up how can i remove it

---

### Post by ukripper on 2007-06-05
> **danzk said:**
> I've updated firefox and everything is messed up how can i remove it

What you want to remove Firefox or Widgets? Not sure what you mean by 'Everything' here

You can still install widgets after updated firefox by using same method. just make sure where is the new updated Firefox in /usr or /opt and then install the widgets accordingly.

---

### Post by Catsworth on 2007-06-05
See my post a little way up the board.  I had the same problem and had to reinstall the widgets.

---

### Post by xncramar on 2007-06-06
Works perfectly under the current version of Gutsy Gibbon too. Great work! Thanks! :popcorn:

---

### Post by Programmerfromthehood on 2007-06-06
How do you use these for swiftfox?

---

### Post by camtech on 2007-06-06
Brilliant! :D

---

### Post by ukripper on 2007-06-07
> **Programmerfromthehood said:**
> How do you use these for swiftfox?

In similiar way you use it for firefox just make sure where swiftfox gets installed (normally /opt/swiftfox) and simply change the path for widgets while installing.

---

### Post by Jedi Penguin on 2007-06-07
I've noticed this widget fix erases the blacktheme text/background fix in firefox for gnome from here: [http://www.gnome-look.org/content/show.php/Neutronium-Midnight?content=57255](http://www.gnome-look.org/content/show.php/Neutronium-Midnight?content=57255)

---

### Post by s4lv1n0 on 2007-06-07
Perfect.
Congratulations and thank you so much, really nice work.

---

### Post by fatsheep on 2007-06-07
> **Abdelmalek said:**
> Nice look but it has compatibility problems with ExtJS javascript library.

The library first try to render nice buttons then your buttons are added on top.

Try any demo on [http://www.extjs.com/deploy/ext/docs/index.html](http://www.extjs.com/deploy/ext/docs/index.html) to see what I mean.

> **Jedi Penguin said:**
> I've noticed this widget fix erases the blacktheme text/background fix in firefox for gnome from here: [http://www.gnome-look.org/content/show.php/Neutronium-Midnight?content=57255](http://www.gnome-look.org/content/show.php/Neutronium-Midnight?content=57255)


Thanks for both of these bug reports.  I don't know if I'll be able to fix them but I will try.  I'm going to remove more of the !important statements in the CSS and see if that helps.

---

### Post by Dread Knight on 2007-06-07
The changes i've seen in the first post are awsome! Will try this soon!

Keep up the good work! :)

---

### Post by derapao on 2007-06-08
this is great!
have you considered submitting the patch to mozilla? this should become the default appearance of firefox.
thank you for you work.

alessandro

---

### Post by sweetthdevil on 2007-06-08
fantastic looking much better, many thanks!!

---

### Post by rockallite on 2007-06-08
Very nice widgets at a first glance. However, something doesn't look good even in this very forum ;)

Please have a look at the screenshot I uploaded, which shows the Go button surrounded by an unexpected border.

---

### Post by uthturn on 2007-06-08
Ok I know this is a stupid question but I downloaded the file into my home directory what do i do next i have no clue. Sorry for such a noobish question

---

### Post by fatsheep on 2007-06-08
> **rockallite said:**
> Very nice widgets at a first glance. However, something doesn't look good even in this very forum ;)

Please have a look at the screenshot I uploaded, which shows the Go button surrounded by an unexpected border.

 I fixed that bug in 1.1.  Make sure you are using the newest version (1.1).  You'll probably have to download the new version, remove the widgets and then install the widgets again.

---

### Post by fatsheep on 2007-06-08
I have just added two revisions:

**1.2** (June 8th 2007) - FIxes a bug that distorted buttons on this website: [http://www.extjs.com/deploy/ext/docs/index.html](http://www.extjs.com/deploy/ext/docs/index.html).
_[COLOR="Red"]**1.5 BETA** [/COLOR]_- All past bug fixes have been made by removal of specific !important statements in the CSS that overrode web page defaults. In this **BETA** I have removed all !important statements in the CSS.  Please report any problems



> **LKRaider said:**
> I created a GTK+ interface for the installer, check the attached screenshots.

It's written in Python, and requires the **python-kiwi** lib to be installed to work. The code is attached too. I had to edit your install script a bit to not ask for a key press on the automated install. The diff is attached aswell.

:popcorn:

:o I completely missed your post.  This should make a great addition to the installer.  Thanks for your contribution, I'll look into incorporating it into the next revision(s).

> **zerwas said:**
> I have a little problem with some webpages.

The text doesn't fit in the text boxes:

What version of the widgets are you using?  If you are using 1.1 or earlier, try the newer 1.2 and 1.5 (beta) revisions to see if this problem has already been fixed.  If not, please provide a link to one of these web pages and as much information as possible.

> **Abdelmalek said:**
> Nice look but it has compatibility problems with ExtJS javascript library.

The library first try to render nice buttons then your buttons are added on top.

Try any demo on [http://www.extjs.com/deploy/ext/docs/index.html](http://www.extjs.com/deploy/ext/docs/index.html) to see what I mean.

Look at the main post, I have just added the **1.2** revision which has fixed the problems I saw on the website you linked to.  Please let me know if there are still any problems.

> **Jedi Penguin said:**
> I've noticed this widget fix erases the blacktheme text/background fix in firefox for gnome from here: [http://www.gnome-look.org/content/show.php/Neutronium-Midnight?content=57255](http://www.gnome-look.org/content/show.php/Neutronium-Midnight?content=57255)

I've downloaded the theme but I don't understand what you mean by the blacktheme text/background fix.  Please clarify.  Thanks.

---

### Post by reclusivemonkey on 2007-06-09
Just installed the BETA version; I seem to have corrupted radio buttons on all websites, as well as corrupted tick boxes.

---

### Post by conjur3r on 2007-06-09
Thanks for your hardwork on beautifying the fox on *nix.

I can confirm ugly radio and checkboxes using the 1.5beta version.

---

### Post by shen-an-doah on 2007-06-09
Yeh, I got the same with radio buttons and checkboxes.

---

### Post by BlackSkad on 2007-06-09
I can confirm them too. It's fixed by replacing "border: none" with "border: none !important" to the css for the radio-buttons and "border-width: 0;" to "border-width: 0 !important;" for the checkboxes.
I also removed the margin and padding from the types text and password, as it messed up some layouts (including the search-box in the top-right corner of [http://tweakers.net](http://tweakers.net) )
I tried to create a patch. It was the first time I created one, so I hope I did it right :) It has to be applied to forms-extra.css

Thank you very much for the beautification, it looks way better then the default :)

---

### Post by fatsheep on 2007-06-09
Thanks for the fast bug reports everyone, 1.6 BETA is available for download in the main post and it features a graphic installer as well as the fixes for the above reported bugs.

> **BlackSkad said:**
> I can confirm them too. It's fixed by replacing "border: none" with "border: none !important" to the css for the radio-buttons and "border-width: 0;" to "border-width: 0 !important;" for the checkboxes.
I also removed the margin and padding from the types text and password, as it messed up some layouts (including the search-box in the top-right corner of [http://tweakers.net](http://tweakers.net) )
I tried to create a patch. It was the first time I created one, so I hope I did it right :) It has to be applied to forms-extra.css

Thank you very much for the beautification, it looks way better then the default :)

Thanks, I looked at that web page as well as gmail and it's settings pages and through some experimentation I think I arrived with about the same solution that you did, it's in the 1.6 BETA.  I'm going to check out your diff file now.

EDIT: I have a few less !important statements on the radio buttons but from what I've seen it still corrects the problem.  If there are any more problems, link me to the site and I'll try to patch it.

---

### Post by Dark Seraphim on 2007-06-09
man I have been lookin for somethin like this for so long. thank you for this its awesome and works well on all the sites I go to and on my router. no longer have to look at those old dodgy circles and boxes got these kick *** new ones. I was wondering if I made my own and replaced the ones in the folder would they show up instead. im tryin to get the ones from vista, they look pretty nice.

---

### Post by fatsheep on 2007-06-09
> **Dark Seraphim said:**
> man I have been lookin for somethin like this for so long. thank you for this its awesome and works well on all the sites I go to and on my router. no longer have to look at those old dodgy circles and boxes got these kick *** new ones. I was wondering if I made my own and replaced the ones in the folder would they show up instead. im tryin to get the ones from vista, they look pretty nice.

Yea sure go ahead and try it, make sure to post some screenshots to! ;)

---

### Post by conjur3r on 2007-06-09
Confirmed: checkboxes and radios are pretty in 1.7beta

Just a question, are buttons supposed to expand left and right after clicking them?  You can view the differences by clicking and holding on a button.

I've disabled this behaviour by commenting out the following line under the 

[B]input[type="button"],
input[type="submit"],
input[type="reset"],
button,
select {[/B]

selector

```
padding: 0px 1px;
```

---

### Post by Mr.mouse on 2007-06-10
can you create the same button as the Ubuntu default human theme ?


thanks

---

### Post by fatsheep on 2007-06-10
> **conjur3r said:**
> Confirmed: checkboxes and radios are pretty in 1.7beta

Just a question, are buttons supposed to expand left and right after clicking them?  You can view the differences by clicking and holding on a button.

I've disabled this behaviour by commenting out the following line under the 

[B]input[type="button"],
input[type="submit"],
input[type="reset"],
button,
select {[/B]

selector

```
padding: 0px 1px;
```

Nope that's a bug, thanks for the report - it is fixed in 1.8 BETA.


> **Mr.mouse said:**
> can you create the same button as the Ubuntu default human theme ?


thanks

If you make images that look like the human theme then yea you probably could do something similar.

---

### Post by rockallite on 2007-06-11
Great improvement since v1.1!

Confirmed a bug of the position of text input widgets in v1.8. 
Screenshots uploaded. ([http://mp3.baidu.com]("http://mp3.baidu.com"))
As far as I remember, this bug didn't exist in earlier versions. (~1.1, maybe?)

---

### Post by mystery on 2007-06-11
> **fatsheep said:**
> I hate to be the one bumping my own topic but I'd really appreciate some feedback.  Of the 43 of you who downloaded the attachment so far, what did you think?  Did it work well for you?

They look great thank you.  If using the latest downloaded version of Firefox 2.0.0.4 just need to change /usr/lib/firefox to /opt/firefox in the commands you have kindly listed.:D

---

### Post by martinarg on 2007-06-11
Install worked fine with the graphic installer and the widget just looks great, and since I use gmail on a daily basis it really changed the looks of my day to day home page.
Great work!

---

### Post by fatsheep on 2007-06-11
> **rockallite said:**
> Great improvement since v1.1!

Confirmed a bug of the position of text input widgets in v1.8. 
Screenshots uploaded. ([http://mp3.baidu.com]("http://mp3.baidu.com"))
As far as I remember, this bug didn't exist in earlier versions. (~1.1, maybe?)

Thanks.  What exactly is the problem?  Are you talking about how the button is higher then the text input?

---

### Post by kknd on 2007-06-11
Great!!!

---

### Post by rockallite on 2007-06-12
> **fatsheep said:**
> Thanks.  What exactly is the problem?  Are you talking about how the button is higher then the text input?

Actually, the button is in the correct position, while the text input seems to be vertically lower than the normal one. Maybe there's a redundant margin at the top of text input?

Since I'm not familiar with programming, I'm able to provide visual information only. :( If there's anything I can help to test or debug this, please do give me instructions. I can't wait to see perfect Firefox widgets!

(Edited: correct some typos.)

---

### Post by rockallite on 2007-06-12
Please take a look at the attached screenshots. There seems to be a redundant margin at the bottom of the button this time, making it higher than the original...I'm really confused now.

---

### Post by rockallite on 2007-06-12
In order to make everything clear, I did an experiment.

[SIZE="3"]**First, a web page for testing:**[/SIZE]
[HTML]<html>
<body bgcolor="orange">
<input type="text" value="fatsheep" 
  style="position:absolute; top:0px; left:0px; width:75px; "/>
<input type="button" value="rocks" 
  style="position:absolute; top:0px; left:75px; width:75px; " />
</body>
</html>[/HTML]

[SIZE="3"]**Test #1, page rendering without the widget patch:**[/SIZE] (unnecessary edges are cut off for clarity)
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=35150&stc=1&d=1181675172[/IMG]

[SIZE="3"]**Test #2, page rendering with the widget patch applied:**[/SIZE]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=35151&stc=1&d=1181675172[/IMG]

[SIZE="3"]**Result:**[/SIZE]
(Since I use absolute positioning, the data should be isolated for each widget.)
```
Normal: (test #1) 
	text input	button
top	0px		0px
left	0px		75px
width	75px		75px
height	23px		23px

Patched: (test #2)
	text input	button
top	0px		2px
left	0px		77px
width	75px		75px
height	21px		23px

```

[SIZE="3"]**Conclusion:**[/SIZE]
After the patch being applied,
1. the text input remained the same position, but shrunk by 2px in height.
2. the button remained the same size, but moved by 2px downward and right.
3. fatsheep rocks! Need to keep on your good job, though...:p

---

### Post by fatsheep on 2007-06-12
> **rockallite said:**
> In order to make everything clear, I did an experiment.

[SIZE="3"]**First, a web page for testing:**[/SIZE]
[HTML]<html>
<body bgcolor="orange">
<input type="text" value="fatsheep" 
  style="position:absolute; top:0px; left:0px; width:75px; "/>
<input type="button" value="rocks" 
  style="position:absolute; top:0px; left:75px; width:75px; " />
</body>
</html>[/HTML]

[SIZE="3"]**Test #1, page rendering without the widget patch:**[/SIZE] (unnecessary edges are cut off for clarity)
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=35150&stc=1&d=1181675172[/IMG]

[SIZE="3"]**Test #2, page rendering with the widget patch applied:**[/SIZE]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=35151&stc=1&d=1181675172[/IMG]

[SIZE="3"]**Result:**[/SIZE]
(Since I use absolute positioning, the data should be isolated for each widget.)
```
Normal: (test #1) 
	text input	button
top	0px		0px
left	0px		75px
width	75px		75px
height	23px		23px

Patched: (test #2)
	text input	button
top	0px		2px
left	0px		77px
width	75px		75px
height	21px		23px

```

[SIZE="3"]**Conclusion:**[/SIZE]
After the patch being applied,
1. the text input remained the same position, but shrunk by 2px in height.
2. the button remained the same size, but moved by 2px downward and right.
3. fatsheep rocks! Need to keep on your good job, though...:p

Alright, thanks for that.  I'll take a look next time I get a chance.

---

### Post by grickaby on 2007-06-12
Freakin' Sweet!

Easy to install (Just double clicked "Graphic Install" and it just worked. This is why I love UBUNTU!

---

### Post by pirothezero on 2007-06-13
Works great have loved it since it came out. Sorry I didn't post earlier.

---

### Post by nchase on 2007-06-13
I just installed the latest version. It fixes a bug that I had noticed in version 1.1. Thank you for this wonderful thing.

---

### Post by LiamPreston on 2007-06-13
It works very well for me - not the most adept of Linux newbies. It certainly is an improvement. Thank you very much.

---

### Post by nosuchuser on 2007-06-13
Thanks! A million thanks!

However...

There is no package called python-kiwi in 6.06, which I'm using. It's called kiwi, so perhaps you should look for the ubuntu distro variant and change the scripts according to that (that only happens in the graphical installer, the text installer did it right once I installed kiwi.

---

### Post by Rui Pais on 2007-06-13
hi,
just to say that the graphical installer worked here with swiftweasel either on Feisty32b as on Feisty64b.

Good work :)

---

### Post by fatsheep on 2007-06-13
Thanks for the comments everyone!


> **rockallite said:**
> In order to make everything clear, I did an experiment.

[SIZE="3"]**First, a web page for testing:**[/SIZE]
[HTML]<html>
<body bgcolor="orange">
<input type="text" value="fatsheep" 
  style="position:absolute; top:0px; left:0px; width:75px; "/>
<input type="button" value="rocks" 
  style="position:absolute; top:0px; left:75px; width:75px; " />
</body>
</html>[/HTML]

[SIZE="3"]**Test #1, page rendering without the widget patch:**[/SIZE] (unnecessary edges are cut off for clarity)
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=35150&stc=1&d=1181675172[/IMG]

[SIZE="3"]**Test #2, page rendering with the widget patch applied:**[/SIZE]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=35151&stc=1&d=1181675172[/IMG]

[SIZE="3"]**Result:**[/SIZE]
(Since I use absolute positioning, the data should be isolated for each widget.)
```
Normal: (test #1) 
	text input	button
top	0px		0px
left	0px		75px
width	75px		75px
height	23px		23px

Patched: (test #2)
	text input	button
top	0px		2px
left	0px		77px
width	75px		75px
height	21px		23px

```

[SIZE="3"]**Conclusion:**[/SIZE]
After the patch being applied,
1. the text input remained the same position, but shrunk by 2px in height.
2. the button remained the same size, but moved by 2px downward and right.
3. fatsheep rocks! Need to keep on your good job, though...:p

Fixed in 1.9:

[img]http://img258.imageshack.us/img258/2804/fixedkf1.png[/img]

There was a 2 px margin applied to the Buttons, I just commented that out and there is no longer a problem.

> **nosuchuser said:**
> Thanks! A million thanks!

However...

There is no package called python-kiwi in 6.06, which I'm using. It's called kiwi, so perhaps you should look for the ubuntu distro variant and change the scripts according to that (that only happens in the graphical installer, the text installer did it right once I installed kiwi.

I added a note about this on the main post.

---

### Post by loserboy on 2007-06-13
hey, thanks for this... I never knew this even existed till i stumbled onto it in ubuntuguide.  Anyway I always knew there was something wrong with the widgets but couldnt figure it out... shows how observant I am.

could I suggest that you add a confirmation dialog when the script finishes installing, I ended up installing it like 3 times before i realized i just need to restart firefox.

btw 1.9 worked perfect for me thanks again

---

### Post by tombug on 2007-06-13
had this before used it for a day maybe, messes up some thing but now its all updated and works great:)
thanks for this great and very usefull

---

### Post by zero_2x on 2007-06-14
looks great, works better!! =)

Thanks men!!

---

### Post by sunexplodes on 2007-06-14
Yeah, kudos. Looks great.

---

### Post by fatsheep on 2007-06-14
> **loserboy said:**
> could I suggest that you add a confirmation dialog when the script finishes installing, I ended up installing it like 3 times before i realized i just need to restart firefox.



Done in 2.0.  Also, has python-kiwi been automatically installed for everyone?  There is an error in the script, it shouldn't work at all.  I've fixed that in 2.0 but I'm suprised no one mentioned that the graphic_install script didn't automatically install python-kiwi like it should.  (I used the dpkg -l option to test if python-kiwi was installed instead of the dpkg -L option)

---

### Post by loserboy on 2007-06-14
actually now that you mention the graphic installer didn't work for me, but I thought it was because I did something wrong and was busy trying to figure out if it was just an instant install, text based installer was super easy though

---

### Post by fatsheep on 2007-06-16
> **loserboy said:**
> actually now that you mention the graphic installer didn't work for me, but I thought it was because I did something wrong and was busy trying to figure out if it was just an instant install, text based installer was super easy though

Does the graphic installer work in 2.0 for you?

---

### Post by loserboy on 2007-06-16
I'll go go try and report back here in a minute

yep worked fine, not that it matters but you named the folder in the tarball 2.1 beta

---

### Post by rockallite on 2007-06-16
Excellent work on 2.0 beta!!

However, I highly recommend the patch introduced below, which is based on 2.0 beta. I'll show you some pictures.

[SIZE="4"]From Google Search:[/SIZE] 
([http://www.google.com/](http://www.google.com/))
[IMG]http://img167.imageshack.us/img167/6655/googlediffmy5.png[/IMG]

[SIZE="4"]From Gmail:[/SIZE] 
([http://mail.google.com/](http://mail.google.com/))
[IMG]http://img201.imageshack.us/img201/9955/gmaildiffiz0.png[/IMG]

[SIZE="4"]From Baidu MP3 Search:[/SIZE] 
([http://mp3.baidu.com/](http://mp3.baidu.com/))
[IMG]http://img201.imageshack.us/img201/1066/baidudiffkz6.png[/IMG]

With the patch applied, it makes the widgets look more similar to the original ones. 

[SIZE="4"]The real thing:[/SIZE]
Here's how I patched **form-extra.css**:
```

## It changes the border of text input widgets to 2px, and adds a 1px 3d inner border 
## for eye candy. Anyway, the original ones has a 2px border. We'd better follow that.
# line 5
/* Text inputs */

input[type=text],
input[type=password],
input:not([type]),
textarea {
  border: 2px solid ThreeDShadow;
[B]  -moz-border-top-colors: ThreeDShadow Window;
  -moz-border-right-colors: ThreeDShadow ThreeDHighlight;
  -moz-border-bottom-colors: ThreeDShadow ThreeDHighlight;
  -moz-border-left-colors: ThreeDShadow Window;
[/B]/*  margin: 2px;
  padding: 2px 0px; */
}


## Margins and paddings of dropdowns are removed. We should treat text inputs
## and dropdowns the same!
# line 98
/* Dropdowns  */

select,
select:not([size]),
select[size="0"],
select[size="1"] {
## ...other configurations omitted...
[B]/*  margin: 2px;
  padding: 0px 1px; */
[/B]  -moz-border-radius: 1px;
}

```

[SIZE="4"]Hey, that button is a bit higher![/SIZE]
You mean the patched version in the 3rd picture? That's true. But it's normal, even if the original version "appears" to be difference from that.

For fastidious users, please take a look at this:
[IMG]http://img201.imageshack.us/img201/4759/baidudiff2pz8.png[/IMG]

(1) shows the original version. It seems that the button are horizontally aligned with the text input. But, wait! 
(2) shows a darken version of (1) via GIMP. Notice that the button is ACTUALLY 1PX HIGHER than the text input. Don't fooled by the similar background color!
(3) shows the patched version. You'll see that it doesn't differ much from (2).

**Conclusion:**
The patched version is perfect. Well, nearly perfect.;)

---

### Post by fatsheep on 2007-06-16
> **rockallite said:**
> Excellent work on 2.0 beta!!

However, I highly recommend the patch introduced below, which is based on 2.0 beta. I'll show you some pictures. (log in to see them!)

[SIZE="4"]From Google Search:[/SIZE] 
([http://www.google.com/](http://www.google.com/))
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=35551&stc=1&d=1182009360[/IMG]

[SIZE="4"]From Gmail:[/SIZE] 
([http://mail.google.com/](http://mail.google.com/))
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=35552&stc=1&d=1182009575[/IMG]

[SIZE="4"]From Baidu MP3 Search:[/SIZE] 
([http://mp3.baidu.com/](http://mp3.baidu.com/))
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=35553&stc=1&d=1182009575[/IMG]

With the patch applied, it makes the widgets look more similar to the original ones. 

[SIZE="4"]The real thing:[/SIZE]
Here's how I patched **form-extra.css**:
```

## It changes the border of text input widgets to 2px, and adds a 1px 3d inner border 
## for eye candy. Anyway, the original ones has a 2px border. We'd better follow that.
# line 5
/* Text inputs */

input[type=text],
input[type=password],
input:not([type]),
textarea {
  border: 2px solid ThreeDShadow;
  -moz-border-top-colors: ThreeDShadow Window;
  -moz-border-right-colors: ThreeDShadow ThreeDHighlight;
  -moz-border-bottom-colors: ThreeDShadow ThreeDHighlight;
  -moz-border-left-colors: ThreeDShadow Window;
/*  margin: 2px;
  padding: 2px 0px; */
}


## Margins and paddings of dropdowns are removed. We should treat text inputs
## and dropdowns the same!
# line 98
/* Dropdowns  */

select,
select:not([size]),
select[size="0"],
select[size="1"] {
## ...other configurations omitted...
/*  margin: 2px;
  padding: 0px 1px; */
  -moz-border-radius: 1px;
}

```

[SIZE="4"]Hey, that button is a bit higher![/SIZE]
You mean the patched version in the 3rd picture? That's true. But it's normal, even if the original version "appears" to be difference from that.

For fastidious users, please take a look at this: (log in to see the picture)
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=35554&stc=1&d=1182011543[/IMG]

(1) shows the original version. It seems that the button are horizontally aligned with the text input. But, wait! 
(2) shows a darken version of (1) via GIMP. Notice that the button is ACTUALLY 1PX HIGHER than the text input. Don't fooled by the similar background color!
(3) shows the patched version. You'll see that it doesn't differ much from (2).

**Conclusion:**
The patched version is perfect. Well, nearly perfect.;)

Good work on the patch but I don't see any pictures.  Did you mean to attach a picture?

---

### Post by sd.chen on 2007-06-16
Beautiful! You should submit this to Mozilla...

---

### Post by conjur3r on 2007-06-16
I've noticed a minor rendering bug to radios and checkboxes.  When they have been specified a height or width that is greater than 13px or 12px (depending on if it's a radio or checkbox), you get repeating of the images.  Take a look at the picture.

This was caused by the following html/css:

[HTML]
<style type="text/css">
input {
	height: 1.5em;
	width: 1.5em;
}
</style>

<h1>radio</h1>
<input type="radio" name="blah" /> option 1<br />
<input type="radio" name="blah" /> option 2<br />
<input type="radio" name="blah" /> option 3

<h1>checkbox</h1>
<input type="checkbox" name="bleh" /> option 1<br />
<input type="checkbox" name="bleh" /> option 2<br />
<input type="checkbox" name="bleh" /> option 3
[/HTML]

To fix this problem, I've tried specifying **no-repeat** to the background-image commands for those form images but it didn't work too well.  So I ended up with a temporary fix of restricting the size of checkboxes and radios to 12px or 13px width and height (changes highlighted in bold):

```

input[type="radio"] {
  width: 13px [B]!important;
  height: 13px !important;[/B]
  background-image: url("form-widgets/radio.png");
  -moz-border-radius: 0;
  border: none !important;
  background-color: inherit;
}

...

input[type="checkbox"] {
  width: 12px **!important**;
  height: 12px **!important**;
  border-width: 0 !important;
  background-image: url("form-widgets/checkbox.png");
  background-color: -moz-Field;
}

```

Edit: I am using 2.0 beta

---

### Post by rockallite on 2007-06-17
> **fatsheep said:**
> Good work on the patch but I don't see any pictures.  Did you mean to attach a picture?

I'm sorry. Didn't know that images uploaded to ubuntuforums.org don't display via [img] tags. I've changed the image source to imageshack.us. It should be OK now.

Here's the link to my post, for convenience::-P
[http://ubuntuforums.org/showpost.php?p=2856079&postcount=235](http://ubuntuforums.org/showpost.php?p=2856079&postcount=235)

---

### Post by rockallite on 2007-06-17
> **conjur3r said:**
> I've noticed a minor rendering bug to radios and checkboxes.  When they have been specified a height or width that is greater than 13px or 12px (depending on if it's a radio or checkbox), you get repeating of the images.  Take a look at the picture.

...

Confirmed this bug in 2.0 beta from [http://imageshack.us](http://imageshack.us) ;)
A picture attached below:
[IMG]http://img72.imageshack.us/img72/8368/imageshackww7.png[/IMG]

However, I don't think it's a good idea to make widgets fixed in size. It would change the layout of web pages, thus violate (Mozilla) browser standard.

---

### Post by mostwanted on 2007-06-17
It's not working for me. My Firefox does live in /usr/lib/firefox and the post-install notice says it installs correctly. I've restarted Firefox, but still get the old square widgets so what am I doing wrong?

---

### Post by peppy.ch on 2007-06-17
work's and looks great 
thanks

---

### Post by fatsheep on 2007-06-17
> **conjur3r said:**
> I've noticed a minor rendering bug to radios and checkboxes.  When they have been specified a height or width that is greater than 13px or 12px (depending on if it's a radio or checkbox), you get repeating of the images.  Take a look at the picture.

This was caused by the following html/css:

[HTML]
<style type="text/css">
input {
	height: 1.5em;
	width: 1.5em;
}
</style>

<h1>radio</h1>
<input type="radio" name="blah" /> option 1<br />
<input type="radio" name="blah" /> option 2<br />
<input type="radio" name="blah" /> option 3

<h1>checkbox</h1>
<input type="checkbox" name="bleh" /> option 1<br />
<input type="checkbox" name="bleh" /> option 2<br />
<input type="checkbox" name="bleh" /> option 3
[/HTML]

To fix this problem, I've tried specifying **no-repeat** to the background-image commands for those form images but it didn't work too well.  So I ended up with a temporary fix of restricting the size of checkboxes and radios to 12px or 13px width and height (changes highlighted in bold):

```

input[type="radio"] {
  width: 13px [B]!important;
  height: 13px !important;[/B]
  background-image: url("form-widgets/radio.png");
  -moz-border-radius: 0;
  border: none !important;
  background-color: inherit;
}

...

input[type="checkbox"] {
  width: 12px **!important**;
  height: 12px **!important**;
  border-width: 0 !important;
  background-image: url("form-widgets/checkbox.png");
  background-color: -moz-Field;
}

```

Edit: I am using 2.0 beta

Could you provide links to web pages where this bug occurs?  I do see it in your html but I haven't seen it on an actual web site.

> **rockallite said:**
> Excellent work on 2.0 beta!!

However, I highly recommend the patch introduced below, which is based on 2.0 beta. I'll show you some pictures.

[SIZE="4"]From Google Search:[/SIZE] 
([http://www.google.com/](http://www.google.com/))
[IMG]http://img167.imageshack.us/img167/6655/googlediffmy5.png[/IMG]

[SIZE="4"]From Gmail:[/SIZE] 
([http://mail.google.com/](http://mail.google.com/))
[IMG]http://img201.imageshack.us/img201/9955/gmaildiffiz0.png[/IMG]

[SIZE="4"]From Baidu MP3 Search:[/SIZE] 
([http://mp3.baidu.com/](http://mp3.baidu.com/))
[IMG]http://img201.imageshack.us/img201/1066/baidudiffkz6.png[/IMG]

With the patch applied, it makes the widgets look more similar to the original ones. 

[SIZE="4"]The real thing:[/SIZE]
Here's how I patched **form-extra.css**:
```

## It changes the border of text input widgets to 2px, and adds a 1px 3d inner border 
## for eye candy. Anyway, the original ones has a 2px border. We'd better follow that.
# line 5
/* Text inputs */

input[type=text],
input[type=password],
input:not([type]),
textarea {
  border: 2px solid ThreeDShadow;
[B]  -moz-border-top-colors: ThreeDShadow Window;
  -moz-border-right-colors: ThreeDShadow ThreeDHighlight;
  -moz-border-bottom-colors: ThreeDShadow ThreeDHighlight;
  -moz-border-left-colors: ThreeDShadow Window;
[/B]/*  margin: 2px;
  padding: 2px 0px; */
}


## Margins and paddings of dropdowns are removed. We should treat text inputs
## and dropdowns the same!
# line 98
/* Dropdowns  */

select,
select:not([size]),
select[size="0"],
select[size="1"] {
## ...other configurations omitted...
[B]/*  margin: 2px;
  padding: 0px 1px; */
[/B]  -moz-border-radius: 1px;
}

```

[SIZE="4"]Hey, that button is a bit higher![/SIZE]
You mean the patched version in the 3rd picture? That's true. But it's normal, even if the original version "appears" to be difference from that.

For fastidious users, please take a look at this:
[IMG]http://img201.imageshack.us/img201/4759/baidudiff2pz8.png[/IMG]

(1) shows the original version. It seems that the button are horizontally aligned with the text input. But, wait! 
(2) shows a darken version of (1) via GIMP. Notice that the button is ACTUALLY 1PX HIGHER than the text input. Don't fooled by the similar background color!
(3) shows the patched version. You'll see that it doesn't differ much from (2).

**Conclusion:**
The patched version is perfect. Well, nearly perfect.;)

Added in 2.1, thanks for the bug report. :)

---

### Post by fortunecookie289 on 2007-06-17
Installing this changed my default firefox font, although it still shows the same default font under preferences. 
I tried uninstalling, and the font change remained. 
Any way this could be fixed without me having to revert to an earlier backup of my system? Forgive me if this was already answered (I did a search through the thread and didn't come up with anything)

---

### Post by DjBones on 2007-06-17
great work! i had to change the path because i use swiftfox, but it worked like a charm
:popcorn:

---

### Post by fatsheep on 2007-06-18
> **fortunecookie289 said:**
> Installing this changed my default firefox font, although it still shows the same default font under preferences. 
I tried uninstalling, and the font change remained. 
Any way this could be fixed without me having to revert to an earlier backup of my system? Forgive me if this was already answered (I did a search through the thread and didn't come up with anything)

I'm really not sure how that could happen?  What was your default font and what is it now?

---

### Post by conjur3r on 2007-06-18
> **fatsheep said:**
> Could you provide links to web pages where this bug occurs?  I do see it in your html but I haven't seen it on an actual web site.

[http://govsearch.publications.gov.au/search/search.cgi?collection=pubs&chksummary=chksummary&fscope=512&form=simple&fqp=1&query=book](http://govsearch.publications.gov.au/search/search.cgi?collection=pubs&chksummary=chksummary&fscope=512&form=simple&fqp=1&query=book)

I played around with **no-repeat** and got it to work but there's white rounded areas filling up the missing gaps.  Maybe when the height/width is larger than the image, the image should be recentred (if possible)?

---

### Post by Surkow on 2007-06-18
[IMG]http://img508.imageshack.us/img508/1180/phpbbbulletuv9.png[/IMG]

Currently my profile in phpBB 2.0 looks like this at the section where you can specifiy your gender.

Part of the code:

```
<tr>
      <td class="row1"><span class="gen">Gender:</span></td>
      <td class="row2">
      <input disabled="disabled" name="gender" value="0" type="radio">
      <span class="gen">None Specified</span>&nbsp;&nbsp;
      <input name="gender" value="1" checked="checked" type="radio">
      <span class="gen">Male</span>&nbsp;&nbsp;

      <input name="gender" value="2" type="radio">
      <span class="gen">Female</span></td>
</tr>
```

As you can see the bullet is disabled and suffers from a render error.

---

### Post by fortunecookie289 on 2007-06-18
> **fatsheep said:**
> I'm really not sure how that could happen?  What was your default font and what is it now?

My default font was serif, and my preferences still show it as being serif, but it looks more like.... arial? sorry I'm bad at identifying fonts.
But the font change was the first thing I noticed after restarting firefox after my install.

---

### Post by fatsheep on 2007-06-18
> **mostwanted said:**
> It's not working for me. My Firefox does live in /usr/lib/firefox and the post-install notice says it installs correctly. I've restarted Firefox, but still get the old square widgets so what am I doing wrong?

Sorry missed this post.  First off, make sure you are closing out ALL firefox windows and then restarting firefox.  I've left a download window open before and thought that the script wasn't working but I actually just hadn't closed everything out.  Second off, make sure you are executing the firefox at /usr/lib/firefox.  Go to the terminal and type: > /usr/lib/firefox/firefox

Also you could try manually inspecting the end of the forms.css file: > gedit /usr/lib/firefox/res/forms.css

Look for a big commented section that looks like:

> /******* BEGIN EXTRA FIREFOX WIDGETS *****/

And a respective:

> /******** END EXTRA FIREFOX WIDGETS ******/ 

at the end.

---

### Post by atria on 2007-06-18
Great work indeed, firefox looks much better now ;)

---

### Post by loserboy on 2007-06-19
2.1 works great, thanks!

---

### Post by DC@DR on 2007-06-19
I got some transparency issue with this version 2.1 (with checkbox and option button), please re-upload the previous version (1.2) also. I need it to fix some CSS problems, many thanks :-)

---

### Post by fatsheep on 2007-06-19
> **DC@DR]got some transparency issue with this version 2.1 (with checkbox and option button), please re-upload the previous version (1.2) also. I need it to fix some CSS problems, many thanks [/quote]

I uploaded 1.2.  In order to diagnose that bug, I'll need a website or some test html code.  


[QUOTE=Surkow said:**
> [IMG]http://img508.imageshack.us/img508/1180/phpbbbulletuv9.png[/IMG]

Currently my profile in phpBB 2.0 looks like this at the section where you can specifiy your gender.

Part of the code:

```
<tr>
      <td class="row1"><span class="gen">Gender:</span></td>
      <td class="row2">
      <input disabled="disabled" name="gender" value="0" type="radio">
      <span class="gen">None Specified</span>&nbsp;&nbsp;
      <input name="gender" value="1" checked="checked" type="radio">
      <span class="gen">Male</span>&nbsp;&nbsp;

      <input name="gender" value="2" type="radio">
      <span class="gen">Female</span></td>
</tr>
```

As you can see the bullet is disabled and suffers from a render error.

Try removing the firefox widgets and installing 2.1.

EDIT: Actually that won't work, I'm getting your bug on 2.1 as well.  It shouldn't be too hard to fix though.  Look for a bug fix in 2.2.

---

### Post by moredhel on 2007-06-19
A graphical installer this time? nice :D

---

### Post by DC@DR on 2007-06-19
@fatsheep: You can check this website: [http://www.vietfinsv.net](http://www.vietfinsv.net). Right on the portal of the site, the TYPING MODE options are not displayed properly. I don't know if it's site-dependent issue, but the previous version 1.2 works just fine on that site. Many thanks for reuploading :-)

---

### Post by loserboy on 2007-06-19
I also found something in 2.1 although I dunno if it's specific to 2.1


where the arrow is pointing there should be the word "envelope", but the whole drop down menu is blank where there should be about 5 options to choose
It's strange because none of the other menus seem to have this problem on the page, but I use this site 3 or 4 times a day [www.fedex.com](www.fedex.com) , but you have to have an account to see that page.

---

### Post by walkerk on 2007-06-19
Cool. Worked great. Firefox looks a lot better now. :)

---

### Post by schnupi on 2007-06-19
Ok so I just updated from 1.1 to 2.2 by uninstalling it first and then installing 2.2... and it looks great

i found one problem though...the ratio buttons which looked good with 1.1 in an invisionboard (ip.board) look terrible with 2.2. with google however they look grand .. below are some screenshots just to illustrate the thing

---

### Post by fatsheep on 2007-06-20
> **DC@DR said:**
> @fatsheep: You can check this website: [http://www.vietfinsv.net](http://www.vietfinsv.net). Right on the portal of the site, the TYPING MODE options are not displayed properly. I don't know if it's site-dependent issue, but the previous version 1.2 works just fine on that site. Many thanks for reuploading :-)

Yep that's definately a bug, I'll get working on it.  

> **loserboy said:**
> I also found something in 2.1 although I dunno if it's specific to 2.1


where the arrow is pointing there should be the word "envelope", but the whole drop down menu is blank where there should be about 5 options to choose
It's strange because none of the other menus seem to have this problem on the page, but I use this site 3 or 4 times a day [www.fedex.com](www.fedex.com) , but you have to have an account to see that page.

Well I'll look around and see if I find a situation similar to this.  It would be helpful if you could reproduce the section of code that causes this problem (Press Ctrl+u to view the source code of a web page in Firefox).

> **schnupi said:**
> Ok so I just updated from 1.1 to 2.2 by uninstalling it first and then installing 2.2... and it looks great

i found one problem though...the ratio buttons which looked good with 1.1 in an invisionboard (ip.board) look terrible with 2.2. with google however they look grand .. below are some screenshots just to illustrate the thing

Do you have a link?

---

### Post by schnupi on 2007-06-20
check ur pm although i think its an ipboard problem

---

### Post by loserboy on 2007-06-20
> Well I'll look around and see if I find a situation similar to this. It would be helpful if you could reproduce the section of code that causes this problem (Press Ctrl+u to view the source code of a web page in Firefox).


ok I'm not very good at this, but this section was the only thing that seemed related, also attached is a full screen shot, but the full code is too big to attach


package1.options[i] = null;
}
package1.options[packIndex] = new Option("Select packaging", "Select packaging");
packIndex++;
package1.options[packIndex] = new Option("FedEx Envelope", "FedEx Envelope");
packIndex++;
package1.options[packIndex] = new Option("FedEx Pak", "FedEx Pak");
packIndex++;
package1.options[packIndex] = new Option("FedEx Box", "FedEx Box");
packIndex++;
package1.options[packIndex] = new Option("FedEx Tube", "FedEx Tube");
packIndex++;
package1.options[packIndex] = new Option("Your Packaging", "Your Packaging");
payment1.options[paymentCount] = null;
if(index2 == paymentCount)
index2 =docshipD.payAccountIndex.value;
}
docshipD.prev_service.value=selectedServiceis;
service1.selectedIndex = index;
package1.selectedIndex = index1;
getDropDownValue(selectedPackaging, package1);
payment1.selectedIndex = index2;
}
}

---

### Post by fatsheep on 2007-06-20
> **schnupi said:**
> Ok so I just updated from 1.1 to 2.2 by uninstalling it first and then installing 2.2... and it looks great

i found one problem though...the ratio buttons which looked good with 1.1 in an invisionboard (ip.board) look terrible with 2.2. with google however they look grand .. below are some screenshots just to illustrate the thing

I registered and I'm waiting  on Admin approval in order to view that page.

> **DC@DR said:**
> @fatsheep: You can check this website: [http://www.vietfinsv.net](http://www.vietfinsv.net). Right on the portal of the site, the TYPING MODE options are not displayed properly. I don't know if it's site-dependent issue, but the previous version 1.2 works just fine on that site. Many thanks for reuploading :-)

Fixed in 2.3.  That bug was so pesky that I'm numbering them and keeping a log now. :-p

---

### Post by DC@DR on 2007-06-20
Hi fatsheep:

Thanks for the fix. But the install.sh (v2.3) file needs to be rewritten, cause when issuing it, it generated this error message:
```

[19:48:32]dbuiviet@ubuntu:~/Temp/firefox_widgets_2.3$ ./install -i
Installing widgets to /home/fatsheep/Desktop/test
Installing the images to /home/fatsheep/Desktop/test/res/form-widgets.
cp: cannot create directory `/home/fatsheep/Desktop/test/res': No such file or directory
Appending contents of forms-extra.css to /home/fatsheep/Desktop/test/res/forms.css.
bash: /home/fatsheep/Desktop/test/res/forms.css: No such file or directory
bash: /home/fatsheep/Desktop/test/res/forms.css: No such file or directory
bash: /home/fatsheep/Desktop/test/res/forms.css: No such file or directory
Installation complete.  Please restart Firefox.

```
When I edited the install.sh and got the forms-extra.css appended to /usr/lib/firefox/res/forms.css properly, the option box is now displayed properly, but the checkbox is still NOT (I tested on the same site, you can test the checkbox by going to login page of the site). Could you take a look once again, and rewrite the install script? Thanks :-)

---

### Post by fatsheep on 2007-06-20
> **DC@DR said:**
> Hi fatsheep:

Thanks for the fix. But the install.sh (v2.3) file needs to be rewritten, cause when issuing it, it generated this error message:
```

[19:48:32]dbuiviet@ubuntu:~/Temp/firefox_widgets_2.3$ ./install -i
Installing widgets to /home/fatsheep/Desktop/test
Installing the images to /home/fatsheep/Desktop/test/res/form-widgets.
cp: cannot create directory `/home/fatsheep/Desktop/test/res': No such file or directory
Appending contents of forms-extra.css to /home/fatsheep/Desktop/test/res/forms.css.
bash: /home/fatsheep/Desktop/test/res/forms.css: No such file or directory
bash: /home/fatsheep/Desktop/test/res/forms.css: No such file or directory
bash: /home/fatsheep/Desktop/test/res/forms.css: No such file or directory
Installation complete.  Please restart Firefox.

```
When I edited the install.sh and got the forms-extra.css appended to /usr/lib/firefox/res/forms.css properly, the option box is now displayed properly, but the checkbox is still NOT (I tested on the same site, you can test the checkbox by going to login page of the site). Could you take a look once again, and rewrite the install script? Thanks :-)

Sorry about that typo, I've uploaded a corrected version 2.3.  However, I'm convinced I fixed your problem, I have 2.3 installed and the web page views 100% normally.  Remember that installing over the previous widgets with the normal install option does not work.  You need to use the reinstall (upgrade) option ("--reinstall" or "-u" on the command line).  I think I might just make it so the install option automatically overwrites any existing firefox widgets in the future and remove the reinstall option.  Having an install option that doesn't install over previous versions is just a source of confusion.

---

### Post by schnupi on 2007-06-20
> **fatsheep said:**
> I registered and I'm waiting  on Admin approval in order to view that page.



Fixed in 2.3.  That bug was so pesky that I'm numbering them and keeping a log now. :-p


thanks 2.3 fixed the problem! i really hope that this widget is going to be integrated into either the new ubuntu version or into the new linux firefox versions

edit: hmm the checkboxes seem to be still not working though... 2 screenshots for comparison below
edit2: if you wanna have a look -> [http://forums.invisionpower.com/index.php?act=Search](http://forums.invisionpower.com/index.php?act=Search) ... the official ipboard has the same problem with the checkboxes

---

### Post by ingvarwolf on 2007-06-21
I have installed and liked that very much. Thank you! Great job!

---

### Post by Twizz on 2007-06-21
Hello! I posted a while ago, and just wanted to say thx again!  I had noticed small problems with this before, but still liked it better than the default.  BTW all the problems I had have been fixed since last I checked the forums lol  so thx :)

---

### Post by Surkow on 2007-06-21
@fatsheep - Thanks for fixing the bug with the disabled bullets.

---

### Post by fatsheep on 2007-06-21
Again, thanks for all the support. :KS

> **schnupi said:**
> thanks 2.3 fixed the problem! i really hope that this widget is going to be integrated into either the new ubuntu version or into the new linux firefox versions

edit: hmm the checkboxes seem to be still not working though... 2 screenshots for comparison below
edit2: if you wanna have a look -> [http://forums.invisionpower.com/index.php?act=Search](http://forums.invisionpower.com/index.php?act=Search) ... the official ipboard has the same problem with the checkboxes

Confirmed as Bug #3.  Thanks for the report.

**EDIT:** Fixed in Revision 2.4.

---

### Post by fatsheep on 2007-06-21
> **loserboy said:**
> ok I'm not very good at this, but this section was the only thing that seemed related, also attached is a full screen shot, but the full code is too big to attach


package1.options[i] = null;
}
package1.options[packIndex] = new Option("Select packaging", "Select packaging");
packIndex++;
package1.options[packIndex] = new Option("FedEx Envelope", "FedEx Envelope");
packIndex++;
package1.options[packIndex] = new Option("FedEx Pak", "FedEx Pak");
packIndex++;
package1.options[packIndex] = new Option("FedEx Box", "FedEx Box");
packIndex++;
package1.options[packIndex] = new Option("FedEx Tube", "FedEx Tube");
packIndex++;
package1.options[packIndex] = new Option("Your Packaging", "Your Packaging");
payment1.options[paymentCount] = null;
if(index2 == paymentCount)
index2 =docshipD.payAccountIndex.value;
}
docshipD.prev_service.value=selectedServiceis;
service1.selectedIndex = index;
package1.selectedIndex = index1;
getDropDownValue(selectedPackaging, package1);
payment1.selectedIndex = index2;
}
}

Could you email me the entire page?  ( jesse <DOT> fatsheep >AT< gmail *DOT* com.  Thanks.

---

### Post by DC@DR on 2007-06-22
Yes, finally, this version 2.4 has fixed all the deformed problems in my website [http://www.vietfinsv.net](http://www.vietfinsv.net). Thanks a lot, fatsheep, for the good works. Cheers :-)

---

### Post by schnupi on 2007-06-22
yap 2.4 absolutely fixed all my problems! thanks alot!:KS

---

### Post by loserboy on 2007-06-22
> **fatsheep said:**
> Could you email me the entire page?  ( jesse <DOT> fatsheep >AT< gmail *DOT* com.  Thanks.

well... it works in 2.4, i dunno why.... i can switch back to 2.1 and it still messes up, but 2.4 is perfect.

you still want the page?

---

### Post by fatsheep on 2007-06-22
> **DC@RC]Yes, finally, this version 2.4 has fixed all the deformed problems in my website [http://www.vietfinsv.net](http://www.vietfinsv.net). Thanks a lot, fatsheep, for the good works. Cheers [/quote]

[quote=schnupi]yap 2.4 absolutely fixed all my problems! thanks alot![/quote]

Glad to hear it. :)

[QUOTE=loserboy said:**
> well... it works in 2.4, i dunno why.... i can switch back to 2.1 and it still messes up, but 2.4 is perfect.

you still want the page?

Yes.  I'd like to have a look and see if I can replicate the problem.  Perhaps I can learn something useful from it.

---

### Post by loserboy on 2007-06-22
sent... that is one big page of code

let me know if theres anything I can do to help

---

### Post by tomane on 2007-06-22
Looks great, I just installed it and firefox looks improved a *lot*. However I think the buttons are a little too flat for my taste but they certainly don't look bad anyway.

Cheers,
--to

---

### Post by jdarias on 2007-06-22
Wow... what a must have!!

tried the text installer, wich was very friendly. No need for the graphic thing! ;) at least for me

congratulations!

thank you!

---

### Post by wersdaluv on 2007-06-22
Fatsheep, you're the man!

---

### Post by yagood on 2007-06-23
Great project, thanks!

---

### Post by AptlyNamed on 2007-06-23
Excellent patch..this should be default in Firefox. But I did notice some disappearing checkboxes such as here: [[COLOR="Blue"]http://polishlinux.org/choose/quiz/[/COLOR]]("http://polishlinux.org/choose/quiz/") . I'm using using  Firefox-Widgets v2.4 and Firefox v2.0.0.4 by the way.

---

### Post by fatsheep on 2007-06-23
> **tomane said:**
> Looks great, I just installed it and firefox looks improved a *lot*. However I think the buttons are a little too flat for my taste but they certainly don't look bad anyway.

Cheers,
--to

Well all the images are in the "form-widgets" folder, so feel free to edit those files install (or just edit the images directly under the res/form-widgets directory in your firefox directory).  So if you have any graphical skill with the gimp that you'd like to put to work for us, feel free to do so.  I've been meaning to experiment with it myself, just haven't gotten around to it yet.

> **AptlyNamed said:**
> Excellent patch..this should be default in Firefox. But I did notice some disappearing checkboxes such as here: [[COLOR="Blue"]http://polishlinux.org/choose/quiz/[/COLOR]]("http://polishlinux.org/choose/quiz/") . I'm using using  Firefox-Widgets v2.4 and Firefox v2.0.0.4 by the way.

Well there aren't any checkboxes on that page, I think you are referring to the radio buttons.  I don't see any problems with the display of the radio buttons, feel free to post a screenshot of the bug.

---

### Post by AptlyNamed on 2007-06-24
> 
Well there aren't any checkboxes on that page, I think you are referring to the radio buttons.  I don't see any problems with the display of the radio buttons, feel free to post a screenshot of the bug.

I found the cause. When I copied the form-widgets folder to /usr/lib/firefox/res/ using sudo, the permissions for the form-widgets folder were set only for root. Could it be that copying from an ntfs partition removes permissions? Anyway when I changed the permissions it worked.

---

### Post by Gauchoo1234 on 2007-06-24
Problem:

/usr/lib/firefox-2.0.0.4/res/form-widgets not found.  No action taken.
The CSS does not appear to be installed.
/usr/lib/firefox-2.0.0.4/res/forms.css will not be edited.


What does this mean? Do i need to install some 'CSS' ? What is this?

Thanks,

---

### Post by Gauchoo1234 on 2007-06-24
> **Gauchoo1234 said:**
> Problem:

/usr/lib/firefox-2.0.0.4/res/form-widgets not found.  No action taken.
The CSS does not appear to be installed.
/usr/lib/firefox-2.0.0.4/res/forms.css will not be edited.


What does this mean? Do i need to install some 'CSS' ? What is this?

Thanks,

Problem fixed, just installed  Firefox Widgets 0.2 :)

Sorry for the dumb question above

---

### Post by haispeedy on 2007-06-25
My Firefox looks better now !
Thanks you for this useful thing. :D

---

### Post by speaker219 on 2007-06-26
Ah, it's beautiful now, thanks alot, the radio buttons were astonishingly ugly before =)
web 2.0ish

---

### Post by u-ben-tu on 2007-06-26
Thanks, this is great. Couldn't bear to look at those ugly buttons before. Now I'm happy :grin:

---

### Post by Steeljack on 2007-06-26
These are lovely. Minimalist without being *too* understated. Elegant. Thanks for creating them, and thanks for keeping them updated!

---

### Post by tzulberti on 2007-06-26
It works great here

---

### Post by xanderer on 2007-06-27
great fix, looks amazing!:p

---

### Post by kingfishr on 2007-06-27
I seem to have a problem with the outlines of checkboxes not showing up...the box is there because i can click it and a check mark appears, but the outlines are invisible and thus i often don't notice checkboxes at all.

Other than that, the widgets are beautiful.

---

### Post by coonj on 2007-06-27
Very nice! Feels more like Ubuntu (less like Windows).

I think my radio buttons may have disappeared though.... there are non in the "Post Icons" selector below

---

### Post by Surkow on 2007-06-28
@fatsheep - I noticed that disabled radio buttons were greyed out before I updated to the new widgets. Can you make the new radio buttons grey out when disabled? I wrote a small [article]("http://surkow.nl/articles/20070627-1.html") to compare the different widgets.

---

### Post by turezky on 2007-06-28
10x, works great :)
And now, how can I customize the .png for myself. Tried GIMP. Opened button.png, and it was empty inside...

---

### Post by xinafoid on 2007-06-28
Works great, a much better UI. Thank You!

---

### Post by GalenX on 2007-06-29
Dear fatsheep,

Thank you very much for the new buttons in firefox. They look awesome and best of all, they work for me without a glitch. As I am writing on a tutorial on how to make the look and feel of firefox better in Ubuntu on the German Ubuntu wiki (see [here]("http://wiki.ubuntuusers.de/Baustelle/Firefox_Optik/")), I would like to ask you, if you would agree to put your wigets on the manual? If yes, is it possible to provide a download link, that does not need a login? Do you want me to put any special link of yours on the wiki page (e.g. your homepage)?

Thanks and keep up the good work, we appreciate it also here in Europe very much. :D

Yours GalenX

---

### Post by Djieff on 2007-06-29
Seriously, I don't know why but the widgets are not there. Firefox has not changed. I installed using the GUI-installer, everything went well, something flashed ( like a refresh rate flash)as if there was something changing.

Unfortunatly, when I relaunched firefox, the same buttons were there, and no new widgets.

Do you have an idea?

---

### Post by Surkow on 2007-06-30
> **Djieff said:**
> Seriously, I don't know why but the widgets are not there. Firefox has not changed. I installed using the GUI-installer, everything went well, something flashed ( like a refresh rate flash)as if there was something changing.

Unfortunatly, when I relaunched firefox, the same buttons were there, and no new widgets.

Do you have an idea?

Where did you install Firefox?

---

### Post by FoolsGold_MKII on 2007-06-30
Tried it today. You've done good work dude, makes things look even slicker on my system. :)

---

### Post by Emx on 2007-06-30
Here is the mirror: [http://emir.linux.org.ba/firefox-widgets-1.1.tar.bz2](http://emir.linux.org.ba/firefox-widgets-1.1.tar.bz2)

---

### Post by Djieff on 2007-06-30
> **Surkow said:**
> Where did you install Firefox?

I rebooted and now the widgets are working. I didn't thought that rebooting was necessary.
I like the results on firefox, it's looks better.

thanks!

---

### Post by Surkow on 2007-06-30
> **Djieff said:**
> I rebooted and now the widgets are working. I didn't thought that rebooting was necessary.
I like the results on firefox, it's looks better.

thanks!

Somehow Fx must have been running...since rebooting isn't needed at all.

---

### Post by TutoWRM on 2007-07-04
thanks, i'm gonna try it now.

---

### Post by fatsheep on 2007-07-05
> **kingfishr said:**
> I seem to have a problem with the outlines of checkboxes not showing up...the box is there because i can click it and a check mark appears, but the outlines are invisible and thus i often don't notice checkboxes at all.

Other than that, the widgets are beautiful.

This sounds like a bug I've already fixed.  Have you upgraded to 2.4?  If so please post a screenshot or link to the page.

> **Surkow said:**
> @fatsheep - I noticed that disabled radio buttons were greyed out before I updated to the new widgets. Can you make the new radio buttons grey out when disabled? I wrote a small [article]("http://surkow.nl/articles/20070627-1.html") to compare the different widgets.

Yea I'm sure that's not hard to do.  No time right now, but I'm writing myself a note to check that out (maybe later tonight).  



> **turezky said:**
> 10x, works great :)
And now, how can I customize the .png for myself. Tried GIMP. Opened button.png, and it was empty inside...

It's actually not empty.  Use the color picker to get the exact color of the pixels on the edges of the image.  If you're next question is how this works, I really don't know, I never got around to experimenting with it.


> **GalenX said:**
> Dear fatsheep,

Thank you very much for the new buttons in firefox. They look awesome and best of all, they work for me without a glitch. As I am writing on a tutorial on how to make the look and feel of firefox better in Ubuntu on the German Ubuntu wiki (see [here]("http://wiki.ubuntuusers.de/Baustelle/Firefox_Optik/")), I would like to ask you, if you would agree to put your wigets on the manual? If yes, is it possible to provide a download link, that does not need a login? Do you want me to put any special link of yours on the wiki page (e.g. your homepage)?

Thanks and keep up the good work, we appreciate it also here in Europe very much. :D

Yours GalenX

Sorry for that late reply, yes you can use widgets.  In fact please do, I don't require any links.  All I ask is that the authors remain listed in the authors file, feel free to make any changes or improvements.  I don't have a way to host the file outside of the forum so I'm afraid I can't help you there.  Good luck on the tutorial!

---

### Post by michaelzap on 2007-07-06
Working perfectly (and looking a whole lot nicer) in Swiftfox - Thanks!

---

### Post by Bashed on 2007-07-06
How do I apply this to a 32bit firefox version, installed via this method?
[http://ubuntuforums.org/showthread.php?t=202537](http://ubuntuforums.org/showthread.php?t=202537)

I am running FF 32 bit on 64bit Gutsy Tribe 2.

I ran the script and selected custom path, /usr/local/firefox32
but nothing happened (yes, FF was closed too).

---

### Post by fatsheep on 2007-07-06
> **TalkJesus said:**
> How do I apply this to a 32bit firefox version, installed via this method?
[http://ubuntuforums.org/showthread.php?t=202537](http://ubuntuforums.org/showthread.php?t=202537)

I am running FF 32 bit on 64bit Gutsy Tribe 2.

I ran the script and selected custom path, /usr/local/firefox32
but nothing happened (yes, FF was closed too).

Check the command of your browser (right click on the icon and go to properties).  It should be firefox32 (I use the same thing).  Type **whereis firefox32** in the terminal or **whereis <Whatever the command for your browser is here>**.  Here's my output:

> fatsheep:~$ whereis firefox32
firefox32: /usr/local/bin/firefox32 **/usr/local/firefox32** /usr/share/firefox32 /usr/share/man/man1/firefox32.1.gz


I put the location of the main directory in bold.  Maybe your firefox32 was installed into /opt/ ?

---

### Post by ElemonGW on 2007-07-07
Buttons and checkboxes are correctly changed. Drop down menus change as well but not correctly, as the button at the right remains the default and doesn't become the one with to arrows. Text fields are converted correctly too, but in some sites the default ones appear. Finally, no problem with radio buttons too. That's all :)

---

### Post by Ted Nancy on 2007-07-07
Much better! Why is this something that needs to be done though? If you can do this, why can't Firefox implement this directly?

---

### Post by ginocic on 2007-07-08
it rocks!!! :guitar:

I can't understand why Firefox team doesn't implement such features directly, too.

Well, we're lucky because there's someone who gave us the Wonderful widgets ;)

Keep up the great work!

---

### Post by moredhel on 2007-07-08
I think these should be the widgets :D

---

### Post by alex_goodwin on 2007-07-08
Works like a charm!
Thanks a lot!

---

### Post by VictorR on 2007-07-09
Really cool!
And the graphical installer is very nice indeed. Thank you!

---

### Post by GalenX on 2007-07-09
Dear fat sheep,
Thank you very much for letting us here on wiki.ubuntuusers.de use the widgets. I have put your package version 2.4 "as is" on our server (that means containing all the authors as you have alrady done) and have put your name on the wiki for the widgets. A link has been made to this threat.
Thanks again

GalenX

---

### Post by fatsheep on 2007-07-09
I'm having trouble getting the radio buttons to gray out when disabled as requested but I did get the dropdown image to work.  I'll post a small update soon.

---

### Post by TNBY963 on 2007-07-09
Thanks,

this works great. Nice.

Greetz

Gert

---

### Post by fatsheep on 2007-07-09
**2.5 is released**.  Radio buttons now  "grey out" as requested when disabled and they also show a bit of color when selected (active), as checkboxes do.  Because of the round, css controlled borders badly distort the appearence of the radio buttons.  Because of this, I haven't been able to achieve the nice little inset border that checkboxes have when selected.  If you find a way to accomplish this in the image for the selected radio button (named "radio-active.png"), then feel free to contact me.  Dropdown menus display the correct image (double arrows) now as well.

---

### Post by hammedhaaret on 2007-07-09
great widgets... really great, and really easy for a ubuntu-newbie like myself.

thx a bunch

---

### Post by Surkow on 2007-07-10
> **fatsheep said:**
> **2.5 is released**.  Radio buttons now  "grey out" as requested when disabled and they also show a bit of color when selected (active), as checkboxes do.  Because of the round, css controlled borders badly distort the appearence of the radio buttons.  Because of this, I haven't been able to achieve the nice little inset border that checkboxes have when selected.  If you find a way to accomplish this in the image for the selected radio button (named "radio-active.png"), then feel free to contact me.  Dropdown menus display the correct image (double arrows) now as well.

Thanks for adding the greyed out radio button. I don't know the solution for the other problems though.

---

### Post by schnupi on 2007-07-10
hey.. found another bug i think.. 

if u go to [http://arcticmonkeys.trinitystreetdirect.com/](http://arcticmonkeys.trinitystreetdirect.com/) there is a drop down menu for the currency change .. the drop down menu button doesnt show ..

added two screenshots.. one browsed with opera where it shows and the other one with firefox where it doesnt show

---

### Post by ceti on 2007-07-11
Thanks, fatsheep. Version 2.5 worked perfectly with CLI.

Cheers

---

### Post by fox88 on 2007-07-11
so mutch better :D

thanks pal ;)

---

### Post by fatsheep on 2007-07-11
> **schnupi said:**
> hey.. found another bug i think.. 

if u go to [http://arcticmonkeys.trinitystreetdirect.com/](http://arcticmonkeys.trinitystreetdirect.com/) there is a drop down menu for the currency change .. the drop down menu button doesnt show ..

added two screenshots.. one browsed with opera where it shows and the other one with firefox where it doesnt show

Confirmed and fixed.  Fix will be included in V2.6.  I want to fiddle around with the CSS for the dropdowns a bit more before I release 2.6 though.

EDIT: Done fiddling. ;)  **2.6 is released.**

---

### Post by schnupi on 2007-07-12
> **fatsheep said:**
> Confirmed and fixed.  Fix will be included in V2.6.  I want to fiddle around with the CSS for the dropdowns a bit more before I release 2.6 though.

EDIT: Done fiddling. ;)  **2.6 is released.**

perfect! thanks very much!

---

### Post by Goombie on 2007-07-12
I can't get the either of the installers to work. I double-clicked on graphic_installer, but all that happened was that the script opened up in a text editor. I tried running the other install script, but I get an error message. Help? :(

---

### Post by fatsheep on 2007-07-12
> **Goombie said:**
> I can't get the either of the installers to work. I double-clicked on graphic_installer, but all that happened was that the script opened up in a text editor. I tried running the other install script, but I get an error message. Help? :(

You extracted the .tar.bz2 archive into a folder didn't you?  If you didn't then do that first.  When you double click on the graphic installer you should get a menu.  You can then select "Run" and the graphic installer will run.  To run the text installer ("install"), open up a terminal in the directory you extracted to and use the command **./install**.

---

### Post by nerzack on 2007-07-13
Very nice! Thank you!

---

### Post by ecoxmit on 2007-07-15
works perfectly

---

### Post by dizney on 2007-07-15
Works fine, thx

---

### Post by dsosa on 2007-07-15
Awesome dude! :)

---

### Post by Goombie on 2007-07-16
> **fatsheep said:**
> You extracted the .tar.bz2 archive into a folder didn't you?  If you didn't then do that first.  When you double click on the graphic installer you should get a menu.  You can then select "Run" and the graphic installer will run.  To run the text installer ("install"), open up a terminal in the directory you extracted to and use the command **./install**.

Yes, I extracted the archive into a folder and all that. Turns out I had to run the graphical installer from a terminal to use it, which is slightly odd. I got the widgets installed though, and they look great. :)

---

### Post by fatsheep on 2007-07-17
> **Goombie said:**
> Yes, I extracted the archive into a folder and all that. Turns out I had to run the graphical installer from a terminal to use it, which is slightly odd. I got the widgets installed though, and they look great. :)

Really?  You shouldn't have to.  On my machine I can just double click on the graphic_installer file and select "Run" on the menu that pops up.  Make sure that graphic_installer has executable permissions.  The one I include in the archive always does but maybe there could be a problem transfering those permissions from computer to computer?

---

### Post by Goombie on 2007-07-18
The file does have executable permissions, so that isn't the problem. For some reason, the script files just open in gedit. I've tested it with other scripts files, so it's a problem with my computer, rather than your scripting. :)
On a side note, does anyone know how I could change my file associations, or whatever they're called in Linux, so I can execute script files correctly?

---

### Post by fatsheep on 2007-07-18
> **Goombie said:**
> The file does have executable permissions, so that isn't the problem. For some reason, the script files just open in gedit. I've tested it with other scripts files, so it's a problem with my computer, rather than your scripting. :)
On a side note, does anyone know how I could change my file associations, or whatever they're called in Linux, so I can execute script files correctly?

**Try this:**

Open up nautilus (file browser), select "Edit" from the top menu bar, then select "Preferences" from the Edit menu.  It should open up a window called "File Management Preferences".  Select the "Behavior" tab at the options under the bold text "Executable Text Files".  I think you want this set at "Ask each time" so you get a menu like I do that will ask you if you want to "Display" the text file (in gedit), run the file, or run it in a terminal.

Hope that solved your problem,

- sheep

---

### Post by Goombie on 2007-07-18
That certainly did solve my problem. Thanks! :KS

---

### Post by fatsheep on 2007-07-18
> **Goombie said:**
> That certainly did solve my problem. Thanks! :KS

I'm glad I could help.  :)

---

### Post by fifth_rune on 2007-07-20
After updating to 2.0.0.5, this no longer seems to be working for me.  Anyone else have this problem or know the solution?

---

### Post by jhnthn on 2007-07-20
I just downloaded the latest Firefox nightly to see how Firefox 3 is shaping up and noticed that forms look native now. Thought you all might be interested.

---

### Post by NilsE on 2007-07-20
> **fifth_rune said:**
> After updating to 2.0.0.5, this no longer seems to be working for me.  Anyone else have this problem or know the solution?

The update resets the forms.css so you need to reinstall the script.

---

### Post by 5hundy on 2007-07-21
Thanks for providing this! I like the older versions better though. I has on 1.1 and now using 1.2. I tried the latest version and everything looked really crowded - even on the google home page the buttons are almost drawn over the text box. This is with FF 2.0.0.5

---

### Post by sunshine12 on 2007-07-21
thanks

---

### Post by fatsheep on 2007-07-21
> **5hundy said:**
> Thanks for providing this! I like the older versions better though. I has on 1.1 and now using 1.2. I tried the latest version and everything looked really crowded - even on the google home page the buttons are almost drawn over the text box. This is with FF 2.0.0.5

Yea, I removed the margins on just about everything so as not to conflict with site layouts.  This can sometimes make things look more crowded but it is also less likely to mess up site layouts so I think it is worth it.  If you like, I could go back in and add in the margins for 2.6 and send you the file so that you could install 2.6 with the margins of 1.2.

---

### Post by GeneralHooHa on 2007-07-21
I really like this. I never realized how old the internet looked until I installed this. Thank you.

---

### Post by ryk on 2007-07-21
It works very well and is easily to install. And, of course, it looks very great ;-)

---

### Post by wersdaluv on 2007-07-22
The widgets look odd on my laptop.

What do I do?

Please see the attachment.

---

### Post by fatsheep on 2007-07-22
> **wersdaluv said:**
> The widgets look odd on my laptop.

What do I do?

Please see the attachment.

That looks normal to me.  If you are talking about the different coloration of the buttons, I think that is because of your GNOME theme.  Try using the default "Human" theme and see how the widgets look then.

---

### Post by dooooomi on 2007-07-23
Is it possible to install these widgets in a way that will survive a Firefox upgrade? Or do I have to reinstall them every time there's a new version of Firefox?

Also, is there a way to install this locally in ~/.mozilla/firefox?

---

### Post by Catsworth on 2007-07-23
Hi, me again :)

Yet another FF update, meaning yet another re-install of the widgets.  Only this time I'm having real problems, I can't even get the file to extract.  Has anybody else had problems?

Any chance someone could give me the Command Line so that I can make sure I've got it right?

Thanks?

---

### Post by flipthedolphin on 2007-07-23
Does this work with **Flock**?
I've installed the [getdeb.net 0.9.0.1 32 bit version]("http://www.getdeb.net/app.php?name=Flock").

On firefox works fine.

---

### Post by amoore on 2007-07-23
cant wait to give this a try!

---

### Post by zsouthboy on 2007-07-23
Heads up, 2.6 works for me in Gutsy Tribe 3, x64 bit - running the trunk build of Firefox (Mozilla/5.0 (X11; U; Linux i686 (x86_64); en-US; rv:1.9a7pre) Gecko/2007072104 Minefield/3.0a7pre)

The scrollbar still looks like old X application scrollbars (compared to say FF2, on the same machine, which uses gnome's theme)

Thanks for the script!

---

### Post by Catsworth on 2007-07-24
> **Catsworth said:**
> Hi, me again :)

Yet another FF update, meaning yet another re-install of the widgets.  Only this time I'm having real problems, I can't even get the file to extract.  Has anybody else had problems?

Any chance someone could give me the Command Line so that I can make sure I've got it right?

Thanks?



Anybody?

Thanks.

---

### Post by fatsheep on 2007-07-24
> **dooooomi said:**
> Is it possible to install these widgets in a way that will survive a Firefox upgrade? Or do I have to reinstall them every time there's a new version of Firefox?

Also, is there a way to install this locally in ~/.mozilla/firefox?

I think you will have to reinstall after each update.  Also, I do not know of a way to install into ~/.mozilla/firefox directory.  However, if I'm wrong let me know.

> **Catsworth said:**
> Hi, me again :)

Yet another FF update, meaning yet another re-install of the widgets.  Only this time I'm having real problems, I can't even get the file to extract.  Has anybody else had problems?

Any chance someone could give me the Command Line so that I can make sure I've got it right?

Thanks?

What version is this?  How are you trying to extract the file?  What error are you getting?

> **flipthedolphin said:**
> Does this work with **Flock**?
I've installed the [getdeb.net 0.9.0.1 32 bit version]("http://www.getdeb.net/app.php?name=Flock").

On firefox works fine.

I have never used Flock but it is based on Firefox's code base so I think it should work.  If you want to check, first go into the flock directory and make sure there is a "res" directory.  Inside that directory there should be a forms.css file and no file or folder named "form-widgets" unless you have already installed the widgets to flock.  After doing this, install the widgets.  It should work.  Let me know how it goes.

---

### Post by Gadren on 2007-07-24
Hey, just wanted to post and say that this worked wonderfully for me!  Thank you so much for making this!

---

### Post by Catsworth on 2007-07-24
> **fatsheep said:**
> What version is this?  How are you trying to extract the file?  What error are you getting?

Think it must have been a corrupted file, it worked fine this time - I like the graphical installer, very nice :)

---

### Post by Catsworth on 2007-07-25
Ok, my previous problem seems to have been caused by the fact that I was downloading the file to a FAT32 formatted drive and trying to extract it there.  I've since downloaded directly to my Desktop and it works fine.

---

### Post by Thene on 2007-07-26
Superb! Thank you fatsheep, you're a :KS.

It works perfectly in FF64bit & FF32bit running on Fiesty Intel 64.

When installing I just had to change the folder for intstalling the widget to where the FF32bit was. Eg. /usr/local/firefox32.

The radio buttons always looked unfinished. I am so pleased!

---

### Post by cheeki on 2007-07-26
Great work :) Thanks

---

### Post by notoeverything on 2007-07-26
Other people have mentioned it but was just wondering if there was any permanent solution to the crowding, especially on Google. You said that fixing it could affect the layouts of sites. How bad would it be? Would it be worth it because I think it looks quite ugly so crowded.

---

### Post by fatsheep on 2007-07-26
> **notoeverything said:**
> Other people have mentioned it but was just wondering if there was any permanent solution to the crowding, especially on Google. You said that fixing it could affect the layouts of sites. How bad would it be? Would it be worth it because I think it looks quite ugly so crowded.

Well I don't remove any padding or margins from Firefox (although the original CSS did) so if its crowded now, it was like that by default.  However, if you want to try an experiment, follow these instructions:

1.  Go to the directory where you have V2.6 extracted.
2.  Open up "forms-extra.css" in a text editor.
3.  Find the "Buttons" section:

> 
/* Buttons */

input[type="button"],
input[type="submit"],
input[type="reset"],
button,
select {
  color: ButtonText;
  background-color: Window;
  background: Window url("form-widgets/button.png") repeat-x bottom right;
  border: 2px solid ThreeDShadow;
  -moz-border-top-colors: ThreeDShadow Window;
  -moz-border-right-colors: ThreeDShadow ThreeDHighlight;
  -moz-border-bottom-colors: ThreeDShadow ThreeDHighlight;
  -moz-border-left-colors: ThreeDShadow Window;
  -moz-border-radius: 1px;
}

4.  Add a 2px margin to those buttons:

> 
/* Buttons */

input[type="button"],
input[type="submit"],
input[type="reset"],
button,
select {
  color: ButtonText;
  background-color: Window;
  background: Window url("form-widgets/button.png") repeat-x bottom right;
  border: 2px solid ThreeDShadow;
  -moz-border-top-colors: ThreeDShadow Window;
  -moz-border-right-colors: ThreeDShadow ThreeDHighlight;
  -moz-border-bottom-colors: ThreeDShadow ThreeDHighlight;
  -moz-border-left-colors: ThreeDShadow Window;
  -moz-border-radius: 1px;
  **margin:2px;**
}

5.  Save the text file.  
6.  Reinstall the widgets (using the installer in that directory).
7.  Now, after you restart Firefox, you will see some padding around the buttons on google and other sites.  You can also increase or decrease the padding if you like.  For example, try **margin:5px** and you'll get even more space around the buttons.

---

### Post by delacerda on 2007-07-26
Thanks! I never liked the way the default widgets looked either. This looks much better. Thanks for the work!

---

### Post by jeroenvrp on 2007-07-26
In installed version 1.0 a while ago and now I've out, it's already version 2.6. Great job!!!

I changed one thing and that's the droparrow. I personally don't like the up+down-arrow, so I changed it to only a down-arrow. Maybe because I'm on Kubuntu/KDE. So maybe it's an idea to have this as an option. I attached the files.

Cheers,

Jeroen

---

### Post by jjgomera on 2007-07-26
wow, finally firefox show pretty like windows, thanks

---

### Post by didwah on 2007-07-27
Looks awesome!!:guitar:

---

### Post by st33med on 2007-07-27
I do like it, however, sometimes it reverts to it's old buttons when I upgrade Firefox (I think that is when it happens, not sure).

But, thank you.

---

### Post by fatsheep on 2007-07-27
> **st33med said:**
> I do like it, however, sometimes it reverts to it's old buttons when I upgrade Firefox (I think that is when it happens, not sure).

But, thank you.

Yep, Firefox overwrites the forms.css file which restores back to the old buttons, forcing you to reinstall the widgets.  There's no good way around it that I know of unless there's a way to detect when firefox gets upgraded and run a certain command when it does but I don't know enough about the package system to do that.  If you find a way please post it here and I'll add it to my main post. :)

---

### Post by lamarcheb on 2007-07-27
Works great. Better than a manual install. Thanks for putting your talents to good use.  The installer is slicks and worked great.  Now Firefox is very usable!:popcorn:

---

### Post by nelamvr6 on 2007-07-27
Excellent work! This is a big improvement!

---

### Post by dizzyboo on 2007-07-28
Thanks for this great tweak. Never realised how ugly the default widgets were.

---

### Post by LKRaider on 2007-07-28
> **fatsheep said:**
> Yep, Firefox overwrites the forms.css file which restores back to the old buttons, forcing you to reinstall the widgets.  There's no good way around it that I know of unless there's a way to detect when firefox gets upgraded and run a certain command when it does but I don't know enough about the package system to do that.  If you find a way please post it here and I'll add it to my main post. :)

You can, using dpkg-divert. From the man page:
> File  ‘diversions’  are  a way of forcing dpkg(1) not to install a file into its location(...)

For each altered file, when installing the widgets, you could run something like:
sudo dpkg-divert /usr/lib/firefox/filename

And when removing:
sudo dpkg-divert --remove /usr/lib/firefox/filename

---

### Post by kostkon on 2007-07-29
Thanks very much.

---

### Post by sur on 2007-07-29
Hi,
That worked out well.
 Thanks !!

--
sur
[http://expressica.com](http://expressica.com)

---

### Post by fatsheep on 2007-07-29
> **LKRaider said:**
> You can, using dpkg-divert. From the man page:


For each altered file, when installing the widgets, you could run something like:
sudo dpkg-divert /usr/lib/firefox/filename

And when removing:
sudo dpkg-divert --remove /usr/lib/firefox/filename

Thanks for the tip.  However, if there is a major Firefox update and there are changes made to the forms.css file then this will prevent that from happening so it might not be a good idea to add it to the script.  I will, however, add it to the main post.

---

### Post by acankat on 2007-08-01
Wonderful !

---

### Post by M.G. on 2007-08-01
Thanks a lot... works great...

---

### Post by yopnono on 2007-08-01
just like to say... that ver 3 of firefox have native buttons etc etc to match the theme selected.

---

### Post by fatsheep on 2007-08-01
> **yopnono said:**
> just like to say... that ver 3 of firefox have native buttons etc etc to match the theme selected.

Well that's good news.  We'll be able to retire my dirty little script. ;)

---

### Post by fatsheep on 2007-08-01
Is noticing web pages where the arrows for the dropdown image do not display?  I noticed this posting at an SMF forum...  It's really easy to fix so I can release a fix in 2.7 but I was suprised no one reported the bug.

---

### Post by aztec13 on 2007-08-02
none of this has anything to do with anything if you use a add-on theme or does it ? By the way PimpZilla frefox add-onn theme is the smoothest look obtainable, especially how nicely it inherits colors from Ubuntu's desktop themes.k

---

### Post by kwaanens on 2007-08-04
Seing as Firefox widgets also work for Swiftfox and more, it would be cool to have the graphic installer have a list of known firefox-based browsers it works with, and then I could change the stuff in all at once. Could be useful to have a manual line or two, so people could put in their specific odd ball browser as well.

Still dreaming of a .deb that will automagically run if swiftfox, firefox, etc. is updated... Isn't this possible to achieve? I picture an array of uses for such functionality within the dpkg-dept.

- Ketil

---

### Post by fatsheep on 2007-08-04
> **aztec13 said:**
> none of this has anything to do with anything if you use a add-on theme or does it ? By the way PimpZilla frefox add-onn theme is the smoothest look obtainable, especially how nicely it inherits colors from Ubuntu's desktop themes.k

Nope, it does not effect themes that I know of unless themes can reskin the widgets.  Even then, I don't think it would interfere...

> **kwaanens said:**
> Seing as Firefox widgets also work for Swiftfox and more, it would be cool to have the graphic installer have a list of known firefox-based browsers it works with, and then I could change the stuff in all at once. Could be useful to have a manual line or two, so people could put in their specific odd ball browser as well.

Still dreaming of a .deb that will automagically run if swiftfox, firefox, etc. is updated... Isn't this possible to achieve? I picture an array of uses for such functionality within the dpkg-dept.

- Ketil

I'm working on it. :)  I'm going to put these paths in the system:

/usr/lib/firefox
/usr/local/firefox32
/usr/local/Iceweasel32
/usr/local/swiftfox


Any others?  Also, I'm going to try and make it "remember" what directory you last installed to.  Coming in 2.7... ;)

---

### Post by jjgomera on 2007-08-04
> **kwaanens said:**
> Seing as Firefox widgets also work for Swiftfox and more, it would be cool to have the graphic installer have a list of known firefox-based browsers it works with, and then I could change the stuff in all at once. Could be useful to have a manual line or two, so people could put in their specific odd ball browser as well.

Still dreaming of a .deb that will automagically run if swiftfox, firefox, etc. is updated... Isn't this possible to achieve? I picture an array of uses for such functionality within the dpkg-dept.

- Ketil
This widgets run well in swiftfox too, you only have to say the path of swiftfox in graphic instalation, i use with switfox fine

> /usr/lib/firefox
/usr/local/firefox32
/usr/local/Iceweasel32
/usr/local/swiftfox

Well,my swiftfox is in: /usr/lib/swiftfox, thanks for this marvelous :D

---

### Post by fatsheep on 2007-08-05
> **jjgomera said:**
> This widgets run well in swiftfox too, you only have to say the path of swiftfox in graphic instalation, i use with switfox fine


Well,my swiftfox is in: /usr/lib/swiftfox, thanks for this marvelous :D

Added that and it's released in V2.7.  :)

---

### Post by Yasumoto on 2007-08-05
I love how each time I check back on this thread, there's an update. Thanks so much! I really love this, it looks awesome. :)

---

### Post by hypnos on 2007-08-06
It looks awesome!!!! :)=D>

---

### Post by Pablo Pablovski on 2007-08-07
Thanks for all your efforts - the widgets look great.. :)

---

### Post by msgnomer on 2007-08-07
Thanks so much for this.  Looks great.

---

### Post by kwaanens on 2007-08-07
What's up with test1 and test2 in v2.7?

And isn't it possible to make the graphic script write to all those directories at once? Making it obsolete to run it more than once?
Either it could check what dirs are available, and then copy the relevant files, or it could just put them all where they belong, disregarding if the browser in question is actually installed.

- Ketil

---

### Post by fatsheep on 2007-08-07
> **kwaanens said:**
> What's up with test1 and test2 in v2.7?

Delete your "paths" file.  Sorry about that, I was testing how the script would handle duplicate entries in the paths file (which would occur if you had to install to the same path twice).  I have re-uploaded V2.7 without all the test1, test2 nonsense. ;)

Thanks for letting me know, that was careless of me...

> 
And isn't it possible to make the graphic script write to all those directories at once? Making it obsolete to run it more than once?
Either it could check what dirs are available, and then copy the relevant files, or it could just put them all where they belong, disregarding if the browser in question is actually installed.

- Ketil

Well it could but what if your browser is in /opt/firefox or /usr/local/swiftweasel? Also consider a situation where the user may not want me installing the widgets to his /usr/lib/firefox installation but only to his /usr/local/swiftweasel installation.  There are way too many different browsers and paths to test all of them.  It's easier just to let the user tell the script where they want the widgets put and then put them there instead of guessing on where everything is and where the user wants the widgets installed.

---

### Post by crjackson on 2007-08-07
**@fatsheep**

After looking at your before and after pictures of the google section, can you tell me howcome IE shows the thin line around the search box in faint blue, and FF is a gray colored box?

I kind of like the blue a little better, but it seems like the page designer should be deciding what color is displayed rather than the browser.

What's the scoop on that?

I can't wait to try out your program when I get home from work tonight.

Thanks for a great project.

---

### Post by fatsheep on 2007-08-07
> **crjackson said:**
> **@fatsheep**

After looking at your before and after pictures of the google section, can you tell me howcome IE shows the thin line around the search box in faint blue, and FF is a gray colored box?

I kind of like the blue a little better, but it seems like the page designer should be deciding what color is displayed rather than the browser.

What's the scoop on that?
...

I don't know why IE does that and I am assuming you are talking about Windows Internet Explorer because IEs 4 Linux doesn't do that...

---

### Post by crjackson on 2007-08-07
> **fatsheep said:**
> I don't know why IE does that and I am assuming you are talking about Windows Internet Explorer because IEs 4 Linux doesn't do that...


Yes, I'm talking about Windows IE.

---

### Post by fatsheep on 2007-08-07
> **crjackson said:**
> Yes, I'm talking about Windows IE.

It's just the style the designers gave it I guess, I've never bothered looking at IE to see how it works.  I don't give much thought to closed source programs especially if they stink. :p

---

### Post by crjackson on 2007-08-07
> **fatsheep said:**
> It's just the style the designers gave it I guess, I've never bothered looking at IE to see how it works.  I don't give much thought to closed source programs especially if they stink. :p

I just didn't know if the browser or the webpage maker did that.

---

### Post by fatsheep on 2007-08-07
> **crjackson said:**
> I just didn't know if the browser or the webpage maker did that.

Well the browser probably has more control over how buttons are displayed than the web page creator does.  This is why buttons look different in different browsers.  Compare the buttons in Internet Explorer to those in Safari to those in Opera to those in Firefox.  It's all the same code from the web developer that is being processed, the browsers just use different styles.

---

### Post by crjackson on 2007-08-08
I applied the widgets today.  I really like the improvement.  Thanks for a great piece of work.

---

### Post by mekgp on 2007-08-08
Very cool!  Works great...  :biggrin::biggrin:

---

### Post by madscience on 2007-08-09
For some reason, since applying this patch my radio buttons and checkboxes are completely invisible...

NM...

It seems that the form-widgets directory was set to no access for everyone but root... fixed that and it's all good

You might want to check that in the script

---

### Post by fatsheep on 2007-08-09
> **madscience said:**
> For some reason, since applying this patch my radio buttons and checkboxes are completely invisible...

NM...

It seems that the form-widgets directory was set to no access for everyone but root... fixed that and it's all good

You might want to check that in the script

That is very strange.  It is especially strange that this has only happened to you (that I know of).  You don't have a custom umask do you?  How did you run the install script (did you use sudo to run it or did you run it in logged in as root)?

---

### Post by tarntow on 2007-08-10
definitely much more pleasant...thx

---

### Post by nakul on 2007-08-12
why is this not included in default ubuntu installation

---

### Post by coolen on 2007-08-12
Just wanted to drop you a line, and say, thank you. Makes my browser much easier on the eyes. Keep up the good work :)

---

### Post by nothing4me on 2007-08-14
Thank you. It looks so much better. :)

---

### Post by Aserone on 2007-08-15
Loving the widgets. Surely should be default, can't understand how I put up with the default so long.

Sorry if this has been asked before, but can't you get contact with the Mozilla foundation for a possible inclusion?

The people/person who designed the default ones must realize that the "win95" style of the widgets shipped isn't desirable for most users 2007.

---

### Post by CowzRule on 2007-08-15
You could add /opt/navigator to your browser path list. I have Navigator ver. 9.0b2 installed and your Widgets work great.

---

### Post by naughtykid on 2007-08-16
I'm Lovin it! Even better!

---

### Post by el.motar on 2007-08-16
Just to thank you for this excellent mod to firefox.
It does make it look more professional and as others have already mention, why is this work not included in the default firefox version?

Thanks
ATB

---

### Post by insllvn on 2007-08-17
Just installed the widgets and they really improve the aesthetic. I am having a bit of a problem with my radio buttons. They are only visible very briefly when clicked on. they don't show up before clicking and they are gone afterwards. I just grabbed the latest release and am running Ubuntu 7.04 and Firefox 2.0.0.6. Thanks for any help.

---

### Post by hackle577 on 2007-08-19
Form controls do not work on searchmash.com for me.

---

### Post by diffuze on 2007-08-20
I'm using firefox32 on feisty fawn 64bit and I can't get this to work. 
It works like a charm in "normal" firefox but I prefer ff32 due to the plugins.
I've read this thread over and over but I can't figure out what I'm doing wrong. Can someone point me in the right direction?
:(

---

### Post by profjohn on 2007-08-21
Very nice, I'm using it on 64-bit Firefox and it looks great, just after I got Compiz Fusion working too :)  Nice job :guitar:

---

### Post by Alucard-sama on 2007-08-21
Works perfectly with swiftfox, all I had to do was change the path to /usr/lib/swiftfox! ^^

---

### Post by punkboy on 2007-08-22
Does exactly what is says on the tin. Works like a champ. Thanks!

---

### Post by crjackson on 2007-08-23
Works perfectly for me on Firefox 64, Firefox 32, and Swiftfox 32.  Thanks for the great work.

---

### Post by emptythevoid on 2007-08-23
Hey, I've been using your widgets for a while - absolutely love them.

Recently I've done a clean Xubuntu install and I installed the 2.7 widgets.  They worked fine until I upgraded Firefox to 2.0.0.6.  On at least one website I regularly visit, the radial buttons are completely gone, however the button enhancements still look good (on Google).  I've tried uninstalling and re-installing to no avail (uninstalling does revert it back to the ugly widgets, but reinstalling just brings me back to missing radials but good buttons).  

When I go ./install and choose option 1, I see a message saying:
Installing widgets to /usr/lib/firefox
Removing any previous installations of the widgets.
/usr/lib/firefox/res/form-widgets not found.  No action taken.
The CSS does not appear to be installed.
/usr/lib/firefox/res/forms.css will not be edited.
Installing the images to /usr/lib/firefox/res/form-widgets.

Any thoughts?   (and yes, I have been restarting Firefox during installations)

---

### Post by Vic_Astro on 2007-08-28
Fascinating! Thank you!

---

### Post by Yizi on 2007-08-29
Wow, That looks sweet nice job.

---

### Post by -SpaZ on 2007-08-29
Very nice.  Firefox will look a lot better now.

---

### Post by T-One on 2007-09-02
***Deleted****

---

### Post by fatsheep on 2007-09-02
> **diffuze said:**
> I'm using firefox32 on feisty fawn 64bit and I can't get this to work. 
It works like a charm in "normal" firefox but I prefer ff32 due to the plugins.
I've read this thread over and over but I can't figure out what I'm doing wrong. Can someone point me in the right direction?
:(

Does it not work at all (the same widgets)?  What browser are you using?  Are you sure you installed to the right path?  Firefox32 is usually /usr/local/firefox32 but you might want to run **dpkg -L firefox32** to check.

> **emptythevoid said:**
> Hey, I've been using your widgets for a while - absolutely love them.

Recently I've done a clean Xubuntu install and I installed the 2.7 widgets.  They worked fine until I upgraded Firefox to 2.0.0.6.  On at least one website I regularly visit, the radial buttons are completely gone, however the button enhancements still look good (on Google).  I've tried uninstalling and re-installing to no avail (uninstalling does revert it back to the ugly widgets, but reinstalling just brings me back to missing radials but good buttons).  

When I go ./install and choose option 1, I see a message saying:
Installing widgets to /usr/lib/firefox
Removing any previous installations of the widgets.
/usr/lib/firefox/res/form-widgets not found.  No action taken.
The CSS does not appear to be installed.
/usr/lib/firefox/res/forms.css will not be edited.
Installing the images to /usr/lib/firefox/res/form-widgets.

Any thoughts?   (and yes, I have been restarting Firefox during installations)

I am using 2.0.0.6 as well but without problems.  What websites display these problems with the radio buttons?

---

### Post by diffuze on 2007-09-05
> **fatsheep said:**
> Does it not work at all (the same widgets)?  What browser are you using?  Are you sure you installed to the right path?  Firefox32 is usually /usr/local/firefox32 but you might want to run **dpkg -L firefox32** to check.
Yes, it's in /usr/local/..
Maybe I'm misunderstanding here, so I took screenshots to show.
Note that "widgets" such as radiobuttons and "submitbuttons" (webpage stuff) works perfectly in both ff and ff32 now. However it's the appearance that doesn't work in ff32, the user interface. As you see below this includes the "linkbuttons" in the personal toolbar, and dialogboxes and everything. 

To the left you see normal ff, to the right is ff32. 

[img]http://www.imgx.org/pfiles/1786/odd_ff.png[/img] [img]http://www.imgx.org/pfiles/1787/odd_ff32.png[/img]

Just to clarify so we're talking about the same things. ;-)

BTW, this occurs in KDE. When in Gnome ff32 looks just smashing, like normal ff.

---

### Post by coolen on 2007-09-05
That's not the widgets (well, not those in Firefox).
Looks like you might have a dodgy Qt theme. I had something similar a while back in Gnome. One bad theme, and a whole heap of my windows came up in the ugly '95 scheme. I went back to a good theme, logged out and back in, and all was well...

---

### Post by diffuze on 2007-09-06
I'm using Polyester, and kgtk-wrapper to launch it.

---

### Post by alfredo_cba on 2007-09-08
[[IMG]http://img209.imageshack.us/img209/2186/pantallazo2xi2.th.png[/IMG]](http://img209.imageshack.us/img209/2186/pantallazo2xi2.png)

having this problem in every forum, the look way too wide. anyone else with this problem?
thx

---

### Post by jjgomera on 2007-09-11
> **alfredo_cba said:**
> [[IMG]http://img209.imageshack.us/img209/2186/pantallazo2xi2.th.png[/IMG]](http://img209.imageshack.us/img209/2186/pantallazo2xi2.png)

having this problem in every forum, the look way too wide. anyone else with this problem?
thx
maybe is a conflict with the firefox icons theme?

---

### Post by madpotato on 2007-09-13
Thanks for the prettier widgets. I've just tried the latest version (2.7) and it works very well (ubuntu/gnome/epiphany)

---

### Post by madpotato on 2007-09-14
Not a huge problem really, but I thought I'd report:
Search field in Google Reader is not replaced by the pretty version. In other words, it stays ugly. Please see the screenshot attached. [IMG]http://ubuntuforums.org/attachment.php?attachmentid=43471&stc=1&d=1189794854[/IMG]

---

### Post by Zancarius on 2007-09-14
Incidentally, this also works perfectly fine for Firefox running under Gentoo (the Firefox base is installed in /usr/lib/mozilla-firefox).

Awesome job on the installer--I used the shell script rather than the gui installer--and on the artwork! No more ugly widgets! This nifty find certainly made my day.

---

### Post by moredhel on 2007-09-15
Pity that this won't work with swiftweasel =[

---

### Post by Rui Pais on 2007-09-15
> **moredhel said:**
> Pity that this won't work with swiftweasel =[

why? it's working normally here. Just give swiftweasel path, instead of firefox.

---

### Post by altonbr on 2007-09-16
Has this been submitted to [http://launchpad.net/ubuntu](http://launchpad.net/ubuntu) for Gusty or Gusty+1 (Hardy) inclusion? Mark Shuttleworth did say that 'pretty is a spec' did he not?

I made a post about improving the aesthetics of Firefox here: [http://ubuntuforums.org/showthread.php?t=418424](http://ubuntuforums.org/showthread.php?t=418424)... I still think this should be a major bug/blueprint.

---

### Post by BatPenguin on 2007-09-19
Thanks! This works great.

Were you aware that this update was mentioned in the latest Linux Format magazine? Just figured you might be interested that it was mentioned, that's how I found it. Looks great, I installed it on both my machines (Edgy desktop, Feisty laptop), big improvement.

---

### Post by taisao on 2007-09-19
Is there something like this for konqueror? The radio buttons in konqueror doesn't look good.

---

### Post by altonbr on 2007-09-19
I've been told and shown that Firefox 3 has much prettier widgets than their current Firefox 2.0 counterparts: [http://ubuntuforums.org/showpost.php?p=3376461&postcount=25](http://ubuntuforums.org/showpost.php?p=3376461&postcount=25)

---

### Post by godlessgeek on 2007-09-21
Great...just what I needed.
Thanx a ton!

---

### Post by mevets on 2007-09-23
the script run with in the terminal no longer works for me, it is only when I use the gui installer that the widgets actually get installed. Is this bug known?

---

### Post by schnupi on 2007-09-23
found another bug...

[http://economictimes.indiatimes.com/ET_Features/Financial_Times/Stock_markets_and_global_events/articleshow/2394437.cms](http://economictimes.indiatimes.com/ET_Features/Financial_Times/Stock_markets_and_global_events/articleshow/2394437.cms)

scroll down to the bottom where the comment box is it appears like half of the boxes are working and the other half not..

i made a screenshot below..

---

### Post by mario.kostelac on 2007-09-24
Works for me... I like it... Thank you

---

### Post by Sturmeh on 2007-09-25
Definately widgriffic!

---

### Post by hypnos on 2007-09-25
I'm not 100% sure but it seems that doesn't work with 2.0.0.7. After the latest upgrade of my distro (Arch Linux) the original forms are back. I've installed once again giving the new path of my FF location but nothing happens.

Can anyone confirm such problem?

---

### Post by nikoPSK on 2007-09-26
Love it! Wonderful! The buttons before looked pretty ugly (lolz Pretty Ugly) anyways Thanks alot!:KS

---

### Post by Gourgi on 2007-09-26
pretty nice feature 
thanks for sharing :)
installed well on feisty 7.04 and also on gutsy 7.10

P.S. first post around ! 
you forced me  to my 1st post to thank you :)

---

### Post by nikoPSK on 2007-09-28
works great. Using it on 7.10 and it definetely spunked things up!:KS

---

### Post by Daedalus on 2007-09-28
I just love these widgets. I think this should even be included on the repositories.

---

### Post by Frak on 2007-09-28
Ever think of making one for Thunderbird?

---

### Post by nikoPSK on 2007-09-29
certain apps still have that ugliness... Even under wine... Mabye some people could gang up and make wine look better:KS

---

### Post by Frak on 2007-09-29
> **nikoPSK said:**
> certain apps still have that ugliness... Even under wine... Mabye some people could gang up and make wine look better:KS
The latest version of Wine has a feature that allows you to use Windows XP Themes (such as the default Luna) to make your programs under Wine run and look like its actual, running on Windows, counterpart.

---

### Post by nikoPSK on 2007-09-29
cool! Just switched back to 7.04 due to some tof my favorite things not running well (or at all). I need to download this again...:KS

---

### Post by Frak on 2007-09-29
> **nikoPSK said:**
> cool! Just switched back to 7.04 due to some tof my favorite things not running well (or at all). I need to download this again...:KS
Remember if you have problems with Gutsy, report a bug so the final release is all the better ;)

[https://bugs.launchpad.net/](https://bugs.launchpad.net/)

---

### Post by nikoPSK on 2007-09-29
I reported three. But I got tired and am gonna wait till final release. Compiz is giving me poo right now... (thread):(

---

### Post by Frak on 2007-09-29
> **nikoPSK said:**
> I reported three. But I got tired and am gonna wait till final release. Compiz is giving me poo right now... (thread):(
Did you right click on Desktop->Change Desktop Background->Visual Effects->"Custom" or "No Effects/None" ?

---

### Post by nikoPSK on 2007-09-29
I right click, Change background but I don't see a visual effects tab/ button...:confused:

---

### Post by Frak on 2007-09-29
> **nikoPSK said:**
> I right click, Change background but I don't see a visual effects tab/ button...:confused:
You're in Gutsy right, and if you are, what are your Video/Graphics Card specs?

---

### Post by nikoPSK on 2007-09-29
nope I switched back to feisty this-morning.

I have an NVidia GeForce 5200 GTX:KS

---

### Post by Frak on 2007-09-29
> **nikoPSK said:**
> nope I switched back to feisty this-morning.

I have an NVidia GeForce 5200 GTX:KS
ok, I was talking about Gutsy. Also, I heard CF Compiler installer script has gotten alot better too, you may want to try that, its much faster than the precompiled .deb binary.

---

### Post by nikoPSK on 2007-09-29
where would I find that? I searched google...:confused:

---

### Post by Frak on 2007-09-29
> **nikoPSK said:**
> where would I find that? I searched google...:confused:
[http://ubuntuforums.org/showthread.php?t=508769](http://ubuntuforums.org/showthread.php?t=508769)

From what I've heard, it works great :)

---

### Post by nikoPSK on 2007-09-29
Thank you. The forums are a great tool. There should be a link on the apps menu in gutsy. :)

---

### Post by mrojas73 on 2007-09-29
Worked great for me, thank you.

---

### Post by GhostZrydA on 2007-10-15
Just installed the RC of gutsy, and having used the widget fix without any problem on feisty fawn, on gutsy it works on the menu buttons, but the radio check buttons are missing.

Is this a known bug with the widget installer, or something else??

Hope someone can help, as i dont want to have to uninstall and go back to the horrible firefox widgets !

GhostZrydA

---

### Post by Frak on 2007-10-15
> **GhostZrydA said:**
> Just installed the RC of gutsy, and having used the widget fix without any problem on feisty fawn, on gutsy it works on the menu buttons, but the radio check buttons are missing.

Is this a known bug with the widget installer, or something else??

Hope someone can help, as i dont want to have to uninstall and go back to the horrible firefox widgets !

GhostZrydA
Try it again and see what happens.

---

### Post by RAV TUX on 2007-10-15
> **fatsheep said:**
> [SIZE=5]_**News**_[/SIZE]

**2.7 has been released** (August 6th).  There are no changes to the CSS.  Changes are strictly to the graphic installer interface.  The text entry for the installation path has been replaced with a combo entry containing a dropdown menu.  The dropdown menu will "remember" previous installation/removal paths you have used and display them the next time you use it (assuming you don't delete the "paths" file it creates!).  It will also display some standard installation paths for browsers such as '/usr/lib/firefox'.  The browse button also now will go to the directory specified in the entry box instead of just automatically going to root.  

Check out the screenshot below. :KS

----------------------------------

[IMG]http://img365.imageshack.us/img365/32/firefoxwidgetsuiof2.png[/IMG]

One thing that has always bothered me about Ubuntu's firefox is that the buttons, radio buttons, drop down menus, text fields, and checkboxes (known as *widgets*) are very cruddy looking.  Fortunately I found a simple way to fix this.  What we have below is a replacement set of images and CSS code for the widgets which will make them much nicer on the eyes (see bottom of the post for screenshots).  

The original widgets are done by Osmo Salomaa <otsaloma@cc.hut.fi>.  I have written a bash script to make the installation and removal process easier.  You can download this at the bottom of this post.  

To run the graphic installer (for point and click installation and removal), simply unpack the archive anywhere you like, double click on the "graphic_installer", then select "Run".  If you do not have the python-kiwi, it will be installed (python-kiwi is required for the graphical installer to run).  It has been reported that on older Ubuntu's such as Dapper (6.06) this package is simply called "kiwi".  If this is the case you will need to install that package by hand.  After python-kiwi is installed (if it has not already been installed), the graphical installer will run (shown above).

Or, if you prefer, you can use the text based installer which does not require python-kiwi: open a shell, cd to the directory you unpacked the firefox widgets to and run install script (do this with the **./install** command).  Now you are presented with a menu. 

Read the README for more information.  Run the "install" script with the "--help" option for command line option help ("./install --help" works if you are in the same directory). 

Also **make sure you are installing to the path of your Firefox directory.**  By default this script installs to /usr/lib/firefox (which is the default location).  If that is not your Firefox directory you can change it easily.  If you are using the graphic installer it will ask you for the path.  If you are using the text installer ("install" script), then you can enter a new path at the main menu or use the "--path=PATH" or "-p=PATH" command line options to set a path (run the "--help" option for more information).

I should also mention, I have included a backup forms.css file incase you mess anything up.  This file is from a default 64-bit Firefox 2.0 installation.  The forms.css file an be found in Firefox's "res" directory.  You won't need my backup unless you accidently delete your's or the script malfunctions (in which case please contact me).  

[SIZE=4]_**Buttons**_[/SIZE]
[IMG]http://img525.imageshack.us/img525/9933/buttoncomparisonit7.png[/IMG]

[SIZE=4]_**Check Boxes**_[/SIZE]
[IMG]http://img525.imageshack.us/img525/4695/checkboxcomparisongb7.png[/IMG]

[SIZE=4]_**Radio Buttons**_[/SIZE]
[IMG]http://img525.imageshack.us/img525/5641/radiobuttoncomparisonyz0.png[/IMG]

[SIZE=4]_**Drop Down Menus**_[/SIZE]
[IMG]http://img410.imageshack.us/img410/7093/scrollercomparisoniy8.png[/IMG]

[SIZE=4]_**Text Fields**_[/SIZE]
Due to image limitations on the forum I've got to hyperlink this image:
[http://img525.imageshack.us/img525/4117/textfieldcomparisondz6.png](http://img525.imageshack.us/img525/4117/textfieldcomparisondz6.png)

[SIZE=4]_**Before**_[/SIZE]


[SIZE=4]_**After**_[/SIZE]
[IMG]http://img410.imageshack.us/img410/9629/newgooglexq7.png[/IMG]

**Note:**

If you are tired of the widgets getting restored after every Firefox update, try this command:

```
sudo dpkg-divert --add **<INSERT FIREFOX ROOT DIRECTORY HERE>**/res/forms.css
```This should prevent the file from getting updated when Firefox does.  To remove this:

```
 sudo dpkg-divert --remove **<INSERT FIREFOX ROOT DIRECTORY HERE>**/res/forms.css
```Let me know if this technique works or not, I have not tested it.

[SIZE=4]_**Revisions**_[/SIZE]

**1.1** (March 24th 2007) - Fixes a bug where the widgets override the Ubuntu forum's default "Go!" button (to the right of the search box in the top right).  I'm assuming this bug could also appear on other sites but have not seen it.
**1.2** (June 8th 2007) - Fixes a bug that distorted buttons on this website: [http://www.extjs.com/deploy/ext/docs/index.html](http://www.extjs.com/deploy/ext/docs/index.html).
**1.5 BETA** - All past bug fixes have been made by removal of specific !important statements in the CSS that overrode web page defaults.  In this **BETA** I have removed all !important statements in the CSS.  Please report any problems.
**1.6 BETA** (June 9th 2007) - The removal of a few !important statements caused the corruption of radio buttons, checkboxes, and some text fields.  These !important statements have been edited back in to correct the problem.
**1.7 BETA** (June 9th 2007) - python-kiwi now automatically installs when you choose to run the graphic interface.  Added information for LKRaider to the "AUTHORS" file.
**1.8 BETA** (June 10th 2007) - Minor bug fixes: a typo in the graphic_installer file that may have caused the prompt to install python-kiwi to pop up when it shouldn't have as well as a fix for a bug where buttons would expand to the right and left when selected.
**1.9 BETA** (June 13th 2007) - Removes the margin from buttons so they wil be located in the right place.
**2.0 BETA** (June 14th 2007) - Added messages to the graphic installer and to the text installer instructing the user to restart firefox after installation or removal.  The python-kiwi package is now installed in an xterm terminal.  Fixed a bug in the graphic_installer script.  Minor changes to the install script (I removed a lot of messages to make the output of the script less verbose).
**2.1**  (June 17th 2007) - Increased text input border to 2 px and removed padding and margin from dropdowns.  Minor message changes to the script and graphic installer.  Minor changes to the README.  Removed borders from active (clicked on), disabled radio buttons.
**2.2** (June 19th 2007) - Added reinstallation option.  The graphic installer now tells you what type of change was completed (installation, removal, or reinstallation) instead of just "changes applied".  Install script modified so that it doesn't produce messages already being displayed by the GUI.  Fixed a re-occuring problem where disabled radio buttons were deformed.  Fixes the size of checkboxes at 12 pixels and radio buttons at 13 pixels in order to avoid the tiling of radio or checkbox images when larger sizes are used like in this website: [http://govsearch.publications.gov.au/search/search.cgi?collection=pubs&chksummary=chksummary&fscope=512&form=simple&fqp=1&query=book](http://govsearch.publications.gov.au/search/search.cgi?collection=pubs&chksummary=chksummary&fscope=512&form=simple&fqp=1&query=book). 
**2.3** (June 20th 2007) - Fixed bug #2: deformed radio buttons on [http://www.vietfinsv.net/](http://www.vietfinsv.net/) due to borders and background-colors that conflict with the site's defaults.
**2.4** (June 21st 2007) - Fixed bug #3: Deformed checkbox on [http://forums.invisionpower.com/index.php?act=Search](http://forums.invisionpower.com/index.php?act=Search).  Removed reinstallation (upgrade) option.  The install option now can install over previous installations of the Firefox Widgets.  Modified the installation script to make better use of functions.
**2.5** (July 9th 2007) - Radio buttons now gray out when disabled, show a slightly different color when active (pressed), and drop down menus show the correct button image.
**2.6** (July 11th 2007) - Fixed a bug where the image for the drop down menu did not display properly on [http://arcticmonkeys.trinitystreetdirect.com/](http://arcticmonkeys.trinitystreetdirect.com/). Borders are also now removed from dropdown menus.
**2.7** (August 6th 2007) - Improved the graphic installer so it now has a dropdown menu to select standard install paths from as well as the previous 5 installation or removal paths.  The number "5" is one that I picked and is set by the max_saved_path variable in ff_widgets.py.  You can change it if you like.  All installation/removal paths are saved in the "paths" file (path_file variable in ff_widgets.py if you want to change this name).  The browse button also now opens to the directory specified in the entry field.

Is there a .xpi available?

__________________

[CENTER][IMG]http://ubuntuforums.org/attachment.php?attachmentid=46333&d=1192382949[/IMG]
[/CENTER]

---

### Post by GhostZrydA on 2007-10-15
> **Frak said:**
> Try it again and see what happens.

No luck, no matter what method is used, so used the un-install , and then installed manually.

Opened the "forms.css" file in the /usr/lib/firefox/res folder.

Copied the contents of the "forms-extra.css" file to the bottom of "forms.css" saved, then copied the "form-widgets" folder to the "res" folder.

restart firefox, problem solved.!

Hope a new graphic installer is released for better gutsy support.

GhostZrydA

---

### Post by Frak on 2007-10-15
> **GhostZrydA said:**
> No luck, no matter what method is used, so used the un-install , and then installed manually.

Opened the "forms.css" file in the /usr/lib/firefox/res folder.

Copied the contents of the "forms-extra.css" file to the bottom of "forms.css" saved, then copied the "form-widgets" folder to the "res" folder.

restart firefox, problem solved.!

Hope a new graphic installer is released for better gutsy support.

GhostZrydA
I just had the same problem (Kubuntu Gutsy Gibbon)

I used the CLI installer and it worked fine (once I made a few modifications)

---

### Post by boolat on 2007-10-17
hello,

I have big  error in the console firefox.... ?
How to delete firefox ?
and install?

thx.

---

### Post by Frak on 2007-10-17
> **boolat said:**
> hello,

I have big  error in the console firefox.... ?
How to delete firefox ?
and install?

thx.
Try
```
sudo dpkg-reconfigure firefox
```

---

### Post by toasterofirony on 2007-10-18
Oh, brilliant. That fixes the problems I had after installing the Gutsy RC :)

---

### Post by veratyr on 2007-10-24
wow! that looks great. +1

---

### Post by crjackson on 2007-10-24
Works great for me too, but for some reason the google home page has the search buttons actually touching the bottom of the search box.  I have 3 machines of different configs. doing the same thing.

Does this happen to anyone else or only me?

---

### Post by swj on 2007-10-28
> **crjackson said:**
> Works great for me too, but for some reason the google home page has the search buttons actually touching the bottom of the search box.  I have 3 machines of different configs. doing the same thing.

Does this happen to anyone else or only me?

Its happens on my install too.  Gusty FF 2.0.0.8

In the preview posted in the thread, it does not touch.

---

### Post by ZacDavis on 2007-10-28
Same here, but otherwise this works great.

---

### Post by crjackson on 2007-10-28
I just did a fresh install of Gutsy and can't get the widgets to work.  The install runs and I've selected every available path.  It runs and installs but I doesn't change anything.  This is the first time this has happened for me.  What am I doing wrong?

What information to you need to help me fix this?

---

### Post by explemonk on 2007-10-29
The buttons are showing up right under the search box on Google for me, too, but they are also doing it without the new widgets installed, as well as in Konqueror and Opera on this install, and Firefox, IE, Opera, Netscape, and Safari on my Windows box.  I suspect it's Google's page that is the issue.

---

### Post by sleepyenglish on 2007-10-30
How come this doesn't come pre-installed with ubuntu, i cant see any down side in using it and its positives are clear to see.

---

### Post by michaelzap on 2007-10-30
> **crjackson said:**
> I just did a fresh install of Gutsy and can't get the widgets to work.  The install runs and I've selected every available path.  It runs and installs but I doesn't change anything.  This is the first time this has happened for me.  What am I doing wrong?

What information to you need to help me fix this?

The same thing was happening to me, but eventually I figured out that I had to install into opt/swiftfox and then it worked as usual.

---

### Post by nikoPSK on 2007-10-30
Umm, in my favourite site lifehacker the search has been screwed up.     I am sure this is due to the widgets... Is there any way to fix this? And I know this seems off topic but how do you attach more files once your post has been made?:)

---

### Post by coolen on 2007-10-30
> **sleepyenglish said:**
> How come this doesn't come pre-installed with ubuntu, i cant see any down side in using it and its positives are clear to see.

Firefox 3 will include much better integration with GTK (not sure about QT). You can download the beta from the Universe repo (I think), but it's still quite unstable. Mine crashed whenever I tried to change themes.

---

### Post by boeing777 on 2007-11-01
hi, i successfully installed it but there's one problem, my buttons seems to be inverted.  buttons are dark grey, hovering over a button makes it whiter,

---

### Post by nikoPSK on 2007-11-01
> **nikoPSK said:**
> Umm, in my favourite site lifehacker the search has been screwed up.     I am sure this is due to the widgets... Is there any way to fix this? And I know this seems off topic but how do you attach more files once your post has been made?:)

anyone?

---

### Post by explemonk on 2007-11-01
> **nikoPSK said:**
> 
[QUOTE=nikoPSK;3672321]Umm, in my favourite site lifehacker the search has been screwed up.     I am sure this is due to the widgets... Is there any way to fix this?

anyone?[/QUOTE]

Lifehacker looks fine on my install.  Are you sure it's the widget replacements causing it?  What happens if you uninstall the widgets and access the site?

---

### Post by Frak on 2007-11-01
Looks fine to me.

---

### Post by nikoPSK on 2007-11-01
the thing is cut in half and its hard to access. It is the widgets
I unistalled em. It was fine. Put em back, got the problem again.I like them better than the defaults so they stay. I want to know how to fix this though.

---

### Post by erlinux on 2007-11-03
does this work for epiphany?

---

### Post by Jegsy on 2007-11-03
Thanks for post.  I've just installed the widgets and Firefox looks more like the way it should. \\:D/ One thing I cannot understand though - why does Firefox not look as good by default in Linux/Ubuntu as it does in windows?

---

### Post by thelinx on 2007-11-03
@**nikoPSK**:

Looks fine to me too.

---

### Post by nikoPSK on 2007-11-03
AAAAAAAAAAAAAAAAAAAAAAAAARGH!!! No it isn't!!!! God let me circle it for you:

[[IMG]http://img35.picoodle.com/img/img35/6/11/3/t_Screenshotm_fd48267.png[/IMG]](http://www.picoodle.com/view.php?img=/6/11/3/f_Screenshotm_fd48267.png&srv=img35)

---

### Post by thelinx on 2007-11-04
Not messed up for me.

Also, is it just me, or is the text boxes and buttons on [FPSBanana]("http://www.fpsbanana.com/") wrongly bordered?

---

### Post by Twizz on 2007-11-05
Worked for me on 7.10 also.  I used the terminal install.

---

### Post by KhaaL on 2007-11-05
fatsheep, are you going to release a similiar thing for granparadiso (firefox 3.0) aswell? I think your version of widgets looks much nicer than FF 3.0 :)

---

### Post by markoloka on 2007-11-07
How do i make this widgets being there after kernel updates etc. or do i have to install after each update?? Don't wanna read all those pages in this topic 
Nice work anyway.

---

### Post by coolen on 2007-11-07
They should remain after kernel updates. Only update that might affect it is a Firefox update, and then I imagine only a major version release would break it.

---

### Post by Frak on 2007-11-07
> **markoloka said:**
> How do i make this widgets being there after kernel updates etc. or do i have to install after each update?? Don't wanna read all those pages in this topic 
Nice work anyway.
Firefox updates are what you worry about, kernel updates don't do anything to any other applications but the kernel itself.

Run
```
sudo dpkg-divert --add /usr/lib/firefox/res/forms.css
```

---

### Post by lydia Pack on 2007-11-08
Hi, looks great, but I was wondering is there any way that you can actually make the drop downs work like the safari menu ie have the contents of the list show up above and below the selected item, and when you use an alpha short cut on the keyboard to get to an item have it automatically enter in (rather than having to push enter).  Or is this a bit to much to ask of firefox?

---

### Post by crjackson on 2007-11-08
> **nikoPSK said:**
> AAAAAAAAAAAAAAAAAAAAAAAAARGH!!! No it isn't!!!! God let me circle it for you:

[[IMG]http://img35.picoodle.com/img/img35/6/11/3/t_Screenshotm_fd48267.png[/IMG]](http://www.picoodle.com/view.php?img=/6/11/3/f_Screenshotm_fd48267.png&srv=img35)

It works fine for me...

---

### Post by nikoPSK on 2007-11-08
well, it doesnt for me...:(

---

### Post by reppekjeks on 2007-11-08
Thank you so much for this fix. I've been wondering why this has been a problem and if there was a way to fix it, but now i don't have to anymore. It works perfectly. Thanks again. :)

---

### Post by disturbedite on 2007-11-14
kubuntu hardy/firefox 3.0-trunk (test daily builds)

ok, i've got several questions about this.

1.  i test daily builds of ff3 (trunk).  has anyone tested this with trunk & if so, what are/were your results?  does it work correctly with trunk?
2.  with trunk, if i were to use this, every day i updated ff wouldn't this be overwritten by the update?
3.  since i'm on kde (kubuntu), the preferred way to use this would be to use it along side prettywidgets like userundefined suggests, correct?
4.  in regards to question 3, is there anything else i can do to get tighter integration of ff with kde/qt?

---

### Post by Frak on 2007-11-14
For #4, you have to change your theme in KDE Control Center, such as what OpenSUSE uses.

---

### Post by thetimekeeper on 2007-11-14
Very cool work, worked flawlessly on mine, just ran the graphic install and I was set.

---

### Post by disturbedite on 2007-11-14
> **Frak said:**
> For #4, you have to change your theme in KDE Control Center, such as what OpenSUSE uses.
thanks for the response, but i know that.  i have the gtk option set to use my kde style in gtk apps, but beyond that type of thing is what i was wondering...

---

### Post by Frak on 2007-11-14
> **disturbedite said:**
> thanks for the response, but i know that.  i have the gtk option set to use my kde style in gtk apps, but beyond that type of thing is what i was wondering...
That's what I mean, for UI integration use a theme that complements GTK apps as well as its QT counterparts.

---

### Post by bettermentflux on 2007-11-14
Have you considered contacting the powers that be to see if the CSS bits can be incorporated into the upcoming Firefox 3?

I understand that they are making efforts to make the icons more gnome/tango-centric.

Alex Faaborg posted an update on their efforts today: [http://blog.mozilla.com/faaborg/2007/11/13/update-on-the-firefox-3-linux-theme/]("http://blog.mozilla.com/faaborg/2007/11/13/update-on-the-firefox-3-linux-theme/")

He may be the person to contact.

Cheers!

---

### Post by disturbedite on 2007-11-15
@ bettermentflux
yes they are.  it landed today actually.

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9b2pre) Gecko/2007111504 Minefield/3.0b2pre - Build ID: 2007111504

---

### Post by zhaoxmmusic on 2007-11-18
It's great except that I can not see any widgets when I tried to print the page..
I guess it is because of the alpha transparency of the PNGs? 
is it possible to use another set of widgets for print ?

---

### Post by djrobthaman on 2007-11-19
Quick question... and apologies if this has been asked and answered already and I skipped over it in my searchings, but can this package be installed properly in gutsy?

I used to use the alt widgets in feisty and loved it but keep having no luck since the upgrade.

Any info on how to get this to work correctly would be great.

Thanks

---

### Post by taisao on 2007-11-19
> **djrobthaman said:**
> Quick question... and apologies if this has been asked and answered already and I skipped over it in my searchings, but can this package be installed properly in gutsy?

I used to use the alt widgets in feisty and loved it but keep having no luck since the upgrade.

Any info on how to get this to work correctly would be great.

Thanks

I don't know if this work, but you could try:

[http://ubuntuforums.org/showthread.php?p=3539219&highlight=gutsy#post3539219](http://ubuntuforums.org/showthread.php?p=3539219&highlight=gutsy#post3539219)

---

### Post by crjackson on 2007-11-20
> **djrobthaman said:**
> Quick question... and apologies if this has been asked and answered already and I skipped over it in my searchings, but can this package be installed properly in gutsy?

I used to use the alt widgets in feisty and loved it but keep having no luck since the upgrade.

Any info on how to get this to work correctly would be great.

Thanks

It works fine for me in Gutsy.

---

### Post by winkman on 2007-11-24
Hi.. I've just installed the Firefox Widgets package on Firefox 2.0.0.8 using Ubuntu 7.10 (Gutsy) and it's working fantastically... :)
Thank you so much. (Now my forms look sexy... :P )
Mitch

---

### Post by Nicostarnux on 2007-11-27
Hello,

I'm using swiftfox too but mine is in /usr/lib/swiftfox ...

using [http://getswiftfox.com/builds/debian](http://getswiftfox.com/builds/debian) unstable non-free as a source on ubuntu 7.10

Works well ;)

---

### Post by Old Pink on 2007-11-27
This doesn't work on Firefox 2.0.0.10 
> Installing widgets to /usr/lib/firefox
Removing any previous installations of the widgets.
/usr/lib/firefox/res/form-widgets not found.  No action taken.
Removing the appended CSS code from /usr/lib/firefox/res/forms.css
Installing the images to /usr/lib/firefox/res/form-widgets.
cp: cannot stat `form-widgets': No such file or directory
Appending contents of forms-extra.css to /usr/lib/firefox/res/forms.css.
cat: forms-extra.css: No such file or directory
And no change after to buttons, etc. 

The [/usr/lib/firefox/res](file:///usr/lib/firefox/res/) folder has also changed a fair bit. 

Just a heads up. :)

---

### Post by Ramses de Norre on 2007-11-28
It works on firefox 2.0.0.10 (Arch linux version) here, the only thing I noticed is that the little arrow icon in a drop down menu isn't there anymore.
I just appended forms-extra.css to forms.css and copied the widgets directory into my res directory.

---

### Post by twright on 2007-11-29
this is great, maybe you should contact the automatix guys, this could be included with that

also this could be included in the ubufox addon

---

### Post by nikoPSK on 2007-11-29
wonderful, kudos. But why doesn't ubuntu/ mozilla adapt this for ubuntu? That would be great.

---

### Post by Vadi on 2007-11-29
One of the first things I did on a new install was get this. Excellent work.

---

### Post by tarntow on 2007-12-03
I have tried to reinstall firefox widgets_2.7  with the lastest release on swiftfox and firefox 2.0.0.11 but it's not been able to anything...??

---

### Post by jvc26 on 2007-12-03
Nice work, with a little alteration this also works perfectly on Fedora 8... finally, a nice firefox regardless of linux flavour :)
Il

---

### Post by Ssurgul on 2007-12-04
Sorry for the delay, but I just got Gutsy working the way I like on my workstation and opted to get your widgets installed finally.  They're looking spectacular!

---

### Post by pipebkn on 2007-12-04
great , i just installed on firefox 2.0.0.10 on ubuntu 2.04, and it work!!
thanks very much

---

### Post by en23 on 2007-12-04
I'm using a dual-boot system (ubuntu and vista) and was using the same profile folder for firefox on both systems so far.
widgets works fine with ubuntu, but firefox does not start using vista.
i don't really know how widgets works, but as far as i comprehend it is based on changed images and css code.
is there any way this could work with vista?
it really looks fine and i'd like to keep it.
Thanks

---

### Post by reppekjeks on 2007-12-04
> **tarntow said:**
> I have tried to reinstall firefox widgets_2.7  with the lastest release on swiftfox and firefox 2.0.0.11 but it's not been able to anything...??I was having some problems with that myself. I ran the graphical installer (GI) and after selecting install and clicking apply nothing happened. Nothing happened when selecting remove either. Tried rebooting but it didn't work either. Finally I deleted the firefox widgets_2.7 folder from my desktop and extracted the tar again. Ran the GI and everything was ok. So it seems that some files in my previous folder was broken. Have no idea how that happened. I know for a fact that it worked yesterday.:confused: Anyway, I'm sure it's not the same problem you're facing, but it might be worth a shot?

---

### Post by choppermad on 2007-12-06
Just installed 2.7...LOVE IT.

---

### Post by Frankly Francois on 2007-12-06
Hey, thanks a lot for your work! I too just installed 2.7. It's much, much better on the eyes.

---

### Post by tarntow on 2007-12-07
> **reppekjeks said:**
> I was having some problems with that myself. I ran the graphical installer (GI) and after selecting install and clicking apply nothing happened. Nothing happened when selecting remove either. Tried rebooting but it didn't work either. Finally I deleted the firefox widgets_2.7 folder from my desktop and extracted the tar again. Ran the GI and everything was ok. So it seems that some files in my previous folder was broken. Have no idea how that happened. I know for a fact that it worked yesterday.:confused: Anyway, I'm sure it's not the same problem you're facing, but it might be worth a shot?

your trick worked a treat..simple but effective...nice one

---

### Post by phatdad on 2007-12-07
Just for the record, have just done the widgets thing, and it has improved the look of things loads. Big thanks and well done from me! (Firefox v2.0.0.11 on Edgy)

---

### Post by volneilo on 2007-12-08
> **michaelzap said:**
> The same thing was happening to me, but eventually I figured out that I had to install into opt/swiftfox and then it worked as usual.

After hours, I was finally enlightened by  michaelzap's statement: installed it in /opt/firefox and... bingo! Before that, I've tried Firefox folders in /usr/lib and /usr/share, but nothing happens. Now it's ok for me too! Thanks a lot!

Firefox  2.0.0.8 in Gutsy here :) .

---

### Post by Arthur Archnix on 2007-12-08
You know what's amazing to me, is how long I've been using these widgets of yours, in all that time after all the updates they are still required. Have you considered submitting them to Firefox as a patch? In the meanwhile, I will continue to apply your beautiful fix.

Thanks.

---

### Post by Old Pink on 2007-12-10
This doesn't seem to work in Firefox 2.0.0.11.

In 2.0.0.10 I had to do the modification manually. In 2.0.0.11 it just won't work. At best I can get some disfiguration on buttons and radio buttons.

Time for 2.8?

---

### Post by Desigen on 2007-12-11
Hi, I would like to say thanks 

It's a great job

---

### Post by gary4gar on 2007-12-12
I can confirm it works great even on hardy alpha one with Firefox 2.0.0.11

---

### Post by radovan01 on 2007-12-12
there is an error downloading attached files:

XML Parsing Error: syntax error
Location: chrome://mozapps/content/downloads/unknownContentType.xul
Line Number 1, Column 4:   var mimeLiteral = gRDF.GetLiteral(aValueString);
---^

---

### Post by faical117 on 2007-12-12
thanks worked perfectly !:guitar:

---

### Post by tomauty on 2007-12-12
They should put this in the next Ubuntu release.

---

### Post by Gourgi on 2007-12-14
> **tomauty said:**
> They should put this in the next Ubuntu release.
+1

---

### Post by faical117 on 2007-12-19
wow Looks very good thanks :-)

---

### Post by ptgoce on 2007-12-24
Hi,
I have just installed this widgets in Mac OS X (10.5.1 - Leopard) and it works just fine, thanks a lot!
It is exactly what Firefox for Mac was missing.

If anyone wants to know how, just run 
./install -p=/Applications/Firefox.app/Contents/MacOS/ and than select option **1** :)

Great job man, thanks again!

---

### Post by kishorebudha on 2007-12-24
It doesn't seem to be working all that well for me (7.10 and Firefox 2.0.0.11). I inadvertently posted it here: [http://ubuntuforums.org/showthread.php?t=648095](http://ubuntuforums.org/showthread.php?t=648095)

---

### Post by v1ncent on 2007-12-29
It works perfect, but i have a problem: my GNOME Theme is BLACK, but i don't wanna see black widgets in Firefox... so, there is a way to fully customize widgets? maybe selecting a different gnome theme?

I would like to use this black theme in my system, but another one in Firefox, is that possible?

---

### Post by v1ncent on 2007-12-29
Something more simple: Is there a way to change the colors of the text and background from TEXT FIELDS in firefox?

---

### Post by taisao on 2007-12-30
> **v1ncent said:**
> Something more simple: Is there a way to change the colors of the text and background from TEXT FIELDS in firefox?

Yes. Using Stylish extension - [https://addons.mozilla.org/en-US/firefox/addon/2108](https://addons.mozilla.org/en-US/firefox/addon/2108)

---

### Post by v1ncent on 2007-12-30
Thank you taisao, it works perfect now.
=)

---

### Post by ikt on 2008-01-02
Is this stuff included in the release now?

---

### Post by ST.x on 2008-01-02
> **ikt said:**
> Is this stuff included in the release now?
This won't be needed for firefox 3.0 I think.

---

### Post by HIFH on 2008-01-04
Wow. Really nice.

Should be included as standard. Using on 7.10, fits much better than the original widgets. This is much more ubuntu, the defaults are more windows, too much windows.

Good job!

---

### Post by Xanatos Craven on 2008-01-06
> **ST.x said:**
> This won't be needed for firefox 3.0 I think.
Dunno about how others see it, but personally, I find Firefox 3's current rendering of form controls more irritating than the plain, (IMO) inoffensive ones Firefox 2 was spitting out. There should not be big grey borders around all the form controls, even if they're native. Mozilla probably won't, but I really hope they don't release the final version like that...

---

### Post by BL00dFox on 2008-01-06
This is awesome. The default firefox is too choppy-like and it feels uncomfortable! :guitar:

---

### Post by warnec on 2008-01-13
Fantastic! That's what I was missing in Gmail. Thank you.

---

### Post by nikoPSK on 2008-01-13
Does this work for mac's firefox? Like, I mean, a widget system. :confused:

---

### Post by Azakus on 2008-01-13
> **nikoPSK said:**
> Does this work for mac's firefox? Like, I mean, a widget system. :confused:

It should. You will definitely have to change the paths though. Mac firefox's install path is different than in Linux.
Other than that, the only thing that changes is the forms.css file, which should be platform neutral.

---

### Post by nikoPSK on 2008-01-13
> **Azakus said:**
> It should. You will definitely have to change the paths though. Mac firefox's install path is different than in Linux.
Other than that, the only thing that changes is the forms.css file, which should be platform neutral.

I'll be sure to give that a try. :)

---

### Post by cookies on 2008-01-13
> **Xanatos Craven said:**
> Dunno about how others see it, but personally, I find Firefox 3's current rendering of form controls more irritating than the plain, (IMO) inoffensive ones Firefox 2 was spitting out. There should not be big grey borders around all the form controls, even if they're native. Mozilla probably won't, but I really hope they don't release the final version like that...

It's your theme's fault. Back in the day (<_<) there was an issue with Clearlooks, so to fix it, the Clearlooks folks made a hack, which puts borders around buttons (they were not expecting native widgets in the HTML area), years passed, and the hack is no longer necessary, but people forgot about it, and it stuck. Most themes are based on Clearlooks, so their offending coding needs to be removed, but it is not all Firefox's fault.

---

### Post by porkepik on 2008-01-15
Huge thanks, it worked great in my ubuntu v7.10 :)

---

### Post by nikoPSK on 2008-01-15
How can I make my own  set? :)

nikoPSK

---

### Post by SanskritFritz on 2008-01-15
Thank you, works like charm. Very nice improvement!

---

### Post by herbster on 2008-01-21
Hi there, I am using this and I must say it's excellent, really makes the fields and outlines look great!

I am wondering how I can change the colour of buttons, though, as I'm using a dark theme and they were the grey-ish that they normally are before I installed this but now they appear as such:

[Please click to see](http://www.bobgill.net/gmail.jpg)

I'd like to make those buttons some shades lighter and text white or something for better visibility. TIA for any help!

---

### Post by ST.x on 2008-01-21
> **herbster said:**
> Hi there, I am using this and I must say it's excellent, really makes the fields and outlines look great!

I am wondering how I can change the colour of buttons, though, as I'm using a dark theme and they were the grey-ish that they normally are before I installed this but now they appear as such:

[Please click to see](http://www.bobgill.net/gmail.jpg)

I'd like to make those buttons some shades lighter and text white or something for better visibility. TIA for any help!
I think those buttons looks nice with your firefox theme actually, can you link me?

thanks

---

### Post by herbster on 2008-01-21
I'm using the NASA Space theme, grab it from addons.mozilla.org.

And yeah, I'd just like to make the text on the buttons whiter if anything :)

---

### Post by derixc on 2008-02-04
Thanks a lot man! You rock. I also have it posted on my blog. [Ubuntusite.com]("http://ubuntusite.com") This is very helpful

---

### Post by alxjl on 2008-02-05
It worked on my lappy running Gutsy. Thanks a lot.

---

### Post by dotancohen on 2008-02-07
The widgets make the form fields on this site look like smilies:
[http://what-is-what.com](http://what-is-what.com)
Note the "Google Search" buttons.

---

### Post by nikoPSK on 2008-02-07
> **dotancohen said:**
> The widgets make the form fields on this site look like smilies:
[http://what-is-what.com](http://what-is-what.com)
Note the "Google Search" buttons.
 
doesn't the new ff have better widgits (3)?

---

### Post by David Valentine on 2008-02-19
Thanks for this!  Now if I can just figure out how to increment your "thanks" count...

---

### Post by Vadi on 2008-02-19
I'm afraid you can't "thank" posts that were made before the "thanks" system was in. That includes the original post in here :|

Otherwise, it's the little medal bottom-right of the post.

---

### Post by anando on 2008-02-22
Worked perfectly - thanks a lot.

---

### Post by eFFeeMMe on 2008-02-23
They work like a charm, thanks!

---

### Post by MeURi on 2008-03-03
Thanks for the good work. Beautiful widgets are what I miss from Windows :-P

Just one thing: buttons seem to receive light from bottom-right, instead of top-left.
I mean: the one-pixel white line is placed on the right and bottom side of buttons, instead of being on the left and top (as I see from your screenshots). Did something go wrong during setup? I used version 2.7

Anyway, it's not that important, at least for me :-)

---

### Post by heartburnkid on 2008-03-18
Not too shabby, but the buttons don't look good under the Crux theme.  Is there a way to install everything but the buttons?

---

### Post by escobar_ on 2008-03-20
Thanks, my Flock looks so much better now. :)

---

### Post by Aikon- on 2008-03-27
I'm getting something a bit weird when I install the widgets.. actually, this has happened for as many versions as I can remember, I've just never bothered to post about it until now.

The spacing between text boxes and buttons seems to be off (see the attached image of Google, how the text boxes touch the bottom of the text box).

-Aikon

---

### Post by octaedro7 on 2008-04-06
It's not working on FFX 2.0.0.13, no widgets at all.
Screenshot attached

---

### Post by jjgomera on 2008-04-06
> **octaedro7 said:**
> It's not working on FFX 2.0.0.13, no widgets at all.
Screenshot attached
in your atatchment buttons and text file are correct, the problem is only with radiobuttons, isnt it?
its work fine for me with 2.0.0.13

---

### Post by octaedro7 on 2008-04-08
Good and bad news you gave me.
I really don't know what happens then :(.
I've tried several times and also tried with the defaul profile (no extensions or themes installed) and the problem is the same.  I've tried FF widgets a lot in the past, even the same version and have always worked.
Here is what I get when installing it:

```
gonzalo@latitude:~/Downloads/firefox_widgets_2.7$ ./install
1 ) Install Firefox widgets.
2 ) Remove Firefox widgets.
3 ) Specify a new installation/removal path.
4 ) Scroll the help file.
5 ) Exit.
Select an Option: 1
Installing widgets to /usr/lib/firefox
Removing any previous installations of the widgets.
/usr/lib/firefox/res/form-widgets not found.  No action taken.
The CSS does not appear to be installed.
/usr/lib/firefox/res/forms.css will not be edited.
Installing the images to /usr/lib/firefox/res/form-widgets.
[sudo] password for gonzalo:
Appending contents of forms-extra.css to /usr/lib/firefox/res/forms.css.
Installation complete.  Please restart Firefox.
```
Does any one have a clue?

Thanks in advance

---

### Post by jjgomera on 2008-04-08
you must check the correct path for firefox, that message terminal i think say that.

For example, i have firefox in /usr/lib/firefox but almost directory, including res are link to other location: /usr/share/firefox, so you could try to install with that path if it exists in your system

and i thik is fine for me:

---

### Post by Vadi on 2008-04-17
Not working in FF3 in 8.04 :(

---

### Post by Rui Pais on 2008-04-17
> **Vadi said:**
> Not working in FF3 in 8.04 :(

Firefox 3 use the widgets of the underlying DE (at least with gnome/xfce/e17 it uses the widgets of gtk theme).
It integrates better and don't require this workaround.

---

### Post by Vadi on 2008-04-17
I require it, I don't like the integration. Internet isn't the same as gnome, hence, the internet things with gnome buttons and such stuck on top of it looks really weird.

---

### Post by Rui Pais on 2008-04-17
> **Vadi said:**
> I require it, I don't like the integration. Internet isn't the same as gnome, hence, the internet things with gnome buttons and such stuck on top of it looks really weird.

Not gnome, gtk. And should be tuned according the gtk theme you have. 
Not sure how it reacts with QT or .NET... 
 
It's kind of strange that an application should look differently from the rest of DE just because it's surf Internet ;) 
I don't know if it's possible to change independently of DE widgets anyway... i read somewhere something about overriding default's .css options. 
Maybe doing a search on that....

---

### Post by z0mbie on 2008-04-17
So will Hardy make this script obsolete? :[ It's like my favorite script.

---

### Post by Vadi on 2008-04-17
Yes, it did. The program says it finished successfully but the buttons are still gtk ones (with non-standard web sizes). Ugh :(

Edit: it's not as much as hardy as firefox 3 I think. I am suspecting atm that ff3 uses different paths, and it might be fixed when ff3 is officially out.

---

### Post by bornagainpenguin on 2008-04-20
> **z0mbie said:**
> So will Hardy make this script obsolete? :[ It's like my favorite script.

Ditto this.

I know the Hardy Heron version of Firefox 3.0 is supposed to use the gtk theme's widgets, but quite frankly those look ugly to me when compared with the widgets in this thread.  Can someone please report how to patch this?

--bornagainpenguin

---

### Post by fhantazm on 2008-04-20
Works GREAT on my install of Hardy 8.04 and FF 3b5. No problems whatsoever! Thanks!

---

### Post by Vadi on 2008-04-21
:( I changed the path from the default usr/lib/firefox to the beta 5 one, but still nothing.

---

### Post by Aikon- on 2008-04-21
> **bornagainpenguin said:**
> Ditto this.

I know the Hardy Heron version of Firefox 3.0 is supposed to use the gtk theme's widgets, but quite frankly those look ugly to me when compared with the widgets in this thread.  Can someone please report how to patch this?

--bornagainpenguin

Solution.. make GTK widgets look like the ones in this script?

---

### Post by crjackson on 2008-04-27
I actually like the widgets on Firefox 3 so I won't be changing them anytime soon.  However, I still have several systems running Gutsy and these widgets are the only way to go.  thanks again...

---

### Post by fatsheep on 2008-05-04
Hey everyone.  Sorry I haven't checked this topic in a long time.  However,  I just upgraded to Hardy Heron 8.04 and I'm glad to find that Firefox 3 now has good integrated widgets.  

This script has always been a workaround.  Whenever I tried to fix one bug, several others would pop up.  Now I think the ideal solution is just to use the default widgets in Firefox 3.  I'm not sure why the people who have Gutsy are using this script?  It doesn't seem like this script is necessary any longer.

---

### Post by Frak on 2008-05-04
> **fatsheep said:**
> Hey everyone.  Sorry I haven't checked this topic in a long time.  However,  I just upgraded to Gutsy Gibbon 8.04 and I'm glad to find that Firefox 3 now has good integrated widgets.  

This script has always been a workaround.  Whenever I tried to fix one bug, several others would pop up.  Now I think the ideal solution is just to use the default widgets in Firefox 3.  I'm not sure why the people who have Gutsy are using this script?  It doesn't seem like this script is necessary any longer.
Do you mean Hardy?

---

### Post by HandyAndy on 2008-05-04
The widgets installer works perfectly on Swiftweasel too (Ubuntu 8.04 and Swiftweasel 2.0.0.14 from the repos).

The install path is:  /usr/local/swiftweasel

---

### Post by fatsheep on 2008-05-04
> **Frak said:**
> Do you mean Hardy?

Yea, my mistake.  All these stupid animal names... ;)

---

### Post by Vadi on 2008-05-05
It's just a matter of preference. I got used to the old ones, and like them better - because really, the un-gnome sizes of internet buttons + gnome pallette on them != integration. For me.

Can't get the script working again unfortunately, but thanks anyways for making it!

---

### Post by Xiong Chiamiov on 2008-05-06
> **fatsheep said:**
> Hey everyone.  Sorry I haven't checked this topic in a long time.  However,  I just upgraded to Hardy Heron 8.04 and I'm glad to find that Firefox 3 now has good integrated widgets.  

This script has always been a workaround.  Whenever I tried to fix one bug, several others would pop up.  Now I think the ideal solution is just to use the default widgets in Firefox 3.  I'm not sure why the people who have Gutsy are using this script?  It doesn't seem like this script is necessary any longer.
Just because I'm using Hardy doesn't mean I'm using a beta version of Firefox...

Yes, it's what's in the repos, but I'm using Swiftweasel anyway.  That's the reason I stopped using Swifterfox a while ago - it switched to using the 3-branch betas.

---

### Post by miwaypet on 2008-05-21
Just used it on swiftweasel. Worked perfectly. Thanks!

---

### Post by N'Jal on 2008-06-19
I use flock 2 beta, which ok yes, is based on firefox3 but the drop down widgets look the same as they did on firefox2. So I prefer using this script to tidy up the last of the gui elements that have not been fixed.

If someone is still maintaining it I would be grateful.

---

### Post by karlmp on 2008-07-08
just upgrade to hardy heron

---

### Post by hsa2 on 2008-11-27
I'm using this cool thing with swiftweasel. But there are some missing icons for read-only icons. For example, read only radio buttons are the ones that i could notice. Can you please add them to installation?

---

### Post by hsa2 on 2008-12-20
Anyone supporting this stuff anymore?

---

### Post by FlyingIsFun1217 on 2008-12-22
Probably not, since Firefox 3 on Linux has support to use native GTK widgets.

FlyingIsFun1217

---

