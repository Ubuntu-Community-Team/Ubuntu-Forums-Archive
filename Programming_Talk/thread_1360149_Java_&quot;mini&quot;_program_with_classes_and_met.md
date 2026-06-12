---
title: "Java &quot;mini&quot; program with classes and methods (works but am confused about something)"
date: 2009-12-20
forum: Programming Talk
---

### Post by s3a on 2009-12-20
Ok, so I was considering buying a new LCD monitor because I saw certain specials but didn't like the resolution and instead of having to use trigonometry to calculate the amount of pixels per square inch of surface area; I made this program. Of course, it has no serious use in the real world but I made it because it seemed to be a neat way to practice what I learned so far. Anyways, my question is: **What is the point of all my set and get methods if all the work is being done by my constructor that takes parameters? What am I doing wrong in a logical sense? (since this causes no syntax errors and works fine)**

```
import java.util.Scanner;
public class PPA
{
	public static void main (String [] args)
	{
		Scanner kb = new Scanner(System.in);
		System.out.print("Enter the measure of the screen's diagonal (in inches): ");
		double diagonal = kb.nextDouble();
		System.out.print("Enter pixel width: ");
		int pixelWidth = kb.nextInt();
		System.out.print("Enter pixel length: ");
		int pixelLength = kb.nextInt();
		System.out.println();
		
		Screen s1 = new Screen(diagonal, pixelWidth, pixelLength);
		
		System.out.println("Diagonal size: " + s1.getDiagonal() + "\"");
		System.out.println("Width: " + s1.getWidth());
		System.out.println("Length: " + s1.getLength());
		System.out.println("Area: " + s1.getArea());
		System.out.println("Pixel Area: " + s1.getPixelArea());
		System.out.println("Pixels per square inch: " + s1.getPixelsPerSquareInch());
	}
}

```

```
public class Screen
{
	private double diagonal;
	private double width;
	private double length;
	private double area;
	private int pixelWidth;
	private int pixelLength;
	private int pixelArea;
	private double pixelsPerSquareInch;
	
	public Screen(){
		diagonal = 0;
		length = 0;
		width = 0;
	}
	public Screen(double diagonal, int pixelWidth, int pixelLength){
		this.diagonal = diagonal;
		this.length = 0.52999894 * diagonal;
		this.width = 0.847998304 * diagonal;
		this.area = length*width;
		this.pixelWidth = pixelWidth;
		this.pixelLength = pixelLength;
		this.pixelArea = pixelWidth * pixelLength;
		this.pixelsPerSquareInch = pixelArea/area;
	}
	public void setDiagonal(double diagonal){
		this.diagonal = diagonal;
	}
	public double getDiagonal(){
		return diagonal;
	}
	public void setWidth(){
		this.width = width;
	}
	public double getWidth(){
		return width;
	}
	public void setLength(){
	}
	public double getLength(){
		return length;
	}
	public void setArea(){
		this.area = length * width;
	}
	public double getArea(){
		return area;
	}
	public void setPixelArea(int pixelWidth, int pixelLength){
		this.pixelArea = pixelWidth * pixelLength;
	}
	public double getPixelArea(){
		return pixelArea;
	}
	public void setPixelsPerSquareInch(double area, int pixelArea){
		this.pixelsPerSquareInch = pixelArea/area;
	}
	public double getPixelsPerSquareInch(){
		return pixelsPerSquareInch;
	}
	public String toString(String diag){
		return "Diagonal size: "; // Figure this out
	}
}

```

Any input would be greatly appreciated!
Thanks in advance!

---

### Post by jobo3208 on 2009-12-20
Hey,
You don't have to put getters and setters for everything.

Obviously you are using the getters in your program, so I think you can see the need for those. You are designing with information hiding in mind. This may not be so important for such a small program, but it's generally good practice.

As for the setters, the only reason you'd really need them in this context is for reuse purposes. Say you (or somebody else) wanted to use the Screen class, but maybe in a different context than your program. The getters and setters would probably be helpful to them. If you don't intend to use the Screen class for anything else, then you can scrap the set methods.

Hope that helps.

---

### Post by shadylookin on 2009-12-20
I wouldn't have made setters since there's no reason to use them in this case.

However the reason they are used is to try and hide the implementation. 

