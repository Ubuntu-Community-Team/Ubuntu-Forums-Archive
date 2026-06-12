---
title: "C Array of Strings and Sorting"
date: 2008-06-19
forum: Programming Talk
---

### Post by remu on 2008-06-19
Hello Everyone,

I read the FAQ, as well as the post regarding homework questions. I think that my question does not violate the rules...or I hope it doesn't.

Anyways, here goes:

I've been working on this code for a bit now, and I'm really stuck. What I need to do is give the user 3 Options upon running the program in the menu. 
Option 1, calculate the cost to purchase ingredients to make animal crackers. 
Option 2, read in the ingredients from a txt file for a batch of Chocolate Chip Cookies, and compare them to the list of the ingredients for the animal crackers and sort them into ingredients needed, and ingredients that we already have, and then display the name of the Chocolate Chip recipe, as well as display the ingredients needed and ingredients we already have.
Option 3, exit.

I was able to get the menu like the Instructor wanted, as well as Option 1.
I was also able to read in the ingredients from the txt file, however I ran into problems trying to get the sorting to work out, my idea was to search the ingredients for the Chocolate chip cookies against the ingredients we already have, and if NULL is returned, then to add the ingredient to the array of ingredients to be purchased, otherwise add it to the list of ingredients on hand.

Upon implementing this, I've completely messed Option 2 up...I think. I get a Segmentation Fault when I run option 2. I have attached the Source Code as well as the text file.

It's getting late, and I'm giving up on this for the night, but if someone could offer some hints, or guidance, it would really be appreciated. Unfortunately I only have this class once a week, and the next time I have it, it's due, and the Instructor never answers e-mails.

However, if this posting is against the rules, I apologize. (And for rambling :))

---

### Post by Can+~ on 2008-06-19
Well, there's a big mess on methods of manipulating the file, mixing fseek in there. Try to avoid fseek on text files.

[http://img.photobucket.com/albums/v517/CanXp/outofbounds.png](http://img.photobucket.com/albums/v517/CanXp/outofbounds.png)

I can't help you more, I'm pretty tired to do a full debug, but try rewriting that section using gets only. And try using STRUCTS to avoid having multiple arrays.

---

### Post by lisati on 2008-06-19
Salt appears to be missing from your array "ingredients". <edit>Is this done on purpose?</edit>

---

### Post by remu on 2008-06-19
Yea, I forgot to put salt in that array. Thanks lisati.
Can+~ thanks for the input, I'll try getting rid of fseek, and take a look at the methods again.

---

