---
title: "[SOLVED] Javascript File Parsing"
date: 2008-05-28
forum: Programming Talk
---

### Post by Mr.Macdonald on 2008-05-28
I am completeing my final project in Web page design (I don't want you to do it for me!)

I am trying to make dynamic pages and to do so i must use javascript because python php etc. would comprimise my teachers self image.

Can you, using javascript, parse a reletive html file and display its contents into a div (whatever that stands for). I know you can't read or write files but i was hoping that i could make a bunch of separate pages and display them based upon the users selection. similar to frames in html but without frames.

I need this so i don't have to write several web pages into javascript.

---

### Post by slavik on 2008-05-28
what you are reffering to is called AJAX, and divs have a field called innerHTML :)

wc3schools has everything on this subject with sample code.

---

### Post by Mr.Macdonald on 2008-05-29
Could i do AJAX on a computer without installing/downloading OR ANYTHING LIKE THAT. Because downloading is a violation of the class rules due to "security".

---

### Post by Jonne on 2008-05-29
it's just a javascript technique. I'd recommend using a framework like jquery, which makes it all a bit easier.

But IMHO there's no point in using AJAX if the information you're going to load is static anyway.

---

### Post by Mr.Macdonald on 2008-05-29
I used iframes to solve it

---

### Post by LaRoza on 2008-05-29
> **slavik said:**
> what you are reffering to is called AJAX, and divs have a field called innerHTML :)

wc3schools has everything on this subject with sample code.

*twitch* innerHTML isn't standard and it is a "MS" thing.

Try to stick with standard interfaces like the DOM.

---

### Post by Jonne on 2008-05-29
InnerHTML is supported by all browsers, and it has its uses. Using the DOM to add complex html is a pain. You have to watch out for differences between browsers sometimes, though (but then again, that's the case with pretty much everything).

---

### Post by Can+~ on 2008-05-29
> **Mr.Macdonald said:**
> I used **iframes** to solve it

Ugh.

---

### Post by LaRoza on 2008-05-29
> **Jonne said:**
> InnerHTML is supported by all browsers, and it has its uses. Using the DOM to add complex html is a pain. You have to watch out for differences between browsers sometimes, though (but then again, that's the case with pretty much everything).

"All browsers"? Will it be in the future? Using the DOM may take a little more code, but that is easy to abstract away.

---

### Post by slavik on 2008-05-29
> **LaRoza said:**
> *twitch* innerHTML isn't standard and it is a "MS" thing.

Try to stick with standard interfaces like the DOM.
it works on firefox ...

---

### Post by LaRoza on 2008-05-29
> **slavik said:**
> it works on firefox ...

Proprietary markup and API's are a poor practice. Not everyone uses firefox (I don't, although I test in it)

---

