---
title: "JavaFX preview not available for Linux"
date: 2008-07-31
forum: Programming Talk
---

### Post by xlinuks on 2008-07-31
Hi,
As you can see at
[http://java.sun.com/javafx/downloads/](http://java.sun.com/javafx/downloads/)
it's only available for windows and apple,
does anyone know when the Linux release gets available if at all?
Sun didn't even release for (their) solaris OS a preview..

---

### Post by kavon89 on 2008-07-31
Java's primary goal is being cross-platform. I can guarantee that it will be available for Linux & Solaris when it's ready.

EDIT:
    * July 31: Launch JavaFX preview;
    * Fall: JavaFX 1.0 launches;
    * Spring 2009: JavaFX Mobile;
    * Later in 2009: JavaFX for TV.

I would wait on fall's full release. :D

---

### Post by kknd on 2008-07-31
I tested an old version months ago on Linux. There must be a version somewhere!

---

### Post by xlinuks on 2008-08-01
> **kknd said:**
> I tested an old version months ago on Linux. There must be a version somewhere!

The preview has only two options: MacOS and windows.
I wish they at least put a note right there on the download page about when they plan to publish a preview release for Linux as well, if ever so that Java Linux developers don't look for questions they knew would arise.

---

### Post by xlinuks on 2008-08-01
Well I found something interesting:
> Frank,

The current release of JavaFX SDK preview release does not support Linux. However there are plans to support Linux in the future release. By support what I mean is the ability to play Media.

- Sandeep 
at:
[http://forums.sun.com/thread.jspa?threadID=5319279](http://forums.sun.com/thread.jspa?threadID=5319279)
so there's some uncertainty about the Linux release (the one with media support).

---

### Post by tinny on 2008-08-01
These types of previews never seem to make it to Linux.

Remember we are only ~2% of the Desktop market. :(

---

### Post by tinny on 2008-12-05
Still no linux version, arrrrrrrrr!!!

[http://javafx.com/downloads/all.jsp](http://javafx.com/downloads/all.jsp)

Well, at least the demo applications run on my Ubuntu machine.

[http://javafx.com/samples/](http://javafx.com/samples/)

Has any body found a way to get the JavaFX SDK on Ubuntu?

---

### Post by jespdj on 2008-12-05
Have a look at this blog post: [Using JavaFX 1.0 On Linux](http://www.weiqigao.com/blog/2008/12/04/using_javafx_1_0_on_linux.html). It seems that you can install it on Linux using the Mac version, but I don't know how well it will work. I haven't tried it myself yet.

But Sun promises that there are going to be versions for Linux and Solaris: [A Word on Linux and Solaris Support](http://blogs.sun.com/javafx/entry/a_word_on_linux_and)

We'll just have to be patient...

---

### Post by cl333r on 2008-12-05
> **tinny said:**
> Still no linux version, arrrrrrrrr!!!
[http://javafx.com/downloads/all.jsp](http://javafx.com/downloads/all.jsp)
Well, at least the demo applications run on my Ubuntu machine.
[http://javafx.com/samples/](http://javafx.com/samples/)
Has any body found a way to get the JavaFX SDK on Ubuntu?

It's indeed disappointing, it's been under development for longer than a year and Sun who is itself a Unix owner can't provide a JDK for it's own OS in time.
On the other hand I'm no longer eager to try out JavaFX, at Java One we've been told it's:
1. Gonna be open source. At least the codecs are not.
2. Cross-platform... (not for developers at least..)
3. Built-in 3D. Support for 3D is installed separately, not as part of JavaFX.
4. High definition audio and video. Also fake.
5. Fast applet startup. Not true for Linux, only partially for windows since it still have a slower startup than a flash plugin.
6. Who knows what else..

In other words that was a marketing stunt, just as pretty much any other company does to keep users loyal.

They also released Java 6 update 11, what's the point since update 10 was specifically targeted for JavaFX?

---

### Post by tinny on 2008-12-05
> **jespdj said:**
> Have a look at this blog post: [Using JavaFX 1.0 On Linux](http://www.weiqigao.com/blog/2008/12/04/using_javafx_1_0_on_linux.html). It seems that you can install it on Linux using the Mac version, but I don't know how well it will work. I haven't tried it myself yet.


Yep that method works well :-)

> **jespdj said:**
> 
But Sun promises that there are going to be versions for Linux and Solaris: [A Word on Linux and Solaris Support](http://blogs.sun.com/javafx/entry/a_word_on_linux_and)

We'll just have to be patient...

No doubt they will, but COME ON Sun!!!

I was able to visit the openjfx compiler Hudson continuous integration  site and download the release candidate build and get it too work, it was so easy just add the ~/bin folder to $PATH.

[http://openjfx.java.sun.com/hudson/job/openjfx-compiler-release-candidate/](http://openjfx.java.sun.com/hudson/job/openjfx-compiler-release-candidate/)

This wasn't rocket science, why couldnt Sun distribute a bash script with this build? I might spend 15min doing it myself.

This is not confidence inspiring... why cant they do this basic stuff after over 1 year of development?

Well I guess it still has big bugs........... :-(

> **cl333r said:**
> 
1. Gonna be open source. At least the codecs are not.


I can live with that, only because my customers wont care.

> **cl333r said:**
> 
2. Cross-platform... (not for developers at least..)


Yep, a nice ball drop.

> **cl333r said:**
> 
3. Built-in 3D. Support for 3D is installed separately, not as part of JavaFX.


Really??? Please explain, link? (Im currently investigating JavaFX for a project)

> **cl333r said:**
> 
4. High definition audio and video. Also fake.


???

> **cl333r said:**
> 
5. Fast applet startup. Not true for Linux, only partially for windows since it still have a slower startup than a flash plugin.


The linux startup time sucks, but none of my customers use linux so I may be able to live with this.

> **cl333r said:**
> 
6. Who knows what else..


Yeah thats the thing, they are going to have to fight there poor client side Java history.

---

### Post by cl333r on 2008-12-05
Well.. "High definition audio and video" means better/excellent quality of audio and video, google has lots of stuff about this issue. Currently according to Sun, JavaFX supports "standard" audio and video.
Here's something I found about HD audio:
[http://www.hardwaresecrets.com/article/265](http://www.hardwaresecrets.com/article/265)
As usually, Google rules :)

---

### Post by Shin_Gouki2501 on 2008-12-05
Well i guess its a much more open approach then adobe flash or ms silverlight. Lets see how good it turns out. I'd love to see that SVG gets a boost through that.

---

### Post by Unterseeboot_234 on 2008-12-05
Whew! I just got my 8.10 install about back up to my 7.10 capabilities. In Gutsy I had NetBeans6.0 working the JavaFX plug-in. Granted, on Linux there are some features missing, but at least I could get code hi-lighting and indentation. I thought I could just grab NetBeans6.5 and get the same plug-in from NetBeans update. No, that is blocked to Linux. I looked for NetBeans6.0 and that is no longer available. Luckily, I had one backup with NetBeans with the plug-in.

You CAN use the command-line to compile and preview JavaFX. You won't have video and few other features. There is currently only one computer book for JavaFX

**[Apress JavaFX(tm) Platform]("http://www.apress.com/book/view/9781430218753")**

the author, James L. Weaver offers a valuable link in his blog for Ubuntu instructions to unArchive the Mac version of JavaFX SDK. Jim's book is insightful because his code works on the Linux version of SKDjavafx. FX is in such flux that trying different code, created from different timeframes, usually results in the code not working. But, like I say, Weaver used the core libraries and the enhancements to JavaFX are extensions of the core.

**[the blog]("http://learnjavafx.typepad.com/")**

**[the linux install link for JavaFX]("http://www.weiqigao.com/blog/2008/12/04/using_javafx_1_0_on_linux.html")**

And, I had Inkscape 0.47 built, but I didn't back that up. I migrated to Ubuntu 8.10 to have 0.47. The SVC branch of Inkscape has .svg export for JavaFX.

JavaFX has the real potential to be everything SilverLining, everything Flex and maybe everything Flash. And that would be good, Flash 10 doesn't work on my machine and Flash 10 is required on Yahoo Video.

---

### Post by jamesstansell on 2008-12-05
> **cl333r said:**
> 
They also released Java 6 update 11, what's the point since update 10 was specifically targeted for JavaFX?

Java 6u10 did include some javafx bits, but its main focus was the "consumer jre".

Java 6u11 fixed a few bugs, but primarily addressed security issues, where 6u10 didn't address any.

Java 6u12 is targeted for February 2009 and supposedly will include a 64-bit browser plugin and java webstart.  Preview releases are expected to start next week.

---

### Post by Shin_Gouki2501 on 2008-12-06
> **Unterseeboot_234 said:**
> Whew! I just got my 8.10 install about back up to my 7.10 capabilities. In Gutsy I had NetBeans6.0 working the JavaFX plug-in. Granted, on Linux there are some features missing, but at least I could get code hi-lighting and indentation. I thought I could just grab NetBeans6.5 and get the same plug-in from NetBeans update. No, that is blocked to Linux. I looked for NetBeans6.0 and that is no longer available. Luckily, I had one backup with NetBeans with the plug-in.

You CAN use the command-line to compile and preview JavaFX. You won't have video and few other features. There is currently only one computer book for JavaFX

**[Apress JavaFX(tm) Platform]("http://www.apress.com/book/view/9781430218753")**

the author, James L. Weaver offers a valuable link in his blog for Ubuntu instructions to unArchive the Mac version of JavaFX SDK. Jim's book is insightful because his code works on the Linux version of SKDjavafx. FX is in such flux that trying different code, created from different timeframes, usually results in the code not working. But, like I say, Weaver used the core libraries and the enhancements to JavaFX are extensions of the core.

**[the blog]("http://learnjavafx.typepad.com/")**

**[the linux install link for JavaFX]("http://www.weiqigao.com/blog/2008/12/04/using_javafx_1_0_on_linux.html")**

And, I had Inkscape 0.47 built, but I didn't back that up. I migrated to Ubuntu 8.10 to have 0.47. The SVC branch of Inkscape has .svg export for JavaFX.

JavaFX has the real potential to be everything SilverLining, everything Flex and maybe everything Flash. And that would be good, Flash 10 doesn't work on my machine and Flash 10 is required on Yahoo Video.


you mean like this?

[inkscape-and-javafx-working-together](http://silveiraneto.net/2008/11/21/inkscape-and-javafx-working-together/)

---

### Post by Unterseeboot_234 on 2008-12-06
Yes, Silveira wrote the C++ plug-in for Inkscape .46-devel that will "Save-As" JavaFX -- outputing ...

 ```
 public class faceplate extends CustomNode {

    ... code omitted ... to show a graphic of Inkscape as Object

    /** path rect2696 */
    private function rect2696() : Path {
        Path {
            id: "rect2696"
            opacity: 1.00000000
            fill: Color.rgb(0xb3, 0xb3, 0xb3, 0.99609375)
            stroke: Color.rgb(0x00, 0x00, 0x00, 0.99609375)
            strokeWidth: 0.00000000
            strokeLineCap: StrokeLineCap.BUTT
            strokeLineJoin: StrokeLineJoin.MITER
            strokeMiterLimit: 4.00000000
            elements: [
                MoveTo {
                    x: 57.28571701
                    y: -812.85714722
                },
                LineTo {
                    x: 414.14286423
                    y: -812.85714722
```

as a text file. Now, what I have not tried yet is the JavaFX method he describes -- public class faceplate extends **CustomNode**

(faceplate was the name of my Inkscape drawing document) and the plug-in makes a class.

Linux JavaFX doesn't have CustomNode yet. Mac and WIN do have it. CustomNode subclasses CompositeNode, which is one level lower. In a sense, we have for Linux the JComponent, and Mac has the JPanel.

---

### Post by Unterseeboot_234 on 2008-12-06
my bad, double posted during the timeout

---

