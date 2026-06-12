---
title: "[Python] Self documenting classes"
date: 2011-12-13
forum: Programming Talk
---

### Post by Tony Flury on 2011-12-13
All,
I am planning to be developing an application with a plug-in interface. I want this framework to allow plug-ins to have effectively arbitary interfaces, and allow the application to build menus on the fly depending on the interfaces that the plug-in advertises. The interface would not be completely arbitary of course, but there would be a limited number of "data types" that the application supports and a plugin should have the freedom to offer methods that take any of these data types in any combination to add useful functionality to the application.

I have been thinking about two methods for the plugin to advertise its capabilities to the application : 
1) The plugin has a registration method (which is always present), and this method returns a structured list detailing the interface that is available and the menu items that the application should build for this plug-in.

2) The Plugin has a registration method (which is always present), and this method returns a class. This class encapsulates the interface to the plugin. The various methods within the class are self documenting (using delimited items within the __doc__ string), and the application looks for these items in the doc string and build the relevant menus itself. The __doc__ string would remain human readable of course, but will have added items which state things like the paramters the application can pass, expected return types, how this capability should appear in the menu (and where in the menu), and maybe even support for toolbars etc.

I prefer method 2 - it feel cleaner and more pythonic - but is that use of doc string recommended or frowned upon ?

---

### Post by juancarlospaco on 2011-12-13
I think i dont understand, ...but maybe DocTest from std lib

---

### Post by Tony Flury on 2011-12-13
> **juancarlospaco said:**
> I think i dont understand, ...but maybe DocTest from std lib

Thanks for trying to help - but I am not trying to define unit tests. I guess though that what I am trying to do is similar.
I will have a look at how DocTest uses Document strings, and adapt that so I can define my plugin interface.

---

### Post by simeon87 on 2011-12-13
Comments should be comments. As long as you use doc strings only for documentation purposes, then it's fine. But the application's execution should not depend on any content in the comments.

---

### Post by Tony Flury on 2011-12-14
> **simeon87 said:**
> Comments should be comments. As long as you use doc strings only for documentation purposes, then it's fine. But the application's execution should not depend on any content in the comments.

I think the point is that Documentation Strings are more than comments. They are accessible via a clear API (which comments are not), and are already used for more than just documentation - DocTest is a good example.
I will continue to have a think about the best way of doing what i want.

---

### Post by juancarlospaco on 2011-12-14
Comments != DocStrings

---

### Post by Tony Flury on 2011-12-14
> **juancarlospaco said:**
> Comments != DocStrings

+1 - completely agree - that is why I considered using something in a DocString to define to the application how it should use the plugin class. The critical thing i think is to try to make it simple so the methods don't need loads of extra lines in their DocStrings.

The way i see it is that there is no good reason why a class should not use DocStrings to document their behaviour/interface - even when that documentation is designed to be used by another class.

---

### Post by ofnuts on 2011-12-14
> **Tony Flury said:**
> +1 - completely agree - that is why I considered using something in a DocString to define to the application how it should use the plugin class. The critical thing i think is to try to make it simple so the methods don't need loads of extra lines in their DocStrings.

The way i see it is that there is no good reason why a class should not use DocStrings to document their behaviour/interface - even when that documentation is designed to be used by another class.
Looks nice on the surface, but it won't be usable for plugins. Docstrings are literals, and only literals. A docstring is one single literal in one piece. You can't make a docstring by appending several string (or even worse, results of expressions), while this is very useful (for instance, to support national languages). I happen to write Python plugins quite often (Gimp plugins). They work like in your 1), and I use dynamic string in registrations, for instance, I made a habit of using:
```

whoiam='\n'+os.path.abspath(sys.argv[0])
    
register(
    "plugin-name",
    N_("Plugin pop-up, followed by plugin file location")+whoiam,
    ....

```

Another case is when the same file contains variations of the same code, so large parts of the registration are common and maintained in single variables somewhere to ensure consistency.

If you want to make use of some of Python introspection, you can load modules you find in some specific places (or listed) and then enumerate the classes they contain, and check classes with a "register_plugin" method, that will return a list/dictionary of parameters, or dictionary of function names, with lists/dictionaries of parameters.

---

### Post by Tony Flury on 2011-12-15
> **ofnuts said:**
> Looks nice on the surface, but it won't be usable for plugins. Docstrings are literals, and only literals. A docstring is one single literal in one piece. You can't make a docstring by appending several string (or even worse, results of expressions), while this is very useful (for instance, to support national languages).
I am not planning on anything ammending the DocString (apart from the original author of the code). After all the behaviour of the method is fixed at the time when the code is authored, so there wont be any need to modify the DocString.

I have already written a framework that works like my method 1, but it actually means that there is definitions in two independent pieces of code - one where the registration list is defined as a dictionary, and then again when the actual method is defined later in the code - hence my docString suggestion of keeping everything in place.

> 
If you want to make use of some of Python introspection, you can load modules you find in some specific places (or listed) and then enumerate the classes they contain, and check classes with a "register_plugin" method, that will return a list/dictionary of parameters, or dictionary of function names, with lists/dictionaries of parameters.

