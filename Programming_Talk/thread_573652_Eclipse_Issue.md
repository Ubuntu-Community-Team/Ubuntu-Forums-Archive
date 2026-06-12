---
title: "Eclipse Issue"
date: 2007-10-11
forum: Programming Talk
---

### Post by RyanZec on 2007-10-11
I am using the PDT Eclipse(the PHP version) and have a issue,  I have created a workspace and then a project.  I go to create a new file and it tells me i need to select source folder but when i browser nothing exist and i can't create one(i have a folder in the root of the project but that does not show up, anyone know what this would happen?

---

### Post by RyanZec on 2007-10-12
anyone know why this is happening, Eclipse seems like the best soultion for an editor but this does not make any sense.

---

### Post by potsofdirt on 2007-10-12
I was experiencing a similar problem to you. After looking in the workspace/.metadata/.log file and googling some of the error messages I found a Russian page that helped.

First, everyone said I needed to go to Window->Open Perspective->Other and select PHP. I did not have the PHP option.

The issue seems to be what version of Java I was running. The Russian page recommended 1.5. Here's how to get it running:

sudo apt-get install sun-java5-jre
sudo update-alternatives --config java
# Select v1.5.0

Now you should be able to fire up Eclipse and select the PHP perspective.

---

### Post by RyanZec on 2007-10-12
> **potsofdirt said:**
> I was experiencing a similar problem to you. After looking in the workspace/.metadata/.log file and googling some of the error messages I found a Russian page that helped.

First, everyone said I needed to go to Window->Open Perspective->Other and select PHP. I did not have the PHP option.

The issue seems to be what version of Java I was running. The Russian page recommended 1.5. Here's how to get it running:

sudo apt-get install sun-java5-jre
sudo update-alternatives --config java
# Select v1.5.0

Now you should be able to fire up Eclipse and select the PHP perspective.

i have that installed and selected.  i was having issue just opening eclipse without that .

let em try to excplain my issue setp by step.

I am currently in PHP Perspective
File->New->PHP Project(Name: Test| Directory: /var/www/test)
Finish
(at this point i would exspect to see something in a tab showing the project name but nothing so i continue)
File->New->PHP File(Name: index.php)
!!!!HERE IS THE PROBLEM!!!!
It show i have to pick a Source folder so i click browse
There are no folders and i can't create anything so what do i do now???

---

### Post by RyanZec on 2007-10-12
I just tried to create a project in the workspace directory and that works.  Why can i not make a project in a different folder?  

The reason is that i don't want to have to copy file to the server root directory, rather just have the project directory in the root so when i save in eclipse the file on the server(localhost server) is saved whithout having to copy.

---

### Post by coldNsunny on 2007-11-25
Hi RyanZec,
I am not very experienced with eclipse but I have noticed that the dialog for a new file will only show the defined project folders.  When I want to save to a different folder I put the folder in a new project.  It helps to have the php perspective with the navigator pane open.   I hope this helps.
Scott.

---

### Post by coldNsunny on 2007-11-25
Hi RyanZec,
I am not very experienced with eclipse but I have noticed that the dialog for a new file will only show the defined project folders.  When I want to save to a different folder I put the folder in a new project.  It helps to have the php perspective with the navigator pane open.   Have you made sure it's not a permissions issue? I hope this helps. 
Scott.

---

