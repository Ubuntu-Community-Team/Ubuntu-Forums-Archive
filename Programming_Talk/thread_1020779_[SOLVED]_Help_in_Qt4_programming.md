---
title: "[SOLVED] Help in Qt4 programming"
date: 2008-12-24
forum: Programming Talk
---

### Post by jjros on 2008-12-24
Hi, I'm looking for information in Qt4 programming for widgets screen and touch pannel, any information or book for this?

Thanks.

---

### Post by samjh on 2008-12-24
Have you consulted the Qt mailing list and documentation?

Qt docs: [http://doc.trolltech.com/](http://doc.trolltech.com/)
Qt knowledge base: [http://trolltech.com/developer/faqs](http://trolltech.com/developer/faqs)
Official forums: [http://labs.trolltech.com/forums/](http://labs.trolltech.com/forums/)

I'm not sure if there is anything specific to touch screens.  Presumably, it's just normal desktop Qt or one of Qt's embedded devices platforms.

This is not really the best place to ask. ;)

---

### Post by Aiman on 2008-12-26
I wasnt sure if i should open a new thread,but the thread title is great :p
i have a problem with my application
when the scan button is pressed,the GUI hangs and waits for the results to return and then you can use the GUI,i want the allow the user to use the GUI even if when the application is scanning,thats the code for the scan
it takes whats written in the Command_LineEdit and then return the result in scan_output(text browser)
```
void ptc::scan()
{ 	
	QProcess scn;

	if(Command_LineEdit->text()==NULL)
	{
		scn.exitCode();

		Scan_Button->setEnabled(false);
	}

	else
    {
    	scn.start(Command_LineEdit->text());    
    	scn.waitForFinished();
		QByteArray result=scn.readAllStandardOutput ();
    	scan_output->append(result.data());
		result = scn.readAllStandardError ();
		scan_output->append(result.data());
    	Scan_Button->setEnabled(true);
    }
}
```

i had an action button,when activated,it starts a terminal,it used to hang the GUI when the terminal starts,but when i used this,it works fine and independent from the GUI
```
void ptc::terminal()
{
        QProcess term;

	term.setProcessChannelMode(QProcess::MergedChannels);

	term.start("gnome-terminal");

	if (!term.waitForFinished())

     qDebug() << term.errorString();

 else

     qDebug() << term.readAll();  

}
```

any help please !

---

### Post by tseliot on 2008-12-26
> **Aiman said:**
> i have a problem with my application
when the scan button is pressed,the GUI hangs and waits for the results to return and then you can use the GUI,i want the allow the user to use the GUI even if when the application is scanning,thats the code for the scan
it takes whats written in the Command_LineEdit and then return the result in scan_output(text browser)

QProcess::waitForFinished() will make the interface hang as it will make the program wait for the process to finish.

You should do it in a different way, without using waitForFinished.

Use a QProcess and connect it to the following signals:
```
readyReadStandardOutput()
readyReadStandardError()
finished(int)

```

In this way, when new standard output or error is available, either the readyReadStandardOutput() or the readyReadStandardError() will be emitted and a member function (which you will have to define) will append the new output to result.data(). When the finished(int) signal is emitted you will then show the result to the user, do Scan_Button->setEnabled(true), etc.

This won't block the UI of your application and should solve your problem.

---

### Post by Aiman on 2008-12-28
i added the readyReadStandardOutput & readyReadStandardError
but the scan doesnt return anything
```
void ptc::scan()

{ 	

	QProcess scn;

	

	if(Command_LineEdit->text()==NULL)

	{

		scn.exitCode();

		Scan_Button->setEnabled(false);

	}

	else

    {

    	scn.start(Command_LineEdit->text());

		QByteArray result=scn.readAllStandardOutput ();

		connect( &scn, SIGNAL(readyReadStandardOutput()),this, SLOT(result.data()));

    	scan_output->append(result.data());

		result = scn.readAllStandardError ();

		connect( &scn, SIGNAL(readyReadStandardError()),this, SLOT(result.data()) );

		scan_output->append(result.data());

    	Scan_Button->setEnabled(true);

    }

}
```

---

### Post by tseliot on 2008-12-29
> **Aiman said:**
> i added the readyReadStandardOutput & readyReadStandardError
but the scan doesnt return anything
...

It's not what I meant.

First of all you will have to connect the signals so that when an event is emitted, a member function will be called:
```
connect( m_Scn, SIGNAL(readyReadStandardOutput()),this, SLOT(readOutput()));

connect( m_Scn, SIGNAL(readyReadStandardError()),this, SLOT(readError()) );
```

Then you can start the QProcess.

scn should really be a class member (which you will access from readOutput and readError too), therefore call it m_Scn or something similar:
```
m_Scn = new QProcess();
```

As regards the 2 functions (readOutput() and readError()) they will have to be separate from ptc::scan().

For example:
```
void ptc::readOutput() {
    QByteArray result=m_Scn.readAllStandardOutput();
    QStringList lines = QString(result).split("\n");
    foreach (QString line, lines) {
        m_LogWidget->append(line);
    }
}
```

Where m_LogWidget is a class member such as a QTextEdit, which will contain the standard output of the command.

You will have to do the same for the standard error (Note: you can append the text to the same QTextEdit widget if you want).

---

### Post by Aiman on 2008-12-29
im still not sure what im trying to do here,heres the changes i tried ( Did a lot but this is the last one that kinda make sense )

In the constructor (ptc.cpp) i added
```
connect( &mscn, SIGNAL(readyReadStandardOutput()),this, SLOT(readOutput()));

	connect( &mscn, SIGNAL(readyReadStandardError()),this, SLOT(readError()) );
```

if i remove the (&) i get an error

and for the scan()
```
void ptc::scan()

{ 	

	QProcess scn;

	

	if(Command_LineEdit->text()==NULL)

	{

		scn.exitCode();

		scan_output->setText("No command to excute !!");

	}

	else

    {

    	scan_output->setText("");

    	scn.start(Command_LineEdit->text());

    	Scan_Button->setEnabled(true);

    }

}
```

for the readError & readOutput
```
oid ptc::readOutput()

{

	QByteArray result=mscn.readAllStandardOutput();

    QStringList lines = QString(result).split("\n");

    foreach (QString line, lines) {

        scan_output->append(line);

    }



}



void ptc::readError()

{

	QByteArray result= mscn.readAllStandardError();

	    QStringList lines = QString(result).split("\n");

    foreach (QString line, lines) {

        scan_output->append(line);

    }

}
```

i added both functions to the header file ptc.h
```
public:

	ptc(QMainWindow *parent = 0);

	[b]QProcess mscn;
[/b]


	public slots:

		void scan();

		void Escan();

		void comboLineAdd();

		void portComboLineAdd();

		void cmndAdd();

		void newScan();

		void about();

		void howto();

		void terminal();

		bool save();

		bool saveR();

		void open();

		bool mSave();

		**void readError();**
		**void readOutput();**

		QString stName(const QString &fullFileName);

		bool saveFile(const QString &fileName);

     	void loadF(const QString &fileName);

		void sCurrentF(const QString &fileName);
```

this is really stressing :/

thanks for all the help mate :)

---

### Post by tseliot on 2008-12-30
> **Aiman said:**
> im still not sure what im trying to do here,heres the changes i tried ( Did a lot but this is the last one that kinda make sense )

In the constructor (ptc.cpp) i added
```
connect( &mscn, SIGNAL(readyReadStandardOutput()),this, SLOT(readOutput()));

	connect( &mscn, SIGNAL(readyReadStandardError()),this, SLOT(readError()) );
```

if i remove the (&) i get an error

Of course you're getting an error. mscn should be a pointer.

```
QProcess *mscn;
mscn = new QProcess();
```

now you won't need to use & when you connect the signals.

Furthermore scn and mscn are the same, therefore please use just one name otherwise the program won't compile.

At this point I strongly recommend you [this book]("http://www.amazon.com/Introduction-Design-Patterns-Perens-Source/dp/0131879057"). If you read the book you will see how to design a QT4 application and you will also find an example which you can use for your program.

---

### Post by Aiman on 2008-12-30
:D im speechless !!

it did take some time to read the book,and understand the idea
but everything worked fine,i even activated the ARP poisoning function and all works fine
now ill do the mail spoofing function and work on the small details like icons and the keyboard shortcuts.

thanks tseliot for your help :)

---

