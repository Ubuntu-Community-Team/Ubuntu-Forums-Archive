---
title: "Can I modify the font system and add the new characters to it, create the pack (...)?"
date: 2014-03-18
forum: Programming Talk
---

### Post by Gustavo_Benedito_d on 2014-03-18
Hello,

I'm newer to Ubuntu forum. 

You can call me Gus. 

I think in planning a new programmation for developing the new characters to the font system of Ubuntu and Linux, as they're open source, I can modify, add and save it as a package or repository for distributing to the users for updating Linux's typography system.

I'm not speaking of creating the new glyphs, new font and putting the new letters on the existing characters. 

But the new characters, which are different of glyphs which are letter's bodies for drawing. Characters are letters which the OSes support. Letters are drawn and written bodies. 

For example, A, B, C, &#12354;, &#12360;, &#12362;, &#12358;, &#945;, &#946;, &#954;, &#960;, &#1072;, &#1074;, &#1095;, &#1103;, &#1513;, &#1500;, &#1506;, &#1488;, are characters which are existing and supported in the most of the OSes.

Before the euro being released, there wasn't the symbol € in the font system. After it, the OSes have updated the font system. 

I don't want to put the Cyrillic letters on the Latin or Japanese characters, or Latin or Japanese on the Cyrillic characters. 

The movies anthropologists, linguists and designers created the new languages as Na'Vi, Tengwar, Klingon and old and new Kryptonian letters and also the new grammar and their rules.

In the current font system, there aren't the new languages characters, Tengwar characters, Klingon characters, Kryptonian characters.

Then I want to create the new characters for new letters that I'm going to draw on the glyphs. I don't want to put new Tengwar, Kryptonian or any fictional or not-recognised languages letters on the existing Latin, Cyrillic, Arabic and Japanese characters for expanding and completing the fonts. 

Not only that, I want to develop new keyboards, languages packs for orthography and grammar, and languages translation packs for the OS and the apps too. If all that is possible, I would like to share and distribute as repositories to the users interested for updating Linux, the characters and the fonts. 

Is it possible? How?

---

### Post by ofnuts on 2014-03-18
If it's for fun you can check[ what has been done for Klingon already.]("http://en.wikipedia.org/wiki/Klingon_alphabets")

Otherwise, if you want to add new characters, they have to be assigned new codes, so you'll have to talk to the Unicode consortium first. And once that is done, you may have to wait a bit before they are generally usable, in most programming languages there is a string support library somewhere that answers questions about character codes (uppercase character? lowercase character? punctuation character? and, more importantly: valid code?) and until these libraries are updated your additional characters won't really be usable.

---

### Post by ssam on 2014-03-18
You can put them in the private use area of Unicode [https://en.wikipedia.org/wiki/Private_Use_Areas](https://en.wikipedia.org/wiki/Private_Use_Areas)

---

### Post by Gustavo_Benedito_d on 2014-03-18
> **ofnuts said:**
> If it's for fun you can check[ what has been done for Klingon already.]("http://en.wikipedia.org/wiki/Klingon_alphabets")

Otherwise, if you want to add new characters, they have to be assigned new codes, so you'll have to talk to the Unicode consortium first. And once that is done, you may have to wait a bit before they are generally usable, in most programming languages there is a string support library somewhere that answers questions about character codes (uppercase character? lowercase character? punctuation character? and, more importantly: valid code?) and until these libraries are updated your additional characters won't really be usable.

Ah, I didn't know Klingon characters have already been added by Unicode Consortium, and as @ssam suggested me, I have seen that the Tengwar and other fictional characters have already been included and added. But the Kryptonian isn't added.

We are planning to add the old (Smallville) and new (Man of Steel) Kryptonian characters for the font.
The old and new Kryptonian languages don't have uppercase or lowercase letters. They're unicase letters. They have punctuation characters, but they're not like the Latin-like, they're typically Kryptonian. The new Kryptonian's space isn't blank for separating, it's a "space letter". 

As I'll talk to Unicode consortium, are they paid or free? For Linux, is it free? I can't update the font system in Apple and Microsoft! because they won't allow. But I'll think Unicode Consortium will ask for a license to them. 

@ssam, I'll check the private use of characters. Does Fontforge show them?

---

