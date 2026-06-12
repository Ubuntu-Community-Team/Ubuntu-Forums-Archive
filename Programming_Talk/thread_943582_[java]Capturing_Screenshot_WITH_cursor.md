---
title: "[java]Capturing Screenshot WITH cursor"
date: 2008-10-10
forum: Programming Talk
---

### Post by Pyro.699 on 2008-10-10
Hello,  I know and understand that when taking a screen shot the cursor is usually left out. A lot of the online solutions were to figure out the position of the cursor and place a rendered image at that place. I already have the method created to take a normal screenshot

```

package defaults;

import java.awt.AWTPermission;
import java.awt.image.RenderedImage;
import java.awt.AWTException;
import java.awt.Rectangle;
import java.awt.Robot;
import java.awt.Toolkit;
import java.io.File;
import java.io.IOException;
import javax.imageio.ImageIO;

public class ScreenCapture {

    public String imageType = "jpg";
    public String imageName = null;
    public String saveLocation = null;
    public void capture() {
        if (imageName == null || saveLocation == null) {
            return;
        }
        try {
            new AWTPermission("listenToAllAWTEvents");
            Robot robot = new Robot();
            Rectangle area = new Rectangle(Toolkit.getDefaultToolkit().getScreenSize());
            File target = new File(saveLocation, imageName + "." + imageType);
            saveImageToFile(robot.createScreenCapture(area), target);
        } catch (AWTException e) {
            e.getStackTrace();
        }
    }

    private void saveImageToFile(RenderedImage renderedImage, File target) {
        try {
            ImageIO.write(renderedImage, imageType, target);
        } catch (IOException e) {
            e.getStackTrace();
        }
    }
}

```

but what i need right now is to figure out how to get the image and place it properly in the screen shot taken by *Robot*. I would imagine you need to create another rectangle and then compile the 2 together to make one, but i could be wrong.

Thanks a lot
~Cody Woolaver

---

### Post by Pyro.699 on 2008-10-12
Sorry for the double post, but after a day and a half of searching online i still don't have the solution to this.

Thanks again
~Cody Woolaver

---

### Post by cl333r on 2008-10-12
1) If you need to take screenshots outside of the frame of your Java program one needs to find a way to track the mouse position  (outside your program/frame).
2) If you manage to solve the former point, drawing it to the final image is no problem, as you can paint a standard cursor, painting the exact shape and color of the user's cursor is I think unimportant. Once again, the whole problem is _where_ to paint it on the screenshot area.

---

### Post by geirha on 2008-10-12
MouseInfo seems to know the location of the mouse pointer.
```

System.out.println(java.awt.MouseInfo.getPointerInfo().getLocation());

```

---

### Post by Pyro.699 on 2008-10-12
So we can now get the location of the pointer:

```

int x = Integer.parseInt(MouseInfo.getPointerInfo().getLocation().x+"");
int y = Integer.parseInt(MouseInfo.getPointerInfo().getLocation().y+"");

```The area that i'm not really the best at is figuring out how to place the mouse vector (**mouse.jpg** for this example) at point **x,y**.

I got the cursor, its the one i'm planning on using for the display.

Thanks
~Cody Woolaver

---

### Post by geirha on 2008-10-12
This tutorial seems to cover it well [http://java.sun.com/docs/books/tutorial/2d/images/index.html](http://java.sun.com/docs/books/tutorial/2d/images/index.html)

EDIT: BTW, the two attributes java.awt.Point has, are the integers x and y, why are you converting them to String and then back to integers?

---

### Post by Pyro.699 on 2008-10-12
Right -.-

I noticed that getLocation() wasn't **int**, it was **Point** guess i should have looked over it a bit better, my bad

---

### Post by cl333r on 2008-10-12
> **Pyro.699 said:**
> So we can now get the location of the pointer:

```

int x = Integer.parseInt(MouseInfo.getPointerInfo().getLocation().x+"");
int y = Integer.parseInt(MouseInfo.getPointerInfo().getLocation().y+"");

```The area that i'm not really the best at is figuring out how to place the mouse vector (**mouse.jpg** for this example) at point **x,y**.

I got the cursor, its the one i'm planning on using for the display.

Thanks
~Cody Woolaver

```

java.awt.image.BufferedImage screeenshot = robot.createScreenCapture(area);
Graphics2D g = screenshot.createGraphics();
g.drawImage( cursorImage, cursorX, cursorY, whateverClass );

//now your screenshot image has a cursor drawn on it
//at the right position,
//time to save it to a file.

```

---

### Post by Pyro.699 on 2008-10-12
I tried to use this:

```

Robot robot = new Robot();
Rectangle area = new Rectangle(Toolkit.getDefaultToolkit().getScreenSize());

BufferedImage sc = robot.createScreenCapture(area);
Image cur = ImageIO.read(new File("cursor.gif"));

Graphics2D g2d = sc.createGraphics();
g2d.drawImage(cur, MouseInfo.getPointerInfo().getLocation().x, MouseInfo.getPointerInfo().getLocation().y, ScreenCapture);

```

But there were a few things that were wrong with it. **ScreenCapture** is the name of the main class (as in the file is called "**ScreenCapture.java**") and it said "ScreenCapture cannot be resolved" (this is being done in eclipse).  Also, is there anyway to change **Graphics2D** back to **BufferedImage** or **RenderedImage**.

Thanks
~Cody Woolaver

---

### Post by Zugzwang on 2008-10-12
> **Pyro.699 said:**
> But there were a few things that were wrong with it. **ScreenCapture** is the name of the main class (as in the file is called "**ScreenCapture.java**") and it said "ScreenCapture cannot be resolved" (this is being done in eclipse).

That must be a problem hidden somewhere in your design - so we cannot help you here (insufficient information).

> 
  Also, is there anyway to change **Graphics2D** back to **BufferedImage** or **RenderedImage**.

You are misinterpreting the idea behing Graphics2D objects (also, I don't know if you can draw on top of images already existing - might not work as expected. In that case, paint both the captured image and the cursor into a new BufferedImage). The "Graphics" class is simply some abstract class for painting onto surfaces of some type. After you have used it, you don't convert it to something - You *dispose* it and forget about it. The changes should then be done on the device/image from which you got that Graphics2D instance.

There's a link for the tutorial somewhere in this thread. You should read that for further information.

---

### Post by cl333r on 2008-10-12
It's ok to paint on the Graphics2D of any Image, that's one way to create animations in Java btw.
Upload your eclipse project and I or someone else will have a look it and figure out why it won't compile.

---

### Post by Pyro.699 on 2008-10-12
Thank you very much for looking at this
~Cody Woolaver

---

### Post by geirha on 2008-10-12
Based on your code I made this simple main-method to test.
```

    public static void main (String args[]) throws Exception
    {
        Robot robot = new Robot();
        Toolkit toolkit= Toolkit.getDefaultToolkit();
        Rectangle screen_area= new Rectangle(toolkit.getScreenSize());

        Point p= MouseInfo.getPointerInfo().getLocation();
        BufferedImage screenshot= robot.createScreenCapture(screen_area);

        BufferedImage cursor= ImageIO.read(new File("cursor.gif"));
        screenshot.createGraphics().drawImage(cursor, p.x, p.y, null);

        ImageIO.write(screenshot, "jpg", new File("output.jpg"));
    }

```
And it works for me. Just passing null as ImageObserver.

---

### Post by cl333r on 2008-10-12
I'm not to bright in Eclipse so I recreated it in Netbeans 6.1, there were a few issues, but now it works and also paints the cursor. Screenshot created with your app is attached as well as the working Netbeans project (sorry, I find eclipse way less intuitive).

---

