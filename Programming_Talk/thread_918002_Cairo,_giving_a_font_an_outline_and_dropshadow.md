---
title: "Cairo, giving a font an outline and dropshadow"
date: 2008-09-12
forum: Programming Talk
---

### Post by llevering on 2008-09-12
For a new project I am using clutter and cairo with Python as scripting language. A part of this program contains slides and in these slides I want to create clearly readable letters. Therefore I want to give them a border/outline and make a dropshadow. For an example see the picture that is attached (it as some anti-aliasing issue, but to give you an idea).

I am trying and thinking for more than an afternoon how to accomplish this wil Cairo. I thought first writing the text with a bigger font in black and then with a smaller font in white (with a little offset). This works for the 'outside' of the letters (if carefully and with every letter positioned separately). However this doesn't work to create the desired effect on the letters that have an opening on the inside like a, b, d, etc. 

I thought of the dropshadow by placing the same text with a small offset and that  using a mask with a curved gradient to create a dropshadow effect, however this doesn't seem to be the best way to create it.

I already searched the internet for libraries that could accomplish something like this, however I was not able to find them. Maybe I am totally looking in the wrong direction and should I use other libraries as clutter and cairo to accomplish something like these, I am quite new to the Python world. Is there anybody with ideas, how to accomplish this with clutter/cairo or if needed with another library?

---

### Post by mike_g on 2008-09-12
Why not use a bitmap font? You could save yourself a lot of time and would probably come up with a nicer looking font, by drawing it to a tiled PNG in the GIMP or something. Bitmap fonts also render a lot faster than if you're drawing procedurally :)

---

### Post by jamescox84 on 2008-10-17
Sorry for the late reply. But this is an idea that might help you, if you did want to draw a dropshadow proceduraly. You just need to stroke the path with progressivly shrincking strokes (13px to 3px step 2 maybe) to create the drop shadow. Use somthing like a (0, 0, 0, 0.1) for the color of the strokes. Once you have done this draw the actual path ontop of this.  Hopes this helps, even if it is a little too late.

---

