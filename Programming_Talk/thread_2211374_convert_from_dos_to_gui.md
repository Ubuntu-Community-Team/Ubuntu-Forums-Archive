---
title: "convert from dos to gui"
date: 2014-03-15
forum: Programming Talk
---

### Post by jgw on 2014-03-15
I have a bunch of programs I wrote, a long time ago, which are still running.  I would like to convert them to gui.  I originally used cscape (codebase for the data which I can easily deal with) but the conversion from cscape is different.  There are a number of ide's available and I would be interested in anybody's thought on which one might be considered the easiest and best.  A couple of ide's I have looked at and seem promising are Anjuta, Geany & Qtcreator.


My code is plain vanilla C and well functioned out with lots of documentation so that part, hopefully, will make it easier.  I have also tried to find somebody to do this but have failed, or am too poor to pay the big bucks, so I guess I will have to make a run at it myself.  I don't need anything visually complicated.  It boils down to menues, notifications, choices, etc.  My thought is to simply convert the existing cscape functions to gui functions.  
 
Thank you................

---

### Post by slooksterpsv on 2014-03-16
I've found that Qt is the easiest for me. The layout structure of GTK type apps is bit foreign to me (even with messing around with it).

For example - here's what I started with in C++ and ended with the same day:

```

#include <iostream>
#include <fstream>
#include <string>
#include <vector>
#include <locale>

std::vector<std::string> GetEachLine(std::string fileName)
{
	std::vector<std::string> tempVector;

	std::ifstream tFile(fileName.c_str());
	if(tFile)
	{
		for(std::string str; std::getline(tFile, str);)
		{
			tempVector.push_back(str);
		}
		return tempVector;
	}
	else
	{
		std::cout << "ERROR!";
	}
	return tempVector;
}

std::vector<std::string> GetEFIBootOrder(std::vector<std::string> efiboot)
{
	std::string bootOrder;
	std::vector bootOrderList;
	for(int x = 0; x < efiboot.size(); x++)
	{
		if(StringStartsWith(efiboot[i], "BootOrder:"))
		{
			bootOrder = efiboot[i];
		}
		if(StringStartsWith(efiboot[i], "Boot", true)
		{
			bootOrderList.push_back(efiboot[i]);
		}
	}
	return bootOrderList;
}

bool StringStartsWith(std::string stringToCheck, std::string startsWith)
{
	int startWithLength = strlen(startsWith);
	if(stringToCheck.compare(0, startWithLength, startsWith) == 0)
	{
		return true;
	}
	return false;
}

bool StringStartsWith(std::string stringToCheck, std::string startsWith, bool containsNumber)
{
	std::locale loc;
	int startWithLength = strlen(startsWith);
	if(stringToCheck.compare(0, startWithLength, startsWith) == 0)
	{
		if(isdigit(stringToCheck[startWithLength], loc))
		{
			return true;
		}
	}
	return false;
}

```

```

#include "mainwindow.h"
#include "ui_mainwindow.h"
#include <QStandardItemModel>
#include <QProcess>
#include <QFile>
#include <iostream>
#include "stkio.h"

using namespace std;


MainWindow::MainWindow(QWidget *parent) :
    QMainWindow(parent),
    ui(new Ui::MainWindow)
{
    QStandardItemModel *stdModel = new QStandardItemModel(this);

    ui->setupUi(this);

    stdModel->insertRow(0, new QStandardItem("EFI Boot Options "));

    ui->listView->setModel(stdModel);

    connect(ui->pushButton, SIGNAL(clicked()), SLOT(PullData()));
    connect(ui->pushButton_2, SIGNAL(clicked()), SLOT(MoveUp()));
    connect(ui->pushButton_3, SIGNAL(clicked()), SLOT(MoveDown()));
    connect(ui->pushButton_4, SIGNAL(clicked()), SLOT(SaveData()));
}

void MainWindow::PullData()
{
    stkio stk;
    vector<string> bootData;
    QStandardItemModel *model = new QStandardItemModel(this);
    model->clear();
    model->appendRow(new QStandardItem("EFI Boot Options"));
    //model->appendRow(new QStandardItem("test"));

    QProcess efiData;
    efiData.start("pkexec efibootmgr");
    efiData.waitForFinished();
    QByteArray output = efiData.readAll();
    efiData.close();

    QFile file("/tmp/efiboot.stk");
    file.open(QIODevice::WriteOnly);
    file.write(output);
    file.close();

    vector<string> values = stk.GetEachLine("/tmp/efiboot.stk");
    vector<string> order = stk.GetEFIBootOptions(values);
    vector<string> fOrder = stk.GetFormattedEFIBootOrder(order, stk.GetEFIBootOrder(values));

    for(unsigned int x = 0; x < fOrder.size(); x++)
        model->appendRow(new QStandardItem(fOrder[x].c_str()));

    ui->listView->setModel(model);
    ui->pushButton_2->setEnabled(true);
    ui->pushButton_3->setEnabled(true);
    ui->pushButton_4->setEnabled(true);
}

void MainWindow::MoveUp()
{
    QStandardItemModel *model = new QStandardItemModel(this);
    model->clear();
    foreach(const QModelIndex &index, ui->listView->selectionModel()->selectedIndexes())
    {
        if(index.row() > 1) {
            std::vector<QString> items;
            for(int i = 0; i < ui->listView->model()->rowCount(); ++i)
            {
                items.push_back(ui->listView->model()->index(i, 0).data().toString());
            }
            QString temp = items[index.row()-1];
            items[index.row()-1] = items[index.row()];
            items[index.row()] = temp;
            for(unsigned int x = 0; x < items.size(); x++)
                model->appendRow(new QStandardItem(items[x]));
            ui->listView->setModel(model);
            ui->listView->setCurrentIndex(ui->listView->model()->index(index.row()-1, 0));
        }

    }
}

void MainWindow::MoveDown()
{
    QStandardItemModel *model = new QStandardItemModel(this);
    model->clear();
    foreach(const QModelIndex &index, ui->listView->selectionModel()->selectedIndexes())
    {
        if(index.row() < ui->listView->model()->rowCount()-1 && index.row() > 0) {
            std::vector<QString> items;
            for(int i = 0; i < ui->listView->model()->rowCount(); ++i)
            {
                items.push_back(ui->listView->model()->index(i, 0).data().toString());
            }
            QString temp = items[index.row()+1];
            items[index.row()+1] = items[index.row()];
            items[index.row()] = temp;
            for(unsigned int x = 0; x < items.size(); x++)
                model->appendRow(new QStandardItem(items[x]));
            ui->listView->setModel(model);
            ui->listView->setCurrentIndex(ui->listView->model()->index(index.row()+1, 0));        }

    }
}

void MainWindow::SaveData()
{
    if(ui->listView->model()->rowCount() > 1)
    {
        std::vector<string> items;
        std::string write;
       for(int i = 0; i < ui->listView->model()->rowCount(); ++i)
        {
            items.push_back(ui->listView->model()->index(i, 0).data().toString().toStdString());
        }
        stkio stk;
        write = stk.GetWriteString(items);
        cout << write;
        QProcess efiData;
        std::string command = "pkexec efibootmgr -o " + write;
        efiData.start(command.c_str());
        efiData.waitForFinished();
        efiData.close();
    } else
    {
        cout << "ERROR PLEASE LOAD UEFIMGR FIRST!";
    }
}

MainWindow::~MainWindow()
{
    delete ui;
}

```

From text program to UI app: [ATTACH=CONFIG]251199[/ATTACH]

---

