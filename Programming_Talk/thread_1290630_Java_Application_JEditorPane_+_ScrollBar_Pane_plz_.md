---
title: "Java Application JEditorPane + ScrollBar/ Pane? plz help"
date: 2009-10-13
forum: Programming Talk
---

### Post by Eremis on 2009-10-13
Hi everybody!

I am still working on my Java senior project (high school, topic: Open Source), and I encountered a problem with my gui. I dont know how to add ScrollBars to JEditorPane. So if you could give me a simple code sample, or point me into a tutorial I would appreciate it.

I attached a screen-shot showing you my gui so far, and photoshoped it to show you want I am talking about.

The Code is below:

```


// Imports
import java.awt.*;
import java.net.URL;
import javax.swing.BoxLayout;
import javax.swing.Box;
import javax.swing.JFrame;
import javax.swing.JPanel;
import javax.swing.JButton;
import javax.swing.JEditorPane;
import javax.swing.ImageIcon;
import javax.swing.AbstractButton;

public class Open_EncryptGUI
{
    // private variables
     private ImageIcon newButtonIcon = createImageIcon("images/new.png");
     private ImageIcon saveButtonIcon = createImageIcon("images/save.png");
     private ImageIcon encryptButtonIcon = createImageIcon("images/encrypt.png");
     private ImageIcon decryptButtonIcon = createImageIcon("images/decrypt.png");
     private ImageIcon sendButtonIcon = createImageIcon("images/send.png");
     private JButton newButton = new JButton("New", newButtonIcon);
     private JButton saveButton = new JButton("Save", saveButtonIcon);
     private JButton encryptButton = new JButton("Encrypt", encryptButtonIcon);
     private JButton decryptButton = new JButton("Decrypt", decryptButtonIcon);
     private JButton sendButton = new JButton("Send", sendButtonIcon);
     private JEditorPane text = new JEditorPane();

     // Top panel of the GUI
     private class ButtonPanel extends JPanel
     {
         public ButtonPanel()
         {
             setLayout(new BoxLayout(this, BoxLayout.X_AXIS));

             newButton.setVerticalTextPosition(AbstractButton.BOTTOM);
             newButton.setHorizontalTextPosition(AbstractButton.CENTER);
             saveButton.setVerticalTextPosition(AbstractButton.BOTTOM);
             saveButton.setHorizontalTextPosition(AbstractButton.CENTER);
             encryptButton.setVerticalTextPosition(AbstractButton.BOTTOM);
             encryptButton.setHorizontalTextPosition(AbstractButton.CENTER);
             decryptButton.setVerticalTextPosition(AbstractButton.BOTTOM);
             decryptButton.setHorizontalTextPosition(AbstractButton.CENTER);
             sendButton.setVerticalTextPosition(AbstractButton.BOTTOM);
             sendButton.setHorizontalTextPosition(AbstractButton.CENTER);

             add(Box.createRigidArea(new Dimension(10, 0)));
             add(newButton);
             add(Box.createRigidArea(new Dimension(30, 0)));
             add(saveButton);
             add(Box.createHorizontalGlue());
             add(Box.createRigidArea(new Dimension(200, 0)));
             
             add(encryptButton);
             add(Box.createRigidArea(new Dimension(30, 0)));
             add(decryptButton);
             add(Box.createRigidArea(new Dimension(30, 0)));
             add(sendButton);
             add(Box.createRigidArea(new Dimension(10, 0)));
         }
     }

     // Bottom Panel of the GUI
     private class EditorPanel extends JPanel
     {
         public EditorPanel()
         {
             setLayout(new BoxLayout(this, BoxLayout.X_AXIS));

             add(Box.createRigidArea(new Dimension(10, 0)));
             add(text);
             add(Box.createRigidArea(new Dimension(10, 0)));
         }
     }

     // The Whole Panel as one
     private class EncryptorPanel extends JPanel
     {
         public EncryptorPanel()
         {
             ButtonPanel bp = new ButtonPanel();
             EditorPanel ep = new EditorPanel();
             Dimension dim = new Dimension(732, 500);

             setLayout(new BoxLayout(this, BoxLayout.Y_AXIS));
             setPreferredSize(dim);
             setMinimumSize(dim);

             add(Box.createRigidArea(new Dimension(0, 10)));
             add(bp);
             add(Box.createRigidArea(new Dimension(0, 10)));
             add(ep);
             add(Box.createRigidArea(new Dimension(0, 10)));
         }

     }

     // JFrame containiang the EncryptorPanel
     private class EncryptorJFrame extends JFrame
     {
         public EncryptorJFrame()
         {
             EncryptorPanel panel = new EncryptorPanel();
             Dimension dim = new Dimension(732, 500);
             setPreferredSize(dim);
             setMinimumSize(dim);

             setTitle("Open Crypt 1.0");
             setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
             add(panel);
             pack();
             setResizable(true);
             setVisible(true);
         }
     }

     // Returns an ImageIcon, or null if the path was invalid.
     // Used for Button Icons
     protected ImageIcon createImageIcon(String path)
     {
         URL imgURL = getClass().getResource(path);

         if (imgURL != null)
         {
             return new ImageIcon(imgURL);
         }
         else
         {
             System.err.println("Couldn't find file: " + path);
             return null;
         }
     }

     // Runs the GUI
     public void run()
     {
         EncryptorJFrame frame = new EncryptorJFrame();
     }

     /* Tester

      public static void main(String[] args)
     {
         Open_EncryptGUI gui = new Open_EncryptGUI();
         gui.run();
     }

      */
}

```

P.S.

I tried adding a "ScrollBar" to EditorPanel(), when I tried that it visually added it, but when I typed a lot of stuff, the scroolbar moved down with the text, so I was not able to see it. 

Thanks a lot!

---

### Post by lykeion on 2009-10-13
I'd suggest Sun's swing tutorial, it's quite good:

[http://java.sun.com/docs/books/tutorial/uiswing/components/scrollpane.html](http://java.sun.com/docs/books/tutorial/uiswing/components/scrollpane.html)

Also here's an example of an JEditorPane with a scrollpane:

[http://www.apl.jhu.edu/~hall/java/Swing-Tutorial/Swing-Tutorial-JEditorPane.html](http://www.apl.jhu.edu/~hall/java/Swing-Tutorial/Swing-Tutorial-JEditorPane.html)

Good luck with your project

---

### Post by Eremis on 2009-10-13
Thanks!

---

