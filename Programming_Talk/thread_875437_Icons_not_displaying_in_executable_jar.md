---
title: "Icons not displaying in executable jar"
date: 2008-07-30
forum: Programming Talk
---

### Post by shadylookin on 2008-07-30
I have this code that creates a JFrame filled with 3 labels 2 of which have Icons.

when i run the code in eclipse the icons are displayed but when i export it as an executable jar it will run without the icons and just display the labels. This isn't anything particularly fancy just to demonstrate a GUI

```


import javax.swing.JFrame;
import javax.swing.JLabel;
import java.awt.FlowLayout;
import javax.swing.SwingConstants;
import javax.swing.Icon;
import javax.swing.ImageIcon;

public class LabelFrame extends JFrame {
	
	private JLabel label1;
	private JLabel label2;
	private JLabel label3;
	
	public LabelFrame(){
		super("testing label");
		setLayout(new FlowLayout());
		
		label1 = new JLabel("Label with text");
		label1.setToolTipText("this is label1");
		add(label1);
		
		**Icon bug = new ImageIcon("bug1.gif");**
		label2 = new JLabel("Label with text and icon",bug,SwingConstants.LEFT);
		label2.setToolTipText("this is label2");
		add(label2);
		
		label3 = new JLabel();
		label3.setText("label with icon and text at bottom");
		label3.setIcon(bug);
		label3.setHorizontalTextPosition(SwingConstants.CENTER);
		label3.setVerticalTextPosition(SwingConstants.BOTTOM);
		label3.setToolTipText("this is label3");
		add(label3);
		
	}
	
	
	public static void main(String args[]){
		LabelFrame lf = new LabelFrame();
		lf.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		lf.setVisible(true);
		lf.setSize(300,500);
		
	}// end main
	
}// end class

```

I'm pretty sure the bolded part is where it all goes down. I've set it to an absolute path before and it works fine, but I'd much rather know how to be able to export the image inside the jar and have it work with a relative path. At the moment i have the image inside the jar file in the same folder as the class file, but the images still don't display. So how do i fix my path so that it works and is still a relative path. 

thanks for the help

---

### Post by tinny on 2008-07-30
You need to build the path to your image dynamically based on the current working directory.

Try something like this...
```

 
 String rootPath = System.getProperty("user.dir");
 String imgPath = rootPath + File.separator + <path to image folder with in your jar> + File.separator;
 ImageIcon image = new ImageIcon(imgPath + "bug1.gif");

```

BTW: "File.separator" provides a platform independent way of obtaining the file separator. (windows = \ linux = /)

---

### Post by ceclauson on 2008-07-31
Another way to do it is to get the URL of the image using the Class class's getResource method.  Something like this:

[PHP]
URL imageUrl = LabelFrame.class.getResource("bug1.gif");
Image bugImage = ImageIO.read(imageUrl);
//etc...
[/PHP]

This will work if bug1.gif is in the same directory as LabelFrame.class, regardless of where they are.

---

### Post by drubin on 2008-07-31
> **ceclauson said:**
> Another way to do it is to get the URL of the image using the Class class's getResource method.  Something like this:

[PHP]
URL imageUrl = LabelFrame.class.getResource("bug1.gif");
Image bugImage = ImageIO.read(imageUrl);
//etc...
[/PHP]

This will work if bug1.gif is in the same directory as LabelFrame.class, regardless of where they are.

This is the preferred way of doing this.

---

### Post by Zugzwang on 2008-07-31
> **rubinboy said:**
> This is the preferred way of doing this.

