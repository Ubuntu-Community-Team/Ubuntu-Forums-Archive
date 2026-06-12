---
title: "[C/XLib] XAtom help"
date: 2009-05-01
forum: Programming Talk
---

### Post by OutOfReach on 2009-05-01
Hey so I am experimenting with Xatoms because I do not quite understand them fully, along with creating my own little WM. I am trying to set the _NET_CLIENT_LIST_STACKING atom, but I am having trouble...here's the relevant code:
[PHP]
    Window root, parent, *children;
    if (XQueryTree(disp, DefaultRootWindow(disp), &root, &parent, &children, &num) == 0) {
        printf("Error while querying tree.\n");
        exit(EXIT_FAILURE);
    }
    XChangeProperty(disp, DefaultRootWindow(disp), main_atoms[NetClientListStacking], XA_WINDOW, 32, PropModeReplace, (unsigned char *)children, num);   /* Update the atom */
    free(children);
[/PHP]

But somehow this isn't working, when I do:
```

xprop -root _NET_CLIENT_LIST_STACKING

```
It just outputs:
```

_NET_CLIENT_LIST(WINDOW): window id #

```


Any ideas?

---