I know I can find the names of methods that a class has but that wont tell me things like : 
* Where in the application menu that the author wants this functionality to appear
* What the Plugin author want's this functionality to be called when it appears on the menu
* What the Plugin author allows to be passed as parameters to this method - i.e. what data types does this method expect.
None of those can be found by introspection alone. I could adopt a brute force method of naming and parameters - Functions appear in the menu in the order they appear in the class, they take the same name on the menu as they take on the class, and they are always passed the same parameters, but that seems incredibly inflexible to me.

---

### Post by ofnuts on 2011-12-15
> **Tony Flury said:**
> I am not planning on anything ammending the DocString (apart from the original author of the code). After all the behaviour of the method is fixed at the time when the code is authored, so there wont be any need to modify the DocString.
Of course you can't... that's why docstrings aren't suitable. From your  side that has to be a string that you parse, and on  the plugin author  side, this is a string that must be completely hardcoded, and, as I  showed you above, in practical plugins you registration data is somewhat  dynamic.
> I have already written a framework that works like my method 1, but it actually means that there is definitions in two independent pieces of code - one where the registration list is defined as a dictionary, and then again when the actual method is defined later in the code - hence my docString suggestion of keeping everything in place.[/quote ]
So now you still have two different pieces to keep in sync, the method and its docstring. You made it even worse, because since everything is hardcoded in the docstring there are even more things to maintain by hand.
[quote]
I know I can find the names of methods that a class has but that wont tell me things like : 
* Where in the application menu that the author wants this functionality to appear
* What the Plugin author want's this functionality to be called when it appears on the menu
* What the Plugin author allows to be passed as parameters to this method - i.e. what data types does this method expect.
None of those can be found by introspection alone. I could adopt a brute force method of naming and parameters - Functions appear in the menu in the order they appear in the class, they take the same name on the menu as they take on the class, and they are always passed the same parameters, but that seems incredibly inflexible to me.
[/quote]Introspection doesn't replace registration... I was just telling where I would use introspection for a plugin.

---

### Post by Tony Flury on 2011-12-15
> **ofnuts said:**
> Of course you can't... that's why docstrings aren't suitable. From your  side that has to be a string that you parse, and on  the plugin author  side, this is a string that must be completely hardcoded, and, as I  showed you above, in practical plugins you registration data is somewhat  dynamic.

To be honest I don't see a need for the data to be dynamic - For a given plugin at a given code version, the plugin will always provide the same functionality to the application, and will continue to do so until the code is changed by the Author.

I agree that the application has to have an initial dynamic phase (to find the plugin's that are available - but that is not a complex activity (I am planning for all plugins to exist as seperate modules within a plugin directory - and the application will dynamically import each plugin that it finds), but once the app has found the plugin then the functionality of the plugin is fixed, unless the plugin author changes the code of the plugin.

> 
[QUOTE]
I have already written a framework that works like my method 1, but it actually means that there is definitions in two independent pieces of code - one where the registration list is defined as a dictionary, and then again when the actual method is defined later in the code - hence my docString suggestion of keeping everything in place.
So now you still have two different pieces to keep in sync, the method and its docstring. You made it even worse, because since everything is hardcoded in the docstring there are even more things to maintain by hand.[/QUOTE]
Under my idea 1 - you have some level of duplication anyway - the meta-description is created in one place (in the registration method), but the functionality is define by the method Source code. At least by using the DocString you can keep the definition of the method together with it's meta-description in the same part of the source code - making it easier to maintain.

I think maybe the title of the thread is misleading - I am not looking for a class to generate Documentation on the fly - I was asking if it was ok to use a DocString to contain Machine readable meta-descriptions that can be used by the application using that class. Is that an acceptable use of DocStrings - has anyone done it before - are there guidlines about what is and is not allowed. 

I am going to close this thread as solved - and maybe open another thread with a better description/title.

---

### Post by ofnuts on 2011-12-15
> **Tony Flury said:**
> To be honest I don't see a need for the data to be dynamic - For a given plugin at a given code version, the plugin will always provide the same functionality to the application, and will continue to do so until the code is changed by the Author.
My experience is that pure static is unworkable, because you often share things between several registrations in the same file. Then, for the author it's really useful to keep a single instance somewhere that the various registrations refer to. And, if you say that once done the registration data doesn't change, then one of your original arguments (making maintenance easier) lose a lot of its appeal.

> **Tony Flury said:**
> I agree that the application has to have an initial dynamic phase (to find the plugin's that are available - but that is not a complex activity (I am planning for all plugins to exist as seperate modules within a plugin directory - and the application will dynamically import each plugin that it finds), but once the app has found the plugin then the functionality of the plugin is fixed, unless the plugin author changes the code of the plugin.

Under my idea 1 - you have some level of duplication anyway - the meta-description is created in one place (in the registration method), but the functionality is define by the method Source code. At least by using the DocString you can keep the definition of the method together with it's meta-description in the same part of the source code - making it easier to maintain.

No, it's too static to maintain... a mere __registration__ attribute would be a lot more usable. With the docstring you are painting yousefl in a tight corner.

> **Tony Flury said:**
>  I think maybe the title of the thread is misleading - I am not looking for a class to generate Documentation on the fly - I was asking if it was ok to use a DocString to contain Machine readable meta-descriptions that can be used by the application using that class. Is that an acceptable use of DocStrings - has anyone done it before - are there guidelines about what is and is not allowed. All the observations above demonstrate that we all understood you correctly.

---

