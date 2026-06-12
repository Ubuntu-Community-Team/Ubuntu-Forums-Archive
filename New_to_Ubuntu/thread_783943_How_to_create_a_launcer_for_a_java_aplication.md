---
title: "How to create a launcer for a java aplication ?"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by pauldinu on 2008-05-06
Hi. I would like to create a launcher for Hattrick organizer. The file is located in /media/GAMES/HO/HO.sh. If i try to create a normal launcher the program never opens i do not get any errors i just click it and nothing happens. I found a thread about creating a java launcher for another program but i couldn't follow that information since it was for another application and i do not know much about ubuntu :(. Can u please tell me step-by-step on how to create my launcher ? Best regards.

---

### Post by kpkeerthi on 2008-05-06
Right-click on desktop, choose Create Launcher and enter **/media/GAMES/HO/HO.sh** under 'Command'

---

### Post by pauldinu on 2008-05-06
> **kpkeerthi said:**
> Right-click on desktop, choose Create Launcher and enter **/media/GAMES/HO/HO.sh** under 'Command'

already tried that... after creating the launcher when i try to run it nothing happens :confused: i have read [here](http://ubuntuforums.org/showthread.php?t=154948) but i don't know how to get it to work for my application

*edit* i tried to place the HO folder in the /home/paul/HO/HO.sh but still no luck ...

---

### Post by terrorsathan on 2008-05-06
If you run /media/GAMES/HO/HO.sh it works normally?
Try running it in the terminal (double click on HO.sh > run in terminal), maybe it'll display an error.

regards

---

### Post by kpkeerthi on 2008-05-06
Are you able to run the sh file from command line? What happens when you type the below commands at command prompt?
```
/media/GAMES/HO/HO.sh
```
```
/home/paul/HO/HO.sh
```

---

### Post by pauldinu on 2008-05-06
> **terrorsathan said:**
> If you run /media/GAMES/HO/HO.sh it works normally?
Try running it in the terminal (double click on HO.sh > run in terminal), maybe it'll display an error.

regards
no errors when runing in the terminal... the application opens just fine

> **kpkeerthi said:**
> Are you able to run the sh file from command line? What happens when you type the below commands at command prompt?
```
/media/GAMES/HO/HO.sh
```
```
/home/paul/HO/HO.sh
```
i pressed alt+f2 and typed ```
/media/GAMES/HO/HO.sh
```
```
/home/paul/HO/HO.sh
```
nothing happened

---

### Post by pauldinu on 2008-05-07
i found how to create a java application launcher [here](http://ubuntuforums.org/showthread.php?t=154948) but i dont know how to get it to work for my problem ...

---

### Post by MrWES on 2008-05-07
I used Movie Manager, which is a Java application; here is my launcher.

```
java -jar /home/bill/Programs/MeDs-Movie-Manager/MovieManager.jar
```

---

### Post by Znort_Ubern00b on 2008-05-07
> **MrWES said:**
> I used Movie Manager, which is a Java application; here is my launcher.

```
java -jar /home/bill/Programs/MeDs-Movie-Manager/MovieManager.jar
```

Then looking at that try 

java -jar /folder/to/you/filename.sh

---

### Post by kpkeerthi on 2008-05-07
> **Znort_Ubern00b said:**
> Then looking at that try 

java -jar /folder/to/you/filename.sh

No.. that won't work. When invoking java with -jar option the target should be a valid jar file containing appropriate manifest information. A manifest file (usually Manifest.mf) in a jar files describes the class path, main class, etc required to launch a java application.

---

### Post by kpkeerthi on 2008-05-07
> **pauldinu said:**
> no errors when runing in the terminal... the application opens just fine

When you run this command in a terminal window, does it open a GUI? Or is just a command-line based application?
```
/media/GAMES/HO/HO.sh
```

---

### Post by pauldinu on 2008-05-07
> **kpkeerthi said:**
> When you run this command in a terminal window, does it open a GUI? Or is just a command-line based application?
```
/media/GAMES/HO/HO.sh
```
when i type this in a terminal i get "bash: No such file or directory"

---

### Post by kpkeerthi on 2008-05-07
> **pauldinu said:**
> yeah that doesen't work :(

If you are unable launch the application from command-line, you will not be able to launch it from a 'launcher'. 

You need to get the program working from command line in the first place.

---

### Post by pauldinu on 2008-05-07
ok thank you for your support

---