...but requires including the .gif file in the .jar file (hasn't been told in this thread yet)!

---

### Post by drubin on 2008-07-31
Do most ide's give you the option to exclude the resources?

---

### Post by Reiger on 2008-07-31
Eclipse gives you full control over what resources (Java files, classes, but also other files you may want) to include...

... Don't know about the others; haven't used those...

---

### Post by tinny on 2008-07-31
> **rubinboy said:**
> This is the preferred way of doing this.


> 
...but requires including the .gif file in the .jar file (hasn't been told in this thread yet)! 


Sorry but the "getResource" technique is NOT the preferred way of doing this. Just do a search for images with in the eclipse IDE folder (a real application), you will see that the images are not included in the jar files.

You should externalise your images from your jar and build the path to these images dynamically.

---

### Post by drubin on 2008-07-31
> **tinny said:**
> Sorry but the "getResource" technique is NOT the preferred way of doing this. Just do a search for images with in the eclipse IDE folder, you will see that the images are not included in the jar files.

You should externalise your images from your jar and build the path to these images dynamically.

Why?? 

What is wrong with "getResource"? :)

**EDIT** The images "were" in the jar file and when you install the plugins they are extracted..

---

### Post by tinny on 2008-07-31
> **rubinboy said:**
> Why?? 

What is wrong with "getResource"? :)

**EDIT** The images "were" in the jar file and when you install the plugins they are extracted..

Look just listen to me, your wrong right!!! :lolflag: Just joking!

I guess that having externalised images gives you more flexibility. If you need to update the images you dont need to release a whole new jar file, you just drop the new images into the images folder. Also you can share images between jars if they are externalised. (different application components can share the same images).

---

### Post by drubin on 2008-07-31
> **tinny said:**
> Look just listen to me, your wrong right!!! :lolflag: Just joking!
Bit harsh :) 

> **tinny said:**
> 
I guess that having externalised images gives you more flexibility. If you need to update the images you dont need to release a whole new jar file, you just drop the new images into the images folder. Also you can share images between jars if they are externalised. (different application components can share the same images).

I can see your point for API'S/LIBRARIES but for applications I would still recommend using the **getResource** method as it makes things easier for what the OP is intending to use it for. (Package his application into a bundle and execute it! ) 

@ the OP you have been given the facts/ideas it it up to you to try and choose what best suites your needs..... (For this project) if the project or needs change then you can change the method.

---

### Post by tinny on 2008-07-31
> **rubinboy said:**
> Bit harsh :) 



I can see your point for API'S/LIBRARIES but for applications I would still recommend using the **getResource** method as it makes things easier for what the OP is intending to use it for. (Package his application into a bundle and execute it! ) 

@ the OP you have been given the facts/ideas it it up to you to try and choose what best suites your needs..... (For this project) if the project or needs change then you can change the method.

For a simple 1 jar application, yes. :)

FTW: "Real" J2SE applications tend to be comprised of multiple jars.

---

### Post by drubin on 2008-07-31
> **tinny said:**
> For a simple 1 jar application, yes. :)

FTW: "Real" J2SE applications tend to be comprised of multiple jars.

learn to crawl before you learn to Run.!! Like this quote has many many uses think it is very fitting for allot of the stuff said in these forums. 

When the OP starts writing "FTW: "Real" J2SE applications tend to be comprised of multiple jars." They will undoubtedly have worked this out or at least know enough about Java to work this out.

---

### Post by christiane_guise@yahoo.co on 2008-11-04
I have the same problem with my java application
no html and images files are displayed for the jar
though the application works normally 
I tried your suggestion but I received an exception thread indicating problem at 
ImageIcon iChing = new ImageIcon(imageURL);

Please could you help me thank you so much

here is the class

