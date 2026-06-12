---
title: "css question about font families."
date: 2009-11-29
forum: Programming Talk
---

### Post by hockey97 on 2009-11-29
Hi, I would like to know how can a website create their own fonts? 

On top of that I downloaded the chiller font. The chiller font is commonly used in microsoft office suit mainly the power point presentations.

I want to use this font for my website. What do I need in order to use such a font with css.

Plus what if my clients do not have such a font installed on their computer? Could I prompt a window or do some automation to automatically install the font to their computer?

I would like to know how to handle custom fonts on a website? Like most likely the custom font won't be on the visitors computer. I would like to have some way to install it on their computer before loading the website.

Any ideas? Thank you for your time.

---

### Post by Reiger on 2009-11-29
CSS can request particular values for font-family rules. But whether or not it is effective depends on whether or not the (first) requested font is available. But you already knew *that*.

Hence the fairly common practice of generating images of particular pieces of text when the font is likely not locally available (e.g. this is what online font previews typically do on the fly). You can look into PHP + image manipulation for the general idea; there are plenty of tutorials on the subject for PHP.

Forcing people to install fonts is not something you should do unless you expect high volumes of text to require that font. It is bad practice, much like requesting that users switch to a different browser because the website author can't be arsed to write portable code (best viewed with rubbish).

Basically only sites such as online libraries requiring uncommon characters such as those found in Ancient Greek, Arabic, Sanskrit, Ogham, etc. etc. works should resort to the practice of (even) suggesting/requiring that you use a particular font -- because the works are cross referenced and indexed and loads of other nice search tricks are pulled off that make pre-rendering as images defeat the purpose of such an online library. Even those sites have typically various fallback options (e.g. unicode or transliterated).

---

### Post by nelfin on 2009-11-29
Reiger solution of custom generated images should work for everyone, but if you don't have any experience with PHP and just want to use a custom font, but don't believe the world will end if it doesn't display properly, use @font-face, which is compatiable with IE 4.0+ if the font is in .eot format (Microsoft have a utility for converting OpenType and TrueType fonts into EOT called WEFT, available from [http://www.microsoft.com/typography/web/embedding/weft3/download.aspx](http://www.microsoft.com/typography/web/embedding/weft3/download.aspx) ) and supported by FF 3.5, Opera 10 and Safari 3.1+.

It's syntax is described in detail here [http://www.w3.org/TR/css3-fonts/#the-font-face-rule](http://www.w3.org/TR/css3-fonts/#the-font-face-rule) but basically it's:
```
@font-face {
  font-face: MyCustomFontFamily;
  src: url('server/path/to/fonts/chiller.eof'); /* if you put this line first, then IE will pick up on it. No other browsers support .eot so they'll go onto the next line */
  src: local('Chiller'), url('server/path/to/fonts/chiller.ttf');
}
```

Then in your site's css you use:
```
#someId {
  font-family: MyCustomFontFamily;
}
```

Make sure the @font-face line comes before rules that use the declared family.

---

