---
title: "axel download from a text file"
date: 2011-10-27
forum: New to Ubuntu
---

### Post by lance bermudez on 2011-10-27
I want know how to get axel to download a list of files from a text file like wget can?

---

### Post by decoherence on 2011-10-27
Not sure if Axel already has a function to read a list, but if it doesn't you can use a while loop. Assuming you have a file named 'mylinks.txt' with your URLs separated by a return, ie

[http://www.example.com/1.jpg](http://www.example.com/1.jpg)
[http://www.example.com/2.mp3](http://www.example.com/2.mp3)
[http://www.example.com/bobsparty.avi](http://www.example.com/bobsparty.avi)

```

while read url; do axel $url; done < mylinks.txt

```

If someone tells you to do this with a for loop, don't. It will probably work but it's a bad habit ;)

---

### Post by lance bermudez on 2011-10-27
Will have have to watch the download? As in when the loop reaches the file's end the program will close or will I have to keep an eye on it as the word loop implies to keep the program from going for ever.

---

### Post by decoherence on 2011-10-27
> **lance bermudez said:**
> Will have have to watch the download? As in when the loop reaches the file's end the program will close or will I have to keep an eye on it as the word loop implies to keep the program from going for ever.

"while read url" translated in to english is "while there is something to read, assign it to the variable 'url'" Once it runs out of stuff to read (ie, it has gone through your entire file) it will stop on its own.

An infinite loop would be a loop that has no exit condition such as 'while [ 1 = 1 ]' -- 1 always equals 1 so it'll run forever (though that isn't generally the way we do an infinite loop -- it's just a clear example of one way to do it)

---

