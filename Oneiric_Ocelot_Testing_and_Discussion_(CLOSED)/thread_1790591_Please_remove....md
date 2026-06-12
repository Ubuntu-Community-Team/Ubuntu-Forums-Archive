---
title: "Please remove..."
date: 2011-06-25
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by rin67630 on 2011-06-25
At the risk of sounding a bit politically incorrect, i'd like to post a serious suggestion.
Does it make sense to include with the vanilla distribution so many very language specific fonts?
Most of us are using latin glyphs eventually with diacritics.
Having dozens of korean, hindi, azeri, arab and hebraic fonts in every distribution not only takes CD room, it cripples the font menu of many applications, with fonts that almost nobody can read.
Would'nt it make more sense to include a robust bench of unicode fonts and _only one_ language font for each language?
The installation program could include the specific ones upon request.

Laszlo

---

### Post by haqking on 2011-06-25
EDIT: removed as  i didnt see the it was concerning ocelot.

sorry ;-)

---

### Post by shuttleworthwannabe on 2011-06-25
> **rin67630 said:**
> At the risk of sounding a bit politically incorrect, i'd like to post a serious suggestion.
Does it make sense to include with the vanilla distribution so many very language specific fonts?
Most of us are using latin glyphs eventually with diacritics.
Having dozens of korean, hindi, azeri, arab and hebraic fonts in every distribution not only takes CD room, it cripples the font menu of many applications, with fonts that almost nobody can read.
Would'nt it make more sense to include a robust bench of unicode fonts and _only one_ language font for each language?
The installation program could include the specific ones upon request.

Laszlo

I support this idea.

---

### Post by cariboo on 2011-06-25
The idea would be fine, if the majority of users where English speakers, we have users from all over the world, does this mean that latin character sets should be removed for users in China, India or Russia?

---

### Post by shuttleworthwannabe on 2011-06-25
How about when we select the language at installation, other packs are not installed by default.

---

### Post by ranch hand on 2011-06-25
Or simply install "localepurge" available in your favorite package manager.

---

### Post by shafin on 2011-06-25
Maybe they can make the removal process post-install. That way if you chose english, all other languages will have only one font. If you chose Russian, all russian fonts will be available. This wont save CD space, but will make the font menus more sane.

---

### Post by seeker5528 on 2011-06-25
> **rin67630 said:**
> Does it make sense to include with the vanilla distribution so many very language specific fonts?
Most of us are using latin glyphs eventually with diacritics.

I don't see any single font that takes up *that* much room. As to which ones are actually necessary, that another question.

Even if I can't read something I want to see the characters that are supposed to be displayed. In particular I want all the track titles in my music collection to be displayed, preferably with no weird little boxes displayed where a character should be. 

> Would'nt it make more sense to include a robust bench of unicode fonts and _only one_ language font for each language?

That assumes that there are single font sets that are licensed in a way they could be included, that cover the needs for each language.

And you have to cover different middle eastern dialects that may or may not have different fonts. I'm pretty sure for Chinese you need multiple sets to cover the different language and character set variations. 

Looking in Synaptic at the size of some of the font packages I have installed, some are not that big at all. 

One of the annoyances I run into with track/album/artist names is they may display fine in gnome or KDE but have boxes where characters should be when viewing the file name at the command line. In some cases it's not displayed correctly in CLI or GUI so I have to play the track in Amarok, then go to Last FM to see what name was scrobbled, then sometimes if it is a UTF8 versus non-UTF8 issue, not so much with file names, but with tags, I can copy/paste the track/album/artist information into the relavant fields assuming that information could be interpreted from the file name or was included in the existing tag.

Later, Seeker

---

### Post by jerrylamos on 2011-06-25
> **cariboo907 said:**
> The idea would be fine, if the majority of users where English speakers, we have users from all over the world, does this mean that latin character sets should be removed for users in China, India or Russia?

I specified English on Install.  Why oh why does Ubuntu development ignore this and dump in lots of language packs during install??  I'm not conversant in any of the other languages although I recognize a few Spanish and German words. 

Moreover, on updates, gobs of time is spent updating these packages which I will never use.

O.K., put them on the CD & have them on the internet.  I just don't need them in my install.

