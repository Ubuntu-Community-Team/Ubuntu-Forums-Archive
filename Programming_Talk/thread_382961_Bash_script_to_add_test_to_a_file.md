---
title: "Bash script to add test to a file"
date: 2007-03-12
forum: Programming Talk
---

### Post by Nameless_one on 2007-03-12
I want to write a bash script that adds the contents of the clipboard to a certain file. I looked around quite a bit and I believe now that I cannot access the system clipboard inside the script, so I want to write a bash script that when invoked, gives me a prompt where I can paste the text I want to add. 

I have come up with this so far: ```
#!/bin/bash

read -p "Paste text: " quote

echo "
$quote" >> ~/.sample_file

exit

```

With this script though, only one line is pasted into the file. 

Also, although this is not necessary, I would like to avoid having to open a terminal and run the script manually. I tried making a launcher in the desktop with "Run in terminal" checked, but that didn't work. The best would be if I could run a command with Alt+F2.

Any ideas?

---

### Post by smartbei on 2007-03-12
why not have the script just open gedit on the sample file, and you would click save rather than ok?

---

### Post by Mr. C. on 2007-03-12
Bash knows nothing about any clipboards.  You will have to find a program that can been those needs and present the output to bash.  Only text messages would be meaningful. (what could bash do with a copied bitmap, for example).

This is a difficult question to answer, as I'm not sure exactly what you are trying to accomplish overall.

Perhaps zenity is useful to you.

```
man zenity
```

Can you clarify ?

Mrc

---

### Post by Nameless_one on 2007-03-12
I want to append the test to the file, without deleting the existing content. It's a quote archive :)

Edit: @Mr C.  thanks for pointing towards zenity! Looks like it can help a lot. I'll try it out.

---

### Post by Mr. C. on 2007-03-12
I see.  In that case, while zenity won't grab the clipboard for you, it will allow you to have a dialog box that you can paste into.  Your script will call zenity with your desired options, and append the input text into the file.  Assign the returned zenity text to a variable in bash, and that will remove newlines for you, so that your quotes are all on a single line in your quotes file.

You can test the idea by comparing the output of :

```
ls -l /

somevar=$(ls -l /)
echo $somevar
```

and then:

```
echo "$somevar" >> my_quotes_file
```

MrC

btw: I do not know if there is some utility in the desktop environment to grab text from the clipboard - their probably is, I just don't know.

---

### Post by Nameless_one on 2007-03-12
Actually I did it like this:```
#!/bin/bash

echo "
" >> ~/docs/quotes
zenity --entry >> ~/docs/quotes
exit
```

and it worked perfectly, newlines and all :) The problem with newlines was that bash's "read" couldn't handle them, but zenity solved that. I also made a launcher on the desktop for the script and it is much better now. Grabbing the clipboard automatically isn't so important, a Ctrl+V after a double click is a small price. 

Thank you very much for the help! :popcorn: for everyone.

---

### Post by Mr. C. on 2007-03-12
I'm glad it worked out for you.

btw. read can handle multiple lines.  You have to change the IFS variable.

MrC

---

### Post by Mr. C. on 2007-03-12
Use 

```
echo -e '\n'
```

instead of your multi-lined double quote.  Its cleaner.

MrC

---

### Post by Nameless_one on 2007-03-12
Thanks again.

---

### Post by smed on 2008-06-17
I realize this is an old post, but my question is closely related.

I'm wondering if it is possible to paste the text to a specific location in the quotes file. For instance the quotes files would look like:

first quote: "quote goes here"
second quote: "quote goes here"

Thanks for your help.

---

