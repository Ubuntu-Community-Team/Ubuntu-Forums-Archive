---
title: "Photo editing with python."
date: 2009-07-26
forum: Programming Talk
---

### Post by Godd on 2009-07-26
Hey.

I have an idea for a neato cryptography script but I need to find a module that handles pictures first.

The idea would be to convert a photo greyscale first. And since all colors are callable by a hex code, go through the list of colors in sequence and remove the corresponding colors to encode a binary data sequence. 

Then, by reading the sequence of present and non-present colors, glean said data from the picture.

The problem is I don't know of a module that is able to handle photo manipulation in such a manner and consequently am not able to even start scripting.

Can someone point me in the right direction?

EDIT: As soon as I posted this I found what I was looking for. Ha. Python Imaging Library. Sorry to post too hastily. Searched for the wrong thing.

---

### Post by manualqr on 2009-07-26
PIL (python imaging library) should be perfect.

edit:
sorry for missing your edit

---

