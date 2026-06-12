---
title: "developing an application that supports plugins"
date: 2007-03-03
forum: Programming Talk
---

### Post by orlox on 2007-03-03
I'm programming a software in java used to control motorized telescopes. Since it may be used on different telescopes, that work and communicate in different ways, I want the application to have the ability to include telescope drivers as if they were plugins, so anyone can program his telescope plugin and use it without having to change the application.

Does anyone know how to do this??

---

### Post by laxmanb on 2007-03-03
I'm not very well informed, but if your program is GUI based, you can base it on a rich client platform (Eclipse/Netbeans)... first thing that comes to mind when the words "Java" & "plugins" are used together...

---

### Post by orlox on 2007-03-03
I also checked that (cause a search on google shows lots of pages on that), but my application is actually daemon, so I don't think a rich client platform could do the job...

---

### Post by Tomosaur on 2007-03-03
Create a plugin interface. All plugins will generally conform to some rules, so an interface is ideally suited for this. You could have the constructor take the name of the plugin, version number etc etc, then a few other methods which would define the behaviour of the plugin. This means that your app can organise all of the plugins itself, rather than rely on the plugin to slot into some area of the program and 'interfere' with it to get it to do whatever it is it's supposed to do.

---

### Post by orlox on 2007-03-03
But how does the plugin effecively get's loaded into the application, and how should the plugin be programmed? The software i'm making should be distributed as a binary, and any user should be able to put a plugin into a plugin folder, specify the plugin name on a config file, and then the application should run using that plugin. 
I understand what you say about the interface, but how can the contructor execute the methods in the plugin??

---

### Post by laxmanb on 2007-03-03
why don't you just keep text/binary/XML files which contain the actual commands/info used to move the telescope and then let the user choose his telescope the first time program runs... the program can map out the user's input to the telescope's commands....

for eg... if telescope A uses the command mov(x) to move forward by x units and telescope B uses move(x) to do the same thing, just lookup the appropriate command from the file and then get it to execute... this seems like a simple enough method...

PS: I like the interface idea too... just look up the text files and slot the data into the interface's constructor...

---

### Post by orlox on 2007-03-03
Sorry if I don't get you, but... I can't figure how to get this things into practice :P...

If I make my plugin in java, containing all the methods to extend an interface I have in my application, how can the application load in run time that code??

---

### Post by Tomosaur on 2007-03-03
> **orlox said:**
> But how does the plugin effecively get's loaded into the application, and how should the plugin be programmed? The software i'm making should be distributed as a binary, and any user should be able to put a plugin into a plugin folder, specify the plugin name on a config file, and then the application should run using that plugin. 
I understand what you say about the interface, but how can the contructor execute the methods in the plugin??

Easy - just include some plugin management code. You could, for example, keep an XML file with all of the plugins available - those which are disabled, those which are enabled. Just include it with your program, and write a simple parser to configure the app on startup by reading the XML file, finding the relevant .class files for the plugins (ie, keep the plugin .class files in a plugins directory), then creating an array, hashtable, list, or some other data structure. The plugin wouldn't communicate directly with the program, it would be the other way around. Once the plugin is registered, you can guarantee which methods are available to you. You could even make the interface methods static, so you could call them using something like this:

```

plugin_array[0].rotate_telescope_right();
plugin_array[0].rotate_telescope_left();
plugin_array[0].zoom_in();
plugin_array[0].zoom_out();

```

Or whatever it is the plugin is supposed to do. The structure of the app would like like this:
```

YOUR TELESCOPE SOFTWARE==\
.....................Controller plugin for telescope brand XYZ==\
..................................................................Connection to telescope==\
.....................................................................................................Telescope

```

If that looks confusing - basically that's because I'm working off some assumptions here. Your main application would have plugins for different types of telescope. The generic plugin interface would have some predefined methods which provide some basic telescope functionality, such as the ones illustrated above (rotation, zooming etc). The body of these methods would communicate with the actual telescope wherever it is. The exact implementation of this is unknown, which is more or less the point of using an interface. All you have to concern yourself with is providing the interface documentation to the end-user, so he/she can implement it to suit their telescope. The plugin doesn't do anything to the software - the software tells the plugin what to do. It already knows what the plugin is capable of, because the interface forces certain methods to be included. The ACTUAL plugin (written by the end user) can include other methods, but it MUST include the methods described in the interface. The method in which the plugin controls the telescope is not of your concern - so there's no need to worry about it. Just as long as the software can statically use the methods in the plugin, then it's all gravy.

---

### Post by orlox on 2007-03-03
Thanks :) . I'll check on that.

---

### Post by Mr. C. on 2007-03-03
To further the previous posters response, but at a higher, more abstract level, plugin interfaces typically:

  1) search for and load plugin from well-defined location(s)
  2) call well-defined initialization/construction routine within plugin
  3) provide *hooks* in main application for various operations that plugin can perform
  4) allow plugins to register into hooks from (3), often during (2).
  5) call well-defined destruction mechanism where plugins can cleanup
  6) optional: provide out-of-band callback mechanism for plugin
  7) optional: provide communication path between main app/plugin

These become the basis for your plugin API.

MrC

---

