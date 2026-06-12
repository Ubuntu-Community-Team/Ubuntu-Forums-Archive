---
title: "Indentation settings in KDevelop/Kate"
date: 2009-10-18
forum: Programming Talk
---

### Post by WebDrake on 2009-10-18
Hello all,

One real annoyance of KDE4 has been that Kate, and consequently all editors that use it (KDevelop, Quanta Plus, Kile, ...), has some new and irritating indentation settings.

My normal code indentation rule is, 'tabs for indentation, spaces for alignment'.  So, for example, if I'm defining a class in C++:
```

class myClass {
private:
    int x;
    int y;
    int z;
public:
    myClass(int X,
            int Y,
            int Z)
    {
        x = X;
        y = Y;
        z = Z;
    }
};

```
then in the lines,
```

    myClass(int X,
            int Y,
            int Z)

```
... the myClass is preceded by a tab; the int Y, and int Z) are preceded by a tab and 8 spaces.

All coders' flamewars aside, I like this because it means that indentation settings can be varied (by varying the tab width) without affecting the alignment of code elements.

The annoyance is that whereas in KDE3 this was easy to do, in KDE4 Kate and its children replace spaces with tabs when starting a newline.  So, in the case of the above code, if I hit enter after
```

    myClass(int X,
            int Y,

```
what I *want* to see is a tab followed by 8 spaces; but what I would see (assuming tab-width is set to 4 spaces) is just 3 tabs.

I've been unable to work out how to get Kate, KDevelop and so on to produce the correct mix of tabs for indentation, spaces for alignment.  Can anyone advise?

Thanks & best wishes,

    -- Joe

---

### Post by WebDrake on 2010-05-05
I'm going to raise this issue again, just in case anyone has found a solution.  It's profoundly irritating; I've found a way to make mixed tab/space indentation work in vim, but I really prefer working in Kate and KDevelop for any kind of text editing, including coding work.

Can anyone suggest solutions? :-)

---

