---
title: "Java Swing JPanel / Combobox question"
date: 2010-04-21
forum: Programming Talk
---

### Post by SNYP40A1 on 2010-04-21
I have a JPanel which is setup using the following code:

[PHP]					public JPanel getJPanel() {
			JPanel jp = new JPanel();
			jp.setLayout(new BoxLayout(jp, BoxLayout.PAGE_AXIS));
			jp.add(new JLabel("Database:"));
			JComboBox databaselist = new JComboBox(basemap.getNames());
			jp.add(databaselist);
			jp.add(new JLabel("ChartTypes:"));
			final JComboBox charttype = new JComboBox(charts.toArray(new PanelOption[0]));
			jp.add(charttype);
			final JPanel copanel = new JPanel();
			jp.add(copanel);
			copanel.setLayout(new BoxLayout(copanel, BoxLayout.PAGE_AXIS));
			
			charttype.addActionListener(new ActionListener() {
				public void actionPerformed(ActionEvent e) {
					PanelOption pot = (PanelOption)charttype.getSelectedItem();
					copanel.removeAll();
					HashMap<String, String> options = pot.getParamOptions();
					Set<String> optkeys = options.keySet();
					for(String str:optkeys)
					{
						System.out.println(str);
						copanel.add(new JLabel(str + ":"));
						copanel.add(new JTextField());
					}
					copanel.setVisible(true);
				}
			});	
			return jp;
		}	[/PHP]

"jp" above is a JPanel which contains a JComboBox called called charttype.  I setup a new JPanel called copanel and I add copanel to the containing JPanel, jp.  I want copanel to add JLabels and JTextFields based on the object currently selected in the JComboBox called charttype.  I can see that the correct strings are printing with the "System.out.println(str);" call inside the for loop.  However, the corresponding JLabels and JTextFields are not added to copanel.  I can add components to copanel by calling copanel.add... outside the actionListener function, for example right after the line 

[PHP]final JPanel copanel = new JPanel();[/PHP]

I can add in copanel.add(new JLabel("Test: ")); and I do see "Test:" label added.  But for some reason, I can't add components to copanel in the actionListener block.  Does anyone see why?

---

### Post by PaulM1985 on 2010-04-22
Try changing the declaration of copanel so that it is not final.

---

### Post by SNYP40A1 on 2010-04-22
Copanel must be final so that it can be accessed in the actionPerformed method directly below.  I probably should have also included this code, here's where getPanel() is called:

[PHP]		JMenuItem rescItem2 = new JMenuItem("Add Panel");
		rescItem2.setToolTipText("Add a panel");
		rescItem2.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {				
				JPanel optpanel = chartmap.getJPanel();
				String options[] = {"OK", "CANCEL"};
				int choice = JOptionPane.showOptionDialog(getChart(), optpanel, 
						"Add Option Panel", JOptionPane.DEFAULT_OPTION, JOptionPane.INFORMATION_MESSAGE, null,
						options, options[0]);	
				if(choice == 0) chartmap.addChart(optpanel);
			}
		});
		configure.add(rescItem2);[/PHP]

I am suspecting that the problem might be related to the fact that the actionListener on charttype is called after getChart() has returned.  By that point, all local variables in the getChart() function would have been popped from the stack, right?  But in that case, I would expect to see an exception rather than no effect.

---

### Post by PaulM1985 on 2010-04-22
I think I would have the variables copanel, jp and charttype as class variables.  This way you have a definate instance of the objects to manipulate.  Also, I think this would allow the variables to not have to be final.

I would add the actionListeners in the class constructor, rather than in "getter methods".  (This would be ok since the other variables are now class variables).

Instead of having the get methods that you currently have, try changing those so that they set the class variables to the appropriate state, rather than get some value.

---

### Post by features on 2010-04-22
(From memory so a bit scratchy and old skool...)


To detect a change in the selected item in a combo box, use ItemStateChangeListener, not an ActionPerformed listener, otherwise you won't know the new state of the combo.

Make your base panel implement the item state change listener, though you can just do it as an anonymous inner class.  Your choice.

Make your components class members, so they can be referred to at any point in the class.


Add your component to its parent component by calling 
[PHP]
JPanel panelWithStuffInIt = new PanelWithStuffInIt();
parentFrame.add(panelWithStuffInIt)
[/PHP]

in the parent frame.  Here's a very basic sketch of the panel


[PHP]
public class PanelWithStuffInIt extends JPanel, implements ItemStateChangeListener {

    JPanel coPanel;
    JComboBox cccComboBox;
    JLabel tehLabel;
    JTextfield textField;

    public PanelWithStuffInIt() {
        super();
        //do init stuff
        cccComboBox.addItemStateChangeListener(this);
    }

    public void itemStateChange(ItemStateChangedEvent evt){
        //do component swap here
        validate();
   }

}
[/PHP]

---

### Post by SNYP40A1 on 2010-04-22
features, I tried your approach and I have something that works...kinda.  The problem is that now the panel updates, but the enclosing JOptionPane does not resize so the added panel is clipped.  Here's a simpler executable example code:

[PHP]import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

import javax.swing.BoxLayout;
import javax.swing.JComboBox;
import javax.swing.JLabel;
import javax.swing.JOptionPane;
import javax.swing.JPanel;

public class Scratch2 extends JPanel implements ActionListener {
	private JComboBox cbox;
	private JPanel copanel;
	
	public Scratch2()
	{
		setLayout(new BoxLayout(this, BoxLayout.PAGE_AXIS));
		String[] items = { "one", "two", "three" };
		add(new JLabel("Pick a number!"));
		cbox = new JComboBox(items);
		add(cbox);
		cbox.addActionListener(this);
		copanel = new JPanel();
		add(copanel);
		JOptionPane.showConfirmDialog(this, this);
	}

	@Override
	public void actionPerformed(ActionEvent e) {
		String selecteditem = (String) cbox.getSelectedItem();
		System.out.println("You selected the number: " + selecteditem);
		copanel.removeAll();
		copanel.add(new JLabel((String) selecteditem));
		validate();
		this.getParent().validate();
	}
	
	public static void main(String args[])
	{
		new Scratch2();
	}
}[/PHP]

I think the key statement that I was missing earlier was the validate call.  If worst case, I can create a separate JFrame and add the panel to that, then add OK and Cancel buttons.  However, I'd like to use the JDialog frame if possible.  Anyone know how to resize it?  I thought this.getParent().validate() would call a resize / repaint, but no.

---

### Post by features on 2010-04-26
> **SNYP40A1 said:**
> features, I tried your approach and I have something that works...kinda.  The problem is that now the panel updates, but the enclosing JOptionPane does not resize so the added panel is clipped. 

Again here, I'm going from memory, but I think you need to call setBounds on the dialog in order to get it to resize.  I would head over to the Sun site, and take a look at one of their tutorial streams to confirm this though :)

---

