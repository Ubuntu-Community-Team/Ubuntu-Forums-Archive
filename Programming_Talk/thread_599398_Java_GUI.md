---
title: "Java GUI"
date: 2007-11-01
forum: Programming Talk
---

### Post by Geir102 on 2007-11-01
Hi I have been programming in java(eclipse) for a wile. but only text stuff never GUI. Now I need to make som gui stuff, and i have been trying to find som good info. But it looks like there are a 1000 ways to do it. Beens+++++ And some times they dont use the main

Can any one help my get started? And what is reguarly used

---

### Post by bukwirm on 2007-11-01
I would borrow a Java programming book from your local library and read the section dealing with GUIs.

---

### Post by dewey on 2007-11-01
In my AP Computer Science class, we were taught to design GUIs using Swing and BreezySwing, AWT was a topic for a week or two, but I found breezyswing to be much simpler.

I don't know if the general standard for java GUIs is swing, but if you're just looking to learn, and maybe create some small projects for yourself, I'd recommend it.

Here's a collection of powerpoints I found:
[http://infovis.cs.vt.edu/GUI/java/](http://infovis.cs.vt.edu/GUI/java/)

---

### Post by Geir102 on 2007-11-01
Tanks:-)

---

### Post by LaRoza on 2007-11-01
Many good resources are Free, I have collected a few on Swing in my wiki.

---

