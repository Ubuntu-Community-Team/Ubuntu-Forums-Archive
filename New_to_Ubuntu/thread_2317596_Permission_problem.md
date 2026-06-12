---
title: "Permission problem"
date: 2016-03-18
forum: New to Ubuntu
---

### Post by stevemid on 2016-03-18
I installed the nautilus-image-converter to resize images with this command: 
sudo apt-get install nautilus-image-converter
This should allow me to right click on an image to resize it.
However when I now right click on a jpeg file to covert it I get an error message that the file cannot be resized and to check whether I have permission to write to this folder
I have RW permissions on the file as well as the enclosing folders (see attached screen print.) I also changed the permission on the file itself to RW for "others" but that had no effect

What am I doing wrong? [ATTACH=CONFIG]267862[/ATTACH]

I am the only user on this computer so I'm assuming that I am me and as such would own everything. However, I would appreciate any pointers to documentation that would explain all this.

---

### Post by deadflowr on 2016-03-18
When resizing, what option are you selecting.
There should be 3 options, 
1) select a size; which let's you convert to a preset size. ie 96x96, or 1024x768, or a few others.
2)scale, in which the image gets scaled up or down by a percentage.
3) custom size. where you can resize based upon your own whims

The thing that tends to happen is that if you don't select the proper action, it goes with the default, which it #1.
And if you don't make a selection of a preset size offered in the dropdown it gives it errors since you cannot resize to nothing.

.
Does that make sense.

---

### Post by stevemid on 2016-03-19
deadflowr, you are correct! Thank you.  In the dialogue, under Image Size, the radio button for Pixels is pre-selected.  I didn't enter a value into the 'pixels option' for image size.  Thus the app had nothing to execute.  I was concentrating on the scale option which was prefilled to 50% BUT I was neglecting to change the radio button to execute scaling.  The error message to check permissions is a bit oblique; it might have said "enter a value in the pixels option or select scaling."  But thank you.  Once again, operator error

---

