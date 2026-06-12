---
title: "Terminal. How do I retreive the messages that were displayed, closed it too early."
date: 2008-05-31
forum: New to Ubuntu
---

### Post by philinux on 2008-05-31
I ran a command and I want to re-read the messages that came up.

Thanks.

---

### Post by sisco311 on 2008-05-31
You can redirect the standard output to a file:
```
echo "message" > message.txt
```or
```
echo "message" >> message.txt
```to append the text file with the output.
or
```
echo "message" | tee message.log
```to display the message on stdout and save in the message.log file.

Use more, less or cat to read the text file
```
more message.txt
less message.txt
cat message.txt
```

---

### Post by philinux on 2008-05-31
I mean I've closed the terminal and now wish to re-read the messages that were displayed.

I don't mean history of commands I've used.

---

### Post by infinitejones on 2008-05-31
You could open the terminal again, press the up arrow, and the last command you entered should appear again, so hit enter to run it again. Assuming you haven't made many other changes inbetween then and now, the error messages should be the same...

---

### Post by philinux on 2008-05-31
> **infinitejones said:**
> You could open the terminal again, press the up arrow, and the last command you entered should appear again, so hit enter to run it again. Assuming you haven't made many other changes inbetween then and now, the error messages should be the same...

Already did that. The error messages aren't the same. I guess they are lost in the ether.

---

### Post by alzwded on 2008-05-31
don't think you can, then again i might be wrong - you can check the log files of the specific application. next time you want to keep track of what the prog printed out do " program > ~/program.log " or something like that.

---

