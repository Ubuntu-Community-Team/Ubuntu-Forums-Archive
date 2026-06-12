---
title: "Sign Java Applet"
date: 2010-09-17
forum: Programming Talk
---

### Post by Vistz on 2010-09-17
I'm creating a GUI Applet and I'm having some difficulty signing the applet. Is there an easy way to sign it?

---

### Post by Finalfantasykid on 2010-09-18
Very tediously -_-

Try this tutorial [http://forums.sun.com/thread.jspa?threadID=174214](http://forums.sun.com/thread.jspa?threadID=174214).  As far as I know there is no automated way to do it, just many semi-long steps using the terminal.

---

### Post by kahumba on 2010-09-18
Besides, signing doesn't yet mean the user will choose to trust it, because unless Oracle or the likes sign it for you - the applet will ask the user whether the user trusts the applet and if the user answers No - it would still run under no privileges.
Thus the first thing to do is to try to get along without the need to sign an applet at all, cause normal users don't have a clue about Java applets, how they work, what they're allowed to do by default and when they're "signed", about the Java/applet sandbox model etc, etc so their answer to the applet's security question will be pretty much random unless you explicitly inform each user to answer Yes.
And you also have to keep taking care of the signed applet cause the signed stuff in the applet expires in a given time frame and you need to re-sign it from time to time.
Yes, it's a pita.

---

### Post by Vistz on 2010-09-18
> **kahumba said:**
> Besides, signing doesn't yet mean the user will choose to trust it, because unless Oracle or the likes sign it for you - the applet will ask the user whether the user trusts the applet and if the user answers No - it would still run under no privileges.
Thus the first thing to do is to try to get along without the need to sign an applet at all, cause normal users don't have a clue about Java applets, how they work, what they're allowed to do by default and when they're "signed", about the Java/applet sandbox model etc, etc so their answer to the applet's security question will be pretty much random unless you explicitly inform each user to answer Yes.
And you also have to keep taking care of the signed applet cause the signed stuff in the applet expires in a given time frame and you need to re-sign it from time to time.
Yes, it's a pita.

I've already created my applet and I tried running it in a browser. But I've been getting an error saying ```
java.security.AccessControlException: access denied (java.io.FilePermission normal.gif read) 
```

"normal.gif" is one of the pictures I'm using. That's the only reason I'm trying to sign it.

---

### Post by Finalfantasykid on 2010-09-18
Can't you embed the gif in a jar?  That way you won't need to rely on File IO.

---

### Post by Vistz on 2010-09-18
> **Finalfantasykid said:**
> Can't you embed the gif in a jar?  That way you won't need to rely on File IO.
As of right now, I have no jar files, just .class, .java, and .gif files. I have just created a jar file called "Images" consisting of all of my .gif files. 

This is the code I use to access the .gif file

```
URL urlImage = getClass().getResource("Images"+ "//" + "normal.gif");
 ImageIcon normal = new ImageIcon(Toolkit.getDefaultToolkit().getImage(urlImage));
```When I run it, I get an error: 

```
java.lang.NullPointerException
    at sun.awt.SunToolkit.getImageFromHash(SunToolkit.java:832)
```

---

### Post by kahumba on 2010-09-19
Create a folder (in my case "res") in the folder where your source code is and put your images in it.
Then use this method to get images by name:

[PHP]
public static BufferedImage getImage(String name) {
    if (name == null || name.length() < 1) {
        return null;
    }
    try {
        URL url = Util.class.getResource("/res/" + name);
        if (url != null) {
            return ImageIO.read(url);
        }
    } catch (Exception exc) {
        //exc.printStackTrace();
    }

    return null;
}
[/PHP]Say you create a class Util.java and put this method there.
From now on you can load images by using Util.getImage("myImage.png");
It returns a buffered image or null if image not found.
The nice thing is that it automatically loads the image
1) From inside the corresponding jar file if the class files are already inside it, or:
2) From the folder on disk where your not-yet-inside-a-jar-file class files are located.
Which is the functionality you're probably looking for.

---

### Post by kahumba on 2010-09-19
PS
- you don't need to sign the applet any longer
- if you put the method in a class say "Main" (not "Util" as in my example) you'll obviously have to use [FONT=monospace]Main[/FONT][COLOR=#000000][COLOR=#007700].class.[/COLOR][COLOR=#0000BB]getResource[/COLOR][COLOR=#007700]([/COLOR][COLOR=#DD0000]"/res/" [/COLOR][COLOR=#007700]+ [/COLOR][COLOR=#0000BB]name[/COLOR][COLOR=#007700]);[/COLOR][/COLOR]

---

### Post by Vistz on 2010-09-19
> **kahumba said:**
> PS
- you don't need to sign the applet any longer
- if you put the method in a class say "Main" (not "Util" as in my example) you'll obviously have to use [FONT=monospace]Main[/FONT][COLOR=#000000][COLOR=#007700].class.[/COLOR][COLOR=#0000bb]getResource[/COLOR][COLOR=#007700]([/COLOR][COLOR=#dd0000]"/res/" [/COLOR][COLOR=#007700]+ [/COLOR][COLOR=#0000bb]name[/COLOR][COLOR=#007700]);[/COLOR][/COLOR]
Thank you. It works now.

---

