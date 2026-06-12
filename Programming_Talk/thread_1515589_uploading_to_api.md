---
title: "uploading to api"
date: 2010-06-22
forum: Programming Talk
---

### Post by mess110 on 2010-06-22
Hello

I am writing an API. I would like to know what other people's design opinions on how to do this are.

I could encode a binary file in base64 and send it.. but the question is how do I send it?

(I am using rails and ruby but I am also curious on the general approach)

Thanks :guitar:

---

### Post by simeon87 on 2010-06-23
I'm not sure what you're asking here: if you're designing an API, shouldn't it hide the actual method of sending the file? So for example (pseudocode):

```
public void sendFile(File file, Destination destination)
```

The actual way of encoding and sending would not be specified. Or do you want to specify that with a parameter?

---

### Post by mess110 on 2010-06-26
What I am curious about is, what approach would one normally take when one wants to send a file to an API designed in rails.

there must be several ways to get the file on the server; I am just curious about learning methods I might not now..

---

