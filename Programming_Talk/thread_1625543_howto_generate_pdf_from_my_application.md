---
title: "howto generate pdf from my application?"
date: 2010-11-19
forum: Programming Talk
---

### Post by c174 on 2010-11-19
Hi,

I have a question about how to generate pdf-files. My application is a simulation program and it runs on both Windows and Linux.

I want to improve the program by writing as summary of the simulation to a file before the program exits. It would be easy to output the summary as a TEXT file... But I think a PDF file is better, since it allows more formatting and is not editable.

For example, the program could create a TEX file and when use latex, dvips, and finally ps2pdf to create a PDF. My question is then: 

* Is it possible to link latex into the executable? 
* Would it be possible to link in the needed latex package also?

It would be nice if users of the program did not have to install e.g. MikTex and so by themselves.

Maybe somebody solved this task in an entirely different way than suggested here? Maybe it is possible to markup a PDF manually?

---

### Post by Zugzwang on 2010-11-19
You can use suitable library. See, e.g., [http://stackoverflow.com/questions/58730/open-source-pdf-library-for-c-c-application](http://stackoverflow.com/questions/58730/open-source-pdf-library-for-c-c-application)

---

### Post by Arndt on 2010-11-19
> **c174 said:**
> Hi,

I have a question about how to generate pdf-files. My application is a simulation program and it runs on both Windows and Linux.

I want to improve the program by writing as summary of the simulation to a file before the program exits. It would be easy to output the summary as a TEXT file... But I think a PDF file is better, since it allows more formatting and is not editable.

For example, the program could create a TEX file and when use latex, dvips, and finally ps2pdf to create a PDF. My question is then: 

* Is it possible to link latex into the executable? 
* Would it be possible to link in the needed latex package also?

It would be nice if users of the program did not have to install e.g. MikTex and so by themselves.

Maybe somebody solved this task in an entirely different way than suggested here? Maybe it is possible to markup a PDF manually?

You know your own needs best, of course, but why is important that the reports not be editable? If that requirement is not so important, then I would generate LaTeX or HTML and let the user do the rest of the processing.

---

### Post by c174 on 2010-11-19
@Zugzwang: 
Thanks for the link! It mentions several projects (libHaru, colorpilot pdflibrary, PoDoFo, ...) of the kind I'm looking for:D

@Arndt:
The reason I value non-editability is that the summary will used for documentation of the simulation setup. A PDF will be "read-only" in normal circumstances avoiding accidental editing.

---

