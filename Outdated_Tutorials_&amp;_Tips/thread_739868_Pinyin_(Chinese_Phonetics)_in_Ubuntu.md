---
title: "Pinyin (Chinese Phonetics) in Ubuntu"
date: 2008-03-30
forum: Outdated Tutorials &amp; Tips
---

### Post by Ian Clark on 2008-03-30
[SIZE=5][COLOR="DarkOliveGreen"]&#24590;&#40636;&#29992;Ubuntu&#36664;&#20837;&#28450;&#35486;&#25340;&#38899;
z&#283;nme yòng Ubuntu sh&#363;rù Hàny&#468; P&#299;ny&#299;n[/COLOR][/SIZE]

Previous posts deal with how to use pinyin as an input method for true Chinese characters in SCIM.  However, this post will deal with how to write proper latin phonetics for Chinese in Ubuntu.  Writing proper phonetics is important to many students of Chinese, as well as people who want to use pinyin to supplant characters altogether.  *yídìng yào xi&#283; sh&#275;ngdiào o!*

There are two methods, the first of which is a better overall solution for most users.

[SIZE=4][COLOR="DarkRed"]Method #1: Using scim-m17n[/COLOR][/SIZE]

1. Install scim-m17n
[INDENT]a. Right-click your scim icon (a keyboard icon if you're inputing English) and select "exit" to exit scim.[/INDENT]
[INDENT]b. Open applications->accesories->terminal and type or paste this code into it:[/INDENT]
```
sudo apt-get install scim-m17n
```
2. Reboot

3. Left-click the scim icon to see a very large list of language selections.  You may have to hover the mouse over the bottom to scroll the menu down to "Chinese-simplified", and under the submenu select "zh-pinyin"

4. Test drive it
[INDENT]a. type something like "xiao3" (without quotes) and hit spacebar.  The tone should appear over the "a", as in "xi&#462;o".  For individual vowels with tones, type a vowel with a number from 1 to 4 after it, then hit spacebar.[/INDENT]

[SIZE="3"]Tweaking[/SIZE]

To tweak your scim, right-click the scim icon and select SCIM setup.

1.  Check your hotkey and remember to use it
[INDENT]a. Under FrontEnd->Global Setup look under "hotkeys" and "trigger".  Mine is control+space, which I find convenient.  I deleted other hotkeys to prevent conflicts with other programs like firefox.[/INDENT]
2.  Reduce the language options on scim menu
[INDENT]a. Under IMEngine->Global Setup deselect any languages you don't think you'll need.
b. Look on your Chinese input submenus as well, and uncheck Chinese inputs that you don't need or cannot use, but still leaving our "zh-pinyin" checked.[/INDENT]

The "reload configuration" option when right-clicking scim icon doesn't usually work for me, so I don't bother with it.  Reboot to see your changes take effect.

[SIZE="4"][COLOR="DarkRed"]Method #2: Copy and paste[/COLOR][/SIZE]

To use method #2, make sure you have Character Palette installed.  [QUOTE=mdurham]Right click on a panel and select "add to panel", select "character palette"[/QUOTE]

1. Character Palette->Preferences
Right click on your current Character Palette (at the top of the screen) and select preferences.

2. Preferences->Add
Of the three choices Add, Edit and Delete, choose "Add".  You'll see a small window "Add Palette" come up.

3. Paste characters into the text field.
In the text field enter the following list of characters by the copy and paste method: &#257;á&#259;à&#275;é&#277;è&#299;í&#301;ì&#333;ó&#335;ò&#363;ú&#365;ù&#470;&#472;&#474;&#476;
or this list for two kinds of 3rd tone markings (the second being more authentic): &#257;á&#259;&#462;à&#275;é&#277;&#283;è&#299;í&#301;&#464;ì&#333;ó&#335;&#466;ò&#363;ú&#365;&#468;ù&#470;&#472;&#474;&#476;
[COLOR="Red"]WARNING[/COLOR]: don't try these long lists of characters if you're using gnome and you already have several launch icons or other items on your top panel.  It can get overloaded and mess up your GUI access to Applications Places and System menus.

4. Click "OK"
After you've entered and clicked "OK", you'll notice a new palette that you can select.

5. Test it.
Click on one of the accented vowels, then enter it into a text field by clicking your scroll button or control+v.

For plain diacritics (which have a more authentic-looking 3rd tone), go back and do step 3, and copy and paste what is after this colon into the text field: &#772;&#769;&#780;&#768;
You'll find that there are four very thin choices, and they go in the order of the four tones, though they aren't visible until you enter them after a vowel and make them appear over the vowel.

I find that the pre-encoded characters from step 3 can be rendered on M$ systems, whereas M$ doesn't render the plain diacritics.

If you want to make any additions or changes use Character Map (the Latin set) to find, copy and paste what you need into Character Palette.

Hope someone finds this useful. h&#462;oh&#257;o xuéxí ba!

**NOTES:** 
1. Method #1 cannot put a tone marking on capital letters, as would be needed for words like [COLOR="Blue"]&#256;nhu&#299;[/COLOR] (the province) or [COLOR="Blue"]&#274;mítuófó[/COLOR] (the Buddha).
2. Method #1 seems to choose the right vowel to put the tone on no matter what combination I try, so word by word input is more convenient vowel by vowel.
3. There is no way to add the fifth tone (a dot on top of the vowel) through method #1, though these characters can be found on Character Palette and used by method #2

---

### Post by zanuvio on 2008-10-03
Hi

I've been trying to set up a way of entering pinyin with tones for a while, you're, just wondering how one installs the character pallette, i couldnt find any application or package with that name and the character map application doesn't have a preferneces section.

(Running Hardy Heron 8.04)

cheers, david

---

### Post by mdurham on 2008-10-10
> **zanuvio said:**
> Hi

I've been trying to set up a way of entering pinyin with tones for a while, you're, just wondering how one installs the character pallette, i couldnt find any application or package with that name and the character map application doesn't have a preferneces section.

(Running Hardy Heron 8.04)

cheers, david
David, right click on a panel and select "add to panel", select "character palette"
This installs the palette in a panel but I don't seem to be able to insert any chars in a document. Clicking the scroll button does nothing for me!
Cheers, Mike

I've discovered that you must select the char from the palette and 'then' click in the document to insert the selected char. (sorry, I'm a bit slow!)
Thanks Ian for the information, but it's a bit cumbersome don't you think?

