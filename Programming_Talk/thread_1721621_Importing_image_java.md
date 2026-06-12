---
title: "Importing image java"
date: 2011-04-04
forum: Programming Talk
---

### Post by orrymr on 2011-04-04
Hi guys, I'm having some trouble importing an image in java.
Here's the code snippet that's giving issues:
```

     public Agent()throws IOException{
         gridPos = new boolean [4] [4];
         gridPos [2] [1] = true; 
         xPos = 200;
         yPos = 200;
         agentImage = ImageIO.read(new File("littleMan.gif"));   //This is the line giving trouble
     }

```I've placed the file littleMan.gif in the same folder as my source. Here's the error console:
```

Exception in thread "main" javax.imageio.IIOException: Can't read input file!
    at javax.imageio.ImageIO.read(ImageIO.java:1291)
    at Agent.<init>(Agent.java:26)
    at GW.<init>(GW.java:30)
    at GW.main(GW.java:59)

```I don't know why it "Can't read input file!"

Thanks

---

### Post by PaulM1985 on 2011-04-05
You are using a relative path to the image.  Does this work if you use an absolute path?

Where is the image with respect to the file that you are running?

Paul

---

### Post by VernonA on 2011-04-05
Some things to watch out for.
1) Are you sure the filename is exactly right (remember it is case-sensitive)? Put the "new File" part on a separate line so you can (a) print the canonical path of the file, and (b) call the exists() method on it.
2) You can use the ImageIO.getReaderFormatNames() function to see what image types are supported. Make sure GIF is in the list. I have nver heard of a JVM which didn't support this right out-of-the-box, but you never know.
3) Are you running the classes from a prompt, or is this a big app that has been put in a Jar? To handle both I normally use the ClassLoader.getResource() call to get the initial path to my classes so I can work relative to that. Eg use something like:
```
    ClassLoader cl = Agent.class.getClassLoader();

    URL imgName = cl.getResource("littleMan.gif");

    if (imgName != null)
        return ImageIO.read(imgName);
    else
        System.out.println("Cant' find: "+ "littleMan.gif");

```
Hope this helps.

---

### Post by orrymr on 2011-04-05
1) - Yeah, the file name is exactly right. Also, I'm not sure what you mean by canonical path.
2)- System.out.println(ImageIO.getReaderFormatNames()); returns: [Ljava.lang.String;@e1899b :confused:
3)-I'm running it through Eclipse, so (as far as I understand), this would be the same as running it from a prompt (as opposed to having been put in a Jar). What difference does this make, by the way? I understand that the second line of your code,
```

URL imgName = cl.getResource("littleMan.gif");URL imgName = cl.getResource("littleMan.gif");  

```
finds the resource I'm looking for, in this case my gif, and stores its url, but I'm not quite sure what the first line is doing.

Thanks for your response; I think I'm starting to wrap my head around this, just a little :)

---

### Post by orrymr on 2011-04-05
this code 
```

         File f = new File( "src/littleMan.gif" );
         if( f.exists() ) {
             agentImage = ImageIO.read( f );
         } else {
             System.out.println( "Missing agent image" );
         }

```
seems to work. (I got it from: [http://ubuntuforums.org/showthread.php?t=858412](http://ubuntuforums.org/showthread.php?t=858412))

---

### Post by VernonA on 2011-04-05
1) The canonical name is a pompous way of saying the full path name. I used it because Java does distinguish between the two. For example, if you do "new File("../dummy")" when you are in /home/vernona/myproj and then ask Java to print the full and canonical names you will get "/home/vernona/myproj/../dummy" and "/home/vernona/dummy" respectively. These refer to the same file but the latter one looks neater and is called the canonical one because it is the shortest! I don't care which one you provide, but please give us one, as all the people reading this thread are convinced this is your mistake!

2) The getReaderFormatNames() function returns an array of Strings, not one string, so you need to do:
```
String[] tmp = ImageIO.getReaderFormatNames();
for (int i=0; i < tmp.length; i++)
    System.out.println("Got reader: "+ tmp[i]);

```
You are expected to read the manual occasionally!

3) When you run class files via IDEs, or cmd prompts or from Jars, then many assumptions occur about where resources are. You need to eliminate these by reading files in relation to the rest of your app, so that wherever it is installed your relative pathnames always work. The code snippet I supplied gets the full pathname of your Agent class, then searches from there to find the littleMan.gif file. Assuming you have put the gif in the same dir as the Agent.class file then it will find it. If you copy the whole dir to somewhere else, or even pack it all into a Jar, it will still find it.

4) On the other hand, and purely in order to get your app working, do try using a hard-coded name. Copy the file to, say, /tmp/littleMan.gif and change the code to open "/tmp/littleMan.gif". Now the potential for ****-up is greatly reduced, since this is completely unambiguous. Once you get this working we just have to work out where the path error is creeping in and fix it.

---

### Post by orrymr on 2011-04-05
1) - canonical: /home/orry/workspace/GridWorld/src/littleMan.gif (after using System.out.println("canonical: " + f.getCanonicalPath());)

2)-Makes sense :D

3 & 4)- Well, like I wrote in my previous post, 
```

File f = new File( "src/littleMan.gif" );
         if( f.exists() ) {
             agentImage = ImageIO.read( f );
         } else {
             System.out.println( "Missing agent image" );
         }

```seems to work. And this should be fine if I move my app around (like to another machine), since this is a relative pathname, assuming I copy my gif across as well.

Edit: clearly it's getting late... In my original post, I set the pathname as "littleMan.gif". It works when I set it to "src/littleMan.gif"... This still doesn't make sense to me since my class file is in the src folder as it is

---

### Post by VernonA on 2011-04-05
As you've noted, the file-name you originally used was wrong. Paul and myself (and I'm sure many others) immediately guessed this, hence our replies. When you distribute an app it is not normal to send out your src, so the code fragment you showed is still only a temporary fix. You do need to decide how you are going to package your app and then use code like I showed you to look for files relative to your classes.
For example, when I write apps, I keep things like logos and help files in src/Resources. When I compile I put my class files in a separate ../work file. This makes it easy to create a Jar file contain these classes plus Resources/*. To load the logo I use code like the example I showed to read "Resources/Logo.jpg" and it will find it. If a user unpacks the Jar (it is only a Zip after all) on, say, a Windows machine, the code will still work. That's the kind of robustness you want to aim for.

---

### Post by orrymr on 2011-04-05
Well using Eclipse my .class files are automatically put into a bin folder. I didn't realise this. I though that if the resource was in the same folder as my .java file I'd be fine, but obviously this isn't the case. It makes a whole lot more sense now. Thanks for your patience, Vernon, in this and the other thread; I truly appreciate it. Hopefully I can get this project flowing a little more smoothly now :D

---

