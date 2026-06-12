---
title: "Command to send keystrokes"
date: 2011-09-23
forum: Programming Talk
---

### Post by jeremygwhite on 2011-09-23
I want to write a program that if you do a certain keyboard shortcut while on a web page login screen, the program will fill in your email or username, tab, then password, then enter.

I don't like saving my passwords in browser, but would like the convenience of a quick login.

I can figure out to see if key is pressed and so forth, but the actual typing of the information from the program is what i was curious about. can be in any language, but i know c/c++/c#/java and some python, so it would be nice if it was one i already knew. i'm always willing to learn a new one if it makes my life easier. thanks!

---

### Post by juancarlospaco on 2011-09-23
echo "KeyStrPress a KeyStrRelease a MotionNotify 0 0" | xmacroplay -d 1 0:0 #This is an example
echo "String This is an example" | xmacroplay -d 1 0:0 #This is an example
echo "ButtonPress 1 ButtonRelease 1" | xmacroplay -d 1 0:0 #This is an example

---

