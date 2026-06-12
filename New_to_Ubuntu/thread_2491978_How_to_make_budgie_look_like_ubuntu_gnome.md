---
title: "How to make budgie look like ubuntu gnome ?"
date: 2023-10-26
forum: New to Ubuntu
---

### Post by misternemo on 2023-10-26
Hi guys

I was wondering how can i make budgie look exactly like ubuntu gnome ?

Is it even possible to look exactly like it if yes what are the steps to do so ?


Thanks in advance

Kind regards

N

---

### Post by TheFu on 2023-10-27
Just install the gnome-desktop and run gnome.  Of course, you'll need to expect the bloat that is gnome to come with it.

---

### Post by MAFoElffen on 2023-10-27
Yes, gnome-desktop would install all the included Gnome desktop application suite.

Or just install 'gnome-session' and tweak it to put the dock on the left... I do that on some things... But expect that other things might have to be installed with it to make it work. 

Sometimes just adding "that piece" on something that is not Gnome based will end up with some dependency issues for other things that usually are included in the whole desktop package. I have tested doing that on something that was originally installed as Kubuntu Desktop, and it has issues doing that, if done alone.  For example, Launchpad swears to me, that they are 100% sure that it requires that you have to start gnome-sessions with GDM3, but I have shown them that it starts and runs fine with LightDM... LOL

I have not tested that on Budgie, so I cannot tell you what else might have to be included.

---

### Post by misternemo on 2023-10-27
> **TheFu said:**
> Just install the gnome-desktop and run gnome.  Of course, you'll need to expect the bloat that is gnome to come with it.

I really like the look of ubuntu gnome i just don't want that whole bloated gnome de to come with it hence the question...

---

### Post by misternemo on 2023-10-27
> **MAFoElffen said:**
> Yes, gnome-desktop would install all the included Gnome desktop application suite.

Or just install 'gnome-session' and tweak it to put the dock on the left... I do that on some things... But expect that other things might have to be installed with it to make it work. 

Sometimes just adding "that piece" on something that is not Gnome based will end up with some dependency issues for other things that usually are included in the whole desktop package. I have tested doing that on something that was originally installed as Kubuntu Desktop, and it has issues doing that, if done alone.  For example, Launchpad swears to me, that they are 100% sure that it requires that you have to start gnome-sessions with GDM3, but I have shown them that it starts and runs fine with LightDM... LOL

I have not tested that on Budgie, so I cannot tell you what else might have to be included.

No if i understood u correctly i mean like customize the budgie desktop to look like ubuntu gnome i dont want to install gnome to big and bloated.

or am i mis understanding you? sorry i am new at this.

---

### Post by Dennis N on 2023-10-27
> **misternemo said:**
> I dont want to install gnome to big and bloated.
Ubuntu Dock on the left side of Ubuntu's desktop only functions in Gnome. So you have to substitute. Plank is a dock you could use instead. I think it will work with most Linux systems. I use it myself with Ubuntu with a custom Plank theme to make it look great. If you go with that, you need to look into Plank themes as the default is rather plain.

---

### Post by misternemo on 2023-10-28
> **Dennis N said:**
> Ubuntu Dock on the left side of Ubuntu's desktop only functions in Gnome. So you have to substitute. Plank is a dock you could use instead. I think it will work with most Linux systems. I use it myself with Ubuntu with a custom Plank theme to make it look great. If you go with that, you need to look into Plank themes as the default is rather plain.



Thank you for your reply,  i think this is it?


I have been looking online for abit but it is mostly that mimics mac os for some reason i cant seem to find one that does ubuntu ? 

do you happen to know or heard of one that can looks exactly like ubuntu ?

---

