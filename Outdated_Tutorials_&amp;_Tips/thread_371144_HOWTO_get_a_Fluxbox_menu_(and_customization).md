---
title: "HOWTO: get a Fluxbox menu (and customization)"
date: 2007-02-26
forum: Outdated Tutorials &amp; Tips
---

### Post by RedSquirrel on 2007-02-26
[SIZE=3][COLOR=DarkRed][B][SIZE=4][COLOR=DarkOrange]Contents[/COLOR][/SIZE]
[/B][/COLOR][/SIZE]
 [SIZE=2][COLOR=DarkOrange][B]General Information

The Default Menu
[/B][/COLOR][/SIZE]
 [SIZE=2][COLOR=DarkOrange]**Tips for Creating a Custom Menu**[/COLOR][/SIZE]
 
[SIZE=2][COLOR=DarkOrange]**More Fluxbox Information and Links**[/COLOR][/SIZE]
 

[CENTER]*********
[/CENTER]


[SIZE=3][COLOR=DarkOrange]**General Information**[/COLOR][/SIZE]

[COLOR=DarkRed]**Basic Requirements for the Fluxbox Menu**[/COLOR]

The Fluxbox menu is created from a simple text file.

The default menu configuration file is created automatically using the [menu]("http://packages.ubuntu.com/lucid/menu") package.
 
The **menu** package is a *dependency* for fluxbox. If you installed the fluxbox package from the Ubuntu repositories, the **menu** package was installed automatically when you installed fluxbox.



[COLOR=DarkRed]**Editing the Fluxbox configuration files**[/COLOR]

The Fluxbox configuration files that you will be editing are located in the directory ~/.fluxbox.
 
 If you have another window manager or desktop environment installed on your system (Openbox, IceWM, GNOME, KDE, XFCE, etc.), you can edit all of your Fluxbox configuration files from there, if you prefer. The next time you run Fluxbox you will see the changes you made. 
 
If you are running Fluxbox and you edit the menu configuration file (~/.fluxbox/menu), you can see the changes you made by simply right-clicking on the desktop to bring up the menu; there is no need to restart Fluxbox to see the changes.
 

[COLOR=DarkRed]**Backups**[/COLOR]
 
 Before you edit a configuration file, it is a good idea to make a backup in case something goes wrong. 
 
 Example:
 
 ```
cp ~/.fluxbox/menu ~/.fluxbox/menu.backup
```[COLOR=DarkRed][B]



Fluxconf[/B][/COLOR]
 
 fluxconf has some nasty bugs, particularly in fluxkeys.

My recommendation is to avoid the program altogether and learn to configure Fluxbox by editing the configuration files directly.
 


[COLOR=DarkRed]**Testing**[/COLOR]

This tutorial has been tested on the following systems:


[LIST]
[*]Fluxbox 1.0.0 on Ubuntu 8.04
[*]Fluxbox 1.1.1 on Ubuntu 9.04
[*]Fluxbox 1.1.1 on Ubuntu 9.10
[*]Fluxbox 1.1.1 on Ubuntu 10.04
[/LIST]




[CENTER]*********
[/CENTER]



[SIZE=3][COLOR=DarkOrange]**The Default Menu**[/COLOR][/SIZE]

In your ~/.fluxbox directory, you have a file named **menu**. It is a text file.

The contents of the default menu file look like this:

```
[begin] (fluxbox)
[include] (/etc/X11/fluxbox/fluxbox-menu)
[end]

```As you can see, the default ~/.fluxbox/menu uses the contents of the file /etc/X11/fluxbox/fluxbox-menu as the menu.

If for any reason you need to recreate a default fluxbox menu, simply create a text file with the above three lines and save it as ~/.fluxbox/menu.

**Steps:**

1. Open the menu file using a text editor:

```
nano -w ~/.fluxbox/menu
```2. Copy and paste the following three lines:

```
[begin] (fluxbox)
[include] (/etc/X11/fluxbox/fluxbox-menu)
[end]

```3. Save and Close the file.





[SIZE=3][COLOR=DarkOrange]**Tips for Creating a Custom Menu**[/COLOR][/SIZE]

**[COLOR=DarkRed]Read the section from the man page that deals with the menu syntax[/COLOR]**

Run (in a terminal):
```
man fluxbox
```[COLOR=DarkRed][COLOR=black]
Look for the section entitled, "MENUS".
[/COLOR][/COLOR][COLOR=DarkRed][B][COLOR=black]
[/COLOR][/B][COLOR=black]Press "q" when you have finished reading the man page.[/COLOR][B][COLOR=black]



[/COLOR][/B][/COLOR][COLOR=DarkRed]**Sample file**[/COLOR]

The default menu is a good place to look for ideas. Make a copy of the  default menu:

```
cp /etc/X11/fluxbox/fluxbox-menu ~/.fluxbox/fluxbox-menu_ideas

```
[COLOR=DarkRed][B][COLOR=black]

[/COLOR]    Helpful Menu Sections[/B][/COLOR]

_Backgrounds Menu_

This will create a menu item that lists all of the backgrounds (wallpapers) in the directories you supply. Adjust the paths to suit wherever you store your wallpapers.

```
[submenu] (Backgrounds)
 [wallpapers] (/usr/share/backgrounds)
 [wallpapers] (~/.fluxbox/backgrounds)
 [wallpapers] (~/misc/wallpapers)
[end] 
```[ATTACH]139348[/ATTACH]



_Debian Menu_

Most of the applications on your system can be found in this menu. When you install new programs, the menu is updated automatically to include them.

```

[submenu] (Debian Menu) </usr/share/pixmaps/debian-logo.png>
[include] (/etc/X11/fluxbox/menudefs.hook)
[end]

```The Debian menu contains the same entries as the default menu, but without the Fluxbox configuration entries. You can see this in the following screenshots:

[ATTACH]139346[/ATTACH][ATTACH]139347[/ATTACH]
[U]



The Fluxbox Configuration Menu[/U]

Here is an example:

```

[submenu] (Fluxbox Menu)

      [config] (Configure) 

      [submenu] (System Styles) {Choose a style...}
        [stylesdir] (/usr/share/fluxbox/styles) 
      [end]

      [submenu] (User Styles) {Choose a style...}
        [stylesdir] (~/.fluxbox/styles)  
      [end] 

      [workspaces] (Workspace List) 
      [reconfig] (Reload config) 
      [restart] (Restart) 
      [exit] (Exit) 

[end]
```[ATTACH]139349[/ATTACH]
[CENTER]

[/CENTER]

**[COLOR=DarkRed]Icons[/COLOR]**

Locations for icon files that you may wish to use in your menu can be found by looking in the sample menu file mentioned above. You can start by looking in the following directories:

/usr/share/pixmaps
/usr/share/icons

A Fluxbox menu with icons:
[ATTACH]139345[/ATTACH]



[COLOR=DarkRed]**Menu delay/click to open or close submenus**[/COLOR]

(from the man page and the Fluxbox source code Changelog)

>    Menu Behavior

       The behavior of the submenus in a menu can be configured in the init
       file, with the following entries (default for both is 0):

       session.screen0.menuDelay: <msec>
       session.screen0.menuDelayClose: <msec>

    The menuDelay is the delay to open an submenu.

    The menuDelayClose is so you don't need to aim that much when
    you're moving the cursor to the submenu, over the item below
    or above, so it stays visible.

    "menuMode: Click" => this means you need to click on the menu item to open it.

    session.screen0.menuMode:  can be either Click or Delay (default: Delay)
    session.screen0.menuDelay:  in msec  (default: 0 )
    session.screen0.menuDelayClose: in msec (default: 0 )

    example:

    session.screen0.menuMode: Delay
    session.screen0.menuDelay: 400
    session.screen0.menuDelayClose: 300

    Notice how the menuDelay is a bit larger than menuCloseDelay.
    This is so the previous menu can close before you open the next.

[CENTER] 

*****
[/CENTER]
 


[SIZE=3][COLOR=DarkOrange]**More Fluxbox Information and Links**[/COLOR][/SIZE] 

The man pages for fluxbox and fluxstyle are definitely worth reading.

```
man fluxbox
``````
man fluxstyle
```Here are some links you might find helpful:

Main Fluxbox site
[http://fluxbox.org](http://fluxbox.org)

Fluxbox wiki (This is an excellent reference.)
[http://fluxbox-wiki.org](http://fluxbox-wiki.org)




[CENTER] 
[/CENTER]
 




**[SIZE=3] Credits[/SIZE]**

1. Fluxbox wiki -- [http://fluxbox-wiki.org](http://fluxbox-wiki.org)

2. posts on ubuntuforums.org (especially by yabbadabbadont and kerry_s)

3. the man page for fluxbox

4. the Changelog of the fluxbox source code

---

### Post by Syr0 on 2007-03-07
Thankyou! You've helped a lot!

---

### Post by RedSquirrel on 2007-03-08
Glad I could help.

Thank you for taking the time to say *Thank you*! I was having a pretty good day already and your post made it even better, Cheers! :)

---

### Post by celadine on 2007-03-13
Thanks for that info!  I'm a long time fluxbox/blackbox user from other distros, and that automatic menu config was driving me nuts.

---

### Post by RedSquirrel on 2007-03-19
Glad you found it useful. :)

---

### Post by bodhi.zazen on 2007-05-15
Great how-to RedSquirrel.

This is a common question.

You *might* want to mention fluxconf. It is in the ubuntu repository 

[Screenshot](http://devaux.fabien.free.fr/flux/)

Also, if anyone just wants to check out Fluxbox and what it can do, it is on the gparted cd, DSL, and wolvix. All 3 distro's have a polished, mauture Fluxbox interface.

Fluxbuntu is based on Ubuntu and is due out in a few weeks.

---

### Post by foureight84 on 2007-05-16
sweet tutorial dude.

---

### Post by RedSquirrel on 2007-05-18
> **bodhi.zazen said:**
> Great how-to RedSquirrel.

This is a common question.

Thanks. :)


> **bodhi.zazen said:**
>  You *might* want to mention fluxconf. It is in the ubuntu repository

Done.


> **foureight84 said:**
> sweet tutorial dude.

Thanks. :)

---

### Post by Thug14 on 2007-06-07
thnks a ton mate,ur how to really helped me a lot :cheers:

---

### Post by RedSquirrel on 2007-06-07
> **Thug14 said:**
> thnks a ton mate,ur how to really helped me a lot :cheers:
Glad I could help. Enjoy your Fluxbox! :)

---

### Post by JMO707 on 2007-06-08
Do you know of some way to have "arrows" to see the extra elements in a menu with lot of them?

I have tons of styles, and every time I pass the cursor over the styles entry, my whole screen is filled with the list.

---

### Post by RedSquirrel on 2007-06-08
> **JMO707 said:**
> Do you know of some way to have "arrows" to see the extra elements in a menu with lot of them?

I have tons of styles, and every time I pass the cursor over the styles entry, my whole screen is filled with the list.

I'm not sure if you can have it work the way you describe.

Probably the easiest thing to do would be to use more directories for your styles.

```
[submenu] (System Styles) {Choose a style...}
      [stylesdir] (/usr/local/share/fluxbox/styles) 
[end]
[submenu] (Styles) {Choose a style...}
      [stylesdir] (~/.fluxbox/styles) 
[end]
[submenu] (More Styles) {Choose a style...}
      [stylesdir] (~/path_to_styles) 
[end]
[submenu] (Even More Styles) {Choose a style...}
       [stylesdir] (~/path_to_more_styles) 
[end]

```

---

### Post by JMO707 on 2007-06-08
Thanks for the idea =)
Plus, d you know of some way to use fbsetbg or something else to rotate the wallpaper on every session start?

---

### Post by yabbadabbadont on 2007-06-08
> **JMO707 said:**
> Thanks for the idea =)
Plus, d you know of some way to use fbsetbg or something else to rotate the wallpaper on every session start?

