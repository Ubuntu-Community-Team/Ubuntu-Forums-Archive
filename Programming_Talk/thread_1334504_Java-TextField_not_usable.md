---
title: "Java-TextField not usable"
date: 2009-11-22
forum: Programming Talk
---

### Post by nzuri on 2009-11-22
hi.
i have problems with ubuntu, java and textfield/area.
when i write a simple applet with this code:
```
import java.awt.*;

public class applet extends java.applet.Applet {

     TextArea ta;
     TextField tf;

     @Override
     public void init () {
      setLayout(new BorderLayout());

      Panel p = new Panel (new BorderLayout());
      add(p,BorderLayout.NORTH);

      //Textarea bsp.
      ta = new TextArea("Dies ist ein Textbereich, und den sollte man nurtzen",10,25);
      p.add(ta);

      //Textfiel bsp.
      tf = new TextField(15);
      tf.setText("Test");

      add(tf,BorderLayout.SOUTH);

     }

     @Override
     public void start () {
        
     }

     @Override
     public void stop () {

     }

     @Override
     public void destroy () {

     }

}

```and then run it with appletviewer i get the following errors:

```

Warning: Cannot convert string "-b&h-luxi sans-medium-r-normal--*-140-*-*-p-*-iso8859-1" to type FontStruct
Warning: Cannot convert string "-arphic-ar pl shanheisun uni-medium-r-normal--*-*-*-*-p-*-iso10646-1" to type FontStruct
Warning: Cannot convert string "-arphic-ar pl uming uni-medium-r-normal--*-*-*-*-p-*-iso10646-1" to type FontStruct
Warning: Cannot convert string "-kochi-gothic-medium-r-normal--*-140-*-*-c-*-jisx0208.1983-0" to type FontStruct
Warning: Cannot convert string "-sazanami-gothic-medium-r-normal--*-140-*-*-c-*-jisx0208.1983-0" to type FontStruct
Warning: Cannot convert string "-baekmuk-gulim-medium-r-normal--*-140-*-*-c-*-ksc5601.1987-0" to type FontStruct
Warning: 
    Name: textfield
    Class: XmTextField
    Character 'T' not supported in font.  Discarded.
.
.
.
and so on

```the applet looks like this: [http://img684.imageshack.us/img684/3987/bildschirmfotozg.png](http://img684.imageshack.us/img684/3987/bildschirmfotozg.png)
and it's not possible to write in the textfield/area

every applet i run has the "Convert-Errors" but i never had further problems with them.

what can be the reason for not supporting simple characters?

it's really annoying, because i have so many problems with java and  ubuntu... i hope this time it's my  fault :).
or anybody knows a solution?

greez nzuri

p.s.: 
:/$ java -version
java version "1.6.0_15"
Java(TM) SE Runtime Environment (build 1.6.0_15-b03)
Java HotSpot(TM) Server VM (build 14.1-b02, mixed mode)

---

