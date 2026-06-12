---
title: "NoSuchMethodException in Java"
date: 2012-08-05
forum: Programming Talk
---

### Post by PaulM1985 on 2012-08-05
Hi

I am using Netbeans and I am using standard Netbeans projects.

I am having a problem where I add a simple get method to a class and I use it in another class in the same project, but when I come to run the code I get a NoSuchMethodException.  Everything builds ok but the issue is when I am running the program.  I am wondering why this would happen. I have deleted the Build and Dist folders to see if that makes a difference, but it hasn't fixed it.

Can anyone suggest anything since I have hit a bit of a brick wall.

Paul

---

### Post by PaulM1985 on 2012-08-05
It works if I use the JAR files that are created and run via the command line, but it doesn't work if I run from within Netbeans.  Anyone know why Netbeans would be getting this wrong?

---

### Post by trent.josephsen on 2012-08-05
> **PaulM1985 said:**
> It works if I use the JAR files that are created and run via the command line, but it doesn't work if I run from within Netbeans.  Anyone know why Netbeans would be getting this wrong?
That suggests to me that Netbeans is looking for the wrong file, or looking in the wrong place for it. It's been a while since I used Netbeans though.

Does the NoSuchMethodException name the get method you created or could it be referring to the main method of your program? I've seen some issues with that before IIRC...

---

### Post by PaulM1985 on 2012-08-05
It names the method I have created.

I agree with this:
"That suggests to me that Netbeans is looking for the wrong file, or looking in the wrong place for it."

but what I find odd is if I intentionally put in erroneous code in the same file with the method that "doesn't exist" it won't compile, Netbeans recognises it and tells me it won't compile.  Similarly, if I put bad code in the calling class, it will recognise it and fail to compile.  So it is as though it is looking in the right place.

Paul

---

### Post by trent.josephsen on 2012-08-05
Weird.

When you say "it works" from the command line, have you verified that the most recent version of the source is being used? I.e. if you change the Java source and recompile, does it change the behavior when run from the command line? That's the next obvious thing that comes to mind...

Is the calling code in the same .jar file as the class with the method? Maybe Netbeans is setting up the classpath wrong.

---

### Post by Some Penguin on 2012-08-05
> **PaulM1985 said:**
> It names the method I have created.

I agree with this:
"That suggests to me that Netbeans is looking for the wrong file, or looking in the wrong place for it."

but what I find odd is if I intentionally put in erroneous code in the same file with the method that "doesn't exist" it won't compile, Netbeans recognises it and tells me it won't compile.  Similarly, if I put bad code in the calling class, it will recognise it and fail to compile.  So it is as though it is looking in the right place.

Paul

Not familiar with Netbeans (I use IntelliJ IDEA, haven't felt the urge to switch away), but I'd suspect that perhaps there's an incorrect custom classpath configured with how it's attempting to execute the relevant class.

A longer shot would be that you're using a build system that supports scopes (like Maven), it's improperly limited to the wrong scope (like 'test' scope when you really needed 'compile'); or it's a transitive dependency that's flagged as 'optional' when it really shouldn't be (and you haven't included it as a direct dependency in your own project); and the IDE is seeing the presence and knows about the existence of the method but hasn't calculated that the dependency structure means that it won't actually be accessible.

---

### Post by dwhitney67 on 2012-08-05
> **PaulM1985 said:**
> 
Can anyone suggest anything since I have hit a bit of a brick wall.


I use Netbeans from time to time.

Can you please tell us a little about your project?  Does it reside in a package?  Can you tell us how you are "telling" Netbeans to run your program... for example, what is the name of your main class; what is the path of the working directory?

Btw, does your application employ the "magic" of Java reflection?

---

### Post by PaulM1985 on 2012-08-06
Ok.  I have two packages PokerUI and PokerAI.  Inside the PokerAI package I have classes NeuralNetwork and NeuralNetworkViewer.
NeuralNetworkViewer is a JPanel and draws the NeuralNetwork.
I added a function getNumLayers() to the NeuralNetwork class which is called by NeuralNetworkViewer in the paint(Graphics g) method.

I run this by clicking on the "Run Project" button in Netbeans, which runs the main method in the PokerUI package.  In here a frame is created containing a tab pane.  When the user opens a new network (loads an array of doubles from which a NeuralNetwork is generated), a new NeuralNetworkViewer is created and added as a tab in the tab pane.  The exception is thrown in the paint(Graphics g) method on NeuralNetworkViewer when calling mNetwork.getNumLayers().

No, there is no reflection.

Paul

PS: I copied all my code across to another machine which already contains this project and used Meld to compare the projects.  The only differences were in the source code, the rest of the configuration files were the same.  I poked in the changes to the sources and everything runs as expected on the other machine.  It is annoying since the problem exists on my main development machine that I use most of the time.

---

### Post by dwhitney67 on 2012-08-06
I'm unable to duplicate the issue you have described.  In Netbeans, I created a sample project with the criteria you provided, appearing as:
```

Sample:
    + Source Packages
        + PokerAI
            NeuralNetwork.java
            NeuralNetworkViewer.java
        + PokerUI
            MainClass.java
    + Libraries

```

NeuralNetwork.java:
```

package PokerAI;

public class NeuralNetwork {
    public int getNumLayers()
    {
        System.out.println("In NeuralNetwork.getNumLayers()...");
        return 1;
    }
}

```
NeuralNetworkViewer.java:
```

package PokerAI;

import java.awt.Graphics;
import javax.swing.JPanel;

public class NeuralNetworkViewer extends JPanel {
    private NeuralNetwork network;

    public NeuralNetworkViewer()
    {
        // Not sure who creates this, or whether NeuralNetworkViewer
        // is given the NeuralNetwork object via a parameter.
        network = new NeuralNetwork();
    }

    @Override
    public void paint(Graphics g)
    {
        System.out.println("In NeuralNetworkViewer.paint()...");
        network.getNumLayers();
    }
}

```
MainClass.java:
```

package PokerUI;

import PokerAI.NeuralNetworkViewer;

public class MainClass {

    public static void main(String[] args) {
        NeuralNetworkViewer viewer = new NeuralNetworkViewer();
        viewer.paint(null);
    }
}

```
The only questions remaining is how are you instantiating the NeuralNetwork object that is used by the NeuralNetworkViewer, and then how is the paint() method called?

I do not work much with Java Swing, so if my understanding of the implementation details above is off, then please accept my apologies.

---

### Post by PaulM1985 on 2012-08-14
This seems to be a very odd NetBeans bug.

When I clean and build, all of the class files in each of the projects look ok.  When I run my PokerUi project one of my other dependencies gets a series of packages added to it's build folder, one of which is the AI package.  I used to have some AI stuff in that package but since deleted it.

I am trying to figure out why these packages are being added and where they are coming from.  I don't seem to be able to find anything.  Does this ring any bells with anyone?

Paul

---

### Post by PaulM1985 on 2012-08-14
It looks like I am suffering from this, [http://netbeans.org/bugzilla/show_bug.cgi?id=211904](http://netbeans.org/bugzilla/show_bug.cgi?id=211904), but I don't know a work around.  I am using Netbeans 6.8.

Anyone got any suggestions?

Paul

---

### Post by dwhitney67 on 2012-08-14
Upgrade to Netbeans 7.1?

---

### Post by PaulM1985 on 2012-08-14
Just uninstalled, deleted the config folder in my home directory and re-installed and it is working again now.

Thanks for your patience everyone.

Paul

---

