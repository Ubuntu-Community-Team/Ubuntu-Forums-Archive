---
title: "Simple Java JFrame Question"
date: 2009-06-14
forum: Programming Talk
---

### Post by SNYP40A1 on 2009-06-14
I have a simple class that I construct to display a frame.  It works, but the frame is only visible when I add a while(3 == 3); statement after setVisible() call below.  What is happening is that the class is constructed quickly and then once the construction is finished, the program terminates and the window is lost.  Besides the while-loop, how can I make the program hold the display until the display window is closed?  Once the user shuts the display window, then the program can terminate.  

[PHP]public class Display extends ApplicationFrame {

	public Display(String title, XYDataset dataset) {
		super(title);
		JFreeChart chart = createChart(dataset);
		ChartPanel chartPanel = new ChartPanel(chart);
		chartPanel.setPreferredSize(new java.awt.Dimension(500, 270));
		chartPanel.setMouseZoomable(true, false);
		setContentPane(chartPanel);
		setPreferredSize(new java.awt.Dimension(500, 270));
		setVisible(true);
	}
...[/PHP]

---

### Post by HotCupOfJava on 2009-06-15
What does your main method say? If it were mine, it might say something like this:

[PHP]public static void main(String args[]){
	Display app = new Display("someTitle", dataset);
	app.addWindowListener(new WindowAdapter(){
		public void windowClosing(WindowEvent we){
			System.exit(0);
		}
	});
}[/PHP]

You could also do this (which is a little safer, where threads are concerned):

[PHP]public static void main(String args[]){
    java.awt.EventQueue.invokeLater(new Runnable(){
        public void run(){
            new Display("someTitle", dataset).setVisible(true);
        }
    });
}[/PHP]

I haven't seen your main method, but I suspect it executes straight through with an exit, which terminates your application immediately after your Display is constructed. It needs to know to wait for Display to be closed before exiting.

---

### Post by froggyswamp on 2009-06-15
The JFrame has nothing to do with your problem, nor the setVisible method. It's a logical/tactical issue with the rest of your code that you didn't post, so people can only second guess what's the actual issue in your case.

---

### Post by SNYP40A1 on 2009-06-15
> **HotCupOfJava said:**
> What does your main method say? If it were mine, it might say something like this:

[PHP]public static void main(String args[]){
	Display app = new Display("someTitle", dataset);
	app.addWindowListener(new WindowAdapter(){
		public void windowClosing(WindowEvent we){
			System.exit(0);
		}
	});
}[/PHP]

You could also do this (which is a little safer, where threads are concerned):

[PHP]public static void main(String args[]){
    java.awt.EventQueue.invokeLater(new Runnable(){
        public void run(){
            new Display("someTitle", dataset).setVisible(true);
        }
    });
}[/PHP]

I haven't seen your main method, but I suspect it executes straight through with an exit, which terminates your application immediately after your Display is constructed. It needs to know to wait for Display to be closed before exiting.

The main method does execute straight though with an exit, which does terminate the application.  So the invokeLater(new Runnable() method spawns off a new thread and does not return until the thread is terminated.  Correct?

---

### Post by C-- on 2009-06-15
> **SNYP40A1 said:**
> The main method does execute straight though with an exit, which does terminate the application.  So the invokeLater(new Runnable() method spawns off a new thread and does not return until the thread is terminated.  Correct?

Yes, the command to set up and run a thread containing the runnable is sent to the event dispatch thread, to be called when available. 

But you shouldn't have to do this!!!

Why are you calling System.exit() at the end of your main method? Let the main method run through to completion and set your JFrame's default close operation to EXIT_ON_CLOSE. Your main thread will end but your GUI thread will continue until you close the window. System.exit() terminates all threads in the process. You should never routinely use System.exit anyway, it's bad form, like a goto statement.

---

### Post by HotCupOfJava on 2009-06-15
> **C-- said:**
>  set your JFrame's default close operation to EXIT_ON_CLOSE. 

This, combined with the second solution I posted, is how NetBeans handles things by default. I feel silly forgetting to mention the static EXIT_ON_CLOSE you can send to setDefaultCloseOperation(int operation). Guess I've still got a lot to learn.

---

### Post by SNYP40A1 on 2009-06-18
Adding invokeLater() or more appropriately invokeAndWait did not fix the problem -- window still gets closed immediately after opening.  The ApplicationFrame is killed as soon as the method returns.  I guess the question to ask what is the difference between the code above and this:

[PHP]import java.awt.BorderLayout;
import javax.swing.*;

public class JFrameTester {
	  public static void main(String[] args) {		    
		    JFrame f = new JFrame("A JFrame");
		    f.setSize(250, 250);
		    f.setLocation(300,200);
		    f.getContentPane().add(BorderLayout.CENTER, new JTextArea(10, 40));
		    f.setVisible(true);		    
		  }
}[/PHP]

That code immediately above also looks like it executes straight-through, but the window is not killed after the last line executes.  The program keeps running until the window is closed.

EDIT:

When I place the code above inside a method of a larger program, the window is immediately closed.  I am actually implementing a method of a larger EC framework (ECJ) and I think what is happening is that after the method returns, all threads are killed.  I tried implementing even this:
[PHP]
    public void finishPopulation(final EvolutionState state, final int result)
    {
    	Runnable runner = new Runnable(){
		    public void run(){
			    JFrame f = new JFrame("A JFrame");
			    f.setSize(250, 250);
			    f.setLocation(300,200);
			    f.getContentPane().add(BorderLayout.CENTER, new JTextArea(10, 40));
			    f.setVisible(true);	
			    f.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		    }
		};		
		Thread displaythread = new Thread(runner);
		displaythread.run();
		try {
			displaythread.join();
		} catch (InterruptedException e1) {
			// TODO Auto-generated catch block
			e1.printStackTrace();
		}
    	    	
//        try {
//	
//			java.awt.EventQueue.invokeAndWait(runner);
//			
//		} catch (InterruptedException e) {
//			// TODO Auto-generated catch block
//			e.printStackTrace();
//		} catch (InvocationTargetException e) {
//			// TODO Auto-generated catch block
//			e.printStackTrace();
//		} 
    }
[/PHP]
But even though I create a new thread for the window, same behavior.  It's immediately closed.  Only thing I can do is put an infinite loop at the end of the method below or slightly better, implement a callback method to not return until the window is closed.

---

### Post by HotCupOfJava on 2009-06-18
I would like to see what the code in your "main" method says....

---

### Post by SNYP40A1 on 2009-06-18
Well, since I am using the ECJ framework ([http://cs.gmu.edu/~eclab/projects/ecj/](http://cs.gmu.edu/~eclab/projects/ecj/)), there's really no main method.  All I did was over-ride a final class that looks like this:

[PHP]
/*
  Copyright 2006 by Sean Luke
  Licensed under the Academic Free License version 3.0
  See the file "LICENSE" for more information
*/


package ec.simple;
import ec.Finisher;
import ec.EvolutionState;
import ec.util.Parameter;

/* 
 * SimpleFinisher.java
 * 
 * Created: Tue Aug 10 21:09:18 1999
 * By: Sean Luke
 */

/**
 * SimpleFinisher is a default Finisher which doesn't do anything.  Most
 * application's don't need Finisher facilities, so this version will work
 * fine.
 *
 * @author Sean Luke
 * @version 1.0 
 */

public class SimpleFinisher extends Finisher
    {

    public void setup(final EvolutionState state, final Parameter base) { }


    /** Doesn't do anything. */
    public void finishPopulation(final EvolutionState state, final int result)
        {
        // don't care
        return;
        }
    }
[/PHP]

The class above is simply called at the end of a run, after final statistics are printed.  All I did was over-ride the public void finishPopulation(...) class, and all I do there, for this case at least, is the code posted above, at this point I am just trying to create a simple empty blank JFrame window and have it stay there until I close it.  For some reason this does not work.  I know ECJ is threaded and so there's probably some method which is used to kill all running threads after the finisher methods return.

---

### Post by SNYP40A1 on 2009-06-19
UPDATE: One of the ECJ authors contacted me and said that the framework calls System.exit(0) right after the method above returns.  System.exit(0) kills all active threads as I suspected.  I'll simply comment out the System.exit(0) in ECJ.

> **SNYP40A1 said:**
> Well, since I am using the ECJ framework ([http://cs.gmu.edu/~eclab/projects/ecj/](http://cs.gmu.edu/~eclab/projects/ecj/)), there's really no main method.  All I did was over-ride a final class that looks like this:

[PHP]
/*
  Copyright 2006 by Sean Luke
  Licensed under the Academic Free License version 3.0
  See the file "LICENSE" for more information
*/


package ec.simple;
import ec.Finisher;
import ec.EvolutionState;
import ec.util.Parameter;

/* 
 * SimpleFinisher.java
 * 
 * Created: Tue Aug 10 21:09:18 1999
 * By: Sean Luke
 */

/**
 * SimpleFinisher is a default Finisher which doesn't do anything.  Most
 * application's don't need Finisher facilities, so this version will work
 * fine.
 *
 * @author Sean Luke
 * @version 1.0 
 */

public class SimpleFinisher extends Finisher
    {

    public void setup(final EvolutionState state, final Parameter base) { }


    /** Doesn't do anything. */
    public void finishPopulation(final EvolutionState state, final int result)
        {
        // don't care
        return;
        }
    }
[/PHP]

The class above is simply called at the end of a run, after final statistics are printed.  All I did was over-ride the public void finishPopulation(...) class, and all I do there, for this case at least, is the code posted above, at this point I am just trying to create a simple empty blank JFrame window and have it stay there until I close it.  For some reason this does not work.  I know ECJ is threaded and so there's probably some method which is used to kill all running threads after the finisher methods return.

---

### Post by HotCupOfJava on 2009-06-22
Well, that explains that............

---

