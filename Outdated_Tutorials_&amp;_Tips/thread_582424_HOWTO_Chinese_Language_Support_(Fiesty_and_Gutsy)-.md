---
title: "HOWTO: Chinese Language Support (Fiesty and Gutsy)--fonts, input, display, problems"
date: 2007-10-19
forum: Outdated Tutorials &amp; Tips
---

### Post by jon.reeve on 2007-10-19
So I may not be an expert on this matter, but I've spent probably a good dozen or so hours battling with problems related to Ubuntu's Chinese language support, including several at the Chinese forums and wiki, and I learned a few things in the process, which I thought I'd share with the community in case some of this should prove to be helpful. This should be considered a guide for those who want to install Chinese language support (to be able to read and write Chinese characters) on a non-Chinese version of Ubuntu, like an English language version, for students of Chinese language, for example. The Chinese version, with Chinese menus and a Chinese login, often doesn't have any of these problems that I'll be describing. 

1) Install Chinese Language support in System -> Administration -> Language Support by selecting Chinese and enable support of complex characters in the checkbox below. It has been noted elsewhere that in Fiesty you might actually have to uncheck this box if it's already checked, hit apply, and then check it again. This should install SCIM. When you log out and log back in, a little keyboard icon in the system tray indicates that SCIM is runinng. 

2) Configure SCIM. This should be in System -> Preferences. Go to "global setup" and choose the input method you'll be using. For example, I use &#25340;&#38899; but others go for other input methods. Familiarize yourself with the keystrokes necessary to activate SCIM, or set ones you like. That way, whenever you want to write Chinese you can just press Cntl+space. I've got it hooked up to change between English and Chinese input every time I press Print Screen, which I find useful. 

3) Now you'll notice that you can input Chinese. But what if you have some characters that come out in serif, and others in sans? Does it look really strange? That's probably because Ubuntu is trying to display Chinese characters using a Japanese font, and is only displaying them with the Chinese font when the Japanese font doesn't contain that particular Chinese character. The way to fix this is by changing the font locale to zh_CN. This can be done by running 

```
fontconfig-voodoo -f -s zh_CN
```

and has worked for me in the past using this method, but there's the chance it might not work under Gutsy, as it tends to give Chinese fonts priority over even regular Western fonts, thereby making your normal western text look all aliased and ugly. To fix this, one of the things you could do is to move the western fonts (ie Bitstream, Deja Vu, etc) higher up on the list in the file /usr/share/language-selector/fontconfig/zh_CN by running

```
sudo gedit /usr/share/language-selector/fontconfig/zh_CN
```

and editing the file accordingly. But in case this doesn't work for some reason, another way to do this is first to revert your voodoo settings: 

```
fontconfig-voodoo -f -s none
```

then make a file called .fonts.conf with all the same stuff in it as a fixed-up zh_CN file would have. For example, mine looks like this: 

```
<fontconfig>
	<include ignore_missing="yes">CJK_aliases</include>
	<alias>
		<family>serif</family>
		<prefer>
			<family>Bitstream Vera Serif</family>
			<family>DejaVu Serif</family>
			<family>AR PL UMing CN</family>
			<family>AR PL ShanHeiSun Uni</family>
			<family>AR PL UKai CN</family>
			<family>AR PL ZenKai Uni</family>
		</prefer>
	</alias>
	<alias>
		<family>sans-serif</family>
		<prefer>
			<family>Bitstream Vera Sans</family>
			<family>DejaVu Sans</family>
			<family>AR PL UMing CN</family>
			<family>AR PL ShanHeiSun Uni</family>
			<family>AR PL UKai CN</family>
			<family>AR PL ZenKai Uni</family>
		</prefer>
	</alias>
	<alias>
		<family>monospace</family>
		<prefer>
			<family>Bitstream Vera Sans Mono</family>
			<family>DejaVu Sans Mono</family>
			<family>AR PL UMing CN</family>
			<family>AR PL ShanHeiSun Uni</family>
			<family>WenQuanYi Bitmap Song</family>
			<family>AR PL UKai CN</family>
			<family>AR PL ZenKai Uni</family>
		</prefer>
	</alias>
</fontconfig>
```

4) Now your Chinese characters display consistently but they're all aliased and ugly-looking under a certain size. That's because there's a few lines in fontconfig that turn off the antialiasing features that would otherwise smooth out the characters. The way to fix this is by editing a file called /etc/fonts/conf.d/70-ttf-arphic-uming.conf where there is a line that says 

```
<test name="pixelsize"  compare="more_eq"><int>17</int></test>
```

There, you can change the number 17 to whatever number you want it to start aliasing from. I changed it to 8, for example. 

And voila! Now you have pretty looking Chinese fonts. 

With that having been said, I really hope that by the next release Ubuntu will have figured this whole thing out, so that people won't have to go through all this just to get their computer to display Chinese correctly.

