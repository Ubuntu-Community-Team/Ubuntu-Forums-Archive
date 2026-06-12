---
title: "[php] number loop"
date: 2010-10-15
forum: Programming Talk
---

### Post by ELD on 2010-10-15
Okay i'm trying to implement a rating system on my website admins can use to rate directory items.

There will be radio buttons from 1-5 for graphics, sound etc. So if i  choose 1 for poor graphics then the number 1 goes into the field  "graphics" as a "1".

I then have two different star images, one yellow and one semi  transparent. I want to be able to go from 1-5 outputting the right  number of yellow stars that corresponds to the number in the database  and anymore up to 5 the semi transparent stars.

Make sense at all?

Cheers.

---

### Post by frankos44 on 2010-10-15
Sort of. It sounds like your front end needs to be client side scripted rather than posting back and fourth to php. jQuery makes this a lot easier than pure javascript alone. There are lots of cool interface solutions. Google jQuery - Have fun!

---

### Post by ELD on 2010-10-15
> **frankos44 said:**
> Sort of. It sounds like your front end needs to be client side scripted rather than posting back and fourth to php. jQuery makes this a lot easier than pure javascript alone. There are lots of cool interface solutions. Google jQuery - Have fun!

I'm not looking for javascript.

Looking for a simple loop to go through the numbers and echo out to the browser the right stars, it's all pre-defined in the database.

---

### Post by spjackson on 2010-10-15
> **ELD said:**
> I'm not looking for javascript.

Looking for a simple loop to go through the numbers and echo out to the browser the right stars, it's all pre-defined in the database.
The number in the database will be 0,1,2,3,4 or 5 yes? And suppose it's 3, then you will output 3 yellow stars followed by 2 sem-transparent one, yes?

That sounds very simple. What code do you have so far?

---

### Post by hobbestec on 2010-10-15
instead of figuring out how many star image files to print out you could also make 6 different images each with the right combination of stars, one with no stars, one star, two stars, three stars, etc and when you get that number print out the right thing like img src = onestar.gif or whatever.

---

### Post by James78 on 2010-10-16
Better yet, using CSS, you could define background images, and define CSS classes, 1 star, 2 star, etc, and in PHP, just output the CSS class, class="1star", and it's done and done.

P.S. [http://www.komodomedia.com/blog/2006/01/css-star-rating-part-deux/](http://www.komodomedia.com/blog/2006/01/css-star-rating-part-deux/)

---

### Post by ELD on 2010-10-16
> **spjackson said:**
> The number in the database will be 0,1,2,3,4 or 5 yes? And suppose it's 3, then you will output 3 yellow stars followed by 2 sem-transparent one, yes?

That sounds very simple. What code do you have so far?

Nothing, the point of me posting here :P

> **hobbestec said:**
> instead of figuring out how many star image files to print out you could also make 6 different images each with the right combination of stars, one with no stars, one star, two stars, three stars, etc and when you get that number print out the right thing like img src = onestar.gif or whatever.

Don't know why i didn't think of that - easily the easiest solution.

> **James78 said:**
> Better yet, using CSS, you could define background images, and define CSS classes, 1 star, 2 star, etc, and in PHP, just output the CSS class, class="1star", and it's done and done.

P.S. [http://www.komodomedia.com/blog/2006/01/css-star-rating-part-deux/](http://www.komodomedia.com/blog/2006/01/css-star-rating-part-deux/)

I know easily how to make everything in CSS for it, but without the php code to actually tell it what to do - it's useless - again the point of me posting here :)

---

### Post by James78 on 2010-10-16
Not tested, but should get the idea across. Hopefully I got the right idea of what you wanted to do.
[php]$num = 5
for ($i = 1; $i <= $num; $i++) {
    if ($i == $num) {
        echo '<ul><li class="' . $i . 'star"></li></ul>'
    }
}[/php]

---

