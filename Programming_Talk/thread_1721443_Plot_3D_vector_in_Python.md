---
title: "Plot 3D vector in Python"
date: 2011-04-04
forum: Programming Talk
---

### Post by anton_09 on 2011-04-04
Dear All,
I have a set of data (x,y,z) for 40 3Dvectors. I would like to plot 3D vector Using python.
Could you please help me ?
Thanks.

---

### Post by Chimes on 2011-04-05
google is your friend

check out numpy in general for scientific data wielding. That said.

[http://wiki.python.org/moin/NumericAndScientific/Plotting](http://wiki.python.org/moin/NumericAndScientific/Plotting)

this project's development died two years ago but was well developed and has good examples.
[http://code.enthought.com/projects/mayavi/docs/development/html/mayavi/mlab.html](http://code.enthought.com/projects/mayavi/docs/development/html/mayavi/mlab.html)

If you want to be cutting edge:
[http://pyla.codeplex.com/](http://pyla.codeplex.com/)

---

### Post by anton_09 on 2011-04-05
Let me see how it works. Do I have to install  any thing beside Python?
Thanks a lot

---

### Post by dazman19 on 2011-04-08
I have not done this in python. So i cant help you with syntax. But i have done it in java so i jave an idea on theory. My understanding was that a vector that is used to render a 3d image is made up of 3(4) things.

an x, y, z co-ordinate. And it has a direction, but you don't need to specify this on the vector class. Generally calculating the distance between 2 3Dpoints will help you. 

I can give you a java example, but you will need to get someone else to help you in python: 

I hope you can understand this java code. I will comment it where i can.

```

public double Pdistance(Point3D p1, Point3D p2) { //returns the distance between two points in 3D space. 
		Point3D tmp = new Point3D();
		tmp.x = p1.x - p2.x;
		tmp.y = p1.y - p2.y;
		tmp.z = p1.z - p2.z;
		double retval = Math.sqrt((tmp.x * tmp.x) + (tmp.y * tmp.y) + (tmp.z * tmp.z));
		
		return retval;
	}

//and to give you an idea of the point3d object:

public class Point3D{ //Start of POINT3D Class
	public double x;
	public double y;
	public double z;
	Point3D(){ x=0.0; y=0.0; z=0.0; } //default constructor
	Point3D( double x, double y, double z ){ this.x= x; this.y= y; this.z= z; } //double constructor
	Point3D( int x, int y, int z ){ this.x= x; this.y= y; this.z= z; } //int constructor

	public Point2D projectPoint(){//method of Point3D
	    Point2D retval = new Point2D();
	    double tmpx = screenPosition.x + x * cosTheta - y * sinTheta;
	    double tmpy = screenPosition.y + x * sinTheta + y * cosTheta * sinPhi + z * cosPhi ;
	    double temp = viewAngle.z / (screenPosition.z + x * sinTheta * cosPhi + y * cosTheta * cosPhi - z * sinPhi );
	    retval.x = xScreenOrigin + (int)(modelScale * temp * tmpx );
	    retval.y = yScreenOrigin + (int)(modelScale * temp * tmpy );
	    return retval;
	}
	
	public double magnitude(){
	    return Math.sqrt( x * x + y * y + z * z );
	}
	
	public double dotProduct( Point3D b ){
	    return x * b.x + y * b.y + z * b.z;
	}
	
	public Point3D crossProduct( Point3D b ){
	    Point3D c = new Point3D();
	    c.x = y * b.z - z * b.y;
	    c.y = z * b.x - x * b.z;
	    c.z = x * b.y - y * b.x;
	    return c;
	}
	
	public Point3D scale( double s ){
	    Point3D c = new Point3D();
	    c.x = s * x;
	    c.y = s * y;
	    c.z = s * z;
	    return c;
	}

	public Point3D add( Point3D b){
	    Point3D c = new Point3D();
	    c.x = x + b.x;
	    c.y = y + b.y;
	    c.z = z + b.z;
	    return c;
	}

	public Point3D minus( Point3D b){
	    Point3D c = new Point3D();
	    c.x = x - b.x;
	    c.y = y - b.y;
	    c.z = z - b.z;
	    return c;
	}
	
	} //POINT3D Class END

```

what you will probably want to do is draw these lines.
Then eventually when you want to do things that are more advanced you will want to create polygons. (Triangles are the easiest type of polygon to create). Once you start using more complex polygons then you have some quite difficult mathematics and formulas on your hands. 

Hopefully you can use some sort of paint/drawline or draw to color in the pixels on the screen for your vector in python.

I do want to get round to learning python one day but I have just done the odd script here and there and the syntax is a bit different from my usual languages of java/c/c++ & php.

---

