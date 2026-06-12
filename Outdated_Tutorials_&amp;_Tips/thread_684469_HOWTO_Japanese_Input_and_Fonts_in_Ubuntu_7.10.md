---
title: "HOWTO: Japanese Input and Fonts in Ubuntu 7.10"
date: 2008-02-01
forum: Outdated Tutorials &amp; Tips
---

### Post by ryukent on 2008-02-01
[SIZE="4"]**HOWTO: Installing Japanese that looks nice on Ubuntu 7.10 (Gutsy): &#26085;&#26412;&#35486;**[/SIZE]
[B]
Installing Japanese Input and Superior Font Setup in Ubuntu
Introduction[/B]

This is a guide to setting up Japanese for Ubuntu 7.10 Gutsy. It is intended as a complete guide encompassing all elements required for using Japanese on any language installation of Ubuntu. It covers input (UIM-Anthy) and configuring the Japanese fonts. There are other 
guides around for older versions of Ubuntu or that use the alternative SCIM. They tend to cover elements only. This guide is intended to cover everything. Please note that Kubuntu requires slightly different steps. Please follow the relevant page accordingly. This is an updated version based on the original 7.04 one, but with some sections changed. Please note that if you follow this guide, your fonts will be reconfigured. This might mean losing some font settings you may have made. I have chosen to switch to UIM from SCIM because SCIM (ubuntu) does not properly support XIM at the moment. That means in applications not written for GTK or QT, you will not be able to use extended characters. UIM on the other hand should support 100% of applications.

**Issues Involved**

There are two main issues here:

1.Installing the UIM input system that will work in a locale other than converting your whole install to Japanese, i.e. you want Japanese input in an English login.

2.The fonts look initially terrible. Therefore a certain amount of customisation is required to make all the Kanji's render in the same style and Hiragana & Katakana to render in a non-handwriting style.

**Japanese Input with UIM**

This section covers setting up the Japanese input system using UIM Anthy. This involves, downloading, installing and configuring it so that you can use it in non-Japanese locales (e.g. your system is in English).

**Setting Up Repositories**

First lets make sure you have the correct repositories installed in order to automatically download the relevant packs. Make sure you have the Universe and Multiverse repositories switched on. This can be done in 'Synaptic Package Manager' under the repositories tab. Also, you need the Japanese repository too. Open the repositories list file:

```
gksudo gedit /etc/apt/sources.list
```

Add the following line at the bottom:

```
deb http://archive.ubuntulinux.jp/ubuntu-ja gutsy/
```

Note that you will need to change 'gutsy' if you are using a different version from 7.10. Now update your repos with:

```
sudo apt-get update
```

At this stage, you will probably get an error saying that the repository is not validated. Ignore this for now. The following step will correct it. After adding the repository and running the update, you also need to add a keyring for the new location:

```
sudo apt-get install ubuntu-ja-keyring
```

**Adding Ubuntu Language Support**

Go to System / Administration / Language Support and select Japanese. This should install the basics.

**Installing UIM**

Although the default input method (SCIM) will have been installed, there are still certain bugs which mean that it will not function correctly in all applications, specifically non GTK (Gnome) ones. For this reason we will install UIM. This alternative provides the same input converter (Anthy) as SCIM did, but also provides a much more stable and compatible back end.

```
sudo apt-get install uim uim-anthy uim-common uim-gtk2.0 uim-qt uim-xim
```

As long as you have followed the above steps (including switching on Japanese language support), you should have all the necessary packages installed. Now we need to set up UIM.

**Making UIM available under a non-Japanese login**

Now you want to make UIM (Language input system) available in your English (or other lang) login and not just the Japanese one.

```
sudo im-switch -s uim-systray
```

This will change the input system over to UIM and tell it to dock itself in the system tray at the top of your screen. You now need to restart your computer. When the system has rebooted and you have logged back into Ubuntu, you should notice a new icon in the top right corner (or wherever your systray is). To check that it is working, open text editor. The icons now displayed in the UIM bar allow you to select different input methods. The first one should be clicked on and set to 'Anthy'. This is the Japanese input system. The second one allows you to choose between character types. Holding SHIFT and hitting SPACE will allow you to toggle between these.

Note: You might want to set Anthy as your default input method. You can do this in the UIM preferences window by clicking on the spanner and screwdriver icon in the UIM bar.

**Setting up the system to display Japanese characters properly**

