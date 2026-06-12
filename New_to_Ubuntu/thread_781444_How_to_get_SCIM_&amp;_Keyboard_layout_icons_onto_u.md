---
title: "How to get SCIM &amp; Keyboard layout icons onto upper panel (Hardy)"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by swarup on 2008-05-04
I just installed Hardy, and installed relevant files for support of several languages (Hindi, Bengali, Spanish) which I need to use. But I need to be able to activate SCIM and for some reason, the toggle switch which is set to active it ("cntrl-space") is not doing so. And in SCIM setup, I have also set the SCIM icon to appear always on the toolbar (upper panel?). But it is not appearing. 

And for my use of Spanish, I need the keyboard layout icon to appear on the upper panel, so I can toggle between English and Spanish keyboards. But I cannot figure out how to get the icon to appear there.

Help? --Thanks!
---------

Add: I just figured out how to add the keyboard layout icon, and it is there on the upper panel. But when I click on it and switch it to "Esp" for Spanish, the Spanish language keyboard layout is still not working. 

And I still need to get the SCIM icon added up there as well, and to get the toggle switch working for SCIM activation.

---

### Post by swarup on 2008-05-04
Now I've got both icons--the keyboard layout icon and the SCIM icon--on the upper panel. But neither works. The keyboard layout icon does switch between English and Spanish when I click on it, but the Spanish language keyboard never actually comes up. 

And the SCIM icon is not working either. When I click on it, nothing happens. It should give a drop-down menu of all the available languages installed. And "cntrl-space" should activate SCIM, but it doesn't. Any ideas?

Edit: 5/8/08: SCIM has started working on its own. Don't know why. But that problem has resolved itself. Now the only issue that remains is the Spanish language keyboard, which continues not to work despite having the Spanish language keyboard label appear on the upper panel

---

### Post by garukun on 2008-05-19
I am experiencing the same problem that you have described there.
My "ctrl+space" does not work, nor does the top panel has a input method icon, or even, I don't think the SCIM control interface works for me either... 

I'm actually wondering if anyone has got their SCIM working for other languages... any reply is much appreciated!

---

### Post by computermacgyver on 2008-06-28
SCIM works for me when I login using the English (USA) interface, but when I login using the Spanish (Mexico) interface (which I prefer), the SCIM icon does not appear. Execuing "scim" at the terminal will add the icon to the panel, but it still does not activate using the hot key. (Under English, however, everything works fine).

I have added es_MX.UFT-8 to my /etc/scim/global file as in:
/SupportedUnicodeLocales = en_US.UTF-8,es_MX.UTF-8
but this still does not work.

Any ideas? I am also using Hardy

---

### Post by computermacgyver on 2008-06-28
All right!
Executing 
```

im-switch -z es_MX.UTF-8 -s scim

```
in a terminal, fixed my problem. I can now use scim to input Japanese or Spanish/English using the Spanish (Mexico) user interface.

This should work for anyone using another interface language (non-English and non-Asian). To find your locale, type
```

locale|grep 'LANG='

```
in a terminal and then take the output listed after LANG= and substitute it for es_MX.UTF-8 above. (My output for locale, for example, is "LANG=es_MX.UTF-8")

Best of luck.

