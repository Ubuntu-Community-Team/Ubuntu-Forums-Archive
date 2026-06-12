---
title: "Loading external classes in Java"
date: 2008-06-07
forum: Programming Talk
---

### Post by Phristen on 2008-06-07
So I have a directory and presumably some .class files in it.
I want to load all those classes so that I can instantiate them later if I want.

Problem is, I do not know what packages these classes belong to so I can't load them via ClassLoader because I get errors like java.lang.NoClassDefFoundError: ClassName (wrong name: package/ClassName) ...

Ideas? :confused:

---

### Post by xlinuks on 2008-06-07
Knowing what packages those classes belong to is a must.
After you find out what they belong to, say, com.ubuntu.CoolClass, put it into your
final .jar file where all _your_ classes lay and just call:
> 
import com.ubuntu.CoolClass;

or
> 
import com.ubuntu.*;

and you're done.

---

### Post by Tomosaur on 2008-06-07
> **Phristen said:**
> So I have a directory and presumably some .class files in it.
I want to load all those classes so that I can instantiate them later if I want.

Problem is, I do not know what packages these classes belong to so I can't load them via ClassLoader because I get errors like java.lang.NoClassDefFoundError: ClassName (wrong name: package/ClassName) ...

Ideas? :confused:

I have run up against this problem in the past. The easiest (maybe the only?) solution for such a case seems to be to decide on some kind of format that the external classes will take (Of course, this only works when you are developing these classes yourself, or at least have some degree of control over the development) - so your format may be that all external classes have to be part of a package called 'external', and then the main class in this package is always called 'Main' or something like that.

The other option is that you ask people who are developing external classes to provide you with an XML file which details the package name, and the main class name for the class file. Then you can use Java's XML parsing to grab this data for each class and load them as you have been trying to - except now you know the package name.

---

### Post by xlinuks on 2008-06-07
Or just attach those classes and I'll let you know their full name.

---

### Post by Phristen on 2008-06-07
> Knowing what packages those classes belong to is a must.Oh, well :(> The other option is that you ask people who are developing external classes to provide you with an XML file Or maybe classes from package "pack" will just go in the subfolder "pack"...
Check this:[PHP]
		ArrayList<Class> classList = new ArrayList<Class>();
		File dir = new File ("something");
		try {
			if (dir.exists()) {
				ArrayList<File> paths = new ArrayList<File>();
				ArrayList<String> classes = new ArrayList<String>();
				
	
				
				for (File f : dir.listFiles()) if (f.isDirectory()) paths.add(f);
				paths.add(dir);
				
				for (File f : paths)
					for (File ff : f.listFiles())
						if (!ff.isDirectory() && ff.getName().endsWith(".class"))
							classes.add((f != dir? f.getName() + "." : "") + ff.getName().substring(0, ff.getName().length() - 6));
					
				
				ClassLoader cl = new URLClassLoader(new URL [] {dir.toURI().toURL()});
				for (String s : classes)
					try {
						classList.add(cl.loadClass(s));
					} catch (Exception e) {}
			}
		} catch (IOException e) {}[/PHP]
Any suggestions on improving this ugliness? ;)
Also, how do I extract classes from .jars?

---

### Post by xlinuks on 2008-06-07
1) You are over-complicating things, it's much easier :)
Try doing what I suggested in my first post, if I didn't make myself clear please ask what you don't understand.
2) To extract classes .jar files (if you indeed mean _extracting_) - right-click on it and choose "extract files here" or whatever the menu might say. Jar files are ordinary .zip files that have a manifest, but the format is the same as those of .zip files.

---

### Post by Phristen on 2008-06-07
1) Ok, maybe I wasn't clear. The program will be ran as jar and user can point to _any_ directory he likes _during runtime_. That directory will contain _any_ number of classes from an unknown variety of packages. I don't know anything before execution time so I can't import.
2) No. By extracting I mean loading the .class files within the .jar to my list of classes.

---

### Post by xlinuks on 2008-06-07
1) Well, then basically the only way you can do it is using a ClassLoader since you're willing to load them during runtime. I'm pretty skeptical that you're gonna be able to do something with them unless they will serve for a purpose with predefined interfaces rather than with random methods.
2) Since that's at runtime you have to "read" those classes from inside the .jar file, see the "java.util.zip" and "java.util.jar" packages on how to read/extract files from .jar files.

---

### Post by Phristen on 2008-06-07
> unless they will serve for a purpose with predefined interfaces rather than with random methodsThey will extend a known abstract class, so no problem.
> Well, then basically the only way you can do it is using a ClassLoader since you're willing to load them during runtimeWhich brings me back to the question if the piece of code I provided can be simplified.

