---
title: "Displaying a counter"
date: 2010-07-18
forum: Programming Talk
---

### Post by Eragon0605 on 2010-07-18
Hello, all. I can't seem to figure out how to display a counter, such as a score counter, in opengl using fonts. It seems that no font library can display integers, so how would I do this? I am using C++, Kubuntu 10.04, and I am using the fnt library in plib.

---

### Post by soltanis on 2010-07-19
Have you considered using FreeType? There is a Windows specific tutorial on [NeHe]("http://nehe.gamedev.net/data/lessons/lesson.asp?lesson=43") that I found that you may be able to adapt to Linux.

---

### Post by Eragon0605 on 2010-07-19
Ah, nevermind. Found the solution on the Ars Technica OpenForum:
```

    int Number = 1834;
    std::string String = static_cast<std::ostringstream*>( &(std::ostringstream() << Number) )->str();
    std::cout << String;


```

---

