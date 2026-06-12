---
title: "Ubuntu desktop freezes in relation to java Swing EventHandling"
date: 2011-01-16
forum: Programming Talk
---

### Post by alanmehio on 2011-01-16
I have tried on both eclipse and Netbeans IDE to debug a Swing java  application with an event handling; the case is a JCombobox with the  below code 

Just when I debug the method which handle the event; the desktop  freezes; I can move the mouse around but I can not activate and do  anything. I can not type on the command line either I just trun off the  electrical supply. The below are the required information:

OpenJDK Runtime Environment (IcedTea6 1.9.2) (6b20-1.9.2-0ubuntu1~10.04.1)
OpenJDK Client VM (build 19.0-b09, mixed mode, sharing)


hardware architecture is   [B]x86 and the ubuntu OS installed is 
Ubuntu 10.04 LTS - the Lucid Lynx 

the sample java application to test is 



import java.awt.BorderLayout;
import java.awt.event.ItemEvent;
import java.awt.event.ItemListener;

import javax.swing.BorderFactory;
import javax.swing.JComboBox;
import javax.swing.JComponent;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JOptionPane;
import javax.swing.JPanel;

public class ComboBoxSample extends JPanel
                          implements ItemListener {
    JLabel picture;

    public ComboBoxSample() {
        super(new BorderLayout());

        String[] petStrings = { "Bird", "Cat", "Dog", "Rabbit", "Pig" };

        //Create the combo box, select the item at index 4.
        //Indices start at 0, so 4 specifies the pig.
        JComboBox petList = new JComboBox(petStrings);
        petList.setSelectedIndex(4);
//        petList.addActionListener(this);
        petList.addItemListener(this);
        //Set up the picture.
       

        //Lay out the demo.
        add(petList, BorderLayout.PAGE_START);
        setBorder(BorderFactory.createEmptyBorder(20,20,20,20));
    }
    
    public void itemStateChanged(ItemEvent e) {
         JComboBox cb = (JComboBox)e.getSource();
         String petName = (String)cb.getSelectedItem();
        JOptionPane.showMessageDialog(null, petName);
    }
//
//    /** Listens to the combo box. */
//    public void actionPerformed(ActionEvent e) {
//        JComboBox cb = (JComboBox)e.getSource();
//        String petName = (String)cb.getSelectedItem();
//        JOptionPane.showMessageDialog(null, petName);
//    }

   
    /**
     * Create the GUI and show it.  For thread safety,
     * this method should be invoked from the
     * event-dispatching thread.
     */
    private static void createAndShowGUI() {
        //Create and set up the window.
        JFrame frame = new JFrame("ComboBoxDemo");
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

        //Create and set up the content pane.
        JComponent newContentPane = new ComboBoxSample();
        newContentPane.setOpaque(true); //content panes must be opaque
        frame.setContentPane(newContentPane);

        //Display the window.
        frame.pack();
        frame.setVisible(true);
    }

    public static void main(String[] args) {
        //Schedule a job for the event-dispatching thread:
        //creating and showing this application's GUI.
        javax.swing.SwingUtilities.invokeLater(new Runnable() {
            public void run() {
                createAndShowGUI();
            }
        });
    }
}


just add a break point in the event handling method ([/B][B]  public void itemStateChanged .... )

Your help is highly appreciated. 

Regards,
Alan Mehio
London,UK
[/B]

---

### Post by t1497f35 on 2011-01-16
opnejdk is still pretty buggy, if you wanna have less problems use sun-java6-jdk

edit: and if you have both installed make sure you're using the correct one, google for "update alternatives java ubuntu", i.e. "sudo update-alternatives --config java"

---

### Post by alanmehio on 2011-01-16
There is only one alternative in link group java: /usr/lib/jvm/java-6-openjdk/jre/bin/java
Nothing to configure.


Now I installed the jdk via an extractor from the link which did not affect the env. variable or the soft link etc..
so I can switch to the java 7 in eclipse and it works fine now. I can switch back if I see more serious problem but now I need to debug my swing application and later I can switch back via eclipse wind preference

the link is from 
[http://dlc.sun.com.edgesuite.net/jdk7/binaries/index.html](http://dlc.sun.com.edgesuite.net/jdk7/binaries/index.html)


Many thanks;  if there is another solution please let me know. I updated to the last openJdk 6 from ubuntu and still the problem exists. 

It is very annoying to see you OS freezes 

Cheers
Alan

---

### Post by benfortuna on 2011-04-28
For the record I am seeing exactly the same problem, total desktop freeze, only the mouse moves.

Does seem to be a Java event dispatch issue, as only seems to happen when I click a UI component..

Ubuntu 10.10 (amd64)
Java 6 (sun)

---