---

### Post by xlinuks on 2008-06-07
It all depends on what you need and how secure you want to be.
You are checking
```

if (file is not dir ) {
  doesItHaveAClassExtension();
}

```
Why not checking whether the file also has the methods it's supposed to have and that it returns the values of the type it's supposed to.
I mean you are doing right but whether you are importing the "right or wrong way" is very subjective in your case.
If you think the user won't feed you with a wrong class (thus your app won't crash) then don't check for that, otherwise you should. And who knows what else.
In other words just test your code and see if it works "in real life", its pretty short I don't think you have to try shrinking it further.

---

### Post by Phristen on 2008-06-07
[PHP]
if (cl.loadClass(s).getSuperclass() == MyKnownAbstractClass.class)
	classList.add(cl.loadClass(s));[/PHP]That's about as secure as I want it.
The main area of concern is getting the String names of classes.
The way I'm currently doing it seems wrong :( I was hoping there could be some built-in aid for that.

---

### Post by NormR2 on 2008-06-07
Is this your problem:
You have a directory with an arbitrary number of class files in it,
source unknown so that there is no subdirectory structure to match the package.class path that the java command/ClassLoader needs.

You want to read each file and extract the full package.class name/path for the contained class code to be able to use it with your own ClassLoader.

I have several programs that do bits and pieces of that. If you could explain what you need, I'll see if I can find the code.

---

### Post by Phristen on 2008-06-07
> **NormR2 said:**
> Is this your problem:
You have a directory with an arbitrary number of class files in it,
source unknown so that there is no subdirectory structure to match the package.class path that the java command/ClassLoader needs.

You want to read each file and extract the full package.class name/path for the contained class code to be able to use it with your own ClassLoader.

I have several programs that do bits and pieces of that. If you could explain what you need, I'll see if I can find the code.
You described it accurately.
I just wanna instantiate a class contained in a .class file, but I don't know the package (and thus can't provide the ClassLoader with a qualified name).

---

### Post by NormR2 on 2008-06-07
Here's a program I got from another forum that might do it.

---

### Post by Phristen on 2008-06-07
Mmmman, is that what it takes :)
Read the class file byte by byte to manually figure stuff out...
Thought there was a nicer way :(

Ok, while we're on the subject, another question.
I have some classes that are sure to be loaded when the app starts, how do I get the list of them all?
Let's say there are 50 classes in my jar, and I only wanna list the ones implementing a certain interface.
Of course, I could just list them manually, but then I would have to modify the code every time new class is added, which I don't think is a good practice.
In this case we can assume the package is known, but the names are not.

---

### Post by NormR2 on 2008-06-07
> classes that are sure to be loaded when the app starts, how do I get the list of them all?
Let's say there are 50 classes in my jar, and I only wanna list the ones implementing a certain interface.
Sounds like 2 questions:
1 - classes that are loaded when the app starts
2 - classes that implement a certain interface

Givens are the interface name, the jar file name and the package name.

Don't know about #1 
#2 - Seems like reflection class Class would have methods for doing that.  Use the zipfile/jarfile class to list the members in the jar file and look at them one by one.

---

### Post by NormR2 on 2008-06-07
A look thru my files found the attached:

---

### Post by Phristen on 2008-06-07
I know how to find interfaces, I just need to get the list of Classes :)
I probably don't understand something, but it just seems strange that ClassLoader doesn't have a method that would return a list of files/classes present in its path.

BTW, why am I getting this?```
(<unknown>:20950): Gtk-CRITICAL **: gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed
```This is when I set look & feel to UIManager.getSystemLookAndFeelClassName(), i.e. GTK+ look & feel.

Apparently, GTk doesn't like JComboBox'es for some reason ;( And they are rendered wrong too.

---

### Post by NormR2 on 2008-06-08
One way to get a list of the classes that have been loaded would be to have your own classloader and have it keep track.

Why do you need the list of classes that have been loaded? 
Do you want just the app's classes or including the Java classes?

---

### Post by Phristen on 2008-06-08
These are just theoretical questions, I am doing this for learning, primarily.

---

### Post by NormR2 on 2008-06-08
Ok. I've written many programs just to see how to do it.
Here's one that I enjoyed. My previous machine was 300Mhz with 128M RAM. I was doing some projects that used several of my java tools. Starting java took seconds, so I thought I'd put all my java tools in a single java VM. 
I think the jar will run on Linux, but the .ini file will have to be tailored.  The program uses a ClassLoader that it feeds from its own local controlled classpath.

---

