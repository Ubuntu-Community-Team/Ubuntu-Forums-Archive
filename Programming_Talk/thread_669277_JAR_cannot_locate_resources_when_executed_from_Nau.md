---
title: "JAR cannot locate resources when executed from Nautilus."
date: 2008-01-16
forum: Programming Talk
---

### Post by Jimm1 on 2008-01-16
I have a Java application which I have made, which reads in resources such as images and text files, from a folder called "res". It works.
I have now compiled a JAR archive to launch my program, and I keep the res file outside of the JAR. Ie, I have a folder called "App", in which contains App.jar and the folder "res", which contains the images. If I navigate to the App folder (With BASH), and launch the App.jar with "java -jar App.jar", it works, and loads all the images and resources. However, if I navigate to the "App" folder with the GUI/Nautilus, then double click on App.jar, it loads the actual program fine, however for some reason it can't locate the resources. When I placed the resources in the ~ (Home) directory, it FOUND the resources, even though the "app" folder was in a completely different directory. Why is it that when I launch the App.jar from the shell, it finds the "res" folder, but if I launch using Nautilus, it tries to locate the "res" directory in my home directory? This is quite a problem, because I want to be able to launch my program from the "Applications" menu, and it won't be able to locate the resources. :confused:

I tried the same program in Windows, and when I loaded the App.JAR from the GUI, it LOADED the images. Why wont Ubuntu?

---

### Post by Jimm1 on 2008-01-16
Could someone please answer this!? I have been waiting hours and no reply, yet there are over 1000 people online answering posts which are hardly important at all. Without this, I might as well ******* well uninstall Ubuntu. I have had so much frustration with Java programming on Ubuntu as it is, and without being able to ******* LOAD A FILE without it searching the HOME path, I might as well just give up on trying to make do with Linux. Loading the program from the console IS NOT an option, it simply takes to long, and I want my program to load when the session starts (Or when I load it from applications menu). Why does everything on Linux have to be so complicated and hard? Such a simple little problem causes JAR's file s to become completely obsolete. :mad:
All I want is too be able to load my program by double clicking on the icon, and also be able to damn well load resources which are in the same folder! How hard can that be! Why does this work on Windows and not Linux?

I knew turning to Ubuntu was a bad idea. Everyone told me how awesome/powerful/reliable it was. What a lie. I took me a whole day just to figure out how to get DVD's to work. I DONT want to turn back to Windows, I hate Windows, but if I cant do something as simple as load a JAR without it skrewing up, it may be the only choice.

---

### Post by Zugzwang on 2008-01-16
According to the forums, you did not wait for more than one hour, you can't expect an answer so fast.

Also you can't expect everyone here to have a good knowledge of Java, which is the reason why other posts get answered and yours doesn't ... especially since this the "Programming Talk" board!

Also, this is not a problem of Ubuntu, you'll have the same problem in Windows as well if you create a shortcut in the start menu.

The problem you're facing is: In your program, you assume that when starting the program, the current directory is the directory your JAR file is located in. This is *not true* in general, under no platform. Furthermore it appears as if you don't catch (and process) Exceptions properly, because you should have got FileNotFoundExceptions.

To get the path your JAR is located in, you can use the following class:
[PHP]package de.nigjo.util;

import java.io.File;
import java.net.URL;

/** Returns the path in which the .jar-Archive which contains this class is 
 *  located
 * 
 * @author nigjo
 */
public class JarSearcher
{
  private Class searchClass;

  public JarSearcher()
  {
  }

  public static File getJar(Object obj)
  {
    JarSearcher searcher = new JarSearcher();

    searcher.setClass(obj.getClass());

    return searcher.findJar();
  }

  /** Returns the File Object of the .jar file
   * 
   * @return <code>null</code> if this class isn't stored in a .jar file
   */
  private File findJar()
  {
    String klasse = getClassURL().getFile();

    if (klasse.indexOf(".jar!") >= 0)
    {
      String jar = klasse.substring(0, klasse.indexOf(".jar!") + 4);

      return new File(jar);
    }

    // no jar found
    return null;
  }

  private URL getClassURL()
  {
    String name = searchClass.getName();

    name = name.replaceAll("\\.", "/");

    return searchClass.getClassLoader().getResource(name + ".class");
  }

  private void setClass(Class toSearch)
  {
    searchClass = toSearch;
  }

  /** Returns the path to the .jar-Datei containing the class of the object given
   * 
   * @param obj
   * @return <code>null</code> if the class of the object is not in a .jar file
   */
  public static File getJarDirectory(Object obj)
  {
    // Search for .jar file
    File jar = getJar(obj);
    if (jar != null)
    {
      // .jar found
      return jar.getParentFile();
    }
    // ... not found
    return null;
  }
}[/PHP]

This class is taken from [http://www.wer-weiss-was.de/theme35/article1701307.html]("http://www.wer-weiss-was.de/theme35/article1701307.html") and translated to English by me.

You can then prefix every file reference by the path you get from this class.

---

### Post by Jimm1 on 2008-01-16
Thanks, that works.

Why does it have to be so complex?

---

### Post by pbrockway2 on 2008-01-16
> Why does it have to be so complex?

It's mostly complex because of the way you have decided to store the resources.

You have them in a *directory* that is in a well known location realative to your jar *file*.  Java's take on this is a little different and need not depend on (somewhat OS dependent) file systems.

In general resources can be stored and retrieved at locations on the *classpath*.  For instance you could include the res directory as an entry in the jar file.  Or have the res directory separate, as you do now, but include a Class-Path entry in the manifest of that jar file.  

Either way, at runtime, you access the resources via the Class methods getResource() and getResourceAsStream().  And you find you are working with streams based on URLs rather than Files.  Both methods take arguments that identify the resource which is located by the class loader the same way it locates classes.

The advantage of working this way is that you are making no assumptions about the location of either the resources or the classes using them: they may be in a jar archive or not, they make be files or not, they may be accessed on the internet via URLs or not, they may be entries in a database or not.

The use of jar files is discussed at length in Sun's Tutorial:
[Packaging Programs in JAR Files]("http://java.sun.com/docs/books/tutorial/deployment/jar/index.html")

---

