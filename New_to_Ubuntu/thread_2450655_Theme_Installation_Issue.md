---
title: "Theme Installation Issue"
date: 2020-09-18
forum: New to Ubuntu
---

### Post by desertwalker1 on 2020-09-18
Hey all, 

I'm trying to install the Flat Remix Darkest theme. I downloaded the version I want, extracted and moved to themes. However, it has not shown up as a theme option through Tweaks. 

The website recommended this command: gsettings set org.gnome.desktop.interface gtk-theme "Flat-Remix-GTK-Red"
However, that seems to be only for the default theme. Any suggestions will be greatly appreciated.

Here's the link for where I downloaded the theme from: [https://www.opendesktop.org/p/1297351](https://www.opendesktop.org/p/1297351)

Thanks in advance.

---

### Post by dino99 on 2020-09-18
A related wikihow  [https://www.wikihow.com/Install-Themes-in-Ubuntu#](https://www.wikihow.com/Install-Themes-in-Ubuntu#)
An ubuntu way [https://www.addictivetips.com/ubuntu-linux-tips/install-custom-themes-and-icons-in-linux/](https://www.addictivetips.com/ubuntu-linux-tips/install-custom-themes-and-icons-in-linux/)
A gnome howto [https://itsfoss.com/install-switch-themes-gnome-shell/](https://itsfoss.com/install-switch-themes-gnome-shell/)

---

### Post by ActionParsnip on 2020-09-18
I'd say replace the thing in the quotes with:
"Flat-Remix-GTK-Red-Dark"
"Flat-Remix-GTK-Red-Darker"
"Flat-Remix-GTK-Red-Darkest"

Then replace "Red" with "Blue", "Green", "Yellow" and so on as you need..... Did you try this?

---

### Post by Dennis N on 2020-09-18
> ...extracted and moved to themes
You should extract the archived folder to ~/.themes, not ~/themes. Note that there is a period before 'themes'.
Then it will appear in Tweaks.

---

### Post by desertwalker1 on 2020-09-18
> **dino99 said:**
> A related wikihow  [https://www.wikihow.com/Install-Themes-in-Ubuntu#](https://www.wikihow.com/Install-Themes-in-Ubuntu#)
An ubuntu way [https://www.addictivetips.com/ubuntu-linux-tips/install-custom-themes-and-icons-in-linux/](https://www.addictivetips.com/ubuntu-linux-tips/install-custom-themes-and-icons-in-linux/)
A gnome howto [https://itsfoss.com/install-switch-themes-gnome-shell/](https://itsfoss.com/install-switch-themes-gnome-shell/)

Thanks for the links dino! I'll give them a look.

> **ActionParsnip said:**
> I'd say replace the thing in the quotes with:
"Flat-Remix-GTK-Red-Dark"
"Flat-Remix-GTK-Red-Darker"
"Flat-Remix-GTK-Red-Darkest"

Then replace "Red" with "Blue", "Green", "Yellow" and so on as you need..... Did you try this?

Thanks for the suggestion. I haven't tried this yet, no. I'll give it a shot.

> **Dennis N said:**
> You should extract the archived folder to ~/.themes, not ~/themes. Note that there is a period before 'themes'.
Then it will appear in Tweaks.

I actually moved it to usr/share/themes. There was no .themes folder in the hidden files. I understand that you can create it. I'm going to try that and check if it works. Thanks for the reply Dennis.

---

### Post by desertwalker1 on 2020-09-18
No luck guys. I made the .themes and .icons folders. I installed the theme and icon versions, extracted them and moved the folders into their respective folders. I installed the user themes extension as well. 

The theme/icon theme did not show up in Tweaks. I also tried using the terminal. However, the command just switched to the default flat remix theme. Adding 'Red-Darkest' and so on did not change anything.

---

### Post by tea for one on 2020-09-18
Which file did you download?

There may be sub-folders within a master folder.

The sub-folders (i.e. colour choices or light/dark options) should be installed in ~/.themes or /usr/share/themes.

---

### Post by desertwalker1 on 2020-09-18
> **tea for one said:**
> Which file did you download?

There may be sub-folders within a master folder.

The sub-folders (i.e. colour choices or light/dark options) should be installed in ~/.themes or /usr/share/themes.

Appreciate the reply.

I installed a sub folder first: Red-Darkest-NoBorder 
I extracted and moved to usr/share/themes. No dice. Then I moved it to .themes in the Home directory. No change. 

I've also tried installing the flat-remix-gtk-master zip file. Extracted and moved to .themes. No result so far unfortunately. 

The User Themes extension in Tweaks is currently on. I've tried it with it off as well. Again, no change. The downloaded themes haven't shown up as an option in Gnome Tweaks and the terminal command only changes it to the one default theme despite adding -Darkest and -Darkest-NoBorder to the command.

---

### Post by Dennis N on 2020-09-18
Are you using Ubuntu 20.04? 

To see if I would have the same problem, using Ubuntu 20.04, I downloaded the theme 07-Flat-Remix-GTK-Red-Darkest_20200718.tar.xz and extracted the theme folder to ~/.local/share/themes (~/.themes should work too). It appeared in Tweaks after I closed it and reopened. But to get the red folders as shown below, you will need to also download the red icon theme that's offered.

But then I found a problem with it:  the music player Audacious doesn't theme properly with this theme, so it's a reject for me. But I hope it will work for you.

---

### Post by tea for one on 2020-09-18
I downloaded the file [COLOR="#000080"]09-Flat-Remix-GTK-Red-Darkest-NoBorder_20200718.tar.xz[/COLOR] to Downloads.

Extract the file to the same location i.e. Downloads.

```
cd Downloads 
```

```
sudo mv Flat-Remix-GTK-Red-Darkest-NoBorder/ /usr/share/themes
```

It then appears in gnome-tweaks under Appearance>Themes>Applications

---

### Post by desertwalker1 on 2020-09-18
> **tea for one said:**
> I downloaded the file [COLOR=#000080]09-Flat-Remix-GTK-Red-Darkest-NoBorder_20200718.tar.xz[/COLOR] to Downloads.

Extract the file to the same location i.e. Downloads.

```
cd Downloads 
```

```
sudo mv Flat-Remix-GTK-Red-Darkest-NoBorder/ /usr/share/themes
```

It then appears in gnome-tweaks under Appearance>Themes>Applications

Did the exact same thing (or at least I think so :P). Got this message in the terminal:

mv: cannot stat 'Flat-Remix-GTK-Red-Darkest-NoBorder/': No such file or directory

Maybe I need to remove all the other files that I downloaded first?

---

### Post by tea for one on 2020-09-19
> **desertwalker1 said:**
> mv: cannot stat 'Flat-Remix-GTK-Red-Darkest-NoBorder/': No such file or directory

There are various reasons why the installation of the theme failed e.g.

You extracted the folder in a different directory.
The folder was not extracted at all.
You downloaded a different zip file.
You ran the terminal command while in the wrong directory.

Can you find the folder?
Where is the folder located on your PC?
Please supply the [COLOR="#0000CD"]exact[/COLOR] name of your folder?
Can you give us the [COLOR="#0000CD"]exact[/COLOR] name of the zip file you downloaded?

Theme changes can be a bit mysterious until you've done it a few times. ;)

---

### Post by desertwalker1 on 2020-09-19
> **tea for one said:**
> There are various reasons why the installation of the theme failed e.g.

You extracted the folder in a different directory.
The folder was not extracted at all.
You downloaded a different zip file.
You ran the terminal command while in the wrong directory.

Can you find the folder?
Where is the folder located on your PC?
Please supply the [COLOR=#0000CD]exact[/COLOR] name of your folder?
Can you give us the [COLOR=#0000CD]exact[/COLOR] name of the zip file you downloaded?

Theme changes can be a bit mysterious until you've done it a few times. ;)

I'd be happy to provide those details, yep!

Folder that I downloaded: [09-Flat-Remix-GTK-Red-Darkest-NoBorder_20200718.tar.xz]("https://www.opendesktop.org/p/1297351/startdownload?file_id=1595062746&file_name=09-Flat-Remix-GTK-Red-Darkest-NoBorder_20200718.tar.xz&file_type=application/x-xz&file_size=132780")
Website link: [https://www.opendesktop.org/p/1297351](https://www.opendesktop.org/p/1297351) 

Zip file name: 09-Flat-Remix-GTK-Red-Darkest-NoBorder_20200718.tar.xz
Folder name: 09-Flat-Remix-GTK-Red-Darkest-NoBorder_20200718

I can see the folder in the .themes folder after I moved it from Downloads to the .themes folder in the Home directory.

How did I create the .themes folder? I right clicked and chose the New Folder option and renamed it .themes in the Home directory. 

Hope that helps. :P

---

### Post by tea for one on 2020-09-19
Your folder name is different to the one mentioned in your post 11.

Flat-Remix-GTK-Red-Darkest-NoBorder/
[COLOR="#0000CD"]09-[/COLOR]Flat-Remix-GTK-Red-Darkest-NoBorder[COLOR="#0000CD"]_20200718[/COLOR]

Terminal commands will always fail unless you use the correct file/folder names.

I suggest that you unzip the tar file in your Downloads folder and use the terminal command I gave earlier but using the correct extracted folder name.

---

### Post by desertwalker1 on 2020-09-19
> **tea for one said:**
> Your folder name is different to the one mentioned in your post 11.

Flat-Remix-GTK-Red-Darkest-NoBorder/
[COLOR=#0000CD]09-[/COLOR]Flat-Remix-GTK-Red-Darkest-NoBorder[COLOR=#0000CD]_20200718[/COLOR]

Terminal commands will always fail unless you use the correct file/folder names.

I suggest that you unzip the tar file in your Downloads folder and use the terminal command I gave earlier but using the correct extracted folder name.

Ok, here's what I did:

Extracted. Used your commands:

```
cd Downloads
```

```
sudo mv 09-Flat-Remix-GTK-Red-Darkest-NoBorder_20200718/ /usr/share/themes
```

No error in the terminal this time. The folder got moved to the usr/share/themes folder. However, still no option in Gnome Tweaks. o.o

---

### Post by tea for one on 2020-09-19
Have you previously managed to use gnome-tweaks to change from the default theme to any other included theme?

Also, please post in code tags the list of themes in /usr/share/themes.

```
cd /usr/share/themes
```

```
ls
```

Example below

```
removed@removed:/usr/share/themes$ ls
Adwaita         Default       vimix-dark-ruby  Yaru-light     Yaru-Red-light
Adwaita-dark    Emacs         Yaru             Yaru-Red
Cameo-Dark-Red  HighContrast  Yaru-dark        Yaru-Red-dark

```

---

### Post by desertwalker1 on 2020-09-19
> **tea for one said:**
> Have you previously managed to use gnome-tweaks to change from the default theme to any other included theme?

Also, please post in code tags the list of themes in /usr/share/themes.

```
cd /usr/share/themes
```

```
ls
```

Example below

```
removed@removed:/usr/share/themes$ ls
Adwaita         Default       vimix-dark-ruby  Yaru-light     Yaru-Red-light
Adwaita-dark    Emacs         Yaru             Yaru-Red
Cameo-Dark-Red  HighContrast  Yaru-dark        Yaru-Red-dark

```

I have only changed from the default theme to the themes already available through gnome tweaks. But yes, the already included themes do work on switching. I just tested them again just in case. This was my first attempt at trying to install a downloaded theme. :P Again, appreciate your patience. 

As per your instructions:

```
***@***:~$ cd /usr/share/themes
***@***:/usr/share/themes$ ls
09-Flat-Remix-GTK-Red-Darkest-NoBorder_20200718  Emacs         Yaru-dark
Adwaita                                          HighContrast  Yaru-light
Adwaita-dark                                     Raleigh
Default                                          Yaru
```

---

### Post by tea for one on 2020-09-19
Therefore gnome-tweaks is functioning OK and, possibly, there is something odd about the [COLOR="#0000CD"]09-Flat-Remix-GTK-Red-Darkest-NoBorder_20200718[/COLOR] folder.

Are there other folders (i.e colour or light/dark choices) within 09-Flat-Remix-GTK-Red-Darkest-NoBorder_20200718?

Finally, now we know gnome-tweaks is working, can you start from scratch and follow the instructions in post 10.

Please use the same theme because I tested it before posting.

If this is successful, then we can have another look at [COLOR="#0000CD"]09-Flat-Remix-GTK-Red-Darkest-NoBorder_20200718[/COLOR]

---

### Post by Dennis N on 2020-09-19
09-Flat-Remix-GTK-Red-Darkest-NoBorder_20200718 is not the theme folder. It should appear as it does here:

```
dmn@Tyana-vm:~/.local/share/themes$ ls -1
Flat-Remix-Dark-2004
Flat-Remix-Dark-mod
[COLOR="#FF0000"]Flat-Remix-GTK-Red-Darkest-NoBorder[/COLOR]

```

The name on your folder looks like the archive. If you open your theme folder, what do you see? It should be this:

```
dmn@Tyana-vm:~/.local/share/themes/Flat-Remix-GTK-Red-Darkest-NoBorder$ ls
cinnamon  gtk-2.0  gtk-3.0  index.theme  metacity-1  xfwm4
```

---

### Post by desertwalker1 on 2020-09-20
Hey guys. Thought I'd take screenshots of the folder and its contents. Maybe that will help? 

The first screenshot shows the themes folder. The second screenshot is after opening the 09 Flat Remix folder and the folder inside, and the third screenshot is another click of the folder inside the 09 Flat Remix folder and the contents inside. Here they are:


[ATTACH=CONFIG]286996[/ATTACH][ATTACH=CONFIG]286997[/ATTACH][ATTACH=CONFIG]286998[/ATTACH]

Hopefully I've attached them correctly.

---

### Post by Dennis N on 2020-09-20
The folder in your second screenshot is the theme folder. It must be in /usr/share/themes. So you could copy it to /usr/share/themes, and then optionally delete the 09-Flat-Remix-GTK..

Be sure to get the color icon theme to match. Also there is a Flat Remix gnome shell theme that can be installed.

---

### Post by desertwalker1 on 2020-09-20
> **Dennis N said:**
> The folder in your second screenshot is the theme folder. It must be in /usr/share/themes. So you could copy it to /usr/share/themes, and then optionally delete the 09-Flat-Remix-GTK..

Be sure to get the color icon theme to match. Also there is a Flat Remix gnome shell theme that can be installed.

Yes that was it. It worked finally!

[ATTACH=CONFIG]287000[/ATTACH]

I opened the 09 Flat Remix folder in the terminal and used the command posted by tea for one in post #10. Thanks guys! As you'll notice, the icons appeared too in Gnome Tweaks. I'm not sure why to be honest. :P But I'm not complaining lol. In fact, all the different colors for icons appeared as options in Tweaks. Maybe I accidentally installed them while testing along the way? Maybe it was included in the folder? Not sure. 

@Dennis: Do you mind explaining what you mean by the gnome shell theme?

---

### Post by Dennis N on 2020-09-20
> @Dennis: Do you mind explaining what you mean by the gnome shell theme? 

A gnome-shell theme will theme the top bar, menus in the top bar, the Calendar & Clocks, and notifications. I use the Flat Remix Dark gnome-shell theme. There are a couple of variations one of which should complement what you have.

As to your having all the colors, you may have downloaded the master.zip? It had folders inside for all the color variations. I downloaded just the single color I wanted to try.

---

### Post by desertwalker1 on 2020-09-20
> **Dennis N said:**
> A gnome-shell theme will theme the top bar, menus in the top bar, the Calendar & Clocks, and notifications. I use the Flat Remix Dark gnome-shell theme. There are a couple of variations one of which should complement what you have.

As to your having all the colors, you may have downloaded the master.zip? It had folders inside for all the color variations. I downloaded just the single color I wanted to try.

I believe I did, yes. That was probably it. 

A final question though: If you look at the screenshot in my post #22; the 09 Flat Remix folder is still in the themes folder. I could not copy the Flat Remix folder from it, nor can I delete it. So in order to get the theme to work as per your instructions, I extracted it again. So essentially, now there are two folders in the themes folder (09 Flat and just Flat). 

How do I go about removing the 09 Flat Remix folder? I hope that's understandable. This is getting a bit jumbled, I realize. :P

---

### Post by Dennis N on 2020-09-20
> How do I go about removing the 09 Flat Remix folder? I hope that's understandable..
It's owned by root, so you need to use sudo with the remove command.
```
cd /usr/share/themes
sudo rm -R 09-Flat-Remix-GTK-Red-Darkest-NoBorder_20200718

```
assuming that's the correct name of the folder to be removed.

---

### Post by tea for one on 2020-09-20
> **desertwalker1 said:**
> How do I go about removing the 09 Flat Remix folder? I hope that's understandable. This is getting a bit jumbled, I realize. :P

```
cd /usr/share/themes

```

```
sudo rm -r 09-Flat-Remix-GTK-Red-Darkest-NoBorder_20200718
```

With the second command, if you do not know the exact file name, you can begin typing 09 and then hit **Tab** and the terminal should complete the file name.

Double check before removing. ;)

Tab completion is very useful to avoid typing long file names or commands,

I'm pleased that your initial problem is solved and you can now experiment with other themes.

If you like red accents, have a look at [https://www.gnome-look.org/p/1013698/](https://www.gnome-look.org/p/1013698/) (ruby version)

Edit: Dennis N 1 - tea for one 0

---

### Post by desertwalker1 on 2020-09-20
> **Dennis N said:**
> .
It's owned by root, so you need to use sudo with the remove command.
```
cd /usr/share/themes
sudo rm -R 09-Flat-Remix-GTK-Red-Darkest-NoBorder_20200718

```
assuming that's the correct name of the folder to be removed.

> **tea for one said:**
> ```
cd /usr/share/themes

```

```
sudo rm -r 09-Flat-Remix-GTK-Red-Darkest-NoBorder_20200718
```

With the second command, if you do not know the exact file name, you can begin typing 09 and then hit **Tab** and the terminal should complete the file name.

Double check before removing. ;)

Tab completion is very useful to avoid typing long file names or commands,

I'm pleased that your initial problem is solved and you can now experiment with other themes.

If you like red accents, have a look at [https://www.gnome-look.org/p/1013698/](https://www.gnome-look.org/p/1013698/) (ruby version)

Edit: Dennis N 1 - tea for one 0

And that resolves it. The journey (at least this specific one >.>) comes to an end. Thanks guys! Until I mess something else up. :P

P.S: + 1mil for that tab completion tip. Appreciate it!

---

