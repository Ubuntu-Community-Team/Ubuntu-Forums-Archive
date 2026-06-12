---
title: "[Java] Image Manapulation"
date: 2008-07-02
forum: Programming Talk
---

### Post by Pyro.699 on 2008-07-02
Hello,

I have a few questions about how to manipulate and retrieve data from images. I have three or four questions that revolve around this topic. I have absolutely no knowledge of the modules to edit images.

Question 1: **Resizing images**
I was wondering how i would take an image and change its resolution to a set value. Say the image is 1024x768, i would like to take it down to a resolution of 250x250. I know that there would be some distortion of the image but the visual appearance is not important for what the script is being used for. I would like the whole method to look something like this *public static <data type for images> setResolution(<data type for images> img, int x, int y)* which would take the image and resize it appropriately.

Question 2: **Getting RBG value at (x,y)**
I was wondering how i could take an image and get the specific RBG values for that individual pixel. I would like the method to look like this *public static String[] getRBG(<data type for images> img, int x, int y)* and it would return the values in an array that would look like [Red, Blue, Green] for that individual pixel.

Question 3: **System memory and time to execute**
Im running on a dual core 2.2 GHz laptop and was wondering how long it would take to a) resize the image and b) getting the values or RBG 62500 times (one execution for each pixel).

Thankyou for your help
~Cody Woolaver

---

### Post by xlinuks on 2008-07-02
Hi,
Have a look at java.awt.image.BufferedImage - that's what you need and it implements the methods you need.
The speed is close to that of the system libraries.

---

