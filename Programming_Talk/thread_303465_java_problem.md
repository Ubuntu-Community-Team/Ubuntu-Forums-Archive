---
title: "java problem"
date: 2006-11-20
forum: Programming Talk
---

### Post by 008325 on 2006-11-20
```

class SlidersPanel extends JPanel implements MouseMotionListener{
	double nx,nhue;
	double nxx = 20;

	public void paint(Graphics g) {
			g.setColor(Color.black);
			g.drawString("HUE:",20,25);
		        int hue_step = 1;
		        float sat = 1;
		        Color c;



		          for (int h=0; h<=360 ;h += hue_step) {
		            float hue = h / 360F;
		            if (hue>=1f) hue = 0f;
		            c = Color.getHSBColor(hue, sat, 1F);
		            g.setColor(c);
					g.fillRect(h+20, 30, 1, 30);



          }
					 g.setColor(Color.black);

					g.drawLine((int)nxx,(int)60,(int)nxx-5,(int)60+5);
					g.drawLine((int)nxx,(int)60,(int)nxx+5,(int)60+5);
					g.drawLine((int)nxx-5,(int)60+5,(int)nxx+5,(int)60+5);


							addMouseMotionListener(this);

	          }

	 		public void mouseMoved(MouseEvent e){

	 			this.setOpaque(false);
	 			this.repaint();



	 			nx  = e.getX();


			if(nx>380){nxx = 380;}
			else if(nx<20){nxx = 20;}
			else{nxx = nx;}

			if(nx>380){nhue = 359;}
			else if(nx<=20){nhue = 0;}
			else{nhue = nx-21;}


			

	 			}
		public void mouseDragged(MouseEvent e){}

	}


public class ABC {
	public static void main(String s[]) {

		JFrame Frame = new JFrame();
		Container c = Frame.getContentPane();
		JPanel TotalPanel = new JPanel();
		TotalPanel.setLayout(null);

		SlidersPanel  sp = new SlidersPanel();
		sp.setBounds(27,230,390,270);
		TotalPanel.add(sp);

		Chart ch = new Chart();
		ch.setBounds(1,-20,380,300);
		TotalPanel.add(ch);

		Rects Rect = new Rects();
		Rect.setBounds(420,-20,130,280);
		TotalPanel.add(Rect);

		c.add(TotalPanel);
		Frame.setSize(720, 420);
		Frame.setVisible(true);

	}
}

```

i got the problem from this code
ABC new all Other Class
i want mouseMoved method to edit Class Chart object
but i can not "New" Chart in this method
you know , the Chart is dependence on ABC class now...

how can i do this ?

thanks

---

### Post by hod139 on 2006-11-20
You don't have a chart class defined anywhere.  You are going to have the same problem when you try to create a new Rects class.  You have to define a class (either local and in the same file or global and in a new file) before you can use it.

---

