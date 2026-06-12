---
title: "Developing a network monitoring app..."
date: 2006-08-15
forum: Programming Talk
---

### Post by JordanSPE on 2006-08-15
Hey All,

I'm looking to develop an application that ping's a node on a network every 10 min and makes a circle red if it is unable to communicate.   I want to be able to monitor 80+ nodes on a continual scan, so that if one of the nodes can not be reached, one of 80 circles will change color, thus informing whoever may be looking at the screen.

I have very sparse programming experience, but do have limited background in Visual Basic.  I am looking for some advice, from seasoned programmers regarding what language they think is best suited to the development of an application of this nature, and someone of my skill level.  I would like it to have a GUI front end, so a visual language would be preferred.

I am not adverse to reading, so if someone could point me to a tutorial or a book that would be greatly appreciated as well.  I have no doubt that this project will take me some time, it is more of a personal goal, although it has excellent usability for what i am going to use it for (A bank monitoring branch offices).

Thanks!

---

### Post by aggyb on 2006-08-15
Hi there,
     Have you considered having this set up as a web page?  This would allow it to be accessed remotely and rather than run the pings every ten minutes you could have it ping when the page is loaded.  This sort of task would be reasonable to accomplish using SSI (server side includes) or PHP.  There are good manuals available for both of those options.

If you definately are after a stand-alone GUI app for this I would suggest either Java (since the documentation at java.sun.com is fantastic) or Mono (since monodevelop is quite easy to get the hang of).

Hope this is in some way helpfull.

AggyB

---

### Post by LordHunter317 on 2006-08-15
> **JordanSPE said:**
> 
I'm looking to develop an application that ping's a node on a network every 10 min and makes a circle red if it is unable to communicate.   I want to be able to monitor 80+ nodes on a continual scan, so that if one of the nodes can not be reached, one of 80 circles will change color, thus informing whoever may be looking at the screen.Use nagios.  It can do this for you.

If you're a bank monitoring branch offices, nothing personal, but nothign you write is likely going to met the actual requirements.  I suspect there are legal requirements too you may not be aware of if your bank chooses to implement such things (Nagios may not be adequate either).  You should do some more research on this field to make sure a custom-rolled solution really will be acceptable.  Big Brother is another server-monitoring product.  On the Windows side, we have MOM.

---

### Post by JordanSPE on 2006-08-15
Hey, 

Thanks for the responses, I am checking out all the recommendations and reading some tutorials to get a better idea of each solution, it's complexity and what it offers. 

To clarify, the application does not need to truly “monitor” the branch offices.  It won't be  pulling any information, and will run on an internal network, behind a CISCO firewall.  In actuality all it needs to do is ping the print server (cause it's always on).  If it is unable to ping the print server, we know there is a connectivity issue, and can then call the branch and provide troubleshooting. That is the extent of what it needs to do.

We have a “homemade” application that does this now, that was programed in REXX (I did not write it).  It uses a simple command line interface, that displays a line to indicate connectivity. It's not that we truly need a replacement, but it's an application I would enjoy programing, and could build on with experience.

Thanks for the all the info.  I am open to all ideas and suggestions so please feel free.

Thanks Again!

JordanSPE

---

### Post by LordHunter317 on 2006-08-16
I'd just write something in Python wrapping around the ping command then, really.  Shouldn't be too difficult.

---

### Post by JordanSPE on 2006-08-17
If anyone cares, I decided to play with Python.  It came highly recommended from a lot of people in the forums.  I read the first 50 pages of &#8220;How to Think Like a Computer Science&#8221;, as recommended in another thread, and it pretty much sealed the deal.  I was impressed with how much sense the basics seemed to make.  I appreciate all the help.

Thanks!

---

