---
title: "need even more help with java! :("
date: 2008-06-30
forum: Programming Talk
---

### Post by rtoot3 on 2008-06-30
ok. i have successfully compiled a java application, but what about applets? i found an applet tutorial and it showed me this

```
/*
By Bavo Bruylandt (Http://www.realapplets.com")

*/

// and now The inevidable "Hello World" example :)

// tell the compiler where to find the methods you will use.
// required when you create an applet
import java.applet.*;
// required to paint on screen
import java.awt.*;
 

// the start of an applet - HelloWorld will be the executable class
// Extends applet means that you will build the code on the standard Applet class
public class HelloWorld extends Applet
{

// The method that will be automatically called  when the applet is started
     public void init()
     {
 // It is required but does not need anything.
     }
 

// This method gets called when the applet is terminated
// That's when the user goes to another page or exits the browser.
     public void stop()
     {
     // no actions needed here now.
     }
 

// The standard method that you have to use to paint things on screen
// This overrides the empty Applet method, you can't called it "display" for example.

     public void paint(Graphics g)
     {
 //method to draw text on screen
 // String first, then x and y coordinate.
      g.drawString("Hey hey hey",20,20);
      g.drawString("Hellooow World",20,40);

     }

}
 

// That's it. Next is drawing special shapes on screen and using fonts.
// Go to DrawExample.java.
```
i typed all that and saved as HelloWorld.java.
and then did the javac thing and it didnt work. and im also at my sisters house and her computor is windows, so it doesnt even tell me what happened!:confused: 
please help

---

### Post by SyL on 2008-06-30
> **rtoot3 said:**
> ok. i have successfully compiled a java application, but what about applets? i found an applet tutorial and it showed me this

i typed all that and saved as HelloWorld.java.
and then did the javac thing and it didnt work. and im also at my sisters house and her computor is windows, so it doesnt even tell me what happened!:confused: 
please help


what is the output of javac?

---

### Post by CptPicard on 2008-06-30
Applets are not standalone... you either need to embed them in a HTML document and view them using a browser, or use Sun's appletviewer utility.

---

### Post by rtoot3 on 2008-06-30
nevermind, i fixed it,
sorry:oops:

---

### Post by rtoot3 on 2008-06-30
well actually i fixed the file and took your advice on embeding it in html

---