I have a set of scripts and one small program that will do that.  They can also rotate the wallpaper every XXX seconds if you like.  (it's a parameter)  I had to write my own since my collection has grown to over 56,000 images.  (Yes, I used the correct number of zeros.  ;))  I would be happy to share if you like.

Edit: Share the scripts that is...  :D

Edit2: I believe that the SVN version of fluxbox supports setting a random wallpaper on every startup using the new "background" options in style files.  You would just need to setup an "overlay" file in ~/.fluxbox that contained the correct options.  (I think.  I'll have to check the docs to be sure.)

---

### Post by kerry_s on 2007-06-08
> **JMO707 said:**
> Thanks for the idea =)
Plus, d you know of some way to use fbsetbg or something else to rotate the wallpaper on every session start?

try looking at the chbg program-> [http://chbg.sourceforge.net/about.html](http://chbg.sourceforge.net/about.html)
it's in the repo's

sudo apt-get install chbg

i never used it, but heard it was nice.

---

### Post by yabbadabbadont on 2007-06-08
Just checked the docs for the SVN fluxbox.  It does support random wallpapers.
```
BACKGROUND
       Every style must specify the background option. If you don&#8217;t want your style to change the user&#8217;s background, then
       use &#8216;background: none&#8217;. The options &#8216;centered&#8217;, &#8216;aspect&#8217;, &#8216;tiled&#8217;, and &#8216;fullscreen&#8217; require the &#8216;background.pixmap&#8217;
       resource to contain a valid file name. The &#8216;random&#8217; option requires &#8216;background.pixmap&#8217; to contain a valid directory
       name. For these options, fluxbox(1) will call fbsetbg(1) to set the background. The options &#8216;gradient&#8217;, &#8216;solid&#8217;, and
       &#8216;mod&#8217; all require &#8216;background.color&#8217; to be set. &#8216;gradient&#8217; and &#8216;mod&#8217; both require &#8216;background.colorTo&#8217;. &#8216;mod&#8217;
       requires &#8216;background.modX&#8217; and &#8216;background.modY&#8217; to be set as well. These options will be passed to fbsetroot(1) to
       set the background.

           background: centered|aspect|tiled|fullscreen|random|solid|gradient <texture>|mod|none
           background.pixmap: <file or directory>
           background.color: <color>
           background.colorTo: <color>
           background.modX: <integer>
           background.modY: <integer>

```
Just put the correct options into ~/.fluxbox/overlay and it should work fine.

Edit: So you would have something like this in your overlay file:
```
background: random
background.pixmap: /path/to/your/wallpaper/directory
```

---

### Post by RedSquirrel on 2007-06-08
The man pages for *fluxbox* and *fluxstyle* contain a wealth of information:

```
man fluxbox | col -b > fluxbox_manpage.txt
``````
man fluxstyle | col -b > fluxstyle_manpage.txt
```

:)

---

### Post by JMO707 on 2007-06-08
It worked!

What a great/small desktop way!

---

### Post by krandun on 2007-06-15
Wow! Thanks for the how-to. Now I just have to spend a few weeks figuring out every command on my system and adding them to a menu. Bliss! ^.^

One thing I haven't been able to find yet. On the default Ubuntu Gnome install, there's the big red "power" button that brings up a shutdown menu with "log off" "switch user" "hibernate" "restart" &c, whatever on it. Is there a way to get something like that in FluxBox, either on a menu or on the panel (if that's the right word, I'm very new to Flux)?

---

### Post by yabbadabbadont on 2007-06-15
> **krandun said:**
> Wow! Thanks for the how-to. Now I just have to spend a few weeks figuring out every command on my system and adding them to a menu. Bliss! ^.^

One thing I haven't been able to find yet. On the default Ubuntu Gnome install, there's the big red "power" button that brings up a shutdown menu with "log off" "switch user" "hibernate" "restart" &c, whatever on it. Is there a way to get something like that in FluxBox, either on a menu or on the panel (if that's the right word, I'm very new to Flux)?

If you built fluxbox from SVN, then there is a script called "fluxbox-generate_menu" you can use to generate your menu.  Personally, I made a copy of it and keep it in my home directory so that I can edit it and add new applications that it doesn't detect by default.

---

### Post by RedSquirrel on 2007-06-15
> **krandun said:**
> Wow! Thanks for the how-to. Now I just have to spend a few weeks figuring out every command on my system and adding them to a menu. Bliss! ^.^

If you use "Method B", the majority of the commands you'll use most often will be placed in your menu automatically. If something is missing, you can always add it to ~/.fluxbox/usermenu so that fluxbox-generate_menu will pick it up.


> **krandun said:**
> One thing I haven't been able to find yet. On the default Ubuntu Gnome install, there's the big red "power" button that brings up a shutdown menu with "log off" "switch user" "hibernate" "restart" &c, whatever on it. Is there a way to get something like that in FluxBox, either on a menu or on the panel (if that's the right word, I'm very new to Flux)?

This isn't something that I would have a need for, so I'm not sure if there's a simple solution. There is a bruteforce way of doing this, but it will take a bit of work. For shutdown and restart, you would have to create a group that has permissions to run 'shutdown' without sudo. I'm not sure about "hibernate" and "switch user". Maybe some laptop users who use Fluxbox would have some ideas about setting up something like that. If no one sees your question in this thread, you might be best off starting a new thread or doing a search for doing this sort of thing in Fluxbox. Sorry I can't be more helpful on this. 


> **yabbadabbadont said:**
> If you built fluxbox from SVN, then there is a script called "fluxbox-generate_menu" you can use to generate your menu. Personally, I made a copy of it and keep it in my home directory so that I can edit it and add new applications that it doesn't detect by default.

fluxbox-generate_menu is also available in the Fluxbox from the repositories. However, it's in a compressed file. The instructions for using fluxbox-generate_menu with the Fluxbox from the repositories are at the end of the HOWTO.

---

### Post by yabbadabbadont on 2007-06-15
You caught me...  I've never read your howto.  :D  (I've never needed to ;))  Otherwise I would have suggested to krandun that (s)he read it a little more closely.  :lol:

---

### Post by RedSquirrel on 2007-06-15
> **yabbadabbadont said:**
> You caught me...  I've never read your howto.  :D  (I've never needed to ;))  Otherwise I would have suggested to krandun that (s)he read it a little more closely.  :lol:

No worries. I just wanted to make it clear that fluxbox-generate_menu is available to those who use the version from the repositories (i.e., you don't have to compile your own just to get fluxbox-generate_menu). ;)

---

### Post by yabbadabbadont on 2007-06-15
> **RedSquirrel said:**
> No worries. I just wanted to make it clear that fluxbox-generate_menu is available to those who use the version from the repositories (i.e., you don't have to compile your own just to get fluxbox-generate_menu). ;)

I actually didn't know that until you said it earlier.  I always use my customized version though, so I really never had a need to look.  I think I'm going to make a modified version of it that creates a menu in the format that is needed for fbpanel this weekend.  The fluxbox menu structure and that used by fbpanel are not that far apart, so it shouldn't be very difficult.  I need to pull down and build fluxbox first though since I'm currently using openbox.  I did a whirlwind tour through three different linux distributions this week and am still getting my feisty install back up to speed.

---

### Post by RedSquirrel on 2007-06-15
> **yabbadabbadont said:**
> I actually didn't know that until you said it earlier.  I always use my customized version though, so I really never had a need to look.  I think I'm going to make a modified version of it that creates a menu in the format that is needed for fbpanel this weekend.  The fluxbox menu structure and that used by fbpanel are not that far apart, so it shouldn't be very difficult.  I need to pull down and build fluxbox first though since I'm currently using openbox.  I did a whirlwind tour through three different linux distributions this week and am still getting my feisty install back up to speed.

Sounds like a fun project. I would be interested in hearing how it goes. I tried out fbpanel a while ago, but I only used it very briefly because I'm generally satisfied with the standard Fluxbox toolbar.

---

### Post by bodhi.zazen on 2007-06-16
I have been working on a script to auto-generate a fluxbox menu.

It is a bash script. There is a custom header and footer and the middle is generated by menumaker.

The script then continues and icons are added.

Here is a link to the script: [http://forum.live-developers.org/index.php/topic,66.msg433.html#msg433](http://forum.live-developers.org/index.php/topic,66.msg433.html#msg433)

The current version of the script is slightly different and the ~/.fluxbox/wolvixmenu contains 3 enteries.

include top
include mid
include bottom

The top and bottom are static and can be in ~/.fluxbox or /usr/share/fluxbox
The mid is generated and kept in ~/.fluxbox

Included in the top menu is a menu entry to regenerate this menu (for use after adding software). Also included are custom entries to turn conky on/off , desktop icons on/off, and switch languages.  The languages are because wolvix is a live CD and could be stripped from Ubuntu, or if you are multilingual you would have a fast switcher.

The bottom panel is primarily a link to the wolvix control panel (WCP) and shutdown/reboot

Just though I would throw this information at you to see if it may be of any use to you :twisted:


If you would like to see it in action PM your email and I will send you an updated version of the script (plus the skeletons for the top and bottom panel).  :popcorn:


Once it is done I will likely generate one for Ubuntu.


The point is this script will generate a fluxbox menu with a number of creature comforts, including icons for the menu enteries.

If you are more adventerous, take a look at wolvix. 1.0.5 Hunter has one of the finest default configurations of fluxbox you will find on any distro. wolvix 1.1.0 is in beta right now, and RC1 is imminent. The beta is very nice as well, but the fluxbox customizations are not yet in the builds.

_Note_: If you use icons in your menu, you will notice they change size when you change themes.

_Solution_: Use your overlay. Add this entry to ~/.fluxbox/overlay :
```
menu.ItemHeight: 20
```
_Note_: You can go smaller 16 or larger 22, 24 if you like.

~ bash wizards : feel free to add words of wisdom regarding the script ;)

---

### Post by yabbadabbadont on 2007-06-16
> **bodhi.zazen said:**
> ...

The script included with fluxbox already provides icons for the menu if you use the "-is" option.  The only real difference that I see is that MenuMaker is used to generate most of the menu in this case.  You can get a similar effect by including /etc/X11/fluxbox/menudefs.hook in your ~/.fluxbox/usermenu when you use the default fluxbox-generate_menu script to create your menu.

Just FYI.  ;)

---

### Post by bodhi.zazen on 2007-06-21
> **yabbadabbadont said:**
> The script included with fluxbox already provides icons for the menu if you use the "-is" option.  The only real difference that I see is that MenuMaker is used to generate most of the menu in this case.  You can get a similar effect by including /etc/X11/fluxbox/menudefs.hook in your ~/.fluxbox/usermenu when you use the default fluxbox-generate_menu script to create your menu.

Just FYI.  ;)

Does fluxbox-generate_menu look this good ?

[[IMG]http://img46.imageshack.us/img46/2761/fluxiconsep5.th.png[/IMG]](http://img46.imageshack.us/my.php?image=fluxiconsep5.png)

---

### Post by yabbadabbadont on 2007-06-21
> **bodhi.zazen said:**
> Does fluxbox-generate_menu look this good ?
It can.  After all, "good", is a subjective term.  "Eye of the beholder" and all that.  ;)

---

### Post by gary4gar on 2007-08-01
Thanks a ton!
helped a lot

---

### Post by RedSquirrel on 2007-08-02
> **gary4gar said:**
> Thanks a ton!
helped a lot

You are most welcome. :)

---

### Post by RedSquirrel on 2007-08-02
Over the past couple of days, I have revised the custom menu section rather substantially and added a Tips section. I hope it helps (and doesn't hurt). ;)

---

### Post by yabbadabbadont on 2007-08-02
Nicely done.  I'm glad that you did it as I didn't have the patience to write all of that up.  (nor the skill ;))

To paraphrase Steve Martin: "Woo hoo!  I was credited in a Howto.  I am somebody!"  :D

---

### Post by RedSquirrel on 2007-08-02
> **yabbadabbadont said:**
> Nicely done.  I'm glad that you did it as I didn't have the patience to write all of that up.  (nor the skill ;))

Thanks. It took longer than I would have thought, but it was definitely time for an update. [Documentation? What's that? ;)]


> **yabbadabbadont said:**
> To paraphrase Steve Martin: "Woo hoo!  I was credited in a Howto.  I am somebody!"  :D

:)

What is that from? (I've been living in a cave, I guess...)

---

### Post by yabbadabbadont on 2007-08-02
> **RedSquirrel said:**
> What is that from? (I've been living in a cave, I guess...)

I was referring to his movie, "The Jerk", when he is running through the streets yelling that "he is someone" because his name was listed in the new phone book.

---

### Post by SadaraX on 2007-08-04
This is an impressive HowTo. Congratulations.

I thought I might just add my little piece of information to this, though it is only partially related. This is a little trick that I got from the fluxbox developers a couple of years ago.

This will allow you to embed the menu in your taskbar. 

1) Get the fluxbox source files.
2) Edit fluxbox/src/ToolFactory.cc
3) Find the line that reads:

```
} else if (name == "prevworkspace" ||
           name == "nextworkspace") {
```

4). Add 'name == "rootmenu" || ' to that section. It should look like this:

```
} else if (name == "rootmenu" ||
           name == "prevworkspace" ||
           name == "nextworkspace") {
```

5. Recompile and install.
6. In your ~/.fluxbox/init, you can now add the word ***rootmenu*** to the session.screen0.toolbar.tools line. For example:

```
session.screen0.toolbar.tools:  iconbar, systemtray, prevwindow, nextwindow, clock
```
Change it to this:
```
session.screen0.toolbar.tools:  rootmenu, iconbar, systemtray, prevwindow, nextwindow, clock
```

This has been confirmed to work all all major releases of Fluxbox since 0.9x until their latest release candidate.

---

### Post by RedSquirrel on 2007-08-04
> **SadaraX said:**
> This is an impressive HowTo. Congratulations.

Thanks. :)


> **SadaraX said:**
>  I thought I might just add my little piece of information to this, though it is only partially related. This is a little trick that I got from the fluxbox developers a couple of years ago.

This will allow you to embed the menu in your taskbar. 


This is a great idea. Thanks for mentioning it.

I don't use the toolbar on my setup (just conky and fbpager) but I'll try this out a little later today when I update to the latest SVN version.

---

### Post by RedSquirrel on 2007-08-04
OK, I compiled the SVN 4997 code with that modification to ToolFactory.cc and it works fine. I put mine on the right side of the clock for the screenshot.

It puts a 'left arrow' button on the toolbar for the menu, but this can be changed to a 'right arrow' by modifying the code a little more.

```
...

    } else if ([COLOR=Red]name == "rootmenu" || [/COLOR] name == "nextworkspace" ||  name == "prevworkspace") {
        FbTk::RefCount<FbTk::Command> cmd(CommandParser::instance().parseLine(name));
        if (*cmd == 0) // we need a command
            return 0;

        // TODO maybe direction of arrows should depend on toolbar layout ?
        FbTk::FbDrawable::TriangleType arrow_type = FbTk::FbDrawable::LEFT;
        if (name == "nextworkspace" **[COLOR=Blue]|| name == "rootmenu"[/COLOR]**)
            arrow_type = FbTk::FbDrawable::RIGHT;

...


```The blue text is the additional code to make a right arrow instead of a left one. That should work, but I haven't recompiled to test it (and I probably won't right away since I *hide* the toolbar on my setup).

Screenshots... The first one is what the toolbar looks like and the second one is what happens when I clicked on the arrow button (gee, my menu popped up :)).

---

### Post by SadaraX on 2007-08-04
Glad it worked for you. This is not especially useful unless you want to have a 'normal' desktop feel with the application menu embedded in your taskbar. Or if you have a system without a right-click button for your mouse (like a PDA).

---

### Post by mojoman on 2007-09-08
Nice Howto, it taught me some useful new tricks.

I think the fluxbox menu is great, and though it can be an extra workload to update it manually I think this is more than compensated by the flexibility it offers. However, one thing that I really want in my menu is the option to shutdown and reboot the computer, not just to restart fluxbox or log out. This, like just about anything else in fluxbox, can be configured but it requires a little more tweaking than adding the regular menu stuff. Here's how I went about it.

First, I have my menu manually configured with the most common apps first (terminal, firefox, thunderbird and thunar), then three submenus (Multimedia, Internet, Office) with the apps I use fairly frequent, then I got the Debian menu (which contain all applications), the Fluxbox menu and then I got the submenu called Quit. That part of the menu looks like this:

