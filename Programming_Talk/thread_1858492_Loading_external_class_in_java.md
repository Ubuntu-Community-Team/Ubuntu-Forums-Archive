---
title: "Loading external class in java"
date: 2011-10-12
forum: Programming Talk
---

### Post by ultddave on 2011-10-12
Hey,
 
I've a question regarding the loading of classes at runtime in java with a classloader.
 
My problem is the same as the one mentioned here: [http://ubuntuforums.org/showthread.php?t=821744](http://ubuntuforums.org/showthread.php?t=821744)
 
Situation:
I've a directory called "plugins". In that directory there is a file called "MyNewAlgorithm2.class". This class's binary name is "implementation.MyNewAlgorithm2".
 
I want to load this class at runtime and use it.
 
Note that the .class file is located directly in the "plugins" folder and not in a "/plugins/implementation" folder.
 
(PS: The situation above is an example to illustrate my problem.)
 
 
This is my code (using some hardcoded strings for testing): 
```

        ClassFileScanner c = new ClassFileScanner();
        c.getReferencedClasses("plugins/MyNewAlgorithm2.class");
        System.out.println(c.getName());
        try
        {
            URLClassLoader loader = URLClassLoader.newInstance(new URL[] { new File("plugins").toURI().toURL() });
            Class<?> cls = loader.loadClass(c.getName());
            System.out.println("Succes");
        }
        catch(Exception e) {System.out.println(e.toString());}
 

```
 
Output:
```

implementation.MyNewAlgorithm2
java.lang.ClassNotFoundException: implementation.MyNewAlgorithm2

```
 
So I can't load the class, probably because it's not in a folder named "implementation".
 
If i use:
```
Class<?> cls = loader.loadClass("MyNewAlgorithm2");
```
instead (hardcoded for a moment).
 
I get this output:
```

implementation.MyNewAlgorithm2
Exception in thread "main" java.lang.NoClassDefFoundError: MyNewAlgorithm2 (wrong name: implementation/MyNewAlgorithm2)

```
 
Anyone know what i'm doing wrong? And/or has a solution?
 
What I'm trying to achieve is the loading of algorithms (as a .class file) developed by other people and use them in my application. Loading algorithms from jar files is no problem. But I also want to support loading seperate .class files.
 
Hopefully I explained my problem clearly ;).
 
Thanks in advance.
 
Kind regards.
Dave

---

### Post by PaulM1985 on 2011-10-12
Why not have the files in the implementation package?  Why do you need to use the plugins folder?

Paul

---

### Post by ultddave on 2011-10-12
Hey,
 
Thanks for the reply. 
 
Well, the issue is that I have an abstract class called "Algorithm" and the users of my application have this file available for use aswell. So they can open their IDE, create a new project, import the algorithm.java file, and create a specific algorithm, derived from that class, say "MyNewAlgorithm2" and compile it.
 
Then I want to allow the users to use their algorithm (the one they created themselves) in my application by loading it @runtime. So i've no control about the location of the .class file. If the user wants to put it in a folder called "qdqfsdfsdfsdf", then i should still be able to load and use it. ;)
 
(The plugin folder was just an example.)
 
But I'm not sure if the thing I want is possible?
 
Kind regards.
Dave

---

### Post by PaulM1985 on 2011-10-12
You are currently using "plugins/MyAlgorithm2.class", which is hard coded.  Why not make the user provide a string to where their class lives?

User code:
```

String pluginPath = "plugin/MyAlg.class";
try
{
  LoadPlugin(pluginPath);
}
catch ([YOUR_SPECIALLY_DEFINED_EXCEPTION] e)
{
  System.out.println("Can't load plugin " + e);
}

```

Paul

---

### Post by ultddave on 2011-10-12
Hey,
 
I know what you mean. But yes, I do that by asking the user to select the file via the JFileChooser, so I know the path to the file(s), but I left that part out of the code because it doesn't really help me solve the issue.
 
The main issue is that I can't seem to load a class if it's not in a directory tree which corresponds to the binary name.
 
