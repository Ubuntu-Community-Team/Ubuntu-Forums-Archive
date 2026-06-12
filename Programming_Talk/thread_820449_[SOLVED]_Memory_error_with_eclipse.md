---
title: "[SOLVED] Memory error with eclipse"
date: 2008-06-06
forum: Programming Talk
---

### Post by Despot Despondency on 2008-06-06
Hey, I'm using eclipse to write a java program and I keep getting the following error when I try to run the program

```

Exception in thread "Image Fetcher 1" java.lang.OutOfMemoryError: Java heap space
	at java.awt.image.DataBufferInt.<init>(DataBufferInt.java:41)
	at java.awt.image.Raster.createPackedRaster(Raster.java:458)
	at java.awt.image.DirectColorModel.createCompatibleWritableRaster(DirectColorModel.java:1015)
	at sun.awt.image.ImageRepresentation.createBufferedImage(ImageRepresentation.java:235)
	at sun.awt.image.ImageRepresentation.setPixels(ImageRepresentation.java:487)
	at sun.awt.image.ImageDecoder.setPixels(ImageDecoder.java:120)
	at sun.awt.image.PNGImageDecoder.sendPixels(PNGImageDecoder.java:531)
	at sun.awt.image.PNGImageDecoder.produceImage(PNGImageDecoder.java:452)
	at sun.awt.image.InputStreamImageSource.doFetch(InputStreamImageSource.java:246)
	at sun.awt.image.ImageFetcher.fetchloop(ImageFetcher.java:172)
	at sun.awt.image.ImageFetcher.run(ImageFetcher.java:136)
Exception in thread "Image Fetcher 0" java.lang.OutOfMemoryError: Java heap space
	at java.awt.image.DataBufferInt.<init>(DataBufferInt.java:41)
	at java.awt.image.Raster.createPackedRaster(Raster.java:458)
	at java.awt.image.DirectColorModel.createCompatibleWritableRaster(DirectColorModel.java:1015)
	at sun.awt.image.ImageRepresentation.createBufferedImage(ImageRepresentation.java:235)
	at sun.awt.image.ImageRepresentation.setPixels(ImageRepresentation.java:487)
	at sun.awt.image.ImageDecoder.setPixels(ImageDecoder.java:120)
	at sun.awt.image.PNGImageDecoder.sendPixels(PNGImageDecoder.java:531)
	at sun.awt.image.PNGImageDecoder.produceImage(PNGImageDecoder.java:452)
	at sun.awt.image.InputStreamImageSource.doFetch(InputStreamImageSource.java:246)
	at sun.awt.image.ImageFetcher.fetchloop(ImageFetcher.java:172)
	at sun.awt.image.ImageFetcher.run(ImageFetcher.java:136)
Exception in thread "Image Fetcher 1" java.lang.OutOfMemoryError: Java heap space
	at java.awt.image.DataBufferInt.<init>(DataBufferInt.java:41)
	at java.awt.image.Raster.createPackedRaster(Raster.java:458)
	at java.awt.image.DirectColorModel.createCompatibleWritableRaster(DirectColorModel.java:1015)
	at sun.awt.image.ImageRepresentation.createBufferedImage(ImageRepresentation.java:235)
	at sun.awt.image.ImageRepresentation.setPixels(ImageRepresentation.java:487)
	at sun.awt.image.ImageDecoder.setPixels(ImageDecoder.java:120)
	at sun.awt.image.PNGImageDecoder.sendPixels(PNGImageDecoder.java:531)
	at sun.awt.image.PNGImageDecoder.produceImage(PNGImageDecoder.java:452)
	at sun.awt.image.InputStreamImageSource.doFetch(InputStreamImageSource.java:246)
	at sun.awt.image.ImageFetcher.fetchloop(ImageFetcher.java:172)
	at sun.awt.image.ImageFetcher.run(ImageFetcher.java:136)
Exception in thread "Image Fetcher 0" java.lang.OutOfMemoryError: Java heap space
	at java.awt.image.DataBufferInt.<init>(DataBufferInt.java:41)
	at java.awt.image.Raster.createPackedRaster(Raster.java:458)
	at java.awt.image.DirectColorModel.createCompatibleWritableRaster(DirectColorModel.java:1015)
	at sun.awt.image.ImageRepresentation.createBufferedImage(ImageRepresentation.java:235)
	at sun.awt.image.ImageRepresentation.setPixels(ImageRepresentation.java:487)
	at sun.awt.image.ImageDecoder.setPixels(ImageDecoder.java:120)
	at sun.awt.image.PNGImageDecoder.sendPixels(PNGImageDecoder.java:531)
	at sun.awt.image.PNGImageDecoder.produceImage(PNGImageDecoder.java:452)
	at sun.awt.image.InputStreamImageSource.doFetch(InputStreamImageSource.java:246)
	at sun.awt.image.ImageFetcher.fetchloop(ImageFetcher.java:172)
	at sun.awt.image.ImageFetcher.run(ImageFetcher.java:136)
Exception in thread "main" java.lang.NullPointerException
	at javax.swing.ImageIcon.<init>(ImageIcon.java:138)
	at gui.GameMap.paintCountry(GameMap.java:105)
	at connector.Game.startGame(Game.java:27)
	at connector.Game.main(Game.java:14)

```