Lightdm just crashed as usual, this on the 24 June daily build.  It did recover my partly entered post - after doing  the usual sudo service lightdm stop & start.

Jerry

---

### Post by sparker256 on 2011-06-25
> **jerrylamos said:**
> I specified English on Install.  Why oh why does Ubuntu development ignore this and dump in lots of language packs during install??  I'm not conversant in any of the other languages although I recognize a few Spanish and German words. 

Moreover, on updates, gobs of time is spent updating these packages which I will never use.

O.K., put them on the CD & have them on the internet.  I just don't need them in my install.

Lightdm just crashed as usual, this on the 24 June daily build.  It did recover my partly entered post - after doing  the usual sudo service lightdm stop & start.

Jerry

I have been using sudo restart lightdm with good success.

Bill

---

### Post by seeker5528 on 2011-06-25
> **jerrylamos said:**
> I specified English on Install.  Why oh why does Ubuntu development ignore this and dump in lots of language packs during install??  I'm not conversant in any of the other languages although I recognize a few Spanish and German words.

Are we talking language packs? I thought we were only talking about the fonts.

Later, Seeker

---

### Post by cariboo on 2011-06-25
As far as I'm concerned, ranch hand offered the best and easiest solution if the extra fonts bother you. We are all experienced users here, how many of use choose to stick with the default installation, if it takes a bit of extra work to make your install the way you want it, what's wrong with that?

If Ubuntu is to be a good out of the box experience for everyone, the way it's being done now is the best way to go, without adding the extra confusion of have having multiple isos, with different font packs for different areas of the world.

---

### Post by 73ckn797 on 2011-06-26
I do not see that having the other language packs installed really makes much difference in used disk space. I have a 14 GiB / partition and only 3.4 GiB are taken up with the OS. Seems that I could actually resize that partition without deleting any installed files.

---

### Post by Harry33 on 2011-06-26
> **73ckn797 said:**
> I do not see that having the other language packs installed really makes much difference in used disk space. I have a 14 GiB / partition and only 3.4 GiB are taken up with the OS. Seems that I could actually resize that partition without deleting any installed files.

Sure, not in HDD or SDD, but having them in the installation CD is a different story, though a minor one, concerning fonts.

---

### Post by 73ckn797 on 2011-06-26
> **Harry33 said:**
> Sure, not in HDD or SDD, but having them in the installation CD is a different story, though a minor one, concerning fonts.
This is true. I consider it a minor issue, in fact it has never really been an issue for myself.

---

### Post by kuvanito on 2011-06-26
since the topic is Please Remove I want to add something else hoping that some one from the dev team will see this.Please Remove Gwibber,Empathy,Evolution Mail,Take Screenshot,Games and any other irrelevant app,keep the ISO clean and small but Please Add the media codecs so that there is no need for an internet connection during first installation.Let people choose the apps the preffer from the Software Center.also do not integrate Icons and Menus,each to it's own.I want the my volume Icon by itself,Unity or Classic they are both fine with me.

---

### Post by shuttleworthwannabe on 2011-06-26
> **kuvanito said:**
> since the topic is Please Remove I want to add something else hoping that some one from the dev team will see this.Please Remove Gwibber,Empathy,Evolution Mail,Take Screenshot,Games and any other irrelevant app,keep the ISO clean and small but Please Add the media codecs so that there is no need for an internet connection during first installation.Let people choose the apps the preffer from the Software Center.also do not integrate Icons and Menus,each to it's own.I want the my volume Icon by itself,Unity or Classic they are both fine with me.

LinuxMint comes close (but it is a DVD).

---

