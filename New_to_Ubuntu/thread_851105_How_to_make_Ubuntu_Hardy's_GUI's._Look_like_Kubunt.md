---
title: "How to make Ubuntu Hardy's GUI's. Look like Kubuntu GUI's"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by Mark.H on 2008-07-06
Hello all..

Can anyone suggest how I cam make Ubuntu 8.04 look a lot nicer foe example when I open synaptic package manager it looks quite dull.

I have given Kubuntu a shot in the past and seen that all the GUI's in all the various packages look better.

I still prefer Ubuntu, but I am trying to get the graphics to resemble kubuntu's.

I do not have a poerful enough graphics card to run compiz, so that is not an option for me...

Cheers for now

Mark...

---

### Post by nothingspecial on 2008-07-06
```
sudo apt-get install kubuntu-desktop
```

Then you can choose between ubuntu & kubuntu at login.Also check this site out for customizing your gnome desktop -

[http://www.gnome-look.org/](http://www.gnome-look.org/)

---

### Post by steveneddy on 2008-07-06
Install

**kubuntu-desktop**

then 

Ctrl+Alt+Backspace

and at the login screen, I think it is Actions, and choose KDE from the menu.

Or you could take off the top bar and install the Novell menu.

---

### Post by issih on 2008-07-06
Just to clarify, you say when you open synaptic package manager it looks dull.
Do you have a theme selected which generally you are happy with, but when you launch administrative applications (e.g. synptic) it isn't applied.

This can happen because the theme selection isn't being applied to applications running as root.

This can be fixed by running:

```
gksudo gnome-appearance-properties %F
```

which will allow you to set a theme for root.

Other than that it really is a case of just looking for a theme you like the look of...may I suggest you look at:

[http://www.gnome-look.org/](http://www.gnome-look.org/)

Hope that helps

---

### Post by steveneddy on 2008-07-06
> **Mark.H said:**
>  when I open synaptic package manager it looks quite dull.



I wonder what you would like Synaptic to look like?

EDIT

Maybe you need to theme you desktop or change the default colors a little to suit your needs.

[www.gnome-look.org/](www.gnome-look.org/)

Right click the Desktop, select Change Desktop Background, click the Theme tab, select the Customize button, then the Colors tab.

There you can change the default window colors to something of your liking.

Change some of the other options while you are there.

Then before you close the window, save the theme as you name, or something.

The manu I was talking abut earlier is called

Gnome Main Menu

installer via apt

```
sudo apt-get install gnome-main-menu
```

---

### Post by Mark.H on 2008-07-06
thanks for all your replyies.

I am not looking to install any extra Kubuntu packages, 

What i would like is when i open a packages GUI eg synaptic package manager I want it to look a lot better...
At the moment it looks like in running Win(%!!!

I have had it in the past where it looks alot better..
Like when I used to rub kubuntu. But I don't want to run Kubuntu as an O/S...

How can I do this??

Even when I change my theme it is still very dull gray (Thats the GUI's)

Any suggestions??

---

### Post by steveneddy on 2008-07-07
> **Mark.H said:**
> 

Even when I change my theme it is still [COLOR="Red"]**very dull gray**[/COLOR] (Thats the GUI's)

Any suggestions??

Right click the Desktop, select Change Desktop Background, click the Theme tab, select the Customize button, then the Colors tab.

[COLOR="Red"]There you can change the default window colors[/COLOR] to something of your liking.

[COLOR="Blue"]Change some of the other options while you are there[/COLOR].

Then before you close the window, [COLOR="Blue"]save the theme[/COLOR] as your name, or something clever.

---

### Post by issih on 2008-07-07
Please look at my previous reply....you are almost certainly having issues with the theme no being applied to programs running as root.

---

