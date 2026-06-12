---
title: "Java Adding Images to JLabels"
date: 2013-03-07
forum: Programming Talk
---

### Post by Kodeine on 2013-03-07
[FONT=Arial]I’m new to Java and are currently having some problems with adding images to a swing window. My method is to load separate images, create a graphic from the background image and merge all images together at specific points on the background. This is then added to a JLabel and appended to the window. [/FONT]

[FONT=Arial]My first call to Draw() works fine [/FONT][http://imgur.com/tuBRFFX](http://imgur.com/tuBRFFX)

[FONT=Arial]But my second doesn't change a thing. This second call comes after the user presses the right arrow key. Upon that we attempt to create another image, of scooby doo, further to the right of the original. Which it does but only[/FONT]* when you maximise*[FONT=Arial] the window. [/FONT][http://imgur.com/JtIUizV](http://imgur.com/JtIUizV)[FONT=Arial] I would like it replace the initial image whilst the window is still in an unmaximised state.[/FONT]

[FONT=Arial]My [/FONT]*DrawArray*[FONT=Arial] is structured as follows, BufferedImage (Whatever image we want to draw),int(it's X position to be placed on BG),int (Y).[/FONT][B][FONT=Arial]

The main java file - ZacksApplication.java
[/FONT][/B]```

      Window.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
      Window.setSize(850, 625);
      Window.setVisible(true); //Setting up the window
      
      DrawArray.add(Load.LoadImg("Images/Backdrops/LivingRoom.png"));//The Image
      DrawArray.add(100);//The X
      DrawArray.add(0);//The Y
      
      DrawArray.add(pth.scooby[0]);//Shaggy and scooby facing down
      DrawArray.add(200);
      DrawArray.add(400);


      Draw.DrawImg();
```
**Draw.Java**
```

public static void DrawImg()
           {
           BufferedImage BGImg = (BufferedImage) ZacksApplication.DrawArray.get(0); //Load background img
           int width = BGImg.getWidth();
           int height = BGImg.getHeight();
              //Get the width and height of the background
           
           BufferedImage Merged = new BufferedImage (width,height,BufferedImage.TYPE_INT_RGB);
               //Create the image that will hold ALL OTHER images.
           Graphics Graph = Merged.getGraphics();
           
           for(int i=0; i<ZacksApplication.DrawArray.size();)
                     {
                     //System.out.println(i);
                     BufferedImage Image = (BufferedImage) ZacksApplication.DrawArray.get(i); //Read the image we need to draw
                     int x = (int) ZacksApplication.DrawArray.get(i+1);
                     int y = (int) ZacksApplication.DrawArray.get(i+2);
                     
                     Graph.drawImage(Image, x, y, null);
                     i = i+3;
                     }
           
           JLabel DoneImg = new JLabel(new ImageIcon(Merged));
           Keys.BindKeys(DoneImg);
           
           ZacksApplication.Window.getContentPane().add(DoneImg);
           }
```

---

