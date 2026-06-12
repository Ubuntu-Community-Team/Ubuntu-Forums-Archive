---
title: "Bash - UTF8"
date: 2013-03-18
forum: New to Ubuntu
---

### Post by Kevin19 on 2013-03-18
Hi guys,

I'm using the Ubuntu Linux Server und working with the Bash. The problem is, that the bash doesn't print UTF-characters. This doesn't work:
echo -e "\xE2\x98\xA0"

I don't know why. Can anyone please help me?

---

### Post by schragge on 2013-03-18
With pleasure.
```
echo $'\uE2\u98\uA0'
``` or ```
echo -e '\uE2\u98\uA0'
```

---

### Post by Kevin19 on 2013-03-18
That doesn't work. The bash doesn't print the unicode char.

---

### Post by steeldriver on 2013-03-18
Isn't it determined by the terminal rather than the shell? for the server console, you could try

```
sudo dpkg-reconfigure console-setup
```

and making sure UTF-8 and the appropriate character set are selected (I don't know what charset those characters are from)

---

### Post by schragge on 2013-03-18
Excuse me, what Unicode character are you trying to print? The commands above should have printed three of them:
U+00E2 â, latin small letter a with circumflex
U+0098 SOS, start of string
U+00A0 NBSP, non-breaking space

---

### Post by Kevin19 on 2013-03-18
Well I'm using the German language "de_DE.UTF-8". Doesn't that mean that i Can print every possible unicode character which exists?

---

### Post by Kevin19 on 2013-03-18
> **schragge said:**
> Excuse me, what Unicode character are you trying to print? The commands above should have printed three of them:
U+00E2 â, latin small letter a with circumflex
U+0098 SOS, start of string
U+00A0 NBSP, non-breaking space
It only prints a diamond.

---

### Post by schragge on 2013-03-18
First, you need a Unicode-capable terminal emulator, obviously. Second, your console font should include glyphs for the characters you're trying to print. If you're doing it over ssh from a PuTTY on Windows, note that PuTTY is configured for Latin-1 charset by default, and you should change it to UTF-8 in the settings.

---

### Post by Kevin19 on 2013-03-18
No I'm using the Ubuntu Server with bash. Many Unicode characters aren't printed. A diamond is printed instead. So what do I have to do to solve this problem?

---

