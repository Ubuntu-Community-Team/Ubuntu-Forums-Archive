---
title: "How To Get GNOME Desktop Working?"
date: 2012-07-09
forum: New to Ubuntu
---

### Post by DoctorVarney on 2012-07-09
Just up and running with Ubuntu.

I have downloaded the GNOME Desktop through the Ubuntu Software Centre ('centre spelled in English for once... wow!') and now I'm scratching my head, wondering where it is and what to do next...

Any help would be greatly appreciated.  Please note, I really am a beginner, so please feel free to dump an idiots guide on me, I won't be offended.  I'm still learning the ropes here!

---

### Post by Basher101 on 2012-07-09
It is not enough to install it through the software center, as you will be missing some packages. 

you will need to add a repository ```
sudo add-apt-repository ppa:gnome3-team/gnome3
sudo apt-get update
sudo apt-get install gnome-shell

```

i advise you also install the gnome-tweak tool ```
sudo apt-get install gnome-tweak-tool
```

this should get you a working Gnome 3 shell desktop environment

regards

p.s. if you want to install Themes, make sure they are for version 3.4 as older ones won't work correctly (or at all)

---

### Post by DoctorVarney on 2012-07-09
Thank you!

When copy and pasting those commands, can I lump them together or must I enter each line individually?

And thanks for the advice on themes.

---

### Post by deadflowr on 2012-07-09
I can't really help you beyond this little tidbit, but when it is installed simply log out and in the login screen in box the where your name and password is is a little ubuntu or cog icon in the top right corner, click it and choose whichever desktop you would like to try.

In an aside, if my fonts are coming up weird, I'm currently running a Kubuntu install, and I forgot that I messed around with the default font setting, and as such I really don't know what they might look like, or if they're rendering normally on this page. But they seem fine.

---

### Post by Basher101 on 2012-07-09
> **DoctorVarney said:**
> Thank you!

When copy and pasting those commands, can I lump them together or must I enter each line individually?

And thanks for the advice on themes.

you can lump them all right, they will be executed in succession

---

### Post by DoctorVarney on 2012-07-09
This is brilliant.  Thank you.

Is this what's known as 'Precise Pangolin'?  I'm using the GNOME Classic, which I found by logging out, as you suggested, deadflowr and it looks like a screen shot I'm looking at here:

[http://www.noobslab.com/2012/04/install-gnome-shell-34-and-extensions.html](http://www.noobslab.com/2012/04/install-gnome-shell-34-and-extensions.html)

---

### Post by DoctorVarney on 2012-07-09
If I want to install other themes (shell extensions?) is that pretty straightforward?  Can I install them from the Advanced Settings window?

---

### Post by tea for one on 2012-07-09
> **DoctorVarney said:**
> If I want to install other themes (shell extensions?) is that pretty straightforward?  Can I install them from the Advanced Settings window?

Good evening

If you wish to use Gnome 3.4 (instead of the Unity interface), there are four principal components of the Desktop where you can alter the appearance.

Gnome Shell
Gnome Theme
Icons
Extensions

Gnome Shell 3.4 styles, Gnome 3.4 themes and Gnome Icons are available from [http://gnome-look.org/](http://gnome-look.org/)

Gnome 3.4 extensions are available from [https://extensions.gnome.org/](https://extensions.gnome.org/)

You have to install and use the Gnome-Tweak-Tool (also known as "Advanced Settings") to choose the component that you wish to alter.

Just a note of caution, make sure that you read all the notes that come with the themes, icons and extensions because some work fine and others are less than perfect.

Kind regards

---

### Post by StardustLuna on 2012-07-16
Hi there, sorry about hijacking the thread, but I as well just downloaded Gnome and all of the little packages mentioned, yet when I go to the Advanced Settings, under Shell Extensions I see nothing. I know that when correctly working there's little on/off buttons? Anyway, I DO have the Shell Extension program installed. It says so in the Software centre. So what am I doing wrong?

---

