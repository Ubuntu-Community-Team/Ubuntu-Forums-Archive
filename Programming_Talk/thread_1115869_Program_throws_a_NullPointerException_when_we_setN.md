---
title: "Program throws a NullPointerException when we setNominalViewingTrasform"
date: 2009-04-04
forum: Programming Talk
---

### Post by rmnproject on 2009-04-04
The following code is supposed to create a Cylinder object and add it to the scenegraph. The radius and height for the Cylinder object are provided using a dialog box, so when the input is entered a Cylinder with the set parameters should appear on the canvas. 


```

import javax.swing.*;
import java.awt.event.*;
import java.awt.*;
import java.awt.BorderLayout;
import java.awt.event.ActionListener;
import java.lang.String;
import com.sun.j3d.utils.geometry.Cylinder;
import com.sun.j3d.utils.universe.SimpleUniverse;
import java.awt.BorderLayout;
import java.awt.GraphicsConfiguration;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import javax.media.j3d.Node;
import javax.media.j3d.Appearance;
import javax.media.j3d.BoundingSphere;
import javax.media.j3d.BranchGroup;
import javax.media.j3d.Canvas3D;
import javax.media.j3d.Shape3D;
import javax.media.j3d.Transform3D;
import javax.media.j3d.TransformGroup;
import javax.swing.Timer;
import javax.swing.Icon;
import javax.swing.JDialog;
import javax.swing.JFrame;
import com.sun.j3d.utils.geometry.Cylinder;
import com.sun.j3d.utils.universe.SimpleUniverse;
import java.awt.BorderLayout;
import java.awt.GraphicsConfiguration;
import com.sun.j3d.utils.geometry.Primitive;
 
 
public class Animapp extends JFrame implements ActionListener{
 
	JButton bCyl;
	JPanel pScene,p;
	InputBox ip;
	float rad,hei;
	BranchGroup scene;
	SimpleUniverse su;
	GraphicsConfiguration config;
	Animapp(){
		
		setSize(400,600);
		setLayout(new BorderLayout());
		
		bCyl = new JButton("Cylinder");
		pScene = new JPanel(new BorderLayout());
		
		bCyl.addActionListener(this);
		
		this.add(bCyl,BorderLayout.SOUTH);
		
		
		/*creation of scenegraph*/
		
	      config = SimpleUniverse.getPreferredConfiguration();
		Canvas3D canvas= new Canvas3D(config);
		add("Center",canvas);
		SimpleUniverse su = new SimpleUniverse();
		scene =	createSceneGraph();
		su.addBranchGraph(scene);
		add(canvas, BorderLayout.CENTER);
		
		setVisible(true);
		this.addWindowListener(new WindowAdapter(){ public void windowClosing(WindowEvent e){System.exit(0);}});
		
	}
 
	public static void main(String [] args){
	
		new Animapp();
	
	}
	
	
	public BranchGroup createSceneGraph(){
		
		BranchGroup s = new BranchGroup();
		s.setCapability(BranchGroup.ALLOW_CHILDREN_EXTEND);
		s.setCapability(BranchGroup.ALLOW_CHILDREN_READ);
		s.setCapability(BranchGroup.ALLOW_CHILDREN_WRITE);
		return s;
	
		
	}
 
	public void actionPerformed(ActionEvent event){
		
		if(event.getSource() == bCyl){
			
			InputBox ip = new InputBox(this,"InputBox",true);
			rad = ip.radius;
			hei = ip.height;
			Appearance app = new Appearance();
			
			// Creating a Cylinder object.
			Cylinder cyl = new Cylinder(rad,hei);
			cyl.setAppearance(app);
			BranchGroup cylBg = new BranchGroup();
			
			//Adding the Cylinder object to a Branchgroup and then to the scenegraph
			cylBg.addChild(cyl);
			scene.addChild(cylBg);
			su.getViewingPlatform().setNominalViewingTransform();
			
		}
	
	}
 
}
 
class InputBox extends JDialog implements ActionListener{
 
	JButton okButton,cancel;
	JTextField radText,heightText;
	JLabel radLabel,heightLabel,mssgLabel ;
	public float radius,height;
	
	InputBox(Frame hostFrame, String title, boolean dModal){
		
		super(hostFrame, title, dModal);
		setSize(300,300);
		setLayout(new FlowLayout());
		
		mssgLabel = new JLabel("Enter the values for radius and height:",JLabel.CENTER);
		add(mssgLabel);
		radLabel = new JLabel("Radius:",JLabel.LEFT);
		add(radLabel);
		radText = new JTextField(10);
		add(radText);
		heightLabel = new JLabel("Height:",JLabel.LEFT);
		add(heightLabel);
		heightText = new JTextField(10);
		add(heightText);
		okButton = new JButton("OK");
		add(okButton);
		cancel = new JButton("Cancel");
		add(cancel);
		okButton.addActionListener(this);
		pack();
      
        setVisible(true);
	
	}
	
	public void actionPerformed(ActionEvent ae){
		
		if(ae.getSource() == okButton){
		
			radius = java.lang.Float.parseFloat(radText.getText());
			height = java.lang.Float.parseFloat(heightText.getText());
			
		}
		setVisible(false);
	
	}
		
}



```



