---
title: "Rendering Without Changing Depth Buffer (OpenGL)"
date: 2008-01-05
forum: Programming Talk
---

### Post by Lster on 2008-01-05
Hi

There may well not be any way I can do this, I certainly haven't found one, but here goes anyway! I would like a way to render an object using depth testing but not altering the depth buffer. Alternately, being able to render to just the depth buffer would be OK (without rendering to the color buffer).

Is there a way to do either of these things?

Thanks
Lster

---

### Post by Auria on 2008-01-05
Yes it is possible:
```

glDepthMask(GL_FALSE);

```

[http://www.opengl.org/documentation/specs/man_pages/hardcopy/GL/html/gl/depthmask.html](http://www.opengl.org/documentation/specs/man_pages/hardcopy/GL/html/gl/depthmask.html)

---

### Post by Lster on 2008-01-05
Perfect - Thank you! :)

---

