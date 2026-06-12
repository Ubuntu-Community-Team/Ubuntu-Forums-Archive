---
title: "Ubuntu Server 12.04 No Menu bar / icon after GUI install"
date: 2013-03-29
forum: New to Ubuntu
---

### Post by wkhan on 2013-03-29
I install ubuntu-desktop on my ubuntu server but for some reason it only logs on and displays the background.

Non of the component such as the menu bar / icons and based software is nowhere to be seen.

Any tips /solutions?

i'm new to Ubuntu so be easy :-)

I have attached a picture of the screen below.

---

### Post by wkhan on 2013-03-31
anyone?

---

### Post by steeldriver on 2013-03-31
how are you starting the GUI? (via lightdm?)

---

### Post by SuaSwe on 2013-03-31
Also, can you bring up the 'Run a command' box by pressing Alt+F2, or does nothing happen?

---

### Post by wkhan on 2013-03-31
How would I check?
I have access to the machine via SSH.

The GUI starts with the machine so it boots straight up after booting

---

### Post by wkhan on 2013-03-31
Alt+F2 does not work.

I can only bring up the file browser by pressing F3

---

### Post by SuaSwe on 2013-03-31
Hmm, you only have access to the machine via SSH, you say - why is this? Are you intending to use the server with a GUI or on command line only?

---

### Post by wkhan on 2013-03-31
> **SuaSwe said:**
> Hmm, you only have access to the machine via SSH, you say - why is this? Are you intending to use the server with a GUI or on command line only?

I wanted to set up a GUI as well as SSH. I had SSH, but wanted to set up the GUI

---

### Post by Nutster on 2013-03-31
I have had similar issues when using Gnome Classic on my laptop running Ubuntu 12.04.  Press **Ctrl**+**Alt**+**Tab** and you can see that the panels are present, just like the task switcher you get by pressing **Alt**+**Tab**; the panels are just hiding behind the desktop.  While holding **Ctrl**+**Alt**, press **Tab** until a panel is selected and release all the buttons.  Do that again for each panel, until you have selected them all and they should appear in the correct places on the desktop.  You may have to click on them to make the auto-hide feature work, if you have selected those features.

This procedure should also work for Xfce and maybe Unity or others.  Which graphics engine are you using?

---

### Post by SuaSwe on 2013-03-31
Ah, I see. :) The general consensus is that it's better to run a server with no GUI (see [here]("https://help.ubuntu.com/community/ServerGUI") for reasons). 

Can you open applications via Terminal, such as by typing 

```
nautilus &
```

?

---

### Post by wkhan on 2013-03-31
**Ctrl+[B]Alt+[B]Tab or **[/B][/B][B]Alt+[B]Tab

[/B][/B]do nothing, I have a integrated graphics in my HP microsever N36L.

---

### Post by wkhan on 2013-03-31
```
nautilus &
```

gives me the following output via SSH 

```
[1] 29024
```

Off couse I do not doubt that using command line for server is the ideal option.
I am currently investigation install of the GUI there may be time I may use it.

---

### Post by ally_uk on 2013-03-31
The GUI is not necessarily a bad thing alot of Linux Professor types will have a nerd fit at the mere mention of a graphical user interface :) my mentality is whatever gets the job done and  use whatever you are comfortable with besides this isn't the 80s I don't want to be greeted with a arcane terminal window when I use my computer :) never feel bad or inadequate for using a GUI and pay no attention to people who say that it is a waste of resources what kind of hardware are the running? Pentium 2s? Not everyone is going to be capable of coding or writing wonderful Bash scripts or memorising every switch for a command. I use Ubuntu Server with Gnome classic or LXDE and I also run Centos ( going for RHCSA). Currently reading Jangs book and he basically teaches you both ways of administration via Cli and the GUI so it's a win win situation :)

---

### Post by wkhan on 2013-04-01
> **ally_uk said:**
> The GUI is not necessarily a bad thing alot of Linux Professor types will have a nerd fit at the mere mention of a graphical user interface :) my mentality is whatever gets the job done and  use whatever you are comfortable with besides this isn't the 80s I don't want to be greeted with a arcane terminal window when I use my computer :) never feel bad or inadequate for using a GUI and pay no attention to people who say that it is a waste of resources what kind of hardware are the running? Pentium 2s? Not everyone is going to be capable of coding or writing wonderful Bash scripts or memorising every switch for a command. I use Ubuntu Server with Gnome classic or LXDE and I also run Centos ( going for RHCSA). Currently reading Jangs book and he basically teaches you both ways of administration via Cli and the GUI so it's a win win situation :)

Yes exactly sometime its good to have both even if you dont use the GUI much.

Any suggestions for a possible fix for me?

---

### Post by steeldriver on 2013-04-01
I'm still confused about exactly what the status of your system is:-

- when you boot the machine, does it bring up the lightdm login screen with your users listed for you to login? or does it go straight to the blank 'desktop'
- when you're at the physical 'desktop' (NOT ssh) can you get a terminal window by pressing Ctrl-Alt-t?

---

### Post by Warprunner on 2013-04-01
Something to consider. 
I put up a 12.04 Ubuntu server the other day. I had the same issue. What I did was right click and went to "Change Background" and then on the next window chose "All Settings" and finally chose "Displays". What had happened was that the resolution was off. Changed it to a lower resolution and it worked fine. 
While it may not help your issue. It's a a quick fix that alleviates the symptoms of something terribly wrong. Worth the check.
Best of Luck!

---

### Post by wkhan on 2013-04-01
> **steeldriver said:**
> I'm still confused about exactly what the status of your system is:-

- when you boot the machine, does it bring up the lightdm login screen with your users listed for you to login? or does it go straight to the blank 'desktop'
- when you're at the physical 'desktop' (NOT ssh) can you get a terminal window by pressing Ctrl-Alt-t?

It logs in automatically to the blank desktop so it does not show login screen but after a while of no use it asks for the password again.

No Ctrl-Alt-t does not work the only thing i can do is hit right click or hit F3 for the file navigation 

> **Warprunner said:**
> Something to consider. 
I put up a 12.04 Ubuntu server the other day. I had the same issue. What I did was right click and went to "Change Background" and then on the next window chose "All Settings" and finally chose "Displays". What had happened was that the resolution was off. Changed it to a lower resolution and it worked fine. 
While it may not help your issue. It's a a quick fix that alleviates the symptoms of something terribly wrong. Worth the check.
Best of Luck!

I was hoping the the problem to be solved with this but no luck.

---

### Post by steeldriver on 2013-04-01
It sounds like your session isn't starting properly - the way it's supposed to work in unity (I think) is that lightdm starts dbus and the gnome-session - AFAIK installing ubuntu-desktop should have pulled in and configured everything, but I guess there's no harm in trying

```
sudo dpkg-reconfigure lightdm
sudo dpkg-reconfigure unity-greeter
```

---

### Post by wkhan on 2013-04-01
> **steeldriver said:**
> It sounds like your session isn't starting properly - the way it's supposed to work in unity (I think) is that lightdm starts dbus and the gnome-session - AFAIK installing ubuntu-desktop should have pulled in and configured everything, but I guess there's no harm in trying

```
sudo dpkg-reconfigure lightdm
sudo dpkg-reconfigure unity-greeter
```


Both returned nothing, although i still restarted. Nothing has changed still the same

---