---

### Post by Echow on 2007-10-30
Thanks this topic helped quite alot. Just a few things to mention (based on xubuntu Gutsy 64bit):
The .fonts.config file goes in your home folder, took me a while to figure that one out haha.
For me the SCIM doesnt activate automatically when using an English session (could be because I use xubuntu). I had to install the scim-bridge package and configure a few files. Check [this page]("https://help.ubuntu.com/community/SCIM") for more information.

---

### Post by zanglang on 2007-11-08
Ah, I have  wondering for a while why fonts in Ubuntu look so horrible. Thank you. ;)

---

### Post by kolslorr on 2007-11-17
Unfortunately, I still cant get it...

I got the keyboard icon to appear... but nothing will trigger it to change to other language... there just no reason for this to be so difficult...

---

### Post by doowgof on 2007-11-18
Hello there! I've tried the method you said.. But it doesn't work for me..
I went to system-administration-language support, unticked chinese, applied, ticked it again, applied, restarted the computer. Then I found the little keyboard icon and went to system-preferences-SCIM input method setup, chose &#25340;&#38899;.
However, after I hit ctrl+space, I just can not input chinese.. Still english.. In the SCIM setup, control+space is the hotkey for 'Trigger'. What shall I do now?
My settings:
[IMG]http://img404.imageshack.us/img404/6457/screenshotsciminputmethaz7.png[/IMG]
[IMG]http://img442.imageshack.us/img442/7117/screenshotsciminputmethir6.png[/IMG]

---

### Post by jon.reeve on 2007-11-18
doofgof, it seems the SCIM setup might be a little more complicated than I originally thought. As echowsays above, this may require more configuration, as outlined on [this page]("https://help.ubuntu.com/community/SCIM").

---

### Post by doowgof on 2007-11-19
Thank you Jon. However this does not work for me neither.. I guess I need to do some more research..

---

### Post by brothermalcolm on 2007-12-05
&#22810;&#27053;&#20320;&#22320; !!!

it all worked fine for me after following the scim guide in ubuntu docs in order to extend support for all gtk apps such as firefox. all you need to do is install the scim-bridge package and change a config file.

the ime's that come with scim seem so easy to use! i typed the above using the cantonhk ime which is specifically designed for hong kong style cantonese pinyin input. no more copy+paste to search for &#22810;&#21862;A&#22818; vids on youtube!

---

### Post by jolleyjoe on 2007-12-07
This was a GREAT help. Chinese works properly now!!

---

### Post by quantboy on 2007-12-31
Thanks Jon- this solved the very same ugly Chinese font problem I've been having ever since I installed Gutsy a month ago.   
:popcorn:

---

### Post by slkwcy on 2007-12-31
Thank you for your instructions.  I finally can read Chinese way better in Gutsy Gibbon. 

=D>

---

### Post by countrylaketj on 2008-01-01
Happy new year!

I have a problem in the first step. My Ubuntu is 7.10 English version. It has no problem showing Chinese characters. However, when I tried to install Chinese input support, I have only "English" option in System -> Administration -> Language Support. What's wrong with my installation?

---

### Post by scrillamaan on 2008-01-09
I just want to say thank you for this guide. The ugly Chinese font thing has been bothering me for a while, but now everything looks pretty good.

:guitar:

---

### Post by acorrigan on 2008-02-04
Thanks so much for this information.

---

### Post by quatz007 on 2008-02-14
Thank you very much for the information. Now I can input Chinese.

---

### Post by zephyrus17 on 2008-02-19
I can't get anything to happen. Even after following the SCIM instructions on the help.ubuntu.com website. It's a vanilla Ubuntu freshly installed. Do you have any more suggestions?

---

### Post by oldHat on 2008-03-04
Hi, thanks,

I had SCIM working under 6.06 but lost it when I jumped to 7.10.

&#29616;&#22312;&#25105;&#22312;&#21487;&#33021;&#25171;&#23376;&#65281;

I tried everything u suggested, as well as what was on the linked page, but didn't get anywhere, although I'm sure it was all necessary.

I *did* find that selecting zh_CN.utf8 at the login window would enable scim, but I didn't like the other side-effects (chinese menus on all GUIs).

Finally, tried all kinds of random keystrokes (mostly ones which were already configured in Global Setup).  After <shift><control> (leftside), the menu popped up!  I can't explain this, unless this somehow cycled scim through its input methods until i lucked into what I needed.

---

### Post by Larir on 2008-05-30
This is a nice guide but it seems that in QT apps the fonts are a little too light... in GTK apps they look nice though, thanks! :)

---

### Post by skeelee on 2008-07-23
Hi guys,
I had been using this guide in Gutsy with perfect results. When Hardy came out, there is the same problem with the Chinese fonts, but the this guide does not work in Hardy. No choice but to revert back to Gutsy.
Any work around or modification for this guide to work in Hardy?

