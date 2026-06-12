---
title: "JAVA:ArrayList store values?"
date: 2007-01-13
forum: Packaging and Compiling Programs
---

### Post by serlex on 2007-01-13
I got an arraylist working, but how do i store the values when the program closed, so i do not have to type them again?

I thought about writing and reading from a file, but you would not need an arraylist then?

Thank you

---

### Post by phossal on 2007-01-13
You can use java.util.ArrayList for a lot of things. How your collection is best stored between program invocations depends entirely on the use. 

Let us know what you're up to, maybe post a code snippet, and we'll try to help.

---

### Post by serlex on 2007-01-13
ok

here is the bit with the arraylist and inputdialog
```

	siteNames = new ArrayList<String>();

	addItem.addActionListener(
		new ActionListener()
			{
		         public void actionPerformed(ActionEvent event)
				{
			         String targetKey = JOptionPane.showInputDialog(null, text,title,icon);
			         siteNames.add(targetKey);
			         System.out.println(siteNames);
				}
			});

```

obviously when I closed the program, data in arraylist is not saved.

---

### Post by phossal on 2007-01-13
Database? Serialized object? Properties File?

---

### Post by serlex on 2007-01-13
ahh i think Serialized is what i'm looking for! Thank you

---

### Post by phossal on 2007-01-13
You're welcome. By the way, you're doing Java *stuff* without manuals? When I'm forced to solve a quick problem and the reference books are at another location, here is where I go:

[Java Developer's Almanac]("http://www.exampledepot.com/")

You can find code examples for almost everything you could want to do. It's a little outdated, but not so much that it won't be incredibly useful for you. Good luck.

---

### Post by serlex on 2007-01-13
Just found out, you cant actually remove object from the file! :(

EDIT: sorry I just applied outputstream to my remove button!

---

