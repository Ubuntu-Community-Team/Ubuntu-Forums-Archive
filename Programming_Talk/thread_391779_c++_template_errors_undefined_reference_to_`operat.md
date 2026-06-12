---
title: "c++ template errors: undefined reference to `operator&lt;&lt; ..."
date: 2007-03-23
forum: Programming Talk
---

### Post by bryan.taylor on 2007-03-23
I'm attempting to make a small set of logging classes, but for the final piece (for now) I keep getting the following error:
```
undefined reference to `operator<<(MBBMultipleOstream&, char const*)'
```
I have code in a header file (mbb_logger.h):
```
class MBBMultipleOstream : public std::ostream
{
 public:
    friend MBBMultipleOstream &operator<<(MBBMultipleOstream &, const char *);

 public:
    MBBMultipleOstream() :
        std::ios(0),
        std::ostream(&mEmptyStreambuf)
        {}

    void AddOstream(std::ostream &os)
        {
            mOstreams.push_back(&os);
        }

    template <class T>
        void Write(T item)
        {
            for (size_t i = 0; i < mOstreams.size(); i++) {
                (*mOstreams[i]) << item;
            }
        }

 private:
    std::vector <std::ostream *> mOstreams;

    MBBEmptyStreambuf mEmptyStreambuf;
};

template <class T>
MBBMultipleOstream &operator<<(MBBMultipleOstream &os, T item)
{
    os.Write(item);
    return os;
}
```

and when I try to use it in main(...) i get the above error:
```
    MBBMultipleOstream mos;
    mos.AddOstream(std::cout);
    mos.AddOstream(std::cerr);
    mos << "foo\n";
    mos << "bar\n";
```

If I explicitly create the following function instead of using the template everything works fine:
```
MBBMultipleOstream &operator<<(MBBMultipleOstream &os, const char *item)
{
    os.Write(item);
    return os;
}
```

Does anyone have any ideas?

I imagine that the code above is rather kludgy, but I don't know iostreams very well, so I'm open to suggestions about how to make the code better. :)

---

### Post by fifo on 2007-03-23
I think the non-template friend declaration might be the culprit.  The following works fine for me:
```
#include <iostream>
#include <vector>

class MBBMultipleOstream
{
 public:
    MBBMultipleOstream()
        {}

    void AddOstream(std::ostream &os)
        {
            mOstreams.push_back(&os);
        }

    template <class T>
        void Write(T item)
        {
            for (size_t i = 0; i < mOstreams.size(); i++) {
                (*mOstreams[i]) << item;
            }
        }

 private:
    std::vector <std::ostream *> mOstreams;
};

template <class T>
MBBMultipleOstream &operator<<(MBBMultipleOstream &os, T item)
{
    os.Write(item);
    return os;
}

int main()
{
    MBBMultipleOstream mos;
    mos.AddOstream(std::cout);
    mos.AddOstream(std::cerr);
    mos << "foo\n";
    mos << "bar\n";
    return 0;
}
```

---

### Post by bryan.taylor on 2007-03-23
Thanks, that worked perfectly. :)

---

