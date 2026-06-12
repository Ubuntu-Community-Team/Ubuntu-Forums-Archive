---
title: "Java: I want to be able to run a GUI I've built with a flag... but cant :-("
date: 2010-11-17
forum: Programming Talk
---

### Post by EvenStevens on 2010-11-17
I'm building a very simple physics engine, and have a bunch of classes which hold the data, which I can print out in a terminal perfectly fine.

But if I want to visualise it, I want to be able to just add a -g flag when I run it and it show up, but this is proving troublesome.

The problem is I need to tell the graphics class to run. The Gui class just builds a JFrame, and takes a list of items from the engine itself to paint them...

But the graphics class needs an instance of the engine to know how to get items.
and the engine needs an instance of the graphics class to know what to run...

And this obviously isn't working, and I dont know how to go about making a sane solution :-\

Any tips, if you can make sense of my jabber?

---

### Post by bryangwilliam on 2010-11-17
I would be careful about having class interdependencies like that. I don't know if this is the "proper" way of looking at things, but I have always gone by the mantra that each additional feature in a program should ADD to the functionality. 

If I were trying to recreate your project, I would probably just have the engine be the core of the program and then, if the -g flag is set, create the graphical object and some sort of interface between the two. The graphical portion would simply respond to the changes fed to it by the engine, not request information.

---

### Post by Reiger on 2010-11-17
You should decouple data/model (engine) from presentation (gui).

In effect the proper sequence for this would be something like this:
[list="1"]
[*]Create display object.
[*]Create engine object.
[*]Assign engine object to be the model of the display object.
[*]Register any listeners on the engine if it generates events you need.
[*]Start the engine.
[/list]

Now if you want to have a different interface the only thing than needs to change is the display object. One could define the display object in terms of an interface:
```

public interface OutputDisplay {
  /**
   * Register an engine object with this display object.
   */
  void setEngine(Engine engine);
  /* ... any other methods you might need ...*/
}

```

Then both your commandline view and your GUI view can implement this interface and you can create one or the other like this:
```

public static void main(String[] args) {
  // may require more sophisticated parsing of args 
  boolean gFlag = args.length > 0 && args[0].equals("-g");
  DisplayOutput view = gFlag ? new GUIOutput() : new CLIOutput();
  Engine engine = new EngineImplementation();
  view.setEngine(engine);
  // start engine now...
}

```

---

### Post by DangerOnTheRanger on 2010-11-17
Look up Design Patterns before actually coding anything big, like a physics engine.
Specifically, look at Model View Presenter/Controller.
Gee, it really surprises me how many programmers are unfamiliar with design...

Granted, I used to be that way too, but that all changed when I began coding on my 2200 line(and counting) game development kit...

Also, bryangwilliam is right. Add, don't change. As a matter of fact, such functionality(rendering graphics) is not usually included in a physics engine. That's an external program's job.

*No *physics engine renders graphics, nowadays. Just look at ODE and Bullet...

---

