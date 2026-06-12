---
title: "Loading Gifs into an array using Java"
date: 2009-04-09
forum: Programming Talk
---

### Post by craigdele on 2009-04-09
I wish to load several Gif pictures into an array and then later select some of these gifs and attach to a label. What is the best approach?


ImageIcon orange = new ImageIcon ("orange.gif");
ImageIcon apple = new ImageIcon ("apple.gif");
ImageIcon banana = new ImageIcon ("banana.gif");

Image[] images = new Image[3];

How do a load into array and then from array to Label

thanks 

Craig Delehanty

---

### Post by soltanis on 2009-04-09
Mo better, put the names into an array, then use a loop to init the image array.

```

String[3] names;
ImageIcon[3] images;
names[0] = "orange.gif";
names[1] = "banana.gif";
names[2] = "apple.gif";

for (int i = 0; i < names.length; i++) {
 images[i] = new ImageIcon(names[i]);
}

```

Second question I don't have an answer to, sorry.

---

### Post by PaulM1985 on 2009-04-10
If you do as the previous post and load the filenames into a String array, you can add them like this:

```
public class MyImages extends JFrame
{
    private JLabel[] myImages;
    private String[] imageNames;
    private JPanel panel;
    public MyImages()
    {
	setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
	setSize(700, 300);
	setVisible(true);

                   // Creates a panel and adds it to the JFrame
	panel = new JPanel();
	this.add(panel);

	imageNames = new String[2];
	myImages = new JLabel[2];

	imageNames[0] = "ImagesTest/smallscarylaser1.gif";
	imageNames[1] = "ImagesTest/smallscarylaser2.gif";

	for (int i = 0; i<2; i++)
	    {
                      // adds a new JLabel to you JLabel array with the 
                      // image loaded in
		myImages[i] = new JLabel(new ImageIcon(imageNames[0]));

                      // adds the JLabel in position i in the JLabel
                      // array to your panel
		panel.add(myImages[i]);
	    }

                      // adds a new JLabel with "Hello" to the panel.
	panel.add(new JLabel("Hello"));
    }
}
```

Hope this helps

Paul

I just thought, you may want to add try and catch statements around the myImages[i] line to avoid an exception being thrown if the gif file cannot be found.

---

