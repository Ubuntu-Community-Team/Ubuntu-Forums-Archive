---
title: "Games Programming in Java.  When to repaint?"
date: 2009-10-08
forum: Programming Talk
---

### Post by JCoster on 2009-10-08
Hey guys.  
I've been trying to program my first GUI game in Java and am having problems when trying to repaint.
What I want to know is when should I call redraw?  At the moment I'm doing it wrong because I've got it running in a looped thread redrawing 30 times per second, but if I have a background then it doesn't get rendered properly and just flicks.

Looped thread:
```
	public void run() {
		Boolean end = false;

		while (!end) {
			try {
				Thread.sleep(60);
				repaint();
			}
			catch (InterruptedException e) {
				
			}
			
		} 
	}
```

And basically that just repaints the whole window...  Is this the right way to go about it?  If it is then why is it not working properly?  And if not then how do I go about it?

---

### Post by JCoster on 2009-10-08
Ok well i've done a bit of Googling and this draft chapter from a book solved my problems and makes for some good useful reading relating to Java game programming:
[http://fivedots.coe.psu.ac.th/~ad/jg/ch1/ch1.pdf](http://fivedots.coe.psu.ac.th/~ad/jg/ch1/ch1.pdf)

---

