---
title: "[SOLVED] Java awt ActionListener question"
date: 2008-04-19
forum: Programming Talk
---

### Post by akudewan on 2008-04-19
Hi there!

I have a simple Java program, using awt, in which I implement an ActionListener for a Button

I was told to make this kind of a comparison:
```

public void actionPerformed(ActionEvent e)
	{
		[COLOR="Red"]if( ( e.getActionCommand() ).equals("Add") )[/COLOR] //"Add" is the text on the button
			//do stuff here
	}

```

What do I use this if-block for ?

If my guess is correct, this provides a way of distinguishing between multiple Buttons. If so, it seems quite a shoddy method - comparing the text on the label instead of something more reliable, like the memory location or the name of the button. Is there a better way?

Thanks!

---

### Post by newb1e on 2008-04-19
Your guess is right. It distinguishes between multiple objects that register the ActionListener.
This is not comparing text on the label. You can set the ActionCommand to any text you want.

Besides, you can check by memory location by using e.getSource()

---

### Post by akudewan on 2008-04-20
Thanks for clearing it up :)

---

