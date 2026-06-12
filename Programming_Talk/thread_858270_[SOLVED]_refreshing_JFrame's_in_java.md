---
title: "[SOLVED] refreshing JFrame's in java"
date: 2008-07-13
forum: Programming Talk
---

### Post by Despot Despondency on 2008-07-13
Hey. I'm having a problem refreshing a JFrame when clearing the contentPane and then adding a new JPanel to it. I've got a JFrame and when I clear the contentPane, with removeAll(), and then add a new JPanel I have to minimize the window and then enlarge it before the changes take affect. Here's the code

```

package gui;

import javax.swing.JFrame;

public class Interface extends JFrame{
	
    private static final long serialVersionUID = 1L;

	private static JFrame frame;

	public Interface(){
	    frame = new JFrame("Risk");	
	    createAndShowGUI();
	}
	
    private static void createAndShowGUI(){
    	FrameUtil.setUp(frame);
	frame.setVisible(true);		
    }
    
    public static void MainMenu(){
    	frame.getContentPane().removeAll();
    	
    	MenuPanel menu = new MenuPanel();
	frame.setContentPane(menu.getPanel());
    }
    
    public static void NewGameMenu(){
    	frame.getContentPane().removeAll();
    	
    	NewGamePanel newGamePanel  = new NewGamePanel();
    	frame.setContentPane(newGamePanel.getPanel());
    }
}

```

Any suggestions?

---

### Post by issih on 2008-07-13
This is off the top of my head, and its a while since I used swing extensively, but I seem to remember there being methods something like revalidate and repaint....those ought to do it.

I might well be remembering the names wrong though..

Actually, this threaed is useful :)

[http://forum.java.sun.com/thread.jspa?threadID=583383&messageID=2981007](http://forum.java.sun.com/thread.jspa?threadID=583383&messageID=2981007)

---

### Post by Despot Despondency on 2008-07-13
Cool, thanks for your help. Used the validate() function, which seemed to work. Didn't seem to be any mention of it in the threads I found. Cheers again. :)

---

### Post by issih on 2008-07-13
Just so you know, I believe swing expects you to use revalidate() not validate(). validate is an awt command, so it probably works, but may cause a few quirks, I'd stick to revalidate instead.

---

