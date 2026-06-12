---
title: "problem loading image to JPanel with getResource()"
date: 2009-06-27
forum: Programming Talk
---

### Post by badperson on 2009-06-27
I'm trying to load an image to a Panel with the following code: 

```
	private Image image;
	
	public LaunchScreenPanel(){
		URL	url = this.getClass().getResource("lib/images/gui-image.jpg");
			if(url==null){
				System.err.println("URL is null: ");
				System.err.println(this.getClass());
				System.err.println("dir: " + System.getProperty("user.dir"));
			}
		image = Toolkit.getDefaultToolkit().getImage(url);
	}
```

I'm getting this output:

> URL is null: 
class com.jasonwardenburg.goalapp.gui.LaunchScreenPanel
dir: /media/files/code/java/Workspaces/GoalApplication
Uncaught error fetching image:
java.lang.NullPointerException
	at sun.awt.image.URLImageSource.getConnection(URLImageSource.java:115)
	at sun.awt.image.URLImageSource.getDecoder(URLImageSource.java:125)
	at sun.awt.image.InputStreamImageSource.doFetch(InputStreamImageSource.java:258)
	at sun.awt.image.ImageFetcher.fetchloop(ImageFetcher.java:189)
	at sun.awt.image.ImageFetcher.run(ImageFetcher.java:153)\

the URL object looks like it's null...I looked around on the internet and found examples like the above...anyone know how to fix this? 
The code works when I have the file loaded as a File object within eclipse. But when I run the code as a jar or through a bash file, it can't find the image (when loaded as a file instead of getResource());
thanks,
bp

---

### Post by froggyswamp on 2009-06-27
You're dealing with one of those ugly situations that happen while learning one language or another.
The getResource() method returns slightly different paths for apps packed inside a .jar.
Debug yourself: let it print (show as a GUI alert) the URL when running from a .jar file and when running "as usual".
So, you'll end up creating a "helper" method that "understands" when the app is running from a jar when when not, and based on that build the correct path to your lib/image.
You're prolly gonna fiddle with class.getProtectionDomain.getSourceCode() or so, don't remember for sure.

---

### Post by pbrockway2 on 2009-06-27
```
this.getClass().getResource("lib/images/gui-image.jpg");
```

This will look for the image relative to whereever LaunchScreenPanel.class is located.  The nice thing about this is that it will find the image (providing it is there!) regardless of whether LaunchScreenPanel.class is a file (in which case it looks in subdirectories) or an entry in a jar archive (in which case it looks in the relevent subentry).

Follow the advice given and actually print the URL.  Then check that you have actually put the image in the same place you are looking for it.

For a simple deployment where the classes and the image (and other) resources are located in known locations relative to one another, the getResource() approach will be effective whether or not the classes and resources are combined into a single jar archive.

---

### Post by froggyswamp on 2009-06-28
> **pbrockway2 said:**
> 
For a simple deployment where the classes and the image (and other) resources are located in known locations relative to one another, the getResource() approach will be effective whether or not the classes and resources are combined into a single jar archive.
My bad, I confused that with detecting at runtime the dir the app is located in.

---

### Post by badperson on 2009-06-28
so the code I posted may have worked had I executed it from a jar as opposed to within eclipse? 

The image also failed to display when I executed the code off the command line using the relative path. 
bp

---

### Post by pbrockway2 on 2009-06-29
So where in the LaunchScreenPanel constructor are you looking for the image?  Ie what is printed with
```

System.out.println(this.getClass().getResource(""));

```

lib/images/etc is being resolved relative to that location.  And the image (whether it be a file or a jar entry) must be at that place or you will get a null URL.

---

### Post by badperson on 2009-06-29
thanks,
that code you suggested returns the following: 
> in constructor: file:/media/files/code/java/Workspaces/GoalApplication/bin/com/jasonwardenburg/goalapp/gui/

I think it has something to do with the fact that eclipse creates the bin and src folders. 

I tried modifying the code you suggested to this:
```
this.getClass().getResource("../../../../")
```

which returns 

> file:/media/files/code/java/Workspaces/GoalApplication/bin/

but if I try to go up again to get at the parent dir, I get null. 
Maybe I need to set this up in ant? 
Or can I import the image folder into eclipse?
bp

---

### Post by badperson on 2009-06-30
fixed it...I needed to move the folder that held the images under the "src" folder in eclipse. Then the getResource() method worked.

---

### Post by pbrockway2 on 2009-06-30
I'm glad you've got it working.

You're right - Eclipse seems to have been set to compile (or copy) the contents of the src folder to the bin folder.  This bin folder is used as the classpath, so that you can't really go "above" it using getResource().

---

