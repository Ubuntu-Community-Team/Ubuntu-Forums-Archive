---
title: "[SOLVED] JAVA getText().length() PROBLEM"
date: 2008-12-07
forum: Programming Talk
---

### Post by meteozguz on 2008-12-07
```
private void jTextField1KeyTyped(java.awt.event.KeyEvent evt) {

           System.out.println(jTextField1.getText().length());
}
```

I simply try to count chars of a text field whenever this field changed.
For example, when I typed "asdf asdf" I want to see 9 for char count.

I now that length() returns actual lenth-1

The best way to describe my problem is to put output:

run the program

type "a"
 System.out.println(jTextField1.getText().length()); returns 0


type "s"
 System.out.println(jTextField1.getText().length()); returns 1


type "d"
 System.out.println(jTextField1.getText().length()); returns 2


type "f"
 System.out.println(jTextField1.getText().length()); returns 3

press Delete
 System.out.println(jTextField1.getText().length()); returns 4

delete "f" pressing Backspace
 System.out.println(jTextField1.getText().length()); returns 3

What is going on? How can achieve my goal properly? Thanks ( I remember the day when I did the same thing in .NEt...... )

---

### Post by pp. on 2008-12-07
Could it possibly be that the event is triggered before the character has been added to or removed from the text buffer? If so, is there another event which is triggered after the update to the buffer?

---

### Post by meteozguz on 2008-12-07
I didn't put any other code which can do that, and I have no other idea... 

By the way
I cut and paste System.out.... line into a buttonMousePressed method and everything works just fine 
but how can i automatize it?
thanks for your reply

---

### Post by pp. on 2008-12-07
I don't quite understand what you are saying.

In my first response to your problem, I was trying to say:

I think that java sends the KeyEvent when you have pressed a key, but before java adds the character to the text in jTextField1. 

Therefore, your statement jTextField1.getText().length() would return the number of characters in jTextField1 at the time the key was pressed, but  before the character was added to jTextField1.

If that was so, length() would indeed return the number of characters in the text field and not one less than that number. I think that much more plausible because otherwise java had to return the value -1 when the string was empty.

---

### Post by achelis on 2008-12-07
Try adding the following key-listener and play around, it should give you an idea of when the different key events are generated:

```

	public void keyPressed(KeyEvent e) {
		System.out.println("Key-pressed: " + txfText.getText());
	}

	public void keyReleased(KeyEvent e) {
		System.out.println("Key-released: " + txfText.getText());
	}

	public void keyTyped(KeyEvent e) {
		System.out.println("Key-typed: " + txfText.getText());
	}

```

---

