---
title: "Propensity - feedback wanted"
date: 2007-09-02
forum: Programming Talk
---

### Post by earobinson on 2007-09-02
**[UPDATE on page 1]("http://ubuntuforums.org/showthread.php?p=3375556#post3375556")**

I have been using ubuntu for quite some time, and I have ubuntu installed on 20+ computers at one time. I find myself always installing ubuntu on a different computer. One of the things that I always do is install some programs that don&#8217;t come stock with ubuntu like [geany]("http://geany.uvena.de/"), or [miro]("http://www.getmiro.com/"). At first I had a simple shell script that I ran that [aptituded]("http://aptitude.sourceforge.net/") (lol) all the programs I wanted to install. But soon that was not enough because different computers had different uses and installing [miro]("http://www.getmiro.com/") or [gaim guifications ]("http://plugins.guifications.org/trac/wiki/Guifications")on a work computer, or a computer that will be going back to a client is out of the question. Another thing I wanted was to updated the source.list file with new repositories cleanly. And so eventually that shell script involved into a python program.
 I have spent a bit of my summer cleaning up that python program and the result is propensity (I looked for synonyms for [aptitude]("http://aptitude.sourceforge.net/")) and now I figure its almost ready to be released into the public. I have uploaded both a [deb file]("http://www.edwardandrewrobinson.com/propensity-0.1.0.1772.deb") and the [source]("http://www.edwardandrewrobinson.com/propensity.tar.gz") to [my website]("http://www.edwardandrewrobinson.com/"), and would love some feedback.
 Some features that I would like to add before I release it are:[LIST]
[*]I would like propensity to generate a standalone shell script that could be used to standalone install the package
[*]Icon
[*]Splash screen[/LIST]To sum up you can get the [deb file here]("http://www.edwardandrewrobinson.com/propensity-0.1.0.1772.deb"), and the [source here]("http://www.edwardandrewrobinson.com/propensity.tar.gz"). Thanks for any feedback you have.

(This was cut and paste from [my blog]("http://earobinson.wordpress.com/"))

Update 01: [Click here for screenshot]("http://earobinson.files.wordpress.com/2007/09/screenshot-propensity.png")
Update 02: I have been [dugg]("http://digg.com/linux_unix/Propensity_for_Ubuntu_feedback_wanted").

---

### Post by knopper67 on 2007-09-02
I Installed the program, and it looks great. It could use a little bit more polish though. I'll grab the source and see what I can help improve.



-Andrew

---

### Post by earobinson on 2007-09-02
Thanks for the feedback, I know it could use a lot more polish, Its something of a work that just evolved into existence and for personal use I dont really need icons and message boxes and the like, so I spent a good part of the summer adding some in and will try to add more as development progresses.

Thanks for the feedback.

---

### Post by AlexThomson_NZ on 2007-09-02
Voted "good".

Good idea- especially like the idea of exporting to a bash script.  Could use a bit of a pretty-up.

Don't do a splash-screen though!  I don't think it's required here...

---

### Post by earobinson on 2007-09-03
> **AlexThomson_NZ said:**
> Voted "good".

Good idea- especially like the idea of exporting to a bash script.  Could use a bit of a pretty-up.

Don't do a splash-screen though!  I don't think it's required here...
No splash screen, the load time is quite a bit, as for prettying up Im very open to ideas / icon suggestions.  I really want to be able to export to bash scripts for to reasons, 1 well users could acheave the same result without propensity. 2 To help teach users about whats propensity dose so they can learn more about how linux works.  Also any suggestions for programs to use would be great!

---

### Post by earobinson on 2007-09-04
Can anyone answer this question? [http://ubuntuforums.org/showthread.php?t=366720](http://ubuntuforums.org/showthread.php?t=366720)

---

### Post by earobinson on 2007-09-16
It has been about a week since I [released Propensity into the wild]("http://earobinson.wordpress.com/2007/09/02/propensity-feedback-wanted/") for your [feedback]("http://earobinson.wordpress.com/2007/09/02/propensity-feedback-wanted/#respond"), I have gotten a fair bit of feedback and received a lot of help. You will also notice that I jumped from version 0.1.0.1772 to 0.1.2.1906 well version 0.1.1.xxxx was released as a limited demo but I have pushed forward to release version 0.1.2.190. New to this version we have:
 [LIST]
[*]The ability to add your own programs to propensity (you can import them or manually add them)
[*]A Propensity Icon
[*]Cleaned up and much prettier terminal
[*]And many other little features.[/LIST] As always feedback is wanted and bugs can be emailed to earobinson+propensity@gmail.com.
 
[Download Propensity Here]("http://www.edwardandrewrobinson.com-a.googlepages.com/propensity-0.1.2.1906.deb")
[Download Propensity Source Here]("http://www.edwardandrewrobinson.com-a.googlepages.com/propensity.tar.gz")


[Ubuntu forums propensity post can be found here]("http://ubuntuforums.org/showthread.php?t=540787&highlight=propensity")

 [Screenshots]("http://picasaweb.google.com/earobinson/Propensity") below
   [[IMG]http://lh4.google.com/earobinson/RuiSR5xINmI/AAAAAAAAAVE/Mxh3StbyV9g/s400/PropensityIcon.jpg[/IMG]]("http://picasaweb.google.com/earobinson/Propensity/photo#5109494613514139234")   From [Propensity]("http://picasaweb.google.com/earobinson/Propensity")   

[[IMG]http://lh6.google.com/earobinson/RuiSMZxINdI/AAAAAAAAATY/bcPpEcFQCh0/s400/Screenshot-Changes%20Applied-1.jpg[/IMG]]("http://picasaweb.google.com/earobinson/Propensity/photo#5109494519024858578")   From [Propensity]("http://picasaweb.google.com/earobinson/Propensity")     

[[IMG]http://lh3.google.com/earobinson/RuiSNpxINfI/AAAAAAAAATw/8fgQoACqtGg/s400/Screenshot-Propensity-1.jpg[/IMG]]("http://picasaweb.google.com/earobinson/Propensity/photo#5109494540499695090")    From [Propensity]("http://picasaweb.google.com/earobinson/Propensity")


[This blog post can be found here]("http://earobinson.wordpress.com/2007/09/17/propensity-v0121906-now-with-an-icon/")
[http://earobinson.wordpress.com/2007/09/17/propensity-v0121906-now-with-an-icon/](http://earobinson.wordpress.com/2007/09/17/propensity-v0121906-now-with-an-icon/)

---

### Post by earobinson on 2007-09-17
Having huge problems with my blog right now, if a links broken, let me know.

---

### Post by Wybiral on 2007-09-17
Sounds cool, but it looks an awful lot like EasyUbuntu or Automatix. Are you going to add any features that set it apart?

---

### Post by UbuWu on 2007-09-17
In gutsy you could install these programs and add the repositories using a simple html file using [apturl]("http://packages.ubuntu.com/gutsy/admin/apturl").

Try it here if you are on gutsy: [install ttb]("apt:ttb")

---

