---
title: "Java KeyListener not working"
date: 2011-05-10
forum: Programming Talk
---

### Post by xrsox on 2011-05-10
Hi,

Im new here... I'm programming a Game in Java but I don't know why the KeyListener is not working correctly... Here are the 2 classes that are involved with the listener.

```
import javax.swing.*;
import javax.swing.border.*;
import javax.accessibility.*;
import java.awt.*;
import java.awt.event.*;
import java.util.*;
import java.io.*;
import java.net.*;
import java.awt.event.KeyEvent;
import java.awt.event.KeyListener;

public class Tablero extends JPanel
{
	public JFrame ventana;
	public Casilla tablero[][];
	private Personaje pers;
	
	
	public Tablero (JFrame v)
	{
		ventana = v;
		leeFichero();
		
		
		System.out.println ( "Termina de leer el fichero!" );
		
		JPanel panel = new JPanel();
		panel.setLayout( new GridBagLayout() );
		GridBagConstraints propsLayout = new GridBagConstraints();
		propsLayout.gridx = 0;
		propsLayout.gridy = 0;
		propsLayout.gridwidth = 1;
		propsLayout.gridheight = 1;
		propsLayout.fill = GridBagConstraints.BOTH;
		propsLayout.weightx = 1.0;
		propsLayout.weighty = 1.0;
		
		//Coloco el personaje en el tablero
		
		pers = new Personaje ( "./Imagenes/personaje.png",40,40 );
		
		panel.add ( pers, propsLayout );
		
		//Pinto el tablero
		
		for ( int i = 0; i < tablero.length; i++ )
		{
			for ( int j = 0; j < tablero[0].length; j++ )
			{
				panel.add( tablero[i][j], propsLayout );
			}
		}
		
		System.out.println ( "Escenario pintado!" );
		
		v.setContentPane(panel);
		
		v.addKeyListener ( new Listener(this) );
		
		v.setSize ( 617, 640 );
		v.setLocationRelativeTo ( null );
		v.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		v.setVisible(true);
		
	}
	
	@Override
	public void paintComponent ( Graphics g )
	{
		for ( int i = 0; i < tablero.length; i++ )
		{
			for ( int j = 0; j < tablero[0].length; j++ )
			{
				tablero[i][j].update(g);
			}
		}
		pers.update(g);
	}
	
	public void muevePersonajeIzquierda()
	{
		//Miro cual es la posición actual del personaje
		int posXact = pers.getX();
		int posYact = pers.getY();
		
		System.out.println (" Entra al muevePersonajeIzquierda() ");
		
		if ( !tablero[posYact][posXact-1].Llena() )
		{
			pers.mueveIzquierda();
			ventana.repaint();
		}
	}
	
	public void muevePersonajeDerecha()
	{
		int posXact = pers.getX();
		int posYact = pers.getY();
		
		if ( !tablero[posYact][posXact+1].Llena() )
		{
			pers.mueveDerecha();
			ventana.repaint();
		}
	}
	
	public void muevePersonajeArriba()
	{
		int posXact = pers.getX();
		int posYact = pers.getY();
		
		if ( !tablero[posYact-1][posXact].Llena() )
		{
			pers.mueveArriba();
			ventana.repaint();
		}
	}
	
	public void muevePersonajeAbajo()
	{
		int posXact = pers.getX();
		int posYact = pers.getY();
		
		if ( !tablero[posYact+1][posXact].Llena() )
		{
			pers.mueveAbajo();
			ventana.repaint();
		}
	}
	
	public void leeFichero()
	{
		String f = "./Ficheros/Escenario.txt";
		
		try
		{
			BufferedReader br = new BufferedReader ( new FileReader(f) );
			String cadena = br.readLine();
			
			//Leo la primera linea donde estan el numero de filas y columnas y
			//el tamaño de las casillas
			int cuantasX = (new Integer ((cadena.split(","))[0])).intValue();
			int cuantasY = (new Integer ((cadena.split(","))[1])).intValue();
			int medidaCasilla = (new Integer(((cadena.substring(1)).split(","))[2])).intValue();
			
			
			tablero = new Casilla[cuantasX][cuantasY];
			
			for ( int i = 0; i < cuantasX; i++ )
			{
				cadena = br.readLine();
				
				
				String cas[] = cadena.split(" ");
				
				
				for ( int j = 0; j < cuantasY; j++ )
				{
					if ( j < cas.length )
					{
						try
						{
							//System.out.println ( "Integer.parseInt( cas[j]: "+Integer.parseInt( cas[j] ) );
							
							tablero[i][j] = new Casilla( Integer.parseInt( cas[j] ), j*medidaCasilla, i*medidaCasilla );
							
							//System.out.println( "tablero[i][j]: "+tablero[i][j] );
							
							
						}catch (Exception e)
						{
							tablero[i][j] = new Casilla();
						}
					}
				}
			}
			
			br.close();
			
		}
		catch(Exception e)
		{
			System.out.println("Error al leer el fichero:" +e.getMessage() );
		}
	}
	
	
	
}

import java.awt.event.*;


public class Listener implements KeyListener
{
	Tablero t;
	
	public Listener ( Tablero tab )
	{
		t = tab;
	}
	
	public void keyPressed ( KeyEvent e )
	{
		if ( e.getKeyCode() == KeyEvent.VK_LEFT )
		{
			t.muevePersonajeIzquierda();
		}
		
		if ( e.getKeyCode() == KeyEvent.VK_RIGHT )
		{
			t.muevePersonajeDerecha();
		}
		
		if ( e.getKeyCode() == KeyEvent.VK_UP )
		{
			t.muevePersonajeArriba();
		}
		
		if ( e.getKeyCode() == KeyEvent.VK_DOWN )
		{
			t.muevePersonajeAbajo();
		}
	}
	
	public void keyReleased ( KeyEvent e ){}
	
	public void keyTyped ( KeyEvent e ){}
	
}
```

