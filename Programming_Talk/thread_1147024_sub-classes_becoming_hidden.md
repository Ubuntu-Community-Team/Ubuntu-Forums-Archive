---
title: "sub-classes becoming hidden?"
date: 2009-05-03
forum: Programming Talk
---

### Post by mikemcleanuk on 2009-05-03
i have a strange problem it seems that part of my code can no longer see my subclasses however they are functioning fine in other parts of very simular code.

The aim of the code is to load settings from a pre-saved file and create the objects and other things with the infomation.

The 3 sub-classes are functioning fine (last bit of code is an example)

```
if(ae.getSource() == loadButton)
		{
			try
			{
				Scanner fs = new Scanner(new File("livingroom.data"));
				myAppliances.clear();
				
				for(int i = 0; i < 9; i++) 
				{
					appLabels[i].setIcon(blankIcon);
				}
				totalAppCount = 0;
				while(fs.hasNext())
				{
					String appType = fs.next();
					if(appType == "Lamp")
					{					
						Lamp tmpLamp = new Lamp(fs.next());
						myAppliances.add(tmpLamp);
						appLabels[totalAppCount].setIcon(tmpLamp.getPicture());
						totalAppCount++;
						fs.nextLine();
					}
					if(appType == "Television")
					{
						Television tmpTele = new Television(fs.next(), fs.nextInt(), fs.nextInt());
						myAppliances.add(tmpTele);
						appLabels[totalAppCount].setIcon(tmpTele.getPicture());
						totalAppCount++;
						fs.nextLine();
					}
					if(appType == "Clock")
					{
						Clock tmpCloc = new Clock(fs.next(), fs.nextInt(), fs.nextInt(), fs.nextInt());
						myAppliances.add(tmpCloc);
						appLabels[totalAppCount].setIcon(tmpCloc.getPicture());
						totalAppCount++;
						fs.nextLine();
					}
				}
				this.validate();
			}
			catch (FileNotFoundException fnfe)
			{
				JOptionPane.showMessageDialog(null, "Load File not Found - Load Failed", "Error", JOptionPane.ERROR_MESSAGE);
			}
		}
```

```
C:\JPR\ICA3\ICA3\Java>javac TestHomeController.java
.\HomeController.java:258: cannot find symbol
symbol  : constructor Lamp(java.lang.String)
location: class Lamp
                                                Lamp tmpLamp = new Lamp(fs.next());
                                                               ^
.\HomeController.java:266: cannot find symbol
symbol  : constructor Television(java.lang.String,int,int)
location: class Television
                                                Television tmpTele = new Television(fs.next(), fs.ne
xtInt(), fs.nextInt());
                                                                     ^
.\HomeController.java:274: cannot find symbol
symbol  : constructor Clock(java.lang.String,int,int,int)
location: class Clock
                                                Clock tmpCloc = new Clock(fs.next(), fs.nextInt(), f
s.nextInt(), fs.nextInt());
                                                                ^
3 errors
```


```
		if(ae.getSource() == teleAddButton)
		{			
			int chanSelection = Integer.valueOf(chanList.getSelectedItem().toString());
			int volSelection = Integer.valueOf(volList.getSelectedItem().toString());
			
			Television tmpTele = new Television(false, chanSelection, volSelection);
			myAppliances.add(tmpTele);
			appLabels[totalAppCount].setIcon(tmpTele.getPicture());
			totalAppCount++;
			this.validate();
		}

		if(ae.getSource() == clockAddButton)
		{
			int ch = Integer.valueOf(clockHours.getText());
			int cm = Integer.valueOf(clockMinutes.getText());
			int cs = Integer.valueOf(clockSeconds.getText());
			
			Clock tmpCloc = new Clock(false, ch, cm, cs);
			myAppliances.add(tmpCloc);
			
			appLabels[totalAppCount].setIcon(tmpCloc.getPicture());
			totalAppCount++;
			this.validate();
		}
```

---

### Post by baizon on 2009-05-03
The problem seems to that he cant find the constructors for that objects. Are they in the same class?

---

### Post by mikemcleanuk on 2009-05-03
the constructors are in sub-classes

however that i dont understand is it works fine even now when i comment out that one bit of code i can do all sorts of other things with the sub-classes fine

its almost like its embedded to much and cant reach the subclasses!

---

