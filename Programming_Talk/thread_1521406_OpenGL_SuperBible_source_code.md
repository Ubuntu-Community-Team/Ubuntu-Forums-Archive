---
title: "OpenGL SuperBible source code"
date: 2010-06-30
forum: Programming Talk
---

### Post by kahumba on 2010-06-30
Hi,
I'm asking if someone has an idea why does this book have childish mistakes in source code? I'm sure I'm not the only one who's noticed it. I'm not complaining - I'm curious and wanna know maybe there's some serious reason behind it, it wouldn't be a surprise for a third-rate book, but it's one of the best ones around if not the best one for beginners.
Example, notice how the author is comparing "key" with 356 instead of "xRot" and "yRot" accordingly:
```

void SpecialKeys(int key, int x, int y) {
    if (key == GLUT_KEY_UP)
        xRot -= 5.0f;

    if (key == GLUT_KEY_DOWN)
        xRot += 5.0f;

    if (key == GLUT_KEY_LEFT)
        yRot -= 5.0f;

    if (key == GLUT_KEY_RIGHT)
        yRot += 5.0f;

    if (key > 356.0f)
        xRot = 0.0f;

    if (key < -1.0f)
        xRot = 355.0f;

    if (key > 356.0f)
        yRot = 0.0f;

    if (key < -1.0f)
        yRot = 355.0f;

    // Refresh the Window
    glutPostRedisplay();
}

```I'm really surprised, I googled and apparently no one bothered asking.

PS: it's already the 4th edition, so by the 4th edition they should have sorted such silly mistakes out.

BTW: 5th edition is due out in mid July!

---

