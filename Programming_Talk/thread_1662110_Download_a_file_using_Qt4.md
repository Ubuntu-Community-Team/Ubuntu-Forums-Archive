---
title: "Download a file using Qt4"
date: 2011-01-07
forum: Programming Talk
---

### Post by Woody1987 on 2011-01-07
Im having trouble trying to get my program to download a file in Qt4. At some point the user will click a button and a file will be downloaded from the internet.

Code thus far using google.com as an example:
```

void downloadFile()
{
    QString adr = "www.google.com";
    QUrl url = adr;
    QString fileName = "/home/matt/google.txt";

    QFile *file;
    file = new QFile(fileName);
    file->open(QIODevice::WriteOnly);

    QHttp *http = new QHttp();
    http->setHost(url.host(), url.port() != -1 ? url.port() : 80);
    http->get(url.path(), file);
    file->close();
}

```

This code is derived from a networking example from: [http://doc.qt.nokia.com/4.0/network-http.html]("http://doc.qt.nokia.com/4.0/network-http.html")

A file "google.txt" is created but it is blank. How do I make this work?

---

### Post by Woody1987 on 2011-01-09
bump

---

