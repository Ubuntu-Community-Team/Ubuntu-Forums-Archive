---
title: "HOWTO: Hoary ClearType-like fonts"
date: 2005-03-19
forum: Outdated Tutorials &amp; Tips
---

### Post by deelerious on 2005-03-19
Q: How can I make my fonts in Hoary more Windows like?

A: See immediately below for a ClearType look. See end note for non-antialiased look.

Note: Much of this can be simplified if not using Tahoma. It is included here since Tahoma is used extensively in XP.

For comparison, here's Windows with ClearType:
[[IMG]http://home.comcast.net/~ddamian/ubuntu/howto/howto_cleartype_WIN_th.png[/IMG]](http://home.comcast.net/~ddamian/ubuntu/howto/howto_cleartype_WIN.png)  

And here's Ubuntu showing the same page:
[[IMG]http://home.comcast.net/~ddamian/ubuntu/howto/howto_cleartype_UBU_th.png[/IMG]](http://home.comcast.net/~ddamian/ubuntu/howto/howto_cleartype_UBU.png)  

Many thanks to all the people who contributed to the links below, most of this is simply adapted to Ubuntu from there.
[http://www.linuxquestions.org/questions/showthread.php?s=&threadid=257705&perpage=15&pagenumber=1](http://www.linuxquestions.org/questions/showthread.php?s=&threadid=257705&perpage=15&pagenumber=1)
[http://avi.alkalay.net/linux/docs/font-howto/Font.html](http://avi.alkalay.net/linux/docs/font-howto/Font.html)
[http://convexhull.com/mandrake_fonts.html](http://convexhull.com/mandrake_fonts.html)
[http://www.ubuntuforums.org/showthread.php?t=4456](http://www.ubuntuforums.org/showthread.php?t=4456)

Step 1. Configure X and Gnome to 96 dpi
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo gedit /etc/X11/xorg.conf
```
Locate Section "Monitor" and add the following lines before EndSection:
```
#	DisplaySize	270	203	# 1024x768 96dpi
#	DisplaySize	338	254	# 1280x960 96dpi
#	DisplaySize	338	270	# 1280x1024 96dpi
#	DisplaySize	370	277	# 1400x1050 96dpi
#	DisplaySize	423	370	# 1600x1400 96dpi
``` 
Uncomment the line corresponding to your current resolution.

To get other values, use the following formula:
displaysize = <pixelsize>/96*25.4

Either restart X or reboot, after which verify the dpi setting is correct:
```
xdpyinfo | grep dimensions
xdpyinfo | grep resolution
``` 
If the resolution is not  96x96 dots per inch slightly adjust the DisplaySize values until correct.

Configure Gnome to run at 96 dpi in System > Preferences > Font > Details

Step 2. Install Microsoft fonts

Install msttcorefonts package (Microsoft TrueType core fonts)

OPTIONAL - If you own a licensed copy of Windows you may also add Tahoma which is not present in msttcorefonts. You can install it in your home directory by simply copying it into ~/.fonts. If so, you're done, skip to the next step. Alternatively, you can follow the more involved steps below and install it system-wide, which has the advantage of making it available to GTK1 appplications.

NOTE: If there's a better way to do this please correct me. Thanks.
```
sudo mkdir /usr/share/fonts/truetype/custom
``` 
Copy tahomabd.ttf  and tahoma.ttf into /usr/share/fonts/truetype/custom/
Create Tahoma hints:
```
sudo gedit /etc/defoma/hints/custom.hints
``` 
Paste this:
```
category truetype
begin /usr/share/fonts/truetype/custom/tahoma.ttf
  Family = Tahoma
  FontName = Tahoma-Regular
  Encoding = Unicode
  Location = Magyar Dutch Spanish Czech Russian English Catalan Slovak Italian Turkish Danish Slovenian Basque Portuguese German Polish Swedish Norwegian French Finnish Greek
  Charset = ISO8859-1 ISO8859-2 ISO8859-3 ISO8859-4 ISO8859-5 ISO8859-7 ISO8859-9 ISO8859-10 ISO8859-13 ISO8859-14 ISO8859-15 KOI8-R KOI8-U CP1251 VISCII1.1-1 TCVN-5712 ISO10646-1
  UniCharset = ISO8859-1 ISO8859-2 ISO8859-3 ISO8859-4 ISO8859-5 ISO8859-7 ISO8859-9 ISO8859-10 ISO8859-13 ISO8859-14 ISO8859-15 KOI8-R KOI8-U CP1251 VISCII1.1-1 TCVN-5712
  GeneralFamily = SansSerif
  Weight = Medium
  Width = Variable
  Shape = NoSerif Upright
  Foundry = Microsoft
  Priority = 20
end
begin /usr/share/fonts/truetype/custom/tahomabd.ttf
  Family = Tahoma
  FontName = Tahoma-Bold
  Encoding = Unicode
  Location = Magyar Dutch Spanish Czech Russian English Catalan Slovak Italian Turkish Danish Slovenian Basque Portuguese German Polish Swedish Norwegian French Finnish Greek
  Charset = ISO8859-1 ISO8859-2 ISO8859-3 ISO8859-4 ISO8859-5 ISO8859-7 ISO8859-9 ISO8859-10 ISO8859-13 ISO8859-14 ISO8859-15 KOI8-R KOI8-U CP1251 VISCII1.1-1 TCVN-5712 ISO10646-1
  UniCharset = ISO8859-1 ISO8859-2 ISO8859-3 ISO8859-4 ISO8859-5 ISO8859-7 ISO8859-9 ISO8859-10 ISO8859-13 ISO8859-14 ISO8859-15 KOI8-R KOI8-U CP1251 VISCII1.1-1 TCVN-5712
  GeneralFamily = SansSerif
  Weight = Bold
  Width = Variable
  Shape = NoSerif Upright
  Foundry = Microsoft
  Priority = 20
end
``` 
Register Tahoma:
```
sudo /usr/bin/defoma-font -v register-all /etc/defoma/hints/custom.hints
``` 

Step 3. Configure system-wide fontconfig rendering method
```
sudo dpkg-reconfigure fontconfig
``` 
Select Bytecode interpreter or Subpixel rendering

Step 4. Configure Gnome font preferences to your liking. Example:
[[IMG]http://home.comcast.net/~ddamian/ubuntu/howto/gnome_font_prefs_th.png[/IMG]](http://home.comcast.net/~ddamian/ubuntu/howto/gnome_font_prefs.png) 

Step 5. Turn autohinting on for fonts larger than 12 pts (this will include the Firefox fonts) and perform font substitution for websites using Bitstream, Helvetica and Palatino fonts. Feel free to adjust these to your liking.

With autohinting on, Tahoma loses proper spacing and the letters mush together. Tweaking .fonts.conf turns off autohinting for smaller font sizes.
```
gedit ~/.fonts.conf
``` 
Paste this:
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
<match target="font">
 <test compare="more" name="pixelsize" qual="any">
  <double>12</double>
 </test>
 <edit name="autohint" mode="assign" >
  <bool>true</bool>
 </edit>
</match>
<match target="pattern">
            <test qual="any" name="family">
                    <string>Bitstream Vera Sans</string>
            </test>
            <edit name="family" mode="assign">
                    <string>Arial</string>
            </edit>
</match>
    <match target="pattern">
            <test qual="any" name="family">
                    <string>Helvetica</string>
            </test>
            <edit name="family" mode="assign">
                    <string>Arial</string>
            </edit>
</match>
<match target="pattern">
            <test qual="any" name="family">
                    <string>Palatino</string>
            </test>
            <edit name="family" mode="assign">
                    <string>Georgia</string>
            </edit>
</match>
</fontconfig>
``` 
Log out of Gnome and log back in.

Step 6. OPTIONAL - Configure GTK1 applications to use Tahoma
```
gedit ~/.gtkrc.mine
``` 
Paste this:
```
style "user-font"
{
  fontset="-microsoft-tahoma-medium-r-normal-*-10-*-*-*-p-*-*"
}
widget_class "*" style "user-font"
``` 
Substitute with Verdana or other font as desired.

Step 7. Configure Firefox fonts. Example:
[[IMG]http://home.comcast.net/~ddamian/ubuntu/howto/firefox_fonts_th.png[/IMG]](http://home.comcast.net/~ddamian/ubuntu/howto/firefox_fonts.png)

END NOTE: This could also be used to turn anti-aliasing off alltogether for the smaller fonts that are used in the menus, dialog boxes, toolbar text, etc. I've seen that question asked a few times, so I'll address it below. Doing so will make Gnome look exactly like Windows without ClearType, while still antialiasing large fonts used for example in website titles and headings. Use this .fonts.conf in Step 5:
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
<match target="font">
 <test compare="more" name="pixelsize" qual="any">
  <double>0</double>
 </test>
 <test compare="less" name="pixelsize" qual="any">
  <double>15</double>
 </test>
 <edit mode="assign" name="antialias">
  <bool>false</bool>
 </edit>
</match>
<!-- UNCOMMENT THIS SECTION TO ENABLE ANTIALIAS FOR BOLD FONTS
<match target="font">
 <test name="weight">
  <const>bold</const>
  <const>black</const>
 </test>
 <edit name="antialias" mode="assign">
  <bool>true</bool>
 </edit>
</match>
-->
<match target="pattern">
            <test qual="any" name="family">
                    <string>Bitstream Vera Sans</string>
            </test>
            <edit name="family" mode="assign">
                    <string>Arial</string>
            </edit>
</match>
    <match target="pattern">
            <test qual="any" name="family">
                    <string>Helvetica</string>
            </test>
            <edit name="family" mode="assign">
                    <string>Arial</string>
            </edit>
</match>
<match target="pattern">
            <test qual="any" name="family">
                    <string>Palatino</string>
            </test>
            <edit name="family" mode="assign">
                    <string>Georgia</string>
            </edit>
</match>
</fontconfig>
```

---

### Post by deelerious on 2005-03-19
I reached the limit of screenshots in the original post, so here is another comparison to Windows, this time with antialias turned off. Using the same steps and the .fonts.conf in the end note.

Windows:
[[IMG]http://home.comcast.net/~ddamian/ubuntu/howto/firefox_nonaa_win_th.png[/IMG]](http://home.comcast.net/~ddamian/ubuntu/howto/firefox_nonaa_win.png) 

Hoary:
[[IMG]http://home.comcast.net/~ddamian/ubuntu/howto/firefox_nonaa_ubuntu_th.png[/IMG]](http://home.comcast.net/~ddamian/ubuntu/howto/firefox_nonaa_ubuntu.png)

---

### Post by Julius on 2005-03-20
Great Howto! What I've been doing until now is just disable antialiasing for all fonts smaller than a certain size. I use Tahoma 8 as app. font so it looks exactly like windows. In firefox it works perfectly because it looks like in windows (I'm used to it :P). 
The only problem is that some apps will still use antialiased fonts (like Openoffice) so they become unreadable. I'd have to set a higher font size as the "antialiasing limit", which will turn off AA in some big font sizes depending on the application. 
It's as if not the size of fonts wasn't the same for all applications.

Is the same problem present with your method? I guess I can disable AA for Tahoma in all its sizes and turn it off on the other fonts for small font sizes...

---

### Post by basse1989 on 2005-03-20
Are you guys crazy? Why don't you install windows instead? Who would want their ubuntu installation to look like windows?

I think ubuntu works GREAT as it is (read my signature).

---

### Post by telmo on 2005-03-20
Just one question... can i do this for a different resolution? I'm currently using 1280x800 with an ATI driver.

---

### Post by Julius on 2005-03-21
[QUOTE=basse1989]Are you guys crazy? Why don't you install windows instead? Who would want their ubuntu installation to look like windows?

I think ubuntu works GREAT as it is (read my signature).[/QUOTE]

I've been using the same fonts for the past 13 years or something, so that's why I want my fonts to look the same. I like Linux, and I think Linux fonts are more 'powerful' than TrueType. THe thing is that most of websites have been designed using true type fonts, so many of them would look really ugly. If there's a way to make them look the same as they do in other operative systems, why not?

---

### Post by deelerious on 2005-03-21
[QUOTE=Julius]The only problem is that some apps will still use antialiased fonts (like Openoffice) so they become unreadable. I'd have to set a higher font size as the "antialiasing limit", which will turn off AA in some big font sizes depending on the application. 
It's as if not the size of fonts wasn't the same for all applications.

Is the same problem present with your method? I guess I can disable AA for Tahoma in all its sizes and turn it off on the other fonts for small font sizes...[/QUOTE]

For OpenOffice, see the post at the bottom of this [page](http://www.linuxquestions.org/questions/showthread.php?s=&threadid=257705&perpage=15&pagenumber=2).

---

### Post by deelerious on 2005-03-21
[QUOTE=telmo]Just one question... can i do this for a different resolution? I'm currently using 1280x800 with an ATI driver.[/QUOTE]

To get other values, use the following formula:
displaysize = <pixelsize>/96*25.4

In your case:
1280/96*25.4 = approx 338
800/96*25.4 = approx 211

So, in xorg.conf use this:
	DisplaySize	338	211	# 1280x800 96dpi

After restarting X, use xdpyinfo | grep resolution as shown above to make sure the dpi is 96 and, if needed, tweak the displaysize values until you get 96x96.

---

### Post by Bicet on 2005-03-26
>  Locate Section "Monitor" and add the following lines before EndSection:
  	Code:
 	[left]#	DisplaySize	270	203	# 1024x768 96dpi
#	DisplaySize	338	254	# 1280x960 96dpi
#	DisplaySize	338	270	# 1280x1024 96dpi
#	DisplaySize	370	277	# 1400x1050 96dpi
#	DisplaySize	423	370	# 1600x1400 96dpi[/left]
 
  
 Uncomment the line corresponding to your current resolution.


I don't have this sections and my resolutions is 1280x800

---

### Post by bored2k on 2005-03-27
Wicked, awsome .

---

### Post by Diego F. on 2005-03-29
Can I get this with Warty? I'm having problems with my resolution and with fonts.

Is a good idea migrating to Hoary?

---

### Post by Sniffer on 2005-03-29
[QUOTE=Diego F.]Can I get this with Warty? I'm having problems with my resolution and with fonts.

Is a good idea migrating to Hoary?[/QUOTE]


Yes on 6th of April....tough if you want much to try it out....  O:)

---

### Post by angrykeyboarder on 2005-03-30
[QUOTE=basse1989]Are you guys crazy? Why don't you install windows instead? Who would want their ubuntu installation to look like windows?

I think ubuntu works GREAT as it is (read my signature).[/QUOTE]

You obviously didn't read this very well did you?  We're talking about fonts here.

Even the most die-hard *nix geek will tell you that X has not been the best when it comes to font rendering and will admit Windows has generally always done it better.

This doesn't mean any of us want Linux to be like Windows....

---

### Post by basse1989 on 2005-03-30
[QUOTE=angrykeyboarder]You obviously didn't read this very well did you?  We're talking about fonts here.

Even the most die-hard *nix geek will tell you that X has not been the best when it comes to font rendering and will admit Windows has generally always done it better.

This doesn't mean any of us want Linux to be like Windows....[/QUOTE]
Windows font rendering looks ugly, ugly. But fonts in any linux distro I've ever tried have always looked nice. Same in OS X. Windows does most things ugly.

---

### Post by bored2k on 2005-03-30
[QUOTE=basse1989]Windows font rendering looks ugly, ugly. But fonts in any linux distro I've ever tried have always looked nice. Same in OS X. Windows does most things ugly.[/QUOTE]
 Supporting basse's opinion. Have you guys ever entered the forums from a Windows machine ? it looks **so** ugly ..

I still use the old ~/.fonts.conf trick to bold things a little bit, but I don't think angrykeyboarder is right when he says Win looks better *ugh* .

---

### Post by basse1989 on 2005-03-31
[QUOTE=bored2k]Supporting basse's opinion. Have you guys ever entered the forums from a Windows machine ? it looks **so** ugly ..

I still use the old ~/.fonts.conf trick to bold things a little bit, but I don't think angrykeyboarder is right when he says Win looks better *ugh* .[/QUOTE]
Now we are 2 to 1. :)

---

### Post by angrykeyboarder on 2005-03-31
[QUOTE=bored2k]Supporting basse's opinion. Have you guys ever entered the forums from a Windows machine ? it looks **so** ugly ..

I still use the old ~/.fonts.conf trick to bold things a little bit, but I don't think angrykeyboarder is right when he says Win looks better *ugh* .[/QUOTE]

What can I tell you. I've ***experienced just the opposite and I'm not alone***.  I will say X has come a ***long*** way over the past several years in the way of decent font rendering.

I've also got the balls to say that Mac OS does things better than others, Windows does things better than others and GNU/Linux does things better than others.

No OS is perfect.  I personally love the freedom and tweaking you get with Linux but sometimes I gotta boot into Windows cuz "Linux can't do that...." (yet).

---

### Post by bored2k on 2005-03-31
Your going off-topic. No ones talking about general  Linux-Mac-MS war *[what you talkin` 'bout Willis?]* , and I didn't say you HAD to experience the same I did. I know that on all machines I have tested in my short life span on Windows have looked nearly as great as anything on Linux [excluding KDE.. *ugh*] . 

You and your friend's boxes look better on Windows ? well, mine doesn't .

Now the part were you started talking about your personal *belongings*, only you should care about those ..

---

### Post by cdhotfire on 2005-03-31
Is it starting to get hot in here?

First impression on fonts at least on ubuntu, fonts dont look to great. Meaning they need some tweaking. But i will say this after spending sometime on ubuntu or any other linux distro, go and check what windows looks like. The letters look kind of blurred out, and it looks horrible. This is my experience, i just see linux distros have more smoothed display than windows. Well that was my input.:-)

edit: not really supporting this
> 
Are you guys crazy? Why don't you install windows instead? Who would want their ubuntu installation to look like windows?
 
 I think ubuntu works GREAT as it is (read my signature).

ubuntu is all about freedom, if you dont like this dont do it, but dont critize others for doing it.  Also i think this makes **my **fonts twice fold in quality,  even if its hard to believe there are somethings windows has done right.;)

---

### Post by gaza on 2005-03-31
[QUOTE=basse1989]Are you guys crazy? Why don't you install windows instead? Who would want their ubuntu installation to look like windows?

I think ubuntu works GREAT as it is (read my signature).[/QUOTE]

I agree with basse1980, I love the way Ubuntu looks. I love my Gnome2. and I really love not using windows.

---

### Post by NeoChaosX on 2005-03-31
Just followed the instructions to add Tahoma system-wide. However, GTK1 still refuses to recognize Tahoma. Whenever I pull up a GTK1 program in console, it comes up with this error:

```
The font "-microsoft-tahoma-medium-r-normal-*-14-*-*-*-p-*-*" does not support all the required character sets for the current locale "C"
  (Missing character set "ISO8859-1")
```

What's up with that?

EDIT: nevermind, X server restart did the trick.

---

### Post by Ren on 2005-03-31
thanks, this is a great guide, my desktop is looking great now

---

### Post by Buffalo Soldier on 2005-04-03
[QUOTE=angrykeyboarder]Even the most die-hard *nix geek will tell you that X has not been the best when it comes to font rendering and will admit Windows has generally always done it better.[/QUOTE][QUOTE=angrykeyboarder]What can I tell you. I've ***experienced just the opposite and I'm not alone***.  I will say X has come a ***long*** way over the past several years in the way of decent font rendering.[/QUOTE]Ubuntu in terms of fonts has been better than in MS Windows. The only two things I've changed are Bitstream Vera and turning on the autohinter.

---

### Post by 23meg on 2005-04-04
i very much respect the original author's efforts to compile this info, and everone's opinions on which os renders fonts better, but i have to say that i myself had no luck with font rendering in Ubuntu at all, and it's the main reason that i'm growing cold of Hoary.

i like small fonts. most people, when they look at my typical computer screen, will be amazed at how small my fonts are. i always use high resolutions (1400x1050 and 1600x1200 typically) and that's one factor that makes the fonts look small, but i also want to make maximum use of available screen space, so i keep them small. and i have to add that *i* am amazed, when i look at most screenshots posted on this forum, at how big the fonts commonly used by people are. there's no use in disputing taste, and my taste is small fonts, but Ubuntu (and so far my impression has been that X in general) simply loses the game against Cleartype when it comes to **rendering small fonts properly.** 

i do not intend to heat up the debate any more. and please don't flame me because i'm speaking just based on my own experience. there are many good guides out there like this one with clear instructions as to how to improve font rendering in Ubuntu and Gnome in general, but i just haven't had any luck with any of them with my small fonts after weeks of wrestling with config files, and here i spill out my frustration :cry: 

the side by side comparison on the first post sums it up for me; Cleartype is just obviously so much better with small fonts. with larger ones, say, over 12, the game is more or less even though. 

i like Hoary more than any other OS i've used, and hope to get this major issue fixed somehow because i am (and i reckon lots of people in here are) very picky when it comes to fonts and look & feel in general. i'm waiting for april 8 now, to totally wipe things off and do a clean install of the final version of Hoary, and try to tackle this issue with a clean start.

just ranting.

---

### Post by Buffalo Soldier on 2005-04-05
I agree with 23meg. It boils down to ones own taste.

Meg, how small are the fonts are we talking about? It would be nice to see how you setup your fonts. A screenshot if there's any.

---

### Post by 23meg on 2005-04-05
i regard 7 to 11 as small.

i've promised not to go back to my existing Hoary installation until April 8, and that will be to note down the latest state of everything directly and indirectly font-related before i reformat my linux partitions and do a clean install of Hoary's final version. that state, in fact, is so messed up after lots of tweaking; i've done things instructed by how-to guides, by experienced people i've met here and on irc, documented in wiki's and other online documentation, etc. in short, so many tweaks that i'm sure some of these are incompatible between themselves and are causing further trouble. 

so, long story short, i'm not going back to Hoary even to take a screenshot :) it's got on my nerves too much recently and that's just not healthy. i'll report back once i've reinstalled everything.

---

### Post by 23meg on 2005-04-05
(i'm so filled up on this; i can't help but keep ranting..)

[one of the articles](http://avi.alkalay.net/linux/docs/font-howto/Font.html) that deelerious has linked to in the first post on this thread says that many recent Linux distros come with versions of the freetype library with Bytecode Interpreter support disabled due to legal issues with Apple, and for best results one needs to update freetype to the latest version with BCI enabled.

what version of freetype do we have on Hoary right now? is it BCI-enabled? does choosing the Bytecode Interpreter option in fontconfig actually employ FreeType's BCI? (i doubt it)

i've tried to follow the instructions on  [this detailed guide to anti-aliasing](http://gnomesupport.org/forums/viewtopic.php?t=51&highlight=font+antialiased) on the gnomesupport forums, and if i'm not getting things totally wrong the author there instructs that we need to actually rebuild Gnome and freetype with BCI support. quite an effort, and honestly i've not survived that guide, but there are people who report success with it.

my point is that, if we already don't, we need to have the latest freetype built for Ubuntu with BCI support, or clear instructions on how to build it for Hoary! i haven't come across any .deb packages so far. i'd appreciate any info on this issue.

---

### Post by remmelt on 2005-04-06
The msttcorefonts package is in multiverse. I am a little worried about putting multiverse in my sources.list, since I broke my system a couple of times with backports and stuff like that.

Can I just install msttcorefonts from multi or does it need all kinds of dependencies?

In general my fonts don't look bad at all, except on this forum... Ain't it a bummer. The Ubuntu Guide site looks perfect, but that one specifies Bitstream Vera in its stylesheet. I have told firefox to use Bitstream, but it doesn't seem to work on the forums.

Also, I'm running fluxbox instead of gnome, and liking it a lot. Altough I can start the gnome-font-config tool, I am not sure if it affects my desktop at all, probably not. Well, more digging to do!

---

### Post by remmelt on 2005-04-06
OK, do first, ask questions later. I installed the msttcorefonts pack from multiverse and it just needs cabextract. Which is fine by me.

After telling Firefox to use Arial instead of Bitstream Vera, even this forum looks nice! Hooray! A little fuzzy, so I might need to adjust the AA a bit, but that's it.

Thanks!

---

### Post by J. S. Jackson on 2005-04-06
Some folks need their glasses checked?   :shock: 

I love gnu/linux, and I love Ubuntu, but I'm not going to lie and pretend that Bitstream Vera Sans is better than Verdana and Tahoma.  It's just not.  As 23meg pointed out, the difference becomes very obvious at small sizes.  Crank Verdana and Bitstream down to 8 pts and compare for yourself.

A lot of sloppiness is hidden by anti-aliasing, but I, personally, cannot stand blurry text.  Sadly the only way to make Bitstream look decent is by anti-aliasing it all to hell.

Those MS fonts are widely regarded as the best in the world, just because MS happens to own them doesn't mean they suck.  It just means they paid for them.  If Bill Gates buys the Mona Lisa, will that suck too?  Do all the Beatles songs that Michael Jackson bought suck too?  :)

---

### Post by bcorcoran on 2005-04-09
[QUOTE=J. S. Jackson]Some folks need their glasses checked?   :shock: 

I love gnu/linux, and I love Ubuntu, but I'm not going to lie and pretend that Bitstream Vera Sans is better than Verdana and Tahoma.  It's just not.  As 23meg pointed out, the difference becomes very obvious at small sizes.  Crank Verdana and Bitstream down to 8 pts and compare for yourself.

A lot of sloppiness is hidden by anti-aliasing, but I, personally, cannot stand blurry text.  Sadly the only way to make Bitstream look decent is by anti-aliasing it all to hell.

Those MS fonts are widely regarded as the best in the world, just because MS happens to own them doesn't mean they suck.  It just means they paid for them.  If Bill Gates buys the Mona Lisa, will that suck too?  Do all the Beatles songs that Michael Jackson bought suck too?  :)[/QUOTE]

Excellent point. I think people instantly regard anything associated with Microsoft as "their crap" without even recognizing what the actual case is. Linux, in its most basic sense, is FREE, and so are all the programs that **come** with it. Just because they're free doesn't necessarily mean they suck, but typography professionals did design the ones Microsoft bought, and that's something the Linux community doesn't have by default. I'm sure if Arial/Tahoma/etc were freely licensed fonts, then Linux would have started using them a long time ago. But they aren't, so Linux doesn't have them by default.

 I think we're fortunate enough, however, to have truetype support in Linux as it is. Think about if there was no way to even use these fonts? I doubt many of the people here would want to use linux having it look ugly to them --  I know I wouldn't.

I'd rather not be flamed for this post, but I think those of you totally against the FONTS associated with Windows/Microsoft should re-evaluate your opinion on where the fonts' origins are, because Microsoft *did not make them*. 

That's just my two cents.

---

### Post by 23meg on 2005-04-09
a side by side comparison of how linux (with aa) and windows (with cleartype) render Verdana 8pt at 72dpi leaves me with a lot of disappointment. i'm still curious as to whether we have freetype's bytecode interpreter support enabled in ubuntu, and if not, whether enabling it will improve things (see my post above). this forum (customization tips & tricks) is not the place to ask questions though, and this deserves a thread of its own, so once i do my clean reinstall of hoary and get the basics right, i'll post one.

---

### Post by donar73 on 2005-04-09
[QUOTE=23meg]a side by side comparison of how linux (with aa) and windows (with cleartype) render Verdana 8pt at 72dpi leaves me with a lot of disappointment. i'm still curious as to whether we have freetype's bytecode interpreter support enabled in ubuntu, and if not, whether enabling it will improve things (see my post above). this forum (customization tips & tricks) is not the place to ask questions though, and this deserves a thread of its own, so once i do my clean reinstall of hoary and get the basics right, i'll post one.[/QUOTE]

Try "sudo dpkg-reconfigure fontconfig". It will ask you for the Font-Rendering-Method: - **Bytecode-Interpreter** (for CRT's), Autohinting (for TFT's) and a third choice (think it was AntiAliasing)

Here's a Screenshot of the current posting with the Bytecode-Interpreter enabled (in my opinion it's a **great** improvement on a CRT!):
[[IMG]http://img209.exs.cx/img209/1958/bildschirmfoto7wi.th.png[/IMG]](http://img209.exs.cx/my.php?loc=img209&image=bildschirmfoto7wi.png)

Btw, i followed this guide to configure the fontrendering.

---

### Post by 23meg on 2005-04-09
i know about fontconfig but as i've stated before i'm not sure that its bytecode interpreter option has anything to do with the bytecode interpreter support in freetype.

---

### Post by piedamaro on 2005-04-09
Antialias doesn't make a font good ;)

---

### Post by donar73 on 2005-04-09
I'm quite sure it's the same thing.  :wink: 
Before installing Hoary I played around with Suse 9.2 in which the Bytecode-Interpreter is disabled by default. So I had to rebuild freetype2 with an enabled B-I (by editing the SPEC-file) and the result looked exactly like Hoary with the B-I enabled via fontconfig.

---

### Post by 23meg on 2005-04-09
that furthers my disappointment...

---

### Post by wordsmith on 2005-04-10
I tried this procedure and I must have messed up the math, because when I reboot i get "gedit:6435 Gtk-warning:cannot open display." can you tell me how to reset my parameters from command line or whatever so that I can get back to a functional ubuntu. Thanks, newbie here.

---

### Post by Ty1er Leeds on 2005-04-11
I did this and I was astounded by the difference in the fonts. I didn't enable the Bytecode interpreter since I use a flat-panel, but damn my fonts look sharp now.  I spend weeks in fedora trying to get my font rendering nicely.  

I'm super pleased.. thanks guys!

---

### Post by juxmw on 2005-04-13
Hi

What about Laptop Resoltion - I have here a Acer Notebook 15.1" and a Pixelresolution of 1400x1050. How to calculate this DisplaySize? I assume that my dpi is higher - isnt it ?

Jux

---

### Post by juxmw on 2005-04-13
Ok. It's me again. I ve measured my Display (measuring tape) and it's 305x230. I ve added this to my xorg and xpdyinfo now says ```
resolution:    116x115 dots per inch
```
Fonts look good, but HUGE !
I'm not sure if this is the correct way to adjust my resolution ???

---

### Post by thinusp on 2005-04-14
Correct me if i'm wrong, but I think the displaysize sould be set to your physical screen dimensions.

I've got mine set to 306x230, resolution of 1600x1200 gives me a 132x132dpi. Setting gnome's font dpi to 96dpi works well.

Just wondering ;)

cheers
T

---

### Post by Roman2K on 2005-04-16
Perfect HowTo, **thank you** a lot !

---

### Post by Graben on 2005-04-16
Wow, I was really doubtful about this and figured my fonts were great.  Was I ever wrong, you can't realize how fuzzy the fonts are until you do this.  I now use 10 point fonts instead of 12 in firefox  because they are actually legible! I do have to add one point, times new roman is the ugliest font i've ever seen. I much prefer bitstream vera sans mono

Edit: Okay I've come to the conclusion that the bitstream all look better to my eyes, that being said I am still disabling hinting at resolutions below 12 point.  This is actually a bigger improvement for crappier fonts.  My reading up on the interpreter states that hinting does not look good on smaller fonts that do not have the information enclosed in them, and that most **DO NOT** have it.

---

### Post by J. S. Jackson on 2005-04-17
[QUOTE=Graben]Wow, I was really doubtful about this and figured my fonts were great.  Was I ever wrong, you can't realize how fuzzy the fonts are until you do this.  I now use 10 point fonts instead of 12 in firefox  because they are actually legible! I do have to add one point, times new roman is the ugliest font i've ever seen. I much prefer bitstream vera sans mono

Edit: Okay I've come to the conclusion that the bitstream all look better to my eyes, that being said I am still disabling hinting at resolutions below 12 point.  This is actually a bigger improvement for crappier fonts.  My reading up on the interpreter states that hinting does not look good on smaller fonts that do not have the information enclosed in them, and that most **DO NOT** have it.[/QUOTE]
Most serif fonts (e.g. times new roman) do not look good on a computer display.  They are more appropriate for printing.  Sans serif fonts always look better on a monitor.

In my opinion, Verdana is probably the best font at small sizes, on a computer monitor.  It was designed for that exact purpose.

---

### Post by 23meg on 2005-04-17
right, but linux just won't render anti-aliased Verdana at smaller than 11 pixels size properly. in fact anything below 11 pixels looks so bad, and using anything bigger than 11 defeats the whole purpose of using a high resolution display.

---

### Post by 23meg on 2005-04-28
i've found a screenshot that **exactly** illustrates the way i want my fonts. it's nice seeing that this *can* somehow be accomplished in linux! (sad that it's a Gentoo screenshot  :? )

here we go: 

[http://gnome-look.org/content/preview.php?preview=3&id=22989&file1=22989-1.png&file2=22989-2.png&file3=22989-3.png&name=gPerfection](http://gnome-look.org/content/preview.php?preview=3&id=22989&file1=22989-1.png&file2=22989-2.png&file3=22989-3.png&name=gPerfection)

needless to say, i'll very much appreciate any hints to get such small fonts looking so good in Ubuntu.

---

### Post by addikt on 2005-04-29
ok used this guide for my LCD display and the fonts, although they look similar to clear type on xp, are just too fuzy to be called good... infact, I liked the default ubuntu font rendering compared to this fuzziness ... is there a way I can fix this problem or a way to go back to the original font setup I had with Ubuntu Hoary ? this guide should really have a way of undoing the operations ...

---

### Post by 23meg on 2005-04-29
you should back up the originals every time you make important changes to your config files, and take notes of each action, so that you can undo it if needed.

in my first crusade of applying every tweak i saw on every forum on top of every other one in the hope of getting my fonts the way i've shown on my last post (and i still haven't!), i messed things up so bad that a reinstall was the easiest way to fix things. sorry for you if this is your situation as well  :? :(

---

### Post by addikt on 2005-04-29
actually I was able to undo the changes myself ... I'm lazy so I just wanted a quick fix but changing things back to what they were wasn't difficult .. however, I am very dissappointed. This is the 4th or 5th guide I have tried hoping to make my fonts look better but none of them have worked out for me. It apparantly works for some people but doesn't for me (and no my eyes aren't screwed up and I followed the steps properly .. I don't wear glasses) ... so I'm gona have to go back to windows xp wth cleartype ... it's just not worth screwing up my eyes over Ubuntu's fonts even though they are a heck lot better than most linux distros out of the box, not to mention Ubuntu's awesome speed, stability and ease of use ... but if I can't read things easily then it's useless ... feels like shit because Ubuntu is everything I want in an operating system except for the damn fonts....

---

### Post by 23meg on 2005-04-29
i hear you. did you look at the screenshot i linked above? liked it?

---

### Post by jodef on 2005-04-30
I must say this little discussion was interesting and informative I never realised recent versions of linux had font problems. I remeber about 3 or 4 years ago I stopped used linux because of horrible fonts/font rendering but up to a year ago when I started back using linux I've had no problems whatsoever. I have never had to adjust a single thing in the over 30 or 40 installs I've done, save maybe screen resolution.

I can however understand how pissed one can get with problematic fonts....

---

### Post by yuk on 2005-04-30
[QUOTE=23meg]i've found a screenshot that **exactly** illustrates the way i want my fonts. [...]

[http://gnome-look.org/content/preview.php?preview=3&id=22989&file1=22989-1.png&file2=22989-2.png&file3=22989-3.png&name=gPerfection](http://gnome-look.org/content/preview.php?preview=3&id=22989&file1=22989-1.png&file2=22989-2.png&file3=22989-3.png&name=gPerfection) [...][/QUOTE]
The creator of gPerfection theme is using:
bitstream vera sans
size=10
font rendering=subpixel smoothing (LCDs)
resolution=72 dpi
smoothing=subpixel
hinting=full
pixel order=RGB
([http://gnome-look.org/content/show.php?content=22989](http://gnome-look.org/content/show.php?content=22989))
but I don't know if it ll be so good in Ubuntu. :)

---

### Post by 23meg on 2005-04-30
i know, it's *me* who asked him there :smile: 

and believe it or not, everything looks exactly like on that screenshot on my desktop now. i've been so obsessed with Verdana and Tahoma, believed so blindly in their "perfect hinting" and "great on-screen looks" that i've completely ignored the wonders of Bitstream Sans Vera. 

for some reason it seems the Bitstream fonts  are rendered much better in Linux than Verdana (and others). maybe their custom hinting is handled better by the bytecode interpreter? and that of Verdana is handled better by Cleartype? perhaps. if you have the time and patience, get a screenshot of Verdana 10pt in 96dpi under both Windows xp and Ubuntu in the same resolution; you'll notice that you almost have two completely different fonts. and subpixel smoothing works much better with Bitstream Sans Vera than the Linux-Verdana.

---

### Post by 23meg on 2005-04-30
[QUOTE=yuk]The creator of gPerfection theme is using:
bitstream vera sans
size=10
font rendering=subpixel smoothing (LCDs)
resolution=72 dpi
smoothing=subpixel
hinting=full
pixel order=RGB
([http://gnome-look.org/content/show.php?content=22989](http://gnome-look.org/content/show.php?content=22989))
but I don't know if it ll be so good in Ubuntu. :)[/QUOTE]

i know, it's me who asked him there :) and it's exactly as good in Ubuntu!

and believe it or not, everything looks exactly like on that screenshot on my desktop now. i've been so obsessed with Verdana and Tahoma, believed so blindly in their "perfect hinting" and "great on-screen looks" that i've completely ignored the wonders of Bitstream Vera Sans.

for some reason it seems the Bitstream fonts are rendered much better in Linux than Verdana (and others). maybe their custom hinting is handled better by the bytecode interpreter? and that of Verdana is handled better by Cleartype? perhaps. if you have the time and patience, get a screenshot of Verdana 10pt in 96dpi under both Windows xp and Ubuntu in the same screen resolution; you'll notice that you almost have two completely different fonts. and subpixel smoothing works much better with Bitstream Vera Sans than the Linux-Verdana.
__________________

---

### Post by Czak on 2005-05-09
Hi! Thanks for this very good HOWTO! I still have a problem with GTK1 apps though:
[IMG]http://beta.mini.pw.edu.pl/~adamczakl/uglygtk.png[/IMG] 
In GTK2 apps (firefox, gnome-terminal), the font looks fine, but in XMMS it's jagged. I have this in my .gtkrc.mine:
```

style "user-font"
{
  fontset="-microsoft-tahoma-medium-r-normal-*-11-*-*-*-p-*-*"
}
widget_class "*" style "user-font"

```
I know it reads from this file, because I can change the font size here. Another strange thing is that the font size in Gnome is 8, but it's 11 for GTK1 apps (and they're equally large). Why is that?
What should I do to have GTK1 apps render fonts properly?
Thanks in advance.

---

### Post by kellie on 2005-05-10
sigh.

ok. pulled the tahoma .ttf fonts off my windows harddrive. am trying to copy to ~/.fonts and they will not go!

any ideas?

using:

sudo cp tahoma.ttf ~/.fonts

right?

thanks in advance....


kellie

 ](*,)

---

### Post by nocturn on 2005-05-10
[QUOTE=kellie]sigh.

ok. pulled the tahoma .ttf fonts off my windows harddrive. am trying to copy to ~/.fonts and they will not go!

any ideas?

using:

sudo cp tahoma.ttf ~/.fonts

right?

thanks in advance....


kellie

 ](*,)[/QUOTE]


Yes.  Where you logged in as a user (not root)?
If so, you shouldn't have used sudo, because now the file in you font directory is owned by root.

The easiest way is to put the font systemwide,
sudo cp tahoma.ttf /usr/share/fonts/[somelocation]

Replace [somelocation] with a suitable directory below fonts.

---

### Post by angrykeyboarder on 2005-05-10
[QUOTE=Czak]Hi! Thanks for this very good HOWTO! I still have a problem with GTK1 apps though:
[img]http://beta.mini.pw.edu.pl/%7Eadamczakl/uglygtk.png[/img] 
In GTK2 apps (firefox, gnome-terminal), the font looks fine, but in XMMS it's jagged. I have this in my .gtkrc.mine:
```

style "user-font"
{
  fontset="-microsoft-tahoma-medium-r-normal-*-11-*-*-*-p-*-*"
}
widget_class "*" style "user-font"

```
I know it reads from this file, because I can change the font size here. Another strange thing is that the font size in Gnome is 8, but it's 11 for GTK1 apps (and they're equally large). Why is that?
What should I do to have GTK1 apps render fonts properly?
Thanks in advance.[/QUOTE]

GTK1 is the root of all evil, hence GTK2. ;-)

If you ***insist*** on your software resembling a microscopic version of a real live stereo amplifier, then I'd recommend[ Beep Media Player (BMP)]("http://packages.ubuntu.com/hoary/sound/beep-media-player") (a GTK2 app).  It's brought to you from the folks who left the XMMS camp cuz XMMS was determined to stay behind the times.

Of course it too, looks like a silly microscopic version of a stereo amplififier....

Scott

(Rhythmbox, amaroK, iTunes, WMP user......)

---

### Post by kellie on 2005-05-10
[QUOTE=nocturn]Yes.  Where you logged in as a user (not root)?
If so, you shouldn't have used sudo, because now the file in you font directory is owned by root.

The easiest way is to put the font systemwide,
sudo cp tahoma.ttf /usr/share/fonts/[somelocation]

Replace [somelocation] with a suitable directory below fonts.[/QUOTE]
 ah thank you! 

still fairly new to the linux world.

worked like a charm.

fonts look awesome.

LOVING my ubunto...


kellie

---

### Post by Segovia on 2005-05-10
[QUOTE=angrykeyboarder]If you ***insist*** on your software resembling a microscopic version of a real live stereo amplifier[/QUOTE]
LOL.  So true...  The fonts are about .01 mm high.

All joking aside, it's the reason I don't use that damn thing.  I run at 1600x1200, and it's nearly impossible to make out any of the fonts/controls unless I really get close and concentrate.

---

### Post by Czak on 2005-05-11
[QUOTE=angrykeyboarder]
If you ***insist*** on your software resembling a microscopic version of a real live stereo amplifier, then I'd recommend[ Beep Media Player (BMP)]("http://packages.ubuntu.com/hoary/sound/beep-media-player") (a GTK2 app).[/QUOTE]

Actually, I'm just used to XMMS and never considered a change. I will look into the programs you mentioned. On the other hand, I remember BMP as being quite unstable. Is it still?

**Anyway**, that doesn't solve the problems with my fonts. Could someone please tell me - do you also have this problem?

---

### Post by jebe on 2005-05-15
interesting link: 

[http://www.objectsspace.com/encyclopedia/index.php/Optimal_Use_of_Fonts_on_Linux](http://www.objectsspace.com/encyclopedia/index.php/Optimal_Use_of_Fonts_on_Linux)

btw: somebody played with recompiling freetype to enable hinting ?

---

### Post by 23meg on 2005-05-15
[QUOTE=jebe]
btw: somebody played with recompiling freetype to enable hinting ?[/QUOTE]

there's still no official word on whether freetype's bytecode interpreter comes enabled in Hoary. plus, i'd like to know for certain whether my assumption that freetype's bytecode interpreter support isn't the same thing as the "bytecode interpreter" option in fontconfig and that it's the piece of code that handles subpixel hinting for lcd screens and autohinting as well is true.

---

### Post by jebe on 2005-05-15
[QUOTE=23meg]there's still no official word on whether freetype's bytecode interpreter comes enabled in Hoary. plus, i'd like to know for certain whether my assumption that freetype's bytecode interpreter support isn't the same thing as the "bytecode interpreter" option in fontconfig and that it's the piece of code that handles subpixel hinting for lcd screens and autohinting as well is true.[/QUOTE]

i think they use a free bytecode inter.

see:

# Turn on bytecode interpreter, but use unpatented hinting
+	# and forces its use.  Many thanks to Graham Asher for this great
+	# feature to circumvent bad Apple's patent.  :-p

[http://archive.ubuntu.com/ubuntu/pool/main/f/freetype/freetype_2.1.7-2.3.diff.gz](http://archive.ubuntu.com/ubuntu/pool/main/f/freetype/freetype_2.1.7-2.3.diff.gz)

---

### Post by CouchMaster on 2005-05-20
You can always install Windows fonts, and here's how.
This is for the KDE desktop only, and works for any linux distro that uses it.

Go to a windows computer and make a folder called 'TrueType'.
Now open the font folder in the control panel.
High-light all of the fonts you want (I did them all) and click 'edit' then 'copy'. This copies the fonts to the clipboard.
Now go to the folder you created and paste them there.
Now burn them to a CD-R.

Now go to your linux distro and fireup KDE.
Copy the TrueType fonts to your home folder.
Now start the 'control center' > 'system administration' and select 'font installer' - you might have to click the Administrator Mode button and enter the root PW.
Now click 'add fonts' - browse to the font folder you just copied to home and select the fonts you want to install - then click OK - thats it.
Now you have tons of new fonts to work with.
In Konqueror I changed them to
Sans Serif
Courier New
Times New Roman
Arial
Arial
Arial
ISO 8859-1
Smooth as a babies behind!!!

---

### Post by Segovia on 2005-05-20
[QUOTE=CouchMaster]You can always install Windows fonts, and here's how.
This is for the KDE desktop only, and works for any linux distro that uses it.

Go to a windows computer and make a folder called 'TrueType'.
Now open the font folder in the control panel.
High-light all of the fonts you want (I did them all) and click 'edit' then 'copy'. This copies the fonts to the clipboard.
Now go to the folder you created and paste them there.
Now burn them to a CD-R.

Now go to your linux distro and fireup KDE.
Copy the TrueType fonts to your home folder.
Now start the 'control center' > 'system administration' and select 'font installer' - you might have to click the Administrator Mode button and enter the root PW.
Now click 'add fonts' - browse to the font folder you just copied to home and select the fonts you want to install - then click OK - thats it.
Now you have tons of new fonts to work with.
In Konqueror I changed them to
Sans Serif
Courier New
Times New Roman
Arial
Arial
Arial
ISO 8859-1
Smooth as a babies behind!!![/QUOTE]
Or you could just "sudo apt-get install msttcorefonts"    ;-)

The problem that 23meg is talking about is that when not anti-aliased (read: blurry as hell) the freefont module does not seem to be able to hint the MS fonts correctly.  And the question is whether or not the byte-code interpreter is *actually* turned on or not.  Yes you can select it, but it's not clear to anyone if it's actually enabled?

---

### Post by dikki on 2005-05-30
This is SOOOOO great! Thanks for the guide!

---

### Post by acrylamid on 2005-06-18
Okay, I'm already stuck :)

I skipped this part:
"Either restart X or reboot, after which verify the dpi setting is correct:
Code:

xdpyinfo | grep dimensions 
xdpyinfo | grep resolution"

Because I cant find it, and I not sure what do to. Maybe it isn't so important.


So I have installed the "msttcorefonts package" with the nice Synaptic Package Manager. Then i should copy two fonts.
"Copy tahomabd.ttf and tahoma.ttf into /usr/share/fonts/truetype/custom/"
But where do I find there fonts, I searched after the file and I can't find it. In the terminal I stand in my home-directory and I believe i must stand where the file is. (Just as in the old DOS-days)

So where does Ubuntu put my fonts?



A question in advance.
Step 3.
"Select Bytecode interpreter or Subpixel rendering"
What are the differents?

---

### Post by Athropos on 2005-06-25
Many thanks for this tutorial!
I'm trying to move from Windows to Ubuntu, and fonts were a real problem for me. Many webpages use small font and I found them difficult to read, now I have a prefect rendering (IMO). Thanks!

---

### Post by Fexx on 2005-06-25
Ive done what you listed on page 1 and my front still look quite bad.

Here are 2 screenshots. Looks nothing like yours.

Edit: nm, fixed it. Your a god, thanks for the tutorial.

---

### Post by hshin on 2005-07-11
Has anyone even tried to turn off hinting without having to go through all that madness of setting your Ubuntu to some Windows DPI? I think some people here are going to trip.

Right now I'm investigating the possibility of doing the same to Windows Xp. Not having any luck.

---

### Post by hshin on 2005-07-11
All this just so your Ubuntu can look like Windows Xp? How about making Ubuntu look like OS X by simply turning off hinting?

---

### Post by Segovia on 2005-07-11
[QUOTE=hshin]All this just so your Ubuntu can look like Windows Xp? How about making Ubuntu look like OS X by simply turning off hinting?[/QUOTE]
I suppose everyone has their own personal taste in regard to fonts.

Personally I don't like the look of fonts in OS-X.  The AA is heavy and the fonts look very "thick" and fuzzy - like they are **bold** all the time.

Windows XP has, IMO, the best looking font rendering.  Very thin lines, sharp, etc.  I think that's why many people wish to emulate it in Linux.

---

### Post by Footer on 2005-07-12
OK.  I followed this "how to" and it's OK but I'm not as satisfied as I thought I would be with the end result.  Unfortunately, I'm not sure how to go back to the default settings.  Anyone have any ideas how to do that?  If nothing else, perhaps the default settings in FireFox when the browser is first installed?  I used the example "Fonts & Colors" in FF given in the how to which is exactly like FF in Windows but I want to go back to default!

Any help, greatly appreciated!

Thanks.

---

### Post by Footer on 2005-07-12
[QUOTE=Segovia]I suppose everyone has their own personal taste in regard to fonts.

Personally I don't like the look of fonts in OS-X.  The AA is heavy and the fonts look very "thick" and fuzzy - like they are **bold** all the time.

Windows XP has, IMO, the best looking font rendering.  Very thin lines, sharp, etc.  I think that's why many people wish to emulate it in Linux.[/QUOTE]

I agree 100%!  But the question is, how?  This how to guide didn't do it for me.

:|

---

### Post by rubengs on 2005-07-19
An aditional improvement: 

There is a distro called Munjoy Linux, this guy created special fonts for an integrated distro with a "unified look-and-feel" the fonts are "optimized for rendering with hinting disabled, but they may work fine with any configuration". The fonts are GPL so can be used in any distro, no need to use proprietary fonts any more. 

My desktop looks really good now with the howto and this fonts, the link to download the tarball with the fonts is in this link: 

[http://www.munjoylinux.org/source/munjoyfonts.tar.gz](http://www.munjoylinux.org/source/munjoyfonts.tar.gz)

The distro page is: [MunjoyLinux.org](http://www.munjoylinux.org/)

---

### Post by zafar on 2005-07-22
[QUOTE=Footer]I agree 100%!  But the question is, how?  This how to guide didn't do it for me.

:|[/QUOTE]

When using the msft fonts, i set gnome to use tahoma with sub pixel rendering, and medium auto hinting and that makes it look VERY similiar to windows xp rendering on my samsung lcd.

---

### Post by hshin on 2005-07-22
[QUOTE=Segovia]I suppose everyone has their own personal taste in regard to fonts.[/QUOTE]

I guess you're right. However my eyes always hurt from prolonged reading on Xp. I had to bump the DPI up from 96 to 120 just for that.

Has it ever occured to you that, perhaps the fonts are smaller on Windows because it was originally designed for 640x480 and 800x600 displays?

---

### Post by flargen on 2005-07-29
Hi

First of all, thanks for the guide. At first it didn't work, but i fixed it.
The reason it didn't work (i think) - this may be the same for some others out there - was because I followed the instructions on the "Unofficial Ubuntu 5.04 Starter Guide" ([http://ubuntuguide.org](http://ubuntuguide.org)) on how to add fonts to the system, which tells you to enable the freetype autohinter module. The method the guide used was to edit the config file by hand. I don't know for sure, but i am guessing that this is what was stopping the options in sudo "dpkg-reconfigure fontconfig" from having any effect. I just replaced the edited config file with the original and everything worked fine. I hope this helps someone!

Thanks again for the great guide.

---

### Post by navilon on 2005-07-30
[QUOTE=basse1989]Are you guys crazy? Why don't you install windows instead? Who would want their ubuntu installation to look like windows?

I think ubuntu works GREAT as it is (read my signature).[/QUOTE]

this is more of a designers issue, the default fonts that come with most linux distros are sub-par

---

### Post by c4pp4 on 2005-08-08
> **angrykeyboarder]GTK1 is the root of all evil, hence GTK2.  said:**
>  Beep Media Player (BMP)[/url] (a GTK2 app).

super tip, thanks! ...and it supports windows winamp skins :p

and mainly thanks to **deelerious** for this howto!!!!

btw:
for e.g. k3b appearance type command - "kcontrol"
for e.g. qtparted - "gksudo kcontrol"

---

### Post by BIGtrouble77 on 2005-09-22
I got one sort of minor issue with this HOWTO... When I launch apps as root the .fonts.conf settings don't apply.  I copied over my .fonts.conf file to /root/, restarted gnome and noticed no noticable difference.  I'm using the second example that disables anitaliasing completely for smaller fonts.

My main work environment is in eclipse which I have to run as root (I'm too lazy to set up proper group permissions).  I use a very small font size so it's easier on my eyes if antialiasing is turned off.  

Any ideas on how to get my .fonts.conf to apply to apps launched as root?

TIA,
-bt

btw, this howto works perfectly, otherwise.  O:)

---

### Post by hw-tph on 2005-10-02
[QUOTE=BIGtrouble77]Any ideas on how to get my .fonts.conf to apply to apps launched as root?[/QUOTE]
Just edit /etc/fonts/local.conf instead of your personal ~/.fonts.conf.
Håkan

---

### Post by leetsauce on 2005-10-11
Hello.

I've followed the guide step by step. My results are pretty good. However, I have noticed that in many areas my font seems like it's squishing together as you can see in the attached screenshot.

Help please.
Thanks in advance,
leetsauce

---

### Post by bluemuffin on 2005-10-11
I'm new to linux and ubuntu. I don't know the difference between gnome and kde. I didn't even know that my ubuntu is breezy until yesterday. 

I don't care if ubuntu does not look like windows. I decided to use it and i did not expect it to be a clone of windows but it sure would be nice to have the varied selection of fonts that i enjoyed in windows, especially for my graphic works. Is there a way we can add to the current selection that is pre-loaded with ubuntu?

---

### Post by matid on 2005-10-12
[QUOTE=Fexx]Ive done what you listed on page 1 and my front still look quite bad.

Here are 2 screenshots. Looks nothing like yours.

Edit: nm, fixed it. Your a god, thanks for the tutorial.[/QUOTE]
Could you tell us what you did to fix it?

---

### Post by rgrig on 2005-10-12
It looks pretty but... now I get
```
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0xb1ae2ef6, pid=16854, tid=2976660400
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_05-b05 mixed mode, sharing)
# Problematic frame:
# C  [libfontmanager.so+0x31ef6]
```
when running javaws applications. Some of them work up to a point and, before they crash, give this warning:
```
usr/share/themes/Clearlooks/gtk-2.0/gtkrc:49: Engine "clearlooks" is unsupported, ignoring
```
I'm not sure if this warning was also present before (since I never bothered to  trace/log the execution of javaws applications).

Any idea what exactly should I roll back?

---

### Post by rgrig on 2005-10-13
It [seems]("http://forums.topcoder.com/?module=Thread&threadID=507619") it is a bug in java 1.5.

---

### Post by angrykeyboarder on 2005-10-14
.

---

### Post by nicolas314 on 2005-10-14
I used this HOWTO with great success on Ubuntu 5.04. Never had such
clear and crispy fonts on Linux! I cannot thank the author enough for
providing such a good document.

... Until I upgraded to Breezy. Tahoma is degraded just enough to make
it hard to read after 5 minutes, Firefox renders unreadable pages, fixed
fonts look Ok but most have changed sizes (I must now use 12 where
I used 10 or sth equivalent). The best I could do so far is delete
/etc/fonts/local.conf and set the screen resolution in Gnome fonts to 92dpi
(xorg being configured for 96 as described in the Howto).

Now it is not so bad but still hard for the eyes. Pity.

---

### Post by jamesford on 2005-10-14
i just installed tahoma on a fresh breezy following this guide. and all works just well, however i skipped step 1 like i always do

for some reason the bitstream vera sans fonts became f*cked up after doing this, but the font called just 'sans' (which i think must be identical to bitstram vera sans) work like before..strange

---

### Post by zerooo on 2005-10-16
Thanks dude! I did everything i wanted with fonts on this "how to" on a fresh breezy install and it works perfect. None bugs, gliches. So thanks again for this wonderful guide.

---

### Post by zerwas on 2005-10-16
I also have to thank you for this :).

It works good in Breezy!

---

### Post by c4pp4 on 2005-10-20
How to turn anti-aliasing off for msttcorefonts **only**?

---

### Post by hw-tph on 2005-10-20
[QUOTE=c4pp4]How to turn anti-aliasing off for msttcorefonts **only**?[/QUOTE]

Set up that in your ~/.fonts.conf. See **fonts-conf(5)**.


Håkan

---

### Post by c4pp4 on 2005-10-21
[QUOTE=hw-tph]Set up that in your ~/.fonts.conf. See **fonts-conf(5)**.


Håkan[/QUOTE]

man fonts-conf :idea:

---

### Post by akb on 2005-10-22
hi,

i followed this guide, and it helped a bit. but the fonts are looking still a bit "dirty" after all... and i dont know how to get this away.

is there anyone running a similar system with fonts looking really good? can you recommend settings for my system?

i am running breezy badger on an acer notebook. my screen is 15,4" @ 1280x800, lcd of course. measured about ~329mm X ~270mm (something like that).

especially in gnome (well, all gtk apps) it looks _really_ dirty. within kde its quite ok, but also not perfect.

can you tell me the best settings? i am using the msttcore fonts, but mainly for web pages. its not a must have on the desktop itself, bitstream vera sans imho looks good too.

---

### Post by JOKe on 2005-10-26
i want ANTIALIASING for EVERYTHINK i want cleartype look forall fonts expecialy for helvetica ? how can i do it i see the ubuntu screenshot in the first post and his file,edit,view are antialiased with helvetica/tahoma how can i do it ? 

im with 15' LCD display and not antialiasign fonts suxs 
resolution 1024x768

---

### Post by Remmelas on 2005-10-28
Just a note, these instructions still give great results in Breezy

---

### Post by yelatia on 2005-12-18
Hi,
thanks for the how to. My eyes are less tired than before. the screen now is simply awesome. Yet, I still have one problem.
I follow exactly each line of the code, but when I came to this part:

[INDENT]Code:[/INDENT]

[INDENT]sudo dpkg-reconfigure fontconfig[/INDENT]

[INDENT]Select Bytecode interpreter or Subpixel rendering[/INDENT]


I got the blue window,( which I miss so much from my last gentoo distro,) but there is no selection for bytecode or subpixel.
anyway I select the default values. Then, I tried to change the fonts from the System->Prefrences->fonts. The problem is whenever I try to select tahoma the application crashs. I reboot the system;the error perssists . However, I was able to change fonts to tahoma from firefox .

Any idea what could be the origine of this error.?

Note ,I'm using Ubuntu breeze 5.10.

Thanks.

---

### Post by John.Michael.Kane on 2005-12-19
has anyone got this to work on a widescreen laptop 1280x800 lcd.. if so please post.

---

### Post by novalis on 2006-02-06
On Kubuntu/KDE it can be necessary to adjust the display to 96 dpi.

To do so,

> sudo nano /etc/kde3/kdm/kdmrc

and add as last line under > [X-:*-Core]

[QUOTE]ServerArgsLocal=-dpi 96

so it looks like

> [X-:*-Core]
AllowNullPasswd=true
AllowShutdown=All
NoPassEnable=false
NoPassUsers=
ServerArgsLocal=-nolisten tcp
ServerCmd=/usr/X11R6/bin/X
ServerArgsLocal=-dpi 96

You can also define standard- and fallback- fonts and fontsizes for KDE here.

After that, restart KDE and enjoy the look. Thanks for this great HowTo!

Greetz,
Nov

---

### Post by steveneddy on 2006-02-11
I would like to have my Windows fonts on Linux becauae I spent years collecting different font styles that I enjoy using when the need arrises. I don't always need or want the Tahoma font all the time and I don't write business only letters in OOo either. I would just like a way in Ubuntu to use my Windows fonts that I have grown fond of using these last few years. 

Don't get me wrong - I love Linux and I think Ubuntu is the future in personal computing - I just want my Windows fonts I worked so hard to collect. I have over 200 different types of fonts for many different needs. 

OK - I'm done. Don't forget to feed the penguins before you go out tonight.

---

### Post by Freddd on 2006-02-14
I can't start Ubuntu after adding this line:
> 
#	DisplaySize	270	203	# 1024x768 96dpi
#	DisplaySize	338	254	# 1280x960 96dpi
	DisplaySize	338	270	 1280x1024 96dpi
#	DisplaySize	370	277	# 1400x1050 96dpi
#	DisplaySize	423	370	# 1600x1400 96dpi

How do I change it back? I get something like can't start X server

---

### Post by Paloseco on 2006-02-20
comment the uncommented line and /etc/init.d/gdm restart

PS: I LOVE how Windows works in the fonts, is really nice. The ubuntu default fonts are really ugly, blurred, some webpages have a very small fonts and other too large, etc. I really wanna see this improved in next ubuntu/kubuntu releases. :KS

---

### Post by pestilence on 2006-02-22
For some strange reason i had to reboot my system for the **DisplaySize** switch to take effect (restarting the X session didn't work).

---

### Post by steveneddy on 2006-03-12
[QUOTE=steveneddy]I would like to have my Windows fonts on Linux becauae I spent years collecting different font styles that I enjoy using when the need arrises. I don't always need or want the Tahoma font all the time and I don't write business only letters in OOo either. I would just like a way in Ubuntu to use my Windows fonts that I have grown fond of using these last few years. 

Don't get me wrong - I love Linux and I think Ubuntu is the future in personal computing - I just want my Windows fonts I worked so hard to collect. I have over 200 different types of fonts for many different needs. 

OK - I'm done. Don't forget to feed the penguins before you go out tonight.[/QUOTE]


EDIT:
I did find out how to get all of my custom Windows fonts in my Ubuntu installation. 

Look here:
[http://www.softwareinreview.com/cms/content/view/32/1/](http://www.softwareinreview.com/cms/content/view/32/1/)


And they look great, BTW. And I now have my favorite Tahoma Font as my system font. Life is good.

---

### Post by StefSOFT on 2006-03-16
I can't get the antialiasing to work. I now have nice clean nonaliased window fonts, also websites look a lot better, but when they use a bigger type (for titles etc.) I see ugly rough corners. In the tutorial they edited the ~/.fonts.conf file, but I don't see aliased rendering for the bigger cases :confused: Where can i edit this?

**Update**: Got the solution from a guy from gathering.tweakers.net

He suggested to paste the following code in /etc/fonts/local.conf. As you can see there are a few differences compared to the xml-code in the how-to provided here.

XML-code tweakers.net:
```

<match target="pattern">
                <test qual="any" name="size" compare="less_eq">
                        <int>12</int>
                </test>
                <edit name="antialias" mode="assign"><bool>false</bool></edit>
        </match>

```

XML-code this how-to thread:
```

<match target="font">
 <test compare="more" name="pixelsize" qual="any">
  <double>0</double>
 </test>
 <test compare="less" name="pixelsize" qual="any">
  <double>15</double>
 </test>
 <edit mode="assign" name="antialias">
  <bool>false</bool>
 </edit>
</match>

```

---

### Post by cerebrix on 2006-03-27
for the life of me i cant get 96x96 dpi

```
christian@ubuntu:~$ xdpyinfo | grep resolution
  resolution:    99x98 dots per inch
christian@ubuntu:~$ xdpyinfo | grep dimensions
  dimensions:    1680x1050 pixels (431x272 millimeters)
```


```
Section "Monitor"
	Identifier	"DELL 2005FPW"
	Option		"DPMS"
	DisplaySize	433	270	# 1680x1050 96dpi
EndSection
```


help me out w/ this one im bangin my head against a wall on this one =p

---

### Post by sstickeler on 2006-04-04
Thanks a lot for this How-to. Followed intusing Dapper and worked great. The default font settings in Ubuntu were giving me a headache!

---

### Post by sstickeler on 2006-04-04
I was having the same problem. I thought I could simply log out and back in again to reset the X server and no matter what I changed the values to in xorg.conf I couldn't get the DPI to change. 

Turns out I had to Ctrl-Alt-Backspace to reset the server. Then I saw things change. If you haven't already give that a shot.

---

### Post by sstickeler on 2006-04-04
[QUOTE=Freddd]I can't start Ubuntu after adding this line:

How do I change it back? I get something like can't start X server[/QUOTE]

You need to put a # before 1280x1024.

---

### Post by jstad on 2006-04-16
I have all the fonts working and Tahoma copied. However I am having one issue. I open the terminal and the fonts look all cramped or rendered very wierd.

Screenshot: [http://www.darksyntax.com/Screenshot.png](http://www.darksyntax.com/Screenshot.png)

If someone can help this it would be fantastic!

---

### Post by jstad on 2006-04-17
Anyone?!

---

### Post by go4fan on 2006-05-11
You've probably figured this one out by now, but just in case, use this:
```

DisplaySize 444 277
```

[QUOTE=cerebrix]for the life of me i cant get 96x96 dpi

```
christian@ubuntu:~$ xdpyinfo | grep resolution
  resolution:    99x98 dots per inch
christian@ubuntu:~$ xdpyinfo | grep dimensions
  dimensions:    1680x1050 pixels (431x272 millimeters)
```


```
Section "Monitor"
	Identifier	"DELL 2005FPW"
	Option		"DPMS"
	DisplaySize	433	270	# 1680x1050 96dpi
EndSection
```


help me out w/ this one im bangin my head against a wall on this one =p[/QUOTE]

---

### Post by Freddd on 2006-05-17
[QUOTE=deelerious]
Step 3. Configure system-wide fontconfig rendering method
```
sudo dpkg-reconfigure fontconfig
``` 
Select Bytecode interpreter or Subpixel rendering
[/QUOTE]
I'm following the guide on the first post of this guide, and I'm trying with tahoma. I get the following questions when I run "sudo dpkg-reconfigure fontconfig":

1. How should fonts be tuned for the screen?
    Native
    Authohinter
    None

2. Enable subpixel rendering of text?
   Automatic
   Always
   Never

3. Enable bitmapped fonts by default?
   yes
   No

What shall I answer on these questions? I have an IBM T41.

---

### Post by Freddd on 2006-05-19
Anyone please?

---

### Post by diegoe on 2006-05-25
If you are using Dapper try my packages here:

[http://ubuntuforums.org/showthread.php?t=182164](http://ubuntuforums.org/showthread.php?t=182164)

---

### Post by calande on 2006-06-10
This works just fine with antialiasing off at small font sizes in all applications, except in Firefox where the fonts are always antialiased. Any idea?

---

### Post by unwoken on 2006-06-14
is there any way to completely undo the installation of this fix so your system is as it was prior to the changes?

i have restored my old .fonts.conf file, but am not sure what else to do.  i am having trouble with some websites (using dapper).

u.

EDIT: Did one of the commands change the default serif on firefox?  because on one site i visit the serif is now extremely difficult to read. 

EDIT: I found my solution.  I just uninstalled the ms fonts through synaptic and firefox shows my selected fonts and not the ms versions... (didn't know it did that).  i now have the fix from this thread on my desktop pc, and no mstt fonts on the laptop!  cheers.

---

### Post by flipkick on 2006-06-14
This thread is still a beauty :cool: 

Thank you for every new beginning and straight font rendering.

---

### Post by lepre on 2006-06-17
it doesn't work for me in gtk (still very bad rendering) and tahoma is not working properly

oh well. i'm using xfce instead of gnome ;)

---

### Post by PedroCC on 2006-06-28
Dude this topic saved my life. Lovya.

---

### Post by calande on 2006-07-02
Can you guys confirm that this doesn't work in Firefox?

[[IMG]http://img244.imageshack.us/img244/7990/capturadatela2jy.th.png[/IMG]](http://img244.imageshack.us/my.php?image=capturadatela2jy.png)

---

### Post by lepre on 2006-07-02
[QUOTE=calande]Can you guys confirm that this doesn't work in Firefox?

[[IMG]http://img244.imageshack.us/img244/7990/capturadatela2jy.th.png[/IMG]](http://img244.imageshack.us/my.php?image=capturadatela2jy.png)[/QUOTE]

have you set up the fonts in firefox preferences?

---

### Post by calande on 2006-07-02
Yes, I have set it to Times New Roman, Arial, and Courier New.

---

### Post by devurandom on 2006-07-03
You guys must be mad.
Why should you want the pixelated, ugly-as-hell non-antialiased Windows-like fonts on a shiny Linux box with all fonts antialiased?
Sigh. I guess Microsoft poisoned people's aesthetic sense. :(

---

### Post by calande on 2006-07-03
Well, at least with the crispy Windows fonts, I can stay more than half an hour in front of my computer :)

The default blurred fonts in Ubuntu hurt my eyes, and they don't look professional at all anyway. Monitors use pixels to show stuff, and if you take advantage of this, you can have something clear to the eyes (clear fonts, clean horizontal line, clean square, etc...).

The MS fonts are among the only ones that are hinted, why shouldn't we take advantage of them? It's so time-consuming to define hints to fonts...

---

### Post by calande on 2006-07-04
Ok, here's an how-to that works fine in Gnome and Opera: [http://digg.com/linux_unix/Display_Microsoft_fonts_in_Unix_like_on_Windows](http://digg.com/linux_unix/Display_Microsoft_fonts_in_Unix_like_on_Windows)

---

### Post by calande on 2006-07-11
Ok, I *finally* found a solution. I updated my XML files, please go ahead and follow the [original tutorial](http://ubuntuforums.org/showthread.php?t=208396) again. Now fonts in Firefox are going to look good, just like in Windows :)

Original thread:
[http://forums.pcbsd.org/viewtopic.php?p=25646](http://forums.pcbsd.org/viewtopic.php?p=25646)

---

### Post by sarman on 2006-08-19
OK, worked now!

---

### Post by DeMagH on 2007-03-06
i can't thank you enough for this awesome guide, believe it or not i was very satisfied with step 1 ALONE, may be because i copied the windows fonts before that from the administration panel.

Anyway, thanks a million

---

### Post by chojin on 2007-03-19
I find it funny that people think linux can do fonts anywhere near close to windows or OSX these days. Don't get me wrong - this is one of the main things keeping me from switching to linux for 100% of my workflow (I work in graphic design and the font rendering just isn't up to par), so I would LOVE for the fonts to be the same, but sorry, even in that screenshot they're completely and utterly miles apart in terms of quality.

Why do people honestly think they're similar?

The bytecode interpreter, when switched on, should, theoretically, produce pixel perfect reproductions of the original fonts. Also, kerning info is in pro fonts but freetype ignores it. There are millions of other things wrong with freetype, should I continue?

Seriously. Stop saying that you can have good fonts on linux, when it really happens, people will think you're crying wolf again.

---

### Post by calande on 2007-03-19
Not even these fonts? :(

[IMG]http://home.comcast.net/~ddamian/ubuntu/howto/firefox_nonaa_ubuntu.png[/IMG]

---

### Post by chojin on 2007-03-20
> **calande said:**
> Not even these fonts? :(

[IMG]http://home.comcast.net/~ddamian/ubuntu/howto/firefox_nonaa_ubuntu.png[/IMG]

Well, those are aliased fonts. I agree the glyphs are ALMOST perfect (look at the 'v' in 'privacy' and 'advanced', the W in 'Web features', the 'x' and 'm' in 'Linux Forums', and these are just bytecode issues - clearly proves many bugs in the BCI).

But... ALIASED FONTS? Maybe in 1998 I might have conceded that yes, this would prove linux fonts weren up to scratch, but this is 2007. Antialiasing is pretty much ubiquitous. As I said, I am a designer, I take fonts seriously - obviously the freetype team either doesn't, either that or people seem to love spreading misinformation.

If you turn on antialiasing, turn off autohinting, and turn on the BCI, the fonts look smushed and WORSE than the autohinter alone. Not only that, you lose the autokern and there are alignment problems all over the place.

It's just not even close to reliable font rendering, please stop making threads claiming 'cleartype-like fonts' or 'osx like font rendering'... it's really not and shows you don't know anything about type. As you have shown even the aliased fonts aren't close to being at production standard. Remember this is microsoft Arial 9pt - pretty much 'the' standard in the aliased font world - it has complete and exhaustive bytecode info, was BUILT for 9pt aliased (read its history on wikipedia), and it is pretty much what the freetype team would have used as a benchmark. Yet it still exhibits errors under the FT BCI. If this one is bad, what about the zillions of other fonts? I apologise for sounding almost aggressively critical, I'm just sick of the false claims.

---

### Post by hugmenot on 2007-03-23
> **chojin said:**
> Seriously. Stop saying that you can have good fonts on linux, when it really happens, people will think you're crying wolf again.

Be prepared to meet the wolf [in your backyard]("http://www.ubuntuforums.org/showthread.php?t=235526") soon.

---

### Post by packjamNL on 2007-04-09
wonderfull fonts now, but my beryl-manager, the window manager will not run on beryl anymore, it chooses Metacity as default, and now the 3D cube doesn' t work, how can I keep running beryl and keep the fonts this way?
I use gnome ofcourse.

---

### Post by calande on 2007-04-09
Try to remove /etc/fonts/local.conf

---

### Post by packjamNL on 2007-04-09
Don' t have any, what I do have is a fonts.conf, and a fonts.dtd, in /etc/fonts
and a $/etc/fonts/conf.d/51-local.conf

Midwhile I reinstall FFawn now and try to do more with the " clean"  font, wich is not standard in FFawn I believe.

---

### Post by pepsi_max2k on 2007-04-20
Thankyou very much :) very clear guide and does exactly what it says on the tin (even in feisty) :D if only they were all like this...

**EDIT:** ohhh spoke too soon... I'm still getting antialiasing on TimesNewRoman fonts in web pages, eg. [http://wordpress.org/](http://wordpress.org/) and [http://tweakhound.com/](http://tweakhound.com/) (though strangely the tnr links on the left of tweakhound aren't aa'd). Any way I can stop this?

**EDIT 2:** Never mind. May have been my fault, may not be, but I had my main firefox font size as 16, so I changed the "15" in ~/fonts.conf to 17 and not only are all the large 16px titles no longer aa'd, the times new roman fonts aren't either. either they were outputting at 16px (didn't look like it) or it's just a nice side effect :)

---

### Post by sparxx on 2007-04-27
Help! Just ran through this tutorial and it was fine for a bit. But then I restarted x server and now none of the windows have title bars (orange one at the top with minimise, close etc). When I open the terminal it just gives me a white box. I even tried installing a different terminal app but still the same thing. Without a terminal I cant get to xorg.conf to fix the problem :(

What can i do?

---

### Post by trmiv on 2007-05-02
I'm trying this in Feisty, but when I do the first part and insert the lines into my xorg.conf, it isn't working.  I uncommented out the 1024x768 line, saved and then restarted X and did that "xdpyinfo | grep resolution" line, but my result is "resolution:    89x92 dots per inch".   Then I tried rebooting to see if that would fix it, but it's still the same. How can I get it to 96x96?

---

### Post by ferossan on 2007-05-06
> **trmiv said:**
> I'm trying this in Feisty, but when I do the first part and insert the lines into my xorg.conf, it isn't working.  I uncommented out the 1024x768 line, saved and then restarted X and did that "xdpyinfo | grep resolution" line, but my result is "resolution:    89x92 dots per inch".   Then I tried rebooting to see if that would fix it, but it's still the same. How can I get it to 96x96?

Just read the previous post #8 in this thread.
( []("http://ubuntuforums.org/showpost.php?p=101269&postcount=8") [http://ubuntuforums.org/showpost.php?p=101269&postcount=8](http://ubuntuforums.org/showpost.php?p=101269&postcount=8) )

---

### Post by trmiv on 2007-05-06
I'm not doing this for a different resolution though.  This is for 1024x768 which was already listed in the original howto.

---

### Post by elnur on 2007-05-30
> **trmiv said:**
> I'm trying this in Feisty, but when I do the first part and insert the lines into my xorg.conf, it isn't working.  I uncommented out the 1024x768 line, saved and then restarted X and did that "xdpyinfo | grep resolution" line, but my result is "resolution:    89x92 dots per inch".   Then I tried rebooting to see if that would fix it, but it's still the same. How can I get it to 96x96?

I got same problem on Feisty, DisplaySize directive has no effect, even if i use CTRL+ALT+backspase. Any thoughts?

---

### Post by elnur on 2007-05-30
And sudo dpkg-reconfigure fontconfig doesn't asks any question.

Output:
```

Cleaning up font configuration of fontconfig...
Cleaning up category cid..
Cleaning up category truetype..
Cleaning up category type1..
Updating font configuration of fontconfig...
Cleaning up category cid..
Cleaning up category truetype..
Cleaning up category type1..
Updating category type1..
Updating category truetype..
Updating category cid..
Regenerating fonts cache... done.

```

I use Feisty Fawn

---

### Post by Gary.M on 2007-05-31
Is this thread still relevant to Feisty? I'm just attempted it and found the same. Displaysize directive seems to have no effect at all. I just get 88dpi for res on my 1152x864 res CRT display setting. Are there newer instructions relevant to Feisty perhaps?

> **elnur said:**
> I got same problem on Feisty, DisplaySize directive has no effect, even if i use CTRL+ALT+backspase. Any thoughts?

---

### Post by elnur on 2007-05-31
> **Gary.M said:**
> Is this thread still relevant to Feisty? I'm just attempted it and found the same. Displaysize directive seems to have no effect at all. I just get 88dpi for res on my 1152x864 res CRT display setting. Are there newer instructions relevant to Feisty perhaps?

I ignored DisplaySize setting and did everything else from guide. It works and I like it. Perhaps it works not as good as would with DisplaySize, I don't know, but it works.

---

### Post by pacut on 2007-06-07
Something Got Wrong With My Font And I Have Now Desktop Fonts Completely Broken.

I See All "squares" Instead Of Chars - This On All Menus

Can Someone Please Provide Any Reset Instruction ?
I Would Avoid To Get Down My Entire Ubuntu

Pleeeease
Thanks

---

### Post by dannymichel on 2007-06-12
Can someone help me set this up for 1440X900 as I am a newb?

---

### Post by dannymichel on 2007-06-14
Anyone?

---

### Post by dannymichel on 2007-06-15
no matter what I type I get the same thing
```
danny@danny-desktop:~$ xdpyinfo | grep resolution
  resolution:    85x87 dots per inch

```
```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Thu Nov  9 17:56:12 PST 2006

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "HSD TW191D"
    HorizSync       31.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
#	DisplaySize	270	203	# 1024x768 96dpi
#	DisplaySize	338	254	# 1280x960 96dpi
#	DisplaySize	338	270	# 1280x1024 96dpi
#	DisplaySize	370	277	# 1400x1050 96dpi
	DisplaySize	381	238	# 1440x900 96dpi
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GT"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "1440x900_60 +0+0; 1280x800 +0+0; 1152x864 +0+0; 1024x768 +0+0; 832x624 +0+0; 800x600 +0+0; 640x480 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

---

### Post by calande on 2007-06-15
There are 2 procedures. You seem to have done the first one, which is setting up X.org properly, according to the specifications of your monitor. Then you have to go through the Gnome settings (menu on top) and go to the display settings to choose your screen resolution ;)

---

### Post by dannymichel on 2007-06-15
> **calande said:**
> There are 2 procedures. You seem to have done the first one, which is setting up X.org properly, according to the specifications of your monitor. Then you have to go through the Gnome settings (menu on top) and go to the display settings to choose your screen resolution ;)
Still shows as 85x95

---

### Post by calande on 2007-06-16
Ah, you're talking about definition? This may help you: [http://www.linuxquestions.org/questions/showthread.php?t=403450](http://www.linuxquestions.org/questions/showthread.php?t=403450)

---

### Post by calande on 2007-06-16
These will help you also:

[http://ubuntuforums.org/showthread.php?t=425684](http://ubuntuforums.org/showthread.php?t=425684)
[http://ubuntuforums.org/showthread.php?t=439880](http://ubuntuforums.org/showthread.php?t=439880)

;)

---

### Post by Gary.M on 2007-06-16
> **dannymichel said:**
> Still shows as 85x95

I've been down this road recently too... mine is showing 81x81. I measured my monitor and calcuated the dpi based on the res I am running, and guess what? My display was running very close to 81dpi. So the X-server screen in Nvidia config was telling me that things are set exactly correct for my monitor. The driver was reading the monitor details and doing what it should. I can't see how this can be forced to 96dpi without changing your display res. You can calc the exact res you need to run if you want 96dpi by simple maths.

There is a setting I discovered you can apply to tell the display driver to ignore the monitors electronic report on its specs and force any dpi you want. I did that and it made no difference to the clarity of the type on screen. Right now of course of lost the notes I made on how that setting was applied :-(

By the way, I think that adding the MS fonts gave me a more fuzzy look, not a clearer one...

---

### Post by tarek on 2007-06-17
Thanks! Great tutorial, the fonts are easy on the eyes now.

---

### Post by dannymichel on 2007-06-25
I SERIOUSLY need to know how to undo this.

[Edit]NVM
The fonts DO look horrible like this.
I prefer the Linux type fonts.
I mean, just cause I prefer the default to THIS thing doesn't mean I don't think Linux fonts aren't despicable.

---

### Post by Gary.M on 2007-06-25
In Kubuntu I just went into the font install under system settings - desktop and removed the Microsoft Fonts... Under ubuntu Gnome I don't know, but I suspect you need to go to the fonts folder and delete and then reconfig to let the system know what is there now...

---

### Post by tuxlinux on 2007-08-06
> **basse1989 said:**
> Are you guys crazy? Why don't you install windows instead? Who would want their ubuntu installation to look like windows?

I think ubuntu works GREAT as it is (read my signature).

I want it because I design many websites. Most websites are designed with Windows font in mind. Quite a headache.

---

### Post by JohnOhl on 2007-10-10
Followed this for Feisty 7.04 and it worked like a charm ;)

Honestly, a lot of people here seem to hate anything that comes from Microsoft. I truly and honestly hate the fonts that come with Ubuntu and most all other *nix distributions.

I do a lot of PHP, HTML, CSS, JavaScript, AJAX programming and I need to have very small, very clear text on a very small screen resolution. Ubuntu and most other *nix distributions simply cannot provide that. Has anybody who posts these microsoft sucks, why not just install windows posts actually tried setting there screen resolution past 1280x1024 and setting their font size smaller than 12? If you have then you probably wouldn't be making those posts, everything is simply unreadable for long periods of time on an LCD monitor...

Anyway, just wanted to say thanks for the guide, works awesomely ;)

---

### Post by calande on 2007-10-10
You welcome! I couldn't agree more with you. Sometimes the automatic anti-M$ hate makes me dizzy. I mean, Microsoft is an evil company, Windows has a number of problems, IE also, but everything is not bad, there are good things that come from Microsoft, and the fonts are one of them. I yet have to see a Windows user installing Linux fonts (Bitstream, Dejavu, Luxi...) on his Windows computer to improve readability, LOL :)

---

### Post by ghandi69_ on 2007-10-11
I seriously have been looking at those screenshots for over 10 minutes, and I cannot for the life of me figure out what it is your trying to do in this thread.

---

### Post by Caffeine_Junky on 2007-11-06
WoooHooo!, I am so glad I found this thread!

I am running the new gOS OS that comes with e17 pre-installed, ...and I ran into a "small font" issue,  

I have had this happen to me before whilst using e17 on Elive Gem 1.0, ...some fonts would become painfully small, for reasons I do not understand..

Anyhoo, the method described in the OP of this thread saved me from allot of stress!   ...I was either going to have to re-install my new OS (that I have just spent hours configuring and tweaking) ...or, just suffer "small application font" and go blind! ..hmmm, a hard decision!...  

This thread saved my butt!

...all I had to do was add this line (in red) to my "xorg.conf" file:
```
Section "Monitor"
    Identifier     "Acer AC711"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
    [COLOR="Red"]DisplaySize	270	203	# 1024x768 96dpi[/COLOR]
EndSection
```

Thanks **deelerious** ! With your help 'Enlightenment DR 17' lives on....

---

### Post by calande on 2007-11-06
Just in case some of you would be searching for sharp fonts, you can have a look at [www.sharpfonts.com](www.sharpfonts.com)

---

### Post by DirtDart on 2007-11-07
> **calande said:**
> ...you can have a look at [www.sharpfonts.com](www.sharpfonts.com)

Thanks for the link!

Personally, I like the look of sharp fonts over polished fonts.

---

### Post by cchevy on 2007-11-07
```
<?xml version="1.0"?>  <!DOCTYPE fontconfig SYSTEM "fonts.dtd">  <fontconfig>    <match target="font">      <edit name="autohint" mode="assign">        <bool>true</bool>      </edit>    </match>  </fontconfig>
```

this is my .fonts.conf

can u tell me what this means and if this affects the current appearance view?

7.10

---

### Post by calande on 2007-11-07
This simulates font hinting, in other words, it tries its best to polish your fonts when there are no hints (all non Microsoft fonts).

---

### Post by Sonja on 2007-12-30
Does this work in newer versions of Ubuntu too?

---

### Post by calande on 2007-12-30
Yes.

---

### Post by cyberkost on 2008-01-09
> **calande said:**
> Yes.

It does NOT seem to work for me! (and I do have "newer" 7.10)  I get
```

met@comp:~$ xdpyinfo | grep resolution
  resolution:    93x92 dots per inch

```
NO MATTER WHAT I put in the "Monitor" section of xorg.conf (Ubuntu 7.10).
So far I've tried the two settings below
```

Section "Monitor"
        Identifier      "DELL 2407WFP"
        Option          "DPMS"
#        DisplaySize    508     318     # 1920x1200
#        DisplaySize    498     306     # 1920x1200
EndSection

```
(uncommenting one at a time) with restarts after each, but I'm getting the same response from xdpyinfo :frown:.  So, I'm kinda stuck at step one.  Does anyone know where xorg.conf settings may be overridden?

---

### Post by hgurol on 2008-02-16
I had the same problem like yours. Try the below, it worked for me and I hope it will work for you too.

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-64
	Vertrefresh	43-60
[B]	Option "USEdidDPI" "false"
	Option "DPI" "96x96"[/B]
EndSection



> **cyberkost said:**
> It does NOT seem to work for me! (and I do have "newer" 7.10)  I get
```

met@comp:~$ xdpyinfo | grep resolution
  resolution:    93x92 dots per inch

```
NO MATTER WHAT I put in the "Monitor" section of xorg.conf (Ubuntu 7.10).
So far I've tried the two settings below
```

Section "Monitor"
        Identifier      "DELL 2407WFP"
        Option          "DPMS"
#        DisplaySize    508     318     # 1920x1200
#        DisplaySize    498     306     # 1920x1200
EndSection

```
(uncommenting one at a time) with restarts after each, but I'm getting the same response from xdpyinfo :frown:.  So, I'm kinda stuck at step one.  Does anyone know where xorg.conf settings may be overridden?

---

### Post by n-alexander on 2008-03-16
deelerious,

I did this to my xorg.conf:
Section "Monitor"
	Identifier	"Generic Monitor"
...
DisplaySize	270	203	# 1024x768 96dpi (203)
EndSection

and restarted X.

then: 
>xdpyinfo | grep dimensions
  dimensions:    1024x768 pixels (491x368 millimeters)
>xdpyinfo | grep resolution
  resolution:    53x53 dots per inch
>

I tried to adjust the numbers in xorg.conf but it does not affect resolution in any way.

Under Gnome, everything's fine, but under E17, Gnome apps seems to think it is 53dpi and that hurts.

(Fonts are set to 96dpi in Gnome.)

Any advise?

Thanks,
Alex

---

### Post by UJM on 2008-03-18
I've yet to find a Linux distro with good looking fonts out of the box, in general my Linux font's look inferior to my Windows Clear Type fonts, there is however one exception. The gOS linux distro does have good looking fonts imo, I wonder if there's a way to copy the fonts & config file from a gOS system into Ubuntu without conflicts, I don't even know what gOS is based on, or whether copying files into Ubuntu would work ?

---

### Post by n-alexander on 2008-03-18
> **UJM said:**
> I've yet to find a Linux distro with good looking fonts out of the box, in general my Linux font's look inferior to my Windows Clear Type fonts, there is however one exception. The gOS linux distro does have good looking fonts imo, I wonder if there's a way to copy the fonts & config file from a gOS system into Ubuntu without conflicts, I don't even know what gOS is based on, or whether copying files into Ubuntu would work ?

gos is Ubuntu + Enlightenment for window manager.

As for fonts, sorry, can't help.

Why not use gos directly? It is so far proving to be  better UI than GNOME and GNOME apps work there

---

### Post by n-alexander on 2008-03-18
in addition to:

Section "Monitor"
...
    DisplaySize	270	203	# 1024x768 96dpi
EndSection

it helps to have ~/.Xresources (was absent in my setup):
Xft.dpi: 96

for all users

---

### Post by UJM on 2008-03-19
> **n-alexander said:**
> gos is Ubuntu + Enlightenment for window manager.

As for fonts, sorry, can't help.

Why not use gos directly? It is so far proving to be  better UI than GNOME and GNOME apps work there

I don't like E17 ... but, I did use the guide from page1 and have to say everything  looks much better for it, I imported the Tahoma font and found that the choices made in Gnome's Font rendering panel under "hinting" had the biggest effect on my LCD monitor, I'm quite happy with my fonts now so many thanks to whoever wrote the guide.

---

### Post by gladstone on 2008-05-03
Just quickly, I was wondering if there is anything similar to Window's "**standard**" font smoothing? - When I say standard, it is an option from the following:

1. None
2. Standard
3. Cleartype

in display\appearence\effects (or something like that ;))

---

### Post by kabel_kabel on 2008-05-05
Hello Everyone,

I'm using Ubuntu 8.04 x64 and this how-to is not working for me. I followed the instructions and i changed the fonts to Tahoma (System -> Preferneces -> Appearance -> Fonts; i changed everything to Tahoma) and my desktop looks worst than before. I decided to follow this howto because i have installed Firefox 3.0b5 and Firefox 32-bit 2.0.0.14. With default fonts (Dejavu Sans) my system looks perfect along with Firefox 3.0b5 but not Firefox 32-bit 2.0.0.14.

So the question is how i can improve the antialiasing in Firefox 32-bit 2.0.0.14

**xorg.conf**
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "HSD Hanns.G HG281"
    HorizSync       24.0 - 80.0
    VertRefresh     56.0 - 75.0
    Option "USEdidDPI" "false"
    Option "DPI" "96x96"
    DisplaySize		508	318	# 1920x1200 96dpi
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1920x1200_60 +0+0; nvidia-auto-select +0+0"
EndSection

**output from *dimensions* and *resolution* commands**
kabel@kabel-pc:~$ xdpyinfo | grep dimensions
  dimensions:    1920x1200 pixels (508x318 millimeters)
kabel@kabel-pc:~$ xdpyinfo | grep resolution
  resolution:    96x96 dots per inch

**.font.conf**
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
<match target="font">
 <test compare="more" name="pixelsize" qual="any">
  <double>12</double>
 </test>
 <edit name="autohint" mode="assign" >
  <bool>true</bool>
 </edit>
</match>
<match target="pattern">
            <test qual="any" name="family">
                    <string>Bitstream Vera Sans</string>
            </test>
            <edit name="family" mode="assign">
                    <string>Arial</string>
            </edit>
</match>
    <match target="pattern">
            <test qual="any" name="family">
                    <string>Helvetica</string>
            </test>
            <edit name="family" mode="assign">
                    <string>Arial</string>
            </edit>
</match>
<match target="pattern">
            <test qual="any" name="family">
                    <string>Palatino</string>
            </test>
            <edit name="family" mode="assign">
                    <string>Georgia</string>
            </edit>
</match>
</fontconfig>


Thank you in advance
Kabel

---

### Post by kabel_kabel on 2008-05-06
Silence explains everything, there is no cure.

---

### Post by YaPaY on 2010-06-10
Is there any update for this topic. (lucid lynx?)

---

