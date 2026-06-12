---
title: "Netbeans file problems.  Please help."
date: 2008-06-27
forum: Programming Talk
---

### Post by farrell2k on 2008-06-27
I cannot seem to get Netbeans to display any of the images used in my application, which is supposed to draw an image to the screen, and play a wav file.

My question is: Where do I put my .png and .wav file?

1. I add them to src, with my .java src file, and both files are added to the jar when built, but the app never displays the pic.   

This is very annoying.  Does anyone have a solution to this, besides defining a fixed path for my image, like: /home/user/file?

Thanks for any help :)

**********code*********

/*
 * To change this template, choose Tools | Templates
 * and open the template in the editor.
 */

package racer;
import java.applet.AudioClip;
import javax.swing.*;
import java.awt.*;
import java.net.URL;

/**
 *
 * @author Tom
 */
public class Main extends JFrame
{
    Panel panel = new Panel();
    Image carl = new ImageIcon("carl.png").getImage();
 
    URL bgMusic = this.getClass().getResource("Theme1.wav");
    AudioClip bgMusicWav = JApplet.newAudioClip(bgMusic);
    
    public Main()
    {
        super("Racer");
        setSize(800,600);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        getContentPane().add(panel);
        setVisible(true);
        bgMusicWav.loop();
    }

    public class Panel extends JPanel
    {
        public void paintComponent(Graphics g)
        {
            super.paintComponent(g);
            g.drawImage(carl,0,0,this);
        }
    }
    
    
    public static void main(String[] args)
    {
        Main racer = new Main();
    }

}

********end code*******

---

### Post by geirha on 2008-06-28
Java will not search for data-files inside jar-files automatically. A quick search came up with this: [http://www.cejug.org/display/~htmfilho/How+a+jar+file+application+can+access+files+in+itself](http://www.cejug.org/display/~htmfilho/How+a+jar+file+application+can+access+files+in+itself)

---

### Post by xlinuks on 2008-06-28
Create a folder inside the "src" folder and call it, say, "images". Put your images (and if you wish other stuff like .wav files as well) there.
Now you can access them like this:
```

	try {
		URL url = getClass().getResource( "/images/your_image.png" );
		if( url != null ) {
			Image img  = Toolkit.getDefaultToolkit().getImage( url ); //you got it!
			your_JFrame.setIconImage( img );//or whatever
		}
	} catch( Exception exc ) {
	}

```

---

### Post by Diabolis on 2008-06-28
If you want to read the files from inside the jar file, you have to use the method posted by xlinuks. If you want to read them using paths, the files must be placed outside the jar.

[PHP]Image carl = new ImageIcon("carl.png").getImage();[/PHP]

According to this, the file **"carl.png"** is inside your **src** folder, which is inside your **proyect folder**. If not, then that is why is not showing up.

---

### Post by farrell2k on 2008-06-28
> **Diabolis said:**
> If you want to read the files from inside the jar file, you have to use the method posted by xlinuks. If you want to read them using paths, the files must be placed outside the jar.

[PHP]Image carl = new ImageIcon("carl.png").getImage();[/PHP]

According to this, the file **"carl.png"** is inside your **src** folder, which is inside your **proyect folder**. If not, then that is why is not showing up.


I tried adding them to the jar, as well as from outside the jar, with no luck, but confusinly, here is the answer in case anyone else is having the same problem:

When you go File -> New Project -> Java Application -> Next to the Name and Location Screen, deselect "Create Main Class".  Now you can put all resource files in the src folder, and they will be added to the jar, or you could build the jar, then put them in the same folder as the jar.

The problem seems to be with netbeans "package option".   I think it is changing current directory rules.    If I create a java app, and allow netbeans to create a main class for me, it places a line of code on top:  "package: 'name of class', which screws everything up.   Now I just don't do it, and things are working just fine.

Thanks for the replies.

---

### Post by Diabolis on 2008-06-28
lol I'm glad you got it working. What it is actually good is that you were able to figure it out, but your solution is partially correct.

In java **packages** are actually folders and I encourage you to use them.

> ... netbeans places a line of code on top: "package: 'name of class', which screws everything up.

this is incorrect, that line is set up like this:

```
"package: 'name of FOLDER'
```

So it wasn't enough to put the files inside the folder **src**, you had to look for the folder(package) inside **src**.

This thread may be of help for you: [http://ubuntuforums.org/showthread.php?t=837166](http://ubuntuforums.org/showthread.php?t=837166)

---

