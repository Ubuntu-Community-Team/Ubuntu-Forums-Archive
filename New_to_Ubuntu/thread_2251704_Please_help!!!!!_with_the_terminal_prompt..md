---
title: "Please help!!!!! with the terminal prompt."
date: 2014-11-06
forum: New to Ubuntu
---

### Post by matthew_Epperson on 2014-11-06
When I try adding somthing it ask me for system product name:$ i just bought this computer and idk what to do!!!! I have the password but not the Systen Product name!!!! Please help ill add pictures if neeeeded!!!!

---

### Post by coffeecat on 2014-11-06
What is the make and model of computer, and what operating system is installed on it? Is it Ubuntu?

---

### Post by Impavidus on 2014-11-06
Can you explain what you were trying to do and how you tried to do that? Which version of Ubuntu do you have? Any other information on your system (like hardware) that you can provide?

Do you mean you opened a terminal and got a line looking like```
user@some-name:~$
```That is a default prompt. It is waiting for a command.

---

### Post by matthew_Epperson on 2014-11-06
M8 when i go into put commands this is it : rick@rick:System Product - Name: -$

Yeah kinda! Idk what to do

I know the passwords and all that, just not the damn product name or whatever it is!!!!!!!!

I bought it off of someone its asking me for the product name and idk what to do i need help

Complete begginer...
\

---

### Post by steeldriver on 2014-11-06
That is just the default *shell prompt* that results if you don't enter your own choice of hostname during installation - it is not expecting you to input that information now

---

### Post by matthew_Epperson on 2014-11-06
Would i be able to delete the original account so i can start freash, I really appreciate the input!!!!!!

---

### Post by coffeecat on 2014-11-06
Where is it asking for the product name? Exactly what is it saying? 

A steeldriver has already said, "rick@rick:System Product - Name: -$" is simply the system prompt.

What are you trying to achieve? If you are being presented with a command prompt, then are you not seeing a graphical desktop? Some more information, coherently expressed, might help others to help you.

---

### Post by matthew_Epperson on 2014-11-06
Im trying to get Java jdk , when i try putting it in, thats what it asks me, along with my password ( which i know )

I might be able to send some pics?

file:///C:/Users/Makana/Downloads/IMG_20141106_043138.jpg

can you help me m8 please

[img]img_20141106_043138[/img]

