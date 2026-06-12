---
title: "Configuring Unity and average users"
date: 2013-03-06
forum: Recurring Discussions
---

### Post by belnac on 2013-03-06
Does anybody know why the teams behind the Unity and Gnome 3 **Desktop Environments** chose not to include a program for easily configuring such trivial aspects of the OS as font size and instead require fiddling with the gnome configuration or an external tool to be installed (such as the gnome tweak tool)? Why was this design decision made? Incidentally, given the above, how does Canonical expect Ubuntu to be adopted by the average user? 

I am not an average user but I would think a desktop environment that aims to be easy to use and adopted by the masses - like Unity - would include a comprehensive configuration tool as an intricate part of it.

I am myself a user of XFCE (since 4.6) and never used Gnome Shell or Unity but I did try the latter a couple of weeks ago out of curiosity. I suppose I just couldn't believe that a company (Canonical) that aims to bring a FOSS OS to the masses as well as now targeting the tablet and smartphone market didn't even think to allow its DE to be easily configurable. Frankly, I find it beyond belief.

Technical users can make informed decisions and choose the DE (and even distro) that suits them best but the same can't be said of the average user who wants something that just works and doesn't introduce radically new paradigms or feels crippled.

---

### Post by coffeecat on 2013-03-06
Not a technical support question.

*Thread moved to **Recurring Discussions**.*

---

### Post by 3rdalbum on 2013-03-06
I wouldn't consider "changing the font size" to be something that many users will want or need to do. For those who want to, there's Gnome Tweak Tool or you can edit Dconf keys.

In the past, any superfluous customisation features were buried in Dconf or Gconf, but now these kinds of things are exposed in Gnome Tweak Tool. It just so happens that fonts had a GUI in Gnome 2, but most people used it only for changing the subpixel font rendering to look more like a Mac for use with their Macintosh themes.

One of the principles behind Gnome that has also made its way to Ubuntu is that you DON'T need a "comprehensive settings tool", that you just start with sensible defaults. Anything that's out of the ordinary for people to change can be done using Gconf, the terminal, or third-party tweaking tools. You actually make things a lot less confusing and a lot less breakable* for the ordinary user.

Gnome's smaller and sparser configuration panels actually make me feel like I have more control over my computer, instead of "Oh my god what on earth does this option mean and will it break things if I try it". KDE's a lot of fun to play with, but it's really got configuration overload. I'm not autistic or anything, either, but KDE's wealth of settings, or Windows XP's, makes me feel less comfortable than a simple settings dialog with a few essential settings.

*Less breakable means "Less like Compizconfig Settings Manager and its ability to hose your desktop if you choose the wrong options".

---

### Post by Paqman on 2013-03-07
> **3rdalbum said:**
> I wouldn't consider "changing the font size" to be something that many users will want or need to do.

I'm not so sure about that. It's probably not something a lot of young software developers with good eyesight do, but if you want to apply Ubuntu to the population at large a lot of people will need a larger than average font. It's a pretty basic accessibility feature. You should be able to bump the font a little without going whole hog into specialist VI themes and screen readers.

---

### Post by vasa1 on 2013-03-07
> **3rdalbum said:**
> I wouldn't consider "changing the font size" to be something that many users will want or need to do. ...
Interesting :)

---

