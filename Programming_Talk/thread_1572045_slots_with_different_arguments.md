---
title: "slots with different arguments"
date: 2010-09-10
forum: Programming Talk
---

### Post by syd919 on 2010-09-10
Hello Im new to qt and I have a problem, I am trying to connect a radio button to a signal and a slot that have different number of arguments,I know this is not possible, is the any way to get around it?

here is my code:

void myclass::createbutton()
  {
  QRadiobutton* radio= new QRadiobutton("word")
 connect(radio, Signal(clicked),this,SLOT(checkedA(QRadiobutton)))
 }

void myclass::checkedA(QRadiobutton* radio)
 {
useranswers.push(radio); //where useranswers is a stack
 }

---

### Post by spjackson on 2010-09-10
> **syd919 said:**
> Hello Im new to qt and I have a problem, I am trying to connect a radio button to a signal and a slot that have different number of arguments,I know this is not possible, is the any way to get around it?

here is my code:

void myclass::createbutton()
  {
  QRadiobutton* radio= new QRadiobutton("word")
 connect(radio, Signal(clicked),this,SLOT(checkedA(QRadiobutton)))
 }

void myclass::checkedA(QRadiobutton* radio)
 {
useranswers.push(radio); //where useranswers is a stack
 }

You cannot do it like that. The simplest solution is to make radio a member of myclass, which is only a problem if you want to connect many QRadioButtons to that same slot. In that case you are supposed to use QSignalMapper.

However, here is some code (untested) that is reasonably close to what you have.

```

void myclass::createbutton()
{
  QRadiobutton* radio= new QRadiobutton("word");
  connect(radio, SIGNAL(clicked()),this,SLOT(checkedA()));
}

void myclass::checkedA()
{
  QRadioButton * radio = qobject_cast<QRadioButton>(sender());

  if (radio) {
    useranswers.push(radio); //where useranswers is a stack
  }
}

```If you are going to be learning Qt, then I strongly recommend [http://lists.trolltech.com/mailman/listinfo/qt-interest](http://lists.trolltech.com/mailman/listinfo/qt-interest) as an excellent resource.

---

### Post by syd919 on 2010-09-10
if i make radio of type myclass i still dont understand how I would call the slot without arguments

---

### Post by spjackson on 2010-09-10
> **syd919 said:**
> if i make radio of type myclass i still dont understand how I would call the slot without arguments
Not of type myclass, but a *member* of myclass, as I said before.
```

class myclass {
.
.
  QRadioButton * radio;
};

void myclass::createbutton() {
  radio= new QRadiobutton("word");
  connect(radio, SIGNAL(clicked()),this,SLOT(checkedA()));
}

void myclass::checkedA() {
     if (radio) {
       useranswers.push(radio); //where useranswers is a stack
   }
}

```But as I said before, this only works if there is only one object's signal connected to this slot.

---

### Post by syd919 on 2010-09-11
Sorry for taking so long to reply and sorry I didnt mention this earlier on but I will be using many buttons, I tried qsignalmapper here is my code:

class myclass {
.
.
  QRadioButton * radio1;
QRadioButton * radio2;
.
.
.

 QRadioButton * radio40;
};

void myclass::createbutton() {
  radio1= new QRadiobutton("word");
  radio2= new QRadiobutton("word");
.
.
.
  radio40= new QRadiobutton("word");


  QSignalMapper *mapper = new QSignalMapper( this );

 mapper->setMapping( radio1, "0" );
  mapper->setMapping( radio2, "1" );
connect( radio1, SIGNAL(clicked()), mapper, SLOT(map()) );
  connect( radio2, SIGNAL(clicked()), mapper, SLOT(map()) );

connect( mapper, SIGNAL(mapped(QRadiobutton)), this, SLOT(checkedA(QRadiobutton)) );
}

the compiler complains that there is no such slot mapper(Qradiobutton)

---

### Post by spjackson on 2010-09-11
You cannot pass QRadioButton by value, you need pointers.
```

connect( mapper, SIGNAL(mapped(QRadiobutton *)), this, SLOT(checkedA(QRadiobutton *)) );

```

---

