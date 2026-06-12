---
title: "Java Program did not work properly when i doubleclick to run"
date: 2013-10-24
forum: Programming Talk
---

### Post by Andrew_tan on 2013-10-24
Dear All Ubuntian:

i new to ubuntu (ubuntu 12.04LTS)and just started to learn java program.

i confuce with java program , i create program , set it to executable file, it run properly on eclipse (IDE) and terminal(after i export it) , but when i doubleclick to run nothing happen, anyone know why?? code as below:

<java code>
 import javax.swing.*;import java.awt.HeadlessException;
import java.io.*;
public class h {
    /**
     * @param args
     * @throws IOException 
     * @throws HeadlessException 
     */
    public static void main(String[] args) throws HeadlessException, IOException {
        // TODO Auto-generated method stub
           String a="";
     InputStream s=new FileInputStream("data.xml");
     int size=s.available();
        
     for(int j=0;j<size;j++){
         a=a+(char)s.read(); 
     } 
     
     JOptionPane.showMessageDialog(null,a);
  }


}
<java code end>

so i wrote another program to launcher this using Runtime.getRuntime().Exec(); method with a  JOptionPane.showMessageDialog(null, "open h.jar").
When i double click  it didn't launch my h.jar but the message show up, when i run with terminal every thing work fine , can anyone help me with this(confuse big time)?Code as below:


<java code>
import java.io.IOException;
import javax.swing.*;




public class launcher {


    /**
     * @param args
     * @throws IOException 
     */
    public static void main(String[] args) throws IOException {
        // TODO Auto-generated method stub
         JOptionPane.showMessageDialog(null, "open h.jar");
        @SuppressWarnings("unused")
    Process p=Runtime.getRuntime().exec("java -jar h.jar");
    }


}
<java code end>



Thank

---

### Post by ofnuts on 2013-10-24
A Java program is a class or a jar, but double clicking on it outside the IDE won't start it because the code in the class/jar should be executed by the Java interpreter (the "java" command) and your file explorer has likely no association between the jar/class types and java (and when it does, it is rarely useful). 

And when the whole code is in a JAR, java must be told which class carries the main(). So either:
[LIST]
[*]you specify both, the JAR as a place to look for classes, plus the class to run that java will find in the jar: "java -cp thejar.jar  theclass"
[*]you give only the jar, but the [MANIFEST.MF in the jar designates the "Entry point" class]("http://docs.oracle.com/javase/tutorial/deployment/jar/appman.html") : "java -jar thejar.jar"
[/LIST]

---

### Post by ICanHasNick on 2013-10-27
This is because the program doesn't find your file "data.xml"

When you double click on the jar file, it thinks it was launched from your home directory and looks there for the file.
Copy the file to ~/ and your program will work.

It would be much safer and more convenient to import the needed resource into your eclipse project 
and than load it with getClass().getRessource("/your_resources_package/data.xml")

---

### Post by Andrew_tan on 2013-10-28
[COLOR=#000000]ICanHasNick, your solution work wonderfully.


[/COLOR]Thank:P

---

