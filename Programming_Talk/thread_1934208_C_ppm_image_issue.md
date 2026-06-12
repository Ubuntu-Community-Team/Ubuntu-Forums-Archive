---
title: "C ppm image issue"
date: 2012-03-01
forum: Programming Talk
---

### Post by tennvolsmb on 2012-03-01
Okay so I'm trying to make a ppm image for a class that creates 3 vertical bars of different colors (similar to how the French flag looks) but every time I run my code I get slanted bars...

Any help would be greatly appreciated!

```

#include <stdio.h>

void make_pixel(int r, int g, int b)
{
	printf("%c%c%c", r, g, b);
}

void make_ppm_header(int width, int height)
{
	printf("P6\n");
	printf("%d %d %d\n", width, height, 255);
}

void make_ppm_image(int width, int height)
{
	int count, hcount;
	make_ppm_header(width, height);
	int size = height * width;
	for(hcount = 0; hcount <= height; hcount++)
	{
		for(count = 0; count < width * 1 / 3; count++)
		{
			make_pixel(128, 192, 85);	
		}
		for(count = count; count < width * 2 / 3; count++)
		{
			make_pixel(84, 92, 139);
		}
		for(count = count; count <= width; count ++)
		{
			make_pixel(74, 29, 84);
		}
	}
}

int main()
{
	int height = 133, width = 200;
	make_ppm_header(width, height);
	make_ppm_image(width, height);

	return 0;
}

```

---

### Post by tennvolsmb on 2012-03-01
Oh and I kind of need to stick to the basic principle outline of my code already.
Thanks

---

### Post by r-senior on 2012-03-01
There are two problems:

1. Your header is wrong
2. Your loops are wrong

You'll kick yourself. Twice. ;)

I changed all the colour to white so I could see the pixel values more easily in a hex dump. You have a bad patch in the top left corner (that you may not have noticed). This is the first few bytes, i.e. the header.

```

$ hexdump temp.ppm | head -3
0000000 3650 3220 3030 3120 3333 3220 3535 5020
0000010 2036 3032 2030 3331 2033 3532 2035 ffff
0000020 ffff ffff ffff ffff ffff ffff ffff ffff

```

Here's your clue: 50 is the hex ASCII code for 'P'.

But fixing that just removes the glitch in the top left corner. It doesn't fix the diagonals. Now what would produce an offset of one column for every row? How many pixels would you have to be off on each row to get a diagonal effect?

Before you answer, count to ten: 0 1 2 3 4 5 6 7 8 9 10

Otherwise good job! Neatly formatted and easy to read.

ps. I changed the colours to get the French flag.

---

### Post by Lokireloaded on 2012-03-01
You're calling the header function twice, once in the main function and once again in the second function you call.

---

### Post by r-senior on 2012-03-01
The idea, given that it's for a class and the forum is not for doing homework, was to give clues rather than answers. ](*,)

---

### Post by Lokireloaded on 2012-03-01
Apologies, I kinda derped and didn't read. Serves me right for diving right into the code first! :oops:

---

### Post by r-senior on 2012-03-02
No problem. Fixing that doesn't fix the diagonal stripes anyway. ;)

---

### Post by ve4cib on 2012-03-02
Think about array how you walk through an array in C.  Do you use this loop:

```
for(i=0; i<=array_length; i++)
    printf("%d\n",array[i]);
```

Or do you use this loop:

```
for(i=0; i<array_length; i++)
    printf("%d\n",array[i]);
```

You can think of each row as an array of pixels, so you want to walk through them using the same kind of look as you'd use for any other array.

---

### Post by Lokireloaded on 2012-03-03
> **r-senior said:**
> No problem. Fixing that doesn't fix the diagonal stripes anyway. ;)

I know that. but it's always the small things that trip me up.
I can remember many a time forgetting to put the & before a variable in a scanf function.

---

