---
title: "&quot;Sun Java System Application Server&quot; Platform location"
date: 2007-04-28
forum: Programming Talk
---

### Post by Luft on 2007-04-28
I have installed Netbeans, GlassFish and Java in my new Festy install but when I try to create a visual web application using the Sun Java System Application Server I can't add the server.  I only have Tomcat available.  

I went into the server manager and clicked on the "Add Server" button.  The problem I'm having is that I can't seem to find the correct platform location.  It looks like GlassFish got installed under the /var/lib/ directory in a folder called "sunappserver."  But Netbeans seems unimpressed.  I've tried all of the sub folders under that directory but no joy.

---

### Post by jamesstansell on 2007-05-02
It sounds like you're taking the right approach.  I hope you find the answer and can post it here.

Have you tried to start glassfish manually?  That would be a good first step to make sure that it's installed and working properly.

I think netbeans might want  the domain directory.  The default one is usually called domain1 or something like that.  Does that exist under the /var/lib/sunappserver directory?

Have you searched or asked in the glassfish forums?

Regards,

-james.

---

### Post by UncleAl on 2007-07-11
I am having the exact same issue. Has there been any resolution?
I see that this post has been up since April.

I did find
[http://www.netbeans.org/issues/show_bug.cgi?id=90221]("http://www.netbeans.org/issues/show_bug.cgi?id=90221")
but that was no help. the '<!DOCTYPE' line was already in the xml.template file. Even when I
edited it to match the line in the URL exactly it had no effect...

Anyone?

---

### Post by nicolasdiogo on 2007-08-12
i am also having difficulties configuring glassfish with netbeans under Ubuntu Feisty 7.04.

it just can not find any domain that i configure using asadim tool.


i will keep on trying.

i am using java 6 and javac 6.

regards

---

### Post by markos.mevorah on 2007-11-23
Here It Is:

I installed all from Synaptic or by terminal:
netbeans5.5 glassfish and their dependencies

Now with the default Ubuntu installations you declare in Netbeans as this:

Platform: /usr/share/sunappserver

And for me I select 2. Register Local Domain

Then I define where I have the domain1 which is:
home/<username>/glassfish/domain1

Cool ...

---

### Post by prabubecse on 2008-06-03
I can get you. please tell me clearly how to add sun java application server . i m using netbeans 6.1. please reply as soon as possible.......

---

### Post by xlinuks on 2008-06-03
> 
The Sun GlassFish Enterprise Server is a comprehensive support offering for GlassFish, the leading open source and open community platform for building and deploying next generation applications and services. Previously named the Sun Java System Application Server, the Sun GlassFish Enterprise Server is ideal for Service-Oriented Architectures and Rich Internet Applications utilizing Java EE, PHP, AJAX and Ruby.

Thus you need GlassFish.
You can get it bundled with NetBeans from here:
[http://download.netbeans.org/netbeans/6.1/final/](http://download.netbeans.org/netbeans/6.1/final/)

Or install it from your Tools->Plugins, if the plugins list seems too large type in the searchbox "Glassfish" to find it faster.

---

