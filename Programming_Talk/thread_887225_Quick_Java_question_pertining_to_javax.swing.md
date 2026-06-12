---
title: "Quick Java question pertining to javax.swing"
date: 2008-08-11
forum: Programming Talk
---

### Post by _UsUrPeR_ on 2008-08-11
Ok, I am having a problem creating a new window pane when an individual clicks on the readyButton. I'm trying to get a frame to pop up when the individual clicks "I am ready to vote!", but it won't compile. It seems to have an error with the commented line
```
new voteFrame();
```

Could someone tell me wtf is wrong? It seems like it should work to me. Also, I'm confused as to why I needed to make the voteFrame() method void.

Here's the code, and thanks in advance.

```
import javax.swing.*;
import java.io.*;
import java.text.*;
import java.awt.event.*;
import java.awt.Container.*;
import java.awt.*;

public class DogCatcher extends JFrame
{
	private JFrame mainFrame;
	public JFrame voteFrame;
	private JButton helpButton;
	private JButton exitButton;
	private JButton dennisButton;
	private JButton timButton;
	private JButton dickButton;
	private JButton homerButton;
	private JButton jesusButton;
	private JButton readyButton;
	private JButton tallyButton;
	
	boolean voted=false;
	
	public DogCatcher()
	{
	
		mainFrame = new JFrame("Rock that Vote!");
		helpButton = new JButton("HELP!");
		exitButton = new JButton("Exit");
		dennisButton = new JButton("Who is Dennis Vehland?");
		timButton = new JButton("Who is Tim Lyon?");
		dickButton = new JButton("Who is Dick Cheney?");
		homerButton = new JButton("Who is Homer Simpson?");
		jesusButton = new JButton("Who is Jesus Christ?");
		readyButton = new JButton("Ready to vote");
		tallyButton = new JButton("See the tallied votes");
	
	
		Container main = mainFrame.getContentPane();
		main.setLayout (new GridLayout(3,3) );
	
		main.add(dickButton);
		main.add(homerButton);
		main.add(jesusButton);
		main.add(dennisButton);
		main.add(timButton);
		main.add(readyButton);
		main.add(tallyButton);
		main.add(helpButton);
		main.add(exitButton);

		mainFrame.setSize(750,100);

		tallyButton.setEnabled(false);


		dickButton.setMnemonic('D');
		dennisButton.setMnemonic('e');
		timButton.setMnemonic('T');
		homerButton.setMnemonic('p');
		jesusButton.setMnemonic('J');
		exitButton.setMnemonic('x');
		helpButton.setMnemonic('H');
		
		mainFrame.show();
		
		
		WinHandler handler = new WinHandler();
		mainFrame.addWindowListener(handler);


		DickButtonHandler dickhandler = new DickButtonHandler();
		dickButton.addActionListener(dickhandler); //lol

		HomerButtonHandler homerhandler = new HomerButtonHandler();
		homerButton.addActionListener(homerhandler);	

		JesusButtonHandler jesushandler = new JesusButtonHandler();
		jesusButton.addActionListener(jesushandler);
		
		DennisButtonHandler dennishandler = new DennisButtonHandler();
		dennisButton.addActionListener(dennishandler);
		
		TimButtonHandler timhandler = new TimButtonHandler();
		timButton.addActionListener(timhandler);
		
		HelpButtonHandler helphandler = new HelpButtonHandler();
		helpButton.addActionListener(helphandler);
		
		ExitButtonHandler ehandler = new ExitButtonHandler();
		exitButton.addActionListener(ehandler);
		
		TallyButtonHandler tallyhandler = new TallyButtonHandler();
		tallyButton.addActionListener(tallyhandler);
		
		ReadyButtonHandler readyhandler = new ReadyButtonHandler();
		readyButton.addActionListener(readyhandler);				
	}

	class DickButtonHandler implements ActionListener
	{
		public void actionPerformed(ActionEvent e)
		{
			JOptionPane.showMessageDialog(null, "Dick Cheney -\n" +
															"\"I want to be dog catcher because my family is going hungry.\n" +
															"All of my progeny have the propensity to devour raw meat,\n" +
															"so the dogs I catch will go to feed them.\" ", "Dick Cheney", JOptionPane.INFORMATION_MESSAGE);
		}
	}

	class HomerButtonHandler implements ActionListener
	{
		public void actionPerformed(ActionEvent e)
		{
			JOptionPane.showMessageDialog(null, "Homer Simpson -\n" +
															"\"I am tired of working at the nuclear power plant, and dogs love me!\n" +
															"After my last stint as Mr. Plow, I can't see how this new job could go wrong.\" " ,
															"Homer Simpson", JOptionPane.INFORMATION_MESSAGE);

				
		}
	}

	class JesusButtonHandler implements ActionListener
	{
		public void actionPerformed(ActionEvent e)
		{
			JOptionPane.showMessageDialog(null, "Jesus Christ -\n" +
															"\"If you elect me as dog catcher, I will save your souls.\n" +
															"All it requires is 10% of your income every sunday\" " ,
															"Jesus Christ", JOptionPane.INFORMATION_MESSAGE);

			}
		}
		
	class DennisButtonHandler implements ActionListener
	{
		public void actionPerformed(ActionEvent e)
		{
			JOptionPane.showMessageDialog(null, "Dennis Vehland -\n" +
															"\"I can't believe we are having this put to a vote. I am a\n" +
															"licensed vetrinarian and the only person actually qualified \n" +
															"to capture dogs. It just so happens that I accidentally gassed\n" +
															"the mayor's dog. He should've had a collar on!\"" ,"Dennis Vehland", JOptionPane.INFORMATION_MESSAGE);
		}
	}

	class TimButtonHandler implements ActionListener
	{
		public void actionPerformed(ActionEvent e)
		{
			JOptionPane.showMessageDialog(null, "Tim Lyon -\n" +
															"\"I don't understand how my name got on the ballot, to be honest.\n" +
															"I am a graduated physics major. How could this happen?  \n",
															"Tim Lyon", JOptionPane.INFORMATION_MESSAGE);
		}
	}

	class HelpButtonHandler implements ActionListener
	{
		public void actionPerformed(ActionEvent e)
		{
			JOptionPane.showMessageDialog(null, "Select the name of the individual you would like to learn about.\n" +
															"Once you see the person you would like to vote for, click the \"Ready to vote\" Button.\n",
															"Help!", JOptionPane.INFORMATION_MESSAGE);			}
	}

	class TallyButtonHandler implements ActionListener
	{
		public void actionPerformed(ActionEvent e)
		{
			System.exit(0);
		}
	}

	class ReadyButtonHandler implements ActionListener
	{
		public void actionPerformed(ActionEvent e)
		{
			tallyButton.setEnabled(true);
//			new VoteFrame();
				
		}
	}

	class ExitButtonHandler implements ActionListener
	{
		public void actionPerformed(ActionEvent e)
		{
			System.exit(0);
		}
	}

	public void VoteFrame()
	{
		voteFrame = new JFrame("Time to make your choice!");
		Container vote = voteFrame.getContentPane();
		vote.setLayout (new GridLayout(3,3) );
		mainFrame.setSize(750,100);
	}


	public static void main(String args[])
	{
		new DogCatcher();
	}
	
}

class WinHandler implements WindowListener
{
	public void windowClosing(WindowEvent e) {System.exit(0);}
	public void windowClosed(WindowEvent e) {}
	public void windowOpened(WindowEvent e) {}
	public void windowIconified(WindowEvent e) {}
	public void windowDeiconified(WindowEvent e) {}
	public void windowActivated(WindowEvent e) {}
	public void windowDeactivated(WindowEvent e) {}
}
```

---

### Post by _UsUrPeR_ on 2008-08-12
NM! Found it!

need to take the new out of in front of voteFrame();

---