```
   [submenu] (Quit)
      [exit] (Log out) 
      [exec] (Reboot) {sudo /sbin/shutdown -r now} <>
      [exec] (Shutdown) {sudo /sbin/shutdown -h now} <>
   [end]
```

Now, the 'Log out' part is the standard from the fluxbox menu so there's no need to define it. The commands for Reboot and Shutdown must be configured as above. Also, they are root commands which means that when you issue them in the terminal you'll be prompted for a password. So, just adding it to menu will issue the correct command to the system but it won't be executed. In order for it to be executed you must allow the user to use the command 'shutdown' without password. This is done in the file /etc/sudoers

Now, be *really careful* when you edit this file. Even to have a peak at it (e.g. cat /etc/sudoers) requires you to have administrative privileges and this should be a warning to anyone. To edit it you must use the visudo command as root:

```
# visudo -f /etc/sudoers
```

What you must do is to allow your ordinary user to shutdown the computer as root without password, and to do absolutely nothing else without a password. In my file, I've added these line under the relevant sections:
```

# Cmnd alias specification
Cmnd_Alias      SHUTDOWN = /sbin/shutdown
```

```
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

mojoman ALL = SHUTDOWN

mojoman ALL = NOPASSWD: SHUTDOWN
```
(The %admin ALL=(ALL) ALL is there by default, I just include it for reference.)

Add these lines but with your users username. Save and exit. You might have to reboot for all changes to take effect but from here on you'll be able to reboot and shutdown your computer with the fluxbox menu, no questions asked.

I got the information on how to give ordinary users root privileges [_here_.]("http://www.debian-administration.org/articles/33")

Hope you find it useful
/mojoman

---

### Post by TeaSwigger on 2007-09-15
Hello mojoman, thanks for the great tip. I followed your suggestions and it works great. What I was doing before was:

```
 [exec] (Shutdown) {konsole -T "Shutdown" -e sudo shutdown now -h}
```

Of course I'm using fluxbox on KDE/Kubuntu and Gnome/ubuntu users would have to change it appropriately. What this does is make the terminal window pop up prompting for the password (if you've not entered it in the past 15mins; if you have it proceeds with shutdown without waiting to open a terminal window). Enter the pass and it shuts down. Just a suggestion for anyone not willing or inclined to edit sudoers. :)

---

### Post by TeaSwigger on 2007-09-15
Thanks again to you RedSquirrel. I've now fashioned a custom menu. One thing I've done is to separate the menus into separate files and include a submenu with a command to open the menu(s) and key user files like startup and backgrounds in mousepad for quick and easy editing. No rummaging into ~/.fluxbox etc :)

Now I have a couple of questions. You know those separators you can do with text, the [nop] ones? Is it possible to choose a color just for them? They don't stand out very legibly in some skins. Secondly but not leastly I installed feh for backgrounds and it works except for .bmps and largeish .pngs. It gives me this error:

```
fbsetbg: Something went wrong while setting the wallpaper.
Run 'wmsetbg -s -S ~/Pictures/wallpapers/drad/Chiana.png' from an xterm to find out what.
```

and doing so it sez:

```
could not find image file used in texture.
```

How can I fix this so I can use png & bmp files?

---

### Post by TeaSwigger on 2007-09-16
Didn't mean to do 3 posts in a row but I messed up trying to get the screenshot in the prior post. Here it is fwiw :)

[ATTACH]43595[/ATTACH]

---

### Post by SadaraX on 2007-09-16
> **TeaSwigger said:**
> Hello mojoman, thanks for the great tip. I followed your suggestions and it works great. What I was doing before was:

```
 [exec] (Shutdown) {konsole /sbin/shutdown -h now}
```

Of course I'm using fluxbox on KDE/Kubuntu and Gnome/ubuntu users would have to change it appropriately. What this does is make the terminal window pop up prompting for the password (if you've not entered it in the past 15mins; if you have it proceeds with shutdown without waiting to open a terminal window). Enter the pass and it shuts down. Just a suggestion for anyone not willing or inclined to edit sudoers. :)

You can get around the problem of passwords for shutdowns and restarts by modifying the /etc/sudoes files.

```

sudo nano /etc/sudoers # or whatever text editor you prefer instead of nano, like kate/emacs/gedit

```

Add the following line:

```

# Passwordless shutdown and reboot
my_user_name ALL=(ALL) NOPASSWD: /sbin/shutdown -h now, /sbin/reboot

```

Now user my_user_name can run 'sudo reboot' or 'sudo halt' without a password

You can modify your menu for the following options:

```

      [exec] (Log out)
      [exec] (Reboot) {sudo /sbin/reboot}
      [exec] (Shutdown) {sudo /sbin/shutdown -h now}

```

This will not require passwords and it will be immediate.

---

### Post by TeaSwigger on 2007-09-16
Yeah mojoman beat you to it on page 4 hehe... I was just posting a thanks and the other method for anyone not willing to modify the sudoers file and/or wanting a pass prompt first. But the thoughts appreciated :)

---

### Post by mojoman on 2007-09-16
> **TeaSwigger said:**
> Hello mojoman, thanks for the great tip. I followed your suggestions and it works great. What I was doing before was:

```
 [exec] (Shutdown) {konsole -T "Shutdown" -e sudo shutdown now -h}
```

Of course I'm using fluxbox on KDE/Kubuntu and Gnome/ubuntu users would have to change it appropriately. What this does is make the terminal window pop up prompting for the password (if you've not entered it in the past 15mins; if you have it proceeds with shutdown without waiting to open a terminal window). Enter the pass and it shuts down. Just a suggestion for anyone not willing or inclined to edit sudoers. :)

You're welcome. Glad it worked. I use this setup on both my desktop and an old laptop of mine and I'm prettty happy with it. I wasn't aware of the possibility of being promted for the password but that's a good solution if one doesn't want to edit the sudoers file.

/mojoman

---

### Post by yabbadabbadont on 2007-09-16
> **TeaSwigger said:**
> How can I fix this so I can use png & bmp files?

Install the eterm package since it includes the Esetroot utility.  It is the first background setting program that fbsetbg looks for and can handle pretty much anything that you can throw at it.

---

### Post by TeaSwigger on 2007-09-16
Thanks yabbadabbadont, I installed eterm and it's all working. I've added a bunch of directories of walls to fluxbox submenus for easy browsing and desktop decorating pleasure. Do we use this "eterm" in ubuntu / fluxbox or are we only after the bg setter? And is it ok for me to go on and on here about fluxbox or is there another forum or anything I "should" be dropping into for fluxbox talk? Anyway I'm really enjoying trying fluxbox on both of my PCs now :)

---

### Post by yabbadabbadont on 2007-09-16
I've got a few too many wallpapers to include them in fluxbox submenus...  (47,180 to be exact :D)  I use my own wallpaper randomizer scripts to rotate my wallpaper every five minutes.  You can use Eterm as your terminal if you like.  It has some nice "blingy" features, but the version in the repositories doesn't seem to include UTF-8 support.  (I'm not even sure if it *can* support UTF-8 )  I just install it to get Esetroot.  You'll need to ask RedSquirrel about "going on and on" about Fluxbox in this thread as he created it.  I doubt that he will mind though.

---

### Post by RedSquirrel on 2007-09-17
> **TeaSwigger said:**
> Thanks again to you RedSquirrel. 

My pleasure. :)

> **TeaSwigger said:**
> I've now fashioned a custom menu. One thing I've done is to separate the menus into separate files and include a submenu with a command to open the menu(s) and key user files like startup and backgrounds in mousepad for quick and easy editing. No rummaging into ~/.fluxbox etc :)

That's a good idea.

I spend a lot of time in the terminal, so for me to rummage around in ~/.fluxbox is not a big problem. I find myself typing the string "vim .fluxbox/..." quite often since there are always little adjustments to make. ;)

Actually, I don't even use my menu that often since I have keyboard shortcuts setup for most of my applications.



> **TeaSwigger said:**
> You know those separators you can do with text, the [nop] ones? Is it possible to choose a color just for them? They don't stand out very legibly in some skins. 

I don't think it's possible to change the color of individual elements in the menu. You can only change the "text color", which is the color that applies to all text, including the separators [separator] and [nop]. Just look in the theme's configuration file for:

```


menu.title.textColor:        <color>
menu.frame.textColor:        <color>
menu.hilite.textColor:        <color>


```By the way, that's a nice menu you have there. I like your wallpaper too. Where did you get it?

Oh, and I don't mind you "going on and on" about Fluxbox here.

---

### Post by RedSquirrel on 2007-09-17
I added some links to the HOWTO regarding shutdown/reboot and embedding the menu in the toolbar. Many thanks to mojoman, TeaSwigger, and SadaraX for posting this information.

I was aware of the "editing the sudoers file" technique for the shutdown/reboot when I wrote the HOWTO but I hesitated to add it. At this point though, it looks like a worthwhile thing to do. It's not something I use myself, but there will be Fluxbox users who will want to know how to do this and having it in this HOWTO will save them from having to search elsewhere. ;) 

I appreciate TeaSwigger's suggestion because it doesn't involve editing the sudoers file (as mentioned by TeaSwigger, some users may not want to do that :)).

---

### Post by yabbadabbadont on 2007-09-17
Just a quick note about directly editing the /etc/sudoers file.  The "correct" way to do this is to use the "visudo" command.  It will prompt you for your password, and then open the sudoers file using the system default editor.  (as defined by the /etc/alternatives/editor symlink)  The advantage of this, is that visudo will check the syntax of the file when you try to save/exit the editor, and will display an error message if there is a problem.  That way you are guaranteed to not end up with a non-functioning sudoer's file.

---

### Post by RedSquirrel on 2007-09-17
> **yabbadabbadont said:**
> Just a quick note about directly editing the /etc/sudoers file.  The "correct" way to do this is to use the "visudo" command.  It will prompt you for your password, and then open the sudoers file using the system default editor.  (as defined by the /etc/alternatives/editor symlink)  The advantage of this, is that visudo will check the syntax of the file when you try to save/exit the editor, and will display an error message if there is a problem.  That way you are guaranteed to not end up with a non-functioning sudoer's file.
Thanks for mentioning this.

```
sudo visudo
```

---

### Post by yabbadabbadont on 2007-09-17
Doh!  I forgot the sudo...  :oops:

I'll go and lock myself in the penitents cell now.

---

### Post by RedSquirrel on 2007-09-17
> **yabbadabbadont said:**
> I'll go and lock myself in the penitents cell now.

:lol:

No need. The rest of your post was very helpful. ;)

---

### Post by TeaSwigger on 2007-09-18
Gosh now I feel... helpful hehe 

I'm really enjoying using Fluxbox. Using FB and KDE together I get some great apps with a very nice speed on modest hardware, with the convenience and excellence of Kubuntu. It helps to lighten the load on my "bad" PC (the celery), making it possible to enjoy the sophisticated Kubuntu OS and apps with a more tolerable speed. On my "good" PC - 933mhz PIII 384mb ram nVidia card - it absolutely flies considering. I'd certainly suggest it for anyone with modest hardware specs or just wanting to enjoy the speed and simplicity it offers compared to the more richly featured desktops. A very attractive setup.

And creating / editing the menu "by hand" helps one gain familiarity with their setup... plus it has had good theraputic value ;)

The photo's from good ole webshots, "King Penguins at the Foot of Fortuna Glacier, Cumberland Sound, South Georgia Island." A search found it [here]("http://entertainment.webshots.com/photo/2857826650101680981AEksaF"). :)

And of course after all this I've forgotten the question I came here to ask. Oh well! A fine HowTo that just gets better :)

---

### Post by TeaSwigger on 2007-09-18
Ah! I remembered the question. How do I (even can I) specify a "run from" in a fluxbox menu entry? In KDE I can specify a "work path" if/when needed. In the terminal I can 'cd' to the location and run it from there. Let me give a hypothetical example:

We have a fictitious app called a jool2sik character converter which we wish to open via a menu entry. Let's say we have to specify the file path to the executable. Let's say that the converter lives in a section of our home directory, at /home/earth/Lame/jool2sik (good thing our virtual homes are all split level eh? :p ). Ordinarily it'd go like so:

```
[exec] (Jool2Sik Converter) {/home/earth/Lame/jool2sik} </usr/share/pixmaps/rdhd.png>
```

Groovy. But let's say that it must be executed from in that directory or it'll shed a thousand 'rdhr.temp' files or something all over your main home directory or might even come screaming to a halt if loaded. Can we make a Fluxbox menu entry for such an annoying case?

---

### Post by mojoman on 2007-09-19
> **RedSquirrel said:**
> I added some links to the HOWTO regarding shutdown/reboot and embedding the menu in the toolbar. Many thanks to mojoman, TeaSwigger, and SadaraX for posting this information.
...
I appreciate TeaSwigger's suggestion because it doesn't involve editing the sudoers file (as mentioned by TeaSwigger, some users may not want to do that :)).

I'm glad you found it useful. I was a bit hesitant to add it at first, partly because editing sudo is not always such a bright idea and partly because I didn't want to intrude on your howto but then I'd guessed that you wouldn't mind (too much at any rate :wink:). 

Anyway, since we're now allowed to go on about fluxbox and there seem to be quite a few subscribers who know their thing about it I thought I'd pop a quick costumization question. :)

I use fbpager. Nifty little tool, especially when started docked. However, I'm not 100% satisfied with my setup as I would like fbpager to be inegrated in the toolbar. Now, it's placed bottom center and it works fairly good but I'd rather have it placed at the bottom left. If I do, it covers the window switcher. Also, if I open a lot of windows, the minimized workspace windows show up behind fbpager. I'll enclose my fbpager file and a screenshot (the screenshot is quite wide as I got a twinview setup. The part with the toolbar is visible on my monitor. The other part is viewed with my HD-projector).

Any ideas on this is much appreciated.

Cheers
/mojoman

---

### Post by yabbadabbadont on 2007-09-19
> **TeaSwigger said:**
> ```
[exec] (Jool2Sik Converter) {/home/earth/Lame/jool2sik} </usr/share/pixmaps/rdhd.png>
```


