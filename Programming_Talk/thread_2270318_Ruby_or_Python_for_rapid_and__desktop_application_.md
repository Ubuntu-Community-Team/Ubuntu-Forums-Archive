---
title: "Ruby or Python for rapid and  desktop application development?"
date: 2015-03-22
forum: Programming Talk
---

### Post by flaymond on 2015-03-22
Hello guys! Back 2 days ago, I'm started a thread about C and asking for opinions, well thanks for the nice feedback you guys give. However, I mentioned to skip C++ and learn other High-Level language that avoid pointers and low-level stuff like Python.  My point is to learn the OOP's deeper since I want to build GUI like text editor and other thing that make people life easier. Unfortunately, Python (The first language I tried and currently) OOP's is so weird and too much 'syntactical sugar' (eg. self. __init__). C++ OO's is far easier to understand, but I want to try something that I can use easier and with some fun instead of long debugging frustation with C/C++. I don't want speed of runtime for my application, just rapid development and less buggy. So here is my question  -1. I found Ruby for Qt and Ruby for Gtk+2.0, I tried make a simple app with them, and it worked (the style is almost same to C++, familiarity is indeed), but I don't know if it good for cross-platform application development since Ruby is not that popular as Python, that probably my target platform don't have ruby installed. Can I 'freeze' them like Python or packaging the app as .deb ?2. Ruby is easy, but most app I found is Ruby on Rails that popular only on the web. I never found any Ruby desktop or mobile application.3. Lack of documentations for Qt Ruby binding, steeper learning curve.If Python OO's not too weird, maybe I would love to use it. :(

---

### Post by Skaperen on 2015-03-22
you can package Python OR Ruby apps easily in .deb OR .rpm OR many other ways ... see Python pip ... or just do tar ... try test packages all ways first and see what you like.

yes, Python seemed weird at first ... so abstract ... so sugary ... **would i get "coder diabetes"?**  i'm doing cloud development (such as [this]("https://s3.amazonaws.com/skaperen/copy_tags_from_spot_request_to_instance.py")) in Python now and have even started recoding shell scripts (once coded for csh/tcsh and recoded for sh/bash) into Python, such as [this one]("https://s3.amazonaws.com/skaperen/screen-bg") and [this one]("https://s3.amazonaws.com/skaperen/screen-in") and [this one]("https://s3.amazonaws.com/skaperen/deciplex.py") ([was]("https://s3.amazonaws.com/skaperen/deciplex.sh") in bash).

---

### Post by ofnuts on 2015-03-23
> **InterProg said:**
> Hello guys! Back 2 days ago, I'm started a thread about C and asking for opinions, well thanks for the nice feedback you guys give. However, I mentioned to skip C++ and learn other High-Level language that avoid pointers and low-level stuff like Python.  My point is to learn the OOP's deeper since I want to build GUI like text editor and other thing that make people life easier. Unfortunately, Python (The first language I tried and currently) OOP's is so weird and too much 'syntactical sugar' (eg. self. __init__). C++ OO's is far easier to understand, but I want to try something that I can use easier and with some fun instead of long debugging frustation with C/C++. I don't want speed of runtime for my application, just rapid development and less buggy. So here is my question  -1. I found Ruby for Qt and Ruby for Gtk+2.0, I tried make a simple app with them, and it worked (the style is almost same to C++, familiarity is indeed), but I don't know if it good for cross-platform application development since Ruby is not that popular as Python, that probably my target platform don't have ruby installed. Can I 'freeze' them like Python or packaging the app as .deb ?2. Ruby is easy, but most app I found is Ruby on Rails that popular only on the web. I never found any Ruby desktop or mobile application.3. Lack of documentations for Qt Ruby binding, steeper learning curve.If Python OO's not too weird, maybe I would love to use it. :(

Aren't you a little bit putting the cart before the horse?  Given the kind of questions I see you asking around here, I don't see you distributing any kind of useful and usable apps before three to four years. So stop worrying about languages and start programming. If you want OO, C-Like, and decently usable for GUI stuff try Java. Even if you switch languages later you will have learned the concepts.

---

### Post by flaymond on 2015-03-23
Thanks for the advice. :)

---