public class Main extends JFrame
{
/**
* objects required for the GUI: JFrame,JLabel, JButton, ImageIcon, JPanel,
* Dimension
*/
private static final long serialVersionUID = 1L;
JButton jbEnter;
ImageIcon iChing, logo;
JPanel buttonPanel, ImagePanel;
JLabel jlbIching;
Dimension dim;
URL imageURL;
File fileName;

// Class constructor to create the GUI
public Main()
{

Container container = getContentPane();

URL imageURL = this.getClass().getClassLoader().getResource("src/myFiles/iching.gif");
ImageIcon iChing = new ImageIcon(imageURL);
jlbIching = new JLabel(iChing);
// button to go to the Title class
jbEnter = new JButton("Enter ");
jbEnter.setBorderPainted(false);
jbEnter.setFont(new Font("Edwardian Script ITC", Font.BOLD, 42));
jbEnter.setBackground(new Color(0, 0, 50));
jbEnter.setForeground(Color.YELLOW);
jbEnter.addActionListener(new ActionListener() {
// method to render the current frame invisible and trigger the
// Welcome Menu
public void actionPerformed(ActionEvent e)
{
setVisible(false);
// this line does not work...............
new Title();
} // close the actionPerformed(ActionEvent e) Method
}); // close the addActionListener(new ActionListener() method
// Panel holding the decorative image and Button
ImagePanel = new JPanel();
ImagePanel.add(jlbIching);
ImagePanel.setBackground(new Color(0, 0, 50));
buttonPanel = new JPanel();
buttonPanel.add(jbEnter);
buttonPanel.setBackground(new Color(0, 0, 50));
// setting up of the panels position
container.add(ImagePanel, BorderLayout.CENTER);
container.add(buttonPanel, BorderLayout.SOUTH);
dim = Toolkit.getDefaultToolkit().getScreenSize();
dim.width = dim.width / 2 - 300;
dim.height = dim.height / 2 - 250;
setBounds(dim.width, dim.height, 400, 400);
setSize(600, 500);
setResizable(false);
setVisible(true);
setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
//To set the icon for the application. Top left hand corner.
//this.setIconImage(Image);
setIconImage(new ImageIcon("src/myFiles/ichingRose.gif").getImage());
} // close the Constructor

/**
* the main method for the program.
* 
* @param args
* The command-line arguments.
*/
public static void main(String[] args)
{
new Main();
} // close the main method
} // close the Main class

---

### Post by Zugzwang on 2008-11-05
> **christiane_guise@yahoo.co said:**
> I have the same problem with my java application
no html and images files are displayed for the jar
though the application works normally 
I tried your suggestion but I received an exception thread indicating problem at 
ImageIcon iChing = new ImageIcon(imageURL);


Please copy and paste the exception, so we don't have to guess what happened. Also put a "System.out.println( System.out.toString());" before the "ImageIcon iChing = new ImageIcon(imageURL);" line and paste the path here. Finally make sure that you actually included the image in your .jar file!

---

### Post by christiane_guise@yahoo.co on 2008-11-17
> **Zugzwang said:**
> Please copy and paste the exception, so we don't have to guess what happened. Also put a "System.out.println( System.out.toString());" before the "ImageIcon iChing = new ImageIcon(imageURL);" line and paste the path here. Finally make sure that you actually included the image in your .jar file!

Ok this is the exception
Exception in thread "main" java.lang.NullPointerException
	at javax.swing.ImageIcon.<init>(Unknown Source)
	at iChing.Main.<init>(Main.java:49)
	at iChing.Main.main(Main.java:100)
and here is what I have done
If I unzip the jar the folder myFiles is in  with the images
I have redone the code as you suggest but probably did not do it right
here it is
public class Main extends JFrame
{
/**
* objects required for the GUI: JFrame,JLabel, JButton, ImageIcon, JPanel,
* Dimension
*/
private static final long serialVersionUID = 1L;
JButton jbEnter;
ImageIcon iChing, logo;
JPanel buttonPanel, ImagePanel;
JLabel jlbIching;
Dimension dim;
URL imageURL;
File fileName;

// Class constructor to create the GUI
public Main()
{

Container container = getContentPane();
URL imageURL = this.getClass().getClassLoader().getResource("src/myFiles/iching.gif");
System.out.println( System.out.toString()); 
String imgPath = "src/myFiles/iching.gif";
ImageIcon iChing = new ImageIcon(imageURL);


jlbIching = new JLabel(iChing);
// button to go to the Title class
jbEnter = new JButton("Enter ");
jbEnter.setBorderPainted(false);
jbEnter.setFont(new Font("Edwardian Script ITC", Font.BOLD, 42));
jbEnter.setBackground(new Color(0, 0, 50));
jbEnter.setForeground(Color.YELLOW);
jbEnter.addActionListener(new ActionListener() {
// method to render the current frame invisible and trigger the
// Welcome Menu
public void actionPerformed(ActionEvent e)
{
setVisible(false);
// this line does not work...............

} // close the actionPerformed(ActionEvent e) Method
}); // close the addActionListener(new ActionListener() method
// Panel holding the decorative image and Button
ImagePanel = new JPanel();
ImagePanel.add(jlbIching);
ImagePanel.setBackground(new Color(0, 0, 50));
buttonPanel = new JPanel();
buttonPanel.add(jbEnter);
buttonPanel.setBackground(new Color(0, 0, 50));
// setting up of the panels position
container.add(ImagePanel, BorderLayout.CENTER);
container.add(buttonPanel, BorderLayout.SOUTH);
dim = Toolkit.getDefaultToolkit().getScreenSize();
dim.width = dim.width / 2 - 300;
dim.height = dim.height / 2 - 250;
setBounds(dim.width, dim.height, 400, 400);
setSize(600, 500);
setResizable(false);
setVisible(true);
setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
//To set the icon for the application. Top left hand corner.
//this.setIconImage(Image);
setIconImage(new ImageIcon("src/myFiles/ichingRose.gif").getImage());
} // close the Constructor

/**
* the main method for the program.
* 
* @param args
* The command-line arguments.
*/
public static void main(String[] args)
{
new Main();
} // close the main method
} // close the Main class