Try:
```
[exec] (Jool2Sik Converter) {(cd /home/earth/Lame && jool2sik)} </usr/share/pixmaps/rdhd.png>
```
If nothing else, create a simple shell script that cd's into the directory and launches the program, then call the shell script from the menu.

---

### Post by yabbadabbadont on 2007-09-19
> **mojoman said:**
> I'm glad you found it useful. I was a bit hesitant to add it at first, partly because editing sudo is not always such a bright idea and partly because I didn't want to intrude on your howto but then I'd guessed that you wouldn't mind (too much at any rate :wink:). 

Anyway, since we're now allowed to go on about fluxbox and there seem to be quite a few subscribers who know their thing about it I thought I'd pop a quick costumization question. :)

I use fbpager. Nifty little tool, especially when started docked. However, I'm not 100% satisfied with my setup as I would like fbpager to be inegrated in the toolbar. Now, it's placed bottom center and it works fairly good but I'd rather have it placed at the bottom left. If I do, it covers the window switcher. Also, if I open a lot of windows, the minimized workspace windows show up behind fbpager. I'll enclose my fbpager file and a screenshot (the screenshot is quite wide as I got a twinview setup. The part with the toolbar is visible on my monitor. The other part is viewed with my HD-projector).

Any ideas on this is much appreciated.

Cheers
/mojoman

Configure fbpager to startup in the bottom left corner, or change your slit position to bottom left if fbpager is being started withdrawn.  Then change the toolbar properties so that it is located on the bottom right and its width percentage is less than 100.

---

### Post by mojoman on 2007-09-19
> **yabbadabbadont said:**
> Configure fbpager to startup in the bottom left corner, or change your slit position to bottom left if fbpager is being started withdrawn.  Then change the toolbar properties so that it is located on the bottom right and its width percentage is less than 100.

Thanks for the tips. It''s a fairly good work-around and I've been thinking along those lines myself but it still doesn't integrate fbpager in the toolbar. I'm not sure if it's at all possible though, I might be asking for too much here...

---

### Post by yabbadabbadont on 2007-09-19
> **mojoman said:**
> Thanks for the tips. It''s a fairly good work-around and I've been thinking along those lines myself but it still doesn't integrate fbpager in the toolbar. I'm not sure if it's at all possible though, I might be asking for too much here...

The toolbar in fluxbox does not include a pager, so there isn't any way to "integrate" one.  If you must have a pager in a toolbar/panel, you might see about running fbpanel in place of the fluxbox toolbar.  It provides a pager plugin by default.

---

### Post by mojoman on 2007-09-19
> **yabbadabbadont said:**
> The toolbar in fluxbox does not include a pager, so there isn't any way to "integrate" one.  If you must have a pager in a toolbar/panel, you might see about running fbpanel in place of the fluxbox toolbar.  It provides a pager plugin by default.

Didn't know that. I might just have a look at fbpanel. Thanks!

---

### Post by TeaSwigger on 2007-09-19
> **yabbadabbadont said:**
> Try:
```
[exec] (Jool2Sik Converter) {(cd /home/earth/Lame && jool2sik)} </usr/share/pixmaps/rdhd.png>
```
If nothing else, create a simple shell script that cd's into the directory and launches the program, then call the shell script from the menu.

aaah thanks! I'll give it a better workout tomorrow but just trying it real quick, it seems to work perfectly. :D

---

### Post by RedSquirrel on 2007-10-09
I added some information about setting up the Debian menu for use with a compiled version of Fluxbox and I have included some brief instructions for compiling Fluxbox (from the tarball and from SVN code).

---

### Post by mojoman on 2007-10-10
> **RedSquirrel said:**
> OK, I compiled the SVN 4997 code with that modification to ToolFactory.cc and it works fine. I put mine on the right side of the clock for the screenshot.

It puts a 'left arrow' button on the toolbar for the menu, but this can be changed to a 'right arrow' by modifying the code a little more.

```
...

    } else if ([COLOR=Red]name == "rootmenu" || [/COLOR] name == "nextworkspace" ||  name == "prevworkspace") {
        FbTk::RefCount<FbTk::Command> cmd(CommandParser::instance().parseLine(name));
        if (*cmd == 0) // we need a command
            return 0;

        // TODO maybe direction of arrows should depend on toolbar layout ?
        FbTk::FbDrawable::TriangleType arrow_type = FbTk::FbDrawable::LEFT;
        if (name == "nextworkspace" **[COLOR=Blue]|| name == "rootmenu"[/COLOR]**)
            arrow_type = FbTk::FbDrawable::RIGHT;

...


```The blue text is the additional code to make a right arrow instead of a left one. That should work, but I haven't recompiled to test it (and I probably won't right away since I *hide* the toolbar on my setup).

Screenshots... The first one is what the toolbar looks like and the second one is what happens when I clicked on the arrow button (gee, my menu popped up :)).

Hm, I've been trying both this and the version without changing the arrows direction but I don't seem to get it right. Or rather, I don't get it at all. There's no arrow, no menu, no nothing. 

I downloaded the tarball, extracted it, made the relevant changes, saved, ./configure, make, # make install. I restart and Fluxbox works nicely but without the expected and very longed after menu in the toolbar. It seem to be the right version.

Any take on what might be wrong? Do I need to do it in console mode and start by uninstalling fluxbox first? (Can't see why but hey, I tend to grasp for straws when I'm at my wits end).

best regards
/mojoman

---

### Post by RedSquirrel on 2007-10-10
> **mojoman said:**
> Hm, I've been trying both this and the version without changing the arrows direction but I don't seem to get it right. Or rather, I don't get it at all. There's no arrow, no menu, no nothing. 

I downloaded the tarball, extracted it, made the relevant changes, saved, ./configure, make, # make install. I restart and Fluxbox works nicely but without the expected and very longed after menu in the toolbar. It seem to be the right version.

Any take on what might be wrong? Do I need to do it in console mode and start by uninstalling fluxbox first? (Can't see why but hey, I tend to grasp for straws when I'm at my wits end).

best regards
/mojoman

I'm going to ask some boring questions first and then if the problem is not related to any of these, I'll build from the tarball to make sure it works...

Is there only one version of Fluxbox on your system? Make sure you're running the one you compiled. You can check with the following command in a terminal:

```
fluxbox -i
```

The compiled version gets installed in /usr/local/bin by default (/usr/local/bin/startfluxbox script). So make sure you're **not** running the script at /usr/bin/startfluxbox.

Did you remember to make the changes to ~/.fluxbox/init? You have to add the word **rootmenu** to the line **session.screen0.toolbar.tools:**.

If these things are not the issue, then tell me which tarball you used and I'll build it and see what happens. I'm assuming you've built the latest tarball (1.0.0) but I just want to be sure. ;)

---

### Post by mojoman on 2007-10-11
> **RedSquirrel said:**
> I'm going to ask some boring questions first and then if the problem is not related to any of these, I'll build from the tarball to make sure it works...

Is there only one version of Fluxbox on your system? Make sure you're running the one you compiled. You can check with the following command in a terminal:

```
fluxbox -i
```

The compiled version gets installed in /usr/local/bin by default (/usr/local/bin/startfluxbox script). So make sure you're **not** running the script at /usr/bin/startfluxbox.

Did you remember to make the changes to ~/.fluxbox/init? You have to add the word **rootmenu** to the line **session.screen0.toolbar.tools:**.

If these things are not the issue, then tell me which tarball you used and I'll build it and see what happens. I'm assuming you've built the latest tarball (1.0.0) but I just want to be sure. ;)

Hi, and thanks for the reply.

I should have been a bit more specific. Sorry about that.

As for the answers to your questions they are:
No, it's not the only fluxbox on my system (I got one from the repos to but I thought the new version replaced that one).
Yes, it's the 1.0.0 that's running.
Most likely I'm running the startup  script from /usr/local/bin/startfluxbox.
Yes, I've made the necessary changes in the ~/fluxbox/init file. 

So, maybe I'm using the wrong startup? Which file points to the startup file? One odd thing is that I've made other changes as well to my init file (e.g. removed the clock) that are implemented and this clearly indicates that the correct init file is read, right? Could using the wrong startup script mean that just the root menu change in the init file is not implemented?

/mojoman

---

### Post by RedSquirrel on 2007-10-11
The /usr/local/bin/startfluxbox script runs your ~/.fluxbox/startup file (or creates the file ~/.fluxbox/startup if it doesn't exist).

Inside ~/.fluxbox/startup is where you call the binary /usr/local/bin/fluxbox (or /usr/bin/fluxbox in the case of the version from the repositories). If you specify the absolute pathname (e.g., /usr/local/bin/fluxbox or /usr/bin/fluxbox) then you know for sure which one you're running. If you have two versions installed and you just call fluxbox (or exec fluxbox) without specifying a path, then the system will use the one that it finds in _your_ path. The one in /usr/local/bin is found first, which you can check by examining your path with:

```
echo $PATH
```When you're running Fluxbox and you fire up a terminal and run 'fluxbox -i' and it reports 1.0.0, then clearly you are running your compiled version and it should use all of the usual configuration files found in ~/.fluxbox.

Note: The compiled version is stored in /usr/local/bin (by default), whereas the version from the repositories is in /usr/bin. Hence, the compiled version does NOT replace the old version, and you end up with two separate versions installed. This is not the end of the world, but it is a tad redundant I suppose. :grin:

When I install a compiled version, I use checkinstall to build a deb package from my compiled code. If I had an older version installed (one of my own debs or the version from the repositories), I remove that first, then I install my own deb. Have a look at the compiling procedure I included recently in the HOWTO. Feel free to ask any questions.

I'll build v. 1.0.0 from the tarball as soon as I can and see what happens. I'm kind of busy with some other tasks at the moment, but I'll get back to you... ;)

---

### Post by mojoman on 2007-10-11
Ok, I've been playing around and managed to narrow the problem down. First of all, I built a .deb-file from source following your howto. Excellent job!

Now, uninstalling fluxbox and installing the .deb meant that fluxbox wouldn't start. I had a look in the startup-file and sure enough, it looked for the binary in the wrong place. After changing path both to fbsetroot and fluxbox it started BUT it wrecked total havoc on my poor conky by starting it over and over again (about 100 times per second or so), doing a horrible flood attack on whatismyip.org. I had also changed fluxbox to startfluxbox in the startup file and when I accidentally forgot to reset this when I installed the repo version again it did the same so I realized that the flood attack was connected to using startfluxbox instead of fluxbox. I went back to the .deb but this time had the path to /usr/local/bin/fluxbox instead of /usr/local/bin/startfluxbox and it didn't flood whatismyip.org BUT it still crashed. The reason seem to be that when whatismyip is resolved it, for some reason I can't figure out, calls fluxbox and it does so with the wrong path, i.e. /usr/bin/fluxbox. The problem is that I don't know where to edit this because this isn't in the .conkyrc file. 

Here's the content of my .xsession-errors

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "mojoman"
/etc/gdm/Xsession: Beginning session setup...
--20:42:48--  http://whatismyip.org/
           => `-'
Resolving whatismyip.org... exec: 50: /usr/bin/fluxbox: not found
```

Now, if I - or someone smarter then I - could only figure out where to edit this I'm sure I could get over this hurdle so I could have a look at the next problem that surely will follow ;-)

Any ideas on this?

cheers
/mojoman

---

### Post by RedSquirrel on 2007-10-11
I would guess there's still a problem with your ~/.fluxbox/startup. It has about 50 lines.

```
exec: 50: /usr/bin/fluxbox: not found
```

I would check line 50 of your ~/.fluxbox/startup file. Post the file here if you like.

By the way, why and where are you using that whatismy ip.org thing? 

Does your menu in the toolbar work now, or is that still an issue?

---

### Post by mojoman on 2007-10-11
> **RedSquirrel said:**
> I would guess there's still a problem with your ~/.fluxbox/startup. It has about 50 lines.

```
exec: 50: /usr/bin/fluxbox: not found
```

I would check line 50 of your ~/.fluxbox/startup file. Post the file here if you like.

By the way, why and where are you using that whatismy ip.org thing? 

Does your menu in the toolbar work now, or is that still an issue?

Ok, good call. I had the wrong path to the fluxbox binary there but it's working now and it's starting with the menu in the toolbar as well. 

I'm using wget to query whatismyip.org in order to have conky display my external IP, just to get a heads up if it has changed (it rarely does but I like to know when it does).

Anyway, it all works now. Thanks for the help!
/mojoman

EDIT: On a sidenote, my system now claims that the package 'menu' is not needed and can be removed but isn't that the debian menu?

---

### Post by yabbadabbadont on 2007-10-11
> **mojoman said:**
> EDIT: On a sidenote, my system now claims that the package 'menu' is not needed and can be removed but isn't that the debian menu?

Yes, it is the debian menu.  To get rid of the warning run
```
sudo apt-mark unmarkauto menu
```

---

### Post by mojoman on 2007-10-12
> **yabbadabbadont said:**
> Yes, it is the debian menu.  To get rid of the warning run
```
sudo apt-mark unmarkauto menu
```

Yup, that worked. Thanks. It's a bit weird  that the debian menu is singled out by autoremove as not needed. I mean, it's not just something that other applications might depend on, it's an application in it's own right as well.

/mojoman

---

### Post by RedSquirrel on 2007-10-12
> **mojoman said:**
> Yup, that worked. Thanks. It's a bit weird  that the debian menu is singled out by autoremove as not needed. I mean, it's not just something that other applications might depend on, it's an application in it's own right as well.

/mojoman
I think it has to do with the fact that the menu package was installed *automatically* to satisfy a dependency of the fluxbox package from the repositories. Once you remove this fluxbox package, apt considers the menu package to be unecessary.

You could remove the fluxbox package you installed from the repositories along with its dependencies and then install menu again. If you have installed menu on its own (sudo apt-get install menu), then apt shouldn't list it as "no longer needed". yabbadabbadont's solution is obviously much faster. :)

---