---

### Post by kadrach on 2008-08-24
It works on Hardy, only the issue with the western text rendered in weird fonts remains ;)

On hardy, undoing voodoo does not work:

```
niko@noe3:~$ fontconfig-voodoo -f -s none
No fontconfig-voodoo configuration found for the selected locale
Aborting

```

How can I undo the fontconfig-voodoo? :)

Something else I have just noticed: I am using a German keyboard (de_nodeadkeys), but when activating scim for wubi, the layout it switched to an english one. Scim config is set to a german layout. Any ideas?

---

### Post by jang on 2008-08-27
Hi there.  Just want to know once you've got SCIM working, is there any way for it to display soft keyboard?  Just like Microsoft IME?  The reason for asking this is I'm using Zhuyin as main input method.  So far, I don't have keyboard with chinese characters.  I don't know which letter to press for which character to come out.  In Microsoft, there's an option to display soft keyboard so you can use mouse to click the letters instead, or use the keyboard.

Another question is I'm used to traditional chinese.  I noted that there's no way to input Mandarin Pinyin?  Or does pinyin only come with simplified Chinese?  I saw there is Cantonese Pinyin, but it's different from Mandarin.

Lastly, does anyone know whether this guide works with Hardy?

Any help will be appreciated.

---

### Post by kadrach on 2008-08-27
I finally got this to work with Hardy:

Follow first post to step 3:
> **jon.reeve said:**
> 
1) Install Chinese Language support in System -> Administration -> Language Support by selecting Chinese and enable support of complex characters in the checkbox below. It has been noted elsewhere that in Fiesty you might actually have to uncheck this box if it's already checked, hit apply, and then check it again. This should install SCIM. When you log out and log back in, a little keyboard icon in the system tray indicates that SCIM is runinng. 

2) Configure SCIM. This should be in System -> Preferences. Go to "global setup" and choose the input method you'll be using. For example, I use &#25340;&#38899; but others go for other input methods. Familiarize yourself with the keystrokes necessary to activate SCIM, or set ones you like. That way, whenever you want to write Chinese you can just press Cntl+space. I've got it hooked up to change between English and Chinese input every time I press Print Screen, which I find useful. 

3) Now you'll notice that you can input Chinese. But what if you have some characters that come out in serif, and others in sans? Does it look really strange? That's probably because Ubuntu is trying to display Chinese characters using a Japanese font, and is only displaying them with the Chinese font when the Japanese font doesn't contain that particular Chinese character. The way to fix this is by changing the font locale to zh_CN. This can be done by running 

```
fontconfig-voodoo -f -s zh_CN 
```

and has worked for me in the past using this method, but there's the chance it might not work under Gutsy, as it tends to give Chinese fonts priority over even regular Western fonts, **[COLOR="Red"]thereby making your normal western text look all aliased and ugly.[/COLOR]** 


As you may note, some latin text may now look rather "unusual". This happens because the language selector prefers several chinese fonts over the standard western fonts for the serif font family. To fix:

Look at your /etc/fonts/conf.d/ directory, find the "*-language-selector-zh-cn.conf" (mine is 69-language-selector-zh-cn.conf, may differ for your system). 

Identifying the problem
```
        <match target="pattern">
                <test qual="any" name="family">
                        <string>serif</string>
                </test>
                <edit name="family" mode="prepend" binding="strong">
[B]                        <string>AR PL UMing CN</string>
                        <string>AR PL ShanHeiSun Uni</string>
                        <string>WenQuanYi Bitmap Song</string>[/B]
[B][COLOR="Red"]                        <string>Bitstream Vera Serif</string>
                        <string>DejaVu Serif</string>[/COLOR][/B]
                        <string>AR PL UKai CN</string>
                        <string>AR PL ZenKai Uni</string>
                </edit>
        </match> 

```

and fixing

```
        <match target="pattern">
                <test qual="any" name="family">
                        <string>serif</string>
                </test>
                <edit name="family" mode="prepend" binding="strong">
[B][COLOR="Red"]                        <string>Bitstream Vera Serif</string>
                        <string>DejaVu Serif</string>[/COLOR][/B]
[B]                        <string>AR PL UMing CN</string>
                        <string>AR PL ShanHeiSun Uni</string>
                        <string>WenQuanYi Bitmap Song</string>[/B]

                        <string>AR PL UKai CN</string>
                        <string>AR PL ZenKai Uni</string>
                </edit>
        </match> 

```

Works like a charm  :)

---

### Post by seraphim426 on 2008-09-07
> **jon.reeve said:**
> doofgof, it seems the SCIM setup might be a little more complicated than I originally thought. As echowsays above, this may require more configuration, as outlined on [this page]("https://help.ubuntu.com/community/SCIM").

Tks, it's working for me now.

---

### Post by weishigoname on 2010-03-15
good job

---

