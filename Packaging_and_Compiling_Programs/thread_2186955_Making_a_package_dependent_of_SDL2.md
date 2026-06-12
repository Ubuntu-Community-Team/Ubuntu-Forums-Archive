---
title: "Making a package dependent of SDL2"
date: 2013-11-10
forum: Packaging and Compiling Programs
---

### Post by tony30 on 2013-11-10
Hi. I'm new to these forums and Ubuntu in general. I'm here because I am trying to release a small, cross platform game which uses SDL2. I have created a .deb file by following the method described in this video [[http://ubuntuone.com/0lj3md7kX1NqLQ7DoiBTGV]](http://ubuntuone.com/0lj3md7kX1NqLQ7DoiBTGV]). However, I also wanted to add a dependency on the SDL2 library. 

I found that I had to add 'libsdl2-2.0-0' to the Depends: line of my control file. I worry that I have embedded the version number of the library in my dependency, and when the next release of Ubuntu updates the library to 2.1 or something, my dependency will break.

Can you advise on what I should be putting on my Depends: line?

Thanks,

Tony

---

