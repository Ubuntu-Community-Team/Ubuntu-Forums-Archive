---
title: "[Java] Frame contents disappear"
date: 2009-08-08
forum: Programming Talk
---

### Post by Fixel on 2009-08-08
I fixed my earlier problem, and thus I have a new inquiry! How do I bind the enter key to a JButton using netbeans? (in this case JButton1) 

Old problem with source code available [here]("http://pastebin.org/7421"):

```
Hey guys, I'm making a Japanese learning program for school. I'm having some trouble with an excercise I made. Basically there is a top menu for the excercise where you choose practice or test.

You choose test and complete the excercise. When the excercise is completed a JFrame shows up to congratulate you on your epic conquest. Or atleast it's supposed to. Instead the frame shows up, but the contents are missing i.e. the frame is transparent!

I tried creating different frames from the excercise frame source code. But it always (except when I call a JOptionPane.showMessageDialog) shows the frame but not the contents! Weirdest thing ever.

The basic goal of the excercise's to guess the phonetic sound of the japanese characters that appear in jLabel1. (For debugging's sake it's limited to 3 characters)

The source for the excercise is available [here.]("http://pastebin.org/7421") I'm using the Netbeans IDE (since I don't feel like building every frame from scratch).

The check buttons event starts from line 132, and you can see on line 152 how I dispose of the excercise frame and create the congratulatory frame! :)

(&#12354;=a&#12288;&#12356;=i&#12288;&#12358;=u)
```

---

### Post by Fixel on 2009-08-08
Oh yeah! Managed to fix it myself! :D

I moved the while-loop outside of the if(answer == true) clause! And but an exterior if(allanswered != true) around it! :D Yay, this makes me so happy! :D

Moving on: How do I bind the jButton1 to the Enter/Return key?

EDIT: Check first post, this post is redundant.

---

### Post by HotCupOfJava on 2009-08-08
Add a KeyListener to the Frame. Check to make sure it was the "Enter" key that was pressed, then call the JButton's actionPerformed method. Netbeans auto-generates a such a method that the item's anonymous ActionListener calls (I'm sure you've already noticed this).

---

### Post by Fixel on 2009-08-09
Thx HotCupOfJava!

I played around with the IDE for about half an hour trying to get it to work. Eventually I added a actionPerformed listener to the jTextField and now when I press enter it calls "jButton1.doClick();" which works wickedly well!

---- Thread Solved ----

p.s. gief mark thread as solved widget!

---

