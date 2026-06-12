---
title: "Query about terminal command equivilant for this program"
date: 2009-10-01
forum: Programming Talk
---

### Post by alzaf on 2009-10-01
This is more of a query than a question.

When downloading text files from the internet like tutorials, they are usually formatted at x number characters per line (think it is 80). 

This is a pain when opening the text file in a word-processor and trying change the right hand page margin in order to fit more text onto a page when printing out. 

To solve this, I have written the below program which works fine but I was wondering if there is a terminal command that could do something similar? 

I tried tr but that strips out all line feeds and making it a jumble of text and not sure how sed works.

Thanks in advance.  

```
# reformat_txtfile.py

import string

def main():
	txtfile = open("file.txt", "r")
	contents_txt = txtfile.read()
	newfile = open("test.txt", "w")
	prev_value = 65
	for x in contents_txt:	
		curr_value = ord(x)
		print "curr_value=" + str(curr_value) + " prev_value=" + str(prev_value)
		if curr_value == 10 and prev_value == 10:
			newfile.write('\n\n')
			prev_value = curr_value
		if curr_value != 10:
			newfile.write(x)
			prev_value = curr_value	
		if curr_value == 10 and  prev_value != 10:
			newfile.write(' ')
			prev_value = curr_value
	txtfile.close()
	newfile.close()

if __name__ == "__main__":
    main()

```

---

