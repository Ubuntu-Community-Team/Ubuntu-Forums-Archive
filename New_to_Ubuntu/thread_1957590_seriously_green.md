---
title: "seriously green"
date: 2012-04-12
forum: New to Ubuntu
---

### Post by Redd4 on 2012-04-12
hi all, take pity on a first timer plz! we've been intructed to learn how to use the command line in ubuntu as part of our course. im trying to find the word count, byte count and line count in a given file. i looked it up and the command seems to be wc. im in the right directory... the file is called shakespeareansonnet. so im typing it as such, but its telling me theres no such file or directory, maybe you could advise me what im doing wrong?

wc -c shakespeareansonnet.txt

regards,
redd .

---

### Post by roelforg on 2012-04-12
If you haven't had man pages yet:
> 
**MANPAGE 101**

Use:
```

man <command_name>

```
To get help, info and examples about a command.
Exit by pressing q
Navigate with arrow keys.


---

### Post by souravc83 on 2012-04-12
Try using the ls command. Go to the terminal and navigate to the directory where you placed the file.
(If you aren't comfortable with that, place the file in the home directory)
Then go to the terminal and type

[HTML]ls[/HTML]

You should be able to see the file listed on the output.

Once you ensure that, it should work. 

The only other thing that I can think of is that you are not writing the spelling of the file correctly.

For that, type "wc -c", then type the first few words of the filename, and press the tab key. The computer will complete the name for you if the file is in the directory. Also, you can probably rename the file to a smaller name that it easy to type, like foo.txt or something.

Let us know if it still doensn't work after both these troubleshoots.

---

### Post by oldos2er on 2012-04-12
> **Redd4 said:**
>  maybe you could advise me what im doing wrong?

wc -c shakespeareansonnet.txt

regards,
redd .

Is it shakespeareansonnet or shakespeareansonnet.txt ? Use the Tab key to auto-complete the file name for you. Type **wc -c sha** then hit **Tab**.

---

### Post by Redd4 on 2012-04-12
guys your legends i cant thank you enough. really though. 

will try those. im thinking the spelling is too long.

---

### Post by Redd4 on 2012-04-12
i renamed it file .txt and it worked. (its always the little things!)  
no doubt ill be back with more questions at some stage. cheers.

---

