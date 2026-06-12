---
title: "C++ MVC framework design"
date: 2008-12-02
forum: Programming Talk
---

### Post by Sydius on 2008-12-02
I have decided to try and make a simple MVC (model-view-controller) framework.  But first, I want to make sure I understand the principles of MVC.  Here's my design so far (it's all interface-based, no implementation):

There's a device object responsible for I/O.  It would be a wrapper for something like SDL or Win32 and handle getting input and displaying output (images, etc., or text in the case of console programs).

Views attach themselves to models as observers and inform the models of what kind of updates they are interested in (defined by the model in question).  They access the device directly for rendering themselves.

Controllers attach themselves as observers to the device to listen for input and send the appropriate requests for change to the models and to the views (only to views in the case of purely UI-related information, as the views already listen to the models for changes to them).

Is my understanding of MVC more or less correct?

---