------
Edit: I've included these steps in the Wiki article here
[https://help.ubuntu.com/community/SCIM](https://help.ubuntu.com/community/SCIM)

---

### Post by swarup on 2008-06-29
Interesting post, computermacgyver. And very useful.

I just checked mine, and I am simply using the banal English (USA) interface.

```
swarup@swarup-laptop:~$ locale|grep 'LANG='
LANG=en_US.UTF-8
```

And my SCIM works fine.

But my problem is that to this day, when I select "Esp" as the keyboard layout, it doesn't work. The keyboard layout icon changes to "Esp", but the keyboard remains that of English (USA).

At one point I added the keyboard "India". And due (it seemed to me) to the presence of the "India" keyboard layout in the list, the Spanish keyboard layout also started to work. But now even though the "India" keyboard is still selected as one of the options, but it no longer appears as one of the toggle options in the keyboard layout icon on the top panel-- even when I make "India" the default option. And due to this fact that the India layout is no longer appearing in the toggle options, even when I select "Esp" the Spanish keyboard layout does not work-- it just remains the English layout. 

I never had any such problem in Feisty; it is only since migrating to Hardy that this ugly issue has raised its head. I tried many times to deselect and reselect the "Spain" and "India" keyboard layout options in the keyboard preferences menu, but to no avail. The India layout is not an option in the toggle menu, and the Esp option although appearing in the toggle menu, but it does not work. Any suggestions?

---

### Post by computermacgyver on 2008-06-30
> **swarup said:**
> 
And my SCIM works fine.

But my problem is that to this day, when I select "Esp" as the keyboard layout, it doesn't work. The keyboard layout icon changes to "Esp", but the keyboard remains that of English (USA).



I just tried adding additional layouts, and experience the same problem trying to select the layout through SCIM--the keyboard simply stays in US English. However, setting and using a keyboard shortcut to switch layouts works for me. The default shortcuts seems to be simultaneously pressing both alt keys. The shortcut can be changed through the System->Preferences->Keyboard dialog. On the second tab (English interface may say "Layout"**), press the "Layout Options"** button in the bottom right corner. Expand the section "Layout switching" and choose a key combination that "changes layout."

**"Layout" and "Layout Options" may not be the exact translations in the English interface. If you have trouble finding these, I will relogin with the English interface and get there exact names. Or let me know if you do find the names and I will update the post.

---

### Post by swarup on 2008-06-30
Your directions were very clear, and also clearly labeled. I easily found the shortcut menu, and decided to leave it set at the default, alt-alt to change the language. The odd thing is that hitting alt-alt in itself does not appear to achieve anything. After hitting alt-alt, the keyboard remains in English. But the good news is, having done alt-alt seems to have somehow reactivated my keyboard layout icon on the upper panel, so that it has started working again! Now when I toggle that upper panel keyboard layout icon, it switches between "USA", "Esp", and "Ind" -- and for the first time in a long time, those changes actually do change the keyboard layout. Estoy muy feliz !

---

### Post by ChameleonDave on 2008-06-30
> **swarup said:**
> 
And for my use of Spanish, I need the keyboard layout icon to appear on the upper panel, so I can toggle between English and Spanish keyboards.

I used to mess around with different keyboards, until I realised that you just need one.  Here in Australia, the keyboards use the US layout.  So, I choose "US-international" (or the variant that uses Alt-Gr) as my one and only layout in Ubuntu.  This means that the keys are as they appear to be on the actual keyboard, and I am also able to input all the accents I want.  I can use it to write French, Spanish, Portuguese, etc.  áéíóú¿?¡!«»àèìòùãõ&#361;ñ

I also use SCIM for Chinese and Japanese input.  The bar floats around the bottom of the screen, and expands when I need it.  I use KDE 4.

---

### Post by swarup on 2008-07-01
> **ChameleonDave said:**
> I used to mess around with different keyboards, until I realised that you just need one.  Here in Australia, the keyboards use the US layout.  So, I choose "US-international" (or the variant that uses Alt-Gr) as my one and only layout in Ubuntu.  This means that the keys are as they appear to be on the actual keyboard, and I am also able to input all the accents I want.  I can use it to write French, Spanish, Portuguese, etc.  áéíóú¿?¡!«»àèìòùãõ&#361;ñ

That is very interesting. I'd also like to try this.

1. "So, I choose "US-international" (or the variant that uses Alt-Gr) as my one and only layout in Ubuntu."

What is "Alt-Gr"?

2. When you say that the keys are as they appear to be on the actual keyboard, then how is it you are also able to input all the accents you want? For example, "áéíóú¿?¡!«»àèìòùãõ&#361;ñ": how did you produce these? Are all these keys available on the US-international keyboard as the keys appear to be on the actual keyboard? If so, that is incredible. I'd like to see a keymap of this layout.

---

### Post by ChameleonDave on 2008-07-01
> **swarup said:**
> That is very interesting. I'd also like to try this.

1. "So, I choose "US-international" (or the variant that uses Alt-Gr) as my one and only layout in Ubuntu."

What is "Alt-Gr"?

2. When you say that the keys are as they appear to be on the actual keyboard, then how is it you are also able to input all the accents you want? For example, "áéíóú¿?¡!«»àèìòùãõ&#361;ñ": how did you produce these? Are all these keys available on the US-international keyboard as the keys appear to be on the actual keyboard? If so, that is incredible. I'd like to see a keymap of this layout.

The internet is your friend.

See:
 [http://en.wikipedia.org/wiki/AltGr_key](http://en.wikipedia.org/wiki/AltGr_key)
 [http://en.wikipedia.org/wiki/Keyboard_layout#US-International](http://en.wikipedia.org/wiki/Keyboard_layout#US-International)

The accents are mapped to symbols that look like them.  For example, the acute accent is mapped to the apostrophe.

---

### Post by computermacgyver on 2008-07-01
Of course, if your keyboard does not have an Alt-Gr key, you may wish to designate another key to serve this purpose. Various options are available in the same location you were able to set the Layout Switching shortcut (System->Preferences->Keyboard->Layout->Layout Options). Expand the section "Compose Key Position". Here you can designate another key such as right alt, windows key, etc.

To enter accented (or other special characters) use the following sequences:
Compose + ! + ! = ¡
Compose + ? + ? = ¿
Compose + ' + a = á
Compose + ~ + n = ñ (requires a shift to type ~ symbol)

The keys do not need to be pressed simultaneously.

---

### Post by swarup on 2008-07-02
I see, yes. Looks great. I don't have the Alt-Gr key to which you refer. But the alternative approach you have given, should work fine. :)

Thanks for the tips! :)

---

### Post by joshzam on 2008-07-08
That US-International Alt Gr trick is super! Thanks for the tip.

It'd still be nice if someone would help guide us as to how we can get Hardy switching layouts as Feisty always did. Looks like it may be a bug.

---