### Post by mojoman on 2007-10-12
> **RedSquirrel said:**
> I think it has to do with the fact that the menu package was installed *automatically* to satisfy a dependency of the fluxbox package from the repositories. Once you remove this fluxbox package, apt considers the menu package to be unecessary.

You could remove the fluxbox package you installed from the repositories along with its dependencies and then install menu again. If you have installed menu on its own (sudo apt-get install menu), then apt shouldn't list it as "no longer needed". yabbadabbadont's solution is obviously much faster. :)

Hehe, no, unistalling it and installing it that won't be necessary. I already solved it with yabbadabbadont's solution and was just curious about why it was marked as not needed. Now I know. Thanks.

---

### Post by cknight on 2007-10-18
Some folks may be interested in the fbrun program (not sure if this comes with fluxbox installed from the repositories or if I installed it myslef).  But, you can add this to your menu file like this:

```
[exec] (Run...) {fbrun}
```

Choosing 'Run...' in your menu will pop up a window in which you can type a terminal command.  Great if you're too lazy to pull up a terminal or just want fast access for a single command.  If you tweak the command, this can also pre-populate part (or all) of the command which you can then edit manually.  

Finally, you could also assign fbrun to a key-binding for a quick launcher.

Thanks for this tutorial by the way.  I'm still amazed at how friendly this community is!  

Speaking of tutorials, any plans to offer a key-binding tutorial?  The basics are, well, fairly basic, but I'm sure that there's a lot of great things you could do with keys which I've not come across/understood.

---

### Post by RedSquirrel on 2007-10-18
> **cknight said:**
> Some folks may be interested in the fbrun program (not sure if this comes with fluxbox installed from the repositories or if I installed it myslef).  

It's included with fluxbox.

> **cknight said:**
> But, you can add this to your menu file like this:

```
[exec] (Run...) {fbrun}
```Choosing 'Run...' in your menu will pop up a window in which you can type a terminal command.  Great if you're too lazy to pull up a terminal or just want fast access for a single command.  If you tweak the command, this can also pre-populate part (or all) of the command which you can then edit manually.  

Finally, you could also assign fbrun to a key-binding for a quick launcher.

Thanks for the reminder about this. I'll add it to the Howto later.

> **cknight said:**
>  Thanks for this tutorial by the way.  I'm still amazed at how friendly this community is!  

You're welcome and I agree, the community is nice. :)

> **cknight said:**
>  Speaking of tutorials, any plans to offer a key-binding tutorial?  The basics are, well, fairly basic, but I'm sure that there's a lot of great things you could do with keys which I've not come across/understood.

I'm not sure. They're not too hard. The fluxbox man page covers this pretty well. 

```
man fluxbox
```The wiki is also worth a look:

[http://fluxbox-wiki.org/index.php/Keyboard_shortcuts](http://fluxbox-wiki.org/index.php/Keyboard_shortcuts)

---

### Post by mojoman on 2007-10-19
This question might be half-way off-topic but I'll post it anyway as it's at least related to fluxbox menu. I use the Debian menu as a submenu on my fluxbox, running on feisty (which uses menu 2.1.32). After I installed deluge from a .deb I updated the menus and it showed up in the Debian menu. However, it was under a separate heading, called applications (all other are under the heading apps). Now, I also installed deluge on my Lenny, and it uses menu 2.1.36 and in that version there is no heading called apps, only applications. So, it seems to me as if the deb I installed was compiled for a later version of menu, and I therefore end up with a mixture, having both applications and apps  in the Debian menu. I had a look in the .desktop file to see if that decided where it showed up but couldn't find anything there to edit to solve this. Does any of you guys have a take on this?

Thanks
/mojoman

---

### Post by RedSquirrel on 2007-10-22
I have added a *simple* procedure to setup a better menu on Gutsy Gibbon since the default menu is somewhat incomplete.

---

### Post by RedSquirrel on 2007-10-22
> **mojoman said:**
> This question might be half-way off-topic but I'll post it anyway as it's at least related to fluxbox menu. I use the Debian menu as a submenu on my fluxbox, running on feisty (which uses menu 2.1.32). After I installed deluge from a .deb I updated the menus and it showed up in the Debian menu. However, it was under a separate heading, called applications (all other are under the heading apps). Now, I also installed deluge on my Lenny, and it uses menu 2.1.36 and in that version there is no heading called apps, only applications. So, it seems to me as if the deb I installed was compiled for a later version of menu, and I therefore end up with a mixture, having both applications and apps  in the Debian menu. I had a look in the .desktop file to see if that decided where it showed up but couldn't find anything there to edit to solve this. Does any of you guys have a take on this?

Thanks
/mojoman

Sorry for not responding sooner. I don't really have a take on this. I think you're right. It has something to do with newer versions of the menu package and perhaps the standards for the .desktop files (and the fact that we're on Ubuntu, which is *Debian-based*, but not Debian). 

I haven't really looked into this too deeply because it isn't hard to make a custom Fluxbox menu. However, it is a shame that the Debian menu (and hence the default Fluxbox menu) is missing entries and has both "apps" and "applications" categories. If I hear anything more about this I'll post. ;)

---

### Post by varinavarmit on 2007-10-25
Thank you so much for posting this information, especially the command line for allowing the right mouse click to function once again in bringing up the fluxbox menu.

---

### Post by RedSquirrel on 2007-10-25
> **varinavarmit said:**
> Thank you so much for posting this information, especially the command line for allowing the right mouse click to function once again in bringing up the fluxbox menu.
You're welcome. I'm glad it helped. :)

---

### Post by kc8hr on 2007-10-25
Hi,

Thanks for supplying the fluxbox-update_menus.gz file. The latest Gutsy package does not include it.

Great tutorial, too!
Tim

---

### Post by RedSquirrel on 2007-10-26
> **kc8hr said:**
> Thanks for supplying the fluxbox-update_menus.gz file. The latest Gutsy package does not include it. 

You're welcome. I was surprised that it wasn't included in the package. It's pretty handy. 

> **kc8hr said:**
>  Great tutorial, too!


Thanks. :)

---

### Post by 3dxtrip on 2007-11-04
Many thanks

I use Linux Mint on a Celeron with 128 MB and fluxbox works fine...
Right clic after install works, added entries for applications no listed.

Here mi Desktop (icons with idesk)
[[IMG]http://img114.imageshack.us/img114/5531/fluxdesksy2.th.png[/IMG]](http://img114.imageshack.us/my.php?image=fluxdesksy2.png)

Muchas gracias!!!

---

### Post by RedSquirrel on 2007-11-04
> **3dxtrip said:**
> Many thanks

I use Linux Mint on a Celeron with 128 MB and fluxbox works fine...
Right clic after install works, added entries for applications no listed.

Here mi Desktop (icons with idesk)
 ... 
Muchas gracias!!!

You're welcome. Nice screenshot. :)

---

### Post by jviscosi on 2007-11-04
Seems like the Fluxbox packages got a bit botched up in Gutsy.  I wonder why.  My focus problem in SVN doesn't seem so bad now ...

---

### Post by RedSquirrel on 2007-11-05
> **jviscosi said:**
> Seems like the Fluxbox packages got a bit botched up in Gutsy.  I wonder why.  My focus problem in SVN doesn't seem so bad now ...
Yeah, the fluxbox package isn't in very good shape (considering that it's missing XShape extension support, I guess that's a pun). I'm glad compiling fluxbox is fast & easy so we don't have to worry too much.

Which SVN version are you running now? (I've chosen to play with Arch for a while and I'm running its fluxbox package [1.0.0] which is just fine. :))

---

### Post by jviscosi on 2007-11-05
> **RedSquirrel said:**
> Yeah, the fluxbox package isn't in very good shape (considering that it's missing XShape extension support, I guess that's a pun).

*SNORT*  :lolflag:

> **RedSquirrel said:**
> Which SVN version are you running now? (I've chosen to play with Arch for a while and I'm running its fluxbox package [1.0.0] which is just fine. :))

I'm on 5118, about to upgrade to 5122.  I'll let you know how it works out.

EDIT:  The focus problem still exists in 5122.  Eh, if it really annoyed me THAT much, I would revert back to 5089 or so.

---

### Post by RedSquirrel on 2007-11-07
> **jviscosi said:**
> EDIT:  The focus problem still exists in 5122.  Eh, if it really annoyed me THAT much, I would revert back to 5089 or so.

Yeah, I think I'll just stick with the stable version for now. It does what I need it to do. I have a few other things to tinker with for the next few days at least. ;)

---

### Post by Anubis on 2007-11-12
So like, when are the package maintainers, who "broke" the fluxbox package, going to fix it (have the fluxbox-menu-generator returned)? More to the point, when are they going to package it so that once fluxbox is installed, it will have a full menu? I mean, Mandrake linux could do this years ago. I just don't understand how stuff like this could happen. People use Fluxbox, so much so, there is a Fluxbuntu coming out. Fluxbuntu, but the regular fluxbox package is not even packaged right? I'll conclude because I'm pissed, and don't want this to sound like troll, or flame bait. Thank you for the how to! Most of all, thanks for providing the flux-menu-gen script!

---

### Post by jviscosi on 2007-11-12
> **Anubis said:**
> So like, when are the package maintainers, who "broke" the fluxbox package, going to fix it (have the fluxbox-menu-generator returned)? More to the point, when are they going to package it so that once fluxbox is installed, it will have a full menu?

That's actually a good question.  I had a look and there are bug reports filed for the various Fluxbox package problems (the missing right-click menu issue is listed as a bug in the "menu" package rather than in Flux), but there's no apparent ETA on fixes.

---

### Post by RedSquirrel on 2007-11-12
> **Anubis said:**
> So like, when are the package maintainers, who "broke" the fluxbox package, going to fix it (have the fluxbox-menu-generator returned)? More to the point, when are they going to package it so that once fluxbox is installed, it will have a full menu? ... Thank you for the how to! Most of all, thanks for providing the flux-menu-gen script!

You're welcome. :)

I agree with your comments. It's disappointing that the fluxbox package isn't in good shape on Ubuntu, especially since Ubuntu is a binary distribution and not everyone will want to compile their own fluxbox package. With regard to an updated package appearing in the repositories, I'm not holding my breath.

---

### Post by jviscosi on 2007-11-12
Red Squirrel, the Fluxbox programmers figured out the click focus problem in SVN.  I posted their explanation in [the other Fluxbox thread]("http://ubuntuforums.org/showthread.php?p=3760070#post3760070") where we were discussing SVN.  I'm sure you'll see it there, but figured I'd mention it here as I had brought it up earlier.

---

### Post by RedSquirrel on 2007-11-13
> **jviscosi said:**
> Red Squirrel, the Fluxbox programmers figured out the click focus problem in SVN.  I posted their explanation in [the other Fluxbox thread]("http://ubuntuforums.org/showthread.php?p=3760070#post3760070") where we were discussing SVN.  I'm sure you'll see it there, but figured I'd mention it here as I had brought it up earlier.
That's good to know. Thanks for the info.

---

### Post by yabbadabbadont on 2007-11-14
While good news, it comes too late for me.  I've become addicted to Openbox.  :shock:  :lol:

---

### Post by jviscosi on 2007-11-14
> **yabbadabbadont said:**
> While good news, it comes too late for me.  I've become addicted to Openbox.  :shock:  :lol:

I used Openbox for a couple of weeks and thought it was terrific, but I drifted back to Fluxbox.  I missed the window handling/remembering options, rounded corners, and the slitlist.  Now I miss the Openbox alt-tab window switching icons (I know some people hate them) and of course I didn't have to hack the Openbox source to keep KDE icons out of the dock like I did with Flux.

If only we could mush them together into OpenFlux, it would be perfect!  ;-)

---

### Post by yabbadabbadont on 2007-11-14
Did you try compiling Fluxbox *without* KDE support to see if it helped with the dock issue?

---

### Post by jviscosi on 2007-11-14
> **yabbadabbadont said:**
> Did you try compiling Fluxbox *without* KDE support to see if it helped with the dock issue?

I knew somebody would ask that eventually.  ;-)

Yes, I did.  I even filed a bug report that the KDE switch had no effect on KDE tray icons going into the slit.  I finally got sick of waiting for it to be fixed.

EDIT:  Actually, now that I think about it, I sent the issue to the Fluxbox developers mailing list, rather than filing an official bug report.  I suppose I should go back and file a bug report about it ...
EDIT #2: I filed a bug report and Mark said they would fix it.

Thanks for the nudge Yabba, I should've reported this one a while ago.

---

### Post by s26c.sayan on 2007-11-19
I've put my limited Python skills at use and tried to create a Fluxbox menu system app. It comprises of a menu generator (from the .desktop files) and also a menu-updater.
Whenever a new package is added or removed from the system, the app auto-refreshes the fluxbox menu accordingly. In this, it tries to emulate the Gnome menu of Ubuntu in looks and functionality.
I'm calling it marchfluxmneu, because I intend to use it with future versions of March Linux, my pet distro!

