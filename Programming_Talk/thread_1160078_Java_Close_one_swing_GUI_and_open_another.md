---
title: "Java: Close one swing GUI and open another"
date: 2009-05-15
forum: Programming Talk
---

### Post by Fixel on 2009-05-15
New, and terrible, at GUI programming. 

What I want is for the mMenu frame to close when the user clicks one of the buttons and (eventually build a new frame but for now just) open a JOptionPane message dialog.

```
/*
 *      MainMenu.java
 *      
 *      Copyright 2009 Felix Mulder <felix.mulder@gmail.com>
 *      
 *      This program is free software; you can redistribute it and/or modify
 *      it under the terms of the GNU General Public License as published by
 *      the Free Software Foundation; either version 2 of the License, or
 *      (at your option) any later version.
 *      
 *      This program is distributed in the hope that it will be useful,
 *      but WITHOUT ANY WARRANTY; without even the implied warranty of
 *      MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 *      GNU General Public License for more details.
 *      
 *      You should have received a copy of the GNU General Public License
 *      along with this program; if not, write to the Free Software
 *      Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston,
 *      MA 02110-1301, USA.
 */


import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

public class MainMenu {
	
	public static void main (String args[]) {
		try{
			UIManager.setLookAndFeel(new com.sun.java.swing.plaf.gtk.GTKLookAndFeel());
		} catch(Exception ex){ ex.printStackTrace(); }

		mainMenu mMenu = new mainMenu();
		mMenu.frame = new JFrame("Benkyou-kun");
		mMenu.build();
		
	}
}


class menu extends JFrame {
	JFrame frame;
	public void build(){
		
		frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		frame.setSize(601,400);
		frame.setLocationRelativeTo(null);
		frame.setVisible(true);


		//Create MenuBar
		JMenuBar menuBar = new JMenuBar();
		//Create File menu
		JMenu fileMenu = new JMenu("File");
		//Create File menu items
		JMenuItem quitMenuItem = new JMenuItem("Quit (Ctrl+Q)");
		//Add File menu items
		fileMenu.add(quitMenuItem);
		//Add File menu to menubar
		menuBar.add(fileMenu);

		
		//Create Edit menu
		JMenu editMenu = new JMenu("Edit");
		//Create Edit menu items
		JMenuItem prefMenuItem = new JMenuItem("Preferences (Ctrl+Q)");
		//Add Edit menu items
		editMenu.add(prefMenuItem);
		//Add Edit menu to menubar
		menuBar.add(editMenu);

		
		//Create About menu
		JMenu aboutMenu = new JMenu("About");
		//Create About menu items
		JMenuItem aboutMenuItem = new JMenuItem("About Me");
		//Add About menu Items
		aboutMenu.add(aboutMenuItem);
		//Add About menu to menubar
		menuBar.add(aboutMenu);


		//Add the menubar to the frame
		frame.setJMenuBar(menuBar);
		
	}
	public void setShow(boolean onOff_switch){
		boolean closemain =(onOff_switch);
	}
}

class mainMenu extends menu{
	
	public void build(){
		//Build frame from super class
		super.build();
		// Override super class' default size
		frame.setSize(600,400);
		
		//Buttons
		JButton WordgapMenu = new JButton("Wordgaps");
		WordgapMenu.addActionListener(new WordgapMenuAction());
		
		JButton MangaMenu = new JButton("Manga");
		MangaMenu.addActionListener(new MangaMenuAction());
		
		JButton ListenCompMenu = new JButton("Listening Comprehension");
		ListenCompMenu.addActionListener(new ListCompMenuAction());
		
		JButton ReadCompMenu = new JButton("Reading Comprehension");
		ReadCompMenu.addActionListener(new ReadCompAction());
		
		JButton WordTestMenu = new JButton("Word Test");
		WordTestMenu.addActionListener(new WordTestAction());
		
		JButton DictionaryMenu = new JButton("Dictionary");
		DictionaryMenu.addActionListener(new DictionaryMenuAction());
		
		JButton KanaMenu = new JButton("Kana Quiz");
		KanaMenu.addActionListener(new KanaMenuAction());
		
		JButton WordPatternMenu = new JButton("Word Patterns");
		WordPatternMenu.addActionListener(new WordPatternAction());
		
		JButton KanjiMenu = new JButton("Kanji");
		KanjiMenu.addActionListener(new KanjiMenuAction());
		
		//Create Panel for the West Buttons
		JPanel westpanel = new JPanel(new GridLayout(0,1));
		//Add buttons to panel!
		westpanel.add(WordgapMenu);
		westpanel.add(MangaMenu);
		westpanel.add(ListenCompMenu);
		westpanel.add(ReadCompMenu);
		westpanel.add(WordTestMenu);
		westpanel.add(DictionaryMenu);
		westpanel.add(KanaMenu);
		westpanel.add(WordPatternMenu);
		westpanel.add(KanjiMenu);
		
		//Set panel layout
		//westpanel.setLayout();
		//westpanel.setLayout(new BoxLayout(westpanel, BoxLayout.Y_AXIS));
		//Add panel to frame
		frame.getContentPane().add(BorderLayout.WEST, westpanel);
		MainMenuPic pic = new MainMenuPic();
		frame.getContentPane().add(BorderLayout.CENTER, pic);		

		
	}
	
}

class MainMenuPic extends JPanel{
	
	public void paintComponent(Graphics g){
		Image image = new ImageIcon("preview.jpg").getImage();
		
		g.drawImage(image,80,20,this);	
	}
}

class WordgapMenuAction extends mainMenu implements ActionListener{
	public void actionPerformed(ActionEvent a){
		//frame.setVisible(false);
		JOptionPane.showMessageDialog(null, "You pressed the 'Wordgaps' button.");
		//frame.setVisible(true);

	}
}
class MangaMenuAction extends mainMenu implements ActionListener{
	public void actionPerformed(ActionEvent a){
		//frame.setVisible(false);
		JOptionPane.showMessageDialog(null, "You pressed the 'Manga' button.");
		//frame.setVisible(true);

	}
}
class ListCompMenuAction extends mainMenu implements ActionListener{
	public void actionPerformed(ActionEvent a){
		//frame.setVisible(false);
		JOptionPane.showMessageDialog(null, "You pressed the 'Listening Comprehension' button.");
		//frame.setVisible(true);

	}
}
class ReadCompAction extends mainMenu implements ActionListener{
	public void actionPerformed(ActionEvent a){
		//frame.setVisible(false);
		JOptionPane.showMessageDialog(null, "You pressed the 'Reading Comprehension' button.");
		//frame.setVisible(true);

	}
}

class WordTestAction extends mainMenu implements ActionListener{
	public void actionPerformed(ActionEvent a){
		// check **** for this fix! frame.setLocationRelativeTo(random);
		JOptionPane.showMessageDialog(null, "You pressed the 'Word Test' button.");
		
		
	}
}
class DictionaryMenuAction extends mainMenu implements ActionListener{
	public void actionPerformed(ActionEvent a){
		//frame.setVisible(false);
		JOptionPane.showMessageDialog(null, "You pressed the 'Dictionary' button.");
		//frame.setVisible(true);

	}
}
class KanaMenuAction extends mainMenu implements ActionListener{
	public void actionPerformed(ActionEvent a){
		//frame.setVisible(false);
		JOptionPane.showMessageDialog(null, "You pressed the 'Kana Quiz' button.");
		//frame.setVisible(true);

	}
}
class WordPatternAction extends mainMenu implements ActionListener{
	public void actionPerformed(ActionEvent a){
		//frame.setVisible(false);
		JOptionPane.showMessageDialog(null, "You pressed the 'Word Patterns' button.");
		//frame.setVisible(true);

	}
}
class KanjiMenuAction extends mainMenu implements ActionListener{
	public void actionPerformed(ActionEvent a){
		JOptionPane.showMessageDialog(null, "You pressed the 'Kanji' button.");
		//frame.setVisible(true);
	}
}

```

