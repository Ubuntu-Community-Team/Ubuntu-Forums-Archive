---
title: "Java Thread"
date: 2010-01-22
forum: Programming Talk
---

### Post by dvlchd3 on 2010-01-22
Hello all.  I'm a Computer Science student, and work as an IT help desk operator.  To make my job slightly easier, I wrote a Java application that provided a graphical way to ping access points within different company locations.

To accomplish the pinging, I created a seperate thread so the GUI didn't appear to "hang" while the APs were being pinged.  I've attached the code for my "PingThread".  Let me know if anything is unclear, I attempted to provide as many comments as I could without cluttering the code, and revealing too much information about our network.

I've noticed when the application is not pinging anything (just waiting for the user to choose which location/blocks to ping), it consumes 40-50% of my CPU resources.  Considering the application should essentially be idle, I believe the only reason this is happening is due to my infinite loop that is essentially do nothing. Is there a better way to handle threads in Java?  Should I just use the suspend method even though it is depreciated?

Please keep in mind, my experience with GUI programming and threading is extremely limited.  In fact, this project is the first I ever had the motivation or success with either.

PingThread.java
```

/************************************************************************
 * PingThread - the thread used when pinging the APs					*
 * 																		*
 * Author: Dan Buhrman													*
 * Date: 12/15/2009														*
 * Last Updated: 12/17/2009												*
 * 																		*
 * Copyright 2009, World Kitchen, LLC									*
 ************************************************************************/
import javax.swing.JOptionPane;
import javax.swing.SwingUtilities;
//import javax.swing.JFrame;

import java.lang.reflect.InvocationTargetException;
import java.util.Vector;
import com.worldkitchen.ping.resources.*;


public class PingThread extends Thread {
	boolean isPinging;	// when to actually utilize this thread
	PingPanel pnl;		// the JPanel to update with ping results
	Vector<AP> APs;		// Vector containing the APs to ping
	Vector<AP> errors;	// APs who did not respond
	GUI gui;			// the main class containing the Frame
	
	public PingThread(PingPanel pnl, GUI gui) {
		super();
		isPinging=false;
		this.pnl = pnl;
		APs = new Vector<AP>();
		errors = new Vector<AP>();
		this.gui = gui;
	}
	
	/************************************************
	 * run() - run the thread.						*
	 * 												*
	 * Precondition: 'APs' contains the APs to ping	*
	 * Postcondition: All APs within 'APs' are		*
	 * 	pinged, and the results printed to PingPanel*
	 ************************************************/
	public void run() {
		// Enter infinite loop.
		for(; ;) {
			if(isPinging) {	// If the thread is supposed to do something.
				SwingUtilities.invokeLater(new Runnable() {
					public void run() {
						pnl.setEnabledCancelButton(true);
					}
				});
				if(APs.size() > 0) {
					try {
						ping(APs.get(0));
						if(isPinging) {
							APs.remove(0);
							pnl.updateScrollBar();
						}
					} catch(InterruptedException e) {
						e.printStackTrace();
					} catch(InvocationTargetException e) {
						e.printStackTrace();
					}
				} else {
					// Print errors if they exist.
					if(errors.size() > 0) {
						SwingUtilities.invokeLater(new Runnable() {
							public void run() {
								String message = "<html>The following APs failed to respond:<br>";
								message += (errors.toString());
								JOptionPane.showMessageDialog(gui.getFrame(), message);
							}
						});
					}
					// Reset everything for next run.
					
					isPinging=false;
					SwingUtilities.invokeLater(new Runnable() {
						public void run() {
							APs = new Vector<AP>();
							gui.cancelPinging();
						}
					});
				}
			}
		}
	}
	
	/********************************************************************
	 * ping() - ping an AP.												*
	 * 																	*
	 * This essentially pings the AP given ('a') and prints the results	*
	 * to PingPanel through the event dispatching thread.				*
	 * 																	*
	 * Precondition: 'a' contains the AP to ping.						*
	 * Postcondition: AP is pinged, and results printed to PingPanel.	*
	 * @param a	- AP to ping.											*
	 ********************************************************************/
	private void ping(final AP a) throws InterruptedException, InvocationTargetException {
		if(!isPinging) return;
		int count=0;
		// Print initial message on the event dispatching thread.
		SwingUtilities.invokeAndWait(new Runnable() {
			public void run() {
				pnl.updateStatus("Pinging AP " + a.getNumber() + "<br>");
				pnl.updateScrollBar();
			}
		});
		if(!isPinging) return;
		// Loop until a.ping returns true, or count is 3.
		while(count < 3 && !a.ping()) {
			if(count < 2) {	// If the first 2 attempts fail.
				// Print failure message on event dispatching thread.
				SwingUtilities.invokeAndWait(new Runnable() {
					public void run() {
						pnl.updateStatus("AP " + a.getNumber() +
								" did not reply. Trying again.<br>");
						pnl.updateScrollBar();
					}
				});
				count++;
				if(!isPinging) return;
			} else {
				// Print total failure message on event dispatching thread.
				// and add to errors array
				SwingUtilities.invokeAndWait(new Runnable() {
					public void run() {
						pnl.updateStatus("AP " + a.getNumber() +
								" did not respond 3 times.<br>");
						pnl.updateScrollBar();
					}
				});
				count++;	// Increment the counter
				return;		// Break from the function.
			}
		}
		// If we reached this point, the AP responded.
		// Print the success message on the event dispatching thread.
		if(!isPinging) return;
		SwingUtilities.invokeAndWait(new Runnable() {
			public void run() {
				pnl.updateStatus("AP " + a.getNumber() +
						" responded.<br>");
				pnl.updateScrollBar();
			}
		});
	}
	
	public void setAPs(Vector<AP> APs) {
		this.APs = APs;
	}
	
	public void startPinging() { isPinging=true; }
}

```

---

### Post by Some Penguin on 2010-01-22
There are better ways to implement this than polling.  Typically, these use constructs which allow a thread to indicate that it wants to sleep until it's woken up by a certain event.

In this particular case, you could look at, say, wait/notify.  See
[http://www.java-samples.com/showtutorial.php?tutorialid=306](http://www.java-samples.com/showtutorial.php?tutorialid=306)
for instance.

Another solution would be to not have the pinging thread exist at all, normally, and to have its creation / demolition be activated by callback functions.

---

### Post by samjh on 2010-01-22
Why does your thread need to loop infinitely?  The thread to ping should be run only if there is an event in your GUI to ping something.  Once the pinging action is complete, the thread should end.

---

### Post by QuimNuss on 2010-01-22
There are many ways to prevent polling, basically you must wait on something (as Some Penguin suggested) or either spawn and kill threads as they are needed (suggested by samjh).

The second option may be faster but it's harder to implement due to concurrency. I suggest to put your thread waiting on a condition which is triggered by the GUI thread. Which can also be achieved with semaphores, or even with a simple mutex.

Without going into detail, Google around semaphore classes in Java, you'll just invoke aSemaphore.V() and aSemaphore.P() to achieve what you want.

---

### Post by dvlchd3 on 2010-01-22
i

---

