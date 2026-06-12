---
title: "Java Swing paintComponent Threading Question"
date: 2010-04-15
forum: Programming Talk
---

### Post by SNYP40A1 on 2010-04-15
I have 3 classes which extend JPanel (actually JFreeChart objects) and I would like to render these objects off of the Swing thread.  The panels are independent and I think I can get away with running each panel's paintComponent() entirely off of the Swing thread.  But paintComponent() is called by the Swing thread.  So how do I fork it off to run on another thread so that the Swing thread can immediately return and go off to do something else?

---

### Post by PaulM1985 on 2010-04-15
Would you be able to create a class which implemented runnable and took the component you wanted to redraw as a constructor?  In the class's run method you could call repaint (or paintComponent) on the object passed into the class constructor.  You could use:

Thread t = new Thread(new MyPainterClass(objectToPaint));
t.start();

which I would have thought would paint the object, splitting the paint command off from the processes that you are running.  I think you would maybe have to add some lock to this component while painting though, so as not to upset the state of the object while it is in the middle of painting.  I am not too sure how overriding works with the "synchronized" keyword, but I think its ok.

(I am not sure this will work, but this is the sort of root I would probably test)

Hope these ideas are of some help.

Paul

---

### Post by Reiger on 2010-04-15
> **SNYP40A1 said:**
> I have 3 classes which extend JPanel (actually JFreeChart objects) and I would like to render these objects off of the Swing thread.  The panels are independent and I think I can get away with running each panel's paintComponent() entirely off of the Swing thread.  But paintComponent() is called by the Swing thread.  So how do I fork it off to run on another thread so that the Swing thread can immediately return and go off to do something else?

If you want to do this, you essentially want the following:

```

@Override
public void paintComponent(final Graphics g) {
  // cancel jobs if they haven't completed yet.
  if(renderTask !=null && renderTask.isDone() == false) {
    renderTask.cancel(true);
  }
  // call super implementation for the background, etc.
  super(g);

  // construct & schedule a new render task
  Runnable task= new Runnable() {
    @Override
    public void run() {
      trigerRender(g);
      cleanup();
    }
  };
  // schedule rendering to take place
  renderTask= renderService.submit(task);
}

// field we use to cancel previous tasks if they haven't completed yet
private Future renderTask;

/* substitute an appropriate static method from the Executors class
 * to obtain a thread pool & event queue
 */
private static final ExecutorService renderService= ... ;

/**
 * Encapsulates rendering logic. 
 */ 
private void triggerRender(Graphics g) {
  // rendering logic.
}

/**
 * cleanup code called after triggerRender finishes.
 */
private void cleanup() {
  // dispose of no longer needed resources...
  renderTask= null;
}

```

Alternatively you can use SwingWorker to do most of this for you, but at least with Java 6 update 18 and 19 this will likely require you to jump through the Executors hoop regardless because of how the SwingWorker thread pool is essentially limited to just one thread. 

(SwingWorkers in Java 6 u18/19 use an unbounded queue internally and at minimum only one thread, so you get the effect of a single-threaded SwingWorker pipe. Therefore your application cannot run two SwingWorkers side by side unless you manually create additional thread pools, for example using the Executors static methods.)

---

### Post by SNYP40A1 on 2010-04-16
Thanks for the ideas.  I tried a similar approach -- I renamed paintComponent to something else then replaced the function with this:

[PHP]
    final ChartPanel cpanel = this;
    final Graphics fgraphics = g;

Thread t = new Thread(new Runnable() {
    public void run()
    {
        cpanel.paintComp(g);
    }
});
t.start();
[/PHP]

Doing that did not cause any errors and I did nearly max out the CPU, however, the display was messed up.  Things were misaligned, I was missing a number axis, etc.  

What's the general approach for painting multiple panels?  I am guessing that most people fork off a separate worker thread for all CPU-intensive work.

[http://www.stanford.edu/class/cs108/handouts092/25Thread3GUI.pdf](http://www.stanford.edu/class/cs108/handouts092/25Thread3GUI.pdf)

Does "event dispatch thread" == "swing thread"?  Assuming that it does...

So when a panel receives a repaint() event, it will call paintComponent(Graphics g) for all of it's members.  But since most of Swing is not thread-safe, each call to paintComponent (assuming that the component has more than one member) will execute serially and run on the Swing thread.  The problem (at least with JFreeChart) is that many things that happen under the paintComponent frame do not involve Swing.  But even if a worker thread was created for these tasks that do not involve swing, that would do no good because the swing thread would then just be waiting for these tasks to finish.  A better solution would be to have the swing thread call paintComponent() on each member object and not wait around for the return so that all calls execute in parallel.  Then use SwingUtilities() invoke later to handle all the Swing calls.

...Is this understanding correct or am I missing something?

---

### Post by Reiger on 2010-04-16
Consider a few points of interest:

[list="1"]
[*]What happens if two events cause the paintComponent() to be called in quick succession?
[*]What happens if one old thread is waiting to run when newer events render the task obsolete?
[*]In general, how does synchronisation work? You can't have two threads using the same Graphics context at the same time; remember that Graphics is *not* an object that keeps graphical state. It is an context object which provides some auxiliary methods to do the actual painting... it is not a render...
[/list]

If you need reliable rendering of the UI widget the most simple thing to do would be to create an Image of some sort (i.e. BufferedImage), render it, and when finished draw it using the Graphics object in e.g. paint().

This could be done using a SwingWorker to take care of most threading issues right away:
```

renderTask=new SwingWorker<BufferedImage, BufferedImage> () {
   @Override
   public void process(List<BufferedImage> doneSoFar) { // called on EDT
     BufferedImage latest = doneSoFar.get(doneSoFar.size() -1);
     // paint latest immediately
   }

   @Override
   public BufferedImage doInBackground() throws Exception {
     // runs outside the EDT

     BufferedImage result = ... ;
     /*
      * Render logic here. At each discrete substep you could 
      * call publish() with the result-so-far which will trigger
      * a call to process() with the result so far
      */
     return result;
   }
   
   @Override
   public void done() { // called on the EDT
     try {
       BufferedImage result=get();
       // paint render now
     }
     catch(Exception ignore) {
       // task canceled/failed
     }
   }
}

```

This allows you to periodically update your UI while the final render is still in progress. However, note that in Java update 18/19 the SwingWorker thread pools is configured in such a way that you can have only one SwingWorker running through SwingWorker.execute() at the same time. As a result I'd recommend to use the SwingWorker in conjunction with the ExecutorService approach (you can submit SwingWorkers since they are instances of Runnable as well as Future) to get the most reliable results.

---

