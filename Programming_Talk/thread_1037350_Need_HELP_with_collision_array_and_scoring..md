---
title: "Need HELP with collision array and scoring."
date: 2009-01-11
forum: Programming Talk
---

### Post by Waylon777 on 2009-01-11
Hi, I'm making a spaceship shooting game and I don't know how to do a collision array and scoring for this one. For the collision, when the shots collides with one of the players, the player will blow up with the image explosion. For the scoring, it has to count how many kills, and if you kill the opponent 3 times, the game will post "Player!@#!@ wins!" with the applause music. Also it's a Ready To Program Java File.

---

### Post by sandyd on 2009-01-11
Welcome to ubuntuforums.org ;)
the code below isn't supposed to work out of the box. its just to give you an idea of how to do it.

shot.java
```

import java.awt.Graphics;

import java.awt.Color;



public class Shot

{

        int score = 1;
	private int x_pos;

	private int y_pos;



	private final int radius = 3;



	public Shot(int x, int y)

	{

		x_pos = x;

		y_pos = y;

	}



	public int getYPos()

	{

		return y_pos;

	}



	public void moveShot(int speed)

	{

		y_pos += speed;

	}



	public void drawShot(Graphics g)

	{

		g.setColor(Color.yellow);

		g.fillOval(x_pos, y_pos, radius, radius);

                Rectangle2D.Float shot new Rectangle2D.Float(x_pos, y_pos, radius, radius );//all in one line//this draws floating rectangle
                if (shot.intersects (ship)) {
//insert your destruction code here(if missile intersects ship then.....)
                score =score +1;
}
	}

}

```. 
enemy.java
```

import java.awt.Graphics;

import java.awt.Color;



public class Enemy

{

    // Variables

    private int x_pos;

    private int y_pos;



    public Enemy (int x, int y)

    {

	x_pos = x;

	y_pos = y;

    }





    public void moveX (int speed)

    {

	x_pos += speed;

    }





    public void moveY (int speed)

    {

	y_pos += speed;

    }





    public Shot generateShot ()

    {

	Shot shot = new Shot (x_pos, y_pos);



	return shot;

    }





    public int getX_pos ()

    {

	return x_pos;

    }





    public int getY_pos ()

    {

	return y_pos;

    }





    public void drawEnemy (Graphics g)

    {
	


	/*

		g.setColor (Color.red);

		int[] x_poly = {x_pos, x_pos - 10, x_pos, x_pos + 10};

		int[] y_poly = {y_pos, y_pos - 15, y_pos - 10, y_pos - 15};

		g.fillPolygon (x_poly, y_poly, 4);

	*/
		Rectangle2D.Float ship new Rectangle2D.Float(x_pos, y_pos, x_pos-20, y_pos-20 );//all in one line//this draws floating rectangle
		

    }

}



```


now for a little explanation...
this is the main part of the colission code
```

Rectangle2D.Float shot new Rectangle2D.Float(x_pos, y_pos, radius, radius );
                if (shot.intersects (ship)) {

                score =score +1;
}

```
a floating rectangle called "shot" is drawn at the place where you click. 

The ship
```

Rectangle2D.Float ship new Rectangle2D.Float(x_pos, y_pos, x_pos-20, y_pos-20 );//all in one line//this draws floating rectangle


```
The ship is also enclosed within a floating rectangle.  when the ship's floating rectangle intersects the circle's, the ship is destroyed. ive also added the scoring part so each time a ship's floating rectangle collides with the missile's a score is added. 

Thats for the colissions...
I don't know much about the destruction part and the arrays so maybe someone else with more knowledge could help with the arrays and the destruction?

carlee

---

### Post by sandyd on 2009-01-11
ooops
i forgot something
now for the rest of scorring
```

if (shots := 3 ) {
g.drawString(blablabla);
}

```

---

### Post by Waylon777 on 2009-01-11
Thank you Carlee

---

