---
title: "looping in C..."
date: 2008-03-19
forum: Programming Talk
---

### Post by provisional_idiot on 2008-03-19
so im trying to write a nested for loop:

```

#define EMPTY 0
int board[7][7];
int countx, county;
for (county=0; county < 7 ; county++)
{
	for (countx=0; countx < 7 ; countx++)
	{
		printf("(%d,%d) ", countx, county);	
		board[countx][county]=EMPTY;
	}
}

```

which does everything correctly...however if I change those 7's to 8's in the for statement, I get an infinite loop and I have no idea why

in particular county does NOT increment, why I dont know

---

### Post by cb951303 on 2008-03-19
it's not infinte. it's just a big random number ;)

---

### Post by mike_g on 2008-03-19
You should be aware that by setting the loops to run to 8 you will be writing out of buffer. Maybe try resizing your arrays as well.

---

### Post by provisional_idiot on 2008-03-19
resizing the array did the trick, however it seems like a waste of memory to allocate space for an additional 17 integers that I'll never use....

---

### Post by jespdj on 2008-03-19
The array 'board' has only 7 x 7 = 49 elements. If you change the 7's in the loops to 8's, then you are trying to access elements in the array that don't exist. You can't do that without getting strange results.

If you let the loops run from 0 to 7 (instead of 0 to 6), then you'll ofcourse also need to change the size of the 'board' array.

---

### Post by LaRoza on 2008-03-19
Instead of hardcoding the values, you might want to use a #define, so you only have to track one number.

---

### Post by pmasiar on 2008-03-19
One of basic [http://en.wikipedia.org/wiki/Code_smell](http://en.wikipedia.org/wiki/Code_smell) criteria is using "magic numbers", like your 7. Always should be #defined

---

### Post by fyplinux on 2008-03-19
> **LaRoza said:**
> Instead of hardcoding the values, you might want to use a #define, so you only have to track one number.

And countx and county are not good naming style, they are somehow too similar that only have one different character, you may easy to get lost.

---

### Post by LaRoza on 2008-03-19
> **pmasiar said:**
> One of basic [http://en.wikipedia.org/wiki/Code_smell](http://en.wikipedia.org/wiki/Code_smell) criteria is using "magic numbers", like your 7. Always should be #defined

Thanks for that article. (Naturally, I clicked on links in it as well)

I liked the God Object, it sounded like a fitting subject for Xkcd.

Back to subject:

You could also use const if you are using the latest C standard.

---

### Post by LaRoza on 2008-03-19
> **fyplinux said:**
> And countx and county are not good naming style, they are somehow too similar that only have one different character, you may easy to get lost.

You are right, I didn't see those two variables, and got a little confused for a moment.

xcount and ycount may be better.

Also, declaring multiple variables on a single line isn't (IMO) a good thing to do

---

### Post by pmasiar on 2008-03-19
> **LaRoza said:**
> Thanks for that article. 

If you are in "education mode", you may dive into original wiki - Portland Pattern Repository (for code patterns) c2.com. You can see that Ward Cunningham registered domain really early, in '95, way before own domain was cool thing to have :-) 

[http://c2.com/xp/CodeSmell.html](http://c2.com/xp/CodeSmell.html)

Be careful, don't spend whole weekend there, your brain might burst :-)

---

