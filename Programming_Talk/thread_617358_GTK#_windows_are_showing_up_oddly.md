---
title: "GTK# windows are showing up oddly"
date: 2007-11-19
forum: Programming Talk
---

### Post by kissg1988 on 2007-11-19
Hello there,

I'm having some problems using GTK# on my C# program.
I'd like to create child windows, but all of my windows appear behind the parent window.
I'm new to GTK, but I have some idea what could be wrong.

I create a window like this:

```
PopupDialog popup = new PopupDialog();
popup.ShowErrorMessage("Bad data format","The postcode can only contain numbers.");

```

My PopupDialog class looks like this:

```
class PopupDialog
	{
		public void ShowErrorMessage(string winTitle, string winMessage)
		{
			ErrorMessageWindow msgWin = new ErrorMessageWindow();
			msgWin.Title = winTitle;
			msgWin.SetMessage(winMessage);
			msgWin.Show();
		}
		public void ShowInformation(string winTitle, string winMessage)
		{
			MessageWindow msgWin = new MessageWindow();
			msgWin.Title = winTitle;
			msgWin.SetMessage(winMessage);
			msgWin.Show();
		}
	}

```

ErrorMessageWindow and MessageWindow are pre-defined windows, created by me.

If I run my program, everything works okay, but as I said, newly created windows appear behind the active window. They get focus, but aren't visible.

Thanks for your help in advance!

---

