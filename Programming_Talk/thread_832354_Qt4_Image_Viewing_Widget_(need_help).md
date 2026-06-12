---
title: "Qt4 Image Viewing Widget (need help)"
date: 2008-06-17
forum: Programming Talk
---

### Post by Dambrosio on 2008-06-17
Hello,
I am working on a simple image viewer widget that initially sets a size and fills the background of the widget then has the option to load a new image in. When I promote my regular widget into a the EngineViewer nothing happens, no background fill or size readjustment. Anyone have an Idea?
Thanks,
Dan

**engineviewer.h**
```
#ifndef ENGINEVIEWER_H
#define ENGINEVIEWER_H

#include <QImage>
#include <QWidget>
//
class EngineViewer : public QWidget
{
Q_OBJECT
public:
	EngineViewer(QWidget *parent=0);
	void setEngineImage(const QString &imageLocation);
private:
	QImage engineImage;
	
};
#endif
```
**engineviewer.cpp**
```
#include <QtGui>
#include "engineviewer.h"

EngineViewer::EngineViewer( QWidget *parent ) 
	: QWidget(parent)
{
	setAttribute(Qt::WA_StaticContents);
	setSizePolicy(QSizePolicy::Preferred,QSizePolicy::Preferred);
	engineImage = QImage(450,242,QImage::Format_ARGB32);
	engineImage.fill(qRgba(0,0,0,255));
	update();
	updateGeometry();
	// TODO
}

void EngineViewer::setEngineImage(const QString &imageLocation)
{
	
	QImage newImage(imageLocation);
	if(newImage != engineImage)
	{
		engineImage.convertToFormat(QImage::Format_ARGB32);
		update();
		updateGeometry();
	}
}
//
```

---

