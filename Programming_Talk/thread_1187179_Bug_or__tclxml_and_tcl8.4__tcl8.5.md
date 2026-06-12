---
title: "Bug or ? tclxml and tcl8.4 / tcl8.5"
date: 2009-06-14
forum: Programming Talk
---

### Post by Wim Sturkenboom on 2009-06-14
```

fortyfourgalena@desktop1:~/progs/tcl/simpledb$ tclsh
% puts $tcl_version
**8.4**
% package require xml
**3.1**
% exit
fortyfourgalena@desktop1:~/progs/tcl/simpledb$ /usr/bin/tclsh8.5
% puts $tcl_version
**8.5**
% package require xml
[COLOR="Red"]attempt to provide package sgmlparser 1.1 failed: package sgmlparser 1.0 provided instead
[/COLOR]% exit
fortyfourgalena@desktop1:~/progs/tcl/simpledb$ 

```

OK, in a first attempt to work with XML I've installed tclxml from the Ubuntu repository. The (little) funny and (mostly) frustrating part is that tcl8.4 is happy and tcl8.5 is not. [COLOR="Blue"]Can somebody shine some light on this?[/COLOR]

Additional info:
[LIST]
[*]tcllib version 1.10 installed (from Ubuntu repository; 1.11 was advised on the tclxml website but that issue would apply to both versions (I think)).
[*]Ubuntu 8.04, upgraded from 6.06
[*]I need tclsh8.5 due to the specifics of *clock scan*
[/LIST]

---

### Post by Wim Sturkenboom on 2009-06-16
We've got a tiny step further.

tclxml is installed in /usr/lib/Tclxml3.1

pkgIndex.tcl
```

package ifneeded sgmlparser   **1.1**       [list source [file join $dir sgmlparser.tcl]]

```
sgmlparser.tcl
```

package provide sgmlparser **1.0**

```

What I have not found yet is where a decision is taken based on the TCL version (8.4 / 8.5)

---

### Post by stevescripts on 2009-06-16
> **Wim Sturkenboom said:**
> 
...
What I have not found yet is where a decision is taken based on the TCL version (8.4 / 8.5)

Wim - those requirements are in the package index file.

FWIW, folks that I know and trust recommend using tdom to parse xml - 
personally I have had no serious requirements for xml parsing ...

Hope this helps a bit.

Steve

---

### Post by Wim Sturkenboom on 2009-06-16
Hi Steve, thanks for the reply.

Can you please indicate which package index file you're refering to (if possble).

I did grep for 8. (eight dot) in the tclxml directory and I have not found anything that relates to 8.4 and 8.5; only thing that I found is from tclsh 8.0 to 8.1 

I'm considering to remove the current tclxml and tclib packages and install from another sources (including tcldom), not the repositories. But I want this to be sorted as well as this all comes from official repositories and therefore should work without further user intervention.
I've now asked a question on launchpad as well.

With what I've found till know, I can change it so this error disappears but I don't know the further implications.

---

### Post by stevescripts on 2009-06-16
Wim

check the contents of the pkgIndex.tcl file in the tclxml-3.x directory - it will list the other package dependencies that your version of tclxml requires.

Steve

---

### Post by Wim Sturkenboom on 2009-06-16
Thanks again.

I did (see post #2)

```

package ifneeded xml::c       3.1 [list load   [file join $dir libTclxml3.1.so]]
package ifneeded xml::tcl     3.1 [list source [file join $dir xml__tcl.tcl]]
[B]package ifneeded sgmlparser   1.1       [list source [file join $dir sgmlparser.tcl]]
[/B]package ifneeded xpath        1.0       [list source [file join $dir xpath.tcl]]
package ifneeded xmldep       1.0       [list source [file join $dir xmldep.tcl]]

```

and sgmlparser.tcl
```

package require sgml 1.9
package require uri 1.1
**package provide sgmlparser 1.0**

```
I think that that's what is going wrong. But for some reason tclsh8.4 is happy and tclsh8.5 is not. And that dependency I have not found yet.

---

### Post by stevescripts on 2009-06-16
Wim,

Out of curiosity, I tried a d/load and install from source - ran into a bit of a snag...

Will try to sort this out in the next day or so (hope that's soon enough)...

Any chance of a workaround for your clock scan options, to allow you to use 8.4 in the meantime?

Steve

---

### Post by Wim Sturkenboom on 2009-06-16
I haven't looked at that (my requirement is based on the fact that clock scan can reliably work). In another project I ran into an issue where *clock scan* choked in certain date formats without the *-format* option; unfortunately those dates came as is, so no chance on getting them in another format.

I do not really expect someone to install something that is not needed but it's highly appreciated.

WimS

---

### Post by stevescripts on 2009-06-16
It is an oddity for anything from that author to not *just work*...

Those of us in the tcl community *expect* tcl (and most of its extensions)
to just work.

Steve

---

### Post by Wim Sturkenboom on 2009-06-20
Update:
I have asked the question on launchpad now as well ( [https://answers.launchpad.net/ubuntu/+question/74419](https://answers.launchpad.net/ubuntu/+question/74419) ; one reply with same issue) and reported it as a bug ( [https://bugs.launchpad.net/ubuntu/+bug/389308](https://bugs.launchpad.net/ubuntu/+bug/389308) )

Keep you posted

---

### Post by Wim Sturkenboom on 2009-08-31
It's finally a confirmed bug (after over 2 months) ;)

A solution/workaround is also posted on launchpad.

---

