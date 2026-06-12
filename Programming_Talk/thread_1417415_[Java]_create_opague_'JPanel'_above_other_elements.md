---
title: "[Java] create opague 'JPanel' above other elements?"
date: 2010-02-27
forum: Programming Talk
---

### Post by SpinningAround on 2010-02-27
I have a JFrame that uses BorderLayout (West,Center,North is used), what I would like to create is a overlay that cover the entire JFrame. So when a certain requirement is meet will the window gray out. Something similar to what is shown in the attachment (gray layer above).

---

### Post by kahumba on 2010-02-27
JFrame has a special component for this, it's called the "Glass pane":
[http://java.sun.com/docs/books/tutorial/uiswing/components/rootpane.html](http://java.sun.com/docs/books/tutorial/uiswing/components/rootpane.html)

but, it took me quite a while to get it to work the way I wanted, maybe you'll have a better time getting used to it.

---

### Post by Reiger on 2010-02-27
If all you want to do is mark the frame as &#8220;disabled&#8221; then myJFrameObject.setEnabled(false); ought to work just fine.

---

### Post by SpinningAround on 2010-02-28
Thanks, I got it to some extent working using the glass pane. I realized that I was looking more for transparent/translucent, glass pane manage to do this also but there is one problem. When I use translucent Color(int r, int b, int g, int a) and repaint command does the program add layer upon layer that remove the translucent effect after a few repaints, question is how to make it refresh itself instead of painting a new above the latest?


[PHP]
    public void inactive() throws InterruptedException{
	  //setup glass pane
        JPanel glass = (JPanel) mainFrame.getGlassPane();
        Color colorA = new Color(200,200,200,200);
        glass.setLayout(new GridLayout(0,1));
        glass.setOpaque(true);
        glass.setBackground(colorA);
        
	  //create a JTextArea to write message in
        JTextArea inactive = new JTextArea("Program inactive, will restart after countdown.");
        inactive.setForeground(Color.red);
        inactive.setEditable(false);
        inactive.setLineWrap(true);
        inactive.setWrapStyleWord(true);
        inactive.setOpaque(false);
        
	  //JLabel to contain countdown
        JLabel inactiveCountdown = new JLabel("Time left:");
        inactiveCountdown.setForeground(Color.red);

	  //finalize frame
        glass.add(inactive);
        glass.add(inactiveCountdown);
        glass.setVisible(true);

	  //initiate countdown
        Calendar DATE = Calendar.getInstance();
        int hour = DATE.get(Calendar.HOUR_OF_DAY),thishour=hour;
	
	  //start countdown, exit when finished
        while(thishour==hour){
            DATE = Calendar.getInstance();
            inactiveCountdown.setText("Time left: " +
            Integer.toString( 59-DATE.get(Calendar.MINUTE) ) + "min " + Integer.toString( 59-DATE.get(Calendar.SECOND) ) + "s" ) );
            thishour = DATE.get(Calendar.HOUR_OF_DAY);
            mainFrame.repaint();
            Thread.currentThread().sleep(1000);
        }
        glass.setVisible(false);
        mainFrame.repaint();
    } 
[/PHP]

---

### Post by kahumba on 2010-02-28
A example of what you're doing that compiles and runs would be great.
The way I implemented my solution didn't require tinkering with the alpha bits, I've overriden glasspane's paintComponent method and used AlphaComposite to draw the contents of the content pane upon the glasspane which creates the illusion of transparency and then draw normally anything that belongs to the glasspane, thus it looks like the glasspane (with a red label up and a textfield a button one line below) is in front with anything else faded away in the background.
I don't know if I make myself clear or if I understood your correctly.

```

@Override
    public void paintComponent(Graphics gr) {
        if(gr == null) {
            return;
        }

        if(!inited) {
            inited = true;
            initComponents();
        }

        Main.itself().getContentPane().paint(gr);
        Graphics2D g = (Graphics2D)gr;
        g.setRenderingHint(RenderingHints.KEY_ANTIALIASING, RenderingHints.VALUE_ANTIALIAS_ON);
        g.setComposite(AlphaComposite.getInstance(AlphaComposite.SRC_OVER, 0.6f));
        g.setColor(Color.white);
        int w = getWidth(), h = getHeight();
        g.fillRect(0,0,w,h);

        g.setColor(Color.red);
        g.setFont(new Font(Font.DIALOG, Font.PLAIN, 18));
        g.setComposite(AlphaComposite.getInstance(AlphaComposite.SRC_OVER, 1f));
        String s = "&#1055;&#1086;&#1080;&#1089;&#1082;:";

        FontMetrics fm = g.getFontMetrics();
        int msg_width = fm.stringWidth(s);
        int msg_x = getSize().width / 2 - msg_width / 2;
        g.drawString (s, msg_x, startY-ygap);

    }

```

