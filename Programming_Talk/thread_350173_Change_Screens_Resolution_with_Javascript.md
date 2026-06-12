---
title: "Change Screens Resolution with Javascript???"
date: 2007-01-31
forum: Programming Talk
---

### Post by jae1227 on 2007-01-31
Is it possible to change a screens resolution with javascript. I don't think it is possible with firefox but I think it is possible with Internet Explorer. That means it would only work on Windows :(  . I have read on the internet that it is possible but know tells how to do it. People also mentioned that active X is needed to do this. I dod not plan to use this with a website but on my LAN with testing so I could change a 800x600 screen to 1024x768. If anyone knows please respond.

---

### Post by The Foz on 2007-01-31
I have written **a lot **of JavaScript, and I haven't heard of this.

Basically, doing such a thing would be a breach of security rules, unless the script is signed (for which you need a digital security certificate). Even then, I know of no DOM method, property or browser API that can do this. Basically, if you can't do something through the browser, JavaScript can't do it.

Maybe, as you say, ActiveX allows this.

Alternatively, maybe you are confused, and what you read was about using Java to change the screen resolution. In principle this could be achieved by a Java Applet.

---

### Post by eXisor on 2007-01-31
I've also scripted a little, and I agree with The Foz.
Javascript's highest object level is the window element, which refers to the viewable area inside the browser. There is no scriptable way to change screen resolution unless you know the target system very well, namely, that there is an activex control which has been marked safe for scripting (but shouldn't be) which can change screen resolution.
ActiveX controls can do this, and so can a Java Applet, but the points made by The Foz are still valid. Such an applet or activex control would need to be signed, and as of the moment of accepting the certificate, it is just another application which has full access to the windows api.

If you're only concerned about the intranet, it is a simple matter to code a java-applet or activex control which does this. Sign it, mark it safe for scripting and distribute it to all machines that need the feature. Then call the applet/activex control from javascript.

---

### Post by Tomosaur on 2007-01-31
Perhaps your confusing screen resolution with page resolution - it is quite possible to change the size of objects in a web-page with JavaScript.

---

### Post by jae1227 on 2007-02-01
OK I was thinking would there be a way to just open up the change resolution box and have the user change the resolution instead of forcing the user to change. I just want to change resolution box to pop up instead of telling the user to go to Start>Control Panel>... I relize this would only apply to windows.

---

### Post by Mirrorball on 2007-02-01
I doubt this is true, but what I know for sure is that if it were true, I'd never go back to a site that dared to change my screen resolution. :mad:

---

### Post by Tomosaur on 2007-02-01
It's just not possible with JavaScript I'm afraid - not only for security reasons, but for practicle reasons too. Would **you** want a website to change your resolution? You'd have to change it back manually too, adding further annoyance.

A Java Applet may seem like it would work, but it wouldn't. Java Applets cannot execute system calls.

---

### Post by eXisor on 2007-02-01
Tomosaur:

Sorry to disagree, but signing gives an applet all the rights of an application, namely, full access to the entire java object base and command set, hence the OS api. It's an essential feature of applets on intranets, one I've used quite a few times. 

Basically signed applet = hosted application.

This means you can code an applet to run as a standalone application when it isn't hosted, just code a 'main' as the alternate entry point. And visa versa, of course.

The same signing rules for apply for activex controls.

---

### Post by blackened on 2007-02-01
This can be done. But only on Windows, and not very securely. I used to do it regularly with active desktop, as a replacement for the regular Windows UI, and everything was javascript based.

So first you will need the run protocol handler from [here]("http://www.blackbit.net/frameset.html"). This allows you to launch executables from within the web page by this method:
```
<a href="run:c:/path/to/executable.exe">
```
So after that you will need an executable that can do the switching. Perhaps something like [VidRes]("http://www.download3000.com/download_2977.html"). I've used it before and I know it will work. It's been a while, and getting the commandline switches to play nicely with the run protocol handler can be a bit tricky. But then if it weren't it wouldn't be any fun eh.

For more fun with Active Desktop (and generally using dhtml to interface with the Windows UI) check out [http://www.virtualplastic.net]("http://www.virtualplastic.net"). Some of the info is kinda old on the regular pages, but there's is loads of good stuff in the forums.

One caveat. If anyone knows you have the run protocol handler installed, then they would, theoretically, be able to put it into a regular webpage to launch malicious executables on your machine.

---

### Post by Tomosaur on 2007-02-02
> **eXisor said:**
> Tomosaur:

Sorry to disagree, but signing gives an applet all the rights of an application, namely, full access to the entire java object base and command set, hence the OS api. It's an essential feature of applets on intranets, one I've used quite a few times. 

Basically signed applet = hosted application.

This means you can code an applet to run as a standalone application when it isn't hosted, just code a 'main' as the alternate entry point. And visa versa, of course.

The same signing rules for apply for activex controls.

You can do that, but using RMI in a 'standalone' (ie, not browser based) seems to me to be a more 'sensible' method in this arena.

---

### Post by eXisor on 2007-02-02
Tomosaur:

Just pointing out that it can be done, and what signing actually allows. 

I agree RMI is very useful, but 'sensible' is defined by the requirement. If integration to a cross-platform browser based intranet solution is important, sensible means signed applet.

---

### Post by Tomosaur on 2007-02-02
> **eXisor said:**
> Tomosaur:

Just pointing out that it can be done, and what signing actually allows. 

I agree RMI is very useful, but 'sensible' is defined by the requirement. If integration to a cross-platform browser based intranet solution is important, sensible means signed applet.

Don't get me wrong - I'm not attacking your or anything, just wanted to throw the RMI out there :). I guess it's just a matter of personal preference as to what you allow Java to do. I know I definitely wouldn't feel comfortable with a website changing my resolution at will, regardless of whether it was signed. The fact he was attempting this in JavaScript made me think it was just a personal website rather than anything business-related or whatever, in which case I definitely wouldn't want the site to change my system settings.

---

### Post by eXisor on 2007-02-02
Tomosaur:  :)

No sweat. I agree completely regarding a website changing my resolution. Heck, I'd even object to it on an intranet, especially with the way ms rearranges icons when you downsize.

Seems to me that any system requiring such a thing is broken by design, i.e. badly designed.

---

### Post by Roptaty on 2007-02-02
I really hope this will never be possible with nonsigned javascript. Imagine websites changing the screen resolution upon entering them. "This site is optimized for 1024x768, therefore we are forcing you to use it, even though your LCD might show blurred text." I hate when websites play sounds/music in the background. Its really annoying. Lets hope a javascript implementor never has this idea.. hehe Would be fun annoying other people with it, though... Maybe Firefox programmers add this feature for an Aprils fool joke or something. On entering a website: "exec xrandr -s random_number(num_resolutions)".

---

