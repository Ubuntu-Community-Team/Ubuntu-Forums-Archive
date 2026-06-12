---
title: "Store '£' in a char variable c++"
date: 2008-11-30
forum: Programming Talk
---

### Post by bubba_169 on 2008-11-30
For the life of me I cant figure this out. At home I use Code::Blocks on ubuntu and at Uni I have to use MS visual c++. I'm trying to write a console program that can be compiled by both and run correctly. I have had no problems so far, the only one I have come across is the way the UK pound sign (£) is stored.

In MSVC++ I have to use (char)156 to get their extended ascii value so cout << (char)156; works fine. In code::Blocks I can put the £ in a string so cout << "£1.00"; works great but I cant store it in a variable.

```
const char poundSign('£');
cout << poundSign << "1.00";
```

will just display a question mark in the terminal where the £ should be? Also the ascii value of the £ seems to differ between code::blocks and MSVC++. Any ideas what I can change so that it works on both? Even if I had to change the value of the poundSign variable for it to compile I wouldn't mind.

---

### Post by bubba_169 on 2008-11-30
Hmmmm using const string poundSign("£") seems to work

---

### Post by wmcbrine on 2008-11-30
The thing to realize is, there's no such thing as "extended ASCII". Once you get beyond ASCII, there are a variety of character sets to deal with. When you say that the pound sign is character 156, that's only true in the DOS-style code page you're using in the console -- not even in the so-called "ANSI" character set used elsewhere in Windows.

Ubuntu uses UTF-8 as its character set. This is a variable-length encoding of Unicode, where (conveniently) ASCII values still map to single bytes. However, for values outside the ASCII range (0-127), multiple bytes are required. Consequently, these characters cannot be represented in an old-style char, which is a single byte. The pound sign is 0x00a3 (163) in Unicode, which in UTF-8 requires two bytes. The string works because it's actually a multi-byte sequence containing the single UTF-8 character.

There are ways around your problem, but it can get somewhat complicated. For now, you might just want to ifdef it.

---

### Post by bubba_169 on 2008-11-30
That makes sense :D thanks for your time! I think I'll just stick with it as a string for now...

---

