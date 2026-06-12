---
title: "I could use a larger Cursor/Mouse Pointers"
date: 2012-01-28
forum: New to Ubuntu
---

### Post by anitaconway on 2012-01-28
Hi,
I've just installed the latest Ubuntu Software on my laptop.
I'm somewhat familiar with Ubuntu but this new has me stumped with regards to changing my mouse pointer size.  I am somewhat older and really need a larger pointer.  I've searched the forums and there are some good ideas there with regards to my question but nothing is seeming to work for me.  I'd appreciate any help.  Thanks

---

### Post by mcduck on 2012-01-28
Here's something you could try:

Open a terminal, and run the following command (replace the number with the size you want, 24 is the default), and then log out and back again:

```
gsettings set org.gnome.desktop.interface cursor-size 40
```

---

### Post by Dennis N on 2012-01-28
There is a good collection of mouse pointers/cursors at:

[http://gnome-look.org/](http://gnome-look.org/)

Use the list on the left, and look for **X11 Mouse Themes**

Several offer large cursor sizes. One example: Flatbed Cursors. After downloading a theme, extract the contents of the package to:

~/.icons

---

### Post by anitaconway on 2012-01-29
Thank you.  I'll give it a try.

---

### Post by hhh on 2012-01-29
[http://packages.ubuntu.com/search?keywords=chameleon-cursor-theme](http://packages.ubuntu.com/search?keywords=chameleon-cursor-theme)

chameleon-cursor-theme is a cursor theme in 5 colors and 3 sizes. To change your cursor theme, run...```
sudo update-alternatives --config x-cursor-theme
```... and pick the number of the theme you want, then logout and back in.

There is also the package big-cursor. I've never used it and don't know what it looks like, but I'd assume it provides, you know, a big cursor...
[http://packages.ubuntu.com/search?searchon=names&keywords=big-cursor](http://packages.ubuntu.com/search?searchon=names&keywords=big-cursor)

---

### Post by cmcanulty on 2012-01-29
This was a no brainer until 11.10 just pick a color and slide to size. I have tried all of the above and many other tries but nothing changes the size. I  don't know how to do the suggestion at [http://gnome-look.org/](http://gnome-look.org/)
I downloaded and extracted the files but then what.I can get a small black cursor in firefox but all other places it is white. A lot of people need this with poor eyesight.

---

### Post by hhh on 2012-01-29
> **cmcanulty said:**
> I have tried all of the above and many other tries but nothing changes the size.
In a terminal...```
sudo apt-get install chameleon-cursor-theme
```
... or...```
sudo apt-get install big-cursor
```
Then, in a terminal...```
sudo update-alternatives --config x-cursor-theme
```... and enter the number of the cursor theme you want. Reboot.

---

### Post by Dennis N on 2012-01-29
> **cmcanulty said:**
> This was a no brainer until 11.10 just pick a color and slide to size. I have tried all of the above and many other tries but nothing changes the size. I  don't know how to do the suggestion at [http://gnome-look.org/](http://gnome-look.org/)
I downloaded and extracted the files but then what.I can get a small black cursor in firefox but all other places it is white. A lot of people need this with poor eyesight.

I agree - I fired up my Unity test installation and I got the Flatbed Cursors to work partially - they functioned within Firefox and Libre Office at least, but as you say, in the file manager and elsewhere (such as the window controls) no go. White cursor only. I copied them into /usr/share/icons for good measure, and used Gnome Tweak tool (advanced settings) to select. Gnome Shell Desktop results were the same. Had thought they would work.

Additional comment: 

They (Flatbed Cursors) work fine in Lubuntu 11.04 and 11.10, and work everywhere. Extracted the cursor theme files just into ~/.icons and select them from Lubuntu's Appearance dialog. I like that distro and have switched.

---

### Post by Dennis N on 2012-01-29
> **hhh said:**
> In a terminal...```
sudo apt-get install chameleon-cursor-theme
```
... or...```
sudo apt-get install big-cursor
```
Then, in a terminal...```
sudo update-alternatives --config x-cursor-theme
```... and enter the number of the cursor theme you want. Reboot.

Yes it works! This sets it in Unity. I also had to set the same cursor choice in gnome tweak tool, as my previous theme selected there was still active in some windows. Now there is a universal cursor everywhere.

Why won't the downloaded X11 cursor themes work in Unity also?  

I wonder how many users would ever discover the commands needed to do this - it's too obscure. I hope such changes will be possible in a settings dialog in the future releases.

Thanks for the solution. Should help the original poster.

---

### Post by hhh on 2012-01-29
> **Dennis N said:**
> Why won't the downloaded X11 cursor themes work in Unity also?
They should if you put them in /usr/share/icons and logout/login before running update-alternatives. When you place them in ~/.icons they are per-user and not system wide.

---

### Post by Dennis N on 2012-01-29
> **hhh said:**
> They should if you put them in /usr/share/icons and logout/login before running update-alternatives. When you place them in ~/.icons they are per-user and not system wide.

I had them in /usr/share/icons as well, but the update-alternatives command did not detect them. There is apparently some incompatability.


I did notice that the chameleons have an cursor.theme file while the flatbeds I downloaded have an index.theme file. Renamed the index.theme to cursor.theme, logged out and back in, but still not detected by update-alternatives. Something else is missing or different.

---

### Post by mcduck on 2012-01-29
> **Dennis N said:**
> I had them in /usr/share/icons as well, but the update-alternatives command did not detect them. There is apparently some incompatability.


I did notice that the chameleons have an cursor.theme file while the flatbeds I downloaded have an index.theme file. Renamed the index.theme to cursor.theme, logged out and back in, but still not detected by update-alternatives. Something else is missing or different.

Update-alternatives only recognises things installed through package management, so it's not going to help you with manually installed themes.

Anyway, the downloaded themes should work just fine with Unity, you just need to log out and back again after selecting the theme to reload Unity and all the running programs.

---

### Post by cmcanulty on 2012-01-29
That seems to make the cursor black but it is still small. I have also changed it to size 40 in gconf and dconf to no effect.

---

### Post by Dennis N on 2012-01-29
> **mcduck said:**
> Update-alternatives only recognises things installed through package management, so it's not going to help you with manually installed themes.

Anyway, the downloaded themes should work just fine with Unity, you just need to log out and back again after selecting the theme to reload Unity and all the running programs.

Got it. The downloaded mouse themes are in /usr/share/icons, the log out and in has been done, but then how do we select a mouse theme outside of using the update-alternatives command, which doesn't see them?

---

### Post by mcduck on 2012-01-29
> **Dennis N said:**
> Got it. The downloaded mouse themes are in /usr/share/icons, the log out and in has been done, but then how do we select a mouse theme outside of using the update-alternatives command, which doesn't see them?

Using any of the programs that give you the options to change themes, like Gnome-Tweak-Tool or Ubuntu Tweak, should work fine. Just remember to log out and back again after changing the theme.

---

### Post by Dennis N on 2012-01-29
> **mcduck said:**
> Using any of the programs that give you the options to change themes, like Gnome-Tweak-Tool or Ubuntu Tweak, should work fine. Just remember to log out and back again after changing the theme.

We did try that previously. Using Gnome Tweak did allow us to use the downloaded theme, but only within certain windows, for example within Firefox, Libre Office and gedit. Once you move outside those windows, onto the desktop, or even the window border to use the window controls, the cursor reverts to the one selected by the update-alternatives that is was in use by Unity.

Just to be sure, I am now rechecking... 

Using Gnome-tweak to select one of the downloaded cursors... 

The new downloaded cursor works immediately within certain program windows as mentioned above. The Unity cursor is still in play everywhere else (window border, desktop, panels, launcher, etc)...
 
Logging out and back in does not change Unity's cursor to the downloaded one which was just selected in Gnome Tweak.

Repeated all this with Ubuntu Tweak instead of Gnome Tweak. No difference.

---

### Post by cmcanulty on 2012-01-29
I see options to change the windows theme but no additional themes show under cursor

---

### Post by Jay Car on 2012-01-29
Changing cursors used to be so easy, but in recent Ubuntu versions it has become frustrating.  However, I copied these instructions and the YouTube link (below) from a post on the forums, several months ago. I don't remember whose post, so I can't give proper credit (nor can I take any credit for it), but it has worked for me.  

Here it is:  in order to get the cursor to work with ALL applications do:

    ```
download other cursor themes
    open gnome tweak tool , change the cursor theme
    open terminal
    insert this command: sudo update-alternatives --config x-cursor-theme
    select the number corresponding to your choice
    log out
    log back in
```

you can see a video tutorial here [http://www.youtube.com/watch?v=2hu9JrdSXB8](http://www.youtube.com/watch?v=2hu9JrdSXB8)

---

### Post by cmcanulty on 2012-01-29
I did that as I said above and it gives choices of colors but not sizes. Synaptic says I have the big-cursor installed.
```

cmcanulty@Darcy25:~$ sudo update-alternatives --config x-cursor-theme
There are 7 choices for the alternative x-cursor-theme (providing /usr/share/icons/default/index.theme).

  Selection    Path                                     Priority   Status
------------------------------------------------------------
  0            /usr/share/icons/DMZ-White/cursor.theme   90        auto mode
  1            /etc/X11/cursors/core.theme               30        manual mode
  2            /etc/X11/cursors/handhelds.theme          20        manual mode
  3            /etc/X11/cursors/oxy-white.theme          50        manual mode
  4            /etc/X11/cursors/redglass.theme           20        manual mode
  5            /etc/X11/cursors/whiteglass.theme         20        manual mode
* 6            /usr/share/icons/DMZ-Black/cursor.theme   30        manual mode
  7            /usr/share/icons/DMZ-White/cursor.theme   90        manual mode

Press enter to keep the current choice[*], or type selection number: 

```

---

### Post by Dennis N on 2012-01-29
I have now found a solution that works! Succeeded in getting my downloaded Flatbed Cursor theme to work **everywhere** in Unity. Will post solution here in about an hour when I am back for anyone interested.


[COLOR="DarkSlateGray"]**See Post #22 for a solution**[/COLOR]

---

### Post by hhh on 2012-01-29
> **mcduck said:**
> Update-alternatives only recognises things installed through package management, so it's not going to help you with manually installed themes.
Ah, thanks for that info.

> **cmcanulty said:**
> I did that as I said above and it gives choices of colors but not sizes. Synaptic says I have the big-cursor installed.Did you try rebooting first so the cursor icon cache was updated? Did you try Chameleon instead of big-cursor?

---

### Post by Dennis N on 2012-01-29
You can use this method to manually install a downloaded third-party cursor theme in Ubuntu Unity 11.10:

Follow the steps here:

[http://grynays.deviantart.com/#/d4hyjjl](http://grynays.deviantart.com/#/d4hyjjl)

His cursor theme is a good one to try first. Download link is at right of page. (His download contains an archive within the archive. What you want to get is the Bold-Knob folder within the inner tar.gz archive.)

For a different downloaded cursor, repeat the steps, and just substitute the cursor name in place of 'Bold-Knob' in his command.

EDIT:

[I]His theme's folder contains a file named **cursor.theme** in addition to **index.theme**. It seems many other mouse themes (mostly older ones) don't. His terminal command won't work when replacing the cursor theme name with another if **cursor.theme** is missing from that new theme's folder, as it is a link target. Neither will the cursor.

If it is missing, create a 2-line file **cursor.theme** with a text editor:

[B][Icon Theme]
Inherits=Theme-Name[/B]

Replace Theme-Name with the actual cursor theme name (the theme folder name) and save the file as **cursor.theme** inside the appropriate cursor theme's folder. (requires root privileges).[/I]

---

### Post by cmcanulty on 2012-01-30
I am attaching a screenshot as I did as you said but still nothing new shows up in advanced settings. I have never been able to get any theme working. I am running 11.10 classic no effects.

---

### Post by Dennis N on 2012-01-30
> **cmcanulty said:**
> I am attaching a screenshot as I did as you said but still nothing new shows up in advanced settings. I have never been able to get any theme working. I am running 11.10 classic no effects.

The instructions outlined in post #22 assume you are using **Ubuntu 11.10 Unity Desktop**.

I haven't used the classic desktop and don't know how it compares in possibilities for customizing to old gnome 2, which as you know had a nice appearance settings dialog!

My guess (and that's all it is) is that advanced settings has little or no effect on classic desktop, since it is intended for gnome shell.

---

### Post by Bumpalot on 2012-01-30
I tried the above but it failed "Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory
How do I solve this?

---

### Post by mcduck on 2012-02-01
> **Bumpalot said:**
> I tried the above but it failed "Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory
How do I solve this?

Make sure you have only one package management tool running at a time (Software Center, Synaptic Package Manager, Update Manager or apt-get/aptitude).

---

### Post by spkemp on 2012-07-03
Works GREAT!

---

