---
title: "Java help"
date: 2010-09-02
forum: Programming Talk
---

### Post by leprkhn on 2010-09-02
I am doing the Stanford Engineering Everywhere CIS106a Java class found [HERE]("http://see.stanford.edu/see/courseinfo.aspx?coll=824a47e1-135f-4508-a5aa-866adcae1111").
Using Eclipse, whenever I run an application the window it creates is about 100x100, and can't be made any larger. Or rather... when dragging out the window to be larger, the background (and it's contents - most of which are located off of the canvas due to window size) doesn't expand. I am left with a larger window with a 100x100 white box in the upper left hand corner. The rest is just grey and doesn't display any of the objects I created.

Below is the source, attached are screenshots.
```

/*
 * File: Target.java
 * Name: 
 * Section Leader: 
 * -----------------
 * This file is the starter file for the Target problem.
 */

import acm.graphics.*;
import acm.program.*;
import java.awt.*;
	
public class Target extends GraphicsProgram {
	
/** Define number of pixels per inch to be equal to 96. */
	private static final int PIXELS_PER_INCH = 96;

/** Define pixel radius for outer circle */
	private static final int OUTER_CIRCLE_RADIUS = 96;
/** Define pixel radius for middle circle (we know it to have a .65 inches radius) */
	private static final int MIDDLE_CIRCLE_RADIUS = (int)(PIXELS_PER_INCH * .65);
/** Define pixel diameter of inner circle (we know it to have a  0.3 inches radius) */
	private static final int INNER_CIRCLE_RADIUS = (int)(PIXELS_PER_INCH * .3);
	
	public void run() {
		drawTarget(50, 50);				// Draws a target at the X and Y coordinates provided.
	}
	
	private void drawTarget(int beginningX, int beginningY){
		/*
		 * Draws a target at supplied x,y coordinates. Oval size determined by *_RADIUS constants.
		 */
		int outerDiameter = (OUTER_CIRCLE_RADIUS * 2);			// d = 2r
		int middleDiameter = (MIDDLE_CIRCLE_RADIUS * 2);
		int innerDiameter = (INNER_CIRCLE_RADIUS * 2);
		/*
		 * Determine the number of pixels to inset the next oval
		 * inset = size of outer - size of current / 2 (equal space on either side)
		 */
		int middleInset = ((outerDiameter - middleDiameter)/2);
		int innerInset = ((outerDiameter - innerDiameter)/2);
		/*
		 * Set the beginning x,y values for each circle.
		 */
		int beginOuterX = beginningX;
		int beginOuterY = beginningY;
		int beginMiddleX = (beginningX + middleInset);
		int beginMiddleY = (beginningY + middleInset);
		int beginInnerX = (beginningX + innerInset);
		int beginInnerY = (beginningY + innerInset);
		/*
		 * Make each ring. Outer and Inner are red, Middle is white.
		 */
		GOval outerRing = new GOval(beginOuterX, beginOuterY, outerDiameter, outerDiameter);
		outerRing.setColor(Color.RED);
		outerRing.setFilled(true);
		outerRing.setFillColor(Color.RED);
		GOval middleRing = new GOval(beginMiddleX, beginMiddleY, middleDiameter, middleDiameter);
		middleRing.setColor(Color.WHITE);
		middleRing.setFilled(true);
		middleRing.setFillColor(Color.WHITE);
		GOval innerRing = new GOval(beginInnerX, beginInnerY, innerDiameter, innerDiameter);
		innerRing.setColor(Color.RED);
		innerRing.setFilled(true);
		innerRing.setFillColor(Color.RED);
		/*
		 * Add each circle to the canvas.
		 */
		add(outerRing);
		add(middleRing);
		add(innerRing);
	}
}

```

Any help would be greatly appreciated.

---

### Post by astx813 on 2010-09-06
Hey, lepkhn, I've been taking a look at CS106 over the past few days, myself.  I've cobbled together some understanding of Java, but figured this would be something a little more formal.  I took a similar approach, but you're putting the target at a fixed position of 50,50.  The assignment is to put the logo in the center of the screen.  So if you calculate that out, it should fit in a 100x100 window.  Also, the description assumes 72 px/in, so I went with that (but, like you, I stored the px/in as a constant and calculated the radii of the circles based on that).

---

### Post by kahumba on 2010-09-06
If you could put the whole project for people to be able to reproduce it probably someone would post a working solution.

---

### Post by leprkhn on 2010-09-06
I'm actually more concerned with setting the size of a window.

According to [THIS]("http://mcis.western.edu/freejavabook/2_ACM_Java_Graphics.pdf") pdf, I should be able to set a static window size using the constants APPLICATION_WIDTH and APPLICATION_HEIGHT, but this does not work for me.

Anyone know how to set a specific window size?

---

### Post by leprkhn on 2010-09-27
Pshaw...
I figured it out.
You can set the application width and height in the file properties. Not sure why it won't let me change those parameters in the code, but there it is.

File > Properties > Run/Debug Settings > "File Name" > Edit > Parameters Tab

---