This is incredible I tried so many things but do not succeed
Thank you anyway for helping me
for I really would like to achieve this

---

### Post by drubin on 2008-11-17
> **christiane_guise@yahoo.co said:**
> Ok this is the exception
Exception in thread "main" java.lang.NullPointerException
	at javax.swing.ImageIcon.<init>(Unknown Source)
	at iChing.Main.<init>(Main.java:49)
	at iChing.Main.main(Main.java:100)
and here is what I have done
If I unzip the jar the folder myFiles is in  with the images
I have redone the code as you suggest but probably did not do it right
here it is

....
This is incredible I tried so many things but do not succeed
Thank you anyway for helping me
for I really would like to achieve this

Please use the code formatting tags. I suggest using the php ones for added color.
IE 
[NOPARSE][PHP]code goes here[/PHP][/NOPARSE]

I also have a sneaky suspicion that the reason for the null pointer would be the image is not located where you think it is. Just double check that the path to the image is the correct one.

If you are using images that are bundleed in the .jar file. you need to use getClass().getResource()

---

### Post by Zugzwang on 2008-11-17
> **drubin said:**
> If you are using images that are bundleed in the .jar file. you need to use getClass().getResource()

That's it! Note that the following part of your code is quite sloopy:
[PHP]
URL imageURL = this.getClass().getClassLoader().getResource("src/myFiles/iching.gif");
System.out.println( System.out.toString());
String imgPath = "src/myFiles/iching.gif";
ImageIcon iChing = new ImageIcon(imageURL);
[/PHP]
Reasons:
[LIST=1]
[*]As already mentioned, it should be "this.getClass().getResource("src/myFiles/iching.gif");", otherwise you are searching for that resource in the classloader's package.
[*] "System.out.println( System.out.toString());" doesn't do anything meaningful. I guess it should be "System.out.println(imgPath.toString());"
[*] What is imgPath good for?
[/LIST]

---

### Post by Reiger on 2008-11-17
As to the reason why you get a null pointer from using the sloppy code: the JVM default classloader is not accessible, getClassLoader() pointing towards the JVM internals will return null. So calling getRescoure() afterwards will result in the nullpointer exception.

getClassLoader() is only useful in combination with your own (dynamic) classloaders.

---

### Post by christiane_guise@yahoo.co on 2008-11-17
> **Reiger said:**
> As to the reason why you get a null pointer from using the sloppy code: the JVM default classloader is not accessible, getClassLoader() pointing towards the JVM internals will return null. So calling getRescoure() afterwards will result in the nullpointer exception.

getClassLoader() is only useful in combination with your own (dynamic) classloaders.

Thank you very much for your replies
I shall look at this now
sorry for the code display 
and yes this part was sloppy and did not even make sense to me
I just tried to apply the suggestion
Badly certainly I do not really understand about the path
Again thanks and shall get back to you hopefully with good news

---

### Post by drubin on 2008-11-19
> **tinny said:**
> I guess that having externalised images gives you more flexibility. If you need to update the images you dont need to release a whole new jar file, you just drop the new images into the images folder. Also you can share images between jars if they are externalised. (different application components can share the same images).