OK, now you've got Japanese input installed (hopefully). But for me, I really couldn't cope with the horrible fonts that defaulted. Here's the next step.

Now that you have the Japanese repositories set up (see above), you'll want to get a nice set of fonts.
[B]
Downloading Repository Fonts[/B]

```
sudo apt-get install msttcorefonts ttf-dejavu ipafont ipamonafont ttf-arphic-ukai ttf-arphic-uming
```

This will install the Microsoft (Freeware) core fonts and a number of other useful fonts, specifically ones that support Japanese unicode characters.

**Downloading External Fonts**

Unfortunately, I am very disappointed in the Ubuntu selection and you will almost certainly want this to be changed to MSGothic and MSMincho. These are Microsoft fonts, but they are freely available to use and are actually from a company called Ricoh. They need to be downloaded and installed manually. They can be found at the following page.

[http://www.linux.ryukent.co.uk/show.php?id=24]("http://www.linux.ryukent.co.uk/show.php?id=24")

So download and extract the files and you need to copy them into the fonts directory. This will need root privileges and is probably easiest done using the file explorer:

```
gksudo nautilus --browser
```

That will give you a browser with the right privileges. So copy your downloaded ttf files and paste them into a folder under the fonts tree. I recommend:

```
/usr/share/fonts/truetype/msttcorefonts
```

Rebuilding the font cache

Now we need to rebuild the fonts cache:

```
sudo fc-cache -f -v
```

**Setting up the font order**

OK, so that might well be enough, but I think you'll probably still have your Japanese fonts not running at optimum and the default might be a little ugly. Lets set up the order in which we like the fonts to be selected. Open the “.fonts.conf” file in your home directory:

```
gksudo gedit ~/.fonts.conf
```

It should read as follows:

```
<?xml version="1.0"?>
<fontconfig>
 <alias>
 <family>serif</family>
 <prefer>
 <family>Times New Roman</family>
 <family>&#65325;&#65331; &#26126;&#26397;</family>
 <family>IPAPMincho</family>
 <family>Sazanami Mincho</family>
 <family>Kochi Mincho</family>
 <family>DejaVu Serif</family>
 <family>Bitstream Vera Serif</family>
 <family>Thorndale AMT</family>
 <family>Luxi Serif</family>
 <family>Nimbus Roman No9 L</family>
 <family>Times</family>
 <family>Frank Ruehl</family>
 <family>MgOpen Canonica</family>
 <family>AR PL SungtiL GB</family>
 <family>AR PL Mingti2L Big5</family>
 <family>FreeSerif</family>
 <family>Baekmuk Batang</family>
 </prefer>
 </alias>
 <alias>
 <family>sans-serif</family>
 <prefer>
 <family>Verdana</family>
 <family>&#65325;&#65331; &#12468;&#12471;&#12483;&#12463;</family>
 <family>IPAPGothic</family>
 <family>Sazanami Gothic</family>
 <family>Kochi Gothic</family>
 <family>DejaVu Sans</family>
 <family>Bitstream Vera Sans</family>
 <family>Arial</family>
 <family>Albany AMT</family>
 <family>Luxi Sans</family>
 <family>Nimbus Sans L</family>
 <family>Helvetica</family>
 <family>Nachlieli</family>
 <family>MgOpen Moderna</family>
 <family>AR PL KaitiM GB</family>
 <family>AR PL KaitiM Big5</family>
 <family>FreeSans</family>
 <family>Baekmuk Dotum</family>
 <family>SimSun</family>
 </prefer>
 </alias>
 <alias>
 <family>monospace</family>
 <prefer>
 <family>Courier New</family>
 <family>&#65325;&#65331; &#12468;&#12471;&#12483;&#12463;</family>
 <family>IPAGothic</family>
 <family>Sazanami Gothic</family>
 <family>Kochi Gothic</family>
 <family>DejaVu Sans Mono</family>
 <family>Bitstream Vera Sans Mono</family>
 <family>Andale Mono</family>
 <family>Cumberland AMT</family>
 <family>Luxi Mono</family>
 <family>Nimbus Mono L</family>
 <family>Courier</family>
 <family>Miriam Mono</family>
 <family>FreeMono</family>
 <family>AR PL KaitiM GB</family>
 <family>Baekmuk Dotum</family>
 </prefer>
 </alias>
 <match target="font" >
 <edit mode="assign" name="embeddedbitmap" >
 <bool>false</bool>
 </edit>
 </match>
 <match target="font" >
 <edit mode="assign" name="autohint" >
 <bool>true</bool>
 </edit>
 </match>
</fontconfig>
```

So, save the file and reboot xwindows (CTLR+ALT+Backspace). Now with any luck the order of fonts should have been updated so that the default Japanese type face is actually a clean one first and foremost instead of the ugly first serving. Also it disables the built in bitmap font which can really make kanji's look odd next to anti aliased hiragana etc. For most people this setting will be fine. If you're not happy, by all means leave out the embeddedbitmap setting.

---

### Post by GutsyVirgin on 2008-02-13
**I was having MAJOR issues** with the SCIM Input method so this tutorial helped me a LOT. Thanks so much. I searched all over on how to fix the problems I was having and would never have imagined that **SCIM was responsible**. This is the only tutorial which actually helped.

**Problems** encountered before replacing SCIM with UIM:
**1.** Open Office would crash every time I tried accessing an item in any menu.
**2.** Couldn't enter any text to rename any files or folders (especially on the desktop).

---

### Post by b0ng0 on 2008-02-17
I used this method but I found that creating the fonts.conf file changed some of my default fonts (e.g. in the terminal, etc) to less nice ones. How can I change the order so that it's just the Japanese fonts that are changed. 

p.s. I didn't originally have a fonts.conf file.

---

### Post by ryukent on 2008-02-18
If you want to change the fonts used by the system for generic stuff, you have two choices.

1. You can to to System / Preferences / Appearance / Fonts and select the application fonts you want there.

2. You can edit the fonts.conf file yourself and swap the first line in each section with the font you want. Note that "serif", "sans-serif" and "monospace" are not actually fonts, they simply refer to the list you have in the fonts.conf file. In the example I gave above, Times New Roman is the serif font, Verdana is the sans-serif font and Courier New is the monospace font. On my system I think this looks pretty good. You may think otherwise and therefore substitute your own selection to the top of the list.

Note, this will only change fonts you already have selected as this generic 3 fonts. Terminal usually uses the system serif font. However, you can specifically set a different font to use in terminal itself.

Also, you might want to enable subpixel smoothing in the font dialogue if you have an LCD screen as it makes the fonts a lot smoother.

Hope this helps.

---

### Post by jmap82 on 2008-03-02
Excellent How-to!  I'm very much a new-comer to the Ubuntu scene and currently living in Japan, having Japanese input is a plus!  Thanks for helping me make that possible!

&#12354;&#12426;&#12364;&#12392;&#12358;&#12288;&#12372;&#12374;&#12356;&#12414;&#12375;&#12383;&#65281;&#12288;

---

### Post by ryukent on 2008-03-05
With regards to my earlier comments about SCIM, it seems the XIM module is not in fact broken. There are however certain problems you might experience if you're using a locale other than en_US.UTF-8. So for people outside the US, if you want to run SCIM in XIM mode:

Install SCIM using the default language packs from System / Admin / Language support. Run "im-switch -z en_GB -s scim". You'll need to change the en_GB to whatever your locale is. Then into your ~/.scim/global file and make sure there a line with:

/SupportedUnicodeLocales = en_US.UTF-8,en_GB.UTF-8

Note also that there is no space after the comma. If you put a space in, it won't work. Again you'll have to change en_GB to your locale.

Now log out and log back in again. Should work now!

---

### Post by ahmadzainul on 2008-03-27
&#12354;&#12426;&#12364;&#12392;&#12357;&#12372;&#12374;&#12356;&#12414;&#12377; (terima kasih, thank you very much):popcorn:

---

### Post by Kiri on 2008-03-29
Hi
I followed the guide, but it did not seem to improve display of the fonts. 
Actually the Japanese fonts in Hardy look ok to me. But the really horrible ones are the ones used in Firefox to display Japanese web pages. 
I was hoping to fix that, but your method did not seem to effect Firefox...
So I reversed the steps to try and get back to where I was before following your guide.

But I cannot get the fonts to go back to the handwriting style they had before (for hiragana and katakana). Can you tell me how can I revert to that style?

Also, do you know anyway to fix theJapanese fonts for Firefox 3b4? (actually the English ones look awful in Firefox too though...)

---

### Post by kung fu buntu on 2008-04-05
I have have &#26085;&#26412;&#35486;&#12288;input. But am facing other problems.


[COLOR="Red"]**1)  **[/COLOR]The keyboard shortcut to toggle between japanese and direct input only works sometimes :( Most of them I have to use the mouse. I'm using KDE.



[COLOR="Red"]**2) ** [/COLOR]How do I get japanese language support in every program? And I don't mean writting. This is what troubles me:

