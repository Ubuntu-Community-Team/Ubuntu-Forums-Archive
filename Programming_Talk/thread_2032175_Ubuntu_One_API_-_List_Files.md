---
title: "Ubuntu One API - List Files"
date: 2012-07-23
forum: Programming Talk
---

### Post by snowz on 2012-07-23
I've wanted to create a JavaScript web app that requires you to put in your **Ubuntu** One username and password and then it would list all your files that are in your Ubuntu One storage. The files would be filtered to show only the **.mp3** ones.

I've been looking at this:

[http://developer.ubuntu.com/resources/app-developer-cookbook/ubuntu-one/adding-ubuntu-one-files-support-to-your-app/](http://developer.ubuntu.com/resources/app-developer-cookbook/ubuntu-one/adding-ubuntu-one-files-support-to-your-app/)

but its all in Python.

Basically it looks like I only need the login script and the list files script, but in JavaScript instead of Python.

I'm worried because there are so many imported lib's.

Any suggestions? :-k

---

### Post by snowz on 2012-07-24
Have to do this, bump [-o<

---

### Post by mevun on 2012-07-25
You will need to re-implement the credential checking library with Oauth functionality in javascript.  I think the other imports are for functionality already present in javascript.  Like if you know how to do AJAX, then you don't need anything like "urllib".  Obviously javascript already parses json format so you don't need the equivalent python module for parsing that.

---

