---
title: "golang read from file x bytes but also include '\n'"
date: 2018-08-03
forum: Programming Talk
---

### Post by jason.jackal on 2018-08-03
Folks,
I am toying around with some Go for a simple idea I have; however, I cannot find any documentation on the Go site that deals with  read 'x' bytes and up to the next '\n'. 

Is this possible with the standard Go library, or has anyone made a function that will do this?

Thank you
JJ

---

### Post by edadasiewicz on 2018-08-04
I don't understand the meaning of reading the next 'x' bytes AND up to the next '\n'.  In all of the go code I have written I was always reading up to the next '\n' by using the bufio package.  For example:

fi, err := os.Open(path)
// check err
defer fi.Close()
scanner := bufio.NewScanner(fi)
for scanner.Scan() {
  line := scanner.Text()
  // skip any blank lines
  if len(line) <= 1 {
    continue
  }
  // remove any trailing newline
  line = strings.TrimSuffix(line , "\n")
  ...
}

I'm not sure if this is any help or just adds to the confusion.

---

### Post by jason.jackal on 2018-11-19
> **edadasiewicz said:**
> I'm not sure if this is any help or just adds to the confusion.

You helped a great deal; however, I still need to learn a great deal about Go. Coming from Python, which does a lot of the heavy lifting for you, which is great, but I am finding it hard to transition to Go.

Thank you

---

