---
title: "Access java class from javascript"
date: 2007-10-02
forum: Programming Talk
---

### Post by carteris21 on 2007-10-02
Hello,
     i need to write simple html with JavaScript which access java class. For example my class:

public class MyClass{
   public MyClass(){
   }
   public String method(){
       ...
   }
}

My Html something like this(but it's not working):

<html>
<head>
<script type="text/javascript">

function foo()
  {
  **var me = new Packages.MyClass();**
  
    document.write(**me.method()**)

  }
</script>
</head>
<body>

<input type="button" onclick="foo()" value="ok" />

</body>
</html>

What i should to insert/edit in my html?

thanks.

---

### Post by tenmillionmilesaway on 2007-10-02
So you're wanting to call a Java class from within a webpage?  I don't think that can be done.

---

### Post by Jussi Kukkonen on 2007-10-02
It's possible on some js environments (see e.g. Netscape Liveconnect), but it's not a  feature of any standard. I believe it is not possible on Spidermonkey (the mozilla browser js engine) but there is such functionality in e.g. the Rhino engine...

---

### Post by coffecup1978 on 2007-10-02
The java class must be used inside a java runtime environment e.g. SUN jre6 , not to be confused with the browsers java script engine. I guess you could include the classes in a java applet and have the java script to generate the code to load the applet through the java plug-in, if that gets you closer to your goal.

---

### Post by realstraw on 2007-10-03
Like what is posted above. Generally it is not possible, at least can not be easily implemented

---

### Post by pbrockway2 on 2007-10-03
It's quite easy to call public methods of Java applets from JavaScript.  I haven't done this with an "applet" which really does nothing but supply the method in question, so I thought I'd give it a go.

(Also I don't really know JavaScript so what follows might be a bit rough.)

First the java class - this MyClass.java, not MyFile.java by the way:

```
import javax.swing.JApplet;

public class MyClass extends JApplet {
    public MyClass() {}
    public String method() {
        return "Some result here";
    }
}
```

Next the html file:```
<html>
<head>

<script type="text/javascript">
function foo() {
    theApplet = document.getElementById("app");
        // The following line clobbers the document...
    //document.write(theApplet.method());
    document.getElementById("display").innerHTML = theApplet.method();
}
</script>

</head>
<body>

<applet id="app" width=0 height=0 code="MyClass.class"></applet>
<form>
    <p><input type="button" onclick="javascript:foo()" value="ok"></input></p>
</form>
<div id="display"></div>

</body>
</html>
```

This displays OK in Konqueror.  Although for some odd reason the page doesn't redraw itself when the button is clicked.  You have to expand the window slightly or cover/uncover it!)  FF doesn't do Java (I'm too lazy to set it up), but these files work OK in Windows (IE6).  so i guess that's konqueror thing.

You can access the applet method within JavaScript using the syntax document.applets[0].method() as well.  also you may want to check out the *mayscript* argument that can be included as part of the applet tag.

---

### Post by carteris21 on 2007-10-03
thanks, i will try to do it with applet.

---