But when i run this code it throws the following exception.


Exception in thread "AWT-EventQueue-0" java.lang.NullPointerException
at Animapp.actionPerformed(Animapp.java:106)
at javax.swing.AbstractButton.fireActionPerformed(AbstractButton.java:1995)
at javax.swing.AbstractButton$Handler.actionPerformed(AbstractButton.java:2318)
at javax.swing.DefaultButtonModel.fireActionPerformed(DefaultButtonModel.java:387)
at javax.swing.DefaultButtonModel.setPressed(DefaultButtonModel.java:242)
at javax.swing.plaf.basic.BasicButtonListener.mouseReleased(BasicButtonListener.java:236)
at java.awt.Component.processMouseEvent(Component.java:6216)
at javax.swing.JComponent.processMouseEvent(JComponent.java:3265)
at java.awt.Component.processEvent(Component.java:5981)
at java.awt.Container.processEvent(Container.java:2041)
at java.awt.Component.dispatchEventImpl(Component.java:4583)
at java.awt.Container.dispatchEventImpl(Container.java:2099)
at java.awt.Component.dispatchEvent(Component.java:4413)
at java.awt.LightweightDispatcher.retargetMouseEvent(Container.java:4556)
at java.awt.LightweightDispatcher.processMouseEvent(Container.java:4220)
at java.awt.LightweightDispatcher.dispatchEvent(Container.java:4150)
at java.awt.Container.dispatchEventImpl(Container.java:2085)
at java.awt.Window.dispatchEventImpl(Window.java:2475)
at java.awt.Component.dispatchEvent(Component.java:4413)
at java.awt.EventQueue.dispatchEvent(EventQueue.java:599)
at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:269)
at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:184)
at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:174)
at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:169)
at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:161)
at java.awt.EventDispatchThread.run(EventDispatchThread.java:122)


any idea what i'm doing wrong?

---

### Post by Arndt on 2009-04-04
> **rmnproject said:**
> 
But when i run this code it throws the following exception.


Exception in thread "AWT-EventQueue-0" java.lang.NullPointerException
at Animapp.actionPerformed(Animapp.java:106)
at javax.swing.AbstractButton.fireActionPerformed(AbstractButton.java:1995)
at javax.swing.AbstractButton$Handler.actionPerformed(AbstractButton.java:2318)
at javax.swing.DefaultButtonModel.fireActionPerformed(DefaultButtonModel.java:387)
...



any idea what i'm doing wrong?


The error message seems to indicate that 'su' is not initialized. This line
	```

         SimpleUniverse su = new SimpleUniverse();
```

seems to shadow the attribute 'su' of the class. What if you do

```

         su = new SimpleUniverse();
```

instead?

---

### Post by rmnproject on 2009-04-04
Thanks, that resolves the null exception ... now the application is running but it's not displaying the cylinder...there's just a black screen where the canvas is supposed to be.

cross posted at:
[http://forums.sun.com/thread.jspa?threadID=5378445&tstart=0](http://forums.sun.com/thread.jspa?threadID=5378445&tstart=0)

[http://www.coderanch.com/t/439526/Swing-AWT-SWT-JFace/java/Program-throws-NullPointerException-when-we#1954547](http://www.coderanch.com/t/439526/Swing-AWT-SWT-JFace/java/Program-throws-NullPointerException-when-we#1954547)

Hi,


It seems there was some problem with my Java3D installation. I uninstalled and reinstalled Java3D and now the same code is working fine. Thanks for your time and sorry for this post.

---

