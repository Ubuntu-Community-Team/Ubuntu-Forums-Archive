---
title: "Creating Plugin for Azureus"
date: 2006-05-29
forum: Packaging and Compiling Programs
---

### Post by cobbweb on 2006-05-29
HI,  
 I need some help in regards to creating a plugin for a program called Azureus (torrent manager program) 
This is going to be the first time I have really created a plugin for anything, so I apoligize in advance if I seem a little dense.  
 
I am trying to create a plugin that will monitor a set of 5 - 10 diffrent torrents and store how much of each torrent has been uploaded in a data file to be send to a server.  
 
There are two problem's that I am encountering.  
 
Problem #1: I created a jar file called tracker.jar with the plugin.properties include. My plugin.properties looks like this..... 
 
plugin.class=Tracker_Plugin.code.theTracker.class 
plugin.name=Ubuntu-Utah Tracker 
plugin.version=.1 
plugin.id=this plugin 
 
 
.....  
 
My class file is found in Tracker_Plugin.code  
 
My class file looks like this: ..... 
 
import java.util.*; 
import org.gudy.azureus2.plugins.*; 
import org.gudy.azureus2.plugins.tracker.*; 
 
public class theTracker implements Plugin 
{ 
public void initialize(PluginInterface _plugin_interface) 
{ 
//System.out.println("Hello, this is the Ubuntu-Utah tracker plugin"); 
} 
} 
...... 
 
I did this to try to figure out how to properly create the plugin, however whenever I jar these files and install them, I get this error:  
 
Error loading plugin 'this plugin' / 'Tracker_Plugin.code.theTracker.class' 
Class 
Tracker_Plugin.code.theRacker.class not found 
 
...... 
 
I can't figure out why it doesn't find the class. Have any ideas the are probably obvious that im not seeing?  
 
Problem #2: Ok, I would like to monitor the upload of say a torrent named, coolguy.torrent I don't know how to get that objects so I can extract properties from it. Or maby i'm going about this the wrong way. If I wanna keep a constant data base of how much of a certain torrent has been uploaded, how should this been done with Azureus's javadocs.  
 
Thanks to anyone that helps me with this. This is a big learning experience for me so it should only be a pain the first time. I have been programing in Java for around 2 years, but never anything of a practical nature (made stupid stuff like a Penny Toss game and a library database program)  

Their website and javadocs can be found here: 

 [http://azureus.sourceforge.net/plugins/doc/](http://azureus.sourceforge.net/plugins/doc/)
[http://azureus.sourceforge.net/index.php](http://azureus.sourceforge.net/index.php)
 
Cobbweb

---

### Post by chrestomanci on 2006-05-29
Wrong forum.

Your question is not Ubuntu specific, you will get better advice in an Azureus forum or mailing list. I suggest you pay a vistit to the Az website, and look for links.

---

### Post by cobbweb on 2006-05-29
I am creatin this for the Ubuntu-Utah Team and have looked threw Azureus website/forum. I'm trying to pull as many recources as possible. 

 Cobbweb

---

