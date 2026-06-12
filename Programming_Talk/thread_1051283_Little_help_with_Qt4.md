---
title: "Little help with Qt4"
date: 2009-01-26
forum: Programming Talk
---

### Post by qbox on 2009-01-26
Hi
Im new in Qt and I want to make like a server client program. But I cant figure out this. I make Widget with Qt4 Designer with one button and one textEdit field. I have this code for the buttons.

```

serverWin::serverWin(QWidget *parent)
{
	setupUi(this);
	connect(btnQuit, SIGNAL(clicked()), qApp, SLOT(quit()));
	connect(btnFill, SIGNAL(clicked()), this, SLOT(showAcction()));

}
```

and this code for the function who write text to textEdit field:

```
void serverWin::showAcction()
{
	textEdit->append("Some example text");
}
```

When I start the program window shows and when I press btnFill the new text is added in the textEdit box. This work fine. But
I have another .cpp file with functions for server. In one function I have this lines of code

```
	
....
serverWin *window1 = new serverWin;
connect(clientConnection, SIGNAL(disconnected()), window1, SLOT(showAcction()));

```

now when I call showAcction() function, the code in void serverWin::showAcction() is executed (I test with text box, the box is shown when I call this function) but no new text is added to a textEdit box.

Can some one give me a little help? Thank you.

---

### Post by qbox on 2009-01-27
53 reviews and no one to reply?
I know that you are smarter then me.... Any help please?
:popcorn:

---

### Post by samjh on 2009-01-28
> **qbox said:**
> now when I call showAcction() function, the code in void serverWin::showAcction() is executed (I test with text box, the box is shown when I call this function) but no new text is added to a textEdit box.

I don't get this part.  Are you saying that the textEdit box is ONLY shown when you call showAcction()?  How do you know this?  The code you posted does not indicate this kind of behaviour.

If you want help, you'll need to post more information and more code.  For example, you should explain how this code relates to the rest of the code you posted:```
serverWin *window1 = new serverWin;
connect(clientConnection, SIGNAL(disconnected()), window1, SLOT(showAcction()));
```

---

### Post by qbox on 2009-01-28
The textEdit box is showed all time. When I click on btnFill some text is written in that box. Thats cool. The text is written from showAcction() function in textEdit box.
In another .cpp file, I have another code. From there I want to call showAcction() function and write some text in textEdit box. I first declare the object in another .cpp file with

serverWin *window1 = new serverWin;

(this is the relation to first .cpp file)
and I call showAcction() function with this line

connect(clientConnection, SIGNAL(disconnected()), window1, SLOT(showAcction()));

This line only call the showAcction() function from first .cpp file.

here is the code in the first .cpp file for showAcction() function

```
void serverWin::showAcction()
{
	textEdit->append("Some example text");
}
```

Now, when I push btnFill the showAcction() function is called and some text is written in textEdit box. But when I call showAcction() function from another .cpp file the function is executed but new text isnt added in the textEdit box.

I know that showAcction() function is executed because for test I add 
QMessageBox::critical(this, tr("TEST"),tr("TEST FOR FUNCTION"));
and the message box pop up. But no new text is added in textEdit box when showAcction() function is executed, when this function is called from another .cpp file.
In the headers I have included .h files so I can make objects and connect each other files.
If you need more code you can ask.
Thanks. ;)

---

