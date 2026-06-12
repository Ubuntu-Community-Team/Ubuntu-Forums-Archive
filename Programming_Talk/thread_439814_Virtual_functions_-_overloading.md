---
title: "Virtual functions - overloading?"
date: 2007-05-11
forum: Programming Talk
---

### Post by aquavitae on 2007-05-11
I'm writing a class called BOQStdItem which inherits Qt's QStandardItem.  In it, I reimplement the member function data(int) which is declared as virtual in QStandardItem. If I do something like
```

QStandardItem* item = new BOQStdItem();
item->data(Qt::DisplayRole);
```
the debug message that I have implemented in data() is not displayed.  I assume then that its calling QStandardItem::data(int) rather than BOQStdItem::data(int).

How can I get it to call BOQStdItem::data(int) without doing a cast?

Here's an extract of my inherited class.
```

/// boqstditem.h

class BOQStdItem : public QObject, public QStandardItem {

   Q_OBJECT
   
   public:
      BOQStdItem(BOQStdRow* vparentrow);
      virtual ~BOQStdItem();
   
      //! Returns the data for a specific role
      virtual QVariant data(int role = Qt::UserRole + 1);
      
      //! Sets the data, and emits a signal notifying of the change
      virtual void setData(const QVariant &value, int role = Qt::UserRole + 1);

      bool visible;

   signals:
   
      //! Emitted when the data in the item changes
      void dataChanged(QVariant value);
};



///boqstditem.cpp

BOQStdItem::BOQStdItem(BOQStdRow* vparentrow) : QObject(vparentrow) { }

BOQStdItem::~BOQStdItem() { }
   
//! Returns the data for a specific role
QVariant BOQStdItem::data(int role) {
   qDebug() << "Reading data";
   if (visible) {
      switch (role) {
         case Qt::DisplayRole | Qt::EditRole:
            return text();
            break;
               
         case Qt::CheckStateRole:
            return checkState();
            break;
            
         default:
            return QVariant();
            break;
      }
   } else
      return QVariant();
}

//! Sets the data, and emits a signal notifying of the change
void BOQStdItem::setData(const QVariant &value, int role) {
   if (role = Qt::EditRole)
      emit(dataChanged(value));
   else if (role == Qt::CheckStateRole)
      emit(checkStateChanged(value.toInt()));
   QStandardItem::setData(value, role);
}

```

---

### Post by cwaldbieser on 2007-05-11
> **aquavitae said:**
> I'm writing a class called BOQStdItem which inherits Qt's QStandardItem.  In it, I reimplement the member function data(int) which is declared as virtual in QStandardItem. If I do something like
```

QStandardItem* item = new BOQStdItem();
item->data(Qt::DisplayRole);
```
the debug message that I have implemented in data() is not displayed.  I assume then that its calling QStandardItem::data(int) rather than BOQStdItem::data(int).

How can I get it to call BOQStdItem::data(int) without doing a cast?

Here's an extract of my inherited class.
```

/// boqstditem.h

class BOQStdItem : public QObject, public QStandardItem {

   Q_OBJECT
   
   public:
      BOQStdItem(BOQStdRow* vparentrow);
      virtual ~BOQStdItem();
   
      //! Returns the data for a specific role
      virtual QVariant data(int role = Qt::UserRole + 1);
      
      //! Sets the data, and emits a signal notifying of the change
      virtual void setData(const QVariant &value, int role = Qt::UserRole + 1);

      bool visible;

   signals:
   
      //! Emitted when the data in the item changes
      void dataChanged(QVariant value);
};



///boqstditem.cpp

BOQStdItem::BOQStdItem(BOQStdRow* vparentrow) : QObject(vparentrow) { }

BOQStdItem::~BOQStdItem() { }
   
//! Returns the data for a specific role
QVariant BOQStdItem::data(int role) {
   qDebug() << "Reading data";
   if (visible) {
      switch (role) {
         case Qt::DisplayRole | Qt::EditRole:
            return text();
            break;
               
         case Qt::CheckStateRole:
            return checkState();
            break;
            
         default:
            return QVariant();
            break;
      }
   } else
      return QVariant();
}

//! Sets the data, and emits a signal notifying of the change
void BOQStdItem::setData(const QVariant &value, int role) {
   if (role = Qt::EditRole)
      emit(dataChanged(value));
   else if (role == Qt::CheckStateRole)
      emit(checkStateChanged(value.toInt()));
   QStandardItem::setData(value, role);
}

```

```

virtual QVariant data ( int role = Qt::UserRole + 1 ) const

```

You did not customize the QStandardItem method because you forgot the "const".

---

### Post by aquavitae on 2007-05-11
I knew I'd done something silly!

Thanks.

---

