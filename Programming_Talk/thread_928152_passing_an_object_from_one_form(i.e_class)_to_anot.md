---
title: "passing an object from one form(i.e class) to another class c++ &amp; Qt"
date: 2008-09-23
forum: Programming Talk
---

### Post by cbarmpar on 2008-09-23
Hi all,

I am new to both Linux and c++.

I just made the next step to start making applications that make sense but it seems that i get confused easy.

I have a main window(kentriko class). I have a dialogue used to initiate a database connection (class database). This dialogue is called from the mainwindow to create the database connection. The dialogue return the database ( *d.get_db() ).

I want to use this connection to make queries from another form called kentriko (kentriko class). This class is subwindowed. This allows me to instate many instances of this window all of the using the same database.

The problem is that I am making a mistake in the constructors somehow and the pointers to the database are not passed. the code is listed bellow.

Any help will be much appreciated.

parathiro implementation:
```
#include "parathiro.h"
#include <iostream>
#include <QString>
#include "../diafores_sinartisis/sinartisis.h"
#include "../database/database.h"

using namespace std;
parathiro::parathiro(QWidget *parent,database  d)//<-- here i pass the oject (the database connection dialog)//
    : QMainWindow(parent)
{
	ui.setupUi(this);
	connect(ui.anixe, SIGNAL(clicked()) , this , SLOT(anixe()));
	connect(ui.pare, SIGNAL(clicked()) , this , SLOT(pare()));
	connect(ui.proto,SIGNAL(textChanged(const QString&)),this,SLOT(alagi()));
}

void parathiro::alagi(){
  QSqlQuery erotisi(*d.get_db());//<- here i attempt to use it//
  proto = sinartisi_SELECT( "onoma,epitheto" ,"onomata", "onoma", ui.proto->text());
  ui.deytero->setText(proto);
  erotisi.exec(proto);
  variant = erotisi.size();
  ui.trito->setText(variant.toString());
}
```

parathiro header:

```
#ifndef PARATHIRO_H
#define PARATHIRO_H

#include <QtGui/QMainWindow>
#include "ui_parathiro.h"
#include "../database/database.h"

class parathiro : public QMainWindow
{
    Q_OBJECT
public:
    parathiro(QWidget *parent = 0, database d );
    ~parathiro();
private slots:
     void anixe();
     void pare();
     void alagi();
private:
    Ui::parathiroClass ui;
    QString  proto;
    QString  deytero;
    QVariant variant;
};
```

kentriko implementation:
```
#include "kentriko.h"
#include <iostream>
#include <QString>
#include "../diafores_sinartisis/sinartisis.h"
#include <QMdiArea>
#include <QMdiSubWindow>
#include "../kentriko/parathiro/parathiro.h"

using namespace std;

kentriko::kentriko(QWidget *parent)
    : QMainWindow(parent)
{
	ui.setupUi(this);
	connect(ui.neo_parathiro, SIGNAL(triggered()), this, SLOT(anixe()));
	connect(ui.sindesi,SIGNAL(triggered()),this,SLOT(sindesi()));
}
void kentriko::anixe(){
    parathiro *para = new parathiro(0,d);//<- here i am trying to pass it to the new parathiro//
	QMdiSubWindow *subwindow = ui.mdiArea->addSubWindow(para);
	subwindow->setAttribute(Qt::WA_DeleteOnClose);
	subwindow->resize(sizeHint());
	subwindow->show();
}

void kentriko::sindesi(){
	database* d;//<<<<- here i am creating the pointer to the database class//
	d->show();
}
```

database implementation:
```
#include "database.h"

database::database(QWidget *parent) :
	QDialog(parent) {
	ui.setupUi(this);
	db = QSqlDatabase::addDatabase("QMYSQL");
	connect(ui.sindesi, SIGNAL(clicked()), this, SLOT(sindesou()));
	connect(ui.aposindesi, SIGNAL(clicked()), this, SLOT(aposindesou()));
	connect(ui.pliroforia_k, SIGNAL(clicked()), this, SLOT(pliroforia()));
}
void database::sindesou() {
	ena.pinakas = ui.pinakas->text();
	ena.onoma = ui.onoma->text();
	ena.kodikos = ui.kodikos->text();
	if (!db.isOpen()) {
		db.setDatabaseName(ena.pinakas);
		db.setUserName(ena.onoma);
		db.setPassword(ena.kodikos);
		db.setHostName("127.0.0.1");
		db.setPort( 3306);
		if (!db.open()) {
			ui.katastasi->setText("Not connected");
		} else {
			ui.katastasi->setText("connected");
		}
	} else {
		ui.katastasi->setText("It has already been connected");
	}
}
void database::aposindesou() {
	db.close();
}
void database::pliroforia() {
	ena.pliroforia = ui.pliroforia->text();
}
A * database::get_alpha() {
	return &ena;
}
QSqlDatabase * database::get_db() {
	return &db;//<<<<---- here i am returning the database connection from the database class in order to use it on the parathiro.
}
database::~database() {
	db.close();
}

```

i have also attached the source code.
Many thanks in advance.

---

