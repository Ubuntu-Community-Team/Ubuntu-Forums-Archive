---
title: "Java Thread question"
date: 2010-12-21
forum: Programming Talk
---

### Post by MrStill on 2010-12-21
I am having an issue with Java threads. I am attempting to create an object that will follow a SASE style observer pattern. The object will automatically notify its observers every second and needs to allow new observers to register themselves with it at any time in the cycle. So, my timer works and notifies its observers every second; however, it seems that when the thread sleeps, the entire program sleeps. Here is what I have so far:

The observer portion of the timer:
```

public abstract class Timer{
	private ArrayList<Observer> observers;
	public Timer(){
		this.observers = new ArrayList<Observer>();
		this.run();
	}
	protected void alertObservers(){
		for(Observer o: observers) o.notifyObserver();
	}
	public void registerObserver(Observer observer){
		this.observers.add(observer);
	}
	//Template Method
	public abstract void run();
}

```
And the thread portion of the timer:
```

public class PCTimer extends Timer implements Runnable{
	private Thread thread;
	public PCTimer(){
		this.thread = new Thread(this);
		this.thread.start();
	}
        //Definition of template method
	public void run(){
		while(true){
			try{ 
				Thread.sleep(1000);
				this.alertObservers();
			}
			catch(InterruptedException e){}
		}
	}	
}

```
And finally the test code from my driver that doesn't work:
```

public class ScheduleManager implements Observer{
        ...
	public static void main(String args[]){
		...
                ScheduleManager sm = new ScheduleManager();
                ...
		PCTimer timer = new PCTimer();
                //Anything from here on never happens.
		timer.registerObserver(sm);
                ...
	}
}

```
As I said above, once the timer is constructed, it calls the run method which constructs the thread. But nothing outside of the run method ever executes. Any advise about what I am doing wrong would be great.

Thanks,
Joseph

---

### Post by r-senior on 2010-12-21
I've not verified this, but I suspect that when the PCTimer instance is created, it invokes the superclass constructor Timer(), which goes into a loop because you call this.run() in what is the main thread. You could confirm with some debugging but I suspect this.thread.start() is never called.

Presumably the main thread is then occupied in its infinite loop and cannot service the registration requests, especially as you don't attempt to process any interrupts in the InterruptedException handler?

I think you should probably remove the run() method (including the abstract method) from Timer so that the constructor in PCTimer can create the worker thread.

Maybe also think about whether registerObserver() needs to be thread-safe?

---

### Post by dwhitney67 on 2010-12-21
I second what r-senior has stated; I recall recently someone has a similar problem starting a thread.  Make sure that the thread object is fully constructed before attempting to run it.

---

