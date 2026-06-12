---
title: "Qt (creator) problem - setting a labels text"
date: 2009-11-19
forum: Programming Talk
---

### Post by matmatmat on 2009-11-19
I am trying to make a simple media player with Qt (creator), the problem is I am trying to set the text of a label with the filename:
```

void MainWindow::setLabel(QString s){
    ui->label->setText(s);
}

void MainWindow::setLabelNowPlaying(){
    std::string stds;
    stds = "Now playing ";
    stds += mediaObject->currentSource().fileName().toStdString();
    std::cout << stds << "\n";
    QString s;
    s.fromStdString(stds);
    ui->label->setText(s);
    std::cout << s.toStdString() << "\n";
}

```
but when setLabelNowPlaying is called the label text is set blank, the problem seems to be converting from std::string to QString, please help!

---

### Post by matmatmat on 2009-11-20
bump?

---

### Post by haTem on 2009-11-20
Could you post a sample default.session file? The program does not run without it.

---

### Post by haTem on 2009-11-20
Er, never mind, I think I see your problem.

fromStdString is a static method, so you should use it like this:

```

QString s = QString::fromStdString(stds);

```

---