### Post by arpanaut on 2011-06-26
> Please Add the media codecs so that there is no need for an internet connection during first installationBecause of legal restraints in some countries, they cannot be installed by default it must be user choice. (they can't be distributed on the iso)
You do have the option to not install on the initial install, they can be added later. (restricted extras)

About the other stuff, you might want to look into the minimal install and then build your system to your personal specs.
The goal of the default install is to provide an "all around" desktop experience.
Anything more or less is up to the user to configure themselves.

I find the default install to be a good balance between too much and too little.

---

### Post by seeker5528 on 2011-06-27
> **Harry33 said:**
> Sure, not in HDD or SDD, but having them in the installation CD is a different story, though a minor one, concerning fonts.

Seems pretty minor to me, it doesn't look to me like fonts or language packs take up all *that* much room. 15 ttf font packages, mostly in the 2 MB or less installed size.

I don't know how much compression they use for the live image, but for the fonts, looking at the installed versus download size, the download is half the size. If you figure 15 packages at 5 MB at 25% compression (15*5/1.25) I get about 60 MB. 5 MB is probably a little high for average installed size of the TTF font packages, don't know how much the fonts get compressed within the live image could be more than 25% could be less, and a few of those fonts are for English. 


Looking at the language packs it looks like the installed size is probably significantly more relative to the installed size of the fonts, but they are much more compressible so probably taking less room on the CD than the fonts.

This is looking at Natty beta 2 CD, but looking at the minifest for the Oneiric Alpha1 CD, it doesn't look like the font or language-pack packages have changed significantly.

Later, Seeker

---

### Post by rin67630 on 2011-06-28
> **cariboo907 said:**
> The idea would be fine, if the majority of users where English speakers, we have users from all over the world, does this mean that latin character sets should be removed for users in China, India or Russia?

So my suggestion was to include at the best a good unicode font that supports most of the glyphs used by 90% of the Earth population. 
At the worst only ONE of the very specific ones not included in the unicode one. So everybody would be able to read his native language.

The problem isn't that much space on the install disk, although...

The main problem is for newbies having a first contact with Libre Office on Ubuntu. They are frequently upset upon the huge number of perfectly unknown fonts, most of them being garbage for them. 

Not so far ago, Linux had not even half-way compatible fonts to the de-facto standards Arial and Timesroman, making imported documents look differently. 

One might dis-consider the Web standard fonts from M$, but they have got a *huge* unicode glyph range, supporting almost any language, with only a few major font families . It's another hurdle on new users not to find them, getting instead tons of perfectly unusable language specific unknown fonts.

I know: you can get then easily... You can!... but the new user? 
He has probably sadly left Ubuntu, before he could learn how to get rid of the useless and reclaim the useful fonts he needs to feel comfortable.

By the way: the hindi, korean and other users of "exotic" fonts are perfectly comfortable with getting the chance to download the fonts they need, no other OS gives them out of the box. 

Laszlo

---

### Post by rin67630 on 2011-06-28
> **seeker5528 said:**
> Seems pretty minor to me, it doesn't look to me like fonts or language packs take up all *that* much room. ...
... If you figure 15 packages at 5 MB at 25% compression (15*5/1.25) I get about 60 MB... 

60 MB being about 9% of the complete CD size!

But the point is more the first impression of a newbie with Libre Office on Ubuntu, getting tons of useless fonts and missing "their" Arial and Timesroman. 

Ubuntu made a huge improvement with 10.04 and it's extremely good Ubuntu font, giving the whole desktop a really professional consistent touch. 
It would now be time to give a brush up to the default font catalog.

Laszlo

---

### Post by cariboo on 2011-06-28
There are licensing issues with the **ms**corefonts package, they aren't free. That's why they are part of the restricted-extras metapackage.

---

### Post by rin67630 on 2011-06-29
> **cariboo907 said:**
> There are licensing issues with the **ms**corefonts package, they aren't free. That's why they are part of the restricted-extras metapackage.

The point is REMOVING all the superfluous fonts and putting them in the language settings. 
The Ubuntu font supports already an impressive set of national glyphs.
Renaming the liberation fonts to something like 
UrialLib, 
UimesLib and 
UourierLib 
would help newbies to find easily the free replacements.
;-)

Don't let the newbies find it out the hard way, they will be gone before finding it.
Or do you expect someone new to Ubuntu to find out easily which fonts are suited to replace his legacy ones in the jungle of 52 perfectly unknown fonts?

---

### Post by cariboo on 2011-06-29
How much of an issue is this really, I service computers for a living, and can count on one hand the number of Windows systems I've seen that don't use the default font. The same here since the Ubuntu font was released. If you check the [screenshot thread]("http://ubuntuforums.org/showthread.php?t=1772639") in the Cafe you'll see quite a few people that make quite an effort to customize their desktop, but still use the default Ubuntu font.

---

