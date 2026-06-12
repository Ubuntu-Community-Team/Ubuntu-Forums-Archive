---
title: "Cant get the app icon I created to run."
date: 2012-10-12
forum: New to Ubuntu
---

### Post by bGonz on 2012-10-12
I used main menu to create an application icon to put in my launcher for minecraft.
I have the minecraft.jar set to excutable and i have openjdk 7 set at the default program to run.
I have done this before and it worked just fine but idk why it isn't working now, also the game runs just fine from the original .jar file.
When i am in main menu and go to the Laucher properties it is like this
Type: Application
Name:Minecraft
Command: /home/brad/.minecraft/minecraft.jar
I also have set a .png for the icon
I have tried making the command a direct link to the minecraft.jar 
I have also tried Xmx1024M -Xms1024M -jar /home/brad/.minecraft/minecraft.jar
Why will the game not run through the launcher or even through dash home?

---

### Post by spcwingo on 2012-10-12
Try changing this:

> **bGonz said:**
> Command: /home/brad/.minecraft/minecraft.jar


To this:

```
Command: java -jar /home/brad/.minecraft/minecraft.jar
```

---

### Post by bGonz on 2012-10-12
ahhh thank you !!! it worked!

---

### Post by spcwingo on 2012-10-12
No problem.  I glad I could help. :)

---