Any help/corrections to my thinking would be sincerely appreciated! Peace

---

### Post by C-- on 2009-05-15
From the JFrame setDefaultCloseOperation Java doc:

    *  DO_NOTHING_ON_CLOSE  (defined in WindowConstants): Don't do anything; require the program to handle the operation in the windowClosing  method of a registered WindowListener object.
    * HIDE_ON_CLOSE (defined in WindowConstants): Automatically hide the frame after invoking any registered WindowListener objects.
    * DISPOSE_ON_CLOSE (defined in WindowConstants): Automatically hide and dispose the frame after invoking any registered WindowListener objects.
    * EXIT_ON_CLOSE (defined in JFrame): Exit the application using the System exit method. Use this only in applications. 

I would suggest, if you want to destroy the JFrame and open another window, is to set the close operation to DISPOSE_ON_CLOSE and add a WindowListener to the window, perhaps as an anonymous class, that creates and shows your new window in the overridden windowClosing() method.

---

### Post by PaulM1985 on 2009-05-15
There are quite a few things wrong with this.

Firstly, In the menu class, you are extending a JFrame and having a JFrame as one of its variables.  It is already a type of JFrame (by extending it) and so you don't need to define another inside it.

I have simplified your code a bit by creating two files.  One is called MainMenu.java and the other is called Menu.java.

