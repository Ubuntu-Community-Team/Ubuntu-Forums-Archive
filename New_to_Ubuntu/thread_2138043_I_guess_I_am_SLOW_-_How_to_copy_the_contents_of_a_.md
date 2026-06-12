---
title: "I guess I am SLOW - How to copy the contents of a hidden directory to a visible one"
date: 2013-04-22
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2013-04-22
OK - let me start off by saying I must be brain dead.
I'm trying to copy the contents of ~/.todo.actions.d to /home/john/SpiderOak/todo.actions.d-hidden-addons
(Ideally the new directory would simply not have a . in front of it's name...)

This doesn't do what I want:

```

cp -r ~/.todo.actions.d ~/SpiderOak/todo.actions.d-hidden-addons

```

with this code I get a directory called .todo.actions.d inside one called todo.actions.d-hidden-addons.


[IMG]https://dl.dropboxusercontent.com/u/23115609/addons.png[/IMG]

What I want is for any new *files and only the files * in .todo.actions.d to be copied to the directory called todo.actions.d-hidden-addons

I've done this in the past, but for the life of me can not remember how.
Have mercy on a moron ;)

---

### Post by themusicalduck on 2013-04-22
Try this instead -

```
cp -r ~/.todo.actions.d/* ~/SpiderOak/todo.actions.d-hidden-addons
```

---

### Post by steeldriver on 2013-04-22
Try

```
cp -r ~/.todo.actions.d[COLOR=#0000ff]**/***[/COLOR] ~/SpiderOak/todo.actions.d-hidden-addons
```

[Actually I'd probably do

```
cp -r ~/.todo.actions.d[COLOR=#0000ff]**/***[/COLOR] ~/SpiderOak/todo.actions.d-hidden-addons[COLOR=#0000ff]**/**[/COLOR]
```

where the trailing slash on the target asserts that it is a directory - not compulsory in this case but it prevents accidents if the directory doesn't exist]

---

### Post by slickymaster on 2013-04-22
Is this what you're looking for:
```
cp t1/. t2/ -R
```
The dot at the end tells it to copy the contents of the current directory, not the directory itself. This method also includes hidden files and folders.

---

### Post by GrouchyGaijin on 2013-04-22
Thanks Guys!

---

