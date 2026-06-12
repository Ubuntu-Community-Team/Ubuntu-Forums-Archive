---
title: "NullPointerException"
date: 2009-05-01
forum: Programming Talk
---

### Post by rmnproject on 2009-05-01
I can't figure out the reason for this NullPointerException . Please help.The code involves use Java3D API.
Here's the code:

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
import javax.media.j3d.*;
import javax.vecmath.*;
import javax.vecmath.Point3d;
import com.sun.j3d.utils.behaviors.vp.*;   
import com.sun.j3d.utils.universe.*;
import com.sun.j3d.utils.behaviors.vp.OrbitBehavior;
import com.sun.j3d.utils.picking.PickTool;
import com.sun.j3d.utils.picking.PickCanvas;
import com.sun.j3d.utils.picking.PickResult;
import com.sun.j3d.utils.picking.behaviors.PickMouseBehavior;



public class Animapp1 extends JFrame implements ActionListener{

	JButton bCyl, bSelect;
	JPanel pScene,p;
	InputBox ip;
	float rad,hei;
	BranchGroup scene;
	SimpleUniverse su;
	GraphicsConfiguration config;
	BoundingSphere bounds = new BoundingSphere(new Point3d(0.0, 0.0, 0.0), 1000.0);	
	OrbitBehavior orbit;
	MyPickMouseBehavior pick;
	Canvas3D canvas;
	
	boolean select = false;//indicates whether the application is in selection mode
	Animapp1(){
		
		setSize(400,600);
		setLayout(new BorderLayout());
		pScene = new JPanel(new FlowLayout());
		
		bCyl = new JButton("Cylinder");
		bCyl.addActionListener(this);
		pScene.add(bCyl);
		
		bSelect = new JButton("Select");
		bSelect.addActionListener(this);
		pScene.add(bSelect);
		this.add(pScene,BorderLayout.SOUTH);
		/*creation of scenegraph*/
		
		config = SimpleUniverse.getPreferredConfiguration();
		canvas= new Canvas3D(config);
		canvas.setSize(300,300);
		su = new SimpleUniverse(canvas);
		add("Center",canvas);
		
		/* creating mousepickbehavior object*/
	
		pick = new MyPickMouseBehavior(canvas,scene,(Bounds)bounds);
		pick.setEnable(false);
	
		
		scene =	createSceneGraph();
		
		scene.addChild(pick);
		
		su.addBranchGraph(scene);
		scene.setUserData("scene");
		setupView();
		



		setVisible(true);
		this.addWindowListener(new WindowAdapter(){ public void windowClosing(WindowEvent e){System.exit(0);}});
		
	}

	public static void main(String [] args){
		
			new Animapp1();
	
	}
	
	
	public BranchGroup createSceneGraph(){
		
		BranchGroup s = new BranchGroup();
		s.setCapability(BranchGroup.ALLOW_CHILDREN_EXTEND);
		s.setCapability(BranchGroup.ALLOW_CHILDREN_READ);
		s.setCapability(BranchGroup.ALLOW_CHILDREN_WRITE);
		s.setCapability(BranchGroup.ENABLE_PICK_REPORTING);
		
		
		return s;
	
		
	}
	
