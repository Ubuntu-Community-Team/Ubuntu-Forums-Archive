---
title: "java problem with getSource()"
date: 2006-11-30
forum: Programming Talk
---

### Post by pontifex3 on 2006-11-30
hi, im learning to program in java and am trying to make a program that will just change a circles size, here's my code:
import java.awt.*;
import java.applet.*;
import java.awt.event.*;

```
public class circulos extends Applet implements ActionListener {

    private Button grande, chico;
    private int tamano=50;

    public void init() {
	grande = new Button("Agrandar");
	chico = new Button("Achicar");
	add(grande);
	add(chico);
	grande.addActionListener(this);
	chico.addActionListener(this);
    }

    public void paint(Graphics g) {
	g.drawOval(50, 50, tamano, tamano);
    }

    public void actionPerformed(ActionEvent event) {
	if (event.getSouce() == grande)
	    tamano++;
	else
	    tamano--;
	repaint();
    }
}
```
and when i try to compile it gives me
```
jjara@geburah:~/programacion/java/new$ javac circulos.java 
circulos.java:19: cannot find symbol
symbol  : method getSouce()
location: class java.awt.event.ActionEvent
        if (event.getSouce() == grande)
                 ^
1 error
jjara@geburah:~/programacion/java/new$ 

```
after this i got a similar program from the web, and i modified it to draw circles, and this one works perfectly, i've compared every single line and they're all identical, only the variable names change, is this some sort of bug or why wont the other compile? any help appreciated, thanks in advance
, here's the code that does compile
```
import java.awt.*;
import java.applet.*;
import java.awt.event.*;

public class boton extends Applet implements ActionListener {

    private Button evaluador,evaluador2;
    private int veces=50;

    public void init() {
	evaluador = new Button("aumentar");
	evaluador2= new Button("reducir");
	add(evaluador);
	add(evaluador2);
	evaluador.addActionListener(this);
	evaluador2.addActionListener(this);
    }

    public void paint(Graphics g){
	g.drawOval(50,50,veces,veces);
    }

    public void actionPerformed(ActionEvent event) {
	if (event.getSource() == evaluador)
	    veces++;
	else
	    veces--;
	repaint();
    }
}
```

---

### Post by hod139 on 2006-11-30
It's getSou**r**ce() not getSouce(), you are missing the r.

---

