---
title: "Basic C++ problem-std::getline"
date: 2010-03-13
forum: Programming Talk
---

### Post by EMR on 2010-03-13
So in a project I'm working on, refrences to an open file are bounced around to get data.  I'm told that something is wrong when I call std::getline here, but I can't seem to figure out why.  Thanks for the help.

```
std::string getStr ( std::ifstream & foo )
{
    std::string bar;
    std::getline( foo, bar );
    return bar;
};
```

Thanks...

---

### Post by MadCow108 on 2010-03-13
what should be wrong here?
it may be missing some error checking and you could use istream as parameter to allow more general streams than filestreams, but else its fine.

---

### Post by Simon17 on 2010-03-14
```

std::string getStr ( std::ifstream & foo )
{
    std::string bar;
    std::getline( foo, bar );
    return bar;
}[COLOR="Red"];[/COLOR]

```

---

### Post by EMR on 2010-03-15
I tried both of your suggestions, and it still seems to mess up.  I'll try it in a vacuum to make sure it isn't a bug somewhere else.

The new function that still steadfastly refuses to compile:

```
std::string getStr ( std::istream & foo )
{
    std::string bar;
    std::getline (foo, bar);
    return bar;
}
```
[B]
Edit:[/B]
I'm dumb, I didn't actually change ifstream to istream.  It works now, thanks.

---

### Post by MadCow108 on 2010-03-15
thats strange
getline also works with ifstream as that is derived from istream
what was the compiler error message?

---

