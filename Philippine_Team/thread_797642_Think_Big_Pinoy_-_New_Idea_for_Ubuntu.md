---
title: "Think Big Pinoy - New Idea for Ubuntu"
date: 2008-05-17
forum: Philippine Team
---

### Post by ch1c0dj on 2008-05-17
New Idea for Ubuntu??? hmmmm...
Ideas for improvements and development of Ubuntu.

Post it here: [http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/)

Post nyo rin dito para may Tatak Pinoy agad.
Yung mga ayaw nyo sa current Ubuntu na gamit nyo sa lahat ng aspect, at mga gusto nyo na ma-include o ma-implement sa next release ng Ubuntu for the improvement of the operating system as a whole. :)

---

### Post by ch1c0dj on 2008-05-18
Ubuntu splash screen resembles Microsoft Windows OS splash screen specifically Windows XP. I don't like the bar line rolling back and fort. I hope this will be remove and change to something unique and Ubuntu style. Something like animated Ubuntu logo is good as replacement.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=67147&d=1209140299[/IMG]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=67148&d=1209140299[/IMG]

---

### Post by loell on 2008-05-18
the progress bar won't go away, I bet.

but animations during login screen is already on the works, its GDM faces..

---

### Post by ragadanga63 on 2008-05-19
Hmmm...sa internet cafe ko, ang laging reklamo ng mga clients ay walang thumbnail view sa dialogue boxes such as when u open/save a file.  Problema kasi nito pag magupload sila ng photos sa social networking accounts nila.  Kailangan pa nilang iview sa Nautilus, ilista ang filenames bago pa sila makapag upload using browser.  

Nasa sa Hardy na ito pero hilaw ang pagkaimplement.  Meron lang siyang parang thumbnail panel kung saan may thumbnail na nakadisplay pag i-select mo ang file.  You have to select the file before u can view the thumbnail.  Eh kung meron kang 100 ka pictures na pipilian, medyo matagalan ka talaga sa paghanap.  Sana sa list na lang makapagpili ka whether detailed, icon or thumbnail view.  Marami na rin akong customers na di na bumalik dahil dito.

This has been reported to Brainstorm many times.

---

### Post by loell on 2008-05-19
dialog thumbnail preview is an application to application basis function.

---

### Post by jeffimperial on 2008-05-19
> Hmmm...sa internet cafe ko, ang laging reklamo ng mga clients ay walang thumbnail view sa dialogue boxes such as when u open/save a file. Problema kasi nito pag magupload sila ng photos sa social networking accounts nila. Kailangan pa nilang iview sa Nautilus, ilista ang filenames bago pa sila makapag upload using browser.


Itong ito rin ang unang reklamo ng kapatid ko simula 'nong i-migrate ko Home PC and laptops ko. Pero sa The GIMP, meron thumbnail preview na lumalabas sa right side kapag i-select mo ang isang supported image file.

---

### Post by jeffimperial on 2008-05-19
> **loell said:**
> dialog thumbnail preview is an application to application basis function.
Daemon da 'to, Loell? Ibig kong sabihin, kapag gumamit/nag-install ako nito, may lalabas nang thumbnail previews sa i-select kong images?

---

### Post by loell on 2008-05-19
> **jeffimperial said:**
> Daemon da 'to, Loell? Ibig kong sabihin, kapag gumamit/nag-install ako nito, may lalabas nang thumbnail previews sa i-select kong images?

hindi eh, talagang hard coded yan each program, so walang magagawa ang ubuntu developers dyan, kahit ang gnome core developers wala din. nasa project developers yan nang mga individual applications.

---

### Post by jeffimperial on 2008-05-19
'Yun din iniisip ko e. Oh well.. Sana addressed na 'to sa Intrepid no? Makapag bug-wishlist nga. Hehe

---

### Post by Jucato on 2008-05-19
Actually, for Open/Save dialogs, it's not on a "per-application" basis. Most apps will use the file dialogs that a toolkit, such at GTK+ or Qt, provides, or one that a desktop environment, like GNOME, KDE, or Xfce, provides. So kadalasan dun nagkukulang. 

I haven't seen the latest GNOME file dialog lately, so I can't comment on that. But in KDE, there's a preview sidebar when you click (or just hover, in KDE 4) on a file. Walang nga lang "inline" previews, like view as icon previews.

So actually may magagawa ang mga GNOME/GTK+/KDE/Qt developers about it by putting the feature in their standard dialog boxes. I can only guess why they don't (performance reasons maybe? or technical reasons?).

---

### Post by loell on 2008-05-19
the gtk file chooser is still the same since 2.4  ,  back then the preview method was already offered to gtk based developers, so it is left out to the application developers on whether its appropriate to implement a preview or not, so in a sense it may be an application to application basis. 

True, they could have add it by default in their file choosers, but since adding it now in the 2.6 gtk series might make some application break, or make the functionality redundant if the application had already made use of  the preview method. so maybe this is the reason why didn't include it in their standard file chooser dialog box, there may also be the issue of portability?

its good though that Qt made it right.

---

### Post by jeffimperial on 2008-05-19
As it turns out, GNOME devs have marked wishlist bugs of these nature as "Wont Fix" primarily because it would take too much on their part when this should be the responsibility of individual apps. Plus, it'd take big chunks of your processing & RAM capacities for something that can be forgone.

---

### Post by Jucato on 2008-05-21
That sounds kinda silly to me... probably a case of difference between GNOME and KDE philosophies. For one, what makes a Desktop Environment a Desktop Environment is the integration. A common set of widgets, a common appearance, a common HIG (Human Interface Guidelines). A file dialog is one of the most common (complex) widget any application has. To leave that up to the individual apps that are part of a DE sounds to me like defeating the purpose.

As for performance and RAM, it doesn't have to be enabled by default right? Just like Preview modes in file managers aren't enabled by default. And they don't have to regenerate thumbnails/previews from scratch since those are cached (in ~/.thumbnails), **if** previews have been turned on before. Sure, even with all that it will be a bit slower, but I'm sure the user is willing to trade that off for his needs.

Hehehe sorry, umagang umaga rant mode na agad. :D

---

### Post by loell on 2008-05-21
:biggrin: medyo tanghali na, kaya ok na ok ang mag rant :biggrin:

---

### Post by ache109 on 2008-06-21
ako me idea,

why not make an ubuntu pinoy edition? alam ko mejo mahrap un, pero my point is i-add nyo sa orig ubuntu ung mga problems or mga interface na makakapag improve sa kanya....

**suggestion lang tutal mdami namang softwaredevelopers d2 sa forum na ito.

---

### Post by jsgotangco on 2008-06-21
That's fine and dandy and I'm sure someone can actually do that (it's very easy to create your own custom distros). But the end question is how do you sustain it, in terms of updates and supporting the said product.

---

### Post by Nessa on 2008-06-21
Open source naman eh. Importante mag-contribute yung may alam. Ang maganda sa mundong ito, may choice. Kung hindi pa ma-reach ng isang DE or app ang needs mo, pwede ka munang gumamit ng iba.

Tingin ko medyo marami nang Linux editions. Mas ok kung tulong-tulong nalang sa flavor na gamit mo ngayon rather than develop a new one. Proficient naman ang karamihan sa atin sa english. Minsan nga nawawala ako sa Google na tagalog at hinahanap ko yung english version. :p

---

