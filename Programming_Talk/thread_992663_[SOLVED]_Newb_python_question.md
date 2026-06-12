---
title: "[SOLVED] Newb python question"
date: 2008-11-25
forum: Programming Talk
---

### Post by Castlef on 2008-11-25
I am doing the tutorial how to think like a computer scientist... on 4.11 it starts using a python module called gasp which is not included in the standard library. My question is how do I put it in the library so python just finds it?

I managed to find gasp from here [https://launchpad.net/gasp-code/stable-0.1.x/0.1.1](https://launchpad.net/gasp-code/stable-0.1.x/0.1.1)

I downloaded it, and it is just a folder containing a few .py files. I then moved it to /usr/lib/python2.5 which is my current python release but it still doesn't find the module when i try to import gasp... 

how do i import all the functions from all the .py's in the gasp folder?

thanks

edit: nm I figured it out. When I extracted it with the archive manager it created another gasp folder inside the gasp folder.. so it was like gasp/gasp/allthefiles . So I went and moved all of the files up one folder to the first gasp and it worked. sudo mv * ../

---

