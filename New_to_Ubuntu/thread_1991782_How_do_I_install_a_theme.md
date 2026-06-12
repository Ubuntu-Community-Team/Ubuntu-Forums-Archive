---
title: "How do I install a theme?"
date: 2012-05-31
forum: New to Ubuntu
---

### Post by Shadius on 2012-05-31
Hello everybody :)

I'd like to know how to install a new theme for Ubuntu. I'm running 12.04, but I use Gnome Classic (No Effects). I see in **Appearances**, there are a few themes, but I don't really like how they go with my wallpaper and I don't really like the icons. I need to know where to go to find the themes, how to install it, and also, if it's possible to mix and match. Say I like how the window borders look and the panel looks, but hate the icons, can I install icons to replace the icons that came with a theme? I'm a beginner as you can probably tell so please explain in simple terms. Thank you!

---

### Post by waynefoutz on 2012-05-31
the easiest way to is to install "MyUnity" from the Software Center. You can tweak to your heart's content.

UbuntuTweak is slightly more powerful, in my opinion. It's not in the repositories, you can get it here:

[http://www.noobslab.com/2012/04/install-ubuntu-tweak-070-on-ubuntu.html]("http://www.noobslab.com/2012/04/install-ubuntu-tweak-070-on-ubuntu.html")

---

### Post by fantab on 2012-05-31
You can start by looking **[here]("http://gnome-look.org/index.php?xcontentmode=167&PHPSESSID=26acaf19d1278e01351e8b7e22775756")**.

I don't use Gnome Classic but think you can install themes manually by placing the yourthemefolder in /usr/share/themes and using it with some sort of tweak tool or dconf-tools or gconf-editor which ever works.

If Gnome Classic uses Metacity then I guess you choose your window borders.

---

### Post by NikTh on 2012-05-31
Here it has a lot of themes --> [http://gnome-look.org/?xsection=home](http://gnome-look.org/?xsection=home) 
Go for GTK3+ or GTK2+ download - extract - and put the folder with theme name to your hidden folder named .themes (with the dot) . 
When you open nautilus  hit Ctrl+h to see hidden folders. If you haven't the folder just create it. (remember , with dot ) 
After that you must use a tool like MyUnity or gnome-tweak-tool or ubuntu-tweak to apply the theme. 
First 2 tools are in ubuntu repositories so you can find them in Ubuntu Software Center . 
"Ubuntu - tweak" you can find it here --> [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by zombifier25 on 2012-05-31
There are loads of themes on gnome-look.org . Category GTK 3.x for GTK themes, Icons for icon themes.

For GTK themes, download them and extract into ~/.themes (if you want the theme for you only) or /usr/share/themes (if you want it to be available to all) Same for icon themes, ~/.icons and /usr/share/icons. After that, install a tool like Ubuntu Tweak to change them. Note that GTK themes and windows border usually comes together, but they can be chosen separately.

---

### Post by deadflowr on 2012-05-31
If your going to be running gnome classic why install myunity when you can install gnome-tweak-tool. When you get your newer themes into the theme folder in /usr/share just open advanced settings.

---

### Post by traditionalist on 2012-05-31
> **Shadius said:**
> Hello everybody :)

I'd like to know how to install a new theme for Ubuntu. I'm running 12.04, but I use Gnome Classic (No Effects). I see in **Appearances**, there are a few themes, but I don't really like how they go with my wallpaper and I don't really like the icons. I need to know where to go to find the themes, how to install it, and also, if it's possible to mix and match. Say I like how the window borders look and the panel looks, but hate the icons, can I install icons to replace the icons that came with a theme? I'm a beginner as you can probably tell so please explain in simple terms. Thank you!

Make your own, it's easy;

[http://ubuntuforums.org/showthread.php?t=1988119](http://ubuntuforums.org/showthread.php?t=1988119)

I have been using Ubuntu for a couple of weeks, and I set that theme up in a short time "on the fly".  I have improved on it a  lot since then.

Here is my latest revision for my desktops attached, also easy to tweak if you want something else

If you want to use other Icons etc, I found this to be very practical indeed ( and not just for themes! );

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by Shadius on 2012-05-31
Thanks for the information. :) Is there a difference between the GTK 1.x, GTK 2.x and GTK 3.x? Like I'm confused if GTK 3.x goes with GNOME 3, GTK 2.x goes with GNOME 2 and such? Is that how it works? Remember I'm using GNOME Classic (No Effects), ***not*** Unity. 

Might you suggest a theme for me to try? :)

---

### Post by fantab on 2012-05-31
You may be using Gnome Classic interface but the engine underneath is Gtk-3.  Since 11.10 its only Gnome3.

---

### Post by NikTh on 2012-05-31
> **fantab said:**
> You may be using Gnome Classic interface but the engine underneath is Gtk-3.  Since 11.10 its only Gnome3.
+1 

Also do not forget to read the instructions. If you download a theme from  [http://gnome-look.org](http://gnome-look.org) you will see (at most of them) detailed instructions of how to apply the theme.

---

### Post by Shadius on 2012-06-01
> **fantab said:**
> You may be using Gnome Classic interface but the engine underneath is Gtk-3.  Since 11.10 its only Gnome3.

Thank you for clearing that up.

> **NikTh said:**
> +1 

Also do not forget to read the instructions. If you download a theme from  [http://gnome-look.org](http://gnome-look.org) you will see (at most of them) detailed instructions of how to apply the theme.

Thank you. I've been noticing that. Stuff like pixbuf and unico, which I have no idea of what the are, but I assume they are engines...?

---

### Post by Shadius on 2012-06-03
Hey again,

I'm trying to install this theme, [Hope]("http://gnome-look.org/content/show.php/Hope+gtk3?content=141491"), but I'm having some problems. In Advanced Settings (Gnome Tweak Tool), whenever I select Hope as the GTK+ theme, the fonts will disappear or maybe the font colors change to white in the windows. Anyway, the theme doesn't look like how it looks on [GNOME-Look]("http://gnome-look.org/content/show.php/Hope+gtk3?content=141491"). I've made sure I've met all the requirements for the installation like the Unico GTK+ engine, which to my understanding is already installed with GNOME 3. I've included some screenshots. So what's the problem here?

---

### Post by mapes12 on 2012-06-03
I recently did a fresh install of 12.04 on my machine then installed a Mac theme by following the instructions here:-

[http://www.noobslab.com/2012/05/mac-os-x-lion-for-ubuntu-1204-precise.html](http://www.noobslab.com/2012/05/mac-os-x-lion-for-ubuntu-1204-precise.html)

It worked perfectly. Then once I had everything as I wanted it including some packages like Ubuntu-restricted- extras, K3B and the Medibuntu repos, I made a system backup using the backup function of Remastersys to make a custom installation DVD of my new system so that if I break it (probability is high) and I can just reinstall it without having to go through the process from scratch. The custom installation DVD will install on other machines as well.

:guitar:

---

