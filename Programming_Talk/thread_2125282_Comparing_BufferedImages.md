---
title: "Comparing BufferedImages"
date: 2013-03-13
forum: Programming Talk
---

### Post by Kodeine on 2013-03-13
I'm attempting to compare every pixel from two images to determine if they are the same. However the function is thinking images are the same when they are not.
```
public static Boolean ImgCompare(BufferedImage Img1,BufferedImage Img2)
           {
           Boolean Result = true;//True until proven false
  Loop : if (Img1.getWidth() == Img2.getWidth() && Img1.getHeight() == Img2.getHeight() )
              {
              for (int x = 0; x < Img1.getWidth(); x++)
                   {
                   for (int y = 0; y < Img1.getHeight(); y++)
                          {
                          if (Img1.getRGB(x, y) != Img2.getRGB(x, y) )
                              {
                              Result = false;
                              break Loop;
                              }
                          }
                    }
               }
         return Result;
         }
```

---

### Post by Mr. Shannon on 2013-03-13
I can't identify which language you are using (almost looks like C++/Java) but how your code is written it looks like if the images are different sizes the value true will be returned.  Probably not what you want.

What does Img1.getRGB(x, y) return?

---

### Post by Kodeine on 2013-03-13
I was so caught up I forgot to mention that it's Java yes and it is because of the image sizes thanks!

---

### Post by slickymaster on 2013-03-13
I would go with Java's PixelGrabber class.

You could create your own class to compare the images you want.
```
import java.awt.Image;
import java.awt.Toolkit;
import java.awt.image.PixelGrabber;

public class Compare {

    static void processImage() {

        String file1 = "img1.png";
        String file2 = "img2.png";

        Image image1 = Toolkit.getDefaultToolkit().getImage(file1);
        Image image2 = Toolkit.getDefaultToolkit().getImage(file2);

        try {

            PixelGrabber grab1 = new PixelGrabber(image1, 0, 0, -1, -1, false);
            PixelGrabber grab2 = new PixelGrabber(image2, 0, 0, -1, -1, false);

            int[] data1 = null;

            if (grab1.grabPixels()) {
                int width = grab1.getWidth();
                int height = grab1.getHeight();
                data1 = new int[width * height];
                data1 = (int[]) grab1.getPixels();
            }

            int[] data2 = null;

            if (grab2.grabPixels()) {
                int width = grab2.getWidth();
                int height = grab2.getHeight();
                data2 = new int[width * height];
                data2 = (int[]) grab2.getPixels();
            }

            System.out.println("Pixels equal: " + java.util.Arrays.equals(data1, data2));

        } catch (InterruptedException ie) {
        }
    }

    public static void main(String args[]) {
        processImage();
    }
}
```

---

