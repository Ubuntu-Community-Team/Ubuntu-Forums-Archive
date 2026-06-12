---
title: "Pyhon: File writing delayed"
date: 2008-05-07
forum: Programming Talk
---

### Post by edd07 on 2008-05-07
Hello, I am trying to append a string to a file in every iteration of a loop, however, it seems that the file only gets written in the next iteration. So, When I run it for the first time, it does nothing; the second time it writes the string it should have written the first time and so on. 

Does anyone have any idea why this is happening?

BTW, I'm opening the file in 'append' mode, and closing the file every iteration. Oh, and somehow, opening the file for reading in the same iteration fixes the problem, but it leads to useless lines of code.

Thanks

---

### Post by tamoneya on 2008-05-07
can you post your code.

---

### Post by LaRoza on 2008-05-07
> **edd07 said:**
> Hello, I am trying to append a string to a file in every iteration of a loop, however, it seems that the file only gets written in the next iteration. So, When I run it for the first time, it does nothing; the second time it writes the string it should have written the first time and so on. 

Does anyone have any idea why this is happening?

BTW, I'm opening the file in 'append' mode, and closing the file every iteration. Oh, and somehow, opening the file for reading in the same iteration fixes the problem, but it leads to useless lines of code.

Thanks

Almost no application will write to a file immediately. That is terribly inefficient and slow. If this isn't a problem, then I wouldn't recommend you alter this.

[http://docs.python.org/lib/bltin-file-objects.html](http://docs.python.org/lib/bltin-file-objects.html)

---

### Post by Can+~ on 2008-05-07
What are you trying to achieve? If it's a sort of log, you could use the [logging module](http://docs.python.org/lib/module-logging.html)

---

### Post by Quikee on 2008-05-08
Just flush() the toilet. :)

---

### Post by edd07 on 2008-05-08
Thank you all very much for your replies.

The flush() thing seems to do the trick :-D

Thanks again...man, I love these forums

---

