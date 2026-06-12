---
title: "Python Project Structure"
date: 2008-08-16
forum: Programming Talk
---

### Post by thepopasmurf on 2008-08-16
What is the recommended structure for making a python project (or other project if it's similar)? I've made small programs but I'm not sure how to organise bigger projects or navigate existing packages.

Any ideas?

---

### Post by pmasiar on 2008-08-16
For web application, both Django and Turbogears will create empty project with 'best of practices' structure for you. If your program is just couple modules for commadline processing, keeping them all in a directory seems to work just fine... For big serious desktop app, ask elsewhere I don't do those :-)

---

### Post by thepopasmurf on 2008-08-17
yeah, I'd like to know because last time I made a program, it had only 3 files but each file had over 1000 lines, I'm just wondering the best way to organise programs

---

### Post by pmasiar on 2008-08-17
> **thepopasmurf said:**
> last time I made a program, it had only 3 files but each file had over 1000 lines, I'm just wondering the best way to organise programs

This depends on many factors:
- which parts of code could be reusable for other tasks
- which parts are independent and which depend on other
- tastes and preferences

This part of design is hard, it comes with experience, after many years and many projects you learn from the problems you solved (or not). Read advanced books about design and software engineering, see sticky FAQ.

---

### Post by Ed J on 2008-08-17
> **thepopasmurf said:**
> What is the recommended structure for making a python project (or other project if it's similar)? I've made small programs but I'm not sure how to organise bigger projects or navigate existing packages.

Any ideas?
Regarding python...
  By using the "import" statement you can use any classes and functions that are in any other module, as long as the file resides in your python system path.  So start out with one top-level module call it mainmother, or bigbadmodule, or whatever. Then import what you need from other modules.  Use object.attribute notation to make objects do your bidding. Namespaces are a key concept.  Place functions that might be used by other projects in modules that can be imported and reused.  Don't use global variables, don't hardcode paths like "C:\docum...", look both ways before you cross the street.
  Go [Here for free computer books]("http://www.freetechbooks.com/"), search for "python".  I know the python.org tutorial can be a tough read sometimes, drink coffee/tea/red bull if necessary.
  GFL

---

### Post by Wybiral on 2008-08-17
Aside from trivial scripting tasks, most Python programs are developed as though they were meant to be modules. This is exactly why this is such a common idiom:

```

if __name__ == "__main__":
    # Some code when run as program

```

Because the intent is that it's also capable of being imported as a module. Code reuse... That's a strong element in Python development (and most dynamic high-level languages).

This also encourages the way of thinking that you should write everything as though it were a reusable API. It makes things clearer for readers and chances are you'll need one of your components in another project down the road.

---

