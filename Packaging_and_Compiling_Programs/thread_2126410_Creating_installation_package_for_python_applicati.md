---
title: "Creating installation package for python application"
date: 2013-03-17
forum: Packaging and Compiling Programs
---

### Post by niranjan_rao on 2013-03-17
First logged the question at [stackoverflow]("http://stackoverflow.com/questions/15442905/creating-deb-file-for-python-application") as I was not aware of this particular forum.

I am new to python programming and this is my first serious python application. Also never created any public application for Ubuntu/GTK platform. Ultimate goal is to make this application available in Ubuntu software repository or similar repositories.

I have been looking up information about building packages and have came across some documents (e.g.[http://developer.ubuntu.com/publish/my-apps-packages/](http://developer.ubuntu.com/publish/my-apps-packages/)) and some packages like Py2deb but it's not clear to me how my application needs to be structured so that deb installer can do the right things

    Application is dependent on some other python libraries which can be installed using apt-get install command. How to indicate this dependency
    Application is dependent on some some python libraries which can be installed using PIP. How to ensure/install these libraries.
    Application needs webkit3. I think this is part of standard ubuntu desktop install, but should I indicate explicit dependency? If yes, how to do that.
    Application has its own resource files - non python files such images/templates etc. Where should these files go.

Current tree structure of the application can be seen at [https://github.com/nhrdl/notesMD](https://github.com/nhrdl/notesMD)

Any pointers or links will be greatly appreciated.

---

### Post by niranjan_rao on 2013-03-20
Any one?

Is there any forum where I can get answers.

Thanks,

---

