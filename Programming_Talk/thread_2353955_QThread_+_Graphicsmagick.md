---
title: "QThread + Graphicsmagick"
date: 2017-02-26
forum: Programming Talk
---

### Post by fallenshadow on 2017-02-26
Hi all,

I'm trying to implement a filter worker to filter an image in a separate thread, then return the image afterwards. However, it doesn't work at the moment. Any ideas? Its hard to debug an issue without an actual error showing up.


filterworker.cpp

```
#include "filterworker.h"
#include "FilterManager.h"
#include "PaintWidget.h"
#include <QDebug>

FilterWorker::FilterWorker(QObject *parent) : QObject(parent)
{

}

void FilterWorker::setImage(QImage image)
{
    currentImage = image;
}

void FilterWorker::process()
{
    qDebug() << "test";
     QImage newImage;
    newImage = FilterManager::instance()->wave(currentImage);

    emit fileProcessFinished(newImage);
}

```

filterworker.h

```
#ifndef FILTERWORKER_H
#define FILTERWORKER_H

#include <QObject>
#include "mainwindow.h"

class FilterWorker : public QObject
{
    Q_OBJECT
public:
    //FilterWorker();
    explicit FilterWorker(QObject *parent = 0);
    void setParent(MainWindow* parent){m_parent = parent;}
    void setImage(QImage image);

public slots:
    void process();

signals:
    void fileProcessFinished(QImage image);

private:
    MainWindow* m_parent;
    QImage currentImage;
};

#endif // FILTERWORKER_H

```

mainwindow.cpp - on_image_filtered(QImage image)

```
void MainWindow::on_image_filtered(QImage image)
{
    PaintWidget *widget = getCurrentPaintWidget();
    if (widget)
        widget->setImage(image);
}
```

mainwindow.cpp -on_actionSwirl_triggered()

```
QThread *thread = new QThread();
    FilterWorker *worker = new FilterWorker();

    PaintWidget *widget = getCurrentPaintWidget();
    if(widget)
    worker->setImage(widget->image());

    worker->setParent(this);
    worker->moveToThread(thread);

    connect(thread, SIGNAL(started()), worker, SLOT(process()));
    connect(worker, SIGNAL(fileProcessFinished(QImage)), this, SLOT(on_image_filtered(QImage)));

    thread->start();
```

If you want to play around with the code you can take a fork here: [https://github.com/PhotoFiltre-LX/photofiltrelx]("https://github.com/PhotoFiltre-LX/photofiltrelx")

I would gladly accept a contribution if someone can figure it out.

---

### Post by norobro on 2017-02-26
Very impressive application.

I was using Qt-5.5.1 and encountered errors with QImage::pixelColor() and QImage::setPixelColor(). They were added in 5.6 so you might up your version check from 5.0.0. I had to add "#include <QMessageBox>" to batchdialog.cpp also.

How is it not working? In the absence of an image that takes a long time to process (swirl), I added sleep(30) to FilterWorker::process(). Control returned to the mainWindow immediately where I was able to load another image and perform other tasks.

---

### Post by fallenshadow on 2017-02-27
> Very impressive application.

Thanks! It has had so many hours of hard work already! I could stop but I wanna keep going with it.

I have updated both the missing include statement and bumped the Qt version. (good idea!)

The QThread is working fine. It will go to the filterworker and return to the main UI. The problem is the image does not get the effect applied. =/

---

### Post by norobro on 2017-02-27
Sorry, I don't see the problem here. Attached is a screenshot of an arrow "swirl"ed once. I was able to save the image and reload it.

---

### Post by fallenshadow on 2017-02-27
Holy moly! I just got this working tonight! xD  I'll write up on how I fixed it later on! (but first sleep)

---

### Post by fallenshadow on 2017-02-28
So basically while the old code was working for you it was doing the work on the main thread. The code on github didn't have some of the above test code. It would have worked but would have been very slow on large images. 

To get the filterworker working as expected I had to move the public function **on_image_filtered** from the _public functions_ to a _public slot_ inside the mainwindow.h. Then the image was returned to the main thread as expected. :)

---

### Post by fallenshadow on 2017-03-14
Thanks for testing it out anyway! The code for this will make its way into the GitHub source soon enough. When you test the older version on big images and test the new version you will definitely notice a huge performance difference.

---

