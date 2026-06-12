---
title: "Java Script communicate with java applet"
date: 2010-05-24
forum: Programming Talk
---

### Post by esya on 2010-05-24
I am trying to netscape.javascript.* to supply communication between java script and java applet.

I am using eclipse and Ubuntu 9.10. 

When I run the code as a java applet I am getting this error 
java.lang.ClassCastException: sun.applet.AppletViewer cannot be cast to sun.applet.PluginAppletViewer

I searched a lot but I could not find any solution. :(

Is there any one who can help me? 

This is the code:

// Importations
 import java.awt.Graphics ;
 import java.awt.Event ;

 // LiveConnect... for JavaScript
 import netscape.javascript.JSObject ;
 

 public class tmin_JS extends java.applet.Applet {
     // Variables

     // Initialisation de l'applet
     public void init() {                       // Methode init()
     }

     // Dessiner l'applet
     public void paint(Graphics g) {             // Methode paint()
          g.drawString("Click here...", 5, 10) ;
     }
     
     // Mouse down
     public boolean mouseDown(Event e, int x, int y) {    
    try  {                    // create JSObject
        JSObject.getWindow (this).eval ("javascript:alert('tmin_JS click " + 
                " x=" + x + " y=" + y + "')") ; 
    }
    catch  (Exception  ex) {            // Error on create JSObject
        showStatus( "Error call javascript err=" + ex );
    }
    return true ;
     }
     
  }

---

### Post by esya on 2010-05-24
I chanced JRE system library java-6-sun-1.6.0.20 then I add nescape.jar as a external library then my error chanced.

Now I am getting this error:

java.lang.UnsatisfiedLinkError: netscape.javascript.JSObject.initClass()V

---

### Post by esya on 2010-05-24
New progress

I added plugin.jar as a referenced library and it has netscape.javascript.

Now It is not giving any error on the console but still it is not working.

In the applet window it gives this error:

error call javascript err=netscape.javascript.JSException

I hope someone can help me.

---

### Post by esya on 2010-05-26
I solved my problem.

I was trying to run applet by using eclipse applet running the I understood I need to 
use html file to see result with .class file.

Maybe it can help others.

---

### Post by soltanis on 2010-05-26
Good work on solving it by yourself. If you mark the thread as [SOLVED] (edit the thread title under the original post) then others will know to come here if they have the same problem. :)

---

