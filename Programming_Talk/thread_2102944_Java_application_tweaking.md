---
title: "Java application tweaking"
date: 2013-01-08
forum: Programming Talk
---

### Post by TheodoreP on 2013-01-08
I am working on a hobby application that I have and will be uploading it to launchpad when I figure out how. The first or trunk version will be a basis for any java application. However I need a little help figuring out how to change the default java app icon to a custom logo/icon. Basically I need to know what the best file format is and how to set it in my code to retrieve said file for the icon.

---

### Post by bird1500 on 2013-01-08
If by "app icon" you mean the window icon:
javax.swing.JFrame.setIconImage(Image image)
or don't set any icon on the window but create and launch the app thru a ".desktop" file, like vuze/azureus does, which has an entry for the app/window icon.

---

### Post by slickymaster on 2013-01-09
> **MasterProgram said:**
> Basically I need to know what the best file format is and how to set it in my code to retrieve said file for the icon.
I usually use PNG format.
> **MasterProgram said:**
> ...how to set it in my code to retrieve said file for the icon.
```
import java.awt.Image;
import java.net.URL;
import javax.swing.*;

public class MyClass extends JFrame{
    
    public MyClass(){

        setTitle("Your App Title");
        URL url = YourApp.class.getResource("images/yourimage.PNG");
        ImageIcon img = new ImageIcon(url);
        Image icon = img.getImage();
        setIconImage(icon);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
    }

    public static void main (String args[])
    {}
}
```

---

### Post by TheodoreP on 2013-01-10
I have a project page on launchpad for this application, however I still need to learn a good way and the best way to upload an eclipse java app project to the launchpad using the terminal and bazaar explorer. I've asked this before and been told to subscribe to the launchpad-users team. I did this, however I have not been answered yet. Please somebody help me.

---

### Post by bird1500 on 2013-01-10
Off topic, I myself tried using launchpad to host, compile & build my app and boy is it sophisticated, they require you to know a lot of stuff like bazaar, signatures management, how what where goes (and when), etc, so good luck with that, I gave up.

---

### Post by TheodoreP on 2013-01-10
> **bird1500 said:**
> Off topic, I myself tried using launchpad to host, compile & build my app and boy is it sophisticated, they require you to know a lot of stuff like bazaar, signatures management, how what where goes (and when), etc, so good luck with that, I gave up.

Understandable, I probably keep going with it though. Nice to know that it isn't just me that has problems with it. What would be nice is if they could just have an upload area on the site.

---

### Post by TheodoreP on 2013-01-13
I am using the eclipse version that is offered on the software centre and I really want to try the bzr-eclipse plug-in to send my program to the launchpad code hosting servers. However I find myself in the predicament that the eclipse marketplace is not included in the application. Does anyone know how I can get it. I find it really weird that eclipse indigo on my mac downloaded from the eclipse site and the eclipse juno that I just finished removing have it but the software centre version isn't up to date. Come to think of it I also checked for updates in eclipse and it told me that there was an update that it couldn't download and install for I have insufficient access. If someone could help me resolve that it might take care of the problem.

Adjust question, if I could get a little help in just being able to use eclipse itself to upload and maintain a code branch in launchpad that would really be of big help.

---

### Post by TheodoreP on 2013-01-15
Basically, I am having issues with uploading just certain items instead of full path directories. Any advice would be greatly appreciated. Also, if anyone knows how to delete files and folders from the branch I would like you to share it as well. Peace Out!

---

