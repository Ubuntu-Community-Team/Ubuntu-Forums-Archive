---
title: "help with java applet"
date: 2007-01-07
forum: Programming Talk
---

### Post by pontifex3 on 2007-01-07
hi, im currently making a java applet for my computer class; it consists of a simple board in which players place pieces, the first one to complete a row of five pieces wins, the applet is uses the class "piece" which consists of x and y coordenates and a boolean value for the turn, when drawing the pieces i simply used the method drawOval changing the color, but now im trying to make it load images to make the board pieces look nicer, the problem is that when i compile it seems the commands im using (getDocumentBase(); for locating where the image is stored, getImage, for loading it, and g.drawImage, for showing it, only work when the class extends an applet, so i get theese errors:

```

jjara@geburah:~/programacion/java/nuevo$ javac five2.java 
five2.java:253: cannot find symbol
symbol  : method getDocumentBase()
location: class Piece
        where=getDocumentBase();
              ^
five2.java:257: cannot find symbol
symbol  : variable NULL
location: class Piece
        this.img=NULL;
                 ^
five2.java:259: cannot find symbol
symbol  : method getImage(java.net.URL,java.lang.String)
location: class Piece
            this.img=getImage(where, "1.jpg");
                     ^
five2.java:261: cannot find symbol
symbol  : method getImage(java.net.URL,java.lang.String)
location: class Piece
            this.img=getImage(where, "2.jpg");
                     ^
five2.java:264: cannot find symbol
symbol  : method drawImage(java.awt.Image,int,int,Piece)
location: class java.awt.Graphics
        g.drawImage(img, x, y, this);
         ^
5 errors
jjara@geburah:~/programacion/java/nuevo$ 

```

the piece class looks like this

```

class Piece{
    Image img;
    private int x,y;
    private boolean turno;
    private URL where;
    public Piece(int x, int y, boolean turn){
	where=getDocumentBase();
	this.x=x;
	this.y=y;
	turno=turn;
	this.img=NULL;
	if(turn)
	    this.img=getImage(where, "1.jpg");
	else
	    this.img=getImage(where, "2.jpg");
    }
    public void mostrar (Graphics g){
	g.drawImage(img, x, y, this);
    }
}

```
java.awt.*;, java.awt.event.*;, java.applet.*; and java.net.*; are imported, im not sure if i have to implement something to class to make this work. the full code is here
```

import java.awt.*;
import java.awt.event.*;
import java.applet.*;
import java.net.*;

public class five2 extends Applet 
    implements MouseListener, MouseMotionListener {
    private int coordx=0, coordy=0, i=0,j;
    private boolean turn=true, terminado=false;  //TRUE ES AZULES!(comienzan)
    private Piece[] ficha;
    private int[][] tabla;
    //URL where;//PASSED
    //************************INIT****************************
    //se crea el arreglo de 100 fichas (maximo posible) y se agregan los listeners
    //public static void main( String args[]){
    //Frame f=new Frame("Five");
    //five juego=new five();
    //juego.init();
    //f.add("Center",juego);
    //f.pack();
    //f.show();
    //}
    public void init() {
	int a,b;
	//where=getDocumentBase();//PASSED
	ficha=new Piece[100];
	tabla=new int[10][10];  //1 significa AZUL y 2 ROSAAAAA
	this.addMouseListener(this);
        this.addMouseMotionListener(this);
	for(a=0; a<=9; a++){
	    for(b=0; b<=9; b++){
		tabla[a][b]=0;
	    }
	}
    }
    //TOMA LAS COORDENADAS X, Y CREA UNA NUEVA FICHA CON SUBINDICE I Y LO AUMENTA
    //MUESTRA DE QUIEN ES TURNO
    public void mousePressed(MouseEvent ev) {
	if (terminado){
	}else
	    {
		int newx, newy;
		coordx=ev.getX();
		coordy=ev.getY();
		//revisa que las coordenadas esten libres! ^.^
		if (tabla[((coordx-(coordx%30))/30)][((coordy-(coordy%30))/30)]!=0)
		    System.out.println("Seleccion ilegal, el espacio ya ha sido utilizado");
		else{
		    //y si no pues venga, crea el objeto tipo Piece, e indica en la matriz que el lugar esta ocupado
		    newx=((coordx-(coordx%30)));
		    newy=((coordy-(coordy%30)));
		    ficha[i]=new Piece(newx,newy,turn);
		    i++;
		    if (turn) {
			tabla[newx/30][newy/30]=1;
			showStatus("Turno: Rosa");
			turn=false;
		    }
		    else{
			tabla[newx/30][newy/30]=2;
			showStatus("Turno: Azul");
			turn=true;
		    }
		    checarlineas();
		    repaint();
		}
	    }
    }
    //NADA IMPORTANTE
    public void mouseExited(MouseEvent event) {}
    public void mouseReleased(MouseEvent event) {}
    public void mouseClicked(MouseEvent event) {}
    public void mouseEntered(MouseEvent event) {}
    public void mouseDragged(MouseEvent ev) {}
    public void mouseMoved(MouseEvent event) {}
    /***********************************************************
     ***********************************************************
     ***********************************************************
     **************REVISANDO LAS LINEAAAAS**********************
     ***********************************************************
     ***********************************************************
     ***********************************************************/



    //REVISA SI HAY ALGUN GANADOR
    public void checarlineas(){
	int a,b,c,d,longitud=0;
	//LINEAS VERTICALES ÑACA ÑACA
	for (c=1; c<=2; c++){
	    for (a=0; a<10; a++){
		longitud=0;
		for (b=0; b<10; b++){
		    if (tabla[a][b]==c)
			longitud=longitud+1;
		    else
			longitud=0;
		    if (longitud==5){
			terminado();
			terminado=true;
		    }
		}
	    }
	}
	//CHECA LAS LINEAS HORIZONTALES!
	for (c=1; c<=2; c++){
	    for (a=0; a<10; a++){
		longitud=0;
		for (b=0; b<10; b++){
		    if (tabla[b][a]==c)
			longitud=longitud+1;
		    else
			longitud=0;
		    if (longitud==5){
			terminado();
			terminado=true;
		    }
		}
	    }
	}
	//VENGAAAAA funciona en lineas que su lado izquierdo es inferior al derecho
	//SOLO AGARRA LA MITAD!
	for (c=1; c<=2; c++){
	    for (a=0; a<10; a++) {
		longitud=0;
		for (b=0; b<=a; b++) {
		    if(tabla[a-b][b]==c)
			longitud=longitud+1;
		    else
			longitud=0;
		    if(longitud==5){
			terminado();
			terminado=true;
		    }
		}
	    }
	}
	//NO BUGGY XD
	//las otras las voy a hacer en dos partes, NO SE TE OLVIDEEEEEE
	//empiezas 4,4 3,3 2,2, bueno 9,9 8,8 7,7
	for (c=1; c<=2; c++){
	    for (a=0; a<10; a++){
		d=0;
		b=a;
		longitud=0;
		while(b<10){
		    if(tabla[d][b]==c)
			longitud=longitud+1;
		    else
			longitud=0;
		    if(longitud==5){
			terminado();
			terminado=true;
		    }
		    b++;
		    d++;
		}
	    }
	}
	for (c=1; c<=2; c++){
	    for (a=0; a<10; a++){
		d=0;
		b=a;
		longitud=0;
		while(b<10){
		    if(tabla[b][d]==c)
			longitud=longitud+1;
		    else
			longitud=0;
		    if(longitud==5){
			terminado();
			terminado=true;
		    }
		    b++;
		    d++;
		}
	    }
	}
    }
    /*********************************************
     *********************************************
     *********************************************
     *****************FIN!************************
     *********************************************
     *********************************************
     *********************************************/
    //DECLARA EL GANADOR!
    public void terminado(){
	if (turn)
	    System.out.println("ROSA HA GANADO!");
	else
	    System.out.println("AZUL HA GANADO!");
    }

    //PAINT MOSTRANDO EL TABLERO Y LAS FICHAS YA CREADAS!!
    public void paint(Graphics g){
	//g.drawImage(img, 50, 50, this);//**************!!!!!!!!
	if (terminado==true){
	    if(turn)
		g.drawString("ROSA HA GANADO!",100,150);
	    else
		g.drawString("AZUL HA GANADO!",100,150);
	} else {
	    int k;
	    tablero(g);
	    //	    status();
	    for (k=0; k<i; k++)
		ficha[k].mostrar(g);
	    //    if(ficha[k].turno)
	    //ficha[k].img=getImage(where, "1.jpg");
	    //else
	    //ficha[k].img=getImage(where, "2.jpg");
	}
    }


    public void tablero(Graphics g){
	int u,v=0;
	for(u=1; u<=10; u++){
	    g.drawLine(v,0,v,300);
	    v=v+30;
	}
	v=0;
	for (u=1; u<=10; u++){
	    g.drawLine(0,v,300,v);
	    v=v+30;
	}
    }


    public void status() {
	int a,b;
	System.out.println("");
	System.out.println("");
	System.out.println("");
	for (a=0; a<10; a++) {
	    for (b=0; b<10; b++) {
		System.out.print(" "+tabla[b][a]);
	    }
	    System.out.println("");
	}
    }
}


//LA CLASE QUE HACE LAS PIEZAS, Y TAMBIEN LAS IMPRIME
class Piece{
    Image img;
    private int x,y;
    private boolean turno;
    private URL where;
    public Piece(int x, int y, boolean turn){
	where=getDocumentBase();
	this.x=x;
	this.y=y;
	turno=turn;
	this.img=NULL;
	if(turn)
	    this.img=getImage(where, "1.jpg");
	else
	    this.img=getImage(where, "2.jpg");
    }
    public void mostrar (Graphics g){
	g.drawImage(img, x, y, this);
	//if (turno)
	//    g.setColor(Color.blue);
	//else
	//    g.setColor(Color.magenta);
	//g.fillOval(x,y,30,30);
    }
}

```

well, im not sure if i made myself clear :-k but any help is appreciated! thanks in advance

---

### Post by icyisamu on 2007-01-07
Some obvious errors I can pick out:

```
where=getDocumentBase();
```

The compiler is telling you that you don't have a method called getDocumentBase() in your Piece class.

```
this.img=NULL;
```

The compiler can't find NULL, because it should be null (small letters)

```
this.img=getImage(where, "1.jpg");
```

The compiler is trying to tell you that there isn't a getImage() method in your piece class.

```
g.drawImage(img, x, y, this);
```

Graphics object does not support such a method signature. You cannot directly draw a Piece.
Here is the API Documentation for Graphics object: [http://java.sun.com/j2se/1.4.2/docs/api/java/awt/Graphics.html](http://java.sun.com/j2se/1.4.2/docs/api/java/awt/Graphics.html)

---

