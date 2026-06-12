---
title: "Xbox 360 C# game programming on Ubuntu?"
date: 2011-08-31
forum: Programming Talk
---

### Post by F1r3st0rm on 2011-08-31
I know one is supposed to download XNA Game Studio to program games for the Xbox 360, but I am pretty sure it does not work on Linux. My question is will MonoDevelop or some other C# IDE support porting your games to the xbox?

Thanks for reading.

---

### Post by CrimsonTurkey on 2011-08-31
MonoDevelop would be your best bet XNA is a framework for game development and XNA Game Studio is a addon for Visual Studios but i believe you can develop XNA games with Mono on Linux

---

### Post by directhex on 2011-08-31
If you only need 2D support, then there's a library at [https://github.com/mono/MonoGame](https://github.com/mono/MonoGame) which will allow you to write 2D XNA games with Mono on Ubuntu. Note: untested.

---

### Post by F1r3st0rm on 2011-08-31
Ok thank you all for your replies. I will build a game and see if I can port it to my Xbox. If not I'll just bring it over to my Windows computer and then port it.

---

### Post by forrestcupp on 2011-08-31
> **directhex said:**
> If you only need 2D support, then there's a library at [https://github.com/mono/MonoGame](https://github.com/mono/MonoGame) which will allow you to write 2D XNA games with Mono on Ubuntu. Note: untested.

I think that's for Windows Phone 7 and not for the 360.

If you really want to program for the 360, you need to just bite the bullet and use the real XNA in Windows. You wouldn't use a chainsaw to mow your yard, and you shouldn't try to use Linux to develop for a Microsoft game console.

---

### Post by Senesence on 2011-08-31
> **forrestcupp said:**
> If you really want to program for the 360, you need to just bite the bullet and use the real XNA in Windows. You wouldn't use a chainsaw to mow your yard, and you shouldn't try to use Linux to develop for a Microsoft game console.

Absolutely right.

---

### Post by directhex on 2011-09-01
> **forrestcupp said:**
> I think that's for Windows Phone 7 and not for the 360.

The selling point with XNA is it's the same thing - you just recompile the game for the target platform (Windows, WP7, 360)

> If you really want to program for the 360, you need to just bite the bullet and use the real XNA in Windows. You wouldn't use a chainsaw to mow your yard, and you shouldn't try to use Linux to develop for a Microsoft game console.

You can do the majority development fine in Ubuntu, but the final submission needs to be done with Windows (much like iOS apps need to be built on a Mac)

---