MainMenu is the thing that runs, ie it has the main() method in it.  Menu.java creates your menu and adds buttons etc.

These are below:
MainMenu.java
```

package Test;

import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

public class MainMenu {
	
	public static void main (String args[]) {
	    // try{
	    //  UIManager.setLookAndFeel(new com.sun.java.swing.plaf.gtk.GTKLookAndFeel());
	    //} catch(Exception ex){ ex.printStackTrace(); }

	    Menu mMenu = new Menu();
		
	}
}

```

Menu.java
```

package Test;

import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

class Menu extends JFrame {
       
    public Menu()
    {
	build();
    }
    
    public void build(){
		
	setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
	setSize(601,400);
	setLocationRelativeTo(null);
	setVisible(true);
	

	//Create MenuBar
	JMenuBar menuBar = new JMenuBar();
	//Create File menu
	JMenu fileMenu = new JMenu("File");
	//Create File menu items
	JMenuItem quitMenuItem = new JMenuItem("Quit (Ctrl+Q)");
	//Add File menu items
	fileMenu.add(quitMenuItem);
	//Add File menu to menubar
	menuBar.add(fileMenu);

		
	//Create Edit menu
	JMenu editMenu = new JMenu("Edit");
	//Create Edit menu items
	JMenuItem prefMenuItem = new JMenuItem("Preferences (Ctrl+Q)");
	//Add Edit menu items
	editMenu.add(prefMenuItem);
	//Add Edit menu to menubar
	menuBar.add(editMenu);

		
	//Create About menu
	JMenu aboutMenu = new JMenu("About");
	//Create About menu items
	JMenuItem aboutMenuItem = new JMenuItem("About Me");
	//Add About menu Items
	aboutMenu.add(aboutMenuItem);
	//Add About menu to menubar
	menuBar.add(aboutMenu);


	//Add the menubar to the frame
	setJMenuBar(menuBar);

	//JPanel pane = new JPanel();
	//pane.add(new JButton("I am a happy button"));
	System.out.println("getting here?");
	//this.add(pane);

	//Buttons
	JButton WordgapMenu = new JButton("Wordgaps");
	WordgapMenu.addActionListener(new WordgapMenuAction());
		
	JButton MangaMenu = new JButton("Manga");
	MangaMenu.addActionListener(new MangaMenuAction());
	
	JButton ListenCompMenu = new JButton("Listening Comprehension");
	ListenCompMenu.addActionListener(new ListCompMenuAction());
	
	JButton ReadCompMenu = new JButton("Reading Comprehension");
	ReadCompMenu.addActionListener(new ReadCompAction());
	
	JButton WordTestMenu = new JButton("Word Test");
	WordTestMenu.addActionListener(new WordTestAction());
	
	JButton DictionaryMenu = new JButton("Dictionary");
	DictionaryMenu.addActionListener(new DictionaryMenuAction());
	
	JButton KanaMenu = new JButton("Kana Quiz");
	KanaMenu.addActionListener(new KanaMenuAction());
	
	JButton WordPatternMenu = new JButton("Word Patterns");
	WordPatternMenu.addActionListener(new WordPatternAction());
	
	JButton KanjiMenu = new JButton("Kanji");
	KanjiMenu.addActionListener(new KanjiMenuAction());
	
	//Create Panel for the West Buttons
	JPanel westpanel = new JPanel();
	//Add buttons to panel!
	westpanel.add(WordgapMenu);
	westpanel.add(MangaMenu);
	westpanel.add(ListenCompMenu);
	westpanel.add(ReadCompMenu);
	westpanel.add(WordTestMenu);
	westpanel.add(DictionaryMenu);
	westpanel.add(KanaMenu);
	westpanel.add(WordPatternMenu);
	westpanel.add(KanjiMenu);
	
	//Set panel layout
	//westpanel.setLayout();
	//westpanel.setLayout(new BoxLayout(westpanel, BoxLayout.Y_AXIS));
	//Add panel to frame
	this.add(westpanel);
	//MainMenuPic pic = new MainMenuPic();
	//this.add(pic);

	
    }

    public void setShow(boolean onOff_switch){
	boolean closemain =(onOff_switch);
    }



    class WordgapMenuAction implements ActionListener{
	public void actionPerformed(ActionEvent a){
	    //frame.setVisible(false);
	    JOptionPane.showMessageDialog(null, "You pressed the 'Wordgaps' button.");
	    //frame.setVisible(true);
	    
	}
    }
    class MangaMenuAction implements ActionListener{
	public void actionPerformed(ActionEvent a){
	    //frame.setVisible(false);
	    JOptionPane.showMessageDialog(null, "You pressed the 'Manga' button.");
	    //frame.setVisible(true);
	    
	}
    }
    class ListCompMenuAction implements ActionListener{
	public void actionPerformed(ActionEvent a){
	    //frame.setVisible(false);
	    JOptionPane.showMessageDialog(null, "You pressed the 'Listening Comprehension' button.");
	    //frame.setVisible(true);
	    
	}
    }
    class ReadCompAction  implements ActionListener{
	public void actionPerformed(ActionEvent a){
	    //frame.setVisible(false);
	    JOptionPane.showMessageDialog(null, "You pressed the 'Reading Comprehension' button.");
	    //frame.setVisible(true);
	    
	}
    }
    
    class WordTestAction  implements ActionListener{
	public void actionPerformed(ActionEvent a){
	    // check **** for this fix! frame.setLocationRelativeTo(random);
	    JOptionPane.showMessageDialog(null, "You pressed the 'Word Test' button.");
	    
	    
	}
    }
    class DictionaryMenuAction implements ActionListener{
	public void actionPerformed(ActionEvent a){
	    //frame.setVisible(false);
	    JOptionPane.showMessageDialog(null, "You pressed the 'Dictionary' button.");
	    //frame.setVisible(true);
	    
	}
    }
    class KanaMenuAction implements ActionListener{
	public void actionPerformed(ActionEvent a){
	    //frame.setVisible(false);
	    JOptionPane.showMessageDialog(null, "You pressed the 'Kana Quiz' button.");
	    //frame.setVisible(true);
	    
	}
    }
    class WordPatternAction implements ActionListener{
	public void actionPerformed(ActionEvent a){
	    //frame.setVisible(false);
	    JOptionPane.showMessageDialog(null, "You pressed the 'Word Patterns' button.");
	    //frame.setVisible(true);
	    
	}
    }
    class KanjiMenuAction implements ActionListener{
	public void actionPerformed(ActionEvent a){
	    JOptionPane.showMessageDialog(null, "You pressed the 'Kanji' button.");
	    //frame.setVisible(true);
	}
    }
    
}

class MainMenuPic extends JPanel{
    
    public void paintComponent(Graphics g){
	Image image = new ImageIcon("preview.jpg").getImage();
	
	g.drawImage(image,80,20,this);	
    }
}


```

