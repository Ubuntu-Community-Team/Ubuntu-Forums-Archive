---
title: "Web Server that can run JSP files"
date: 2008-07-04
forum: Programming Talk
---

### Post by balagosa on 2008-07-04
Hi all, this is my first time posting on this side of the forums. Let me get to the point, I will be creating JSP files for my School Project and I have no idea to what web server can support them. We use **TomCat Apache** at school and I was wondering if it is a good web server. 

Currenlty, I have Apache2 installed for PHP programming, and MySQL inter-action. Apache2 was a pre-requisite of the program that I was aiming for; PHPMyAdmin.

Question:
1) If I can run JSP using Apache2, how can it be done?
2) What other web servers will be good for JSP and Ubuntu?
3) Can anyone please cite differences between JSP and JS? I know that JS is embedded on HTML. What I want to know are the pros and cons of each.

---

### Post by xlinuks on 2008-07-04
2) JBoss (Red Hat, only J2EE 1.4), WebSphere (IBM), GlassFish (Sun Microsystems, supports J2EE 1.5 !!). The latter is enterprise class (Tomcat is not), free, open source and GPLed.

3) js is the extension scripts written in JavaScript, while jsp stands for Java Server Pages written in Java.
Java != JavaScript.

---

### Post by balagosa on 2008-07-04
> **xlinuks said:**
> 

3) js is the extension scripts written in JavaScript, while jsp stands for Java Server Pages written in Java.
Java != JavaScript.

Then TomCat for me then, Support the Open-Source Communtiy. 

#3, those are definition-based differences, I already know about those. What I want to know are technical differences.

e.g. JavaScript would be better to use for web than Applets because Applets would take more time to load on a webpage.

---

### Post by xlinuks on 2008-07-04
There are _many_ technical differences, but, the first one I can think of (which may not matter to you) is the speed: JPS pages are compiled under the hood into servlets which are Java classes (executed by the JVM which is much faster than the .js interpreter) which means they are executed much faster than JavaScript scripts (but again, it's not gonna be important to you).

> e.g. JavaScript would be better to use for web than Applets because Applets would take more time to load on a webpage.
JPS != Applets.
JSP is for the server-side, while .js can be used for both client and server side. 

GlassFish and Tomcat - both of them are open source and under a "cool" licence, so one can't really say that "Tomcat" is more community-friendly than, say, GlassFish (without bias).
btw Java is also fully open sourced and under GPL, have a look here:
[http://osdir.com/Article10100.phtml](http://osdir.com/Article10100.phtml)

---

### Post by balagosa on 2008-07-04
> **xlinuks said:**
> There are _many_ technical differences, but, the first one I can think of (which may not matter to you) is the speed: JPS pages are compiled under the hood into servlets which are Java classes (executed by the JVM which is much faster than the .js interpreter) which means they are executed much faster than JavaScript scripts (but again, it's not gonna be important to you).

GlassFish and Tomcat - both of them are open source and under a "cool" licence, so one can't really say that "Tomcat" is more community-friendly than, say, GlassFish (without bias).
btw Java is also fully open sourced and under GPL, have a look here:
[http://osdir.com/Article10100.phtml](http://osdir.com/Article10100.phtml)

Actually, that kind of difference will matter to me. It will not matter now while I am still a student but it will be vital in work scenarios, where efficiency + time is important! Would there be a link that you can refer to the so-called technical differences?

I said **Tomcat** in the previous post because it is what my school used. When I would get into trouble concerning the Server Configuration, I can just ask my teacher to help with. This is the reason why I chose Tomcat.

---

### Post by xlinuks on 2008-07-04
> e.g. JavaScript would be better to use for web than Applets because Applets would take more time to load on a webpage.
In the initial post you are clearly talking about server-side programming, but, since you mention applets, I think you might misunderstand the usage case of Applets over JSP (Applets have almost nothing in common with JSP). Besides, regardless of what you're using on the server-side, you can use whatever you wish on the client-side, that is, if you choose JSP (for the server-side) - you can use JavaScript on the client side, no problem here.

---

### Post by balagosa on 2008-07-04
> **xlinuks said:**
> In the initial post you are clearly talking about server-side programming, but, since you mention applets, I think you might misunderstand the usage case of Applets over JSP (Applets have almost nothing in common with JSP). Besides, regardless of what you're using on the server-side, you can use whatever you wish on the client-side, that is, if you choose JSP (for the server-side) - you can use JavaScript on the client side, no problem here.

:) sorry for this. To make it clear, I was referring to embedding applets to webpages; like a Circuit Simulator which I saw on one website. If I would be using JavaScript, then I can find an alternative to embedding an applet, which requires time to load; maybe make an equivalent program to that applet.


-----------------------------------------------------------------------------
Help: What is the default port for Tomcat? I remembered in school it was localhost:**8080**? I am not sure about this. Can anyone help me?

---

### Post by xlinuks on 2008-07-04
Can you please give a link to the Circuit Simulator you're talking about?
By "load" time I guess you mean the JVM "startup" time, cause the size of an applet is generally smaller than the equivalent code written in JavaScript (due to .jar compression) - in this sense the applets "load" time is generally faster.

---

### Post by balagosa on 2008-07-04
I am sorry but I lost the link. It was on my previous laptop. The last time I touched that link was a year ago.

Isnt 8080 the default port for Tomcat? hmmm...it is not working.
**/etc/init.d/tomcat5.5 status** yields 
*** Tomcat servlet engine is running with pid 23268**

---

### Post by xlinuks on 2008-07-04
8080 is the default one if you use the official installation - which I always do. If you used the version from the repos - they could change it.

---

### Post by balagosa on 2008-07-04
yeah I used the repos. Any idea where I can locate the Config?

------------------------------------------------------------------------------------------------

Okay, got the port number. port = 8180.

So, to access **localhost:8180**

---

### Post by xlinuks on 2008-07-04
Here's for Gutsy, could be same for Hardy:
> Tomcats configuration is in /etc/tomcat5.5
[http://programminglinuxblog.blogspot.com/2007/11/tomcat-55-on-ubuntu-gutsy.html](http://programminglinuxblog.blogspot.com/2007/11/tomcat-55-on-ubuntu-gutsy.html)

---

### Post by hendra40 on 2009-10-14
Hello all,
I will try to clear the answer.
I test it and it is success.

The steps to run JSP files on ubuntu with tomcat6 are :
1. Install tomcat6, tomcat6-admin, tomcat6-example from synaptic package manager.

2. Change port if needed.
   In my case, I change the port because I have installed oracle on port 8080
   Type sudo gedit /etc/tomcat6/server.xml
   Look on the connector port that contains 8080, change it with any number example 8081.

3. Save it

4. Save your JSP files in /var/lib/tomcat6/webapps/ROOT using gksu nautilus 

5. Type sudo /etc/init.d/tomcat6 start in terminal

6. Type in browser with [http://localhost:8081/your_folder/your_file.jsp](http://localhost:8081/your_folder/your_file.jsp)
   ( case if you make folder on step 4 )
   ( case if you change port to 8081 default is 8080 )

I hope my explanation is useful for all members in ubuntu forum who wants run jsp in ubuntu.

:)

---