I downloaded an archive from amule, whose filename showed japanese characters (kanji alphabet) in amule.

The downloaded file no longer shows japanese characters in the filename, neither in bash, nor in konqueror.

Opening the archive with xarchive shows the archive's filename correctly (with japanese characters).
But it messes up all the filenames of the mp3s inside. It can't handle the filenames and ends up by showing the same name for several files.
The result is that when I try to extract the files, it only extracts some... the ones that have different names.

If I go to bash and use the non-FOSS unrar program I can list the filenames with no problems (both kanji, katakana and hiragana)... I see some squared dots in the rar file comments section, but I think those are supposed to be there.
Extracted files have the correct filename both in bash and in konqueror.

I put the mp3s in Amarok and the ID3 tags get all messed up for most of the files :(




[COLOR="Red"]**3) **[/COLOR]Where do I get a spellcheker?
I am learning japanese and I don't know if it's &#12371;&#12395;&#12385;&#12431;  or  &#12371;&#12395;&#12385;&#12356;&#12431;.  This is just an example. A spell checker will help me a lot.


[COLOR="Red"]**4) **[/COLOR]When I install ttf-vlgothic or ttf-arphic-ukai I get this message:```
Setting up ttf-vlgothic (20071215-2) ...
/var/cache/fontconfig: invalid cache file: 3830d5c3ddfd5cd38a049b759396e72e-x86-64.cache-2
/var/cache/fontconfig: invalid cache file: 7ef2298fde41cc6eeb7af42e48b7d293-x86-64.cache-2
/var/cache/fontconfig: invalid cache file: cabbd14511b9e8a55e92af97fb3a0461-x86-64.cache-2
/var/cache/fontconfig: invalid cache file: 3830d5c3ddfd5cd38a049b759396e72e-x86-64.cache-2
/var/cache/fontconfig: invalid cache file: 7ef2298fde41cc6eeb7af42e48b7d293-x86-64.cache-2
/var/cache/fontconfig: invalid cache file: cabbd14511b9e8a55e92af97fb3a0461-x86-64.cache-2
No CIDSupplement specified for Gulim-Regular, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular-JaH, defaulting to 0.
No CIDSupplement specified for Mikachan-PB, defaulting to 0.
No CIDSupplement specified for ShanHeiSun-Uni-JaH, defaulting to 0.
No CIDSupplement specified for SazanamiGothic-Regular, defaulting to 0.
No CIDSupplement specified for Mikachan-JaH, defaulting to 0.
No CIDSupplement specified for Mikachan-P-JaH, defaulting to 0.
No CIDSupplement specified for SazanamiMincho-Regular, defaulting to 0.
No CIDSupplement specified for Mikachan-P, defaulting to 0.
No CIDSupplement specified for Mikachan, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular, defaulting to 0.
No CIDSupplement specified for ShanHeiSun-Light, defaulting to 0.
No CIDSupplement specified for SazanamiGothic-Regular-JaH, defaulting to 0.
No CIDSupplement specified for ShanHeiSun-Uni-Ja, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular-JaH, defaulting to 0.
No CIDSupplement specified for ShanHeiSun-Uni-GB, defaulting to 0.
No CIDSupplement specified for SazanamiMincho-Regular-JaH, defaulting to 0.
No CIDSupplement specified for Mikachan-PS-JaH, defaulting to 0.
No CIDSupplement specified for ShanHeiSun-Uni, defaulting to 0.
No CIDSupplement specified for Mikachan-PS, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for Mikachan-PB-JaH, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
No CIDSupplement specified for Headline-Regular, defaulting to 0.





Setting up ttf-arphic-ukai (0.1.20060928-2.2) ...
/var/cache/fontconfig: invalid cache file: 089dead882dea3570ffc31a9898cfb69-x86-64.cache-2
No CIDSupplement specified for Gulim-Regular, defaulting to 0.
No CIDSupplement specified for ZenKai-Uni-Medium-JaH, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular-JaH, defaulting to 0.
No CIDSupplement specified for Mikachan-PB, defaulting to 0.
No CIDSupplement specified for ShanHeiSun-Uni-JaH, defaulting to 0.
No CIDSupplement specified for SazanamiGothic-Regular, defaulting to 0.
No CIDSupplement specified for Mikachan-JaH, defaulting to 0.
No CIDSupplement specified for Mikachan-P-JaH, defaulting to 0.
No CIDSupplement specified for SazanamiMincho-Regular, defaulting to 0.
No CIDSupplement specified for Mikachan-P, defaulting to 0.
No CIDSupplement specified for ZenKai-Uni-Medium-GB, defaulting to 0.
No CIDSupplement specified for Mikachan, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular, defaulting to 0.
No CIDSupplement specified for ShanHeiSun-Light, defaulting to 0.
No CIDSupplement specified for SazanamiGothic-Regular-JaH, defaulting to 0.
No CIDSupplement specified for ShanHeiSun-Uni-Ja, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular-JaH, defaulting to 0.
No CIDSupplement specified for ZenKai-Uni-Medium-Ja, defaulting to 0.
No CIDSupplement specified for ShanHeiSun-Uni-GB, defaulting to 0.
No CIDSupplement specified for SazanamiMincho-Regular-JaH, defaulting to 0.
No CIDSupplement specified for Mikachan-PS-JaH, defaulting to 0.
No CIDSupplement specified for ShanHeiSun-Uni, defaulting to 0.
No CIDSupplement specified for Mikachan-PS, defaulting to 0.
No CIDSupplement specified for ZenKai-Uni-Medium, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for Mikachan-PB-JaH, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
No CIDSupplement specified for Headline-Regular, defaulting to 0.
/var/cache/fontconfig: invalid cache file: 089dead882dea3570ffc31a9898cfb69-x86-64.cache-2
```


