---
title: "Construct a QUrl"
date: 2012-03-19
forum: Programming Talk
---

### Post by Woody1987 on 2012-03-19
Im trying to download an xml file using QNetworkAccessManager. The url i am using is:

[http://query.yahooapis.com/v1/public/yql?q=select%20*%20from%20yahoo.finance.quotes%20where%20symbol%20in%20(%22LLOY.L%22)%0A%09%09&env=http%3A%2F%2Fdatatables.org%2Falltables.env](http://query.yahooapis.com/v1/public/yql?q=select%20*%20from%20yahoo.finance.quotes%20where%20symbol%20in%20(%22LLOY.L%22)%0A%09%09&env=http%3A%2F%2Fdatatables.org%2Falltables.env)

The QUrl i create from this replaces the % in the url with %25. How do I construct a QUrl from this?

---

### Post by Woody1987 on 2012-03-19
I solved this by using fromPercentEncoding

```

QUrl url = QUrl::fromPercentEncoding("http://query.yahooapis.com/v1/public/yql?q=select%20*%20from%20yahoo.finance.quotes%20where%20symbol%20in%20(%22LLOY.L%22)%0A%09%09&env=http%3A%2F%2Fdatatables.org%2Falltables.env");

```

---