### Post by IanW on 2011-06-29
> **rin67630 said:**
> The point is REMOVING all the superfluous fonts and putting them in the language settings. 
The Ubuntu font supports already an impressive set of national glyphs.
Renaming the liberation fonts to something like 
UrialLib, 
UimesLib and 
UourierLib 
would help newbies to find easily the free replacements.
;-)

Don't let the newbies find it out the hard way, they will be gone before finding it.
Or do you expect someone new to Ubuntu to find out easily which fonts are suited to replace his legacy ones in the jungle of 52 perfectly unknown fonts?

Perhaps providing a suitable [font.alias](https://wiki.ubuntu.com/Fonts) file in the base install would be a more elegant solution to this?

---

### Post by seeker5528 on 2011-06-29
> **rin67630 said:**
> By the way: the hindi, korean and other users of "exotic" fonts are perfectly comfortable with getting the chance to download the fonts they need, no other OS gives them out of the box.

Judging by the input and keyboard layout options Vista gives when booting off the DVD, it appears Vista includes fonts for these.

If users of "exotic" fonts need those fonts, who says they are "comfortable with getting the chance to download the fonts they need".

I'm not seeing what the issue is in LibreOffice, you click on the dropdown box where the font is selected, see a listing by name, the name using the font to give you some idea what to expect from the font.

If there isn't a freely redistributable font included that could act as a replacement for the ones people would commonly use elsewhere or the freely available ones that are included don't show an alias when looking for a font that makes it clear what they would work as a replacement for that is a separate issue.

If I open up word pad on XP and go to the font dialog, the list of fonts doesn't really seem any saner than my Ubuntu installation in LibreOffice, and I installed additional fonts in my Ubuntu installation.

Later, Seeker

---

### Post by Reiger on 2011-06-29
If you have a single font which can satisfy 90% of the earth's population then currently this means that you have a font which is about as large as the fonts in the current default install combined.

The reason why the CD install image *has* to carry fonts for “exotic” languages (which is a bit an issue of perspective: 1bn Chinese, 1bn Indians, millions of Japanese and Koreans, millions of people who use an Arabic script and millions of Russians...) is that it does not know in advance which fonts will be absolutely required.

And there is a good reason for using dedicated fonts for these scripts rather than a big generic one. The generic one is typically poor, just like the renders of Western scripts in these fonts are typically a poor Arial/Helvetica clone. So you can't really cut these fonts on the Live image to save space without making the whole thing decidedly less usable.

For the default install it is also somewhat important that the OS comes with such fonts preloaded, because again it is impossible to know in advance in what environment the OS is used and these fonts play a key role for all sorts of software to function correctly. For instance web browsers are required to substitute fonts if a specific font cannot render characters in the HTML, and office apps do the same thing. Since space is generally not a concern here either, there's not much reason to opt for degraded functionality.

---

### Post by ranch hand on 2011-06-30
> **Reiger said:**
> If you have a single font which can satisfy 90% of the earth's population then currently this means that you have a font which is about as large as the fonts in the current default install combined.

The reason why the CD install image *has* to carry fonts for “exotic” languages (which is a bit an issue of perspective: 1bn Chinese, 1bn Indians, millions of Japanese and Koreans, millions of people who use an Arabic script and millions of Russians...) is that it does not know in advance which fonts will be absolutely required.

And there is a good reason for using dedicated fonts for these scripts rather than a big generic one. The generic one is typically poor, just like the renders of Western scripts in these fonts are typically a poor Arial/Helvetica clone. So you can't really cut these fonts on the Live image to save space without making the whole thing decidedly less usable.

For the default install it is also somewhat important that the OS comes with such fonts preloaded, because again it is impossible to know in advance in what environment the OS is used and these fonts play a key role for all sorts of software to function correctly. For instance web browsers are required to substitute fonts if a specific font cannot render characters in the HTML, and office apps do the same thing. Since space is generally not a concern here either, there's not much reason to opt for degraded functionality.
What an exibition of good sense.

I know that the thing to do is remove all the silly drivers that have nothing to do with my ati vid card.  Those buggers with exotic ibm and nvidia cards will be happy to download theirs.

---

### Post by kyleabaker on 2011-06-30
> **shuttleworthwannabe said:**
> How about when we select the language at installation, other packs are not installed by default.

I support this idea. With a minimal feature during installation for language pack selection, the user could select alternate or extra languages to install.

---

