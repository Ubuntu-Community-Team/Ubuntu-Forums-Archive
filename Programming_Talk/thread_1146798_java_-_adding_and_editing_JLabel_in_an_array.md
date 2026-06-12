---
title: "java - adding and editing JLabel in an array"
date: 2009-05-02
forum: Programming Talk
---

### Post by mikemcleanuk on 2009-05-02
I am trying to find a way i can add and modify a JLabel through the use of an array or vector.

in Psudo Code i want to:

Create Array
Start For loop
Add JLabel to the array
Add JLabel to a GridLayout Panel (3x3).

Then through the use of additional for loops i can edit the different Lables with the use of the "i" variable. I have this at the moment:

```

int i = 0;
for(i = 0; i < 9; i++) 
{
	appLabels[i] = new JLabel(blank);
	GridPanel.add(appLabels[i]);
}

```

Then i want to be able to do something like:

```
	int++;
	delete.appLabels[i];
	appLabels[i] = new JLabel(baloon);
	GridPanel.add(appLabels[i]);
```

so i can easily manage the different Lables within the array.

I am open to using Vectors also if someone would like to suggest a solution using that instead.

The overall aim of my project is to have a 3x3 grid that orriginally is filled with placeholder label images (blank) and then through the use of buttons i want to be able to replace the labels in order with a new label image. If you think i am way off track and can suggest a better way to do this that allows me to attack mouselisteners to the individual lables easily then please go ahed and show me!

Thanks
Mike

---

### Post by MeLight on 2009-05-04
Why aren't you just implementing what you showed us in the pseudo-code example?

---

