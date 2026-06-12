---
title: "Qt Signal Connect Problem"
date: 2008-12-14
forum: Programming Talk
---

### Post by Jay3205 on 2008-12-14
I'm a relatively new programmer, and I'm trying to make a program to play a collectible card game online using Qt and QDevelop IDE. However, I'm currently running into a problem trying to connect a signal from my main window class to a player class slot. It compiles fine, but it crashes the program when the program is run. Here's the code:

MAIN WINDOW header ifle 
```
#ifndef MAINWINDOWIMPL_H
#define MAINWINDOWIMPL_H

#include <QMainWindow>
#include "ui_mainwindow.h"
#include "card.h"
#include "definitions.h"
#include "player.h"
#include "bigPic.h"

class MainWindowImpl : public QMainWindow, public Ui::MainWindow
{
Q_OBJECT
	public:
		MainWindowImpl( QWidget * parent = 0, Qt::WFlags f = 0 );
		
		// the various parts of the form
		QGraphicsScene playerFieldScene;
		QGraphicsScene opponentFieldScene;
		QGraphicsScene bigPicScene;
		QGraphicsScene handScene;
		BigPic bigPic;	
		
		Player * player;
		Player * opponent;
		
	private:
		void startup();
		void initializeBigPic();
		
	signals:
		void loadPlayerDeck(QString filename);

	public slots:
		void resetPlayers();

};
#endif
```

MAIN WINDOW cpp
```
#include "mainwindowimpl.h"
#include <QtGui>

MainWindowImpl::MainWindowImpl( QWidget * parent, Qt::WFlags f) 
	: QMainWindow(parent, f)
{
	// load the user interface
	setupUi(this);
	
	startup(); 
	
	// load the player's deck
	emit loadPlayerDeck("");
	
	// initialize the big pic
	initializeBigPic();
	
}

// attach scenes to views and handle all signal/slot connections
void MainWindowImpl::startup()
{
	// attach scenes to views
	playerFieldView->setScene(&playerFieldScene);
	opponentFieldView->setScene(&opponentFieldScene);
	bigPicView->setScene(&bigPicScene);
	handView->setScene(&handScene);
	
	// signal and slot connections **** FOLLOWING LINE CAUSES RUNTIME PROBLEM ******
	connect(this, SIGNAL(loadPlayerDeck(QString)), player, SIGNAL(loadDeck(QString)));
	
}

/* initialize the scene containing the big picture of a card */
void MainWindowImpl::initializeBigPic()
{
	// render the big picture
	bigPicScene.addItem(&bigPic);
		
	//bigPic.setTransform(QTransform().rotate(60, Qt::YAxis));
}

// reset the deck, field, grave, hand, and mana zone of each player
void MainWindowImpl::resetPlayers(){
	player->resetZones();
	opponent->resetZones();
	
}
```

PLAYER header file
```
#ifndef __PLAYER_H__
#define __PLAYER_H__

#include <QObject>
#include "card.h"
#include "definitions.h"

class Player : public QObject
{
	Q_OBJECT
	
	public:
		Player();
		
	    QString name;
	    QList<Card *> deck;		// position 0 is the top of the deck
	    QList<Card *> field;
	    QList<Card *> mana;
	    QList<Card *> grave;
	    QList<Card *> hand;
	    
    	void setDeck(QList<Card *> newDeck);
		void resetZones();
		
	signals:
	
	public slots:
		void loadDeck(QString filename);
	
};

#endif 
```

When I run this, it crashes with the following message:
```
Program received signal SIGSEGV, Segmentation fault.
0xb7223d8b in QObject::connect (sender=0xbfee6e90, signal=0x80509f8 "loadPlayerDeck(QString)", receiver=0x804b728, method=0x80509e5 "loadDeck(QString)", type=Qt::AutoConnection) at kernel/qobject.cpp:2403
```

Any help would be *greatly* appreciated.

---

### Post by scourge on 2008-12-15
You're telling the connect function that Player::loadDeck is a signal, when it's actually a slot.

Change this:
```
connect(this, SIGNAL(loadPlayerDeck(QString)), player, SIGNAL(loadDeck(QString)));
```
to this:
```
connect(this, SIGNAL(loadPlayerDeck(QString)), player, SLOT(loadDeck(QString)));
```

Btw, instead of passing containers like QList and QString by value, you should pass them by const reference.

---

### Post by Jay3205 on 2008-12-15
I've made the change, but it is still the same error. I've tried connecting them as a signal and a slot, and I've changed loadDeck into a signal and tried connecting them, but it gives the same error. However, when I make the following change, the program works:

replace:
```
// signal and slot connections 
	connect(this, SIGNAL(loadPlayerDeck(QString)), player, SIGNAL(loadDeck(QString)));

```
with
```
// signal and slot connections 
        Player * p;
	connect(this, SIGNAL(loadPlayerDeck(QString)), p, SIGNAL(loadDeck(QString)));

```
Of course, doing this doesn't really solve the problem, and I have no idea why that even works. Any more recommendations?

---

### Post by scourge on 2008-12-15
Looks like you're not initializing the player. You should have "player = new Player;" in MainWindowImpl's constructor (and delete it in the destructor).

---

### Post by Jay3205 on 2008-12-15
Thanks! Not intializing it was the problem.

---

