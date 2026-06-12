---
title: "[SOLVED] Missing Window Icon in Jar executable"
date: 2007-10-17
forum: Programming Talk
---

### Post by liviubero on 2007-10-17
Hy,
I am on Ubuntu-Feisty and running Java 6. 
I wrote an application in Java and wanted to add an Icon for the main window.
I added it, put all classes and image (a 16x16 pixels gif) in a jar file and tried it.
The window works and the icon is there, but under certain circumstances the icon is missing.
First, here is an extract of the Code:

```
public class Calc extends Frame
 implements WindowListener, ActionListener
  {
   .....
   public Calc()
  {
    ...
    setIconImage(Toolkit.getDefaultToolkit().getImage("icon.gif"));
    ...
 }
}
```The application contains the following files: Calc.class, Rechner.class, icon.gif.
I added all in a jar with this command:
```
jar -cvef Calc Calculator.jar *.*
```Now, the application works great in the following conditions:
- In Terminal, change in the directory where the whole stuff is (jar and classes and gif):
    [COLOR=Navy]cd Calculator/[/COLOR]
then run either
    [COLOR=Navy]java Calc[/COLOR] (this is the main class)
or
    [COLOR=Navy]java -jar Calculator.jar[/COLOR] (this is the jar which contains all)

The application won't show me the icon in the following conditions:

-If I try right click on the jar and then chose "Open with Sun Java 6 Runtime";
-If I try to open the jar from Terminal, but not being in the directory which contains the jar:
    java -jar Calculator/Calculator.jar

Otherwise, there are no problems.

Would someone have any idea?

---

### Post by mvs1207 on 2007-10-17
try this

```

   public class Calc extends Frame
 implements WindowListener, ActionListener
  {
   .....
   public Calc()
  {
    ...
    setIconImage(getImage("icon.gif"));
    ...
 }
}
  
   private Icon getImage(String name) {

        URL url = getClass().getResource(name);

        if(url == null) {
            return null;
        }
        return new ImageIcon(url);

    }

```

---

### Post by liviubero on 2007-10-17
```
Calc.java:213: cannot find symbol
symbol  : method setIconImage(javax.swing.Icon)
location: class Calc
setIconImage(getImage("icon.gif"));
^
1 error
```
It seems that the method setIconImage(Image) of the java.awt.Frame class won't take an Icon as parameter.

---

### Post by tenmillionmilesaway on 2007-10-17
Is the gif actually in the Jar file, or is it just in the folder with the jar file.  I have had problems in the past with this sort of thing because my gifs and such weren't actually in my jar file, or weren't where  the code thought they should be.  This would explain why your gif is displayed when you are in the same dir as the gif but not otherwise.  I don't know enough about making jars to know how to fix it but I do think that this could be your problem.

Richard

Edit: as far as i can see your original code is fine

---

### Post by mvs1207 on 2007-10-18
sorry my bad.. try this

```

public class Calc extends Frame
 implements WindowListener, ActionListener
  {
   .....
   public Calc()
  {
    ...
    setIconImage(Toolkit.getDefaultToolkit().getImage(getClass().getResource("icon.gif")));
    ...
 }
}

```

---

### Post by liviubero on 2007-10-18
[COLOR=Navy]tenmillionmilesaway[/COLOR]:
All files are there in the jar. If I look inside with File Roller, all necessary things are there.

 [COLOR=Navy]VMUKKAMALA[/COLOR]:
Thanks, this solved it.
Now it works.

Thank you all for your answers.
This forum is indeed great!

---