[http://code.google.com/p/marchfluxmenu/](http://code.google.com/p/marchfluxmenu/)

Please give it a try.

---

### Post by n8bounds on 2007-11-22
You Are The Man, thanks so much!!

---

### Post by eumetaxas on 2007-11-28
Hi!
How can i switch between languages (eg using alt-shift as i did in gnome or add a language icon)? 
i have installed fluxbox through synaptic and generated the menus using the first option of the how-to.

I did a search but could not find an answer.
thanx!

---

### Post by RedSquirrel on 2007-11-30
> **eumetaxas said:**
> Hi!
How can i switch between languages (eg using alt-shift as i did in gnome or add a language icon)? 
i have installed fluxbox through synaptic and generated the menus using the first option of the how-to.

I did a search but could not find an answer.
thanx!

I've never tried to switch languages. However, a quick search on Google generated this [link]("http://www.linuxquestions.org/questions/linux-newbie-8/fluxbox-change-languages-keyboard-layout-393468/"). There may be more.

---

### Post by eumetaxas on 2007-12-01
THANX for the answer!

i had found this post before posting here but it seemed like chinese to me (i'm still newbie) and did not try. i tried now but did not work (obviously did something wrong!!!!). 
1. made a file in scripts folder named xkbSwitch, pasted script and made executable.
2. made the folder .xkbSwitch in /root directory (logged as root) and  
3. made the file xkb_layouts and written inside en and el , english and greek (also tried gr instead el) 
4.re-logged in and did not work,

Let me tell you that when i log into user accounts that did not generate the menus as described in method 1, the alt-shift changes input language as does in gnome but some menus are missing.

thanx again!

---

### Post by eumetaxas on 2007-12-01
Got it!
 gnome-keyboard-properties in terminal and opens the gnome keyboard properties. Just navigate to change group tab, change nothing-just navigate! and then everything is ok as it was in gnome! don't know how and why but it works:)
thanx!

---

### Post by Odd-rationale on 2007-12-04
> **s26c.sayan said:**
> I've put my limited Python skills at use and tried to create a Fluxbox menu system app. It comprises of a menu generator (from the .desktop files) and also a menu-updater.
Whenever a new package is added or removed from the system, the app auto-refreshes the fluxbox menu accordingly. In this, it tries to emulate the Gnome menu of Ubuntu in looks and functionality.
I'm calling it marchfluxmneu, because I intend to use it with future versions of March Linux, my pet distro!

[http://code.google.com/p/marchfluxmenu/](http://code.google.com/p/marchfluxmenu/)

Please give it a try.

Wow! I've been wanting something like this for a long time! Thanks so much!

---

### Post by subs on 2007-12-13
this is great... thanks

---

### Post by S.O.P on 2007-12-17
> **s26c.sayan said:**
> I've put my limited Python skills at use and tried to create a Fluxbox menu system app. It comprises of a menu generator (from the .desktop files) and also a menu-updater.
Whenever a new package is added or removed from the system, the app auto-refreshes the fluxbox menu accordingly. In this, it tries to emulate the Gnome menu of Ubuntu in looks and functionality.
I'm calling it marchfluxmneu, because I intend to use it with future versions of March Linux, my pet distro!

[http://code.google.com/p/marchfluxmenu/](http://code.google.com/p/marchfluxmenu/)

Please give it a try.
Works as advertised.  Speed of fluxbox, hallmarks of gnome.

Very nice.

---

### Post by mark-t on 2007-12-20
> 
Code:

cd ~/fluxbox-git/fluxbox
git-pull
./autogen.sh

5. Now that you have the source code, go to step #5 under "Compiling from the Stable Source Tarball" and follow it and the remaining steps. When you have finished and your new fluxbox is installed, I would recommend running:

Code:

make clean

in the ~/fluxbox-git/fluxbox directory to remove the files that were created during compilation.

This seems a bit off. Both `./autogen.sh' and `make clean' will force you to recompile a lot of things (everything in the case of `make clean') the next time you update. If you don't run these commands, updating fluxbox is usually a matter of seconds. The extra 20MB of disk space probably aren't worth the difference to you.

---

### Post by yabbadabbadont on 2007-12-20
> **mark-t said:**
> This seems a bit off. Both `./autogen.sh' and `make clean' will force you to recompile a lot of things (everything in the case of `make clean') the next time you update. If you don't run these commands, updating fluxbox is usually a matter of seconds. The extra 20MB of disk space probably aren't worth the difference to you.

I've seen problems caused by not running the "make clean" before.  Flux only takes a few minutes to build on most machines.  Are the extra couple of minutes worth the time you'll waste trying to track down problems?  ;)

---

### Post by mark-t on 2007-12-21
It is to me. I compile it many times a day. Sitting around for a few minutes would definitely interrupt my thought processes.

Anyway, such an occurrence would be extremely rare. I can only imagine it making a difference if you've run the configure script with different settings (and it still shouldn't matter then) or manually changed a Makefile.

---

### Post by RedSquirrel on 2007-12-29
> **mark-t said:**
> This seems a bit off. Both `./autogen.sh' and `make clean' will force you to recompile a lot of things (everything in the case of `make clean') the next time you update. If you don't run these commands, updating fluxbox is usually a matter of seconds. The extra 20MB of disk space probably aren't worth the difference to you.

Thanks for your input.

I removed the './autogen.sh' line since it isn't really necessary when one is merely *updating* the code.

With regard to 'make clean', it is my habit to do it that way to avoid potential problems. (I wasn't really thinking about the disk space.)

I added a link to your post in that tutorial section so that anyone who wants to compile from the GIT code can consider both approaches... to 'make clean' or not to 'make clean'. :)

---

### Post by rjmdomingo2003 on 2007-12-30
At the moment, I have svn 5144 installed, and am thinking of installing the latest version. That is, the latest git version. Am I correct?

So my question is: Will it be fine if I update using git even if I have the svn version? If not, then, how do I go about it? Do I need to uninstall my current flux svn, and compile from source (using git)?

Thanks & Happy New Year in advance!

---

### Post by RedSquirrel on 2007-12-30
> **rjmdomingo2003 said:**
> At the moment, I have svn 5144 installed, and am thinking of installing the latest version. That is, the latest git version. Am I correct?

So my question is: Will it be fine if I update using git even if I have the svn version? If not, then, how do I go about it? Do I need to uninstall my current flux svn, and compile from source (using git)?

Thanks & Happy New Year in advance!

Right, the latest version of the code is obtained using git instead of svn. The procedure is the same except for the method used to obtain the source code. You will use 'git' commands instead of 'svn' commands.

So, just remove your old svn version of the Fluxbox package and follow the instructions to obtain the code, compile it, and make a new deb package and you should be fine. :)

I would recommend creating a new directory for your fluxbox git code, either by renaming the 'fluxbox' directory where you downloaded the svn code or by creating a whole new 'git' directory in your home directory and pulling down the sources in there (as described in the tutorial).

```
mkdir ~/fluxbox-git
cd ~/fluxbox-git
git clone git://git.fluxbox.org/fluxbox.git

```Happy New Year! (in advance)

---

### Post by rjmdomingo2003 on 2007-12-30
> **RedSquirrel said:**
> Right, the latest version of the code is obtained using git instead of svn. The procedure is the same except for the method used to obtain the source code. You will use 'git' commands instead of 'svn' commands.

So, just remove your old svn version of the Fluxbox package and follow the instructions to obtain the code, compile it, and make a new deb package and you should be fine. :)

I would recommend creating a new directory for your fluxbox git code, either by renaming the 'fluxbox' directory where you downloaded the svn code or by creating a whole new 'git' directory in your home directory and pulling down the sources in there (as described in the tutorial).

```
mkdir ~/fluxbox-git
cd ~/fluxbox-git
git clone git://git.fluxbox.org/fluxbox.git

```Happy New Year! (in advance)
Thanks a bunch, Red! You & yabbadabba have been THE motivating factors in my flux journey :popcorn:

Happy New Year to you & your baby squirrels! :)

---

### Post by eriqjaffe on 2008-01-04
> **s26c.sayan said:**
> I've put my limited Python skills at use and tried to create a Fluxbox menu system app. It comprises of a menu generator (from the .desktop files) and also a menu-updater.
Whenever a new package is added or removed from the system, the app auto-refreshes the fluxbox menu accordingly. In this, it tries to emulate the Gnome menu of Ubuntu in looks and functionality.
I'm calling it marchfluxmneu, because I intend to use it with future versions of March Linux, my pet distro!

[http://code.google.com/p/marchfluxmenu/](http://code.google.com/p/marchfluxmenu/)

Please give it a try.I really, really like marchfluxmenu, but I'm having problems getting .png icons to show up for some reason, although XPMs work just fine...is there some other dependency I need for PNG support?

PNGs work fine with wbar, for what it's worth.

---

### Post by yabbadabbadont on 2008-01-04
@eriqjaffe: You have to configure fluxbox to include imlib2 support when building it.

Edit: If you are using the fluxbox included in the repositories, then you are probably out of luck.  (assuming that they didn't include imlib2 support when they built it)

Post the output of running, in a terminal window ```
fluxbox -i
```

---

### Post by RedSquirrel on 2008-01-04
If I recall correctly, the fluxbox package on feisty does not have imlib2 support. The package on gutsy does (but it's missing XShape support).

---

### Post by s26c.sayan on 2008-01-05
> **eriqjaffe said:**
> I really, really like marchfluxmenu, but I'm having problems getting .png icons to show up for some reason, although XPMs work just fine...is there some other dependency I need for PNG support?

PNGs work fine with wbar, for what it's worth.

I have seen screenies of marchfluxmenu taken on a friend's Ubuntu Gutsy (I don't have Ubuntu ATM in my system). And I can say that at least the main menu icons (the ones which comes with mfm itself) looks fine!
Mfm works fine with my March Linux as well.

So maybe you are using Fluxbox without imlib2 support, as pointed out above.

Anyway, thank you for trying it out! :)
Any other suggestions?

---

### Post by randomhuman on 2008-01-05
> **mojoman said:**
> This question might be half-way off-topic but I'll post it anyway as it's at least related to fluxbox menu. I use the Debian menu as a submenu on my fluxbox, running on feisty (which uses menu 2.1.32). After I installed deluge from a .deb I updated the menus and it showed up in the Debian menu. However, it was under a separate heading, called applications (all other are under the heading apps). Now, I also installed deluge on my Lenny, and it uses menu 2.1.36 and in that version there is no heading called apps, only applications. So, it seems to me as if the deb I installed was compiled for a later version of menu, and I therefore end up with a mixture, having both applications and apps  in the Debian menu. I had a look in the .desktop file to see if that decided where it showed up but couldn't find anything there to edit to solve this. Does any of you guys have a take on this?

Thanks
/mojoman

update-menus, and therefore your fluxbox menu, don't use the .desktop files like gnome does. I believe it uses the files in /usr/share/menu, and files in ~/.menu will override them.

So:

copy /usr/share/menu/deluge to ~/.menu (creating the directory if it doesn't exist)
edit the file and change section="Applications" to section="Apps/Net"
run update-menus

---

### Post by randomhuman on 2008-01-05
This looks like a great tutorial, but unfortunately I came across it about 5 minutes after I got my menu working properly :)

Thanks anyway, and I got lots of good suggestions from the thread too. Thanks all!

---

### Post by eriqjaffe on 2008-01-05
> **yabbadabbadont said:**
> @eriqjaffe: You have to configure fluxbox to include imlib2 support when building it.

Edit: If you are using the fluxbox included in the repositories, then you are probably out of luck.  (assuming that they didn't include imlib2 support when they built it)

Post the output of running, in a terminal window ```
fluxbox -i
```Ah, that would be it - I am, indeed, using the one from the Feisty repos (and I have no real intention of updating to Gutsy on this old system):
```
Compiled options (- => disabled): 
-DEBUG
EWMH
GNOME
**-IMLIB2**
KDE
NLS
REMEMBER
RENDER
SHAPE
SLIT
TOOLBAR
XFT
XINERAMA
XMB
XPM
```If I compiled from source with imlib2 support, can I upgrade Fluxbox from within Fluxbox?

---

### Post by jviscosi on 2008-01-05
> **eriqjaffe said:**
> Ah, that would be it - I am, indeed, using the one from the Feisty repos (and I have no real intention of updating to Gutsy on this old system)


That's okay, upgrading to Gutsy would just break a bunch of other stuff in Fluxbox.

> **eriqjaffe said:**
> 
If I compiled from source with imlib2 support, can I upgrade Fluxbox from within Fluxbox?

Yep, I do it all the time (compiling from SVN and now from git).  You can make and install a new version of Fluxbox while Fluxbox is running, and the new version will take effect the next time you start Fluxbox. I like to install using checkinstall so I can easily go back to an older version if something bad happens.

---

### Post by yabbadabbadont on 2008-01-05
> **eriqjaffe said:**
> If I compiled from source with imlib2 support, can I upgrade Fluxbox from within Fluxbox?

RedSquirrel has provided a nice set of instructions for building fluxbox from source in the first post of this thread.  (If that was what you were asking)

If you are asking, "Can I install a newer version of fluxbox over the top of my currently running fluxbox?", the answer is yes.  But it might be safer to logout.  Hit Control-Alt-F1 to drop to the text console.  Login and install it from there.   Logout when finished, then hit Alt-F7 to switch back the graphical login screen.

You can safely follow all of the build instructions, except the last one, "checkinstall", while you are in a running fluxbox.  As I said before, you could even replace the running binaries.  You would just have to logout and back in to make the new binaries take effect.  Since you have to do that anyway, you might as well run the final installation step from the text console.

Edit: Too slow.  :lol:

---

### Post by eriqjaffe on 2008-01-05
Thanks, guys, I'll give it a go tomorrow, probably.

---

### Post by r41nz0r on 2008-01-06
Thanks, I was interested in doing this.

---

### Post by mojoman on 2008-01-06
> **randomhuman said:**
> update-menus, and therefore your fluxbox menu, don't use the .desktop files like gnome does. I believe it uses the files in /usr/share/menu, and files in ~/.menu will override them.

So:

copy /usr/share/menu/deluge to ~/.menu (creating the directory if it doesn't exist)
edit the file and change section="Applications" to section="Apps/Net"
run update-menus

Thanks for clearing that out for me. Right now, I mainly use my Debian Lenny partition so I don't have that problem right now but it's probably just a matter of time before it arises again (when I start mixing in a little more sid for example :twisted: ). If it does I'll now how to fix it.

/mojoman

---

### Post by RedSquirrel on 2008-01-06
> **yabbadabbadont said:**
> If you are asking, "Can I install a newer version of fluxbox over the top of my currently running fluxbox?", the answer is yes.  But it might be safer to logout.  Hit Control-Alt-F1 to drop to the text console.  Login and install it from there.   Logout when finished, then hit Alt-F7 to switch back the graphical login screen.

I like to install it while on the console just to be safe. ;)

Another option is to install it while running some other window manager or DE, if you have one installed.

---

### Post by eriqjaffe on 2008-01-06
OK, I'm running into a bit of a problem...I have no menu when I right-click the desktop.  It's not that it's **empty**, it's just not there...

I followed the steps on the first page of this thread, compiling and installing Fluxbox from the stable tarball, and that all went fine.  My init file references ~/.fluxbox/menu, which seems right, and the menu file seems fine.  If I run  fluxbox-generate_menu, it seems to run, and my ~/.fluxbox/menu file gets modified. but right-clicking on the desktop never makes anything pop up.

The really strange thing is that, after installing the compiled version, I **had** my menu, but now it's gone, and I don't think I did anything to make it go away.  I did a little bit with the style and the wallpaper...but I don't think I did anything to make my menu disappear.  If I right-click on the slit, I get the slit menu, and if I right-click on the toolbar, I get that menu it's just the desktop that doesn't work.  Let me know if posting any of my config files woul be of help...

---

### Post by yabbadabbadont on 2008-01-06
The problem is most likely that your keys file was not properly updated.  Mouse actions are now, for whatever reason, located in the keys file.  Logout.  Drop to the console and move your existing keys file to a new name.  Then switch back to gdm and login.  Hopefully, fluxbox will recreate it for you with the missing entries.  There is an update program installed that you may have to run manually.  fluxbox-update-something or other.  I can't remember exactly.

---

### Post by eriqjaffe on 2008-01-06
> **yabbadabbadont said:**
> The problem is most likely that your keys file was not properly updated.  Mouse actions are now, for whatever reason, located in the keys file.  Logout.  Drop to the console and move your existing keys file to a new name.  Then switch back to gdm and login.  Hopefully, fluxbox will recreate it for you with the missing entries.  There is an update program installed that you may have to run manually.  fluxbox-update-something or other.  I can't remember exactly.Yep, that was it.  If I had known that the mouse actions were in the keys file, I never would've blindly copied & pasted my old one into the .fluxbox folder.  ;)

Thanks again!

---

### Post by randomhuman on 2008-01-06
> **mojoman said:**
> Thanks for clearing that out for me. Right now, I mainly use my Debian Lenny partition so I don't have that problem right now but it's probably just a matter of time before it arises again (when I start mixing in a little more sid for example :twisted: ). If it does I'll now how to fix it.

/mojoman

No bother. I just hope I have my info right! :)

