---
title: "How to set up dual screens Extended desktop"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by Paddy Landau on 2008-06-05
I have two screens. One that comes built into my laptop, and another larger monitor that I've attached to the laptop.

On Windows, I set my larger monitor as the main monitor, with the smaller screen as an extension to the desktop. In other words, I can (for example) drag windows between the two screens. This is a huge help to me when I want to compare two windows-full of data, as I often do.

However, my Ubuntu sees the two screens as identical; both screens show the same thing (but the windows run off the bottom of the smaller screen, because it's smaller).

How do I ask Ubuntu to do the same thing -- to use one monitor as the main desktop, and the other as an extended desktop?

---

### Post by BikerGeek on 2008-06-05
Maaaan are you in for a lot of fun. Took me 3 days to get mine set up to my satisfaction.

Here's a good start since it covers so many methods.

[http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)

---

### Post by Inxsible on 2008-06-05
Depends on your graphics card. If you use nVidia, then firstly you should be using the restricted drivers. If you are, 

1) then press Alt+F2 and type in ```
nvidia-settings
```2)In the window that comes up, type in your password - if required - and then look for TwinView. That's what you need to set. Also mark which one you want to make your primary monitor and which one your secondary.

3)Make sure you click "Save to X config file" or something along those lines. Then either reboot or simply restart X (Ctrl + Alt + Backspace)


If you have an ATI card, then I am not sure.

---

### Post by dicecca112 on 2008-06-05
> **Inxsible said:**
> Depends on your graphics card. If you use nVidia, then firstly you should be using the restricted drivers. If you are, 

1) then press Alt+F2 and type in ```
nvidia-settings
```2)In the window that comes up, type in your password - if required - and then look for TwinView. That's what you need to set. Also mark which one you want to make your primary monitor and which one your secondary.

3)Make sure you click "Save to X config file" or something along those lines. Then either reboot or simply restart X (Ctrl + Alt + Backspace)


If you have an ATI card, then I am not sure.

In order for changes to be saved you need to run nvidia-settings as sudo.  If not, it won't save.  Setting up with nvidia-settings is rather easy, should take no more than 10 minutes

---

### Post by Inxsible on 2008-06-05
> **dicecca112 said:**
> In order for changes to be saved you need to run nvidia-settings as sudo.  If not, it won't save.  Setting up with nvidia-settings is rather easy, should take no more than 10 minutes
you are right :)

But if you type the command in the Run Dialog(as I mentioned) as opposed to the terminal, all administration apps will ask you for you password, correct?

Correct me if I am wrong.

---

### Post by Paddy Landau on 2008-06-06
> **Inxsible said:**
> Depends on your graphics card. If you use nVidia...
How do I tell what graphics card I use?

---

### Post by Inxsible on 2008-06-06
> **Paddy Landau said:**
> How do I tell what graphics card I use?Open up a terminal and type in ```
lspci | grep VGA
```Post the result back here.

---

### Post by ameseisch on 2008-06-06
nvidia-settings is very handy. anyway to acces that through gui? that would be even nicer.

twinView works but i do have some weird bugs. Firefox renders some pages very strangely. fonts are to large and things aren't sized right. Not sure why twinview would cause this, but so it is.

---

### Post by Inxsible on 2008-06-06
> **ameseisch said:**
> nvidia-settings is very handy. anyway to acces that through gui? that would be even nicer.

twinView works but i do have some weird bugs. Firefox renders some pages very strangely. fonts are to large and things aren't sized right. Not sure why twinview would cause this, but so it is.I have noticed in Hardy, that the NVidia Settings is also a menu item under System for Xubuntu. 

It might be there for Ubuntu under System>>Administration as well.

I can say for sure that until gutsy, it wasn't automatically created.

---

### Post by ameseisch on 2008-06-06
i had to instal nvidia-settings on ubuntu 8.04. it prompted me to instal it the first time I entered nvidia-settings in the terminal.

also noticed that large font-thing happens in the help windows as well, and that gnome pannels don't really like the extended desktop. I acidently deleted my wireless monitor in the top panel when I was trying to get them arranged nicely. creating a lot of extra work for myself.

---

### Post by Paddy Landau on 2008-06-07
> **Inxsible said:**
> Open up a terminal and type in ```
lspci | grep VGA
```Post the result back here.
This is what I get:

```
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
```I guess this means that I should use Xinerama. I'll try it, anyway, and report back here.

---

### Post by Paddy Landau on 2008-06-07
I've made a copy of xorg.conf and made the changes (but only on the copy so far).

Now, I'm unsure about using Xinerama, because...

[LIST=1]
[*][quote="[Wikipedia]("http://en.wikipedia.org/wiki/Xinerama")"][As of 2008]("http://en.wikipedia.org/wiki/As_of_2008"), Xinerama is planned to be [deprecated]("http://en.wikipedia.org/wiki/Deprecated") in the future by [X.org]("http://en.wikipedia.org/wiki/X.Org_Server") in favor of [XRandR]("http://en.wikipedia.org/wiki/XRandR").[/quote]
[*][quote="[Sourceforge]("http://sourceforge.net/projects/xinerama")"]As of 2007-09-20 10:44, this project is no longer under active development.[/quote]
[/LIST]
Any comments?

(Anyway, my installation manager isn't working, so I can't progress until that's solved. :()

---

### Post by Paddy Landau on 2008-06-23
Yay! I got it working!

For anyone else who's struggling, this is how I did it...


[LIST]
[*]I made a backup of xorg.conf as explained in the [How To post]("http://ubuntuforums.org/showthread.php?p=1288786#post1288786").
[*]I discovered a hidden menu item: Applications -> Other -> Screens and Graphics. (To reveal this menu, use System -> Preferences -> Main Menu.) I experimented with this Screens and Graphics program (making use of the backup copy of xorg.conf) until I'd manged to at least get both screens responding, albeit with incorrect resolutions.
[*]I made another backup of xorg.conf at this point, so I could revert to it or refer to it.
[*]Referring to the tips in the aforementioned [How To post]("http://ubuntuforums.org/showthread.php?p=1288786#post1288786"), and to the [Xinerama "How To"]("http://ubuntuforums.org/showthread.php?p=1773624"), I experimented hugely until I got it right. Watch out: Even the smallest typo causes problems! Do baby steps: Make a small change, test, and repeat.
[/LIST]

There was lots that I wouldn't have known about had I not found the Screens and Graphics program.

Once you have it working, back up your new xorg.conf. You should then keep two copies just in case: The original xorg.conf (before you started to change things), and the new working xorg.conf. Put them on your backups.

---

### Post by Paddy Landau on 2008-07-01
Well, Xinerama is deprecated. And someone pointed me to a much better method (far quicker and easier to set up):

[RandR HowTo]("http://www.thinkwiki.org/wiki/Xorg_RandR_1.2")

---

