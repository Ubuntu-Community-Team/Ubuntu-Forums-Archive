---
title: "Java -- Making a mouse click and a key press do the same thing"
date: 2007-09-05
forum: Programming Talk
---

### Post by thomasaaron on 2007-09-05
Hi, guys.

Another java question, if you don't mind.

I'm writing a little Swing application, and I've run into an issue:

When ever a button is clicked, I need for a certain action to be performed. (I know how to do that.)
The button is now set as the default button. So, when I press enter, I need for a certain action to be performed. (And I know how to do that.)

This requires two separate action listeners. Is there a way for me to have both actions do the same thing without duplicating the code?

The code looks something like this:

```
 private void StopButtonMouseReleased(java.awt.event.MouseEvent evt) {
//Code to execute when button is clicked...
}


private void EnterButtonActionPerformed(java.awt.event.ActionEvent evt) {
//Duplicated code to execute when enter key is pressed...
}
```


How do I do the following:

```
 private void StopButtonMouseReleased(java.awt.event.MouseEvent evt) {
//Code to execute when button is clicked...
}


private void EnterButtonActionPerformed(java.awt.event.ActionEvent evt) {
StopButtonMouseReleased(); //Just calls the code already written.
}
```

Thanks for your help.

Best,
Tom

---

### Post by Milk &amp; Toast &amp; Honey on 2007-09-05
Hi, it's pretty simple actually.

```

 private void StopButtonMouseReleased(java.awt.event.MouseEvent evt) {
    yourCommonFunction();
}


private void EnterButtonActionPerformed(java.awt.event.ActionEvent evt) {
    yourCommonFunction();
}

private void yourCommonFunction() {
// do something...
}

```

---

### Post by namesmike on 2007-09-05
yes i agree with that way of doing it, just create a method and use it for both events.

---

### Post by thomasaaron on 2007-09-05
Isn't it amazing how the simple answers elude us at 1AM?

Thanks, guys. That'll work.

Best,
Tom

---

### Post by gentoo5555 on 2010-10-07
Hi i Have a same kind of a problem.
to run a method i need to check 


if ( Right Click && Key "Delete" Press ){

   void method();
}

this what i have so far ====
```

class panel extends JPanel implements MouseListener , MouseMotionListener,KeyListener {
     
           A a1 = new A();
            
            public void mousePressed(MouseEvent e) {   
                    if("H" == keyperessed ){
                                 a1.myfunction(e)
                     }
              }
            public void keyPressed(KeyEvent e){    }

           
}

class A{
   
    void myfunction(MouseEvent e){}

}

```
Please Help.
thank you.

---

### Post by Zugzwang on 2010-10-07
> **gentoo5555 said:**
> 
if ( Right Click && Key "Delete" Press ){


What is this supposed to mean? Do you want an action to be performed if the right mouse button is pressed while the delete key is held down or if both the button and the key are pressed down at the same time?

---

### Post by VernonA on 2010-10-07
As mentioned, this problem is pretty easy, and is just a small variation on the previously supplied solution. You are making it too hard by creating helper classes when all you really need is a local variable to maintain state. Assuming you want to invoke a routine when the mouse is clicked whilst Del is pressed you would do:

```
class myPanel extends JPanel implements MouseListener, KeyListener 
{
    boolean delPressed = false;

    public void keyPressed(KeyEvent e)
    {
        if (e.getKeyCode() == VK_DELETE) delPressed = true;
    }

    public void keyReleased(KeyEvent e)
    {
        if (e.getKeyCode() == VK_DELETE) delPressed = false;
    }

    public void mousePressed(MouseEvent e) 
    {
        if(e.getButton()== BUTTON1 && delPressed)
        {
            myFunction();
        }
    }
    ...       
}
```
The more interesting case is when you DO want to know if the user pressed the key and the mouse at the same time. In this case don't use a boolean, use a couple of longs instead. In each one record the time when the key or mouse was depressed, and clear them to 0 when released. If (keyPressTime ^ mouseClickTime) is small, then they were pressed very close together. You would need to do some testing to find a good threshold for the delta, as pressing them at absolutely identical times would be almost impossible (ie you don't want to write ..if keyTime == mouseTime ...)

---

