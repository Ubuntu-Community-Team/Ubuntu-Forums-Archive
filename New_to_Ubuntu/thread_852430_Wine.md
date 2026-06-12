---
title: "Wine"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by jimi_hendrix on 2008-07-07
hi

I am trying to get the WINE emulator so i can use my windows programs in ubuntu

however, it asks me to post this in the terminal...

 ```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
``` 

after this it asks me for a password but it wont let me type...what do i do:guitar:

---

### Post by hrod beraht on 2008-07-07
Install WINE by going to *System*-->*Administration*-->*Synaptic Package Manager*. Search for *wine* in the package manager and install it that way.

Bob

---

### Post by phidia on 2008-07-07
You need to type your password there in the terminal. Entering your password is not mirrored back (you won't see anything) just type you password and press the enter key.

---

### Post by jimi_hendrix on 2008-07-07
thank you all...anything else i should download from that package thing?

---

### Post by hrod beraht on 2008-07-07
> **jimi_hendrix said:**
> thank you all...anything else i should download from that package thing?

Once you install it using Synaptic Package Manager, check and see if it shows up under the *Applications* menu. If not, log off and back on.
To install a windows program, just double-click the install file. The program will show up under *Applications*-->*Wine*-->*Programs*. Again, if it doesn't show up there after installation, log off and back on.

Bob

---

### Post by estyles on 2008-07-07
You should pretty much install everything from the package manager, whenever possible.  If you want to get a program or if a website tells you to install something, your best bet is to search the repositories first, via synaptic - it will make your life much easier in the long run.

Assuming you have Hardy, you will have compiz installed by default, so you'll want to install compiz configuration settings manager from Synaptic.  You should probably also install "build essential", in case you download anything that requires you to compile yourself.  Other than that, if there's a particular type of application you're looking for, do a search in synaptic and see what comes up.

---

### Post by jimi_hendrix on 2008-07-07
ok...one last thing

is it possible to get directX on linux because ive heard games run faster  on linux and i am a big gamer

if not i guess ill just have to settle with gaming on laggy old vista:guitar:

---

### Post by tjwoosta on 2008-07-07
if your a big gamer then youd probably better keep a copy of windows around

WINE does run some windows games but they are difinatly not faster then if you ran them on the same machine with windows

---

### Post by BGFG on 2008-07-07
I just now installed wine using 
```

sudo apt-get install wine
```

When i had just come to Ubuntu, i was definitely more comfortable with add remove and synaptic, being a windows baby. But I've come to love the terminal and the text environment. Basically there both really powerful. Just pick which is best for you.

I just happily burnt a cd using IMGBURN through wine. Went flawlessly.
One thing to make sure is that in 
System>>Administration>>Software Sources>>Ubuntu Software
You check all the options. So that whether in the terminal or in Synaptic. You can  access almost everything.

---

### Post by jimi_hendrix on 2008-07-07
ok ty

---

### Post by billgoldberg on 2008-07-07
You might want to install the stuff in my "codecs" guide in my signature.

---

