---
title: "accesing windows thru network and running its applications"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by Walc on 2008-04-27
Hey folks
I need an advice here.
Im having 2 pcs connected thru router: 1 is ubuntu 7.10, other one is vista desktop. Now the thing is: is it possible in my case to connect on my laptop with ubuntu to vista desktop pc, access its resources and especially run particular application? Or theres no way 2 do that and i have to install virtuall windows on my ubuntu laptop....? i would rather not use wine.....
thx

---

### Post by KillerKiwi on 2008-04-27
You can use rdp to access the windows desktop from ubuntu

Applications -> Internet -> Terminal Server Client

---

### Post by Walc on 2008-04-27
ok
but what can i do to run windows applications? <exe files> ?
is it even possible?

---

### Post by nhandler on 2008-04-27
I would suggest setting up a vnc server on the windows machine. You could then connect to it from Ubunu. This would allow you to control your windows machine as if you were sitting in front of it. By that, I mean you would be able to access all of the files on it, run ALL of the applications, access any devices connected to it, etc. The only limitation is that if you were to launch MS Word (or any application), you would not be able to open a .doc file on your ubuntu computer. You would only be able to open .doc files on your windows computer. This problem can be overcome by emailing the file to yourself and then downloading it on the windows computer.

---

### Post by Walc on 2008-04-27
which vnc server would u suggest m8?

---

### Post by Walc on 2008-04-27
i have chosen tight VNC
but the thing is....<i have never used vnc b4 so...> once im connected to desktop pc, im able to run its applications and  stuff, just as i wanted.
But there is a big BUT > its basiclly impossible for any1 else to use that desktop pc in the same time, doin whatever they want, like surfing web, watching tv...
Is there less invasive way to achieve my goal? By that i mean me beeing able to axx desktop pc, run its appz, and 2nd person using that desktop pc at the same time, doin random things., without lookin at what im doin, and therefore making it impossible to work on it.

---

### Post by Walc on 2008-04-29
bump

---

