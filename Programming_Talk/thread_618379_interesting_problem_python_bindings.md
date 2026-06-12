---
title: "interesting problem: python bindings"
date: 2007-11-20
forum: Programming Talk
---

### Post by Hendrixski on 2007-11-20
We're working on a new library that will do cool stuff with mythtv, and are hoping to make some python bindings so as to lower the barrier to entry for hacking it.

We're using SIP because it integrates well with Qt, in fact it was developed in order to make PyQt, and is used for KDE's Python bindings (pyKDE).  So we're using the sourcecode of pyKDE as an example, and we're using this manual: [http://www.riverbankcomputing.com/Docs/sip4/sipref.html#a-more-complex-c-example](http://www.riverbankcomputing.com/Docs/sip4/sipref.html#a-more-complex-c-example)

The only changes to the example form the manual are that we changed the configure.py script to handle multiple lines as follows:
```

# Run SIP to generate the code.  Note that we tell SIP where to find the qt
# module's specification files using the -I flag.
os.system(" ".join([config.sip_bin, "-c", ".", "-b", build_file, "-I", config.pyqt_sip_dir, qt_sip_flags, os.path.join("sip", "master.sip
")]))

#install the SIP specification file for this module
sipfiles = []

for s in os.listdir ("sip"):
    if s.endswith (".sip"):
        sipfiles.append(os.path.join("sip", os.path.basename(s)))

installs = []

installs.append([sipfiles, os.path.join(config.default_sip_dir, "Vex")])

```

and we have a master.sip file which looks like this
```

%Module Vex

%Include elementfield.sip
%Include element.sip
.......

```

Which basically ends up calling all of the other .sip files that correlate to the .h files.  They look like this:
```

%Import qt/qtmod.sip

namespace vex{

class ElementField : QObject {

%TypeHeaderCode
#include <elementfield.h>
%End

  public:
    ElementField(const char*, bool );
    virtual ~ElementField();

    const QString &GetName() const;
    const QString &GetValue() const;
    const bool GetReadOnly() const;

    bool SetValue(QString Value);
  signals:
    void ChangedSignal(const ElementField*, QString&, QString&);

}; //class elementfield
}; //namespace vex

```

Now the interesting thing is that when we run **python configure.py** all it says is
[quote=error_message]
sip: ElementField is undefined
[/quote]

Meaning that python isn't recognizing ElementField at _some point in the process_.  I suspect it's the part where at the end where ChangedSignal() uses ElemengField as a parameter before python could have picked it up.  However, we do this kind of thing a lot in the library that we wrote, and I hope that doesn't mean we simply can't make bindings for it.

Does anybody have any experience with this kind of thing or have any ideas that would help us break the deadlock?

---

### Post by Hendrixski on 2007-11-21
:-( Well the solution wasn't as interesting as the problem.

In the .sip files where ElementField has a method that takes an ElementField, the problem is in the namespace.  All I had to do was prepend the namespace to the parameter, like this:  vex::ElementField

Coming from a Java background, this is absolutely non-apparent.  Well, at least I hope that this helps somebody else in the near future if they do a search on how to generate Python bindings. :-)

---

