---
title: "[SOLVED] What fonts to choose, or where to download new ones?"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by Paddy Landau on 2008-07-11
Having nearly completed my migration from Vista to Ubuntu, I'm finding that my use of fonts is different in OpenOffice.

On Windows, I usually used Times New Roman for serif fonts, Arial for sans-serif, and Courier New for monospacing. Some people send me documents with extra fonts such as Comic Sans MS. Those fonts don't seem to be installed on Ubuntu. As I need to print these for a magazine, this is somewhat disconcerting.


[LIST=1]
[*]Can you suggest good alternative fonts to use on Ubuntu? And...
[*]Can you tell me where (and how) to download extra fonts for Ubuntu, especially for use with OpenOffice?
[/LIST]

Thank you.

---

### Post by DezSP on 2008-07-11
The package msttcorefonts should have stuff like Arial in it for documents people send you:

sudo apt-get instal msttcorefonts

I never use Office so I'm not really one to suggest decent fonts to use. I believe Ubuntu offers a standard 'Monospace', 'Serif' and 'Sans-serif' font to be used based on your default preferences. Other fonts can also be found in the repository, as packages usually prefixed with ttf-, or you can google the forums to find a guide to install custom ones, it's fairly simple.

---

### Post by tibellus on 2008-07-11
I'm really curious how I could return to the default fonts and font sizes that came along with Ubuntu. I forgot which they were, and I've kinda switched a lot of fonts since I installed Ubuntu (now I'm using Lucida Mac and co. to make Ubuntu look more like Mac OS X).:lolflag:

---

### Post by coffeecat on 2008-07-11
> **DezSP said:**
> The package msttcorefonts should have stuff like Arial in it 

Yes. The package information for msttcorefonts:

> Installer for Microsoft TrueType core fonts
This package allows for easy installation of the Microsoft True Type
Core Fonts for the Web including:

  Andale Mono
  Arial Black
  Arial (Bold, Italic, Bold Italic)
  Comic Sans MS (Bold)
  Courier New (Bold, Italic, Bold Italic)
  Georgia (Bold, Italic, Bold Italic)
  Impact
  Times New Roman (Bold, Italic, Bold Italic)
  Trebuchet (Bold, Italic, Bold Italic)
  Verdana (Bold, Italic, Bold Italic)
  Webdings**Paddy Landau**, if you have access to the .ttf files for your favourite fonts there's an easy way of installing them on your system. Create a folder called '.fonts' (no quotes) in your home folder. Take care to include the leading stop. This makes it a hidden folder, but it can be made visible in the Nautilus file browser with ctrl-H or View > Show Hidden. Simply drag and drop your .ttf files into that folder. You may have to restart the desktop - I can't remember. Be aware though that this is slightly iffy copyright-wise with proprietary fonts. Personally I don't have problem with the likes of Times new Roman because I could install them quite legally with mstcorefonts anyway. I've just found it easier to make a bundle of fonts that I can quickly install. (I like to try out different distros.)

---

### Post by coffeecat on 2008-07-11
> **tibellus said:**
> I'm really curious how I could return to the default fonts and font sizes that came along with Ubuntu. I forgot which they were

Boot up from the live CD and check in System > Appearance > Fonts.

But I'm afraid you'll need a real high-tech device to save the details - a pencil and paper. :lol:

---

### Post by tibellus on 2008-07-11
And where could I get those? :))

---

### Post by coffeecat on 2008-07-11
> **tibellus said:**
> And where could I get those? :))

This reminds me of the story of the zero-gravity ballpoint pens. It's probably totally fictional but it's a good one, so I'll tell you. There are several versions of the story but, in essence, in the early days of space exploration NASA needed something for the astronauts to write with. The problem was that in zero gravity conventional ballpoints seized up or the ink wouldn't flow or whatever. So NASA embarked upon a major research project together with one of the major pen manufacturers. Several years passed and an enormous amount of money - something like $200,000 - was spent, but in the end they succeeded: a ballpoint that could be used in zero-gravity.

In the meantime the Russians used pencils.

---

### Post by Paddy Landau on 2008-07-11
> **DezSP said:**
> The package msttcorefonts...
Doh! Why didn't I look in Synaptic Package Manager? I see that it has a large number of fonts.

Thanks for the suggestion of msttcorefonts. It gave me exactly what I needed!

> **coffeecat said:**
> if you have access to the .ttf files ...
Thanks for that suggestion. It's something to remember for the future!

---

