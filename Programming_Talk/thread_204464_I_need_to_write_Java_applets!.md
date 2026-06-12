---
title: "I need to write Java applets!"
date: 2006-06-27
forum: Programming Talk
---

### Post by Hambo on 2006-06-27
Hello all.

I'm a reasonably new Linux user, and am still dual booting. I have been learning Java at college, by just writing simple Java applets. At the moment, I am using RealJ under Windows. It is a very simple program, and I find it easy to use.

Could anyone suggest to me a program I can get for Linux that I can write applets in and compile, that isn't too complicated? I also don't have much idea about what the Java SDK is, or if I even have it installed on my machine, or if I even need it to write applets.

Any help would be appreciated!

---

### Post by DolphinWeb on 2006-06-27
Really, any text editor will do, at least, for making applets. For compiled programs...You could use Eciplise. (sp?) I think what you're asking for is an IDE. If so, AnyJ, JUDO, or NetBeans would work quite well!

But, for something not that complicated, I'd look at a simple 2-window way: the terminal opened to your current directory, and gEdit opening your files and editing away!

---

### Post by Daverz on 2006-06-27
Netbeans has an excellent GUI builder called matisse and is very good in general for Java development.  I think it now edges out eclipse if you're doing GUI development.

---

### Post by AdamTheCamper on 2006-06-27
I ve learned java by making applets in Eclipse so there should be no problem. Only thing you need is working jwm and hit download on eclipse.org

[http://www.eclipse.org/downloads/download.php?file=/eclipse/downloads/drops/R-3.1.2-200601181600/eclipse-SDK-3.1.2-linux-gtk.tar.gz](http://www.eclipse.org/downloads/download.php?file=/eclipse/downloads/drops/R-3.1.2-200601181600/eclipse-SDK-3.1.2-linux-gtk.tar.gz)

---

### Post by hod139 on 2006-06-27
Eclipse is part of the ubuntu repositories, no need to download from Eclipse's website.  I even have a [howto]("http://ubuntuforums.org/showthread.php?t=201378") written for installing eclipse and Sun's Java.

---

### Post by Hambo on 2006-06-28
Thanks for the help guys, but I'm still not sure how to compile it and display the applet.

Do I have to compile an applet?

---

### Post by hod139 on 2006-06-28
Here is the official [Sun tutorial on applets]("http://java.sun.com/docs/books/tutorial/deployment/applet/index.html").  If anything in the tutorials is unclear, just post back.

---

### Post by Luggy on 2006-07-24
I'm having some problems getting an applet to compile. All the tutorials I can see tell me to go and compile the source code and then use appletviewer to view the resulting html file but I never get an html file ](*,) 

Here is the code I am working with and the output I get
```
import java.awt.*;
import java.applet.Applet;

public class HelloFromVenus extends Applet {
  public void paint(Graphics g) {
    Dimension d = getSize();
    g.setColor(Color.black);
    g.fillRect(0,0,d.width,d.height);
    g.setFont(new Font("Helvetica", Font.BOLD, 24));
    g.setColor(new Color(255, 215, 0)); // gold color
    g.drawString("Hello From Venus!", 40, 25);
    g.drawImage(getImage(getCodeBase(), "Venus.gif"),
                20, 60, this);
  }
}

```

```
paul@dapper:~/docs/school/CET431-Java/lab2$ javac HelloFromVenus.java
paul@dapper:~/docs/school/CET431-Java/lab2$ ls
chap02.html  HelloFromVenus.class  Hello.java
Hello.class  HelloFromVenus.java   Venus.gif
paul@dapper:~/docs/school/CET431-Java/lab2$

```

Can anyone help me out in what i'm missing to get this applet compiled?

---

### Post by hod139 on 2006-07-24
You need to create the html file yourself.  See the section on deploying applets in the tutorial I linked: [http://java.sun.com/docs/books/tutorial/deployment/applet/deployindex.html](http://java.sun.com/docs/books/tutorial/deployment/applet/deployindex.html)
basically, you need this
[HTML]
<html>
<head>
<title>Title</title>
<body bgcolor=white>
        <applet code=HelloFromVenus.class width="800" height="200">
        Your browser does not support the applet tag.
        </applet> 
</body>
[/HTML]

---

### Post by Luggy on 2006-07-25
Awesome! Thanks dude!

---

