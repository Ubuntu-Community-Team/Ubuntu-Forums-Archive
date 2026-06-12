---
title: "read pixel"
date: 2009-09-05
forum: Programming Talk
---

### Post by nipunreddevil on 2009-09-05
What function can i use to read pixel value and its attributes in pygame.Could someone please suggest any good open source library for c/c++/python to implement basic computer graphics(must be capable of setting pixels/reading them etc)

---

### Post by smartbei on 2009-09-05
Check out [http://www.pygame.org/docs/ref/surface.html](http://www.pygame.org/docs/ref/surface.html). Specifically, the get_at and set_at functions seem to be what you are looking for.

---

### Post by nipunreddevil on 2009-09-05
Thanks but how do i extract only the color out of the tuple i get from get_at function excluding the alpha value

---

### Post by smartbei on 2009-09-05
The tuple is in the format RGBA so to extract the color information simply take the first three values. For example:
```

surf = pygame.display.set_mode((640,480))
print "RGBA:", surf.get_at((0,0))
print "RGB:", surg.get_at((0,0))[:3]
print "The red component:", surf.get_at((0,0))[0]

```

---

### Post by nipunreddevil on 2009-09-05
Thanks a lot.worked perfectly.Really helpful example

---

