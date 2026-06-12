---
title: "Need help with my Java game"
date: 2008-06-16
forum: Programming Talk
---

### Post by Despot Despondency on 2008-06-16
Hey. I'm writing a version of risk with java and I'm at a stage where some different ideas would be helpful. 

I want a map of the world split up into the various countries and then to have a button for each country. At the moment I've cut up my map with GIMP and then I'm loading each country as a JLabel. 

```

for(Iterator j = countries.iterator(); j.hasNext();)
{
 	Country country = (Country)j.next();
 	String country_name = country.toString();
 
	ImageIcon image = new ImageIcon(GameMap.class.getResource("images/countries/" + colour + "/" + country_name + ".png"));

	JLabel label = new JLabel(image);

	Countries.put(country_name, label);
        backgroundPanel.add(label, gbc);
}

```


This works fine, but now I'm having difficulty with the buttons, especially positioning. I would ideally like to be able to create each button in the above loop and then just and it to the JLabel, so that it's positioned over the picture of the country, but I can't add JButtons to JLabels. 

Can someone suggest any ideas for this problem?

---

### Post by mike_g on 2008-06-16
I'm pretty sure you can't add buttons to a JLabel as its not a container. Maybe you could set the image to background of the button and get rid of the JLabels? Or would that not work?

---

### Post by Despot Despondency on 2008-06-16
Hey, thanks for your reply. That's what I thought about add JButtons to JLabels. I tried your solution and it works fine. Thanks again. I tried this solution before but didn't know how to get rid of the background then, which I've done now, so it didn't really work. 

Other suggestions for this problem would still be appreciated. Would ideally like the situation where the button is inside the image of the country, rather than the whole country itself. 

Thanks again for your solution, I can carry on with the rest of the game now. :)

---

### Post by Aeph on 2008-06-16
You might be able to try JPanels.

---

### Post by themusicwave on 2008-06-16
Normally when you want to group some GUI items together you would use a JPanel to do it.JPanels can contain pretty much any other GUI item, including other Jpanels.

The other nice thing about JPanels, is that you can move the whole panel around.  So once you have the items placed properly in the individual JPanels, then you place the Panels in your JFrame.

Typically, that is how GUIs tend to be created in Java.

---

### Post by Despot Despondency on 2008-06-16
Unfortunately, having tested it out a bit,  the button solution doesn't really seem to be working. Because I set the background of the buttons to transparent it looks like the buttons are the right shape, but in actual fact all the buttons on top of one another. For example, when I press the 'Brazil' button I'm actually pressing the button for some other country. Thinking about trying to reshape the buttons to the shape of the image? Or is there a way to set the background of a JButton inactive?

With regard to the JPanel suggestion, should I go about that? Is there a way that I can make each Jpanel the shape of the ImageIcon?

---

### Post by NormR2 on 2008-06-16
> **mike_g said:**
> I'm pretty sure you can't add buttons to a JLabel as its not a container. 
??
My API doc shows JLabel extends JComponent which extends Container.

---

### Post by NormR2 on 2008-06-16
> but in actual fact all the buttons on top of one another. For example, when I press the 'Brazil' button I'm actually pressing the button for some other country.

Not sure what you mean by "on top of one another". Is each button added to a separate component or to the same component? 

You need to post your code so we can see what you have coded.

---

### Post by Despot Despondency on 2008-06-16
Of course. Here it is. This method creates the frame and adds the backgroundPanel, which is going to be the map.

```

private static void createAndShowMAP(){
        frame = new JFrame("Risk");		
		
	FrameUtil.setUp(frame);
        
        ImageIcon Outline = new ImageIcon(GameMap.class.getResource("images/countries/outline.png"));
        ImageIcon Sea = new ImageIcon(GameMap.class.getResource("images/countries/sea.png"));
        
        JLabel outline = new JLabel(Outline);
        JLabel sea = new JLabel(Sea);
       
        backgroundPanel.add(outline, gbc);
        backgroundPanel.add(sea, gbc);
        
	frame.setContentPane(backgroundPanel);
        
    }

```

I then call the method paintNation(Nations nations) to colour the countries different colours for different nations

```

public void paintCountries(Nations n){
    	
   Set nations = n.entrySet();
   Set colours = n.keySet();
   Iterator col_it = colours.iterator();
    	
   for(Iterator i = nations.iterator(); i.hasNext(); )
   {
   	String colour = (String)col_it.next();
   		
        Map.Entry me1 = (Map.Entry)i.next();
	Nation nation = (Nation)me1.getValue();
	Set countries = nation.keySet();
    		
	for(Iterator j = countries.iterator(); j.hasNext();)
	{
		Country country = (Country)j.next();
		String country_name = country.toString();
    			
		ImageIcon image = new ImageIcon(GameMap.class.getResource("images/countries/" + colour + "/" + country_name + ".png"));
	        JButton button = new JButton(image);

	        button.setContentAreaFilled(false);
	        button.addActionListener(this);

	        Countries.put(country_name, button);
	        backgroundPanel.add(button, gbc);
	}
     }
    	
    frame.setVisible(true);	
}

```

I had with JLabels in the previous post, but at present I'm using JButtons.  The map looks fine but when I wrote a test the bring up the country name for each button, I got random results like the buttons are overlapping. I think one of the problems might be because the image files are the size of the map, but mostly transparent, so each button is that size. I could cut them down, but it's good to be able to load the countries into their correct positions easily, which this allows me to do.

---

### Post by jspolen on 2008-06-16
Maybe it's possible to implement the *mouselistener* interface, and make it look for a valid "clicking area" by checking the x and y coordinates.

---

### Post by NormR2 on 2008-06-16
I'm not sure I understand your problem. Without a working program it's hard to see what's happening.

---

### Post by mike_g on 2008-06-16
> My API doc shows JLabel extends JComponent which extends Container.
Oh maybe it does then.

**Despot Despondency:** it sounds like you're making a risk (or similar game. If so I think the easiest way to go about it would be to ditch the GUI components for each country. 

Instead you could have a background drawn to a graphics buffer. You could have a duplicate stencil like copy of the map with a different colour for each country. You can then map the mouse co-ords to a position on the stencil, read the pixels colour and find what country the mouse is over. 

It would be pretty much a total rework, but tbh I dont think GUIs were really built for this sort of thing. 

Cheers

---

