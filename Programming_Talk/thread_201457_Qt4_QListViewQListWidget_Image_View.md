---
title: "Qt4 QListView/QListWidget Image View"
date: 2006-06-21
forum: Programming Talk
---

### Post by QMario on 2006-06-21
Hello,

I am trying to show images using a QListWidget, but each time I add a QListWidgetItem to the QListWidget, and run my program, the image doesn't show.

Here is a code snippet of what I mean by adding a QListWidgetItem to the QListWidget:

```

   QPixmap fileImage = QPixmap(imageFilesTemp.at(i));
    fileImage = fileImage.scaled(120,165,Qt::KeepAspectRatio);      
 
    QListWidgetItem* image = new QListWidgetItem(this);
    QIcon imageIcon = QIcon(fileImage);
 
    image->setIcon(imageIcon);
    this->addItem(image);
    this->insertItem(i,image);   

```


What am I doing incorrectly?

---

### Post by raedbenz on 2010-07-24
[http://wiki.forum.nokia.com/index.php/How_to_use_QListWidget_and_QListWidgetItem]("http://wiki.forum.nokia.com/index.php/How_to_use_QListWidget_and_QListWidgetItem")

---

