---
title: "scriptable applications"
date: 2009-12-03
forum: Programming Talk
---

### Post by iRounak on 2009-12-03
In Mac OS, there is an applescript dictionary which gives a clear picture of how scriptable an application is. 
Can someone tell me which applications support scripting extensively and which scripting language should be learned to script them? 
These are the kinds of applications I need to script:
1. music player 
2. mail client
3. browser
4. scripts for managing files and folders i.e. processing them, compressing them and moving them all in one script

---

### Post by fatality_uk on 2009-12-03
What are you tryingt to script? The last item, 4 can easily be done in a bash script then you point a CRON entry to automate that process from the script. Others, if you let us know more what you need, easier to tell if it's doable

---

### Post by iRounak on 2009-12-03
**Re: scriptable applications**
         > What are you tryingt to script? > 1. music player [http://dougscripts.com/](http://dougscripts.com/)
See the link above. Practically, everything is possible in iTunes with applescript. There are atleast 15-20 scripts that I use personally like
1. a script that collects all my songs which have no lyrics and puts them in a separate "No Lyrics" playlist) 
1. fetching lyrics for the selected or now playing song
2. fetching artwork for the selected or now playing song
3. mass adding of start and stop time so as to skip intro and concluding parts of all videos in a podcast
4. checking for updates of all podcasts and displaying them in a neat dialog box and if an item is selected it will be downloaded
5. opening the selected video in an iTunes playlist in vlc at the press of a hotkey in case it does not play properly in iTunes
6. Super Remove Dead Tracks script which removes all tracks from the entire library whose file locations have become non-existent due to moving or deleting
7. Encoding of aac to mp3


