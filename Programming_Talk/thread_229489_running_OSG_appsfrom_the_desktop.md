---
title: "running OSG appsfrom the desktop"
date: 2006-08-04
forum: Programming Talk
---

### Post by Hacim on 2006-08-04
Hi I was wondering why I can't run apps made with OpenSceneGraph from desktop instead of the terminal?If I click on them nothing happens anyone know why that is?

thanks.

---

### Post by Robert Osfield on 2006-08-05
> **Hacim said:**
> Hi I was wondering why I can't run apps made with OpenSceneGraph from desktop instead of the terminal?If I click on them nothing happens anyone know why that is?

thanks.

Most of the OpenSceneGraph applications/examples are designed to run with an argument passed in on the command line, so if you run from the desktop they will just exit.

The OpenSceneGraph is middleware, so is used by developers to develop their own simulators or games.  The applications that come with the OpenSceneGraph distribution exist primarily as examples to help developers learn how to program with the API, rather to used by an end user.  For this reason you won't find any GUI applications, its purely graphics focused.

For OpenSceneGraph support you'll find it best to use the osg-users mailing list:
 
    [http://www.openscenegraph.org/support](http://www.openscenegraph.org/support)

---

