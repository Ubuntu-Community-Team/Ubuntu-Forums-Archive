---
title: "Any parsing buffs out there?"
date: 2006-10-09
forum: Programming Talk
---

### Post by almahtar on 2006-10-09
I bought a Mac Mini (one of the Intels), and got frustrated with OSX so I slapped Linux on it. I can do everything in Linux that I could in OSX easier and with better eye candy except one thing: get the infrared remote to work.

Now before anyone suggests lirc, tried it: doesn't recognize my stuff.

The reciever resides at /dev/hiddev0, so I directed its output through a little program I made that'd just print the integer values of the bytes it recieves.

After watching it for a little while, I saw a few patterns so I wrote up a quick grammar for it and threw it into Bison.

Now here's where I need help: I can parse everything just fine, but it has to be a static file. The "compiler" that Bison generates won't start parsing until it gets an EOF. Does anyone know a program that can parse stuff on the fly so I can just aim it at /dev/hiddevice0 and let it go?

---

### Post by Steveire on 2006-10-10
I'm not sure about this stuff, but here's something you might be able to work with. I don't have that device, so I just did 
```

cat /dev/random >> somefile.

```
Then I opened a python interpreter while that was running, and I did
```

file = open("somefile", "r")

```
Then, everytime I did file.read(), python printed the new part of somefile. You can probably do both actions within python with multithreading. You'd want to trim the file as well, otherwise it could get very big.

Hope that helps.

---

