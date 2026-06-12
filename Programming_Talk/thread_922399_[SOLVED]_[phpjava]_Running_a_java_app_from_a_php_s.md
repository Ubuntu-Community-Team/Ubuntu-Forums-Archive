---
title: "[SOLVED] [php/java] Running a java app from a php script"
date: 2008-09-17
forum: Programming Talk
---

### Post by Pyro.699 on 2008-09-17
Hello,

I currently have a very simple script that basically just takes a screenshot of the servers desktop, and saves it to a file. The main class is called **ScreenCapture.class** and contains the information needed to do this. Another class called **Main.class**, which is basically just a test file to see if i can get this working. Here are the contents of those 2 files

```

package main; 
 
import java.awt.image.RenderedImage; 
import java.awt.AWTException; 
import java.awt.Rectangle; 
import java.awt.Robot; 
import java.awt.Toolkit; 
import java.io.File; 
import java.io.IOException; 
import javax.imageio.ImageIO; 
 
public class ScreenCapture { 
 
    public String imageType = "jpg"; 
    public String imageName = null; 
    public String saveLocation = null; 
     
    public  void capture() { 
         
        if(imageName==null || saveLocation==null){ 
            return; 
        } 
         
        try { 
            Robot robot = new Robot(); 
            Rectangle area = new Rectangle(Toolkit.getDefaultToolkit().getScreenSize()); 
            File target = new File(saveLocation, imageName + "." + imageType); 
            saveImageToFile(robot.createScreenCapture(area), target); 
        } catch (AWTException e) { 
            System.err.println("Exception while capturing screen. " + e); 
        } 
    } 
 
    private void saveImageToFile(RenderedImage renderedImage, File target) { 
        try { 
            ImageIO.write(renderedImage, imageType, target); 
        } catch (IOException e) { 
            System.err.println(e); 
        } 
    } 
} 

``````

package main;

import main.ScreenCapture;

public class Main{

    public static void main(String[] args){
        System.out.println("Started");
        ScreenCapture sc = new ScreenCapture();
        sc.imageName = "Screen";
        sc.saveLocation = "/home/cody/Desktop/";
        sc.capture();
        System.out.println("Finished");
    }

}

```Now, when i go to the terminal, go to the location and type **java main.Main** it works fine, and there is a jpg file on my desktop named **Screen.jpg**. Now when i try to execute this from a webpage using a php script, the script starts, but doesn't finish. Heres my php script.

```

<?php
if(!$fh = popen("/usr/bin/java main.Main", "r"))
{
    echo ("Could open java");
}

while(!feof($fh))
{
    $output = fgets($fh, 1024);
    echo ("$output<br>");
}

pclose($fh);
?>

```When i browse to the location of this file, it displays "Started" but it does not display the "Finished" text, which should appear after the script has taken the screenshot. The screenshot is meant to be taken from the server computer, and not from any guests that are browsing the site.

Thanks for any help
~Cody Woolaver

---

### Post by NoReflex on 2008-09-17
You could try to use the system command from php : 
```
system("java main.Main")
```
Best wishes,
NoReflex

---

### Post by Pyro.699 on 2008-09-17
Nope, i tried using this exact php file and it still only returned "Started"
```

<?php
system("java main.Main");
?>

```

Thanks again
~Cody Woolaver

---

### Post by Reiger on 2008-09-17
This suggests (a) you don't get an EOF character or (b) you interpret it wrongly (i.e. the Java encoding for EOF differs from the PHP one and therefore isn't signalled in the PHP loop; or even (c) you do get an EOF character and do pick it up correctly; but (unfortunately) get it prematurely.

