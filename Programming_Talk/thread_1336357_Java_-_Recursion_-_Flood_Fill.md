---
title: "Java - Recursion - Flood Fill"
date: 2009-11-24
forum: Programming Talk
---

### Post by PaulM1985 on 2009-11-24
Hi

I am using Java to write a program that will perform flood filling.

The code I am using at the moment is:

```

private static void floodFill(BufferedImage aGreyImage, BufferedImage aColourImage, BufferedImage aEdgeImage, int aX, int aY)
	{
		tester++;
		System.out.println("tester is " + tester);
		if (tester > 10000)
			return;

		if (aX < 2 || aX > aEdgeImage.getWidth() - 1 || aY < 2 || aY > aEdgeImage.getHeight() - 1)
			return;

		Color colour = new Color(aEdgeImage.getRGB(aX, aY));

		if (colour.getRed() < 25 && aGreyImage.getRGB(aX, aY) != aColourImage.getRGB(aX, aY))
		{
			aGreyImage.setRGB(aX, aY, aColourImage.getRGB(aX, aY));

			if (aX > 2 && aX < aEdgeImage.getWidth() - 2 && aY > 2 && aY < aEdgeImage.getHeight() - 2)
			{
				floodFill(aGreyImage, aColourImage, aEdgeImage, aX, aY - 1);
				floodFill(aGreyImage, aColourImage, aEdgeImage, aX - 1, aY);
				floodFill(aGreyImage, aColourImage, aEdgeImage, aX, aY + 1);
				floodFill(aGreyImage, aColourImage, aEdgeImage, aX + 1, aY);
			}
		}
	}

```

It seems that I am getting an error. Because I seem to be unable to catch the error, I think it is because I am calling floodFill and going too deep into the stack.

Would anyone else be able to comfirm whether this may be the case and know of some work around?

The only bit of the errors I am able to get are the ones that point to the lines where flood fill is called again.

Paul

---

### Post by Zugzwang on 2009-11-24
Why don't you try using a debugger? This way, you can inspect the stack when a stack overflow occurs.

---

### Post by CptPicard on 2009-11-24
Care to post your error? "Stack overflow" or something?

Yes, your floodfill may well do that. I would probably change the algorithm to making use of a queue, and going breadth-first around an "edge" of the filled region. Look for "breadth-first search/traversal" or something :)

---

### Post by Reiger on 2009-11-24
EDIT:
Actually the best thing would probaly to do for loops in all 4 directions and only call your algorithm recursively on (x-1,y-1); (x+1,y-1); (x+1,y+1); (x-1,y+1).
EDIT2: And I did not know the Java compiler would accept "return;" like that? I always had that fail on me even in void methods?

---

### Post by Zugzwang on 2009-11-24
> **Reiger said:**
> In Java you cannot do "return;". You must restructure your program flow.

Why shouldn't you be able to do that? Looks syntactically valid.

---

### Post by Reiger on 2009-11-24
I edited it.

---

### Post by PaulM1985 on 2009-11-24
> **CptPicard said:**
> Care to post your error? "Stack overflow" or something?
I was running out of terminal and was cut too many lines short of the actual error.  I was just getting errors showing the position of the error in my code. Debug would have been useful but thiswas a lunchbreak project.  Running using -ss(largenumber)seemed to make it run longer so it looks like it must be too deep.

Thanks for breadth first advice. I will look into it.

---