For instance you have

width
height
area

if you directly access the width variable then you have to directly access the area variable and change it to something reasonable, but it would be better to do

void setWidth(int w){ width = w; area = w * height;}

---

### Post by Some Penguin on 2009-12-20
In this case, it's your constructor that is slightly weird -- it could just as easily be calling the set methods, which in turn could be doing the work.  That would be useful if you intend to change properties after instantiation...


Incidentally, the 

   void setFoo(X blah) /   X getFoo() 

idiom is sufficiently popular that it's used in certain frameworks.  For instance:
[http://www.springsource.org/about](http://www.springsource.org/about)

The Spring Framework can invoke these calls to initialize objects as specified by XML files. e.g.

<bean id="foo" class="com.blah.blah.blah">
   <property name="someProperty" value="800"/>  <!-- calls setSomeProperty(800) -->
  <property name="anotherProperty" ref="someOtherBean"/> <!-- calls setAnotherProperty(someOtherBean) -->
</bean>


Spring is quite nifty if you're writing something of complexity.

---

### Post by s3a on 2009-12-20
Oh ya! So I changed the Screen class to the following:

```
public class Screen
{
	private double diagonal;
	private double width;
	private double length;
	private double area;
	private int pixelWidth;
	private int pixelLength;
	private int pixelArea;
	private double pixelsPerSquareInch;
	
	public Screen(){
		diagonal = 0;
		length = 0;
		width = 0;
	}
	public Screen(double diagonal, int pixelWidth, int pixelLength){
		setDiagonal(diagonal);
		//this.diagonal = diagonal;
		setLength(0.52999894 * diagonal);
		//this.length = 0.52999894 * diagonal;
		setWidth(0.847998304 * diagonal);
		//this.width = 0.847998304 * diagonal;
		setArea(length * width);
		//this.area = length*width;
		setPixelWidth(pixelWidth);
		//this.pixelWidth = pixelWidth;
		setPixelLength(pixelLength);
		//this.pixelLength = pixelLength;
		setPixelArea(pixelWidth, pixelLength);
		//this.pixelArea = pixelWidth * pixelLength;
		setPixelsPerSquareInch(area, pixelArea);
		//this.pixelsPerSquareInch = pixelArea/area;
	}
	public void setDiagonal(double diagonal){
		this.diagonal = diagonal;
	}
	public double getDiagonal(){
		return diagonal;
	}
	public void setWidth(double width){
		this.width = width;
	}
	public double getWidth(){
		return width;
	}
	public void setLength(double length){
		this.length = length;
	}
	public double getLength(){
		return length;
	}
	public void setArea(double area){
		this.area = area;
	}
	public double getArea(){
		return area;
	}
	public void setPixelWidth(int pixelWidth){
		this.pixelWidth = pixelWidth;
	}
	public int getPixelWidth(){
		return pixelWidth;
	}
	public void setPixelLength(int pixelLength){
		this.pixelLength = pixelLength;
	}
	public int getPixelLength(){
		return pixelLength;
	}
	public void setPixelArea(int pixelWidth, int pixelLength){
		this.pixelArea = pixelWidth * pixelLength;
	}
	public int getPixelArea(){
		return pixelArea;
	}
	public void setPixelsPerSquareInch(double area, int pixelArea){
		this.pixelsPerSquareInch = pixelArea/area;
	}
	public double getPixelsPerSquareInch(){
		return pixelsPerSquareInch;
	}
	/*public String toString(String diag){
		return "Diagonal size: "; // Figure this out
	}
	public equals(){ // Figure this out
	}*/
}
```

So, what would be the use of the toString method as well as the equals method? (assuming that in the future I will be using JOptionPane which I think creates strings and I will be adding a feature to compare two monitors)

(I will also add a feature to choose 4:3, 16:9 or 16:10 screens. Just in case it's not obvious, I'm complicating my program so that I understand what I studied fully and by "complicating" I mean just using everything I learned (which is pretty much classes, methods --> constructors, accessors, mutators, toString method, and equals method) in my first semester in school so I don't want to learn new things yet until I master what I already know and what I'm slightly confused about is the toString method and more so the equals method.

---

### Post by shadylookin on 2009-12-21
> **s3a said:**
> 

So, what would be the use of the toString method as well as the equals method? (assuming that in the future I will be using JOptionPane which I think creates strings and I will be adding a feature to compare two monitors)

(I will also add a feature to choose 4:3, 16:9 or 16:10 screens. Just in case it's not obvious, I'm complicating my program so that I understand what I studied fully and by "complicating" I mean just using everything I learned (which is pretty much classes, methods --> constructors, accessors, mutators, toString method, and equals method) in my first semester in school so I don't want to learn new things yet until I master what I already know and what I'm slightly confused about is the toString method and more so the equals method.

You probably have no reason to override the equals or toString methods so I wouldn't bother. 

For whatever its worth I think you should ween yourself off of these excessive setters and getters. They're generally considered bad design and while they do hide the implementation better than public variables they're not an optimal solution. 

I know you're relatively knew to it and if you're anything like me I was grateful when it worked regardless of how terrible it was written, but it's something to think about for the future.

---

### Post by Some Penguin on 2009-12-21
There's always a 
  String toString()
and a
  boolean equals(Object o)

method.  If you leave them unspecified, then they're inherited (ultimately using the implementations in Object if nothing override those along the way).

toString() is supposed to do just that:  provide a string encoding of the object.  It's potentially useful for serialization and/or logging.

equals() is more important to not mess up, as it is called by various Collection classes, for instance.  Incidentally, equals() should through a null pointer exception if given a null parameter, and should be partly consistent with the hashCode()   (two objects should return the same hashCode if they're considered equal, but equal hashCode does not mean that they ARE equal) and fully consistent with any comparison methods (for Comparables).

You often won't be overriding either of 'em.

---

### Post by s3a on 2009-12-31
Well, I tried to implement the equals method to compare two monitors. Until, I properly define my definition of "equal" between a 16:10 and 16:9 monitor (I'll probably consider the pixel width divided by the screen's width measurement what makes two screens equal). That's not the point now though.

Here are the two files like before:

```
import java.util.Scanner;
public class PPA
{
	public static void main (String [] args)
	{
		Scanner kb = new Scanner(System.in);
		System.out.print("Monitor = 1; HDTV = 2; Choose: ");
		double choice = kb.nextDouble();
		if(choice != 1 && choice != 2)
		{
			System.out.println("Choose either 1 or 2 next time!\nBye.");
			System.exit(0);
		}
		System.out.print("Enter the measure of the screen's diagonal (in inches): ");
		double diagonal = kb.nextDouble();
		System.out.print("Enter pixel width: ");
		int pixelWidth = kb.nextInt();
		System.out.print("Enter pixel length: ");
		int pixelLength = kb.nextInt();
		System.out.println();
		
**		Screen s1 = new Screen(choice, diagonal, pixelWidth, pixelLength);**
		
		System.out.println("Diagonal size: " + s1.getDiagonal() + "\"");
		System.out.println("Width: " + s1.getWidth());
		System.out.println("Length: " + s1.getLength());
		System.out.println("Area: " + s1.getArea());
		System.out.println("Resolution: " + s1.getPixelWidth() + " x " + s1.getPixelLength());
		System.out.println("Pixel Area: " + s1.getPixelArea());
		System.out.println("Pixels per square inch: " + s1.getPixelsPerSquareInch());
		
		**Screen s2 = new Screen(choice, diagonal, pixelWidth, pixelLength);**
		
[I]		if(s1.equals(s2))
			System.out.println("Screen 1 and Screen 2 both have similar or congruent characteristics.");
		else
			System.out.println("Screen 1 and Screen 2 have different characteristics.");[/I]
	}
}

```
```
public class Screen
{
	private double diagonal;
	private double length;
	private double width;
	private double area;
	private int pixelWidth;
	private int pixelLength;
	private int pixelArea;
	private double pixelsPerSquareInch;
	
	public Screen(){
		diagonal = 0;
		length = 0;
		width = 0;
	}
	public Screen(double choice, double diagonal, int pixelWidth, int pixelLength){
		setDiagonal(diagonal);
		if(choice == 1)
		{
			setLength(getMonitorLengthRatio() * diagonal);
			setWidth(getMonitorWidthRatio() * diagonal);
		}
		else if (choice == 2)
		{
			setLength(getHDTV_LengthRatio() * diagonal);
			setWidth(getHDTV_WidthRatio() * diagonal);	
		}
		setArea(length * width);
		setPixelWidth(pixelWidth);
		setPixelLength(pixelLength);
		setPixelArea(pixelWidth, pixelLength);
		setPixelsPerSquareInch(area, pixelArea);
	}
	//
	public double getMonitorLengthRatio(){
		double MonitorLengthRatio = 0.52999894; // Calculated using trigonometry
		return MonitorLengthRatio;
	}
	public double getMonitorWidthRatio(){
		double MonitorWidthRatio = 0.847998304; // Calculated using trigonometry
		return MonitorWidthRatio;
	}
	public double getHDTV_LengthRatio(){
		double HDTV_LengthRatio = 0.49026124; // Calculated using trigonometry
		return HDTV_LengthRatio;
	}
	public double getHDTV_WidthRatio(){
		double HDTV_WidthRatio = 0.871575537; // Calculated using trigonometry
		return HDTV_WidthRatio;
	}
	//
	public void setDiagonal(double diagonal){
		this.diagonal = diagonal;
	}
	public double getDiagonal(){
		return diagonal;
	}
	public void setWidth(double width){
		this.width = width;
	}
	public double getWidth(){
		return width;
	}
	public void setLength(double length){
		this.length = length;
	}
	public double getLength(){
		return length;
	}
	public void setArea(double area){
		this.area = area;
	}
	public double getArea(){
		return area;
	}
	public void setPixelWidth(int pixelWidth){
		this.pixelWidth = pixelWidth;
	}
	public int getPixelWidth(){
		return pixelWidth;
	}
	public void setPixelLength(int pixelLength){
		this.pixelLength = pixelLength;
	}
	public int getPixelLength(){
		return pixelLength;
	}
	public void setPixelArea(int pixelWidth, int pixelLength){
		this.pixelArea = pixelWidth * pixelLength;
	}
	public int getPixelArea(){
		return pixelArea;
	}
	public void setPixelsPerSquareInch(double area, int pixelArea){
		this.pixelsPerSquareInch = pixelArea/area;
	}
	public double getPixelsPerSquareInch(){
		return pixelsPerSquareInch;
	}
	public String toString(String diag){
		String result = "Screen" + getPixelLength() + "x" + getPixelWidth(); // What exactly does this do?
		return result;
	}
	public boolean equals(Object obj){ // Figure this out
		boolean equality = this == obj ? true: false;
		return equality;		
	}
}

```

On my PPA class, I assumed that the s1 and s2 objects (what's in bold) would both end up being equal given what I've implemented so far in my program since they both give the same exact parameter values. When I run the program however, it says that my my two "screens" (what objects s1 and s2 refer to - which is the Screen class) are NOT equal. (what's in italic) **Why is this the case?**

---

### Post by Some Penguin on 2009-12-31
Because you wrote:

    public boolean equals(Object obj){ // Figure this out
        boolean equality = this == obj ? true: false;
        return equality;        
    }


And to elaborate:  What makes you think that "this == obj", the test you specifically use to override the ordinary equals implementation, has anything to do with checking the members?  You're testing the references for equality, only.

---

### Post by s3a on 2009-12-31
@Some Penguin: could you elaborate more on how to check if the members are the same please?

---

### Post by shadylookin on 2009-12-31
use your getter methods

---

### Post by s3a on 2009-12-31
I'm still having trouble grasping the concept. Could someone show me a mini example?

---

### Post by shadylookin on 2009-12-31
For the sake of simplicity lets say a Screen is equal to another screen as long as the area is the same. 

[PHP]
public boolean equals(Object other){
    if(area == (Screen)other.getArea()){
        return true;
    }
    return false;
}

[/PHP]

basically saying if the area of this Screen is the same as the other Screen then it's equal otherwise it's false. 

There's other things you need to check for like a null pointer and you need to make sure it's the same class type, but that's the gist of it.

---

### Post by Some Penguin on 2010-01-01
I'll note that comparing by all members is the *default* behavior, so you don't need to provide your own equals() method if that's what you want to do (i.e. it will normally recurse checking equals on each member field, and check equality in the obvious way for primitives like ints and chars).

You override equals when you want to do something else, such as ignore particular fields.

---

