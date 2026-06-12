---
title: "Missing Frame Title"
date: 2006-10-23
forum: Programming Talk
---

### Post by mitesh_agg on 2006-10-23
I am a starter in java programming.
I learned to create the GUI frame usin java awt package.
the code is as follws:  

import java.awt.*;
public class Ex1 {
  private Frame f;
 public Ex1() {
  f= new Frame("hello");
 }
 public void launchFrame() {
  f.setSize(400,300);
  f.setVisible(true);
 }
 public static void main(String a[]) {
  Ex1 gw=new Ex1();
  gw.launchFrame();
 }
}

The code works fine in Windows XP but in Ubuntu when class file runs the title "hello" of frame is missing.
I am using JSDK 1.5 update 9 in both operatin syatem and all paths are well defined as all of my codes tried bfore run properly on both systems.

Please help me out.

---

### Post by hod139 on 2006-10-23
Running your posted code I get the title "hello".  Are you sure you are using Sun's java and not gnu's?  See [this post]("http://ubuntuforums.org/showthread.php?t=201378") for setting up the repository version of Sun's java and making it the default on your system (just ignore the Eclipse stuff unless you want to install eclipse too)

---

### Post by mitesh_agg on 2006-10-24
As per ur reply i checked the compiler version "javac -version" and jre version "java -version".
Both of them are jdk1.5.0_9.
I do want to mention that, being ignorant about previously installed packages -GJC and jdk1.4, jre1.4 (as checked in Synaptic), i downloaded and installed suceesfully (without errors) SDK 1.5 update 9 with netbeans.
After installing the downloaded package I set the $PATH variable as
PATH=/opt/jdk1.5.0_9/bin:$PATH in .bash_profile successfully.
Still I am getting the mentioned problem.
Can u guide me if there is someting wrong installations or conflicts that i should modify.:confused:

---