Lately I have actually been bundling a resources.jar and all images/media are "proxied" through a Class located in there. It works pretty well on smaller scale projects haven't quite thought about having multiple themes/resource jars yet, or even larger scale dev. :)

---

### Post by tinny on 2008-11-19
> **drubin said:**
> Lately I have actually been bundling a resources.jar and all images/media are "proxied" through a Class located in there. It works pretty well on smaller scale projects haven't quite thought about having multiple themes/resource jars yet, or even larger scale dev. :)

Yeah, thanks a pretty good idea. :-)

---

### Post by drubin on 2008-11-19
> **tinny said:**
> Yeah, thanks a pretty good idea. :-)

I will post the code on my blog. this week and PM/post the link here.

The only reason I thought about this was people could download theme packages, and then just "over write"/move around the themes and the program would still pick up the reference. (and the object/class would still have the same path so would work)

---

### Post by Chudilo on 2009-04-16
I think this would be a bit more elegant.
And don't forget to enclose that in a try/catch 
[PHP]
URL frameIconURL = this.getClass().getResource("icon.gif");
Image windowImage = ImageIO.read(frameIconURL);
this.setIconImage(windowImage);
[/PHP]

---

### Post by Shekibobo on 2009-10-30
I've tried pretty much every combination of suggestions for making this work, and none of them have been successful.  Maybe I'm doing something else wrong.  Here's my code for importing these images:
[PHP]
    private final ImageIcon EMPTY_CELL = new ImageIcon(getClass().getResource("/emptyCell.png"));
    private final ImageIcon[] PLAYER_SELECT_CELL = {     new ImageIcon(getClass().getResource("/redSelectedCell.png")),
                                                        new ImageIcon(getClass().getResource("/greenSelectedCell.png")), 
                                                        new ImageIcon(getClass().getResource("/yellowSelectedCell.png")),
                                                        new ImageIcon(getClass().getResource("/blueSelectedCell.png"))    };
    
    private final ImageIcon[] PLAYER_CELL = {    new ImageIcon(getClass().getResource("/redCell.png")), 
                                                new ImageIcon(getClass().getResource("/greenCell.png")), 
                                                new ImageIcon(getClass().getResource("/yellowCell.png")), 
                                                new ImageIcon(getClass().getResource("/blueCell.png"))     };
[/PHP]

This works great within Eclipse, but in a jar file none of the images load.  The images are in the same directory as the class.  I've also tried removing the '/' from the beginning of the String.  Originally I just had them as new ImageIcon("*.png") and that worked great except in the exported Jar file.  I checked and the images are definitely in the jar, in the same directory as the main class.

Can you see what I'm doing wrong?

---

### Post by froggyswamp on 2009-10-30
can you post your project

---

