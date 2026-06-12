---
title: "Develop for GUI in QT?"
date: 2012-04-14
forum: Programming Talk
---

### Post by kio_http on 2012-04-14
After having some of my fears with the future of development on Windows (Windows 8 in particular), I seriously want to get into developing on Linux with QT.

My needs, I want to get into GUI mainly and connect to databases (probably mysql). The applications will be optimally for a KDE environment. It should also be easy enough to learn.

I currently have zero C++ experience. I've always been using C# and vb.net with MS .NET framework before. 

I've had a look at nokia's qt site and I feel a bit lost. I am looking for a very elaborate step by step tutorial for a complete beginner in both C++ and QT. I want to use QML (qtquick).

I would prefer a video based tutorial. The tutorials that Microsoft are really well made (and include video tutorials. developer.ubuntu.com looks flashy but has no information on QT and QML.

---

### Post by r-senior on 2012-04-14
There are some useful tutorials here:

[http://zetcode.com/](http://zetcode.com/)

No video, but good all the same. There's a C++ and Python tutorial for Qt.

If you have C#/.NET experience, have you considered Mono?

[https://en.wikipedia.org/wiki/Mono_%28software%29](https://en.wikipedia.org/wiki/Mono_%28software%29)

---

### Post by kio_http on 2012-04-14
> **r-senior said:**
> There are some useful tutorials here:

[http://zetcode.com/](http://zetcode.com/)

No video, but good all the same. There's a C++ and Python tutorial for Qt.

If you have C#/.NET experience, have you considered Mono?

[https://en.wikipedia.org/wiki/Mono_%28software%29](https://en.wikipedia.org/wiki/Mono_%28software%29)

Mono is not an option for me. I don't want GTK.

---

### Post by r-senior on 2012-04-14
What about Qyoto?

[http://techbase.kde.org/Development/Languages/Qyoto](http://techbase.kde.org/Development/Languages/Qyoto)

---

### Post by kio_http on 2012-04-14
> **r-senior said:**
> What about Qyoto?

[http://techbase.kde.org/Development/Languages/Qyoto](http://techbase.kde.org/Development/Languages/Qyoto)

Seems interesting. But I really like the was Visual Studio integrates GUI and coding. Like double clicking a button in the designer to create the code to handle the button click event.

Can I use an IDE for qyoto?

---

### Post by kio_http on 2012-04-14
Hi, I want to start developing (well to a more serious level than present) GUI applications in Ubuntu. 

I'm still choosing the language and I was thinking of maybe choosing depending on the IDE.

Ms Visual Studio is a really advanced and intuitive IDE. I want to be able to code in a similar environment. It should integrate GUI development with coding and functions like clicking on the button to auto generate event code etc would be nice. Database support is a must. I would prefer the application toolkit to be qt.

There should also be very good step by step tutorials for whatever language it uses.

I assume I need mysql for my database needs instead of mssql.

It seems like most development involves seperate designer, editor and compiler components.

---

### Post by CharlesA on 2012-04-14
mysql or postgresql unless you want to run a copy of Windows in a VM for mssql.

---

### Post by haqking on 2012-04-14
codeblocks
eclipse

But alot of people in linux dont use IDE

---

### Post by drdos2006 on 2012-04-14
Also think about the platform you want to develop for. For instance, tablets are becoming more popular. 
If you want to program for tablets as compared to desktops or laptops, then Java IDE might be more suitable. 
Netbeans for desktop, netbooks has a very good IDE, but to run the executable on a tablet needs lots of modifications. 
Eclipse has a very good IDE with WindowBuilder but again, to run on an Android tablet, needs lots of modifications.

regards

---

### Post by CharlesA on 2012-04-14
> **haqking said:**
> codeblocks
eclipse

But alot of people in linux dont use IDE
Does eclipse do Java? I've been told that Netbeans is pretty good, but I don't know if it does anything other than Java.

---

### Post by kio_http on 2012-04-14
> **drdos2006 said:**
> Also think about the platform you want to develop for. For instance, tablets are becoming more popular. 
If you want to program for tablets as compared to desktops or laptops, then Java IDE might be more suitable. 
Netbeans for desktop, netbooks has a very good IDE, but to run the executable on a tablet needs lots of modifications. 
Eclipse has a very good IDE with WindowBuilder but again, to run on an Android tablet, needs lots of modifications.

regards

No intention of tablets here. Traditional desktop applications.

---

### Post by haqking on 2012-04-14
> **CharlesA said:**
> Does eclipse do Java? I've been told that Netbeans is pretty good, b
ut I don't know if it does anything other than Java.

yes eclipse SDK includes the JDT java devtools

---

### Post by memilanuk on 2012-04-14
I don't really have any experience in this area... but would [QT Creator]("http://qt.nokia.com/products/developer-tools") be something of use to you?

---

### Post by CharlesA on 2012-04-14
> **haqking said:**
> yes eclipse SDK includes the JDT java devtools
Thanks!

---

### Post by QIII on 2012-04-14
> **haqking said:**
> But alot of people in linux dont use IDE

Well, a lot of us who make a living at it do.

---

### Post by mörgæs on 2012-04-14
Threads merged. Please don't post the same (or almost the same) question twice.

---

### Post by haqking on 2012-04-14
> **QIII said:**
> Well, a lot of us who make a living at it do.

yeah thats true, sorry i didnt mean it as a generalisation.

Peace

---

### Post by QIII on 2012-04-14
> **haqking said:**
> yeah thats true, sorry i didnt mean it as a generalisation

Yeah, I know.  I hope you realize that wasn't meant to be nasty.  Tone of voice doesn't carry very well in writing.  And I don't generally like emoticons to indicate humor - too AOL-ish.

;)

---

### Post by haqking on 2012-04-14
> **QIII said:**
> Yeah, I know.  I hope you realize that wasn't meant to be nasty.  Tone of voice doesn't carry very well in writing.  And I don't generally like emoticons to indicate humor - too AOL-ish.

;)

yeah no worries, i can usually tell ;)

and when im being sarcastic i <sarcasm> it

Peace

---

