---
title: "OpenGL VNC Qualms"
date: 2009-08-06
forum: Programming Talk
---

### Post by JohnnySage50307 on 2009-08-06
Ok, I'm having some issues with a simulation that I'm writing.  Originally, I started coding all of this in Microsoft Visual Studio 2008 using OpenGL 2.6 (GLUT 3.6).  Recently, when I compiled some old OpenGL code (stuff I submitted as homework durring the spring semester that I know worked), I get an error that reads:
 
[FONT=Courier New]The application has failed to start because its side-by-side configurarion is incorrect. Please see the application event log for more detail.[/FONT]
[FONT=Courier New][/FONT] 
Out of a bit of frustration, I decided to try to migrate my code to my Ubuntu Server.  Reading several things, it appeared that all I needed to do was attach the -lglut flag.  When I am working on my server machine itself, everything runs all fine.  However, if I vnc into the server and run the application, I get the following error:

[FONT=Courier New]freeglut (/home/johnny/Graphics/Assignment1): OpenGL GLX extension not supported by display ':1.0'[/FONT]
[FONT=Courier New][/FONT] 
My question is how do I correct this?  When I used PuTTY to SSH into the server, I enabled X11 forwarding.  I do feel this has something to do with the client I'm using, however I need to be able to VNC and run OpenGL applications--especially since I would like to demo my simulation by mid September!!
 
As always, thanks to everyone who helps!!

---

### Post by slavik on 2009-08-06
VNC and X forwarding are separate. VNC creates a new X session for you (without OpenGL accelaration). once you have forwarding, you simply should be able to run a GUI app.

---

