---
title: "Java Frames and issues with load times"
date: 2010-08-28
forum: Programming Talk
---

### Post by Ravenshade on 2010-08-28
Okay, so not exactly certain where to put this but I have a feeling some of you might have had this problem before. 

I've installed netbeans on Ubuntu (Karmic) and I've been playing around with creating programs and simple applications. Yet then I come to frames (via swing). 

My problem is that, I can start a frame up (on testing) and it'll freeze...as I'm then unable to close it or do much else. 

I think this is to do with openJDK...I remember having problems with one of the other before (not sure which one was causing the problems) and this is the only problem I've found since. 

Anyone know a quick solution?

---

### Post by akoskm on 2010-08-28
> **Ravenshade said:**
> Okay, so not exactly certain where to put this but I have a feeling some of you might have had this problem before. 

I've installed netbeans on Ubuntu (Karmic) and I've been playing around with creating programs and simple applications. Yet then I come to frames (via swing). 

My problem is that, I can start a frame up (on testing) and it'll freeze...as I'm then unable to close it or do much else. 

I think this is to do with openJDK...I remember having problems with one of the other before (not sure which one was causing the problems) and this is the only problem I've found since. 

Anyone know a quick solution?

My experience is that swing components are "freezing" if you remove their reference after creating and putting them to a container/frame.
But... there are a few more things what can causes your frame to "freeze", example if you forget to set the default close operation for the frame - in this case the frame is appearing but you can't close it by clicking on the X button.
Can you post the source of a simple application, where the frame is freezing?

---

### Post by Ravenshade on 2010-08-28
Bearing in mind the application is not yet complete (and my knowledge of swing is sketchy at best) 

note: I also have a familiar problem, where the frame itself doesn't appear no matter what settings I declare. It appears right at start up, it loads, displays the images and runs through the programs (although I can't get it to work without needing netbeans at the moment) then it just drags and takes ages to respond. 

```


package javagameexperiment;

import javax.swing.JFrame;

/**
 *
 * @author ravenshade
 */
public class GameFrame {

    public static void main(String args[]) {

        int fWidth = 600;
        int fHeight = 400;

        JFrame frame = new JFrame("2d Game");

        frame.setIgnoreRepaint(true);
        frame.setBounds(0, 0, fWidth, fHeight);
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

        GameCanvas game = new GameCanvas();

        frame.add(game);

        frame.setVisible(true);


    }
}

```

---

### Post by Reiger on 2010-08-29
And you would not by any chance happen to be doing resource intensive computations (I/O, complex renders etc.) during “new GameCanvas()” ?

---

### Post by Ravenshade on 2010-08-29
Erm, I wouldn't have thought so, but Java isn't really designed for getting input from the user -.-; 

I've still got more to do to it and I think I may have to split the canvas into different sections but... 

Here's the code:

```


package javagameexperiment;
import java.awt.Canvas;
import java.awt.Color;
import java.awt.Graphics;
import java.awt.event.KeyEvent;
import java.awt.event.KeyListener;
import java.awt.image.BufferStrategy;



/**
 *
 * @author tsenzori
 */
public class GameCanvas extends Canvas implements Runnable, KeyListener {

    int fWidth = 600;
    int fHeight = 400;

    public long period = 10;

    public BufferStrategy Buffer;
    public Graphics graphics;

    //list of known entities

    public AppleEntity apple;
    public ManEntity man;

    private Thread t; //needed for runnable interfaces

    public GameCanvas(){
        this.setIgnoreRepaint(true);
        this.setBounds(0, 0, fWidth, fHeight);
        this.setBackground(Color.WHITE);

        this.setVisible(true);

        apple = new AppleEntity("apple1.gif", 50, 50);
        man = new ManEntity("ball.gif", 50, 50);
    }
    @Override
    public void addNotify() {
        super.addNotify();
        this.createBufferStrategy(2);
        this.Buffer = this.getBufferStrategy();
        this.addKeyListener(this);
        requestFocus();

        startGame();
    }

    public void startGame() {
        if (t == null) {
            t = new Thread(this);
            t.start();
        }
        
    }
    
    
    public void run(){
        while(true) {
            
            long beginTime = System.currentTimeMillis();
            
            update();
            render();
            draw();
            
            long timeTaken = System.currentTimeMillis();
            long sleepTime = period - timeTaken;
            
            try {
                
                Thread.sleep(sleepTime);
                
            } catch (Exception e){
                
            }
        }
    }
    
    public void update() {
        //apple.Fall();
        man.move(200);
    }
    
    public void render() {
        graphics = Buffer.getDrawGraphics();
        graphics.setColor(Color.BLACK);
        graphics.fillRect(0,0, fWidth, fHeight);
        
        //paint stuff =D
        apple.Draw(graphics);
        man.Draw(graphics);

    }
    
    public void draw() {
        if(!Buffer.contentsLost()) {
            Buffer.show();
            
            if (graphics != null) {
                graphics.dispose();
            }
        }
    }

    public void keyPressed(KeyEvent e) {
        if (man.exists()){
            if (e.getKeyCode() == KeyEvent.VK_LEFT) {
                man.setHorizontalMovement(-5);
            }
        }
        if (man.exists()){
            if (e.getKeyCode() == KeyEvent.VK_RIGHT) {
                man.setHorizontalMovement(5);
            }
        }
    }

    public void keyReleased(KeyEvent e) {
        if (man.exists()){
            if (e.getKeyCode() == KeyEvent.VK_LEFT) {
                man.setHorizontalMovement(0);
            }
        }
        if (man.exists()){
            if (e.getKeyCode() == KeyEvent.VK_RIGHT) {
                man.setHorizontalMovement(0);
            }
        }
    }

    public void keyTyped(KeyEvent arg0) {
        throw new UnsupportedOperationException("Not supported yet.");
    }
}

```

---