heres a pic of my problem help please, ill send some paypal if i can fget this figured out!!              [COLOR=#000000][INDENT]file:///C:/Users/Makana/Downloads/IMG_20141106_043138.jpg[/INDENT]


[/COLOR]
[COLOR=#000000][B][RIGHT][/RIGHT]
[/B][/COLOR]

---

### Post by howefield on 2014-11-06
Please use the Edit Post button rather than fresh ramblings a minute after the previous.

Also using the "paperclip" icon will allow you to add an image to your post.

---

### Post by matthew_Epperson on 2014-11-06
thank you sir can you help me out tho with this computer im clueless

---

### Post by buzzingrobot on 2014-11-06
You need to post the images somewhere (like imgur, perhaps) and post links here. 

The "C:" in "file:///C:/Users/Makana/Downloads/IMG_20141106_043138.jpg" indicates you're using a Windows machine, or at least dualbooting.

---

### Post by grahammechanical on 2014-11-06
When we install Ubuntu we are asked for our name and a user name. The installer will offer our first name as a suggested user name.

 We also need to put in a name for the computer/system so that it can be recognised if it is connected to a local network. The installer will make a suggestion and the suggestion is: System Product Name. That is right!!!!!!!!!!!!!

That should have been edited by the person who installed Ubuntu into something more meaningful. The name given for the computer appears as part of the prompt in the terminal.

I have several installations of Ubuntu. I use the partition label as part of the computer/system name. Right now I am typing from an install of Ubuntu on sdb8 (partition 8 on the second hard disk) and this is the prompt I get in the terminal.

> graham@sdb8-Roll-Dev:~$

So, now you know my user name and the name I have given to this particular installation of Ubuntu. Is it clear now? 

At least you know the administrator password. You can now go to System Settings>User Accounts and use the password to change the user name to one of your choosing. Now all that is needed is to find out how to change the Device name that appears in Details.

Regards.

---

### Post by matthew_Epperson on 2014-11-06
it wants me to put in a product name like a password

[http://imagebin.ca/v/1gMlrzJEdT7m](http://imagebin.ca/v/1gMlrzJEdT7m)

---

### Post by steeldriver on 2014-11-06
> **matthew_Epperson said:**
> it wants me to put in a product name like a password

No. It's just an arbitrary "prompt string" - indicating that the terminal is ready to accept any command that you type

---

### Post by matthew_Epperson on 2014-11-07
Anyone out there that can get me some help? [http://imagebin.ca/v/1gNoVcQ8CV](http://imagebin.ca/v/1gNoVcQ8CV)             I dont know the command after that or what to do

[IMG]http://imagebin.ca/v/1gNoVcQ8CVmH[/IMG] help please i dont have the password / code for that

---

### Post by deadflowr on 2014-11-07
> **matthew_Epperson said:**
> Anyone out there that can get me some help? [http://imagebin.ca/v/1gNoVcQ8CV](http://imagebin.ca/v/1gNoVcQ8CV)             I dont know the command after that or what to do

You need to fix your image, as it keeps showing up as file not found for this link.
The other posted image link shows up just fine.

Anyway what command are you trying to run?

---

### Post by CantankRus on 2014-11-07
> **matthew_Epperson said:**
> [IMG]http://imagebin.ca/v/1gNoVcQ8CVmH[/IMG] help please i dont have the password / code for that

Listen to what people are saying.
Every terminal has what your seeing.
It's not asking you to input anything specifically.
eg 
when I open a terminal I get this (yours will be different depending on your user and computer name).....
```
[COLOR="#FF0000"]glen@Trusty:~$ [/COLOR]
```

Then if I want, I type in a command and press Enter.
When the command has finished it returns to the command prompt.
eg I type in the command **date** it runs the command then returns to the [COLOR="#FF0000"]command prompt[/COLOR]
```
[COLOR="#FF0000"]glen@Trusty:~$[/COLOR] **date**
Fri Nov  7 17:06:48 AWST 2014
[COLOR="#FF0000"]glen@Trusty:~$[/COLOR]
```

From your image in post #14 , you ran a command, it finished and returned to the command prompt for you to run another command **if you wish**.

---

### Post by matthew_Epperson on 2014-11-07
Java JDK i need it installed

[http://imagebin.ca/v/1gNoVcQ8CV](http://imagebin.ca/v/1gNoVcQ8CV) mate look at the bottom whats its asking what do i do then<

---

### Post by lisati on 2014-11-07
You should be able to install OpenJDK Java runtime library using the Software Centre.

---

### Post by lisati on 2014-11-07
> **matthew_Epperson said:**
> [http://imagebin.ca/v/1gNoVcQ8CV](http://imagebin.ca/v/1gNoVcQ8CV) mate look at the bottom whats its asking what do i do then<

I'm getting an "Imagebin - file not found" error message when I visit the link.

---

### Post by CantankRus on 2014-11-07
> **matthew_Epperson said:**
> [http://imagebin.ca/v/1gNoVcQ8CV](http://imagebin.ca/v/1gNoVcQ8CV) mate look at the bottom whats its asking what do i do then<
Relax, make a cup of tea and reread the thread.
Maybe you already installed java.
Have you run any terminal commands to install java.

In the terminal run 
```
java -version
```

Copy and paste your output.
eg
```
[COLOR="#FF0000"]glen@Trusty:~$[/COLOR]** java -version**
Picked up JAVA_TOOL_OPTIONS: -javaagent:/usr/share/java/jayatanaag.jar 
java version "1.8.0_25"
Java(TM) SE Runtime Environment (build 1.8.0_25-b17)
Java HotSpot(TM) 64-Bit Server VM (build 25.25-b02, mixed mode)
```

---

### Post by matthew_Epperson on 2014-11-07
yes mam 12.04 , its an hp desktop

you sir area genius

I need JAVA64bit

---

### Post by Impavidus on 2014-11-07
Just open the software centre, type **openjdk java** in the search box and select either java 7 or java 6. Then click install. If it already has been installed, the install button is replaced by an uninstall button. No need for the terminal. If you run a 64 bit Ubuntu, then you'll automatically get a 64 bit java.

---

### Post by whitesmith on 2014-11-07
The way not to be clueless is to read the first webpage in my sig line. Many of your problem appear semantic: you simply are not speaking our language, nor we yours. An answer isn't going to rise magically out of so great a degree of entropy. ***Peruse the webpage, then please get back to us!*** Warm regards.

---

