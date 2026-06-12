---
title: "Multiple Keyboard Layouts and US International"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by fballem on 2008-05-10
I work in three languages (English, French, and Portuguese).

In Windows:

I could use two keyboard layouts (US Standard and US International). In US International, for example, I could type the apostrophe, followed by the c to get a c-cedille or apostrophe, followed by the a or e to get an accented letter. If I type apostrophe followed by space, then I get the apostrophe.

Each keyboard layout could then be associated with a specific language. In Windows, I had four language settings:

English (Canada), which used the US Keyboard
English (US), which used the US Keyboard
French (Canada), which used the US International Keyboard
Portuguese (Portugal), which used the US International Keyboard

On my desktop, I had a little symbol showing the language. If I clicked on the symbol, I could change languages and the correct keyboard would be instantly available.

Can I set up something similar in ubuntu, and if I can, how do I do it?

Many thanks,
Flavelle Ballem

---

### Post by warbread on 2008-05-10
You actually have two options here.  The easiest one is to right click on one of your desktop panels and select "Add to panel".  From there, find something called "Keyboard indicator".  That will put the gnome language selector tool thingy up for you.  Right click on that and go to 'Keyboard layouts' and from there, the 'Layouts' tab.  You can add up to four here (a limitation of Gnome, unfortunately) and under 'Layout Options', configure how to want to change layouts.  Here's a nifty how to that will put national flags on your indicator, Mac OSX style :)

[**HOWTO Make Gnome Keyboard Indicator Show Country Flags**]("http://ubuntuforums.org/showthread.php?t=528890&highlight=keyboard+indicator+flags")

Your other option is a little more complicated, but necessary for things like the international phonetic alphabet.  SCIM (the Smart Common Input Method) might work for you, but I find it more frustrating and only use it when I have to type up IPA transcriptions.  A short how to on installig SCIM can be found [here.]("http://www.ubuntugeek.com/fix-for-scim-errors-in-ubuntu-gutsy-and-hardy.html")

Hope that helps!

---

### Post by fballem on 2008-05-10
Thanks for the information. Keyboard input may be a challenge, and it may be that I don't understand the Linux keyboard. I'll share my Windows-based understanding, in the hope that someone can explain linux keyboards.

1. In Windows, there are three indicators that are used: Language, Country, and Keyboard (or input device).

2. My default (in the old world) was English(Canada)-US Keyboard, which is fairly normal for English-speaking Canadians. This meant that I was using a US keyboard. If there were specific aspects (such as a dictionary) for English(Canada) then that would be used, otherwise, English (generally US) would be used.

3. Additional options, for me, were French(Canada)-US International Keyboard and Portuguese(Portugal)-US International keyboard. This meant that if I chose French, then my keyboard would be switched to US International.

4. The US International keyboard, in Windows, was pretty simple. Specific characters, when typed, would be treated as dead keys (~`^',). If I typed one of those characters, then the system would wait for the next key. If it was a character that could take an accent, then the accent would be applied. If it was not a character that could take an accent (such as a space), then the character would be applied. For example, the '. If I typed the ', followed by a, then an accented a would appear. If I typed the ', followed by a space, then the ' would appear.

5. In trying to follow the layout diagrams, I'm not sure that I'm getting it. It sounds like linux selects specific keys to act as additional shift-type functions. In addition, if I select Canada, then I get a very strange set of mappings (most English Canadians are using a standard US keyboard). This might be part of a learning curve that I have to go through, but if there is something that works like the US International keyboard in Windows, then this would be better.

I am probably missing something, so any clarification would be much appreciated.

Thanks

---

### Post by warbread on 2008-05-10
I'm not sure what to tell you.  At work, I use the Windows language bar to switch between English, French and Russian.  I do the same in Ubuntu using the first option I described and they end up typing exactly the same.  Maybe [this link would help?]("http://raviratlami1.blogspot.com/2006/10/how-to-add-another-language-and.html")

---

### Post by fballem on 2008-05-10
> **warbread said:**
> I'm not sure what to tell you.  At work, I use the Windows language bar to switch between English, French and Russian.  I do the same in Ubuntu using the first option I described and they end up typing exactly the same.  Maybe [this link would help?]("http://raviratlami1.blogspot.com/2006/10/how-to-add-another-language-and.html")

When you are at work, which keyboard do you use for English and which keyboard do you use for French?

When you are working in Linux, which keyboard do you use for English and which keyboard do you use for French?

Many thanks,
Flavelle

---

### Post by krimo on 2009-07-10
> **fballem said:**
> When you are at work, which keyboard do you use for English and which keyboard do you use for French?

When you are working in Linux, which keyboard do you use for English and which keyboard do you use for French?

Many thanks,
Flavelle

Hi Flavelle,

Just in case no one has answered in a year (!), I use Canadian Multilingual for French and US for English (default layout). Canadian multilingual is QWERTY but has all the accents and cedille-c, etc. Also, the post given ([http://ubuntuforums.org/showthread.php?t=528890&highlight=keyboard+indicator+flags](http://ubuntuforums.org/showthread.php?t=528890&highlight=keyboard+indicator+flags)) works fine, just tried it. 

Good luck :)

Kerim

---

### Post by fballem on 2009-07-27
> **krimo said:**
> Hi Flavelle,

Just in case no one has answered in a year (!), I use Canadian Multilingual for French and US for English (default layout). Canadian multilingual is QWERTY but has all the accents and cedille-c, etc. Also, the post given ([http://ubuntuforums.org/showthread.php?t=528890&highlight=keyboard+indicator+flags](http://ubuntuforums.org/showthread.php?t=528890&highlight=keyboard+indicator+flags)) works fine, just tried it. 

Good luck :)

Kerim

Actually, I've long since found a solution. I configure the English-US Keyboard and the English-US International (with dead keys) keyboard. The keyboard indicator that was suggested on earlier posts sits on my upper panel. When I want to switch, I click it. The indicator will read either US or US2 (in my case normal or US International with dead keys).

I am surmising that Linus separates the language from the input method, since I have four dictionaries loaded in Open Office, and they seem to work quite well (English Canada, American English, French, and Portuguese).

Thanks for following up on this thread!

---

### Post by lores on 2009-08-29
Hi!

I've got yet another problem. When I add an additional keyboard layout to my Ubuntu 9.04 desktop (I default to Polish, which is English + extra diacritics with ALT, and I'm adding German), it works all fine until I reboot the PC.

But after the X starts, I get additional "??" and "??2" *layouts* in the GNOME Indicator Applet (they're not listed in Keyboard Preferences, only Pol and Ger are), which are quite messed up (some weird letters, symbols etc.).

The problem is, after those two ??-layouts appear, I am unable to use some special symbols with the Ger layout, for example the "@".

Does anyone have a clue as to how to get rid of those odd ??s and have the functional layouts restored? I think it's a general ubuntu-issue, because it happens on lots of other machines with same software config, too (Ubu 9.04 (and older versions as well) + the conjunction of the Polish and German layout).

Thanks!

---