I have moved your actionlisteners to be inside the Menu class.  This is so that now when you click on a button they will pop up and show you an alert.  You may want to change this and create a single action listener that you add to all of the buttons.  You would write the actionlistener so that it could distinguish between the different buttons clicked on using a.getSource(), a being the ActionEvent.

I have commented out the part for the Image and the UIManager because they didnt work on my system.  They may do on yours.  The UIManager didn't display JPanels and I don't have the image so that wouldn't work.

Both of these files have to be inside a Test folder and you compile and run them using:
javac Test/Menu.java
javac Test/MainMenu.java
java Test/MainMenu

I hope this has helped.

Paul

---

### Post by Fixel on 2009-05-16
Sorry for the confusion. This is what I want to do:

```
import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

public class Simplified{
	public static void main(String[] args){
		Menu mMenu = new Menu();
		mMenu.build();
	}
}

class Menu{
	JFrame frame = new JFrame("Test");
	public void build(){
		
		frame.setDefaultCloseOperation(JFrame.DO_NOTHING_ON_CLOSE);
		//frame.setSize(601,400);
		frame.setLocationRelativeTo(null);
		frame.setVisible(true);
			
		JButton Button = new JButton("This button closes the window and opens another.");
		Button.addActionListener(new pressedAction());
		frame.getContentPane().add(BorderLayout.CENTER, Button);
		frame.pack();

	}
	public void close(){
		frame.setVisible(false);
		frame.dispose();
	}
}
class pressedAction extends Menu implements ActionListener{
		public void actionPerformed(ActionEvent a){
		// Close the mMenu frame
		close();
		JOptionPane.showMessageDialog(null, "When you press ok the main frame should appear again!.");
		// Open the mMenu frame on pressing the ok button
		build();
	}
}

```

The only thing that works is building the frame again... so I can get more of the same frame.. but I can't close it. (My close(); method doesn't work so to speak).. :(

I'm sure there's something I missed.

---

### Post by Fixel on 2009-05-16
So in short I know what I'm doing wrong, but I don't know the right way to do it. When I extend the listener's class with "Menu" I inherit the methods but not the actual frame I'm trying to close =(

So how do I close the actual "mMenu" while the JOpPane is open?! Preferebly from within the pressedAction class. =)

nvm.. solved it... added a private class (that didn't extend menu) in the build frame class =)

---

