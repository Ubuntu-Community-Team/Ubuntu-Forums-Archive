---
title: "Java BufferedWriter question"
date: 2010-02-08
forum: Programming Talk
---

### Post by SNYP40A1 on 2010-02-08
I have implemented a function in Java which logs data to a text file using BufferedWriter.  Periodically, I want to close the currently-opened text file and write my data to a new one depending on what the data to be written looks like.  I have that part figured out, but how do I check to ensure that the stream is ready to be written (allowed enough time for the BufferedStream to be setup)?  In C++, there's an is-open or good command one can call to ensure that the stream is ready ([http://www.cplusplus.com/doc/tutorial/files/](http://www.cplusplus.com/doc/tutorial/files/)).  For the buffered writer class in Java, is it safe to assume that once this line is called:

FileWriter fstream = new FileWriter("out.txt");
        BufferedWriter out = new BufferedWriter(fstream);

It's safe to write to BufferedWriter out?

---

### Post by Some Penguin on 2010-02-08
> **SNYP40A1 said:**
> For the buffered writer class in Java, is it safe to assume that once this line is called:

FileWriter fstream = new FileWriter("out.txt");
        BufferedWriter out = new BufferedWriter(fstream);

It's safe to write to BufferedWriter out?

Short answer:  yes.

Long answer:  If the write occurs to a network file system or something else special like that, I could see a situation in which subsequent writes will trigger exceptions due to problems with the network that didn't happen until then.  However, regarding specifically what you ask about: a properly functioning JVM should not proceed to the next bit of bytecode until 'out' is valid.  I have heard about the occasional not-properly functioning JVM, but these are hopefully rare and failing in more subtle ways.

---

### Post by SNYP40A1 on 2010-02-10
Ok, thanks for your help.

---

