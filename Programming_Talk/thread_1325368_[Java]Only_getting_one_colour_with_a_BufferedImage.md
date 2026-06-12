---
title: "[Java]Only getting one colour with a BufferedImage"
date: 2009-11-13
forum: Programming Talk
---

### Post by Moustacha on 2009-11-13
I'm having trouble trying to get a colour other than blue with a BufferedImage

So I've got my buffered image, and just for testing I've got a loop to colour in the top left corner, however no matter what RGB value i set, it only colours in blue. Changing the value changes how bright the blue is.

```
static BufferedImage I = new BufferedImage(X, Y, BufferedImage.TYPE_INT_RGB);

...

for (int i = 0; i<100; i++)
		{
			for (int j = 0; j < 100; j++)
			{
				I.setRGB(i,j,100);
			}
		}
		Frame f = new Frame("Mandelbrot");
		f.add("Center", new MandelCanvas());
		f.setSize(X,Y);
		f.setVisible(true);

...

class MandelCanvas extends Canvas
{
   public void paint(Graphics g)
   {
	   g.drawImage(Mandelbrot.I, 0, 0, null);
   }
}
```

Is there some special voodoo magic I'm missing?

---

### Post by Reiger on 2009-11-13
You are using setRGB(x,y, colorCode) method which requires a colour code which in *hexadecimal* looks like this: RRGGBB. E.g.: 0xFF0000, 0x00FF00, 0x0000FF.

And you are working with decimal values that are clearly less than 256 and therefore in the all-blue part of the colour code format.

---

### Post by Moustacha on 2009-11-13
Thank you very much. Using a bit-shift seems to make it work well.

---

### Post by PaulM1985 on 2009-11-14
What I tend to use is

setRGB(i, j, new Color(r, g, b).getRGB());

That way I am able to choose the actual values for red, green and blue.

---

