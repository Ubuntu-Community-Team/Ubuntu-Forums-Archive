---
title: "Java program error that I cant solve... (Resizing picture)"
date: 2010-09-29
forum: Programming Talk
---

### Post by Eremis on 2010-09-29
Hi everyone!

I made this program to resize pictures, but its not working due to a Runtime error. 

Can someone help me?

Thanks


Program Code:

```

/**
 *
 * @author %%%%%%% %%%%%%%%
 *
 * @version 29 September, 2010.
 *
 * Description: A program that converts an Image to a certain size.
 */

import java.awt.AWTError;
import java.awt.Image;
import java.awt.Toolkit;
import java.io.File;
import java.io.IOException;
import java.awt.Graphics2D;
import java.awt.image.BufferedImage;
import javax.imageio.ImageIO;

public class PictureReSize{

    /** The default width */
    private final int DEFAULT_WIDTH = 800;

    /** The default heigth */
    private final int DEFAULT_HEIGHT = 600;

    /** The Image being viewed */
    private Image image;

    /** The path to the original Image */
    private String pathFrom;

    /** The path to the converted Image */
    private String pathTo;

    /**
     * Creates a new PictureReSize object, which lets the user 
     * resize an image.
     *
     * @param pathFrom the path from which to get image
     *
     * @param pathTo the path to the converted image
     *
     * @throws AWTError if a toolkit could not be found
     */
    public PictureReSize(String pathFrom, String pathTo)throws AWTError { 
        this.image = Toolkit.getDefaultToolkit().getImage(pathFrom);
        this.pathFrom = pathFrom;
        this.pathTo = pathTo;
    }

    /**
     * Re-sizes the image to given sizes and writes to a file
     *
     * @param width the width of the picture to resize to
     *
     * @param height the height of the picture to resize to
     *
     * @throws IOException IO operation failed or interupted
     */
    public void resizeTo(int width, int height) throws IOException {
        // Make new "re-sized" image
        Image newImage = image.getScaledInstance(width, height, 
                Image.SCALE_SMOOTH);
        // Make a buffered image from existing image
        BufferedImage bufferedImage = new BufferedImage(newImage.getWidth(null),
                image.getHeight(null), BufferedImage.TYPE_INT_RGB);
        // Create and draw the image to buffered reader
        Graphics2D graphics = bufferedImage.createGraphics();
        graphics.drawImage(newImage, null, null);
        // Write new Image to a file
        ImageIO.write(bufferedImage, "JPEG", new File(this.pathTo));
    }

    /**
     * Re-sizes the image to default values and writes to a file
     *
     * @throws IOException IO operation failed or interupted
     */
    public void resizeToDefault() throws IOException {
        // Call resizeTo meathod to resize with default parameters
        this.resizeTo(this.DEFAULT_WIDTH, this.DEFAULT_HEIGHT);
    }

    public static void main(String[]args) {
        try{
            PictureReSize pic = new PictureReSize("/home/%%%%%%/Pictures/Wallpapers/grass.jpg", "/home/andriy/Documents/grassResized.jpg");
            pic.resizeToDefault();
        }
        catch(IOException e){
            e.printStackTrace();
        }
    }
}

```

Runtime Error:

```

%%%%%%@linux-machine:~/Documents/Development/Pic Resize$ java PictureReSize
Exception in thread "main" java.lang.IllegalArgumentException: Width (-1) and height (-1) cannot be <= 0
        at java.awt.image.DirectColorModel.createCompatibleWritableRaster(DirectColorModel.java:1016)
        at java.awt.image.BufferedImage.<init>(BufferedImage.java:329)
        at PictureReSize.resizeTo(PictureReSize.java:66)
        at PictureReSize.resizeToDefault(PictureReSize.java:82)
        at PictureReSize.main(PictureReSize.java:88)


```

---

### Post by PaulM1985 on 2010-09-30
It looks like your newImage.getWidth(null) is returning -1. See here:
[http://download.oracle.com/javase/1.5.0/docs/api/java/awt/Image.html#getWidth(java.awt.image.ImageObserver](http://download.oracle.com/javase/1.5.0/docs/api/java/awt/Image.html#getWidth(java.awt.image.ImageObserver))

Make sure that your newImage actually has an image in it.

Also, I have never used Toolkit... to get an image.  I have always used ImageIO.read(File file) to get a buffered image.  I find this works well.  The Toolkit may work well, I just havent used it or come across it before.

Paul

---

### Post by algnod on 2010-09-30
I made the following changes to the program:

replaced:
//this.image = Toolkit.getDefaultToolkit().getImage(pathFrom);
with:
this.image = new ImageIcon(pathFrom).getImage();
...but like the previous comment said it would probably be better to use ImageIO for loading

replaced your resizeTo method
with:
public void resizeTo(int width, int height) throws IOException {
BufferedImage bufferedImage = new BufferedImage(width,height,BufferedImage.TYPE_INT_RGB);

// Create and draw the image to buffered reader
Graphics2D graphics = bufferedImage.createGraphics();
        graphics.setRenderingHint(RenderingHints.KEY_INTERPOLATION,RenderingHints.VALUE_INTERPOLATION_BILINEAR);

graphics.drawImage(image,0,0,width,height,null);
// Write new Image to a file
ImageIO.write(bufferedImage, "JPEG", new File(this.pathTo));
}

The use of getScaledInstance is discouraged for this and more info see here:
[http://today.java.net/pub/a/today/2007/04/03/perils-of-image-getscaledinstance.html](http://today.java.net/pub/a/today/2007/04/03/perils-of-image-getscaledinstance.html)

hope this helps

---

### Post by Finalfantasykid on 2010-09-30
Ya if you use an ImageObserver, it will solve your problem, as you will be able to check to see if the image is infact loaded.

However another solution, which is a little more crude, but should still work is this:

```

public PictureReSize(String pathFrom, String pathTo)throws AWTError { 
        this.image = Toolkit.getDefaultToolkit().getImage(pathFrom);
        while(this.image.getWidth() <= 0 || this.image.getHeight() <= 0){
               this.image = Toolkit.getDefaultToolkit().getImage(pathFrom);
        }
        this.pathFrom = pathFrom;
        this.pathTo = pathTo;
    }

```

But as you can imagine, this is a pretty unsafe way of doing this, and is fairly cpu intense since it is doing frequent polling until the image is fully loaded.

---

### Post by Zugzwang on 2010-09-30
> **Finalfantasykid said:**
> But as you can imagine, this is a pretty unsafe way of doing this, and is fairly cpu intense since it is doing frequent polling until the image is fully loaded.

Note that this doesn't look so much like a good idea as actually your code loads the image multiple times. I would propose to replace the line "this.image = Toolkit.getDefaultToolkit().getImage(pathFrom);" **in the loop** by:
```

Thread.yield();

```

This will tell the scheduler to let the current thread wait for a moment until (roughly) there is nothing else better to compute. You can also add a "Thread.sleep(1)" afterwards to reduce CPU consumption (but possibly increase the time to wait if you load a lot of image sequentially).

Needless to say that using the "javax.imageio.ImageIO" class is probably the tool to use if you need your image data immediately.

---

### Post by Eremis on 2010-10-01
Thanks guys,
algnod's meathod helped me a lot...

Once again thx for all the help!!!

---