Thank you.

---

### Post by Kiri on 2008-04-05
The 2nd problem you are having might be to do with fonts. Try to set a Japanese capable font for document and/or application in your font settings (in admin>prefs>appearance)


I don't know about spell checking in Japanese, but for a lot of words when you hit the space bar it will try and convert to kanji if iyouve typed the word correctly. If it doesn't, or only converts parts of it, then chances are you've made a mistake

and its &#12371;&#12435;&#12395;&#12385;&#12399; by the way ;)

---

### Post by kung fu buntu on 2008-04-05
> **Kiri said:**
> The 2nd problem you are having might be to do with fonts. Try to set a Japanese capable font for document and/or application in your font settings (in admin>prefs>appearance)

I'm using Debian with KDE, so for me it's in Kcontrol / Appearance & Themes / Fonts.
I don't know if it gives the same control or not, but this is what I get: 
[IMG]http://www.linux.org/docs/ldp/howto/Font-HOWTO/kde.png[/IMG] 

Note that this isn't my screenshot. All my fonts are set to Sans Serif and Monospace.
What should I use instead?

Thank you.

---

### Post by Kiri on 2008-04-05
Actually I just tried making a file with a Japanese name and scim changed the font for it automatically, so maybe that is not the problem. 
Are you able to actually make a new file and give it a Japanese name?
And is it only those particular files that are giving you a problem or others too?
I wonder if it might be an encoding problem.. 
Different programs seem to use different encodings, so sometimes those special characters get messed up depending on what prog they are in... And it may also be possible that the program you downloaded them with didnt support those characters and so saved them with incorrect names.