So suppose (a): 
- Do you take care to close your streams *after* sending the last bit of output? (Answer: you don't, I never see you closing System.out. for instance)
So suppose (b):
- Java signals an EOF as -1 value for a 4-byte integer in raw byte input streams; perhaps that'll help you work something out? ...
So suppose (c):
- You use at least 3 output streams; time to review those?

From looking at your code I suspect it's (a) as I've seen something similar when I coded 'persistent' pipes in Java. I never closed it so I never received the EOF mark (hence infinite read-loop). I solved that by combining the int available(); and void read(byte [] buffer, int number_of_bytes); methods.

---

### Post by Pyro.699 on 2008-09-17
> **Reiger said:**
> This suggests (a) you don't get an EOF character or (b) you interpret it wrongly (i.e. the Java encoding for EOF differs from the PHP one and therefore isn't signalled in the PHP loop; or even (c) you do get an EOF character and do pick it up correctly; but (unfortunately) get it prematurely.

So suppose (a): 
- Do you take care to close your streams *after* sending the last bit of output? (Answer: you don't, I never see you closing System.out. for instance)
So suppose (b):
- Java signals an EOF as -1 value for a 4-byte integer in raw byte input streams; perhaps that'll help you work something out? ...
So suppose (c):
- You use at least 3 output streams; time to review those?

From looking at your code I suspect it's (a) as I've seen something similar when I coded 'persistent' pipes in Java. I never closed it so I never received the EOF mark (hence infinite read-loop). I solved that by combining the int available(); and void read(byte [] buffer, int number_of_bytes); methods.
Im sorry but i dont quite understand what your saying exactly.

---

### Post by drubin on 2008-09-17
> **NoReflex said:**
> You could try to use the system command from php : 
```
system("java main.Main")
```
Best wishes,
NoReflex

I would much rather use it returns the output of the commands that are executed.. 
```
$var=shell_exec('java main.Main');
```
[http://us3.php.net/shell_exec](http://us3.php.net/shell_exec)

---

### Post by drubin on 2008-09-17
Something else to try is to change the output streams.
Replace ALL 
```
 System.err.println with System.out.println
```

---

### Post by HotCupOfJava on 2008-09-17
Reiger is suggesting that you need to close the output stream for your file. If you were using the ImageIO.write method that is passed an ImageOutputStream or an OutputStream (for "output")that would be true. But I notice you are using the version where you pass a File, so closing the stream should not be necessary. The ImageIO.write method does return a boolean, though. perhaps you should test this. It will return a false if no appropriate ImageWriter is found....

Also, I notice you use the Robot class from java.awt - Robot performs some low-level functions that may be restricted from webpage launching (for security purposes). I'm not sure about that, but you may need to find a way to work around it.....It would certainly explain the behavior you have observed.

---

### Post by drubin on 2008-09-18
> **HotCupOfJava said:**
> Also, I notice you use the Robot class from java.awt - Robot performs some low-level functions that may be restricted from webpage launching (for security purposes). I'm not sure about that, but you may need to find a way to work around it.....It would certainly explain the behavior you have observed.

How is the Robot class going to know that it is being executed from with in a web page?

---

### Post by Pyro.699 on 2008-09-18
I'm actually going to have to agree that it is the robot class. I modified the 2 java files to see how it all works. Heres the changes:

```

package main;

import main.ScreenCapture;

public class Main{

    public static void main(String[] args){
        System.out.println("000");
        ScreenCapture sc = new ScreenCapture();
        System.out.println("001");        
        sc.imageName = "Screen";
        System.out.println("002");
        sc.saveLocation = "/home/cody/Desktop/";
        System.out.println("003");        
        sc.capture();
        System.out.println("Finished");
    }

}

```

```

package main; 
 
import java.awt.image.RenderedImage; 
import java.awt.AWTException; 
import java.awt.Rectangle; 
import java.awt.Robot; 
import java.awt.Toolkit; 
import java.io.File; 
import java.io.IOException; 
import javax.imageio.ImageIO; 
 
public class ScreenCapture { 
 
    public String imageType = "jpg"; 
    public String imageName = null; 
    public String saveLocation = null; 
     
    public void capture() {
        System.out.println("004"); 
        if(imageName==null || saveLocation==null){ 
            return; 
        } 
         
        try {
            System.out.println("005"); 
            Robot robot = new Robot();
            System.out.println("006"); 
            Rectangle area = new Rectangle(Toolkit.getDefaultToolkit().getScreenSize());
            System.out.println("007"); 
            File target = new File(saveLocation, imageName + "." + imageType);
            System.out.println("008"); 
            saveImageToFile(robot.createScreenCapture(area), target);
            System.out.println("010"); 
        } catch (AWTException e) { 
            System.out.println("Exception while capturing screen. " + e); 
        } 
    } 
 
    private void saveImageToFile(RenderedImage renderedImage, File target) { 
        try {
            System.out.println("009"); 
            ImageIO.write(renderedImage, imageType, target); 
        } catch (IOException e) { 
            System.out.println(e); 
        } 
    } 
} 

```

It will print out **005** but stops their, and doesn't print **006** so it stops the second that the robot class is declared.

Anyone have a way to take a screenshot (with the methods i need) without using AWT?

Thanks
~Cody Woolaver

---

### Post by HotCupOfJava on 2008-09-18
> **rubinboy said:**
> How is the Robot class going to know that it is being executed from with in a web page?

I don't believe the Robot class itself does know that - but the Java Virtual Machine probably does. When Java first came out, there was major concern about the security of it - users did not want to hit a website and have a potentially malicious program running on their machine. This was addressed and alot of extra security has been built into Java. Anything that may have the ability to access low-level machine functions is restricted from running remotely. This is actually a good thing.

From the Java SE6 Robot documentation:

"Note that some platforms require special privileges or extensions to access low-level input control. If the current platform configuration does not allow input control, an AWTException will be thrown when trying to construct Robot objects. For example, X-Window systems will throw the exception if the XTEST 2.2 standard extension is not supported (or not enabled) by the X server. "

---

### Post by Pyro.699 on 2008-09-18
I dont want the program to run on the guests computer, i want it to run on the hosts computer. Is there anyway to get around that block?

---

### Post by drubin on 2008-09-18
> **HotCupOfJava said:**
> I don't believe the Robot class itself does know that - but the Java Virtual Machine probably does. When Java first came out, there was major concern about the security of it - users did not want to hit a website and have a potentially malicious program running on their machine. This was addressed and alot of extra security has been built into Java. Anything that may have the ability to access low-level machine functions is restricted from running remotely. This is actually a good thing.

I do agree it is a good thing I would just love to know how it knows the script is running remotly. Php executes on the server site. from the OS's point of view it runs on the same machine.

Just something that would interest me.

---

### Post by HotCupOfJava on 2008-09-18
> **Pyro.699 said:**
> I dont want the program to run on the guests computer, i want it to run on the hosts computer. Is there anyway to get around that block?

You may have to look at the actual source code behind Robot.....I'm trying to look for it myself now......

---

### Post by HotCupOfJava on 2008-09-18
> **rubinboy said:**
> I do agree it is a good thing I would just love to know how it knows the script is running remotly.

That is a good question - I really don't know the answer. Honestly it is just an educated guess on my part. I know that Robot throws a exception when you attempt to create a Robot under certain circumstances. It is logical to assume that is what is happening here. But I don't know exactly HOW the JVM knows what is going on. I suppose we could test that theory by placing the creation of the Robot object into a try/catch block.

---

### Post by Pyro.699 on 2008-09-19
Is their anyway to remove that restriction? Later on in my scripts development im going to require a lot of modules from Robot. Basically heres the breakdown of the script.

Im on dial-up at home and its a real pain, so what I'm doing is developing a way i can remotely control a computer that I've placed in a location with faster internet. I have several java classes designed to mimic keystrokes and mouse jestures. The site will consists of a textbox and an image screen. The image (which is where this part comes into play) can be refreshed only at will (because rapid image refreshing could cause lag). The text box will be where i can type in commands that will allow me to controll different aspects of the computer. I understand that on a normal computer this is a HUGE securety risk, but the laptop that this is going on; is absolutly worthless so i personally dont mind this securety risk (although there will be a .htaccess to get to the webpage thats set up.

Thanks again guys
~Cody Woolaver

---

### Post by Pyro.699 on 2008-09-19
After doing a bit of searching ive come accross this; [AWTPermission](http://jav.sun.com/j2se/1.3/docs/api/java/awt/AWTPermission.html) which (from my understanding) is what controls the security settings for the AWT objects. The only problem that i find is that i dont know how to apply it to the robot class to allow the useage of it. Any ideas?

Thanks
~Cody Woolaver

---

### Post by HotCupOfJava on 2008-09-19
OK - I may have a solution for you (this is cool - I've learned ALOT helping with this little project!) In the terminal window, type "policytool". The Java policy tool utility will execute. You can use this to change the permissions for individual applications! Click the Add Policy Entry button, which opens the policy entry dialog box.Type "file://<location of your .class file>" next to "CodeBase:". Click the Add Permission button. This will open another dialog box. You need to set the AWTPermission, so you select that. Then you would select createRobot below that. Click OK and then click Done. You should then be able to create the Robot!

Hope that works

---

### Post by Pyro.699 on 2008-09-19
awesome, is there anyway to do a directory of classes? because there is alot of them in the script. Thanks a ll ton for you help too

EDIT:
I did everything that the above mentioned, set the file to "file://var/www/main/ScreenCapture.class" and added the AWTPermision but it is still not working. I tried to change the **try/catch** to [SecurityException]("http://java.sun.com/j2se/1.3/docs/api/java/lang/SecurityException.html") and it still worked, meaning that it isnt throwing a security violation.

---

### Post by HotCupOfJava on 2008-09-19
Durn.....now I'm stumped......

---

### Post by Pyro.699 on 2008-09-20
I know that perl has the ability to run scripts, what if i made a special script in perl that could open the java file? it would be like Php -> Perl -> Java anyone think that would work?

---

### Post by drubin on 2008-09-21
> **Pyro.699 said:**
> I know that perl has the ability to run scripts, what if i made a special script in perl that could open the java file? it would be like Php -> Perl -> Java anyone think that would work?

I do not have high hopes for that, Because it would still be running through a shell only environment. 

But give it  a try and post the results. If it works then you have found a work around.

---

### Post by Pyro.699 on 2008-09-21
i created this file:

test.pl
```

exec("java main.Main")

```

and that worked fine, it showed the numbers 001 -> 010 and also Finished. I then changed the *index.php* file to the exact same thing except replaced **java main.Main** with **perl test.pl** and it only showed 001-005. So that brings me to think that maybe it has something to do with apache's settings, does anyone know if there is something in the php.ini file about this kind of thing?

Thanks again for all your help, this is a huge part of my script xD i probally should have looked into this but i didnt really expect this kind of proplem.
~Cody Woolaver

---

### Post by drubin on 2008-09-21
WAIT, I have an idea......:)

What user does apache run us? Did you install apache vim sudo apt-get ?

if you did then the user is www-data

Try this. 
```
sudo su www-data 
cd script folder
./test.pl

```

This  is because apache runs under the specified user Java is very fussy about permissions if it does not have access to run something it will throw that error. We are just running the script "as" the same user as apache would to see if the access user specific or apache?  

Good luck, let me know how this goes.

---

### Post by Pyro.699 on 2008-09-21
Ooooo, i think your onto something!

[quote=terminal]
cody@Charmander:/var/www$ sudo su www-data
[sudo] password for cody: 
$ cd /var/www
$ perl test.pl
000
001
002
003
004
005
No protocol specified

(.:10963): Gtk-WARNING **: cannot open display: :0.0
[/quote]

Now that i think about it, it makes complete sence why it wasnt working. Because the only user that the display is showing for is **cody**. What if i changed the user from **www-data** to **cody**?

Thanks
~Cody Woolaver

---

### Post by drubin on 2008-09-21
> **Pyro.699 said:**
> 
Now that i think about it, it makes complete sence why it wasnt working. Because the only user that the display is showing for is **cody**. What if i changed the user from **www-data** to **cody**?

Simple when you work it out hey :) 

It would work. but a security whole.mmmmmm not sure if you would like your "admin" user running stuff from external php script. (That *could* be hacked). 

If this is only going to be used on an internal network, with no external access I would say it is ok But I would **highly** recommend getting a second option. 

It is rather late now. I am about to hit the hay but I will try and think about it and get back to you.

---

### Post by Pyro.699 on 2008-09-21
Alright, well as i said before this computer is going to be used for just downloading at an external source... there will be no personal information on the computer at all so i dont mind if it gets hacked. Although i will be adding quite a bit of security to it to begin with. What would be the best way to do this?

Thanks
~Cody Woolaver

---

### Post by Pyro.699 on 2008-09-21
Alright after doing a lot of searching online I've realized something quite obvious if you think about it. The way that this works is a lot like another problem i had a while back with running java applications in crontab. I had to add **DISPLAY=:0.0** (:0.0 is my display id) to the top of the file to set the display, and that's what i need to do with PHP. So, i really dont know where i need to go with this because i have a feeling that just changing the "run user" from **www-data** to **cody** wont work because the application still doesnt have a set display. I had an idea that involve editing many files so i thought i would ask before i made too many changes. What if i added **xhost +www-data** to the top of the **/etc/init.d/apache2** file which would add that user to the display, atleast i think how** xhost** works.


**[UPDATE]**
Ok, just learned something new. I don't know how the **php5** executable works, but i ran **php5 /var/www/index.php** and it worked completely, made the screenshot, and then saved it to the desktop. So its not the permissions, it is the display.

Thanks
~Cody Woolaver

---

### Post by HotCupOfJava on 2008-09-22
Well, I'm glad you got that all worked out. Your persistence paid off....and I got to learn something in the process. Win/win

---

### Post by Pyro.699 on 2008-09-23
I did learn quite a bit from all this, but the problem is still there. I m unsure of how to get the permissions changed around so that the display runs on **:0.0**

---

### Post by Pyro.699 on 2008-09-23
**I GOT IT!!**

I was searching online for different terminals using xservers and other things, and came accross this ;)
```

<?php
$fh = shell_exec("xterm -display :0.0 -e \"java main.Main\"");
?>

```

And it works :)

Thanks so much to everyone for all their help <3
~Cody Woolaver

---

### Post by drubin on 2008-10-05
I know this thread is kinda old but it was very on topic so I thought I should post the answer here

[http://www.php.net/manual/en/java.examples.php](http://www.php.net/manual/en/java.examples.php)

This might be a neat way of running java code through php.

---

### Post by Pyro.699 on 2008-10-05
That is quite a neat topic, although wouldn't it be difficult to have large amounts of java code? And i believe the problem was having the display setup, not running the actual code.

Thanks tho

---

### Post by drubin on 2008-10-05
> **Pyro.699 said:**
> That is quite a neat topic, although wouldn't it be difficult to have large amounts of java code? And i believe the problem was having the display setup, not running the actual code.

Thanks tho

Ye I have never tried it. I do think it can be rather complex... hehe. But  thought it was on topic so posted it. If you/any one else uses this post the result I would to know how it holds up :)

---

### Post by doodsangel on 2008-10-28
Hi Guys/Girls,

I'm unable to make the proposed solution stick. I'm working on Web-based signature application (for mail signatures) for our company. They want it rendered to a .jpg so that users cannot stuff around with the text. 

I have found "html2image" software which renders a jpg from a web-page which is thus exactly what I want.

The code I want to execute is the following:

```
   $cmd = 'xterm -display :0.0 -e "export   LD_LIBRARY_PATH=/html2image; cd /html2image; ./html2image http://localhost/signature/signatureFiles/'.$fileName.'.html /var/www/html/signature/signatureDone/'.$fileName.'.jpg"';
   $result = shell_exec("$cmd");
```

When the PHP script executes this code, nothing appears to happen (not creating the JPG file). When I look at the console, I can see the xterm popping up and dissapearing, but it appears that its not executing the commands:

```
 export LD_LIBRARY_PATH=/html2image; cd /html2image; ./html2image http://localhost/signature/signatureFiles/'.$fileName.'.html /var/www/html/signature/signatureDone/'.$fileName.'.jpg
```

Another test that I did was to create an echo statement:
```
echo $cmd;
```
When the code is supposed to execute, it displays the whole cmd string, which I then copy and paste into a putty session. It executes fine through putty and creates the JPG.

Please help, even if suggesting another way of creating the JPG.

---

### Post by Pyro.699 on 2008-10-28
Does the code run normally in the terminal? Sometimes the best thing to do is run a mockup of the script.... get all the "test files" your going to run and then try that.

also, check the outputs...


```

command1 > /home/user/folder/cmd1.out; command2 > /home/user/folder/cmd2.out; command3 > /home/user/folder/cmd3.out

```

another problem i ran into was allowing access to the xhost... try typing in
**xhost +:locals**

(or something close to that read back a bit)

---

### Post by doodsangel on 2008-10-29
Thanks for the advice. Will try.

---

### Post by shahryar on 2009-05-26
were u able to resolve this issue?

---

### Post by drubin on 2009-05-26
> **shahryar said:**
> were u able to resolve this issue?

Notice the solved tag :) 

BTW running GUI from with in webpages would not be recommend since the user/permisions would need to change but running java is pretty simple and easy using the shell_exec command (see previous comments)

---

