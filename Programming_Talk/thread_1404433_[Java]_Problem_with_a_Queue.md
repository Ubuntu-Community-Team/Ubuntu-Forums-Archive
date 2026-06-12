---
title: "[Java] Problem with a Queue"
date: 2010-02-11
forum: Programming Talk
---

### Post by cdiem on 2010-02-11
I'm trying to make a simple snake clone for fun. I got stuck when trying to update the drawing of the snake on the screen. The problematic part is adding a node to a queue (similar to the following):

```

		int[] test = new int[2];
		Queue<int[]> dummyQueue = new LinkedList<int[]>();
		for (int i = 0; i < 3; i++) {
			test[1] += 50;
			dummyQueue.add(test);
                        
                        // show me some results:
			for (int[] node : dummyQueue) {
				System.out.print(Arrays.toString(node));
			}
			System.out.println();
		}

```

This outputs:

```

[0, 50]
[0, 100][0, 100]
[0, 150][0, 150][0, 150]

``` 

Why does adding an element to the queue change every other element in the queue? Is this an expected behaviour? How would you rewrite it, so that it shows:
```

[0, 50]
[0, 50][0, 100]
[0, 50][0, 100][0, 150]

```

Basically I need a queue of tuples of (x,y) coordinates - but the above outputs surprised me. Please, help.

---

### Post by Zugzwang on 2010-02-11
Ok, the problem here is that you keep appending the same tuple over and over again to the Queue. When adding the arrray to the queue, it is *not* copied. You will need to allocate a *new* one each time.

---

### Post by raffaele181188 on 2010-02-11
zugzwang was right. You'd better use a Point obj, consider
```

class Point {
  // Add constructor
  int x, y;
}

public class DrawRoutine {
  int lastX = 0, lastY = 0;
  
  public void draw(...args...) {
    for (...) {
      dummyQueue.add(new Point(lastX, lastY =+ 50));
    }
  }
}

```

---

### Post by cdiem on 2010-02-11
Thank you very much; now I understood my mistake. The "test" array mutates inside the queue, not being copied - hence the results. Thanks once again.

---