---

### Post by skyshock21 on 2008-02-11
fluxbox-generate_menu file you attached doesn't appear to download as a valid filetype.  I tried adding the .gz extension manually, but to no avail.  Where can I get this file from?

---

### Post by yabbadabbadont on 2008-02-11
> **skyshock21 said:**
> fluxbox-generate_menu file you attached doesn't appear to download as a valid filetype.  I tried adding the .gz extension manually, but to no avail.  Where can I get this file from?

You must have something wrong with your settings.  I just download and gunzip'd it fine.

---

### Post by RedSquirrel on 2008-02-11
> **skyshock21 said:**
> fluxbox-generate_menu file you attached doesn't appear to download as a valid filetype.  I tried adding the .gz extension manually, but to no avail.  Where can I get this file from?
If you simply click on the link it should open the Save As dialog of your browser and the filename will be [COLOR=DarkGreen]fluxbox-generate_menu.gz[/COLOR].

It will _not_ work if you right-click on the link for the attachment and select "Save link as...". That will want to save "attachment.php". ;)

---

### Post by b0rka7a on 2008-03-09
Thank you for this wonderful guide, RedSquirrel !

---

### Post by RedSquirrel on 2008-03-09
> **b0rka7a said:**
> Thank you for this wonderful guide, RedSquirrel !
You are most welcome! :)

---

### Post by tad1073 on 2008-03-10
I am having problems with alpha opacity. There is only one user style that works but it seems to take on the colors of the background and is not realy transparent. Also I am having trouble with gnome terminal and aterm as far as the window being transparent.

---

### Post by yabbadabbadont on 2008-03-10
> **tad1073 said:**
> I am having problems with alpha opacity. There is only one user style that works but it seems to take on the colors of the background and is not realy transparent. Also I am having trouble with gnome terminal and aterm as far as the window being transparent.

Without details, no one will be able to help you.  :D

---

### Post by tad1073 on 2008-03-10
What kind of details do you need?

---

### Post by yabbadabbadont on 2008-03-10
> **tad1073 said:**
> What kind of details do you need?

Which style?  How did you set the background (exact command)?  What commands/settings are you using with your terminal?  Screenshots that illustrate the issues...

---

### Post by tad1073 on 2008-03-10
this is what I used for aterm.
```
aterm -tr -tink black
```
which returns this error:
```
aterm has encountered the following problem interacting with X Windows :
      Request: 64,    Error: 8(BadMatch (invalid parameter attributes))
      in resource: 0x2600019

```
with the gnome terminal under fluxbox I use edit>current profile>effects>transparent background but it just shows up black.

I set my background with the menu entry that points to /.fluxbox/backgrounds.

opacity only seems to work with the themes that comes with fluxbox

---

### Post by RedSquirrel on 2008-03-10
Which Fluxbox theme is that (in your screenshot)?

I have used urxvt (rxvt-unicode) for a transparent terminal in the past (mainly for screenshots! :)) and it worked fine.

I haven't used aterm or gnome-terminal in ages, so I'm not much help there. (I don't use any transparency these days, so I just stick to xterm.)

---

### Post by PurposeOfReason on 2008-03-10
> **tad1073 said:**
> this is what I used for aterm.
```
aterm -tr -tink black
```
which returns this error:
```
aterm has encountered the following problem interacting with X Windows :
      Request: 64,    Error: 8(BadMatch (invalid parameter attributes))
      in resource: 0x2600019

```
with the gnome terminal under fluxbox I use edit>current profile>effects>transparent background but it just shows up black.

I set my background with the menu entry that points to /.fluxbox/backgrounds.

opacity only seems to work with the themes that comes with fluxbox
I would say use urxvt (sudo aptitude install rxvt-unicode) and use these xdefaults to start (copy them into the file ~/.Xdefaults it may not exist yet). You also need xcompmgr running.

```

URxvt.termName: rxvt
URxvt.transparent: true
URxvt.inheritPixmap: False
URxvt.imLocale: pl_PL.UTF-8
URxvt.scrollBar: false
URxvt.saveLines: 5000
URxvt.urlLauncher:      firefox3
URxvt.cursorBlink: true
URxvt.geometry: 85x21
URxvt.fading: 15%
URxvt.shading: 75
urxvt.font:             xft:Bitstream Vera Sans Mono:pixelsize=8
urxvt.boldFont:         xft:Bitstream Vera Sans Mono:bold:pixelsize=9
URxvt*background:      [80]#000000
URxvt.foreground: [80]#ffffff
urxvt.depth: 32
!urxvt.background:  rgba:7860/6830/5600/eeee
!urxvt.foreground: rgba:3860/3030/2500/ffff
URxvt.tintColor: #d9d7d1
URxvt.borderLess: true
!URxvt.InternalBorder: .5
URxvt.externalBorder: .5
URxvt.borderColor: #3d352a

*foreground:     rgba:1000/1000/1000/eeee
*background:     rgb:10/10/10
!black
*color0:         rgb:20/20/20
*color8:         rgb:75/77/73
!red
*color1:         rgb:cc/00/00  
*color9:         rgb:ef/29/29
!green
*color2:         rgb:4e/9a/06
*color10:        rgb:8a/e2/34
!brown/yellow
*color3:         rgb:c4/a0/00
*color11:        rgb:fc/e9/4f
!blue
*color4:         rgb:34/65/a4
*color12:        rgb:72/9f/cf
!magenta
*color5:         rgb:75/50/7b
*color13:        rgb:ad/7f/a8
!cyan
*color6:         rgb:06/98/9a
*color14:        rgb:34/e2/e2
!white
*color7:         rgb:d3/d7/cf
*color15:        rgb:ee/ee/ec


```

---

### Post by RedSquirrel on 2008-03-10
> **tad1073 said:**
> this is what I used for aterm.
```
aterm -tr **[COLOR=Blue]-tink[/COLOR]** black
```which returns this error: ...


That should be 'tint', right? Is that just a typo in this post? ;)

---

### Post by RedSquirrel on 2008-03-10
> **PurposeOfReason said:**
> I would say use urxvt (sudo aptitude install rxvt-unicode) and use these xdefaults to start (copy them into the file ~/.Xdefaults it may not exist yet). You also need xcompmgr running.

I just used pseudo-transparency. xcompmgr is too slow for me. ;)

---

### Post by tad1073 on 2008-03-10
> **RedSquirrel said:**
> Which Fluxbox theme is that (in your screenshot)?

I have used urxvt (rxvt-unicode) for a transparent terminal in the past (mainly for screenshots! :)) and it worked fine.

I haven't used aterm or gnome-terminal in ages, so I'm not much help there. (I don't use any transparency these days, so I just stick to xterm.)

It is called SII w/my own back ground

> **RedSquirrel said:**
> That should be 'tint', right? Is that just a typo in this post? ;)

yes it was a typo

> **PurposeOfReason said:**
> I would say use urxvt (sudo aptitude install rxvt-unicode) and use these xdefaults to start (copy them into the file ~/.Xdefaults it may not exist yet). You also need xcompmgr running.


what is xcompmgr, it is not compiz-fusion is it? My video card can not support compiz-fussion

---

### Post by PurposeOfReason on 2008-03-10
> **tad1073 said:**
> 
what is xcompmgr, it is not compiz-fusion is it? My video card can not support compiz-fussion
It is a light compositor for the *box WMs. It just does shadows, transparency, and fade in and out. Basically anything can run it.

---

### Post by RedSquirrel on 2008-03-10
> **tad1073 said:**
> It is called SII w/my own back ground

Works fine for me. (This is on Debian, mind you.)

I set my alpha to 160 for the menu. Are you using alpha values that are low enough? If transparency works for the default themes, it should work for the themes you installed.


Other things I can think of are to restart Fluxbox (from the menu) to see if that applies the transparency.

If it's still not working, post the output of:

```
fbsetbg -i
```and 

```
fluxbox -i
```and 

```
xdpyinfo | grep -i render
```




> **tad1073 said:**
>  what is xcompmgr, it is not compiz-fusion is it? My video card can not support compiz-fussion

No, it is not compiz. 

[http://packages.ubuntu.com/gutsy/xcompmgr](http://packages.ubuntu.com/gutsy/xcompmgr)

---

### Post by yabbadabbadont on 2008-03-10
Also, make sure that you have:
```
session.forcePseudoTransparency:        true
```
in your ~/.fluxbox/init file.

---

### Post by tad1073 on 2008-03-10
```
thomas@computer:~$ fbsetbg -i

display doesn't set the wallpaper properly. Transparency for fluxbox and apps like aterm and 
xchat won't work right with it. Consider installing feh, wmsetbg (from windowmaker) or Esetroot 
(from Eterm) and I'll use them instead.

```

```
thomas@computer:~$ fluxbox -i
Fluxbox version: 1.0.0
Compiled: Oct  9 2007 15:28:22
Compiler: GCC
Compiler version: 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)

Defaults:
    menu: /etc/X11/fluxbox/fluxbox.menu-user
   style: /usr/share/fluxbox/styles/Clean
    keys: /etc/X11/fluxbox/keys
    init: /etc/X11/fluxbox/init
     nls: /usr/share/fluxbox/nls

Compiled options (- => disabled): 
-DEBUG
EWMH
GNOME
IMLIB2
KDE
NLS
REMEMBER
RENDER
-SHAPE
SLIT
TOOLBAR
XFT
XINERAMA
XMB
XPM

```

```
thomas@computer:~$ xdpyinfo | grep -i render
    RENDER

```

---

### Post by tad1073 on 2008-03-10
I got thing figured out now. i played with some settings and everyting is working.

---

### Post by solarwind on 2008-03-24
> **s26c.sayan said:**
> I've put my limited Python skills at use and tried to create a Fluxbox menu system app. It comprises of a menu generator (from the .desktop files) and also a menu-updater.
Whenever a new package is added or removed from the system, the app auto-refreshes the fluxbox menu accordingly. In this, it tries to emulate the Gnome menu of Ubuntu in looks and functionality.
I'm calling it marchfluxmneu, because I intend to use it with future versions of March Linux, my pet distro!

[http://code.google.com/p/marchfluxmenu/](http://code.google.com/p/marchfluxmenu/)

Please give it a try.

Very nice. Thank you!

---

### Post by the dsc on 2008-04-23
I'm just posting to thank SadaraX and Red Squirrel for the [_tip early on page 4_](http://ubuntuforums.org/showpost.php?p=3130878&postcount=36) of this topic, about compiling a rootmenu on fluxbox' toolbar! :)

Eventually I'll take a look at the code and see if I can figure out a way to add some extra eyecandyness to it: I want to see if I can find something that would make the rootmenu on the toolbar be created with the menu title (as given in the "menu" file - perhaps it may look somewhat like whatever makes the workspaces have customizable names) and perhaps even add some icon (which I think I may find by taking a peek at the area related with the system tray).



...but I may be underestimating the hardness of such task for someone with my level of newbieness, anyway... does not seems risky, however. Would be cool if we could run the program to test before compiling... is that possible? (it used to be in MS Basic)


That's so cool. Allows to use full maximization and retractile toolbar (for even fuller maximization) and yet have the rootmenu on the same screen. I don't understand why it does not come compiled by default!


Just in case someone likes the idea but thinks that the whole compilation thing may be hard, I've found that by [_this "debian way"_](http://www.debian.org/doc/manuals/apt-howto/ch-sourcehandling.en.html) (I think) is pretty much easier than the way that is described in the "install" text file. I tried the "install" way and it didn't work for some reason (errors with "make" during the screenresources.cc file). I must say that I'm now using debian itself, but I think that it's very likely to apply to Ubuntu as well... ask someone if in doubt, anyway.

---

### Post by RedSquirrel on 2008-04-25
> **the dsc said:**
> I'm just posting to thank SadaraX and Red Squirrel for the [_tip early on page 4_]("http://ubuntuforums.org/showpost.php?p=3130878&postcount=36") of this topic, about compiling a rootmenu on fluxbox' toolbar! :)

You are most welcome. I'm glad SadaraX dropped by with that little gem. :)


> **the dsc said:**
> Eventually I'll take a look at the code and see if I can figure out a way to add some extra eyecandyness to it: I want to see if I can find something that would make the rootmenu on the toolbar be created with the menu title (as given in the "menu" file - perhaps it may look somewhat like whatever makes the workspaces have customizable names) and perhaps even add some icon (which I think I may find by taking a peek at the area related with the system tray).

