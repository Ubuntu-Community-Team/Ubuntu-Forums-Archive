---
title: "What are resouce files?"
date: 2008-08-23
forum: Programming Talk
---

### Post by StOoZ on 2008-08-23
I see in netbeans , in my project tree , a node with the name "Resource Files" , so what are they?

10x

---

### Post by mike_g on 2008-08-23
I'm not sure about this, but I think they hold stuff like the icons for executables on Windows.

Edit: [http://angusj.com/resourcehacker/](http://angusj.com/resourcehacker/)

---

### Post by aloshbennett on 2008-08-23
Resources contain any image, and other media files you application might be needing. Instead of refering to an image by the path, if you add it to the resources folder you can access it by APIs like getResource().

Finally, when you build your application, the resources are included into the jar and all you need to do is ship a single jar file.

---

### Post by StOoZ on 2008-08-23
sound interesting , do you know of a good tutorial about that ??? (found one on MSDN , but its not that good)

---

### Post by aloshbennett on 2008-08-23
Its spread all over the place. You could find something about creating jar files and how to include images in them.

To retrieve them, you can look at the Class.getResource() method.

---

