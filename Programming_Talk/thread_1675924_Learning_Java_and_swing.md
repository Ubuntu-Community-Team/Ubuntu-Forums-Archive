---
title: "Learning Java and swing"
date: 2011-01-26
forum: Programming Talk
---

### Post by minerbog on 2011-01-26
Hi Guys,

I am just learning Java and have a question that I'm not sure of.

In my project I have Main.java, MP3.java, GUI.java. Referencing javazoom.

When running from main its easy to:
```

MP3 mp3 = new MP3(filename);
mp3.play();  etc etc

```

How ever no matter what I see to do I cannot get a reference to the mp3 object from my button action sub. 
```

private void button1ActionPerformed(java.awt.event.ActionEvent evt) {


    }

```
I just get the 'cant find symbol' error.

What am I doing wrong.

Many Thanks

Gavin.

---

### Post by PaulM1985 on 2011-01-26
Can you post more code so that it is easier to see what is going on?

Do you give your GUI an MP3 object that it can act on?

Paul

---

### Post by minerbog on 2011-01-26
Paul,

The Main.java file:
```

/*
 * To change this template, choose Tools | Templates
 * and open the template in the editor.
 */

package listerplayer;

import java.util.Scanner;
/**
 *
 * @author gavin
 */
public class Main {

    /**
     * @param args the command line arguments
     */
    public static void main(String[] args) {
        // TODO code application logic here


        new ListerPlayerUI().setVisible(true);
        String filename = "/home/gavin/Music/1.mp3";
        MP3 mp3 = new MP3 (filename);
        mp3.load();

    }

}

```
The MP3.java file:
```

/*
 * To change this template, choose Tools | Templates
 * and open the template in the editor.
 */

package listerplayer;

/**
 *
 * @author gavin
 */
import java.io.BufferedInputStream;
import java.io.FileInputStream;
import java.text.DecimalFormat;
import javazoom.jl.player.Player;


public class MP3 {
    private String filename;
    private Player player;

    // constructor that takes the name of an MP3 file
    public MP3(String filename) {
        this.filename = filename;
    }

    public int gettime() {
    	return player.getPosition();
    }

    public boolean getcomp() {
    	return player.isComplete();
    }

    public void close() { if (player != null) player.close(); }

    // play the MP3 file to the sound card
    public void load() {
        try {
        	System.out.println("Start of play()");
        	System.out.println("FileInutstream");
            FileInputStream fis     = new FileInputStream(filename);
            System.out.println("BufferInputStream");
            BufferedInputStream bis = new BufferedInputStream(fis);
            System.out.println("Loading...");
            player = new Player(bis);

        }
        catch (Exception e) {
            System.out.println("Problem playing file " + filename);
            System.out.println(e);
        }
    }

    public void play() {
                // run in new thread to play in background
        new Thread() {
            public void run() { System.out.println("New Run");
                try {player.play();
                }
                catch (Exception e) { System.out.println(e); }
            }
        }.start();
    }

    public void times() {
            new Thread() {
            public void run() {
                try {
                int test = 0;
                int lastprint = 0;
                boolean flag = false;
                test = player.getPosition();
                DecimalFormat formatter = new DecimalFormat("00");
                 do{
                    double sec1 = (test / 1000) % 60;
                    int min = (test / 1000) / 60;
                    String sec = formatter.format(sec1);
                    int milsec = (test / 100) % 10;
                            if(milsec!=lastprint){
                            System.out.println(min + ":" + sec + "." + milsec);
                            lastprint = milsec;
                                    if (player.isComplete()){
                                            //flag = false;
                                            break;
                                    }
                            }
                    }while(flag);
                }catch (Exception e) { System.out.println(e); }
            }
            }.start();
    }
    // test client
    public static void main(String[] args) {
        String filename = "/home/gavin/Music/1.mp3";
        MP3 mp3 = new MP3(filename);
        System.out.println("MP3 object loaded.  Now Playing..." + filename);
        mp3.play();
        boolean flag = true;
        int test = 0;
        int lastprint = 0;
        DecimalFormat formatter = new DecimalFormat("00");
        do{
        	test = mp3.gettime();
	        double sec1 = (test / 1000) % 60;
	        int min = (test / 1000) / 60;
	        String sec = formatter.format(sec1);
	        int milsec = (test / 100) % 10;
		        if(milsec!=lastprint){
		        System.out.println(min + ":" + sec + "." + milsec);
		        lastprint = milsec;
			        if (mp3.getcomp()){
			        	//flag = false;
			        	break;
			        }
		        }
        }while(flag);
        //mp3.close();
        System.out.println("End of file");





    }//close main

}//close class

```
The gui java file:
```

/*
 * To change this template, choose Tools | Templates
 * and open the template in the editor.
 */

/*
 * ListerPlayerUI.java
 *
 * Created on 26-Jan-2011, 15:27:01
 */

package listerplayer;

 
/**
 *
 * @author gavin
 */
public class ListerPlayerUI extends javax.swing.JFrame {

    /** Creates new form ListerPlayerUI */
    public ListerPlayerUI() {
        initComponents();
    }

    /** This method is called from within the constructor to
     * initialize the form.
     * WARNING: Do NOT modify this code. The content of this method is
     * always regenerated by the Form Editor.
     */
    @SuppressWarnings("unchecked")
    // <editor-fold defaultstate="collapsed" desc="Generated Code">
    private void initComponents() {

        button1 = new java.awt.Button();
        button2 = new java.awt.Button();

        setDefaultCloseOperation(javax.swing.WindowConstants.EXIT_ON_CLOSE);

        button1.setLabel("button1");
        button1.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                button1ActionPerformed(evt);
            }
        });

        button2.setLabel("button2");
        button2.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                button2ActionPerformed(evt);
            }
        });

        javax.swing.GroupLayout layout = new javax.swing.GroupLayout(getContentPane());
        getContentPane().setLayout(layout);
        layout.setHorizontalGroup(
            layout.createParallelGroup(javax.swing.GroupLayout.Alignment.LEADING)
            .addGroup(layout.createSequentialGroup()
                .addGap(61, 61, 61)
                .addComponent(button1, javax.swing.GroupLayout.PREFERRED_SIZE, javax.swing.GroupLayout.DEFAULT_SIZE, javax.swing.GroupLayout.PREFERRED_SIZE)
                .addContainerGap(273, Short.MAX_VALUE))
            .addGroup(javax.swing.GroupLayout.Alignment.TRAILING, layout.createSequentialGroup()
                .addContainerGap(222, Short.MAX_VALUE)
                .addComponent(button2, javax.swing.GroupLayout.PREFERRED_SIZE, javax.swing.GroupLayout.DEFAULT_SIZE, javax.swing.GroupLayout.PREFERRED_SIZE)
                .addGap(112, 112, 112))
        );
        layout.setVerticalGroup(
            layout.createParallelGroup(javax.swing.GroupLayout.Alignment.LEADING)
            .addGroup(layout.createSequentialGroup()
                .addGap(89, 89, 89)
                .addComponent(button1, javax.swing.GroupLayout.PREFERRED_SIZE, javax.swing.GroupLayout.DEFAULT_SIZE, javax.swing.GroupLayout.PREFERRED_SIZE)
                .addGap(47, 47, 47)
                .addComponent(button2, javax.swing.GroupLayout.PREFERRED_SIZE, javax.swing.GroupLayout.DEFAULT_SIZE, javax.swing.GroupLayout.PREFERRED_SIZE)
                .addContainerGap(118, Short.MAX_VALUE))
        );

        pack();
    }// </editor-fold>

    private void button1ActionPerformed(java.awt.event.ActionEvent evt) {

    mp3.play();
    }

    private void button2ActionPerformed(java.awt.event.ActionEvent evt) {

    }

    /**
    * @param args the command line arguments
    */
    public static void main(String args[]) {

        java.awt.EventQueue.invokeLater(new Runnable() {
            public void run() {
                new ListerPlayerUI().setVisible(true);
            }
        });

    }

    // Variables declaration - do not modify
    private java.awt.Button button1;
    private java.awt.Button button2;
    // End of variables declaration

}

```

