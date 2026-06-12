---
title: "Qt4 get signal sender"
date: 2011-01-31
forum: Programming Talk
---

### Post by Woody1987 on 2011-01-31
I have a bunch of qcheckboxes. These are created on the fly as the number of qcheckboxes will vary. I do this in a loop as such:

```

for(int i = 0; i < someNumber; i++)
{
    QCheckBox *chk = new QCheckBox("some text");
    ui->detailObjectLayout->addWidget(chk);
}

```

This works fine. But what I want is to connect each qcheckbox to the stateChanged signal, and for that to call a slot which will work like this:

```

void onChkPress(QComboBox *chk)
{
    if(chkbox->isChecked())
    {
        if(chkbox->text() == "some text")
        {
            //do something
        }
        if(chkbox->text() == "some other text")
        {
            //do something else
        }
    }
}

```

How do I connect a signal which will send the current state and the widget to this function?

---

### Post by Woody1987 on 2011-01-31
solved, I added all the qcheckboxes to a QList as they were created, and now i can go through them to find what i need.

---