	public void setupView() {
         /** Add some view related things to view branch side
         of scene graph */
         // add mouse interaction to the ViewingPlatform
		
        orbit = new OrbitBehavior(canvas,
                 OrbitBehavior.REVERSE_ALL|OrbitBehavior.STOP_ZOOM|OrbitBehavior.PROPORTIONAL_ZOOM);
        orbit.setSchedulingBounds(bounds);
		//orbit.setZoomEnable(true);
         ViewingPlatform viewingPlatform = su.getViewingPlatform();
         // This will move the ViewPlatform back a bit so the
         // objects in the scene can be viewed.
         viewingPlatform.setNominalViewingTransform();
         viewingPlatform.setViewPlatformBehavior(orbit);       

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
			cyl.setUserData("cyl");
			BranchGroup cylBg = new BranchGroup();
			cylBg.setUserData("cylBg");
	Transform3D tRotX = new Transform3D();//Try and reuse Transform3D objects if possible: to reduce memory burn
	Transform3D tRotY = new Transform3D();
	Transform3D tRotZ = new Transform3D();
	Transform3D tTltY = new Transform3D();

	tRotX.rotX(Math.PI*0.25d);
	tRotY.rotY(Math.PI*0.25d);
	tRotZ.rotZ(Math.PI*0.25d);
	tTltY.set(new Vector3f(0.0f,0.4f,0.0f));

	TransformGroup TGX = new TransformGroup(tRotX);
	TransformGroup TGY = new TransformGroup(tRotY);
	TransformGroup TGZ = new TransformGroup(tRotZ);
	//TGX.setCapability(TransformGroup.ALLOW_CHILDREN_EXTEND);

	TGX.setCapability(TransformGroup.ALLOW_CHILDREN_READ);
	TGX.setCapability(TransformGroup.ALLOW_CHILDREN_WRITE);
	TGY.setCapability(TransformGroup.ALLOW_CHILDREN_READ);
	TGY.setCapability(TransformGroup.ALLOW_CHILDREN_WRITE);
	TGZ.setCapability(TransformGroup.ALLOW_CHILDREN_READ);
	TGZ.setCapability(TransformGroup.ALLOW_CHILDREN_WRITE);


		//Adding the Cylinder object to a TransformGroup and then to the Scene part of the SceneGraph
	
	TGX.addChild(cyl);
	TGY.addChild(TGX);
	TGZ.addChild(TGY);
	

	cylBg.addChild(TGZ);

	TGX.setUserData("TGX");
	TGY.setUserData("TGY");
	TGZ.setUserData("TGZ");
			
			scene.addChild(cylBg);
			//su.getViewingPlatform().setNominalViewingTransform();
				
		}
	

	if (event.getSource()== bSelect){

		orbit.setEnable(false);
		select = true;
		
		pick.setEnable(true);

				
		

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


class MyPickMouseBehavior extends PickMouseBehavior{

	//public PickResult pickResult = null;

	MyPickMouseBehavior(Canvas3D canvas, BranchGroup bg, Bounds bounds){
		
		super(canvas,bg,bounds);
		setSchedulingBounds(bounds);
		pickCanvas.setMode(PickTool.GEOMETRY_INTERSECT_INFO);
	}
	
	public void updateScene(int xpos, int ypos){

		pickCanvas.setShapeLocation(xpos,ypos);
		Point3d eyePos = pickCanvas.getStartPosition();
		PickResult pickResult = null;
		pickResult = pickCanvas.pickClosest();
		SceneGraphPath path = pickResult.getSceneGraphPath();
		int pathLen = path.nodeCount();
		for(int i = 0; i<pathLen;i++){
			Node node = path.getNode(i);
			String u = (String) node.getUserData();
			System.out.println(i +":Node Name - "+ u );	
		}
		

	}	

}



Here's the exception it's throwing:

Exception in thread "main" java.lang.NullPointerException
	at com.sun.j3d.utils.picking.behaviors.PickMouseBehavior.<init>(PickMouseBehavior.java:78)
	at MyPickMouseBehavior.<init>(Animapp1.java:267)
	at Animapp1.<init>(Animapp1.java:82)
	at Animapp1.main(Animapp1.java:104)

---

### Post by Arndt on 2009-05-01
> **rmnproject said:**
> I can't figure out the reason for this NullPointerException . Please help.The code involves use Java3D API.



Here's the exception it's throwing:

Exception in thread "main" java.lang.NullPointerException
	at com.sun.j3d.utils.picking.behaviors.PickMouseBehavior.<init>(PickMouseBehavior.java:78)
	at MyPickMouseBehavior.<init>(Animapp1.java:267)
	at Animapp1.<init>(Animapp1.java:82)
	at Animapp1.main(Animapp1.java:104)

Maybe this is the problem:

```

		pick = new MyPickMouseBehavior(canvas,scene,(Bounds)bounds);
		pick.setEnable(false);
	
		
		scene =	createSceneGraph();

```

You use 'scene' before you create it.

---

### Post by rmnproject on 2009-05-01
Oh yeah..Thanks so much :)

---

