---
title: "How To Type Traditional Chinese Pinyin (12.04)?"
date: 2012-08-19
forum: New to Ubuntu
---

### Post by linuxn00bface on 2012-08-19
This seems much more difficult than it should be. I tried installing GCIN, now there's a GCIN icon on the menu bar.

1. For anyone using GCIN (or anyone not, even), why when I open it does it first display a "do not enter" minus (-) sign dialog bog with "chewing-modile.so:  can't open shared object file:  there is no file or directory"
after clicking "Close",
"anthy-module.so: can't open shared object file:  there is no file or directory"

Close, then it opens.

Then it pops open. What is causing this error, how might it have happened, and how can I fix it? And more importantly, how do I USE it and switch to traditional chinese input easily?

2. Is there anyone who can provide a straightforward way to install and type traditional chinese characters with pinyin, using or not using GCIN?

Thanks :)

---

### Post by 25tom on 2012-08-19
Maybe try the Character Map application?
Applications>Accessories>Character Map

---

### Post by linuxn00bface on 2012-08-20
> **25tom said:**
> Maybe try the Character Map application?
Applications>Accessories>Character Map

Haven't been able to find it.

Cmon, typing Chinese can't be this hard?!

---

### Post by linuxn00bface on 2012-08-22
> **linuxn00bface said:**
> Haven't been able to find it.

Cmon, typing Chinese can't be this hard?!

Help, please?

Does anyone at least know of someone who types Chinese? Anyone from Taiwan/Hong Kong who uses Pinyin? iBus is supposed to have Traditional Chinese input, but for the life of me I only see SunPinyin, Chewing, etc.

---

### Post by Hadaka on 2012-08-22
hvae you seen this?

[http://www.pinyinjoe.com/linux/ubuntu-12-chinese-setup.htm](http://www.pinyinjoe.com/linux/ubuntu-12-chinese-setup.htm)

also...click system settings, then language support.

google is your friend.

---

### Post by linuxn00bface on 2012-09-03
> **Hadaka said:**
> hvae you seen this?

[http://www.pinyinjoe.com/linux/ubuntu-12-chinese-setup.htm](http://www.pinyinjoe.com/linux/ubuntu-12-chinese-setup.htm)

also...click system settings, then language support.

google is your friend.

I appreciate that you are trying to help, however I'm confused how someone can believe that anyone who can register on a forum and type a coherent sentence didn't first Google the **** out of something before asking, especially about something so basic.

Traditional Chinese input does NOT work for me on Ubuntu 12.04, and it seems to have worked for others on 10 and 11 just fine, so something is clearly wrong, either with my system, or Ubuntu itself. "Pinyin" is simply not an option in the iBus settings. I have SunPinyin, Chewing, etc., but NO "PINYIN." Therefore, I can't switch to traditional characters.

For Pete's sake, this is so basic, can someone from Ubuntu please step in here and tell me exactly what to do?

---

### Post by Hadaka on 2012-09-03
Hi, I use pinyin often with Ubuntu 12.04 and have not experienced any
problems, I had to do a couple tweaks but other than that , it seems
to work well. When people ask questions on here, the reader has no idea
what the poster knows or has done prior to posting,sorry if you were offended
it was not my intent, good luck.

---

### Post by linuxn00bface on 2012-09-04
> **Hadaka said:**
> Hi, I use pinyin often with Ubuntu 12.04 and have not experienced any
problems, I had to do a couple tweaks but other than that , it seems
to work well. When people ask questions on here, the reader has no idea
what the poster knows or has done prior to posting,sorry if you were offended
it was not my intent, good luck.

Fair enough, so I assume you use Traditional Chinese then, since that's what I've been asking about, and that's the title of this thread? If so, can you please take a screenshot of your iBus settings?

_Crash course so maybe someone unfamiliar with Chinese can help_:
Pinyin: way to use English-ish phonetics to write Chinese; e.g., I type "nihao" and &#20320;&#22909; appears.
There are two commonly-used types of Chinese writing: Simplified (China PRC, Singapore), and Traditional (Taiwan, Hong Kong, etc).
Simplified (Pinyin input): How have you been? -> nizuijinzenmeyang -> &#20320;&#26368;&#36817;&#24590;_&#20040;&#26679;_?
Traditional (Pinyin input): How have you been? -> nizuijinzenmeyang -> &#20320;&#26368;&#36817;&#24590;_&#40636;&#27171;_&#65311;

Note that both of the traditional pinyin input methods described by **[COLOR=Blue][Pinyin Joe]("http://www.pinyinjoe.com/linux/ubuntu-10-chinese-input-pinyin-chewing.htm")[/COLOR]** ([http://www.pinyinjoe.com/linux/ubuntu-10-chinese-input-pinyin-chewing.htm](http://www.pinyinjoe.com/linux/ubuntu-10-chinese-input-pinyin-chewing.htm)) -- first, simply called "PInyin, and fourth, called "Bopomofo" -- are not options for me (see attached images; &#8220;&#20559;&#22909;&#35373;&#23450;&#65288;P&#65289;" is "Preferences" in ibus1.png, and clicking it opens the window pictured in ibus2.png).

---

### Post by linuxn00bface on 2012-09-06
bump

---

### Post by linuxn00bface on 2012-09-11
bump x2

adminsayswhat?

---

### Post by linuxn00bface on 2012-09-12
uhhh..srsly?

UBUNTU guys, this should be basic of basic. Can someone at least tell me who to message to address this, por favor?

Thanks

---

### Post by mips on 2012-09-12
I know nothing about your problem but have you maybe tried [http://ubuntu.opensource.hk/](http://ubuntu.opensource.hk/)

---

### Post by linuxn00bface on 2012-09-12
> **mips said:**
> I know nothing about your problem but have you maybe tried [http://ubuntu.opensource.hk/](http://ubuntu.opensource.hk/)

Woah thanks guy, I'll try there and report back. :)

---

### Post by linuxn00bface on 2012-12-03
Hey guys, after many people got back to me on the Ubuntu-Taiwan forum, one nailed it: I needed to do Software Center->ibus-pinyin and install that. Then, "Pinyin" showed up in my list of choices in iBus.

Man do I miss Taiwan...

---

