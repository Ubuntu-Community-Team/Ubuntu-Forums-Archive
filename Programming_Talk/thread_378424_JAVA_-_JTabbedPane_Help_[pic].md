---
title: "JAVA - JTabbedPane Help [pic]"
date: 2007-03-07
forum: Programming Talk
---

### Post by serlex on 2007-03-07
Got a little java problem, cant seem to figure it out.

I wanna point a JMenuItem to one of the tabs, so when i click the MenuItem the tab is selected.

screenshot

---

### Post by hod139 on 2007-03-07
Look into the Model-View-Controller (MVC) GUI design strategy.   Selecting a menu item will trigger an event processed by the controller which updates the model, and the view renders the updated model.

---

### Post by laxmanb on 2007-03-07
Add an ActionListener to JMenuItem(It is a type of button after all) ... when clicked do a requestFocus() on the component in the Tab...

---

### Post by serlex on 2007-03-07
Thx for reply


I did ```
	 int sel = tabbs.getSelectedIndex() + 3;
			 if(sel>=0)
			 tabbs.setSelectedIndex(sel);
```

which did what i wanted it to do, when i click it 'New Customer' is selected'. But its not pointing at that tab, its pointing at tab number 4 (0,1,2,3), so if there were more tabs it would move on to tab number 8

better way of doing this? :)

---

### Post by laxmanb on 2007-03-07
why are you adding 3 to the getSelectedIndex()??

---

### Post by serlex on 2007-03-07
Well I havent figured out any other way of using it! I thought u could specify a tab by its name, can someone give me an example

Here is my code
```

JMenuItem addCustomer = new JMenuItem("Add Customer",new ImageIcon("plus.gif"));
addCustomer.setMnemonic('A');
jmi1.add(addCustomer);

JPanel new_panel = new JPanel(); //create details panel
tabbs.addTab("New Customer",null,new_panel,"New Customer");

				addCustomer.addActionListener(
					new ActionListener()
					{
					  public void actionPerformed(ActionEvent event)
					  {
                                          ??????????
					  }
	  				});

```

---

