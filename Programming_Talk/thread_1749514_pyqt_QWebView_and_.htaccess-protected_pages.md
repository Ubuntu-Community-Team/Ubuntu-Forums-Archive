---
title: "pyqt QWebView and .htaccess-protected pages"
date: 2011-05-04
forum: Programming Talk
---

### Post by lykwydchykyn on 2011-05-04
I have a utility I wrote in pyQT that accesses several password-protected pages in a QWebView.  The pages use basic .htaccess/apache security, and run on various debian squeeze servers running apache2.

It worked fine for a long time, then at some point it stopped (I only occasionally use this function of the utility, so I'm not sure what proceeded the failure).

I wrote this demo code:
```


from PyQt4.QtGui import *
from PyQt4.QtCore import *
from PyQt4.QtWebKit import *


app = QApplication([])

w = QWebView()

w.show()

url = QUrl("http://some/secure/site")
url.setUserName("myuser")
url.setPassword("correctpassword")

print url.toString()

w.load(url)

app.exec_()

```

I cannot get this code to connect to any .htaccess password-protected site that I know of.  What am I doing wrong?


EDIT: I should add, the error in the apache logs basically indicates the wrong password, but I know I'm using the correct one.  If I copy the URL that this script produces and paste it into any conventional browser, it logs in fine.

---

### Post by lykwydchykyn on 2011-05-12
bump...

---

