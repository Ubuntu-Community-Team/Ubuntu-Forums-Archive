---
title: "[SOLVED] Open Office: It's Greek to me! (really!)"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by dinostabOMG on 2008-08-27
[IMG]http://i210.photobucket.com/albums/bb69/joentdothat/greek.png[/IMG]

How did this happen??? And how can I fix it?

It wasn't like this before, and the Open Office apps are the only ones that are doing this. Note it's only the menus and such, not the contents of documents.

Kallisti,
Dinostab

---

### Post by Crafty Kisses on 2008-08-27
Looks like a language problem.

**System->Administration->Language Support **

You should be able to set it there.

---

### Post by danmeetswood on 2008-08-27
Or you might just need to go to Tools>Options>Language_Settings>Language within the program. Unless your whole computer is in Greek!
(That's the third tab, then the first tab, then the fourth button down on the right for those of you who don't speak Greek.

---

### Post by freak42 on 2008-08-27
I think it is a **font problem**, if you look close (and compare to my screenshot) you can see that only the characters have been replaced, it is not actually greek, but english written in greek characters.

Now I am not sure how to fix this, you can try setting the ui to use a system font (if it is not already set), if this doesn't help, check your system default fonts for ui maybe one of them is a strange greek font and make sure you have the fonts installed that oo uses (however I cannot help further there).

And please forgive my use of *ahem* another OS right now.

---

### Post by dinostabOMG on 2008-08-27
> **freak42 said:**
> check your system default fonts for ui maybe one of them is a strange greek font 

That was it. Thanks! I wonder why this only manifested in Open Office. I guess it has to do with that checkbox, but still, that Greek-style font looks Latin in my menus and in other applications.

I guess a wider problem is that Ubuntu doesn't ship with many comfortable typefaces, I was scrounging for one that was comfortable to read and it looked like the Latin script of that Greek-style font was the best. 

But for now everything is in order. Thanks.

---

### Post by elmoosecapitan on 2008-08-27
The latest major Open Office release has a few bugs that are really just inexplicable. No idea why they are caused, but for some reason it will translate itself, and its pdf-outputs, into different languages. I ended up with a few pdfs in arabic.

A few months ago, a small update was made available that somehow, magically, made it all better. Just keep an eye out for Update manager and it should never happen again.

---

### Post by simosx on 2008-08-27
What happened here is that for some reason, OpenOffice.org could not find any suitable fonts, and resorted in using the Symbol font. This font may also come with OpenOffice.org.

The issue with this font is that it is not a Unicode font. It is a font that has the latin letters replaced with Greek letters (math symbols).

So the real issue is why OpenOffice did not figure out that it should use the default desktop settings for fonts (Sans). There is an OpenOffice.org - GNOME package that provides the link (and another one for OOo+KDE), so the bug is around there.

In your cases, are you using Ubuntu or Kubuntu?

---

### Post by dinostabOMG on 2008-08-28
> **simosx said:**
> What happened here is that for some reason, OpenOffice.org could not find any suitable fonts, and resorted in using the Symbol font. This font may also come with OpenOffice.org

Actually, I chose the Symbol font (Standard Symbols L) as the Application font myself because I found the Latin letters it displayed in the Appearance tab to be the most comfortable to read. OpenOffice is the only group of applications that reacted in that way, however. All the rest, including all text elements of GNOME, showed the Latin script.

Ubuntu, not Kubuntu - as in the thread prefix

---

### Post by simosx on 2008-08-29
> **dinostabOMG said:**
> Actually, I chose the Symbol font (Standard Symbols L) as the Application font myself because I found the Latin letters it displayed in the Appearance tab to be the most comfortable to read. OpenOffice is the only group of applications that reacted in that way, however. All the rest, including all text elements of GNOME, showed the Latin script.

Ubuntu, not Kubuntu - as in the thread prefix

Start Character Map and select the OpenSymbol font.
To figure out whether a shown character comes from OpenSymbol itself or is being substituted from another font, right click on each character.

If you do that for the typical Latin characters (ABCDEF...), you will notice that OpenSymbol does not have any characters for Latin, nor Greek. These characters come from the default font, being DejaVu Sans ("Sans" virtual font).

So, what's going on then? All proper GTK+ applications can do font substitution if a character is missing, so you get a good fallback if your selected font does not have all chars. It appears that in the case of OpenOffice.org, it does a fallback, but for some reason it fallbacks on some very basic OpenOffice (or is it X?) fonts. I do not know which font that is (looks like some default X font).

If you are interested in investigating, the issue appears to be with the "bridge" package openoffice.org-gnome, or with OpenOffice.org's support for GTK+.

---

### Post by dinostabOMG on 2008-08-29
Not sure I follow, but I did find Latin and Greek letters for both of those fonts. And nothing happened when I right-clicked.

---

### Post by simosx on 2008-08-29
> **dinostabOMG said:**
> Not sure I follow, but I did find Latin and Greek letters for both of those fonts. And nothing happened when I right-clicked.

I suppose you have the visual effects enabled. When these are enabled, nothing appears when you right-click on the characters. You need to disable the visual effects for this to work.

---

