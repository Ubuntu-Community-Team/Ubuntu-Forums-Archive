---
title: "Separating view, model and controller (PyGTK)"
date: 2008-07-30
forum: Programming Talk
---

### Post by ib.lundgren on 2008-07-30
My problem is that I'm not fully understanding the fundamentals of MVC programming and how to implement it.

[LIST]

[*] (View) I have created a simple GUI with glade with a class, Interface, which basically initializes the GUI and handles signals etc.

[*] (Model) I have an XML document with some data coupled with the class Database, which saves, loads, data from this document.

[*] (Controller) I have a file called manager which supposedly should control these two other classes. This currently only is a few lines under main but will be a class eventually.

[/LIST]

My scenario goes something like this:

```


if __name__ == '__main__': 

   ui = Interface()
   db = Database()

   list = db.get_all_items()
   
   for item in list:
      ui.add_item(item)

   ui.main()


```

So far so good, my problem is when it comes to updating the list in the gui. The signal from a button click is captured in the Interface class and I would like it to passed on to the (to-be) Controller class. All my ideas seem to end up with the Interface class having a Controller member. But then it feels like the View is controlling the controller that is controlling the model.

I assume I have missed something very important in the basics of MVC, would anyone care to enlighten me?

---

### Post by dwhitney67 on 2008-07-30
There are many ways to implement the MVC paradigm, but I believe you have a good enough grasp of understanding it.

Some applications do supply a reference of the controller to the viewer (for purposes of sending requests), whereas other applications have been known to use a TCP socket, thus allowing the viewer to send and receive data, and more importantly run independently of the Model/Controller.  This latter approach would permit the GUI front-end to run on any networked system and the Model/Controller on another.

Another alternative is to create a proxy that serves as the middle-man between the viewer and the controller.  Both the viewer and the controller would have to have a reference to this proxy.  Initially this proxy can be designed with simple interfaces, but later it can be expanded to support TCP (or other IP protocol), message queues, pipes, shared memory, etc.

So essentially the choices are numerous and ultimately up to you as to which you prefer and is applicable to your application.

---

