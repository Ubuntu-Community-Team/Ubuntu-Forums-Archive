---
title: "How do I change the appearance of the close, maximize, minimize buttons?"
date: 2013-07-30
forum: New to Ubuntu
---

### Post by MagisterDixit on 2013-07-30
I recently switched from Mint 15 to Ubuntu 12.04 LTS. The transition was easy for the most part and with the help of google and youtube I was able to customize just about everything the way I like it except the title bar buttons. I do not want to change the theme for my whole computer. I like Ambiance. I do want to know: How do I change the close, maximize, and minimize buttons to something more attractive? I would like for them to look like Mac (red close, yellow min, green max- all round) but even Windows is preferrable to the Ubuntu default look. Can I change just the buttons and how? The only help google and youtube gave me was how to switch sides but that is not what I want to do.

---

### Post by deadflowr on 2013-07-30
First, for 12.04, install MyUnity. It's in the repos(software center)

Second go here
[http://gnome-look.org/?xsection=home](http://gnome-look.org/?xsection=home)

Find the theme you want to use, if you can.

Then download it, and open the home folder and go to Downloads.
Find the tar file for the theme you downloaded and extract it.
When extracting move the location of where to extract to your home folder.
The home folder will list the normal folder you have, such as Downloads document, Pictures,Videos ,etc,etc.
Before extracting here, make a new folder and call it .themes. The dot "." is important.
Then extract and when finished, open up the Myunity program and go to the themes section.
The newly added theme should show up.

The theme folder should be listed as /home/yourusername/.themes

Good luck.

---

### Post by mojo706 on 2013-07-30
Hello **FpCrPnW**, 
Here is a short tutorial that you can use to solve your problem. 
First of all to be able to apply themes to your system (I know that you don't want to change the theme yet) and also to change the said close, maximize, and minimize buttons install Ubuntu Tweak using the following commands in the [Terminal]("https://help.ubuntu.com/community/UsingTheTerminal") : Open the terminal by using the following shortcut ```
ctrl + alt + T
```

This first command adds the tualatrix [ppa]("https://launchpad.net/ubuntu/+ppas") to your computer.
```
sudo add-apt-repository ppa:tualatrix/ppa
```
This second command sort allows you to refresh your software sources
```
sudo apt-get update
```
This command install ubuntu-tweak
```
sudo apt-get install ubuntu-tweak
```

Now that you have installed Ubuntu Tweak, you now need to install a ***macish*** theme use the following commands in the Terminal.

```
sudo add-apt-repository ppa:webupd8team/themes
```
```
sudo apt-get update
```
```
sudo apt-get install adwaita-cupertino-gtk-theme
```

Adwaita Cupertino gtk theme is the theme with the actual ***close***, ***maximize*** and ***minimize*** buttons that you want

Now fireup Ubuntu Tweak (click Dash Home then search for Ubuntu Tweak) and under the Tweaks Tab (see screenshot below)
[IMG]http://i.imgur.com/1s7ZiPt.jpg[/IMG] 
choose Theme then under themes click the windows theme drop down and choose the window theme you want.(see below screenshot)
[IMG]http://i.imgur.com/vRibJIy.png[/IMG]

Hope this helps you. Any more questions feel free to ask!

---

### Post by MG&amp;TL on 2013-07-30
As far as I can tell (apologies to previous posters if I'm mistaken) everybody has given solutions involving changing the entire theme, which isn't actually what the OP asked for.

According to [http://bazaar.launchpad.net/~ubuntu-branches/ubuntu/precise/light-themes/precise/files/head:/](http://bazaar.launchpad.net/~ubuntu-branches/ubuntu/precise/light-themes/precise/files/head:/), you need to look in */usr/share/themes/Ambiance/unity/*, then replace any the data files with the replacements you desire. You'll need to do this as root, so use Alt-F2 to run this command:

```
gksu nautilus /usr/share/themes/Ambiance/unity/
```

which should produce a file manager window after prompting you for your password. Be *extremely careful* with what you do within this window: being root means that you can delete, edit or move *anything*, and the system will let you. Carefully replace the icons using this window.

Hope that helps, I can expand upon any of the points if required.

---

### Post by MagisterDixit on 2013-07-30
Thanks Mojo706! That was fast and worked great. Thanks also to Deadflowr. I have no doubt your way would have worked too. There is always more than one way to do things in Ubuntu. :D

---

### Post by deadflowr on 2013-07-30
^ If you wanted to mess around with a theme folder, such as Ambiance, then copying it into the home folder and muck about would be a better solution.
That way, if you break stuff, the original in the /usr/share/themes folder will remain untouched.
If the result works to satisfaction in the local users folder, then simply move or copy it into the system folder using sudo/gksudo.

---

### Post by MagisterDixit on 2013-07-30
I was OK with changing the theme of the windows only as long as it didn't make changes to what the rest of my computer looked like. It took me forever to get the desktop to look the way it does and changing the default folder color probably took me a lot longer to find than it should have. In my defense, the forums were down that whole time. Thanks again to everyone who replied.

---

### Post by MG&amp;TL on 2013-07-30
> **deadflowr said:**
> copying it into the home folder and muck about would be a better solution.


Yup, that it would be. I was thinking that you would be able to see the fruits of your labours immediately if you did it my way, but then I realised you need to restart X/compiz anyway, so it's pointless. Cheers!

---

### Post by mojo706 on 2013-07-31
glad I could be of assistance :D

---

