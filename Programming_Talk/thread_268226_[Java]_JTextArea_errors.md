---
title: "[Java] JTextArea errors"
date: 2006-09-29
forum: Programming Talk
---

### Post by Ryan Marcus on 2006-09-29
I've written an application in Eclispe on Fedora, and then sent it home to my Ubuntu machine. When I compiled it, I got some very strange behaviors.

I tried this again on my x86 laptop (my main computer is a PPC) and got the same results.

Here was the code I was trying to run, or at least the GUI part of it.
```

package gui;
import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

import generators.ImageTag;
import gui.AppendTextArea;

public class GUIManager implements ActionListener {
	public JFrame mainFrame, linkFrame;
	public JPanel mainPanel, linkPanel;
	public AppendTextArea mainEditor;
	public JLabel jlIMGsrc, jlIMGwidth, jlIMGheight, jlIMGalt;
	public JTextField tfIMGsrc, tfIMGwidth, tfIMGheight, tfIMGalt;
	public JButton jbIMGadd;
	
	public void Create() {
		CreateMainWindow();
		CreateImageWindow();
	}
	
	private void CreateMainWindow() {
		JFrame mainFrame = new JFrame("Tiguex");
		mainFrame.setVisible(true);
		mainFrame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		
		JPanel mainPanel = new JPanel(new BorderLayout());
		
		mainEditor = new AppendTextArea();
		JScrollPane myPane = new JScrollPane(mainEditor);
		
		
		mainPanel.add(myPane);
		
		mainFrame.add(mainPanel);
		mainFrame.pack();
		mainFrame.setSize(500, 500);
	}
	
	private void CreateImageWindow() {
		JFrame linkFrame = new JFrame("Add Link");
		linkFrame.setVisible(true);
		
		JPanel linkPanel = new JPanel(new GridLayout(0, 2));
		
		jlIMGsrc = new JLabel("Location:", JLabel.LEFT);
		jlIMGwidth = new JLabel("Width:", JLabel.LEFT);
		jlIMGheight = new JLabel("Height:", JLabel.LEFT);
		jlIMGalt = new JLabel("Alt:", JLabel.LEFT);
		
		tfIMGsrc = new JTextField();
		tfIMGwidth = new JTextField();
		tfIMGheight = new JTextField();
		tfIMGalt = new JTextField();
		
		jbIMGadd = new JButton("Add Link");
		jbIMGadd.setActionCommand("add_link");
		jbIMGadd.addActionListener(this);
		
		linkPanel.add(jlIMGsrc);
		linkPanel.add(tfIMGsrc);
		
		linkPanel.add(jlIMGwidth);
		linkPanel.add(tfIMGwidth);
		
		linkPanel.add(jlIMGheight);
		linkPanel.add(tfIMGheight);
		
		linkPanel.add(jlIMGalt);
		linkPanel.add(tfIMGalt);
		
		linkPanel.add(jbIMGadd);
		
		linkFrame.add(linkPanel);
		linkFrame.pack();
		linkFrame.setSize(400,150);
	}


	public void actionPerformed(ActionEvent e) {
		// TODO Auto-generated method stub
		if (e.getActionCommand().equals("add_link")) {
			// The add link button was clicked. Add a link from the fields
			ImageTag myIMG = new ImageTag();
			if (tfIMGwidth.getText().equals("") == false) {
				// Width was set. Was height?
				if (tfIMGheight.getText().equals("") == false) {
					// Height was set. Was alt?
					if (tfIMGalt.getText().equals("") == false) {
						// All properties set.
						mainEditor.AppendText(myIMG.Image(tfIMGsrc.getText(), Integer.parseInt(tfIMGwidth.getText()), Integer.parseInt(tfIMGheight.getText()), tfIMGalt.getText()));
					} else {
						// All but alt was set.
						mainEditor.AppendText(myIMG.Image(tfIMGsrc.getText(), Integer.parseInt(tfIMGwidth.getText()), Integer.parseInt(tfIMGheight.getText())));
					}
				} else {
					// All but alt and height set.
					mainEditor.AppendText(myIMG.Image(tfIMGsrc.getText(), Integer.parseInt(tfIMGwidth.getText())));
				}
			} else {
				mainEditor.AppendText(myIMG.Image(tfIMGsrc.getText()));
			}
		}
	}
	
}


```

I got everything from random AWT errors to the bottom half of the JTextArea vanishing. What is going on?

---

### Post by hod139 on 2006-10-02
Without seeing the error messages I can only guess.  My guess is that you are using GNU's java, not Sun's.  Simply installing the official Sun java from the repository is not enough.  See this thread for setting up Sun's java:
[http://www.ubuntuforums.org/showthread.php?t=201378](http://www.ubuntuforums.org/showthread.php?t=201378)

---

