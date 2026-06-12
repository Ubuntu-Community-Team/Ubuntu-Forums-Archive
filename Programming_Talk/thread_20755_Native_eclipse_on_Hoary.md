---
title: "Native eclipse on Hoary?"
date: 2005-03-18
forum: Programming Talk
---

### Post by cow_racer on 2005-03-18
I read somewhere that the native version of eclipse will be shipped wih hoary?  I am interested since I have a slow machine.

---

### Post by smallguy on 2006-05-01
[COLOR="Silver"](sorry about this 'me too'-message, but me too, i would be interested to see native eclipse running on ubuntu. that's why i am bringing the subject to the top of the list again... )[/COLOR]

so has anyone heard news about native eclipse being ported to debian/ubuntu?

some links for people wanting to know what this is all about:
* article by linuxjournal.com [http://www.linuxjournal.com/article/7413](http://www.linuxjournal.com/article/7413)
* description on the 'classpath showcase' [http://developer.classpath.org/mediation/ClasspathShowcase](http://developer.classpath.org/mediation/ClasspathShowcase)

---

### Post by kaamos on 2006-05-02
You mean this?
> 
$ apt-cache search eclipse | grep gcj
ecj-bootstrap-gcj - bootstrap version of the Eclipse Java compiler (native version)
eclipse-ecj-gcj - Native version of the Eclipse Java compiler
eclipse-jdt-gcj - Java Development Tools plug-ins for Eclipse (GCJ version)
eclipse-pde-gcj - Plug-in Development Environment to develop Eclipse plug-ins (GCJ version)
eclipse-platform-gcj - Eclipse platform without plug-ins to develop any language (GCJ version)
eclipse-rcp-gcj - Eclipse rich client platform (GCJ version)
libgcj6-src - libgcj java sources for use in eclipse

:)

---

### Post by macxek on 2006-05-02
Speaking of Eclipse, I installed it on my machine (running breezy) and it's dead slow! Anything I'd do takes up to a few seconds, including simply typing code... I don't understand what's going on, Eclipse is running lightning fast on Winxp. Anyone experiencing the same issue?

---

### Post by cabezon on 2006-08-10
I got that some client application but its not working right after aptitude install form the breazy repositories. 

Is it meant to be run using the gcj vm ?

Its not working for me, giving me this error on some log:

!MESSAGE Bundle [email]update@plugins/org.eclipse.swt.gtk.linux.x86_64_3.1.1.jar[/email] [23] was not resolved.

---

