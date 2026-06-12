---
title: "Full screen web browser, controlled from the command line"
date: 2009-01-12
forum: Programming Talk
---

### Post by un_dave on 2009-01-12
In the quest to create a simple information display screen for my lounge, (see the full story here: [http://ubuntuforums.org/showthread.php?p=6543085](http://ubuntuforums.org/showthread.php?p=6543085) )
I've decided to try create something myself, and I've come up with a system that will hopefully work something like this:

1. I create a list of simple bash 'page' scripts, which, when executed, retrieves stats, then uses them to create a simple html page. 
2. The master script, which runs each of the page scripts, then displays the resulting html file full screen, with a yet to be determined web browser. The script then waits for a predefined delay, then repeats the process with the next script.  

So far, I have a list of page scripts, which create html files, and a simple master script, which can execute each of the page scripts. However, the point that I'm stuck on is how to open the pages in the web browser from the command line, and get them to open in the current window. 

I'm assuming I'll be able to get the web browser to default to full screen, and I'm sure I could probably just kill the browser process, and re-open pointing to a new url, but i'm hoping for something which just allows me to open the url in the current browser window. 

Firefox is the only browser currently installed, but I don't mind installing any other browser as necessary. 

Thanks in advance! 

Dave.

---

### Post by Reiger on 2009-01-12
Opera has a -remote switch which enables remote commands.

It also has various openURL() functions which (reading the output of opera -v) should allow you to select the 'target' (window/tab/background-tab) to do the stuff in.

---

### Post by un_dave on 2009-01-12
Cool, looking here, it looks like you might be onto something.
[http://www.opera.com/docs/switches/#remote](http://www.opera.com/docs/switches/#remote)

so i could call 
opera -remote "openURL(html/001.html)"

and if opera isn't open, it will start it and open that file, and if it is, it will open the file supplied in the current window. 

I think that should work! I'll test it out later today, and see how I go. 

Thanks!

---

### Post by HyperHacker on 2009-01-14
If you're generating these pages, you could use Javascript or a meta refresh to reload the page or move to another, and perhaps PHP or Python to generate them. (If you don't want to set up a web server, it's pretty easy to write a simple one in Python that will just serve one or two pages.)

---

### Post by skullmunky on 2009-01-15
Another interesting option is Konqueror, which you can control using the DBUS message protocol.  I don't know too much about it, but it could work.

find a running konqueror process:
```

qdbus | grep konqueror

```

tell it to open a URL:
```

qdbus org.kde.konqueror-10810 /konqueror/MainWindow_1 org.kde.Konqueror.MainWindow.openUrl "www.google.com" False

```

see the other things you can do with it:
```

qdbus org.kde.konqueror-10810 /konqueror/MainWindow_1 

```

that -10810 will unfortunately be different for every process; maybe there's a way to send it using wildcards.

---