I'm attaching a text file with Japanese file name. See if it displays correctly for you after you dl it

---

### Post by kung fu buntu on 2008-04-05
mmmh... guess I forgot to say an important thing.
I downloaded the file before I had IUM and japanese fonts in my system -_-'

But even though at that time, when using unrar (non free version) I was able to see and extract the files correctly from the .rar file.

And now that I have UIM installed and running, still none of the archive programs (xarchive, xarchiver, ark, karchive) is able to list or extract the files correctly. Only unrar non-FOSS is able to do that!

Yes I can create files with japanese filenames.
I was also able to download and open your file.
"This is japanese!
&#35501;&#12417;&#12427;&#12363;&#12356;?" :lolflag: What does the 2nd sentence mean? :-p

---

### Post by 2benglish on 2008-04-06
Thanks very much for this guide.
I used it before and it worked flawlessly. However, I have since had to reinstall 7.10 and now I get stopped at the pasting of the ttf files.

I am getting the message that I don't have permission to do so. Any ideas why, or another way to get access other than the line:

gksudo nautilus --browser

Thanks.

---

### Post by kung fu buntu on 2008-04-18
I'm having one problem with UIM.

How do you write word like &#12385;&#12424;&#12388;&#12392;? IIRC the &#12388; should be a little one.

