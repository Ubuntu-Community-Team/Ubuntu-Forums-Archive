---
title: "What else do I need to code"
date: 2012-01-05
forum: Programming Talk
---

### Post by vanangamudi on 2012-01-05
I've started with Clutter examples, and installed clutter libs... and some more libs... system got clumpsy... so i reinstalled the system and installed Gnome3 since it is based on gtk-clutter ... 

[https://lh4.googleusercontent.com/-Q_INkYyPIfI/TwZ7-a_IdAI/AAAAAAAAAKU/OyjT3D7CWq0/s1152/Screenshot.png](https://lh4.googleusercontent.com/-Q_INkYyPIfI/TwZ7-a_IdAI/AAAAAAAAAKU/OyjT3D7CWq0/s1152/Screenshot.png)

---

### Post by layers on 2012-01-06
which language? and for what purposes? (except taking over the world, brain)

---

### Post by sisco311 on 2012-01-06
Please don't post large images; use thumbnails instead.

---

### Post by vanangamudi on 2012-01-06
> **layers said:**
> which language? and for what purposes? (except taking over the world, brain)

C++ or Python... for now I'm on C++...

---

### Post by Tony Flury on 2012-01-06
What sort of applications do you want to develop - that will determine what (if any) extra libraries you want or need.

Normally the Devlopment process starts with a concept (and maybe a choice of language), and from the concept you do some very high level design work (i.e. an understanding of how your application will work) - from that you can determine what libraries you might need to accomplish your design.

For instance if you are looking at writing a command line application which does some basic file manipulation - then all you need is the standard C library - no GTK, no database etc.

If you want to write a GUI application that drags data from the internet, stores and processes that data over a significant amount of time etc - then you need a different set of libraries(GUI toolkit, internet/web protocols, databases, maybe numeric processing etc).

Starting by installing a load of libraries seems the wrong way round to me.

---

### Post by vanangamudi on 2012-01-06
> **Tony Flury said:**
> What sort of applications do you want to develop - that will determine what (if any) extra libraries you want or need.

Normally the Devlopment process starts with a concept (and maybe a choice of language), and from the concept you do some very high level design work (i.e. an understanding of how your application will work) - from that you can determine what libraries you might need to accomplish your design.

For instance if you are looking at writing a command line application which does some basic file manipulation - then all you need is the standard C library - no GTK, no database etc.

If you want to write a GUI application that drags data from the internet, stores and processes that data over a significant amount of time etc - then you need a different set of libraries(GUI toolkit, internet/web protocols, databases, maybe numeric processing etc).

Starting by installing a load of libraries seems the wrong way round to me.

I'm going to write a real-time data acquisition and plotting program for my 8051 Proj. GUI is necesary and I'm gonna use Clutter Since Hardware acceleration is available, and custom gui components can be generated on my own... I'm a techie fellow ad also hav enough xperience in programming but never completed a proj still. As for now no need for Internet for my app. so just GUI toolkit of my own developed(going to be developed) based on CLutter... Hope u got my question >>>>>:confused:

---

### Post by layers on 2012-01-06
In my programming days, I've never done GUI with C++. All I know, for all my needs, installing g++ would suffice.
```
suod apt-get install g++
```

---

### Post by layers on 2012-01-06
In my programming days, I've never done GUI with C++. All I know, for all my needs, installing g++ would suffice.
```
sudo apt-get install g++
```

---

### Post by robgraves on 2012-01-06
You can use any text editor and g++ as compiler for c++, or if you want an IDE you can use code:blocks amongst others.

---

### Post by vanangamudi on 2012-01-07
Guys I'm using Code::Blocks IDE and I've installed g++ already... I need info specific to Clutter.... how to use CLutter in my project... what I hav to do to compile my Project with Clutter...?

---

### Post by vanangamudi on 2012-01-08
Thanx for your help guys. I found out how to setup the development environment in Code::Blocks IDE...

---

