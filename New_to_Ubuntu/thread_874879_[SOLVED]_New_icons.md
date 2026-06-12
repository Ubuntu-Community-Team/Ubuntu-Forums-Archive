---
title: "[SOLVED] New icons"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by Andrew79 on 2008-07-30
How do I go about putting some new icons in? I found Ubuntu-art site, and they have some cool stuff, but I need to know what to do with the icons in order to get them going?

---

### Post by tuxxy on 2008-07-30
Move your new icons folder to 

**/home/your-username/.icons**

Now select them from the theme tab in appereance preferences

---

### Post by SunnyRabbiera on 2008-07-30
or just right click on your desktop and select "change desktop background"
go to the "theme" tab
go to "install" and select where you installed your icon set to.

---

### Post by JoneYee on 2008-07-30
> **SunnyRabbiera said:**
> or just right click on your desktop and select "change desktop background"
go to the "theme" tab
go to "install" and select where you installed your icon set to.

That's how I do it as well.

---

### Post by Joeb454 on 2008-07-30
You can also drag and drop the .tar.* file into the appearance window, which will also install it :)

---

### Post by tuxxy on 2008-07-30
Excellent tip joeb, well its true you do learn something every day :guitar:

---

### Post by Andrew79 on 2008-07-30
Okay, cool, I follow all your advice. I downloaded the icon theme from the site, and it says it downloaded it. I opened it with the debian installer, and ....... now I have no clue where they went?? I can not find where they were deposited? WTF!

---

### Post by SunnyRabbiera on 2008-07-30
> **Andrew79 said:**
> Okay, cool, I follow all your advice. I downloaded the icon theme from the site, and it says it downloaded it. I opened it with the debian installer, and ....... now I have no clue where they went?? I can not find where they were deposited? WTF!

huh?
You dont need the debian installer to install most icon themes and such..
what did you download might I ask???

---

### Post by JoneYee on 2008-07-30
> **Andrew79 said:**
> Okay, cool, I follow all your advice. I downloaded the icon theme from the site, and it says it downloaded it. I opened it with the debian installer, and ....... now I have no clue where they went?? I can not find where they were deposited? WTF!

See if its in the folder /usr/share/icons

Joeb's tip is usually how I install X11 Cursors and that's where they go when I do the drag and drop.

---

### Post by Andrew79 on 2008-07-30
okay, with some uncoordinated finesse I was able to find them. I downloaded the Gartoon Redux icon set. It looked like i opened it with the package installer, then I was able to find it buried deep inside somewhere inthe home folder. I had to open 2 more packages then finally was able to get to the icon folder. So, I moved the actual folders with the icons to my documents. 
So, now how do I put the icons in places I want? I want to put them on my desktop and panels for the various programs.
Thanks

---

### Post by tuxxy on 2008-07-30
You need to select that package to be used right clicking on your desktop and navigating to themes > customize > icons

---

### Post by SunnyRabbiera on 2008-07-30
you dont have to do that sort of thing actually, if the icon theme has a .tar extension it should be very easy to install.

---

### Post by Andrew79 on 2008-07-30
Okay, I finally got them in to an easy to find area. I went change desktop, themes, install, all files, then opened up till I could not anymore. I got to where the icon files are. If I click on the file, is it going to automatically change the icon in whichever theme I currently have selected? Should I make sure it is my custom theme to do this?

---

### Post by JoneYee on 2008-07-30
> **Andrew79 said:**
> Okay, I finally got them in to an easy to find area. I went change desktop, themes, install, all files, then opened up till I could not anymore. I got to where the icon files are. If I click on the file, is it going to automatically change the icon in whichever theme I currently have selected? Should I make sure it is my custom theme to do this?

You don't need the individual icons extracted, you need the tar.gz file for the theme.  

Installing themes[4] (including icons) is relatively painless in Gnome. You open the Theme Preferences which you'll find at System &#8594; Preferences &#8594; Theme. With this application you can change icons, controls and window borders to your liking. To install your theme, simply drag and drop the package onto the Theme Preferences window and confirm the dialog window that pops up. To use your new theme, edit one of the existing themes to use your new icons, controls or window borders.

Reference: [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by Andrew79 on 2008-07-30
Cool, thank you. It worked. I was opening the packages, so I did it the way you said, and BAM! Everything is changed, new icons! 
How would I go about changing individual icons though?

---

### Post by JoneYee on 2008-07-30
> **Andrew79 said:**
> Cool, thank you. It worked. I was opening the packages, so I did it the way you said, and BAM! Everything is changed, new icons! 
How would I go about changing individual icons though?


I pulled this: (user wanted to change the usp icon)
> gconf-editor

apps > usp

applet_icon_name

just add the name of your icon leaving off the extension, it seems to auto-detect the format at least, png and xpm

*edit* also it appears to look in /usr/share/icons by default.

From this thread: [http://ubuntuforums.org/showthread.php?t=228892](http://ubuntuforums.org/showthread.php?t=228892)

it may point you in the right direction until someone steps up who can answer your question more specifically.


EDIT: You might also try this:
[http://linuxtnt.wordpress.com/2008/05/22/changing-the-icon-for-a-file-type-with-nautilus-gnome-ubuntu/](http://linuxtnt.wordpress.com/2008/05/22/changing-the-icon-for-a-file-type-with-nautilus-gnome-ubuntu/)

---

### Post by Andrew79 on 2008-07-30
I figured out the way to change the individual icons now. Thank you for all you help.

---

### Post by JoneYee on 2008-07-30
> **Andrew79 said:**
> I figured out the way to change the individual icons now. Thank you for all you help.

Please mark the thread as solved =)  Glad to help.

---

