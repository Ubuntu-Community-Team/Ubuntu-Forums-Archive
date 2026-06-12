---
title: "Java Event Listener Paradigm Question"
date: 2010-03-03
forum: Programming Talk
---

### Post by SNYP40A1 on 2010-03-03
I have three Java Swing objects that I am trying to keep in sync by using event listeners.  The problem is that when one object changes, it will notify the others about the change.  But when the objects are notified they too change / update which cause their own change event listeners to fire off a notification about the same change to the other objects.  The objects are Swing objects so it's not so easy to temporarily disable the event notifications due to buffering.  Anyone know of the best approach for dealing with this issue?  

One approach that I can think of is by having one of the objects be the master and the others be slaves.  So that all slaves only notify the master object with their changes and the master object sends changes out to all slaves.  However, this would not solve the ping-ponging between master and slaves.  It would only solve the ping-ponging among the slaves.

---

### Post by k@e on 2010-03-03
A while ago, I had the same problem trying to sync two comboboxes. They would just keep triggering item events until a stack overflow error occurs.

The solution was to check the item event whether an actual change by the user took place.

```

public class EventOne implements ItemListener {
	public void itemStateChanged(ItemEvent arg0) {
		if (arg0.getStateChange() == ItemEvent.SELECTED) {
			// changing contents of widget #2 ...
		}
	}
}

public class EventTwo implements ItemListener {
	public void itemStateChanged(ItemEvent arg0) {
		if (arg0.getStateChange() == ItemEvent.SELECTED) {
			// changing contents of widget #1 ...
		}
	}
}

widgetOne.addItemListener(new EventOne());
widgetTwo.addItemListener(new EventTwo());

```

Depending on what kind of event you are having problem with, there may be a similar solution.

---

### Post by SNYP40A1 on 2010-03-03
> **k@e said:**
> A while ago, I had the same problem trying to sync two comboboxes. They would just keep triggering item events until a stack overflow error occurs.

The solution was to check the item event whether an actual change by the user took place.

```

public class EventOne implements ItemListener {
	public void itemStateChanged(ItemEvent arg0) {
		if (arg0.getStateChange() == ItemEvent.SELECTED) {
			// changing contents of widget #2 ...
		}
	}
}

public class EventTwo implements ItemListener {
	public void itemStateChanged(ItemEvent arg0) {
		if (arg0.getStateChange() == ItemEvent.SELECTED) {
			// changing contents of widget #1 ...
		}
	}
}

widgetOne.addItemListener(new EventOne());
widgetTwo.addItemListener(new EventTwo());

```

Depending on what kind of event you are having problem with, there may be a similar solution.

That's a good solution.  The library that I am using, JFreeChart, event listener is ChartChangeListener:

[http://www.jfree.org/jfreechart/api/javadoc/org/jfree/chart/event/ChartChangeListener.html](http://www.jfree.org/jfreechart/api/javadoc/org/jfree/chart/event/ChartChangeListener.html)

[http://www.jfree.org/jfreechart/api/javadoc/org/jfree/chart/event/package-summary.html](http://www.jfree.org/jfreechart/api/javadoc/org/jfree/chart/event/package-summary.html)

And the listener does provide a getChart() call so that I can tell which chart caused the call.  However, there's a subtle problem with using getChart() to resolve this issue.  Although the objects can simply ignore all calls which originated from itself, if an object does make a change, it will fire off another event with the source chart as itself.  So even 3 objects can start a pin-pong loop.  I am using this for updating crosshair and domain range bounds.  So if I get a change event, I can't just blindly update the crosshair and range from the chart that originated the event because that would cause another change event to fire for the chart that is being updated, that's how the looping starts.  Maybe JFreeChart is smart enough to only fire an event update if something was actually changed (if I called a set method to change a parameter to what it was already set at, no change occured), but I doubt they did this, would add extra overhead.

---