### Post by shafi on 2007-11-05
I have programed an english - persian dictionary but now i have problem with the database of this dictionary, mean when i enter the english word , i want that the meaning appear from **generic.xdb** , please help me..........
please sea the database file from here: 
[http://xfardic.sf.net/generic.xdb.bz2](http://xfardic.sf.net/generic.xdb.bz2)

this is my Gui code, plzzzzzzzzzzz help
> 
import java.awt.*; 
import java.awt.event.*; 
import javax.swing.*; 
import java.io.*;
import javax.xml.parsers.*;
import org.xml.sax.*;
import org.xml.sax.helpers.DefaultHandler; 
 
public class Dictionary extends JFrame implements ActionListener{ 
    String words[] = {"book","pen","ruler","fan","age","name","job","trouble group ///Dictionary"}; 
    JLabel label = new JLabel("Trouble Group Dictionary"); 
    JLabel lab = new JLabel("Enter the Word: "); 
    JComboBox jt = new JComboBox(words); 
    JTextArea area = new JTextArea(35,35); 
    JButton button = new JButton("Color"); 
    JButton go = new JButton("go"); 
    JButton about = new JButton("about us"); 
 
    Dictionary(){ 
        setTitle("TG Dictionary"); 
        Container c = getContentPane(); 
         
        c.setLayout(new FlowLayout()); 
        c.add(label); 
        //c.add(lab); 
        c.add(about); 
        c.add(jt); 
        //jt.getSelectedItem(); 
        c.add(go); 
        go.addActionListener(this); 
        go.setActionCommand("go"); 
        c.add(button); 
        button.addActionListener(this); 
        button.setActionCommand("color"); 
        c.add(area); 
        //c.add(new JColorChooser(Color Red)); 
         
        about.addActionListener(this); 
        about.setActionCommand("about us"); 
         
        label.setFont(new Font("Times New Roman",Font.BOLD,45)); 
        jt.setFont(new Font("Times New Roman",Font.ITALIC,20)); 
        area.setFont(new Font("Tahoma",Font.ITALIC,23)); 
        //t1.setFont(new Font("Arial",Font.BOLD,15)); 
        area.setEditable(false); 
        jt.setEditable(true); 
         
    } 
         
    public void actionPerformed(ActionEvent e,String[] args){ 
             
            if (e.getActionCommand().equals("color")) { 
            Color c=JColorChooser.showDialog(getContentPane(),"Choose a color",getContentPane().getBackground()); 
                getContentPane().setBackground(c); 
         
                } 
            else 
            if(e.getActionCommand().equals("about us")){ 
                JFrame f = new JFrame("about us"); 
                JLabel image = new JLabel( new ImageIcon("pic.gif") ); 
                //JLabel l = new JLabel("Programmed by TG Group!"); 
                //image.setHorizontalTextPosition(SwingConstants.CENTER ); 
                 
                f.setVisible(true); 
                f.add(image); 
                f.pack(); 
                f.show(); 
                f.setSize(500,500); 
                f.setLocation(250,250); 
                f.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE); 
                //area.append("\tMOst Welcom!\n\tThis Dictionary is Programmed by TG Group"); 
                 
            } 
                 
            else
             
            if(e.getActionCommand().equals("go")){ 
                
                //String url = "java ExampleSaxGetData generic.xdb word in shafi out";                
                try {
      MyDefaultHandlerImpl handler = new MyDefaultHandlerImpl();
      handler.args = args;
      SAXParser saxParser = SAXParserFactory.newInstance().newSAXParser();
      saxParser.parse( new File( args[0] ), handler );
      if( 0 < handler.sbResult.length() )
      {
        System.out.println( "Result string in child element '<"
                            + args[4] + ">':" );
        System.out.println( handler.sbResult );
        System.exit( 0 );
      }
      else
      {
        System.out.println( "No fitting element found." );
        System.exit( 2 );
      }
      area.append(url);
    } catch( Throwable t ) {
      t.printStackTrace();
      System.exit( 3 );
    }
                
                // here i have the problem .............
                
                
                /*try{
                FileReader fr = new FileReader("generic.xdb");
                BufferedReader bf = new BufferedReader(fr);
                while(bf.ready()){
                    if((jt.getSelectedItem().equals("book"))){
                    
                    String read = bf.readLine();
                    area.append(read);
                    }
                }
                area.append("Not Found !");
                }catch(Exception e1){
                    System.out.println(e1.getMessage());
                } 
                //while(jt.getSelectedItem()== "book"){
                //    area.append(url);
                //}
                
                
                
                     
            clean 
                    area.append("\t\t????\n"); 
                else 
                if(jt.getSelectedItem()=="pen") 
                    area.append("\t???\n"); 
                 
             
            else 
                if(jt.getSelectedItem()=="ruler") 
                    area.append("\n\t\t????\n"); 
            *///} 
    //}         
     
    public static void main(String[] rags){ 
        Dictionary dic = new Dictionary(); 
        dic.setSize(550,300); 
        dic.setLocation(200,200); 
         
        //dic.setResizable(false); 
        dic.setVisible(true); 
        dic.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE); 
         
    } 
} 
         




---

### Post by jespdj on 2007-11-05
Have a look at Sun's Java Tutorials, especially the tutorials about creating a GUI with Swing:

[http://java.sun.com/docs/books/tutorial/](http://java.sun.com/docs/books/tutorial/)

---

### Post by smartbei on 2007-11-05
@shafi: I'm not much of a Java person, but please put your well-indented code in code tags instead of quote tags.

---

### Post by LaRoza on 2007-11-05
> **smartbei said:**
> @shafi: I'm not much of a Java person, but please put your well-indented code in code tags instead of quote tags.

Or PHP tags, for syntax highlighting.

---

### Post by Vadi on 2007-11-05
This is a bit offtopic, but still close enough:

Where does java get its look from? It looks absoltely fugly on my ubuntu (especially the scrollbars) - I was hoping to give it a better skin somehow. I can post a screenshot if what/

---

### Post by LaRoza on 2007-11-05
> **Vadi said:**
> This is a bit offtopic, but still close enough:

Where does java get its look from? It looks absoltely fugly on my ubuntu (especially the scrollbars) - I was hoping to give it a better skin somehow. I can post a screenshot if what/

[http://www.developerfusion.co.uk/show/3798/6/](http://www.developerfusion.co.uk/show/3798/6/)

---

### Post by Vadi on 2007-11-05
Hm yes the problem is that I'm not making the application; I'm just a user here. Is there anything I can do about that?

---

### Post by LaRoza on 2007-11-05
> **Vadi said:**
> Hm yes the problem is that I'm not making the application; I'm just a user here. Is there anything I can do about that?

Then that was very OT. If you have display issues, use another forum, sorry.

---

### Post by shafi on 2007-11-17
I have problem with the **xml** file which i want to connect to my GUI application, but i don't know  how to connect it, when i write the English word into the combo box then after pressing the enter i want the Persian meaning of that word to  be shown from the xml file  into the text area
if any one knows please help me ......... thanks

this is the xml file (**generic.xdb**) that i want to be connect ( i have it locally in my laptop):
 click it : [http://xfardic.sf.net/generic.xdb.bz2](http://xfardic.sf.net/generic.xdb.bz2)

this is the code: 
[HTML] import java.awt.*;

import java.awt.event.*;

import javax.swing.*;

//import java.sql.*;
//import java.io.*;
import java.io.*;
import javax.xml.parsers.*;
import org.xml.sax.*;
import org.xml.sax.helpers.DefaultHandler;



public class Dictionary extends JFrame implements ActionListener{

	String words[] = {"book","pen","ruler","fan","age","name","job","trouble group ///Dictionary"}; //here i have create an array temporary but instead this i want to be connect to the xml file

	JLabel label = new JLabel("Trouble Group Dictionary");

	JLabel lab = new JLabel("Enter the Word: ");

	JComboBox jt = new JComboBox(words);

	JTextArea area = new JTextArea(35,35);

	JButton button = new JButton("Color");

	JButton go = new JButton("go");

	JButton about = new JButton("about us");



	Dictionary(){

		setTitle("TG Dictionary");

		Container c = getContentPane();

		

		c.setLayout(new FlowLayout());

		c.add(label);

		c.add(about);

		c.add(jt);

		c.add(go);

		go.addActionListener(this);

		go.setActionCommand("go");

		c.add(button);

		button.addActionListener(this);

		button.setActionCommand("color");

		c.add(area);

		

		

		about.addActionListener(this);

		about.setActionCommand("about us");

		

		label.setFont(new Font("Times New Roman",Font.BOLD,45));

		jt.setFont(new Font("Times New Roman",Font.ITALIC,20));

		area.setFont(new Font("Tahoma",Font.ITALIC,23));

		area.setEditable(false);

		jt.setEditable(true);

		

	}

		

	public void actionPerformed(ActionEvent e,String[] args){

			

			if (e.getActionCommand().equals("color")) {

			Color c=JColorChooser.showDialog(getContentPane(),"Choose a color",getContentPane().getBackground());

				getContentPane().setBackground(c);

		

				}

			else

			if(e.getActionCommand().equals("about us")){

				JFrame f = new JFrame("about us");

				JLabel image = new JLabel( new ImageIcon("pic.gif") );

							

				f.setVisible(true);

				f.add(image);

				f.pack();

				f.show();

				f.setSize(500,500);

				f.setLocation(250,250);

				f.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

								

			}

				

			else
			

			if(e.getActionCommand().equals("go")){

				
				//String url = "java ExampleSaxGetData generic.xdb word in shafi out";				
				try {
      MyDefaultHandlerImpl handler = new MyDefaultHandlerImpl();
      handler.args = args;
      SAXParser saxParser = SAXParserFactory.newInstance().newSAXParser();
      saxParser.parse( new File( args[0] ), handler );
      if( 0 < handler.sbResult.length() )
      {
        System.out.println( "Result string in child element '<"
                            + args[4] + ">':" );
        System.out.println( handler.sbResult );
        System.exit( 0 );
      }
      else
      {
        System.out.println( "No fitting element found." );
        System.exit( 2 );
      }
      area.append(url);
    } catch( Throwable t ) {
      t.printStackTrace();
      System.exit( 3 );
    }
					

	public static void main(String[] rags){

		Dictionary dic = new Dictionary();

		dic.setSize(550,300);

		dic.setLocation(200,200);

		

		dic.setResizable(false);

		dic.setVisible(true);

		dic.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

		

	}

}

		

 [/HTML]

---

### Post by xlinuks on 2007-11-18
Since your .XDB file is simple IMO it's faster and easier to write the code by hand (without an XML parser).
Here's my/an example of your application:
```

screenshot:
http://xlinuks.googlepages.com/dict.screen.jpg

The application itself (runs on Java 6 or later):
http://xlinuks.googlepages.com/Dictionary.jar (1MB, includes your database)

The source code:
http://xlinuks.googlepages.com/Dictionary.source.zip (only 2.5KB)

```

If you are plannig to extend it, you should consider using MySQL, cause when you get big files it's both faster and more powerful than an XML parser.

---

### Post by shafi on 2007-11-24
> **xlinuks said:**
> Since your .XDB file is simple IMO it's faster and easier to write the code by hand (without an XML parser).
Here's my/an example of your application:
```

screenshot:
http://xlinuks.googlepages.com/dict.screen.jpg

The application itself (runs on Java 6 or later):
http://xlinuks.googlepages.com/Dictionary.jar (1MB, includes your database)

The source code:
http://xlinuks.googlepages.com/Dictionary.source.zip (only 2.5KB)

```

If you are plannig to extend it, you should consider using MySQL, cause when you get big files it's both faster and more powerful than an XML parser.
************** Thanks! *******************
Dear XLinuks thanks alot for the code, I don't konw how to thank you, it is working but i have some few questions:
**Q1:** could you please explain alittle bit the following method?
[HTML] private void loadDatabase( String sFileName ) {
		StringBuilder sbBuffer = new StringBuilder( 300000 );
		
		try {
			
			InputStream fin = this.getClass().getResourceAsStream( "/" + sFileName );
			byte[] bytes = new byte[ 1024 ];
			int iRead = 0;
			
			while( (iRead = fin.read( bytes )) > -1 ) {
				sbBuffer.append( new String( bytes, 0, iRead ) );
			}
			
			fin.close();
		} catch( Exception exc ) {
			tell( "<html><pre>Exception while reading the database: " + exc.getStackTrace() + "</pre></html>" );
			exc.printStackTrace();
			return;
		}[/HTML]
**Q2:** another problem that i have is reading the persian fonts they are readable but no totally clear , how can i solve this problem? if you guide me please.

**Q3:** how I can add this package to Ubuntu softwares?
that every one could install it using apt-get, please help me thanks alot.

---

### Post by shafi on 2007-12-01
Dear all, I have programmed and application using Java and now i want to build a package that could install it on my ubuntu, but when i try the dpkge -b i find the following error: please help me,
I have used the following packages in my program:

import java.awt.*;
import java.awt.event.*;
import java.io.*;
import java.net.*;
import java.util.Vector;
import javax.swing.*;

> 
dpkg -b /usr/bin/XDicFa/ XDicFa.deb

dpkg-deb: failed to open package info file `/usr/bin/XDicFa//DEBIAN/control' for reading: No such file or directory
this is the control file:

[HTML]

Version: 1.0
Section: Accessories
Priority: optional
Architecture: all
Essential: no
Depends: libgcj7-awt  
Installed-Size: 5MB
Provides: XDicFa
Description: English Persian Dictionary

[/HTML]

---

### Post by shafi on 2007-12-08
Dear all,
I have programmed a **java application(English-persian Dictionary) ** but now I dont know how to convert it into a **.deb package**.

plzzzzzzzzzzzzzzzzzzz helpppppppppp meeeeeee

this is the fourth time that i am posting this problem plzzzz help me

I have attached the source code and  the database of the dictionary: 
 
[http://xfardic.sf.net/generic.xdb.bz2](http://xfardic.sf.net/generic.xdb.bz2)

---

### Post by Glennji on 2007-12-13
> **shafi said:**
>                               dpkg -b /usr/bin/XDicFa/ XDicFa.deb

dpkg-deb: failed to open package info file `/usr/bin/XDicFa//DEBIAN/control' for reading: No such file or directory

Look at the output -- there is an extra / in there.  I would try the following i.e. without the / at the end of the first parameter.

```
dpkg -b /usr/bin/XDicFa XDicFa.deb
```

---

### Post by sh!ft on 2007-12-13
I suggest using AWT as apposed to SWING, it's generic, and has a much better feel as it's handled by your window manager natively.

For the most part SWING extends AWT anyway, at least, the main modular classes. So you're going to use AWT anyway, you just wont be aware of it from the programmers aspect.

AWT is rendered by your window manager, while SWING is rendered by Java2D which can lead to more overhead when a GPU is not present. (Virtualization inside of virtualization, yes to recursion.)

Don't get me wrong, SWING has benefits, I've just never found a case where I needed them.

---

