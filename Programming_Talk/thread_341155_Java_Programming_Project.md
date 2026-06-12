---
title: "Java Programming Project"
date: 2007-01-18
forum: Programming Talk
---

### Post by zsimplicityz on 2007-01-18
Hey all ..

I've got a serious problem for the following school project !

Been a really newbie in Java GUI & Applets ..

So hopefully you guys could give me a hand .

Thanks :) 

The following are the project details ..

[[IMG]http://img181.imageshack.us/img181/7859/tp3wu5.th.png[/IMG]](http://img181.imageshack.us/my.php?image=tp3wu5.png)

[[IMG]http://img442.imageshack.us/img442/5536/tp4bj6.th.png[/IMG]](http://img442.imageshack.us/my.php?image=tp4bj6.png)

---

### Post by Josh1 on 2007-01-18
Whats the problem? Maybe show some information? :-?

---

### Post by Tomosaur on 2007-01-18
Yeah seriously, what's the problem? GUI creation in Java is fairly straightforward as GUI programming goes, but GUI programming in itself is pretty complex.

---

### Post by zsimplicityz on 2007-01-18
Er ..

for me it's like extremely difficult .

have done till here and i'm kinda lost for now ..

[[IMG]http://img346.imageshack.us/img346/8526/untitledyq8.th.jpg[/IMG]](http://img346.imageshack.us/my.php?image=untitledyq8.jpg)

---

### Post by Tomosaur on 2007-01-18
Sorry, that code image is far too small to read. Can't you just copy and paste?

BTW: I doubt anyone here is going to do your homework for you. Aside from a few pointers / corrections, this is the kind of thing you need to talk to your teacher about.

---

### Post by pmasiar on 2007-01-18
correct me if I am wrong, but your request (to me) looks more like: "please do my homework for me so I dont need to learn programming at all". Well, helping you would be *wrong* because; (1) it will help you cheat your teacher, and (2) you will not learn solve your own problems, and come again asking for more.

Correct way to ask for help is in format: "I am trying to do X, and A, B C does not work - what I am doing wrong?" - Do your homework first, do your best try, and many people will be tempted to help.

---

### Post by lloyd mcclendon on 2007-01-18
i will do it but i charge $40 / hr

---

### Post by jordilin on 2007-01-18
I recommend you read the java tutorial in the java.sun.com webpage and download the Netbeans IDE to do the GUI application. Work with it, begin coding and then if you have any doubt, ask.

---

### Post by gh0st on 2007-01-18
> **lloyd mcclendon said:**
> i will do it but i charge $40 / hr

This could start a bidding war :D

---

### Post by zsimplicityz on 2007-01-19
Oh man ..

You guys have got the wrong idea ..

This is the code that i've type out .

For now , i've got problem inserting images into my proecjt ..

Any idea where i should insert the command into ?


/*@authorNurhaslinda
 *@class P02*/
 
import java.awt.*;
import java.awt.event.*;
import java.awt.image.*;
import java.io.*;
import javax.imageio.*;
import javax.swing.*;


public class Jackpot extends JFrame {


  private JButton    jbtnSpin , jbtnReset;
  private JPanel     jpJackpotSys , jpImages , jpBetAmt , jpTp, jpButtons, 
  				     jpMiddle, jpMoney;
  private JTextField jtfMoney , jtfAttempts , jtfBetAmt;
  private JLabel     jlblJackpot, jlblBetAmt, jlblJackpotSys, jlblImages1,jlblImages2,
  					 jlblImages3, jlblMoney,jlblAttempts, jlblLotto1, jlblLotto2, jlblTp;
      
  
  public static void main (String args[]){
  
	Jackpot f= new Jackpot();
	f.setVisible(true);
	f.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
  }
  
  public Jackpot(){
  	setSize(500,500);
  	setTitle("Jackpot System");
  	getContentPane().setLayout(new GridLayout (4,1));// set layout
  	getContentPane().setBackground(Color.white);// set colour
  
		
		/***jackpot system***/
		jpJackpotSys = new JPanel();
		//jlblJackpotSys.setFont(new Font("Serif", Font.ITALIC, 12));

		Font bigFont = new Font ("ComicSans", Font.ITALIC, 24);
		jpJackpotSys.setBackground (Color.orange);
		jlblJackpotSys  = new JLabel("Jackpot System");
		jlblJackpotSys.setFont(bigFont);
	    jlblLotto1 = new JLabel("Lotto1");
		jlblLotto2 = new JLabel("Lotto2");
		
		
		jpJackpotSys.add(jlblLotto2, BorderLayout.SOUTH );
		getContentPane().add( jpJackpotSys );
		
		jpJackpotSys.add (jlblJackpotSys, BorderLayout.CENTER);
		getContentPane().add( jpJackpotSys );
		

		jpJackpotSys.add(jlblLotto1, BorderLayout.EAST );
		getContentPane().add( jpJackpotSys );
		
		
     	/***jpImages***/
     	
     	jpMiddle= new JPanel();
    	jpMiddle.setLayout(new BorderLayout());
    	jpMiddle.setBackground (Color.red);
     	
		jpImages = new JPanel();
		jpImages.setLayout(new GridLayout(1,3));
		jpMiddle.setBackground (Color.orange);
		
		jlblImages1 = new JLabel( "Pic 1");
		jlblImages2 = new JLabel( "Pic 2");
		jlblImages3 = new JLabel( "Pic 3");
		
		jpImages.add(jlblImages1);
		getContentPane().add( jpMiddle );

		jpImages.add(jlblImages2 );
		getContentPane().add( jpMiddle );
		
		jpImages.add(jlblImages3);
		getContentPane().add(  jpMiddle );
		
		jpMiddle.add(jpImages, BorderLayout.CENTER);
		
		jpMoney= new JPanel();
		jpMoney.setLayout(new FlowLayout());
		jlblMoney= new JLabel("Money Available:");
		jtfMoney= new JTextField(4);
		jlblAttempts= new JLabel("No. of attempts:");
		jtfAttempts= new JTextField(4);
		
		jpMoney.add(jlblMoney);
		jpMoney.add(jtfMoney);
		jpMoney.add(jlblAttempts);
		jpMoney.add(jtfAttempts);
		jpMiddle.add(jpMoney,BorderLayout.NORTH);
		getContentPane().add(jpMiddle);
		
		
		/***bet amt***/
		jpBetAmt = new JPanel();
		jpBetAmt.setLayout(new FlowLayout());
		
	    jlblBetAmt = new JLabel("Bet Amount ($0.50 to $1.00):");
		jtfBetAmt = new JTextField(4);
		
		jpBetAmt.add(jlblBetAmt);
		jpBetAmt.add(jtfBetAmt);
		
		jpButtons = new JPanel();
		jbtnSpin = new JButton ("Spin");
		jbtnReset = new JButton ("Reset");
      	
        jpButtons.add(jbtnSpin);
        jpButtons.add(jbtnReset);
        
        JPanel pBelowPic = new JPanel();
        pBelowPic.setLayout(new BorderLayout());
        pBelowPic.add(jpBetAmt, BorderLayout.NORTH);
        pBelowPic.add(jpButtons, BorderLayout.CENTER);
        
        getContentPane().add(pBelowPic);
        
       /***big pic***/
       jpTp= new JPanel();
       jlblTp = new JLabel("TP");
       jpTp.setLayout(new BorderLayout());
       jpTp.add(jlblTp, BorderLayout.SOUTH);
       getContentPane().add(jpTp);
       
        }
}

---

### Post by zsimplicityz on 2007-01-20
need help !!

---

### Post by Tomosaur on 2007-01-20
Just read Java Swing API, it'll tell you all you need to know.

I would advise splitting your code up into more 'sensible' objects too. It just seems like you have lots of different things going on there, it would be better to isolate them so when you run into problems (which you probably will) it's easier to fix.

---

### Post by daneel_olivaw on 2007-01-20
if you're at university i suggest you take a look at some design patterns usage examples, like MVC -- there are examples somewhere on java.sun.com about how swing is designed around some fondamental patterns you can use.

more roughly,  you'll like to add functionalities to your buttons, like telling what should happen when they get pressed

look at APIs (i.e. javadocs) expecially for the JButton class for how to do that

this is a tutorial about buttons: [http://java.sun.com/docs/books/tutorial/uiswing/components/button.html](http://java.sun.com/docs/books/tutorial/uiswing/components/button.html)

cheers

---

