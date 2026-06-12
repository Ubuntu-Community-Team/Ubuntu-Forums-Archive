---
title: "Java StackOverflowError Help"
date: 2008-08-18
forum: Programming Talk
---

### Post by bobbocanfly on 2008-08-18
I'm writing a small app in Java with the Swing GUI toolkit. I want to keep the actual window building code in one file and the handlers in a different file, so I dont end up with one file, 500+ lines long.

I am getting an error when using this code and I cant find how to fix it.

MainForm.java
```
package freespeech.gui;

import java.awt.Container;
import java.awt.BorderLayout;
import java.awt.FlowLayout;
import java.awt.event.*;

import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JTextArea;
import javax.swing.JPanel;
import javax.swing.JMenu;
import javax.swing.JMenuItem;
import javax.swing.JMenuBar;
import javax.swing.KeyStroke;
import javax.swing.JCheckBoxMenuItem;
import javax.swing.JRadioButtonMenuItem;
import javax.swing.ButtonGroup;
import javax.swing.ImageIcon;

import freespeech.Constants;
import freespeech.Speech;
import freespeech.Settings;
import freespeech.Error;
import freespeech.gui.MainFormHandlers;

public class MainForm {

    public MainFormHandlers handlers = new MainFormHandlers();

    public Constants constants = new Constants();
    public Speech speech = new Speech();
    public Settings settings = new Settings();
    public Error error = new Error();

    public JPanel button_panel = new JPanel();
    public JButton submit_button = new JButton("Speak");
    public JButton clear_button = new JButton("Clear");
    public JTextArea text_field = new JTextArea(20, 80);
    
    public JFrame frame = new JFrame(constants.name);

    /**
     * Sets up the main form and runs it
     * @param String[] args Because we might need them sometime (may be removed)
     */
    public void run(String[] args)
    {
        settings.load();
        speech.set_voice((String)settings.settings.get("voice")); /* TODO: The obvious, read this from settings */
    
        init_frame();
        show_frame();
    }
    
    /* Thankyou Sun*/
        /** Returns an ImageIcon, or null if the path was invalid. */
    protected static ImageIcon createImageIcon(String path) {
 return null;
    }

    
    public JMenuBar create_menu_bar() {
        JMenuBar menuBar;
        JMenu menu, submenu;
        JMenuItem menuItem;
        JRadioButtonMenuItem rbMenuItem;
        JCheckBoxMenuItem cbMenuItem;

        //Create the menu bar.
        menuBar = new JMenuBar();

        //Build the first menu.
        menu = new JMenu("File");
        menu.setMnemonic(KeyEvent.VK_A);
        menu.getAccessibleContext().setAccessibleDescription(
                "Open, Close, Export Files");
        menuBar.add(menu);

        //a group of JMenuItems
        menuItem = new JMenuItem("Save", KeyEvent.VK_S);
        menuItem.getAccessibleContext().setAccessibleDescription(
                "Saves current text to disk");
        menu.add(menuItem);

      	menuItem = new JMenuItem("Open", KeyEvent.VK_O);
        menuItem.getAccessibleContext().setAccessibleDescription(
                "Open a text file and put its contents in the speech area");
        menu.add(menuItem);

        menuItem = new JMenuItem("Export", KeyEvent.VK_E);
        menuItem.getAccessibleContext().setAccessibleDescription(
                "Export speech to Wav");
        menu.add(menuItem);

        menuItem = new JMenuItem("Exit", KeyEvent.VK_X);
        menuItem.getAccessibleContext().setAccessibleDescription(
                "Quit the application");
        menu.add(menuItem);
        
        //Build second menu in the menu bar.
        menu = new JMenu("Edit");
        menu.getAccessibleContext().setAccessibleDescription(
                "Edit the current text");
        menuBar.add(menu);
        
        menuItem = new JMenuItem("Clear");
        menuItem.getAccessibleContext().setAccessibleDescription(
                "Clears all of the current text");
        menu.add(menuItem);

        menuItem = new JMenuItem("Copy");
        menuItem.getAccessibleContext().setAccessibleDescription(
                "Copies selected text");
        menu.add(menuItem);

        menuItem = new JMenuItem("Cut");
        menuItem.getAccessibleContext().setAccessibleDescription(
                "Cuts selected text");
        menu.add(menuItem);

        menuItem = new JMenuItem("Paste");
        menuItem.getAccessibleContext().setAccessibleDescription(
                "Pastes text from the clipboard");
        menu.add(menuItem);
        
        menu = new JMenu("Help");
        menu.getAccessibleContext().setAccessibleDescription(
                "Edit the current text");
        menuBar.add(menu);
        
        menuItem = new JMenuItem("About");
        menuItem.getAccessibleContext().setAccessibleDescription(
                "About FreeSpeech");
        menu.add(menuItem);
        
        return menuBar;
    }
    
    /**
     * Sets up the frame and adds the buttons etc into it
     */
    public void init_frame()
    {
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        //frame.setSize(width, height);
        
        //submit_button.addActionListener(handlers.submit_listener);
        //clear_button.addActionListener(handlers.clear_listener);
        
        frame.setJMenuBar(create_menu_bar());
        
        button_panel.setLayout(new FlowLayout());
        button_panel.add(submit_button);
        button_panel.add(clear_button);
        
        Container container = frame.getContentPane();
        container.setLayout(new BorderLayout());
        
        container.add(text_field, BorderLayout.CENTER);
        container.add(button_panel, BorderLayout.SOUTH);

    }
    
    /**
     * Shows the frame generated in init_frame();
     */
    public void show_frame()
    {
        frame.pack();
        frame.setVisible(true);
    }

}
```

