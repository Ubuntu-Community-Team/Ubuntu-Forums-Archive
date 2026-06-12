---
title: "java - symbol not found"
date: 2009-05-03
forum: Programming Talk
---

### Post by mikemcleanuk on 2009-05-03
i am attempting to process some code that has been called from a different JFrame to the rest of the code and i have got a problem.

I have a popup that asks the user to fill out a small form and then click a button. This should then run a action script. I have a compile error however. I think its because the infomation is stored in a different frame but im not sure.

```
public class HomeController extends JPanel implements ActionListener
{
	...
	
	private JFrame TeleFrame = new JFrame("Television Settings");
	private JButton teleAddButton = new JButton("Add");
	private JButton teleCancelButton = new JButton("Cancel");
	
	String[] chans = { "1","2","3","4","5","6","7","8","9","10" };
	String[] vols = { "1","2","3","4","5","6","7","8","9","10" };
	private JComboBox chanList = new JComboBox(chans);
	private JComboBox volList = new JComboBox(vols);
	
	....
	public HomeController()
	{
	...
	}
	
	public void actionPerformed(ActionEvent ae)
	{
	....
		if(ae.getSource() == addButton) // located in the main frame
		{
			Object[] possibleValues = { "Lamp", "Television", "Clock" };
			Object selectedValue = JOptionPane.showInputDialog(null, "What do you want to add?", "Add an Application", JOptionPane.INFORMATION_MESSAGE, null, possibleValues, possibleValues[0]);
			
			if(selectedValue == "Lamp")
			{
				...
			}
			if(selectedValue == "Television")
			{
				teleFrameOpen();
			}
	
		if(ae.getSource() == teleAddButton) // located in the popup frame
		{
			//int chanSelection = Integer.parseInt(chanList.getSelectedItem());
			//int volSelection = Integer.parseInt(volList.getSelectedItem());
			
			String cs = getSelectedItem(chanList);
			String vs = getSelectedItem(volList);
			int chanSelection = Integer.valueOf(cs);
			int volSelection = Integer.valueOf(vs);
			
			Television tmpTele = new Television(false, chanSelection, volSelection);
			myAppliances.add(tmpTele);
			GridPanel.add(new JLabel(tmpTele.getPicture()));
			this.validate();
		}
	}
	
	private void teleFrameOpen()
	{
		teleAddButton.addActionListener(this);
		teleCancelButton.addActionListener(this);
		
		TeleFramePanel.add(new JLabel("Add a New Television!"));
		TeleFramePanel.add(new JLabel(new ImageIcon("../images/television.jpg")));
		TeleFramePanel.add(new JLabel("Choose default channel: "));
		TeleFramePanel.add(chanList);
		TeleFramePanel.add(new JLabel("Choose default volume: "));
		TeleFramePanel.add(volList);
		TeleFramePanel.add(teleAddButton);
		TeleFramePanel.add(teleCancelButton);
		
		TeleFrame.setSize(200, 300);
		TeleFrame.setResizable(false);
		TeleFrame.getContentPane().add(TeleFramePanel);
		TeleFrame.setVisible(true);
	}
}
```

```
C:\JPR\ICA3\ICA3\Java>javac TestHomeController.java
.\HomeController.java:219: cannot find symbol
symbol  : method getSelectedItem(javax.swing.JComboBox)
location: class HomeController
                        String cs = getSelectedItem(chanList);
                                    ^
.\HomeController.java:220: cannot find symbol
symbol  : method getSelectedItem(javax.swing.JComboBox)
location: class HomeController
                        String vs = getSelectedItem(volList);
                                    ^
2 errors
```

I have tried several things but dont seem to be able to get it to work. I also know that if i just made my array Int instead of String then i wouldnt have to convert the selection to Int. But i get errors when i do that also so i assume that JComboBox can only have String values.

Thanks 
Mike

---

### Post by baizon on 2009-05-03
Try this:
 ```
String cs = chanList.getSelectedItem();
String vs = volList.getSelectedItem();
```

---

### Post by mikemcleanuk on 2009-05-03
> **baizon said:**
> Try this:
 ```
String cs = chanList.getSelectedItem();
String vs = volList.getSelectedItem();
```

```
C:\JPR\ICA3\ICA3\Java>javac TestHomeController.java
.\HomeController.java:217: incompatible types
found   : java.lang.Object
required: java.lang.String
                        String cs = chanList.getSelectedItem();
                                                            ^
.\HomeController.java:218: incompatible types
found   : java.lang.Object
required: java.lang.String
                        String vs = volList.getSelectedItem();
                                                           ^
2 errors
```

worth a try but got this error

---

### Post by baizon on 2009-05-03
Sorry, was my fault... i was to hasty.
```
String cs = chanList.getSelectedItem().toString();
String vs = volList.getSelectedItem().toString();
```

---

### Post by mikemcleanuk on 2009-05-03
thanks fixed it :D

---

