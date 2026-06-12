---
title: "Java Drawing Multiple Images"
date: 2013-02-28
forum: Programming Talk
---

### Post by Kodeine on 2013-02-28
[B][FONT=Arial]I’m attempting to create a simple point-n-click adventure game in Java. I’m currently trying to get the fundamental aspect of it down that is drawing images on the screen. The scenario is going to be the same almost all the time whereby I will need to draw a background image and then several other images (characters etc) over the top of the background. Later on I will need to move character images, I imagine this will involve needing to draw the background again followed by the same character images but moved slightly.[/FONT]

[FONT=Arial]I was recently working under the idea of using ‘Graphic2D’ and that’s why you will see it popup in the code below. My original idea was to load an image and add it to a jlabel. Then use setLocation() to position the image in the frame.[/FONT]

[/B]```
[B][FONT=Arial]public static Graphics2D Graphic = LoadImg("Images/Backdrops/Outside1.png").createGraphics();[/FONT]
[FONT=Arial]     //Graphic.setRenderingHint(RenderingHints.KEY_ANTIALIASING,RenderingHints.VALUE_ANTIALIAS_ON);[/FONT]
[FONT=Arial]         //Create graphic that will hopefully hold all images displayed on the JFrame.[/FONT]

[FONT=Arial]     public static void main(String[] args)[/FONT]
[FONT=Arial]          {[/FONT]
[FONT=Arial]          JFrame Window = new JFrame();[/FONT]
[FONT=Arial]          Window.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);[/FONT]
[FONT=Arial]          Window.setSize(1000, 625);[/FONT]
[FONT=Arial]          Window.setVisible(true);[/FONT]
[FONT=Arial]             //Setup window using swing[/FONT]

[FONT=Arial]          Window.getContentPane().add(DrawImg("Images/Backdrops/Outside1.png",500,0));[/FONT]
[FONT=Arial]          //Window.getContentPane().add(DrawImg("Images/Characters/Test.png",500,0));[/FONT]
[FONT=Arial]          }[/FONT]

[FONT=Arial]     public static JLabel DrawImg(String ImageLoc, int x, int y) [/FONT]
[FONT=Arial]        {[/FONT]
[FONT=Arial]        BufferedImage Image = LoadImg(ImageLoc);[/FONT]

[FONT=Arial]        //Graphic.drawImage(Image, x, y, null);[/FONT]
[FONT=Arial]        //Graphic.dispose(); //![/FONT]

[FONT=Arial]        JLabel ReadyLabel = new JLabel(new ImageIcon(Image));[/FONT]
[FONT=Arial]        ReadyLabel.setLocation(x,y); //Doesn't seem to maneuver the image?[/FONT]
[FONT=Arial]        return ReadyLabel;[/FONT]
[FONT=Arial]        }[/FONT]

[FONT=Arial]     public static BufferedImage LoadImg(String ImgPath)[/FONT]
[FONT=Arial]              {[/FONT]
[FONT=Arial]              BufferedImage buffer = null;[/FONT]
[FONT=Arial]              try[/FONT]
[FONT=Arial]                 { [/FONT]
[FONT=Arial]                 buffer = ImageIO.read(new File(ImgPath));[/FONT]
[FONT=Arial]                 }[/FONT]
[FONT=Arial]              catch (Exception e){}[/FONT]
[FONT=Arial]              return buffer;[/FONT]
[FONT=Arial]              }[/FONT][/B]
```[B]
[FONT=Arial]setLocation() however does not place the image where specified. There is also the problem of only displaying one image at a time. How can I accomplish these two things? Do I need to use either Graphic2D or Canvas?[/FONT][/B]

---

### Post by Zugzwang on 2013-03-01
Hi Kodeine, 

I suggest that you look up what the "setLocation" location function does. It sets the location of a component *in a layout*, and not in pixels. If your layout contains only one element, then it doesn't matter if you put an element at position (500,0) or (0,0) - the other layout cells are simply not used.

If you want to get fine-grained control of where stuff is drawn, then you will need to paint on your own.  Either you derive a JPanel and override the paining methods, *or* you allocate a BufferedImage of the correct size and you draw *into* that image what you want to draw. There are examples for that on the web. After finishing the BufferedImage, you can convert it to an ImageIcon and assign it to a JLabel. This approach of doing things is mainly used for the case that what you want to display doesn't change often.

---

### Post by slickymaster on 2013-03-01
> **Zugzwang said:**
> Hi Kodeine, 

I suggest that you look up what the "setLocation" location function does. It sets the location of a component *in a layout*, and not in pixels. If your layout contains only one element, then it doesn't matter if you put an element at position (500,0) or (0,0) - the other layout cells are simply not used.

If you want to get fine-grained control of where stuff is drawn, then you will need to paint on your own.  Either you derive a JPanel and override the paining methods, *or* you allocate a BufferedImage of the correct size and you draw *into* that image what you want to draw. There are examples for that on the web. After finishing the BufferedImage, you can convert it to an ImageIcon and assign it to a JLabel. This approach of doing things is mainly used for the case that what you want to display doesn't change often.

Completely correct.

A BufferedImage is essentially an Image with an accessible data buffer. It is therefore more efficient to work directly with it, because not only it manages the image in memory but also provides methods for storing, interpreting, and obtaining pixel data.

---