Any ideas?? I need help :_(

---

### Post by stchman on 2011-05-10
To OP:

Please wrap your code using the CODE tags.  It makes it FAR easier to read.

Also please include your import statements.

---

### Post by xrsox on 2011-05-10
> **stchman said:**
> To OP:

Please wrap your code using the CODE tags.  It makes it FAR easier to read.

Also please include your import statements.

Did it :)
Sorry... I'm new here.. thanks

---

### Post by PaulM1985 on 2011-05-10
It is possible that your panel does not have focus.  If you call requestFocus() your panel will have the focus and then should receive key pressed events.

Paul

---

### Post by xrsox on 2011-05-10
Hi Paul,

just called RequestFocus() in the Tablero class but it did nothing =(... any other ideas??

Thanks for your answer

Ricardo

---

### Post by trozamon on 2011-05-10
Instead of calling ventana.repaint() in your muevePersonaje methods, Oracle recommends calling validate() because it repaints as well as laying out components.

Besides that, I would put System.out.println("keyPressed() has been activated to send the character left.") in the keyPressed method of your listener to make sure that it's the JPanel and not the listener's fault.

---

### Post by xrsox on 2011-05-11
Just tried the validate() instead of repaint but it didn't work. I think the problem is in the JPanel because I did the System.out.println("Keypressed"); in the Listener class but it didn't print anything... any other ideas?

Thank you trozamon

---

### Post by xrsox on 2011-05-11
Just made a System.out.println (); in the constructor of the class Listener and it did print

---

### Post by PaulM1985 on 2011-05-11
You are adding a key listener to the frame. Shouldn't you be adding this to the panel?

Paul

---

### Post by xrsox on 2011-05-11
Just solved the problem with some help I gotta say :P...  You were right Paul... I needed requestFocus(). Here is the solution...

```
import javax.swing.*;
import javax.swing.border.*;
import javax.accessibility.*;

import java.awt.*;
import java.awt.event.*;

import java.util.*;
import java.io.*;

import java.net.*;
import java.awt.event.KeyEvent;
import java.awt.event.KeyListener;


public class Tablero extends JPanel
{
	public JFrame ventana;
	public Casilla tablero[][];
	private Personaje pers;
	
	
	public Tablero (JFrame v)
	{
		ventana = v;
		leeFichero();
		
		
		System.out.println ( "Termina de leer el fichero!" );
		
		JPanel panel = new JPanel();
		panel.setLayout( new GridBagLayout() );
		GridBagConstraints propsLayout = new GridBagConstraints();
		propsLayout.gridx = 0;
		propsLayout.gridy = 0;
		propsLayout.gridwidth = 1;
		propsLayout.gridheight = 1;
		propsLayout.fill = GridBagConstraints.BOTH;
		propsLayout.weightx = 1.0;
		propsLayout.weighty = 1.0;
		
		//Coloco el personaje en el tablero
		
		pers = new Personaje ( "./Imagenes/personaje.png", 40, 40 );
		
		panel.add ( pers, propsLayout );
		
		//Pinto el tablero
		
		for ( int i = 0; i < tablero.length; i++ )
		{
			for ( int j = 0; j < tablero[0].length; j++ )
			{
				panel.add( tablero[i][j], propsLayout );
			}
		}
		
		System.out.println ( "Escenario pintado!" );
		
		v.setContentPane(panel);
		
		
		v.setSize ( 617, 640 );
		v.setLocationRelativeTo ( null );
		v.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		v.setVisible(true);
		
		[B][COLOR="Red"]v.addKeyListener ( new Listener(this) );
		v.requestFocus();[/COLOR][/B]
	}
	
	@Override
	public void paintComponent ( Graphics g )
	{
		for ( int i = 0; i < tablero.length; i++ )
		{
			for ( int j = 0; j < tablero[0].length; j++ )
			{
				tablero[i][j].update(g);
			}
		}
		pers.update(g);
	}
	
	public void muevePersonajeIzquierda()
	{
		//Miro cual es la posición actual del personaje
		int posXact = pers.getX();
		int posYact = pers.getY();
		
		//System.out.println (" Entra al muevePersonajeIzquierda() ");
		System.out.println (tablero[posYact][posXact-1]	);
		if ( !tablero[posYact][posXact-1].Llena() )
		{
			pers.mueveIzquierda();
			ventana.repaint();
		}
	}
	
	public void muevePersonajeDerecha()
	{
		int posXact = pers.getX();
		int posYact = pers.getY();
		
		//System.out.println (" Entra al muevePersonajeDerecha() ");
		System.out.println (tablero[posYact][posXact+1]);
		if ( !tablero[posYact][posXact+1].Llena() )
		{
			pers.mueveDerecha();
			ventana.repaint();
		}
	}
	
	public void muevePersonajeArriba()
	{
		int posXact = pers.getX();
		int posYact = pers.getY();
		
		//System.out.println (" Entra al muevePersonajeArriba() ");
		System.out.println (tablero[posYact-1][posXact]);
		if ( !tablero[posYact-1][posXact].Llena() )
		{
			pers.mueveArriba();
			ventana.repaint();
		}
	}
	
	public void muevePersonajeAbajo()
	{
		int posXact = pers.getX();
		int posYact = pers.getY();
		
		//System.out.println (" Entra al muevePersonajeAbajo() ");
		System.out.println (tablero[posYact+1][posXact]);
		if ( !tablero[posYact+1][posXact].Llena() )
		{
			pers.mueveAbajo();
			ventana.repaint();
		}
	}
	
	public void leeFichero()
	{
		String f = "./Ficheros/Escenario.txt";
		
		try
		{
			BufferedReader br = new BufferedReader ( new FileReader(f) );
			String cadena = br.readLine();
			
			//Leo la primera linea donde estan el numero de filas y columnas y
			//el tamaño de las casillas
			int cuantasX = (new Integer ((cadena.split(","))[0])).intValue();
			int cuantasY = (new Integer ((cadena.split(","))[1])).intValue();
			int medidaCasilla = (new Integer(((cadena.substring(1)).split(","))[2])).intValue();
			
			
			tablero = new Casilla[cuantasX][cuantasY];
			
			for ( int i = 0; i < cuantasX; i++ )
			{
				cadena = br.readLine();
				
				String cas[] = cadena.split(" ");
				
				
				for ( int j = 0; j < cuantasY; j++ )
				{
					if ( j < cas.length )
					{
						try
						{
							//System.out.println ( "Integer.parseInt( cas[j]: "+Integer.parseInt( cas[j] ) );
							
							tablero[i][j] = new Casilla( Integer.parseInt( cas[j] ), j*medidaCasilla, i*medidaCasilla );
							
							//System.out.println( "tablero[i][j]: "+tablero[i][j] );
							
							
						}catch (Exception e)
						{
							tablero[i][j] = new Casilla(j*medidaCasilla, i*medidaCasilla);
						}
					}
				}
			}
			
			br.close();
			
		}
		catch(Exception e)
		{
			System.out.println("Error al leer el fichero:" +e.getMessage() );
		}
	}
	
	
	
}

import java.awt.event.*;


public class Listener implements KeyListener
{
	Tablero t;
	
	public Listener ( Tablero tab )
	{
		t = tab;
	}
	
	public void keyPressed ( KeyEvent e )
	{
		//System.out.println(e.getKeyCode());
		
		if ( e.getKeyCode() == KeyEvent.VK_LEFT )
		{
			t.muevePersonajeIzquierda();
		}
		
		if ( e.getKeyCode() == KeyEvent.VK_RIGHT )
		{
			t.muevePersonajeDerecha();
		}
		
		if ( e.getKeyCode() == KeyEvent.VK_UP )
		{
			t.muevePersonajeArriba();
		}
		
		if ( e.getKeyCode() == KeyEvent.VK_DOWN )
		{
			t.muevePersonajeAbajo();
		}
		
	}
	
	public void keyReleased ( KeyEvent e ){}
	
	public void keyTyped ( KeyEvent e ){}
	
}

```

Thank you all for your help :P

---

### Post by PaulM1985 on 2011-05-11
It would also have worked if you had added the key listener to the panel, so your call would have been:
```

addKeyListener ( new Listener(this) );
requestFocus();

```
instead of
```

v.addKeyListener ( new Listener(this) );
v.requestFocus();

```

In your case you are adding the key listener to the window instead of the panel. I am glad it is working for you now anyway.

Paul

---