### Post by xlinuks on 2008-07-02
If you google you're gonna find lots of useful stuff, here's something fresh:
[http://www.comesolvego.com/2008/04/29/resize-images-with-java-high-quality-and-working-solution/](http://www.comesolvego.com/2008/04/29/resize-images-with-java-high-quality-and-working-solution/)

---

### Post by myrtle1908 on 2008-07-02
**For resizing:-**
[COLOR="Red"]
[http://today.java.net/cs/user/view/cs_msg/157411](http://today.java.net/cs/user/view/cs_msg/157411)[/COLOR] - edit: this looks promising.  i wish i thought of this many years ago when i was doing this kind of thing.

[http://www.geocities.com/marcoschmidt.geo/java-save-jpeg-thumbnail.html](http://www.geocities.com/marcoschmidt.geo/java-save-jpeg-thumbnail.html)
[http://www.comesolvego.com/2008/04/29/resize-images-with-java-high-quality-and-working-solution/](http://www.comesolvego.com/2008/04/29/resize-images-with-java-high-quality-and-working-solution/)
[http://www.i-proving.ca/space/Technologies/Java+Advanced+Imaging](http://www.i-proving.ca/space/Technologies/Java+Advanced+Imaging)

Seems there may be speed problems using getScaledInstance() **.  There is also discussion of shelling out to ImageMagic (JMagic for Java I think) when speed if of the essence.

** [http://today.java.net/pub/a/today/2007/04/03/perils-of-image-getscaledinstance.html](http://today.java.net/pub/a/today/2007/04/03/perils-of-image-getscaledinstance.html)

**For grabbing pixels:-**

java.awt.image.PixelGrabber
[http://java.sun.com/j2se/1.4.2/docs/api/java/awt/image/PixelGrabber.html](http://java.sun.com/j2se/1.4.2/docs/api/java/awt/image/PixelGrabber.html)

**For System memory and time to execute:-**

I'm afraid I don't know.  For speed, look at the Java Advanced Imaging (JAI) libraries and/or ImageMagick.

Discussion: [http://www.darcynorman.net/2005/03/15/jai-vs-imagemagick-image-resizing/](http://www.darcynorman.net/2005/03/15/jai-vs-imagemagick-image-resizing/)
ImageMagick: [http://www.imagemagick.org/script/index.php](http://www.imagemagick.org/script/index.php)
JMagic: [http://sourceforge.net/projects/jmagick/](http://sourceforge.net/projects/jmagick/)

---

### Post by Biochem on 2008-07-03
You migt whant t have a look at ImageJ. It's an open source java imaging software. You can browse the code for inspiration (since your mentionned issue were solved) or use java macro with ImageJ to directly do the job.

Good luck

---

### Post by Pyro.699 on 2008-07-03
Thankyou all for your replies and i did try out all of the ideas you put forth, but as i stated before i know very very little about all of these image modules. I found myself wrapped up in several thousands of lines of code that really did nothing. Could someone write the actchual code segments that could do what i needed.

[php]
public static Image resize(Image img, int x, int y){
Image ret=null;
//All the code that you use to resize
return ret;
}
[/php]

[php]
public static int[] getRGBAt(Image img, int x, int y){
int[] ret = new int[3];
//All the code that you use to get the color.
return ret;
}
[/php]

Sorry for seeming so reliant on the ability of others, but once im able to see exactly what it is that i want ill be able to understand better the code from whats given.

Thankyou all again for your help
~Cody Woolaver

---

### Post by myrtle1908 on 2008-07-04
Here's a program that scales a JPG down to 32x32 and prints out the pixels in rgb.  It is un-tested (however it does work), has no error handling etc. 

It should be enough to get you started.

I put little to no thought into this and it's been a while since I've done anything like this so I am unsure if this is the best/fastest way.  Still, you seemed to need some assistance so I've coughed it up.  Use at your own risk.

[PHP]
import java.awt.*;
import java.awt.geom.*;
import java.awt.image.*;
import java.io.*;
import javax.imageio.*;


public class Whatever {

    public static void main (String args[]) {
    	try {
	    	String src = "black.jpg";
	    	String dest = "black_scaled.jpg";
	    	scaleJPG(src, 32, 32, dest);
	    	printPixels(dest);
    	} catch (Exception e) {
    		e.printStackTrace();
    	}
    }
    
    private static void scaleJPG(String src, int width, int height, String dest) throws Exception {
    	BufferedImage bsrc = ImageIO.read(new File(src));
    	BufferedImage bdest = new BufferedImage(width, height, BufferedImage.TYPE_INT_RGB);
    	Graphics2D g = bdest.createGraphics();
    	AffineTransform at = AffineTransform.getScaleInstance((double)width/bsrc.getWidth(), (double)height/bsrc.getHeight());
    	g.drawRenderedImage(bsrc, at);
    	ImageIO.write(bdest, "JPG", new File(dest));
    }
    
    private static void printPixels(String src) throws Exception {
    	BufferedImage bsrc = ImageIO.read(new File(src));
    	int w = bsrc.getWidth();
    	int h = bsrc.getHeight();
    	int[] pixels = new int[w * h];
    	PixelGrabber pg = new PixelGrabber(bsrc, 0, 0, w, h, pixels, 0, w);
    	pg.grabPixels();
    	for (int j = 0; j < h; j++) {
            for (int i = 0; i < w; i++) {
            	printPixel(pixels[j * w + i]);
            }
        }
    }
    
    private static void printPixel(int pixel) {
        int alpha = (pixel >> 24) & 0xff;
        int red   = (pixel >> 16) & 0xff;
        int green = (pixel >>  8) & 0xff;
        int blue  = (pixel      ) & 0xff;
        System.out.println(red + "," + green + "," + blue);
        
 }
    
}
[/PHP]

---

### Post by Pyro.699 on 2008-07-04
Thankyou very much, but i dont need it to write to a file i just need to read it and read data from that variable. Awesome help though.

---

### Post by myrtle1908 on 2008-07-04
> **Pyro.699 said:**
> Thankyou very much, but i dont need it to write to a file i just need to read it and read data from that variable. Awesome help though.

Understand.  I just didn't have the time to get it to do exactly what you wanted.  You should be able to make use of it however.  See how you go.

PS.  I changed a few minor things in the code above.

---

### Post by Pyro.699 on 2008-07-04
Alright, how about images that are not JPG; like PNG or TAR.

---

### Post by myrtle1908 on 2008-07-04
> **Pyro.699 said:**
> Alright, how about images that are not JPG; like PNG or TAR.

I believe ImageIO.write() can deal with gif, jpg and png.

So you can change the output format in this line: [PHP]ImageIO.write(bdest, "JPG", new File(dest));[/PHP]

At some stage you are going to have to normalize the images you are comparing. I would attack the problem like this:-

**Step 1** - With the two images you want to compare, convert them to  the same size and format eg. 128x128, PNG.

**Step 2** - Grab pixels from both images into arrays.

**Step 3** - Compare all pixels or sections thereof.


Sample compare code which returns a percent different:

[PHP]
public class Whatever {
	
    public static void main (String args[]) {
    	try {
	    	String[] a = {"a", "b", "c", "d", "e", "f", "g", "h", "i", "j"};
	    	String[] b = {"a", "b", "c", "d", "x", "f", "g", "h", "x", "j"};    	
	    	String[] c = {"x", "b", "x", "d", "x", "f", "x", "h", "x", "j"};
	    	String[] d = {"x", "x", "x", "x", "x", "x", "x", "x", "x", "x"};
	    	System.out.println("b is " + compare(a,b) + "% different to a");
	    	System.out.println("c is " + compare(a,c) + "% different to a");
	    	System.out.println("d is " + compare(a,d) + "% different to a");
    	} catch (Exception e) {
    		e.printStackTrace();
    	}
    }
    
    public static float compare(String[] a, String[] b) {
    	int nomatch = 0;
    	for (int i=0; i<a.length; i++) {
    		if (!a[i].equals(b[i])) {
    			nomatch++;
    		}
    	}
    	return ((float)nomatch / (float)a.length) * 100;
    }
    
}
[/PHP]

---

### Post by myrtle1908 on 2008-07-04
Well I got bored and hacked together a solution for you.  It is not the quickest thing on the planet and needs some work.  There are many things that I could have done better but it's getting late and I need a beer :)

The isDuplicate() and normalizeImage() functions need alot of tuning for speed so I've made it simple to just replace these with better versions.

You can play with the constant 'DUPLICATE_THRESHOLD' to get differing results.  For example (using the sample images I have attached) with the 'DUPLICATE_THRESHOLD' set at 95.0 'Untitled3.jpg' and 'Untitled4.gif' are reported as duplicates whilst at 99.9 they are not.

[PHP]
import java.awt.*;
import java.awt.geom.*;
import java.awt.image.*;
import java.io.*;
import javax.imageio.*;
import java.util.*;

public class ImageDiff {

	static final String TEMP_FOLDER = "/tmp/"; /* normalized images are written here temporarily */
	static final String NORM_PREFIX = ".norm"; /* normalized images are postfixed with this */
	static final int NORM_WIDTH = 128; /* normalized width */
	static final int NORM_HEIGHT = 128; /* normalized height */
	static final String NORM_FORMAT = "PNG"; /* normalized output format.  PNG best cos it's smallest */
	static final float DUPLICATE_THRESHOLD = 95.0f; /* considered a duplicate when pixel match percentage greater than this */

	public static void main(String[] argv) {
		File imageDir = null;
		ArrayList imageFiles = null;
		Hashtable duplicateImages = null;
		ArrayList duplicates = null;
		String imageName = "";
		if (argv.length != 1) { usage(); return; }
		try {
			imageDir = new File(argv[0]);
			if (!imageDir.isDirectory()) { usage(); return; }
			imageFiles = getImageFiles(imageDir);
			duplicateImages = findDuplicates(imageFiles);
			Enumeration e = duplicateImages.keys();
			while (e.hasMoreElements()) {
				imageName = (String)e.nextElement();
				duplicates = (ArrayList)duplicateImages.get(imageName);
				if (duplicates.size() > 0) {
					System.out.println("The image '" + imageName + "' is duplicated by " + duplicates.toString());
				}
			}
			
		} catch (Exception e) {
			e.printStackTrace();
		}
	}

	static ArrayList getImageFiles(File imageDir) throws Exception {
		ArrayList imageFiles = new ArrayList();
		File[] files = null;
		File file = null;
		String fileName = "";
		String rex = ".*?[jpe?g|png|gif]$";
		files = imageDir.listFiles();
		for (int i=0; i<files.length; i++) {
			file = (File)files[i];
			fileName = file.getName().toLowerCase();
			if (fileName.matches(rex)) {
				imageFiles.add(file);
			}
		}
		return imageFiles;
	}

	static Hashtable findDuplicates(ArrayList imageFiles) throws Exception {
		Hashtable duplicateImages = new Hashtable();
		Object[] list1 = imageFiles.toArray();
		Object[] list2 = imageFiles.toArray();
		File image1 = null;
		File image2 = null;
		ArrayList duplicates;
		boolean duplicate;
		for (int i=0; i<list1.length; i++) {
			image1 = (File)list1[i];
			duplicates = new ArrayList();
			duplicate = false;
			for (int j=0; j<list2.length; j++) {
				image2 = (File)list2[j];
				if (!image1.getName().equals(image2.getName())) {
					duplicate = isDuplicate(image1, image2);
					if (duplicate) {
						duplicates.add(image2.getName());
					}
				}
			}
			duplicateImages.put(image1.getName(), duplicates);
		}
		return duplicateImages;
	}

	static boolean isDuplicate(File image1, File image2) throws Exception {
		PixelGrabber pg;

		File image1Norm = normalizeImage(image1);
		BufferedImage b1 = ImageIO.read(image1Norm);
		int image1Width = b1.getWidth();
		int image1Height = b1.getHeight();
		int[] image1pixels = new int[image1Width * image1Height];
		pg = new PixelGrabber(b1, 0, 0, image1Width, image1Height, image1pixels, 0, image1Width);
		pg.grabPixels();
		image1Norm.delete();

		File image2Norm = normalizeImage(image2);
		BufferedImage b2 = ImageIO.read(image2Norm);
		int image2Width = b2.getWidth();
		int image2Height = b2.getHeight();
		int[] image2pixels = new int[image2Width * image2Height];
		pg = new PixelGrabber(b2, 0, 0, image2Width, image2Height, image2pixels, 0, image2Width);
		pg.grabPixels();
		image2Norm.delete();
		
		

		int pixelMatch = 0;
		for (int i=0; i<image1pixels.length; i++) {
			if (image1pixels[i] == image2pixels[i]) {
				pixelMatch++;
			}
		}
		
		return ((float)pixelMatch / image1pixels.length * 100) >= DUPLICATE_THRESHOLD;
		
	}

	static File normalizeImage(File image) throws Exception {
		BufferedImage src = ImageIO.read(image);
		BufferedImage dst = new BufferedImage(NORM_WIDTH, NORM_HEIGHT, BufferedImage.TYPE_INT_RGB);
		Graphics2D g = dst.createGraphics();
		AffineTransform at = AffineTransform.getScaleInstance((double)NORM_WIDTH/src.getWidth(), 
			(double)NORM_HEIGHT/src.getHeight());
		g.drawRenderedImage(src, at);
		File normalized = new File(TEMP_FOLDER + image.getName() + NORM_PREFIX);
		ImageIO.write(dst, NORM_FORMAT, normalized);
		return normalized;
	}

	static void usage() {
		System.out.println("Usage: java ImageDiff image_directory");
	}

}
[/PHP]

---

### Post by Pyro.699 on 2008-07-04
Wow, thankyou very much for that although i have a few comments (i did modify it a bit). I made it so that the script had a built in folder to browse from because the files will all be put into a specified folder. Also it took alot of time to run the scipt (it had 700 images in the folder and that was a small amound). I just looked at the script and i found an error.

[quote=ImageDiff.java]
cody@Charmander:~/Stuff/Testing$ java main.ImageDiff
javax.imageio.IIOException: Error reading PNG image data
	at com.sun.imageio.plugins.png.PNGImageReader.readImage(PNGImageReader.java:1287)
	at com.sun.imageio.plugins.png.PNGImageReader.read(PNGImageReader.java:1552)
	at javax.imageio.ImageIO.read(ImageIO.java:1438)
	at javax.imageio.ImageIO.read(ImageIO.java:1298)
	at main.ImageDiff.normalizeImage(ImageDiff.java:125)
	at main.ImageDiff.isDuplicate(ImageDiff.java:102)
	at main.ImageDiff.findDuplicates(ImageDiff.java:79)
	at main.ImageDiff.main(ImageDiff.java:30)
Caused by: java.io.EOFException: Unexpected end of ZLIB input stream
	at java.util.zip.InflaterInputStream.fill(InflaterInputStream.java:240)
	at java.util.zip.InflaterInputStream.read(InflaterInputStream.java:158)
	at java.io.BufferedInputStream.fill(BufferedInputStream.java:235)
	at java.io.BufferedInputStream.read1(BufferedInputStream.java:275)
	at java.io.BufferedInputStream.read(BufferedInputStream.java:334)
	at java.io.DataInputStream.readFully(DataInputStream.java:195)
	at com.sun.imageio.plugins.png.PNGImageReader.decodePass(PNGImageReader.java:1084)
	at com.sun.imageio.plugins.png.PNGImageReader.decodeImage(PNGImageReader.java:1188)
	at com.sun.imageio.plugins.png.PNGImageReader.readImage(PNGImageReader.java:1280)
	... 7 more
[/quote]

Thanks so much again
~Cody Woolaver

---

### Post by myrtle1908 on 2008-07-04
Here's a revised version that is a bit quicker ie. 
the program no longer writes images to the disk before the compare and uses a different method of getting the pixels.

At the end of the day the number of images and their size will adversely affect the time the program takes to run.  I have added some output so you know what's going on when it's running.

The slow parts are the scaling of the images and the pixel compare,  If anybody knows a better way to handle either of these then that would be useful.  With the scaling I have tried using JAI and it was actually slower than using AWT.

The pixel comparison can surely be sped up.  **Does anyone know the fastest way to compare two arrays of type int and return the number of differences?**

Finally, the error you posted ... looks like a bogus image.

[PHP]
import java.awt.*;
import java.awt.geom.*;
import java.awt.image.*;
import java.io.*;
import javax.imageio.*;
import java.util.*;

public class ImageDiff {

	static final int NORM_SIZE_MAX = 16; /* normalized maximum size (width vs height) */
	static final String NORM_FORMAT = "PNG"; /* normalized output format.  PNG best cos it's smallest */
	static final float DUPLICATE_THRESHOLD = 95.0f; /* considered a duplicate when pixel match percentage greater than this */

	public static void main(String[] argv) {
		File imageDir = null;
		ArrayList imageFiles = null;
		Hashtable duplicateImages = null;
		ArrayList duplicates = null;
		String imageName = "";
		if (argv.length != 1) { usage(); return; }
		try {
			long start = System.currentTimeMillis();
			imageDir = new File(argv[0]);
			if (!imageDir.isDirectory()) { usage(); return; }
			imageFiles = getImageFiles(imageDir);
			duplicateImages = findDuplicates(imageFiles);
			Enumeration e = duplicateImages.keys();
			while (e.hasMoreElements()) {
				imageName = (String)e.nextElement();
				duplicates = (ArrayList)duplicateImages.get(imageName);
				if (duplicates.size() > 0) {
					System.out.println("The image '" + imageName + "' is duplicated by " + duplicates.toString());
				}
			}
			long end = System.currentTimeMillis();
			System.out.println("Runtime: " + ((end-start) / 1000) + " seconds");
			
		} catch (Exception e) {
			e.printStackTrace();
		}
	}

	static ArrayList getImageFiles(File imageDir) throws Exception {
		ArrayList imageFiles = new ArrayList();
		File[] files = null;
		File file = null;
		String fileName = "";
		String rex = ".*?[jpe?g|png|gif]$";
		files = imageDir.listFiles();
		for (int i=0; i<files.length; i++) {
			file = (File)files[i];
			if (!file.isDirectory()) {
				fileName = file.getName().toLowerCase();
				if (fileName.matches(rex)) {
					imageFiles.add(file);
				}
			}
		}
		return imageFiles;
	}

	static Hashtable findDuplicates(ArrayList imageFiles) throws Exception {
		Hashtable duplicateImages = new Hashtable();
		Object[] list1 = imageFiles.toArray();
		Object[] list2 = imageFiles.toArray();
		File image1 = null;
		File image2 = null;
		ArrayList duplicates;
		boolean duplicate;
		for (int i=0; i<list1.length; i++) {
			image1 = (File)list1[i];
			duplicates = new ArrayList();
			duplicate = false;
			for (int j=0; j<list2.length; j++) {
				image2 = (File)list2[j];
				if (!image1.getName().equals(image2.getName())) {
					System.out.print(image1.getName() + " vs " + image2.getName() + " : ");
					duplicate = isDuplicate(image1, image2);
					if (duplicate) {
						System.out.println("DUPLICATE!");
						duplicates.add(image2.getName());
					} else {
						System.out.println("images are different.");
					}
				}
			}
			duplicateImages.put(image1.getName(), duplicates);
		}
		return duplicateImages;
	}

	static boolean isDuplicate(File image1, File image2) throws Exception {
		
		BufferedImage b1 = normalizeImage(image1);
		WritableRaster r = b1.getRaster();
		DataBuffer db = r.getDataBuffer();
		DataBufferInt dbi = (DataBufferInt)db;
		int[] image1pixels = dbi.getData();

		BufferedImage b2 = normalizeImage(image2);
		r = b2.getRaster();
		db = r.getDataBuffer();
		dbi = (DataBufferInt)db;
		int[] image2pixels = dbi.getData();
		
		int pixelMatch = 0;
		if (image1pixels.length == image2pixels.length) {
			for (int i=0; i<image1pixels.length; i++) {
				if (image1pixels[i] == image2pixels[i]) {
					pixelMatch++;
				}
			}
		}
		return ((float)pixelMatch / image1pixels.length * 100) >= DUPLICATE_THRESHOLD;
	}

	static BufferedImage normalizeImage(File image) throws Exception {
		BufferedImage src = ImageIO.read(image);
		BufferedImage dst = new BufferedImage(NORM_SIZE_MAX, NORM_SIZE_MAX, BufferedImage.TYPE_INT_RGB);
		Graphics2D g = dst.createGraphics();
		AffineTransform at = AffineTransform.getScaleInstance((double)NORM_SIZE_MAX/src.getWidth(), 
			(double)NORM_SIZE_MAX/src.getHeight());
		g.drawRenderedImage(src, at);
		return dst;
	}

	static void usage() {
		System.out.println("Usage: java ImageDiff image_directory");
	}

}
[/PHP]

---

### Post by Pyro.699 on 2008-07-04
I came up with this.

[php]
	public static double getSimilar(int[][] Image1, int[][] Image2, int pixles){

		int r1=0,g1=0,b1=0;
		int r2=0,g2=0,b2=0;
		
		double diff=0D;

		double rt=0D,gt=0D,bt=0D;
		
		for(int i=0;i<=(pixels-1);i++){
			r1=Image1[i][0]; g1=Image1[i][1]; b1=Image1[i][2];
			r2=Image2[i][0]; g2=Image2[i][1]; b2=Image2[i][2];
			
			rt = Math.abs(r1-r2)/255D;
			gt = Math.abs(g1-g2)/255D;
			bt = Math.abs(b1-b2)/255D;
			
			diff += (rt + gt + bt) / 3D;
			//System.out.print("("+r1+", "+g1+", "+b1+") & ");
			//System.out.println("("+r2+", "+g2+", "+b2+")");
		}
		diff = 100D-((diff/pixels)*100D);
		return diff;
	}
[/php]

It compairs one image RGB values to another. The inputs look like *Image[pixel number][0-2 (red,green,blue)]* then it returns a decimal representation of how similar one image is to another.

Would that work?

Thanks again
~Cody Woolaver

---

### Post by myrtle1908 on 2008-07-06
Turns out the really slow part is getting the pixels from the image rather than the bit that compares them.  Need a fast way to get the pixels ... something other than getRaster/getDataBuffer.

---

### Post by myrtle1908 on 2008-07-06
Just dawned on me that my code shouldn't call isDuplicate() on images that are of differing size ie. if width and height of two images are different then they cant possibly be duplicates (duh!). 

Add some code to findDuplicates() that checks this.  This should speed it up massively.

---

### Post by ceclauson on 2008-07-06
I'm going to try at this, hopefully this will be helpful.

It looks from your posts so far that you're familiar with the java.awt.Image class that represents an image.  However, the Image class is written is such a way that
(1) You can't access the pixel data directly and
(2) You can't alter the image in any way -- like change pixel data
Do do these things, you need to use the java.awt.BufferedImage class, which is a subclass of Image, but allows you to access pixel data directly using setRGB(int color, int x, int y) and getRGB(int x, int y) methods.  Because BufferedImage is a subclass of Image, you can do anything with it that you can do with an Image, and more.

There are two common ways to create a BufferedImage.  You can (1) load an image from a file using the javax.imageio.ImageIO class's static read() method, or (2) create a blank one using the BufferedImage constructor.  Here's a code example that does this:

```

import java.net.URL;
import java.awt.*;
import java.awt.image.*;
import javax.imageio.ImageIO;
import java.io.IOException;

class MainClass {

	public static void main(String[] args) {

		//create a BufferedImage variable
		BufferedImage myBufferedImage = null;

		try {
			//get the URL of the image file.  This will only work if
			//the image file is in the same directory as this class.
			URL imageLocation = MainClass.class.getResource("myimage.png");
			//throw an IOException if it couldn't load.
			if(imageLocation == null)
				throw new IOException("Trouble loading " + "myimage.png");
			//use ImageIO's read() method to load the BufferedImage
			myBufferedImage = ImageIO.read(imageLocation);
		} catch(IOException e) {
			//if there's an error, print it and quit
			System.err.println(e);
			return;
		}

		//now we can get at the pixel data of the image.
		//this gets the color at pixel x = 20, y = 40;
		int myColor = myBufferedImage.getRGB(20, 40);

		//we can also change it
		//this changes the color at pixel x = 70, y = 45
		myBufferedImage.setRGB(70, 45, myColor);

		//here we can create a blank BufferedImage
		//the width is 100 pixels, and height 200 pixels
		BufferedImage myOtherBufferedImage =
			new BufferedImage(100, 200, BufferedImage.TYPE_4BYTE_ABGR);

		//we can draw a circle on it
		for(x = 0; x < myOtherBufferedImage.getWidth(); x++)
		for(y = 0; y < myOtherBufferedImage.getHeight(); y++)
		if( ((x - 20) * (x - 20) + (y - 50) * (y - 50)) < 25)
			myOtherBufferedImage.setRGB(x, y, 0xFFFFFFFF);

		//and so on...
	
		return;

	}
}

```

To answer your last question, ImageIO.read() automatically determines the type of the image file and decodes it.  I think it understands a lot of common types (.bmp, .png, .jpeg, .gif for sure, because I've done these before).

If you have a regular image, and want to convert it to a BufferedImage, there's no easy way to do it, you actually have to create a new BufferedImage of the same size as the original image, and then blit the original onto it.  Here's a method that will do this:

```

	public static BufferedImage convertToBI(Image image) {
		//create a new BufferedImage the same size as the image
		BufferedImage bi = new BufferedImage(image.getWidth(null),
			image.getHeight(null), BufferedImage.TYPE_4BYTE_ABGR);
		//get the graphics context of the buffered image
		Graphics g = bi.getGraphics();
		//blit the image onto the buffered image
		g.drawImage(image, 0, 0, null);.
		//...
		return bi;
	}

```

I haven't tried to compile any of these fragments, but hopefully they'll work -- they're basically correct, though.

Good luck,
Cooper

---

### Post by myrtle1908 on 2008-07-06
**Third revision.**

_* The regex that selects image files now works properly._
[PHP][^.]+?\\.((png)|(jpeg)|(jpg)|(gif))[/PHP]
_* Images of differing dimensions are assumed to be different (ie. cannot be a duplicate)._

Not sure how this can be made any faster.  Open to suggestions.

In my testing on a directory with 60 images of differing formats, file sizes (largest 5MB) and dimensions (largest 1024x1280) it took the program 5 minutes to complete...each image must check 59 others for duplication...3540 iterations!

[PHP]
import java.awt.*;
import java.awt.geom.*;
import java.awt.image.*;
import java.io.*;
import javax.imageio.*;
import java.util.*;

public class ImageDiff {

    static final int NORM_SIZE_MAX = 16; /* normalized maximum size (width vs height) */
    static final String NORM_FORMAT = "PNG"; /* normalized output format.  PNG best cos it's smallest */
    static final float DUPLICATE_THRESHOLD = 95.0f; /* considered a duplicate when pixel match percentage greater than this */

    public static void main(String[] argv) {
        File imageDir = null;
        ArrayList imageFiles = null;
        Hashtable duplicateImages = null;
        ArrayList duplicates = null;
        String imageName = "";
        if (argv.length != 1) { usage(); return; }
        try {
            long start = System.currentTimeMillis();
            imageDir = new File(argv[0]);
            if (!imageDir.isDirectory()) { usage(); return; }
            imageFiles = getImageFiles(imageDir);
            duplicateImages = findDuplicates(imageFiles);
            Enumeration e = duplicateImages.keys();
            while (e.hasMoreElements()) {
                imageName = (String)e.nextElement();
                duplicates = (ArrayList)duplicateImages.get(imageName);
                if (duplicates.size() > 0) {
                    System.out.println("The image '" + imageName + "' is duplicated by " + duplicates.toString());
                }
            }
            long end = System.currentTimeMillis();
        } catch (Exception e) {
            e.printStackTrace();
        }
    }

    static ArrayList getImageFiles(File imageDir) throws Exception {
        ArrayList imageFiles = new ArrayList();
        File[] files = null;
        File file = null;
        String fileName = "";
        String rex = "[^.]+?\\.((png)|(jpeg)|(jpg)|(gif))";
        files = imageDir.listFiles();
        for (int i=0; i<files.length; i++) {
            file = (File)files[i];
            if (!file.isDirectory()) {
                fileName = file.getName().toLowerCase();
                if (fileName.toLowerCase().matches(rex)) {
                    imageFiles.add(file);
                }
            }
        }
        return imageFiles;
    }

    static Hashtable findDuplicates(ArrayList imageFiles) throws Exception {
        Hashtable duplicateImages = new Hashtable();
        Object[] list1 = imageFiles.toArray();
        Object[] list2 = imageFiles.toArray();
        File image1 = null;
        File image2 = null;
        ArrayList duplicates;
        boolean duplicate;
        for (int i=0; i<list1.length; i++) {
            image1 = (File)list1[i];
            duplicates = new ArrayList();
            duplicate = false;
            for (int j=0; j<list2.length; j++) {
                image2 = (File)list2[j];
                if (!image1.getName().equals(image2.getName())) {
                    System.out.print(image1.getName() + " vs " + image2.getName() + " : ");
                    duplicate = isDuplicate(image1, image2);
                    if (duplicate) {
                        System.out.println("DUPLICATE!");
                        duplicates.add(image2.getName());
                    } else {
                        System.out.println("images are different.");
                    }
                }
            }
            duplicateImages.put(image1.getName(), duplicates);
        }
        return duplicateImages;
    }

    static boolean isDuplicate(File image1, File image2) throws Exception {
    	
    	BufferedImage b1 = ImageIO.read(image1);
    	BufferedImage b2 = ImageIO.read(image2);
    	
        if ((b1.getWidth() != b2.getWidth()) || (b1.getHeight() != b2.getHeight())) {
        	return false;
        }
        
        b1 = normalizeImage(b1);
        WritableRaster r = b1.getRaster();
        DataBuffer db = r.getDataBuffer();
        DataBufferInt dbi = (DataBufferInt)db;
        int[] image1pixels = dbi.getData();
        
        b2 = normalizeImage(b2);
        r = b2.getRaster();
        db = r.getDataBuffer();
        dbi = (DataBufferInt)db;
        int[] image2pixels = dbi.getData();
        
        int pixelMatch = 0;
        if (image1pixels.length == image2pixels.length) {
            for (int i=0; i<image1pixels.length; i++) {
                if (image1pixels[i] == image2pixels[i]) {
                    pixelMatch++;
                }
            }
        }
        return ((float)pixelMatch / image1pixels.length * 100) >= DUPLICATE_THRESHOLD;
    }

    static BufferedImage normalizeImage(BufferedImage src) throws Exception {
        //BufferedImage src = ImageIO.read(image);
        BufferedImage dst = new BufferedImage(NORM_SIZE_MAX, NORM_SIZE_MAX, BufferedImage.TYPE_INT_RGB);
        Graphics2D g = dst.createGraphics();
        AffineTransform at = AffineTransform.getScaleInstance((double)NORM_SIZE_MAX/src.getWidth(), 
            (double)NORM_SIZE_MAX/src.getHeight());
        g.drawRenderedImage(src, at);
        return dst;
    }

    static void usage() {
        System.out.println("Usage: java ImageDiff image_directory");
    }

}  
[/PHP]

---

### Post by HotCupOfJava on 2008-07-06
One minor note I might toss in: you might find the ArrayList class to be a bit more flexible than using standard arrays for your comparisons. Do read the documentation for the constructors and methods - the syntax isn't exactly like normal arrays. The ArrayList's size can be altered on the fly.

---

### Post by HotCupOfJava on 2008-07-06
Apologies, Myrtle....I see you DID use ArrayList...I should have examined your code before I posted.

---