MainFormHandlers.java
```
/* gui/MainForm.java - Main GUI Window
   Copyright (C) 2008 David Futcher (bobbo) <bobbo@ubuntu.com>
   
   This file is part of the FreeSpeech application
   
   This program is free software: you can redistribute it and/or modify
   it under the terms of the GNU General Public License as published by
   the Free Software Foundation, either version 3 of the License, or
   (at your option) any later version.

   This program is distributed in the hope that it will be useful,
   but WITHOUT ANY WARRANTY; without even the implied warranty of
   MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
   GNU General Public License for more details.

   You should have received a copy of the GNU General Public License
   along with this program.  If not, see <http://www.gnu.org/licenses/>. */
   
package freespeech.gui;

import java.awt.event.*;

public class MainFormHandlers extends MainForm {

    //public SubmitButtonListener submit_listener = new SubmitButtonListener();
    //public ClearButtonListener clear_listener = new ClearButtonListener();


    /**
     * Listener for submit button (So we can actually speak)
     */
    class SubmitButtonListener implements ActionListener 
    {
        /**
         * Handler for submit button press
         * @param ActionEvent e Describes the event performed (auto)
         */
        public void actionPerformed(ActionEvent e) 
        {
            String to_speak = text_field.getText();
            
            /* Stops the frontend from 'locking' when it doesnt need to */
            if (to_speak.length() == 0)
            {
                error.error("No text to speak"); /* @todo error box? */
            }
            else
            {          
                speech.speak(to_speak);      
            }     
        }
    }
    
    /**
     * Listener for clear button
     */
    class ClearButtonListener implements ActionListener 
    {
        /**
         * Handler for clear button press
         * @param ActionEvent e Describes the event performed (auto)
         */
        public void actionPerformed(ActionEvent e) 
        {
            text_field.setText("");
        }
    }
}
```

Error:
```
	at freespeech.gui.MainFormHandlers.<init>(MainFormHandlers.java:23)
	at freespeech.gui.MainForm.<init>(MainForm.java:47)
	at freespeech.gui.MainFormHandlers.<init>(MainFormHandlers.java:23)
	at freespeech.gui.MainForm.<init>(MainForm.java:47)
        <repeated lots>

```

It compiles into a .jar just fine, but I get the above error when running the jar. How can I fix this?

---

### Post by dwhitney67 on 2008-08-18
It's been a long time since I developed any code in Java, so I may very well wrong with my assessment of your code... but I believe the issue lies with your instantiation of a 'MainFormHandlers' object in your class 'MainForm'.

Since MainFormHandlers subclasses MainForm, it seems that you have a recursive/infinite construction of classes.  This is probably is what is throwing java, and hence your program, for a spin.

---

### Post by bobbocanfly on 2008-08-18
Ok, I have managed to stop the problem by moving the MainFormHandlers inti code to init_frame():

```
    public void init_frame()
    {
        MainFormHandlers handlers = new MainFormHandlers();
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        //frame.setSize(width, height);
        
        //submit_button.addActionListener(handlers.submit_listener);
        //clear_button.addActionListener(handlers.clear_listener);
        
        frame.setJMenuBar(create_menu_bar());
        
        button_panel.setLayout(new FlowLayout());
        button_panel.add(submit_button);
        button_panel.add(clear_button);
        
        Container container = frame.getContentPane();
        container.setLayout(new BorderLayout());
        
        container.add(text_field, BorderLayout.CENTER);
        container.add(button_panel, BorderLayout.SOUTH);

    }
```

But now (obviously) when I click things, the handlers aren't run. How can I get this code to work properly?

---

### Post by mike_g on 2008-08-18
I havent used handlers yet but in the past adding listeners something like this:
```
submit_button.addActionListener(new ActionListener()
{
    public void actionPerfomed(ActionEvent e)
    {
        doSomething();      
    }
});
```
It always seemed to work fine so far.

---

### Post by dwhitney67 on 2008-08-18
First of all, I would recommend that your MainForm extend JFrame.  Then you add your widgets (buttons, labels, etc.) to JPanels using whatever layout you like.  Then add the JPanels to the content-pane.

For any JButtons you have, you can add an action listener using something like:
[PHP]myButton.addActionListener( new MyActionListener(this) );[/PHP]
MyActionListener needs to implement ActionListener, and hold a reference (handle) to the object using it.  For instance:
[PHP]
import java.awt.event.*;

class MyActionListener implements ActionListener
{
  private MainForm mainForm;

  public MyActionListener(MainForm client)
  {
    mainForm = client;
  }

  public void actionPerformed(ActionEvent event)
  {
    if (event.getActionCommand().equals("Speak"))
    {
      mainForm.doSomething();
    }
    else if (event.getActionCommand().equals("Clear"))
    {
      mainForm.doSomethingElse();
    }
  }
}[/PHP]
There might be other ways to "skin this cat", so the suggestion above is merely an example.

---

