---
title: "IBus Problems"
date: 2016-10-13
forum: Programming Talk
---

### Post by 7husky on 2016-10-13
Hi,
I have a Problem with Ibus. I want to make it possible to write Chinese in an Application. I have created the Application with Visual Studio and Run it with mono on Ubuntu Mate 16.04. The Ibus version is 1.5.11.
But now I have 2 Problems.
IBus with Pinyin works quite well in FireFox, Libre Office etc.
But I have problems with my own Application. If I run my Application normally, Ibus works quite well, but I have to run my Application as sudo.
And then Ibus doesn't turn on.
My Second Problem is that Chinese Charakters in my Application were shown as []. But in Applications like FireFox usw. they were Shown right.

Do you have any suggestions?

Best regards,
Julian

---

### Post by mcgbb on 2016-10-21
Can't help with the Ibus problem but might be able to help with the second problem.  Its something that I have already come across developing an application that requires Japanese characters.

On Windows, a .NET program will use the selected font unless its trying to display a character that doesn't exist in that font.  At that point it will resort to a backup font that does contain the required characters, and so gives a consistent output. 
On Mono under Linux, this sometimes doesn't happen.  
It may be that your Linux doesn't have a font installed that supports Chinese characters, and so cant fall back.  Try installing a font with Chinese character support and try again.
It could also be that the Mono text renderer isn't handling the font fall back properly, in which case probably the easiest way round this is to explicitly specify a font in your application that supports all the characters you want to display, then ensure the font is distributed with your application (check the licensing).  
You can install a ttf file on Linux by copying it into the /usr/share/fonts/ folder then running fc-cache
Firefox can pull its fonts from the web which is probably why they work find in the browser.

---

