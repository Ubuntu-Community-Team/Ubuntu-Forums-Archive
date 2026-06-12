---
title: "[Java] keep getting error message during runtime"
date: 2008-11-26
forum: Programming Talk
---

### Post by gotenks05 on 2008-11-26
I have made a program a while back that finds each variable in the pythagorean theorem and I decided to turn it into a GUI program.  However, I'm having troubles at runtime.  I have an input dialog that is supposed to reveal another Dialog box, if the right thing is typed in.  However, the error message I have it display if none of the inputs match keeps showing up, even when the input is correct.  Is there a way to fix this or should I turn the input dialog into a JFrame?  If it helps, I have included the source in this post.

```
import java.awt.*;
import java.awt.event.*;
import javax.swing.*;
import java.lang.Math;
public class Rightri
{
	public static void main(String[] args)
	{
		String choice;
		choice = JOptionPane.showInputDialog(null, "enter the variable you seek [side1, side2, hypot]:");
		boolean select = (choice == "side1");
		boolean select2 = (choice == "side2");
		boolean select3 = (choice == "hypot");
		if(select)
		{
			class Pythagcalc extends JDialog
			{
				JPanel panel;
				JTextField num1;
				JTextField num2;
				JTextField num3;
				JButton CalcButton;
				JLabel mess1;
				JLabel mess2;
				JLabel mess3;
				public Pythagcalc()
				{
					setSize(300, 100);
					mess1 = new JLabel("Enter the value of side1:");
					num1 = new JTextField(10);
					num1.setEditable(false);
					mess2 = new JLabel("Enter the value of side2:");
					num2 = new JTextField(10);
					mess3 = new JLabel("Enter the value of hypot:");
					num3 = new JTextField(10);
					CalcButton = new JButton("Calculate");
					CalcButton.addActionListener(new CalcListener());
					panel = new JPanel();
					panel.add(mess1);
					panel.add(num1);
					panel.add(mess2);
					panel.add(num2);
					panel.add(mess3);
					panel.add(num3);
					panel.add(CalcButton);
					setVisible(true);
					Container content = getContentPane();
					content.setBackground(Color.white);
					content.add(panel);
					setContentPane(content);
				}
				class CalcListener implements ActionListener
				{
					public void actionPerformed(ActionEvent e)
					{
						String str1 = num2.getText();
						String str2 = num3.getText();
						double first;
						double answer;
						first = Math.pow(Double.parseDouble(str2), 2) - Math.pow(Double.parseDouble(str1), 2);
						answer = Math.sqrt(first);
						JOptionPane.showMessageDialog(null, "the value of side2 is " +str1+ " units\n" + "the value of hypot is " +str2+ " units\n" + "The value of side1 is " +answer+ " units");
					}
				}
			}
		}
		else if(select2)
		{
			class Pythagcalc extends JDialog
			{
				JPanel panel;
				JTextField num1;
				JTextField num2;
				JTextField num3;
				JButton CalcButton;
				JLabel mess1;
				JLabel mess2;
				JLabel mess3;
				public Pythagcalc()
				{
					setSize(300, 100);
					mess1 = new JLabel("Enter the value of side1:");
					num1 = new JTextField(10);
					mess2 = new JLabel("Enter the value of side2:");
					num2 = new JTextField(10);
					num2.setEditable(false);
					mess3 = new JLabel("Enter the value of hypot:");
					num3 = new JTextField(10);
					CalcButton = new JButton("Calculate");
					panel = new JPanel();
					panel.add(mess1);
					panel.add(num1);
					panel.add(mess2);
					panel.add(num2);
					panel.add(mess3);
					panel.add(num3);
					panel.add(CalcButton);
					setVisible(true);
					Container content = getContentPane();
					content.setBackground(Color.white);
					content.add(panel);
					setContentPane(content);
				}
				class CalcListener implements ActionListener
				{
					public void actionPerformed(ActionEvent e)
					{
						String str1 = num1.getText();
						String str2 = num3.getText();
						double first;
						double answer;
						first = Math.pow(Double.parseDouble(str2), 2) - Math.pow(Double.parseDouble(str1), 2);
						answer = Math.sqrt(first);
						JOptionPane.showMessageDialog(null, "the value of side1 is " +str1+ " units\n" + "the value of hypot is " +str2+ " units\n" + "The value of side2 is " +answer+ " units");
					}
				}
			}
		}
		else if(select3)
		{
			class Pythagcalc extends JDialog
			{
				JPanel panel;
				JTextField num1;
				JTextField num2;
				JTextField num3;
				JButton CalcButton;
				JLabel mess1;
				JLabel mess2;
				JLabel mess3;
				public Pythagcalc()
				{
					setSize(300, 100);
					mess1 = new JLabel("Enter the value of side1:");
					num1 = new JTextField(10);
					mess2 = new JLabel("Enter the value of side2:");
					num2 = new JTextField(10);
					mess3 = new JLabel("Enter the value of hypot:");
					num3 = new JTextField(10);
					num3.setEditable(false);
					CalcButton = new JButton("Calculate");
					panel = new JPanel();
					panel.add(mess1);
					panel.add(num1);
					panel.add(mess2);
					panel.add(num2);
					panel.add(mess3);
					panel.add(num3);
					panel.add(CalcButton);
					setVisible(true);
					Container content = getContentPane();
					content.setBackground(Color.white);
					content.add(panel);
					setContentPane(content);
				}
				class CalcListener implements ActionListener
				{
					public void actionPerformed(ActionEvent e)
					{
						String str1 = num1.getText();
						String str2 = num2.getText();
						double first;
						double answer;
						first = Math.pow(Double.parseDouble(str2), 2) + Math.pow(Double.parseDouble(str1), 2);
						answer = Math.sqrt(first);
						JOptionPane.showMessageDialog(null, "the value of side1 is " +str1+ " units\n" + "the value of side2 is " +str2+ " units\n" + "The value of hypot is " +answer+ " units");
					}
				}
			}
		}
		else
		{ 
			JOptionPane.showMessageDialog(new JFrame(), "\"invalid choice!\"\n" + " The variable entered must be side1, side2, or hypot", "Error", JOptionPane.ERROR_MESSAGE);
		}
		JDialog dialog = new JDialog();
	}
}
```

While I'm waiting, I'll try changing the input dialog into a JFrame and see if it changes anything.

---

### Post by bobrocks on 2008-11-26
I will start you off -

You cant compare string contents with ==, this will merely compare object references.  To compare the contents of a string you should use the equals method.  choice.equals("side1") for example.

---

