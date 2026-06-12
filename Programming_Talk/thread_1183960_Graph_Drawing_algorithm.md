---
title: "Graph Drawing algorithm"
date: 2009-06-10
forum: Programming Talk
---

### Post by Dbugger on 2009-06-10
Hey guys!

Im developing an application in C# and I have to render a State based diagram that changes in runtime, (think of it as if I was developing some kind of Visio), and I need some algorithm to prepare the layout. Unfortunately I havent had any luck. Can anyone give me some pointers as to where to find an algorithm to prepare the layout?

Thank you!

---

### Post by Habbit on 2009-06-10
I don't know any such library for C#, but there is a C++ library you might be able to interact with: the [Open Graph Drawing Framework]("http://www.ogdf.net")

---

### Post by Dbugger on 2009-06-10
Im using VG.net to draw the application, but what Im in really need of is the algorithm for the layout, not the tools. (Unless you know some library that contructs directly the diagram automatically :D)

---

### Post by zippaplick on 2009-06-10
Checkout UbiGraph:
[http://ubietylab.net/ubigraph/](http://ubietylab.net/ubigraph/)
[http://ubietylab.net/ubigraph/content/Docs/index.html](http://ubietylab.net/ubigraph/content/Docs/index.html)

I've used it with python a little bit. Renders your data as live 3D graph. Sports an xmlrpc interface, so most languages with xml-rpc support should work.

Might be overkill for what you need but it is cool!

---

### Post by leblancmeneses on 2009-06-10
thats actually something i started to work on.  I currently have the ability to scale canvas and drag around states.  I do not have the capabilities to draw lines and connect end points. In regards to algorithms i currently support hierchical state machines.
Although i got pretty far i stopped progress on this since npeg.codeplex.com is closer to becomming a real product for my company so i have held off finishing the uml tool i was building for ASIC hardware designers.

What i did learn is:
use C# and wpf.  Why?

Because it separates your model from presentation.   You can design your objects as plain c# objects then in your presentation layer apply datatemplates (wpf will bind ui styles + datatemplates to your model).  

This approach pushes the UI back in the timeline which allows you to offshore and makes you concentrate on important parts of your framework. 1) algorithm 2) application programming interface.
It also helps in unit testing efforts as you never bring in UI logic.

---