---

### Post by FaceLeg on 2009-02-28
> **mdurham said:**
> ...it's a bit cumbersome don't you think?

It is a bit - but at least I can use Pinyin now!

MacOS has a feature where one can insert diacritics (tone-marks) by pressing some key combination (say, apple + alt + a letter - apple + alt + a = first tone mark), followed by a vowel.  This was quite quick.

Is there anything like this for linux?

Thanks for the post by the way, very helpful!

---

### Post by Ian Clark on 2009-04-27
@faceleg
You're welcome!  My post has been updated to include a more convenient method which you'll hopefully like.

@mdurham
Yes method #2 is cumbersome, but it is still necessary to input tones on capital letters.

---

### Post by nanbanjin on 2009-04-27
How about using [compose key]("https://help.ubuntu.com/community/ComposeKey")? I think you can edit the compose key sequences to make typing pinyin as easy as typing Czech, for example.

---

### Post by Ian Clark on 2009-04-27
> **nanbanjin said:**
> How about using [compose key]("https://help.ubuntu.com/community/ComposeKey")? 
Doesn't work for me.  Probably hotkey conflicts between firefox, scim, etc.

---

### Post by nanbanjin on 2009-04-28
Funny, have you tried changing the hotkey for compose? I use SCIM for Japanese and Russian input and I haven't run into any conflicts (maybe in qt4 apps but there is a way around that too, I am sure). How about changing compose key sequences?

---

### Post by Ian Clark on 2009-04-29
I've tried changing the settings and such, to no avail.  I'm running a system with scim (don't know if you're doing that now), and there's all kinds of hotkeys for scim, firefox and compiz.  There's probably something in there that's conflicting, but I can't find it yet.

---

### Post by frazerr on 2009-08-26
> **Ian Clark said:**
> 
[SIZE=4][COLOR="DarkRed"]Method #1: Using scim-m17n[/COLOR][/SIZE]

1. Install scim-m17n
[INDENT]a. Right-click your scim icon (a keyboard icon if you're inputing English) and select "exit" to exit scim.[/INDENT]
[INDENT]b. Open applications->accesories->terminal and type or paste this code into it:[/INDENT]
```
sudo apt-get install scim-m17n
```


Does this import existing scim setting?

Is it a replacement of scim or just an add on?

---

### Post by Ian Clark on 2009-08-27
> **frazerr said:**
> Does this import existing scim setting?

Is it a replacement of scim or just an add on?

It's an add-on.  After installing it, you'll have more languages available on your original language list.

---