### Post by MAFoElffen on 2023-10-28
> **Dennis N said:**
> Ubuntu Dock on the left side of Ubuntu's desktop only functions in Gnome. So you have to substitute. [COLOR=#ff0000]Plank is a dock you could use instead. [/COLOR]I think it will work with most Linux systems. I use it myself with Ubuntu with a custom Plank theme to make it look great. If you go with that, you need to look into Plank themes as the default is rather plain.
Plank is already installed as a default package in Budgie... And the Budgie DE is built on top of the Gnome Stack... If you search on plank, > Go to Plank Preferences > On the first tab, then on it's position, choose left... (See attachment) If you hover over the Plank Dock, then <Cntrl><Right-click> the Dock, that is the shortcut to open the Plank Dock Preferences. (Alternate route)

So I think from what you suggested, he would only have to install a custom plank theme from here: 
[https://www.gnome-look.org/browse?cat=273](https://www.gnome-look.org/browse?cat=273)
[https://github.com/andreystarkov/humanization](https://github.com/andreystarkov/humanization)

From what you said you wanted, and didn't want, that would be the minimal install change. There are also Plank Docklets available...

Package 'gnome-session' is just the Gnome Desktop DE "piece" of the Gnome Desktop. I tested this on Budgie this morning and it works fine. Since the Budgie desktop is based on the Gnome Stack, there are very little that it installs with it:
```

The following NEW packages will be installed:
  gdm3 gir1.2-accountsservice-1.0 gir1.2-adw-1 gir1.2-gck-1 gir1.2-gcr-3
  gir1.2-gdm-1.0 gir1.2-gnomebluetooth-3.0 gir1.2-graphene-1.0 gir1.2-gtk-4.0
  gir1.2-mutter-10 gir1.2-nm-1.0 gir1.2-nma-1.0 gir1.2-rsvg-2.0
  gir1.2-upowerglib-1.0 gnome-bluetooth-3-common gnome-session gnome-shell
  gnome-shell-common gstreamer1.0-pipewire libadwaita-1-0 libgdm1
  libgnome-autoar-0-0 libgnome-bluetooth-3.0-13 libxcb-icccm4 libxcb-image0
  libxcb-keysyms1 libxcb-render-util0 libxcb-xv0 switcheroo-control
  ubuntu-wallpapers ubuntu-wallpapers-jammy xserver-xephyr xwayland
  yaru-theme-gnome-shell

```
Then just change the Dock to the left.

---

### Post by Dennis N on 2023-10-28
If you install a plank theme, you should know each theme can be customized further:

Azeny is a theme.  
In the theme folder, in the location shown here, **dock.theme** contains many user defined settings:
```
dmn@Sydney:~/.local/share/plank/themes/Azeny$ ls
dock.theme

```
Its Contents (as customized):
```
dmn@Sydney:~/.local/share/plank/themes/Azeny$ cat dock.theme
[PlankTheme]
TopRoundness=4
BottomRoundness=0
LineWidth=0
OuterStrokeColor=42;;50;;56;;164
FillStartColor=42;;50;;56;;255
FillEndColor=105;;111;;122;;255
InnerStrokeColor=42;;50;;56;;0

[PlankDockTheme]
HorizPadding=3
TopPadding=2
BottomPadding=1.6

ItemPadding=4
IndicatorSize=8
IconShadowSize=1

UrgentBounceHeight=1.6
LaunchBounceHeight=0.625
FadeOpacity=1
ClickTime=300
UrgentBounceTime=600
LaunchBounceTime=600
ActiveTime=300
SlideTime=300
FadeTime=250
HideTime=250
GlowSize=30
GlowTime=10000
GlowPulseTime=2000
UrgentHueShift=150
ItemMoveTime=450
CascadeHide=true
BadgeColor=0;;0;;0;;0

```

Have fun customizing!

---

### Post by MAFoElffen on 2023-10-28
Dang you Dennis N! Now you have my temped to play with that myself. (LOL!)

---

### Post by misternemo on 2023-10-31
hmmm i am not sure i understand might have to put a pin in this for now...

Edit: thanks for the help guys.

---

