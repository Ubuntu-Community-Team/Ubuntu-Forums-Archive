---
title: "Java Mouse Listener"
date: 2008-07-28
forum: Programming Talk
---

### Post by gorded on 2008-07-28
In Java is there a way to register a mouse listener on a seperate thread so that mouse events dont get held back by processing in the main loop

Thanks

---

### Post by dribeas on 2008-07-28
> **gorded said:**
> In Java is there a way to register a mouse listener on a seperate thread so that mouse events dont get held back by processing in the main loop

Thanks

A lot of people mistakes classes and methods with threads. Classes contain data and methods that are instructions that will be executed by one thread. You can decide what code will be called when an event occurs, but the thread that will call your code is Java's event processing loop.

Now, if you don't want that to interfere with your processing, you can always do your processing in a different thread.

   David

---

### Post by jviscosi on 2008-07-28
I haven't done much Java lately but I would think you could create a listener that delegates its actions to another class that implements Runnable and then run the Runnable class in a separate thread initiated by the listener.  Depending on how your listener is structured you will have to deal with thread safety, sharing data between the threads, etc.

Like I said, I haven't done Java professionally for over two years and I'm certainly rusty and not up to speed on the latest favored methodology for this sort of thing ...

---

### Post by drubin on 2008-07-28
Take a look at  SwingUtilities.invokeAndWait()  and swingUtilities.invokeLater().

Something similar