---

### Post by SpinningAround on 2010-03-01
It solved it :) But for some wired reason don't the glass pane cover the entire frame.

[PHP]
import java.awt.*;
import javax.swing.*;
public class Test extends JFrame{
	JPanel glass = (JPanel) getGlassPane();
	public Test(){
		setVisible(true);
		setSize(new Dimension(200,300));
		JLabel a = new JLabel("a");
		add(a);
		Container cp = getContentPane();
		cp.setBackground(Color.green);

		JLabel c = new JLabel("RED");
		c.setForeground(Color.red);
		glass.add(c);
		
		JTextField d = new JTextField("d",5);
		glass.add(d);
	}

	public void paint(Graphics g){
		super.paint(g);
		glass.setVisible(true);
		Graphics2D g2d = (Graphics2D) g;
		AlphaComposite newComposite = AlphaComposite.getInstance(AlphaComposite.SRC_OVER, .7f);
		g2d.setRenderingHint(RenderingHints.KEY_ANTIALIASING, RenderingHints.VALUE_ANTIALIAS_ON);
		g2d.setComposite(newComposite);
		g2d.setColor(Color.white);
		g2d.fillRect(0,0,glass.getWidth(),glass.getHeight());
		
		newComposite = AlphaComposite.getInstance(AlphaComposite.SRC_OVER, 1f);
		g2d.setComposite(newComposite);
		g2d.drawString("Sunshine",50,100);

	}

	public static void main (String args[]) {		
		Test b = new Test();
		b.repaint();
	}
}
[/PHP]

---

### Post by kahumba on 2010-03-01
If you wanna live a long happy life better put the glass pane code into a new class:

Test.java (the JFrame)
[PHP]
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import javax.swing.*;

public class Test extends JFrame implements ActionListener {

    public Test() {
        setGlassPane(new MyGlass(getContentPane()));

        Container cp = getContentPane();
        cp.setLayout(new BoxLayout(cp, BoxLayout.PAGE_AXIS));
        cp.setBackground(Color.green);

        cp.add(new JLabel("Content pane Label"));
        cp.add(Box.createVerticalStrut(20));
        
        JLabel label = new JLabel("Content pane Red Label");
        label.setForeground(Color.red);
        cp.add(label);
        cp.add(Box.createVerticalStrut(20));

        JButton btn = new JButton("ContentPane button (enables glass pane)");
        btn.addActionListener(this);
        cp.add(btn);

        setDefaultCloseOperation(EXIT_ON_CLOSE);
        setSize(new Dimension(400, 300));
        setVisible(true);
    }

    public static void main(String args[]) {
        new Test();
    }

    public void actionPerformed(ActionEvent ae) {
        getGlassPane().setVisible(true);
    }
}
[/PHP]MyGlass.java (The glass pane)
[PHP]

import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import javax.swing.*;

public class MyGlass extends JPanel implements ActionListener {
    private Container contentPane;
    private boolean inited;
    JPasswordField pass;

    public MyGlass(Container contentPane) {
        this.contentPane = contentPane;
        setLayout(null);

    }

    private void init() {
        inited = true;
        //let's have some fun, ask for a password
        JLabel label = new JLabel("(glass pane JLabel) Enter password and hit enter:");
        label.setForeground(Color.blue);
        add(label);
        label.setBounds(40, getHeight()/2, 350, 20);

        pass = new JPasswordField("password");
        add(pass);
        pass.addActionListener(this);
        pass.setBounds(40, getHeight()/2+20, 250, 20);
        pass.requestFocus();
    }

    @Override
    public void paintComponent(Graphics gr) {
        super.paintComponent(gr);//makes sure MyGlass's widgets are drawn automatically
        
        if(!inited) {
            init();
        }

        Graphics2D g = (Graphics2D) gr;
        //create (fake) transparency
        AlphaComposite transparent = AlphaComposite.getInstance(AlphaComposite.SRC_OVER, .7f);
        g.setRenderingHint(RenderingHints.KEY_ANTIALIASING, RenderingHints.VALUE_ANTIALIAS_ON);
        g.setComposite(transparent);
        //draw the contents of the JFrame's content pane upon our glass pane.
        contentPane.paint(gr);
        g.setColor(Color.white);
        g.fillRect(0, 0, getWidth(), getHeight());

        AlphaComposite solid = AlphaComposite.getInstance(AlphaComposite.SRC_OVER, 1f);
        g.setComposite(solid);
        g.setColor(Color.black);
        g.drawString("Glass pane string", 50, 100);
        g.drawString("which is drawn manually!", 50, 120);
    }

    public void actionPerformed(ActionEvent ae) {
        setVisible(false);
    }
}
[/PHP]

---

### Post by SpinningAround on 2010-03-01
wow, thanks :D

---

