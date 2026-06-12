---
title: "Changing theme in lightdm-gtk-greeter.conf"
date: 2015-05-04
forum: New to Ubuntu
---

### Post by tkullander on 2015-05-04
Hello everyone,

I would like to ask for assistance regarding themes in LightDM greeter. The question might be a bit silly...

As a standard, the theme is initially set to **lubuntu-default**

The line in **~/etc/lightdm/lightdm-gtk-greeter.conf** looks like this;
> theme-name=lubuntu-default

I would like to change the theme to "Elementary dark", but whatever I have tried does not register. I believe it's caused by the space.

I have tried the following combinations without success;
> theme-name=elementary dark
theme-name="elementary dark"
theme-name=elementary-dark

Could someone please advise on how to set the "elementary dark" theme in the greeter? If it makes any difference, I'm using Lubuntu 15.04 with the proprietary updated Nvidia drivers. 

Many thanks in advance.

---

### Post by Dennis N on 2015-05-04
Have you copied the theme folder into **/usr/share/themes**? I think it needs to be there to work, not **~/.themes**. It can be in both. 
Nothing wrong otherwise. I change mine in the same way.

---

### Post by tkullander on 2015-05-04
Yes, I am using the Elementary Dark theme normally, so it is installed properly.

However, I managed to actually solve it! It seems lightdm-gtk-greeter.conf is **case sensitive when specifying theme**. I just had to write it like this;
> theme-name=elementary Dark

However, I encountered a bug with this though, since only grey background was shown in the greeter, even though a wallpaper had been specified. I used the solution mentioned in the comment [here]("http://zaantar.eu/2014/10/guide-to-dark-gui-in-elementaryos-and-lubuntu/?lang=en"), by adding the following at the end of **~/usr/share/themes/elementary Dark/gtk-3.0/gtk-widgets.css**
> GtkImage,
GtkImage:insensitive,
GtkLabel,
GtkLabel:insensitive,
GtkBox,
GtkBox:insensitive,
GtkGrid,
GtkGrid:insensitive {
    background-color: transparent;
}

Thanks for the help!

---

### Post by Dennis N on 2015-05-04
I downloaded the theme to test it, and what I did was just change the folder name to **elementary-dark** and used that in theme-name=. Nothing else needed to be done for it to display properly.

---

### Post by tkullander on 2015-05-04
Yeah, I can see that it would work - I was just worried that changing the directory would cause some issues. Again, thanks for the help - much appreciated.

---