### Post by Reiger on 2009-10-30
Well if it works within Eclipse but not if you run it as plain jar outside then you are clearly not running it with the same run parameters (Classpath! Classpath! Classpath! Can you tell it's the classpath?) as within...

... Sometimes a little induction can get you far.

---

### Post by froggyswamp on 2009-10-30
Adjusting the classpath shouldn't be absolutely necessary. I've created apps that could use resources from inside and outside the (executable) jar file and never needed to adjust the class path (and worked both on windows and Linux).
But to know for sure what's the matter with his code I need to look at both the code and the project structure (otherwise it would be just guessing).

---

### Post by pbrockway2 on 2009-10-30
```

getResource("/emptyCell.png")

```

The leading slash means that the location of the class returned by getClass() is essentially ignored.  Ie the part following the slash is interpreted as the absolute name. See [getResource(String)]("http://java.sun.com/javase/6/docs/api/java/lang/Class.html#getResource(java.lang.String)") API docs.

Note if you are using Windows that the case of the name you use to identify elements of a jar file is important.  (Unlike the corresponding names if they were files.)

You can always use System.out.println() to actually print out the URL you are using to load the resources.  That way you can see exactly where the runtime is looking.

```

System.out.println("loading empty cell from " + getClass().getResource("/emptyCell.png"));
EMPTY_CELL = new ImageIcon(getClass().getResource("/emptyCell.png"));

```

---

### Post by Shekibobo on 2009-10-30
> **pbrockway2 said:**
> ```

getResource("/emptyCell.png")

```

The leading slash means that the location of the class returned by getClass() is essentially ignored.  Ie the part following the slash is interpreted as the absolute name. See [getResource(String)]("http://java.sun.com/javase/6/docs/api/java/lang/Class.html#getResource(java.lang.String)") API docs.

Note if you are using Windows that the case of the name you use to identify elements of a jar file is important.  (Unlike the corresponding names if they were files.)

You can always use System.out.println() to actually print out the URL you are using to load the resources.  That way you can see exactly where the runtime is looking.

```

System.out.println("loading empty cell from " + getClass().getResource("/emptyCell.png"));
EMPTY_CELL = new ImageIcon(getClass().getResource("/emptyCell.png"));

```
I tried adding the println to the constructor of the game.  Interestingly, it shows up in the eclipse terminal, but not when I run it in the terminal.

---

### Post by Shekibobo on 2009-10-30
I also tried exporting the whole project as an runnable jar (apparently I wasn't doing that before), and then when I run java -jar connections-1.10.09, I get the following error:

```

$ java -jar connections-1.10.09
Exception in thread "main" java.lang.NullPointerException
    at javax.swing.ImageIcon.<init>(ImageIcon.java:155)
    at Connect4GUI.<init>(Connect4GUI.java:29)
    at Connect4GUI.main(Connect4GUI.java:327)

```

I'm attaching the project.

---

### Post by pbrockway2 on 2009-10-30
Are you sure that code goes with that runtime exception?  I ask because line 29 of Connect4GUI.java does not contain an ImageIcon constructor invocation.

System.out.println() *will* provide useful diagnostic information.  If you did not see the output when you ran the program from the terminal then either the constructor did not get called (unlikely) or you ran a different version of the program that the one you ran within Eclipse (much more likely).  The code you posted does not contain the code necessary to output the URL you are using to get the image resources.

Edit: Also the code you posted uses the **filename** version of the ImageIcon constructor.  This is never going to work if you intend adding the images to the .jar archive.

---

### Post by froggyswamp on 2009-10-30
I changed a few things in your project like making it a NetBeans (6.7.1) project and adding a function that takes care of loading the images and moved the images to a separate folder "images".
I'd suggest you use NetBeans for Java development cause it really helps and makes suggestions when you do something undesirable or wrong (like in your case i.e. you don't specify a package which is not good, you have fields you don't use etc.).

The NetBeans project (the source code is in the "src" subfolder) with a working .jar executable is attached below.

---

### Post by froggyswamp on 2009-10-30
There's a few more places I haven't spotted where you use "new ImageIcon" directly, please change them to loadIcon() too yourself.

---

### Post by Shekibobo on 2009-10-31
So....I like all the magic of just changing my code and all, but what makes that work rather than what I was trying to do?

And Eclipse works fine and does all those things you mentioned.  I just haven't used those settings.  There are a lot of things regarding proper programing practices that they don't feel the need to teach us in school.

---

### Post by froggyswamp on 2009-10-31
> **Shekibobo said:**
> So....I like all the magic of just changing my code and all, but what makes that work rather than what I was trying to do?

Putting a few issues aside, please answer this:
Would you show me please the documentation page that specifies a constructor of ImageIcon that (according to your last version of code) uses a string param to load an image from the current .jar file?

---

### Post by nds17 on 2011-01-05
While going through one project, I also faced same problems. Please find the below mentioned steps what I used to resolve the problems(Using Eclipse IDE):
1. created /images folder parallel to /src.
2. Right click on the /images folder then ->"Build Path"->click on the "Use as Source folder"
3. fetched respective images using the way shown in other posts.
4. but strange thing was that application was working fine for the jpg,gif,png files in Eclipse IDE but when I created executable JAR and run it in Windows, images were not displayed.
Its solution I got that when I changed the jpg file with GIF file it started working in executable JAR.
5. JAR creation: Export-> Java->Runnable JAR then click on "Next". Provide details for "Launch Configuraion" and "Destination folder".
Runnable JAR file is created.
Hope it will help you... but i am eager to know why JPG was not working but GIF worked?:confused::p

---

