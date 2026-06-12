---
title: "Renaming Trash and Changing Icon"
date: 2012-07-31
forum: New to Ubuntu
---

### Post by VX967 on 2012-07-31
Hey everyone, I'm totally new to Ubuntu and have absolutely no idea what I'm doing. Great introduction. XD

Anyway, I'd like to accomplish a (hopefully) simple task. I'd like to rename the "Trash" to "Toilet," change its icon, replace the "Empty Trash" button text with "Flush Toilet," and when doing so, triggering a sound file of- you guessed it- a toilet flushing. Because why not?

I've looked up how to rename the Trash, and have tried a couple of methods, but none seem to work. The main method I stumbled across was to open the Configuration Editor (gconf-editor), selecting apps/nautilus/desktop, and changing the text string for trash_icon_name. I've already done this, but it doesn't seem to affect anything. It's still called the Trash. Are there other methods of renaming it, or doing any of the other things I listed above?

If it helps, I'm running Ubuntu 12.04 LTS.

---

### Post by gifford on 2012-07-31
If I understand your question...this link might help.
[http://www.upubuntu.com/2012/07/menulibre-advanced-menu-editor-for.html](http://www.upubuntu.com/2012/07/menulibre-advanced-menu-editor-for.html)

---

### Post by Paddy Landau on 2012-07-31
Did you log out and back in after making your changes?

---

### Post by VX967 on 2012-07-31
@gifford: I downloaded Menu Libre and took a look at it, but I didn't see anything that lets you access or edit the Trash.

@Paddy Landau: Yep: logged off, logged in, restarted, and the Trash is still called the Trash. No change. Although something seemed suspicious- when accessing the trash_icon_name key via the configuration editor, this information is listed below:

```

This key has no schema
Key Name: /apps/nautilus/desktop/trash_icon_name
Key Owner: (None)
Short Description: (None)
Long Description: (None)
```

I feel that it really shouldn't say "(None)" in those fields but... I might be wrong. I'm just starting with Ubuntu, so I've got a lot to learn. Is this information significant at all?

---

### Post by Paddy Landau on 2012-08-01
I've come back to my computer. I see that my bin is called the Rubbish Bin, and it is in the Launcher. Where is your bin with the name "Trash"?

---

### Post by Frogs Hair on 2012-08-01
Ubuntu uses the dconf-editor so you may have to make changes using that application. The path you described in the first post in the gconf-editor doesn't seem to appear in the dconf-editor unless I am looking in the wrong place.

I also wonder if the context menu and applications linked to trash such as mail clients and office programs would reflect the change. The name for the icon on my U.S. English system is trash . That name appears in the Unity launcher and all links to that folder.

---

### Post by Paddy Landau on 2012-08-01
I wonder if the difference between your and my names is in the language? You use US English, whereas I use UK. If that is the case, we'd have to find out where the language files are held.

---

### Post by drs305 on 2012-08-01
The Ubuntu Tweak app allows you to change the trash icon and name. I don't know where the name change actually shows up (only on the Desktop or in the filename itself), but it's worth a look. (Note: The Tweaks link in my signature line is for something else).

---

### Post by VX967 on 2012-08-02
> **Frogs Hair said:**
> Ubuntu uses the dconf-editor so you may have to make changes using that application. The path you described in the first post in the gconf-editor doesn't seem to appear in the dconf-editor unless I am looking in the wrong place.

I had to download dconf-editor [thought it would already be installed, but I guess not.] I actually did find it under org.gnome.nautilus.desktop.trash_icon_name. Changing that string DID change the text for the trash icon in the desktop, but not the side panel [The Dash/Dashboard, or Launcher?] In addition, when I click on the "Toilet" icon on the desktop, the resulting window still calls it the "Trash" folder.

@Paddy Landau: Yeah, I believe that UK English calls it the "Rubbish Bin" whereas the US English calls it "Trash." I could try looking for the language files, though I'd had no idea where to look. Google is my friend...

@drs305: I found the website for Ubuntu Tweak, and downloaded it. It shows up with a ".deb" extension. When I click it, it just opens up the ubuntu-tweak page in the Ubuntu Software Center, but I can't seem to find how to actually install and use the software...

---

### Post by gifford on 2012-08-02
When the Ubuntu software center opens with "tweak" you should have the install option. Let the software center do the installation.

---

### Post by VX967 on 2012-08-02
@gifford: Oops. Didn't see the Install button because the window extended beyond the monitor. Figures. XD 

Anyway, I downloaded Tweak. Looks like I can change the name of the Trash with it, but again, it ONLY affects the desktop name and not the actual Trash. So it's doing the same thing as the dconf-editor method.

You guys think I'd be able to open up the US English Language file and modify the name of the Trash there?

---

### Post by VX967 on 2012-08-05
Other related questions: what format would a picture have to be in order to replace the icon? Can it just be a .png, or is there a specific extension or format for icons?

In addition, I would assume that .ogg would be the optimal format for playing an audio file. If otherwise, let me know.

I've found that when you empty the trash, a sound file isn't triggered by default, so... how difficult would it be to trigger a sound file to play when the trash is emptied?

---

