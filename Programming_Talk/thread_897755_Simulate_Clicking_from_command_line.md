---
title: "Simulate Clicking from command line"
date: 2008-08-22
forum: Programming Talk
---

### Post by themostunoriginalname on 2008-08-22
I'm currently running some scripts involving opening up firefox, accessing a website, and then closing firefox. Currently, I'm doing so, but doing killall firefox, but after about a few kills, firefox starts displaying error messages on the command line and things start not working right. I kind of want to know of a want to simulate clicking on the X on the top right. Is there any way I can do this through BASH or some other programming language?

---

### Post by MaxIBoy on 2008-08-22
It would probably be easier to simulate alt-f4, but then again, what do I know.

---

### Post by mssever on 2008-08-22
What you need to figure out is which signal the window manager send when yo uclick the close box. Then use the kill command to send that signal. I don't know off-hand what the signal is.

EDIT: Sending SIGTERM shouldn't cause any harm. You aren't sending SIGKILL, are you?

---

### Post by themostunoriginalname on 2008-08-22
is there a command for killing using SIGTERM because the great thing about killall is that I don't need the pid

---

### Post by themostunoriginalname on 2008-08-22
actually... killall using SIGTERM, so it's still giving me an error message. Here's the error message: 

$ firefox
Error sanitizing history: [Exception... "Component returned failure code: 0x80570016 (NS_ERROR_XPC_GS_RETURNED_FAILURE) [nsIJSCID.getService]"  nsresult: "0x80570016 (NS_ERROR_XPC_GS_RETURNED_FAILURE)"  location: "JS frame :: chrome://browser/content/sanitize.js :: anonymous :: line 115"  data: no]

---

### Post by mssever on 2008-08-22
> **themostunoriginalname said:**
> actually... killall using SIGTERM, so it's still giving me an error message. Here's the error message: 

$ firefox
Error sanitizing history: [Exception... "Component returned failure code: 0x80570016 (NS_ERROR_XPC_GS_RETURNED_FAILURE) [nsIJSCID.getService]"  nsresult: "0x80570016 (NS_ERROR_XPC_GS_RETURNED_FAILURE)"  location: "JS frame :: chrome://browser/content/sanitize.js :: anonymous :: line 115"  data: no]
It looks to me like you've got a buggy extension. SIGTERM is a legitimate way to exit any program, and if your extension can't handle it, that's a bug.

---

### Post by themostunoriginalname on 2008-08-22
no extensions.

---

### Post by dtmilano on 2008-08-22
Use wmctrl.
For example,

```
$ wmctrl -c 'Welcome to Ubuntu 8.04 LTS!'
```

closes gracefully the window that matches the title. There are much more options, check man.

---

### Post by mssever on 2008-08-22
> **themostunoriginalname said:**
> no extensions.
Then I don't know what's going wrong. (You could try SIGHUP and see what happens, or Google up the signal that the close button sends.)

It also wouldn't hurt to try with a clean profile.

---

### Post by themostunoriginalname on 2008-08-22
well. that is how I'm fixing, but after a few kills, it shows back up again. The only I'm doing is disabling the crash handler, cleaning up my profile on closure, and start on a blank page. I'm going to make a guess that it's the disabling crash handler. Actually, is there a way to default to just start a new session?

---

### Post by nanotube on 2008-08-22
this thread may be handy for you. i posted a bit of code there that can generate any keystrokes.
[http://ubuntuforums.org/showthread.php?t=858766](http://ubuntuforums.org/showthread.php?t=858766)

you can modify it to generate alt-f4, that would probably do what you need.

that said, generating keystrokes is probably not the most elegant solution, using wmctrl as posted by dtmilano seems much easier. :)

still, i don't know why you are having problems just sending sigterm... that should work and make firefox exit cleanly, but maybe they have a bug...

---

### Post by tinny on 2008-08-22
> **themostunoriginalname said:**
> I'm currently running some scripts involving opening up firefox, accessing a website, and then closing firefox. Currently, I'm doing so, but doing killall firefox, but after about a few kills, firefox starts displaying error messages on the command line and things start not working right. I kind of want to know of a want to simulate clicking on the X on the top right. Is there any way I can do this through BASH or some other programming language?

Are you wanting to test this website? You are wanting to run an automated script that interacts with a web page, right?

You may want to have a look at [Selenium]("http://en.wikipedia.org/wiki/Selenium_(software)").

Maybe have a look at [Selenium IDE]("https://addons.mozilla.org/en-US/firefox/addon/2079"), its great. It allows you to record interactions with a web site as a script (various languages supported) and then you can play this scrip back.

---

### Post by ghostdog74 on 2008-08-22
> **themostunoriginalname said:**
> I'm currently running some scripts involving opening up firefox, accessing a website, and then closing firefox. 
if this is just what you are going to do, use an automated tool like wget or curl to grab the website. Depending on what you want to find(access) on the website, you can parse the result of the grab to a parser to get what you want.

---

