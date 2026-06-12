---
title: "Can't read image from executable jar file"
date: 2006-03-29
forum: Programming Talk
---

### Post by HokeyFry on 2006-03-29
I am creating a text editor for my java class in high school. I have all of the essential parts done (i.e. input text, save, change color, etc.) and now I am moving on to sprucing it up with at least 15 pieces of flair ;) .

One of these things is a splash image. But, since I can't get a proper one to come up, I just made a message box using JOptionPane and stuck an ImageIcon in it, just to make it look cool. When I run the class in bluej before creating a jar file, it works perfectly. But when I create an executable jar file, the image won't display. Just so you know, the image is in the same directory when I create the jar file, and the ImageIcon respects this. Also, the rest of the program works perfectly, it is just this one problem at this point. I would also like to point out that this is the first jar file I have ever made before, so if it is something easy and/or obvious, please bear with me.

---

### Post by HokeyFry on 2006-03-29
Okay, I figured out that it is reading in the directory that the jar file is in, not the jar file itself (I extracted the image into the folder). But I really want the picture inside the jar file. Is there a way to get java to look inside the jar file for the picture?

---

### Post by hod139 on 2006-04-03
[quote=HokeyFry]Okay, I figured out that it is reading in the directory that the jar file is in, not the jar file itself (I extracted the image into the folder). But I really want the picture inside the jar file. Is there a way to get java to look inside the jar file for the picture?[/quote]

You have to open the image either as a URL or as an input stream. Input streams tend to be faster.  Here is a demo from one of Java's[ Swing tutorials]("http://java.sun.com/docs/books/tutorial/uiswing/misc/icon.html"):
```

public class IconDemoApplet extends JApplet ... {
    protected String leftButtonFilename = "images/left.gif";
    ...
    public void init() {
        ...
        ImageIcon leftButtonIcon = createAppletImageIcon(leftButtonFilename,
                                                   "an arrow pointing left");
        ...
    }
    ...
    //Returns an ImageIcon, or null if the path was invalid.
    //When running an applet using Java Plug-in,
    //getResourceAsStream is more efficient than getResource.
    protected static ImageIcon createAppletImageIcon(String path,
                                              String description) {
        int MAX_IMAGE_SIZE = 75000; //Change this to the size of
                                    //your biggest image, in bytes.
        int count = 0;
        BufferedInputStream imgStream = new BufferedInputStream(
           IconDemoApplet.class.getResourceAsStream(path));
        if (imgStream != null) {
            byte buf[] = new byte[MAX_IMAGE_SIZE];
            try {
                count = imgStream.read(buf);
            } catch (IOException ieo) {
                System.err.println("Couldn't read stream from file: " + path);
            }

            try {
                imgStream.close();
            } catch (IOException ieo) {
                 System.err.println("Can't close file " + path);
            }

            if (count <= 0) {
                System.err.println("Empty file: " + path);
                return null;
            }
            return new ImageIcon(Toolkit.getDefaultToolkit().createImage(buf),
                                 description);
        } else {
            System.err.println("Couldn't find file: " + path);
            return null;
        }
    }
    ...
} 

```

---

