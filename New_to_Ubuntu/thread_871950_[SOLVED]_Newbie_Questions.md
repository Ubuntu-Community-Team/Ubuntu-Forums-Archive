---
title: "[SOLVED] Newbie Questions"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by diego898 on 2008-07-27
1. What is the ubuntu equivalent to "Program Files"? 

2. How do install a theme? People keep saying go to gnome-look.org and download one but under what section do I download from? How do I install a theme?

3. Will my prefs.js file from firefox on windows work on this installation of the fox?

4. What are some necessary programs to install? Amarok?

---

### Post by perlluver on 2008-07-27
> **diego898 said:**
> 1. What is the ubuntu equivalent to "Program Files"? 

2. How do install a theme? People keep saying go to gnome-look.org and download one but under what section do I download from? How do I install a theme?

3. Will my prefs.js file from firefox on windows work on this installation of the fox?

4. What are some necessary programs to install? Amarok?

For 2, You want to download GTK.2 Themes, and Metacity.  To Install them, you just drag them into the themes window.  Not sure about 3.  And if you want Amarok you can install it.  But gnome already comes with rhythmbox.  If you need MP3 support and Flash, search for ubuntu-restricted-extras in synaptic package manager.

---

### Post by gjoellee on 2008-07-27
there is actually nothing that is like Program Files in Ubuntu, but if you want to enter the program folder many of then is viewable if you go to your home folder and press CTRL+H

the download gtk.2 themes from can be dragged over to the theme window, which is located in System->Preferences->Appearnce

---

### Post by scragar on 2008-07-27
1. I havn't used windows enough to know what the folder(I'm assuming it's a folder right?) is/does, explain a little.
2. Those files are for emerald, which is a pretty cool tool. Guide: [http://hacktivision.com/index.php/2008/01/08/how-to-install-emerald-theme-manager-in-?blog=2](http://hacktivision.com/index.php/2008/01/08/how-to-install-emerald-theme-manager-in-?blog=2)
3. Yeah, your entire firefox settings can be moved/coppied over, ubuntu stores your settings in ~/.mozilla/firefox where ~ repesents your home folder. use ctrl+H to see folders starting with . in the file manager.
4. everything required is normaly installed by default, anything after that is a matter of preference.

---

### Post by UbuntuNerd on 2008-07-27
to install themes use Emerald Theme manager here is a real simple  guide 


[http://hacktivision.com/index.php/2008/06/07/how-to-enhance-ubuntu-8-04-hardy-heron-e?blog=2]("http://hacktivision.com/index.php/2008/06/07/how-to-enhance-ubuntu-8-04-hardy-heron-e?blog=2") 

once you download the theme you want from gnome-look.org you can open emerald theme manager and browse for the theme you downloaded and install thats it

---

### Post by diego898 on 2008-07-27
Are there fonts that I can install that look clearler?

---

### Post by Ryadt on 2008-07-27
> **diego898 said:**
> Are there fonts that I can install that look clearler?

System > Preferences > Apperance > Fonts.

Can you please start a new thread for a different question and also use a more descriptive title.

---

### Post by Vicfred on 2008-07-27
If you're using gnome you could try Exaile as a music player, it's my favourite <3

---

### Post by RiceMonster on 2008-07-27
> **diego898 said:**
> 4. What are some necessary programs to install? Amarok?

Well what do you want to do? Everything the average person would need is already installed by default. Amarok is an audio player, which I like, but you can use Rhythmbox, which is installed by default, or some of the many other players available like Audacious, Exaile, Banshee, etc.

---

### Post by diego898 on 2008-07-27
> **Ryadt said:**
> System > Preferences > Apperance > Fonts.

Can you please start a new thread for a different question and also use a more descriptive title.

you're right sorry. Thanks for the help everyone

---

### Post by diego898 on 2008-07-27
> **Ryadt said:**
> System > Preferences > Apperance > Fonts.

Can you please start a new thread for a different question and also use a more descriptive title.

are there fonts that are part of the restricted packages ?

---

### Post by geekygirl on 2008-07-27
If you want the fonts that come with a Windows install such as Verdana or Courier New, Arial etc...you will have to install a package called **msttcorefonts**

Easiest way is to open a terminal window and type: 

```
sudo apt-get install msttcorefonts
```

If you want other fonts there are some font packages in Synaptic, just do a search for 'fonts'.

If you are using an LCD screen and mean that you want smoother looking fonts, as was already mentioned you can open: system/appearance/fonts and there are some settings in there to adjust the appearance of the fonts with things like Sub-Pixel Rendering etc.

---

