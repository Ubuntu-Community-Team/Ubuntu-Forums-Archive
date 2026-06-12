---
title: "Java - KeyListener Problem with multiple keys pressed"
date: 2010-05-11
forum: Programming Talk
---

### Post by Finalfantasykid on 2010-05-11
I am making a 2D RPG where the character can go left, right, up, down and diagonal(all 4 diagonal directions).  The character can also run by using the spacebar.

I have a problem though in that if you want to go up/left, then you decide to run, the spacebar will not be registered as a keyPressed() call, and this seems to vary depending on what computer I am using, for some people it seems it affects all diagonal directions.

Is there a way to make a KeyListener that will register many button presses all at the same time, or even better a listener for a single key.

---

### Post by PaulM1985 on 2010-05-11
Maybe try registering for key pressed and key released events.

For example if left key is pressed isLeft is set.  When left key is released isLeft is unset.  For diagonal "isTopLeft" you could check that isLeft and isTop are set.  That way it may be possible to register each single key, but use them as a group if you have something iterating through to check what state your keyboard is in with respect to keys being up or down.

Paul

(I have not checked that this definitely works.  Its just an idea.)

---

### Post by kahumba on 2010-05-11
You only need to track the key pressed and key released events and based on this info decide whether the key you're interested in is still pressed or not, it's the only way (that I know) which can solve your problem of having multiple keys pressed at the same time and processing them all accordingly.
I stumbled across this problem while creating a Java 2D game and that's how I solved it.

---

### Post by Finalfantasykid on 2010-05-11
> **kahumba said:**
> You only need to track the key pressed and key released events and based on this info decide whether the key you're interested in is still pressed or not, it's the only way (that I know) which can solve your problem of having multiple keys pressed at the same time and processing them all accordingly.
I stumbled across this problem while creating a Java 2D game and that's how I solved it.

By the sounds of it, that is what I am doing right now...
```

if(e.getKeyCode() == SPACE){
            this.location.doubleSpeed(true);
            this.location.talkToNPC();
            this.location.openChest();
            this.location.goShopping();
}
  else if (e.getKeyCode() == LEFT){
            this.location.moveLeft(speed);
}
else if (e.getKeyCode() == UP){
            this.location.moveUp(speed);
}
else if (e.getKeyCode() == DOWN){
            this.location.moveDown(speed);
}
else if (e.getKeyCode() == RIGHT){
            this.location.moveRight(speed);
}
else if (e.getKeyCode() == ENTER){
            this.location.toggleMenuGrid("mainMenu");
            this.sounds.getSound(Sound.Select).play();
}
```Unfortunatly, if do the following:

- Hold Left Button, then...
- Hold Up Button, then...
- Hold Spacebar

pressing the spacebar will not fire an Event.  Similarly, if...

- Hold Left Button, then...
- Hold Spacebar, then...
- Hold Up Button

Then the up button will not fire an Event, and you will continue to run left, not diagonally.

---

### Post by PaulM1985 on 2010-05-12
So currently you have created your own class and implemented KeyListener.  I am now assuming that you have implemented the methods keyPressed(KeyEvent e), keyReleased(KeyEvent e) and keyTyped(KeyEvent e)

Does the third press not get picked up by any of these events?

Also, I found this on another forum.. [http://72.5.124.102/thread.jspa?messageID=9422569](http://72.5.124.102/thread.jspa?messageID=9422569)

One poster suggests it could be hardware related.  Are you able to register 3 keys being pressed for any other different combination of three keys?

Paul

---

### Post by kahumba on 2010-05-12
This is tested and works on xp, windows 7, ubuntu and mac os x 10.6.2, run the code and watch the title as it shows that the app is aware of when and for how long is each key (up, down, space bar) pressed and released.

```

package app;

import javax.swing.*;
import java.awt.event.*;

public class Main extends JPanel implements KeyListener, Runnable {
    boolean isUpPressed, isDownPressed, isSpacePressed;
    static JFrame f;

    public static void main(String[] args) {
        f = new JFrame();
        f.setSize(600,300);
        f.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        f.setContentPane(new Main());
        f.setVisible(true);
    }

    public Main() {
        setFocusable(true);
        addKeyListener(this);
        new Thread(this).start();
    }

    public void keyTyped(KeyEvent ke) {
    }

    public void keyPressed(KeyEvent ke) {
        switch(ke.getKeyCode()) {
            case KeyEvent.VK_UP: isUpPressed = true; break;
            case KeyEvent.VK_DOWN: isDownPressed = true; break;
            case KeyEvent.VK_SPACE: isSpacePressed = true; break;
        }
    }

    public void keyReleased(KeyEvent ke) {
        switch(ke.getKeyCode()) {
            case KeyEvent.VK_UP: isUpPressed = false; break;
            case KeyEvent.VK_DOWN: isDownPressed = false; break;
            case KeyEvent.VK_SPACE: isSpacePressed = false; break;
        }
    }

    public void run() {
        while(true) {
            try {
                String s = "up pressed: " + isUpPressed + ", down pressed: " + isDownPressed +
                        ", spacePressed: " + isSpacePressed;
                f.setTitle(s);
                Thread.sleep(200);
            } catch(Exception exc) {
                exc.printStackTrace();
                break;
            }
        }
    }
}

```

---

