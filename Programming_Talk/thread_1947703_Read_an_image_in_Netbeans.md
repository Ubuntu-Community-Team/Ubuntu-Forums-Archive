---
title: "Read an image in Netbeans"
date: 2012-03-27
forum: Programming Talk
---

### Post by Brooksy_FC on 2012-03-27
I've got NetBeans installed, but I want to be able to read a image with it.

I'm not too familiar with Java and I've only tried to run HelloWorld! (I know, very basic)

The image is a TIFF file, but I can start with a basic format first.

Can anyone help guide me through what to do?

I'd much appreciated it :)

---

### Post by CynicRus on 2012-03-27
[http://code.imagej.net/trac/imagej](http://code.imagej.net/trac/imagej)

[http://sourceforge.net/apps/mediawiki/djatoka/index.php?title=Overview](http://sourceforge.net/apps/mediawiki/djatoka/index.php?title=Overview)

[http://www.javalobby.org/articles/ultimate-image/](http://www.javalobby.org/articles/ultimate-image/)

---

### Post by Brooksy_FC on 2012-03-27
Thanks for the post, but I'm still confused.

Can someone show me some code that just always me to read a jpg image. Just to start off with

---

### Post by CynicRus on 2012-03-27
```

import java.awt.image.*;
import javax.imageio.*;
import java.io.*;
import java.awt.*;
import javax.swing.*;

public class ReadSharp {
  private static class FrameShower implements Runnable {
    final Frame frame;

    public FrameShower(Frame frame) {
      this.frame = frame;
    }

    public void run() {
      frame.show();
    }
  }

  public static void main(String args[]) throws IOException {
    if (args.length != 1) {
      System.err.println("Please include image filename on command line");
      System.exit(-1);
    }
    // Read
    File file = new File(args[0]);
    BufferedImage input = ImageIO.read(file);
    // Convert
    Kernel sharpKernel = new Kernel(3, 3, new float[] { 0.0f, -1.0f, 0.0f,
        -1.0f, 5.0f, -1.0f, 0.0f, -1.0f, 0.0f });
    ConvolveOp convolveOp = new ConvolveOp(sharpKernel,
        ConvolveOp.EDGE_NO_OP, null);
    int width = input.getWidth();
    int height = input.getHeight();
    BufferedImage output = new BufferedImage(width, height,
        BufferedImage.TYPE_INT_ARGB);
    convolveOp.filter(input, output);
    // Make screen
    Icon icon = new ImageIcon(output);
    JLabel label = new JLabel(icon);
    JFrame frame = new JFrame("Sharp Image");
    frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
    frame.getContentPane().add(label, BorderLayout.CENTER);
    frame.pack();
    // Show
    Runnable runner = new FrameShower(frame);
    EventQueue.invokeLater(runner);
  }
}


```

---

### Post by Brooksy_FC on 2012-03-27
I'm using a similar code

```
import java.awt.*;
import java.awt.image.BufferedImage;
import java.io.*;
import javax.imageio.ImageIO;
import javax.swing.*;
 
public class LoadAndShow extends JPanel {
    BufferedImage image;
    Dimension size = new Dimension();
 
    public LoadAndShow(BufferedImage image) {
        this.image = image;
        size.setSize(image.getWidth(), image.getHeight());
    }
 
    /**
     * Drawing an image can allow for more
     * flexibility in processing/editing.
     */
    protected void paintComponent(Graphics g) {
        // Center image in this component.
        int x = (getWidth() - size.width)/2;
        int y = (getHeight() - size.height)/2;
        g.drawImage(image, x, y, this);
    }
 
    public Dimension getPreferredSize() { return size; }
 
    public static void main(String[] args) throws IOException {
        String path = "Snow.jpg";
        BufferedImage image = ImageIO.read(new File(path));
        LoadAndShow test = new LoadAndShow(image);
        JFrame f = new JFrame();
        f.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        f.add(new JScrollPane(test));
        f.setSize(400,400);
        f.setLocation(200,200);
        f.setVisible(true);
        //showIcon(image);
    }
 
    /**
     * Easy way to show an image: load it into a JLabel
     * and add the label to a container in your gui.
     */
    private static void showIcon(BufferedImage image) {
        ImageIcon icon = new ImageIcon(image);
        JLabel label = new JLabel(icon, JLabel.CENTER);
        JOptionPane.showMessageDialog(null, label, "icon", -1);
    }
}
```

But I keep getting this error back:

> error: class LoadAndShow is public, should be declared in a file named LoadAndShow.java
public class LoadAndShow extends JPanel {
1 error

---

### Post by CynicRus on 2012-03-27
Public-classes must be declared in separate java-files.

---

### Post by Zugzwang on 2012-03-27
> **CynicRus said:**
> Public-classes must be declared in separate java-files.

Even more, in Java, the file name of the java file a class source code resides in *must* be the same as the name of the class, including the capitalization of the class name! The error message says just that: The file name of the class "LoadAndShow" must be "LoadAndShow.java".

---

### Post by Brooksy_FC on 2012-03-27
Ok cool, how do I find this file and change it?

---

### Post by CynicRus on 2012-03-27
No, you need create file with this name. And put to file some class code.

some class code>>some.java

---

### Post by Brooksy_FC on 2012-03-27
Right ok. I've never written this kinda of code before, what sorta stuff should I be writing?

---

### Post by Brooksy_FC on 2012-03-27
OK, I've managed to download a LoadAndDisplay, but that's not exactly what I need

---

### Post by CynicRus on 2012-03-27
[http://filedeluxe.com/de030x4tmnkk.html](http://filedeluxe.com/de030x4tmnkk.html)- you fixed code.

---

### Post by Brooksy_FC on 2012-03-27
Nice one, I'll try and download this. Where do I put the file? I'm using windows at the mo

---

### Post by CynicRus on 2012-03-27
Unarchive with winrar etc, and open it in netbeans.

---

### Post by CynicRus on 2012-03-27
```

/*
 * To change this template, choose Tools | Templates
 * and open the template in the editor.
 */
package loadandshow;
import java.awt.image.*;
import javax.imageio.*;
import java.io.*;
import java.awt.*;
import javax.swing.*;
/**
 *
 * @author cynic
 */
public class LoadAndShow {
private static class FrameShower implements Runnable {
    final Frame frame;

    public FrameShower(Frame frame) {
      this.frame = frame;
    }

    public void run() {
      frame.show();
    }
  }

  public static void main(String args[]) throws IOException {
    if (args.length != 1) {
      System.err.println("Please include image filename on command line");
      System.exit(-1);
    }
    // Read
    File file = new File(args[0]);
    BufferedImage input = ImageIO.read(file);
    // Convert
    Kernel sharpKernel = new Kernel(3, 3, new float[] { 0.0f, -1.0f, 0.0f,
        -1.0f, 5.0f, -1.0f, 0.0f, -1.0f, 0.0f });
    ConvolveOp convolveOp = new ConvolveOp(sharpKernel,
        ConvolveOp.EDGE_NO_OP, null);
    int width = input.getWidth();
    int height = input.getHeight();
    BufferedImage output = new BufferedImage(width, height,
        BufferedImage.TYPE_INT_ARGB);
    convolveOp.filter(input, output);
    // Make screen
    Icon icon = new ImageIcon(output);
    JLabel label = new JLabel(icon);
    JFrame frame = new JFrame("Sharp Image");
    frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
    frame.getContentPane().add(label, BorderLayout.CENTER);
    frame.pack();
    // Show
    Runnable runner = new FrameShower(frame);
    EventQueue.invokeLater(runner);
  }
}


``` and, after opened package and test him -  can try my code.

---

### Post by Brooksy_FC on 2012-03-27
Right, I've got the file, so do I just have this opened in netbeans along side the code I already have?

Sorry for all the questions, I have no idea what I am doing

---

### Post by CynicRus on 2012-03-27
Don't understand you problem. You can extract tar.gz? If you extract this:
```


[LIST=1]
[*]Choose File > New Project (Ctrl-Shift-N on Windows/Cmd-Shift-N on Mac OS X).
[*]Choose Java > Java Project with Existing Sources. Click Next.
[*]In the Name and Location page of the wizard, follow these steps:
[LIST]
[*]Type a project name.
[*](Optional) Change the location of the project folder.
[*](Optional) Change the name of the build script used by the IDE.                             This might be desirable if there is already a build script called                         build.xml that is used to build the sources.
[*](Optional) Select the Use Dedicated Folder for Storing Libraries                             checkbox and specify the location for the libraries folder.                             See [Sharing Project Libraries]("http://netbeans.org/kb/docs/java/project-setup.html#projects-shared-libraries")                         for more information on this option.
[*](Optional) Select the Set as Main Project checkbox. When you select this option,                             keyboard shortcuts for commands such as Clean and Build Main Project (Shift-F11)                         apply to this project.
[/LIST]
[*]Click Next to advance to the Existing Sources page of the wizard.
[*]In the Source Packages Folder pane, click Add Folder. Then navigate to                         your sources and select the source roots, click Open.                         When you add a folder containing source code, you must add the folder that                             contains the highest folder in your package tree. For example, for the                             com.mycompany.myapp.ui package, you add the folder that               contains the com folder. 
[*](Optional) In the Test Package Folders pane, click Add Folder to select the                 folder containing the JUnit package folders.
[*]Click Next to advance to the Includes & Excludes page of the wizard.
[*](Optional) In the Includes & Excludes page of the wizard, enter file                     name patterns for any files that should be included or excluded from the project.                 By default, all files in your source roots are included.
[*] Click Finish.
[/LIST]


```

---