---

### Post by johnraff on 2008-04-18
> **kung fu buntu said:**
> I'm having one problem with UIM.

How do you write word like &#12385;&#12424;&#12388;&#12392;? IIRC the &#12388; should be a little one.
How did you input it?
c h o t t o ought to work...

---

### Post by Kiri on 2008-04-19
> **kung fu buntu said:**
> I'm having one problem with UIM.

How do you write word like &#12385;&#12424;&#12388;&#12392;? IIRC the &#12388; should be a little one.

When you press T twice it should make it a small&#12288;&#12387;
(ie with japanese input type the following key combo:
chotto, and it should come out &#12385;&#12423;&#12387;&#12392;)

---

### Post by kung fu buntu on 2008-04-19
I also wasn't aware that if you type *cho* it becomes &#12385;&#12423;.

&#12393;&#12358;&#12418;&#12288;&#12354;&#12426;&#12364;&#12392;&#12288;&#12415;&#12394;&#12540;&#12373;&#12435;&#12290;

&#12385;&#12423;&#12387;&#12392;&#12290;&#12290;&#12290;

---

### Post by Tanizaki on 2008-04-19
> **kung fu buntu said:**
> I'm having one problem with UIM.

How do you write word like &#12385;&#12424;&#12388;&#12392;? IIRC the &#12388; should be a little one.

You can also make it and some other kana small by typing an x before it. For example, "xya" is &#12419; (compare with &#12420;) or "xtsu" is &#12387; (compare with &#12388;). This will only work for kana that have a small version in Japanese for use as a y&#333;on or sokuon.

---

### Post by ryukent on 2008-04-22
To answer some point above:

If you can type in Japanese in gnome, but some programs don't allow you to view Japanese text, it is usually because they were written without correct support for unicode. I think this especially affects stuff written in C. Sadly there's not much you can do about it other than write to the coders and ask them to add support for extended character sets.

"sudo nautilus --browser" should give you a root browser is gksudo doesn't work... are you using KDE? gksudo is for gnome.

You can also get the small characters using the "L" button before you type. So "ltu" gives &#12387; but "tu" gives &#12388;. I just remember it as "little ~" hence the "L". This is the same for &#38651;&#23376;&#36766;&#26360;'s too so I guess it's standard.

---

### Post by tora201 on 2008-04-28
Just noticed that this guide no longer works with inputting Japanese in non-GTK programs (Skype for example) in a new install of 8.04. Nor does the  UIM panel display in Gnome's panel or appear in the menu bar... although you can still input Japanese (in GTK programs) by pressing the key-combination. 

It all worked fine in 8.04 beta, though..... 

Any ideas would be welcome.

---

### Post by dr_bovine on 2008-04-28
> **tora201 said:**
> Just noticed that this guide no longer works with inputting Japanese in non-GTK programs (Skype for example) in a new install of 8.04. Nor does the  UIM panel display in Gnome's panel or appear in the menu bar... although you can still input Japanese (in GTK programs) by pressing the key-combination. 

It all worked fine in 8.04 beta, though..... 

Any ideas would be welcome.

It works for me in Skype (though the characters look like crap) for a clean install of Hardy.  However, the UIM panel isn't showing up in the bar like it did for me in Gutsy.  I get a single keyboard icon that let's me select the input language, instead of the four icons I had before.  It all seems to work, so I'm not complaining ... just thought I'd mention it.

ryokent-&#12373;&#12435;&#12395;&#12289;&#12372;&#25945;&#31034;&#12354;&#12426;&#12364;&#12392;&#12358;&#12372;&#12374;&#12356;&#12414;&#12377;&#12290;&#21161;&#12363;&#12426;&#12414;&#12375;&#12383;&#12290;

---

### Post by tora201 on 2008-04-29
> **dr_bovine said:**
> It works for me in Skype (though the characters look like crap) for a clean install of Hardy.  However, the UIM panel isn't showing up in the bar like it did for me in Gutsy.  I get a single keyboard icon that let's me select the input language, instead of the four icons I had before.  It all seems to work, so I'm not complaining ... just thought I'd mention it.

ryokent-&#12373;&#12435;&#12395;&#12289;&#12372;&#25945;&#31034;&#12354;&#12426;&#12364;&#12392;&#12358;&#12372;&#12374;&#12356;&#12414;&#12377;&#12290;&#21161;&#12363;&#12426;&#12414;&#12375;&#12383;&#12290;

Strange..  I will re-install and see if I can't fix this. Annoying, but oh well! Cheers for the input -- it should work, then!

---

### Post by tora201 on 2008-04-30
> **dr_bovine said:**
> It works for me in Skype (though the characters look like crap) for a clean install of Hardy.  However, the UIM panel isn't showing up in the bar like it did for me in Gutsy.  I get a single keyboard icon that let's me select the input language, instead of the four icons I had before.  It all seems to work, so I'm not complaining ... just thought I'd mention it.

ryokent-&#12373;&#12435;&#12395;&#12289;&#12372;&#25945;&#31034;&#12354;&#12426;&#12364;&#12392;&#12358;&#12372;&#12374;&#12356;&#12414;&#12377;&#12290;&#21161;&#12363;&#12426;&#12414;&#12375;&#12383;&#12290;

Oh... by the way, it still did not work after a clean install. When reading your message again, I realized you are probably talking about SCIM.(from the description of the keyboard item). I guess SCIM works better than UIM, then? Somebody care to elaborate or clear this up? So, SCIM now suddenly works with SKYPE and UIM doesn't? Or, I am just confused?

---

### Post by tora201 on 2008-05-02
Ok... to solve this problem (and use UIM, which works in ALL non-GTK applications, including Skype btw), I re-installed 8.04 beta 4, and then followed the guide presented in the first post of this thread. After that, I did a distro-upgrade to Hardy 8.04 Final and all is now fine. 

Oh, one thing: while I did install all the extra Japanese fonts (including the Microsoft ones) I did not alter the font settings. (latter part of the first post). I find that Hardy works very well in Japanese sites without changes, with the display very similar to or if not better than Vista - smooth and pleasing to the eye. Just make sure that if you are using a LCD, you change to sub-pixel smoothing in system --> appearance. Anyway, pleased to have it all set up perfectly now.

:guitar:

---

### Post by ryukent on 2008-05-30
I've done a new guide for Hardy. It's with SCIM this time as SCIM seems to be default and compatibility problems have been solved. Please note that a number of changes have been made. If you're using hardy, I strongly recommend using the new tutorial.

[http://ubuntuforums.org/showthread.php?t=812552](http://ubuntuforums.org/showthread.php?t=812552)

UIM guide is to follow.... when I have time.

---

### Post by marlon89br on 2008-06-01
Hi, very nice tutorial!! I executed it a few weeks ago and it worked just fine.

I am learning japanese just for fun and I don't study a lot. I don't want UIM toolbar to load in my tray anymore. How do I revert it? And how can I enable it when I want to use it?

Thanks.

---

### Post by ryukent on 2008-06-02
Marlon,

im-switch -c

Will give you a list of input methods on a menu and allow you to select the one you want. Running it under sudo should allow changes to the root user.

Select none to turn off uim and run the command again to put it back to uim if you want.

Also, good luck with the Japanese!!!

---

### Post by marlon89br on 2008-06-03
Thank you... got it.

---

### Post by marlon89br on 2008-07-26
&#12371;&#12435;&#12395;&#12385;&#12399;
Is there a way to enable handwrite recognition pad using this tutorial? I've used it when I had Hardy installed, but I came back to Gutsy due some hardware compatibility problems (random freezes).
This feature would be a lot of useful to me, I'm just beginning my japanese studies, so I don't know the readings of the kanjis.
&#12354;&#12426;&#12364;&#12392;&#12358;&#12372;&#12374;&#12356;&#12414;&#12377;

---

### Post by msnel on 2008-08-03
Couldn't find a "thank you" button or some other way to thank you without writing a message so I'll just do it like this. Thanks, that was very helpful.

---

### Post by kmajor on 2009-06-13
+1 on a huge &#12354;&#12426;&#12364;&#12392;&#12358;&#12372;&#12374;&#12356;&#12414;&#12377;&#65281;&#65281;  My SCIM was definitely Fu#@'d and your tutorial saved me countless hours.  Cheers!!!!

&#12288;

---

