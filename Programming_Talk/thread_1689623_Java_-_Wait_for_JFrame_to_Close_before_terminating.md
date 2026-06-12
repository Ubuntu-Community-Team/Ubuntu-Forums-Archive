---
title: "Java - Wait for JFrame to Close before terminating"
date: 2011-02-17
forum: Programming Talk
---

### Post by SNYP40A1 on 2011-02-17
I'm using a program that I developed which displays some results in a JFrame and then exits.  The problem is that the results display in a JFrame instantaneously, then the function returns and the JFrame is closed.  Is there a way to make the program halt until the JFrame is closed?  I'm achieving this effect by waiting for a keystroke at the end of the function.  However, would be nice if the JFrame would just suspend the thread until closed.

---

### Post by jwcalla on 2011-02-17
The JFrame shouldn't close unless the operator closes it and the program shouldn't terminate until all threads are defunct.  Are you explicitly calling System.exit() somewhere?

---

### Post by PaulM1985 on 2011-02-17
If you want the program to halt execution until the window is closed, you could use a JDialog.

```

JDialog d = new JDialog();  // Creates dialog
d.setModal(true);           // Means it will wait
ResultsPanel p = new ResultsPanel(d); // A panel to show your results.  Pass in the dialog as an argument
d.add(p);                   // Add your panel
d.setSize(500, 500);        // Set size (probably want this relating to your panel
d.setVisible(true);

```

The reason to pass the JDialog into the constructor of your results panel is to provide the results panel a reference to the dialog so it can call setVisible(false) on it to close it, (probably on a button click or something).

I hope this solves your problem.

Paul

---

