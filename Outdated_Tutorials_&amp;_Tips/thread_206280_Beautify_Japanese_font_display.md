---
title: "Beautify Japanese font display"
date: 2006-06-29
forum: Outdated Tutorials &amp; Tips
---

### Post by Endukugga on 2006-06-29
I have seen so far a few threads concerning improving support/display for Japanese fonts in Dapper. Most of them offer incomplete solutions, so after having a look at them and messing **a lot** with fontconfig, here's my take. I hope you find it useful and you won't need anything else.

**A bit of background** (you can skip this but I think it's better to read it):
In Dapper we have some families of fonts installed by default which offer rendering of Japanese characters. The most popular of them are Freefont (ttf-freefont), Kochi Subst (ttf-kochi-gothic and ttf-kochi-mincho) and Sazanami (ttf-sazanami-gothic and ttf-sazanami-mincho). *[1]*
Freefont only offers, to my knowledge, katakana and hiragana, while the other two offer also kanji and other glyphs and characters that you can usually find in Japanese fontsets (e.g. circled numbers). So it would seem a good idea to use one of these two fonts for general Japanese display. Of those two Sazanami is better, in my opinion.

*[1]* Gothic and Mincho are the equivalent of Western sans-serif and serif fonts, respectively.


**Licensing problems**:
The problem many people have with those two fontsets is that they are quite worse than the Japanese fonts you can find in Windows (MSGothic and MSMincho) or Mac OS X (Hiragino family and Osaka font). A good alternative, which is quite popular among Japanese people and which is indeed included in the Japanese localised distribution of Ubuntu is the IPA font family. However, IPA fonts have some licence problems and they are not completely free. For a comparison among some Japanese fonts you can have a look [here]("http://www.geocities.jp/ep3797/japanese_fonts.html"). *[2]* My feeling is that it's OK to download them for personal use but there could be problems if they are to be included in the distribution by default. From what I've read the situation isn't still clear. In any case, I'm going to suppose that we'll use the IPA fonts through this HOWTO. If you have a legal copy of Windows with the MSMincho and MSGothic fonts you **may** use those. The legal issues with fonts aren't very clear, and that's one of the reasons why Apple includes their Apple logo in their system fonts. My recommendation are the IPA fonts because they look the less problematic of all.

*[2]* The IPAMona font is a variation of the IPA font with the width of some characters fixed to be the same than their Microsoft counterparts.


**The HOWTO:**
NOTE: In the following I assume you know how to add repositories and manage packages with Synaptic and have some basic knowledge with the Terminal. If that's not the case look for that information elsewhere on the Ubuntu forums, Ubuntu Documentation Project, etc. It should be fairly easy to find.

1. Getting the fonts:
The first thing we need are the IPA fonts. You can obtain them through the Japanese repositories of Ubuntu or downloading the files through the link above. We'll cover both methods here. The second one might be necessary if you don't have administrator privileges.

1.1. Using Synaptic Package Manager:
Add the following repository:
```
deb http://archive.ubuntulinux.jp/ubuntu-ja dapper/
```
Update your package list.
Install the ipafont and ipamonafont packages. *[3]*

*[3]* Notice that the added repository may update other Japanese related packages. If you want to have a "pure" Ubuntu Dapper 6.06 you can choose the following method.

1.2. Manually downloading the files:
Download the files from [this site]("http://www.geocities.jp/ep3797/japanese_fonts.html") and copy them to your local fonts directory:
~/.fonts/

2. The following step will set our prefered Japanese fonts. Go to the Text Editor and paste the following text and save the file as .font.config (notice the first dot) in your home folder:
```
<?xml version="1.0"?>
<fontconfig>
	<alias>
		<family>serif</family>
		<prefer>
			<family>DejaVu Serif</family>
			<family>Bitstream Vera Serif</family>
			<family>Times New Roman</family>
			<family>Thorndale AMT</family>
			<family>Luxi Serif</family>
			<family>Nimbus Roman No9 L</family>
			<family>Times</family>
			<family>Frank Ruehl</family>
			<family>MgOpen Canonica</family>
			<family>AR PL SungtiL GB</family>
			<family>AR PL Mingti2L Big5</family>
			<family>IPAPMincho</family>
			<family>&#65325;&#65331; &#26126;&#26397;</family>
			<family>Sazanami Mincho</family>
			<family>Kochi Mincho</family>
			<family>FreeSerif</family>
			<family>Baekmuk Batang</family>
		</prefer>
	</alias>
	<alias>
		<family>sans-serif</family>
		<prefer>
			<family>DejaVu Sans</family>
			<family>Bitstream Vera Sans</family>
			<family>Verdana</family>
			<family>Arial</family>
			<family>Albany AMT</family>
			<family>Luxi Sans</family>
			<family>Nimbus Sans L</family>
			<family>Helvetica</family>
			<family>Nachlieli</family>
			<family>MgOpen Moderna</family>
			<family>AR PL KaitiM GB</family>
			<family>AR PL KaitiM Big5</family>
			<family>IPAPGothic</family>
			<family>&#65325;&#65331; &#12468;&#12471;&#12483;&#12463;</family>
			<family>Sazanami Gothic</family>
			<family>Kochi Gothic</family>
			<family>FreeSans</family>
			<family>Baekmuk Dotum</family>
			<family>SimSun</family>
		</prefer>
	</alias>
	<alias>
		<family>monospace</family>
		<prefer>
			<family>DejaVu Sans Mono</family>
			<family>Bitstream Vera Sans Mono</family>
			<family>Andale Mono</family>
			<family>Courier New</family>
			<family>Cumberland AMT</family>
			<family>Luxi Mono</family>
			<family>Nimbus Mono L</family>
			<family>Courier</family>
			<family>Miriam Mono</family>
			<family>IPAGothic</family>
			<family>&#65325;&#65331; &#12468;&#12471;&#12483;&#12463;</family>
			<family>Sazanami Gothic</family>
			<family>Kochi Gothic</family>
			<family>FreeMono</family>
			<family>AR PL KaitiM GB</family>
			<family>Baekmuk Dotum</family>
		</prefer>
	</alias>

	<match target="font">
		<edit name="embeddedbitmap" mode="assign">
			<bool>false</bool>
		</edit>
	</match>
</fontconfig>
```

The alias portion of the file will make that whenever we need a Japanese (or any language) character the list will be traversed in that order and use the first font that matches. So if we have the IPA fonts those will be used, if not then we'll fall back to MS fonts, Sazanami, etc. You can change the order to suit your personal taste.

For the second part you need to know a bit about how fonts work. With some fonts and certain sizes, if the font's got an embedded bitmap, it's used instead of the outlined antialiased version *[4]*. The reason behind this could be readability, but in my opinion the great majority of modern displays offer far more pleasant fonts for the outline versions, no matter the size. I've read that some Chinese users like the bitmap versions, but I'm not sure of that. If you want to be on the safe side so that for other fonts the bitmap versions are used when Gnome (fontconfig?) dictates appropriate, you could use this portion of text instead of the above:
```
	<match target="font">
		<test name="lang" compare="contains">
			<string>ja</string>
		</string>
		<edit name="embeddedbitmap" mode="assign">
			<bool>false</bool>
		</edit>
	</match>
```

On the other hand you might like the bitmap versions for Japanese fonts, too (maybe for very high DPI screens, but I'd like feedback on this) and drop that part altogether.

*[4]* For example, in my system IPA fonts with size 12 or MS fonts with size 14. Although the IPA fonts have embedded bitmaps for sizes 14 and 16, too, they're not used for that size, unlike MS fonts.

**Final notes:**
I should say that this applies to native Gnome applications. OOo uses its own idiosyncrasies when it comes to use bitmap versions or outline versions of the font. A way to force the use of outline versions can be using FontForge, load the fonts without loading the bitmap versions, and then export them as TrueType fonts. I must say that because each fontset includes several fonts inside (e.g. MSGothic includes MSGothic, MSPGothic and MSUIGothic) it can be a bit tiresome. Again, this applies if the font is displayed at certain sizes (remember that all this is for **displaying** text, so if you zoom on it or print it the appearance should be fine).

**Credits and other stuff:**
All that's been described here has been the product of a couple of hours going through several threads in Ubuntu forums, looking through .font.conf examples and language-selector stuff and browsing some fontconfig documentation. If you feel you can add anything here or I'm wrong on some (or much) of this HOWTO please post it here so that more people can get the most out of it. I'm not an expert of any sort, but this worked for me so let me know if it works for you, too.

---

### Post by kirillrdy on 2006-07-01
&#12354;&#12426;&#12364;&#12392;&#12358;&#12288;&#65306;-&#65289;

---

### Post by WoggleOne on 2007-02-01
Just wanted to say thank you.

As a new Ubuntu (and Linux in general) user, who spends as much if not more time working in Japanese than English I was really having a hard time coping with the fonts as display by default.

This has made things look oh so, oh so much better!  A million thanks.  Learned quite a bit while following the instructions, also. :)

Now, if only SCIM would play nice with Firefox 2.0 so I can upgrade from 1.5.0.9 without FF hanging at start!!

---

### Post by BioTeX on 2007-08-17
Nice, now I no longer get blank squares for certain kanji in Amarok.

---