I've looked around and apparently the java VM has run out of memory. 

I don't know how to increase the memory of the java VM with eclipse. Apparently I'm meant to alter the file /usr/lib/eclipse/eclipse.ini, which I've done, but I still get the same error. Any ideas?

---

### Post by rangalo on 2008-06-06
Hi 

yes, you have to edit eclipse.ini file

write

```

-Xmx256m
```

in the file and replace 256 with whatever memory you want to give to your vm in mb.

regards,
Hardik

---

### Post by Despot Despondency on 2008-06-06
Hey, thanks for your reply. Is it in the folder /usr/lib/eclipse? I've changed the eclipse.ini file in this folder to the following

```

-vmargs
-Xms256m
-Xmx1024m
```

but I still get the same error. Do I have refresh anything in eclipse itself? I'm using gutsy btw.

---

### Post by rangalo on 2008-06-06
this is unusual, but I think you need more memory than 256 so try changing  256  to something bigger like 512  be sure to leave some ram for other processes.

---

### Post by Despot Despondency on 2008-06-06
I've put it to Xms512m but I still have the same problem. I think it might be a problem with my program. I'm only trying to load a couple of megabytes of images so I should have enough memory. Thanks for your help. Is there anyway I can check the memory allocation to the java VM from eclipse, to ensure that the previous stuff has worked?

---

### Post by Despot Despondency on 2008-06-06
Maybe it would be easier if I just show the program. This part of the program is just going to load of images to create a map. 

```

package gui;

import java.awt.Dimension;
import java.awt.GridBagConstraints;
import java.awt.GridBagLayout;
import java.awt.Image;
import java.awt.Toolkit;
import java.util.Iterator;
import java.util.Set;

import javax.swing.ImageIcon;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JPanel;

import mechanics.Atlas;

import java.util.*;


public class GameMap {
	
    private static JFrame frame;
    private static JPanel backgroundPanel = new JPanel(new GridBagLayout());
    private static Map<String, JLabel> Countries;
    
    private static final GridBagConstraints gbc;
    static{
        gbc = new GridBagConstraints();
        gbc.gridx = 0;
        gbc.gridy = 0;
        gbc.weightx = 1.0;
        gbc.weighty = 1.0;
        gbc.fill = GridBagConstraints.BOTH;
        gbc.anchor = GridBagConstraints.NORTHWEST;
    }
    
    public static void main(String[] args){
        javax.swing.SwingUtilities.invokeLater(new Runnable(){
            public void run() {createAndShowMAP();}
        });
    }
    
    public GameMap(){
    	Countries = new HashMap<String, JLabel>();
    	createAndShowMAP();
    }
    
    private static void createAndShowMAP(){
		frame = new JFrame("Risk");		
		JFrame.setDefaultLookAndFeelDecorated(true);
		
        Image image = ImageUtil.create("images/risk.gif");
        frame.setIconImage(image);
        
		Dimension dim = Toolkit.getDefaultToolkit().getScreenSize();
        int screenWidth = (int)dim.getWidth();
        int screenHeight = (int)dim.getHeight(); 
        frame.setSize(screenWidth, screenHeight);
        
        ImageIcon Outline = new ImageIcon(GameMap.class.getResource("images/countries/outline.png"));
        ImageIcon Sea = new ImageIcon(GameMap.class.getResource("images/countries/sea.png"));
        
        JLabel outline = new JLabel(Outline);
        JLabel sea = new JLabel(Sea);
       
        backgroundPanel.add(outline, gbc);
        backgroundPanel.add(sea, gbc);
        
		frame.setContentPane(backgroundPanel);
        
		frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		frame.setVisible(true);	
        
    }
    
    public static void paintCountries(Atlas atlas){
    	
		Set countries = atlas.keySet();
		
		for(Iterator i = countries.iterator(); i.hasNext();)
		{
			String country = (String)i.next();
    	
			ImageIcon image = new ImageIcon(GameMap.class.getResource("images/countries/blue/" + country + ".png"));
			JLabel label = new JLabel(image);
			Countries.put(country, label);
			backgroundPanel.add(label, gbc);
		}
    }
}

```