I don't think I have passed anything????? :(

Gavin.

---

### Post by fct on 2011-01-26
Hi.

The scope of the mp3 var is ONLY in the main method, since it was declared there and is not passed on.

You need to pass it to the UI class somehow.

Also, please check some OOP tutorials since it's better if you learn the basics about objects before getting into Java GUIs (which use it extensively).

---

### Post by minerbog on 2011-01-26
> **fct said:**
> Hi.

The scope of the mp3 var is ONLY in the main method, since it was declared there and is not passed on.

You need to pass it to the UI class somehow.


I understand scope and a bit about oop from PHP. I just need to know how to pass the mp3 object to the UI!!

Thanks

---

### Post by GregBrannon on 2011-01-26
Passing object a to object b:

Create object a:

A a = new A();

pass object a to object b through the object b constructor:

B b = new B(a);


Good luck!

---

### Post by fct on 2011-01-26
> **minerbog said:**
> I understand scope and a bit about oop from PHP. I just need to know how to pass the mp3 object to the UI!!

Thanks

This is one way: you would declare it as a field in the UI class (considering it's a dialog), then set it from the caller before show()ing it.

That is, for example, add this to the UI class:

```

private MP3 mp3;
public MP3 getMp3(){ return this.mp3};
public void setMp3(MP3 newMp3){ this.mp3 = newMp3 };

```

And call it using this style, more or less:
```

ui.setMp3(new MP3(filename ) );
ui.show();

```

Also, this way you can know which MP3 is playing from outside of the UI, using its getMp3() method.

---

### Post by minerbog on 2011-01-26
> **GregBrannon said:**
> Passing object a to object b:

Create object a:

A a = new A();

pass object a to object b through the object b constructor:

B b = new B(a);


Good luck!

Right so in Main.java I:
```

MP3 mp3 = new MP3(filename);

```
Then in ListerPlayerUI.java I:
```

MP3 mp31 = new MP3(mp3);

```

Yes??

If so it doesn't work. Its still saying it cannot find symbol for variable mp3??

Thanks Again.

---

### Post by fct on 2011-01-26
No, that's not the way. ListerPlayerUI still has no idea where that "mp3" is coming from.

It's a class, it needs either a var declared in its body, or it being passed as an arg thru some method.

Anyway, I'm afraid I can't help you further without writing a chapter on OOP that you can find elsewhere. Here:

[http://download.oracle.com/javase/tutorial/java/javaOO/variables.html](http://download.oracle.com/javase/tutorial/java/javaOO/variables.html)

---

