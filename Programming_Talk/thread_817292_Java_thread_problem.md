---
title: "Java thread problem"
date: 2008-06-03
forum: Programming Talk
---

### Post by Jens_Li on 2008-06-03
We have written a small game using Java2d, Swing and standard java network sockets.

It runs fine under xp, vista, debian, redhat, and on macs. But not under Ubuntu! We have tried on two different machines.

The problems, only under Ubuntu:
1.) Window opened and swing menu showning, but when start button was clicked the game graphics didnt show up, just a grey field. This was fixed by declaring a field that control the starting of the game as "volatile".

2.) After that the game starts but runs incredibly slow and jerky.

The fix to 1.) is why I think this has something to do with threads. We use a swing event thread for keyboard input, a game and rendering thread, and different threads for networking, but problem remains even if the game is not run in network mode. We dont have much experience with writing multithreaded stuff.


Any ideas why this can be? Anyone know of differences with thread handling between Ubuntu and other systems?

/Jens

---

### Post by xlinuks on 2008-06-03
I would suggest posting the source code.

---

### Post by SeanHodges on 2008-06-03
Are you sure you're not running the GCJ version of Java instead of Sun's official OpenJDK version?

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by Jens_Li on 2008-06-03
> **SeanHodges said:**
> Are you sure you're not running the GCJ version of Java instead of Sun's official OpenJDK version?

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

Yes, positive about that. All traces of GCJ removed.


> **xlinuks said:**
> I would suggest posting the source code.

It is some 50 classes so its not that easy to just look throught. And I dont have a simple way to make it accesible, Ill try to find that.


Anyway, I just suspect this has to do with cuncurrency because we arent 100% sure have to handle those threads...

---

### Post by xlinuks on 2008-06-03
If this is an Eclipse or NetBeans project - just zip it and post it here as an attachment, we'll open the project and run it, we (I) don't guarantee to find the answer but we'll try at least, without having a look at your program we unfortunately have few chances to help.

---

### Post by Jens_Li on 2008-06-03
> **xlinuks said:**
> If this is an Eclipse or NetBeans project - just zip it and post it here as an attachment, we'll open the project and run it, we (I) don't guarantee to find the answer but we'll try at least, without having a look at your program we unfortunately have few chances to help.

Thats obviously a very simple solution. Im gratefull towards anyone who have a look to spot anything suspicious in the code. Unfortunatly you will not be able to run it since it uses nearly 2mb of images and attachmets that big isnt allowed.

The main class is called ClientApp. The game is a space thruster with network support. It will propobly be hard for an outsider to get a grip of the structure thought, its all a bit messy.

And Ill try to find a way to put it all up...

---

### Post by NormR2 on 2008-06-03
Would it be possible for us to test your program with our own images? 

For example if I insert a statement in the GUIImage.loadImage() method to set name to one local file, what happens?
```

name = "myimg";   // use same image for all .pngs
```

---

### Post by Jens_Li on 2008-06-03
I appreciate your help, I just have to find somewhere to put it all up, there are quite  a lot of images so its a lot of work to create dummy versions of them all.

I get back when I have a way to show it all.


But have anyone heard of weard differences between how threads are handled unders differnet os:s?

---

### Post by NormR2 on 2008-06-03
The list of images I was refering to would be created by going to the images diretory and entering something like:
    ls *.png > listOfImages.txt

I dummied out the loadImage() method as above but then ran into a problem with an infinite loop in GUIAnimation so changed the following as noted:

```
		while ( (image = GUIImage.loadImage(name + "_" + i)) != null  && i < 20) {  //NCR added i < 20
```

What is the program supposed to do after you click the Single user button?

**You probably need to convert your references to Canvas to use Swing components like JPanel.**

I recently ported a program that was working on XP to Ubuntu and found that the mouseListeners worked differently and that the x,y values returned by some methods for component placements were different.  The program had been AWT and I converted it to Swing. The new version now works on both XP and Ubuntu.

---

### Post by NormR2 on 2008-06-04
Your main() method should setup the gui and exit, not keep control. Try something like this to put the forever loop on its own thread:
```

	public static void main( String[] args )
	{
		System.out.println( "Starting..." );
      javax.swing.SwingUtilities.invokeLater(new Runnable() {  //NCR
         public void run() {
      		final ClientApp ca = new ClientApp();
            // Put mainloop on own thread
            new Thread(new Runnable() {
               public void run() {
                  ca.mainLoop();   // start main loop
               }
            }).start();
         }
     });

		System.out.println( "Exiting..." );
	}


```

---

### Post by xlinuks on 2008-06-04
> **Jens_Li said:**
> Thats obviously a very simple solution. Im gratefull towards anyone who have a look to spot anything suspicious in the code. Unfortunatly you will not be able to run it since it uses nearly 2mb of images and attachmets that big isnt allowed.

The main class is called ClientApp. The game is a space thruster with network support. It will propobly be hard for an outsider to get a grip of the structure thought, its all a bit messy.

And Ill try to find a way to put it all up...

Google offers free hosting with lots of space, I usually put there anything above 1MB when I have to share with someone.
See
> pages.google.com
Look at the screenshot, there's an "upload" link to the lower right.

---

### Post by Jens_Li on 2008-06-04
> **NormR2 said:**
> Your main() method should setup the gui and exit, not keep control. Try something like this to put the forever loop on its own thread:


Yeah, I guess your right, this is exactly the kind of thing we didnt know how to do right. Im thinking, if you scew stuff like this up, maybe it will produce slightly different results on different systems.

-> xlinuks: Cheers, that saves me some time looking around.

Heres a link to the complete project (Eclipse):
[http://jenslidestrom.googlepages.com/CallistoCarnival.zip](http://jenslidestrom.googlepages.com/CallistoCarnival.zip)
( feels a bit embarasing showing it to other people though, hole thing is full of cheap hacks)

 
Acctualy it runs better than I remenbered, but worse than it does on other systems. And problem 1.) behaved totaly different on different systems.


( xlinuks: I noticed links in russian on your screenshot. im propobly going to Moskva this summer to study russian. Have any advice for that?)

---