The class the runs 

```

package connector;

import mechanics.Atlas;
import gui.GameMap;


public class Game {

	private static Atlas atlas;
	
	public static void main(String[] args){
		new GameMap();
		startGame();
	}
	
	public static void startGame(){
		
		atlas = new Atlas("maps/");
		
		GameMap.paintCountries(atlas);
	}
}

```

The folder of images is 169KB, so I don't understand why I'm getting these memory errors. Any help would be appreciated.

---

### Post by jespdj on 2008-06-06
> **rangalo said:**
> Hi 

yes, you have to edit eclipse.ini file
No. This will only increase the amount of memory available to the JVM in which Eclipse runs, but not to the JVM in which your program runs (it's launched as a separate process). Editing eclipse.ini will not make any difference for your program.

To increase the amount of memory for your program, go to Run / Open Run Dialog...

In the run configuration for your program, click on the Arguments tab, and in the VM Arguments box add the relevant parameters, for example: -Xmx256m

---

### Post by NormR2 on 2008-06-06
Is this the same program/problem:
[http://ubuntuforums.org/showthread.php?t=820721](http://ubuntuforums.org/showthread.php?t=820721)

Have you tried debugging your program to see where it's using all the memory?

Try adding print outs of the Runtime freeMemory() and totalMemory() values to see what is happening.

---

### Post by Despot Despondency on 2008-06-07
Hey, thanks for your responses. I've increased the memory using jespdj's method and the program seems to be working fine. I'm going to check my memory usage with jhat. Never used jhat before, so will have to find out about that. Cheers again for your help.

---

### Post by Plan B on 2008-06-10
> **rangalo said:**
> this is unusual, but I think you need more memory than 256 so try changing  256  to something bigger like 512  be sure to leave some ram for other processes.  

I tried doing this and got the message 
> You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.

How do I get permission to change it?

---

### Post by Despot Despondency on 2008-06-10
You need superuser/root rights to change the file, so in the terminal type

```

sudo gedit /usr/lib/eclipse/eclipse.ini

```

and then enter the superuser/root password when asked for it. 

Note that I use gedit, so if you use a different text editor you will need to change the above line accordingly.

---

### Post by Plan B on 2008-06-10
Worked brilliantly, thanks.
:)

Though there is an eclipse.ini file in the lib64 folder also (cause I've got 64bit OS).  Should I change that too?


Another question what do   -Xms  & -Xmx  stand for?    Should I change both?

---

### Post by Despot Despondency on 2008-06-10
No worries. :)

Don't know about the first question. Afraid I'm a bit of a newbie  to linux and programming etc. 

Regarding the second question, I think Xms is the minimum memory allocation and Xmx is the maximum. Think the settings are dependent on your computer, how much RAM you have etc. Personally, I'd just play around with them until I'm happy. You could probably find the recommended minimum for eclipse somewhere on  the eclipse website. 

Hope that helps.

---

### Post by Plan B on 2008-06-11
> **Despot Despondency said:**
> 
Hope that helps.


Does, thanks again.

---

