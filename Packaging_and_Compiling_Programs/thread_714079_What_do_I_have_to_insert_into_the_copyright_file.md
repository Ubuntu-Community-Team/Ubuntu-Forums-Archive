---
title: "What do I have to insert into the copyright file?"
date: 2008-03-03
forum: Packaging and Compiling Programs
---

### Post by Adnarim on 2008-03-03
Hi,
I'm creating a deb package and have some questions regarding the copyright file.The default one looks like this here:
```

 This package was debianized by adnarim <adnarim@pochta.ru> on
Mon, 03 Mar 2008 18:38:14 +0100.

It was downloaded from <url://example.com>

Upstream Author(s):

    <put author's name and email here>
    <likewise for another author>

Copyright:

    <Copyright (C) YYYY Name OfAuthor>
    <likewise for another author>

License:

    This package is free software; you can redistribute it and/or modify
    it under the terms of the GNU General Public License as published by
    the Free Software Foundation; either version 2 of the License, or
    (at your option) any later version.


```


Okay by:
```

It was downloaded from <url://example.com>

```
Comes here the acutal downloadlocation of the sources?

And what's the difference between these fields:
```

Upstream Author(s):

    <put author's name and email here>
    <likewise for another author>

```
```

Copyright:

    <Copyright (C) YYYY Name OfAuthor>
    <likewise for another author>

```
Who's the upstream author of an application and whats the difference between the second part?

greets

---

### Post by Vorian on 2008-03-03
The answer to your first question:  Enter the url of the site you downloaded the package.  It doesn't need to be the actual download link.

The second question:  List the Author or Authors then the copyright, like

Upstream Author: 
      Upstream Dude <usdude@kewlpackage.net>

Copyright: 
      (C) 2008 Upstream Dude 

[Here is a copyright you can check out ]("http://revu.tauware.de/revu1-incoming/kio-ftps-kde4-0802200500/kio-ftps-kde4-0.2/debian/copyright")

---

### Post by WW on 2008-03-04
The "upstream author" is the developer of the program.  If you are packaging a program that you wrote, then you are the upstream author.  In Debian (and therefore Ubuntu), it is very common for someone other than the original author to create the debian package.

---

### Post by Adnarim on 2008-03-04
Okay thank you very much I think I got it now :)

---