...but I may be underestimating the hardness of such task for someone with my level of newbieness, anyway... does not seems risky, however. 

Sounds interesting. Do let us know how it goes.


> **the dsc said:**
> Would be cool if we could run the program to test before compiling... is that possible? (it used to be in MS Basic)

No. Fluxbox is written in C++, so you must compile to see the effect of the changes you make to the code.


> **the dsc said:**
>  That's so cool. Allows to use full maximization and retractile toolbar (for even fuller maximization) and yet have the rootmenu on the same screen. I don't understand why it does not come compiled by default!

I think most people just use the right-click or setup a key binding for the menu.


> **the dsc said:**
>  Just in case someone likes the idea but thinks that the whole compilation thing may be hard, I've found that by [_this "debian way"_]("http://www.debian.org/doc/manuals/apt-howto/ch-sourcehandling.en.html") (I think) is pretty much easier than the way that is described in the "install" text file. I tried the "install" way and it didn't work for some reason (errors with "make" during the screenresources.cc file). I must say that I'm now using debian itself, but I think that it's very likely to apply to Ubuntu as well... ask someone if in doubt, anyway.

That should work on Ubuntu as well. 

I haven't had any trouble doing ./configure, make, etc. Did you do 'apt-get build-dep fluxbox' before trying to compile?

---

### Post by the dsc on 2008-04-30
> 
Sounds interesting. Do let us know how it goes.


Up to now, I just confirmed that's harder than I thought it could be :lol:

I still have to examine the "fbrun" thing, which perhaps has something more obvious that would allow to create a button with the fluxbox icon itself.




> I think most people just use the right-click or setup a key binding for the menu.

And maybe most people left the non-retractile toolbar, with non-full width as well, which kinda emulates a classical rootmenu button.

As I prefer retractile full width toolbar and full maximization, that does not work with me. Actually I got used to go over the toolbar and roll the mouse wheel to a less populated desktop, and then right click on the empty space; more recently, I got used with the key binding. 

But when I first started with FB that would have been so much better (and still is convenient even now that I don't even have other WM at all). I had the reflex of going to the nonexistent button all the time. I think that it creates a kind of "abyss" (that's probably a strong word) of usability between the KDE and GNOME interfaces and fluxbox. Make it feels somewhat "weird". I think that if it had it natively, KDE and GNOME (or even windows) users would feel much more at ease with the transition. Eventually they could even disable it with the init file, if they find it unnecessary. I personaly think that the "next/previous" buttons are the most useless, both for desktops and running programs. But that totally depends on having a wheel button, anyway.




> 
I haven't had any trouble doing ./configure, make, etc. Did you do 'apt-get build-dep fluxbox' before trying to compile?


I'm sorry. At this point I don't recall how I did it anymore :lol: . I've actually done it a second time after that, and I had some trouble even trying doing it by "my own" way. Partially related with debian-related stuff (manual dl of the source and other files ("dsc" and the other one) somehow didn't work file and things like that). And just newbieness, like frustratingly trying to download the source from the backport's repository without having the line for the backport's sources on the sources.list. So I think that all that I said regarding easy of hard ways of installation can be pretty much safely ignored. :lol:

I did it again because I learn't that newer versions of FB have a "style overlay" file that I find much interesting; I like to vary the "styles" but I like font and size consistency.





By the way, I think that newer versions of fluxbox permit to emulate a rootmenu on toolbar without this different compilation, but through the "keys" file; now it's possible bind the mouse buttons to do things over the toolbar (or over other places), including rootmenu, if I recall. It could be activated by the middle button/wheel, or to the right click, with the usual right click menu transfered to the middle button, I think.

---

### Post by zenTux on 2008-05-31
sorry for this dumb question but i really do need your answers. I had attached a screenshot i got from this thread and can somebody please tell what the name of the program i had encircle at the screenshot. Its located at the bottom right of the screenshot. Thanks!!!

---

### Post by urukrama on 2008-05-31
That looks like conky. There is [a thread]("http://ubuntuforums.org/showthread.php?t=281865") about its configuration on these forums.

---

### Post by RedSquirrel on 2008-05-31
Just to confirm: Yes, that's conky. :)

```
sudo apt-get install conky
```

In addition to the link urukrama gave, have a look at conky's homepage:

[http://conky.sourceforge.net/](http://conky.sourceforge.net/)

---

### Post by zenTux on 2008-06-02
To: urukrama & RedSqirrel

Thanks a Lot ;-)

---

### Post by dot2kode on 2008-07-27
Thanks for taking the time and putting this togather.  It has been a big help! =D>

---

### Post by RedSquirrel on 2008-07-28
> **dot2kode said:**
> Thanks for taking the time and putting this togather.  It has been a big help! =D>
My pleasure. I'm glad you found it helpful. :)

---

### Post by matija_kc on 2008-07-30
RedSquirrel, can you please post your fbpager configuration? 
thanx!

btw- my fluxbox: :)

[http://www.imagesforme.com/show.php/114766_screen2008073016.27.png](http://www.imagesforme.com/show.php/114766_screen2008073016.27.png)

---

### Post by billgoldberg on 2008-07-30
Thanks, I learned a few new things.

---

### Post by RedSquirrel on 2008-07-30
> **matija_kc said:**
> RedSquirrel, can you please post your fbpager configuration? 
thanx!

I haven't used fbpager in a long time, but you're in luck: I backup _EVERYTHING_! :twisted:

After a bit of digging around in my old files... here you go:

```
fbpager.alpha: 160
fbpager.x: 1123
fbpager.y: 992
fbpager.workspace.width: 38
fbpager.workspace.height: 30
fbpager.workspacesPerRow: 6400
fbpager.followDrag: false
fbpager.followMove: false
fbpager.changeWorkspaceButton: 11
fbpager.raiseWindowButton: 2
fbpager.lowerWindowButton: 3
fbpager.closeWindowButton: 3 3 1
fbpager.exitButton: 1 3 3
fbpager.nextWorkspaceButton: 4
fbpager.prevWorkspaceButton: 5
fbpager.moveInWorkspaceButton: 1
fbpager.dragToWorkspaceButton: 2
fbpager.align: LeftToRight
fbpager.color: white
fbpager.windowColor: gray
fbpager.focusedWindowColor: white
fbpager.windowBorderColor: black
fbpager.backgroundColor: black
fbpager.currentBackgroundColor: skyblue
fbpager.multiClickTime: 250
fbpager.icons: false
fbpager.windowBorderWidth: 1

```The screenshots I attached to this thread are quite old (maybe I should put up some new ones...). The last time I used fbpager, I used the fbpager.x/fbpager.y settings to move it away from the corner by a few pixels. I think it looks better that way rather than shoved into the corner as it is in my old screenshots.



> **matija_kc said:**
> btw- my fluxbox: :)

[http://www.imagesforme.com/show.php/114766_screen2008073016.27.png](http://www.imagesforme.com/show.php/114766_screen2008073016.27.png)

Very nice! I see you're using [March Linux]("http://marchlinux.wikidot.com/"). ;)


Here's one for you:

---

### Post by RedSquirrel on 2008-07-30
> **billgoldberg said:**
> Thanks, I learned a few new things.
You are most welcome. :)

---

### Post by matija_kc on 2008-07-31
thank you so much, i modified it a bit and it now looks and works perfect;)
i like your flux, looks like jwm on slitaz linux:)
i use marchflux menu gen just for menu. i didn't know that march is linux distro, will try it sometime. most of things on my desktop were modified by me or ever written by me, but still this is ubuntu hardy:( i think arch will replace it soon. 
btw is that pypanel?

---

### Post by RedSquirrel on 2008-07-31
> **matija_kc said:**
> btw is that pypanel?

That's the Fluxbox toolbar. [Solaris theme]("http://box-look.org/content/show.php/Solaris%3A+Java+Fluxbox+System?content=63303").

---

### Post by Anzan on 2008-08-12
Thanks very much, RedSquirrel. And to all who contributed on this thread.

---

### Post by mojoman on 2008-09-20
> **RedSquirrel said:**
> That's the Fluxbox toolbar. [Solaris theme]("http://box-look.org/content/show.php/Solaris%3A+Java+Fluxbox+System?content=63303").

Really nice theme! I might just switch to it...


/mojoman

ps @ RS: I seldom check in these days, I'm mostly on Debian and occasionally on Arch but I re-read most of this thread today (at least the beginning) and it's amazing how much useful info it contains. Hell of a good job. Are you still hanging out here regularly? ds.

---

### Post by RedSquirrel on 2008-09-21
> **mojoman said:**
> Really nice theme! I might just switch to it...

I agree, it is a nice one.

I came across that theme while looking for something else. I really like the nimbus GTK+ engine and nimbus icon theme as well.



> **mojoman said:**
>  ps @ RS: I seldom check in these days, I'm mostly on Debian and occasionally on Arch but I re-read most of this thread today (at least the beginning) and it's amazing how much useful info it contains. Hell of a good job. 

I was pleased that so many people dropped by with tips & tricks. Wow! 18 pages! :)



> **mojoman said:**
> Are you still hanging out here regularly? ds.

I was away for a few days, but I usually keep an eye on this thread. I browse the rest of the forums (e.g., the Cafe word games!) as time permits.

When the next Ubuntu release rolls around I will give it and its fluxbox package a whirl. On the OS front, after a bit of distro-hopping (including Debian and Arch), I have settled on Gentoo.

---

### Post by Niniel on 2008-11-10
I'm not going to read 18 pages now... :)
I built my own menu - took the auto-generated default menu and reorganized it with a lot of copy and paste. It's a lot better now...
I had hoped that "include" might let me re-use the Gnome menu, but no such luck. Copying shortcuts/launchers to a directory and including that also didn't work. How annoying. But I'm almost done with above-mentioned rebuild. And then I'll need to figure out how to lock the screen and get shutdown and reboot command. Oh joy. :)

---

### Post by RedSquirrel on 2008-11-10
> **Niniel said:**
> I'm not going to read 18 pages now... :)

Bah. It's not that much. :)


> **Niniel said:**
> And then I'll need to figure out how to lock the screen and get shutdown and reboot command. Oh joy. :)

For shutdown and reboot, have a look at page 4, starting with post #40. In Post #52, yabbadabbadont suggests (wisely) that one should use the visudo command when editing the sudoers file.

```
sudo visudo
```I used to have links to these posts in the tutorial itself. However, shutdown/reboot in the menu is not something I use, so I felt a bit "uncomfortable" having it in the tutorial. I might add them back.

(I also used to have a large section on compiling fluxbox from source, but that got dropped too. The Fluxbox package from Hardy onwards is in pretty good shape; the older packages were somewhat problematic.)

---

### Post by Niniel on 2008-11-13
But is it up to date? The fluxbox site says they're at 1.10.1 now, whereas the Ubuntu repositories, at lest the default ones, only have 1.0. Or did I misread that?

Thanks for telling me on which page/s I can find the information I seek. :)

---

### Post by RedSquirrel on 2008-11-13
> **Niniel said:**
> But is it up to date? The fluxbox site says they're at 1.10.1 now, whereas the Ubuntu repositories, at lest the default ones, only have 1.0. Or did I misread that?

Version 1.1.1 is a **development** release.

The most recent **stable** version of Fluxbox is 1.0.0. This is the version Ubuntu elected to use for their fluxbox package.



> **Niniel said:**
> Thanks for telling me on which page/s I can find the information I seek. :)

No problem. :)

---

### Post by kevinguillorytraining on 2009-10-10
Thank you for a nice tutorial

---

### Post by RedSquirrel on 2009-10-11
> **kevinguillorytraining said:**
> Thank you for a nice tutorial
My pleasure. :)

---

### Post by joplass on 2009-10-16
Just a little question.  I used fluxbox long ago there is something I can't remember.  How do you give a pleasant appearance to apps.  I am not talking styles.  Let's say in Thunar for example the area with "File - Edit - Go - Help".  That background is really dull but I know there is some program to make it look like in Gnome for example.
Thank you,

---

### Post by yabbadabbadont on 2009-10-17
If you have gnome on the system, then you can run gnome-settings-daemon from your ~/.fluxbox/startup file.  Or you can manually configure your ~/.gtkrc-2.0 file, or use a tool to do so.  I prefer using lxappearance as it is easy to use and allows you to set the gtk+ theme, icon theme, and default application font.

---

### Post by joplass on 2009-10-17
lxapperance did the trick.  
thanks 

Now one more.  Can I change the path to pixmaps icons to ~/.icons?  Years back it never worked for me my icons will always fall back to pixmaps.

---

### Post by RedSquirrel on 2009-10-17
> **joplass said:**
> Can I change the path to pixmaps icons to ~/.icons?  Years back it never worked for me my icons will always fall back to pixmaps.

Where do you want to use these icons?


In the menu configuration, you can specify the full path to the desired icon, for example:

```
[exec] (LeafPad) {/usr/bin/leafpad} <~/.icons/my_leafpad.xpm>
```You can use PNG files in the menu as long as your fluxbox has imlib2 support. (Recent versions of fluxbox from the Ubuntu repositories have this.) You can check with:

```
fluxbox -i
```


In styles, you can create a symbolic link to ~/.icons, 

```
cd ~/.fluxbox/styles/foo
mv pixmaps pixmaps.old
ln -s  ~/.icons pixmaps

```

If the style had any pixmaps initially, you would have to copy them to ~/.icons. 

Alternatively, you could create symlinks individually under the original ~/.fluxbox/styles/foo/pixmaps directory for each icon you want to change.

You can also modify the style's configuration file and adjust the pixmaps:

```
window.iconify.pixmap:        /home/user/.icons/minimize.xpm
```(Use of ~ or $HOME won't work there; it must be /home/user/...)

---

### Post by joplass on 2009-10-17
Just in menu.  Worked great.
Is there a tutorial about transparent and bordeless aterm in this thread?  I tried reading through the 18 pages but that did not go too well.

No worries I figured this one out from old memories.
Thank you for a great how to.

---

