---
title: "[C++] - Crescendo - QtSql Problem"
date: 2007-11-15
forum: Programming Talk
---

### Post by open_coder on 2007-11-15
Hello,

I have been working on a music collection and organization application for the better part of this semester. It is part of my Capstone Graduation Project. I have decided to use the following libraries:
[LIST]
[*]Qt4
[*]SQLite
[*]Gstreamer or MPD
[*]ID3lib
[/LIST]

I am using the Qt wrapper for SQL execution. And I have a big problem. When trying to write data to the database, the tables never get populated. I can retrieve information from the database. I made a database with a bunch of dummy values using "sqlite3 db" from the command line. And when I run the Qt application, it displays the "artists" table. However, I cannot insert these values from the actual application. Is there some kind of read-write setting that I need to change? How would I do this? Is there a way to check if the application has access to the database? The db can be opened, because it displays the table in a window. Does anybody know how to get this working?

Below is the code for the SQL program that I am writing currently. Keep in mind that this application is a test application. All the values within it are Dummy values that do not correspond to any real files on a computer.

crescql.h:
```
#ifndef CRESCQL_H
#define CRESCQL_H

#include <QWidget>
#include <QtSql>
#include <QTableView>
class QSqlDatabase;

class Crescql : public QWidget
{
	Q_OBJECT
	
	public:
		Crescql(QWidget *parent = 0);
		int dbAddRecord();
		int dbRemRecord();
		int dbCreateTables();
		QSqlTableModel *dbCreateModel();
		QTableView *dbCreateView(QSqlTableModel *model);
		
	private:
		QSqlDatabase music;
};

#endif 
```

crescql.cpp
```
#include <QtSql>
#include <QPushButton>
#include <QVBoxLayout>
#include <QTableView>
#include <QMessageBox>
#include <iostream>
#include "crescql.h"

using namespace std;

Crescql::Crescql(QWidget *parent)
	:QWidget(parent)
{
	music = QSqlDatabase::addDatabase("QSQLITE", "musicconnection");
	music.setDatabaseName("crescdb");
	if(music.open())
		cout<<"problem opening db";
	
	QSqlQuery query(music);
	
	QVBoxLayout *layout = new QVBoxLayout;
	layout->addWidget(dbCreateView(dbCreateModel())); //create the view/model and add to layout
	setLayout(layout);
}

int Crescql::dbCreateTables()
{
	QSqlQuery query(music);
	query.exec("create table artists(id int primary key, artist varchar(20))");
	
	//set up the artists
	query.exec("insert into artist values(0, 'Billy') "); 
	return 0;
}


int Crescql::dbRemRecord()
{
	QSqlQuery query(music);
	
	return 0;
}

QSqlTableModel* Crescql::dbCreateModel()
{
	QSqlTableModel *model = new QSqlTableModel(this, music);
	model->setTable("artists");
	model->select();
	
	model->setHeaderData(0, Qt::Horizontal, QObject::tr("Id"));
	model->setHeaderData(1, Qt::Horizontal, QObject::tr("Artist"));
	
	return model;
}

QTableView *Crescql::dbCreateView(QSqlTableModel *model)
{
	QTableView *playlist = new QTableView;
	playlist->setModel(model);
	return playlist;
}
```

main.cpp:
```
#include <QApplication>
#include <QWidget>
#include <QVBoxLayout>
#include <QPushButton>
#include "crescql.h" 

class MyWidget : public QWidget
{
	public:
		MyWidget(QWidget *parent = 0);
};

MyWidget::MyWidget(QWidget *parent)
	:QWidget(parent)
{
	Crescql *db = new Crescql();
	
	QVBoxLayout *layout = new QVBoxLayout;
	layout->addWidget(db);
	setLayout(layout);
	
}

int main (int argc, char *argv[])
{
	QApplication app(argc, argv);
	MyWidget widget;
	widget.show();
	
	return app.exec();
}
```

Also, I want to add, that I tried to run the example program form the documentation, and it didn't work either.

Thanks,

OC

---

### Post by katu on 2008-05-12
Which version of qt are you on? Also did you solve your problem? 
I have a similar one. I tried the qt-interest archive:
[http://lists.trolltech.com/qt-interest/2008-04/thread00907-0.html](http://lists.trolltech.com/qt-interest/2008-04/thread00907-0.html)

But I got no reply. 
the really strange thing is the code (in a much more advanced version) worked with qt3.3. I'm probably gonna try to recompile qt from source, and see how that works. When and if I find the time.

---

### Post by dwhitney67 on 2008-05-12
How come you are not examining the return value from query.exec() statements?  I have no experience with QtSql, however the API looks very similar to MySQL++.  Maybe if you examine the return value and/or examine the reason why the query is not succeeding you may learn something that is not readily obvious.

---

