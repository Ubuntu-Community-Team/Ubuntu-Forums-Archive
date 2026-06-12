---
title: "C++ in linux..."
date: 2007-03-04
forum: Programming Talk
---

### Post by Fittersman on 2007-03-04
well i found kdevelop and under build, all it has is 'stop' but that is in light text (so if you click on it nothing happens), how do i build my C++ programs in linux and run them?

unless there is a better C++ app out there than kdevelop...

---

### Post by olejorgen on 2007-03-04
Check if you have build-essensial installed

---

### Post by Fittersman on 2007-03-04
yeah i do

---

### Post by j_g on 2007-03-04
Yet another testament to ease-of-use and intuitive nature of Linux IDEs.

---

### Post by lnostdal on 2007-03-04
> **Fittersman said:**
> well i found kdevelop and under build, all it has is 'stop' but that is in light text (so if you click on it nothing happens), how do i build my C++ programs in linux and run them?

unless there is a better C++ app out there than kdevelop...

i haven't used kdevelop(#1), but ..uhm.. have you tried creating a new project (from the file-menu i guess)?

#1: the ubuntu-programming*.pdf-files [here]("http://nostdal.org/~lars/writings/") describe my setup for C development (btw .. i would not trade this setup for any other IDE)

---

### Post by lnostdal on 2007-03-04
alright .. i installed kdevelop ..

* Project -> New Project
* Select the topnode "C" then "Simple hello world program" .. fill in an application name and click next
* click next all the way and click finish at the last one
* click Build --> Build Project (or press F8 )

```

lars@ibmr52:~/Desktop/blah/debug/src$ ./blah
Hello, world!

```

(edit: i can also start it using Debug -> Start .. or by pressing F9 .. the output from the application is in the "Application" pane at the bottom ....)

..so what's the problem? this took me 5 seconds to figure out - and i have _never_ used kdevelop before .. go figure

---

