---
title: "Java: Can classes be executed in Applets?"
date: 2011-10-07
forum: Programming Talk
---

### Post by fallenshadow on 2011-10-07
Probably a silly question but this does not seem to work for an applet:

> 
className newClassName = new className();
                  newClassName.init();


Any ideas? or are classes not possible to execute with an applet?

---

### Post by PaulM1985 on 2011-10-07
That should work fine.  Have you got any example code where something is not working?

---

### Post by fallenshadow on 2011-10-08
[PHP]Panel aPanel = new Panel();
    

public void actionPerformed(ActionEvent evt) 
         {
 
              if (evt.getSource() == okButton) 
              {
                  
                  aPanel.init();
              }

         }    [/PHP]

It looks like it should work and Netbeans doesn't underline anything as an error.

---

### Post by simeon87 on 2011-10-08
Did you get an error or so? This should work because if it would not work, you would not be able to do much with Java in applets :)

---

### Post by fallenshadow on 2011-10-08
I have no errors but when I press the button nothing happens.

Its supposed to open another applet window in a separate class.. this is possible, right?

---

### Post by PaulM1985 on 2011-10-09
OK, so you should get another window to appear.  What does your init function do?  Is there any code that adds the panel to the top level component so that it can be visible?

Paul

---

### Post by HotCupOfJava on 2011-10-09
I would add a System.out.println("sometext") to the aPanel.init() method to ensure that the method is indeed being called. If it is, you probably have an issue with the visibility of the applet container. Merely instantiating and initializing a container is not enough to show a new window in most cases.

---

### Post by fallenshadow on 2011-10-10
Ok I got it fixed. Instead of having my second class extend an Applet I made it extend a frame instead.

Now my second class (gui) pops up in a separate window. However my button to close the popup window ends up closing my Applet too. I am currently using a System.exit(0); call to close it.

Is there a way to just close this popup window and not my whole application?

---

### Post by PaulM1985 on 2011-10-10
System.exit(0) closes the application.  That is a standard call to close Java applications.  If you want the frame to go away, why not set it to be invisible?  myFrame.setVisible(false);

Paul

---

### Post by ofnuts on 2011-10-10
> **fallenshadow said:**
> Ok I got it fixed. Instead of having my second class extend an Applet I made it extend a frame instead.

Now my second class (gui) pops up in a separate window. However my button to close the popup window ends up closing my Applet too. I am currently using a System.exit(0); call to close it.

Is there a way to just close this popup window and not my whole application?
[http://download.oracle.com/javase/6/docs/api/java/awt/Window.html#dispose%28%29](http://download.oracle.com/javase/6/docs/api/java/awt/Window.html#dispose%28%29)

---

