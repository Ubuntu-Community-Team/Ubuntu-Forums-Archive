---
title: "Netbeans 5.5.1 and Visual Library 2.0"
date: 2007-06-10
forum: Programming Talk
---

### Post by Megacan on 2007-06-10
Hi,

I've been reading about the Visual Library API a viewing tutorials, so I wanted to give it a try but I noted that in the examples they were using Netbeans 6. I have Netbeans 5.5.1 installed and I didn't want to switch to version 6 yet.

So I was looking for some tutorial or something on how to integrate Visual Library in Netbeans I came across this one: [http://graph.netbeans.org/setup.html](http://graph.netbeans.org/setup.html). I followed all the instructions and got these three packages in the end:

   1. org-openide-util.jar - contains openide/util module.
   2. org-netbeans-api-visual.jar - contains the Visual Library.
   3. org-netbeans-modules-visual-examples.jar - contains the Visual Library examples. 

And my question was: where do I install the packages to make them available in netbeans.

This might seem a kind of stupid question but I'm no used to working with Netbeans, or java in general, or linux for that matter.

Any help would be appreciated, tks.

---

### Post by kknd on 2007-06-10
Do you want to use the library in your program?

If yes, put it on your classpath and use it.

---

### Post by Megacan on 2007-06-10
But then I would have to do that every time I needed it. Isn't there a way to make it available for any program without doing that everytime?

---

### Post by nimrod_abing on 2007-06-11
> **Megacan said:**
> But then I would have to do that every time I needed it. Isn't there a way to make it available for any program without doing that everytime?

You can add the jars to your CLASSPATH environment variable. From your terminal, assuming you're using Bash:

```
export CLASSPATH=/path/to/org-openide-util.jar:/path/to/org-netbeans-api-visual.jar:.
```You can also edit your ~/.bashrc file to include that line so that it sets the CLASSPATH everytime you login or use a terminal. Of course, from now on if you need to modify CLASSPATH prior to running your Java app you should say:

```
export CLASSPATH=/additional/library.jar:${CLASSPATH}
```Alternatively, you can also change CLASSPATH to another name, say:

```
export NB_VISUAL_LIBS=/path/to/org-openide-util.jar:/path/to/org-netbeans-api-visual.jar
```Add that to your ~/.bashrc and open up another terminal session for it to take effect. Then every time you want to use the Visual Library, just say:

```
java -cp ${NB_VISUAL_LIBS}:. MyVisualLibProgram
```HTH.

---

### Post by Megacan on 2007-06-11
tks, that will do it.

:p:p

---

