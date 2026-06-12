---
title: "Strange segfault issue..reboot solved the problem"
date: 2007-12-29
forum: Programming Talk
---

### Post by akudewan on 2007-12-29
I was working on a Sudoku program using Qt. There is a "New Game" dialog that I've made. The lines to create it are: 

```

void Grid::newGame()
{
	if(!newDialog)
	{
		newDialog = new NewDialog;
		connect(newDialog, SIGNAL(okClicked(Level)), this, SLOT(makeLevel(Level)));
	}
	newDialog->show();
	newDialog->activateWindow();
}

```

This was working fine, until suddenly I started getting a segfault in this function. On dubugging, I found that the NewDialog constructor was not being called. the newDialog pointer was already assigned an address! But it didn't point to any object.

Since I had not made any changes to the code, I didn't think that it was a mistake on my part. I rebooted the PC, deleted the *.o and moc* files, recompiled, and now it works just like before...Any idea why this happened?

Should I explicitly assign a null address to the pointer in the constructor for the main widget?

---

### Post by akudewan on 2007-12-29
I tried declaring a destructor for NewDialog. Nothing happened. Then I tried declaring a destructor for the main widget, in which I wrote "delete NewDialog". Nothing happened. Then I added the line "newDialog = NULL;" in the constructor for the main widget, and it worked!

Btw. Is it necessary to declare destructors in C++, is memory automatically freed when I close a widget (or the function returns)?

---