> 2. mail client & 3.browserMail (Apple's Mail client) is also hightly scriptable. I use scripts like
1. When a notification email of a new reply in a forum thread is received, it contains a link to see the reply. I have a script which checks for the subject of the email and if it finds that it is one of the forums that i have subscribed to, it opens the first link in my default browser.
2. Often, we register at any website and the first email that we receive is the email id verification email which requires us to open a link to activate our registration. I have  a scripts that displays all the links in the newest email and allows me to open any of them in my browser.
3. All my new emails are displayed in large type as soon as they arrive. But I guess, linux does not have large type. ([http://www.coldpizzasoftware.com/largetype/](http://www.coldpizzasoftware.com/largetype/))
4. I have a script that takes selected text in my browser as the message of the email, inserts the current URL in the message, and takes the title of the window as the subject which I am allowed to edit. [http://dl.getdropbox.com/u/872430/dialog%20box.tiff]("http://dl.getdropbox.com/u/872430/dialog%20box.tiff")
After this dialog box another dialog box comes up which shows me a list of friends/groups to which I have to send the email to.
5. A script similar to one described in 4 is used in many other applications as well to send selected text in those applications as email. In both the scripts described in 4 and 5 the user does not have to leave the current application he is working in. The email is sent in the background.

Let me know if all this is scriptable. PLEASE DO NOT SUGGEST ME AN APPLICATION WHICH DOES ALL THIS BY ITSELF WITHOUT SCRIPTS. SCRIPTS OFFER FLEXIBILITY AND CUSTOMIZATION WHEN NEEDS CHANGE WITH TIME.

---

### Post by falconindy on 2009-12-03
> **iRounak said:**
> PLEASE DO NOT SUGGEST ME AN APPLICATION WHICH DOES ALL THIS BY ITSELF WITHOUT SCRIPTS. SCRIPTS OFFER FLEXIBILITY AND CUSTOMIZATION WHEN NEEDS CHANGE WITH TIME.
[This](http://en.wikipedia.org/wiki/Reinventing_the_wheel) will get you started.

---

### Post by iRounak on 2009-12-04
What exactly do you want to say? Maybe you are not a scripter. Hence, you do not understand the advantage of using a script over a feature provided by an application.** This will get you started**:

The most basic advantage of using a script instead of an application is to be able to do several different tasks without leaving your current application. 
example: let us say I am typing you a reply now and I want to listen to a song or I want to check my mail. All I have to do is press a hotkey. I continue to be where I am(i.e. typing a reply to you) and the song starts playing and my email client checks of a new mail. If a new mail arrives, it is displayed in "large type" (which means the message floats on top of my current application and exits when any key is pressed). If I want to pause the song I am listening to, or fetch album artwork, lyrics, I don't have to activate my music player. I can continue typing you a reply and perform those activities with hotkeys.

---

### Post by iRounak on 2009-12-04
It cannot be done in Ubuntu?

---

### Post by grief -l on 2009-12-04
Can't answer your question but Ubuntu comes with Python so it must be possible. Maybe you're just in the wrong forum? Try asking [here]("http://ubuntuforums.org/forumdisplay.php?f=39").
 
Gabe

---

### Post by iRounak on 2009-12-04
[http://ubuntuforums.org/showthread.php?p=8442171](http://ubuntuforums.org/showthread.php?p=8442171)

---

### Post by iRounak on 2009-12-04
thanks. [http://ubuntuforums.org/showthread.php?p=8442234](http://ubuntuforums.org/showthread.php?p=8442234)

---

### Post by conehead77 on 2009-12-04
make a google search for "ubuntu email command line" or similar. for almost every program there are also several command line tools. for mail for example there is nail or mutt that should be easily scriptable. also take a look at sendmail.
for scripting firefox the way you described it i think you need to make a plugin. but there are other browsers, you may like uzbl. 
file management should be similar to the mac on command line.
glue all those command line tools together with bash or python.
also if safari is scriptable on a mac it should make little difference if you run safari on ubuntu. i don't know anything about macs and mac applications so i could be wrong...

---

### Post by iRounak on 2009-12-04
> **conehead77 said:**
> make a google search for "ubuntu email command line" or similar. for almost every program there are also several command line tools. for mail for example there is nail or mutt that should be easily scriptable. also take a look at sendmail.
for scripting firefox the way you described it i think you need to make a plugin. but there are other browsers, you may like uzbl. 
file management should be similar to the mac on command line.
glue all those command line tools together with bash or python.
I know about command line tools. I have used tools like ffmpeg, Imagemagick etc. in Mac OS since it is also UNIX based. 
From what I understand, you mean, for every application, I must find out the manner in which it is scriptable. Or I must use applications which are scriptable in a particular language. 
I tried to learn python but I am extremely confused about how it will be useful to me. I posted a similar query in the python mailing list it was not answered satisfactorily. If someone can show me python examples of any of the above things I have mentioned, I could start learning python again. 
> also if safari is scriptable on a mac it should make little difference if you run safari on ubuntu. i don't know anything about macs and mac applications so i could be wrong...
Yes, you are wrong here. Developers in Mac make applications scriptable for applescript. And ofcourse, other UNIX based operating system do not understand applescript.

---

### Post by grief -l on 2009-12-05
> I tried to learn python but /snip
 
I only mentioned .py because I know because I know about it. Looking around I see you can use many others. Look [here]("http://wiki.debian.org/FrontPage") under DEVELOPERS and there's probably one you know already.
 
Gabe

---

### Post by conehead77 on 2009-12-05
here is a little example for retrieving an email from an IMAP server:

```

from imaplib import *

server = IMAP4("your.mail.server")
server.login("accountname", "passsword")
mboxes = server.list()[1]
r = server.select("INBOX")   # name of IMAP folder
r, data = server.fetch('1', '(UID BODY[TEXT])')   #gets UID and message body of the first message in folder
print data  # print message body

```

save as pymail.py and run "python pymail.py" to execute.

you don't script a special application though and it's a little bit more low level, don't know.

---

### Post by cariboo on 2009-12-05
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by cabalas on 2009-12-05
If you are looking at writing scripts which interact with your applications it might be worth looking into [D-Bus]("http://www.freedesktop.org/wiki/Software/dbus"), what (if any) functionality your preferred apps expose via D-Bus and what language bindings for D-Bus exist - my personal preference being [python]("http://python.org/").  

If you are feeling adventurous here's a [link]("http://www.kryogenix.org/days/2009/02/08/linglish-or-some-thoughts-on-a-scripting-language-for-the-linux-desktop") to an attempt to bring applescript type of syntax/functionality to the linux desktop - Though I don't know how much more it has been developed since it was announced.

---

### Post by openuniverse on 2009-12-05
.

---

### Post by iRounak on 2009-12-05
Thank you everyone for the replies. It will take some time to explore your suggestions. 
> If you are feeling adventurous here's a link to an attempt to bring applescript type of syntax/functionality to the linux desktop - Though I don't know how much more it has been developed since it was announced.
Did you forget to post the link?

---

### Post by cabalas on 2009-12-05
> **iRounak said:**
> Thank you everyone for the replies. It will take some time to explore your suggestions. 

Did you forget to post the link?

Whoops I did, added the link to the original post but here it is again [http://www.kryogenix.org/days/2009/02/08/linglish-or-some-thoughts-on-a-scripting-language-for-the-linux-desktop](http://www.kryogenix.org/days/2009/02/08/linglish-or-some-thoughts-on-a-scripting-language-for-the-linux-desktop)

---

### Post by iRounak on 2009-12-05
> **cabalas said:**
> Whoops I did, added the link to the original post but here it is again [http://www.kryogenix.org/days/2009/02/08/linglish-or-some-thoughts-on-a-scripting-language-for-the-linux-desktop](http://www.kryogenix.org/days/2009/02/08/linglish-or-some-thoughts-on-a-scripting-language-for-the-linux-desktop)
Its cool!!! However, more than english-like language what is important is that applications become scriptable in one single language like applescript is for almost all mac applications.

---

### Post by phrostbyte on 2009-12-05
Another you might look into is DBus, it allows apps to expose a interface which is scriptable from many languages.

[http://www.freedesktop.org/wiki/Software/dbus](http://www.freedesktop.org/wiki/Software/dbus)

Many Gnome/KDE apps have a DBus interface.

---

### Post by iRounak on 2009-12-06
thanks. yes, cabalas did point to D-bus in this thread.

---

### Post by Mr. Picklesworth on 2009-12-14
And on the topic of Dbus, you'll want to use D-Feet to quickly find the different tools available.

---