Eg: The class "xxxx.yyyy.MyAlgorithm" can (only?) be loaded if the "MyAlgorithm.class" file resides in the yyyy folder, which in turn is in the xxxx folder. (If I'm correct?)
 
But I want to load that MyAlgorithm.class file if it's in the "zzzzz" folder, even though it's binary name is "xxxx.yyyy.MyAlgorithm". Is this possible? 
 
PS: Finding out the binary name is no problem. I can use the ClassFileScanner or ask the user to create an XML file with the fullname or something. But it's the classloading itself that doesn't want to work unfortunaly :(.
 
So to rephrase my question with another example:
Eg: The classfile MyAlg.class which has binary name: "xxxx.yyyy.MyAlg" is located in the directory "C:\users\ultddave\project\". How can I load it? Because it's not in a "xxxx/yyyy" directory tree like the binary name would suggest.
(Given you have the filepath to the .class file and you can find out it's binary name.)
 
Or is this impossible?
 
Kind regards.
Dave

---

### Post by ofnuts on 2011-10-12
> **ultddave said:**
> Hey,
 
I know what you mean. But yes, I do that by asking the user to select the file via the JFileChooser, so I know the path to the file(s), but I left that part out of the code because it doesn't really help me solve the issue.
 
The main issue is that I can't seem to load a class if it's not in a directory tree which corresponds to the binary name.
 
Eg: The class "xxxx.yyyy.MyAlgorithm" can (only?) be loaded if the "MyAlgorithm.class" file resides in the yyyy folder, which in turn is in the xxxx folder. (If I'm correct?)
 
But I want to load that MyAlgorithm.class file if it's in the "zzzzz" folder, even though it's binary name is "xxxx.yyyy.MyAlgorithm". Is this possible? 
 
PS: Finding out the binary name is no problem. I can use the ClassFileScanner or ask the user to create an XML file with the fullname or something. But it's the classloading itself that doesn't want to work unfortunaly :(.
 
So to rephrase my question with another example:
Eg: The classfile MyAlg.class which has binary name: "xxxx.yyyy.MyAlg" is located in the directory "C:\users\ultddave\project\". How can I load it? Because it's not in a "xxxx/yyyy" directory tree like the binary name would suggest.
(Given you have the filepath to the .class file and you can find out it's binary name.)
 
Or is this impossible?
 
Kind regards.
DaveWhat can't you let the file go in plugins/implementation/TheAlgorithm.class? One reason why Java does this is that you can then have several TheAlgorithm classes from several origins that won't conflict. Another benefit of using the standard Java way is that the class  people want to use may come with other classes or resources and you wouldn't have as much control in the loading of such classes (actually, you should even be prepared to be given JARs...). Plus people writing Java eventually learn that Java packages and directory are related, so they would expect your code to work the standard way.

---

### Post by ultddave on 2011-10-12
> **ofnuts said:**
> What can't you let the file go in plugins/implementation/TheAlgorithm.class? One reason why Java does this is that you can then have several TheAlgorithm classes from several origins that won't conflict. Another benefit of using the standard Java way is that the class people want to use may come with other classes or resources and you wouldn't have as much control in the loading of such classes (actually, you should even be prepared to be given JARs...). Plus people writing Java eventually learn that Java packages and directory are related, so they would expect your code to work the standard way.
 
Well. I wish I could do that, but the user creates the "TheAlgorithm" class, so i've no control over it's binary name. And the user chooses where he puts the .class file. For all I know he might have placed the file at "C:\".
 
And the user controls which .class file(s) he wants to load (using the JFileChooser). ;)
 
So I've no control over the location of the .class file, nor over it's binary name. But I still want to load it. Which is basicly what makes it so complicated in this case. ;)
 
PS: Loading JARs is no problem. I already implemented that feature. I used the ServiceLoader from Java. Works fine. ;)
 
Or is this really impossible to do?
 
> Plus people writing Java eventually learn that Java packages and directory are related, so they would expect your code to work the standard way.
Good point. If the thing I want to do, is impossible, i'll just do it like you suggested. ;)
 
(On a sidenote; The people who will be using the application are students and I want to make the application as easy to use as possible. The goal of the application will be to visualize their sortalgorithms.)
 
Kind regards.
Dave

---

### Post by ofnuts on 2011-10-12
> **ultddave said:**
> 
 
(On a sidenote; The people who will be using the application are students and I want to make the application as easy to use as possible. The goal of the application will be to visualize their sortalgorithms.)
 
Kind regards.
DaveThen you can instruct them to not use any package for their class in this case... especially since you have the JAR support already.

---

### Post by ultddave on 2011-10-12
Ok thanks, I think I'll do that then. ;)
 
(PS: I'm not a teacher, just a fellow student, but I'll do it like that then.)
 
Kind regards.
Dave

---

