---
title: "[Java] enter data into arrays of Textfields"
date: 2009-08-06
forum: Programming Talk
---

### Post by gotenks05 on 2009-08-06
I am making a Java program that creates an XSPF file.  I know that I can already make one via VLC, but I want to see if I can create a valid XSPF file anyway.  I looked up the specs and typed out the basics of what an example in the specs looked like, but I'm stuck.  I want to use JFilechooser to have it be as easy as possible to select a file to add it in the apporiate textfield.  However, this is where things get difficult.  I setup an array of JtextFields to put in the data, which works fine for manually inputting the file's location, but my original code had a flaw that would not work out in the program, so I moved the Action Listener class inside of the method, so I could try and specify the array element, but the compiler says that there is an error and wants the variable "count" to be a final datatype instead of an integer, but since "count" is used for the for loop, that would render my loop useless.  The button, which I labelled "Browse..", and also an array in of itself, is supposed to open up and put it in the textfield that it resides next to.  For example, browse[0] is supposed to set the text in file[0] and browse[1] is supposed to set the text in file[1].  How can I get this to compile and work?  This is the first time I attempted a program like this, but not my first time using loops or arrays.

This is my source code:

```
import javax.swing.*;
import java.awt.*;
import java.awt.event.*;
import java.io.*;

public class Playlist extends JFrame
{
	String name, filename[];
	JTextField playname, file[];
	JLabel messname, messfile[];
	JButton create, browse[];

	String items = JOptionPane.showInputeDialog(null, "Enter number of items in the playlist", "playlist items", JOptionPane.QUESTION_MESSAGE);
	int files = Integer.parseInt(items);

	String path = File.separator+"tmp";

	JFileChooser window = new JFileChooser(new File(path));
	JPanel panel = new JPanel();

	public Playlist()
	{

		super("XSPF Generator");
		setSize(700, 450);
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

		file = new JTextField[files];
		messfile = new JLabel[files];
		browse = new JButton[files];

		messname = new JLabel("Enter name for playlist:");
		playname = new JTextField(10);

		for (int count = 0; count <= files -1; count++)
		{
			messfile[count] = new JLabel("Enter file path:");
			file[count] = new JTextField(10);
			browse[count] = new JButton("Browse...");
			browse.addActionListener(new ActionListener()
			{
				public void actionPerformed(ActionEvent e)
				{
					window.showOpenDialog(null);
					File input = window.getSelectedFile();

					String con = String.valueOf(input);

					file[count].setText(con);
				}
			});

		}

		create = new JButton("Create");
		create.addActionListener(new CreateListener());

		panel.add(messname);
		panel.add(playname);

		for (int display = 0; display <= files -1; display++)
		{
			panel.add(messfile[display]);
			panel.add(file[display]);
			panel.add(browse[display]);
		}

		panel.add(create);

		add(panel);

		setBackground(Color.GRAY);

		setVisible(true);
	}

	private class CreateListener implements ActionListener
	{
		public void actionPerformed(ActionEvent a)
		{
			for (int collect = 0; collect <= files -1; collect++)
			{
				filename[collect] = file[collect].getText();
			}
			
			name = playname.getText() +".xspf";
			try
			{
				FileWriter xspf = new FileWriter(name, true);
				
				xspf.write("<?xml version=\"1.0\"?>");
				xspf.write("<playlist version=\"1\"  xmlns=\"http://xspf.org/ns/0/\">");
				xspf.write("<tracklist>");
				
				for (int output = 0; output <= files -1; output++)
				{
					xspf.write("<track>\n<location>" + filename[output] + "</location>\n</track>");
				
				}

                                xspf.write("</tracklist>");
				xspf.write("</playlist>");
				
				xspf.close();
			}
			
			catch (IOException ioe)
			{
				JOptionPane.showMessageDialog(null, "file creation failed", "Failed to generated", JOptionPane.ERROR_MESSAGE);
			}
		}
	}
	
	public static void main(String[] args)
	{
		new Playlist();
	}
}
```

---

### Post by furuno on 2009-08-07
Instead of using arrays maybe a map (HashMap) is more suitable for this kind of problem. A HashMap is a class that stores a collections of objects in pairs. Each objects has a 1-1 relationships with their corresponding objects. For example (in your case) :

browseButton1 - textField1
browseButton2 - textField2
browseButton3 - textField3
...

So you'll only need to bind each button with a textfield.

---

