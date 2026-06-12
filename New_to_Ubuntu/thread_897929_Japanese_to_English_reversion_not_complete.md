---
title: "Japanese to English reversion not complete"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by mikebravo on 2008-08-22
Well, my Japanese house guests have gone home now, but while there were here it was really nice to have Ubuntu operating in Japanese. My guests spent many hours sending email to their non-english reading friends and were quite happy to be able to keyboard in Japanese. My problem now, the reversion to English has been less than perfect in that when I go to menu item APPLICATIONS > ADD/REMOVE, the list below ALL is in Japanese, and anything I have not installed carries a Japanese name like Mergeant &#12487;&#12540;&#12479;&#12505;&#12540;&#12473;&#31649;&#29702; or Orca &#12473;&#12463;&#12522;&#12540;&#12531;&#12539;&#12522;&#12540;&#12480;&#12392;&#25313;&#22823;&#37857;. How do I root out the last vestiges of this language I cannot read?

---

### Post by Pro-reason on 2008-08-23
There are two issues here.  One is any software for using Japanese, which you may not need any more.  It can be safely left on your computer for next time.  If you really don't want it, simply delete it in Synaptic.  It's no big deal.

The second issue is locale.  You must have set your locale to Japan, so that system messages would be translated into Japanese.  The sensible way to do this would be to create a guest account and give it a Japanese locale, while leaving your own account alone.  I haven't done it myself, but it is surely possible.  I suspect you didn't do this. 

Try “gnome-language-selector” on the command line to change some system language support settings.

---

### Post by mikebravo on 2008-08-25
Dear Pro-reason, you said "There are two issues here. One is any software for using Japanese.." and "The second issue is locale."

On the first, possibly. I have added no Japanese software, however I have done automatic updates while logged on with Japanese language selected. I find it surprising that this would be a problem, one would think that Ubuntu could change between languages seamlessly.

On the second, my local has been USA and Central Time Zone since the day I installed Hardy months ago. The only thing I have done differently is log on selecting Japanese a couple of weeks ago. I said NO to the option to rename folders to that language.

As for your suggestion to run “gnome-language-selector” on the command line, I did, removed the check in the Japanese box and left the check in the English box and rebooted. No joy. APPLICATIONS -> ADD/REMOVE still shows Japanese. If there is anything else not in English, I have not found it yet.

---

### Post by Pro-reason on 2008-08-27
If the problem is that the language for certain programs is whatever language was selected when those programs were installed, then a possible solution is to reinstall them.

---

### Post by mikebravo on 2008-09-03
It is beyond my skill level to install what I suppose is a component of the operating system.
It is not really hurting anything so I shall just live with it.

---

### Post by Pro-reason on 2008-09-03
> **mikebravo said:**
> It is beyond my skill level to install what I suppose is a component of the operating system.
It is not really hurting anything so I shall just live with it.

The program in the screenshot is “Add/Remove Applications”, also known as “Install and Remove Applications”.  The relevant package for that program is *gnome-app-install*.

You can use Synaptic to reinstall that software package, or else you can just use the Terminal:

```

sudo apt-get install --reinstall  **gnome-app-install**

```

I don't know if that will reset it to English or not.  If it doesn't, then try the following:

```

sudo dpkg --purge --force-depends  **gnome-app-install**
sudo apt-get install  **gnome-app-install**

```

---

### Post by gandaran on 2008-09-04
mikebravo
         have you tried looking in synaptic package manager for the locale packages? language support and language pack, if theres a Japanese package installed remove it, it doesn't come installed by default!
there are also locale openoffice and locale mozilla packages, just remove the Japanese files.

---

