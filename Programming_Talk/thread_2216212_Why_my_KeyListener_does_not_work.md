---
title: "Why my KeyListener does not work ?"
date: 2014-04-10
forum: Programming Talk
---

### Post by Songpol on 2014-04-10
import java.awt.Graphics;
import java.awt.*;
import javax.swing.*;
import java.awt.event.*;


public class Background extends JPanel implements KeyListener
{
    public Block bar[][];
    public Circle ball;
    public Calculate c;
    public Paddle p;
    public Background()
    {
        ball = new Circle();
        bar = new Block[9][12];
        c = new Calculate();
        p = new Paddle(278,330,80,10,10,10);
        this.setFocusable(true);
        this.requestFocus();
        addKeyListener(this);


        Thread t = new Thread(new Runnable()
                {


                    @Override
                    public void run(){
                        while (true){
                            try{
                                Thread.sleep(20);
                            } catch (Exception e){}
                            ball.move();
                            if(p.getLeft()) p.moveLeft();


                            if(p.getRight()) p.moveRight();


                            for (int i = 0; i < bar.length; i++){
                                for (int j = 0; j < bar[0].length; j++){


                                }
                            }
                            repaint();
                        }
                    }
                });
        t.start();


    }


    public void paint(Graphics g){
        super.paint(g);
        for (int i = 0; i < bar.length; i++){
            for (int j = 0; j < bar[0].length; j++){
                if((j<2||j>9 )){
                    g.setColor(new Color(251,113,152)); 
                    g.fillRect(c.getBlock(i,j).getX(),c.getBlock(i,j).getY(),c.getBlock(i,j).getWidth(),c.getBlock(i,j).getHeight());
                    g.setColor(new Color(254,14,14)); 
                    g.drawRect(c.getBlock(i,j).getX(),c.getBlock(i,j).getY(),c.getBlock(i,j).getWidth(),c.getBlock(i,j).getHeight());
                }
                else if ((i==4)&&(j>1 && j<10)){
                    g.setColor(new Color(115,163,233)); 
                    g.fillRect(c.getBlock(i,j).getX(),c.getBlock(i,j).getY(),c.getBlock(i,j).getWidth(),c.getBlock(i,j).getHeight());
                    g.setColor(new Color(0,0,0)); 
                    g.drawRect(c.getBlock(i,j).getX(),c.getBlock(i,j).getY(),c.getBlock(i,j).getWidth(),c.getBlock(i,j).getHeight());
                }
                else if((j>3&&j<8 && (i<3 || i>5))){
                    g.setColor(new Color(204,102,205)); 
                    g.fillRect(c.getBlock(i,j).getX(),c.getBlock(i,j).getY(),c.getBlock(i,j).getWidth(),c.getBlock(i,j).getHeight());
                    g.setColor(new Color(83,10,106)); 
                    g.drawRect(c.getBlock(i,j).getX(),c.getBlock(i,j).getY(),c.getBlock(i,j).getWidth(),c.getBlock(i,j).getHeight());
                }
            }
        }
        ball.draw(g);
        p.draw(g);
    }


    public void keyPressed(KeyEvent e) {
        System.out.println("TTTTTTTTTTTTttt");
        if (e.getKeyCode() == KeyEvent.VK_LEFT) {
            System.out.println("TTTTTTTTTTTTttt");
            p.setLeft(true);
        }
        if (e.getKeyCode() == KeyEvent.VK_RIGHT) {
            p.setRight(true);
        }
    } 


    public void keyReleased(KeyEvent e) {
        System.out.println("TTTTTTTTTTTTttt");
        if (e.getKeyCode() == KeyEvent.VK_LEFT) {
            p.setLeft(false);
        }
        if (e.getKeyCode() == KeyEvent.VK_RIGHT) {
            p.setRight(false);
        }
    }


    public void keyTyped(KeyEvent e) {}
}

---

### Post by ofnuts on 2014-04-10
[http://ubuntuforums.org/showthread.php?t=835021](http://ubuntuforums.org/showthread.php?t=835021)

---

### Post by Songpol on 2014-04-11
It's does not work for me.

---

