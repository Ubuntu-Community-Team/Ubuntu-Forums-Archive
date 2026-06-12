---
title: "How do you get Spanish accents on a US keyboard in 13.04?"
date: 2013-10-28
forum: New to Ubuntu
---

### Post by janl162 on 2013-10-28
How do you get Spanish accent marks on a US English keyboard in Ubuntu 13.04? (Or 13.10, since I'm about ready to update.)

I've found instructions from back in 2008 for how to do it in Gnome, but how do you do it in Unity? The options recommended don't seem to exist.

Thanks in advance

- Janet.

---

### Post by janl162 on 2013-10-28
I figured it out:

Settings>Keyboard Layout>+>English (US international with dead keys)

That pretty much solves it.

---

### Post by janl162 on 2013-10-28
Oh. Then you need to use the arrows at the bottom to promote it to the top.

---

### Post by Impavidus on 2013-10-29
The five basic ways to solve this:
- Use a graphical selector, use some copy-paste work. Really slow, you don't want that if you are typing in a language with many accents, but easy to remember.
- Use a keyboard layout with the accented character. Inconvenient if it differs too much from your real layout, or if you have to switch layout too often.
- Use hexadecimal Unicode code points: press <ctrl>+<shift>+u, f, 1, <space> &#8594; ñ. You have to remember the codes, but can access every character defined.
- Use dead keys: press <dead ~>, n &#8594; ñ. Many people's favorite.
- Use compose: press <compose>, ~, n &#8594; ñ. My favorite, as it provides much more than just the accented characters whilst staying intuitive, like the arrows in this post (<compose>, -, >).
Of course, you can use any combination of these techniques.

---