[http://www.javaworld.com/javaworld/jw-08-2007/jw-08-swingthreading.html](http://www.javaworld.com/javaworld/jw-08-2007/jw-08-swingthreading.html)

---

### Post by tinny on 2008-07-28
I think this is what you want.

[PHP]
public class ThreadedMouseListener implements MouseListener {

    public void mouseClicked(MouseEvent e) {
        Thread thread = new Thread(new Runnable() {

            public void run() {
                //Handle this event hear
            }
        });
        thread.start();
    }

    public void mousePressed(MouseEvent e) {
        Thread thread = new Thread(new Runnable() {

            public void run() {
                //Handle this event hear
            }
        });
        thread.start();
    }

    public void mouseReleased(MouseEvent e) {
        Thread thread = new Thread(new Runnable() {

            public void run() {
                //Handle this event hear
            }
        });
        thread.start();
    }

    public void mouseEntered(MouseEvent e) {
        Thread thread = new Thread(new Runnable() {

            public void run() {
                //Handle this event hear
            }
        });
        thread.start();
    }

    public void mouseExited(MouseEvent e) {
        Thread thread = new Thread(new Runnable() {

            public void run() {
                //Handle this event hear
            }
        });
        thread.start();
    }
}
[/PHP]

Alternately if you only want to handle specific events and not all Mouse events extend "MouseAdapter".

Or MouseMotionListener etc whatever you are try listening for....

---

### Post by jviscosi on 2008-07-28
> **tinny said:**
> I think this is what you want.

[php]
public class ThreadedMouseListener implements MouseListener {

    public void mouseClicked(MouseEvent e) {
        Thread thread = new Thread(new Runnable() {

            public void run() {
                //Handle this event hear
            }
        });
        thread.start();
    }
[/php]

I miss anonymous inner classes ...

---

### Post by ceclauson on 2008-07-28
It's not obvious to me what exactly you're trying to do.  If one of these posts hasn't answered your question, try posting again with more specifics.

---

### Post by ceclauson on 2008-07-28
> **jviscosi said:**
> I miss anonymous inner classes ...

Anonymous inner classes are nice.  Without them, I think java programming would be pretty terrible, without support for function pointers/delegates.

---

### Post by tinny on 2008-07-28
> **ceclauson said:**
> Anonymous inner classes are nice.  Without them, I think java programming would be pretty terrible, without support for function pointers/delegates.

Yes, but things are about to change. [Java 7 closures ]("http://gafter.blogspot.com/2006/08/closures-for-java.html")

---

### Post by ceclauson on 2008-07-29
> **tinny said:**
> Yes, but things are about to change. [Java 7 closures ]("http://gafter.blogspot.com/2006/08/closures-for-java.html")

That's really funny that they're introducing it now, because I remember that I wished Java had something like this when I first started, but now I'm all used to anonymous inner classes.

The irony is that now that I'm used to the current way of doing it, I'll probably be that crotchety old programmer who insists on using anonymous inner classes after closures are available. :-P

---

### Post by dribeas on 2008-07-29
> **tinny said:**
> I think this is what you want.

[PHP]    public void mouseClicked(MouseEvent e) {
        Thread thread = new Thread(new Runnable() {

            public void run() {
                //Handle this event hear
            }
        });
        thread.start();
    }
[/PHP]

It's been long since I last programmed Java, so I am asking. When you get out of mouseClicked() method the 'thread' reference goes out of scope, and as far as I can see there are no other references to the thread object. Would it not get garbage collected at some (unpredictable) point?

   David

---

### Post by dribeas on 2008-07-29
> **tinny said:**
> [PHP]
    public void mouseClicked(MouseEvent e) {
        Thread thread = new Thread(new Runnable() {

            public void run() {
                //Handle this event hear
            }
        });
        thread.start();
    }[/PHP]


Also note the cost of what you are doing, as you are incurring the cost of Thread creation/deletion for each event that gets processed. And you must be careful on how you access the UI inside those run()'s, as they are other threads, all UI operations must be performed through invokeLater()/invokeAndWait().

[Threads and Swing]("http://java.sun.com/products/jfc/tsc/articles/threads/threads1.html")

   David

---

### Post by ceclauson on 2008-07-30
> 
It's been long since I last programmed Java, so I am asking. When you get out of mouseClicked() method the 'thread' reference goes out of scope, and as far as I can see there are no other references to the thread object. Would it not get garbage collected at some (unpredictable) point?

I've never thought about this before, but I'm pretty confident saying no.  The reason is that I usually don't save references to threads, and I've never had a problem with this before, and I know this idiom is used by professional programmers to start a new thread (specifically, because I've seen in it O'Reilly's "Learning Java"):

[PHP]
new Thread() {
	public void run() {
		//do stuff here
	}
}.start();
[/PHP]

As far as the cost of creating and destroying threads goes, you could just have one thread handling the events which spends most of its time sleeping, and wake it up periodically to do its thing.  I think this code would do it, or something like this:

[PHP]import java.awt.event.*;
import java.util.*;

public class ThreadedMouseListener implements MouseListener {

	private static class MouseEventWithType {
		public MouseEvent me;
		public int type;
	}
	
	private static final int CLICKED = 0;
	private static final int PRESSED = 1;
	private static final int RELEASED = 2;
	private static final int ENTERED = 3;
	private static final int EXITED = 4;
	
	private Thread handlingThread;
	private Queue<MouseEventWithType> eventQueue;
	
	public void ThreadedMouseListener() {
		
		eventQueue = new LinkedList<MouseEventWithType>();
		
		handlingThread = new Thread() {
			public void run() {
				//thread loops its whole life
				while(true) {
					//pump events
					while(true) {
						MouseEventWithType mewt = eventQueue.poll();
						//break if queue is empty
						if(mewt == null)
							break;
						switch(mewt.type) {
							case CLICKED:
								//handle clicked
								break;
							case PRESSED:
								//handle pressed
								break;
							case RELEASED:
								//handle released
								break;
							case ENTERED:
								//handle entered
								break;
							case EXITED:
								//handle exited
								break;
						}
					} //finished pumping events
					//wait until notified
					try {
						this.wait();
					} catch(InterruptedException e) {
						//go to top of loop, handle all events again
					}
				} //this loop never exits
			} //end of run method, never exits
		};
		
		//thread dies when application dies
		handlingThread.setDaemon(true);
		//start thread and return
		handlingThread.start();
		
	}
	
    public void mouseClicked(MouseEvent e) {
        //push event with type onto queue
    	MouseEventWithType mewt = new MouseEventWithType();
    	mewt.me = e;
    	mewt.type = CLICKED;
    	eventQueue.offer(new MouseEventWithType());
    	//notify thread to handle it
    	handlingThread.notify();
    }

    public void mousePressed(MouseEvent e) {
        //push event with type onto queue
    	MouseEventWithType mewt = new MouseEventWithType();
    	mewt.me = e;
    	mewt.type = PRESSED;
    	eventQueue.offer(new MouseEventWithType());
    	//notify thread to handle it
    	handlingThread.notify();
    }

    public void mouseReleased(MouseEvent e) {
        //push event with type onto queue
    	MouseEventWithType mewt = new MouseEventWithType();
    	mewt.me = e;
    	mewt.type = RELEASED;
    	eventQueue.offer(new MouseEventWithType());
    	//notify thread to handle it
    	handlingThread.notify();
    }

    public void mouseEntered(MouseEvent e) {
        //push event with type onto queue
    	MouseEventWithType mewt = new MouseEventWithType();
    	mewt.me = e;
    	mewt.type = ENTERED;
    	eventQueue.offer(new MouseEventWithType());
    	//notify thread to handle it
    	handlingThread.notify();
    }

    public void mouseExited(MouseEvent e) {
        //push event with type onto queue
    	MouseEventWithType mewt = new MouseEventWithType();
    	mewt.me = e;
    	mewt.type = EXITED;
    	eventQueue.offer(new MouseEventWithType());
    	//notify thread to handle it
    	handlingThread.notify();
    }
}  
[/PHP]

Using invokeLater() and invokeAndWait() cause some thread to have the event thread to do something, whereas the code that I posted and that posted by Tinny cause the event thread to get another thread to do something, so these are two different tasks.  As I posted before, though, it's not obvious to me which the original poster was trying to do.

---

### Post by dribeas on 2008-07-30
> **ceclauson said:**
> Using invokeLater() and invokeAndWait() cause some thread to have the event thread to do something, whereas the code that I posted and that posted by Tinny cause the event thread to get another thread to do something, so these are two different tasks.  As I posted before, though, it's not obvious to me which the original poster was trying to do.

Agree, what I was trying to state is that if the code in the newly created thread needs to update the interface, that operation should not be done directly, as it is in a different thread. If the callback does not update UI, then it is fine.

   David

---

### Post by drubin on 2008-07-31
> **ceclauson said:**
> 
As far as the cost of creating and destroying threads goes, you could just have one thread handling the events which spends most of its time sleeping, and wake it up periodically to do its thing.  I think this code would do it, or something like this:
**.....**


Never really thought about this approach but pretty sure I would not like this thread just sitting in the background for the whole time until some one uses the mouse.:s

---

### Post by tinny on 2008-07-31
Thread creation / destruction is trivial.
If you are worried about this you shouldn't be using Java.

However in this case it would be way better to have 1 Mouse event thread processing the delegated mouse events (processing a queue of mouse events periodically).

---

