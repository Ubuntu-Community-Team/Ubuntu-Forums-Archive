---
title: "loading XML content through XPATH in QML"
date: 2013-02-22
forum: Programming Talk
---

### Post by Nr90 on 2013-02-22
Dear all,
I have been playing with the Ubuntu touch SDK and I wanted to create an app that shows some content from a webpage. I have no experience working with QML or Xpaths.

The start of the source file of the webpage is:

```

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xmlns:fb="http://www.facebook.com/2008/fbml">

```

This is my XmlListModel:
```

XmlListModel {
        id: contentFetcher
        source: "http://www.nu.nl/buitenland/3270318/gedetineerde-slaat-directielid-ziekenhuis-in.html"
        namespaceDeclarations: "declare namespace fb='http://www.facebook.com/2008/fbml';"
            +"declare default element namespace 'http://www.w3.org/1999/xhtml';"
        query: "//*[@id='leadarticle']/div[2]"

        onStatusChanged: {
            if (status === XmlListModel.Ready) {
                for (var i = 0; i < count; i++)
                    inhoud.append("inhoud")
            }
        }

        XmlRole { name: "inhoud"; query: "@p/string()" }
    }

```

I have tried to declare the namespace using the xmlns values of the source page.
When running qmlscene I get the error:
```
Error FODC0002 in tag:trolltech.com,2007:QtXmlPatterns:QIODeviceVariable:src, at line 162, column 66: Expected '#' or '[a-zA-Z]', but got '&'.
```
Which I believe to occur when QML fails to find readable XML at the source. Is this correct?
What mistakes did I make here?

Thanks in advance

---

